---
ms.openlocfilehash: 3300a74b81fc9eeba670ee0ceb2c2615fd3925bd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617222"
---
### <a name="listlttgtforeach-can-throw-exception-when-modifying-list-item"></a>Seznam &lt; T &gt; . ForEach může vyvolat výjimku při změně položky seznamu.

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4,5, <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> enumerátor vyvolá <xref:System.InvalidOperationException?displayProperty=fullName> výjimku, pokud je změněn element v kolekci volání. Dřív to nevyvolalo výjimku, ale může vést ke konfliktům časování.

#### <a name="suggestion"></a>Návrh

V ideálním případě by měl být kód při vytváření výčtu svých prvků vyřešen, aby se seznamy nezměnily, protože to není nikdy bezpečná operace. Pokud se chcete vrátit k předchozímu chování, může se stát, že se aplikace bude cílit .NET Framework 4,0.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.5         |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType>
