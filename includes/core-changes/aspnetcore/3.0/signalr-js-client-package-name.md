---
ms.openlocfilehash: acef6d7177ee5ad7e18dc8ba1e383d6f76263623
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393955"
---
### <a name="signalr-javascript-client-package-name-changed"></a><span data-ttu-id="9abbe-101">Signal: změnil se název balíčku klienta JavaScript</span><span class="sxs-lookup"><span data-stu-id="9abbe-101">SignalR: JavaScript client package name changed</span></span>

<span data-ttu-id="9abbe-102">V ASP.NET Core 3,0 Preview 7 se název klientského balíčku JavaScriptu pro signály změnil z `@aspnet/signalr` na `@microsoft/signalr`.</span><span class="sxs-lookup"><span data-stu-id="9abbe-102">In ASP.NET Core 3.0 Preview 7, the SignalR JavaScript client package name changed from `@aspnet/signalr` to `@microsoft/signalr`.</span></span> <span data-ttu-id="9abbe-103">Tato změna názvu odráží skutečnost, že signál je užitečný ve více než jenom ASP.NET Corech aplikacích díky službě Azure Signaler.</span><span class="sxs-lookup"><span data-stu-id="9abbe-103">The name change reflects the fact that SignalR is useful in more than just ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

<span data-ttu-id="9abbe-104">Pro reakci na tuto změnu, změňte odkazy v souborech *Package. JSON* , příkazech `require` a příkazech jazyka ECMAScript `import`.</span><span class="sxs-lookup"><span data-stu-id="9abbe-104">To react to this change, change references in your *package.json* files, `require` statements, and ECMAScript `import` statements.</span></span> <span data-ttu-id="9abbe-105">V rámci tohoto přejmenování se žádné rozhraní API nemění.</span><span class="sxs-lookup"><span data-stu-id="9abbe-105">No API will change as part of this rename.</span></span>

<span data-ttu-id="9abbe-106">Diskuzi najdete v tématu [ASPNET/AspNetCore # 11637](https://github.com/aspnet/AspNetCore/issues/11637).</span><span class="sxs-lookup"><span data-stu-id="9abbe-106">For discussion, see [aspnet/AspNetCore#11637](https://github.com/aspnet/AspNetCore/issues/11637).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9abbe-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="9abbe-107">Version introduced</span></span>

<span data-ttu-id="9abbe-108">3.0</span><span class="sxs-lookup"><span data-stu-id="9abbe-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9abbe-109">Staré chování</span><span class="sxs-lookup"><span data-stu-id="9abbe-109">Old behavior</span></span>

<span data-ttu-id="9abbe-110">Balíček klienta byl pojmenován `@aspnet/signalr`.</span><span class="sxs-lookup"><span data-stu-id="9abbe-110">The client package was named `@aspnet/signalr`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="9abbe-111">Nové chování</span><span class="sxs-lookup"><span data-stu-id="9abbe-111">New behavior</span></span>

<span data-ttu-id="9abbe-112">Balíček klienta má název `@microsoft/signalr`.</span><span class="sxs-lookup"><span data-stu-id="9abbe-112">The client package is named `@microsoft/signalr`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9abbe-113">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="9abbe-113">Reason for change</span></span>

<span data-ttu-id="9abbe-114">Změna názvu upřesňuje, že je signál, který je užitečný pro ASP.NET Core aplikace, díky službě Azure Signal Service.</span><span class="sxs-lookup"><span data-stu-id="9abbe-114">The name change clarifies that SignalR is useful beyond ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9abbe-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="9abbe-115">Recommended action</span></span>

<span data-ttu-id="9abbe-116">Přepněte do nového balíčku `@microsoft/signalr`.</span><span class="sxs-lookup"><span data-stu-id="9abbe-116">Switch to the new package `@microsoft/signalr`.</span></span>

#### <a name="category"></a><span data-ttu-id="9abbe-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="9abbe-117">Category</span></span>

<span data-ttu-id="9abbe-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9abbe-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9abbe-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="9abbe-119">Affected APIs</span></span>

<span data-ttu-id="9abbe-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="9abbe-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
