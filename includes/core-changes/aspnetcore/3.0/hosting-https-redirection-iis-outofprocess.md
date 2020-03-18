---
ms.openlocfilehash: eb3fa768a491f6c0ff4b15479beabd71b0670338
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937260"
---
### <a name="hosting-https-redirection-enabled-for-iis-out-of-process-apps"></a><span data-ttu-id="cf668-101">Hostování: Přesměrování HTTPS povoleno pro mimoprocesové aplikace služby IIS</span><span class="sxs-lookup"><span data-stu-id="cf668-101">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>

<span data-ttu-id="cf668-102">Verze 13.0.19218.0 [ASP.NET core modulu (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) pro hostování přes mimoproces služby IIS umožňuje stávající funkci přesměrování HTTPS pro aplikace ASP.NET core 3.0 a 2.2.</span><span class="sxs-lookup"><span data-stu-id="cf668-102">Version 13.0.19218.0 of the [ASP.NET Core Module (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) for hosting via IIS out-of-process enables an existing HTTPS redirection feature for ASP.NET Core 3.0 and 2.2 apps.</span></span>

<span data-ttu-id="cf668-103">Diskuse naleznete [v tématu dotnet/AspNetCore#15243](https://github.com/dotnet/AspNetCore/issues/15243).</span><span class="sxs-lookup"><span data-stu-id="cf668-103">For discussion, see [dotnet/AspNetCore#15243](https://github.com/dotnet/AspNetCore/issues/15243).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cf668-104">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="cf668-104">Version introduced</span></span>

<span data-ttu-id="cf668-105">3.0</span><span class="sxs-lookup"><span data-stu-id="cf668-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="cf668-106">Staré chování</span><span class="sxs-lookup"><span data-stu-id="cf668-106">Old behavior</span></span>

<span data-ttu-id="cf668-107">Šablona projektu ASP.NET Core 2.1 poprvé zavedla <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>podporu pro metody middlewaru HTTPS, jako je a .</span><span class="sxs-lookup"><span data-stu-id="cf668-107">The ASP.NET Core 2.1 project template first introduced support for HTTPS middleware methods like <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> and <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>.</span></span> <span data-ttu-id="cf668-108">Povolení přesměrování HTTPS vyžadovalo přidání konfigurace, protože aplikace ve vývoji nepoužívají výchozí port 443.</span><span class="sxs-lookup"><span data-stu-id="cf668-108">Enabling HTTPS redirection required the addition of configuration, since apps in development don't use the default port of 443.</span></span> <span data-ttu-id="cf668-109">[HTTP Strict Transport Security (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) je aktivní pouze v případě, že požadavek již používá protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="cf668-109">[HTTP Strict Transport Security (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) is active only if the request is already using HTTPS.</span></span> <span data-ttu-id="cf668-110">Localhost je ve výchozím nastavení přeskočen.</span><span class="sxs-lookup"><span data-stu-id="cf668-110">Localhost is skipped by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="cf668-111">Nové chování</span><span class="sxs-lookup"><span data-stu-id="cf668-111">New behavior</span></span>

<span data-ttu-id="cf668-112">V ASP.NET jádrem 3.0 byl [vylepšen](https://github.com/dotnet/AspNetCore/pull/4685)scénář protokolu HTTPS protokolu IIS .</span><span class="sxs-lookup"><span data-stu-id="cf668-112">In ASP.NET Core 3.0, the IIS HTTPS scenario was [enhanced](https://github.com/dotnet/AspNetCore/pull/4685).</span></span> <span data-ttu-id="cf668-113">S vylepšením může aplikace zjistit porty HTTPS `UseHttpsRedirection` serveru a ve výchozím nastavení pracovat.</span><span class="sxs-lookup"><span data-stu-id="cf668-113">With the enhancement, an app could discover the server's HTTPS ports and make `UseHttpsRedirection` work by default.</span></span> <span data-ttu-id="cf668-114">Komponenta v procesu provádí zjišťování `IServerAddresses` portů s funkcí, která ovlivňuje pouze ASP.NET aplikací Core 3.0, protože knihovna v procesu je verzí s architekturou.</span><span class="sxs-lookup"><span data-stu-id="cf668-114">The in-process component accomplished port discovery with the `IServerAddresses` feature, which only affects ASP.NET Core 3.0 apps because the in-process library is versioned with the framework.</span></span> <span data-ttu-id="cf668-115">Součást mimo proces se změnila tak, `ASPNETCORE_HTTPS_PORT` aby automaticky přidávala proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="cf668-115">The out-of-process component changed to automatically add the `ASPNETCORE_HTTPS_PORT` environment variable.</span></span> <span data-ttu-id="cf668-116">Tato změna ovlivnila aplikace ASP.NET Core 2.2 i 3.0, protože součást mimo proces je sdílena globálně.</span><span class="sxs-lookup"><span data-stu-id="cf668-116">This change affected both ASP.NET Core 2.2 and 3.0 apps because the out-of-process component is shared globally.</span></span> <span data-ttu-id="cf668-117">ASP.NET aplikace Core 2.1 nejsou ovlivněny, protože ve výchozím nastavení používají předchozí verzi ANCM.</span><span class="sxs-lookup"><span data-stu-id="cf668-117">ASP.NET Core 2.1 apps aren't affected because they use a prior version of ANCM by default.</span></span>

<span data-ttu-id="cf668-118">Předchozí chování bylo upraveno v ASP.NET Core 3.0.1 a 3.1.0 Náhled 3 zvrátit změny chování v ASP.NET Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="cf668-118">The preceding behavior was modified in ASP.NET Core 3.0.1 and 3.1.0 Preview 3 to reverse the behavior changes in ASP.NET Core 2.x.</span></span> <span data-ttu-id="cf668-119">Tyto změny ovlivní pouze mimoprocesové aplikace služby IIS.</span><span class="sxs-lookup"><span data-stu-id="cf668-119">These changes only affect IIS out-of-process apps.</span></span>

<span data-ttu-id="cf668-120">Jak je podrobně popsáno výše, instalace ASP.NET Core 3.0.0 měla vedlejší účinek také aktivace `UseHttpsRedirection` middleware v ASP.NET aplikací core 2.x.</span><span class="sxs-lookup"><span data-stu-id="cf668-120">As detailed above, installing ASP.NET Core 3.0.0 had the side effect of also activating the `UseHttpsRedirection` middleware in ASP.NET Core 2.x apps.</span></span> <span data-ttu-id="cf668-121">V ASP.NET Core 3.0.1 a 3.1.0 Preview 3 byla provedena změna, takže jejich instalace již nemá tento vliv na aplikace ASP.NET Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="cf668-121">A change was made to ANCM in ASP.NET Core 3.0.1 and 3.1.0 Preview 3 such that installing them no longer has this effect on ASP.NET Core 2.x apps.</span></span> <span data-ttu-id="cf668-122">Proměnná `ASPNETCORE_HTTPS_PORT` prostředí, kterou ANCM osazena v `ASPNETCORE_ANCM_HTTPS_PORT` ASP.NET Core 3.0.0 byl změněn v ASP.NET Core 3.0.1 a 3.1.0 Náhled 3.</span><span class="sxs-lookup"><span data-stu-id="cf668-122">The `ASPNETCORE_HTTPS_PORT` environment variable that ANCM populated in ASP.NET Core 3.0.0 was changed to `ASPNETCORE_ANCM_HTTPS_PORT` in ASP.NET Core 3.0.1 and 3.1.0 Preview 3.</span></span> <span data-ttu-id="cf668-123">`UseHttpsRedirection`byl také aktualizován v těchto verzích pochopit nové i staré proměnné.</span><span class="sxs-lookup"><span data-stu-id="cf668-123">`UseHttpsRedirection` was also updated in these releases to understand both the new and old variables.</span></span> <span data-ttu-id="cf668-124">ASP.NET Core 2.x nebude aktualizován.</span><span class="sxs-lookup"><span data-stu-id="cf668-124">ASP.NET Core 2.x won't be updated.</span></span> <span data-ttu-id="cf668-125">V důsledku toho se vrátí k předchozí chování je zakázáno ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="cf668-125">As a result, it reverts to the previous behavior of being disabled by default.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="cf668-126">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="cf668-126">Reason for change</span></span>

<span data-ttu-id="cf668-127">Vylepšená ASP.NET core 3.0 funkce.</span><span class="sxs-lookup"><span data-stu-id="cf668-127">Improved ASP.NET Core 3.0 functionality.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cf668-128">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="cf668-128">Recommended action</span></span>

<span data-ttu-id="cf668-129">Pokud chcete, aby všichni klienti používali protokol HTTPS, není vyžadována žádná akce.</span><span class="sxs-lookup"><span data-stu-id="cf668-129">No action is required if you want all clients to use HTTPS.</span></span> <span data-ttu-id="cf668-130">Chcete-li některým klientům povolit používání protokolu HTTP, postupujte jedním z následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="cf668-130">To allow some clients to use HTTP, take one of the following steps:</span></span>

* <span data-ttu-id="cf668-131">Odeberte `UseHttpsRedirection` volání `UseHsts` do a `Startup.Configure` z metody projektu a znovu nasadit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cf668-131">Remove the calls to `UseHttpsRedirection` and `UseHsts` from your project's `Startup.Configure` method, and redeploy the app.</span></span>
* <span data-ttu-id="cf668-132">V souboru *web.config* `ASPNETCORE_HTTPS_PORT` nastavte proměnnou prostředí na prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="cf668-132">In your *web.config* file, set the `ASPNETCORE_HTTPS_PORT` environment variable to an empty string.</span></span> <span data-ttu-id="cf668-133">K této změně může dojít přímo na serveru bez opětovného nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="cf668-133">This change can occur directly on the server without redeploying the app.</span></span> <span data-ttu-id="cf668-134">Například:</span><span class="sxs-lookup"><span data-stu-id="cf668-134">For example:</span></span>

    ```xml
    <aspNetCore processPath="dotnet" arguments=".\WebApplication3.dll" stdoutLogEnabled="false" stdoutLogFile="\\?\%home%\LogFiles\stdout" >
        <environmentVariables>
        <environmentVariable name="ASPNETCORE_HTTPS_PORT" value="" />
        </environmentVariables>
    </aspNetCore>
    ```

<span data-ttu-id="cf668-135">`UseHttpsRedirection`může být stále:</span><span class="sxs-lookup"><span data-stu-id="cf668-135">`UseHttpsRedirection` can still be:</span></span>

* <span data-ttu-id="cf668-136">Aktivuje se ručně v ASP.NET Core `ASPNETCORE_HTTPS_PORT` 2.x nastavením proměnné prostředí na příslušné číslo portu (443 ve většině produkčních scénářů).</span><span class="sxs-lookup"><span data-stu-id="cf668-136">Activated manually in ASP.NET Core 2.x by setting the `ASPNETCORE_HTTPS_PORT` environment variable to the appropriate port number (443 in most production scenarios).</span></span>
* <span data-ttu-id="cf668-137">Deaktivován v ASP.NET Core 3.x definováním `ASPNETCORE_ANCM_HTTPS_PORT` s prázdnou hodnotou řetězce.</span><span class="sxs-lookup"><span data-stu-id="cf668-137">Deactivated in ASP.NET Core 3.x by defining `ASPNETCORE_ANCM_HTTPS_PORT` with an empty string value.</span></span> <span data-ttu-id="cf668-138">Tato hodnota je nastavena stejným způsobem `ASPNETCORE_HTTPS_PORT` jako předchozí příklad.</span><span class="sxs-lookup"><span data-stu-id="cf668-138">This value is set in the same fashion as the preceding `ASPNETCORE_HTTPS_PORT` example.</span></span>

<span data-ttu-id="cf668-139">Počítače se systémem ASP.NET aplikací Core 3.0.0 by měl ASP.NETy před instalací ASP.NET Core 3.1.0 Preview 3 ANCM nainstalovat core 3.0.1.</span><span class="sxs-lookup"><span data-stu-id="cf668-139">Machines running ASP.NET Core 3.0.0 apps should install the ASP.NET Core 3.0.1 runtime before installing the ASP.NET Core 3.1.0 Preview 3 ANCM.</span></span> <span data-ttu-id="cf668-140">Tím zajistíte, `UseHttpsRedirection` že bude fungovat podle očekávání pro ASP.NET aplikace Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="cf668-140">Doing so ensures that `UseHttpsRedirection` continues to operate as expected for the ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="cf668-141">Ve službě Azure App Service ANCM nasazuje na samostatný plán od běhu z důvodu jeho globální povahy.</span><span class="sxs-lookup"><span data-stu-id="cf668-141">In Azure App Service, ANCM deploys on a separate schedule from the runtime because of its global nature.</span></span> <span data-ttu-id="cf668-142">ANCM byl nasazen do Azure s těmito změnami po nasazení ASP.NET Core 3.0.1 a 3.1.0.</span><span class="sxs-lookup"><span data-stu-id="cf668-142">ANCM was deployed to Azure with these changes after ASP.NET Core 3.0.1 and 3.1.0 were deployed.</span></span>

#### <a name="category"></a><span data-ttu-id="cf668-143">Kategorie</span><span class="sxs-lookup"><span data-stu-id="cf668-143">Category</span></span>

<span data-ttu-id="cf668-144">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="cf668-144">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cf668-145">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="cf668-145">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)`

-->
