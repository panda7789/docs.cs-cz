---
ms.openlocfilehash: 43ebb37124b8efe077b9f81fe5351bd7db2c72f7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302703"
---
### <a name="vectort-always-throws-notsupportedexception-for-unsupported-types"></a><span data-ttu-id="8440f-101">Vector \<T> vždy vyvolá NotSupportedException pro nepodporované typy</span><span class="sxs-lookup"><span data-stu-id="8440f-101">Vector\<T> always throws NotSupportedException for unsupported types</span></span>

<span data-ttu-id="8440f-102"><xref:System.Numerics.Vector%601?displayProperty=nameWithType>nyní vždy vyvolá výjimku <xref:System.NotSupportedException> pro nepodporované parametry typu.</span><span class="sxs-lookup"><span data-stu-id="8440f-102"><xref:System.Numerics.Vector%601?displayProperty=nameWithType> now always throws a <xref:System.NotSupportedException> for unsupported type parameters.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8440f-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="8440f-103">Change description</span></span>

<span data-ttu-id="8440f-104">Dřív členové by nemuseli <xref:System.Numerics.Vector%601> vždycky vyvolat výjimku, kdy se nejedná o <xref:System.NotSupportedException> `T` [nepodporovaný typ](#unsupported-types).</span><span class="sxs-lookup"><span data-stu-id="8440f-104">Previously, members of <xref:System.Numerics.Vector%601> would not always throw a <xref:System.NotSupportedException> when `T` was an [unsupported type](#unsupported-types).</span></span> <span data-ttu-id="8440f-105">Výjimka se vyvolala vždycky kvůli cestám kódu, které podporují hardwarovou akceleraci.</span><span class="sxs-lookup"><span data-stu-id="8440f-105">The exception wasn't always thrown because of code paths that supported hardware acceleration.</span></span> <span data-ttu-id="8440f-106">Například `Vector<bool> + Vector<bool>` vrátí `default` místo vyvolání výjimky na platformách, které nemají žádnou hardwarovou akceleraci, jako je například ARM32.</span><span class="sxs-lookup"><span data-stu-id="8440f-106">For example, `Vector<bool> + Vector<bool>` returned `default` instead of throwing an exception on platforms that have no hardware acceleration, such as ARM32.</span></span> <span data-ttu-id="8440f-107">Pro nepodporované typy <xref:System.Numerics.Vector%601> Členové nakazují nekonzistentní chování napříč různými platformami a hardwarovými konfiguracemi.</span><span class="sxs-lookup"><span data-stu-id="8440f-107">For unsupported types, <xref:System.Numerics.Vector%601> members exhibited inconsistent behavior across different platforms and hardware configurations.</span></span>

<span data-ttu-id="8440f-108">Počínaje platformou .NET 5,0 <xref:System.Numerics.Vector%601> Členové vždy vyvolají <xref:System.NotSupportedException> u všech konfigurací hardwaru, pokud `T` není podporovaným typem.</span><span class="sxs-lookup"><span data-stu-id="8440f-108">Starting in .NET 5.0, <xref:System.Numerics.Vector%601> members always throw a <xref:System.NotSupportedException> on all hardware configurations when `T` is not a supported type.</span></span>

##### <a name="unsupported-types"></a><span data-ttu-id="8440f-109">Nepodporované typy</span><span class="sxs-lookup"><span data-stu-id="8440f-109">Unsupported types</span></span>

<span data-ttu-id="8440f-110">Podporované typy pro parametr typu <xref:System.Numerics.Vector%601> jsou:</span><span class="sxs-lookup"><span data-stu-id="8440f-110">The supported types for the type parameter of <xref:System.Numerics.Vector%601> are:</span></span>

- `byte`
- `sbyte`
- `short`
- `ushort`
- `int`
- `uint`
- `long`
- `ulong`
- `float`
- `double`

<span data-ttu-id="8440f-111">Podporované typy se nezměnily, ale mohou být v budoucnu změněny.</span><span class="sxs-lookup"><span data-stu-id="8440f-111">The supported types have not changed, however, they may change in the future.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8440f-112">Představená verze</span><span class="sxs-lookup"><span data-stu-id="8440f-112">Version introduced</span></span>

<span data-ttu-id="8440f-113">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="8440f-113">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8440f-114">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="8440f-114">Recommended action</span></span>

<span data-ttu-id="8440f-115">Nepoužívejte nepodporovaný typ pro parametr typu <xref:System.Numerics.Vector%601> .</span><span class="sxs-lookup"><span data-stu-id="8440f-115">Don't use an unsupported type for the type parameter of <xref:System.Numerics.Vector%601>.</span></span>

#### <a name="category"></a><span data-ttu-id="8440f-116">Kategorie</span><span class="sxs-lookup"><span data-stu-id="8440f-116">Category</span></span>

<span data-ttu-id="8440f-117">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="8440f-117">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8440f-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="8440f-118">Affected APIs</span></span>

- <span data-ttu-id="8440f-119"><xref:System.Numerics.Vector%601?displayProperty=fullName>a všechny její členy</span><span class="sxs-lookup"><span data-stu-id="8440f-119"><xref:System.Numerics.Vector%601?displayProperty=fullName> and all its members</span></span>

<!--

#### Affected APIs

- ``T:System.Numerics.Vector`1``

-->
