---
ms.openlocfilehash: 1d8bcaf68d44f27642048c1c207b52c55b604690
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901589"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a>Signál: HandshakeProtocol. SuccessHandshakeData nahrazeno

Pole [HandshakeProtocol. SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) se odebralo a nahradilo pomocnou metodou, která generuje úspěšnou odpověď handshake pro konkrétní `IHubProtocol`.

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="old-behavior"></a>Staré chování

`HandshakeProtocol.SuccessHandshakeData` bylo `public static ReadOnlyMemory<byte>` poli.

#### <a name="new-behavior"></a>Nové chování

`HandshakeProtocol.SuccessHandshakeData` byl nahrazen metodou `static` `GetSuccessfulHandshake(IHubProtocol protocol)`, která vrací `ReadOnlyMemory<byte>` na základě zadaného protokolu.

#### <a name="reason-for-change"></a>Důvod změny

Do _odpovědi_ handshake byly přidány další pole, která nejsou konstantní a mění se v závislosti na vybraném protokolu.

#### <a name="recommended-action"></a>Doporučená akce

Žádné Tento typ není určený pro použití z uživatelského kódu. Je `public`, aby bylo možné je sdílet mezi serverem a klientem signalizace. Můžou je používat i klienti návěstí zákazníka napsané v .NET. Tato změna by neměla mít vliv na **uživatele** signálu.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
