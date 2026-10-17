# Blinkit Grocery Analytics Dashboard

An interactive, Power BI-style sales dashboard for the Blinkit grocery dataset. It is a single HTML file with no build step and no framework, and every visual is connected to every other through cross-filtering.

![Dashboard preview](assets/dashboard-preview.png)
<!-- Add a screenshot at assets/dashboard-preview.png -->

## Features

- **Cross-filtering across all visuals.** Click any bar, donut slice, column or table row and every other chart updates, the way slicers work in Power BI. Click again to deselect.
- **KPI cards that switch the measure.** Total Sales, Avg Sales, No. of Items and Avg Rating are clickable, and the charts re-draw using the chosen measure.
- **Active filter chips.** See what is applied at a glance, remove filters one by one, or use "Clear all filters".
- **Blinkit-themed palette.** Yellow for default bars, green for selections, dark green for headers and the table.
- **Light and dark mode.** Follows the viewer's system setting.
- **Responsive and keyboard accessible.** Works on phones, and every clickable element can be reached and toggled with the keyboard.

## Visuals

| Visual | Dimension |
|---|---|
| Donut | Item Fat Content |
| Donut | Outlet Size |
| Horizontal bars | Outlet Location Type (Tier 1, 2, 3) |
| Horizontal bars | Item Type (16 categories) |
| Columns | Outlet Establishment Year |
| Scorecard table | Outlet Type (items, total sales, avg sales, avg rating, avg visibility) |

## Dataset

`BlinkIT_Grocery_Data.xlsx` has 8,523 item records and 12 columns:

| Column | Description |
|---|---|
| Item Fat Content | Low Fat or Regular |
| Item Identifier | Unique item ID |
| Item Type | Product category (Dairy, Snack Foods, Meat, and so on) |
| Outlet Establishment Year | Year the outlet opened (2011 to 2022) |
| Outlet Identifier | Outlet ID (10 outlets) |
| Outlet Location Type | Tier 1, Tier 2 or Tier 3 |
| Outlet Size | Small, Medium or High |
| Outlet Type | Grocery Store or Supermarket Type 1, 2, 3 |
| Item Visibility | Share of display area given to the item |
| Item Weight | Item weight (1,463 values are missing) |
| Sales | Sales value (the dataset does not state a currency) |
| Rating | Customer rating, 1 to 5 |

### Data cleaning

- **Item Fat Content** had five spellings (`Low Fat`, `LF`, `low fat`, `Regular`, `reg`). They are merged into two values, **Low Fat** and **Regular**.
- **Item Weight** is not used in the dashboard, so its missing values do not affect any figure.

### Headline figures

- 8,523 item records across 10 outlets
- Total sales of about 1.20M
- Average sales per item of about 141.0
- Average rating of about 3.97

## Getting started

1. Clone the repository:
   ```bash
   git clone https://github.com/<your-username>/blinkit-dashboard.git
   cd blinkit-dashboard
   ```
2. Open `blinkit_dashboard.html` in any modern browser.

That is all. The cleaned data is embedded in the HTML file, so no server or install is needed. The only external request is the Outfit font from Google Fonts, and the page falls back to the system font if it is offline.

## Project structure

```
blinkit-dashboard/
├── blinkit_dashboard.html      # The dashboard (HTML, CSS, JS and embedded data)
├── BlinkIT_Grocery_Data.xlsx   # Original dataset
├── assets/
│   └── dashboard-preview.png   # Screenshot for this README
└── README.md
```

## Updating the data

The dataset is stored inline in the HTML as an array of rows in this order:

```
[fat, type, year, location, size, outletType, visibility, sales, rating]
```

To refresh it, clean the Excel file with pandas (apply the fat-content mapping above), export the rows in that order as JSON, and replace the data array in the `<script>` block.

## Built with

- Vanilla JavaScript, HTML and CSS (no libraries)
- Inline SVG for the donut charts
- Python and pandas for cleaning and embedding the data

## Recreating it in Power BI

The same design maps directly to Power BI:

- **Theme colours:** `#F8CB46` (yellow), `#0C831F` (green), `#085A15` (dark green), `#FFF9E3` (cream background)
- **Cross-filtering:** Power BI does this by default between visuals on the same page
- **Measure switching:** use a field parameter over Total Sales, Avg Sales, Item Count and Avg Rating

## License

Released under the MIT License. Add a `LICENSE` file to the repository to apply it.

## Author

Your Name · [GitHub](https://github.com/<your-username>) · [LinkedIn](https://www.linkedin.com/in/<your-profile>)
