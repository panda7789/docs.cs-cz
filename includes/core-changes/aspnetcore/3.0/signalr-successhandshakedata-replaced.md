---
ms.openlocfilehash: 1d8bcaf68d44f27642048c1c207b52c55b604690
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901589"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a><span data-ttu-id="68345-101">SignalR: HandshakeProtocol.SuccessHandshakeData nahrazen</span><span class="sxs-lookup"><span data-stu-id="68345-101">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>

<span data-ttu-id="68345-102">Pole [HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) bylo odebráno a nahrazeno pomocnou metodou, která generuje `IHubProtocol`úspěšnou odpověď handshake dané konkrétní .</span><span class="sxs-lookup"><span data-stu-id="68345-102">The [HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) field was removed and replaced with a helper method that generates a successful handshake response given a specific `IHubProtocol`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="68345-103">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="68345-103">Version introduced</span></span>

<span data-ttu-id="68345-104">3.0</span><span class="sxs-lookup"><span data-stu-id="68345-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="68345-105">Staré chování</span><span class="sxs-lookup"><span data-stu-id="68345-105">Old behavior</span></span>

<span data-ttu-id="68345-106">`HandshakeProtocol.SuccessHandshakeData`bylo `public static ReadOnlyMemory<byte>` pole.</span><span class="sxs-lookup"><span data-stu-id="68345-106">`HandshakeProtocol.SuccessHandshakeData` was a `public static ReadOnlyMemory<byte>` field.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="68345-107">Nové chování</span><span class="sxs-lookup"><span data-stu-id="68345-107">New behavior</span></span>

<span data-ttu-id="68345-108">`HandshakeProtocol.SuccessHandshakeData`byla nahrazena `static` `GetSuccessfulHandshake(IHubProtocol protocol)` metodou, která `ReadOnlyMemory<byte>` vrací na základě zadaného protokolu.</span><span class="sxs-lookup"><span data-stu-id="68345-108">`HandshakeProtocol.SuccessHandshakeData` has been replaced by a `static` `GetSuccessfulHandshake(IHubProtocol protocol)` method that returns a `ReadOnlyMemory<byte>` based on the specified protocol.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="68345-109">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="68345-109">Reason for change</span></span>

<span data-ttu-id="68345-110">Další pole byla přidána do _odpovědi_ handshake, které nejsou konstantní a mění se v závislosti na vybraném protokolu.</span><span class="sxs-lookup"><span data-stu-id="68345-110">Additional fields were added to the handshake _response_ that are non-constant and change depending on the selected protocol.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="68345-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="68345-111">Recommended action</span></span>

<span data-ttu-id="68345-112">Žádné.</span><span class="sxs-lookup"><span data-stu-id="68345-112">None.</span></span> <span data-ttu-id="68345-113">Tento typ není určen pro použití z uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="68345-113">This type isn't designed for use from user code.</span></span> <span data-ttu-id="68345-114">Je to `public`, takže může být sdílena mezi serverem SignalR a klientem.</span><span class="sxs-lookup"><span data-stu-id="68345-114">It's `public`, so it can be shared between the SignalR server and client.</span></span> <span data-ttu-id="68345-115">Může být také používán klienty signalr zákazníka napsanými v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="68345-115">It may also be used by customer SignalR clients written in .NET.</span></span> <span data-ttu-id="68345-116">**Uživatelé** SignalR by neměly být ovlivněny touto změnou.</span><span class="sxs-lookup"><span data-stu-id="68345-116">**Users** of SignalR shouldn't be affected by this change.</span></span>

#### <a name="category"></a><span data-ttu-id="68345-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="68345-117">Category</span></span>

<span data-ttu-id="68345-118">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="68345-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="68345-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="68345-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
