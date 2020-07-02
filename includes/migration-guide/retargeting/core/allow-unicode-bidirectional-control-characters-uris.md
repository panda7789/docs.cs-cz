---
ms.openlocfilehash: 53d74db1a77e62cc64250658281fd3e4706fe494
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614428"
---
### <a name="allow-unicode-bidirectional-control-characters-in-uris"></a>Povoluje v identifikátorech URI obousměrné řídicí znaky (Unicode).

#### <a name="details"></a>Podrobnosti

Unicode určuje několik speciálních řídicích znaků, které se používají k určení orientace textu. V předchozích verzích .NET Framework byly tyto znaky nesprávně odstraněny ze všech identifikátorů URI i v případě, že byly přítomny ve formuláři s kódováním v procentech. Aby bylo možné lépe dodržovat [specifikaci RFC 3987](https://tools.ietf.org/html/rfc3987), teď tyto znaky povolujeme v identifikátorech URI. Pokud se v identifikátoru URI najde nekódovaný, jsou v procentech zakódované. V případě, že nalezené procento jsou zakódovány, jsou ponechány, jak jsou.

#### <a name="suggestion"></a>Návrh

Pro aplikace, které cílí na verze .NET Framework počínaje 4.7.2, je ve výchozím nastavení povolená podpora obousměrných znaků Unicode. Pokud je tato změna nežádoucí, můžete ji zakázat přidáním následujícího přepínače [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do `<runtime>` části konfiguračního souboru aplikace:

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=true" />
</runtime>
```

Pro aplikace, které cílí na starší verze .NET Framework, ale běží v rámci verzí počínaje .NET Framework 4.7.2, je ve výchozím nastavení zakázaná podpora obousměrných znaků Unicode. Můžete ji povolit přidáním následujícího přepínače [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do `<runtime>` části konfiguračního souboru aplikace::

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=false" />
</runtime>
```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.7.2       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Uri?displayProperty=nameWithType>
