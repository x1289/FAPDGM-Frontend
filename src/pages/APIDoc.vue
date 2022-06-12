<template>
  <main>
    <h4>API Dokumentation:</h4>
    <div id="vueapp">
      <p>
        Der Server liefert die im Folgenden beschriebenen Daten im JSON-Format
        aus und ist unter der Addresse
        <a :href="serverAddress" target="_blank">{{ serverAddress }}</a>
        erreichbar.
      </p>
      <pre>{{ jsonData }}</pre>
    </div>
  </main>
</template>

<script>
export default {
  data() {
    return {
      serverAddress: `http://${import.meta.env.VITE_SERVER_URL}:${
        import.meta.env.VITE_SERVER_PORT
      }`,
      jsonData: {
        blockchaininfo: {
          blocks: "number                   // Anzahl aller blöcke insgesamt",
          difficulty: "number               // Aktuelle Mining-Schwierigkeit",
          verificationprogress:
            "number     // Prozent der Synchronisation der verbundenen Bitcoin Node",
          sizeondisk:
            "number               // Aktueller Speicherbedarf der Bitcoin Blockchain",
          bestblockhash: "string            // Hash des aktuellen Blocks",
        },
        block: {
          confirmations:
            "number            // Anzahl der Bestätigungen dieses Blocks",
          size: "number                     // Größe des Blocks in Byte",
          merkleroot: "string               // Merkle-Wurzel dieses Blocks",
          nonce:
            "number                    // Nonce, die diesen Block gültig macht",
          nTx: "number                      // Anzahl an Transaktionen in diesem Block",
        },
        chaintxstats: {
          count:
            "number                    // Anzahl der Transaktionen in den letzten 30 Tagen",
          blockcount:
            "number               // Anzahl der Blöcke in den letzten 30 Tagen",
          txrate:
            "number                   // Anzahl der Transaktionen pro Sekunde",
          minutesperblock: "number          // Minuten pro Block",
        },
        mempoolinfo: {
          size: "number                     // Aktuelle Anzahl der Transaktionen im Memory Pool",
          minfee:
            "number                   // Minimale Gebühren für eine Transaktion in BTC",
          totalfee:
            "number                 // Summe aller Gebühren der Transaktionen im Memory Pool",
        },
        uptime:
          "number                     // Laufzeit der verbundenen Bitcoin Node",
        price: {
          coinbase: {
            usd: "number                    // Preis in USD auf Coinbase.com",
            eur: "number                    // Preis in EUR auf Coinbase.com",
            gbp: "number                    // Preis in GBP auf Coinbase.com",
            jpy: "number                    // Preis in JPY auf Coinbase.com",
          },
          kraken: {
            usd: "number                    // Preis in USD auf Kraken.com",
            eur: "number                    // Preis in EUR auf Kraken.com",
            gbp: "number                    // Preis in GBP auf Kraken.com",
            jpy: "number                    // Preis in JPY auf Kraken.com",
          },
          binance: {
            usd: "number                    // Preis in USD auf Binance.com",
            eur: "number                    // Preis in EUR auf Binance.com",
            gbp: "number                    // Preis in GBP auf Binance.com",
            jpy: "number                    // Preis in JPY auf Binance.com",
          },
        },
      },
    };
  },
};
</script>

<style>
@import "../assets/base.css";

main {
  margin-top: 20px;
}
</style>
