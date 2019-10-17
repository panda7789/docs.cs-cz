---
ms.openlocfilehash: be9a79f6ead3e72d7ffaade758704f0c1e2477f0
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394029"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a><span data-ttu-id="08c29-101">Hostování: obecný hostitel omezuje úvodní vkládání spouštěcího konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="08c29-101">Hosting: Generic host restricts Startup constructor injection</span></span>

<span data-ttu-id="08c29-102">Jediné typy, které podporuje obecný hostitel, pro vkládání konstruktoru třídy `Startup` jsou `IHostEnvironment`, `IWebHostEnvironment` a `IConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="08c29-102">The only types the generic host supports for `Startup` class constructor injection are `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration`.</span></span> <span data-ttu-id="08c29-103">Aplikace používající `WebHost` nejsou ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="08c29-103">Apps using `WebHost` are unaffected.</span></span>

#### <a name="change-description"></a><span data-ttu-id="08c29-104">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="08c29-104">Change description</span></span>

<span data-ttu-id="08c29-105">Před ASP.NET Core 3,0 lze injektáže konstruktoru použít pro libovolný typ v konstruktoru třídy `Startup`.</span><span class="sxs-lookup"><span data-stu-id="08c29-105">Prior to ASP.NET Core 3.0, constructor injection could be used for arbitrary types in the `Startup` class's constructor.</span></span> <span data-ttu-id="08c29-106">V ASP.NET Core 3,0 byl webový zásobník znovu založen na obecné knihovně hostitelů.</span><span class="sxs-lookup"><span data-stu-id="08c29-106">In ASP.NET Core 3.0, the web stack was replatformed onto the generic host library.</span></span> <span data-ttu-id="08c29-107">Můžete zobrazit změnu v souboru *program.cs* šablony:</span><span class="sxs-lookup"><span data-stu-id="08c29-107">You can see the change in the *Program.cs* file of the templates:</span></span>

<span data-ttu-id="08c29-108">**ASP.NET Core 2. x:**</span><span class="sxs-lookup"><span data-stu-id="08c29-108">**ASP.NET Core 2.x:**</span></span>

<https://github.com/aspnet/AspNetCore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

<span data-ttu-id="08c29-109">**ASP.NET Core 3,0:**</span><span class="sxs-lookup"><span data-stu-id="08c29-109">**ASP.NET Core 3.0:**</span></span>

<https://github.com/aspnet/AspNetCore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

<span data-ttu-id="08c29-110">`Host` používá k sestavení aplikace jeden kontejner vkládání závislostí (DI).</span><span class="sxs-lookup"><span data-stu-id="08c29-110">`Host` uses one dependency injection (DI) container to build the app.</span></span> <span data-ttu-id="08c29-111">`WebHost` používá dva kontejnery: jeden pro hostitele a jeden pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="08c29-111">`WebHost` uses two containers: one for the host and one for the app.</span></span> <span data-ttu-id="08c29-112">V důsledku toho konstruktor `Startup` již nepodporuje vlastní vkládání služeb.</span><span class="sxs-lookup"><span data-stu-id="08c29-112">As a result, the `Startup` constructor no longer supports custom service injection.</span></span> <span data-ttu-id="08c29-113">Vložit lze pouze `IHostEnvironment`, `IWebHostEnvironment` a `IConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="08c29-113">Only `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration` can be injected.</span></span> <span data-ttu-id="08c29-114">Tato změna zabraňuje chybám typu DI, jako je vytváření duplicitních služeb typu singleton.</span><span class="sxs-lookup"><span data-stu-id="08c29-114">This change prevents DI issues such as the duplicate creation of a singleton service.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="08c29-115">Představená verze</span><span class="sxs-lookup"><span data-stu-id="08c29-115">Version introduced</span></span>

<span data-ttu-id="08c29-116">3.0</span><span class="sxs-lookup"><span data-stu-id="08c29-116">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="08c29-117">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="08c29-117">Reason for change</span></span>

<span data-ttu-id="08c29-118">Tato změna je v důsledku opětovného hostování webového zásobníku do obecné knihovny hostitelů.</span><span class="sxs-lookup"><span data-stu-id="08c29-118">This change is a consequence of replatforming the web stack onto the generic host library.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="08c29-119">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="08c29-119">Recommended action</span></span>

<span data-ttu-id="08c29-120">Vloží služby do signatury metody `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="08c29-120">Inject services into the `Startup.Configure` method signature.</span></span> <span data-ttu-id="08c29-121">Příklad:</span><span class="sxs-lookup"><span data-stu-id="08c29-121">For example:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IOptions<MyOptions> options)
```

#### <a name="category"></a><span data-ttu-id="08c29-122">Kategorie</span><span class="sxs-lookup"><span data-stu-id="08c29-122">Category</span></span>

<span data-ttu-id="08c29-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="08c29-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="08c29-124">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="08c29-124">Affected APIs</span></span>

<span data-ttu-id="08c29-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="08c29-125">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
