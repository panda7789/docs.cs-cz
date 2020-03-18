---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394109"
---
### <a name="logging-debuglogger-class-made-internal"></a>Protokolování: Třída DebugLogger byla interní

Před ASP.NET Core 3.0 byl `DebugLogger` `public`modifikátor přístupu společnosti . V ASP.NET Core 3.0 se modifikátor přístupu změnil na `internal`.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="reason-for-change"></a>Důvod změny

Změna se provádí takto:

* Vynutit konzistenci s `ConsoleLogger`jinými implementacemi protokolování, jako je například .
* Zmenšete povrch rozhraní API.

#### <a name="recommended-action"></a>Doporučená akce

<xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` Pomocí metody rozšíření povolte protokolování ladění. <xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider>je také `public` stále v případě, že služba musí být registrována ručně.

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
