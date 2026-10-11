# Smart Meter Calculator

A lightweight, single-page electricity bill calculator. The interface is primarily in Burmese and lets users estimate a bill from electricity consumption in kilowatt-hours (kWh). It runs directly in a web browser; no build system, backend, or package installation is required.

## Features

- Calculates estimated charges for three customer categories:
  - Residential
  - Non-residential
  - Special power line
- Shows the energy charge, a fixed service fee, and the total.
- Displays a usage-tier breakdown for the selected category.
- Includes energy-saving and electrical-safety tips.
- Responsive layout for mobile and desktop screens.
- Supports submitting the consumption value with **Enter** or the calculate button.

## Run locally

1. Download or clone this project.
2. Open `index.html` in a modern web browser.

Alternatively, from the project directory, start a simple local web server:

```bash
python3 -m http.server 8000
```

Then visit <http://localhost:8000>.

## How to use

1. Enter your electricity consumption in **kWh**.
2. Select the customer category.
3. Choose **Calculate** (or press **Enter** while in the input field).
4. Review the estimated net charge, service fee, total, and tariff breakdown.

The input must be a positive numeric value. The calculator rejects zero, non-numeric values, and values containing a hyphen.

## Tariffs currently encoded

Rates are hard-coded in `index.html` and displayed in Myanmar kyat (Ks). The residential and non-residential rates are progressive: each rate applies only to consumption within its tier.

### Residential

| Consumption tier | Rate per kWh |
| --- | ---: |
| First 50 kWh | 50 Ks |
| Next 50 kWh (51–100) | 100 Ks |
| Next 100 kWh (101–200) | 150 Ks |
| Above 200 kWh | 300 Ks |

### Non-residential

| Consumption tier | Rate per kWh |
| --- | ---: |
| First 5,000 kWh | 250 Ks |
| Next 15,000 kWh (5,001–20,000) | 400 Ks |
| Above 20,000 kWh | 500 Ks |

### Special power line

| Consumption tier | Rate per kWh |
| --- | ---: |
| All consumption | 900 Ks |

A fixed **500 Ks service fee** is added to the energy charge in all categories.

> These are the rates implemented in this project, not a guarantee of current official tariffs. Confirm applicable rates and fees with the relevant electricity provider before relying on an estimate.

## Dependencies

The application is implemented in plain HTML, CSS, and JavaScript. It loads these libraries from public CDNs, so an internet connection may be needed for all styling, icons, and validation alerts to render:

- [Bootstrap 5.3.8](https://getbootstrap.com/) — layout and table styles
- [Font Awesome 7.0.1](https://fontawesome.com/) — icons
- [SweetAlert2 11](https://sweetalert2.github.io/) — invalid-input alert

There is no `npm install` or compilation step.

## Project structure

```text
smart-meter-calc-main/
├── index.html   # Complete application: markup, styles, and calculator logic
└── README.md    # Project documentation
```

## Customization

Tariff rates and the service fee are defined directly in the JavaScript in `index.html`. The tier tables are also written in the page markup, so update both the calculation logic and the displayed table values when changing tariffs.
