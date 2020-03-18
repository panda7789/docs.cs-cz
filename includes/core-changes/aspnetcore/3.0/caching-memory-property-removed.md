---
ms.openlocfilehash: 2c1362d6982206b14475f77700add0bae61da173
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901756"
---
### <a name="caching-compactonmemorypressure-property-removed"></a>Ukládání do mezipaměti: CompactOnMemoryPressure vlastnost odstraněna

Verze ASP.NET Core 3.0 odebrala [zastaralá api MemoryCacheOptions .](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18)

#### <a name="change-description"></a>Popis změny

Tato změna je zpracování [aspnet/ukládání do mezipaměti #221](https://github.com/aspnet/Caching/issues/221). Diskuse naleznete [v tématu dotnet/extensions#1062](https://github.com/dotnet/extensions/issues/1062).

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

`MemoryCacheOptions.CompactOnMemoryPressure`majetek byl k dispozici.

#### <a name="new-behavior"></a>Nové chování

Vlastnost `MemoryCacheOptions.CompactOnMemoryPressure` byla odebrána.

#### <a name="reason-for-change"></a>Důvod změny

Automatické komprimace mezipaměti způsobila problémy. Chcete-li se vyhnout neočekávanému chování, mezipaměť by měla být zkomprimována pouze v případě potřeby.

#### <a name="recommended-action"></a>Doporučená akce

Chcete-li komprimovat `MemoryCache` mezipaměť, v případě potřeby svrhnout a volat. `Compact`

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->
