---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901908"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a><span data-ttu-id="12c50-101">HTTP: HeaderNames konstanty se změnily na static jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="12c50-101">HTTP: HeaderNames constants changed to static readonly</span></span>

<span data-ttu-id="12c50-102">Počínaje verzí ASP.NET Core 3,0 Preview 5 se pole v <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> změnila z `const` na `static readonly`.</span><span class="sxs-lookup"><span data-stu-id="12c50-102">Starting in ASP.NET Core 3.0 Preview 5, the fields in <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> changed from `const` to `static readonly`.</span></span>

<span data-ttu-id="12c50-103">Diskuzi najdete v tématu [dotnet/aspnetcore # 9514](https://github.com/dotnet/aspnetcore/issues/9514).</span><span class="sxs-lookup"><span data-stu-id="12c50-103">For discussion, see [dotnet/aspnetcore#9514](https://github.com/dotnet/aspnetcore/issues/9514).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="12c50-104">Představená verze</span><span class="sxs-lookup"><span data-stu-id="12c50-104">Version introduced</span></span>

<span data-ttu-id="12c50-105">3,0</span><span class="sxs-lookup"><span data-stu-id="12c50-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="12c50-106">Staré chování</span><span class="sxs-lookup"><span data-stu-id="12c50-106">Old behavior</span></span>

<span data-ttu-id="12c50-107">Tato pole se používají k `const`.</span><span class="sxs-lookup"><span data-stu-id="12c50-107">These fields used to be `const`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="12c50-108">Nové chování</span><span class="sxs-lookup"><span data-stu-id="12c50-108">New behavior</span></span>

<span data-ttu-id="12c50-109">Tato pole jsou nyní `static readonly`.</span><span class="sxs-lookup"><span data-stu-id="12c50-109">These fields are now `static readonly`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="12c50-110">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="12c50-110">Reason for change</span></span>

<span data-ttu-id="12c50-111">Změna:</span><span class="sxs-lookup"><span data-stu-id="12c50-111">The change:</span></span>

* <span data-ttu-id="12c50-112">Zabraňuje vložení hodnoty přes hranice sestavení, což umožňuje opravy hodnot podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="12c50-112">Prevents the values from being embedded across assembly boundaries, allowing for value corrections as needed.</span></span>
* <span data-ttu-id="12c50-113">Umožňuje rychlejší kontroly rovnosti odkazů.</span><span class="sxs-lookup"><span data-stu-id="12c50-113">Enables faster reference equality checks.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="12c50-114">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="12c50-114">Recommended action</span></span>

<span data-ttu-id="12c50-115">Znovu kompilovat proti 3,0.</span><span class="sxs-lookup"><span data-stu-id="12c50-115">Recompile against 3.0.</span></span> <span data-ttu-id="12c50-116">Zdrojový kód pomocí těchto polí již neumožňuje následující akce:</span><span class="sxs-lookup"><span data-stu-id="12c50-116">Source code using these fields in the following ways can no longer do so:</span></span>

* <span data-ttu-id="12c50-117">Jako argument atributu</span><span class="sxs-lookup"><span data-stu-id="12c50-117">As an attribute argument</span></span>
* <span data-ttu-id="12c50-118">Jako `case` v příkazu `switch`</span><span class="sxs-lookup"><span data-stu-id="12c50-118">As a `case` in a `switch` statement</span></span>
* <span data-ttu-id="12c50-119">Při definování jiného `const`</span><span class="sxs-lookup"><span data-stu-id="12c50-119">When defining another `const`</span></span>

<span data-ttu-id="12c50-120">Chcete-li obejít zásadní změnu, přepněte na použití vlastní konstanty názvů hlaviček nebo řetězcových literálů.</span><span class="sxs-lookup"><span data-stu-id="12c50-120">To work around the breaking change, switch to using self-defined header name constants or string literals.</span></span>

#### <a name="category"></a><span data-ttu-id="12c50-121">Kategorie</span><span class="sxs-lookup"><span data-stu-id="12c50-121">Category</span></span>

<span data-ttu-id="12c50-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="12c50-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="12c50-123">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="12c50-123">Affected APIs</span></span>

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
