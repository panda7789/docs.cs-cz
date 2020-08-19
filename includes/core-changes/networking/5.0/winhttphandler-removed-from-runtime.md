---
ms.openlocfilehash: 115cd6be935ae12a1293f948a0f899c6c3ff0d78
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608472"
---
### <a name="winhttphandler-removed-from-net-runtime"></a>WinHttpHandler odebrané z modulu runtime .NET

`WinHttpHandler`Třída byla odebrána z *System.Net.Http.dll* sestavení. Je teď dostupná jenom jako [balíček NuGet](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)pro vzdálenou správu (OOB).

#### <a name="version-introduced"></a>Představená verze

5.0

#### <a name="change-description"></a>Popis změny

V předchozích verzích .NET <xref:System.Net.Http.WinHttpHandler> je třída k dispozici jako součást základních knihoven .NET. Počínaje platformou .NET 5,0 <xref:System.Net.Http.WinHttpHandler> je třída k dispozici pouze jako samostatně instalovaný [balíček NuGet](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).

#### <a name="recommended-action"></a>Doporučená akce

Nainstalujte [balíček NuGet System .NET. http. WinHttpHandler](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/). Nebo pokud nepotřebujete funkce specifické pro službu WinHTTP, použijte <xref:System.Net.Http.SocketsHttpHandler> místo toho.

#### <a name="category"></a>Kategorie

Sítě

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Net.Http.WinHttpHandler?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Http.WinHttpHandler`

-->
