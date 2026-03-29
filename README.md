# Freqtrade Paper Trading Deployment

**Subdomain:** https://freqtrade.rainomotion.com
**Mode:** Paper Trading (Dry Run - $10,000 virtual USDT)
**Telegram Control:** Enabled (chat_id: 389857712)

## Deployment Status

✅ Configuration files created
✅ Credentials saved in 1Password (`Freqtrade Paper Trading Bot`)
⏳ Pending: Coolify deployment
⏳ Pending: Telegram bot token configuration

---

## Configuration Summary

### Paper Trading Settings
- **Initial Balance:** $10,000 USDT (virtual)
- **Max Open Trades:** 3 simultaneous positions
- **Markets:** BTC, ETH, SOL, XRP (Binance spot)
- **Strategy:** SampleStrategy (default - can be customized)
- **Risk:** ZERO (no real money - simulation only)

### Access
- **WebUI:** https://freqtrade.rainomotion.com (after deployment)
- **Username:** rabiaa
- **Password:** Stored in 1Password
- **Telegram:** Control bot via commands (after bot token setup)

---

## Deployment Steps (Autonomous)

### 1. Push to GitHub
```bash
cd /tmp/freqtrade-deploy
git init
git add .
git commit -m "Initial Freqtrade paper trading setup"
gh repo create freqtrade-deployment --private --source=. --push
```

### 2. Deploy on Coolify
- Service Type: Docker Compose
- Repository: github.com/rainollm/freqtrade-deployment
- Domain: freqtrade.rainomotion.com
- Environment variables from 1Password

### 3. Telegram Bot Setup
**Option A: Reuse existing bot** (transcriber bot token)
**Option B: Create new bot** (@BotFather → /newbot → copy token)

Set in Coolify environment:
```
TELEGRAM_BOT_TOKEN=<token>
TELEGRAM_CHAT_ID=389857712
```

### 4. Start Trading (Auto)
- Bot starts in dry-run mode automatically
- Telegram commands active immediately
- WebUI accessible at https://freqtrade.rainomotion.com

---

## Telegram Commands (Once Live)

### Basic Control
- `/start` - Start the bot
- `/stop` - Stop the bot
- `/status` - Show open positions
- `/profit` - Show total profit/loss
- `/balance` - Show account balance

### Trading
- `/forceexit <trade_id>` - Close specific position
- `/performance` - Show performance per pair
- `/daily` - Daily profit/loss summary

### Info
- `/help` - Show all commands
- `/version` - Bot version

---

## Strategy Customization (Later)

Default strategy: `SampleStrategy` (basic trend-following)

To add custom strategies:
1. Create `.py` file in `user_data/strategies/`
2. Update `config.json` → `"strategy": "YourStrategyName"`
3. Restart bot

---

## Monitoring & Logs

- **WebUI Dashboard:** https://freqtrade.rainomotion.com
- **Logs:** `user_data/logs/freqtrade.log`
- **Database:** `user_data/tradesv3.sqlite`
- **Telegram:** Real-time alerts on trades

---

## Safety Notes

✅ **Paper trading ONLY** - No real money at risk
✅ **No exchange API keys required** for dry-run
✅ **Zero risk** - purely educational simulation
⚠️ **Do NOT switch to live trading** without:
  - 12+ weeks successful paper trading
  - Positive expectancy proven
  - Full understanding of risks
  - Starting capital you can afford to lose 100%

---

## Next Steps (After Deployment)

1. ✅ Deploy to Coolify
2. ✅ Configure Telegram bot token
3. ✅ Access WebUI and verify bot is running
4. ✅ Send `/status` to Telegram to test
5. ✅ Let it run for 24 hours and observe first trades
6. ✅ Track results in trading journal (Google Sheets)

---

**Estimated Setup Time:** 15-20 minutes
**Estimated First Trade:** Within 1-4 hours (depends on market conditions)
