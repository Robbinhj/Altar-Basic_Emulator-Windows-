name: Bygg och testa ABC80 Emulator

on:
  push:
  pull_request:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Klona repo
        uses: actions/checkout@v4

      - name: Installera byggverktyg
        run: sudo apt-get update && sudo apt-get install -y build-essential libsdl2-dev git

      - name: Kör installation och bygg
        run: bash install-and-run-abc80sim.sh || true

      - name: Bekräftelsemeddelande
        run: echo "🚀 Workflowen kördes klart! Kontrollera stegen ovan för eventuella fel."
