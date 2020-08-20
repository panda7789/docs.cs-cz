---
ms.openlocfilehash: 3d29848e12d496d2d53c204e00ef8604831495e1
ms.sourcegitcommit: 1e6439ec4d5889fc08cf3bfb4dac2b91931eb827
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2020
ms.locfileid: "88024693"
---
### <a name="intptr-and-uintptr-implement-iformattable"></a><span data-ttu-id="55d1c-101">IntPtr a UIntPtr implementují IFormattable</span><span class="sxs-lookup"><span data-stu-id="55d1c-101">IntPtr and UIntPtr implement IFormattable</span></span>

<span data-ttu-id="55d1c-102"><xref:System.IntPtr> a <xref:System.UIntPtr> teď je implementovaná <xref:System.IFormattable> .</span><span class="sxs-lookup"><span data-stu-id="55d1c-102"><xref:System.IntPtr> and <xref:System.UIntPtr> now implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="55d1c-103">Funkce, které kontrolují <xref:System.IFormattable> podporu, mohou nyní vracet různé výsledky pro tyto typy, protože mohou předat specifikátor formátu a jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="55d1c-103">Functions that check for <xref:System.IFormattable> support may now return different results for these types, because they may pass in a format specifier and a culture.</span></span>

#### <a name="change-description"></a><span data-ttu-id="55d1c-104">Popis změny</span><span class="sxs-lookup"><span data-stu-id="55d1c-104">Change description</span></span>

<span data-ttu-id="55d1c-105">V předchozích verzích rozhraní .NET <xref:System.IntPtr> a <xref:System.UIntPtr> neimplementují <xref:System.IFormattable> .</span><span class="sxs-lookup"><span data-stu-id="55d1c-105">In previous versions of .NET, <xref:System.IntPtr> and <xref:System.UIntPtr> do not implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="55d1c-106">Funkce, které kontrolují, <xref:System.IFormattable> mohou vracet pouze volání <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> nebo <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType> , což znamená, že specifikátory formátu a jazykové verze nejsou dodržovány.</span><span class="sxs-lookup"><span data-stu-id="55d1c-106">Functions that check for <xref:System.IFormattable> may fall back to just calling <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> or <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType>, which means that format specifiers and cultures are not respected.</span></span>

<span data-ttu-id="55d1c-107">V rozhraní .NET 5,0 a novějších verzích <xref:System.IntPtr> a <xref:System.UIntPtr> implementujte <xref:System.IFormattable> .</span><span class="sxs-lookup"><span data-stu-id="55d1c-107">In .NET 5.0 and later versions, <xref:System.IntPtr> and <xref:System.UIntPtr> implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="55d1c-108">Funkce, které kontrolují <xref:System.IFormattable> podporu, mohou nyní vracet různé výsledky pro tyto typy, protože mohou předat specifikátor formátu a jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="55d1c-108">Functions that check for <xref:System.IFormattable> support may now return different results for these types, because they may pass in a format specifier and a culture.</span></span>

<span data-ttu-id="55d1c-109">Tato změna má vliv na scénáře jako interpolované řetězce a <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> mimo jiné.</span><span class="sxs-lookup"><span data-stu-id="55d1c-109">This change impacts scenarios like interpolated strings and <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, among others.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="55d1c-110">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="55d1c-110">Reason for change</span></span>

<span data-ttu-id="55d1c-111"><xref:System.IntPtr> a <xref:System.UIntPtr> teď mají jazykovou podporu v jazyce C# `nint` prostřednictvím `nuint` klíčových slov a.</span><span class="sxs-lookup"><span data-stu-id="55d1c-111"><xref:System.IntPtr> and <xref:System.UIntPtr> now have language support in C# through the `nint` and `nuint` keywords.</span></span> <span data-ttu-id="55d1c-112">Typy zálohování byly aktualizovány tak, aby poskytovaly téměř paritu (Pokud je to možné) s funkcemi, které jsou vystaveny jinými primitivními typy, jako například <xref:System.Int32?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="55d1c-112">The backing types were updated to provide near parity (where possible) with functionality exposed by other primitive types, such as <xref:System.Int32?displayProperty=nameWithType>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="55d1c-113">Představená verze</span><span class="sxs-lookup"><span data-stu-id="55d1c-113">Version introduced</span></span>

<span data-ttu-id="55d1c-114">5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="55d1c-114">5.0 Preview 4</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="55d1c-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="55d1c-115">Recommended action</span></span>

<span data-ttu-id="55d1c-116">Pokud nechcete, aby se specifikátor formátu nebo vlastní jazyková verze používaly při zobrazení hodnot těchto typů, můžete zavolat <xref:System.IntPtr.ToString?displayProperty=nameWithType> a <xref:System.UIntPtr.ToString?displayProperty=nameWithType> přetížení `ToString()` .</span><span class="sxs-lookup"><span data-stu-id="55d1c-116">If you don't want a format specifier or custom culture to be used when displaying values of these types, you can call the <xref:System.IntPtr.ToString?displayProperty=nameWithType> and <xref:System.UIntPtr.ToString?displayProperty=nameWithType> overloads of `ToString()`.</span></span>

#### <a name="category"></a><span data-ttu-id="55d1c-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="55d1c-117">Category</span></span>

<span data-ttu-id="55d1c-118">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="55d1c-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="55d1c-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="55d1c-119">Affected APIs</span></span>

<span data-ttu-id="55d1c-120">Nedá se detekovat přes analýzu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="55d1c-120">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
