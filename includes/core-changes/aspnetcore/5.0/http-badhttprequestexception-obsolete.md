---
ms.openlocfilehash: c4e7864262a11aafa4b7f1f4bdf632fbf084c560
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507074"
---
### <a name="http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced"></a><span data-ttu-id="0cfec-101">HTTP: typy Kestrel a IIS BadHttpRequestException označené jako zastaralé a nahrazené</span><span class="sxs-lookup"><span data-stu-id="0cfec-101">HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced</span></span>

<span data-ttu-id="0cfec-102">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` a byly `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` označeny jako zastaralé a změnily se, aby byly odvozeny od `Microsoft.AspNetCore.Http.BadHttpRequestException` .</span><span class="sxs-lookup"><span data-stu-id="0cfec-102">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` have been marked obsolete and changed to derive from `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span></span> <span data-ttu-id="0cfec-103">Servery Kestrel a IIS stále vyvolávají své staré typy výjimek, aby se zajistila zpětná kompatibilita.</span><span class="sxs-lookup"><span data-stu-id="0cfec-103">The Kestrel and IIS servers still throw their old exception types for backwards compatibility.</span></span> <span data-ttu-id="0cfec-104">Zastaralé typy budou v budoucí verzi odebrány.</span><span class="sxs-lookup"><span data-stu-id="0cfec-104">The obsolete types will be removed in a future release.</span></span>

<span data-ttu-id="0cfec-105">Diskuzi najdete v tématu [dotnet/aspnetcore # 20614](https://github.com/dotnet/aspnetcore/issues/20614).</span><span class="sxs-lookup"><span data-stu-id="0cfec-105">For discussion, see [dotnet/aspnetcore#20614](https://github.com/dotnet/aspnetcore/issues/20614).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0cfec-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="0cfec-106">Version introduced</span></span>

<span data-ttu-id="0cfec-107">5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="0cfec-107">5.0 Preview 4</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0cfec-108">Staré chování</span><span class="sxs-lookup"><span data-stu-id="0cfec-108">Old behavior</span></span>

<span data-ttu-id="0cfec-109">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` a jsou `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` odvozeny z <xref:System.IO.IOException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0cfec-109">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` derived from <xref:System.IO.IOException?displayProperty=nameWithType>.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0cfec-110">Nové chování</span><span class="sxs-lookup"><span data-stu-id="0cfec-110">New behavior</span></span>

<span data-ttu-id="0cfec-111">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` a `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` jsou zastaralé.</span><span class="sxs-lookup"><span data-stu-id="0cfec-111">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` are obsolete.</span></span> <span data-ttu-id="0cfec-112">Typy také jsou odvozeny z `Microsoft.AspNetCore.Http.BadHttpRequestException` , který je odvozen z `System.IO.IOException` .</span><span class="sxs-lookup"><span data-stu-id="0cfec-112">The types also derive from `Microsoft.AspNetCore.Http.BadHttpRequestException`, which derives from `System.IO.IOException`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0cfec-113">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="0cfec-113">Reason for change</span></span>

<span data-ttu-id="0cfec-114">Tato změna byla provedena na:</span><span class="sxs-lookup"><span data-stu-id="0cfec-114">The change was made to:</span></span>

* <span data-ttu-id="0cfec-115">Konsolidujte duplicitní typy.</span><span class="sxs-lookup"><span data-stu-id="0cfec-115">Consolidate duplicate types.</span></span>
* <span data-ttu-id="0cfec-116">Sjednocení chování napříč serverovými implementacemi.</span><span class="sxs-lookup"><span data-stu-id="0cfec-116">Unify behavior across server implementations.</span></span>

<span data-ttu-id="0cfec-117">Aplikace teď může zachytit základní výjimku `Microsoft.AspNetCore.Http.BadHttpRequestException` při použití Kestrel nebo IIS.</span><span class="sxs-lookup"><span data-stu-id="0cfec-117">An app can now catch the base exception `Microsoft.AspNetCore.Http.BadHttpRequestException` when using either Kestrel or IIS.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0cfec-118">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="0cfec-118">Recommended action</span></span>

<span data-ttu-id="0cfec-119">Nahraďte použití `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` a `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` s `Microsoft.AspNetCore.Http.BadHttpRequestException` .</span><span class="sxs-lookup"><span data-stu-id="0cfec-119">Replace usages of `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` with `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span></span>

#### <a name="category"></a><span data-ttu-id="0cfec-120">Kategorie</span><span class="sxs-lookup"><span data-stu-id="0cfec-120">Category</span></span>

<span data-ttu-id="0cfec-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0cfec-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0cfec-122">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0cfec-122">Affected APIs</span></span>

- [<span data-ttu-id="0cfec-123">Microsoft. AspNetCore. Server. IIS. BadHttpRequestException</span><span class="sxs-lookup"><span data-stu-id="0cfec-123">Microsoft.AspNetCore.Server.IIS.BadHttpRequestException</span></span>](/dotnet/api/microsoft.aspnetcore.server.iis.badhttprequestexception?view=aspnetcore-3.1)
- [<span data-ttu-id="0cfec-124">Microsoft. AspNetCore. Server. Kestrel. BadHttpRequestException</span><span class="sxs-lookup"><span data-stu-id="0cfec-124">Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.badhttprequestexception?view=aspnetcore-1.1)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Server.IIS.BadHttpRequestException`
- `T:Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`

-->
