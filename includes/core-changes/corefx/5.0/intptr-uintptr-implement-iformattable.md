---
ms.openlocfilehash: 3d29848e12d496d2d53c204e00ef8604831495e1
ms.sourcegitcommit: 1e6439ec4d5889fc08cf3bfb4dac2b91931eb827
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2020
ms.locfileid: "88024693"
---
### <a name="intptr-and-uintptr-implement-iformattable"></a>IntPtr a UIntPtr implementují IFormattable

<xref:System.IntPtr>a <xref:System.UIntPtr> teď je implementovaná <xref:System.IFormattable> . Funkce, které kontrolují <xref:System.IFormattable> podporu, mohou nyní vracet různé výsledky pro tyto typy, protože mohou předat specifikátor formátu a jazykovou verzi.

#### <a name="change-description"></a>Popis změny

V předchozích verzích rozhraní .NET <xref:System.IntPtr> a <xref:System.UIntPtr> neimplementují <xref:System.IFormattable> . Funkce, které kontrolují, <xref:System.IFormattable> mohou vracet pouze volání <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> nebo <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType> , což znamená, že specifikátory formátu a jazykové verze nejsou dodržovány.

V rozhraní .NET 5,0 a novějších verzích <xref:System.IntPtr> a <xref:System.UIntPtr> implementujte <xref:System.IFormattable> . Funkce, které kontrolují <xref:System.IFormattable> podporu, mohou nyní vracet různé výsledky pro tyto typy, protože mohou předat specifikátor formátu a jazykovou verzi.

Tato změna má vliv na scénáře jako interpolované řetězce a <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> mimo jiné.

#### <a name="reason-for-change"></a>Důvod změny

<xref:System.IntPtr>a <xref:System.UIntPtr> teď mají jazykovou podporu v jazyce C# `nint` prostřednictvím `nuint` klíčových slov a. Typy zálohování byly aktualizovány tak, aby poskytovaly téměř paritu (Pokud je to možné) s funkcemi, které jsou vystaveny jinými primitivními typy, jako například <xref:System.Int32?displayProperty=nameWithType> .

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 4

#### <a name="recommended-action"></a>Doporučená akce

Pokud nechcete, aby se specifikátor formátu nebo vlastní jazyková verze používaly při zobrazení hodnot těchto typů, můžete zavolat <xref:System.IntPtr.ToString?displayProperty=nameWithType> a <xref:System.UIntPtr.ToString?displayProperty=nameWithType> přetížení `ToString()` .

#### <a name="category"></a>Kategorie

Knihovny Core .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Nedá se detekovat přes analýzu rozhraní API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
