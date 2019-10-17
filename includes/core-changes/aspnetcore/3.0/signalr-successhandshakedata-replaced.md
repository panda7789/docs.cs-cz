---
ms.openlocfilehash: fa0f54404d1e14afa6ce48a425c984a48498a1ee
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394460"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a>Signál: HandshakeProtocol. SuccessHandshakeData nahrazeno

Pole [HandshakeProtocol. SuccessHandshakeData](https://github.com/aspnet/AspNetCore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) bylo odebráno a nahrazeno podpůrnou metodou, která generuje úspěšnou odpověď handshake s daným konkrétním `IHubProtocol`. 

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

`HandshakeProtocol.SuccessHandshakeData` bylo pole `public static ReadOnlyMemory<byte>`.

#### <a name="new-behavior"></a>Nové chování

`HandshakeProtocol.SuccessHandshakeData` byl nahrazen metodou `static` `GetSuccessfulHandshake(IHubProtocol protocol)`, která vrací `ReadOnlyMemory<byte>` na základě zadaného protokolu. 

#### <a name="reason-for-change"></a>Důvod změny

Do _odpovědi_ handshake byly přidány další pole, která nejsou konstantní a mění se v závislosti na vybraném protokolu.

#### <a name="recommended-action"></a>Doporučená akce

Žádné Tento typ není určený pro použití z uživatelského kódu. Je `public`, takže se dá sdílet mezi serverem a klientem signalizace. Můžou je používat i klienti návěstí zákazníka napsané v .NET. Tato změna by neměla mít vliv na **uživatele** signálu.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
