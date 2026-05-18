# Mystery Cipher – Lösungswege

Dieses Repository dient als zentrale Sammlung für die Lösungswege und die mathematisch-technischen Hintergründe der Krypto-Challenges auf der öffentlich zugänglichen Plattform https://mystery-cipher.com/. 

Der Inhalt dieses Repositories beschränkt sich ausschließlich auf die Dokumentation der einzelnen Aufgaben und deren systematische Entschlüsselung. Der Quellcode der eigentlichen Plattform ist hier nicht enthalten.

## Übersicht der Dokumentierten Lösungen

Die Lösungswege sind nach den auf der Website vorgegebenen Schwierigkeitsgraden gegliedert.

---

## Kategorie: Leicht

### Puzzle L1 – Julius’ Nachricht
* **Plattform-Link:** https://mystery-cipher.com/
* **Verfahren:** Caesar-Chiffre (Monalphabetische Substitution)
* **Parameter:** Shift $+7$
* **Chiffretext:** `KPL SVLZBUN PZA JHLZHY`
* **Lösungsweg:**
  Die Entschlüsselung erfolgt durch die Verschiebung des Alphabets um 7 Zeichen rückwärts:
  $$C_i = (P_i - 7) \pmod{26}$$
  * $K \rightarrow D$
  * $P \rightarrow I$
  * $L \rightarrow E$
* **Klartext:** `DIE LOESUNG IST CAESAR`
* **Gesuchte Lösung:** `CAESAR` (oder die vollständige Phrase)

### Puzzle L2 – Web-Code
* **Verfahren:** Base64-Enkodierung
* **Spezifikation:** Zeichenvorrat bestehend aus A–Z, a–z, 0–9, +, / mit `=` als Padding am String-Ende.
* **Chiffretext:** `RElFIExPRVNVTkcgSVNUIEJBU0U2NA==`
* **Lösungsweg:** Standardisierte Base64-Dekodierung des Datenstroms zur Wiederherstellung des Klartexts.
* **Klartext:** `DIE LOESUNG IST BASE64`
* **Gesuchte Lösung:** `BASE64`

### Puzzle L3 – Spiegelschrift
* **Verfahren:** Atbash-Chiffre
* **Spezifikation:** Symmetrische Substitution durch Spiegelung des Alphabets ($A \leftrightarrow Z$, $B \leftrightarrow Y$, $C \leftrightarrow X$).
* **Chiffretext:** `ZGYZHH`
* **Lösungsweg:**
  * $Z \rightarrow A$
  * $G \rightarrow T$
  * $Y \rightarrow B$
* **Gesuchte Lösung:** `ATBASH`

### Puzzle L4 – Maschinensprache
* **Verfahren:** Binär-zu-ASCII-Konvertierung
* **Chiffretext:** `01000010 01001001 01001110 01000001 01010010 01011001`
* **Lösungsweg:** Die 8-Bit-Blöcke (Bytes) werden in ihre dezimalen Äquivalente umgerechnet und über den ASCII-Standard interpretiert:
  * $01000010_2 = 66_{10} \rightarrow \text{B}$
  * $01001001_2 = 73_{10} \rightarrow \text{I}$
  * $01001110_2 = 78_{10} \rightarrow \text{N}$
* **Gesuchte Lösung:** `BINARY`

---

## Kategorie: Mittel

### Puzzle M1 – Fingerabdruck #1
* **Verfahren:** MD5 (Message-Digest Algorithm 5)
* **Spezifikation:** 128-Bit Kryptographische Hashfunktion, dargestellt als 32-stelliger Hexadezimalwert.
* **Hashwert:** `5ae9b7f211e23aac3df5f2b8f3b8eada`
* **Lösungsweg:** Da MD5 nicht kollisionsresistent und anfällig für Brute-Force-Angriffe ist, lässt sich der Wert über bestehende Rainbow Tables (z.B. CrackStation) auflösen.
* **Klartext:** `crypto`
* **Gesuchte Lösung:** `crypto` (case-insensitive)

### Puzzle M2 – Fingerabdruck #2
* **Verfahren:** SHA-256 (Secure Hash Algorithm 2)
* **Spezifikation:** 256-Bit Hashfunktion, dargestellt als 64-stelliger Hexadezimalwert.
* **Hashwert:** `dffdca1f7dd5c94afea2936253a2463a26aad06fa9b5f36b5affc8851e8c8d42`
* **Lösungsweg:** Abgleich des Hashes mit bekannten Wörterbuchlisten oder gängigen Begriffen aus dem Blockchain-Sektor.
* **Klartext:** `BLOCKCHAIN`
* **Gesuchte Lösung:** `BLOCKCHAIN`

### Puzzle M3 – Der Diplomat
* **Verfahren:** Vigenère-Chiffre (Polyalphabetische Substitution)
* **Schlüssel:** `KEY`
* **Chiffretext:** `ZMKIQRBI`
* **Lösungsweg:** Periodische Verschiebung der einzelnen Zeichen basierend auf dem Schlüsselwort:
  $$P_i = (C_i - K_i) \pmod{26}$$
  * $Z(25) - K(10) = 15 \rightarrow \text{V}$
  * $M(12) - E(4) = 8 \rightarrow \text{I}$
  * $K(10) - Y(24) = -14 \equiv 12 \pmod{26} \rightarrow \text{G}$
* **Gesuchte Lösung:** `VIGENERE`

