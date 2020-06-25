---
ms.openlocfilehash: 29908ed916690e67db3cc5d72ebe1b1c6aea45c6
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325216"
---
### <a name="iis-urlrewrite-middleware-query-strings-are-preserved"></a><span data-ttu-id="7a9ee-101">IIS: UrlRewrite řetězce dotazů middleware jsou zachovány.</span><span class="sxs-lookup"><span data-stu-id="7a9ee-101">IIS: UrlRewrite middleware query strings are preserved</span></span>

<span data-ttu-id="7a9ee-102">UrlRewrite middlewaru služby IIS zabránila zachovávání řetězce dotazu v pravidlech pro přepsání.</span><span class="sxs-lookup"><span data-stu-id="7a9ee-102">An IIS UrlRewrite middleware defect prevented the query string from being preserved in rewrite rules.</span></span> <span data-ttu-id="7a9ee-103">Tato vada byla opravena, aby zachovala konzistenci s chováním modulu IIS UrlRewrite.</span><span class="sxs-lookup"><span data-stu-id="7a9ee-103">That defect has been fixed to maintain consistency with the IIS UrlRewrite Module's behavior.</span></span>

<span data-ttu-id="7a9ee-104">Diskuzi najdete v tématu problém [dotnet/aspnetcore # 22972](https://github.com/dotnet/aspnetcore/issues/22972).</span><span class="sxs-lookup"><span data-stu-id="7a9ee-104">For discussion, see issue [dotnet/aspnetcore#22972](https://github.com/dotnet/aspnetcore/issues/22972).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7a9ee-105">Představená verze</span><span class="sxs-lookup"><span data-stu-id="7a9ee-105">Version introduced</span></span>

<span data-ttu-id="7a9ee-106">ASP.NET Core 5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="7a9ee-106">ASP.NET Core 5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="7a9ee-107">Staré chování</span><span class="sxs-lookup"><span data-stu-id="7a9ee-107">Old behavior</span></span>

<span data-ttu-id="7a9ee-108">Vezměte v úvahu následující pravidlo přepsání:</span><span class="sxs-lookup"><span data-stu-id="7a9ee-108">Consider the following rewrite rule:</span></span>

```xml
<rule name="MyRule" stopProcessing="true">
  <match url="^about" />
  <action type="Redirect" url="/contact" redirectType="Temporary" appendQueryString="true" />
</rule>
```

<span data-ttu-id="7a9ee-109">Předchozí pravidlo nepřipojí řetězec dotazu.</span><span class="sxs-lookup"><span data-stu-id="7a9ee-109">The preceding rule doesn't append the query string.</span></span> <span data-ttu-id="7a9ee-110">Identifikátor URI, jako je `/about?id=1` přesměrování na `/contact` místo `/contact?id=1` .</span><span class="sxs-lookup"><span data-stu-id="7a9ee-110">A URI like `/about?id=1` redirects to `/contact` instead of `/contact?id=1`.</span></span> <span data-ttu-id="7a9ee-111">`appendQueryString`Výchozí hodnota atributu je `true` také.</span><span class="sxs-lookup"><span data-stu-id="7a9ee-111">The `appendQueryString` attribute defaults to `true` as well.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="7a9ee-112">Nové chování</span><span class="sxs-lookup"><span data-stu-id="7a9ee-112">New behavior</span></span>

<span data-ttu-id="7a9ee-113">Řetězec dotazu se zachová.</span><span class="sxs-lookup"><span data-stu-id="7a9ee-113">The query string is preserved.</span></span> <span data-ttu-id="7a9ee-114">Identifikátor URI z příkladu ve [starém chování](#old-behavior) by byl `/contact?id=1` .</span><span class="sxs-lookup"><span data-stu-id="7a9ee-114">The URI from the example in [Old behavior](#old-behavior) would be `/contact?id=1`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7a9ee-115">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="7a9ee-115">Reason for change</span></span>

<span data-ttu-id="7a9ee-116">Původní chování se neshodovalo s chováním modulu IIS UrlRewrite.</span><span class="sxs-lookup"><span data-stu-id="7a9ee-116">The old behavior didn't match the IIS UrlRewrite Module's behavior.</span></span> <span data-ttu-id="7a9ee-117">Aby bylo možné podporovat přenos mezi middlewarem a modulem, je cílem zachovat konzistentní chování.</span><span class="sxs-lookup"><span data-stu-id="7a9ee-117">To support porting between the middleware and module, the goal is to maintain consistent behaviors.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7a9ee-118">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="7a9ee-118">Recommended action</span></span>

<span data-ttu-id="7a9ee-119">Pokud je upřednostňováno chování při odebírání řetězce dotazu, nastavte `action` element na `appendQueryString="false"` .</span><span class="sxs-lookup"><span data-stu-id="7a9ee-119">If the behavior of removing the query string is preferred, set the `action` element to `appendQueryString="false"`.</span></span>

#### <a name="category"></a><span data-ttu-id="7a9ee-120">Kategorie</span><span class="sxs-lookup"><span data-stu-id="7a9ee-120">Category</span></span>

<span data-ttu-id="7a9ee-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7a9ee-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7a9ee-122">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="7a9ee-122">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite`

-->
