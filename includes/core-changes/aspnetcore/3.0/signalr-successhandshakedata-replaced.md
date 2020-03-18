---
ms.openlocfilehash: 1d8bcaf68d44f27642048c1c207b52c55b604690
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901589"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a>SignalR: HandshakeProtocol.SuccessHandshakeData nahrazen

Pole [HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) bylo odebráno a nahrazeno pomocnou metodou, která generuje `IHubProtocol`úspěšnou odpověď handshake dané konkrétní .

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

`HandshakeProtocol.SuccessHandshakeData`bylo `public static ReadOnlyMemory<byte>` pole.

#### <a name="new-behavior"></a>Nové chování

`HandshakeProtocol.SuccessHandshakeData`byla nahrazena `static` `GetSuccessfulHandshake(IHubProtocol protocol)` metodou, která `ReadOnlyMemory<byte>` vrací na základě zadaného protokolu.

#### <a name="reason-for-change"></a>Důvod změny

Další pole byla přidána do _odpovědi_ handshake, které nejsou konstantní a mění se v závislosti na vybraném protokolu.

#### <a name="recommended-action"></a>Doporučená akce

Žádné. Tento typ není určen pro použití z uživatelského kódu. Je to `public`, takže může být sdílena mezi serverem SignalR a klientem. Může být také používán klienty signalr zákazníka napsanými v rozhraní .NET. **Uživatelé** SignalR by neměly být ovlivněny touto změnou.

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
