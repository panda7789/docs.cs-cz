---
ms.openlocfilehash: 2c1362d6982206b14475f77700add0bae61da173
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901756"
---
### <a name="caching-compactonmemorypressure-property-removed"></a>Ukládání do mezipaměti: byla odebrána vlastnost CompactOnMemoryPressure

Verze ASP.NET Core 3,0 odebrala [zastaralá rozhraní API MemoryCacheOptions](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).

#### <a name="change-description"></a>Popis změny

Tato změna je následná pro [ASPNET/Caching # 221](https://github.com/aspnet/Caching/issues/221). Diskuzi najdete v tématu [dotnet/Extensions # 1062](https://github.com/dotnet/extensions/issues/1062).

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="old-behavior"></a>Staré chování

byla k dispozici vlastnost `MemoryCacheOptions.CompactOnMemoryPressure`.

#### <a name="new-behavior"></a>Nové chování

Vlastnost `MemoryCacheOptions.CompactOnMemoryPressure` byla odebrána.

#### <a name="reason-for-change"></a>Důvod změny

Automatické komprimace mezipaměti způsobilo problémy. Aby nedocházelo k neočekávanému chování, měla by být mezipaměť komprimována pouze v případě potřeby.

#### <a name="recommended-action"></a>Doporučená akce

Pro komprimaci mezipaměti, downcast na `MemoryCache` a volání `Compact` v případě potřeby.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->
