---
ms.openlocfilehash: c4e7864262a11aafa4b7f1f4bdf632fbf084c560
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507074"
---
### <a name="http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced"></a>HTTP: typy Kestrel a IIS BadHttpRequestException označené jako zastaralé a nahrazené

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` a byly `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` označeny jako zastaralé a změnily se, aby byly odvozeny od `Microsoft.AspNetCore.Http.BadHttpRequestException` . Servery Kestrel a IIS stále vyvolávají své staré typy výjimek, aby se zajistila zpětná kompatibilita. Zastaralé typy budou v budoucí verzi odebrány.

Diskuzi najdete v tématu [dotnet/aspnetcore # 20614](https://github.com/dotnet/aspnetcore/issues/20614).

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 4

#### <a name="old-behavior"></a>Staré chování

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` a jsou `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` odvozeny z <xref:System.IO.IOException?displayProperty=nameWithType> .

#### <a name="new-behavior"></a>Nové chování

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` a `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` jsou zastaralé. Typy také jsou odvozeny z `Microsoft.AspNetCore.Http.BadHttpRequestException` , který je odvozen z `System.IO.IOException` .

#### <a name="reason-for-change"></a>Důvod změny

Tato změna byla provedena na:

* Konsolidujte duplicitní typy.
* Sjednocení chování napříč serverovými implementacemi.

Aplikace teď může zachytit základní výjimku `Microsoft.AspNetCore.Http.BadHttpRequestException` při použití Kestrel nebo IIS.

#### <a name="recommended-action"></a>Doporučená akce

Nahraďte použití `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` a `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` s `Microsoft.AspNetCore.Http.BadHttpRequestException` .

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- [Microsoft. AspNetCore. Server. IIS. BadHttpRequestException](/dotnet/api/microsoft.aspnetcore.server.iis.badhttprequestexception?view=aspnetcore-3.1)
- [Microsoft. AspNetCore. Server. Kestrel. BadHttpRequestException](/dotnet/api/microsoft.aspnetcore.server.kestrel.badhttprequestexception?view=aspnetcore-1.1)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Server.IIS.BadHttpRequestException`
- `T:Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`

-->
