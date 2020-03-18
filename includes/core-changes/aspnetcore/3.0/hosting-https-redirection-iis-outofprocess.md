---
ms.openlocfilehash: eb3fa768a491f6c0ff4b15479beabd71b0670338
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937260"
---
### <a name="hosting-https-redirection-enabled-for-iis-out-of-process-apps"></a>Hostování: Přesměrování HTTPS povoleno pro mimoprocesové aplikace služby IIS

Verze 13.0.19218.0 [ASP.NET core modulu (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) pro hostování přes mimoproces služby IIS umožňuje stávající funkci přesměrování HTTPS pro aplikace ASP.NET core 3.0 a 2.2.

Diskuse naleznete [v tématu dotnet/AspNetCore#15243](https://github.com/dotnet/AspNetCore/issues/15243).

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Šablona projektu ASP.NET Core 2.1 poprvé zavedla <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>podporu pro metody middlewaru HTTPS, jako je a . Povolení přesměrování HTTPS vyžadovalo přidání konfigurace, protože aplikace ve vývoji nepoužívají výchozí port 443. [HTTP Strict Transport Security (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) je aktivní pouze v případě, že požadavek již používá protokol HTTPS. Localhost je ve výchozím nastavení přeskočen.

#### <a name="new-behavior"></a>Nové chování

V ASP.NET jádrem 3.0 byl [vylepšen](https://github.com/dotnet/AspNetCore/pull/4685)scénář protokolu HTTPS protokolu IIS . S vylepšením může aplikace zjistit porty HTTPS `UseHttpsRedirection` serveru a ve výchozím nastavení pracovat. Komponenta v procesu provádí zjišťování `IServerAddresses` portů s funkcí, která ovlivňuje pouze ASP.NET aplikací Core 3.0, protože knihovna v procesu je verzí s architekturou. Součást mimo proces se změnila tak, `ASPNETCORE_HTTPS_PORT` aby automaticky přidávala proměnnou prostředí. Tato změna ovlivnila aplikace ASP.NET Core 2.2 i 3.0, protože součást mimo proces je sdílena globálně. ASP.NET aplikace Core 2.1 nejsou ovlivněny, protože ve výchozím nastavení používají předchozí verzi ANCM.

Předchozí chování bylo upraveno v ASP.NET Core 3.0.1 a 3.1.0 Náhled 3 zvrátit změny chování v ASP.NET Core 2.x. Tyto změny ovlivní pouze mimoprocesové aplikace služby IIS.

Jak je podrobně popsáno výše, instalace ASP.NET Core 3.0.0 měla vedlejší účinek také aktivace `UseHttpsRedirection` middleware v ASP.NET aplikací core 2.x. V ASP.NET Core 3.0.1 a 3.1.0 Preview 3 byla provedena změna, takže jejich instalace již nemá tento vliv na aplikace ASP.NET Core 2.x. Proměnná `ASPNETCORE_HTTPS_PORT` prostředí, kterou ANCM osazena v `ASPNETCORE_ANCM_HTTPS_PORT` ASP.NET Core 3.0.0 byl změněn v ASP.NET Core 3.0.1 a 3.1.0 Náhled 3. `UseHttpsRedirection`byl také aktualizován v těchto verzích pochopit nové i staré proměnné. ASP.NET Core 2.x nebude aktualizován. V důsledku toho se vrátí k předchozí chování je zakázáno ve výchozím nastavení.

#### <a name="reason-for-change"></a>Důvod změny

Vylepšená ASP.NET core 3.0 funkce.

#### <a name="recommended-action"></a>Doporučená akce

Pokud chcete, aby všichni klienti používali protokol HTTPS, není vyžadována žádná akce. Chcete-li některým klientům povolit používání protokolu HTTP, postupujte jedním z následujících kroků:

* Odeberte `UseHttpsRedirection` volání `UseHsts` do a `Startup.Configure` z metody projektu a znovu nasadit aplikaci.
* V souboru *web.config* `ASPNETCORE_HTTPS_PORT` nastavte proměnnou prostředí na prázdný řetězec. K této změně může dojít přímo na serveru bez opětovného nasazení aplikace. Například:

    ```xml
    <aspNetCore processPath="dotnet" arguments=".\WebApplication3.dll" stdoutLogEnabled="false" stdoutLogFile="\\?\%home%\LogFiles\stdout" >
        <environmentVariables>
        <environmentVariable name="ASPNETCORE_HTTPS_PORT" value="" />
        </environmentVariables>
    </aspNetCore>
    ```

`UseHttpsRedirection`může být stále:

* Aktivuje se ručně v ASP.NET Core `ASPNETCORE_HTTPS_PORT` 2.x nastavením proměnné prostředí na příslušné číslo portu (443 ve většině produkčních scénářů).
* Deaktivován v ASP.NET Core 3.x definováním `ASPNETCORE_ANCM_HTTPS_PORT` s prázdnou hodnotou řetězce. Tato hodnota je nastavena stejným způsobem `ASPNETCORE_HTTPS_PORT` jako předchozí příklad.

Počítače se systémem ASP.NET aplikací Core 3.0.0 by měl ASP.NETy před instalací ASP.NET Core 3.1.0 Preview 3 ANCM nainstalovat core 3.0.1. Tím zajistíte, `UseHttpsRedirection` že bude fungovat podle očekávání pro ASP.NET aplikace Core 3.0.

Ve službě Azure App Service ANCM nasazuje na samostatný plán od běhu z důvodu jeho globální povahy. ANCM byl nasazen do Azure s těmito změnami po nasazení ASP.NET Core 3.0.1 a 3.1.0.

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)`

-->
