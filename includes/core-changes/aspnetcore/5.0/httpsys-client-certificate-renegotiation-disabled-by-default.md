---
ms.openlocfilehash: 9a747d8fc15ca8fa2b915f89291f118d7344d172
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325251"
---
### <a name="httpsys-client-certificate-renegotiation-disabled-by-default"></a>HttpSys: nové vyjednávání klientského certifikátu je ve výchozím nastavení zakázané.

Možnost opětovného vyjednání připojení a vyžádání klientského certifikátu je ve výchozím nastavení zakázaná. Diskuzi najdete v tématu problém [dotnet/aspnetcore # 23181](https://github.com/dotnet/aspnetcore/issues/23181).

#### <a name="version-introduced"></a>Představená verze

ASP.NET Core 5,0

#### <a name="old-behavior"></a>Staré chování

Připojení se dá znovu vyjednávat pro vyžádání klientského certifikátu.

#### <a name="new-behavior"></a>Nové chování

Klientské certifikáty je možné požadovat jenom při počátečním handshaki připojení. Další informace najdete v tématu o žádosti o získání dat [dotnet/aspnetcore # 23162](https://github.com/dotnet/aspnetcore/pull/23162).

#### <a name="reason-for-change"></a>Důvod změny

Nové vyjednávání způsobilo několik problémů s výkonem a zablokování. V HTTP/2 to také není podporováno. Další kontext z toho, kdy se možnost řízení tohoto chování zavedla v ASP.NET Core 3,1, najdete v tématu problém [dotnet/aspnetcore # 14806](https://github.com/dotnet/aspnetcore/issues/14806).

#### <a name="recommended-action"></a>Doporučená akce

Aplikace, které vyžadují klientské certifikáty, by se měly *netsh.exe* použít k nastavení `clientcertnegotiation` Možnosti na `enabled` . Další informace najdete v tématu [příkazy netsh http](/windows-server/networking/technologies/netsh/netsh-http).

Pokud chcete, aby klientské certifikáty byly povolené jenom pro některé části vaší aplikace, přečtěte si pokyny v tématu [volitelné klientské certifikáty](/aspnet/core/security/authentication/certauth?view=aspnetcore-3.1#optional-client-certificates).

Pokud budete potřebovat původní chování redohadování, nastavte `HttpSysOptions.ClientCertificateMethod` na starou hodnotu `ClientCertificateMethod.AllowRenegotiate` . To se nedoporučuje z důvodů uvedených výše a v propojených pokynech.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate`
- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync`
- `Overload:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod`

-->
