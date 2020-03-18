---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901908"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a><span data-ttu-id="1e3ee-101">HTTP: Konstanty HeaderNames se změnily na statické jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="1e3ee-101">HTTP: HeaderNames constants changed to static readonly</span></span>

<span data-ttu-id="1e3ee-102">Počínaje ASP.NET jádrem 3.0 Náhled <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> 5 `const` se `static readonly`pole v polích změnila z na .</span><span class="sxs-lookup"><span data-stu-id="1e3ee-102">Starting in ASP.NET Core 3.0 Preview 5, the fields in <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> changed from `const` to `static readonly`.</span></span>

<span data-ttu-id="1e3ee-103">Diskuse naleznete [v tématu dotnet/aspnetcore#9514](https://github.com/dotnet/aspnetcore/issues/9514).</span><span class="sxs-lookup"><span data-stu-id="1e3ee-103">For discussion, see [dotnet/aspnetcore#9514](https://github.com/dotnet/aspnetcore/issues/9514).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1e3ee-104">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="1e3ee-104">Version introduced</span></span>

<span data-ttu-id="1e3ee-105">3.0</span><span class="sxs-lookup"><span data-stu-id="1e3ee-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1e3ee-106">Staré chování</span><span class="sxs-lookup"><span data-stu-id="1e3ee-106">Old behavior</span></span>

<span data-ttu-id="1e3ee-107">Tato pole bývala `const`.</span><span class="sxs-lookup"><span data-stu-id="1e3ee-107">These fields used to be `const`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="1e3ee-108">Nové chování</span><span class="sxs-lookup"><span data-stu-id="1e3ee-108">New behavior</span></span>

<span data-ttu-id="1e3ee-109">Tato pole `static readonly`jsou nyní .</span><span class="sxs-lookup"><span data-stu-id="1e3ee-109">These fields are now `static readonly`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1e3ee-110">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="1e3ee-110">Reason for change</span></span>

<span data-ttu-id="1e3ee-111">Změna:</span><span class="sxs-lookup"><span data-stu-id="1e3ee-111">The change:</span></span>

* <span data-ttu-id="1e3ee-112">Zabrání vkládání hodnot přes hranice sestavy, což umožňuje podle potřeby opravy hodnot.</span><span class="sxs-lookup"><span data-stu-id="1e3ee-112">Prevents the values from being embedded across assembly boundaries, allowing for value corrections as needed.</span></span>
* <span data-ttu-id="1e3ee-113">Umožňuje rychlejší kontroly rovnosti odkazů.</span><span class="sxs-lookup"><span data-stu-id="1e3ee-113">Enables faster reference equality checks.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1e3ee-114">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="1e3ee-114">Recommended action</span></span>

<span data-ttu-id="1e3ee-115">Překompilovat proti 3.0.</span><span class="sxs-lookup"><span data-stu-id="1e3ee-115">Recompile against 3.0.</span></span> <span data-ttu-id="1e3ee-116">Zdrojový kód používající tato pole následujícími způsoby již nemůže:</span><span class="sxs-lookup"><span data-stu-id="1e3ee-116">Source code using these fields in the following ways can no longer do so:</span></span>

* <span data-ttu-id="1e3ee-117">Jako atribut ový argument</span><span class="sxs-lookup"><span data-stu-id="1e3ee-117">As an attribute argument</span></span>
* <span data-ttu-id="1e3ee-118">Jako `case` v `switch` prohlášení</span><span class="sxs-lookup"><span data-stu-id="1e3ee-118">As a `case` in a `switch` statement</span></span>
* <span data-ttu-id="1e3ee-119">Při definování jiného`const`</span><span class="sxs-lookup"><span data-stu-id="1e3ee-119">When defining another `const`</span></span>

<span data-ttu-id="1e3ee-120">Chcete-li obejít narušující změnu, přepněte na použití samodefinovaných konstant názvu záhlaví nebo literál řetězce.</span><span class="sxs-lookup"><span data-stu-id="1e3ee-120">To work around the breaking change, switch to using self-defined header name constants or string literals.</span></span>

#### <a name="category"></a><span data-ttu-id="1e3ee-121">Kategorie</span><span class="sxs-lookup"><span data-stu-id="1e3ee-121">Category</span></span>

<span data-ttu-id="1e3ee-122">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="1e3ee-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1e3ee-123">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="1e3ee-123">Affected APIs</span></span>

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
