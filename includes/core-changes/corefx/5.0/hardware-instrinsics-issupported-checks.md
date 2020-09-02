---
ms.openlocfilehash: bba9659b92e5aabc276c585929c99898316036c5
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89359129"
---
### <a name="hardware-intrinsic-issupported-checks-may-differ-for-nested-types"></a>U vnořených typů se můžou u vnitřních typů lišit.

Kontrola `<Isa>.X64.IsSupported` , kde `<Isa>` odkazuje na třídy v <xref:System.Runtime.Intrinsics.X86?displayProperty=nameWithType> oboru názvů, teď může vytvořit jiný výsledek pro předchozí verze rozhraní .NET.

> [!TIP]
> *ISA* představuje oborovou standardní architekturu.

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 8

#### <a name="change-description"></a>Popis změny

V předchozích verzích rozhraní .NET některé <xref:System.Runtime.Intrinsics.X86> typy vnitřního hardwaru, například <xref:System.Runtime.Intrinsics.X86.Aes?displayProperty=nameWithType> , nezveřejnila vnořenou `X64` třídu. Pro tyto typy volání se `<Isa>.X64.IsSupported` přeloží na `IsSupported` Vlastnost vnořené `X64` třídy nadřazené třídy `<Isa>` . To znamenalo, že vlastnost může vracet `true` i při `<Isa>.IsSupported` návratu `false` .

V rozhraní .NET 5,0 a novějších verzích všechny <xref:System.Runtime.Intrinsics.X86> typy zpřístupňují vnořenou `X64` třídu, která vhodně oznamuje podporu. Tím se zajistí, že obecná hierarchie zůstane správná a pokud `<Isa>.X64.IsSupported` je `true` , pak je `<Isa>.IsSupported` možné ji také předpokládat `true` .

#### <a name="reason-for-change"></a>Důvod změny

Bylo zamýšleno, že pokud `<Isa>.X64.IsSupported` je `true` , `<Isa>.IsSupported` je také implicitní `true` . Nicméně vzhledem k tomu, že řešení členů funguje v jazyce C#, třídy, které nemají vnořenou `X64` třídu, vystaví situaci, kdy to nebylo vždy v případě případu a vedlo k chybám v uživatelském kódu.

#### <a name="recommended-action"></a>Doporučená akce

V případě potřeby upravte kód, který kontroluje kontrolu `IsSupported` příslušného serveru ISA.

#### <a name="category"></a>Kategorie

Knihovny Core .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Runtime.Intrinsics.X86.Aes.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Avx.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Avx2.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Fma.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Pclmulqdq.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse3.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Ssse3.X64.IsSupported?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Runtime.Intrinsics.X86.Aes.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Avx.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Avx2.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Fma.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Pclmulqdq.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Sse3.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Ssse3.X64.IsSupported`

-->
