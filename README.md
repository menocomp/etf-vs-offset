# ETF vs leaving money in redraw/offset

A small web page that answers one question:

> What yearly price growth would make an ETF end up level with the interest saved by leaving the same money in a home loan redraw/offset?

If you expect the ETF to grow faster than the break-even figure, it comes out ahead. If you expect slower growth, leaving the money in redraw/offset wins. The page works this out after tax and brokerage fees.

It is for an Australian resident and for ASX-listed, Australian-domiciled ETFs only.

## General information only

**This is general information only. It is not financial, tax or investment advice.** It does not take your personal situation into account. The results come from a simple model with the assumptions listed below, and real outcomes will differ. Check the numbers against your own tax statements and talk to a licensed adviser or registered tax agent before you make a decision.

**There is no warranty of any kind.** The page and its code are provided "as is", without any promise that they are accurate, complete or up to date. The author is not liable for any loss or damage that comes from using them.

## How to use it

1. Open `index.html` in a browser. There is no build step and nothing to install. It only loads a Google Fonts stylesheet from the internet, and works without it.
2. Fill in the boxes on the left. Everything on the right updates as you type.
   - **Investment:** the amount, the number of years you hold it, and the brokerage fee per trade.
   - **Home loan:** your loan rate.
   - **Capital gains tax:** your tax rate in the year you sell, inflation for indexation, and the minimum CGT rate.
   - **Fund and dividends:** pick a fund preset (IVV, NDQ, A200 or VAS) or type your own dividend type, yield and tax rate on dividends.
3. Read the result on the right.
   - **Break-even** shows the yearly price growth where the ETF and redraw/offset finish level.
   - **The working at break-even** shows each step in dollars.
   - **Test a growth rate** lets you type a growth rate you expect and see which side comes out ahead, and by how much.
4. "Reset all" puts every box back to the defaults.

### Defaults

| Setting | Default |
|---|---|
| Amount | $6,000 |
| Years held | 1 |
| Brokerage per trade | $3 |
| Loan rate | 6.24% a year |
| Tax rate on dividends | 39% (37% plus 2% Medicare) |
| Tax rate in the year you sell | 17% (15% plus 2% Medicare) |
| Inflation for indexation | 2.5% |
| Minimum CGT rate | 30% |
| Fund | IVV preset |

## How the numbers are worked out

- **Redraw/offset saving:** the amount plus the buy fee, earning the loan rate, compounded monthly for the years held.
- **Dividends:** each year the ETF pays a dividend based on its value at the start of that year. The dividend is taxed at your dividend rate, and what is left is assumed to go against the loan, saving interest until the sale. Dividends are not reinvested (DRP off).
- **Foreign funds (IVV, NDQ):** the dividend is grossed up for the foreign income tax offset (FITO) before tax is worked out.
- **Franked funds (A200, VAS):** the dividend is grossed up for franking credits. If the credits are bigger than the tax, the difference is treated as a refund.
- **Sale:** the cost base goes up each year by inflation (indexation), and the gain above it is taxed at your tax rate in the sale year or the minimum CGT rate, whichever is higher. This follows the new capital gains tax rules from 1 July 2027. The sell fee comes off the proceeds.
- **Break-even:** the page tries growth rates until the ETF profit after tax and fees equals the redraw/offset saving.

A fund is treated as either foreign or franked, not both.

## Fund presets

Clicking a fund tag fills in only the dividend type, the FITO or franking figures, and the yield. All figures are as at 30 September 2026 and will go out of date.

| Ticker | Type | FITO or franking | Cash yield | Where it came from |
|---|---|---|---|---|
| IVV | Foreign | 15% FITO | 1.25% | BlackRock fact sheet, 12 month trailing yield |
| NDQ | Foreign | 15% FITO | 1.4% | BetaShares fact sheet, 12 month distribution yield |
| A200 | Franked | 71.1% franked, company rate 30% | 3.3% | BetaShares fact sheet, 12 month cash yield and franking level |
| VAS | Franked | 79.59% franked, company rate 30% | 3.2% | Vanguard website: the last four quarterly payments divided by the 30 September 2026 price. The franking level is for the year to June 2026 and is worked out differently to A200's |

The 15% FITO for IVV and NDQ is the US/Australia treaty cap on dividend withholding. It is an assumption. The real figure is on each fund's annual tax statement.

If you change any preset number by hand, the tag switches to "Custom".

## Limitations

In rough order of importance:

1. **ASX-listed, Australian-domiciled ETFs only.** US-listed and other overseas funds are taxed differently and are not covered.
2. **Flat growth rate.** The model grows the ETF by the same percentage every year. Real returns go up and down, and the order of good and bad years matters.
3. **One lump sum.** You buy once and sell once. Dollar cost averaging is not modelled.
4. **DRP is assumed off.** Reinvested dividends would each need their own cost base and 12 month indexation test.
5. **Old CGT discount not modelled.** The 50% discount that applies to gains made before 1 July 2027 is ignored, so holds that straddle that date are a little off.
6. **Constant loan rate.** The loan rate is assumed to stay the same for the whole hold. Loan interest is not tax deductible because it is a home loan.
7. **Franking.** The 45 day holding rule is not modelled, the credit is assumed to be fully usable and refundable, and any interest or other income in a distribution is not separated out.
8. **General information only.** See the notice at the top.

## License

The code in this repo is licensed under the [PolyForm Noncommercial License 1.0.0](https://polyformproject.org/licenses/noncommercial/1.0.0), which allows non-commercial use only. See the `LICENSE` file for the full text, or visit [polyformproject.org](https://polyformproject.org).

## Files

- `index.html`: the whole calculator (page, styles and script in one file).
- `LICENSE`: the PolyForm Noncommercial License 1.0.0, with the required copyright notice.
