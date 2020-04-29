---
ms.openlocfilehash: d7a93cb539baee6a70f75d3afe52fd7546ac2399
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507073"
---
### <a name="extensions-package-reference-changes-affecting-some-nuget-packages"></a>Rozšíření: změny odkazů balíčku ovlivňují některé balíčky NuGet

S migrací `Microsoft.Extensions.*` některých balíčků NuGet z úložiště [dotnet/Extensions](https://github.com/dotnet/extensions) do [dotnet/runtime](https://github.com/dotnet/runtime), jak je popsáno v tématu [ASPNET/oznámení # 411](https://github.com/aspnet/Announcements/issues/411), se změny balení aplikují na některé migrované balíčky. Diskuzi o tomto problému najdete v tématu [dotnet/aspnetcore # 21033](https://github.com/dotnet/aspnetcore/issues/21033).

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 4

#### <a name="old-behavior"></a>Staré chování

Některé `Microsoft.Extensions.*` balíčky zahrnovaly odkazy na balíčky pro rozhraní API, na kterých se vaše aplikace spoléhala.

#### <a name="new-behavior"></a>Nové chování

Vaše aplikace může muset přidat `Microsoft.Extensions.*` závislosti balíčků.

#### <a name="reason-for-change"></a>Důvod změny

Zásady balení byly aktualizovány pro lepší zarovnání s úložištěm *dotnet/runtime* . V rámci nové zásady se nepoužité odkazy na balíčky během balení odeberou ze souborů *. nupkg* .

#### <a name="recommended-action"></a>Doporučená akce

Uživatelé ovlivněných balíčků by měli přidat přímou závislost na odebrané závislosti balíčku ve svém projektu, pokud se používají rozhraní API ze odebrané závislosti balíčku. V následující tabulce jsou uvedeny ovlivněné balíčky a příslušné změny.

|Název balíčku|Popis změny|
|------------|------------------|
|[Microsoft. Extensions. Configuration. Binder](https://nuget.org/packages/Microsoft.Extensions.Configuration.Binder)|Odebraný odkaz na`Microsoft.Extensions.Configuration`|
|[Microsoft. Extensions. Configuration. JSON](https://nuget.org/packages/Microsoft.Extensions.Configuration.Json)    |Odebraný odkaz na`System.Threading.Tasks.Extensions`|
|[Microsoft. Extensions. Hosting. abstrakce](https://nuget.org/packages/Microsoft.Extensions.Hosting.Abstractions)|Odebraný odkaz na`Microsoft.Extensions.Logging.Abstractions`|
|[Microsoft. Extensions. Logging](https://nuget.org/packages/Microsoft.Extensions.Logging)                          |Odebraný odkaz na`Microsoft.Extensions.Configuration.Binder`|
|[Microsoft. Extensions. Logging. Console](https://nuget.org/packages/Microsoft.Extensions.Logging.Console)          |Odebraný odkaz na`Microsoft.Extensions.Configuration.Abstractions`|
|[Microsoft. Extensions. Logging. EventLog](https://nuget.org/packages/Microsoft.Extensions.Logging.EventLog)        |Odebral se odkaz `System.Diagnostics.EventLog` na pro zástupný název cílového rozhraní .NET Framework 4.6.1.|
|[Microsoft. Extensions. Logging. EventSource](https://nuget.org/packages/Microsoft.Extensions.Logging.EventSource)  |Odebraný odkaz na`System.Threading.Tasks.Extensions`|
|[Microsoft. Extensions. Options](https://nuget.org/packages/Microsoft.Extensions.Options)                          |Odebraný odkaz na`System.ComponentModel.Annotations`|

Například odkaz na balíček, který `Microsoft.Extensions.Configuration` byl odebrán z. `Microsoft.Extensions.Configuration.Binder` V balíčku se nepoužilo žádné rozhraní API ze závislostí. Uživatelé `Microsoft.Extensions.Configuration.Binder` , kteří závisejí na rozhraních `Microsoft.Extensions.Configuration` API z, by měli do svého projektu přidat přímý odkaz.

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádná

<!--

#### Affected APIs

Not detectable via API analysis

-->
