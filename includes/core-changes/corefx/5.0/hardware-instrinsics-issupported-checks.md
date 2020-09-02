---
ms.openlocfilehash: bba9659b92e5aabc276c585929c99898316036c5
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89359129"
---
### <a name="hardware-intrinsic-issupported-checks-may-differ-for-nested-types"></a><span data-ttu-id="ea45f-101">U vnořených typů se můžou u vnitřních typů lišit.</span><span class="sxs-lookup"><span data-stu-id="ea45f-101">Hardware intrinsic IsSupported checks may differ for nested types</span></span>

<span data-ttu-id="ea45f-102">Kontrola `<Isa>.X64.IsSupported` , kde `<Isa>` odkazuje na třídy v <xref:System.Runtime.Intrinsics.X86?displayProperty=nameWithType> oboru názvů, teď může vytvořit jiný výsledek pro předchozí verze rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="ea45f-102">Checking `<Isa>.X64.IsSupported`, where `<Isa>` refers to the classes in the <xref:System.Runtime.Intrinsics.X86?displayProperty=nameWithType> namespace, may now produce a different result to previous versions of .NET.</span></span>

> [!TIP]
> <span data-ttu-id="ea45f-103">*ISA* představuje oborovou standardní architekturu.</span><span class="sxs-lookup"><span data-stu-id="ea45f-103">*ISA* stands for industry standard architecture.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ea45f-104">Představená verze</span><span class="sxs-lookup"><span data-stu-id="ea45f-104">Version introduced</span></span>

<span data-ttu-id="ea45f-105">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="ea45f-105">5.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="ea45f-106">Popis změny</span><span class="sxs-lookup"><span data-stu-id="ea45f-106">Change description</span></span>

<span data-ttu-id="ea45f-107">V předchozích verzích rozhraní .NET některé <xref:System.Runtime.Intrinsics.X86> typy vnitřního hardwaru, například <xref:System.Runtime.Intrinsics.X86.Aes?displayProperty=nameWithType> , nezveřejnila vnořenou `X64` třídu.</span><span class="sxs-lookup"><span data-stu-id="ea45f-107">In previous versions of .NET, some of the <xref:System.Runtime.Intrinsics.X86> hardware-intrinsic types, for example, <xref:System.Runtime.Intrinsics.X86.Aes?displayProperty=nameWithType>, didn't expose a nested `X64` class.</span></span> <span data-ttu-id="ea45f-108">Pro tyto typy volání se `<Isa>.X64.IsSupported` přeloží na `IsSupported` Vlastnost vnořené `X64` třídy nadřazené třídy `<Isa>` .</span><span class="sxs-lookup"><span data-stu-id="ea45f-108">For these types, calling `<Isa>.X64.IsSupported` resolved to an `IsSupported` property on a nested `X64` class of a parent class of `<Isa>`.</span></span> <span data-ttu-id="ea45f-109">To znamenalo, že vlastnost může vracet `true` i při `<Isa>.IsSupported` návratu `false` .</span><span class="sxs-lookup"><span data-stu-id="ea45f-109">This meant that the property could return `true` even when `<Isa>.IsSupported` returns `false`.</span></span>

<span data-ttu-id="ea45f-110">V rozhraní .NET 5,0 a novějších verzích všechny <xref:System.Runtime.Intrinsics.X86> typy zpřístupňují vnořenou `X64` třídu, která vhodně oznamuje podporu.</span><span class="sxs-lookup"><span data-stu-id="ea45f-110">In .NET 5.0 and later versions, all of the <xref:System.Runtime.Intrinsics.X86> types expose a nested `X64` class that appropriately reports support.</span></span> <span data-ttu-id="ea45f-111">Tím se zajistí, že obecná hierarchie zůstane správná a pokud `<Isa>.X64.IsSupported` je `true` , pak je `<Isa>.IsSupported` možné ji také předpokládat `true` .</span><span class="sxs-lookup"><span data-stu-id="ea45f-111">This ensures that the general hierarchy remains correct, and that if `<Isa>.X64.IsSupported` is `true`, then `<Isa>.IsSupported` can also be assumed to be `true`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ea45f-112">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="ea45f-112">Reason for change</span></span>

<span data-ttu-id="ea45f-113">Bylo zamýšleno, že pokud `<Isa>.X64.IsSupported` je `true` , `<Isa>.IsSupported` je také implicitní `true` .</span><span class="sxs-lookup"><span data-stu-id="ea45f-113">It was intended that if `<Isa>.X64.IsSupported` is `true`, `<Isa>.IsSupported` is also implied to be `true`.</span></span> <span data-ttu-id="ea45f-114">Nicméně vzhledem k tomu, že řešení členů funguje v jazyce C#, třídy, které nemají vnořenou `X64` třídu, vystaví situaci, kdy to nebylo vždy v případě případu a vedlo k chybám v uživatelském kódu.</span><span class="sxs-lookup"><span data-stu-id="ea45f-114">However, due to how member resolution works in C#, classes that didn't have a nested `X64` class exposed a situation where this wasn't always the case and led to bugs in user code.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ea45f-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="ea45f-115">Recommended action</span></span>

<span data-ttu-id="ea45f-116">V případě potřeby upravte kód, který kontroluje kontrolu `IsSupported` příslušného serveru ISA.</span><span class="sxs-lookup"><span data-stu-id="ea45f-116">If necessary, adjust code that checks `IsSupported` to check for the appropriate ISA.</span></span>

#### <a name="category"></a><span data-ttu-id="ea45f-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="ea45f-117">Category</span></span>

<span data-ttu-id="ea45f-118">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="ea45f-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ea45f-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="ea45f-119">Affected APIs</span></span>

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
