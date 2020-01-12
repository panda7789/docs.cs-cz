---
ms.openlocfilehash: d1ddba72ce25c5e01025d916d52f785b5a1a9e71
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901990"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a><span data-ttu-id="d42be-101">Hostování: obecný hostitel omezuje úvodní vkládání spouštěcího konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d42be-101">Hosting: Generic host restricts Startup constructor injection</span></span>

<span data-ttu-id="d42be-102">Jediný typ, který je podporován pro vkládání konstruktoru `Startup` třídy, je `IHostEnvironment`, `IWebHostEnvironment`a `IConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="d42be-102">The only types the generic host supports for `Startup` class constructor injection are `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration`.</span></span> <span data-ttu-id="d42be-103">Aplikace používající `WebHost` nejsou nijak ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="d42be-103">Apps using `WebHost` are unaffected.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d42be-104">Popis změny</span><span class="sxs-lookup"><span data-stu-id="d42be-104">Change description</span></span>

<span data-ttu-id="d42be-105">Před ASP.NET Core 3,0 lze vložení konstruktoru použít pro libovolný typ v konstruktoru třídy `Startup`.</span><span class="sxs-lookup"><span data-stu-id="d42be-105">Prior to ASP.NET Core 3.0, constructor injection could be used for arbitrary types in the `Startup` class's constructor.</span></span> <span data-ttu-id="d42be-106">V ASP.NET Core 3,0 byl webový zásobník znovu založen na obecné knihovně hostitelů.</span><span class="sxs-lookup"><span data-stu-id="d42be-106">In ASP.NET Core 3.0, the web stack was replatformed onto the generic host library.</span></span> <span data-ttu-id="d42be-107">Můžete zobrazit změnu v souboru *program.cs* šablony:</span><span class="sxs-lookup"><span data-stu-id="d42be-107">You can see the change in the *Program.cs* file of the templates:</span></span>

<span data-ttu-id="d42be-108">**ASP.NET Core 2. x:**</span><span class="sxs-lookup"><span data-stu-id="d42be-108">**ASP.NET Core 2.x:**</span></span>

<https://github.com/dotnet/aspnetcore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

<span data-ttu-id="d42be-109">**ASP.NET Core 3,0:**</span><span class="sxs-lookup"><span data-stu-id="d42be-109">**ASP.NET Core 3.0:**</span></span>

<https://github.com/dotnet/aspnetcore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

<span data-ttu-id="d42be-110">`Host` používá k sestavení aplikace jeden kontejner vkládání závislostí (DI).</span><span class="sxs-lookup"><span data-stu-id="d42be-110">`Host` uses one dependency injection (DI) container to build the app.</span></span> <span data-ttu-id="d42be-111">`WebHost` používá dva kontejnery: jeden pro hostitele a jeden pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d42be-111">`WebHost` uses two containers: one for the host and one for the app.</span></span> <span data-ttu-id="d42be-112">V důsledku toho konstruktor `Startup` již nepodporuje vlastní vkládání služeb.</span><span class="sxs-lookup"><span data-stu-id="d42be-112">As a result, the `Startup` constructor no longer supports custom service injection.</span></span> <span data-ttu-id="d42be-113">Vložit lze pouze `IHostEnvironment`, `IWebHostEnvironment`a `IConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="d42be-113">Only `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration` can be injected.</span></span> <span data-ttu-id="d42be-114">Tato změna zabraňuje chybám typu DI, jako je vytváření duplicitních služeb typu singleton.</span><span class="sxs-lookup"><span data-stu-id="d42be-114">This change prevents DI issues such as the duplicate creation of a singleton service.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d42be-115">Představená verze</span><span class="sxs-lookup"><span data-stu-id="d42be-115">Version introduced</span></span>

<span data-ttu-id="d42be-116">3,0</span><span class="sxs-lookup"><span data-stu-id="d42be-116">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d42be-117">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="d42be-117">Reason for change</span></span>

<span data-ttu-id="d42be-118">Tato změna je v důsledku opětovného hostování webového zásobníku do obecné knihovny hostitelů.</span><span class="sxs-lookup"><span data-stu-id="d42be-118">This change is a consequence of replatforming the web stack onto the generic host library.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d42be-119">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="d42be-119">Recommended action</span></span>

<span data-ttu-id="d42be-120">Vloží služby do signatury `Startup.Configure` metody.</span><span class="sxs-lookup"><span data-stu-id="d42be-120">Inject services into the `Startup.Configure` method signature.</span></span> <span data-ttu-id="d42be-121">Příklad:</span><span class="sxs-lookup"><span data-stu-id="d42be-121">For example:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IOptions<MyOptions> options)
```

#### <a name="category"></a><span data-ttu-id="d42be-122">Kategorie</span><span class="sxs-lookup"><span data-stu-id="d42be-122">Category</span></span>

<span data-ttu-id="d42be-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d42be-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d42be-124">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="d42be-124">Affected APIs</span></span>

<span data-ttu-id="d42be-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="d42be-125">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
