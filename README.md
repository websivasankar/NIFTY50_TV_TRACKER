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

## 🚀 Complete TradingView Setup Instructions

### Prerequisites
- TradingView account (Free or Premium)
- Basic familiarity with TradingView interface

### Step 1: Add NIFTYTRACKER10 (Secondary Indicator)

1. **Open TradingView Chart**
   - Go to [TradingView.com](https://tradingview.com)
   - Open a chart with any Indian stock (e.g., NSE:NIFTY)

2. **Access Pine Editor**
   - Click the "Pine Editor" tab at the bottom of the screen
   - If not visible, click the `</>` icon in the bottom toolbar

3. **Create New Indicator**
   - Click "+ Create" button in Pine Editor
   - Select "New blank indicator"

4. **Copy NIFTYTRACKER10 Code**
   - Delete all default code in the editor
   - Copy the entire content from `NIFTYTRACKER10.txt`
   - Paste it into the Pine Editor

5. **Save and Add to Chart**
   - Click "Save" (Ctrl+S)
   - Name it "NIFTYTRACKER10"
   - Click "Add to Chart"
   - The indicator will appear in a separate pane below the main chart

### Step 2: Add NIFTYTRACKER (Main Indicator)

1. **Create Second Indicator**
   - Click "+ Create" again in Pine Editor
   - Select "New blank indicator"

2. **Copy NIFTYTRACKER Code**
   - Delete all default code
   - Copy the entire content from `NIFTYTRACKER.txt`
   - Paste it into the Pine Editor

3. **Save and Add to Chart**
   - Click "Save" (Ctrl+S)
   - Name it "NIFTYTRACKER"
   - Click "Add to Chart"

### Step 3: Link the Indicators (Critical Step)

1. **Access NIFTYTRACKER Settings**
   - Right-click on the NIFTYTRACKER indicator on your chart
   - Select "Settings" or click the gear icon

2. **Configure External Inputs**
   In the "Inputs" tab, you'll see these fields that need to be connected:
   
   - **Up 10**: Click dropdown → Select "NIFTYTRACKER10: Up 10"
   - **Down 10**: Click dropdown → Select "NIFTYTRACKER10: Down 10"
   - **Sideway 10**: Click dropdown → Select "NIFTYTRACKER10: Sideway 10"
   - **Up 10 sa**: Click dropdown → Select "NIFTYTRACKER10: Up 10 SA"
   - **Down 10 sa**: Click dropdown → Select "NIFTYTRACKER10: Down 10 SA"
   - **Sideway 10 sa**: Click dropdown → Select "NIFTYTRACKER10: Sideway 10 SA"

3. **Apply Settings**
   - Click "OK" to apply the settings
   - The indicators are now properly linked

### Step 4: Configure Display Options

1. **Enable Labels (Optional)**
   - In NIFTYTRACKER settings → Inputs tab
   - Check "Show Label" to see detailed sector breakdowns
   - This will show green/red labels with stock counts and tooltips

2. **Adjust Smoothing**
   - Change "SMA Short" value (default: 2) for signal smoothing
   - Lower values = more sensitive signals
   - Higher values = smoother, less noisy signals

3. **Visual Customization**
   - Go to "Style" tab in settings
   - Customize line colors, thickness, and styles
   - Enable/disable specific plots as needed

### Step 5: Set Up Alerts (Optional)

1. **Create Alert**
   - Right-click on chart → "Add Alert"
   - Or use the clock icon in the top toolbar

2. **Configure Alert Conditions**
   - Source: Select "NIFTYTRACKER"
   - Condition: Choose from available alert conditions
   - Set up notifications (email, SMS, webhook)

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

### Labels (When Enabled)
- **Green Labels**: Bullish stocks count with sector breakdown
- **Red Labels**: Bearish stocks count with sector breakdown
- **Size**: Automatically adjusts based on market strength (≥7 stocks = larger size)
- **Tooltips**: Hover over labels to see which specific stocks are trending

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

## ⚠️ Troubleshooting

### Common Issues

1. **"Study Error" Messages**
   - Ensure both indicators are added to the same chart
   - Check that external inputs are properly linked
   - Refresh the page and re-add indicators if needed

2. **Missing Data/Empty Charts**
   - Verify you're on an Indian stock chart (NSE symbols)
   - Check TradingView data subscription includes Indian markets
   - Try switching to a different timeframe

3. **Indicators Not Connecting**
   - Remove both indicators and re-add in correct order
   - NIFTYTRACKER10 must be added BEFORE NIFTYTRACKER
   - Ensure external input mapping is correct

4. **Labels Not Showing**
   - Enable "Show Label" in NIFTYTRACKER settings
   - Check chart zoom level (labels may be outside visible area)
   - Verify force_overlay settings in code

### Performance Tips
- **Use 15-minute timeframe** for optimal signal generation
- **Keep both indicators on same chart** for proper data linking
- **Avoid excessive label display** on lower timeframes to prevent clutter

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
6. **Risk Management**: Always use stop-losses and position sizing
7. **Backtesting**: Test the strategy on historical data before live trading

## 📱 Mobile Setup

### TradingView Mobile App
1. Install TradingView app on your mobile device
2. Log in with the same account where you created the indicators
3. Open any chart and add the saved indicators
4. The indicators will sync automatically with your desktop setup

## 🤝 Support & Updates

### Getting Help
- Check TradingView's Pine Script documentation
- Join TradingView community forums
- Review Pine Script debugging guides

### Code Updates
- Save your indicator versions before making changes
- Test modifications on paper trades first
- Keep backup copies of working versions

---

**⚠️ Important Disclaimer**: This indicator is for educational and informational purposes only. Always conduct your own research and consider your risk tolerance before making trading decisions. Past performance does not guarantee future results.

*Last Updated: July 2025*  
*Compatible with: TradingView Pine Script v6*  
