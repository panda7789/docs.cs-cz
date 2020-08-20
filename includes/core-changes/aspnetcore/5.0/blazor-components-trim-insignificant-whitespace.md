---
ms.openlocfilehash: ca369c4e3f78648c6e8e0bcb5d54711d3009a769
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174257"
---
### <a name="blazor-insignificant-whitespace-trimmed-from-components-at-compile-time"></a><span data-ttu-id="9244e-101">Blazor: nevýznamné prázdné znaky oříznuté z komponent v době kompilace</span><span class="sxs-lookup"><span data-stu-id="9244e-101">Blazor: Insignificant whitespace trimmed from components at compile time</span></span>

<span data-ttu-id="9244e-102">Počínaje verzí ASP.NET Core 5,0 Preview 7 kompilátor Razor vynechává v době kompilace nevýznamné prázdné znaky v komponentách Blazor (soubory *. Razor* ).</span><span class="sxs-lookup"><span data-stu-id="9244e-102">Starting with ASP.NET Core 5.0 Preview 7, the Razor compiler omits insignificant whitespace in Blazor components (*.razor* files) at compile time.</span></span> <span data-ttu-id="9244e-103">Diskuzi najdete v tématu problém [dotnet/aspnetcore # 23568](https://github.com/dotnet/aspnetcore/issues/23568).</span><span class="sxs-lookup"><span data-stu-id="9244e-103">For discussion, see issue [dotnet/aspnetcore#23568](https://github.com/dotnet/aspnetcore/issues/23568).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9244e-104">Představená verze</span><span class="sxs-lookup"><span data-stu-id="9244e-104">Version introduced</span></span>

<span data-ttu-id="9244e-105">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="9244e-105">5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9244e-106">Staré chování</span><span class="sxs-lookup"><span data-stu-id="9244e-106">Old behavior</span></span>

<span data-ttu-id="9244e-107">Ve 3. x verzích serveru Blazor a v Blazor WebAssembly se ve zdrojovém kódu komponenty nepoužívá prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="9244e-107">In 3.x versions of Blazor Server and Blazor WebAssembly, whitespace is honored in a component's source code.</span></span> <span data-ttu-id="9244e-108">Jenom prázdné textové uzly se vykreslují v model DOM (Document Object Model) v prohlížeči (DOM), a to i v případě, že není k dispozici žádný vizuální efekt.</span><span class="sxs-lookup"><span data-stu-id="9244e-108">Whitespace-only text nodes render in the browser's Document Object Model (DOM) even when there's no visual effect.</span></span>

<span data-ttu-id="9244e-109">Vezměte v úvahu následující kód komponenty Blazor:</span><span class="sxs-lookup"><span data-stu-id="9244e-109">Consider the following Blazor component code:</span></span>

```razor
<ul>
    @foreach (var item in Items)
    {
        <li>
            @item.Text
        </li>
    }
</ul>
```

<span data-ttu-id="9244e-110">Předchozí příklad vykreslí dva prázdné uzly:</span><span class="sxs-lookup"><span data-stu-id="9244e-110">The preceding example renders two whitespace nodes:</span></span>

* <span data-ttu-id="9244e-111">Mimo `@foreach` blok kódu.</span><span class="sxs-lookup"><span data-stu-id="9244e-111">Outside of the `@foreach` code block.</span></span>
* <span data-ttu-id="9244e-112">Kolem `<li>` prvku.</span><span class="sxs-lookup"><span data-stu-id="9244e-112">Around the `<li>` element.</span></span>
* <span data-ttu-id="9244e-113">Kolem `@item.Text` výstupu.</span><span class="sxs-lookup"><span data-stu-id="9244e-113">Around the `@item.Text` output.</span></span>

<span data-ttu-id="9244e-114">Seznam obsahující 100 položek má za následek 402 prázdných uzlů.</span><span class="sxs-lookup"><span data-stu-id="9244e-114">A list containing 100 items results in 402 whitespace nodes.</span></span> <span data-ttu-id="9244e-115">To je více než polovina všech vykreslených uzlů, i když žádný z uzlů prázdných znaků nemá vizuálně vliv na Vykreslený výstup.</span><span class="sxs-lookup"><span data-stu-id="9244e-115">That's over half of all nodes rendered, even though none of the whitespace nodes visually affect the rendered output.</span></span>

<span data-ttu-id="9244e-116">Při vykreslování statického HTML pro součásti se nezachovají prázdné znaky uvnitř značky.</span><span class="sxs-lookup"><span data-stu-id="9244e-116">When rendering static HTML for components, whitespace inside a tag wasn't preserved.</span></span> <span data-ttu-id="9244e-117">Můžete například zobrazit zdroj následující součásti:</span><span class="sxs-lookup"><span data-stu-id="9244e-117">For example, view the source of the following component:</span></span>

```razor
<foo        bar="baz"     />
```

<span data-ttu-id="9244e-118">Prázdný znak se nezachová.</span><span class="sxs-lookup"><span data-stu-id="9244e-118">Whitespace isn't preserved.</span></span> <span data-ttu-id="9244e-119">Předem Vykreslený výstup je:</span><span class="sxs-lookup"><span data-stu-id="9244e-119">The pre-rendered output is:</span></span>

```razor
<foo bar="baz" />
```

#### <a name="new-behavior"></a><span data-ttu-id="9244e-120">Nové chování</span><span class="sxs-lookup"><span data-stu-id="9244e-120">New behavior</span></span>

<span data-ttu-id="9244e-121">Pokud se `@preservewhitespace` direktiva nepoužívá s hodnotou `true` , prázdné uzly se odeberou, pokud jsou:</span><span class="sxs-lookup"><span data-stu-id="9244e-121">Unless the `@preservewhitespace` directive is used with value `true`, whitespace nodes are removed if they:</span></span>

* <span data-ttu-id="9244e-122">Jsou na začátku nebo na konci elementu.</span><span class="sxs-lookup"><span data-stu-id="9244e-122">Are leading or trailing within an element.</span></span>
* <span data-ttu-id="9244e-123">Jsou na začátku nebo na konci v rámci `RenderFragment` parametru.</span><span class="sxs-lookup"><span data-stu-id="9244e-123">Are leading or trailing within a `RenderFragment` parameter.</span></span> <span data-ttu-id="9244e-124">Například podřízený obsah předávaný do jiné součásti.</span><span class="sxs-lookup"><span data-stu-id="9244e-124">For example, child content being passed to another component.</span></span>
* <span data-ttu-id="9244e-125">Předchází nebo dodržujte blok kódu jazyka C#, jako je `@if` a `@foreach` .</span><span class="sxs-lookup"><span data-stu-id="9244e-125">Precede or follow a C# code block such as `@if` and `@foreach`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9244e-126">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="9244e-126">Reason for change</span></span>

<span data-ttu-id="9244e-127">Cílem pro Blazor v ASP.NET Core 5,0 je vylepšit výkon vykreslování a rozdílů.</span><span class="sxs-lookup"><span data-stu-id="9244e-127">A goal for Blazor in ASP.NET Core 5.0 is to improve the performance of rendering and diffing.</span></span> <span data-ttu-id="9244e-128">Nevýznamné uzly stromu prázdných znaků využily až 40 procent času vykreslování v srovnávacích testech.</span><span class="sxs-lookup"><span data-stu-id="9244e-128">Insignificant whitespace tree nodes consumed up to 40 percent of the rendering time in benchmarks.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9244e-129">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="9244e-129">Recommended action</span></span>

<span data-ttu-id="9244e-130">Ve většině případů je vizuální rozložení vykreslené komponenty neovlivněno.</span><span class="sxs-lookup"><span data-stu-id="9244e-130">In most cases, the visual layout of the rendered component is unaffected.</span></span> <span data-ttu-id="9244e-131">Odebrání prázdných znaků však může ovlivnit Vykreslený výstup při použití pravidla šablony stylů CSS `white-space: pre` , jako je.</span><span class="sxs-lookup"><span data-stu-id="9244e-131">However, the whitespace removal might affect the rendered output when using a CSS rule like `white-space: pre`.</span></span> <span data-ttu-id="9244e-132">Chcete-li zakázat tuto optimalizaci výkonu a zachovat prázdné znaky, proveďte jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="9244e-132">To disable this performance optimization and preserve the whitespace, take one of the following actions:</span></span>

* <span data-ttu-id="9244e-133">Přidejte `@preservewhitespace true` direktivu v horní části souboru *. Razor* , abyste použili předvolby pro konkrétní komponentu.</span><span class="sxs-lookup"><span data-stu-id="9244e-133">Add the `@preservewhitespace true` directive at the top of the *.razor* file to apply the preference to a specific component.</span></span>
* <span data-ttu-id="9244e-134">Přidejte `@preservewhitespace true` direktivu do souboru *_Imports. Razor* pro použití předvolby pro celý podadresář nebo celý projekt.</span><span class="sxs-lookup"><span data-stu-id="9244e-134">Add the `@preservewhitespace true` directive inside an *_Imports.razor* file to apply the preference to an entire subdirectory or the entire project.</span></span>

<span data-ttu-id="9244e-135">Ve většině případů není nutná žádná akce, protože aplikace se obvykle budou často chovat normálně (ale rychleji).</span><span class="sxs-lookup"><span data-stu-id="9244e-135">In most cases, no action is required, as applications will typically continue to behave normally (but faster).</span></span> <span data-ttu-id="9244e-136">Pokud odstranění prázdných znaků způsobí jakékoli problémy určité součásti, použijte `@preservewhitespace true` v této součásti tuto optimalizaci.</span><span class="sxs-lookup"><span data-stu-id="9244e-136">If the whitespace stripping causes any problems for a particular component, use `@preservewhitespace true` in that component to disable this optimization.</span></span>

#### <a name="category"></a><span data-ttu-id="9244e-137">Kategorie</span><span class="sxs-lookup"><span data-stu-id="9244e-137">Category</span></span>

<span data-ttu-id="9244e-138">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9244e-138">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9244e-139">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="9244e-139">Affected APIs</span></span>

<span data-ttu-id="9244e-140">Žádné</span><span class="sxs-lookup"><span data-stu-id="9244e-140">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
