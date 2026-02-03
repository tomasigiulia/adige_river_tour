# 🏔️ Skyline Editor - Guida Rapida

## Come Usare lo Skyline Editor

### Apertura
Premi **K** (Keycode per sKyline) per aprire/chiudere lo Skyline Editor

### Funzioni Principali

#### 1. **➕ Aggiungi Nuova Etichetta**
- Clicca sul pulsante verde "Aggiungi Nuova Etichetta"
- Apparirà un'etichetta al centro della vista con il testo "ETICHETTA 1", "ETICHETTA 2", ecc.
- Apparirà anche un marker blu (icona info) per spostarla

#### 2. **🎯 Spostare l'Etichetta**
- **Clicca sul marker blu** per selezionare l'etichetta
- **Trascina il marker** per spostare l'etichetta dove vuoi (es. sopra una montagna)
- L'etichetta si sposterà insieme al marker

#### 3. **📋 Copiare il Codice**
- Seleziona l'etichetta cliccando sul suo marker
- Clicca su "📋 Copia Codice"
- Il codice XML apparirà:
  - Nel riquadro nero in basso del panel
  - Nella console del browser (premi F12 per vederlo)
- **Copia il codice** e incollalo nel file `tour.xml` nella scena desiderata

#### 4. **🗑️ Eliminare un'Etichetta**
- Seleziona l'etichetta cliccando sul marker
- Clicca su "🗑️ Elimina"

#### 5. **👁️ Nascondere/Mostrare i Marker**
- **Nascondi Marker**: nasconde i marker blu, lasciando visibili solo le etichette
- **Mostra Marker**: mostra di nuovo i marker per poterle spostare

## Esempio di Utilizzo

### Scenario: Voglio aggiungere "Monte Baldo" nella scena PANO_5

1. **Apri il tour** e vai alla scena PANO_5
2. **Premi K** per aprire lo Skyline Editor
3. **Clicca "Aggiungi Nuova Etichetta"**
4. **Trascina il marker blu** fino a posizionarlo sopra il Monte Baldo nel panorama
5. **Clicca sul marker** per selezionarlo
6. **Clicca "Copia Codice"**
7. **Apri la console** (F12) e copia il codice che appare
8. **Apri tour.xml** in VS Code
9. **Trova la scena `scene_pano_5`**
10. **Incolla il codice** dentro la scena, ad esempio:

```xml
<scene name="scene_pano_5" ...>
    ...
    
    <!-- Etichetta Monte Baldo -->
    <hotspot name="skyline_label_1"
             style="skyline_label"
             ath="45.123"
             atv="-12.456"
             html="[div style='text-align:center;display:flex;flex-direction:column;align-items:center;'][span style='font-size:12px;opacity:0.9;display:block;margin-bottom:2px;']1.5km · 3 min[br/]800m · 15 min[/span][b style='font-size:18px;display:block;margin-bottom:5px;']ETICHETTA 1[/b][img src='hotspots/arrow_down.svg' style='display:block;width:30px;height:50px;'][/img][/div]"
    />
    
</scene>
```

11. **Modifica il testo** nell'attributo `html`:
    - Cambia `ETICHETTA 1` con `MONTE BALDO`
    - Cambia distanza e tempo se vuoi: `2.3km · 5 min`
12. **Salva tour.xml** e ricarica il tour

## Personalizzare l'HTML dell'Etichetta

Il codice HTML generato usa la sintassi di krpano (parentesi quadre invece di <>).

Esempio:
```html
[div style='text-align:center;display:flex;flex-direction:column;align-items:center;']
    [span style='font-size:12px;opacity:0.9;display:block;margin-bottom:2px;']
        2.3km · 5 min[br/]1200m · 25 min
    [/span]
    [b style='font-size:18px;display:block;margin-bottom:5px;']
        MONTE BALDO
    [/b]
    [img src='hotspots/arrow_down.svg' style='display:block;width:30px;height:50px;'][/img]
[/div]
```

### Cosa puoi modificare:
- **Nome montagna**: dentro `[b]...[/b]`
- **Distanza e tempo**: dentro `[span]...[/span]`
- **Dimensione testo**: cambia `font-size:18px`
- **Colore**: aggiungi `color:#FFAA00;`
- **Rimuovi freccia**: cancella la riga con `[img src='hotspots/arrow_down.svg'...]`

## Tasti Rapidi del Toolbox

- **T**: Apri/Chiudi Toolbox principale
- **K**: Apri/Chiudi Skyline Editor ⭐
- **D**: Distorted Hotspot Editor (per ruotare/scalare etichette esistenti)
- **P**: Polygonal Hotspot Editor
- **M**: Menu principale
- **G**: Griglia
- **S**: Stickies (note)
- **L**: Log (stampa info nella console)

## Note Importanti

1. **Le etichette create nello Skyline Editor sono temporanee**: esistono solo finché il tour è aperto. Per renderle permanenti, devi copiare il codice e incollarlo in `tour.xml`

2. **Usa il Distorted Hotspot Editor (D)** se hai bisogno di ruotare l'etichetta per farla seguire meglio la prospettiva

3. **Le etichette skyline**:
   - NON intercettano il mouse (puoi trascinare la panoramica attraverso di loro)
   - Seguono la prospettiva 3D (distorted="true")
   - Sono sempre visibili
   - Hanno sfondo trasparente di default

4. **Il marker blu** serve solo per spostare l'etichetta durante l'editing. Una volta copiato il codice nel tour.xml, il marker non ci sarà più.

## Troubleshooting

**Problema**: L'etichetta non appare dove voglio
- **Soluzione**: Assicurati di aver cliccato sul marker prima di trascinarlo

**Problema**: Non riesco a vedere il codice
- **Soluzione**: Premi F12 per aprire la console del browser, il codice completo è lì

**Problema**: L'etichetta è troppo grande/piccola
- **Soluzione**: Modifica `font-size` nell'HTML o usa il Distorted Hotspot Editor (D) per scalare

**Problema**: Voglio ruotare l'etichetta
- **Soluzione**: Dopo aver posizionato l'etichetta, chiudi lo Skyline Editor e premi D per aprire il Distorted Hotspot Editor. Lì puoi regolare RX, RY, RZ per ruotarla.

## Workflow Completo

1. Apri il tour → Vai alla scena
2. Premi **K** → Skyline Editor aperto
3. Clicca **Aggiungi** → Etichetta creata
4. **Trascina** il marker → Posizionata
5. Clicca **Copia Codice** → Codice copiato
6. Apri **tour.xml** → Trova la scena
7. **Incolla** il codice → Modifica il testo
8. **Salva** → Ricarica il tour
9. ✅ **Fatto!**

---

**Creato da Skyline Editor v1.0**
