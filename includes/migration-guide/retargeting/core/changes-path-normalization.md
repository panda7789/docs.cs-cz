---
ms.openlocfilehash: 04c4fb4c8e9da8c58a5e26f78a7b13aa6a0df4a0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614461"
---
### <a name="changes-in-path-normalization"></a>Změny normalizace cesty

#### <a name="details"></a>Podrobnosti

Počínaje aplikacemi, které cílí na .NET Framework 4.6.2, způsob, jakým se změnily cesty modulu runtime normalizovat. Normalizace cesty zahrnuje úpravu řetězce, který identifikuje cestu nebo soubor tak, aby splňoval platnou cestu v cílovém operačním systému. Normalizace obvykle zahrnuje:

- Kanonizace součásti a oddělovače adresářů.
- Použití aktuálního adresáře na relativní cestu.
- Vyhodnocuje se relativní adresář (.) nebo nadřazený adresář (..) v cestě.
- Ořezávání zadaných znaků.
Počínaje aplikacemi, které cílí na .NET Framework 4.6.2, jsou ve výchozím nastavení povolené následující změny normalizace cesty:
  - Modul runtime se odkládá na funkci [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) operačního systému k normalizaci cest.
- Normalizace už nezahrnuje oříznutí konce segmentů adresáře (například místa na konci názvu adresáře).
- Podpora syntaxe cest zařízení v úplném vztahu důvěryhodnosti, včetně `\\.\` a, pro vstupně-výstupní rozhraní API souborů v mscorlib.dll `\\?\` .
- Modul runtime neověřuje cestu k syntaxi zařízení.
- Podporuje se použití syntaxe zařízení pro přístup k alternativním datovým proudům.
Tyto změny zlepšují výkon a zároveň umožňují přístup k dříve nepřístupným cestám metod. Aplikace, které cílí na .NET Framework 4.6.1 a starší verze, ale jsou spuštěné v .NET Framework 4.6.2 nebo novějším, tato změna neovlivní.

#### <a name="suggestion"></a>Návrh

Aplikace, které cílí na .NET Framework 4.6.2 nebo novější, si mohou tuto změnu odhlásit a použít starší normalizaci přidáním následujícího do `<runtime>` oddílu konfiguračního souboru aplikace:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>
```

Aplikace, které cílí na .NET Framework 4.6.1 nebo starší, ale běží na .NET Framework 4.6.2 nebo novějším, můžou povolit normalizaci cest přidáním následujícího řádku do `<runtime>` oddílu souboru Application. Configuration:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>
```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.6.2       |
| Typ    | Změna cílení |
