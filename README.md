# Analýza signálu EKG

## 1. Rezampling signálu
- Navrhol som low-pass Butterworth filter 5. rádu s orezovou frekvenciou tesne pod 50 Hz.
- Použil som funkcie 'butter' a 'filtfilt' z knižnice 'scipy.signal' na filtrovanie signálu.
- Signál som následne rezamploval na požadovanú frekvenciu 100 Hz pomocou funkcie 'decimate', čo zjednodušilo ďalšiu analýzu.

## 2. Filtrovanie signálu
- Navrhol som Butterworth bandpass filter 5. rádu s hranicami 10 Hz a 20 Hz.
- Použil som funkciu 'filtfilt' na aplikáciu filtra bez fázového skreslenia.

## 3. Detekcia komplexu QRS
- **Na základe prahu:** Identifikoval som max. amplitúdu vo filtrovanom signáli a nastavil prah detekcie na 60% tejto amplitúdy.
- **Na základe autokorelácie:** Začal som identifikáciou iniciálnych výrazných peakov v signáli a následne som vykonal autokoreláciu vzorky QRS komplexu s celým signálom.
- **Na základe spektrogramu:** Nastavil som parametre spektrogramu a na základe priemerných hodnôt a odchýlok energie určil prah detekcie QRS komplexov.
- **Na základe obálky a Hilbertovej transformácie:** Implementoval som vlastnú funkciu na vykonanie Hilbertovej transformácie a následne som získal obálku signálu.

## 4. Detekcia intervalu R-R
- Identifikoval som vrcholy v signáli, ktoré prekračovali stanovený prah na základe 60% max. amplitúdy signálu.
- Vypočítal som časové body v sekundách na základe týchto vrcholov a následne premenil R-R intervaly na milisekundy.

## 5. Záver
- Úspešne som analyzoval signály EKG s dôrazom na detekciu komplexu QRS a výpočet intervalov R-R.
- Použil som rôzne techniky spracovania signálu ako filtrovanie, rezampling, Hilbertova transformácia a výpočet spektrogramu na efektívnu identifikáciu dôležitých vlastností signálu EKG.
