# prestitonesto · funnel Cessione del Quinto (prototipo)

Prototipo funzionante del funnel di qualificazione lead. File unico `index.html`, nessuna dipendenza, nessun invio reale di dati (il lead finisce nella console del browser).

- **Demo online:** https://tom-pier.github.io/prestitonesto-funnel-cdq/
- **Mappa delle diramazioni, regole ed uscite:** [`MAPPA_FUNNEL.md`](MAPPA_FUNNEL.md)
- **Note di ricostruzione rispetto al riferimento:** [`RICOSTRUZIONE.md`](RICOSTRUZIONE.md)

## Provarlo in locale

```bash
python3 -m http.server 8765
# poi apri http://localhost:8765
```

## Parametri

Tutte le soglie (reddito minimo, età massima, dipendenti, anzianità, rinnovi, SLA di richiamo, endpoint) sono nel blocco `CFG` in testa a `index.html`.

Documento di lavoro Performance Boutique. I testi di conformità (footer, informativa) sono placeholder da completare con ragione sociale, iscrizione OAM e mandante.
