---
ms.openlocfilehash: d1ddba72ce25c5e01025d916d52f785b5a1a9e71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901990"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a><span data-ttu-id="10f43-101">Hostování: Obecný hostitel omezuje injekci konstruktoru spuštění</span><span class="sxs-lookup"><span data-stu-id="10f43-101">Hosting: Generic host restricts Startup constructor injection</span></span>

<span data-ttu-id="10f43-102">Jediné typy, které obecný `Startup` hostitel podporuje `IHostEnvironment`pro `IWebHostEnvironment`vstřikování konstruktoru třídy, jsou , , a `IConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="10f43-102">The only types the generic host supports for `Startup` class constructor injection are `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration`.</span></span> <span data-ttu-id="10f43-103">Aplikace, `WebHost` které používají, nejsou ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="10f43-103">Apps using `WebHost` are unaffected.</span></span>

#### <a name="change-description"></a><span data-ttu-id="10f43-104">Popis změny</span><span class="sxs-lookup"><span data-stu-id="10f43-104">Change description</span></span>

<span data-ttu-id="10f43-105">Před ASP.NET Core 3.0, vstřikování konstruktoru `Startup` lze použít pro libovolné typy v konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="10f43-105">Prior to ASP.NET Core 3.0, constructor injection could be used for arbitrary types in the `Startup` class's constructor.</span></span> <span data-ttu-id="10f43-106">V ASP.NET Core 3.0 byl webový zásobník přepojován do obecné hostitelské knihovny.</span><span class="sxs-lookup"><span data-stu-id="10f43-106">In ASP.NET Core 3.0, the web stack was replatformed onto the generic host library.</span></span> <span data-ttu-id="10f43-107">Můžete vidět změnu v *souboru Program.cs* šablon:</span><span class="sxs-lookup"><span data-stu-id="10f43-107">You can see the change in the *Program.cs* file of the templates:</span></span>

<span data-ttu-id="10f43-108">**ASP.NET Jádro 2.x:**</span><span class="sxs-lookup"><span data-stu-id="10f43-108">**ASP.NET Core 2.x:**</span></span>

<https://github.com/dotnet/aspnetcore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

<span data-ttu-id="10f43-109">**ASP.NET jádro 3.0:**</span><span class="sxs-lookup"><span data-stu-id="10f43-109">**ASP.NET Core 3.0:**</span></span>

<https://github.com/dotnet/aspnetcore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

<span data-ttu-id="10f43-110">`Host`používá jeden kontejner vkládání závislostí (DI) k vytvoření aplikace.</span><span class="sxs-lookup"><span data-stu-id="10f43-110">`Host` uses one dependency injection (DI) container to build the app.</span></span> <span data-ttu-id="10f43-111">`WebHost`používá dva kontejnery: jeden pro hostitele a jeden pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="10f43-111">`WebHost` uses two containers: one for the host and one for the app.</span></span> <span data-ttu-id="10f43-112">V důsledku toho `Startup` konstruktor již podporuje vlastní injektáž služby.</span><span class="sxs-lookup"><span data-stu-id="10f43-112">As a result, the `Startup` constructor no longer supports custom service injection.</span></span> <span data-ttu-id="10f43-113">Pouze `IHostEnvironment` `IWebHostEnvironment`, `IConfiguration` , a může být aplikován.</span><span class="sxs-lookup"><span data-stu-id="10f43-113">Only `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration` can be injected.</span></span> <span data-ttu-id="10f43-114">Tato změna zabraňuje di problémy, jako je například duplicitní vytvoření služby singleton.</span><span class="sxs-lookup"><span data-stu-id="10f43-114">This change prevents DI issues such as the duplicate creation of a singleton service.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="10f43-115">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="10f43-115">Version introduced</span></span>

<span data-ttu-id="10f43-116">3.0</span><span class="sxs-lookup"><span data-stu-id="10f43-116">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="10f43-117">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="10f43-117">Reason for change</span></span>

<span data-ttu-id="10f43-118">Tato změna je důsledkem replatforming webovézásobníku do obecné knihovny hostitelů.</span><span class="sxs-lookup"><span data-stu-id="10f43-118">This change is a consequence of replatforming the web stack onto the generic host library.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="10f43-119">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="10f43-119">Recommended action</span></span>

<span data-ttu-id="10f43-120">Vložte služby do podpisu `Startup.Configure` metody.</span><span class="sxs-lookup"><span data-stu-id="10f43-120">Inject services into the `Startup.Configure` method signature.</span></span> <span data-ttu-id="10f43-121">Například:</span><span class="sxs-lookup"><span data-stu-id="10f43-121">For example:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IOptions<MyOptions> options)
```

#### <a name="category"></a><span data-ttu-id="10f43-122">Kategorie</span><span class="sxs-lookup"><span data-stu-id="10f43-122">Category</span></span>

<span data-ttu-id="10f43-123">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="10f43-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="10f43-124">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="10f43-124">Affected APIs</span></span>

<span data-ttu-id="10f43-125">Žádný</span><span class="sxs-lookup"><span data-stu-id="10f43-125">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
