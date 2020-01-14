---
ms.openlocfilehash: eb3fa768a491f6c0ff4b15479beabd71b0670338
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937260"
---
### <a name="hosting-https-redirection-enabled-for-iis-out-of-process-apps"></a><span data-ttu-id="210eb-101">Hostování: přesměrování protokolu HTTPS je povolené pro vnitroprocesové aplikace IIS.</span><span class="sxs-lookup"><span data-stu-id="210eb-101">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>

<span data-ttu-id="210eb-102">13.0.19218.0 [modulu ASP.NET Core (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) pro hostování prostřednictvím služby IIS mimo procesy umožňuje existující funkci přesměrování HTTPS pro aplikace ASP.NET Core 3,0 a 2,2.</span><span class="sxs-lookup"><span data-stu-id="210eb-102">Version 13.0.19218.0 of the [ASP.NET Core Module (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) for hosting via IIS out-of-process enables an existing HTTPS redirection feature for ASP.NET Core 3.0 and 2.2 apps.</span></span>

<span data-ttu-id="210eb-103">Diskuzi najdete v tématu [dotnet/AspNetCore # 15243](https://github.com/dotnet/AspNetCore/issues/15243).</span><span class="sxs-lookup"><span data-stu-id="210eb-103">For discussion, see [dotnet/AspNetCore#15243](https://github.com/dotnet/AspNetCore/issues/15243).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="210eb-104">Představená verze</span><span class="sxs-lookup"><span data-stu-id="210eb-104">Version introduced</span></span>

<span data-ttu-id="210eb-105">3,0</span><span class="sxs-lookup"><span data-stu-id="210eb-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="210eb-106">Staré chování</span><span class="sxs-lookup"><span data-stu-id="210eb-106">Old behavior</span></span>

<span data-ttu-id="210eb-107">Šablona projektu ASP.NET Core 2,1 nejprve představila podporu middlewarových metod protokolu HTTPS, jako je <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> a <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>.</span><span class="sxs-lookup"><span data-stu-id="210eb-107">The ASP.NET Core 2.1 project template first introduced support for HTTPS middleware methods like <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> and <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>.</span></span> <span data-ttu-id="210eb-108">Povolení přesměrování protokolu HTTPS vyžaduje přidání konfigurace, protože aplikace ve vývoji nepoužívají výchozí port 443.</span><span class="sxs-lookup"><span data-stu-id="210eb-108">Enabling HTTPS redirection required the addition of configuration, since apps in development don't use the default port of 443.</span></span> <span data-ttu-id="210eb-109">[HSTS (http Strict Transport Security)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) je aktivní jenom v případě, že požadavek už používá protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="210eb-109">[HTTP Strict Transport Security (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) is active only if the request is already using HTTPS.</span></span> <span data-ttu-id="210eb-110">Localhost je ve výchozím nastavení vynecháno.</span><span class="sxs-lookup"><span data-stu-id="210eb-110">Localhost is skipped by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="210eb-111">Nové chování</span><span class="sxs-lookup"><span data-stu-id="210eb-111">New behavior</span></span>

<span data-ttu-id="210eb-112">V ASP.NET Core 3,0 byl scénář služby IIS HTTPS [Vylepšený](https://github.com/dotnet/AspNetCore/pull/4685).</span><span class="sxs-lookup"><span data-stu-id="210eb-112">In ASP.NET Core 3.0, the IIS HTTPS scenario was [enhanced](https://github.com/dotnet/AspNetCore/pull/4685).</span></span> <span data-ttu-id="210eb-113">Díky vylepšení může aplikace zjistit porty HTTPS serveru a ve výchozím nastavení nastavit `UseHttpsRedirection` fungování.</span><span class="sxs-lookup"><span data-stu-id="210eb-113">With the enhancement, an app could discover the server's HTTPS ports and make `UseHttpsRedirection` work by default.</span></span> <span data-ttu-id="210eb-114">Vnitroprocesové komponenta provedla zjišťování portů pomocí funkce `IServerAddresses`, která má vliv pouze na ASP.NET Core 3,0 aplikací, protože knihovna v procesu je označena verzí rozhraní.</span><span class="sxs-lookup"><span data-stu-id="210eb-114">The in-process component accomplished port discovery with the `IServerAddresses` feature, which only affects ASP.NET Core 3.0 apps because the in-process library is versioned with the framework.</span></span> <span data-ttu-id="210eb-115">Součást mimo proces se změnila tak, aby automaticky přidala proměnnou prostředí `ASPNETCORE_HTTPS_PORT`.</span><span class="sxs-lookup"><span data-stu-id="210eb-115">The out-of-process component changed to automatically add the `ASPNETCORE_HTTPS_PORT` environment variable.</span></span> <span data-ttu-id="210eb-116">Tato změna ovlivnila aplikace ASP.NET Core 2,2 a 3,0, protože součást mimo proces je sdílena globálně.</span><span class="sxs-lookup"><span data-stu-id="210eb-116">This change affected both ASP.NET Core 2.2 and 3.0 apps because the out-of-process component is shared globally.</span></span> <span data-ttu-id="210eb-117">Aplikace ASP.NET Core 2,1 nejsou ovlivněné, protože ve výchozím nastavení používají předchozí verzi ANCM.</span><span class="sxs-lookup"><span data-stu-id="210eb-117">ASP.NET Core 2.1 apps aren't affected because they use a prior version of ANCM by default.</span></span>

<span data-ttu-id="210eb-118">Předchozí chování bylo upraveno v ASP.NET Core 3.0.1 a 3.1.0 Preview 3 pro vrácení změn chování v ASP.NET Core 2. x.</span><span class="sxs-lookup"><span data-stu-id="210eb-118">The preceding behavior was modified in ASP.NET Core 3.0.1 and 3.1.0 Preview 3 to reverse the behavior changes in ASP.NET Core 2.x.</span></span> <span data-ttu-id="210eb-119">Tyto změny ovlivní pouze vnitroprocesové aplikace služby IIS.</span><span class="sxs-lookup"><span data-stu-id="210eb-119">These changes only affect IIS out-of-process apps.</span></span>

<span data-ttu-id="210eb-120">Jak je uvedeno výše, instalace ASP.NET Core 3.0.0 měla vedlejší účinek také k aktivaci `UseHttpsRedirection` middlewaru v aplikacích ASP.NET Core 2. x.</span><span class="sxs-lookup"><span data-stu-id="210eb-120">As detailed above, installing ASP.NET Core 3.0.0 had the side effect of also activating the `UseHttpsRedirection` middleware in ASP.NET Core 2.x apps.</span></span> <span data-ttu-id="210eb-121">V ASP.NET Core 3.0.1 a 3.1.0 Preview 3 se provedla změna, takže jejich instalace už nemá vliv na ASP.NET Core 2. x aplikací.</span><span class="sxs-lookup"><span data-stu-id="210eb-121">A change was made to ANCM in ASP.NET Core 3.0.1 and 3.1.0 Preview 3 such that installing them no longer has this effect on ASP.NET Core 2.x apps.</span></span> <span data-ttu-id="210eb-122">Proměnná prostředí `ASPNETCORE_HTTPS_PORT`, kterou ANCM naplněná v ASP.NET Core 3.0.0, se změnila na `ASPNETCORE_ANCM_HTTPS_PORT` v ASP.NET Core 3.0.1 a 3.1.0 Preview 3.</span><span class="sxs-lookup"><span data-stu-id="210eb-122">The `ASPNETCORE_HTTPS_PORT` environment variable that ANCM populated in ASP.NET Core 3.0.0 was changed to `ASPNETCORE_ANCM_HTTPS_PORT` in ASP.NET Core 3.0.1 and 3.1.0 Preview 3.</span></span> <span data-ttu-id="210eb-123">`UseHttpsRedirection` se v těchto vydáních aktualizovala i pro pochopení nových i starých proměnných.</span><span class="sxs-lookup"><span data-stu-id="210eb-123">`UseHttpsRedirection` was also updated in these releases to understand both the new and old variables.</span></span> <span data-ttu-id="210eb-124">ASP.NET Core 2. x se nebude aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="210eb-124">ASP.NET Core 2.x won't be updated.</span></span> <span data-ttu-id="210eb-125">V důsledku toho se vrátí k předchozímu chování, které je ve výchozím nastavení zakázáno.</span><span class="sxs-lookup"><span data-stu-id="210eb-125">As a result, it reverts to the previous behavior of being disabled by default.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="210eb-126">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="210eb-126">Reason for change</span></span>

<span data-ttu-id="210eb-127">Vylepšená funkce ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="210eb-127">Improved ASP.NET Core 3.0 functionality.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="210eb-128">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="210eb-128">Recommended action</span></span>

<span data-ttu-id="210eb-129">Pokud chcete, aby všichni klienti používali protokol HTTPS, není nutná žádná akce.</span><span class="sxs-lookup"><span data-stu-id="210eb-129">No action is required if you want all clients to use HTTPS.</span></span> <span data-ttu-id="210eb-130">Pokud chcete některým klientům dovolit používat protokol HTTP, proveďte jeden z následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="210eb-130">To allow some clients to use HTTP, take one of the following steps:</span></span>

* <span data-ttu-id="210eb-131">Odeberte volání `UseHttpsRedirection` a `UseHsts` z `Startup.Configure` metody vašeho projektu a aplikaci znovu nasaďte.</span><span class="sxs-lookup"><span data-stu-id="210eb-131">Remove the calls to `UseHttpsRedirection` and `UseHsts` from your project's `Startup.Configure` method, and redeploy the app.</span></span>
* <span data-ttu-id="210eb-132">V souboru *Web. config* nastavte proměnnou prostředí `ASPNETCORE_HTTPS_PORT` na prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="210eb-132">In your *web.config* file, set the `ASPNETCORE_HTTPS_PORT` environment variable to an empty string.</span></span> <span data-ttu-id="210eb-133">Tato změna se může provádět přímo na serveru bez opětovného nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="210eb-133">This change can occur directly on the server without redeploying the app.</span></span> <span data-ttu-id="210eb-134">Příklad:</span><span class="sxs-lookup"><span data-stu-id="210eb-134">For example:</span></span>

    ```xml
    <aspNetCore processPath="dotnet" arguments=".\WebApplication3.dll" stdoutLogEnabled="false" stdoutLogFile="\\?\%home%\LogFiles\stdout" >
        <environmentVariables>
        <environmentVariable name="ASPNETCORE_HTTPS_PORT" value="" />
        </environmentVariables>
    </aspNetCore>
    ```

<span data-ttu-id="210eb-135">`UseHttpsRedirection` můžou pořád:</span><span class="sxs-lookup"><span data-stu-id="210eb-135">`UseHttpsRedirection` can still be:</span></span>

* <span data-ttu-id="210eb-136">Aktivováno ručně v ASP.NET Core 2. x nastavením proměnné prostředí `ASPNETCORE_HTTPS_PORT` na příslušné číslo portu (443 ve většině produkčních scénářů).</span><span class="sxs-lookup"><span data-stu-id="210eb-136">Activated manually in ASP.NET Core 2.x by setting the `ASPNETCORE_HTTPS_PORT` environment variable to the appropriate port number (443 in most production scenarios).</span></span>
* <span data-ttu-id="210eb-137">Deaktivováno v ASP.NET Core 3. x definováním `ASPNETCORE_ANCM_HTTPS_PORT` s hodnotou prázdného řetězce.</span><span class="sxs-lookup"><span data-stu-id="210eb-137">Deactivated in ASP.NET Core 3.x by defining `ASPNETCORE_ANCM_HTTPS_PORT` with an empty string value.</span></span> <span data-ttu-id="210eb-138">Tato hodnota je nastavena stejným způsobem jako v předchozím příkladu `ASPNETCORE_HTTPS_PORT`.</span><span class="sxs-lookup"><span data-stu-id="210eb-138">This value is set in the same fashion as the preceding `ASPNETCORE_HTTPS_PORT` example.</span></span>

<span data-ttu-id="210eb-139">Počítače, na kterých běží ASP.NET Core aplikace 3.0.0, by před instalací ASP.NET Core 3.1.0 Preview 3 ANCM měli nainstalovat ASP.NET Core 3.0.1 runtime.</span><span class="sxs-lookup"><span data-stu-id="210eb-139">Machines running ASP.NET Core 3.0.0 apps should install the ASP.NET Core 3.0.1 runtime before installing the ASP.NET Core 3.1.0 Preview 3 ANCM.</span></span> <span data-ttu-id="210eb-140">Tím zajistíte, že `UseHttpsRedirection` nadále fungovat podle očekávání pro aplikace ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="210eb-140">Doing so ensures that `UseHttpsRedirection` continues to operate as expected for the ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="210eb-141">V Azure App Service se ANCM nasadí podle vlastního plánu z modulu runtime z důvodu jeho globální povahy.</span><span class="sxs-lookup"><span data-stu-id="210eb-141">In Azure App Service, ANCM deploys on a separate schedule from the runtime because of its global nature.</span></span> <span data-ttu-id="210eb-142">ANCM se ASP.NET Core po nasazení 3.0.1 a 3.1.0 do Azure nasadily s těmito změnami.</span><span class="sxs-lookup"><span data-stu-id="210eb-142">ANCM was deployed to Azure with these changes after ASP.NET Core 3.0.1 and 3.1.0 were deployed.</span></span>

#### <a name="category"></a><span data-ttu-id="210eb-143">Kategorie</span><span class="sxs-lookup"><span data-stu-id="210eb-143">Category</span></span>

<span data-ttu-id="210eb-144">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="210eb-144">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="210eb-145">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="210eb-145">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)`

-->
