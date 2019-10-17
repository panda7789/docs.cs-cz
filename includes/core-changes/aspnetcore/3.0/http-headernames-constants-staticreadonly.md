---
ms.openlocfilehash: e0d0a680915f14c2d33f1864ad5ad05aff3dde5f
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394130"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a><span data-ttu-id="176f9-101">HTTP: HeaderNames konstanty se změnily na static jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="176f9-101">HTTP: HeaderNames constants changed to static readonly</span></span>

<span data-ttu-id="176f9-102">Počínaje verzí ASP.NET Core 3,0 Preview 5 se pole v <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> změnila z `const` na `static readonly`.</span><span class="sxs-lookup"><span data-stu-id="176f9-102">Starting in ASP.NET Core 3.0 Preview 5, the fields in <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> changed from `const` to `static readonly`.</span></span>

<span data-ttu-id="176f9-103">Diskuzi najdete v tématu [ASPNET/AspNetCore # 9514](https://github.com/aspnet/AspNetCore/issues/9514).</span><span class="sxs-lookup"><span data-stu-id="176f9-103">For discussion, see [aspnet/AspNetCore#9514](https://github.com/aspnet/AspNetCore/issues/9514).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="176f9-104">Představená verze</span><span class="sxs-lookup"><span data-stu-id="176f9-104">Version introduced</span></span>

<span data-ttu-id="176f9-105">3.0</span><span class="sxs-lookup"><span data-stu-id="176f9-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="176f9-106">Staré chování</span><span class="sxs-lookup"><span data-stu-id="176f9-106">Old behavior</span></span>

<span data-ttu-id="176f9-107">Tato pole se používají `const`.</span><span class="sxs-lookup"><span data-stu-id="176f9-107">These fields used to be `const`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="176f9-108">Nové chování</span><span class="sxs-lookup"><span data-stu-id="176f9-108">New behavior</span></span>

<span data-ttu-id="176f9-109">Tato pole jsou nyní `static readonly`.</span><span class="sxs-lookup"><span data-stu-id="176f9-109">These fields are now `static readonly`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="176f9-110">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="176f9-110">Reason for change</span></span>

<span data-ttu-id="176f9-111">Změna:</span><span class="sxs-lookup"><span data-stu-id="176f9-111">The change:</span></span>

* <span data-ttu-id="176f9-112">Zabraňuje vložení hodnoty přes hranice sestavení, což umožňuje opravy hodnot podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="176f9-112">Prevents the values from being embedded across assembly boundaries, allowing for value corrections as needed.</span></span>
* <span data-ttu-id="176f9-113">Umožňuje rychlejší kontroly rovnosti odkazů.</span><span class="sxs-lookup"><span data-stu-id="176f9-113">Enables faster reference equality checks.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="176f9-114">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="176f9-114">Recommended action</span></span>

<span data-ttu-id="176f9-115">Znovu kompilovat proti 3,0.</span><span class="sxs-lookup"><span data-stu-id="176f9-115">Recompile against 3.0.</span></span> <span data-ttu-id="176f9-116">Zdrojový kód pomocí těchto polí již neumožňuje následující akce:</span><span class="sxs-lookup"><span data-stu-id="176f9-116">Source code using these fields in the following ways can no longer do so:</span></span>

* <span data-ttu-id="176f9-117">Jako argument atributu</span><span class="sxs-lookup"><span data-stu-id="176f9-117">As an attribute argument</span></span>
* <span data-ttu-id="176f9-118">Jako `case` v příkazu `switch`</span><span class="sxs-lookup"><span data-stu-id="176f9-118">As a `case` in a `switch` statement</span></span>
* <span data-ttu-id="176f9-119">Při definování jiného `const`</span><span class="sxs-lookup"><span data-stu-id="176f9-119">When defining another `const`</span></span>

<span data-ttu-id="176f9-120">Chcete-li obejít zásadní změnu, přepněte na použití vlastní konstanty názvů hlaviček nebo řetězcových literálů.</span><span class="sxs-lookup"><span data-stu-id="176f9-120">To work around the breaking change, switch to using self-defined header name constants or string literals.</span></span>

#### <a name="category"></a><span data-ttu-id="176f9-121">Kategorie</span><span class="sxs-lookup"><span data-stu-id="176f9-121">Category</span></span>

<span data-ttu-id="176f9-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="176f9-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="176f9-123">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="176f9-123">Affected APIs</span></span>

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
