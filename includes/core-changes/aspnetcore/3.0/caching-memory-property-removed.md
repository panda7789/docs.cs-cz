---
ms.openlocfilehash: 7d40324e6b0bc4afab9dd39b236f0909f360cc9b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394023"
---
### <a name="caching-compactonmemorypressure-property-removed"></a><span data-ttu-id="cdb6f-101">Ukládání do mezipaměti: byla odebrána vlastnost CompactOnMemoryPressure</span><span class="sxs-lookup"><span data-stu-id="cdb6f-101">Caching: CompactOnMemoryPressure property removed</span></span>

<span data-ttu-id="cdb6f-102">Verze ASP.NET Core 3,0 odebrala [zastaralá rozhraní API MemoryCacheOptions](https://github.com/aspnet/Extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).</span><span class="sxs-lookup"><span data-stu-id="cdb6f-102">The ASP.NET Core 3.0 release removed the [obsolete MemoryCacheOptions APIs](https://github.com/aspnet/Extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).</span></span>

#### <a name="change-description"></a><span data-ttu-id="cdb6f-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="cdb6f-103">Change description</span></span>

<span data-ttu-id="cdb6f-104">Tato změna je následná pro [ASPNET/Caching # 221](https://github.com/aspnet/Caching/issues/221).</span><span class="sxs-lookup"><span data-stu-id="cdb6f-104">This change is a follow-up to [aspnet/Caching#221](https://github.com/aspnet/Caching/issues/221).</span></span> <span data-ttu-id="cdb6f-105">Diskuzi najdete v tématu [ASPNET/Extensions # 1062](https://github.com/aspnet/Extensions/issues/1062).</span><span class="sxs-lookup"><span data-stu-id="cdb6f-105">For discussion, see [aspnet/Extensions#1062](https://github.com/aspnet/Extensions/issues/1062).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cdb6f-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="cdb6f-106">Version introduced</span></span>

<span data-ttu-id="cdb6f-107">3.0</span><span class="sxs-lookup"><span data-stu-id="cdb6f-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="cdb6f-108">Staré chování</span><span class="sxs-lookup"><span data-stu-id="cdb6f-108">Old behavior</span></span>

<span data-ttu-id="cdb6f-109">byla k dispozici vlastnost `MemoryCacheOptions.CompactOnMemoryPressure`.</span><span class="sxs-lookup"><span data-stu-id="cdb6f-109">`MemoryCacheOptions.CompactOnMemoryPressure` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="cdb6f-110">Nové chování</span><span class="sxs-lookup"><span data-stu-id="cdb6f-110">New behavior</span></span>

<span data-ttu-id="cdb6f-111">Vlastnost `MemoryCacheOptions.CompactOnMemoryPressure` byla odebrána.</span><span class="sxs-lookup"><span data-stu-id="cdb6f-111">The `MemoryCacheOptions.CompactOnMemoryPressure` property has been removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="cdb6f-112">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="cdb6f-112">Reason for change</span></span>

<span data-ttu-id="cdb6f-113">Automatické komprimace mezipaměti způsobilo problémy.</span><span class="sxs-lookup"><span data-stu-id="cdb6f-113">Automatically compacting the cache caused problems.</span></span> <span data-ttu-id="cdb6f-114">Aby nedocházelo k neočekávanému chování, měla by být mezipaměť komprimována pouze v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="cdb6f-114">To avoid unexpected behavior, the cache should only be compacted when needed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cdb6f-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="cdb6f-115">Recommended action</span></span>

<span data-ttu-id="cdb6f-116">Pro komprimaci mezipaměti, downcast na `MemoryCache` a volání `Compact` v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="cdb6f-116">To compact the cache, downcast to `MemoryCache` and call `Compact` when needed.</span></span>

#### <a name="category"></a><span data-ttu-id="cdb6f-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="cdb6f-117">Category</span></span>

<span data-ttu-id="cdb6f-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cdb6f-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cdb6f-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="cdb6f-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->
