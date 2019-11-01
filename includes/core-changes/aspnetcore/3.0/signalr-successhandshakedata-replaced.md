---
ms.openlocfilehash: e9278320ee3fdf9e6b89698d187f047c309ea791
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198402"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a><span data-ttu-id="4e38a-101">Signál: HandshakeProtocol. SuccessHandshakeData nahrazeno</span><span class="sxs-lookup"><span data-stu-id="4e38a-101">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>

<span data-ttu-id="4e38a-102">Pole [HandshakeProtocol. SuccessHandshakeData](https://github.com/aspnet/AspNetCore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) bylo odebráno a nahrazeno podpůrnou metodou, která generuje úspěšnou odpověď handshake s daným konkrétním `IHubProtocol`.</span><span class="sxs-lookup"><span data-stu-id="4e38a-102">The [HandshakeProtocol.SuccessHandshakeData](https://github.com/aspnet/AspNetCore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) field was removed and replaced with a helper method that generates a successful handshake response given a specific `IHubProtocol`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4e38a-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="4e38a-103">Version introduced</span></span>

<span data-ttu-id="4e38a-104">3.0</span><span class="sxs-lookup"><span data-stu-id="4e38a-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="4e38a-105">Staré chování</span><span class="sxs-lookup"><span data-stu-id="4e38a-105">Old behavior</span></span>

<span data-ttu-id="4e38a-106">`HandshakeProtocol.SuccessHandshakeData` bylo pole `public static ReadOnlyMemory<byte>`.</span><span class="sxs-lookup"><span data-stu-id="4e38a-106">`HandshakeProtocol.SuccessHandshakeData` was a `public static ReadOnlyMemory<byte>` field.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="4e38a-107">Nové chování</span><span class="sxs-lookup"><span data-stu-id="4e38a-107">New behavior</span></span>

<span data-ttu-id="4e38a-108">`HandshakeProtocol.SuccessHandshakeData` byl nahrazen metodou `static` `GetSuccessfulHandshake(IHubProtocol protocol)`, která vrací `ReadOnlyMemory<byte>` na základě zadaného protokolu.</span><span class="sxs-lookup"><span data-stu-id="4e38a-108">`HandshakeProtocol.SuccessHandshakeData` has been replaced by a `static` `GetSuccessfulHandshake(IHubProtocol protocol)` method that returns a `ReadOnlyMemory<byte>` based on the specified protocol.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4e38a-109">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="4e38a-109">Reason for change</span></span>

<span data-ttu-id="4e38a-110">Do _odpovědi_ handshake byly přidány další pole, která nejsou konstantní a mění se v závislosti na vybraném protokolu.</span><span class="sxs-lookup"><span data-stu-id="4e38a-110">Additional fields were added to the handshake _response_ that are non-constant and change depending on the selected protocol.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4e38a-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="4e38a-111">Recommended action</span></span>

<span data-ttu-id="4e38a-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="4e38a-112">None.</span></span> <span data-ttu-id="4e38a-113">Tento typ není určený pro použití z uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="4e38a-113">This type isn't designed for use from user code.</span></span> <span data-ttu-id="4e38a-114">Je `public`, takže se dá sdílet mezi serverem a klientem signalizace.</span><span class="sxs-lookup"><span data-stu-id="4e38a-114">It's `public`, so it can be shared between the SignalR server and client.</span></span> <span data-ttu-id="4e38a-115">Můžou je používat i klienti návěstí zákazníka napsané v .NET.</span><span class="sxs-lookup"><span data-stu-id="4e38a-115">It may also be used by customer SignalR clients written in .NET.</span></span> <span data-ttu-id="4e38a-116">Tato změna by neměla mít vliv na **uživatele** signálu.</span><span class="sxs-lookup"><span data-stu-id="4e38a-116">**Users** of SignalR shouldn't be affected by this change.</span></span>

#### <a name="category"></a><span data-ttu-id="4e38a-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="4e38a-117">Category</span></span>

<span data-ttu-id="4e38a-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4e38a-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4e38a-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="4e38a-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