### Puzzle M4 – Exklusiv-Oder
* **Verfahren:** XOR-Verknüpfung
* **Schlüssel:** `0x42` (Dezimal: 66)
* **Chiffretext (Hex):** `1a 0d 10`
* **Lösungsweg:** Bitweise XOR-Operation ($\oplus$) jedes Bytes mit dem statischen Key:
  * $\text{0x1A} \oplus \text{0x42} = 26 \oplus 66 = 88 \rightarrow \text{X}$
  * $\text{0x0D} \oplus \text{0x42} = 13 \oplus 66 = 79 \rightarrow \text{O}$
  * $\text{0x10} \oplus \text{0x42} = 16 \oplus 66 = 82 \rightarrow \text{R}$
* **Gesuchte Lösung:** `XOR`

---

## Kategorie: Schwer

### Puzzle H1 – 13 & 64
* **Verfahren:** Kaskadenverschlüsselung (ROT13 + Base64)
* **Chiffretext:** `WUJSRkhBVCBGUFVKUkU=`
* **Lösungsweg:** Im ersten Schritt wird die Base64-Kodierung aufgelöst. Das Resultat wird anschließend einer ROT13-Dekodierung (Verschiebung um 13 Stellen) unterzogen:
  1. `WUJSRkhBVCBGUFVKUkU=` $\rightarrow$ `YBRFHAT FPUJRE`
  2. `YBRFHAT FPUJRE` $\rightarrow$ `LOESUNG SCHWER`
* **Gesuchte Lösung:** `SCHWER` (oder die vollständige Phrase)

### Puzzle H2 – Verkleidete 64
* **Verfahren:** Kaskadenverschlüsselung (Base64 + Caesar)
* **Chiffretext:** `WpcGWdGYV0mCWANd`
* **Lösungsweg:** Zuerst muss die Caesar-Verschiebung um $-5$ Stellen auf den gesamten String angewendet werden (unter Beibehaltung von Groß- und Kleinschreibung). Der resultierende String entspricht einer gültigen Base64-Struktur und wird dekodiert:
  1. `WpcGWdGYV0mCWANd` $\rightarrow$ `RkxBRyBTQ0hXRVIy`
  2. `RkxBRyBTQ0hXRVIy` $\rightarrow$ `FLAG SCHWER2`
* **Gesuchte Lösung:** `SCHWER2`

### Puzzle H3 – Primzahlen-Power
* **Verfahren:** Asymmetrisches Kryptosystem (RSA)
* **Parameter:** Öffentlicher Schlüssel $(n=33, e=7)$, Kryptotext: `[18, 4, 18]`
* **Lösungsweg:**
  1. Faktorisierung des Moduls $n$: $n = p \cdot q = 3 \cdot 11$.
  2. Berechnung der Eulerschen Phi-Funktion: $\varphi(n) = (3-1) \cdot (11-1) = 20$.
  3. Berechnung des privaten Exponenten $d$ via Modular Inverse: $d \cdot 7 \equiv 1 \pmod{20} \rightarrow d = 3$.
  4. Entschlüsselung über $m = c^d \pmod n$:
     * $18^3 \pmod{33} = 5832 \pmod{33} = 18 \rightarrow \text{R}$
     * $4^3 \pmod{33} = 64 \pmod{33} = 31 \rightarrow \text{S}$
* **Gesuchte Lösung:** `RSA`

### Puzzle H4 – Blockchiffre
* **Verfahren:** AES-128-ECB (Symmetrische Blockchiffre)
* **Schlüssel:** `GEHEIM`
* **Chiffretext (Base64):** `U2FsdGVkX1+vupppZksvRgBkdW5nIGFlcw==`
* **Lösungsweg:** Der Base64-String wird dekodiert und der resultierende Ciphertext mittels des Electronic Codebook Mode (ECB) und dem definierten Key entschlüsselt.
* **Gesuchte Lösung:** `AES`

---

## Kategorie: Extrem

### Puzzle X1 – Das verborgene Geheimnis

Diese Challenge erfordert ein zweistufiges Vorgehen aus OSINT/Steganographie und asymmetrischer Kryptographie.

#### Stufe 1: Metadaten-Analyse (EXIF)
Das auf der Plattform bereitgestellte Bild enthält eingebettete GPS-Metadaten. Die Extraktion liefert folgende Werte:
`40°44'52.5"N 73°59'7.5"W`

Diese Koordinaten verweisen auf das *Empire State Building*. Die Eingabe des entsprechenden Pfades schaltet das versteckte Verzeichnis auf der Website frei: `/empire-state`.

#### Stufe 2: Dekonstruktion des kryptographischen Vektors
Auf der Unterseite befindet sich das Array `[14, 18, 26, 6, 14, 7]`. Die mathematische Entschlüsselung erfolgt analog zu Puzzle H3 mit den bekannten RSA-Parametern $n=33$ und $d=3$ über die Funktion $m = c^3 \pmod{33}$:
* $14^3 \pmod{33} = 2744 \pmod{33} = 5 \rightarrow \text{E}$
* $18^3 \pmod{33} = 5832 \pmod{33} = 24 \rightarrow \text{X}$
* $26^3 \pmod{33} = 17576 \pmod{33} = 20 \rightarrow \text{T}$
* $6^3 \pmod{33} = 216 \pmod{33} = 18 \rightarrow \text{R}$
* $14^3 \pmod{33} = 5 \rightarrow \text{E}$
* $7^3 \pmod{33} = 343 \pmod{33} = 13 \rightarrow \text{M}$

* **Gesuchte Lösung:** `EXTREM`

---

## Lizenz
Dieses Projekt ist unter den Bedingungen der MIT-Lizenz lizenziert. Details sind der Datei [LICENSE](LICENSE) zu entnehmen.
