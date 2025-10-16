on: push
jobs:
  build:
    steps:
      - run: npm test
      - run: |
          if [ $? -eq 0 ]; then
            MSG="✅ Tests passed!"
          else
            MSG="❌ Tests failed!"
          fi
          curl -H "Content-Type: application/json" \
               -d "{\"content\": \"$MSG\"}" \
               ${{ secrets.DISCORD_WEBHOOK_URL }}
