# Guida Etichette Skyline per Virtual Tour

## Come funziona

Le etichette skyline sono hotspot di tipo "text" con `distorted="true"` che seguono la prospettiva della panoramica. Sono sempre visibili e non intercettano il mouse (capture="false"), permettendo di trascinare la panoramica.

## Come aggiungere una nuova etichetta

### Metodo 1: Manuale
Copia questo codice nella scena desiderata:

```xml
<hotspot name="skyline_nome_montagna" 
         style="skyline_label" 
         ath="0" 
         atv="-10" 
         html="[div style='text-align:center;'][img src='hotspots/arrow_down.svg' style='display:block;margin:0 auto 5px;width:30px;height:50px;'][/img][b style='font-size:18px;display:block;margin-bottom:3px;']NOME MONTAGNA[/b][span style='font-size:12px;opacity:0.9;']1.5km · 3 min[br/]800m · 15 min[/span][/div]" 
/>
```

Modifica:
- `name`: nome univoco dell'hotspot
- `ath`: angolo orizzontale (usa editor grafico, vedi sotto)
- `atv`: angolo verticale (usa editor grafico, vedi sotto)
- `html`: contenuto dell'etichetta (nome, distanza, tempo)

### Metodo 2: Editor Grafico (CONSIGLIATO)

1. **Apri il tour** e vai alla scena dove vuoi aggiungere l'etichetta
2. **Premi T** per aprire il Toolbox
3. **Premi D** per aprire il "Distorted Hotspot Editor"
4. **Aggiungi temporaneamente un hotspot** alla scena con il codice sopra
5. **Clicca sull'etichetta** nel panorama per selezionarla
6. **Trascina** l'etichetta per posizionarla sulla montagna/luogo
7. **Usa i controlli**:
   - **RX, RY, RZ**: rotazione su 3 assi per allineare l'etichetta alla prospettiva
   - **SCALE**: dimensione dell'etichetta
   - **Tune** (-/+): modifiche grandi
   - **Fine Tune** (-/+): modifiche piccole e precise
8. **Reset ATH/ATV**: se necessario resettare la posizione
9. **Premi L** per stampare il codice finale con tutti i valori (ath, atv, rx, ry, rz, scale)
10. **Copia il codice** dalla console e sostituisci nel file XML

## Personalizzazione dell'HTML

L'HTML dell'etichetta usa una sintassi speciale di krpano (con parentesi quadre invece di <>):

```html
[div style='text-align:center;']
    [img src='hotspots/arrow_down.svg' style='display:block;margin:0 auto 5px;width:30px;height:50px;'][/img]
    [b style='font-size:18px;display:block;margin-bottom:3px;']NOME LUOGO[/b]
    [span style='font-size:12px;opacity:0.9;']
        1.5km · 3 min[br/]
        800m · 15 min
    [/span]
[/div]
```

Puoi personalizzare:
- **Dimensione testo**: modifica `font-size`
- **Colore**: aggiungi `color:#FFFFFF;` negli style
- **Distanza/tempo**: modifica i valori nel testo
- **Rimuovere la freccia**: elimina la riga `[img...]`
- **Aggiungere icone**: inserisci altre immagini SVG

## Modificare lo stile globale

Se vuoi cambiare l'aspetto di tutte le etichette, modifica lo style `skyline_label` in tour.xml:

```xml
<style name="skyline_label" 
       type="text" 
       distorted="true" 
       capture="false" 
       enabled="false"
       width="220"           <!-- larghezza -->
       height="80"           <!-- altezza -->
       css="text-align:left; color:#FFFFFF; font-family:Arial,sans-serif; font-size:16px; font-weight:bold; text-shadow: 2px 2px 4px #000000;" 
       bgcolor="0x000000"    <!-- colore sfondo -->
       bgalpha="0.0"         <!-- trasparenza sfondo (0.0 = trasparente) -->
       ...
/>
```

## Esempio completo

Vedi la scena `scene_pano_5` nel file tour.xml per un esempio funzionante con l'etichetta `skyline_example`.

## Tasti rapidi Toolbox

- **T**: Apri/Chiudi Toolbox
- **D**: Distorted Hotspot Editor
- **P**: Polygonal Hotspot Editor
- **L**: Stampa codice (Log)
- **M**: Menu principale Toolbox
- **G**: Griglia
- **S**: Stickies (note)

## Suggerimenti

1. **Prospettiva**: usa RX, RY, RZ per far "distorcere" l'etichetta come se fosse parte della scena
2. **Sfondo semi-trasparente**: se il testo non si legge bene, imposta `bgalpha="0.5"` e `bgcolor="0x000000"` nello style
3. **Frecce personalizzate**: crea altri file SVG in hotspots/ con frecce diverse
4. **Multilingua**: usa `get(languages[get(language)].nome_variabile)` invece del testo fisso
