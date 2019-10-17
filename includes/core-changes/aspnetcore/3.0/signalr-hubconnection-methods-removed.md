---
ms.openlocfilehash: a56c5fc32b5fd274d5da0d9b295918f5ea3b345e
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394467"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a><span data-ttu-id="439b9-101">Signál: odebraly se HubConnection ResetSendPing a metody ResetTimeout.</span><span class="sxs-lookup"><span data-stu-id="439b9-101">SignalR: HubConnection ResetSendPing and ResetTimeout methods removed</span></span>

<span data-ttu-id="439b9-102">Metody `ResetSendPing` a `ResetTimeout` byly odebrány z rozhraní API pro signalizaci `HubConnection`.</span><span class="sxs-lookup"><span data-stu-id="439b9-102">The `ResetSendPing` and `ResetTimeout` methods were removed from the SignalR `HubConnection` API.</span></span> <span data-ttu-id="439b9-103">Tyto metody byly původně určeny pouze pro interní použití, ale byly zveřejněny v ASP.NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="439b9-103">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span> <span data-ttu-id="439b9-104">Tyto metody nebudou dostupné od verze ASP.NET Core 3,0 Preview 4.</span><span class="sxs-lookup"><span data-stu-id="439b9-104">These methods won't be available starting in the ASP.NET Core 3.0 Preview 4 release.</span></span> <span data-ttu-id="439b9-105">Diskuzi najdete v tématu [ASPNET/AspNetCore # 8543](https://github.com/aspnet/AspNetCore/issues/8543).</span><span class="sxs-lookup"><span data-stu-id="439b9-105">For discussion, see [aspnet/AspNetCore#8543](https://github.com/aspnet/AspNetCore/issues/8543).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="439b9-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="439b9-106">Version introduced</span></span>

<span data-ttu-id="439b9-107">3.0</span><span class="sxs-lookup"><span data-stu-id="439b9-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="439b9-108">Staré chování</span><span class="sxs-lookup"><span data-stu-id="439b9-108">Old behavior</span></span>

<span data-ttu-id="439b9-109">Rozhraní API jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="439b9-109">APIs were available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="439b9-110">Nové chování</span><span class="sxs-lookup"><span data-stu-id="439b9-110">New behavior</span></span>

<span data-ttu-id="439b9-111">Rozhraní API se odeberou.</span><span class="sxs-lookup"><span data-stu-id="439b9-111">APIs are removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="439b9-112">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="439b9-112">Reason for change</span></span>

<span data-ttu-id="439b9-113">Tyto metody byly původně určeny pouze pro interní použití, ale byly zveřejněny v ASP.NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="439b9-113">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="439b9-114">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="439b9-114">Recommended action</span></span>

<span data-ttu-id="439b9-115">Tyto metody nepoužívejte.</span><span class="sxs-lookup"><span data-stu-id="439b9-115">Don't use these methods.</span></span>

#### <a name="category"></a><span data-ttu-id="439b9-116">Kategorie</span><span class="sxs-lookup"><span data-stu-id="439b9-116">Category</span></span>

<span data-ttu-id="439b9-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="439b9-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="439b9-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="439b9-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing`
- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout`

-->
