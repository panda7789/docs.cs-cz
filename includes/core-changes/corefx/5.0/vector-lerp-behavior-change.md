---
ms.openlocfilehash: 4bc060f991501b81db0cb7c521e55996a2b5e91e
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281294"
---
### <a name="behavior-change-for-vector2lerp-and-vector4lerp"></a>Změna chování pro Vector2. lerp a Vector4. lerp

Implementace <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> a <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> Změna správného účtu pro chybu zaokrouhlení s plovoucí desetinnou čárkou.

#### <a name="change-description"></a>Popis změny

Dříve <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> a <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> byly implementovány jako `value1 + (value2 - value1) * amount` . Z důvodu chyby zaokrouhlení plovoucí desetinné čárky však tento algoritmus vždy nevrátí, `value2` Pokud `amount` je `1.0f` .

V rozhraní .NET 5,0 a novější implementace používá stejný algoritmus jako <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType> , což je `(value1 * (1.0f - amount)) + (value2 * amount)` . Tento algoritmus správně účty pro chybu zaokrouhlování. Teď, když `amount` je `1.0f` , výsledek je přesně `value2` . Aktualizovaný algoritmus také umožňuje, aby byl algoritmus volně optimalizovaný pomocí, <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> když je dostupný.

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 7

#### <a name="recommended-action"></a>Doporučená akce

Není nutná žádná akce. Pokud však chcete zachovat staré chování, můžete implementovat vlastní `Lerp` funkci, která používá předchozí algoritmus `value1 + (value2 - value1) * amount` .

#### <a name="category"></a>Kategorie

Knihovny Core .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=fullName>
- <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)`
- `M:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)`

-->
