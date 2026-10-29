# Purchase-intent-dashboard-
I built an Executive Sales Dashboard, an interactive, single-page web dashboard that gives leadership a quick view of sales performance. It was built from a dataset of 12,000 website sessions and is designed as “Page 1: Executive Overview.”
"What I Did"

First, I prepared and aggregated the data. Instead of loading 12,000 raw rows into the browser, I pre-aggregated the dataset for every combination of month and visitor type (All, Returning, New, Other). For each combination I stored sessions, orders, orders by region, orders by product-engagement level (Light, Medium, Heavy, Power), and orders by traffic source. This keeps the file small, fast, and fully self-contained.

Second, I designed the KPI layer. The dashboard shows five headline metrics: Sessions, Orders, Conversion Rate, Estimated Sales, and Estimated Profit.

Third, I built the visuals:
- A combined monthly trend chart, with bars for estimated sales and a line for conversion rate.
- Horizontal bar charts for sales by region, sales by product engagement, and the top 10 traffic sources by orders.

Fourth, I added interactivity. Users can filter by month (by clicking a chip or a bar) and by visitor type. Two sliders, Average Order Value and Margin, let executives run what-if scenarios, and every number updates instantly.
"Challenges and How I Solved Them"

1. "No revenue data in the dataset." The data had sessions and purchase flags but no sales or profit columns. I solved this by estimating sales as orders × average order value, and profit as sales × margin. I made the assumption transparent with adjustable sliders and a footnote on the dashboard, so no one mistakes the estimates for actuals.

2. "Large data, lightweight output." Embedding 12,000 rows would have made the page slow. Pre-aggregating into compact arrays solved this, but it required careful indexing so each region, source, and engagement level mapped to the right position.

3. "Keeping every view consistent." Filters, KPIs, charts, and chips all had to respond together. I used one central render function driven by shared state (selected month, visitor type, AOV, margin), so every component always shows the same slice of data.

4. "Missing or uneven data." Some months (for example April) are absent from the dataset, and some segments are very small ("Other" visitors), which can produce zero orders and divide-by-zero issues. I added safeguards so the conversion rate shows "-" instead of breaking, and the charts handle empty values.

5. "Design for executives." Executives need clarity, not clutter. I limited the page to key metrics, used a consistent navy and teal palette, highlighted the selected month in amber, and kept chart labels short.

6. "Cross-device and theme support." Making the charts readable on small screens and in dark mode meant using CSS variables, flexible grids, and a scrollable chart container.

Finally, I focused on usability. The layout is responsive (it works on phones and desktops), supports light and dark mode, and respects mobile safe areas.
