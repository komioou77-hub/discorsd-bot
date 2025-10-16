name: Notify Discord on Push

on:
  push:
    branches: [ main ]   # 当推送到 main 分支时触发

jobs:
  notify:
    runs-on: ubuntu-latest
    steps:
      - name: Send message to Discord
        run: |
          curl -H "Content-Type: application/json" \
               -d '{"content":"🚀 New commit pushed to main!"}' \
               ${{ secrets.DISCORD_WEBHOOK_URL }}

