---
ms.openlocfilehash: ca0792a3fd05d28cecceac1d644e3e4bf64722bc
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345226"
---
### <a name="signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package"></a><span data-ttu-id="27e53-101">Signal: protokol centra MessagePack se přesunul do balíčku MessagePack 2. x.</span><span class="sxs-lookup"><span data-stu-id="27e53-101">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>

<span data-ttu-id="27e53-102">[Protokol MessagePack hub](/aspnet/core/signalr/messagepackhubprotocol) používá [MessagePack balíček NuGet](https://www.nuget.org/packages/MessagePack) pro serializaci MessagePack. ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="27e53-102">The ASP.NET Core SignalR [MessagePack Hub Protocol](/aspnet/core/signalr/messagepackhubprotocol) uses the [MessagePack NuGet package](https://www.nuget.org/packages/MessagePack) for MessagePack serialization.</span></span> <span data-ttu-id="27e53-103">ASP.NET Core 5,0 upgraduje balíček z 1. x na nejnovější verzi balíčku 2. x.</span><span class="sxs-lookup"><span data-stu-id="27e53-103">ASP.NET Core 5.0 upgrades the package from 1.x to the latest 2.x package version.</span></span>

<span data-ttu-id="27e53-104">Diskuzi o tomto problému najdete v tématu [dotnet/aspnetcore # 18692](https://github.com/dotnet/aspnetcore/issues/18692).</span><span class="sxs-lookup"><span data-stu-id="27e53-104">For discussion on this issue, see [dotnet/aspnetcore#18692](https://github.com/dotnet/aspnetcore/issues/18692).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="27e53-105">Představená verze</span><span class="sxs-lookup"><span data-stu-id="27e53-105">Version introduced</span></span>

<span data-ttu-id="27e53-106">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="27e53-106">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="27e53-107">Staré chování</span><span class="sxs-lookup"><span data-stu-id="27e53-107">Old behavior</span></span>

<span data-ttu-id="27e53-108">ASP.NET Core Signal používá balíček MessagePack 1. x k serializaci a deserializaci zpráv MessagePack.</span><span class="sxs-lookup"><span data-stu-id="27e53-108">ASP.NET Core SignalR used the MessagePack 1.x package to serialize and deserialize MessagePack messages.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="27e53-109">Nové chování</span><span class="sxs-lookup"><span data-stu-id="27e53-109">New behavior</span></span>

<span data-ttu-id="27e53-110">ASP.NET Core Signal používá k serializaci a deserializaci MessagePack zpráv balíček MessagePack 2. x.</span><span class="sxs-lookup"><span data-stu-id="27e53-110">ASP.NET Core SignalR uses the MessagePack 2.x package to serialize and deserialize MessagePack messages.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="27e53-111">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="27e53-111">Reason for change</span></span>

<span data-ttu-id="27e53-112">Nejnovější vylepšení v balíčku MessagePack 2. x přidávají užitečné funkce.</span><span class="sxs-lookup"><span data-stu-id="27e53-112">The latest improvements in the MessagePack 2.x package add useful functionality.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="27e53-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="27e53-113">Recommended action</span></span>

<span data-ttu-id="27e53-114">Tato změna se projeví v těchto případech:</span><span class="sxs-lookup"><span data-stu-id="27e53-114">This breaking change applies when:</span></span>

* <span data-ttu-id="27e53-115">Nastavení nebo konfigurace hodnot na <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions> .</span><span class="sxs-lookup"><span data-stu-id="27e53-115">Setting or configuring values on <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span></span>
* <span data-ttu-id="27e53-116">Pomocí rozhraní API MessagePack přímo a pomocí protokolu MessagePack (ASP.NET Core Signaler hub) ve stejném projektu.</span><span class="sxs-lookup"><span data-stu-id="27e53-116">Using the MessagePack APIs directly and using the ASP.NET Core SignalR MessagePack Hub Protocol in the same project.</span></span> <span data-ttu-id="27e53-117">Místo předchozí verze se načte novější verze.</span><span class="sxs-lookup"><span data-stu-id="27e53-117">The newer version will be loaded instead of the previous version.</span></span>

<span data-ttu-id="27e53-118">Pokyny k migraci pro autory balíčku najdete v tématu [migrace z MessagePack v1. x na MessagePack v2. x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md).</span><span class="sxs-lookup"><span data-stu-id="27e53-118">For migration guidance from the package authors, see [Migrating from MessagePack v1.x to MessagePack v2.x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md).</span></span> <span data-ttu-id="27e53-119">Jsou ovlivněny některé aspekty serializace a deserializace zprávy.</span><span class="sxs-lookup"><span data-stu-id="27e53-119">Some aspects of message serialization and deserialization are affected.</span></span> <span data-ttu-id="27e53-120">Konkrétně existují [změny chování při serializaci hodnot data a času](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes).</span><span class="sxs-lookup"><span data-stu-id="27e53-120">Specifically, there are [behavioral changes to how DateTime values are serialized](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes).</span></span>

#### <a name="category"></a><span data-ttu-id="27e53-121">Kategorie</span><span class="sxs-lookup"><span data-stu-id="27e53-121">Category</span></span>

<span data-ttu-id="27e53-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="27e53-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="27e53-123">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="27e53-123">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
