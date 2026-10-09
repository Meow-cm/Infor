import os
import time
import threading
import discord
from discord.ext import commands
from flask import Flask

# =========================================================
# 1. Web Server giữ bot "sống" 24/7 trên Render
#    Render tự cấp cổng qua biến môi trường PORT,
#    KHÔNG được tự ý đổi số cổng cứng trong code.
# =========================================================
app = Flask(__name__)

@app.route('/')
def home():
    return "CustomRP Active!"

def run_flask():
    port = int(os.environ.get("PORT", 10000))
    app.run(host='0.0.0.0', port=port)


# =========================================================
# 2. Khởi tạo Bot (dùng BOT TOKEN thật từ Developer Portal,
#    KHÔNG phải user token -> không self_bot)
# =========================================================
intents = discord.Intents.default()
client = commands.Bot(command_prefix="!", intents=intents)

# Application ID của chính bot này (công khai, không cần giấu)
APPLICATION_ID = 1557763779595341855
start_time = int(time.time())


@client.event
async def on_ready():
    print(f"[OK] Logged in as {client.user} (ID: {client.user.id})")

    activity = discord.Activity(
        type=discord.ActivityType.playing,
        name="Meowcoding",
        details="MEOW",
        state="Meowing in a pile of programming languages",
        application_id=APPLICATION_ID,
        timestamps={"start": start_time},
        assets={
            'large_image': 'cat-pfp-cat-mugshot--cat-mugshot',
            'large_text': 'Just a fat cat',
            'small_image': 'gemini_generated_image_wdtxxmwdtxxmwdtx',
            'small_text': 'Meow v3.6.2'
        },
        buttons=[
            {"label": ":3", "url": "https://meow-cm.github.io/Infor/"}
        ]
    )

    try:
        await client.change_presence(activity=activity, status=discord.Status.online)
        print("[OK] Presence updated")
    except Exception as e:
        # Một số field (details/state/assets/buttons) có thể bị bỏ qua
        # với bot account tuỳ phiên bản client -> log lại, không crash
        print(f"[WARN] change_presence lỗi hoặc field không được hỗ trợ: {e}")


@client.event
async def on_error(event, *args, **kwargs):
    import traceback
    print(f"[ERROR] Lỗi tại event: {event}")
    traceback.print_exc()


# =========================================================
# 3. Chạy song song: Flask (giữ Render sống) + Discord bot
# =========================================================
if __name__ == "__main__":
    threading.Thread(target=run_flask, daemon=True).start()

    token = os.environ.get("DISCORD_TOKEN")
    if not token:
        raise SystemExit(
            "[FATAL] Thiếu biến môi trường DISCORD_TOKEN. "
            "Vào Render > Environment > thêm DISCORD_TOKEN = bot token thật."
        )

    try:
        client.run(token)
    except discord.errors.LoginFailure:
        raise SystemExit(
            "[FATAL] Token không hợp lệ. Kiểm tra lại DISCORD_TOKEN "
            "trên Render có đúng là bot token (không phải user token) không."
        )
    except discord.errors.HTTPException as e:
        print(f"[FATAL] Lỗi HTTP khi login: {e}")
        raise
