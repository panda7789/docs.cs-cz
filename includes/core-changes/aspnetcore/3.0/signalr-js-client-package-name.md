---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75902060"
---
### <a name="signalr-javascript-client-package-name-changed"></a><span data-ttu-id="a04d8-101">Signal: změnil se název balíčku klienta JavaScript</span><span class="sxs-lookup"><span data-stu-id="a04d8-101">SignalR: JavaScript client package name changed</span></span>

<span data-ttu-id="a04d8-102">V ASP.NET Core 3,0 Preview 7 se název klientského balíčku JavaScriptu pro signály změnil z `@aspnet/signalr` na `@microsoft/signalr`.</span><span class="sxs-lookup"><span data-stu-id="a04d8-102">In ASP.NET Core 3.0 Preview 7, the SignalR JavaScript client package name changed from `@aspnet/signalr` to `@microsoft/signalr`.</span></span> <span data-ttu-id="a04d8-103">Tato změna názvu odráží skutečnost, že signál je užitečný ve více než jenom ASP.NET Corech aplikacích díky službě Azure Signaler.</span><span class="sxs-lookup"><span data-stu-id="a04d8-103">The name change reflects the fact that SignalR is useful in more than just ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

<span data-ttu-id="a04d8-104">Chcete-li na tuto změnu reagovat, změňte odkazy v souborech *Package. JSON* , `require` příkazy a ECMAScript `import` příkazy.</span><span class="sxs-lookup"><span data-stu-id="a04d8-104">To react to this change, change references in your *package.json* files, `require` statements, and ECMAScript `import` statements.</span></span> <span data-ttu-id="a04d8-105">V rámci tohoto přejmenování se žádné rozhraní API nemění.</span><span class="sxs-lookup"><span data-stu-id="a04d8-105">No API will change as part of this rename.</span></span>

<span data-ttu-id="a04d8-106">Diskuzi najdete v tématu [dotnet/aspnetcore # 11637](https://github.com/dotnet/aspnetcore/issues/11637).</span><span class="sxs-lookup"><span data-stu-id="a04d8-106">For discussion, see [dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a04d8-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="a04d8-107">Version introduced</span></span>

<span data-ttu-id="a04d8-108">3,0</span><span class="sxs-lookup"><span data-stu-id="a04d8-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a04d8-109">Staré chování</span><span class="sxs-lookup"><span data-stu-id="a04d8-109">Old behavior</span></span>

<span data-ttu-id="a04d8-110">Balíček klienta byl pojmenován `@aspnet/signalr`.</span><span class="sxs-lookup"><span data-stu-id="a04d8-110">The client package was named `@aspnet/signalr`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a04d8-111">Nové chování</span><span class="sxs-lookup"><span data-stu-id="a04d8-111">New behavior</span></span>

<span data-ttu-id="a04d8-112">Balíček klienta má název `@microsoft/signalr`.</span><span class="sxs-lookup"><span data-stu-id="a04d8-112">The client package is named `@microsoft/signalr`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a04d8-113">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="a04d8-113">Reason for change</span></span>

<span data-ttu-id="a04d8-114">Změna názvu upřesňuje, že je signál, který je užitečný pro ASP.NET Core aplikace, díky službě Azure Signal Service.</span><span class="sxs-lookup"><span data-stu-id="a04d8-114">The name change clarifies that SignalR is useful beyond ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a04d8-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="a04d8-115">Recommended action</span></span>

<span data-ttu-id="a04d8-116">Přepněte na `@microsoft/signalr`nového balíčku.</span><span class="sxs-lookup"><span data-stu-id="a04d8-116">Switch to the new package `@microsoft/signalr`.</span></span>

#### <a name="category"></a><span data-ttu-id="a04d8-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="a04d8-117">Category</span></span>

<span data-ttu-id="a04d8-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a04d8-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a04d8-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="a04d8-119">Affected APIs</span></span>

<span data-ttu-id="a04d8-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="a04d8-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
