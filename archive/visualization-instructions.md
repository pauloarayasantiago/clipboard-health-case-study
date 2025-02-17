# Instructions for Adding Census Data to Day-of-Week Visualizations

## Modification 1: Day-of-Week Analysis (Section 8)

Please add census data to the day-of-week analysis visualization by making these changes:

1. Before the plotting code, add census calculations with facility-level aggregation:
```python
# First calculate facility-level averages for each day of week
facility_daily_census = (
    df_pbj_nurse
    .groupby(['provnum', 'day_of_week'])['mdscensus']
    .mean()
    .reset_index()
)

# Then calculate the overall average across facilities
census_daily = (
    facility_daily_census
    .groupby('day_of_week')['mdscensus']
    .mean()
)

# Calculate weekend vs weekday census difference at facility level
facility_weekend_census = (
    df_pbj_nurse
    .groupby('provnum')
    .apply(lambda x: x[x['is_weekend']]['mdscensus'].mean())
)

facility_weekday_census = (
    df_pbj_nurse
    .groupby('provnum')
    .apply(lambda x: x[~x['is_weekend']]['mdscensus'].mean())
)

# Calculate the mean percentage change across facilities
census_weekend_dip = (
    (facility_weekend_census / facility_weekday_census - 1).mean() * 100
)
```

2. Modify the plot layout to accommodate census data:
```python
# Change the subplot layout from (2,1) to (3,1)
fig, (ax1, ax2, ax3) = plt.subplots(3, 1, figsize=(15, 16))
```

3. Add the census subplot after the support staff plot:
```python
# Census plot with enhanced styling
ax3.plot(
    day_order,
    census_daily.reindex(day_order),
    marker='o',
    linewidth=2.5,
    markersize=8,
    color='#9370DB',  # Soft purple for census
    label='Average Census'
)

# Add data labels
for i, val in enumerate(census_daily.reindex(day_order)):
    ax3.text(
        i, val + 0.5,
        f'{val:.1f}',
        ha='center',
        va='bottom',
        fontsize=10,
        color='#9370DB'
    )

# Weekend highlight
ax3.axvspan(4.5, 6.5, color='#FFFF99', alpha=0.2)

# Add error bars showing facility variation
facility_std = (
    facility_daily_census
    .groupby('day_of_week')['mdscensus']
    .std()
    .reindex(day_order)
)

ax3.errorbar(
    range(len(day_order)),
    census_daily.reindex(day_order),
    yerr=facility_std,
    fmt='none',
    color='#9370DB',
    alpha=0.3,
    capsize=5
)

# Enhanced title and labels
ax3.set_title('Average Daily Census (Facility-Level)', fontsize=14, pad=20, fontweight='bold')
ax3.set_xlabel('Day of Week', fontsize=12)
ax3.set_ylabel('Average Census', fontsize=12)
ax3.grid(True, linestyle='--', alpha=0.3)
ax3.legend(
    fontsize=12,
    bbox_to_anchor=(0.5, 1.15),
    loc='center',
    frameon=True
)
```

4. Update the weekend increase information text box:
```python
increase_text = (
    'Weekend vs. Weekday Changes (Facility-Level Averages):\n\n'
    f'RN Contract:      {increases["RN"]:+.1f}%\n'
    f'LPN Contract:     {increases["LPN"]:+.1f}%\n'
    f'CNA Contract:     {increases["CNA"]:+.1f}%\n'
    f'Support Contract: {increases["Support"]:+.1f}%\n'
    f'Census:           {census_weekend_dip:+.1f}%'
)
```

## Modification 2: Exclusive RN Contract Staffing by Day (Section 9)

Add census as a secondary y-axis to the exclusive contract staffing visualization:

1. Before the plotting code, add facility-level census calculations:
```python
# Calculate facility-level averages for each day
facility_daily_census = (
    df_pbj_nurse
    .groupby(['provnum', 'day_of_week'])['mdscensus']
    .mean()
    .reset_index()
)

# Calculate overall average across facilities
census_by_day = (
    facility_daily_census
    .groupby('day_of_week')['mdscensus']
    .mean()
    .reindex(day_order)
)

# Calculate standard deviation across facilities
census_std_by_day = (
    facility_daily_census
    .groupby('day_of_week')['mdscensus']
    .std()
    .reindex(day_order)
)
```

2. Add secondary y-axis for census with error bars:
```python
# Create the secondary axis
ax2 = ax.twinx()

# Plot census line
line = ax2.plot(
    range(len(day_order)),
    census_by_day.values,
    color='#9370DB',  # Soft purple
    marker='o',
    linewidth=2,
    markersize=8,
    label='Average Census'
)

# Add error bars
ax2.errorbar(
    range(len(day_order)),
    census_by_day.values,
    yerr=census_std_by_day.values,
    fmt='none',
    color='#9370DB',
    alpha=0.3,
    capsize=5
)

# Add census data labels
for i, val in enumerate(census_by_day):
    ax2.text(
        i,
        val + (val * 0.02),  # 2% padding
        f'{val:.1f}',
        ha='center',
        va='bottom',
        color='#9370DB',
        fontsize=10
    )

# Configure secondary axis
ax2.set_ylabel('Average Census (Facility-Level)', color='#9370DB', fontsize=12)
ax2.tick_params(axis='y', labelcolor='#9370DB')
```

3. Update the legend to include both metrics:
```python
# Combine legends
lines1, labels1 = ax.get_legend_handles_labels()
lines2, labels2 = ax2.get_legend_handles_labels()
ax.legend(
    lines1 + lines2,
    labels1 + labels2,
    fontsize=12,
    loc='upper right',
    frameon=True,
    edgecolor='black'
)
```

4. Add facility-level census weekend difference to summary text:
```python
# Calculate weekend vs weekday difference at facility level
facility_weekend_census = (
    df_pbj_nurse
    .groupby('provnum')
    .apply(lambda x: x[x['is_weekend']]['mdscensus'].mean())
)

facility_weekday_census = (
    df_pbj_nurse
    .groupby('provnum')
    .apply(lambda x: x[~x['is_weekend']]['mdscensus'].mean())
)

census_weekend_dip = (
    (facility_weekend_census / facility_weekday_census - 1).mean() * 100
)

summary_text = (
    f"Weekend total: {weekend_pct:.1f}% ({weekend_days:.0f} days)\n"
    f"Weekday total: {weekday_pct:.1f}% ({weekday_days:.0f} days)\n"
    f"Total exclusive contract days: {exclusive_by_day.sum():.0f}\n"
    f"Weekend census change: {census_weekend_dip:+.1f}% (facility-level avg)"
)
```

Key changes from the previous version:
1. All census calculations now use facility-level aggregation first
2. Added error bars to show facility-to-facility variation
3. Updated labels to clarify that these are facility-level averages
4. Included facility-level standard deviations in the visualizations
5. Modified the weekend dip calculation to compute at the facility level first

Note: Make sure to adjust the subplot spacing and overall figure