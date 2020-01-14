---
ms.openlocfilehash: eb3fa768a491f6c0ff4b15479beabd71b0670338
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937260"
---
### <a name="hosting-https-redirection-enabled-for-iis-out-of-process-apps"></a>Hostování: přesměrování protokolu HTTPS je povolené pro vnitroprocesové aplikace IIS.

13.0.19218.0 [modulu ASP.NET Core (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) pro hostování prostřednictvím služby IIS mimo procesy umožňuje existující funkci přesměrování HTTPS pro aplikace ASP.NET Core 3,0 a 2,2.

Diskuzi najdete v tématu [dotnet/AspNetCore # 15243](https://github.com/dotnet/AspNetCore/issues/15243).

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="old-behavior"></a>Staré chování

Šablona projektu ASP.NET Core 2,1 nejprve představila podporu middlewarových metod protokolu HTTPS, jako je <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> a <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>. Povolení přesměrování protokolu HTTPS vyžaduje přidání konfigurace, protože aplikace ve vývoji nepoužívají výchozí port 443. [HSTS (http Strict Transport Security)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) je aktivní jenom v případě, že požadavek už používá protokol HTTPS. Localhost je ve výchozím nastavení vynecháno.

#### <a name="new-behavior"></a>Nové chování

V ASP.NET Core 3,0 byl scénář služby IIS HTTPS [Vylepšený](https://github.com/dotnet/AspNetCore/pull/4685). Díky vylepšení může aplikace zjistit porty HTTPS serveru a ve výchozím nastavení nastavit `UseHttpsRedirection` fungování. Vnitroprocesové komponenta provedla zjišťování portů pomocí funkce `IServerAddresses`, která má vliv pouze na ASP.NET Core 3,0 aplikací, protože knihovna v procesu je označena verzí rozhraní. Součást mimo proces se změnila tak, aby automaticky přidala proměnnou prostředí `ASPNETCORE_HTTPS_PORT`. Tato změna ovlivnila aplikace ASP.NET Core 2,2 a 3,0, protože součást mimo proces je sdílena globálně. Aplikace ASP.NET Core 2,1 nejsou ovlivněné, protože ve výchozím nastavení používají předchozí verzi ANCM.

Předchozí chování bylo upraveno v ASP.NET Core 3.0.1 a 3.1.0 Preview 3 pro vrácení změn chování v ASP.NET Core 2. x. Tyto změny ovlivní pouze vnitroprocesové aplikace služby IIS.

Jak je uvedeno výše, instalace ASP.NET Core 3.0.0 měla vedlejší účinek také k aktivaci `UseHttpsRedirection` middlewaru v aplikacích ASP.NET Core 2. x. V ASP.NET Core 3.0.1 a 3.1.0 Preview 3 se provedla změna, takže jejich instalace už nemá vliv na ASP.NET Core 2. x aplikací. Proměnná prostředí `ASPNETCORE_HTTPS_PORT`, kterou ANCM naplněná v ASP.NET Core 3.0.0, se změnila na `ASPNETCORE_ANCM_HTTPS_PORT` v ASP.NET Core 3.0.1 a 3.1.0 Preview 3. `UseHttpsRedirection` se v těchto vydáních aktualizovala i pro pochopení nových i starých proměnných. ASP.NET Core 2. x se nebude aktualizovat. V důsledku toho se vrátí k předchozímu chování, které je ve výchozím nastavení zakázáno.

#### <a name="reason-for-change"></a>Důvod změny

Vylepšená funkce ASP.NET Core 3,0.

#### <a name="recommended-action"></a>Doporučená akce

Pokud chcete, aby všichni klienti používali protokol HTTPS, není nutná žádná akce. Pokud chcete některým klientům dovolit používat protokol HTTP, proveďte jeden z následujících kroků:

* Odeberte volání `UseHttpsRedirection` a `UseHsts` z `Startup.Configure` metody vašeho projektu a aplikaci znovu nasaďte.
* V souboru *Web. config* nastavte proměnnou prostředí `ASPNETCORE_HTTPS_PORT` na prázdný řetězec. Tato změna se může provádět přímo na serveru bez opětovného nasazení aplikace. Příklad:

    ```xml
    <aspNetCore processPath="dotnet" arguments=".\WebApplication3.dll" stdoutLogEnabled="false" stdoutLogFile="\\?\%home%\LogFiles\stdout" >
        <environmentVariables>
        <environmentVariable name="ASPNETCORE_HTTPS_PORT" value="" />
        </environmentVariables>
    </aspNetCore>
    ```

`UseHttpsRedirection` můžou pořád:

* Aktivováno ručně v ASP.NET Core 2. x nastavením proměnné prostředí `ASPNETCORE_HTTPS_PORT` na příslušné číslo portu (443 ve většině produkčních scénářů).
* Deaktivováno v ASP.NET Core 3. x definováním `ASPNETCORE_ANCM_HTTPS_PORT` s hodnotou prázdného řetězce. Tato hodnota je nastavena stejným způsobem jako v předchozím příkladu `ASPNETCORE_HTTPS_PORT`.

Počítače, na kterých běží ASP.NET Core aplikace 3.0.0, by před instalací ASP.NET Core 3.1.0 Preview 3 ANCM měli nainstalovat ASP.NET Core 3.0.1 runtime. Tím zajistíte, že `UseHttpsRedirection` nadále fungovat podle očekávání pro aplikace ASP.NET Core 3,0.

V Azure App Service se ANCM nasadí podle vlastního plánu z modulu runtime z důvodu jeho globální povahy. ANCM se ASP.NET Core po nasazení 3.0.1 a 3.1.0 do Azure nasadily s těmito změnami.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)`

-->
