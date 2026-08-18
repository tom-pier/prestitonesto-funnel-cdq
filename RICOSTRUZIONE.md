# Ricostruzione step-by-step rispetto al funnel di riferimento

**Base:** funnel Prestito al Telefono (`richiedi.prestitoaltelefono.com/cap/swq_01.php`), 12 screenshot + sorgente JS letto per intero.

## Mappa 1:1

| # | Riferimento | Logica nel codice del riferimento | Prestitonesto (`lungo/index.html`) |
|---|---|---|---|
| 1 | Modal "Dove ti trovi?", CAP, "verifica se la tua zona è coperta" | `resolve_cap.php` restituisce partner, redirect, footer e privacy dinamici: **il CAP sceglie a chi va il lead** | Modal "Dove abiti?", stessa meccanica. Oggi accetta ogni CAP a 5 cifre |
| 2 | Situazione lavorativa: indeterminato / determinato / pensionato | determinato → blocco | "Che tipo di reddito hai?", determinato → uscita spiegata |
| 3 | Datore: grande azienda / piccola / ente PA / famiglia / autonomo | piccola, famiglia, autonomo → blocco. Soglia nel codice 16, negli screenshot 9: cambia per campagna | "Per chi lavori?", soglia parametrica `MIN_EMPLOYEES` (16). Uscite spiegate |
| 4 | Importo: fino a 10k / 20k / 30k / oltre | nessun blocco | identico |
| 5a | Ricerca azienda (DB esterno) | poi modal "quanti dipendenti?" → sotto soglia blocco; anno assunzione oltre soglia → blocco | campo libero azienda + anno, stessa modal, stesse regole |
| 5b | Ente + anno assunzione | PA non passa dal check dipendenti | identico |
| 5c | Tipo pensione (4 opzioni con descrizione, scelta singola) | inabilità o altro → blocco | identico: vecchiaia e superstiti passano, invalidità e altro escono |
| 6 | Reddito netto + cessione in corso sì/no (mese/anno) | reddito < 700 → blocco; cessione recente → blocco se attivato | identico, `MIN_INCOME`, `MIN_YEARS_EXISTING_CQS` |
| 7 | Nascita: nazione, comune, sesso, data | età <18 o >81 → blocco | identico, `MAX_AGE = 81` per tutti |
| 8 | Nome, cognome, email opz., cellulare, privacy | — | "Dove ti richiamiamo?", con la promessa "una chiamata sola, entro X". Privacy e marketing separati |
| 9 | Modal "Conferma il tuo numero" | confronto normalizzato +39/0039 | identico |
| — | Loading "Stiamo verificando le migliori proposte…" | invio + pixel | "Registriamo la richiesta… Assegniamo il consulente…" |
| ✓ | "Richiesta inviata con successo! 🎉" | — | "Fatto." con consulente, SLA, numero, riepilogo, documenti, opt-out |
| ✗ | "Spiacenti, questa offerta non è disponibile per te", senza motivo | tag GTM sul bloccato | uscita spiegata, senza pulsanti, evento `quiz_out{reason}` |

## Identico per scelta
Ordine degli step, progress 9/9, gate CAP, ramificazione al 5, modal dipendenti, doppia conferma numero, tutte le regole di esclusione, tracking del bloccato.

## Diverso per scelta
- Uscite spiegate e senza via di ritorno (rispetto + niente dati falsi da chi non rientra)
- Promessa "una chiamata sola" nello step dati e in thank-you
- Errori che dicono esattamente cosa manca, in ogni step
- Domande sul prodotto, mai "sei…?"
- Palette e tipografia brand

## Non incluso, per ora
DB aziende e comuni con autocomplete, CAP multi-partner, pixel affiliati, endpoint CRM reale.
