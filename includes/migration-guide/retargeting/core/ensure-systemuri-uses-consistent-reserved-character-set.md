---
ms.openlocfilehash: 21921156295d89aad04f3197fef9fa322f3c8c87
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614445"
---
### <a name="ensure-systemuri-uses-a-consistent-reserved-character-set"></a>Zajistěte, aby System. URI používal konzistentní vyhrazenou znakovou sadu.

#### <a name="details"></a>Podrobnosti

V <xref:System.Uri?displayProperty=fullName> je teď zakódovaných znaků, které jsou v procentech zakódovaných v procentech, trvale zakódované. K tomu dojde v rámci vlastností a metod, které přistupují k komponentám URI, dotaz, fragment nebo UserInfo. Chování se změní jenom v případě, že jsou splněné obě následující podmínky:

- Identifikátor URI obsahuje kódovaný tvar libovolného z následujících vyhrazených znaků: `:` , `'` , `(` , `)` `!` nebo `*` .
- Identifikátor URI obsahuje znak Unicode nebo kódovaný nevyhrazený znak. Pokud jsou obě výše uvedené pravdivé, zakódované vyhrazené znaky jsou zakódované vlevo. V předchozích verzích .NET Framework jsou Dekódovatelné.

#### <a name="suggestion"></a>Návrh

U aplikací, které cílí na verze .NET Framework počínaje 4.7.2, je ve výchozím nastavení povolené nové chování při dekódování. Pokud je tato změna nežádoucí, můžete ji zakázat přidáním následujícího přepínače [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do `<runtime>` části konfiguračního souboru aplikace:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=true" />
</runtime>
```

U aplikací, které cílí na starší verze .NET Framework, ale běží v rámci verzí počínaje .NET Framework 4.7.2, je ve výchozím nastavení zakázané nové chování při dekódování. Můžete ji povolit přidáním následujícího přepínače [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do `<runtime>` části konfiguračního souboru aplikace:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=false" />
</runtime>
```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.7.2       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Uri?displayProperty=nameWithType>
