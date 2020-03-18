---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902060"
---
### <a name="signalr-javascript-client-package-name-changed"></a><span data-ttu-id="7eae7-101">SignalR: Název klientského balíčku JavaScriptu byl změněn.</span><span class="sxs-lookup"><span data-stu-id="7eae7-101">SignalR: JavaScript client package name changed</span></span>

<span data-ttu-id="7eae7-102">V ASP.NET Core 3.0 Preview 7 se název klientského `@microsoft/signalr`balíčku SignalR JavaScript změnil z na `@aspnet/signalr` .</span><span class="sxs-lookup"><span data-stu-id="7eae7-102">In ASP.NET Core 3.0 Preview 7, the SignalR JavaScript client package name changed from `@aspnet/signalr` to `@microsoft/signalr`.</span></span> <span data-ttu-id="7eae7-103">Změna názvu odráží skutečnost, že SignalR je užitečný ve více než jen ASP.NET aplikace core, díky službě Azure SignalR.</span><span class="sxs-lookup"><span data-stu-id="7eae7-103">The name change reflects the fact that SignalR is useful in more than just ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

<span data-ttu-id="7eae7-104">Chcete-li reagovat na tuto změnu, změňte `require` odkazy v souborech `import` *package.json,* příkazech a příkazech ECMAScript.</span><span class="sxs-lookup"><span data-stu-id="7eae7-104">To react to this change, change references in your *package.json* files, `require` statements, and ECMAScript `import` statements.</span></span> <span data-ttu-id="7eae7-105">Žádné rozhraní API se změní jako součást tohoto přejmenování.</span><span class="sxs-lookup"><span data-stu-id="7eae7-105">No API will change as part of this rename.</span></span>

<span data-ttu-id="7eae7-106">Diskuse naleznete [v tématu dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637).</span><span class="sxs-lookup"><span data-stu-id="7eae7-106">For discussion, see [dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7eae7-107">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="7eae7-107">Version introduced</span></span>

<span data-ttu-id="7eae7-108">3.0</span><span class="sxs-lookup"><span data-stu-id="7eae7-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="7eae7-109">Staré chování</span><span class="sxs-lookup"><span data-stu-id="7eae7-109">Old behavior</span></span>

<span data-ttu-id="7eae7-110">Klientský balíček `@aspnet/signalr`byl pojmenován .</span><span class="sxs-lookup"><span data-stu-id="7eae7-110">The client package was named `@aspnet/signalr`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="7eae7-111">Nové chování</span><span class="sxs-lookup"><span data-stu-id="7eae7-111">New behavior</span></span>

<span data-ttu-id="7eae7-112">Klientský balíček `@microsoft/signalr`je pojmenován .</span><span class="sxs-lookup"><span data-stu-id="7eae7-112">The client package is named `@microsoft/signalr`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7eae7-113">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="7eae7-113">Reason for change</span></span>

<span data-ttu-id="7eae7-114">Změna názvu objasňuje, že SignalR je užitečný mimo ASP.NET aplikace core, díky službě Azure SignalR.</span><span class="sxs-lookup"><span data-stu-id="7eae7-114">The name change clarifies that SignalR is useful beyond ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7eae7-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="7eae7-115">Recommended action</span></span>

<span data-ttu-id="7eae7-116">Přepněte na `@microsoft/signalr`nový balíček .</span><span class="sxs-lookup"><span data-stu-id="7eae7-116">Switch to the new package `@microsoft/signalr`.</span></span>

#### <a name="category"></a><span data-ttu-id="7eae7-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="7eae7-117">Category</span></span>

<span data-ttu-id="7eae7-118">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="7eae7-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7eae7-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="7eae7-119">Affected APIs</span></span>

<span data-ttu-id="7eae7-120">Žádný</span><span class="sxs-lookup"><span data-stu-id="7eae7-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
