name: Notify Discord on Push
on:
  push:
    branches: [ main ]

jobs:
  notify:
    runs-on: ubuntu-latest
    steps:
      - name: Send to Discord
        uses: tsickert/discord-webhook-action@v7
        with:
          webhook-url: ${{ secrets.DISCORD_WEBHOOK_URL }}
          content: |
            ✅ Push 到 **${{ github.repository }}**@${{ github.ref_name }}
            作者：${{ github.actor }}
          
            提交：${{ github.sha }}

