---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394109"
---
### <a name="logging-debuglogger-class-made-internal"></a>Protokolování: DebugLogger třída provedla interní

Před ASP.NET Core 3,0 byl modifikátor přístupu `DebugLogger` `public`. V ASP.NET Core 3,0 se modifikátor přístupu změnil na `internal`.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="reason-for-change"></a>Důvod změny

Změna je provedena na:

* Vyvynuťte konzistenci s jinými implementacemi protokolovacího nástroje, jako je například `ConsoleLogger`.
* Snižte plochu rozhraní API.

#### <a name="recommended-action"></a>Doporučená akce

K povolení protokolování ladění použijte metodu rozšíření <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder`. <xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> stále v případě, že je nutné zaregistrovat službu ručně, `public`.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
