# NIFTY50 Technical Analysis Tracker

A comprehensive Pine Script indicator system for tracking all Nifty50 stocks with real-time technical analysis and trend visualization.

## 📁 File Structure

### NIFTYTRACKER.txt (Main Indicator)
- **Stocks Tracked**: 40 major Nifty50 stocks
- **Sectors**: Finance (11), IT (5), Oil/Gas (4), FMCG (5), Auto (6), Healthcare (4), Telecom (1), Construction (1), Mining/Metals (3)
- **Primary Function**: Complete technical analysis with entry/exit signals

### NIFTYTRACKER10.txt (Secondary Indicator) 
- **Stocks Tracked**: Remaining 10 Nifty50 stocks
- **Purpose**: Extends coverage due to TradingView's 40-stock per script limitation
- **Function**: Provides trend data as external inputs for the main indicator

## 🔧 Technical Indicators Used

### Primary Trend Detection
- **MACD**: Moving Average Convergence Divergence (6, 13, 5)
- **Supertrend**: Trend following indicator (3, 10)
- **Combination Logic**: Both indicators must align for trend confirmation

### Advanced Analysis
- **Spread Analysis**: Price action based on bar range and close position
- **Hull Moving Average**: 55-period HMA for trend smoothing
- **Volume Weight Price (VWAP)**: For price level analysis

## 📊 Visual Outputs

### Main Chart Plots
- **Green Line**: Number of stocks in uptrend
- **Red Line**: Number of stocks in downtrend
- **Character Indicators**: 
  - 'R' = Reliance trend (Green↑/Red↓)
  - 'H' = HDFC Bank trend (Green↑/Red↓)

### Labels (Optional)
- **Green Labels**: Bullish stocks count with sector breakdown
- **Red Labels**: Bearish stocks count with sector breakdown
- **Size**: Automatically adjusts based on market strength (≥7 stocks = larger size)

## ⚙️ Key Parameters

### Configurable Inputs
```pinescript
smashort = 2           // SMA smoothing period
showlabel = false      // Toggle sector breakdown labels
up10/down10/sideway10  // External inputs from NIFTYTRACKER10
```

### Signal Generation
- **Long Entry**: 
  - Uptrend SMA > Downtrend SMA
  - Hull MA trending up
  - ≥7 stocks bullish
  - Reliance & HDFC both bullish
  
- **Short Entry**:
  - Downtrend SMA > Uptrend SMA  
  - Hull MA trending down
  - ≥7 stocks bearish
  - Reliance & HDFC both bearish

## 🚀 Setup Instructions

### Step 1: Load Both Indicators
1. Add **NIFTYTRACKER10** to your chart first
2. Add **NIFTYTRACKER** to the same chart
3. In NIFTYTRACKER settings, connect the external inputs:
   - `up10` → NIFTYTRACKER10: Up 10
   - `down10` → NIFTYTRACKER10: Down 10  
   - `sideway10` → NIFTYTRACKER10: Sideway 10
   - `up10sa` → NIFTYTRACKER10: Up 10 SA
   - `down10sa` → NIFTYTRACKER10: Down 10 SA
   - `sideway10sa` → NIFTYTRACKER10: Sideway 10 SA

### Step 2: Configure Display
- Enable `showlabel = true` for detailed sector analysis
- Adjust `smashort` for signal smoothing (default: 2)
- Set up alerts for entry/exit signals

## 📈 Interpretation Guide

### Market Strength Levels
- **Strong Bullish**: Green line >30, Red line <10
- **Bullish**: Green line >20, Red line <15  
- **Neutral**: Green/Red lines between 15-25
- **Bearish**: Red line >20, Green line <15
- **Strong Bearish**: Red line >30, Green line <10

### Sector Rotation Analysis
Use label tooltips to identify:
- **Leading Sectors**: High concentration in green labels
- **Lagging Sectors**: High concentration in red labels
- **Rotation Opportunities**: Sectors switching between labels

### Entry Timing
- **Trend Following**: Wait for Hull MA alignment
- **Mean Reversion**: Look for extreme readings (>35 or <5)
- **Confirmation**: Both Reliance and HDFC alignment critical

## ⚠️ Important Notes

### TradingView Limitations
- **40 Stock Limit**: Each script can track maximum 40 securities
- **Solution**: Split into two complementary indicators
- **Data Sync**: External inputs ensure unified analysis

### Risk Management
- **Stop Loss**: Built-in 10-point stop for signals
- **Time Exit**: Automatic exit at 3:15 PM
- **Max Trades**: Limited to 2 trades per direction per session

### Performance Optimization
- **Lookahead Bias**: Uses `barmerge.lookahead_on` for real-time data
- **Memory Management**: Arrays reset daily to prevent overflow
- **Computation Efficiency**: Optimized for fast execution

## 🔍 Sector Breakdown

### Banking/Finance (11 stocks)
HDFCBANK, ICICIBANK, KOTAKBANK, AXISBANK, SBIN, SBILIFE, SHRIRAMFIN, BAJFINANCE, BAJAJFINSV, INDUSINDBK, HDFCLIFE

### Information Technology (5 stocks)  
TCS, INFY, HCLTECH, TECHM, WIPRO

### Oil & Gas (4 stocks)
RELIANCE, ONGC, COALINDIA, BPCL

### FMCG (5 stocks)
ITC, HINDUNILVR, NESTLEIND, BRITANNIA, TATACONSUM

### Automotive (6 stocks)
MARUTI, M&M, EICHERMOT, TATAMOTORS, BAJAJ_AUTO, HEROMOTOCO

### Healthcare (4 stocks)
SUNPHARMA, DRREDDY, CIPLA, APOLLOHOSP

### Others
- **Telecom**: BHARTIARTL
- **Construction**: LT  
- **Mining/Metals**: ADANIENT, JSWSTEEL, TATASTEEL
- **Utilities**: HINDALCO, POWERGRID, NTPC
- **Consumer**: TITAN, ASIANPAINT, TRENT
- **Services**: ADANIPORTS
- **Materials**: ULTRACEMCO, GRASIM
- **Capital Goods**: BEL

## 🎯 Best Practices

1. **Monitor Both Charts**: Keep both indicators visible for complete picture
2. **Sector Analysis**: Use labels during market turning points
3. **Confluence Trading**: Combine with price action on Nifty50 index
4. **Session Timing**: Most effective during regular trading hours (9:15 AM - 3:30 PM IST)
5. **Market Context**: Consider overall market sentiment and news flow

---

*Last Updated: July 2025*
*Compatible with: TradingView Pine Script v6*