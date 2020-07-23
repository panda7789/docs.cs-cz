---
title: Co je nového v .NET Framework
description: Podívejte se, co je nového v různých verzích .NET Framework. Přečtěte si přehled klíčových nových funkcí a vylepšení v každé verzi.
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.assetid: 1d971dd7-10fc-4692-8dac-30ca308fc0fa
ms.openlocfilehash: 42f872bba87a88fc92a37879e815ee7068407cf7
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925589"
---
# <a name="whats-new-in-net-framework"></a><span data-ttu-id="87f14-104">Co je nového v .NET Framework</span><span class="sxs-lookup"><span data-stu-id="87f14-104">What's new in .NET Framework</span></span>

<span data-ttu-id="87f14-105">Tento článek shrnuje klíčové nové funkce a vylepšení v následujících verzích .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="87f14-105">This article summarizes key new features and improvements in the following versions of the .NET Framework:</span></span>

- [<span data-ttu-id="87f14-106">.NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="87f14-106">.NET Framework 4.8</span></span>](#v48)
- [<span data-ttu-id="87f14-107">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="87f14-107">.NET Framework 4.7.2</span></span>](#v472)
- [<span data-ttu-id="87f14-108">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="87f14-108">.NET Framework 4.7.1</span></span>](#v471)
- [<span data-ttu-id="87f14-109">.NET Framework 4,7</span><span class="sxs-lookup"><span data-stu-id="87f14-109">.NET Framework 4.7</span></span>](#v47)
- [<span data-ttu-id="87f14-110">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="87f14-110">.NET Framework 4.6.2</span></span>](#v462)
- [<span data-ttu-id="87f14-111">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="87f14-111">.NET Framework 4.6.1</span></span>](#v461)
- [<span data-ttu-id="87f14-112">.NET 2015 a .NET Framework 4,6</span><span class="sxs-lookup"><span data-stu-id="87f14-112">.NET 2015 and .NET Framework 4.6</span></span>](#v46)
- [<span data-ttu-id="87f14-113">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="87f14-113">.NET Framework 4.5.2</span></span>](#v452)
- [<span data-ttu-id="87f14-114">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="87f14-114">.NET Framework 4.5.1</span></span>](#v451)
- [<span data-ttu-id="87f14-115">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="87f14-115">.NET Framework 4.5</span></span>](#v45)

<span data-ttu-id="87f14-116">Tento článek neposkytuje úplné informace o každé nové funkci a může se změnit.</span><span class="sxs-lookup"><span data-stu-id="87f14-116">This article does not provide comprehensive information about each new feature and is subject to change.</span></span> <span data-ttu-id="87f14-117">Obecné informace o .NET Framework najdete v tématu [Začínáme](../get-started/index.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-117">For general information about the .NET Framework, see [Getting Started](../get-started/index.md).</span></span> <span data-ttu-id="87f14-118">Podporované platformy najdete v tématu [požadavky na systém](../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-118">For supported platforms, see [System Requirements](../get-started/system-requirements.md).</span></span> <span data-ttu-id="87f14-119">Odkazy na stažení a pokyny k instalaci najdete v [Průvodci instalací](../install/guide-for-developers.md)nástroje.</span><span class="sxs-lookup"><span data-stu-id="87f14-119">For download links and installation instructions, see [Installation Guide](../install/guide-for-developers.md).</span></span>

> [!NOTE]
> <span data-ttu-id="87f14-120">.NET Framework tým také uvolní funkce mimo pásmo s nástrojem NuGet, aby rozšířila podporu platforem a zavedla nové funkce, jako jsou neměnné kolekce a typy vektorů s podporou SIMD.</span><span class="sxs-lookup"><span data-stu-id="87f14-120">The .NET Framework team also releases features out of band with NuGet to expand platform support and to introduce new functionality, such as immutable collections and SIMD-enabled vector types.</span></span> <span data-ttu-id="87f14-121">Další informace najdete v tématech [Další knihovny tříd a rozhraní API](../additional-apis/index.md) a [.NET Framework a vzdálené verze](../get-started/the-net-framework-and-out-of-band-releases.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-121">For more information, see [Additional Class Libraries and APIs](../additional-apis/index.md) and [The .NET Framework and Out-of-Band Releases](../get-started/the-net-framework-and-out-of-band-releases.md).</span></span>
> <span data-ttu-id="87f14-122">Podívejte se na [úplný seznam balíčků NuGet](https://www.nuget.org/profiles/dotnetframework) pro .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="87f14-122">See a [complete list of NuGet packages](https://www.nuget.org/profiles/dotnetframework) for the .NET Framework.</span></span>

<a name="v48"></a>

## <a name="introducing-net-framework-48"></a><span data-ttu-id="87f14-123">Představujeme .NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="87f14-123">Introducing .NET Framework 4.8</span></span>

<span data-ttu-id="87f14-124">.NET Framework 4,8 sestaví na předchozích verzích .NET Framework 4. x přidáním mnoha nových oprav a několika nových funkcí a zbývajícím produktem.</span><span class="sxs-lookup"><span data-stu-id="87f14-124">.NET Framework 4.8 builds on previous versions of the .NET Framework 4.x by adding many new fixes and several new features while remaining a very stable product.</span></span>

### <a name="download-and-install-net-framework-48"></a><span data-ttu-id="87f14-125">Stažení a instalace .NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="87f14-125">Download and install .NET Framework 4.8</span></span>

<span data-ttu-id="87f14-126">.NET Framework 4,8 si můžete stáhnout z těchto umístění:</span><span class="sxs-lookup"><span data-stu-id="87f14-126">You can download .NET Framework 4.8  from the following locations:</span></span>

- [<span data-ttu-id="87f14-127">Webová instalační služba .NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="87f14-127">.NET Framework 4.8 Web Installer</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)

- [<span data-ttu-id="87f14-128">.NET Framework 4,8 – offline instalační program</span><span class="sxs-lookup"><span data-stu-id="87f14-128">NET Framework 4.8 Offline Installer</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)

<span data-ttu-id="87f14-129">.NET Framework 4,8 lze nainstalovat do systému Windows 10, Windows 8.1, Windows 7 SP1 a odpovídajících serverových platforem od verze Windows Server 2008 R2 SP1.</span><span class="sxs-lookup"><span data-stu-id="87f14-129">.NET Framework 4.8 can be installed on Windows 10, Windows 8.1, Windows 7 SP1, and the corresponding server platforms starting with Windows Server 2008 R2 SP1.</span></span> <span data-ttu-id="87f14-130">.NET Framework 4,8 můžete nainstalovat buď pomocí webové instalační služby, nebo v offline instalačním programu.</span><span class="sxs-lookup"><span data-stu-id="87f14-130">You can install .NET Framework 4.8 by using either the web installer or the offline installer.</span></span> <span data-ttu-id="87f14-131">Doporučeným způsobem pro většinu uživatelů je použití webové instalační služby.</span><span class="sxs-lookup"><span data-stu-id="87f14-131">The recommended way for most users is to use the web installer.</span></span>

<span data-ttu-id="87f14-132">Můžete cílit .NET Framework 4,8 v sadě Visual Studio 2012 nebo novější instalací sady [.NET Framework 4,8 Developer Pack](https://go.microsoft.com/fwlink/?LinkId=2085167).</span><span class="sxs-lookup"><span data-stu-id="87f14-132">You can target .NET Framework 4.8 in Visual Studio 2012 or later by installing the [.NET Framework 4.8 Developer Pack](https://go.microsoft.com/fwlink/?LinkId=2085167).</span></span>

### <a name="whats-new-in-net-framework-48"></a><span data-ttu-id="87f14-133">Co je nového v .NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="87f14-133">What's new in .NET Framework 4.8</span></span>

<span data-ttu-id="87f14-134">.NET Framework 4,8 zavádí nové funkce v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="87f14-134">.NET Framework 4.8 introduces new features in the following areas:</span></span>

- [<span data-ttu-id="87f14-135">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="87f14-135">Base classes</span></span>](#core48)
- [<span data-ttu-id="87f14-136">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="87f14-136">Windows Communication Foundation (WCF)</span></span>](#wcf48)
- [<span data-ttu-id="87f14-137">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="87f14-137">Windows Presentation Foundation (WPF)</span></span>](#wpf48)
- [<span data-ttu-id="87f14-138">Modul CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="87f14-138">Common language runtime</span></span>](#clr48)

<span data-ttu-id="87f14-139">Vylepšené přístupnost, která aplikaci umožňuje zajistit vhodné prostředí pro uživatele technologie pro usnadnění práce, je nadále hlavním cílem .NET Framework 4,8.</span><span class="sxs-lookup"><span data-stu-id="87f14-139">Improved accessibility, which allows an application to provide an appropriate experience for users of Assistive Technology, continues to be a major focus of .NET Framework 4.8.</span></span> <span data-ttu-id="87f14-140">Informace o vylepšeních usnadnění v .NET Framework 4,8 najdete v tématu [co je nového v přístupnosti v .NET Framework](whats-new-in-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-140">For information on accessibility improvements in .NET Framework 4.8, see [What's new in accessibility in the .NET Framework](whats-new-in-accessibility.md).</span></span>

<a name="core48"></a>

#### <a name="base-classes"></a><span data-ttu-id="87f14-141">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="87f14-141">Base classes</span></span>

<span data-ttu-id="87f14-142">Byl **snížen dopad FIPS na kryptografii**.</span><span class="sxs-lookup"><span data-stu-id="87f14-142">**Reduced FIPS impact on Cryptography**.</span></span> <span data-ttu-id="87f14-143">V předchozích verzích .NET Framework spravované třídy zprostředkovatele kryptografických služeb, jako je například <xref:System.Security.Cryptography.SHA256Managed> throw a v <xref:System.Security.Cryptography.CryptographicException> případě, že systémové šifrovací knihovny jsou konfigurovány v režimu FIPS.</span><span class="sxs-lookup"><span data-stu-id="87f14-143">In previous versions of the .NET Framework, managed cryptographic provider classes such as <xref:System.Security.Cryptography.SHA256Managed> throw a <xref:System.Security.Cryptography.CryptographicException> when the system cryptographic libraries are configured in "FIPS mode".</span></span> <span data-ttu-id="87f14-144">Tyto výjimky jsou vyvolány, protože spravované verze tříd zprostředkovatele kryptografických služeb, na rozdíl od systémových kryptografických knihoven, neprošly certifikací FIPS (Federal Information Processing Standards) 140-2.</span><span class="sxs-lookup"><span data-stu-id="87f14-144">These exceptions are thrown because the managed versions of the cryptographic provider classes, unlike the system cryptographic libraries, have not undergone FIPS (Federal Information Processing Standards) 140-2 certification.</span></span> <span data-ttu-id="87f14-145">Vzhledem k tomu, že někteří vývojáři mají své vývojové počítače v režimu FIPS, jsou výjimky obvykle vyvolány v produkčních systémech.</span><span class="sxs-lookup"><span data-stu-id="87f14-145">Because few developers have their development machines in FIPS mode, the exceptions are commonly thrown in production systems.</span></span>

<span data-ttu-id="87f14-146">Ve výchozím nastavení nejsou v aplikacích, které cílí na .NET Framework 4,8, následující spravované třídy kryptografie již <xref:System.Security.Cryptography.CryptographicException> v tomto případě vyvolávat:</span><span class="sxs-lookup"><span data-stu-id="87f14-146">By default in applications that target .NET Framework 4.8, the following managed cryptography classes no longer throw a <xref:System.Security.Cryptography.CryptographicException> in this case:</span></span>

- <xref:System.Security.Cryptography.MD5Cng>
- <xref:System.Security.Cryptography.MD5CryptoServiceProvider>
- <xref:System.Security.Cryptography.RC2CryptoServiceProvider>
- <xref:System.Security.Cryptography.RijndaelManaged>
- <xref:System.Security.Cryptography.RIPEMD160Managed>
- <xref:System.Security.Cryptography.SHA256Managed>

<span data-ttu-id="87f14-147">Místo toho tyto třídy přesměrují kryptografické operace do systémové knihovny kryptografie.</span><span class="sxs-lookup"><span data-stu-id="87f14-147">Instead, these classes redirect cryptographic operations to a system cryptography library.</span></span> <span data-ttu-id="87f14-148">Tato změna efektivně odstraňuje potenciálně matoucí rozdíl mezi vývojářskými prostředími a provozními prostředími a zpřístupňuje nativní komponenty a spravované komponenty v rámci stejných kryptografických zásad.</span><span class="sxs-lookup"><span data-stu-id="87f14-148">This change effectively removes a potentially confusing difference between developer environments and production environments and makes native components and managed components operate under the same cryptographic policy.</span></span> <span data-ttu-id="87f14-149">Aplikace, které závisí na těchto výjimkách, mohou obnovit předchozí chování nastavením přepínače AppContext `Switch.System.Security.Cryptography.UseLegacyFipsThrow` na `true` .</span><span class="sxs-lookup"><span data-stu-id="87f14-149">Applications that depend on these exceptions can restore the previous behavior by setting the AppContext switch `Switch.System.Security.Cryptography.UseLegacyFipsThrow` to `true`.</span></span> <span data-ttu-id="87f14-150">Další informace najdete v tématu [spravované kryptografické třídy nevyvolávají výjimku CryptographyException v režimu FIPS](../migration-guide/retargeting/4.7.2-4.8.md#managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode).</span><span class="sxs-lookup"><span data-stu-id="87f14-150">For more information, see [Managed cryptography classes do not throw a CryptographyException in FIPS mode](../migration-guide/retargeting/4.7.2-4.8.md#managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode).</span></span>

<span data-ttu-id="87f14-151">**Použití aktualizované verze ZLib**</span><span class="sxs-lookup"><span data-stu-id="87f14-151">**Use of updated version of ZLib**</span></span>

<span data-ttu-id="87f14-152">Počínaje .NET Framework 4,5 clrcompression.dll sestavení používá [ZLib](https://www.zlib.net), nativní externí knihovnu pro kompresi dat, aby bylo možné poskytnout implementaci pro algoritmus deflate.</span><span class="sxs-lookup"><span data-stu-id="87f14-152">Starting with .NET Framework 4.5, the clrcompression.dll assembly uses [ZLib](https://www.zlib.net), a native external library for data compression, in order to provide an implementation for the deflate algorithm.</span></span> <span data-ttu-id="87f14-153">clrcompression.dll .NET Framework 4,8 se aktualizuje tak, aby používal ZLib verzi 1.2.11, která zahrnuje několik klíčových vylepšení a oprav.</span><span class="sxs-lookup"><span data-stu-id="87f14-153">The .NET Framework 4.8, clrcompression.dll is updated to use ZLib Version 1.2.11, which includes several key improvements and fixes.</span></span>

<a name="wcf48"></a>

#### <a name="windows-communication-foundation-wcf"></a><span data-ttu-id="87f14-154">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="87f14-154">Windows Communication Foundation (WCF)</span></span>

<span data-ttu-id="87f14-155">**Úvod do ServiceHealthBehavior**</span><span class="sxs-lookup"><span data-stu-id="87f14-155">**Introduction of ServiceHealthBehavior**</span></span>

<span data-ttu-id="87f14-156">Nástroje pro orchestraci využívají koncové body stavu ke správě služeb na základě jejich stavu.</span><span class="sxs-lookup"><span data-stu-id="87f14-156">Health endpoints are widely used by orchestration tools to manage services based on their health status.</span></span> <span data-ttu-id="87f14-157">Kontroly stavu lze také použít pomocí nástrojů pro monitorování ke sledování a poskytování oznámení o dostupnosti a výkonu služby.</span><span class="sxs-lookup"><span data-stu-id="87f14-157">Health checks can also be used by monitoring tools to track and provide notifications about the availability and performance of a service.</span></span>

<span data-ttu-id="87f14-158">**ServiceHealthBehavior** je chování služby WCF, které rozšiřuje <xref:System.ServiceModel.Description.IServiceBehavior> .</span><span class="sxs-lookup"><span data-stu-id="87f14-158">**ServiceHealthBehavior** is a WCF service behavior that extends <xref:System.ServiceModel.Description.IServiceBehavior>.</span></span>  <span data-ttu-id="87f14-159">Při přidání do <xref:System.ServiceModel.Description.ServiceDescription.Behaviors?displayProperty=nameWithType> kolekce provede chování služby následující akce:</span><span class="sxs-lookup"><span data-stu-id="87f14-159">When added to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors?displayProperty=nameWithType> collection, a service behavior does the following:</span></span>

- <span data-ttu-id="87f14-160">Vrátí stav služby s kódy odpovědí HTTP.</span><span class="sxs-lookup"><span data-stu-id="87f14-160">Returns service health status with HTTP response codes.</span></span> <span data-ttu-id="87f14-161">V řetězci dotazu můžete zadat stavový kód HTTP pro požadavek na test stavu HTTP/GET.</span><span class="sxs-lookup"><span data-stu-id="87f14-161">You can specify in a query string the HTTP status code for a HTTP/GET health probe request.</span></span>

- <span data-ttu-id="87f14-162">Publikuje informace o stavu služby.</span><span class="sxs-lookup"><span data-stu-id="87f14-162">Publishes information about service health.</span></span> <span data-ttu-id="87f14-163">Podrobnosti konkrétní služby, včetně stavu služby, počtu omezení a kapacity, se dají zobrazit pomocí požadavku HTTP/GET s `?health` řetězcem dotazu.</span><span class="sxs-lookup"><span data-stu-id="87f14-163">Service-specific details, including service state, throttle counts, and capacity can be displayed by using an HTTP/GET request with the `?health` query string.</span></span> <span data-ttu-id="87f14-164">Usnadnění přístupu k těmto informacím je důležité při řešení potíží se službou WCF, která se nechová.</span><span class="sxs-lookup"><span data-stu-id="87f14-164">Ease of access to such information is important when troubleshooting a misbehaving WCF service.</span></span>

<span data-ttu-id="87f14-165">Existují dva způsoby, jak vystavit koncový bod stavu a publikovat informace o stavu služby WCF:</span><span class="sxs-lookup"><span data-stu-id="87f14-165">There are two ways to expose the health endpoint and publish WCF service health information:</span></span>

- <span data-ttu-id="87f14-166">Prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="87f14-166">Through code.</span></span> <span data-ttu-id="87f14-167">Příklad:</span><span class="sxs-lookup"><span data-stu-id="87f14-167">For example:</span></span>

  ```csharp
  ServiceHost host = new ServiceHost(typeof(Service1),
                     new Uri("http://contoso:81/Service1"));
  ServiceHealthBehavior healthBehavior =
      host.Description.Behaviors.Find<ServiceHealthBehavior>();
  healthBehavior ??= new ServiceHealthBehavior();
  host.Description.Behaviors.Add(healthBehavior);
  ```

  ```vb
  Dim host As New ServiceHost(GetType(Service1),
              New Uri("http://contoso:81/Service1"))
  Dim healthBehavior As ServiceHealthBehavior =
     host.Description.Behaviors.Find(Of ServiceHealthBehavior)()
  If healthBehavior Is Nothing Then
     healthBehavior = New ServiceHealthBehavior()
  End If
  host.Description.Behaviors.Add(healthBehavior)
  ```

- <span data-ttu-id="87f14-168">Pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="87f14-168">By using a configuration file.</span></span> <span data-ttu-id="87f14-169">Příklad:</span><span class="sxs-lookup"><span data-stu-id="87f14-169">For example:</span></span>

  ```xml
  <behaviors>
    <serviceBehaviors>
      <behavior name="DefaultBehavior">
        <serviceHealth httpsGetEnabled="true"/>
      </behavior>
    </serviceBehaviors>
  </behaviors>
  ```

<span data-ttu-id="87f14-170">Na stav služby se dá zadat dotaz pomocí parametrů dotazu `OnServiceFailure` , jako jsou,, a `OnDispatcherFailure` `OnListenerFailure` `OnThrottlePercentExceeded` ), a pro každý parametr dotazu je možné zadat kód odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="87f14-170">A service's health status can be queried by using query parameters such as `OnServiceFailure`, `OnDispatcherFailure`, `OnListenerFailure`, `OnThrottlePercentExceeded`), and an HTTP response code can be specified for each query parameter.</span></span> <span data-ttu-id="87f14-171">Pokud je pro parametr dotazu vynechání kódu odpovědi HTTP, ve výchozím nastavení se používá kód odpovědi HTTP 503.</span><span class="sxs-lookup"><span data-stu-id="87f14-171">If the HTTP response code is omitted for a query parameter, a 503 HTTP response code is used by default.</span></span> <span data-ttu-id="87f14-172">Příklad:</span><span class="sxs-lookup"><span data-stu-id="87f14-172">For example:</span></span>

- <span data-ttu-id="87f14-173">OnServiceFailure:`https://contoso:81/Service1?health&OnServiceFailure=450`</span><span class="sxs-lookup"><span data-stu-id="87f14-173">OnServiceFailure: `https://contoso:81/Service1?health&OnServiceFailure=450`</span></span>

  <span data-ttu-id="87f14-174">Kód stavu odpovědi HTTP 450 je vrácen, když je [Třída ServiceHost. State](xref:System.ServiceModel.Channels.CommunicationObject.State) je větší než <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="87f14-174">A 450 HTTP response status code is returned when [ServiceHost.State](xref:System.ServiceModel.Channels.CommunicationObject.State) is greater than <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.</span></span>
<span data-ttu-id="87f14-175">Parametry a příklady dotazů:</span><span class="sxs-lookup"><span data-stu-id="87f14-175">Query parameters and examples:</span></span>

- <span data-ttu-id="87f14-176">OnDispatcherFailure:`https://contoso:81/Service1?health&OnDispatcherFailure=455`</span><span class="sxs-lookup"><span data-stu-id="87f14-176">OnDispatcherFailure: `https://contoso:81/Service1?health&OnDispatcherFailure=455`</span></span>

  <span data-ttu-id="87f14-177">Stavový kód odpovědi HTTP 455 se vrátí, pokud je stav některého z přeslaných kanálů větší než <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="87f14-177">A 455 HTTP response status code is returned when the state of any of the channel dispatchers is greater than <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="87f14-178">OnListenerFailure:`https://contoso:81/Service1?health&OnListenerFailure=465`</span><span class="sxs-lookup"><span data-stu-id="87f14-178">OnListenerFailure: `https://contoso:81/Service1?health&OnListenerFailure=465`</span></span>

  <span data-ttu-id="87f14-179">Stavový kód odpovědi HTTP 465 se vrátí, pokud je stav jakéhokoli naslouchacího procesu kanálu větší než <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="87f14-179">A 465 HTTP response status code is returned when the state of any of the channel listeners is greater than <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="87f14-180">OnThrottlePercentExceeded:`https://contoso:81/Service1?health&OnThrottlePercentExceeded= 70:350,95:500`</span><span class="sxs-lookup"><span data-stu-id="87f14-180">OnThrottlePercentExceeded: `https://contoso:81/Service1?health&OnThrottlePercentExceeded= 70:350,95:500`</span></span>

  <span data-ttu-id="87f14-181">Určuje procento {1 – 100}, které aktivuje odpověď a kód odpovědi HTTP {200 – 599}.</span><span class="sxs-lookup"><span data-stu-id="87f14-181">Specifies the percentage {1 – 100} that triggers the response and its HTTP response code {200 – 599}.</span></span> <span data-ttu-id="87f14-182">V tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="87f14-182">In this example:</span></span>

  - <span data-ttu-id="87f14-183">Pokud je procento větší než 95, vrátí se kód odpovědi HTTP 500.</span><span class="sxs-lookup"><span data-stu-id="87f14-183">If the percentage is greater than 95, a 500 HTTP response code is returned.</span></span>

  - <span data-ttu-id="87f14-184">Pokud je vráceno procento nebo mezi 70 a 95, 350.</span><span class="sxs-lookup"><span data-stu-id="87f14-184">If the percentage or between 70 and 95, 350 is returned.</span></span>

  - <span data-ttu-id="87f14-185">V opačném případě se vrátí 200.</span><span class="sxs-lookup"><span data-stu-id="87f14-185">Otherwise, 200 is returned.</span></span>

<span data-ttu-id="87f14-186">Stav služby se dá zobrazit v HTML zadáním řetězce dotazu, jako je `https://contoso:81/Service1?health` nebo v XML, zadáním řetězce dotazu, jako je `https://contoso:81/Service1?health&Xml` .</span><span class="sxs-lookup"><span data-stu-id="87f14-186">The service health status can be displayed either in HTML by specifying a query string like `https://contoso:81/Service1?health` or in XML by specifying a query string like `https://contoso:81/Service1?health&Xml`.</span></span> <span data-ttu-id="87f14-187">Řetězec dotazu jako `https://contoso:81/Service1?health&NoContent` vrátí prázdnou stránku HTML.</span><span class="sxs-lookup"><span data-stu-id="87f14-187">A query string like `https://contoso:81/Service1?health&NoContent` returns an empty HTML page.</span></span>

<a name="wpf48"></a>

#### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="87f14-188">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="87f14-188">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="87f14-189">**Vylepšení vysokého rozlišení DPI**</span><span class="sxs-lookup"><span data-stu-id="87f14-189">**High DPI enhancements**</span></span>

<span data-ttu-id="87f14-190">V .NET Framework 4,8 WPF přidává podporu pro sledování rozlišení DPI podle monitoru v2 a škálování ve smíšeném režimu.</span><span class="sxs-lookup"><span data-stu-id="87f14-190">In .NET Framework 4.8, WPF adds support for Per-Monitor V2 DPI Awareness and Mixed-Mode DPI scaling.</span></span> <span data-ttu-id="87f14-191">Další informace o vývoji vysokého rozlišení DPI najdete v tématu [vývoj desktopových aplikací s vysokým rozlišením v systému Windows](/windows/win32/hidpi/high-dpi-desktop-application-development-on-windows) .</span><span class="sxs-lookup"><span data-stu-id="87f14-191">See [High DPI Desktop Application Development on Windows](/windows/win32/hidpi/high-dpi-desktop-application-development-on-windows) for additional information about high DPI development.</span></span>

<span data-ttu-id="87f14-192">.NET Framework 4,8 vylepšuje podporu hostovaných HWND a model Windows Forms spolupráce v aplikacích WPF s vysokým rozlišením DPI na platformách, které podporují škálování DPI ve smíšeném režimu (od aktualizace Windows 10. dubna 2018).</span><span class="sxs-lookup"><span data-stu-id="87f14-192">.NET Framework 4.8 improves support for hosted HWNDs and Windows Forms interoperation in High-DPI WPF applications on platforms that support Mixed-Mode DPI scaling (starting with Windows 10 April 2018 Update).</span></span> <span data-ttu-id="87f14-193">Když jsou hostované ovládací prvky HWND nebo model Windows Forms vytvořeny jako okna s rozlišením DPI ve smíšeném režimu pomocí volání [SetThreadDpiHostingBehavior](/windows/desktop/api/winuser/nf-winuser-setthreaddpihostingbehavior) a [SetThreadDpiAwarenessContext](/windows/desktop/api/winuser/nf-winuser-setthreaddpiawarenesscontext), mohou být hostovány v aplikaci WPF pro monitor v2 a mají odpovídající velikost a správné škálování.</span><span class="sxs-lookup"><span data-stu-id="87f14-193">When hosted HWNDs or Windows Forms controls are created as Mixed-Mode DPI-scaled windows by calling [SetThreadDpiHostingBehavior](/windows/desktop/api/winuser/nf-winuser-setthreaddpihostingbehavior) and [SetThreadDpiAwarenessContext](/windows/desktop/api/winuser/nf-winuser-setthreaddpiawarenesscontext), they can be hosted in a Per-Monitor V2 WPF application and are sized and scaled appropriately.</span></span> <span data-ttu-id="87f14-194">Takový hostovaný obsah se nevykresluje s nativním rozlišením DPI; operační systém místo toho škáluje hostovaný obsah na příslušnou velikost.</span><span class="sxs-lookup"><span data-stu-id="87f14-194">Such hosted content is not rendered at the native DPI; instead, the operating system scales the hosted content to the appropriate size.</span></span> <span data-ttu-id="87f14-195">Podpora režimu sledování DPI v rámci monitoru v2 také umožňuje hostování ovládacích prvků WPF (tj. nadřazených) v nativním okně aplikace s vysokým rozlišením DPI.</span><span class="sxs-lookup"><span data-stu-id="87f14-195">The support for Per-Monitor v2 DPI awareness mode also allows WPF controls to be hosted (i.e., parented) in a native window in a high-DPI application.</span></span>

<span data-ttu-id="87f14-196">Pokud chcete povolit podporu pro škálování ve smíšeném režimu s vysokým rozlišením DPI, můžete nastavit následující [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) přepínače konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="87f14-196">To enable support for Mixed-Mode High DPI scaling, you can set the following [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switches the application configuration file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value = "Switch.System.Windows.DoNotScaleForDpiChanges=false; Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false"/>
</runtime>
```

<a name="clr48"></a>

#### <a name="common-language-runtime"></a><span data-ttu-id="87f14-197">Modul CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="87f14-197">Common language runtime</span></span>

<span data-ttu-id="87f14-198">Modul runtime v .NET Framework 4,8 obsahuje následující změny a vylepšení:</span><span class="sxs-lookup"><span data-stu-id="87f14-198">The runtime in .NET Framework 4.8 includes the following changes and improvements:</span></span>

<span data-ttu-id="87f14-199">**Vylepšení kompilátoru JIT**.</span><span class="sxs-lookup"><span data-stu-id="87f14-199">**Improvements to the JIT compiler**.</span></span> <span data-ttu-id="87f14-200">Kompilátor JIT (just-in-time) v .NET Framework 4,8 je založen na kompilátoru JIT v rozhraní .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="87f14-200">The Just-in-time (JIT) compiler in .NET Framework 4.8 is based on the JIT compiler in .NET Core 2.1.</span></span> <span data-ttu-id="87f14-201">Mnohé z optimalizací a všechny opravy chyb provedené kompilátorem JIT .NET Core 2,1 jsou součástí kompilátoru .NET Framework 4,8 JIT.</span><span class="sxs-lookup"><span data-stu-id="87f14-201">Many of the optimizations and all of the bug fixes made to the .NET Core 2.1 JIT compiler are included in the .NET Framework 4.8 JIT compiler.</span></span>

<span data-ttu-id="87f14-202">**Vylepšení Ngen**.</span><span class="sxs-lookup"><span data-stu-id="87f14-202">**NGEN improvements**.</span></span> <span data-ttu-id="87f14-203">Modul runtime zlepšil správu paměti pro Image [generátoru nativních imagí](../tools/ngen-exe-native-image-generator.md) (NGen), takže data mapovaná z imagí Ngen nejsou rezidentní v paměti.</span><span class="sxs-lookup"><span data-stu-id="87f14-203">The runtime has improved its memory management for [Native Image Generator](../tools/ngen-exe-native-image-generator.md) (NGEN) images so that data mapped from NGEN images are not memory-resident.</span></span> <span data-ttu-id="87f14-204">Tím se snižuje plocha dostupná pro útoky, které se pokoušejí spustit libovolný kód úpravou paměti, která se spustí.</span><span class="sxs-lookup"><span data-stu-id="87f14-204">This reduces the surface area available to attacks that attempt to execute arbitrary code by modifying memory that will be executed.</span></span>

<span data-ttu-id="87f14-205">**Kontrola antimalwaru pro všechna sestavení**.</span><span class="sxs-lookup"><span data-stu-id="87f14-205">**Antimalware scanning for all assemblies**.</span></span> <span data-ttu-id="87f14-206">V předchozích verzích .NET Framework modul runtime prohledává všechna sestavení načtená z disku pomocí programu Windows Defender nebo antimalwarového softwaru jiného výrobce.</span><span class="sxs-lookup"><span data-stu-id="87f14-206">In previous versions of the .NET Framework, the runtime scans all assemblies loaded from disk using either Windows Defender or third-party antimalware software.</span></span> <span data-ttu-id="87f14-207">Nicméně sestavení načtená z jiných zdrojů, například <xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType> metodou, nejsou prohledávána a mohou potenciálně obsahovat nezjištěné malware.</span><span class="sxs-lookup"><span data-stu-id="87f14-207">However, assemblies loaded from other sources, such as by the <xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType> method, are not scanned and can potentially contain undetected malware.</span></span> <span data-ttu-id="87f14-208">Počínaje .NET Framework 4,8 spuštěným v systému Windows 10 spustí modul runtime kontrolu pomocí antimalwarových řešení, která implementují [rozhraní AMSI (antimalwarová kontrola)](/windows/desktop/AMSI/antimalware-scan-interface-portal).</span><span class="sxs-lookup"><span data-stu-id="87f14-208">Starting with .NET Framework 4.8 running on Windows 10, the runtime triggers a scan by antimalware solutions that implement the [Antimalware Scan Interface (AMSI)](/windows/desktop/AMSI/antimalware-scan-interface-portal).</span></span>

<a name="v472"></a>

## <a name="whats-new-in-net-framework-472"></a><span data-ttu-id="87f14-209">Co je nového v .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="87f14-209">What's new in .NET Framework 4.7.2</span></span>

<span data-ttu-id="87f14-210">.NET Framework 4.7.2 zahrnuje nové funkce v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="87f14-210">.NET Framework 4.7.2 includes new features in the following areas:</span></span>

- [<span data-ttu-id="87f14-211">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="87f14-211">Base classes</span></span>](#core-472)
- [<span data-ttu-id="87f14-212">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="87f14-212">ASP.NET</span></span>](#asp-net472)
- [<span data-ttu-id="87f14-213">Sítě</span><span class="sxs-lookup"><span data-stu-id="87f14-213">Networking</span></span>](#net472)
- [<span data-ttu-id="87f14-214">SQL</span><span class="sxs-lookup"><span data-stu-id="87f14-214">SQL</span></span>](#sql472)
- [<span data-ttu-id="87f14-215">WPF</span><span class="sxs-lookup"><span data-stu-id="87f14-215">WPF</span></span>](#wpf472)
- [<span data-ttu-id="87f14-216">ClickOnce</span><span class="sxs-lookup"><span data-stu-id="87f14-216">ClickOnce</span></span>](#clickonce)

<span data-ttu-id="87f14-217">Dalším cílem .NET Framework 4.7.2 je lepší přístupnost, která umožňuje aplikaci poskytovat vhodné prostředí pro uživatele technologie usnadnění.</span><span class="sxs-lookup"><span data-stu-id="87f14-217">A continuing focus in .NET Framework 4.7.2 is improved accessibility, which allows an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="87f14-218">Informace o vylepšeních usnadnění v .NET Framework 4.7.2 najdete v tématu [co je nového v přístupnosti v .NET Framework](whats-new-in-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-218">For information on accessibility improvements in .NET Framework 4.7.2, see [What's new in accessibility in the .NET Framework](whats-new-in-accessibility.md).</span></span>

<a name="core-472"></a>

#### <a name="base-classes"></a><span data-ttu-id="87f14-219">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="87f14-219">Base classes</span></span>

<span data-ttu-id="87f14-220">.NET Framework 4.7.2 obsahuje velký počet kryptografických vylepšení, lepší podporu dekomprese pro archivy ZIP a další rozhraní API pro shromažďování dat.</span><span class="sxs-lookup"><span data-stu-id="87f14-220">.NET Framework 4.7.2 features a large number of cryptographic enhancements, better decompression support for ZIP archives, and additional collection APIs.</span></span>

<span data-ttu-id="87f14-221">**Nová přetížení RSA. Vytvořte a DSA. Vytvořeny**</span><span class="sxs-lookup"><span data-stu-id="87f14-221">**New overloads of RSA.Create and DSA.Create**</span></span>

<span data-ttu-id="87f14-222"><xref:System.Security.Cryptography.DSA.Create(System.Security.Cryptography.DSAParameters)?displayProperty=nameWithType>Metody a <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> umožňují zadávat klíčové parametry při vytváření instance nového <xref:System.Security.Cryptography.DSA> nebo <xref:System.Security.Cryptography.RSA> klíče.</span><span class="sxs-lookup"><span data-stu-id="87f14-222">The <xref:System.Security.Cryptography.DSA.Create(System.Security.Cryptography.DSAParameters)?displayProperty=nameWithType> and <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> methods let you supply key parameters when instantiating a new <xref:System.Security.Cryptography.DSA> or <xref:System.Security.Cryptography.RSA> key.</span></span> <span data-ttu-id="87f14-223">Umožňují nahradit kód podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="87f14-223">They allow you to replace code like the following:</span></span>

```csharp
// Before .NET Framework 4.7.2
using (RSA rsa = RSA.Create())
{
   rsa.ImportParameters(rsaParameters);
   // Other code to execute using the RSA instance.
}
```

```vb
' Before .NET Framework 4.7.2
Using rsa = RSA.Create()
   rsa.ImportParameters(rsaParameters)
   ' Other code to execute using the rsa instance.
End Using
```

<span data-ttu-id="87f14-224">podobný kód:</span><span class="sxs-lookup"><span data-stu-id="87f14-224">with code like this:</span></span>

```csharp
// Starting with .NET Framework 4.7.2
using (RSA rsa = RSA.Create(rsaParameters))
{
   // Other code to execute using the rsa instance.
}
```

```vb
' Starting with .NET Framework 4.7.2
Using rsa = RSA.Create(rsaParameters)
   ' Other code to execute using the rsa instance.
End Using
```

<span data-ttu-id="87f14-225"><xref:System.Security.Cryptography.DSA.Create(System.Int32)?displayProperty=nameWithType>Metody a <xref:System.Security.Cryptography.RSA.Create(System.Int32)?displayProperty=nameWithType> umožňují generovat nové klíče <xref:System.Security.Cryptography.DSA> nebo <xref:System.Security.Cryptography.RSA> klíče s určitou velikostí klíče.</span><span class="sxs-lookup"><span data-stu-id="87f14-225">The <xref:System.Security.Cryptography.DSA.Create(System.Int32)?displayProperty=nameWithType> and <xref:System.Security.Cryptography.RSA.Create(System.Int32)?displayProperty=nameWithType> methods let you generate new <xref:System.Security.Cryptography.DSA> or <xref:System.Security.Cryptography.RSA> keys with a specific key size.</span></span> <span data-ttu-id="87f14-226">Příklad:</span><span class="sxs-lookup"><span data-stu-id="87f14-226">For example:</span></span>

```csharp
using (DSA dsa = DSA.Create(2048))
{
   // Other code to execute using the dsa instance.
}
```

```vb
Using dsa = DSA.Create(2048)
   ' Other code to execute using the dsa instance.
End Using
```

<span data-ttu-id="87f14-227">**Konstruktory Rfc2898DeriveBytes přijímají název algoritmu hash.**</span><span class="sxs-lookup"><span data-stu-id="87f14-227">**Rfc2898DeriveBytes constructors accept a hash algorithm name**</span></span>

<span data-ttu-id="87f14-228"><xref:System.Security.Cryptography.Rfc2898DeriveBytes>Třída má tři nové konstruktory s <xref:System.Security.Cryptography.HashAlgorithmName> parametrem, který IDENTIFIKUJE algoritmus HMAC, který má být použit při odvozování klíčů.</span><span class="sxs-lookup"><span data-stu-id="87f14-228">The <xref:System.Security.Cryptography.Rfc2898DeriveBytes> class has three new constructors with a <xref:System.Security.Cryptography.HashAlgorithmName> parameter that identifies the HMAC algorithm to use when deriving keys.</span></span> <span data-ttu-id="87f14-229">Místo použití algoritmu SHA-1 by vývojáři měli používat HMAC založené na SHA-2, jako je SHA-256, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="87f14-229">Instead of using SHA-1, developers should use a SHA-2-based HMAC like SHA-256, as shown in the following example:</span></span>

```csharp
private static byte[] DeriveKey(string password, out int iterations, out byte[] salt,
                                out HashAlgorithmName algorithm)
{
   iterations = 100000;
   algorithm = HashAlgorithmName.SHA256;

   const int SaltSize = 32;
   const int DerivedValueSize = 32;

   using (Rfc2898DeriveBytes pbkdf2 = new Rfc2898DeriveBytes(password, SaltSize,
                                                             iterations, algorithm))
   {
      salt = pbkdf2.Salt;
      return pbkdf2.GetBytes(DerivedValueSize);
   }
}
```

```vb
Private Shared Function DeriveKey(password As String, ByRef iterations As Integer,
                                  ByRef salt AS Byte(), ByRef algorithm As HashAlgorithmName) As Byte()
   iterations = 100000
   algorithm = HashAlgorithmName.SHA256

   Const SaltSize As Integer = 32
   Const  DerivedValueSize As Integer = 32

   Using pbkdf2 = New Rfc2898DeriveBytes(password, SaltSize, iterations, algorithm)
      salt = pbkdf2.Salt
      Return pbkdf2.GetBytes(DerivedValueSize)
   End Using
End Function
```

<span data-ttu-id="87f14-230">**Podpora dočasných klíčů**</span><span class="sxs-lookup"><span data-stu-id="87f14-230">**Support for ephemeral keys**</span></span>

<span data-ttu-id="87f14-231">Import PFX může volitelně načíst soukromé klíče přímo z paměti a obejít pevný disk.</span><span class="sxs-lookup"><span data-stu-id="87f14-231">PFX import can optionally load private keys directly from memory, bypassing the hard drive.</span></span><span data-ttu-id="87f14-232">Když je nový <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> příznak zadán v <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> konstruktoru nebo v jednom z přetížení <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.Import%2A?displayProperty=nameWithType> metody, privátní klíče budou načteny jako dočasné klíče.</span><span class="sxs-lookup"><span data-stu-id="87f14-232"> When the new <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> flag is specified in an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> constructor or one of the overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.Import%2A?displayProperty=nameWithType> method, the private keys will be loaded as ephemeral keys.</span></span> <span data-ttu-id="87f14-233">To brání tomu, aby se klíče na disku zobrazily.</span><span class="sxs-lookup"><span data-stu-id="87f14-233">This prevents the keys from being visible on the disk.</span></span> <span data-ttu-id="87f14-234">Naopak</span><span class="sxs-lookup"><span data-stu-id="87f14-234">However:</span></span>

- <span data-ttu-id="87f14-235">Vzhledem k tomu, že klíče nejsou trvale uložené na disku, certifikáty načtené pomocí tohoto příznaku nejsou vhodnými kandidáty k přidání do X509Store.</span><span class="sxs-lookup"><span data-stu-id="87f14-235">Since the keys are not persisted to disk, certificates loaded with this flag are not good candidates to add to an X509Store.</span></span>

- <span data-ttu-id="87f14-236">Klíče načtené tímto způsobem jsou téměř vždy načítány prostřednictvím služby Windows CNG.</span><span class="sxs-lookup"><span data-stu-id="87f14-236">Keys loaded in this manner are almost always loaded via Windows CNG.</span></span> <span data-ttu-id="87f14-237">Proto volající musí získat přístup k privátnímu klíči voláním metod rozšíření, jako je například [CERT. GetRSAPrivateKey ()](xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A).</span><span class="sxs-lookup"><span data-stu-id="87f14-237">Therefore, callers must access the private key by calling extension methods, such as [cert.GetRSAPrivateKey()](xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A).</span></span> <span data-ttu-id="87f14-238">Vlastnost nefunguje <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="87f14-238">The <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> property does not function.</span></span>

- <span data-ttu-id="87f14-239">Vzhledem k tomu <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> , že vlastnost starší verze nefunguje s certifikáty, vývojáři by měli před přechodem na dočasné klíče provádět přísné testy.</span><span class="sxs-lookup"><span data-stu-id="87f14-239">Since the legacy <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> property does not work with certificates, developers should perform rigorous testing before switching to ephemeral keys.</span></span>

<span data-ttu-id="87f14-240">**Programové vytváření žádostí o podepsání certifikátu PKCS # 10 a certifikátů veřejných klíčů X. 509**</span><span class="sxs-lookup"><span data-stu-id="87f14-240">**Programmatic creation of PKCS#10 certification signing requests and X.509 public key certificates**</span></span>

<span data-ttu-id="87f14-241">Počínaje .NET Framework 4.7.2 můžou úlohy generovat žádosti o podepsání certifikátu (oddělení IT), které umožňují, aby se generování žádosti o certifikát připravilo na stávající nástroje.</span><span class="sxs-lookup"><span data-stu-id="87f14-241">Starting with .NET Framework 4.7.2, workloads can generate certificate signing requests (CSRs), which allows certificate request generation to be staged into existing tooling.</span></span> <span data-ttu-id="87f14-242">To je často užitečné v testovacích scénářích.</span><span class="sxs-lookup"><span data-stu-id="87f14-242">This is frequently useful in test scenarios.</span></span>

<span data-ttu-id="87f14-243">Další informace a příklady kódu naleznete v tématu "programové vytváření žádostí o podepsání certifikátu PKCS # 10 a" certifikátů veřejných klíčů X. 509 "na [blogu .NET](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).</span><span class="sxs-lookup"><span data-stu-id="87f14-243">For more information and code examples, see "Programmatic creation of PKCS#10 certification signing requests and X.509 public key certificates" in the [.NET Blog](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).</span></span>

<span data-ttu-id="87f14-244">**Noví členové SignerInfo**</span><span class="sxs-lookup"><span data-stu-id="87f14-244">**New SignerInfo members**</span></span>

<span data-ttu-id="87f14-245">Počínaje .NET Framework 4.7.2 <xref:System.Security.Cryptography.Pkcs.SignerInfo> Třída zveřejňuje Další informace o podpisu.</span><span class="sxs-lookup"><span data-stu-id="87f14-245">Starting with .NET Framework 4.7.2, the <xref:System.Security.Cryptography.Pkcs.SignerInfo> class exposes more information about the signature.</span></span> <span data-ttu-id="87f14-246">Můžete načíst hodnotu <xref:System.Security.Cryptography.Pkcs.SignerInfo.SignatureAlgorithm?displayProperty=fullName> vlastnosti a určit tak algoritmus podpisu, který používá podepisující osoba.</span><span class="sxs-lookup"><span data-stu-id="87f14-246">You can retrieve the value of the <xref:System.Security.Cryptography.Pkcs.SignerInfo.SignatureAlgorithm?displayProperty=fullName> property to determine the signature algorithm used by the signer.</span></span> <span data-ttu-id="87f14-247"><xref:System.Security.Cryptography.Pkcs.SignerInfo.GetSignature%2A?displayProperty=nameWithType>dá se zavolat, aby se získala kopie kryptografického podpisu pro tohoto podepsaného.</span><span class="sxs-lookup"><span data-stu-id="87f14-247"><xref:System.Security.Cryptography.Pkcs.SignerInfo.GetSignature%2A?displayProperty=nameWithType> can be called to get a copy of the cryptographic signature for this signer.</span></span>

<span data-ttu-id="87f14-248">**Otevření zabaleného datového proudu po odstranění CryptoStream**</span><span class="sxs-lookup"><span data-stu-id="87f14-248">**Leaving a wrapped stream open after CryptoStream is disposed**</span></span>

<span data-ttu-id="87f14-249">Počínaje .NET Framework 4.7.2 <xref:System.Security.Cryptography.CryptoStream> má třída další konstruktor, který umožňuje <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> Zavřít zabalený datový proud.</span><span class="sxs-lookup"><span data-stu-id="87f14-249">Starting with .NET Framework 4.7.2, the <xref:System.Security.Cryptography.CryptoStream> class has an additional constructor that allows <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> to not close the wrapped stream.</span></span><span data-ttu-id="87f14-250">Chcete-li nechat zabalený datový proud otevřený po <xref:System.Security.Cryptography.CryptoStream> uvolnění instance, zavolejte nový <xref:System.Security.Cryptography.CryptoStream> konstruktor následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="87f14-250"> To leave the wrapped stream open after the <xref:System.Security.Cryptography.CryptoStream> instance is disposed, call the new <xref:System.Security.Cryptography.CryptoStream> constructor as follows:</span></span>

```csharp
var cStream = new CryptoStream(stream, transform, mode, leaveOpen: true);
```

```vb
Dim cStream = New CryptoStream(stream, transform, mode, leaveOpen:=true)
```

<span data-ttu-id="87f14-251">**Dekomprese změn v DeflateStream**</span><span class="sxs-lookup"><span data-stu-id="87f14-251">**Decompression changes in DeflateStream**</span></span>

<span data-ttu-id="87f14-252">Počínaje .NET Framework 4.7.2 se implementace operací dekomprese ve <xref:System.IO.Compression.DeflateStream> třídě změnila tak, aby ve výchozím nastavení používala nativní rozhraní API systému Windows.</span><span class="sxs-lookup"><span data-stu-id="87f14-252">Starting with .NET Framework 4.7.2, the implementation of decompression operations in the <xref:System.IO.Compression.DeflateStream> class has changed to use native Windows APIs by default.</span></span> <span data-ttu-id="87f14-253">Obvykle to vede k výraznému zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="87f14-253">Typically, this results in a substantial performance improvement.</span></span>

<span data-ttu-id="87f14-254">Podpora dekomprese pomocí rozhraní Windows API je ve výchozím nastavení povolená pro aplikace, které cílí na .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="87f14-254">Support for decompression by using Windows APIs is enabled by default for applications that target .NET Framework 4.7.2.</span></span> <span data-ttu-id="87f14-255">Aplikace, které jsou cíleny na starší verze .NET Framework, ale jsou spuštěny v rámci .NET Framework 4.7.2, se můžou na toto chování vyjádřit přidáním následujícího [přepínače AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="87f14-255">Applications that target earlier versions of .NET Framework but are running under .NET Framework 4.7.2 can opt into this behavior by adding the following [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the application configuration file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=false" />
```

<span data-ttu-id="87f14-256">**Další rozhraní API pro shromažďování**</span><span class="sxs-lookup"><span data-stu-id="87f14-256">**Additional collection APIs**</span></span>

<span data-ttu-id="87f14-257">.NET Framework 4.7.2 přidá mnoho nových rozhraní API k <xref:System.Collections.Generic.SortedSet%601> <xref:System.Collections.Generic.HashSet%601> typům a.</span><span class="sxs-lookup"><span data-stu-id="87f14-257">.NET Framework 4.7.2 adds a number of new APIs to the <xref:System.Collections.Generic.SortedSet%601> and <xref:System.Collections.Generic.HashSet%601> types.</span></span> <span data-ttu-id="87f14-258">Mezi ně patří:</span><span class="sxs-lookup"><span data-stu-id="87f14-258">These include:</span></span>

- <span data-ttu-id="87f14-259">`TryGetValue`metody, které přesahují vzor try použitý v jiných typech kolekcí těchto dvou typů.</span><span class="sxs-lookup"><span data-stu-id="87f14-259">`TryGetValue` methods, which extend the try pattern used in other collection types to these two types.</span></span> <span data-ttu-id="87f14-260">Existují tyto metody:</span><span class="sxs-lookup"><span data-stu-id="87f14-260">The methods are:</span></span>

  - [<span data-ttu-id="87f14-261">Public \<T> bool HashSet – TryGetValue (T equalValue; out T actualValue)</span><span class="sxs-lookup"><span data-stu-id="87f14-261">public bool HashSet\<T>.TryGetValue(T equalValue, out T actualValue)</span></span>](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)
  - [<span data-ttu-id="87f14-262">Public \<T> bool SortedSet TryGetValue (T equalValue; out T actualValue)</span><span class="sxs-lookup"><span data-stu-id="87f14-262">public bool SortedSet\<T>.TryGetValue(T equalValue, out T actualValue)</span></span>](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)

- <span data-ttu-id="87f14-263">`Enumerable.To*`metody rozšíření, které převádějí kolekci na <xref:System.Collections.Generic.HashSet%601> :</span><span class="sxs-lookup"><span data-stu-id="87f14-263">`Enumerable.To*` extension methods, which convert a collection to a <xref:System.Collections.Generic.HashSet%601>:</span></span>

  - [<span data-ttu-id="87f14-264">veřejný statický HashSet – \<TSource> ToHashSet \<TSource> (Tento \<TSource> zdroj IEnumerable)</span><span class="sxs-lookup"><span data-stu-id="87f14-264">public static HashSet\<TSource> ToHashSet\<TSource>(this IEnumerable\<TSource> source)</span></span>](xref:System.Linq.Enumerable.ToHashSet%2A)
  - [<span data-ttu-id="87f14-265">public static HashSet – \<TSource> ToHashSet \<TSource> (this IEnumerable \<TSource> source, IEqualityComparer \<TSource> Comparer)</span><span class="sxs-lookup"><span data-stu-id="87f14-265">public static HashSet\<TSource> ToHashSet\<TSource>(this IEnumerable\<TSource> source, IEqualityComparer\<TSource> comparer)</span></span>](xref:System.Linq.Enumerable.ToHashSet%2A)

- <span data-ttu-id="87f14-266">Nové <xref:System.Collections.Generic.HashSet%601> konstruktory, které umožňují nastavit kapacitu kolekce, což vede k výhodám výkonu, když znáte velikost <xref:System.Collections.Generic.HashSet%601> předem:</span><span class="sxs-lookup"><span data-stu-id="87f14-266">New <xref:System.Collections.Generic.HashSet%601> constructors that let you set the collection's capacity, which yields a performance benefit when you know the size of the <xref:System.Collections.Generic.HashSet%601> in advance:</span></span>

  - <span data-ttu-id="87f14-267">[veřejné HashSet – (kapacita celé číslo)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32))</span><span class="sxs-lookup"><span data-stu-id="87f14-267">[public HashSet(int capacity)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32))</span></span>
  - <span data-ttu-id="87f14-268">[Public HashSet – (kapacita int, IEqualityComparer \<T> Comparer)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32,System.Collections.Generic.IEqualityComparer%7B%600%7D))</span><span class="sxs-lookup"><span data-stu-id="87f14-268">[public HashSet(int capacity, IEqualityComparer\<T> comparer)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32,System.Collections.Generic.IEqualityComparer%7B%600%7D))</span></span>

<span data-ttu-id="87f14-269"><xref:System.Collections.Concurrent.ConcurrentDictionary%602>Třída obsahuje nová přetížení <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> metod a k načtení hodnoty ze slovníku nebo k jejímu přidání, pokud nebyla nalezena, a pro přidání hodnoty do slovníku nebo její aktualizaci, pokud již existuje.</span><span class="sxs-lookup"><span data-stu-id="87f14-269">The <xref:System.Collections.Concurrent.ConcurrentDictionary%602> class includes new overloads of the <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> and <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> methods to retrieve a value from the dictionary or to add it if it is not found, and to add a value to the dictionary or to update it if it already exists.</span></span>

```csharp
public TValue AddOrUpdate<TArg>(TKey key, Func<TKey, TArg, TValue> addValueFactory, Func<TKey, TValue, TArg, TValue> updateValueFactory, TArg factoryArgument)

public TValue GetOrAdd<TArg>(TKey key, Func<TKey, TArg, TValue> valueFactory, TArg factoryArgument)
```

```vb
Public AddOrUpdate(Of TArg)(key As TKey, addValueFactory As Func(Of TKey, TArg, TValue), updateValueFactory As Func(Of TKey, TValue, TArg, TValue), factoryArgument As TArg) As TValue

Public GetOrAdd(Of TArg)(key As TKey, valueFactory As Func(Of TKey, TArg, TValue), factoryArgument As TArg) As TValue
```

<a name="asp-net472"></a>

#### <a name="aspnet"></a><span data-ttu-id="87f14-270">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="87f14-270">ASP.NET</span></span>

<span data-ttu-id="87f14-271">**Podpora pro vkládání závislostí ve webových formulářích**</span><span class="sxs-lookup"><span data-stu-id="87f14-271">**Support for dependency injection in Web Forms**</span></span>

<span data-ttu-id="87f14-272">[Vkládání závislostí (di)](/aspnet/core/fundamentals/dependency-injection#overview-of-dependency-injection) odděluje objekty a jejich závislosti tak, že kód objektu již není nutné změnit pouze proto, že došlo ke změně závislosti.</span><span class="sxs-lookup"><span data-stu-id="87f14-272">[Dependency injection (DI)](/aspnet/core/fundamentals/dependency-injection#overview-of-dependency-injection) decouples objects and their dependencies so that an object's code no longer needs to be changed just because a dependency has changed.</span></span> <span data-ttu-id="87f14-273">Při vývoji aplikací ASP.NET, které cílí na .NET Framework 4.7.2, můžete:</span><span class="sxs-lookup"><span data-stu-id="87f14-273">When developing ASP.NET applications that target .NET Framework 4.7.2, you can:</span></span>

- <span data-ttu-id="87f14-274">Použijte metodu setter založenou na rozhraních a na bázi konstruktoru v [obslužných rutinách a modulech](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [instancích stránky](xref:System.Web.UI.Page)a [uživatelských ovládacích prvcích](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) projektů webové aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="87f14-274">Use setter-based, interface-based, and constructor-based injection in [handlers and modules](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [Page instances](xref:System.Web.UI.Page), and [user controls](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) of ASP.NET web application projects.</span></span>

- <span data-ttu-id="87f14-275">Používejte vkládání na základě rozhraní a založených na rozhraních v [obslužných rutinách a modulech](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [instancích stránky](xref:System.Web.UI.Page)a [uživatelských ovládacích prvcích](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) projektů webu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="87f14-275">Use setter-based and interface-based injection in [handlers and modules](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [Page instances](xref:System.Web.UI.Page), and [user controls](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) of ASP.NET web site projects.</span></span>

- <span data-ttu-id="87f14-276">Připojte se k různým rozhraním injektáže pro vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="87f14-276">Plug in different dependency injection frameworks.</span></span>

<span data-ttu-id="87f14-277">**Podpora souborů cookie stejného webu**</span><span class="sxs-lookup"><span data-stu-id="87f14-277">**Support for same-site cookies**</span></span>

<span data-ttu-id="87f14-278">[SameSite](https://tools.ietf.org/html/draft-west-first-party-cookies-07) zabraňuje prohlížeči v posílání souborů cookie spolu s žádostí mezi weby.</span><span class="sxs-lookup"><span data-stu-id="87f14-278">[SameSite](https://tools.ietf.org/html/draft-west-first-party-cookies-07) prevents a browser from sending a cookie along with a cross-site request.</span></span> <span data-ttu-id="87f14-279">.NET Framework 4.7.2 přidá <xref:System.Web.HttpCookie.SameSite?displayProperty=nameWithType> vlastnost, jejíž hodnota je <xref:System.Web.SameSiteMode?displayProperty=nameWithType> člen výčtu.</span><span class="sxs-lookup"><span data-stu-id="87f14-279">.NET Framework 4.7.2 adds a <xref:System.Web.HttpCookie.SameSite?displayProperty=nameWithType> property whose value is a <xref:System.Web.SameSiteMode?displayProperty=nameWithType> enumeration member.</span></span> <span data-ttu-id="87f14-280">Pokud je jeho hodnota <xref:System.Web.SameSiteMode.Strict?displayProperty=nameWithType> nebo <xref:System.Web.SameSiteMode.Lax?displayProperty=nameWithType> , ASP.NET přidá `SameSite` atribut do hlavičky Set-cookie.</span><span class="sxs-lookup"><span data-stu-id="87f14-280">If its value is <xref:System.Web.SameSiteMode.Strict?displayProperty=nameWithType> or <xref:System.Web.SameSiteMode.Lax?displayProperty=nameWithType>, ASP.NET adds the `SameSite` attribute to the set-cookie header.</span></span> <span data-ttu-id="87f14-281">Podpora SameSite se vztahuje na <xref:System.Web.HttpCookie> objekty i na <xref:System.Web.Security.FormsAuthentication> <xref:System.Web.SessionState> soubory cookie a.</span><span class="sxs-lookup"><span data-stu-id="87f14-281">SameSite support applies to <xref:System.Web.HttpCookie> objects, as well as to <xref:System.Web.Security.FormsAuthentication> and <xref:System.Web.SessionState> cookies.</span></span>

<span data-ttu-id="87f14-282">SameSite pro objekt můžete nastavit takto <xref:System.Web.HttpCookie> :</span><span class="sxs-lookup"><span data-stu-id="87f14-282">You can set SameSite for an <xref:System.Web.HttpCookie> object as follows:</span></span>

```csharp
var c = new HttpCookie("secureCookie", "same origin");
c.SameSite = SameSiteMode.Lax;
```

```vb
Dim c As New HttpCookie("secureCookie", "same origin")
c.SameSite = SameSiteMode.Lax
```

<span data-ttu-id="87f14-283">Soubory cookie SameSite můžete na úrovni aplikace nakonfigurovat také úpravou souboru web.config:</span><span class="sxs-lookup"><span data-stu-id="87f14-283">You can also configure SameSite cookies at the application level by modifying the web.config file:</span></span>

```xml
<system.web>
   <httpCookies sameSite="Strict" />
</system.web>
```

<span data-ttu-id="87f14-284">SameSite pro <xref:System.Web.Security.FormsAuthentication> a <xref:System.Web.SessionState> soubory cookie můžete přidat úpravou konfiguračního souboru Web:</span><span class="sxs-lookup"><span data-stu-id="87f14-284">You can add SameSite for <xref:System.Web.Security.FormsAuthentication> and <xref:System.Web.SessionState> cookies by modifying the web config file:</span></span>

```xml
<system.web>
   <authentication mode="Forms">
      <forms cookieSameSite="Lax">
         <!-- ...   -->
      </forms>
   </authentication>
   <sessionState cookieSameSite="Lax"></sessionState>
</system.web>
```

<a name="net472"></a>

#### <a name="networking"></a><span data-ttu-id="87f14-285">Sítě</span><span class="sxs-lookup"><span data-stu-id="87f14-285">Networking</span></span>

<span data-ttu-id="87f14-286">**Implementace vlastností HttpClientHandler**</span><span class="sxs-lookup"><span data-stu-id="87f14-286">**Implementation of HttpClientHandler properties**</span></span>

<span data-ttu-id="87f14-287">.NET Framework 4.7.1 přidal do třídy osm vlastností <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="87f14-287">.NET Framework 4.7.1 added eight properties to the <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="87f14-288">Nicméně dvě vyvolaly výjimku <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="87f14-288">However, two threw a <xref:System.PlatformNotSupportedException>.</span></span> <span data-ttu-id="87f14-289">.NET Framework 4.7.2 nyní poskytuje implementaci těchto vlastností.</span><span class="sxs-lookup"><span data-stu-id="87f14-289">.NET Framework 4.7.2 now provides an implementation for these properties.</span></span> <span data-ttu-id="87f14-290">Mezi vlastnosti patří:</span><span class="sxs-lookup"><span data-stu-id="87f14-290">The properties are:</span></span>

- <xref:System.Net.Http.HttpClientHandler.CheckCertificateRevocationList>
- <xref:System.Net.Http.HttpClientHandler.SslProtocols>

<a name="sql472"></a>

#### <a name="sqlclient"></a><span data-ttu-id="87f14-291">SQLClient</span><span class="sxs-lookup"><span data-stu-id="87f14-291">SQLClient</span></span>

<span data-ttu-id="87f14-292">**Podpora Azure Active Directory univerzálního ověřování a Multi-Factor Authentication**</span><span class="sxs-lookup"><span data-stu-id="87f14-292">**Support for Azure Active Directory Universal Authentication and Multi-Factor authentication**</span></span>

<span data-ttu-id="87f14-293">Rostoucí požadavky na dodržování předpisů a požadavky na zabezpečení vyžadují, aby spousta zákazníků používala vícefaktorové ověřování (MFA).</span><span class="sxs-lookup"><span data-stu-id="87f14-293">Growing compliance and security demands require that many customers use multi-factor authentication (MFA).</span></span> <span data-ttu-id="87f14-294">Kromě toho aktuální osvědčené postupy zabrání zahrnutí uživatelských hesel přímo v připojovacích řetězcích.</span><span class="sxs-lookup"><span data-stu-id="87f14-294">In addition, current best practices discourage including user passwords directly in connection strings.</span></span> <span data-ttu-id="87f14-295">Pro podporu těchto změn .NET Framework 4.7.2 rozšiřuje [připojovací řetězce SqlClient](xref:System.Data.SqlClient.SqlConnection.ConnectionString) přidáním nové hodnoty "Active Directory Interactive" pro stávající klíčové slovo "ověřování" pro podporu MFA a [ověřování Azure AD](/azure/sql-database/sql-database-aad-authentication-configure).</span><span class="sxs-lookup"><span data-stu-id="87f14-295">To support these changes, .NET Framework 4.7.2 extends [SQLClient connection strings](xref:System.Data.SqlClient.SqlConnection.ConnectionString) by adding a new value, "Active Directory Interactive", for the existing "Authentication" keyword to support MFA and [Azure AD Authentication](/azure/sql-database/sql-database-aad-authentication-configure).</span></span> <span data-ttu-id="87f14-296">Nová interaktivní metoda podporuje uživatele v rámci nativních a federovaných uživatelů Azure AD i uživatele typu Host služby Azure AD.</span><span class="sxs-lookup"><span data-stu-id="87f14-296">The new interactive method supports native and federated Azure AD users as well as Azure AD guest users.</span></span> <span data-ttu-id="87f14-297">Při použití této metody se pro databáze SQL podporuje ověřování MFA, které ukládá služba Azure AD.</span><span class="sxs-lookup"><span data-stu-id="87f14-297">When this method is used, the MFA authentication imposed by Azure AD is supported for SQL databases.</span></span> <span data-ttu-id="87f14-298">Kromě toho proces ověřování požaduje heslo uživatele, aby dodržoval osvědčené postupy zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="87f14-298">In addition, the authentication process requests a user password to adhere to security best practices.</span></span>

<span data-ttu-id="87f14-299">V předchozích verzích .NET Framework připojení SQL podporovalo pouze <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryPassword?displayProperty=nameWithType> <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryIntegrated?displayProperty=nameWithType> Možnosti a.</span><span class="sxs-lookup"><span data-stu-id="87f14-299">In previous versions of the .NET Framework, SQL connectivity supported only the <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryPassword?displayProperty=nameWithType> and <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryIntegrated?displayProperty=nameWithType> options.</span></span> <span data-ttu-id="87f14-300">Obě tyto součásti jsou součástí neinteraktivního [protokolu ADAL](/azure/active-directory/develop/active-directory-authentication-libraries), který nepodporuje vícefaktorové ověřování.</span><span class="sxs-lookup"><span data-stu-id="87f14-300">Both of these are part of the non-interactive [ADAL protocol](/azure/active-directory/develop/active-directory-authentication-libraries), which does not support MFA.</span></span> <span data-ttu-id="87f14-301">Díky nové <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryInteractive?displayProperty=nameWithType> Možnosti připojení SQL podporuje vícefaktorové ověřování a taky existující metody ověřování (heslo a integrované ověřování), které uživatelům umožňují zadat uživatelská hesla interaktivně, aniž by museli uchovávat hesla v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="87f14-301">With the new <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryInteractive?displayProperty=nameWithType> option, SQL connectivity supports MFA as well as existing authentication methods (password and integrated authentication), which allows users to enter user passwords interactively without persisting passwords in the connection string.</span></span>

<span data-ttu-id="87f14-302">Další informace a příklad najdete v tématu Podpora SQL--Azure AD Universal a Multi-Factor Authentication na [blogu .NET](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).</span><span class="sxs-lookup"><span data-stu-id="87f14-302">For more information and an example, see "SQL -- Azure AD Universal and Multi-factor Authentication Support" in the [.NET Blog](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).</span></span>

<span data-ttu-id="87f14-303">**Podpora pro Always Encrypted verze 2**</span><span class="sxs-lookup"><span data-stu-id="87f14-303">**Support for Always Encrypted version 2**</span></span>

<span data-ttu-id="87f14-304">NET Framework 4.7.2 přidává podporu pro Always Encrypted založenou na enklávy.</span><span class="sxs-lookup"><span data-stu-id="87f14-304">NET Framework 4.7.2 adds supports for enclave-based Always Encrypted.</span></span> <span data-ttu-id="87f14-305">Původní verze Always Encrypted je technologie šifrování na straně klienta, ve které šifrovací klíče nikdy nenechávají klienta.</span><span class="sxs-lookup"><span data-stu-id="87f14-305">The original version of Always Encrypted is a client-side encryption technology in which encryption keys never leave the client.</span></span> <span data-ttu-id="87f14-306">V Always Encrypted založeném na enklávy může klient volitelně odesílat šifrovací klíče na zabezpečený enklávy, což je zabezpečená výpočetní entita, kterou je možné považovat za součást SQL Server, ale SQL Server kód nemůže manipulovat.</span><span class="sxs-lookup"><span data-stu-id="87f14-306">In enclave-based Always Encrypted, the client can optionally send the encryption keys to a secure enclave, which is a secure computational entity that can be considered part of SQL Server but that SQL Server code cannot tamper with.</span></span> <span data-ttu-id="87f14-307">Pro podporu Always Encrypted založeného na enklávy, .NET Framework 4.7.2 přidá následující typy a členy do <xref:System.Data.SqlClient> oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="87f14-307">To support enclave-based Always Encrypted, .NET Framework 4.7.2 adds the following types and members to the <xref:System.Data.SqlClient> namespace:</span></span>

- <span data-ttu-id="87f14-308"><xref:System.Data.SqlClient.SqlConnectionStringBuilder.EnclaveAttestationUrl?displayProperty=nameWithType>, který určuje identifikátor URI pro Always Encrypted založené na enklávy.</span><span class="sxs-lookup"><span data-stu-id="87f14-308"><xref:System.Data.SqlClient.SqlConnectionStringBuilder.EnclaveAttestationUrl?displayProperty=nameWithType>, which specifies the Uri for enclave-based Always Encrypted.</span></span>

- <span data-ttu-id="87f14-309"><xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider>, což je abstraktní třída, ze které jsou odvozeni všichni poskytovatelé enklávy.</span><span class="sxs-lookup"><span data-stu-id="87f14-309"><xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider>, which is an abstract class from which all enclave providers are derived.</span></span>

- <span data-ttu-id="87f14-310"><xref:System.Data.SqlClient.SqlEnclaveSession>, který zapouzdřuje stav pro danou relaci enklávy.</span><span class="sxs-lookup"><span data-stu-id="87f14-310"><xref:System.Data.SqlClient.SqlEnclaveSession>, which encapsulates the state for a given enclave session.</span></span>

- <span data-ttu-id="87f14-311"><xref:System.Data.SqlClient.SqlEnclaveAttestationParameters>, který poskytuje parametry ověření identity používané SQL Server k získání informací potřebných ke spuštění konkrétního protokolu ověření identity.</span><span class="sxs-lookup"><span data-stu-id="87f14-311"><xref:System.Data.SqlClient.SqlEnclaveAttestationParameters>, which provides the attestation parameters used by SQL Server to get information required to execute a particular Attestation Protocol.</span></span>

<span data-ttu-id="87f14-312">Konfigurační soubor aplikace pak určí konkrétní implementaci abstraktní <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider?displayProperty=nameWithType> třídy, která poskytuje funkce pro poskytovatele enklávy.</span><span class="sxs-lookup"><span data-stu-id="87f14-312">The application configuration file then specifies a concrete implementation of the abstract <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider?displayProperty=nameWithType> class that provides the functionality for the enclave provider.</span></span> <span data-ttu-id="87f14-313">Příklad:</span><span class="sxs-lookup"><span data-stu-id="87f14-313">For example:</span></span>

```xml
<configuration>
  <configSections>
    <section name="SqlColumnEncryptionEnclaveProviders" type="System.Data.SqlClient.SqlColumnEncryptionEnclaveProviderConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>
  </configSections>
  <SqlColumnEncryptionEnclaveProviders>
    <providers>
      <add name="Azure" type="Microsoft.SqlServer.Management.AlwaysEncrypted.AzureEnclaveProvider,MyApp"/>
      <add name="HGS" type="Microsoft.SqlServer.Management.AlwaysEncrypted.HGSEnclaveProvider,MyApp" />
    </providers>
  </SqlColumnEncryptionEnclaveProviders >
</configuration>
```

<span data-ttu-id="87f14-314">Základní tok Always Encrypted založeného na enklávy:</span><span class="sxs-lookup"><span data-stu-id="87f14-314">The basic flow of enclave-based Always Encrypted is:</span></span>

1. <span data-ttu-id="87f14-315">Uživatel vytvoří připojení AlwaysEncrypted k SQL Server, která podporuje Always Encrypted založenou na enklávy.</span><span class="sxs-lookup"><span data-stu-id="87f14-315">The user creates an AlwaysEncrypted connection to SQL Server that supported enclave-based Always Encrypted.</span></span> <span data-ttu-id="87f14-316">Ovladač kontaktuje službu ověření identity, aby zajistil, že se připojí k pravé enklávy.</span><span class="sxs-lookup"><span data-stu-id="87f14-316">The driver contacts the attestation service to ensure that it is connecting to right enclave.</span></span>

1. <span data-ttu-id="87f14-317">Po ověření enklávy ovladač vytvoří zabezpečený kanál se zabezpečeným enklávy hostovaným na SQL Server.</span><span class="sxs-lookup"><span data-stu-id="87f14-317">Once the enclave has been attested, the driver establishes a secure channel with the secure enclave hosted on SQL Server.</span></span>

1. <span data-ttu-id="87f14-318">Ovladač sdílí šifrovací klíče autorizované klientem s zabezpečeným enklávy po dobu trvání připojení SQL.</span><span class="sxs-lookup"><span data-stu-id="87f14-318">The driver shares encryption keys authorized by the client with the secure enclave for the duration of the SQL connection.</span></span>

<a name="wpf472"></a>

#### <a name="windows-presentation-foundation"></a><span data-ttu-id="87f14-319">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="87f14-319">Windows Presentation Foundation</span></span>

<span data-ttu-id="87f14-320">**Hledání třídách ResourceDictionaries podle zdroje**</span><span class="sxs-lookup"><span data-stu-id="87f14-320">**Finding ResourceDictionaries by Source**</span></span>

<span data-ttu-id="87f14-321">Počínaje .NET Framework 4.7.2 může diagnostický pomocník najít  <xref:System.Windows.Xps.Packaging.IXpsFixedPageReader.ResourceDictionaries> vytvářený z daného zdrojového identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="87f14-321">Starting with .NET Framework 4.7.2, a diagnostic assistant can locate the <xref:System.Windows.Xps.Packaging.IXpsFixedPageReader.ResourceDictionaries> that have been created from a given source Uri.</span></span><span data-ttu-id="87f14-322">(Tato funkce se používá pro diagnostické asistenty, nikoli pro produkční aplikace.) Pomocník pro diagnostiku, jako je "Edit-and-Continue" sady Visual Studio, umožňuje svému uživateli upravit ResourceDictionary s záměrem, aby se změny projevily u běžící aplikace.</span><span class="sxs-lookup"><span data-stu-id="87f14-322"> (This feature is for use by diagnostic assistants, not by production applications.) A diagnostic assistant such as Visual Studio's "Edit-and-Continue" facility lets its user edit a ResourceDictionary with the intent that the changes be applied to the running application.</span></span> <span data-ttu-id="87f14-323">V tomto kroku najdete všechny třídách ResourceDictionaries, které spuštěná aplikace vytvořila ze upravovaného slovníku.</span><span class="sxs-lookup"><span data-stu-id="87f14-323">One step in achieving this is finding all the ResourceDictionaries that the running application has created from the dictionary that's being edited.</span></span> <span data-ttu-id="87f14-324">Například aplikace může deklarovat ResourceDictionary, jehož obsah je zkopírován z daného zdrojového identifikátoru URI:</span><span class="sxs-lookup"><span data-stu-id="87f14-324">For example, an application can declare a ResourceDictionary whose content is copied from a given source URI:</span></span>

```xml
<ResourceDictionary Source="MyRD.xaml" />
```

<span data-ttu-id="87f14-325">Diagnostický pomocník, který upravuje původní kód v souboru *MyRD. XAML*,   může k vyhledání slovníku použít novou funkci.</span><span class="sxs-lookup"><span data-stu-id="87f14-325">A diagnostic assistant that edits the original markup in *MyRD.xaml* can use the new feature to locate the dictionary.</span></span><span data-ttu-id="87f14-326">Tato funkce je implementována novou statickou metodou <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetResourceDictionariesForSource%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="87f14-326"> The feature is implemented by a new static method, <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetResourceDictionariesForSource%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="87f14-327">Pomocník diagnostiky volá novou metodu pomocí absolutního identifikátoru URI, který identifikuje původní kód, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="87f14-327">The diagnostic assistant calls the new method using an absolute Uri that identifies the original markup, as illustrated by the following code:</span></span>

```csharp
IEnumerable<ResourceDictionary> dictionaries = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(new Uri("pack://application:,,,/MyApp;component/MyRD.xaml"));
```

```vb
Dim dictionaries As IEnumerable(Of ResourceDictionary) = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(New Uri("pack://application:,,,/MyApp;component/MyRD.xaml"))
```

<span data-ttu-id="87f14-328">Metoda vrátí prázdnou hodnotu výčtu, pokud  <xref:System.Windows.Diagnostics.VisualDiagnostics> není povolena a [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)   Proměnná prostředí je nastavena.</span><span class="sxs-lookup"><span data-stu-id="87f14-328">The method returns an empty enumerable unless <xref:System.Windows.Diagnostics.VisualDiagnostics> is enabled and the [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) environment variable is set.</span></span>

<span data-ttu-id="87f14-329">**Hledání vlastníků ResourceDictionary**</span><span class="sxs-lookup"><span data-stu-id="87f14-329">**Finding ResourceDictionary owners**</span></span>

<span data-ttu-id="87f14-330">Počínaje .NET Framework 4.7.2 může pomocník pro diagnostiku najít vlastníky daného <xref:Windows.UI.Xaml.ResourceDictionary> .</span><span class="sxs-lookup"><span data-stu-id="87f14-330">Starting with .NET Framework 4.7.2, a diagnostic assistant can locate the owners of a given <xref:Windows.UI.Xaml.ResourceDictionary>.</span></span><span data-ttu-id="87f14-331">(Tato funkce je určena pro diagnostické asistenty, nikoli pro produkční aplikace.) Pokaždé, když je provedena změna na <xref:Windows.UI.Xaml.ResourceDictionary> , WPF automaticky najde všechny odkazy na [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) , které mohou být ovlivněny změnou.</span><span class="sxs-lookup"><span data-stu-id="87f14-331"> (The feature is for use by diagnostic assistants and not by production applications.) Whenever a change is made to a <xref:Windows.UI.Xaml.ResourceDictionary>, WPF automatically finds all [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) references that might be affected by the change.</span></span>

<span data-ttu-id="87f14-332">Nástroj pro diagnostiku, jako je například zařízení "Edit-and-Continue" sady Visual Studio, může chtít tuto funkci zvětšit, aby zpracovávala odkazy na [StaticResource](../wpf/advanced/staticresource-markup-extension.md) .</span><span class="sxs-lookup"><span data-stu-id="87f14-332">A diagnostic assistant such as Visual Studio's "Edit-and-Continue" facility may want to extend this to handle [StaticResource](../wpf/advanced/staticresource-markup-extension.md) references.</span></span> <span data-ttu-id="87f14-333">Prvním krokem v tomto procesu je vyhledání vlastníků slovníku; To znamená, aby bylo možné najít všechny objekty, jejichž `Resources` vlastnost odkazuje na slovník (buď přímo, nebo nepřímo přes <xref:System.Windows.ResourceDictionary.MergedDictionaries?displayProperty=nameWithType> vlastnost).</span><span class="sxs-lookup"><span data-stu-id="87f14-333">The first step in this process is to find the owners of the dictionary; that is, to find all the objects whose `Resources` property refers to the dictionary (either directly, or indirectly via the <xref:System.Windows.ResourceDictionary.MergedDictionaries?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="87f14-334">Tři nové statické metody implementované u <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics?displayProperty=nameWithType> třídy, jeden pro každý ze základních typů, které mají `Resources` vlastnost, podporují tento krok:</span><span class="sxs-lookup"><span data-stu-id="87f14-334">Three new static methods implemented on the <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics?displayProperty=nameWithType> class, one for each of the base types that has a `Resources` property, support this step:</span></span>

- [`public static IEnumerable<FrameworkElement> GetFrameworkElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkElementOwners%2A)

- [`public static IEnumerable<FrameworkContentElement> GetFrameworkContentElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkContentElementOwners%2A)

- [`public static IEnumerable<Application> GetApplicationOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetApplicationOwners%2A)

<span data-ttu-id="87f14-335">Tyto metody vrátí prázdný vyčíslitelné, pokud  <xref:System.Windows.Diagnostics.VisualDiagnostics> není povoleno a [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)   Proměnná prostředí je nastavena.</span><span class="sxs-lookup"><span data-stu-id="87f14-335">These methods return an empty enumerable unless <xref:System.Windows.Diagnostics.VisualDiagnostics> is enabled and the [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) environment variable is set.</span></span>

<span data-ttu-id="87f14-336">**Hledání odkazů na StaticResource**</span><span class="sxs-lookup"><span data-stu-id="87f14-336">**Finding StaticResource references**</span></span>

<span data-ttu-id="87f14-337">Diagnostika pomocníka teď může obdržet oznámení vždy, když se vyřeší odkaz na [StaticResource](../wpf/advanced/staticresource-markup-extension.md) .</span><span class="sxs-lookup"><span data-stu-id="87f14-337">A diagnostic assistant can now receive a notification whenever a [StaticResource](../wpf/advanced/staticresource-markup-extension.md) reference is resolved.</span></span><span data-ttu-id="87f14-338">(Tato funkce se používá pro diagnostické asistenty, nikoli pro produkční aplikace.) Nástroj pro diagnostiku, jako je například zařízení "Edit-and-Continue" sady Visual Studio, může chtít aktualizovat všechna použití prostředku, když se změní jeho hodnota <xref:Windows.UI.Xaml.ResourceDictionary> .</span><span class="sxs-lookup"><span data-stu-id="87f14-338"> (The feature is for use by diagnostic assistants, not by production applications.) A diagnostic assistant such as Visual Studio's "Edit-and-Continue" facility may want to update all uses of a resource when its value in a <xref:Windows.UI.Xaml.ResourceDictionary> changes.</span></span> <span data-ttu-id="87f14-339">WPF to provede automaticky pro [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) odkazy, ale záměrně to neudělá pro odkazy [StaticResource](../wpf/advanced/staticresource-markup-extension.md) .</span><span class="sxs-lookup"><span data-stu-id="87f14-339">WPF does this automatically for [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) references, but it intentionally does not do so for [StaticResource](../wpf/advanced/staticresource-markup-extension.md) references.</span></span> <span data-ttu-id="87f14-340">Od .NET Framework 4.7.2 může pomocník diagnostiky použít tato oznámení k vyhledání těchto použití statického prostředku.</span><span class="sxs-lookup"><span data-stu-id="87f14-340">Starting with .NET Framework 4.7.2, the diagnostic assistant can use these notifications to locate those uses of the static resource.</span></span>

<span data-ttu-id="87f14-341">Oznámení je implementováno novou <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.StaticResourceResolved?displayProperty=nameWithType> událostí:</span><span class="sxs-lookup"><span data-stu-id="87f14-341">The notification is implemented by the new <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.StaticResourceResolved?displayProperty=nameWithType> event:</span></span>

```csharp
public static event EventHandler<StaticResourceResolvedEventArgs> StaticResourceResolved;
```

```vb
Public Shared Event StaticResourceResolved As EventHandler(Of StaticResourceResolvedEventArgs)
```

<span data-ttu-id="87f14-342">Tato událost je vyvolána pokaždé, když modul runtime vyřeší odkaz [StaticResource](../wpf/advanced/staticresource-markup-extension.md) .</span><span class="sxs-lookup"><span data-stu-id="87f14-342">This event is raised whenever the runtime resolves a [StaticResource](../wpf/advanced/staticresource-markup-extension.md) reference.</span></span><span data-ttu-id="87f14-343"><xref:System.Windows.Diagnostics.StaticResourceResolvedEventArgs>Argumenty popisují rozlišení a označují objekt a vlastnost, které hostují odkaz [StaticResource](../wpf/advanced/staticresource-markup-extension.md) a klíč a, který  <xref:Windows.UI.Xaml.ResourceDictionary> se používá pro řešení:</span><span class="sxs-lookup"><span data-stu-id="87f14-343"> The <xref:System.Windows.Diagnostics.StaticResourceResolvedEventArgs> arguments describe the resolution, and indicate the object and property that host the [StaticResource](../wpf/advanced/staticresource-markup-extension.md) reference and the <xref:Windows.UI.Xaml.ResourceDictionary> and key used for the resolution:</span></span>

```csharp
public class StaticResourceResolvedEventArgs : EventArgs
{
   public Object TargetObject { get; }

   public Object TargetProperty { get; }

   public ResourceDictionary ResourceDictionary { get; }

   public object ResourceKey { get; }
}
```

```vb
Public Class StaticResourceResolvedEventArgs : Inherits EventArgs
   Public ReadOnly Property TargetObject As Object
   Public ReadOnly Property TargetProperty As Object
   Public ReadOnly Property ResourceDictionary As ResourceDictionary
   Public ReadOnly Property ResourceKey As Object
End Class
```

<span data-ttu-id="87f14-344">Událost není vyvolána (a její `add` přistupující objekt je ignorován), pokud  <xref:System.Windows.Diagnostics.VisualDiagnostics> není povolena a [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)   Proměnná prostředí je nastavena.</span><span class="sxs-lookup"><span data-stu-id="87f14-344">The event is not raised (and its `add` accessor is ignored) unless <xref:System.Windows.Diagnostics.VisualDiagnostics> is enabled and the [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) environment variable is set.</span></span>

#### <a name="clickonce"></a><span data-ttu-id="87f14-345">ClickOnce</span><span class="sxs-lookup"><span data-stu-id="87f14-345">ClickOnce</span></span>

<span data-ttu-id="87f14-346">HDPI aplikace pro model Windows Forms, Windows Presentation Foundation (WPF) a Visual Studio Tools for Office (VSTO) se dají nasadit pomocí technologie ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="87f14-346">HDPI-aware applications for Windows Forms, Windows Presentation Foundation (WPF), and Visual Studio Tools for Office (VSTO) can all be deployed by using ClickOnce.</span></span> <span data-ttu-id="87f14-347">Pokud je v manifestu aplikace nalezen následující záznam, nasazení bude úspěšné v části .NET Framework 4.7.2:</span><span class="sxs-lookup"><span data-stu-id="87f14-347">If the following entry is found in the application manifest, deployment will succeed under .NET Framework 4.7.2:</span></span>

```xml
<windowsSettings>
   <dpiAware xmlns="http://schemas.microsoft.com/SMI/2005/WindowsSettings">true</dpiAware>
</windowsSettings>
```

<span data-ttu-id="87f14-348">V případě model Windows Forms aplikace není pro úspěšné nasazení ClickOnce předchozí alternativní řešení nastavení zvyšování rozlišení DPI v konfiguračním souboru aplikace, a ne jako manifest aplikace, již nutné.</span><span class="sxs-lookup"><span data-stu-id="87f14-348">For Windows Forms application, the previous workaround of setting DPI awareness in the application configuration file rather than the application manifest is no longer necessary for ClickOnce deployment to succeed.</span></span>

<a name="v471"></a>

## <a name="whats-new-in-net-framework-471"></a><span data-ttu-id="87f14-349">Co je nového v .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="87f14-349">What's new in .NET Framework 4.7.1</span></span>

<span data-ttu-id="87f14-350">.NET Framework 4.7.1 zahrnuje nové funkce v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="87f14-350">.NET Framework 4.7.1 includes new features in the following areas:</span></span>

- [<span data-ttu-id="87f14-351">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="87f14-351">Base classes</span></span>](#core471)
- [<span data-ttu-id="87f14-352">Modul CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="87f14-352">Common language runtime (CLR)</span></span>](#clr)
- [<span data-ttu-id="87f14-353">Sítě</span><span class="sxs-lookup"><span data-stu-id="87f14-353">Networking</span></span>](#net471)
- [<span data-ttu-id="87f14-354">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="87f14-354">ASP.NET</span></span>](#asp-net471)

<span data-ttu-id="87f14-355">Navíc je hlavní fokus v .NET Framework 4.7.1 vylepšený přístupnost, což aplikaci umožňuje zajistit vhodné prostředí pro uživatele technologie usnadnění.</span><span class="sxs-lookup"><span data-stu-id="87f14-355">In addition, a major focus in .NET Framework 4.7.1 is improved accessibility, which allows an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="87f14-356">Informace o vylepšeních usnadnění v .NET Framework 4.7.1 najdete v tématu [co je nového v přístupnosti v .NET Framework](whats-new-in-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-356">For information on accessibility improvements in .NET Framework 4.7.1, see [What's new in accessibility in the .NET Framework](whats-new-in-accessibility.md).</span></span>

<a name="core471"></a>

#### <a name="base-classes"></a><span data-ttu-id="87f14-357">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="87f14-357">Base classes</span></span>

<span data-ttu-id="87f14-358">**Podpora pro .NET Standard 2,0**</span><span class="sxs-lookup"><span data-stu-id="87f14-358">**Support for .NET Standard 2.0**</span></span>

<span data-ttu-id="87f14-359">[.NET Standard](../../standard/net-standard.md) definuje sadu rozhraní API, která musí být k dispozici v každé implementaci rozhraní .NET, která podporuje tuto verzi standardu.</span><span class="sxs-lookup"><span data-stu-id="87f14-359">[.NET Standard](../../standard/net-standard.md) defines a set of APIs that must be available on each .NET implementation that supports that version of the standard.</span></span> <span data-ttu-id="87f14-360">.NET Framework 4.7.1 plně podporuje .NET Standard 2,0 a přidává [asi 200 rozhraní API](https://github.com/dotnet/standard/blob/master/src/netstandard/src/ApiCompatBaseline.net461.txt) , která jsou definována v .NET Standard 2,0 a chybí v .NET Framework 4.6.1, 4.6.2 a 4,7.</span><span class="sxs-lookup"><span data-stu-id="87f14-360">.NET Framework 4.7.1 fully supports .NET Standard 2.0 and adds [about 200 APIs](https://github.com/dotnet/standard/blob/master/src/netstandard/src/ApiCompatBaseline.net461.txt) that are defined in .NET Standard 2.0 and are missing from .NET Framework 4.6.1, 4.6.2, and 4.7.</span></span> <span data-ttu-id="87f14-361">(Upozorňujeme, že tyto verze .NET Framework podporují .NET Standard 2,0 pouze v případě, že jsou do cílového systému nasazeny také další .NET Standard podpůrné soubory.) Další informace najdete v příspěvku na blogu o podpoře BCL-.NET Standard 2,0 v tématu [.NET Framework 4.7.1 runtime a funkce kompilátoru](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) .</span><span class="sxs-lookup"><span data-stu-id="87f14-361">(Note that these versions of the .NET Framework support .NET Standard 2.0 only if additional .NET Standard support files are also deployed on the target system.) For more information, see "BCL - .NET Standard 2.0 Support" in the [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog post.</span></span>

<span data-ttu-id="87f14-362">**Podpora pro sestavovatele konfigurace**</span><span class="sxs-lookup"><span data-stu-id="87f14-362">**Support for configuration builders**</span></span>

<span data-ttu-id="87f14-363">Tvůrci konfigurace umožňují vývojářům dynamicky vkládat a sestavovat nastavení konfigurace pro aplikace v době běhu.</span><span class="sxs-lookup"><span data-stu-id="87f14-363">Configuration builders allow developers to inject and build configuration settings for applications dynamically at run time.</span></span> <span data-ttu-id="87f14-364">Vlastní tvůrci konfigurace lze použít k úpravě existujících dat v konfiguračním oddílu nebo k sestavení konfiguračního oddílu úplně od začátku.</span><span class="sxs-lookup"><span data-stu-id="87f14-364">Custom configuration builders can be used to modify existing data in a configuration section or to build a configuration section entirely from scratch.</span></span> <span data-ttu-id="87f14-365">Bez konfiguračních tvůrců, soubory. config jsou statické a jejich nastavení je definováno určitou dobu před spuštěním aplikace.</span><span class="sxs-lookup"><span data-stu-id="87f14-365">Without configuration builders, .config files are static, and their settings are defined some time before an application is launched.</span></span>

<span data-ttu-id="87f14-366">Chcete-li vytvořit vlastního tvůrce konfigurace, odvodit svého tvůrce z abstraktní <xref:System.Configuration.ConfigurationBuilder> třídy a přepsat jeho <xref:System.Configuration.ConfigurationBuilder.ProcessConfigurationSection%2A?displayProperty=nameWithType> a <xref:System.Configuration.ConfigurationBuilder.ProcessRawXml%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="87f14-366">To create a custom configuration builder, you derive your builder from the abstract <xref:System.Configuration.ConfigurationBuilder> class and override its <xref:System.Configuration.ConfigurationBuilder.ProcessConfigurationSection%2A?displayProperty=nameWithType> and <xref:System.Configuration.ConfigurationBuilder.ProcessRawXml%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="87f14-367">Můžete také definovat své sestavovatele v souboru. config.</span><span class="sxs-lookup"><span data-stu-id="87f14-367">You also define your builders in your .config file.</span></span> <span data-ttu-id="87f14-368">Další informace najdete v části "tvůrci konfigurace" v příspěvku na blogu [.NET Framework 4.7.1 ASP.NET a konfigurační funkce](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) .</span><span class="sxs-lookup"><span data-stu-id="87f14-368">For more information, see the "Configuration Builders" section in the [.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog post.</span></span>

<span data-ttu-id="87f14-369">**Detekce funkcí za běhu**</span><span class="sxs-lookup"><span data-stu-id="87f14-369">**Run-time feature detection**</span></span>

<span data-ttu-id="87f14-370"><xref:System.Runtime.CompilerServices.RuntimeFeature?displayProperty=nameWithType>Třída poskytuje mechanismus pro určení, zda je předdefinovaná funkce v dané implementaci rozhraní .NET podporována v době kompilace nebo v době běhu.</span><span class="sxs-lookup"><span data-stu-id="87f14-370">The <xref:System.Runtime.CompilerServices.RuntimeFeature?displayProperty=nameWithType> class provides a mechanism for determine whether a predefined feature is supported on a given .NET implementation at compile time or run time.</span></span> <span data-ttu-id="87f14-371">V době kompilace může kompilátor ověřit, zda zadané pole existuje k určení, zda je funkce podporována. Pokud ano, může vygenerovat kód, který tuto funkci využívá.</span><span class="sxs-lookup"><span data-stu-id="87f14-371">At compile time, a compiler can check whether a specified field exists to determine whether the feature is supported; if so, it can emit code that takes advantage of that feature.</span></span> <span data-ttu-id="87f14-372">V době běhu může aplikace zavolat <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported%2A?displayProperty=nameWithType> metodu před vygenerováním kódu za běhu.</span><span class="sxs-lookup"><span data-stu-id="87f14-372">At run time, an application can call the <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported%2A?displayProperty=nameWithType> method before emitting code at runtime.</span></span> <span data-ttu-id="87f14-373">Další informace najdete v tématu [Přidání pomocné metody pro popis funkcí podporovaných modulem runtime](https://github.com/dotnet/corefx/issues/17116).</span><span class="sxs-lookup"><span data-stu-id="87f14-373">For more information, see [Add helper method to describe features supported by the runtime](https://github.com/dotnet/corefx/issues/17116).</span></span>

<span data-ttu-id="87f14-374">**Typy řazené kolekce členů mají hodnotu serializovat.**</span><span class="sxs-lookup"><span data-stu-id="87f14-374">**Value tuple types are serializable**</span></span>

<span data-ttu-id="87f14-375">Počínaje .NET Framework 4.7.1 <xref:System.ValueTuple?displayProperty=nameWithType> a přidružené obecné typy jsou označeny jako [serializovatelný](xref:System.SerializableAttribute), což umožňuje binární serializaci.</span><span class="sxs-lookup"><span data-stu-id="87f14-375">Starting with .NET Framework 4.7.1, <xref:System.ValueTuple?displayProperty=nameWithType> and its associated generic types are marked as [Serializable](xref:System.SerializableAttribute), which allows binary serialization.</span></span> <span data-ttu-id="87f14-376">To by mělo být pro snazší migraci typů řazené kolekce členů, například <xref:System.Tuple%603> a <xref:System.Tuple%604> , k hodnotám řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="87f14-376">This should make migrating Tuple types, such as <xref:System.Tuple%603> and <xref:System.Tuple%604>, to value tuple types easier.</span></span> <span data-ttu-id="87f14-377">Další informace naleznete v příspěvku "Compiler--ValueTuple je serializovatelný" v příspěvku blogu [.NET Framework 4.7.1 runtime a funkce kompilátoru](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) .</span><span class="sxs-lookup"><span data-stu-id="87f14-377">For more information, see "Compiler -- ValueTuple is Serializable" in the [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog post.</span></span>

<span data-ttu-id="87f14-378">**Podpora odkazů jen pro čtení**</span><span class="sxs-lookup"><span data-stu-id="87f14-378">**Support for read-only references**</span></span>

<span data-ttu-id="87f14-379">.NET Framework 4.7.1 přidá <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="87f14-379">.NET Framework 4.7.1 adds the <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="87f14-380">Tento atribut používají kompilátory jazyka k označení členů, kteří mají návratový typ nebo parametry ref jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="87f14-380">This attribute is used by language compilers to mark members that have read-only ref return types or parameters.</span></span> <span data-ttu-id="87f14-381">Další informace najdete v příspěvku na blogu o kompilátoru – podpora pro ReadOnlyReferences v tématu [.NET Framework 4.7.1 runtime a funkce kompilátoru](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) .</span><span class="sxs-lookup"><span data-stu-id="87f14-381">For more information, see "Compiler -- Support for ReadOnlyReferences" in the [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog post.</span></span> <span data-ttu-id="87f14-382">Informace o vrácených hodnotách ref naleznete v tématech [ref Return Values a Locals (příručka C#)](../../csharp/programming-guide/classes-and-structs/ref-returns.md) a [ref Return values (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/ref-return-values.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-382">For information on ref return values, see [Ref return values and ref locals (C# Guide)](../../csharp/programming-guide/classes-and-structs/ref-returns.md) and [Ref return values (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/ref-return-values.md).</span></span>

<a name="clr"></a>

#### <a name="common-language-runtime-clr"></a><span data-ttu-id="87f14-383">Common language runtime (CLR)</span><span class="sxs-lookup"><span data-stu-id="87f14-383">Common language runtime (CLR)</span></span>

<span data-ttu-id="87f14-384">**Vylepšení výkonu shromažďování paměti**</span><span class="sxs-lookup"><span data-stu-id="87f14-384">**Garbage collection performance improvements**</span></span>

<span data-ttu-id="87f14-385">Změny uvolňování paměti (GC) v .NET Framework 4.7.1 vylepšit celkový výkon, zejména pro přidělení LOH (large object Heap).</span><span class="sxs-lookup"><span data-stu-id="87f14-385">Changes to garbage collection (GC) in .NET Framework 4.7.1 improve overall performance, especially for large object heap (LOH) allocations.</span></span> <span data-ttu-id="87f14-386">V .NET Framework 4.7.1 jsou používány samostatné zámky pro LOH (Small Object Heap) a LOH alokace, což umožňuje přidělení, když je uvolňování paměti SOH na pozadí.</span><span class="sxs-lookup"><span data-stu-id="87f14-386">In .NET Framework 4.7.1, separate locks are used for small object heap (SOH) and LOH allocations, which allows LOH allocations to occur when background GC is sweeping the SOH.</span></span> <span data-ttu-id="87f14-387">V důsledku toho by aplikace, které vytvářejí velký počet přidělení LOH, měly vidět snížení kolizí uzamčení přidělení a lepší výkon.</span><span class="sxs-lookup"><span data-stu-id="87f14-387">As a result, applications that make a large number of LOH allocations should see a reduction in allocation lock contention and improved performance.</span></span> <span data-ttu-id="87f14-388">Další informace najdete v části "prostředí runtime – vylepšení výkonu GC" v příspěvku blogu [.NET Framework 4.7.1 runtime a funkce kompilátoru](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) .</span><span class="sxs-lookup"><span data-stu-id="87f14-388">For more information, see the "Runtime -- GC Performance Improvements" section in the [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog post.</span></span>

<a name="net471"/>

#### <a name="networking"></a><span data-ttu-id="87f14-389">Sítě</span><span class="sxs-lookup"><span data-stu-id="87f14-389">Networking</span></span>

<span data-ttu-id="87f14-390">**Podpora SHA-2 pro Message. HashAlgorithm**</span><span class="sxs-lookup"><span data-stu-id="87f14-390">**SHA-2 support for Message.HashAlgorithm**</span></span>

<span data-ttu-id="87f14-391">V .NET Framework 4,7 a starších verzích <xref:System.Messaging.Message.HashAlgorithm%2A?displayProperty=nameWithType> podporuje vlastnost <xref:System.Messaging.HashAlgorithm.Md5?displayProperty=nameWithType> pouze hodnoty a <xref:System.Messaging.HashAlgorithm.Sha?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="87f14-391">In .NET Framework 4.7 and earlier versions, the <xref:System.Messaging.Message.HashAlgorithm%2A?displayProperty=nameWithType> property supported values of <xref:System.Messaging.HashAlgorithm.Md5?displayProperty=nameWithType> and <xref:System.Messaging.HashAlgorithm.Sha?displayProperty=nameWithType> only.</span></span> <span data-ttu-id="87f14-392">Počínaje .NET Framework 4.7.1, <xref:System.Messaging.HashAlgorithm.Sha256?displayProperty=nameWithType> , a <xref:System.Messaging.HashAlgorithm.Sha384?displayProperty=nameWithType> <xref:System.Messaging.HashAlgorithm.Sha512?displayProperty=nameWithType> jsou také podporovány.</span><span class="sxs-lookup"><span data-stu-id="87f14-392">Starting with .NET Framework 4.7.1, <xref:System.Messaging.HashAlgorithm.Sha256?displayProperty=nameWithType>, <xref:System.Messaging.HashAlgorithm.Sha384?displayProperty=nameWithType>, and <xref:System.Messaging.HashAlgorithm.Sha512?displayProperty=nameWithType> are also supported.</span></span> <span data-ttu-id="87f14-393">Určuje, zda je tato hodnota skutečně používána, záleží na službě MSMQ, protože <xref:System.Messaging.Message> samotná instance neprovádí žádné hodnoty hash, ale jednoduše předává hodnoty do služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="87f14-393">Whether this value is actually used depends on MSMQ, since the <xref:System.Messaging.Message> instance itself does no hashing but simply passes on values to MSMQ.</span></span> <span data-ttu-id="87f14-394">Další informace najdete v tomto příspěvku na blogu podpora SHA-2 pro Message. HashAlgorithm v části [.NET Framework 4.7.1 ASP.NET a konfigurační funkce](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) .</span><span class="sxs-lookup"><span data-stu-id="87f14-394">For more information, see the "SHA-2 support for Message.HashAlgorithm" section in the [.NET Framework 4.7.1 ASP.NET and Configuration features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog post.</span></span>

<a name="asp-net471"></a>

#### <a name="aspnet"></a><span data-ttu-id="87f14-395">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="87f14-395">ASP.NET</span></span>

<span data-ttu-id="87f14-396">**Kroky provádění v aplikacích ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="87f14-396">**Execution steps in ASP.NET applications**</span></span>

<span data-ttu-id="87f14-397">ASP.NET zpracovává požadavky v předdefinovaném kanálu, který zahrnuje 23 událostí.</span><span class="sxs-lookup"><span data-stu-id="87f14-397">ASP.NET processes requests in a predefined pipeline that includes 23 events.</span></span> <span data-ttu-id="87f14-398">ASP.NET spustí jednotlivé obslužné rutiny události jako krok provedení.</span><span class="sxs-lookup"><span data-stu-id="87f14-398">ASP.NET executes each event handler as an execution step.</span></span> <span data-ttu-id="87f14-399">Ve verzích ASP.NET až .NET Framework 4,7 nemůže ASP.NET z důvodu přepínání mezi nativními a spravovanými vlákny flowovat kontext spuštění.</span><span class="sxs-lookup"><span data-stu-id="87f14-399">In versions of ASP.NET up to .NET Framework 4.7, ASP.NET can't flow the execution context due to switching between native and managed threads.</span></span> <span data-ttu-id="87f14-400">Místo toho ASP.NET selektivní toky pouze <xref:System.Web.HttpContext> .</span><span class="sxs-lookup"><span data-stu-id="87f14-400">Instead, ASP.NET selectively flows only the <xref:System.Web.HttpContext>.</span></span> <span data-ttu-id="87f14-401">Počínaje .NET Framework 4.7.1 <xref:System.Web.HttpApplication.OnExecuteRequestStep(System.Action{System.Web.HttpContextBase,System.Action})?displayProperty=nameWithType> Metoda také umožňuje modulům obnovovat okolní data.</span><span class="sxs-lookup"><span data-stu-id="87f14-401">Starting with .NET Framework 4.7.1, the <xref:System.Web.HttpApplication.OnExecuteRequestStep(System.Action{System.Web.HttpContextBase,System.Action})?displayProperty=nameWithType> method also allows modules to restore ambient data.</span></span> <span data-ttu-id="87f14-402">Tato funkce je zaměřená na knihovny, které mají na starosti trasování, profilování, diagnostiku nebo transakce, například informace o toku spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="87f14-402">This feature is targeted at libraries concerned with tracing, profiling, diagnostics, or transactions, for example, that care about the execution flow of the application.</span></span> <span data-ttu-id="87f14-403">Další informace najdete v příspěvku na blogu věnovaném funkci "ASP.NET provádění kroku" v tématu [.NET Framework 4.7.1 ASP.NET a konfigurační funkce](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) .</span><span class="sxs-lookup"><span data-stu-id="87f14-403">For more information, see the "ASP.NET Execution Step Feature" in the [.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog post.</span></span>

<span data-ttu-id="87f14-404">**ASP.NET HttpCookie – analýza**</span><span class="sxs-lookup"><span data-stu-id="87f14-404">**ASP.NET HttpCookie parsing**</span></span>

<span data-ttu-id="87f14-405">.NET Framework 4.7.1 zahrnuje novou metodu, <xref:System.Web.HttpCookie.TryParse%2A?displayProperty=nameWithType> která poskytuje standardizovaný způsob, jak vytvořit <xref:System.Web.HttpCookie> objekt z řetězce a přesně přiřadit hodnoty souborů cookie, jako je datum vypršení platnosti a cesta.</span><span class="sxs-lookup"><span data-stu-id="87f14-405">.NET Framework 4.7.1 includes a new method, <xref:System.Web.HttpCookie.TryParse%2A?displayProperty=nameWithType>, that provides a standardized way to create an <xref:System.Web.HttpCookie> object from a string and accurately assign cookie values such as expiration date and path.</span></span> <span data-ttu-id="87f14-406">Další informace najdete v blogovém příspěvku "ASP.NET HttpCookie analyze" v blogu [.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) .</span><span class="sxs-lookup"><span data-stu-id="87f14-406">For more information, see "ASP.NET HttpCookie parsing" in the [.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog post.</span></span>

<span data-ttu-id="87f14-407">**Možnosti hash SHA-2 pro přihlašovací údaje ověřování ASP.NET Forms**</span><span class="sxs-lookup"><span data-stu-id="87f14-407">**SHA-2 hash options for ASP.NET forms authentication credentials**</span></span>

<span data-ttu-id="87f14-408">V .NET Framework 4,7 a starších verzích umožnili vývojářům ASP.NET ukládat přihlašovací údaje uživatele s hashými hesly v konfiguračních souborech pomocí MD5 nebo SHA1.</span><span class="sxs-lookup"><span data-stu-id="87f14-408">In .NET Framework 4.7 and earlier versions, ASP.NET allowed developers to store user credentials with hashed passwords in configuration files using either MD5 or SHA1.</span></span> <span data-ttu-id="87f14-409">Počínaje .NET Framework 4.7.1, ASP.NET podporuje také nové zabezpečené možnosti hash SHA-2, jako jsou SHA256, SHA384 a SHA512.</span><span class="sxs-lookup"><span data-stu-id="87f14-409">Starting with .NET Framework 4.7.1, ASP.NET also supports new secure SHA-2 hash options such as SHA256, SHA384, and SHA512.</span></span> <span data-ttu-id="87f14-410">SHA1 zůstává výchozí a v konfiguračním souboru webu lze definovat jiný algoritmus hash, který není výchozí.</span><span class="sxs-lookup"><span data-stu-id="87f14-410">SHA1 remains the default, and a non-default hash algorithm can be defined in the web configuration file.</span></span> <span data-ttu-id="87f14-411">Příklad:</span><span class="sxs-lookup"><span data-stu-id="87f14-411">For example:</span></span>

```xml
<system.web>
    <authentication mode="Forms">
        <forms loginUrl="~/login.aspx">
          <credentials passwordFormat="SHA512">
            <user name="jdoe" password="6D003E98EA1C7F04ABF8FCB375388907B7F3EE06F278DB966BE960E7CBBD103DF30CA6D61F7E7FD981B2E4E3A64D43C836A4BEDCA165C33B163E6BCDC538A664" />
          </credentials>
        </forms>
    </authentication>
</system.web>
```

<a name="v47"></a>

## <a name="whats-new-in-net-framework-47"></a><span data-ttu-id="87f14-412">Co je nového v .NET Framework 4,7</span><span class="sxs-lookup"><span data-stu-id="87f14-412">What's new in .NET Framework 4.7</span></span>

<span data-ttu-id="87f14-413">.NET Framework 4,7 obsahuje nové funkce v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="87f14-413">.NET Framework 4.7 includes new features in the following areas:</span></span>

- [<span data-ttu-id="87f14-414">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="87f14-414">Base classes</span></span>](#Core47)
- [<span data-ttu-id="87f14-415">Sítě</span><span class="sxs-lookup"><span data-stu-id="87f14-415">Networking</span></span>](#net47)
- [<span data-ttu-id="87f14-416">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="87f14-416">ASP.NET</span></span>](#ASP-NET47)
- [<span data-ttu-id="87f14-417">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="87f14-417">Windows Communication Foundation (WCF)</span></span>](#wcf47)
- [<span data-ttu-id="87f14-418">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="87f14-418">Windows Forms</span></span>](#wf47)
- [<span data-ttu-id="87f14-419">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="87f14-419">Windows Presentation Foundation (WPF)</span></span>](#WPF47)

<span data-ttu-id="87f14-420">Seznam nových rozhraní API přidaných do .NET Framework 4,7 najdete v článku [změny rozhraní api .NET Framework 4,7](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="87f14-420">For a list of new APIs added to .NET Framework 4.7, see [.NET Framework 4.7 API Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md) on GitHub.</span></span> <span data-ttu-id="87f14-421">Seznam vylepšení funkcí a oprav chyb v .NET Framework 4,7 naleznete v části [.NET Framework 4,7 seznam změn](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="87f14-421">For a list of feature improvements and bug fixes in .NET Framework 4.7, see [.NET Framework 4.7 List of Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md) on GitHub.</span></span> <span data-ttu-id="87f14-422">Další informace najdete v tématu [oznámení .NET Framework 4,7](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-7/) na blogu .NET.</span><span class="sxs-lookup"><span data-stu-id="87f14-422">For more information, see [Announcing the .NET Framework 4.7](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-7/) in the .NET blog.</span></span>

<a name="Core47"></a>

#### <a name="base-classes"></a><span data-ttu-id="87f14-423">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="87f14-423">Base classes</span></span>

<span data-ttu-id="87f14-424">.NET Framework 4,7 vylepšuje serializaci <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> :</span><span class="sxs-lookup"><span data-stu-id="87f14-424">.NET Framework 4.7 improves serialization by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:</span></span>

<span data-ttu-id="87f14-425">**Vylepšená funkce s použitím kryptografie s eliptickou křivkou (ECC)**\*</span><span class="sxs-lookup"><span data-stu-id="87f14-425">**Enhanced functionality with Elliptic Curve Cryptography (ECC)**\*</span></span>

<span data-ttu-id="87f14-426">V .NET Framework 4,7 `ImportParameters(ECParameters)` byly metody přidány do <xref:System.Security.Cryptography.ECDsa> tříd a, <xref:System.Security.Cryptography.ECDiffieHellman> aby objekt mohl představovat již zavedený klíč.</span><span class="sxs-lookup"><span data-stu-id="87f14-426">In .NET Framework 4.7, `ImportParameters(ECParameters)` methods were added to the <xref:System.Security.Cryptography.ECDsa> and <xref:System.Security.Cryptography.ECDiffieHellman> classes to allow for an object to represent an already-established key.</span></span> <span data-ttu-id="87f14-427">`ExportParameters(Boolean)`Metoda byla přidána také pro export klíče pomocí explicitních parametrů křivky.</span><span class="sxs-lookup"><span data-stu-id="87f14-427">An `ExportParameters(Boolean)` method was also added for exporting the key using explicit curve parameters.</span></span>

<span data-ttu-id="87f14-428">.NET Framework 4,7 také přidává podporu pro další křivky (včetně sady křivky Brainpool) a přidala předdefinované definice pro usnadnění vytváření prostřednictvím nových <xref:System.Security.Cryptography.ECDsa.Create%2A> a <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> výrobních metod.</span><span class="sxs-lookup"><span data-stu-id="87f14-428">.NET Framework 4.7 also adds support for additional curves (including the Brainpool curve suite), and has added predefined definitions for ease-of-creation through the new <xref:System.Security.Cryptography.ECDsa.Create%2A> and <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> factory methods.</span></span>

<span data-ttu-id="87f14-429">Na GitHubu můžete vidět [příklad kryptografických vylepšení .NET Framework 4,7](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e) .</span><span class="sxs-lookup"><span data-stu-id="87f14-429">You can see an [example of .NET Framework 4.7 cryptography improvements](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e) on GitHub.</span></span>

<span data-ttu-id="87f14-430">**Lepší podpora kontrolních znaků DataContractJsonSerializer**</span><span class="sxs-lookup"><span data-stu-id="87f14-430">**Better support for control characters by the DataContractJsonSerializer**</span></span>

<span data-ttu-id="87f14-431">V .NET Framework 4,7 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> třída serializace řídicích znaků v souladu se standardem ECMAScript 6.</span><span class="sxs-lookup"><span data-stu-id="87f14-431">In .NET Framework 4.7, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> class serializes control characters in conformity with the ECMAScript 6 standard.</span></span> <span data-ttu-id="87f14-432">Toto chování je ve výchozím nastavení povolené pro aplikace, které cílí na .NET Framework 4,7, a je funkce pro přihlášení k aplikacím, které běží v .NET Framework 4,7, ale cílí na předchozí verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="87f14-432">This behavior is enabled by default for applications that target .NET Framework 4.7, and is an opt-in feature for applications that are running under .NET Framework 4.7 but target a previous version of .NET Framework.</span></span> <span data-ttu-id="87f14-433">Další informace najdete v části [Kompatibilita aplikací](../migration-guide/application-compatibility.md) .</span><span class="sxs-lookup"><span data-stu-id="87f14-433">For more information, see the [Application compatibility](../migration-guide/application-compatibility.md) section.</span></span>

<a name="net47"></a>

#### <a name="networking"></a><span data-ttu-id="87f14-434">Sítě</span><span class="sxs-lookup"><span data-stu-id="87f14-434">Networking</span></span>

<span data-ttu-id="87f14-435">.NET Framework 4,7 přidává následující funkci související se sítí:</span><span class="sxs-lookup"><span data-stu-id="87f14-435">.NET Framework 4.7 adds the following network-related feature:</span></span>

<span data-ttu-id="87f14-436">**Výchozí podpora operačního systému pro protokoly TLS**\*</span><span class="sxs-lookup"><span data-stu-id="87f14-436">**Default operating system support for TLS protocols**\*</span></span>

<span data-ttu-id="87f14-437">Zásobník protokolu TLS, který používají <xref:System.Net.Security.SslStream?displayProperty=nameWithType> komponenty a součásti v zásobníku, jako jsou http, FTP a SMTP, umožňuje vývojářům používat výchozí protokoly TLS podporované operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="87f14-437">The TLS stack, which is used by <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and up-stack components such as HTTP, FTP, and SMTP, allows developers to use the default TLS protocols supported by the operating system.</span></span> <span data-ttu-id="87f14-438">Vývojáři už nemusejí mít pevně zakódování verze TLS.</span><span class="sxs-lookup"><span data-stu-id="87f14-438">Developers need no longer hard-code a TLS version.</span></span>

<a name="ASP-NET47"></a>

#### <a name="aspnet"></a><span data-ttu-id="87f14-439">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="87f14-439">ASP.NET</span></span>

<span data-ttu-id="87f14-440">V .NET Framework 4,7 obsahuje ASP.NET následující nové funkce:</span><span class="sxs-lookup"><span data-stu-id="87f14-440">In .NET Framework 4.7, ASP.NET includes the following new features:</span></span>

<span data-ttu-id="87f14-441">**Rozšiřitelnost mezipaměti objektů**</span><span class="sxs-lookup"><span data-stu-id="87f14-441">**Object Cache Extensibility**</span></span>

<span data-ttu-id="87f14-442">Počínaje .NET Framework 4,7 přidá ASP.NET novou sadu rozhraní API, která vývojářům umožní nahradit výchozí implementaci ASP.NET pro ukládání objektů do paměti a monitorování paměti.</span><span class="sxs-lookup"><span data-stu-id="87f14-442">Starting with .NET Framework 4.7, ASP.NET adds a new set of APIs that allow developers to replace the default ASP.NET implementations for in-memory object caching and memory monitoring.</span></span> <span data-ttu-id="87f14-443">Vývojáři teď můžou nahradit některou z následujících tří součástí, pokud ASP.NET implementace není adekvátní:</span><span class="sxs-lookup"><span data-stu-id="87f14-443">Developers can now replace any of the following three components if the ASP.NET implementation is not adequate:</span></span>

- <span data-ttu-id="87f14-444">**Úložiště mezipaměti objektů**.</span><span class="sxs-lookup"><span data-stu-id="87f14-444">**Object Cache Store**.</span></span> <span data-ttu-id="87f14-445">Při použití konfiguračního oddílu Noví poskytovatelé mezipaměti můžou vývojáři připojit nové implementace mezipaměti objektů pro aplikaci ASP.NET pomocí nového rozhraní **ICacheStoreProvider** .</span><span class="sxs-lookup"><span data-stu-id="87f14-445">By using the new cache providers configuration section, developers can plug in new implementations of an object cache for an ASP.NET application by using the new **ICacheStoreProvider** interface.</span></span>

- <span data-ttu-id="87f14-446">**Monitorování paměti**.</span><span class="sxs-lookup"><span data-stu-id="87f14-446">**Memory monitoring**.</span></span> <span data-ttu-id="87f14-447">Výchozí monitorování paměti v ASP.NET upozorní aplikace, když běží blízko nakonfigurovaného limitu privátních bajtů pro daný proces, nebo když má počítač nedostatek celkového dostupné fyzické paměti RAM.</span><span class="sxs-lookup"><span data-stu-id="87f14-447">The default memory monitor in ASP.NET notifies applications when they are running close to the configured private bytes limit for the process, or when the machine is low on total available physical RAM.</span></span> <span data-ttu-id="87f14-448">Když jsou tato omezení blízko, jsou aktivována oznámení.</span><span class="sxs-lookup"><span data-stu-id="87f14-448">When these limits are near, notifications are fired.</span></span> <span data-ttu-id="87f14-449">U některých aplikací se oznámení aktivují příliš blízko nakonfigurovaných limitů, aby bylo možné reakce na užitečné.</span><span class="sxs-lookup"><span data-stu-id="87f14-449">For some applications, notifications are fired too close to the configured limits to allow for useful reactions.</span></span> <span data-ttu-id="87f14-450">Vývojáři teď můžou zapisovat vlastní monitory paměti, které nahradí výchozí hodnotu pomocí <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=nameWithType> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="87f14-450">Developers can now write their own memory monitors to replace the default by using the <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=nameWithType> property.</span></span>

- <span data-ttu-id="87f14-451">**Reakce na limit paměti**.</span><span class="sxs-lookup"><span data-stu-id="87f14-451">**Memory Limit Reactions**.</span></span> <span data-ttu-id="87f14-452">Ve výchozím nastavení se ASP.NET pokusí oříznout mezipaměť objektů a pravidelně volat, <xref:System.GC.Collect%2A?displayProperty=nameWithType> Pokud je limit procesu privátního bajtu blízko.</span><span class="sxs-lookup"><span data-stu-id="87f14-452">By default, ASP.NET attempts to trim the object cache and periodically call <xref:System.GC.Collect%2A?displayProperty=nameWithType> when the private byte process limit is near.</span></span> <span data-ttu-id="87f14-453">U některých aplikací je frekvence volání <xref:System.GC.Collect%2A?displayProperty=nameWithType> nebo množství mezipaměti, která je oříznuta, neefektivní.</span><span class="sxs-lookup"><span data-stu-id="87f14-453">For some applications, the frequency of calls to <xref:System.GC.Collect%2A?displayProperty=nameWithType> or the amount of cache that is trimmed are inefficient.</span></span> <span data-ttu-id="87f14-454">Vývojáři teď můžou nahradit nebo doplnit výchozí chování tím, že se přihlásí k odběru **IObserver** implementace do monitorování paměti aplikace.</span><span class="sxs-lookup"><span data-stu-id="87f14-454">Developers can now replace or supplement the default behavior by subscribing **IObserver** implementations to the application's memory monitor.</span></span>

<a name="wcf47"></a>

#### <a name="windows-communication-foundation-wcf"></a><span data-ttu-id="87f14-455">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="87f14-455">Windows Communication Foundation (WCF)</span></span>

<span data-ttu-id="87f14-456">Windows Communication Foundation (WCF) přidá následující funkce a změny:</span><span class="sxs-lookup"><span data-stu-id="87f14-456">Windows Communication Foundation (WCF) adds the following features and changes:</span></span>

<span data-ttu-id="87f14-457">**Možnost konfigurovat výchozí nastavení zabezpečení zpráv na TLS 1,1 nebo TLS 1,2**</span><span class="sxs-lookup"><span data-stu-id="87f14-457">**Ability to configure the default message security settings to TLS 1.1 or TLS 1.2**</span></span>

<span data-ttu-id="87f14-458">Počínaje .NET Framework 4,7 umožňuje WCF nakonfigurovat kromě protokolu SSL 3,0 a TSL 1,0 i možnost TSL 1,1 nebo TLS 1,2 jako výchozí protokol zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="87f14-458">Starting with .NET Framework 4.7, WCF allows you to configure TSL 1.1 or TLS 1.2 in addition to SSL 3.0 and TSL 1.0 as the default message security protocol.</span></span> <span data-ttu-id="87f14-459">Toto je nastavení výslovného souhlasu; Pokud ho chcete povolit, musíte do konfiguračního souboru aplikace přidat následující položku:</span><span class="sxs-lookup"><span data-stu-id="87f14-459">This is an opt-in setting; to enable it, you must add the following entry to your application configuration file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
</runtime>
```

<span data-ttu-id="87f14-460">**Vylepšená spolehlivost aplikací WCF a serializace WCF**</span><span class="sxs-lookup"><span data-stu-id="87f14-460">**Improved reliability of WCF applications and WCF serialization**</span></span>

<span data-ttu-id="87f14-461">WCF zahrnuje řadu změn kódu, které eliminují konflikty časování, což zvyšuje výkon a spolehlivost možností serializace.</span><span class="sxs-lookup"><span data-stu-id="87f14-461">WCF includes a number of code changes that eliminate race conditions, thereby improving performance and the reliability of serialization options.</span></span> <span data-ttu-id="87f14-462">Mezi ně patří:</span><span class="sxs-lookup"><span data-stu-id="87f14-462">These include:</span></span>

- <span data-ttu-id="87f14-463">Lepší podpora pro kombinování asynchronního a synchronního kódu v voláních **Připojení SocketConnection bylo. BeginRead** a **Připojení SocketConnection bylo. Read**.</span><span class="sxs-lookup"><span data-stu-id="87f14-463">Better support for mixing asynchronous and synchronous code in calls to **SocketConnection.BeginRead** and **SocketConnection.Read**.</span></span>
- <span data-ttu-id="87f14-464">Lepší spolehlivost při přerušení připojení pomocí **SharedConnectionListener** a **DuplexChannelBinder**.</span><span class="sxs-lookup"><span data-stu-id="87f14-464">Improved reliability when aborting a connection with **SharedConnectionListener** and **DuplexChannelBinder**.</span></span>
- <span data-ttu-id="87f14-465">Zlepšená spolehlivost operací serializace při volání <xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="87f14-465">Improved reliability of serialization operations when calling the <xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=nameWithType> method.</span></span>
- <span data-ttu-id="87f14-466">Lepší spolehlivost při odebírání nástroje Wait voláním metody **ChannelSynchronizer. RemoveWaiter** .</span><span class="sxs-lookup"><span data-stu-id="87f14-466">Improved reliability when removing a waiter by calling the **ChannelSynchronizer.RemoveWaiter** method.</span></span>

<a name="wf47"></a>

#### <a name="windows-forms"></a><span data-ttu-id="87f14-467">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="87f14-467">Windows Forms</span></span>

<span data-ttu-id="87f14-468">V .NET Framework 4,7 model Windows Forms vylepšuje podporu pro monitory s vysokým rozlišením DPI.</span><span class="sxs-lookup"><span data-stu-id="87f14-468">In .NET Framework 4.7, Windows Forms improves support for high DPI monitors.</span></span>

<span data-ttu-id="87f14-469">**Podpora vysokého rozlišení DPI**</span><span class="sxs-lookup"><span data-stu-id="87f14-469">**High DPI support**</span></span>

<span data-ttu-id="87f14-470">Počínaje aplikacemi, které cílí na .NET Framework 4,7, .NET Framework funkce vysokého rozlišení DPI a podpora dynamického DPI pro model Windows Forms aplikace.</span><span class="sxs-lookup"><span data-stu-id="87f14-470">Starting with applications that target .NET Framework 4.7, the .NET Framework features high DPI and dynamic DPI support for Windows Forms applications.</span></span> <span data-ttu-id="87f14-471">Podpora vysokého rozlišení DPI vylepšuje rozložení a vzhled formulářů a ovládacích prvků na obrazovkách s vysokým rozlišením DPI.</span><span class="sxs-lookup"><span data-stu-id="87f14-471">High DPI support improves the layout and appearance of forms and controls on high DPI monitors.</span></span> <span data-ttu-id="87f14-472">Dynamické DPI mění rozložení a vzhled formulářů a ovládacích prvků, když uživatel změní v běžící aplikaci Měřítko DPI nebo zobrazení.</span><span class="sxs-lookup"><span data-stu-id="87f14-472">Dynamic DPI changes the layout and appearance of forms and controls when the user changes the DPI or display scale factor of a running application.</span></span>

<span data-ttu-id="87f14-473">Podpora vysokého rozlišení DPI je funkce výslovného souhlasu, kterou nakonfigurujete tak, že definujete [\<System.Windows.Forms.ConfigurationSection>](../configure-apps/file-schema/winforms/index.md) oddíl v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="87f14-473">High DPI support is an opt-in feature that you configure by defining a [\<System.Windows.Forms.ConfigurationSection>](../configure-apps/file-schema/winforms/index.md) section in your application configuration file.</span></span> <span data-ttu-id="87f14-474">Další informace o přidání podpory vysokého rozlišení DPI a dynamické podpory DPI do vaší aplikace model Windows Forms najdete [v tématu Podpora vysokého rozlišení DPI v model Windows Forms](../winforms/high-dpi-support-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-474">For more information on adding high DPI support and dynamic DPI support to your Windows Forms application, see [High DPI Support in Windows Forms](../winforms/high-dpi-support-in-windows-forms.md).</span></span>

<a name="WPF47"></a>

#### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="87f14-475">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="87f14-475">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="87f14-476">V .NET Framework 4,7 zahrnuje WPF následující vylepšení:</span><span class="sxs-lookup"><span data-stu-id="87f14-476">In .NET Framework 4.7, WPF includes the following enhancements:</span></span>

<span data-ttu-id="87f14-477">**Podpora pro sadu dotykové a stylusové sady založená na zprávách Windows WM_POINTER**</span><span class="sxs-lookup"><span data-stu-id="87f14-477">**Support for a touch/stylus stack based on Windows WM_POINTER messages**</span></span>

<span data-ttu-id="87f14-478">Teď máte možnost používat pro [WM_POINTER zprávy](https://docs.microsoft.com/previous-versions/windows/desktop/InputMsg/messages) místo platformy Windows Ink Services (Wispr) k dispozici tónovou nebo stylusovou sadu.</span><span class="sxs-lookup"><span data-stu-id="87f14-478">You now have the option of using a touch/stylus stack based on [WM_POINTER messages](https://docs.microsoft.com/previous-versions/windows/desktop/InputMsg/messages) instead of the Windows Ink Services Platform (WISP).</span></span> <span data-ttu-id="87f14-479">Toto je funkce výslovného souhlasu v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="87f14-479">This is an opt-in feature in .NET Framework.</span></span> <span data-ttu-id="87f14-480">Další informace najdete v části [Kompatibilita aplikací](../migration-guide/application-compatibility.md) .</span><span class="sxs-lookup"><span data-stu-id="87f14-480">For more information, see the [Application compatibility](../migration-guide/application-compatibility.md) section.</span></span>

<span data-ttu-id="87f14-481">**Nová implementace pro rozhraní API pro tisk WPF**</span><span class="sxs-lookup"><span data-stu-id="87f14-481">**New implementation for WPF printing APIs**</span></span>

<span data-ttu-id="87f14-482">Rozhraní API pro tisk v platformě WPF ve <xref:System.Printing.PrintQueue?displayProperty=nameWithType> třídě volají [rozhraní API pro tiskové dokumenty](/windows/desktop/printdocs/tailored-app-printing-api) systému Windows namísto zastaralých [tiskových rozhraní XPS](/windows/desktop/printdocs/xps-printing).</span><span class="sxs-lookup"><span data-stu-id="87f14-482">WPF's printing APIs in the <xref:System.Printing.PrintQueue?displayProperty=nameWithType> class call the Windows [Print Document Package API](/windows/desktop/printdocs/tailored-app-printing-api) instead of the deprecated [XPS Print API](/windows/desktop/printdocs/xps-printing).</span></span> <span data-ttu-id="87f14-483">Dopad této změny na kompatibilitu aplikace naleznete v části [Kompatibilita aplikací](../migration-guide/application-compatibility.md) .</span><span class="sxs-lookup"><span data-stu-id="87f14-483">For the impact of this change on application compatibility, see the [Application compatibility](../migration-guide/application-compatibility.md) section.</span></span>

<a name="v462"></a>

## <a name="whats-new-in-net-framework-462"></a><span data-ttu-id="87f14-484">Co je nového v .NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="87f14-484">What's new in .NET Framework 4.6.2</span></span>

<span data-ttu-id="87f14-485">.NET Framework 4.6.2 zahrnuje nové funkce v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="87f14-485">The .NET Framework 4.6.2 includes new features in the following areas:</span></span>

- [<span data-ttu-id="87f14-486">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="87f14-486">ASP.NET</span></span>](#ASPNET462)

- [<span data-ttu-id="87f14-487">Kategorie znaků</span><span class="sxs-lookup"><span data-stu-id="87f14-487">Character categories</span></span>](#Strings)

- [<span data-ttu-id="87f14-488">Kryptografie</span><span class="sxs-lookup"><span data-stu-id="87f14-488">Cryptography</span></span>](#Crypto462)

- [<span data-ttu-id="87f14-489">SqlClient</span><span class="sxs-lookup"><span data-stu-id="87f14-489">SqlClient</span></span>](#SQLClient)

- [<span data-ttu-id="87f14-490">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="87f14-490">Windows Communication Foundation</span></span>](#WCF)

- [<span data-ttu-id="87f14-491">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="87f14-491">Windows Presentation Foundation (WPF)</span></span>](#WPF462)

- [<span data-ttu-id="87f14-492">Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="87f14-492">Windows Workflow Foundation (WF)</span></span>](#WF462)

- [<span data-ttu-id="87f14-493">ClickOnce</span><span class="sxs-lookup"><span data-stu-id="87f14-493">ClickOnce</span></span>](#clickonce-1)

- [<span data-ttu-id="87f14-494">Převod aplikací model Windows Forms a WPF na aplikace pro UWP</span><span class="sxs-lookup"><span data-stu-id="87f14-494">Converting Windows Forms and WPF apps to UWP apps</span></span>](#UWPConvert)

- [<span data-ttu-id="87f14-495">Vylepšení ladění</span><span class="sxs-lookup"><span data-stu-id="87f14-495">Debugging improvements</span></span>](#Debug462)

<span data-ttu-id="87f14-496">Seznam nových rozhraní API přidaných do .NET Framework 4.6.2 najdete v tématu [.NET Framework změn rozhraní API 4.6.2](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="87f14-496">For a list of new APIs added to .NET Framework 4.6.2, see [.NET Framework 4.6.2 API Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) on GitHub.</span></span> <span data-ttu-id="87f14-497">Seznam vylepšení funkcí a oprav chyb v .NET Framework 4.6.2 najdete v článku [.NET Framework 4.6.2 seznam změn](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-changes.md) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="87f14-497">For a list of feature improvements and bug fixes in .NET Framework 4.6.2, see [.NET Framework 4.6.2 List of Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-changes.md) on GitHub.</span></span> <span data-ttu-id="87f14-498">Další informace najdete v tématu [oznámení .NET Framework 4.6.2](https://devblogs.microsoft.com/dotnet/announcing-net-framework-4-6-2/) na blogu .NET.</span><span class="sxs-lookup"><span data-stu-id="87f14-498">For more information, see [Announcing .NET Framework 4.6.2](https://devblogs.microsoft.com/dotnet/announcing-net-framework-4-6-2/) in the .NET blog.</span></span>

<a name="ASPNET462"></a>

### <a name="aspnet"></a><span data-ttu-id="87f14-499">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="87f14-499">ASP.NET</span></span>

<span data-ttu-id="87f14-500">ASP.NET v .NET Framework 4.6.2 zahrnuje následující vylepšení:</span><span class="sxs-lookup"><span data-stu-id="87f14-500">In the .NET Framework 4.6.2, ASP.NET includes the following enhancements:</span></span>

<span data-ttu-id="87f14-501">**Vylepšená podpora pro lokalizované chybové zprávy v validátorech datových poznámek**</span><span class="sxs-lookup"><span data-stu-id="87f14-501">**Improved support for localized error messages in data annotation validators**</span></span>

<span data-ttu-id="87f14-502">Validátory datových poznámek umožňují provádět ověřování přidáním jednoho nebo více atributů do vlastnosti třídy.</span><span class="sxs-lookup"><span data-stu-id="87f14-502">Data annotation validators enable you to perform validation by adding one or more attributes to a class property.</span></span> <span data-ttu-id="87f14-503"><xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType>Element atributu definuje text chybové zprávy, pokud se ověření nepovede.</span><span class="sxs-lookup"><span data-stu-id="87f14-503">The attribute's <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> element defines the text of the error message if validation fails.</span></span> <span data-ttu-id="87f14-504">Počínaje .NET Framework 4.6.2, ASP.NET usnadňuje lokalizaci chybových zpráv.</span><span class="sxs-lookup"><span data-stu-id="87f14-504">Starting with the .NET Framework 4.6.2, ASP.NET makes it easy to localize error messages.</span></span> <span data-ttu-id="87f14-505">Chybové zprávy budou lokalizovány v těchto případech:</span><span class="sxs-lookup"><span data-stu-id="87f14-505">Error messages will be localized if:</span></span>

1. <span data-ttu-id="87f14-506"><xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType>Je k dispozici v atributu ověřování.</span><span class="sxs-lookup"><span data-stu-id="87f14-506">The <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> is provided in the validation attribute.</span></span>

2. <span data-ttu-id="87f14-507">Soubor prostředků je uložený ve složce App_LocalResources.</span><span class="sxs-lookup"><span data-stu-id="87f14-507">The resource file is stored in the App_LocalResources folder.</span></span>

3. <span data-ttu-id="87f14-508">Název souboru lokalizovaných zdrojů má `DataAnnotation.Localization.{` *název*formuláře `}.resx` , kde *název* je název jazykové verze ve formátu *languageCode* `-` *Country/regionCode* nebo *languageCode*.</span><span class="sxs-lookup"><span data-stu-id="87f14-508">The name of the localized resources file has the form `DataAnnotation.Localization.{`*name*`}.resx`, where *name* is a culture name in the format *languageCode*`-`*country/regionCode* or *languageCode*.</span></span>

4. <span data-ttu-id="87f14-509">Klíčovým názvem prostředku je řetězec přiřazený k <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> atributu a jeho hodnota je lokalizovaná chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="87f14-509">The key name of the resource is the string assigned to the <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> attribute,  and its value is the localized error message.</span></span>

<span data-ttu-id="87f14-510">Například následující atribut poznámky k datům definuje chybovou zprávu výchozí jazykové verze pro neplatné hodnocení.</span><span class="sxs-lookup"><span data-stu-id="87f14-510">For example, the following data annotation attribute defines the default culture's error message for an invalid rating.</span></span>

```csharp
public class RatingInfo
{
   [Required(ErrorMessage = "The rating must be between 1 and 10.")]
   [Display(Name = "Your Rating")]
   public int Rating { get; set; }
}
```

```vb
Public Class RatingInfo
   <Required(ErrorMessage = "The rating must be between 1 and 10.")>
   <Display(Name = "Your Rating")>
   Public Property Rating As Integer = 1
End Class
```

<span data-ttu-id="87f14-511">Pak můžete vytvořit soubor prostředků, dataanotace. Localization. fr. resx, jehož klíč je řetězec chybové zprávy a jehož hodnota je lokalizovaná chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="87f14-511">You can then create a resource file, DataAnnotation.Localization.fr.resx, whose key is the error message string and whose value is the localized error message.</span></span> <span data-ttu-id="87f14-512">Soubor se musí nacházet ve `App.LocalResources` složce.</span><span class="sxs-lookup"><span data-stu-id="87f14-512">The file must be found in the `App.LocalResources` folder.</span></span> <span data-ttu-id="87f14-513">Například následující je klíč a jeho hodnota v lokalizované chybové zprávě jazyka francouzštiny (FR):</span><span class="sxs-lookup"><span data-stu-id="87f14-513">For example, the following is the key and its value in a localized French (fr) language error message:</span></span>

| <span data-ttu-id="87f14-514">Název</span><span class="sxs-lookup"><span data-stu-id="87f14-514">Name</span></span>                                 | <span data-ttu-id="87f14-515">Hodnota</span><span class="sxs-lookup"><span data-stu-id="87f14-515">Value</span></span>                                     |
| ------------------------------------ | ----------------------------------------- |
| <span data-ttu-id="87f14-516">Hodnocení musí být v rozmezí od 1 do 10.</span><span class="sxs-lookup"><span data-stu-id="87f14-516">The rating must be between 1 and 10.</span></span> | <span data-ttu-id="87f14-517">La doit être tvoří meziplatformní 1 et 10.</span><span class="sxs-lookup"><span data-stu-id="87f14-517">La note doit être comprise entre 1 et 10.</span></span> |

 <span data-ttu-id="87f14-518">Lokalizace datových poznámek je navíc rozšiřitelná.</span><span class="sxs-lookup"><span data-stu-id="87f14-518">In addition, data annotation localization is extensible.</span></span> <span data-ttu-id="87f14-519">Vývojáři mohou připojit vlastní poskytovatele řetězce lokalizátora implementací <xref:System.Web.Globalization.IStringLocalizerProvider> rozhraní k uložení lokalizačního řetězce jinde než v souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="87f14-519">Developers can plug in their own string localizer provider by implementing the <xref:System.Web.Globalization.IStringLocalizerProvider> interface to store localization string somewhere other than in a resource file.</span></span>

 <span data-ttu-id="87f14-520">**Asynchronní podpora s poskytovateli úložiště stavu relace**</span><span class="sxs-lookup"><span data-stu-id="87f14-520">**Async support with session-state store providers**</span></span>

 <span data-ttu-id="87f14-521">ASP.NET teď umožňuje používat metody vracející úlohy s poskytovateli úložiště stavu relace, což aplikacím ASP.NET umožní získat výhody škálovatelnosti Async.</span><span class="sxs-lookup"><span data-stu-id="87f14-521">ASP.NET now allows task-returning methods to be used with session-state store providers, thereby allowing ASP.NET apps to get the scalability benefits of async.</span></span> <span data-ttu-id="87f14-522">Pro podporu asynchronních operací s poskytovateli úložiště stavu relace zahrnuje ASP.NET nové rozhraní, <xref:System.Web.SessionState.ISessionStateModule?displayProperty=nameWithType> které dědí z <xref:System.Web.IHttpModule> a umožňuje vývojářům implementovat vlastní modul stavu relace a zprostředkovatele úložiště asynchronních relací.</span><span class="sxs-lookup"><span data-stu-id="87f14-522">To supports asynchronous operations with session state store providers, ASP.NET includes  a new interface, <xref:System.Web.SessionState.ISessionStateModule?displayProperty=nameWithType>, which inherits from <xref:System.Web.IHttpModule> and allows developers to implement their own session-state module and async session store providers.</span></span> <span data-ttu-id="87f14-523">Rozhraní je definováno následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="87f14-523">The interface is defined as follows:</span></span>

```csharp
public interface ISessionStateModule : IHttpModule {
    void ReleaseSessionState(HttpContext context);
    Task ReleaseSessionStateAsync(HttpContext context);
}
```

```vb
Public Interface ISessionStateModule : Inherits IHttpModule
   Sub ReleaseSessionState(context As HttpContext)
   Function ReleaseSessionStateAsync(context As HttpContext) As Task
End Interface
```

 <span data-ttu-id="87f14-524">Kromě toho <xref:System.Web.SessionState.SessionStateUtility> Třída obsahuje dvě nové metody <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> a <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A> , které lze použít k podpoře asynchronních operací.</span><span class="sxs-lookup"><span data-stu-id="87f14-524">In addition, the <xref:System.Web.SessionState.SessionStateUtility> class includes two new methods, <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> and <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A>, that can be used to support asynchronous operations.</span></span>

 <span data-ttu-id="87f14-525">**Asynchronní podpora pro poskytovatele výstupní mezipaměti**</span><span class="sxs-lookup"><span data-stu-id="87f14-525">**Async support for output-cache providers**</span></span>

 <span data-ttu-id="87f14-526">Počínaje .NET Framework 4.6.2 lze metody vracející úlohy použít s poskytovateli výstupní mezipaměti k zajištění výhod škálovatelnosti Async.</span><span class="sxs-lookup"><span data-stu-id="87f14-526">Starting with the .NET Framework 4.6.2, task-returning methods can be used with output-cache providers to provide the scalability benefits of async.</span></span>  <span data-ttu-id="87f14-527">Poskytovatelé, kteří implementují tyto metody, omezují blokování vláken na webovém serveru a zlepšují škálovatelnost služby ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="87f14-527">Providers that implement these methods reduce thread-blocking on a web server and improve the scalability of an ASP.NET service.</span></span>

 <span data-ttu-id="87f14-528">Byla přidána následující rozhraní API pro podporu zprostředkovatelů asynchronní výstupní mezipaměti:</span><span class="sxs-lookup"><span data-stu-id="87f14-528">The following APIs have been added to support asynchronous output-cache providers:</span></span>

- <span data-ttu-id="87f14-529"><xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=nameWithType>Třída, která dědí z <xref:System.Web.Caching.OutputCacheProvider?displayProperty=nameWithType> a umožňuje vývojářům implementovat asynchronního poskytovatele výstupní mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="87f14-529">The <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=nameWithType> class, which inherits from <xref:System.Web.Caching.OutputCacheProvider?displayProperty=nameWithType> and allows developers to implement an asynchronous output-cache provider.</span></span>

- <span data-ttu-id="87f14-530"><xref:System.Web.Caching.OutputCacheUtility>Třída, která poskytuje podpůrné metody pro konfiguraci výstupní mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="87f14-530">The <xref:System.Web.Caching.OutputCacheUtility> class, which provides helper methods for configuring the output cache.</span></span>

- <span data-ttu-id="87f14-531">18 nových metod <xref:System.Web.HttpCachePolicy?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="87f14-531">18 new methods in the <xref:System.Web.HttpCachePolicy?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="87f14-532">Mezi ně patří <xref:System.Web.HttpCachePolicy.GetCacheability%2A> ,,,, <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A> <xref:System.Web.HttpCachePolicy.GetETag%2A> <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A> <xref:System.Web.HttpCachePolicy.GetMaxAge%2A> , <xref:System.Web.HttpCachePolicy.GetMaxAge%2A> , <xref:System.Web.HttpCachePolicy.GetNoStore%2A> , <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A> , <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A> , <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A> , <xref:System.Web.HttpCachePolicy.GetRevalidation%2A> , <xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A> ,, a <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A> <xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A> <xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A> .</span><span class="sxs-lookup"><span data-stu-id="87f14-532">These include <xref:System.Web.HttpCachePolicy.GetCacheability%2A>, <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A>, <xref:System.Web.HttpCachePolicy.GetETag%2A>, <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetNoStore%2A>, <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A>, <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>, <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetRevalidation%2A>, <xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A>, <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A>, <xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A>, and <xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A>.</span></span>

- <span data-ttu-id="87f14-533">2 nové metody ve <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=nameWithType> třídě: <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> a <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A> .</span><span class="sxs-lookup"><span data-stu-id="87f14-533">2 new methods in the <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=nameWithType> class:  <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> and <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A>.</span></span>

- <span data-ttu-id="87f14-534">2 nové metody ve <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=nameWithType> třídě: <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> a <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A> .</span><span class="sxs-lookup"><span data-stu-id="87f14-534">2 new methods in the <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=nameWithType> class: <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> and <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A>.</span></span>

- <span data-ttu-id="87f14-535">2 nové metody ve <xref:System.Web.HttpCacheVaryByParams?displayProperty=nameWithType> třídě: <xref:System.Web.HttpCacheVaryByParams.GetParams%2A> a <xref:System.Web.HttpCacheVaryByParams.SetParams%2A> .</span><span class="sxs-lookup"><span data-stu-id="87f14-535">2 new methods in the <xref:System.Web.HttpCacheVaryByParams?displayProperty=nameWithType> class: <xref:System.Web.HttpCacheVaryByParams.GetParams%2A> and <xref:System.Web.HttpCacheVaryByParams.SetParams%2A>.</span></span>

- <span data-ttu-id="87f14-536">Ve <xref:System.Web.Caching.AggregateCacheDependency?displayProperty=nameWithType> třídě <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="87f14-536">In the <xref:System.Web.Caching.AggregateCacheDependency?displayProperty=nameWithType> class, the <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A> method.</span></span>

- <span data-ttu-id="87f14-537">V <xref:System.Web.Caching.CacheDependency> <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> metodě metoda.</span><span class="sxs-lookup"><span data-stu-id="87f14-537">In the <xref:System.Web.Caching.CacheDependency>, the <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> method.</span></span>

<a name="Strings"></a>

### <a name="character-categories"></a><span data-ttu-id="87f14-538">Kategorie znaků</span><span class="sxs-lookup"><span data-stu-id="87f14-538">Character categories</span></span>

<span data-ttu-id="87f14-539">Znaky v .NET Framework 4.6.2 jsou klasifikovány na základě [standardu Unicode verze 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/).</span><span class="sxs-lookup"><span data-stu-id="87f14-539">Characters in the .NET Framework 4.6.2 are classified based on the [Unicode Standard, Version 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/).</span></span> <span data-ttu-id="87f14-540">V .NET Framework 4,6 a .NET Framework 4.6.1 byly znaky klasifikovány na základě kategorií znaků Unicode 6,3.</span><span class="sxs-lookup"><span data-stu-id="87f14-540">In .NET Framework 4.6 and .NET Framework 4.6.1, characters were classified based on Unicode 6.3 character categories.</span></span>

<span data-ttu-id="87f14-541">Podpora Unicode 8,0 je omezená na klasifikaci znaků <xref:System.Globalization.CharUnicodeInfo> třídou a na typy a metody, které na ní spoléhají.</span><span class="sxs-lookup"><span data-stu-id="87f14-541">Support for Unicode 8.0 is limited to the classification of characters by the <xref:System.Globalization.CharUnicodeInfo> class and to types and methods that rely on it.</span></span> <span data-ttu-id="87f14-542">Mezi ně patří <xref:System.Globalization.StringInfo> třída, přetížená <xref:System.Char.GetUnicodeCategory%2A?displayProperty=nameWithType> Metoda a [třídy znaků](../../standard/base-types/character-classes-in-regular-expressions.md) rozpoznané modulem .NET Framework regulárních výrazů.</span><span class="sxs-lookup"><span data-stu-id="87f14-542">These include the <xref:System.Globalization.StringInfo> class, the overloaded <xref:System.Char.GetUnicodeCategory%2A?displayProperty=nameWithType> method, and the [character classes](../../standard/base-types/character-classes-in-regular-expressions.md) recognized by the .NET Framework regular expression engine.</span></span>  <span data-ttu-id="87f14-543">Porovnání znaků a řetězců a jejich řazení není ovlivněno touto změnou a nadále se spoléhá na základní operační systém nebo v systémech Windows 7 na znaková data, která poskytuje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="87f14-543">Character and string comparison and sorting is unaffected by this change and continues to rely on the underlying operating system or, on Windows 7 systems, on character data provided by the .NET Framework.</span></span>

<span data-ttu-id="87f14-544">Změny v kategoriích znaků z Unicode 6,0 až Unicode 7,0 najdete na webu Unicode Consortium na [standardu Unicode verze 7.0.0](https://www.unicode.org/versions/Unicode7.0.0/) .</span><span class="sxs-lookup"><span data-stu-id="87f14-544">For changes in character categories from Unicode 6.0 to Unicode 7.0, see [The Unicode Standard, Version 7.0.0](https://www.unicode.org/versions/Unicode7.0.0/) at The Unicode Consortium website.</span></span> <span data-ttu-id="87f14-545">Změny z Unicode 7,0 na Unicode 8,0 najdete na webu Unicode Consortium na [standardu Unicode verze 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/) .</span><span class="sxs-lookup"><span data-stu-id="87f14-545">For changes from Unicode 7.0 to Unicode 8.0, see [The Unicode Standard, Version 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/) at The Unicode Consortium website.</span></span>

<a name="Crypto462"></a>

### <a name="cryptography"></a><span data-ttu-id="87f14-546">Kryptografie</span><span class="sxs-lookup"><span data-stu-id="87f14-546">Cryptography</span></span>

<span data-ttu-id="87f14-547">**Podpora pro certifikáty x509 obsahující FIPS 186-3 DSA**</span><span class="sxs-lookup"><span data-stu-id="87f14-547">**Support for X509 certificates containing FIPS 186-3 DSA**</span></span>

<span data-ttu-id="87f14-548">.NET Framework 4.6.2 přidává podporu certifikátů x509 (Digital Signature Algorithm), jejichž klíče překračují limit bitů FIPS 186-2 1024.</span><span class="sxs-lookup"><span data-stu-id="87f14-548">The .NET Framework 4.6.2 adds support for DSA (Digital Signature Algorithm) X509 certificates whose keys exceed the FIPS 186-2 1024-bit limit.</span></span>

<span data-ttu-id="87f14-549">Kromě podpory většího počtu klíčových velikostí FIPS 186-3 umožňuje .NET Framework 4.6.2 výpočetních signatur pomocí řady SHA-2 algoritmů hash (SHA256, SHA384 a SHA512).</span><span class="sxs-lookup"><span data-stu-id="87f14-549">In addition to supporting the larger key sizes of FIPS 186-3, the .NET Framework 4.6.2 allows computing signatures with the SHA-2 family of hash algorithms (SHA256, SHA384, and SHA512).</span></span> <span data-ttu-id="87f14-550">Podpora FIPS 186-3 je poskytována novou <xref:System.Security.Cryptography.DSACng?displayProperty=nameWithType> třídou.</span><span class="sxs-lookup"><span data-stu-id="87f14-550">FIPS 186-3 support is provided by the new <xref:System.Security.Cryptography.DSACng?displayProperty=nameWithType> class.</span></span>

<span data-ttu-id="87f14-551">V případě, že se v <xref:System.Security.Cryptography.RSA> .NET Framework 4,6 a třídě v .NET Framework 4.6.1 zachovává poslední změny třídy <xref:System.Security.Cryptography.ECDsa> , <xref:System.Security.Cryptography.DSA> má abstraktní základní třída v .NET Framework 4.6.2 další metody, které umožňují volajícím používat tuto funkci bez přetypování.</span><span class="sxs-lookup"><span data-stu-id="87f14-551">In keeping with recent changes to the <xref:System.Security.Cryptography.RSA> class in .NET Framework 4.6 and the <xref:System.Security.Cryptography.ECDsa> class in .NET Framework 4.6.1, the <xref:System.Security.Cryptography.DSA> abstract base class in .NET Framework 4.6.2 has additional methods to allow callers to use this functionality without casting.</span></span> <span data-ttu-id="87f14-552">Můžete zavolat <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=nameWithType> metodu rozšíření pro podepsání dat, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="87f14-552">You can call the <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=nameWithType> extension method to sign data, as the following example shows.</span></span>

```csharp
public static byte[] SignDataDsaSha384(byte[] data, X509Certificate2 cert)
{
    using (DSA dsa = cert.GetDSAPrivateKey())
    {
        return dsa.SignData(data, HashAlgorithmName.SHA384);
    }
}
```

```vb
Public Shared Function SignDataDsaSha384(data As Byte(), cert As X509Certificate2) As Byte()
    Using DSA As DSA = cert.GetDSAPrivateKey()
        Return DSA.SignData(data, HashAlgorithmName.SHA384)
    End Using
End Function
```

<span data-ttu-id="87f14-553">A můžete zavolat <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=nameWithType> metodu rozšíření pro ověření podepsaných dat, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="87f14-553">And you can call the <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=nameWithType> extension method to verify signed data, as the following example shows.</span></span>

```csharp
public static bool VerifyDataDsaSha384(byte[] data, byte[] signature, X509Certificate2 cert)
{
    using (DSA dsa = cert.GetDSAPublicKey())
    {
        return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384);
    }
}
```

```vb
 Public Shared Function VerifyDataDsaSha384(data As Byte(), signature As Byte(), cert As X509Certificate2) As Boolean
    Using dsa As DSA = cert.GetDSAPublicKey()
        Return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384)
    End Using
End Function
```

<span data-ttu-id="87f14-554">**Větší přehlednost pro vstupy pro rutiny odvození ECDiffieHellman klíčů**</span><span class="sxs-lookup"><span data-stu-id="87f14-554">**Increased clarity for inputs to ECDiffieHellman key derivation routines**</span></span>

<span data-ttu-id="87f14-555">.NET Framework 3,5 přidali podporu pro klíčovou smlouvu Diffie-Hellman s eliptickou křivkou se třemi různými rutinami funkce odvození klíče (KDF).</span><span class="sxs-lookup"><span data-stu-id="87f14-555">.NET Framework 3.5 added support for Elliptic Curve Diffie-Hellman Key Agreement with three different Key Derivation Function (KDF) routines.</span></span> <span data-ttu-id="87f14-556">Vstupy pro rutiny a samotné rutiny byly nakonfigurovány prostřednictvím vlastností <xref:System.Security.Cryptography.ECDiffieHellmanCng> objektu.</span><span class="sxs-lookup"><span data-stu-id="87f14-556">The inputs to the routines, and the routines themselves, were configured via properties on the <xref:System.Security.Cryptography.ECDiffieHellmanCng> object.</span></span> <span data-ttu-id="87f14-557">Ale vzhledem k tomu, že ne všechny rutiny čtou všechna vstupní vlastnost, existovala v minulosti pro vás rozsáhlá místnost pro nejasnost.</span><span class="sxs-lookup"><span data-stu-id="87f14-557">But since not every routine read every input property, there was ample room for confusion on the past of the developer.</span></span>

<span data-ttu-id="87f14-558">Pro vyřešení tohoto .NET Framework 4.6.2 byly do základní třídy přidány následující tři metody, <xref:System.Security.Cryptography.ECDiffieHellman> které jasně reprezentují tyto KDF rutiny a jejich vstupy:</span><span class="sxs-lookup"><span data-stu-id="87f14-558">To address this in the .NET Framework 4.6.2, the following three methods have been added to the  <xref:System.Security.Cryptography.ECDiffieHellman> base class to more clearly represent these KDF routines and their inputs:</span></span>

|<span data-ttu-id="87f14-559">Metoda ECDiffieHellman</span><span class="sxs-lookup"><span data-stu-id="87f14-559">ECDiffieHellman method</span></span>|<span data-ttu-id="87f14-560">Popis</span><span class="sxs-lookup"><span data-stu-id="87f14-560">Description</span></span>|
|----------------------------|-----------------|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|<span data-ttu-id="87f14-561">Odvozuje materiál klíče pomocí vzorce.</span><span class="sxs-lookup"><span data-stu-id="87f14-561">Derives key material using the formula</span></span><br /><br /> <span data-ttu-id="87f14-562">HASH (secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)</span><span class="sxs-lookup"><span data-stu-id="87f14-562">HASH(secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)</span></span><br /><br /> <span data-ttu-id="87f14-563">HASH (secretPrepend OrElse *×* OrElse secretAppend)</span><span class="sxs-lookup"><span data-stu-id="87f14-563">HASH(secretPrepend OrElse *x* OrElse secretAppend)</span></span><br /><br /> <span data-ttu-id="87f14-564">kde *x* je vypočtený výsledek algoritmu ES Diffie-Hellman.</span><span class="sxs-lookup"><span data-stu-id="87f14-564">where *x* is the computed result of the EC Diffie-Hellman algorithm.</span></span>|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|<span data-ttu-id="87f14-565">Odvozuje materiál klíče pomocí vzorce.</span><span class="sxs-lookup"><span data-stu-id="87f14-565">Derives key material using the formula</span></span><br /><br /> <span data-ttu-id="87f14-566">HMAC (hmacKey, secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)</span><span class="sxs-lookup"><span data-stu-id="87f14-566">HMAC(hmacKey, secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)</span></span><br /><br /> <span data-ttu-id="87f14-567">HMAC (hmacKey; secretPrepend OrElse *x* OrElse secretAppend)</span><span class="sxs-lookup"><span data-stu-id="87f14-567">HMAC(hmacKey, secretPrepend OrElse *x* OrElse secretAppend)</span></span><br /><br /> <span data-ttu-id="87f14-568">kde *x* je vypočtený výsledek algoritmu ES Diffie-Hellman.</span><span class="sxs-lookup"><span data-stu-id="87f14-568">where *x* is the computed result of the EC Diffie-Hellman algorithm.</span></span>|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|<span data-ttu-id="87f14-569">Odvodí klíč klíče pomocí algoritmu odvození náhodného použití funkce TLS.</span><span class="sxs-lookup"><span data-stu-id="87f14-569">Derives key material using the TLS pseudo-random function (PRF) derivation algorithm.</span></span>|

<span data-ttu-id="87f14-570">**Podpora trvalého symetrického šifrování s trvalým klíčem**</span><span class="sxs-lookup"><span data-stu-id="87f14-570">**Support for persisted-key symmetric encryption**</span></span>

<span data-ttu-id="87f14-571">Knihovna kryptografických služeb systému Windows (CNG) přidala podporu pro ukládání trvalých symetrických klíčů a používání hardwarových symetrických klíčů a .NET Framework 4.6.2 umožňuje vývojářům využít tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="87f14-571">The Windows cryptography library (CNG) added support for storing persisted symmetric keys and using hardware-stored symmetric keys, and the .NET Framework 4.6.2 made it possible for developers to make use of this feature.</span></span>  <span data-ttu-id="87f14-572">Vzhledem k tomu, že pojem názvů klíčů a poskytovatelů klíčů jsou specifické pro konkrétní implementaci, vyžaduje použití této funkce konstruktor konkrétních typů implementace namísto preferovaného přístupu k továrně (například volání `Aes.Create` ).</span><span class="sxs-lookup"><span data-stu-id="87f14-572">Since the notion of key names and key providers is implementation-specific, using this feature requires utilizing the constructor of the concrete implementation types instead of the preferred factory approach (such as calling `Aes.Create`).</span></span>

<span data-ttu-id="87f14-573">Pro algoritmy AES ( <xref:System.Security.Cryptography.AesCng> ) a 3DES () existují trvalé podpory symetrického šifrování-Key <xref:System.Security.Cryptography.TripleDESCng> .</span><span class="sxs-lookup"><span data-stu-id="87f14-573">Persisted-key symmetric encryption support exists for the AES (<xref:System.Security.Cryptography.AesCng>) and 3DES (<xref:System.Security.Cryptography.TripleDESCng>) algorithms.</span></span> <span data-ttu-id="87f14-574">Příklad:</span><span class="sxs-lookup"><span data-stu-id="87f14-574">For example:</span></span>

```csharp
public static byte[] EncryptDataWithPersistedKey(byte[] data, byte[] iv)
{
    using (Aes aes = new AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider))
    {
        aes.IV = iv;

        // Using the zero-argument overload is required to make use of the persisted key
        using (ICryptoTransform encryptor = aes.CreateEncryptor())
        {
            if (!encryptor.CanTransformMultipleBlocks)
            {
                throw new InvalidOperationException("This is a sample, this case wasn't handled...");
            }

            return encryptor.TransformFinalBlock(data, 0, data.Length);
        }
    }
}
```

```vb
Public Shared Function EncryptDataWithPersistedKey(data As Byte(), iv As Byte()) As Byte()
    Using Aes As Aes = New AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider)
        Aes.IV = iv

        ' Using the zero-argument overload Is required to make use of the persisted key
        Using encryptor As ICryptoTransform = Aes.CreateEncryptor()
            If Not encryptor.CanTransformMultipleBlocks Then
                Throw New InvalidOperationException("This is a sample, this case wasn't handled...")
            End If
            Return encryptor.TransformFinalBlock(data, 0, data.Length)
        End Using
    End Using
End Function
```

<span data-ttu-id="87f14-575">**Podpora SignedXml pro algoritmus hash SHA-2**</span><span class="sxs-lookup"><span data-stu-id="87f14-575">**SignedXml support for SHA-2 hashing**</span></span>

<span data-ttu-id="87f14-576">.NET Framework 4.6.2 přidává podporu <xref:System.Security.Cryptography.Xml.SignedXml> tříd pro signatury RSA-SHA256, RSA-SHA384 a RSA-SHA512 pro podpisové metody a SHA256, SHA384 a SHA512 referenční algoritmy Digest.</span><span class="sxs-lookup"><span data-stu-id="87f14-576">The .NET Framework 4.6.2 adds support to  the <xref:System.Security.Cryptography.Xml.SignedXml> class for RSA-SHA256, RSA-SHA384, and RSA-SHA512 PKCS#1 signature methods, and SHA256, SHA384, and SHA512 reference digest algorithms.</span></span>

<span data-ttu-id="87f14-577">Konstanty identifikátoru URI jsou všechny vystavené na <xref:System.Security.Cryptography.Xml.SignedXml> :</span><span class="sxs-lookup"><span data-stu-id="87f14-577">The URI constants are all exposed on <xref:System.Security.Cryptography.Xml.SignedXml>:</span></span>

|<span data-ttu-id="87f14-578">Pole SignedXml</span><span class="sxs-lookup"><span data-stu-id="87f14-578">SignedXml field</span></span>|<span data-ttu-id="87f14-579">Trvalé</span><span class="sxs-lookup"><span data-stu-id="87f14-579">Constant</span></span>|
|---------------------|--------------|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url>|<span data-ttu-id="87f14-580">"http://www.w3.org/2001/04/xmlenc#sha256"</span><span class="sxs-lookup"><span data-stu-id="87f14-580">"http://www.w3.org/2001/04/xmlenc#sha256"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url>|<span data-ttu-id="87f14-581">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"</span><span class="sxs-lookup"><span data-stu-id="87f14-581">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url>|<span data-ttu-id="87f14-582">"http://www.w3.org/2001/04/xmldsig-more#sha384"</span><span class="sxs-lookup"><span data-stu-id="87f14-582">"http://www.w3.org/2001/04/xmldsig-more#sha384"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url>|<span data-ttu-id="87f14-583">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"</span><span class="sxs-lookup"><span data-stu-id="87f14-583">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url>|<span data-ttu-id="87f14-584">"http://www.w3.org/2001/04/xmlenc#sha512"</span><span class="sxs-lookup"><span data-stu-id="87f14-584">"http://www.w3.org/2001/04/xmlenc#sha512"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url>|<span data-ttu-id="87f14-585">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"</span><span class="sxs-lookup"><span data-stu-id="87f14-585">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"</span></span>|

 <span data-ttu-id="87f14-586">Všechny programy, které zaregistrovaly vlastní <xref:System.Security.Cryptography.SignatureDescription> obslužnou rutinu do nástroje <xref:System.Security.Cryptography.CryptoConfig> pro přidání podpory pro tyto algoritmy, budou i nadále fungovat stejně jako v minulosti, ale vzhledem k tomu, že jsou teď výchozí nastavení platformy, <xref:System.Security.Cryptography.CryptoConfig> registrace už není potřeba.</span><span class="sxs-lookup"><span data-stu-id="87f14-586">Any programs that have registered a custom <xref:System.Security.Cryptography.SignatureDescription> handler into <xref:System.Security.Cryptography.CryptoConfig> to add support for these algorithms will continue to function as they did in the past, but since there are now platform defaults, the <xref:System.Security.Cryptography.CryptoConfig> registration is no longer necessary.</span></span>

<a name="SQLClient"></a>

### <a name="sqlclient"></a><span data-ttu-id="87f14-587">SqlClient</span><span class="sxs-lookup"><span data-stu-id="87f14-587">SqlClient</span></span>

<span data-ttu-id="87f14-588">.NET Framework Zprostředkovatel dat pro SQL Server ( <xref:System.Data.SqlClient?displayProperty=nameWithType> ) obsahuje následující nové funkce .NET Framework 4.6.2:</span><span class="sxs-lookup"><span data-stu-id="87f14-588">.NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>) includes the following new features in the .NET Framework 4.6.2:</span></span>

<span data-ttu-id="87f14-589">**Sdružování připojení a vypršení časových limitů pomocí databází SQL Azure**</span><span class="sxs-lookup"><span data-stu-id="87f14-589">**Connection pooling and timeouts with Azure SQL databases**</span></span>

<span data-ttu-id="87f14-590">Je-li povoleno sdružování připojení a dojde k vypršení časového limitu nebo jiné chyby přihlášení, je výjimka uložena do mezipaměti a při každém následném pokusu o připojení na dalších 5 sekund až 1 minutu je vyvolána výjimka v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="87f14-590">When connection pooling is enabled and a timeout or other login error occurs, an exception is cached, and the cached exception is thrown on any subsequent connection attempt for the next 5 seconds to 1 minute.</span></span> <span data-ttu-id="87f14-591">Další informace najdete v tématu věnovaném [sdružování připojení SQL Server (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-591">For more information, see [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span></span>

<span data-ttu-id="87f14-592">Toto chování není vhodné při připojování k databázím Azure SQL, protože pokusy o připojení mohou selhat s přechodem k přechodným chybám, které se obvykle obnovují rychle.</span><span class="sxs-lookup"><span data-stu-id="87f14-592">This behavior is not desirable when connecting to Azure SQL Databases, since connection attempts can fail with transient errors that are typically recovered quickly.</span></span> <span data-ttu-id="87f14-593">Pro lepší optimalizaci možností opakovaného pokusu o připojení se při selhání připojení k databázím Azure SQL odstraní chování při blokování fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="87f14-593">To better optimize the connection retry experience, the connection pool blocking period behavior is removed when connections to Azure SQL Databases fail.</span></span>

<span data-ttu-id="87f14-594">Přidání `PoolBlockingPeriod` klíčového slova New vám umožní vybrat dobu blokování, která se pro vaši aplikaci nejlépe hodí.</span><span class="sxs-lookup"><span data-stu-id="87f14-594">The addition of the new `PoolBlockingPeriod` keyword lets you select the blocking period best suited for your app.</span></span> <span data-ttu-id="87f14-595">Mezi tyto hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="87f14-595">Values include:</span></span>

<xref:System.Data.SqlClient.PoolBlockingPeriod.Auto>

<span data-ttu-id="87f14-596">Doba blokování fondu připojení pro aplikaci, která se připojuje k Azure SQL Database je zakázána a je povolená doba blokování fondu připojení pro aplikaci, která se připojuje k jakékoli jiné instanci SQL Server.</span><span class="sxs-lookup"><span data-stu-id="87f14-596">The connection pool blocking period for an application that connects to an Azure SQL Database is disabled, and the connection pool blocking period for an application that connects to any other SQL Server instance is enabled.</span></span> <span data-ttu-id="87f14-597">Toto je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="87f14-597">This is the default value.</span></span> <span data-ttu-id="87f14-598">Pokud název koncového bodu serveru končí některým z následujících, považují se za databáze SQL Azure:</span><span class="sxs-lookup"><span data-stu-id="87f14-598">If the Server endpoint name ends with any of the following, they are considered Azure SQL Databases:</span></span>

- <span data-ttu-id="87f14-599">. database.windows.net</span><span class="sxs-lookup"><span data-stu-id="87f14-599">.database.windows.net</span></span>

- <span data-ttu-id="87f14-600">. database.chinacloudapi.cn</span><span class="sxs-lookup"><span data-stu-id="87f14-600">.database.chinacloudapi.cn</span></span>

- <span data-ttu-id="87f14-601">. database.usgovcloudapi.net</span><span class="sxs-lookup"><span data-stu-id="87f14-601">.database.usgovcloudapi.net</span></span>

- <span data-ttu-id="87f14-602">. database.cloudapi.de</span><span class="sxs-lookup"><span data-stu-id="87f14-602">.database.cloudapi.de</span></span>

<xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock>

<span data-ttu-id="87f14-603">Doba blokování fondu připojení je vždycky povolená.</span><span class="sxs-lookup"><span data-stu-id="87f14-603">The connection pool blocking period is always enabled.</span></span>

<xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock>

<span data-ttu-id="87f14-604">Doba blokování fondu připojení je vždycky zakázaná.</span><span class="sxs-lookup"><span data-stu-id="87f14-604">The connection pool blocking period is always disabled.</span></span>

<span data-ttu-id="87f14-605">**Vylepšení pro Always Encrypted**</span><span class="sxs-lookup"><span data-stu-id="87f14-605">**Enhancements for Always Encrypted**</span></span>

<span data-ttu-id="87f14-606">SQLClient přináší dvě vylepšení pro Always Encrypted:</span><span class="sxs-lookup"><span data-stu-id="87f14-606">SQLClient introduces two enhancements for Always Encrypted:</span></span>

- <span data-ttu-id="87f14-607">Pro zlepšení výkonu parametrizovaných dotazů proti šifrovaným databázovým sloupcům jsou metadata šifrování pro parametry dotazu nyní ukládána do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="87f14-607">To improve performance of parameterized queries against encrypted database columns, encryption metadata for query parameters is now cached.</span></span> <span data-ttu-id="87f14-608"><xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=nameWithType>Pokud je vlastnost nastavena na `true` (což je výchozí hodnota), je-li stejný dotaz volán několikrát, klient načte metadata parametrů ze serveru pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="87f14-608">With the <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=nameWithType> property set to `true` (which is the default value), if the same query is called multiple times, the client retrieves parameter metadata from the server only once.</span></span>

- <span data-ttu-id="87f14-609">Položky šifrovacího klíče sloupce v mezipaměti klíčů jsou teď po konfigurovatelném časovém intervalu vyřazení, které nastavíte pomocí <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=nameWithType> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="87f14-609">Column encryption key entries in the key cache are now evicted after a configurable time interval, set using the <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=nameWithType> property.</span></span>

<a name="WCF"></a>

### <a name="windows-communication-foundation"></a><span data-ttu-id="87f14-610">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="87f14-610">Windows Communication Foundation</span></span>

<span data-ttu-id="87f14-611">V .NET Framework 4.6.2 byly Windows Communication Foundation rozšířeny v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="87f14-611">In the .NET Framework 4.6.2, Windows Communication Foundation has been enhanced in the following areas:</span></span>

<span data-ttu-id="87f14-612">**Podpora zabezpečení přenosu WCF pro certifikáty uložené pomocí CNG**</span><span class="sxs-lookup"><span data-stu-id="87f14-612">**WCF transport security support for certificates stored using CNG**</span></span>

<span data-ttu-id="87f14-613">Zabezpečení přenosu WCF podporuje certifikáty uložené pomocí knihovny kryptografických služeb systému Windows (CNG).</span><span class="sxs-lookup"><span data-stu-id="87f14-613">WCF transport security supports certificates stored using the Windows cryptography library (CNG).</span></span> <span data-ttu-id="87f14-614">V .NET Framework 4.6.2 je tato podpora omezená na použití certifikátů s veřejným klíčem, který má exponent větší než 32 bitů.</span><span class="sxs-lookup"><span data-stu-id="87f14-614">In the .NET Framework 4.6.2, this support is limited to using certificates with a public key that has an exponent no more than 32 bits in length.</span></span> <span data-ttu-id="87f14-615">Když je aplikace cílena na .NET Framework 4.6.2, je tato funkce ve výchozím nastavení zapnutá.</span><span class="sxs-lookup"><span data-stu-id="87f14-615">When an application targets the .NET Framework 4.6.2, this feature is on by default.</span></span>

<span data-ttu-id="87f14-616">Pro aplikace, které cílí na .NET Framework 4.6.1 a starší, ale běží na .NET Framework 4.6.2, je možné tuto funkci povolit přidáním následujícího řádku do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) části souboru app.config nebo web.config.</span><span class="sxs-lookup"><span data-stu-id="87f14-616">For applications that target the .NET Framework 4.6.1 and earlier but are running on the .NET Framework 4.6.2, this feature can be enabled by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app.config or web.config file.</span></span>

```xml
<AppContextSwitchOverrides
    value="Switch.System.ServiceModel.DisableCngCertificates=false"
/>
```

<span data-ttu-id="87f14-617">To lze provést také programově s kódem podobným následujícímu:</span><span class="sxs-lookup"><span data-stu-id="87f14-617">This can also be done programmatically with code like the following:</span></span>

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificates";
AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

<span data-ttu-id="87f14-618">**Lepší podpora více pravidel úprav více letního času pomocí třídy DataContractJsonSerializer**</span><span class="sxs-lookup"><span data-stu-id="87f14-618">**Better support for multiple daylight saving time adjustment rules by the DataContractJsonSerializer class**</span></span>

<span data-ttu-id="87f14-619">Zákazníci mohou použít nastavení konfigurace aplikace k určení, zda <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Třída podporuje více pravidel úprav pro jedno časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="87f14-619">Customers can use an application configuration setting to determine whether the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> class supports multiple adjustment rules for a single time zone.</span></span> <span data-ttu-id="87f14-620">Toto je funkce výslovného souhlasu.</span><span class="sxs-lookup"><span data-stu-id="87f14-620">This is an opt-in feature.</span></span> <span data-ttu-id="87f14-621">Pokud ho chcete povolit, přidejte do souboru app.config následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="87f14-621">To enable it, add the following setting to your app.config file:</span></span>

```xml
<runtime>
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />
</runtime>
```

<span data-ttu-id="87f14-622">Když je tato funkce povolená, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> objekt <xref:System.TimeZoneInfo> místo <xref:System.TimeZone> typu použije k deserializaci dat data a času typ.</span><span class="sxs-lookup"><span data-stu-id="87f14-622">When this feature is enabled, a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> object uses the <xref:System.TimeZoneInfo> type instead of the <xref:System.TimeZone> type to deserialize date and time data.</span></span> <span data-ttu-id="87f14-623"><xref:System.TimeZoneInfo>podporuje více pravidel úprav, což umožňuje pracovat s historickými daty časových pásem;   <xref:System.TimeZone>není.</span><span class="sxs-lookup"><span data-stu-id="87f14-623"><xref:System.TimeZoneInfo> supports multiple adjustment rules, which makes it possible to work with historic time zone data;   <xref:System.TimeZone> does not.</span></span>

<span data-ttu-id="87f14-624">Další informace o <xref:System.TimeZoneInfo> úpravách struktury a časových pásem najdete v tématu [Přehled časových pásem](../../standard/datetime/time-zone-overview.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-624">For more information on the <xref:System.TimeZoneInfo> structure and time zone adjustments, see [Time Zone Overview](../../standard/datetime/time-zone-overview.md).</span></span>

<span data-ttu-id="87f14-625">**NetNamedPipeBinding nejlepší shody**</span><span class="sxs-lookup"><span data-stu-id="87f14-625">**NetNamedPipeBinding best match**</span></span>

<span data-ttu-id="87f14-626">Služba WCF má nové nastavení aplikace, které lze nastavit na klientských aplikacích, aby bylo zajištěno, že se budou vždy připojovat ke službě naslouchat na identifikátoru URI, který nejlépe odpovídá tomu, kterou vyžádají.</span><span class="sxs-lookup"><span data-stu-id="87f14-626">WCF has a new app setting that can be set on client applications to ensure they always connect to the service listening on the URI that best matches the one that they request.</span></span> <span data-ttu-id="87f14-627">Když je nastavení této aplikace nastaveno na `false` (výchozí), klienti nástroje používají <xref:System.ServiceModel.NetNamedPipeBinding> k pokusu o připojení ke službě naslouchající na identifikátoru URI, který je podřetězec požadovaného identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="87f14-627">With this app setting set to `false` (the default), it is possible for clients using <xref:System.ServiceModel.NetNamedPipeBinding> to attempt to connect to a service listening on a URI that is a substring of the requested URI.</span></span>

<span data-ttu-id="87f14-628">Například klient se pokusí připojit ke službě naslouchat na adrese `net.pipe://localhost/Service1` , ale na tomto počítači, na kterém je spuštěná s oprávněním správce, naslouchá jiná služba `net.pipe://localhost` .</span><span class="sxs-lookup"><span data-stu-id="87f14-628">For example, a client tries to connect to a service listening at `net.pipe://localhost/Service1`, but a different service on that machine running with administrator privilege is listening at `net.pipe://localhost`.</span></span> <span data-ttu-id="87f14-629">Když je nastavení této aplikace nastaveno na `false` , klient se pokusí připojit k nesprávné službě.</span><span class="sxs-lookup"><span data-stu-id="87f14-629">With this app setting set to `false`, the client would attempt to connect to the wrong service.</span></span> <span data-ttu-id="87f14-630">Po nastavení nastavení aplikace se `true` Klient vždy připojí k nejlépe vyhovující službě.</span><span class="sxs-lookup"><span data-stu-id="87f14-630">After setting the app setting to `true`, the client will always connect to the best matching service.</span></span>

> [!NOTE]
> <span data-ttu-id="87f14-631">Klienti používají <xref:System.ServiceModel.NetNamedPipeBinding> Najít služby na základě základní adresy služby (pokud existuje), nikoli úplné adresy koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="87f14-631">Clients using <xref:System.ServiceModel.NetNamedPipeBinding> find services based on the service's base address (if it exists) rather than the full endpoint address.</span></span> <span data-ttu-id="87f14-632">Chcete-li zajistit, aby toto nastavení vždy fungovalo, měla by služba používat jedinečnou základní adresu.</span><span class="sxs-lookup"><span data-stu-id="87f14-632">To ensure this setting always works the service should use a unique base address.</span></span>

<span data-ttu-id="87f14-633">Pokud chcete tuto změnu povolit, přidejte do souboru App.config nebo Web.config klientské aplikace následující nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="87f14-633">To enable this change, add the following app setting to your client application's App.config or Web.config file:</span></span>

```xml
<configuration>
    <appSettings>
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />
    </appSettings>
</configuration>
```

<span data-ttu-id="87f14-634">**SSL 3,0 není výchozím protokolem.**</span><span class="sxs-lookup"><span data-stu-id="87f14-634">**SSL 3.0 is not a default protocol**</span></span>

<span data-ttu-id="87f14-635">Pokud používáte NetTcp se zabezpečením přenosu a typem přihlašovacích údajů certifikátu, SSL 3,0 už není výchozím protokolem používaným pro vyjednávání zabezpečeného připojení.</span><span class="sxs-lookup"><span data-stu-id="87f14-635">When using NetTcp with transport security and a credential type of certificate, SSL 3.0 is no longer a default protocol used for negotiating a secure connection.</span></span> <span data-ttu-id="87f14-636">Ve většině případů by nemělo dojít k žádným dopadům na existující aplikace, protože TLS 1,0 je zahrnutý v seznamu protokolů pro NetTcp.</span><span class="sxs-lookup"><span data-stu-id="87f14-636">In most cases, there should be no impact to existing apps, because TLS 1.0 is included in the protocol list for NetTcp.</span></span> <span data-ttu-id="87f14-637">Všichni existující klienti by měli být schopni vyjednat připojení pomocí aspoň TLS 1,0.</span><span class="sxs-lookup"><span data-stu-id="87f14-637">All existing clients should be able to negotiate a connection using at least TLS 1.0.</span></span> <span data-ttu-id="87f14-638">Pokud se vyžaduje SSL3, použijte jeden z následujících konfiguračních mechanismů a přidejte ho do seznamu sjednaných protokolů.</span><span class="sxs-lookup"><span data-stu-id="87f14-638">If Ssl3 is required, use one of the following configuration mechanisms to add it to the list of negotiated protocols.</span></span>

- <span data-ttu-id="87f14-639"><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=nameWithType>Vlastnost</span><span class="sxs-lookup"><span data-stu-id="87f14-639">The <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=nameWithType> property</span></span>

- <span data-ttu-id="87f14-640"><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType>Vlastnost</span><span class="sxs-lookup"><span data-stu-id="87f14-640">The <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> property</span></span>

- <span data-ttu-id="87f14-641">[\<transport>](../configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)Část [\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md) oddílu</span><span class="sxs-lookup"><span data-stu-id="87f14-641">The [\<transport>](../configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) section of the [\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md) section</span></span>

- <span data-ttu-id="87f14-642">[\<sslStreamSecurity>](../configure-apps/file-schema/wcf/sslstreamsecurity.md)Část [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md) oddílu</span><span class="sxs-lookup"><span data-stu-id="87f14-642">The [\<sslStreamSecurity>](../configure-apps/file-schema/wcf/sslstreamsecurity.md) section of the [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md) section</span></span>

<a name="WPF462"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="87f14-643">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="87f14-643">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="87f14-644">V .NET Framework 4.6.2 byly Windows Presentation Foundation rozšířeny v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="87f14-644">In the .NET Framework 4.6.2, Windows Presentation Foundation has been enhanced in the following areas:</span></span>

<span data-ttu-id="87f14-645">**Seskupení řazení**</span><span class="sxs-lookup"><span data-stu-id="87f14-645">**Group sorting**</span></span>

<span data-ttu-id="87f14-646">Aplikace, která používá <xref:System.Windows.Data.CollectionView> objekt k seskupení dat, teď může explicitně deklarovat způsob řazení skupin.</span><span class="sxs-lookup"><span data-stu-id="87f14-646">An application that uses a <xref:System.Windows.Data.CollectionView> object to group data can now explicitly declare how to  sort the groups.</span></span> <span data-ttu-id="87f14-647">Explicitní řazení řeší problém neintuitivního řazení, ke kterému dochází, když aplikace dynamicky přidává nebo odebírá skupiny nebo když změní hodnotu vlastností položek, které jsou součástí seskupení.</span><span class="sxs-lookup"><span data-stu-id="87f14-647">Explicit sorting addresses the problem of non-intuitive ordering that occurs when an app dynamically adds or removes groups, or when it changes the value of item properties involved in grouping.</span></span> <span data-ttu-id="87f14-648">Může také zvýšit výkon procesu vytváření skupiny přesunutím porovnání vlastností seskupení z řazení celé kolekce do řazení skupin.</span><span class="sxs-lookup"><span data-stu-id="87f14-648">It can also improve the performance of the group creation process by moving comparisons of the grouping properties from the sort of the full collection to the sort of the groups.</span></span>

<span data-ttu-id="87f14-649">Aby bylo možné podporovat řazení skupin, nové <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=nameWithType> a <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=nameWithType> vlastnosti popisují způsob řazení kolekce skupin vytvořených <xref:System.ComponentModel.GroupDescription> objektem.</span><span class="sxs-lookup"><span data-stu-id="87f14-649">To support group sorting, the new <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=nameWithType> and <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=nameWithType> properties describe how to sort the collection of groups produced by the <xref:System.ComponentModel.GroupDescription> object.</span></span> <span data-ttu-id="87f14-650">To je analogické jako způsob, jakým identicky pojmenované <xref:System.Windows.Data.ListCollectionView> vlastnosti popisují způsob řazení datových položek.</span><span class="sxs-lookup"><span data-stu-id="87f14-650">This is analogous to the way the identically named <xref:System.Windows.Data.ListCollectionView> properties describe how to sort the data items.</span></span>

<span data-ttu-id="87f14-651">Dvě nové statické vlastnosti <xref:System.Windows.Data.PropertyGroupDescription> třídy <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> a <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A> lze použít v nejběžnějších případech.</span><span class="sxs-lookup"><span data-stu-id="87f14-651">Two new static properties of the <xref:System.Windows.Data.PropertyGroupDescription> class,  <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> and <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A>, can be used for the most common cases.</span></span>

<span data-ttu-id="87f14-652">Například následující XAML seskupuje data podle stáří, řadí věkové skupiny ve vzestupném pořadí a seskupuje položky v rámci každé věkové skupiny podle příjmení.</span><span class="sxs-lookup"><span data-stu-id="87f14-652">For example, the following XAML groups data by age, sort the age groups in ascending order, and group the items within each age group by last name.</span></span>

```xaml
<GroupDescriptions>
     <PropertyGroupDescription
         PropertyName="Age"
         CustomSort=
              "{x:Static PropertyGroupDescription.CompareNamesAscending}"/>
     </PropertyGroupDescription>
</GroupDescriptions>

<SortDescriptions>
     <SortDescription PropertyName="LastName"/>
</SortDescriptions>
```

<span data-ttu-id="87f14-653">**Podpora dotykové klávesnice**</span><span class="sxs-lookup"><span data-stu-id="87f14-653">**Touch keyboard support**</span></span>

<span data-ttu-id="87f14-654">Podpora dotykové klávesnice umožňuje sledovat fokus v aplikacích WPF automatickým vyvoláním a chybějícím dotykovou klávesnicí ve Windows 10, když je vstup dotykového ovládání přijatý ovládacím prvkem, který může přebírat textový vstup.</span><span class="sxs-lookup"><span data-stu-id="87f14-654">Touch keyboard support enables focus tracking in WPF applications by automatically invoking and dismissing the touch Keyboard in Windows 10 when the touch input is received by a control that can take textual input.</span></span>

<span data-ttu-id="87f14-655">V předchozích verzích .NET Framework se aplikace WPF nemůžou vyjádřit k sledování fokusu bez zakázání podpory gesta perem a dotykového ovládání WPF.</span><span class="sxs-lookup"><span data-stu-id="87f14-655">In previous versions of .NET Framework, WPF applications can't opt into the focus tracking without disabling WPF pen/touch gesture support.</span></span> <span data-ttu-id="87f14-656">V důsledku toho musí aplikace WPF zvolit mezi plnou podporou WPF touch nebo se spoléhat na povýšení myší systému Windows.</span><span class="sxs-lookup"><span data-stu-id="87f14-656">As a result, WPF applications must choose between full WPF touch support or rely on Windows mouse promotion.</span></span>

<span data-ttu-id="87f14-657">**Rozlišení DPI pro monitor**</span><span class="sxs-lookup"><span data-stu-id="87f14-657">**Per-monitor DPI**</span></span>

<span data-ttu-id="87f14-658">Pro podporu nedávných rozmnožení prostředí s vysokým rozlišením DPI a hybridních DPI pro aplikace WPF se v .NET Framework 4.6.2 umožňuje sledovat jednotlivé monitory.</span><span class="sxs-lookup"><span data-stu-id="87f14-658">To support the recent proliferation of high-DPI and hybrid-DPI environments for WPF apps, WPF in the .NET Framework 4.6.2 enables per-monitor awareness.</span></span> <span data-ttu-id="87f14-659">Další informace o tom, jak povolit aplikaci WPF pro monitorování rozlišení DPI na monitoru, najdete v [ukázkách a v příručce pro vývojáře](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="87f14-659">See the [samples and developer guide](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) on GitHub for more information about how to enable your WPF app to become per-monitor DPI aware.</span></span>

<span data-ttu-id="87f14-660">V předchozích verzích .NET Framework aplikace WPF používají systémovou rozlišení DPI.</span><span class="sxs-lookup"><span data-stu-id="87f14-660">In previous versions of the .NET Framework, WPF apps are system-DPI aware.</span></span> <span data-ttu-id="87f14-661">Jinými slovy, uživatelské rozhraní aplikace se podle potřeby škáluje operačním systémem, v závislosti na DPI monitoru, na kterém je aplikace vykreslená.</span><span class="sxs-lookup"><span data-stu-id="87f14-661">In other words, the application's UI is scaled by the OS as appropriate, depending on the DPI of the monitor on which the app is rendered.</span></span>

<span data-ttu-id="87f14-662">Pro aplikace běžící pod .NET Framework 4.6.2 můžete v aplikacích WPF zakázat změny rozlišení DPI podle monitoru přidáním příkazu konfigurace do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="87f14-662">For apps running under the .NET Framework 4.6.2, you can disable per-monitor DPI changes in WPF apps by adding a configuration statement to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file, as follows:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Windows.DoNotScaleForDpiChanges=false"/>
</runtime>
```

<a name="WF462"></a>

### <a name="windows-workflow-foundation-wf"></a><span data-ttu-id="87f14-663">Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="87f14-663">Windows Workflow Foundation (WF)</span></span>

<span data-ttu-id="87f14-664">V .NET Framework 4.6.2 bylo programovací model Windows Workflow Foundation vylepšeno v následující oblasti:</span><span class="sxs-lookup"><span data-stu-id="87f14-664">In the .NET Framework 4.6.2, Windows Workflow Foundation has been enhanced in the following area:</span></span>

<span data-ttu-id="87f14-665">**Podpora pro výrazy jazyka C# a IntelliSense v přehostovaném návrháři WF**</span><span class="sxs-lookup"><span data-stu-id="87f14-665">**Support for C# expressions and IntelliSense in the Rehosted WF Designer**</span></span>

<span data-ttu-id="87f14-666">Počínaje .NET Framework 4,5 podporuje WF výrazy jazyka C# v návrháři sady Visual Studio i v pracovních postupech kódu.</span><span class="sxs-lookup"><span data-stu-id="87f14-666">Starting with .NET Framework 4.5, WF supports C# expressions in both the Visual Studio Designer and in code workflows.</span></span> <span data-ttu-id="87f14-667">Rehostovaná Návrhář postupu provádění je klíčovou funkcí WF, která umožňuje, aby se Návrhář postupu provádění v aplikaci mimo Visual Studio (například v WPF).</span><span class="sxs-lookup"><span data-stu-id="87f14-667">The Rehosted Workflow Designer is a key feature of WF that allows for the Workflow Designer to be in an application outside Visual Studio (for example, in WPF).</span></span>  <span data-ttu-id="87f14-668">Programovací model Windows Workflow Foundation poskytuje možnost podporovat výrazy jazyka C# a IntelliSense v Návrhář postupu provádění hostitele.</span><span class="sxs-lookup"><span data-stu-id="87f14-668">Windows Workflow Foundation provides the ability to support C# expressions and IntelliSense in the Rehosted Workflow Designer.</span></span> <span data-ttu-id="87f14-669">Další informace najdete na [blogu programovací model Windows Workflow Foundation](https://docs.microsoft.com/archive/blogs/workflowteam/building-c-expressions-support-and-intellisense-in-the-rehosted-workflow-designer).</span><span class="sxs-lookup"><span data-stu-id="87f14-669">For more information, see the [Windows Workflow Foundation blog](https://docs.microsoft.com/archive/blogs/workflowteam/building-c-expressions-support-and-intellisense-in-the-rehosted-workflow-designer).</span></span>

<span data-ttu-id="87f14-670">`Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio`Ve verzích .NET Framework před 4.6.2 se IntelliSense Návrháře WF při opětovném sestavení projektu pracovního postupu ze sady Visual Studio přeruší.</span><span class="sxs-lookup"><span data-stu-id="87f14-670">`Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio` In versions of the .NET Framework prior to 4.6.2, WF Designer IntelliSense is broken when a customer rebuilds a workflow project from Visual Studio.</span></span> <span data-ttu-id="87f14-671">I když je sestavení projektu úspěšné, typy pracovních postupů nejsou v Návrháři nalezeny a upozornění z IntelliSense pro chybějící typy pracovních postupů se zobrazí v okně **Seznam chyb** .</span><span class="sxs-lookup"><span data-stu-id="87f14-671">While the project build is successful, the workflow types are not found on the designer, and warnings from IntelliSense for the missing workflow types appear in the **Error List** window.</span></span> <span data-ttu-id="87f14-672">.NET Framework 4.6.2 řeší tento problém a zpřístupňuje IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="87f14-672">.NET Framework 4.6.2 addresses this issue and makes IntelliSense available.</span></span>

<span data-ttu-id="87f14-673">**Aplikace pracovního postupu V1 se sledováním pracovních postupů zapnuto v režimu FIPS**</span><span class="sxs-lookup"><span data-stu-id="87f14-673">**Workflow V1 applications with Workflow Tracking on now run under FIPS-mode**</span></span>

<span data-ttu-id="87f14-674">Počítače s povoleným režimem dodržování standardů FIPS teď můžou úspěšně spustit aplikaci ve stylu pracovního postupu verze 1 se sledováním pracovních postupů zapnutým.</span><span class="sxs-lookup"><span data-stu-id="87f14-674">Machines with FIPS Compliance Mode enabled can now successfully run a workflow Version 1-style application with Workflow tracking on.</span></span> <span data-ttu-id="87f14-675">Chcete-li povolit tento scénář, musíte provést následující změnu app.config souboru:</span><span class="sxs-lookup"><span data-stu-id="87f14-675">To enable this scenario, you must make the following change to your app.config file:</span></span>

```xml
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />
```

<span data-ttu-id="87f14-676">Pokud tento scénář není povolený, bude při spuštění aplikace i nadále vygenerována výjimka se zprávou "Tato implementace není součástí ověřených kryptografických algoritmů standardu FIPS platformy Windows."</span><span class="sxs-lookup"><span data-stu-id="87f14-676">If this scenario is not enabled, running the application continues to generate an exception with the message, "This implementation is not part of the Windows Platform FIPS validated cryptographic algorithms."</span></span>

<span data-ttu-id="87f14-677">**Vylepšení pracovního postupu při použití dynamické aktualizace se sadou Visual Studio Návrhář postupu provádění**</span><span class="sxs-lookup"><span data-stu-id="87f14-677">**Workflow Improvements when using Dynamic Update with Visual Studio Workflow Designer**</span></span>

<span data-ttu-id="87f14-678">Návrháři aktivity Návrhář postupu provádění, vývojový diagram a jiní návrháři aktivit pracovního postupu nyní úspěšně načetli a zobrazili pracovní postupy, které byly uloženy po volání <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="87f14-678">The Workflow Designer, FlowChart Activity Designer, and other Workflow Activity Designers now successfully load and display workflows that have been saved after calling  the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="87f14-679">Ve verzích .NET Framework před .NET Framework 4.6.2 načítání souboru XAML v sadě Visual Studio pro pracovní postup, který byl uložen po volání, <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> může způsobit následující problémy:</span><span class="sxs-lookup"><span data-stu-id="87f14-679">In versions of the .NET Framework before .NET Framework 4.6.2, loading a XAML file in Visual Studio for a workflow that has been saved after calling <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> can result in the following issues:</span></span>

- <span data-ttu-id="87f14-680">Návrhář postupu provádění nemůže správně načíst soubor XAML (když <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=nameWithType> je na konci řádku).</span><span class="sxs-lookup"><span data-stu-id="87f14-680">The Workflow Designer can't load the XAML file correctly (when the <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=nameWithType> is at the end of the line).</span></span>

- <span data-ttu-id="87f14-681">Návrhář aktivity vývojového diagramu nebo jiný Návrhář aktivity pracovního postupu může zobrazit všechny objekty ve výchozích umístěních na rozdíl od hodnot připojených vlastností.</span><span class="sxs-lookup"><span data-stu-id="87f14-681">Flowchart Activity Designer or other Workflow Activity Designers may display all objects in their default locations as opposed to attached property values.</span></span>

<a name="clickonce-1"></a>

### <a name="clickonce"></a><span data-ttu-id="87f14-682">ClickOnce</span><span class="sxs-lookup"><span data-stu-id="87f14-682">ClickOnce</span></span>

<span data-ttu-id="87f14-683">ClickOnce je aktualizovaná tak, aby podporovala TLS 1,1 a TLS 1,2 kromě protokolu 1,0, který už podporuje.</span><span class="sxs-lookup"><span data-stu-id="87f14-683">ClickOnce has been updated to support TLS 1.1 and TLS 1.2 in addition to the 1.0 protocol, which it already supports.</span></span> <span data-ttu-id="87f14-684">ClickOnce automaticky zjišťuje, který protokol je vyžadován; aby bylo možné povolit podporu TLS 1,1 a 1,2, nejsou v rámci aplikace ClickOnce nutné žádné další kroky.</span><span class="sxs-lookup"><span data-stu-id="87f14-684">ClickOnce automatically detects which protocol is required; no extra steps within the ClickOnce application are required to enable TLS 1.1 and 1.2 support.</span></span>

<a name="UWPConvert"></a>

### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a><span data-ttu-id="87f14-685">Převod aplikací model Windows Forms a WPF na aplikace pro UWP</span><span class="sxs-lookup"><span data-stu-id="87f14-685">Converting Windows Forms and WPF apps to  UWP apps</span></span>

<span data-ttu-id="87f14-686">Windows teď nabízí možnosti, jak přenést existující desktopové aplikace pro Windows, včetně WPF a model Windows Forms aplikací, do Univerzální platforma Windows (UWP).</span><span class="sxs-lookup"><span data-stu-id="87f14-686">Windows now offers capabilities to bring existing Windows desktop apps, including WPF and Windows Forms apps, to the Universal Windows Platform (UWP).</span></span> <span data-ttu-id="87f14-687">Tato technologie funguje jako most, protože vám umožní postupně migrovat stávající základ kódu na UWP. tím se vaše aplikace přinášejí všem zařízením s Windows 10.</span><span class="sxs-lookup"><span data-stu-id="87f14-687">This technology acts as a bridge by enabling you to gradually migrate your existing code base to UWP, thereby bringing your app to all Windows 10 devices.</span></span>

<span data-ttu-id="87f14-688">Převedená aplikace klasické pracovní plochy získala identitu aplikace podobnou identitě aplikací v aplikacích UWP, což zpřístupňuje rozhraní API UWP pro povolení funkcí, jako jsou živé dlaždice a oznámení.</span><span class="sxs-lookup"><span data-stu-id="87f14-688">Converted desktop apps gain an app identity similar to the app identity of UWP apps, which makes UWP APIs accessible to enable features such as Live Tiles and notifications.</span></span> <span data-ttu-id="87f14-689">Aplikace se i nadále chová stejně jako dřív a běží jako aplikace s plnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="87f14-689">The app continues to behave as before and runs as a full trust app.</span></span> <span data-ttu-id="87f14-690">Po převedení aplikace lze do stávajícího procesu úplného vztahu důvěryhodnosti přidat proces kontejneru aplikace a přidat adaptivní uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="87f14-690">Once the app is converted, an app container process can be added to the existing full trust process to add an adaptive user interface.</span></span> <span data-ttu-id="87f14-691">Když se všechny funkce přesunou do procesu kontejneru aplikace, může se odebrat úplný proces důvěryhodnosti a nová aplikace pro UWP se dá zpřístupnit pro všechna zařízení s Windows 10.</span><span class="sxs-lookup"><span data-stu-id="87f14-691">When all functionality is moved to the app container process, the full trust process can be removed and the new UWP app can be made available to all Windows 10 devices.</span></span>

<a name="Debug462"></a>

### <a name="debugging-improvements"></a><span data-ttu-id="87f14-692">Vylepšení ladění</span><span class="sxs-lookup"><span data-stu-id="87f14-692">Debugging improvements</span></span>

<span data-ttu-id="87f14-693">*Rozhraní API pro nespravované ladění* bylo vylepšeno v .NET Framework 4.6.2, aby bylo možné provést další analýzu při <xref:System.NullReferenceException> vyvolání, aby bylo možné určit, která proměnná v jednom řádku zdrojového kódu je `null` .</span><span class="sxs-lookup"><span data-stu-id="87f14-693">The *unmanaged debugging API* has been enhanced in the .NET Framework 4.6.2 to perform additional analysis when a <xref:System.NullReferenceException> is thrown so that it is possible to determine which variable in a single line of source code is `null`.</span></span>   <span data-ttu-id="87f14-694">Pro podporu tohoto scénáře byla do nespravovaného ladicího rozhraní API přidána následující rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="87f14-694">To support this scenario, the following APIs have been added to the unmanaged debugging API.</span></span>

- <span data-ttu-id="87f14-695">Rozhraní [ICorDebugCode4](../unmanaged-api/debugging/icordebugcode4-interface.md), [ICorDebugVariableHome](../unmanaged-api/debugging/icordebugvariablehome-interface.md)a [ICorDebugVariableHomeEnum](../unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) , která zveřejňují nativní domy spravovaných proměnných.</span><span class="sxs-lookup"><span data-stu-id="87f14-695">The [ICorDebugCode4](../unmanaged-api/debugging/icordebugcode4-interface.md), [ICorDebugVariableHome](../unmanaged-api/debugging/icordebugvariablehome-interface.md), and [ICorDebugVariableHomeEnum](../unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interfaces, which expose the native homes of managed variables.</span></span> <span data-ttu-id="87f14-696">To umožňuje ladicím programům provádět některé analýzy toku kódu <xref:System.NullReferenceException> , když dojde k chybě a chcete-li pracovat zpět k určení spravované proměnné, která odpovídá nativnímu umístění, které bylo `null` .</span><span class="sxs-lookup"><span data-stu-id="87f14-696">This enables debuggers to do some code flow analysis when a  <xref:System.NullReferenceException> occurs and to work backwards to determine the managed variable that corresponds to the native location that was `null`.</span></span>

- <span data-ttu-id="87f14-697">Metoda [ICorDebugType2:: GetTypeId.](../unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) poskytuje mapování pro ICorDebugType pro [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md), což ladicímu programu umožňuje získat [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) bez instance ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="87f14-697">The [ICorDebugType2::GetTypeID](../unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) method provides a mapping for ICorDebugType to [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md), which allows the debugger to obtain a [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) without an instance of the ICorDebugType.</span></span> <span data-ttu-id="87f14-698">Existující rozhraní API na [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) lze použít k určení rozložení třídy typu.</span><span class="sxs-lookup"><span data-stu-id="87f14-698">Existing APIs on [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) can then be used to determine the class layout of the type.</span></span>

<a name="v461"></a>

## <a name="whats-new-in-net-framework-461"></a><span data-ttu-id="87f14-699">Co je nového v .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="87f14-699">What's new in .NET Framework 4.6.1</span></span>

<span data-ttu-id="87f14-700">.NET Framework 4.6.1 zahrnuje nové funkce v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="87f14-700">The .NET Framework 4.6.1 includes new features in the following areas:</span></span>

- [<span data-ttu-id="87f14-701">Kryptografie</span><span class="sxs-lookup"><span data-stu-id="87f14-701">Cryptography</span></span>](#Crypto)

- [<span data-ttu-id="87f14-702">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="87f14-702">ADO.NET</span></span>](#ADO.NET461)

- [<span data-ttu-id="87f14-703">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="87f14-703">Windows Presentation Foundation (WPF)</span></span>](#WPF461)

- [<span data-ttu-id="87f14-704">Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="87f14-704">Windows Workflow Foundation</span></span>](#WWF461)

- [<span data-ttu-id="87f14-705">Profilace</span><span class="sxs-lookup"><span data-stu-id="87f14-705">Profiling</span></span>](#Profile461)

- [<span data-ttu-id="87f14-706">NGen</span><span class="sxs-lookup"><span data-stu-id="87f14-706">NGen</span></span>](#NGEN461)

<span data-ttu-id="87f14-707">Další informace o .NET Framework 4.6.1 najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="87f14-707">For more information on the .NET Framework 4.6.1, see the following topics:</span></span>

- [<span data-ttu-id="87f14-708">Seznam změn .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="87f14-708">.NET Framework 4.6.1 list of changes</span></span>](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-changes.md)

- [<span data-ttu-id="87f14-709">Kompatibilita aplikací v 4.6.1</span><span class="sxs-lookup"><span data-stu-id="87f14-709">Application Compatibility in 4.6.1</span></span>](../migration-guide/application-compatibility.md)

- <span data-ttu-id="87f14-710">[Rozdíl .NET Framework rozhraní API](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-api-changes.md) (na GitHubu)</span><span class="sxs-lookup"><span data-stu-id="87f14-710">[.NET Framework API diff](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-api-changes.md) (on GitHub)</span></span>

<a name="Crypto"></a>

### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a><span data-ttu-id="87f14-711">Kryptografie: podpora pro certifikáty x509 obsahující ECDSA</span><span class="sxs-lookup"><span data-stu-id="87f14-711">Cryptography: Support for X509 certificates containing ECDSA</span></span>

<span data-ttu-id="87f14-712">.NET Framework 4,6 přidal podporu algoritmem RSACng pro certifikáty x509.</span><span class="sxs-lookup"><span data-stu-id="87f14-712">.NET Framework 4.6 added RSACng support for X509 certificates.</span></span> <span data-ttu-id="87f14-713">.NET Framework 4.6.1 přidává podporu pro certifikáty x509 ECDSA (s eliptickou křivkou pro digitální podpis algoritmu).</span><span class="sxs-lookup"><span data-stu-id="87f14-713">The .NET Framework 4.6.1 adds support for ECDSA (Elliptic Curve Digital Signature Algorithm) X509 certificates.</span></span>

<span data-ttu-id="87f14-714">ECDSA nabízí lepší výkon a jedná se o bezpečnější algoritmus šifrování než RSA. poskytuje skvělou volbu toho, kde je výkon a škálovatelnost protokolu TLS (Transport Layer Security) obavy.</span><span class="sxs-lookup"><span data-stu-id="87f14-714">ECDSA offers better performance and is a more secure cryptography algorithm than RSA, providing an excellent choice where Transport Layer Security (TLS) performance and scalability is a concern.</span></span> <span data-ttu-id="87f14-715">Implementace .NET Framework zabalí volání do stávajících funkcí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="87f14-715">The .NET Framework implementation wraps calls into existing Windows functionality.</span></span>

<span data-ttu-id="87f14-716">Následující příklad kódu ukazuje, jak snadné je generovat signaturu pro datový proud bajtů pomocí nové podpory pro certifikáty ECDSA x509 zahrnuté do .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="87f14-716">The following example code shows how easy it is to generate a signature for a byte stream by using the new  support for ECDSA  X509 certificates included in the .NET Framework 4.6.1.</span></span>

[!code-csharp[whatsnew.461.crypto#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#1)]
[!code-vb[whatsnew.461.crypto#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code461.vb#1)]

<span data-ttu-id="87f14-717">To nabízí označený rozdíl na kód potřebný k vygenerování podpisu v .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="87f14-717">This offers a marked contrast to the code needed to generate a signature in .NET Framework 4.6.</span></span>

[!code-csharp[whatsnew.461.crypto#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#2)]
[!code-vb[whatsnew.461.crypto#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code46.vb#2)]

<a name="ADO.NET461"></a>

### <a name="adonet"></a><span data-ttu-id="87f14-718">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="87f14-718">ADO.NET</span></span>

<span data-ttu-id="87f14-719">Do ADO.NET byly přidány následující:</span><span class="sxs-lookup"><span data-stu-id="87f14-719">The following have been added to ADO.NET:</span></span>

<span data-ttu-id="87f14-720">**Always Encrypted podpora pro klíče chráněné hardwarem**</span><span class="sxs-lookup"><span data-stu-id="87f14-720">**Always Encrypted support for hardware protected keys**</span></span>

<span data-ttu-id="87f14-721">ADO.NET teď podporuje nativně ukládání Always Encrypted hlavních klíčů sloupce v modulech zabezpečení hardwaru (HSM).</span><span class="sxs-lookup"><span data-stu-id="87f14-721">ADO.NET now supports storing Always Encrypted column master keys natively in Hardware Security Modules (HSMs).</span></span> <span data-ttu-id="87f14-722">Díky této podpoře můžou zákazníci využívat asymetrické klíče uložené v HSM, aniž by museli psát vlastní Zprostředkovatelé úložiště klíčů pro vlastní sloupce a zaregistrovali je v aplikacích.</span><span class="sxs-lookup"><span data-stu-id="87f14-722">With this support, customers can leverage asymmetric keys stored in HSMs without having to write custom column master key store providers and registering them in applications.</span></span>

<span data-ttu-id="87f14-723">Aby mohli uživatelé získat přístup k Always Encrypted chráněným pomocí hlavních klíčů, které jsou uložené v modulu hardwarového zabezpečení (HSM), musí si do aplikačních serverů nebo klientských počítačů nainstalovat poskytovatele kryptografických služeb na základě dodavatele modulu hardwarového zabezpečení (HSM).</span><span class="sxs-lookup"><span data-stu-id="87f14-723">Customers need to install the HSM vendor-provided CSP provider or CNG key store providers on the app servers or client computers in order to access Always Encrypted data protected with column master keys stored in a HSM.</span></span>

<span data-ttu-id="87f14-724">**Vylepšené <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> chování připojení pro AlwaysOn**</span><span class="sxs-lookup"><span data-stu-id="87f14-724">**Improved <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> connection behavior for AlwaysOn**</span></span>

<span data-ttu-id="87f14-725">SqlClient nyní automaticky poskytuje rychlejší připojení ke skupině dostupnosti AlwaysOn (AG).</span><span class="sxs-lookup"><span data-stu-id="87f14-725">SqlClient now automatically provides faster connections to an AlwaysOn Availability Group (AG).</span></span> <span data-ttu-id="87f14-726">Transparentně detekuje, jestli se vaše aplikace připojuje ke skupině dostupnosti AlwaysOn (AG) v jiné podsíti, a rychle zjistí aktuální aktivní server a poskytuje připojení k serveru.</span><span class="sxs-lookup"><span data-stu-id="87f14-726">It transparently detects whether your application is connecting to an AlwaysOn availability group (AG) on a different subnet and quickly discovers the current active server and provides a connection to the server.</span></span> <span data-ttu-id="87f14-727">Před touto verzí musela aplikace nastavit připojovací řetězec tak, aby obsahovala `"MultisubnetFailover=true"` , aby označovala, že se připojil ke skupině dostupnosti AlwaysOn.</span><span class="sxs-lookup"><span data-stu-id="87f14-727">Prior to this release, an application had to set the connection string to include `"MultisubnetFailover=true"` to indicate that it was connecting to an AlwaysOn Availability Group.</span></span> <span data-ttu-id="87f14-728">Bez nastavení klíčového slova Connection na `true` se může u aplikace při připojování ke skupině dostupnosti AlwaysOn vyskytnout časový limit.</span><span class="sxs-lookup"><span data-stu-id="87f14-728">Without setting the connection keyword to `true`, an application might experience a timeout while connecting to an AlwaysOn Availability Group.</span></span> <span data-ttu-id="87f14-729">V této *verzi nemusí aplikace* nastavovat <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> `true` již.</span><span class="sxs-lookup"><span data-stu-id="87f14-729">With this release, an application does *not* need to set <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> to `true` anymore.</span></span> <span data-ttu-id="87f14-730">Další informace o podpoře SqlClient pro skupiny dostupnosti Always On najdete v článku [Podpora SqlClient pro vysokou dostupnost a zotavení po havárii](../data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-730">For more information about SqlClient support for Always On Availability Groups, see [SqlClient Support for High Availability, Disaster Recovery](../data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).</span></span>

<a name="WPF461"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="87f14-731">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="87f14-731">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="87f14-732">Windows Presentation Foundation zahrnuje řadu vylepšení a změn.</span><span class="sxs-lookup"><span data-stu-id="87f14-732">Windows Presentation Foundation includes a number of improvements and changes.</span></span>

<span data-ttu-id="87f14-733">**Vylepšený výkon**</span><span class="sxs-lookup"><span data-stu-id="87f14-733">**Improved performance**</span></span>

<span data-ttu-id="87f14-734">Zpoždění při vyvolávání událostí dotyku bylo opraveno .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="87f14-734">The delay in firing touch events has been fixed in the .NET Framework 4.6.1.</span></span> <span data-ttu-id="87f14-735">Kromě toho psaní v <xref:System.Windows.Controls.RichTextBox> ovládacím prvku již během rychlého vstupu nespojuje vlákno vykreslování.</span><span class="sxs-lookup"><span data-stu-id="87f14-735">In addition, typing in a <xref:System.Windows.Controls.RichTextBox> control no longer ties up the render thread during fast input.</span></span>

<span data-ttu-id="87f14-736">**Vylepšení kontroly pravopisu**</span><span class="sxs-lookup"><span data-stu-id="87f14-736">**Spell checking improvements**</span></span>

<span data-ttu-id="87f14-737">Kontrola pravopisu v subsystému WPF byla aktualizována na Windows 8.1 a novějších verzích, aby bylo možné využívat operační systém pro kontrolu pravopisu dalších jazyků.</span><span class="sxs-lookup"><span data-stu-id="87f14-737">The spell checker in WPF has been updated on Windows 8.1 and later versions to leverage operating system support for spell-checking additional languages.</span></span>  <span data-ttu-id="87f14-738">Před Windows 8.1 se ve verzích Windows nezměnily žádné funkce.</span><span class="sxs-lookup"><span data-stu-id="87f14-738">There is no change in functionality on Windows versions prior to Windows 8.1.</span></span>

<span data-ttu-id="87f14-739">Stejně jako v předchozích verzích .NET Framework se detekuje jazyk pro <xref:System.Windows.Controls.TextBox> Ora blok ovládacího prvku <xref:System.Windows.Controls.RichTextBox> hledáním informací v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="87f14-739">As in previous versions of the .NET Framework, the language for a <xref:System.Windows.Controls.TextBox> control ora <xref:System.Windows.Controls.RichTextBox> block is detected by looking for information in the following order:</span></span>

- <span data-ttu-id="87f14-740">`xml:lang`, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="87f14-740">`xml:lang`, if it is present.</span></span>

- <span data-ttu-id="87f14-741">Aktuální jazyk vstupu.</span><span class="sxs-lookup"><span data-stu-id="87f14-741">Current input language.</span></span>

- <span data-ttu-id="87f14-742">Aktuální jazyková verze vlákna.</span><span class="sxs-lookup"><span data-stu-id="87f14-742">Current thread culture.</span></span>

<span data-ttu-id="87f14-743">Další informace o podpoře jazyků v subsystému WPF najdete v [blogovém příspěvku WPF o funkcích .NET Framework 4.6.1](https://devblogs.microsoft.com/wpf/wpf-in-net-4-6-1/).</span><span class="sxs-lookup"><span data-stu-id="87f14-743">For more information on language support in WPF, see the [WPF blog post on .NET Framework 4.6.1 features](https://devblogs.microsoft.com/wpf/wpf-in-net-4-6-1/).</span></span>

<span data-ttu-id="87f14-744">**Další podpora pro vlastní slovníky pro jednotlivé uživatele**</span><span class="sxs-lookup"><span data-stu-id="87f14-744">**Additional support for per-user custom dictionaries**</span></span>

<span data-ttu-id="87f14-745">V .NET Framework 4.6.1 rozpozná WPF vlastní slovníky, které jsou zaregistrované globálně.</span><span class="sxs-lookup"><span data-stu-id="87f14-745">In .NET Framework 4.6.1, WPF recognizes custom dictionaries that are registered globally.</span></span> <span data-ttu-id="87f14-746">Tato funkce je kromě možnosti registrace pro jednotlivé ovládací prvky k dispozici.</span><span class="sxs-lookup"><span data-stu-id="87f14-746">This capability is available in addition to the ability to register them per-control.</span></span>

<span data-ttu-id="87f14-747">V předchozích verzích WPF vlastní slovníky nerozpoznaly vyloučená slova a seznamy automatických oprav.</span><span class="sxs-lookup"><span data-stu-id="87f14-747">In previous versions of WPF, custom dictionaries did not recognize Excluded Words and AutoCorrect lists.</span></span> <span data-ttu-id="87f14-748">Jsou podporovány v Windows 8.1 a Windows 10 prostřednictvím souborů, které lze umístit do `%AppData%\Microsoft\Spelling\<language tag>` adresáře.</span><span class="sxs-lookup"><span data-stu-id="87f14-748">They are supported on Windows 8.1 and Windows 10 through the use of files that can be placed under the `%AppData%\Microsoft\Spelling\<language tag>` directory.</span></span>  <span data-ttu-id="87f14-749">Následující pravidla se vztahují na tyto soubory:</span><span class="sxs-lookup"><span data-stu-id="87f14-749">The following rules apply to these files:</span></span>

- <span data-ttu-id="87f14-750">Soubory by měly mít přípony. dic (pro přidaná slova),. EXC (vyloučená slova) nebo. ACL (pro automatické opravy).</span><span class="sxs-lookup"><span data-stu-id="87f14-750">The files should have extensions of .dic (for added words), .exc (for excluded words), or .acl (for AutoCorrect).</span></span>

- <span data-ttu-id="87f14-751">Soubory by měly být UTF-16 LE prostého textu, který začíná znakem pořadí bajtů (BOM).</span><span class="sxs-lookup"><span data-stu-id="87f14-751">The files should be UTF-16 LE plaintext that starts with the Byte Order Mark (BOM).</span></span>

- <span data-ttu-id="87f14-752">Každý řádek by měl obsahovat slovo (v seznamech přidaných a vyloučených slov) nebo dvojici automatických slov oddělených svislým pruhem ("&#124;") (v seznamu slov pro automatické opravy).</span><span class="sxs-lookup"><span data-stu-id="87f14-752">Each line should consist of a word (in the added and excluded word lists), or an autocorrect pair with the words separated by a vertical bar ("&#124;") (in the AutoCorrect word list).</span></span>

- <span data-ttu-id="87f14-753">Tyto soubory jsou považovány za jen pro čtení a systém je nemění.</span><span class="sxs-lookup"><span data-stu-id="87f14-753">These files are considered read-only and are not modified by the system.</span></span>

> [!NOTE]
> <span data-ttu-id="87f14-754">Tyto nové formáty souborů nejsou přímo podporovány rozhraními API pro kontrolu pravopisu WPF a vlastní slovníky dodávané WPF v aplikacích by měly dál používat soubory. lex.</span><span class="sxs-lookup"><span data-stu-id="87f14-754">These new file-formats are not directly supported by the WPF spell checking APIs, and the custom dictionaries supplied to WPF in applications should continue to use .lex files.</span></span>

<span data-ttu-id="87f14-755">**ukázky**</span><span class="sxs-lookup"><span data-stu-id="87f14-755">**Samples**</span></span>

<span data-ttu-id="87f14-756">V úložišti GitHub [Microsoft/WPF-Samples](https://github.com/Microsoft/WPF-Samples) je několik ukázek WPF.</span><span class="sxs-lookup"><span data-stu-id="87f14-756">There are a number of WPF samples on the [Microsoft/WPF-Samples](https://github.com/Microsoft/WPF-Samples) GitHub repository.</span></span> <span data-ttu-id="87f14-757">Nám pomůžou vylepšit naše ukázky odesláním žádosti o přijetí změn nebo otevřením [problému GitHubu](https://github.com/Microsoft/WPF-Samples/issues).</span><span class="sxs-lookup"><span data-stu-id="87f14-757">Help us improve our samples by sending us a pull-request or opening a [GitHub issue](https://github.com/Microsoft/WPF-Samples/issues).</span></span>

<span data-ttu-id="87f14-758">**Rozšíření DirectX**</span><span class="sxs-lookup"><span data-stu-id="87f14-758">**DirectX extensions**</span></span>

<span data-ttu-id="87f14-759">WPF obsahuje [balíček NuGet](https://www.nuget.org/packages/Microsoft.Wpf.Interop.DirectX-x86/) , který poskytuje nové implementace, které usnadňují <xref:System.Windows.Interop.D3DImage> spolupráci s DX10 a DX11 obsahem.</span><span class="sxs-lookup"><span data-stu-id="87f14-759">WPF includes a [NuGet package](https://www.nuget.org/packages/Microsoft.Wpf.Interop.DirectX-x86/) that provides new implementations of <xref:System.Windows.Interop.D3DImage> that make it easy for you to interoperate with DX10 and Dx11 content.</span></span> <span data-ttu-id="87f14-760">Kód pro tento balíček je otevřený source a je dostupný [na GitHubu](https://github.com/Microsoft/WPFDXInterop).</span><span class="sxs-lookup"><span data-stu-id="87f14-760">The code for this package has been open sourced and is available [on GitHub](https://github.com/Microsoft/WPFDXInterop).</span></span>

<a name="WWF461"></a>

### <a name="windows-workflow-foundation-transactions"></a><span data-ttu-id="87f14-761">Programovací model Windows Workflow Foundation: transakcí</span><span class="sxs-lookup"><span data-stu-id="87f14-761">Windows Workflow Foundation: Transactions</span></span>

<span data-ttu-id="87f14-762"><xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType>Metoda teď může použít jiný správce distribuovaných transakcí než MSDTC k povýšení transakce.</span><span class="sxs-lookup"><span data-stu-id="87f14-762">The <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> method can now use a distributed transaction manager other than MSDTC to promote the transaction.</span></span> <span data-ttu-id="87f14-763">To provedete tak, že zadáte identifikátor ID zvýšení transakce GUID k novému <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> přetížení.</span><span class="sxs-lookup"><span data-stu-id="87f14-763">You do this by specifying a GUID transaction promoter identifier to the  new <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> overload .</span></span> <span data-ttu-id="87f14-764">Pokud je tato operace úspěšná, existují omezení na možnosti transakce.</span><span class="sxs-lookup"><span data-stu-id="87f14-764">If this operation is successful, there are limitations placed on the capabilities of the transaction.</span></span> <span data-ttu-id="87f14-765">Jakmile je povýšen na transakci bez služby MSDTC, následující metody vyvolávají výjimku, <xref:System.Transactions.TransactionPromotionException> protože tyto metody vyžadují povýšení na MSDTC:</span><span class="sxs-lookup"><span data-stu-id="87f14-765">Once a non-MSDTC transaction promoter is enlisted, the following methods throw a <xref:System.Transactions.TransactionPromotionException> because these methods require promotion to MSDTC:</span></span>

- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetDtcTransaction%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetExportCookie%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetTransmitterPropagationToken%2A?displayProperty=nameWithType>

<span data-ttu-id="87f14-766">Jakmile je vyřazení transakce bez služby MSDTC, je nutné ji použít pro budoucí trvalé zařazení pomocí protokolů, které definuje.</span><span class="sxs-lookup"><span data-stu-id="87f14-766">Once a non-MSDTC transaction promoter is enlisted, it must be used for future durable enlistments by using protocols that it defines.</span></span> <span data-ttu-id="87f14-767">Na <xref:System.Guid> zvýšení transakce lze získat pomocí <xref:System.Transactions.Transaction.PromoterType%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="87f14-767">The <xref:System.Guid> of the transaction promoter can be obtained by using the <xref:System.Transactions.Transaction.PromoterType%2A> property.</span></span> <span data-ttu-id="87f14-768">V případě, že transakce propaguje, poskytne vykonavatel transakce <xref:System.Byte> pole, které představuje povýšený token.</span><span class="sxs-lookup"><span data-stu-id="87f14-768">When the transaction promotes, the transaction promoter provides a <xref:System.Byte> array that represents the promoted token.</span></span> <span data-ttu-id="87f14-769">Aplikace může získat povýšený token pro transakci, která není povýšena MSDTC, s <xref:System.Transactions.Transaction.GetPromotedToken%2A> metodou.</span><span class="sxs-lookup"><span data-stu-id="87f14-769">An application can obtain the promoted token for a non-MSDTC promoted transaction with the <xref:System.Transactions.Transaction.GetPromotedToken%2A> method.</span></span>

<span data-ttu-id="87f14-770">Aby <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> bylo možné operaci povýšení úspěšně dokončit, musí se uživatelé nového přetížení řídit konkrétní sekvencí volání.</span><span class="sxs-lookup"><span data-stu-id="87f14-770">Users of the new <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> overload must follow a specific call sequence in order for the promotion operation to complete successfully.</span></span> <span data-ttu-id="87f14-771">Tato pravidla jsou popsána v dokumentaci metody.</span><span class="sxs-lookup"><span data-stu-id="87f14-771">These rules are documented in the method's documentation.</span></span>

<a name="Profile461"></a>

### <a name="profiling"></a><span data-ttu-id="87f14-772">Profilace</span><span class="sxs-lookup"><span data-stu-id="87f14-772">Profiling</span></span>

<span data-ttu-id="87f14-773">Nespravované rozhraní API profilování bylo vylepšeno následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="87f14-773">The unmanaged profiling API has been enhanced as follows:</span></span>

- <span data-ttu-id="87f14-774">Lepší podpora pro přístup k soubory PDB v rozhraní [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="87f14-774">Better support for accessing PDBs in the [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) interface.</span></span>

  <span data-ttu-id="87f14-775">V ASP.NET Core se sestavení stane mnohem častější, aby sestavení bylo zkompilováno v paměti pomocí Roslyn.</span><span class="sxs-lookup"><span data-stu-id="87f14-775">In ASP.NET Core, it is becoming much more common for assemblies to be compiled in-memory by Roslyn.</span></span> <span data-ttu-id="87f14-776">Pro vývojáře, kteří vytvářejí nástroje pro profilaci, to znamená, že soubory PDB, který historicky byly serializovány na disk, již nemusí být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="87f14-776">For developers making profiling tools, this means that PDBs that historically were serialized on disk may no longer be present.</span></span> <span data-ttu-id="87f14-777">Nástroje profileru často používají soubory PDB k mapování kódu zpět na zdrojové řádky pro úlohy, jako je pokrytí kódu nebo analýza výkonu po jednotlivých řádcích.</span><span class="sxs-lookup"><span data-stu-id="87f14-777">Profiler tools often use PDBs to map code back to source lines for tasks such as code coverage or line-by-line performance analysis.</span></span> <span data-ttu-id="87f14-778">Rozhraní [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) nyní obsahuje dvě nové metody, [ICorProfilerInfo7:: GetInMemorySymbolsLength](../unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) a [ICorProfilerInfo7:: ReadInMemorySymbols](../unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)k poskytnutí těchto nástrojů profileru s přístupem k datům PDB v paměti pomocí nových rozhraní API může Profiler získat obsah souboru PDB v paměti jako bajtové pole a pak ho zpracovat nebo serializovat na disk.</span><span class="sxs-lookup"><span data-stu-id="87f14-778">The [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) interface now includes two new methods, [ICorProfilerInfo7::GetInMemorySymbolsLength](../unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) and [ICorProfilerInfo7::ReadInMemorySymbols](../unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md), to provide these profiler tools with access to the in-memory PDB data, By using the new APIs, a profiler can obtain the contents of an in-memory PDB as a byte array and then process it or serialize it to disk.</span></span>

- <span data-ttu-id="87f14-779">Lepší instrumentaci pomocí rozhraní ICorProfiler.</span><span class="sxs-lookup"><span data-stu-id="87f14-779">Better instrumentation with the ICorProfiler interface.</span></span>

  <span data-ttu-id="87f14-780">Profilery, které používají `ICorProfiler` funkci ReJIT rozhraní API pro dynamickou instrumentaci, teď můžou upravovat některá metadata.</span><span class="sxs-lookup"><span data-stu-id="87f14-780">Profilers that are using the `ICorProfiler` APIs ReJit functionality for dynamic instrumentation can now modify some metadata.</span></span> <span data-ttu-id="87f14-781">Dříve takové nástroje mohly instrumentaci IL kdykoli instrumentovat, ale metadata se dají upravovat jenom v době načtení modulu.</span><span class="sxs-lookup"><span data-stu-id="87f14-781">Previously such tools could instrument IL at any time, but metadata could only be modified at module load time.</span></span> <span data-ttu-id="87f14-782">Vzhledem k tomu, že IL odkazuje na metadata, omezíme tak druhy instrumentace, které by bylo možné provést.</span><span class="sxs-lookup"><span data-stu-id="87f14-782">Because IL refers to metadata, this limited the kinds of instrumentation that could be done.</span></span> <span data-ttu-id="87f14-783">Některé z těchto omezení jsme převedli přidáním metody [ICorProfilerInfo7:: ApplyMetaData](../unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) pro podporu podmnožiny úprav metadat po načtení modulu, zejména přidáním nových `AssemblyRef` záznamů,,,, a `TypeRef` `TypeSpec` `MemberRef` `MemberSpec` `UserString` .</span><span class="sxs-lookup"><span data-stu-id="87f14-783">We have lifted some of those limits by adding the [ICorProfilerInfo7::ApplyMetaData](../unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) method to support a subset of metadata edits after the module loads, in particular by adding new `AssemblyRef`, `TypeRef`, `TypeSpec`, `MemberRef`, `MemberSpec`, and `UserString` records.</span></span> <span data-ttu-id="87f14-784">Tato změna přináší mnohem širší množství možností instrumentace.</span><span class="sxs-lookup"><span data-stu-id="87f14-784">This change makes a much broader range of on-the-fly instrumentation possible.</span></span>

<a name="NGEN461"></a>

### <a name="native-image-generator-ngen-pdbs"></a><span data-ttu-id="87f14-785">Generátor nativních bitových kopií (NGEN) soubory PDB</span><span class="sxs-lookup"><span data-stu-id="87f14-785">Native Image Generator (NGEN) PDBs</span></span>

<span data-ttu-id="87f14-786">Trasování událostí mezi počítači umožňuje zákazníkům profilovat program na počítači a a prohlédnout si data profilace pomocí mapování zdrojového řádku na počítači B. pomocí předchozích verzí .NET Framework, uživatel zkopíruje všechny moduly a nativní bitové kopie z profilované počítače do počítače analýzy, který obsahuje soubor. PDB, aby vytvořil mapování zdrojové na nativní.</span><span class="sxs-lookup"><span data-stu-id="87f14-786">Cross-machine event tracing allows customers to profile a program on Machine A and look at the profiling data with source line mapping on Machine B. Using previous versions of the .NET Framework, the user would copy all the modules and native images from the profiled machine to the analysis machine that contains the IL PDB to create the source-to-native mapping.</span></span> <span data-ttu-id="87f14-787">I když tento proces může fungovat i v případě, že jsou soubory relativně malé, například pro telefonní aplikace, můžou být soubory velmi velké na stolních počítačích a vyžadovat delší dobu kopírování.</span><span class="sxs-lookup"><span data-stu-id="87f14-787">While this process may work well when the files are relatively small, such as for phone applications, the files can be very large on desktop systems and require significant time to copy.</span></span>

<span data-ttu-id="87f14-788">V případě Ngen soubory PDB může NGen vytvořit PDB, který obsahuje mapování IL-to-Native bez závislosti na souboru PDB IL.</span><span class="sxs-lookup"><span data-stu-id="87f14-788">With Ngen PDBs, NGen can create a PDB that contains the IL-to-native mapping without a dependency on the IL PDB.</span></span> <span data-ttu-id="87f14-789">V našem scénáři trasování událostí mezi počítači je potřeba ke zkopírování nativní bitové kopie image generované počítačem A na počítač B a k použití rozhraní [API pro přístup k rozhraní ladění](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) , aby se načetlo mapování typu source-to-Il z nativního souboru PDB na nativní.</span><span class="sxs-lookup"><span data-stu-id="87f14-789">In our cross-machine event tracing scenario, all that is needed is to copy the native image PDB that is generated by Machine A to Machine B and to use [Debug Interface Access APIs](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) to read the IL PDB's source-to-IL mapping and the native image PDB's IL-to-native mapping.</span></span> <span data-ttu-id="87f14-790">Kombinování obou mapování poskytuje mapování zdrojové na nativní.</span><span class="sxs-lookup"><span data-stu-id="87f14-790">Combining both mappings provides a source-to-native mapping.</span></span> <span data-ttu-id="87f14-791">Vzhledem k tomu, že je soubor PDB nativní image mnohem menší než všechny moduly a nativní bitové kopie, proces kopírování z počítače A na počítač B je mnohem rychlejší.</span><span class="sxs-lookup"><span data-stu-id="87f14-791">Since the native image PDB is much smaller than all the modules and native images, the process of copying from Machine A to Machine B is much faster.</span></span>

<a name="v46"></a>

## <a name="whats-new-in-net-2015"></a><span data-ttu-id="87f14-792">Co je nového v .NET 2015</span><span class="sxs-lookup"><span data-stu-id="87f14-792">What's new in .NET 2015</span></span>

<span data-ttu-id="87f14-793">.NET 2015 zavádí .NET Framework 4,6 a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="87f14-793">.NET 2015 introduces the .NET Framework 4.6 and .NET Core.</span></span> <span data-ttu-id="87f14-794">Některé nové funkce platí i pro i další funkce jsou specifické pro .NET Framework 4,6 nebo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="87f14-794">Some new features apply to both, and other features are specific to .NET Framework 4.6 or .NET Core.</span></span>

- <span data-ttu-id="87f14-795">**ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="87f14-795">**ASP.NET Core**</span></span>

  <span data-ttu-id="87f14-796">.NET 2015 zahrnuje ASP.NET Core, což je implementace štíhlé aplikace .NET pro vytváření moderních cloudových aplikací.</span><span class="sxs-lookup"><span data-stu-id="87f14-796">.NET 2015 includes ASP.NET Core, which is a lean .NET implementation for building modern cloud-based apps.</span></span> <span data-ttu-id="87f14-797">ASP.NET Core je modulární, takže můžete zahrnout jenom ty funkce, které jsou potřeba ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="87f14-797">ASP.NET Core is modular so you can include only those features that are needed in your application.</span></span> <span data-ttu-id="87f14-798">Dá se hostovat ve službě IIS nebo v místním prostředí ve vlastním procesu a můžete spouštět aplikace s různými verzemi .NET Framework na stejném serveru.</span><span class="sxs-lookup"><span data-stu-id="87f14-798">It can be hosted on IIS or self-hosted in a custom process, and you can run apps with different versions of the .NET Framework on the same server.</span></span> <span data-ttu-id="87f14-799">Obsahuje nový systém konfigurace prostředí, který je určený pro nasazení v cloudu.</span><span class="sxs-lookup"><span data-stu-id="87f14-799">It includes a new environment configuration system that is designed for cloud deployment.</span></span>

  <span data-ttu-id="87f14-800">MVC, webové rozhraní API a webové stránky jsou sjednocené do jediného rozhraní s názvem MVC 6.</span><span class="sxs-lookup"><span data-stu-id="87f14-800">MVC, Web API, and Web Pages are unified into a single framework called MVC 6.</span></span> <span data-ttu-id="87f14-801">ASP.NET Core aplikace můžete vytvářet prostřednictvím nástrojů v aplikaci Visual Studio 2015 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="87f14-801">You build ASP.NET Core apps through tools in Visual Studio 2015 or later.</span></span> <span data-ttu-id="87f14-802">Stávající aplikace budou fungovat na novém .NET Framework. Chcete-li však vytvořit aplikaci, která používá MVC 6 nebo Signal 3, je nutné použít systém projektu v aplikaci Visual Studio 2015 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="87f14-802">Your existing applications will work on the new .NET Framework; however to build an app that uses MVC 6 or SignalR 3, you must use the project system in Visual Studio 2015 or later.</span></span>

  <span data-ttu-id="87f14-803">Informace najdete v tématu [ASP.NET Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="87f14-803">For information, see [ASP.NET Core](/aspnet/core/).</span></span>

- <span data-ttu-id="87f14-804">**ASP.NET aktualizace**</span><span class="sxs-lookup"><span data-stu-id="87f14-804">**ASP.NET Updates**</span></span>

  - <span data-ttu-id="87f14-805">**Rozhraní API založené na úlohách pro vyprazdňování asynchronních odpovědí**</span><span class="sxs-lookup"><span data-stu-id="87f14-805">**Task-based API for Asynchronous Response Flushing**</span></span>

    <span data-ttu-id="87f14-806">ASP.NET nyní poskytuje jednoduché rozhraní API založené na úlohách pro vyprazdňování asynchronních odpovědí, <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=nameWithType> což umožňuje, aby odpovědi byly vyčištěny asynchronně pomocí podpory vašeho jazyka `async/await` .</span><span class="sxs-lookup"><span data-stu-id="87f14-806">ASP.NET now provides a simple task-based API for asynchronous response flushing, <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=nameWithType>, that allows responses to be flushed asynchronously by using your language's `async/await` support.</span></span>

  - <span data-ttu-id="87f14-807">**Vazba modelu podporuje metody vracející úlohy**</span><span class="sxs-lookup"><span data-stu-id="87f14-807">**Model binding supports task-returning methods**</span></span>

    <span data-ttu-id="87f14-808">V .NET Framework 4,5 přidal ASP.NET funkci vazby modelu, která povolila rozšiřitelný přístup k datům na základě kódu, na stránky webových formulářů a uživatelské ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="87f14-808">In the .NET Framework 4.5, ASP.NET added the Model Binding feature that enabled an extensible, code-focused approach to CRUD-based data operations in Web Forms pages and user controls.</span></span> <span data-ttu-id="87f14-809">Systém vazby modelu teď podporuje <xref:System.Threading.Tasks.Task> – vrací metody vazby modelu.</span><span class="sxs-lookup"><span data-stu-id="87f14-809">The Model Binding system now supports <xref:System.Threading.Tasks.Task>-returning model binding methods.</span></span> <span data-ttu-id="87f14-810">Tato funkce umožňuje vývojářům webových formulářů získat výhody škálovatelnosti v rámci asynchronního přenosu dat při použití novějších verzí systému ORMs, včetně Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="87f14-810">This feature allows Web Forms developers to get the scalability benefits of async with the ease of the data-binding system when using newer versions of ORMs, including the Entity Framework.</span></span>

    <span data-ttu-id="87f14-811">Vazba asynchronního modelu je řízena `aspnet:EnableAsyncModelBinding` nastavením konfigurace.</span><span class="sxs-lookup"><span data-stu-id="87f14-811">Async model binding is controlled by the `aspnet:EnableAsyncModelBinding` configuration setting.</span></span>

    ```xml
    <appSettings>
        <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />
    </appSettings>
    ```

    <span data-ttu-id="87f14-812">U aplikací, které cílí na .NET Framework 4,6, se nastaví jako výchozí `true` .</span><span class="sxs-lookup"><span data-stu-id="87f14-812">On apps the target the .NET Framework 4.6, it defaults to `true`.</span></span> <span data-ttu-id="87f14-813">V aplikacích běžících na .NET Framework 4,6, které cílí na starší verzi .NET Framework, je `false` ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="87f14-813">On apps running on the .NET Framework 4.6 that target an earlier version of the .NET Framework, it is `false` by default.</span></span> <span data-ttu-id="87f14-814">Dá se povolit nastavením nastavení konfigurace na `true` .</span><span class="sxs-lookup"><span data-stu-id="87f14-814">It can be enabled by setting the configuration setting to `true`.</span></span>

  - <span data-ttu-id="87f14-815">**Podpora HTTP/2 (Windows 10)**</span><span class="sxs-lookup"><span data-stu-id="87f14-815">**HTTP/2 Support (Windows 10)**</span></span>

    <span data-ttu-id="87f14-816">[Http/2](https://www.wikipedia.org/wiki/HTTP/2) je nová verze protokolu HTTP, která poskytuje mnohem lepší využití připojení (méně zpátečních cest mezi klientem a serverem). Výsledkem je načítání webových stránek s nižší latencí pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="87f14-816">[HTTP/2](https://www.wikipedia.org/wiki/HTTP/2) is a new version of the HTTP protocol that provides much better connection utilization (fewer round-trips between client and server), resulting in lower latency web page loading for users.</span></span>  <span data-ttu-id="87f14-817">Webové stránky (na rozdíl od služeb) využívají maximum HTTP/2, protože protokol je optimalizován pro více artefaktů, které jsou požadovány v rámci jednoho prostředí.</span><span class="sxs-lookup"><span data-stu-id="87f14-817">Web pages (as opposed to services) benefit the most from HTTP/2, since the protocol optimizes for multiple artifacts being requested as part of a single experience.</span></span> <span data-ttu-id="87f14-818">Do ASP.NET v .NET Framework 4,6 byla přidána podpora protokolu HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="87f14-818">HTTP/2 support has been added to ASP.NET in .NET Framework 4.6.</span></span> <span data-ttu-id="87f14-819">Vzhledem k tomu, že síťové funkce existují na více vrstvách, byly v systému Windows, ve službě IIS a v ASP.NET k dispozici nové funkce pro povolení protokolu HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="87f14-819">Because networking functionality exists at multiple layers, new features were required in Windows, in IIS, and in ASP.NET to enable HTTP/2.</span></span> <span data-ttu-id="87f14-820">Abyste mohli používat HTTP/2 s ASP.NET, musíte běžet na Windows 10.</span><span class="sxs-lookup"><span data-stu-id="87f14-820">You must be running on Windows 10 to use HTTP/2 with ASP.NET.</span></span>

    <span data-ttu-id="87f14-821">Pro aplikace Windows 10 Univerzální platforma Windows (UWP), které používají rozhraní API, se standardně podporuje i HTTP/2 <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="87f14-821">HTTP/2 is also supported and on by default for Windows 10 Universal Windows Platform (UWP) apps that use the <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> API.</span></span>

    <span data-ttu-id="87f14-822">Aby bylo možné používat funkci [PUSH_PROMISE](https://http2.github.io/http2-spec/#PUSH_PROMISE) v aplikacích ASP.NET, je nová metoda se dvěma přetíženími <xref:System.Web.HttpResponse.PushPromise%28System.String%29> a <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29> přidána do <xref:System.Web.HttpResponse> třídy.</span><span class="sxs-lookup"><span data-stu-id="87f14-822">In order to provide a way to use the [PUSH_PROMISE](https://http2.github.io/http2-spec/#PUSH_PROMISE) feature in ASP.NET applications, a new method with two overloads, <xref:System.Web.HttpResponse.PushPromise%28System.String%29> and <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29>, has been added to the <xref:System.Web.HttpResponse> class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="87f14-823">I když ASP.NET Core podporuje HTTP/2, podpora funkce PUSH Promise ještě není přidaná.</span><span class="sxs-lookup"><span data-stu-id="87f14-823">While ASP.NET Core supports HTTP/2, support for the PUSH PROMISE feature has not yet been added.</span></span>

    <span data-ttu-id="87f14-824">Prohlížeč a webový server (IIS v systému Windows) mají veškerou práci.</span><span class="sxs-lookup"><span data-stu-id="87f14-824">The browser and the web server (IIS on Windows) do all the work.</span></span> <span data-ttu-id="87f14-825">Nemusíte pro uživatele dělat těžkou zdvihání.</span><span class="sxs-lookup"><span data-stu-id="87f14-825">You don't have to do any heavy-lifting for your users.</span></span>

    <span data-ttu-id="87f14-826">Většina [hlavních prohlížečů podporuje HTTP/2](https://www.wikipedia.org/wiki/HTTP/2), takže pokud je server podporuje, bude vám vaše uživatelé moci podporu HTTP/2 využít.</span><span class="sxs-lookup"><span data-stu-id="87f14-826">Most of the [major browsers support HTTP/2](https://www.wikipedia.org/wiki/HTTP/2), so it's likely that your users will benefit from HTTP/2 support if your server supports it.</span></span>

  - <span data-ttu-id="87f14-827">**Podpora pro protokol vazby tokenů**</span><span class="sxs-lookup"><span data-stu-id="87f14-827">**Support for the Token Binding Protocol**</span></span>

    <span data-ttu-id="87f14-828">Microsoft a Google spolupracuje na novém přístupu k ověřování, který se nazývá [protokol vazby tokenů](https://github.com/TokenBinding/Internet-Drafts).</span><span class="sxs-lookup"><span data-stu-id="87f14-828">Microsoft and Google have been collaborating on a new approach to authentication, called the [Token Binding Protocol](https://github.com/TokenBinding/Internet-Drafts).</span></span> <span data-ttu-id="87f14-829">Místní je, že ověřovací tokeny (v mezipaměti prohlížeče) můžou být odcizené a používané podvodníky pro přístup k jiným zabezpečeným prostředkům (třeba k bankovnímu účtu) bez vyžadování hesla nebo jakýchkoli dalších privilegovaných znalostí.</span><span class="sxs-lookup"><span data-stu-id="87f14-829">The premise is that authentication tokens (in your browser cache) can be stolen and used by criminals to access otherwise secure resources (for example, your bank account) without requiring your password or any other privileged knowledge.</span></span> <span data-ttu-id="87f14-830">Nový protokol se zaměřuje na zmírnění tohoto problému.</span><span class="sxs-lookup"><span data-stu-id="87f14-830">The new protocol aims to mitigate this problem.</span></span>

    <span data-ttu-id="87f14-831">Protokol vazby tokenu bude v systému Windows 10 implementován jako funkce prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="87f14-831">The Token Binding Protocol will be implemented in Windows 10 as a browser feature.</span></span> <span data-ttu-id="87f14-832">Aplikace ASP.NET se budou podílet na protokolu, aby ověřovací tokeny byly ověřené jako legitimní.</span><span class="sxs-lookup"><span data-stu-id="87f14-832">ASP.NET apps will participate in the protocol, so that authentication tokens are validated to be legitimate.</span></span> <span data-ttu-id="87f14-833">Implementace klienta a serveru vytvoří kompletní ochranu určenou protokolem.</span><span class="sxs-lookup"><span data-stu-id="87f14-833">The client and the server implementations establish the end-to-end protection specified by the protocol.</span></span>

  - <span data-ttu-id="87f14-834">**Algoritmy hash s náhodným řetězcem**</span><span class="sxs-lookup"><span data-stu-id="87f14-834">**Randomized string hash algorithms**</span></span>

    <span data-ttu-id="87f14-835">.NET Framework 4,5 představil [algoritmus hash s náhodným řetězcem](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-835">.NET Framework 4.5 introduced a [randomized string hash algorithm](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).</span></span> <span data-ttu-id="87f14-836">ASP.NET ho ale nepodporuje, protože některé funkce ASP.NET jsou závislé na stabilním kódu hash.</span><span class="sxs-lookup"><span data-stu-id="87f14-836">However, it was not supported by ASP.NET because of some ASP.NET features depended on a stable hash code.</span></span> <span data-ttu-id="87f14-837">V .NET Framework 4,6 jsou nyní podporovány algoritmy hash s náhodným řetězcem.</span><span class="sxs-lookup"><span data-stu-id="87f14-837">In .NET Framework 4.6, randomized string hash algorithms are now supported.</span></span> <span data-ttu-id="87f14-838">Pokud chcete tuto funkci povolit, použijte `aspnet:UseRandomizedStringHashAlgorithm` nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="87f14-838">To enable this feature, use the `aspnet:UseRandomizedStringHashAlgorithm` config setting.</span></span>

    ```xml
    <appSettings>
        <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />
    </appSettings>
    ```

- <span data-ttu-id="87f14-839">**ADO.NET**</span><span class="sxs-lookup"><span data-stu-id="87f14-839">**ADO.NET**</span></span>

  <span data-ttu-id="87f14-840">Rozhraní ADO .NET teď podporuje funkci Always Encrypted dostupnou v SQL Server 2016 Community Technology Preview 2 (CTP2).</span><span class="sxs-lookup"><span data-stu-id="87f14-840">ADO .NET now supports the Always Encrypted feature available in SQL Server 2016 Community Technology Preview 2 (CTP2).</span></span> <span data-ttu-id="87f14-841">Pomocí Always Encrypted může SQL Server provádět operace s šifrovanými daty a nejlepší ze všech šifrovacích klíčů se nachází v rámci důvěryhodného prostředí zákazníka, nikoli na serveru.</span><span class="sxs-lookup"><span data-stu-id="87f14-841">With Always Encrypted, SQL Server can perform operations on encrypted data, and best of all the encryption key resides with the application inside the customer's trusted environment and not on the server.</span></span> <span data-ttu-id="87f14-842">Always Encrypted zabezpečuje zákaznická data, takže specializující nemají přístup k datům ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="87f14-842">Always Encrypted secures customer data so DBAs do not have access to plain text data.</span></span> <span data-ttu-id="87f14-843">Šifrování a dešifrování dat probíhá transparentně na úrovni ovladače a minimalizuje změny, které je třeba provést u existujících aplikací.</span><span class="sxs-lookup"><span data-stu-id="87f14-843">Encryption and decryption of data happens transparently at the driver level, minimizing changes that have to be made to existing applications.</span></span> <span data-ttu-id="87f14-844">Podrobnosti najdete v tématu [Always Encrypted (databázový stroj)](/sql/relational-databases/security/encryption/always-encrypted-database-engine) a [Always Encrypted (vývoj klientů)](/sql/relational-databases/security/encryption/always-encrypted-client-development).</span><span class="sxs-lookup"><span data-stu-id="87f14-844">For details, see [Always Encrypted (Database Engine)](/sql/relational-databases/security/encryption/always-encrypted-database-engine) and [Always Encrypted (client development)](/sql/relational-databases/security/encryption/always-encrypted-client-development).</span></span>

- <span data-ttu-id="87f14-845">**64 kompilátor JIT pro spravovaný kód**</span><span class="sxs-lookup"><span data-stu-id="87f14-845">**64-bit JIT Compiler for managed code**</span></span>

  <span data-ttu-id="87f14-846">.NET Framework 4,6 obsahuje novou verzi 64 kompilátoru JIT (původně kódu s názvem RyuJIT).</span><span class="sxs-lookup"><span data-stu-id="87f14-846">.NET Framework 4.6 features a new version of the 64-bit JIT compiler (originally code-named RyuJIT).</span></span> <span data-ttu-id="87f14-847">Nový 64 kompilátor poskytuje významné zlepšení výkonu oproti staršímu 64 kompilátoru JIT.</span><span class="sxs-lookup"><span data-stu-id="87f14-847">The new 64-bit compiler provides significant performance improvements over the older 64-bit JIT compiler.</span></span> <span data-ttu-id="87f14-848">Nový 64 kompilátor je povolen pro 64 procesy spuštěné nad .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="87f14-848">The new 64-bit compiler is enabled for 64-bit processes running on top of .NET Framework 4.6.</span></span> <span data-ttu-id="87f14-849">Vaše aplikace bude spuštěna v 64m procesu, pokud je kompilována jako 64-bit nebo AnyCPU a je spuštěna v operačním systému 64.</span><span class="sxs-lookup"><span data-stu-id="87f14-849">Your app will run in a 64-bit process if it is compiled as 64-bit or AnyCPU and is running on a 64-bit operating system.</span></span> <span data-ttu-id="87f14-850">I když jste se ujistili, že přechod na nový kompilátor je co možná transparentní, jsou možné změny v chování.</span><span class="sxs-lookup"><span data-stu-id="87f14-850">While care has been taken to make the transition to the new compiler as transparent as possible, changes in behavior are possible.</span></span>

  <span data-ttu-id="87f14-851">Nový 64 kompilátor JIT zahrnuje také funkce akcelerace hardwarového SIMDu v případě, že se v oboru názvů společně s typy SIMD podporují <xref:System.Numerics> , což může přinést dobré zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="87f14-851">The new 64-bit JIT compiler also includes hardware SIMD acceleration features when coupled with SIMD-enabled types in the <xref:System.Numerics> namespace, which can yield good performance improvements.</span></span>

- <span data-ttu-id="87f14-852">**Vylepšení zavaděče sestavení**</span><span class="sxs-lookup"><span data-stu-id="87f14-852">**Assembly loader improvements**</span></span>

  <span data-ttu-id="87f14-853">Zavaděč sestavení nyní používá paměť efektivněji uvolněním sestavení IL po načtení odpovídající image NGEN.</span><span class="sxs-lookup"><span data-stu-id="87f14-853">The assembly loader now uses memory more efficiently by unloading IL assemblies after a corresponding NGEN image is loaded.</span></span> <span data-ttu-id="87f14-854">Tato změna snižuje virtuální paměť, což je zvláště užitečné pro velké 32ové aplikace (jako je například Visual Studio), a také šetří fyzickou paměť.</span><span class="sxs-lookup"><span data-stu-id="87f14-854">This change decreases virtual memory, which is particularly beneficial for large 32-bit apps (such as Visual Studio), and also saves physical memory.</span></span>

- <span data-ttu-id="87f14-855">**Změny knihovny základních tříd**</span><span class="sxs-lookup"><span data-stu-id="87f14-855">**Base class library changes**</span></span>

  <span data-ttu-id="87f14-856">K .NET Framework 4,6 bylo přidáno mnoho nových rozhraní API, které umožňuje použití klíčových scénářů.</span><span class="sxs-lookup"><span data-stu-id="87f14-856">Many new APIs have been added around to .NET Framework 4.6 to enable key scenarios.</span></span> <span data-ttu-id="87f14-857">Mezi ně patří tyto změny a dodatky:</span><span class="sxs-lookup"><span data-stu-id="87f14-857">These include the following changes and additions:</span></span>

  - <span data-ttu-id="87f14-858">**\<T>Implementace IReadOnlyCollection**</span><span class="sxs-lookup"><span data-stu-id="87f14-858">**IReadOnlyCollection\<T> implementations**</span></span>

    <span data-ttu-id="87f14-859">Další kolekce implementují <xref:System.Collections.Generic.IReadOnlyCollection%601> například <xref:System.Collections.Generic.Queue%601> a <xref:System.Collections.Generic.Stack%601> .</span><span class="sxs-lookup"><span data-stu-id="87f14-859">Additional collections implement <xref:System.Collections.Generic.IReadOnlyCollection%601> such as <xref:System.Collections.Generic.Queue%601> and <xref:System.Collections.Generic.Stack%601>.</span></span>

  - <span data-ttu-id="87f14-860">**CultureInfo. CurrentCulture a CultureInfo. CurrentUICulture**</span><span class="sxs-lookup"><span data-stu-id="87f14-860">**CultureInfo.CurrentCulture and CultureInfo.CurrentUICulture**</span></span>

    <span data-ttu-id="87f14-861"><xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>Vlastnosti a <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> jsou nyní určeny pro čtení i zápis, nikoli jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="87f14-861">The <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> properties are now read-write rather than read-only.</span></span> <span data-ttu-id="87f14-862">Pokud <xref:System.Globalization.CultureInfo> k těmto vlastnostem přiřadíte nový objekt, změní se také aktuální jazyková verze vlákna definovaná `Thread.CurrentThread.CurrentCulture` vlastností a aktuální jazyková verze vlákna uživatelského rozhraní definovaná `Thread.CurrentThread.CurrentUICulture` vlastnostmi.</span><span class="sxs-lookup"><span data-stu-id="87f14-862">If you assign a new <xref:System.Globalization.CultureInfo> object to these properties, the current thread culture defined by the `Thread.CurrentThread.CurrentCulture` property and the current UI thread culture defined by the `Thread.CurrentThread.CurrentUICulture` properties also change.</span></span>

  - <span data-ttu-id="87f14-863">**Vylepšení uvolňování paměti (GC)**</span><span class="sxs-lookup"><span data-stu-id="87f14-863">**Enhancements to garbage collection (GC)**</span></span>

    <span data-ttu-id="87f14-864"><xref:System.GC>Třída teď obsahuje <xref:System.GC.TryStartNoGCRegion%2A> metody a <xref:System.GC.EndNoGCRegion%2A> , které umožňují zakázat uvolňování paměti během provádění kritické cesty.</span><span class="sxs-lookup"><span data-stu-id="87f14-864">The <xref:System.GC> class now includes <xref:System.GC.TryStartNoGCRegion%2A> and <xref:System.GC.EndNoGCRegion%2A> methods that allow you to disallow garbage collection during the execution of a critical path.</span></span>

    <span data-ttu-id="87f14-865">Nové přetížení <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType> metody umožňuje řídit, zda je halda malých objektů i halda pro velké objekty Swept a komprimována nebo Swept pouze.</span><span class="sxs-lookup"><span data-stu-id="87f14-865">A new overload of the <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType> method allows you to control whether both the small object heap and the large object heap are swept and compacted or swept only.</span></span>

  - <span data-ttu-id="87f14-866">**Typy s povoleným SIMD**</span><span class="sxs-lookup"><span data-stu-id="87f14-866">**SIMD-enabled types**</span></span>

    <span data-ttu-id="87f14-867"><xref:System.Numerics>Obor názvů teď obsahuje několik typů s povoleným SIMD, jako <xref:System.Numerics.Matrix3x2> jsou, <xref:System.Numerics.Matrix4x4> ,, <xref:System.Numerics.Plane> <xref:System.Numerics.Quaternion> , <xref:System.Numerics.Vector2> , <xref:System.Numerics.Vector3> a <xref:System.Numerics.Vector4> .</span><span class="sxs-lookup"><span data-stu-id="87f14-867">The <xref:System.Numerics> namespace now includes a number of SIMD-enabled types, such as <xref:System.Numerics.Matrix3x2>, <xref:System.Numerics.Matrix4x4>, <xref:System.Numerics.Plane>, <xref:System.Numerics.Quaternion>, <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, and <xref:System.Numerics.Vector4>.</span></span>

    <span data-ttu-id="87f14-868">Vzhledem k tomu, že nový 64 kompilátor JIT zahrnuje také funkce akcelerace hardwarového SIMD, existují obzvláště významná zlepšení výkonu při použití typů SIMD s novým 64 kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="87f14-868">Because the new 64-bit JIT compiler also includes hardware SIMD acceleration features, there are especially significant performance improvements when using the SIMD-enabled types with the new 64-bit JIT compiler.</span></span>

  - <span data-ttu-id="87f14-869">**Aktualizace kryptografie**</span><span class="sxs-lookup"><span data-stu-id="87f14-869">**Cryptography updates**</span></span>

    <span data-ttu-id="87f14-870"><xref:System.Security.Cryptography?displayProperty=nameWithType>Rozhraní API se aktualizuje tak, aby podporovalo [rozhraní API kryptografie Windows CNG](/windows/desktop/SecCNG/cng-reference).</span><span class="sxs-lookup"><span data-stu-id="87f14-870">The <xref:System.Security.Cryptography?displayProperty=nameWithType> API is being updated to support the [Windows CNG cryptography APIs](/windows/desktop/SecCNG/cng-reference).</span></span> <span data-ttu-id="87f14-871">Předchozí verze .NET Framework se jako základ pro implementaci spoléhaly jenom na [starší verzi rozhraní API kryptografie Windows](/windows/desktop/SecCrypto/cryptography-portal) <xref:System.Security.Cryptography?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="87f14-871">Previous versions of the .NET Framework have relied entirely on an [earlier version of the Windows Cryptography APIs](/windows/desktop/SecCrypto/cryptography-portal) as the basis for the <xref:System.Security.Cryptography?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="87f14-872">Měli jsme požadavky na podporu rozhraní API CNG, protože podporuje [moderní kryptografické algoritmy](/windows/desktop/SecCNG/cng-features#suite-b-support), které jsou důležité pro určité kategorie aplikací.</span><span class="sxs-lookup"><span data-stu-id="87f14-872">We have had requests to support the CNG API, since it supports [modern cryptography algorithms](/windows/desktop/SecCNG/cng-features#suite-b-support), which are important for certain categories of apps.</span></span>

    <span data-ttu-id="87f14-873">.NET Framework 4,6 obsahuje následující nová vylepšení pro podporu kryptografických rozhraní API Windows CNG:</span><span class="sxs-lookup"><span data-stu-id="87f14-873">.NET Framework 4.6 includes the following new enhancements to support the Windows CNG cryptography APIs:</span></span>

    - <span data-ttu-id="87f14-874">Sada rozšiřujících metod pro certifikáty x509 `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` a `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` , která vrací implementaci založenou na CNG spíše než implementaci založenou na rozhraní CAPI, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="87f14-874">A set of extension methods for X509 Certificates, `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` and `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`, that return a CNG-based implementation rather than a CAPI-based implementation when possible.</span></span> <span data-ttu-id="87f14-875">(Některé čipové karty atd., stále vyžadují rozhraní CAPI a rozhraní API zařídí záložní verze.)</span><span class="sxs-lookup"><span data-stu-id="87f14-875">(Some smartcards, etc., still require CAPI, and the APIs handle the fallback).</span></span>

    - <span data-ttu-id="87f14-876"><xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType>Třída, která poskytuje implementaci CNG algoritmu RSA.</span><span class="sxs-lookup"><span data-stu-id="87f14-876">The <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> class, which provides a CNG implementation of the RSA algorithm.</span></span>

    - <span data-ttu-id="87f14-877">Vylepšení rozhraní RSA API tak, aby běžné akce již nevyžadovaly přetypování.</span><span class="sxs-lookup"><span data-stu-id="87f14-877">Enhancements to the RSA API so that common actions no longer require casting.</span></span> <span data-ttu-id="87f14-878">Například šifrování dat pomocí <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> objektu vyžaduje v předchozích verzích .NET Framework kód jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="87f14-878">For example, encrypting data using an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> object requires code like the following in previous versions of the .NET Framework.</span></span>

      [!code-csharp[WhatsNew.Casting#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#1)]
      [!code-vb[WhatsNew.Casting#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#1)]

      <span data-ttu-id="87f14-879">Kód, který používá nová rozhraní API kryptografie v .NET Framework 4,6, lze přepsat následujícím způsobem, aby se zabránilo přetypování.</span><span class="sxs-lookup"><span data-stu-id="87f14-879">Code that uses the new cryptography APIs in .NET Framework 4.6 can be rewritten as follows to avoid the cast.</span></span>

      [!code-csharp[WhatsNew.Casting#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#2)]
      [!code-vb[WhatsNew.Casting#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#2)]

  - <span data-ttu-id="87f14-880">**Podpora převodu dat a časů do nebo z času v systému UNIX**</span><span class="sxs-lookup"><span data-stu-id="87f14-880">**Support for converting dates and times to or from Unix time**</span></span>

    <span data-ttu-id="87f14-881">Do struktury byly přidány následující nové metody <xref:System.DateTimeOffset> , které podporují převod hodnot data a času na čas systému UNIX nebo z něj:</span><span class="sxs-lookup"><span data-stu-id="87f14-881">The following new methods have been added to the <xref:System.DateTimeOffset> structure to support converting date and time values to or from Unix time:</span></span>

    - <xref:System.DateTimeOffset.FromUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.FromUnixTimeMilliseconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeMilliseconds%2A?displayProperty=nameWithType>

  - <span data-ttu-id="87f14-882">**Přepínače kompatibility**</span><span class="sxs-lookup"><span data-stu-id="87f14-882">**Compatibility switches**</span></span>

    <span data-ttu-id="87f14-883"><xref:System.AppContext>Třída přidává novou funkci kompatibility, která umožňuje zapisovačům knihoven poskytnout jednotný mechanismus pro odhlášení pro nové funkce pro své uživatele.</span><span class="sxs-lookup"><span data-stu-id="87f14-883">The <xref:System.AppContext> class adds a new compatibility feature that enables library writers to provide a uniform opt-out mechanism for new functionality for their users.</span></span> <span data-ttu-id="87f14-884">Zřizuje volně spojený kontrakt mezi komponentami, aby bylo možné sdělit požadavek na výslovný souhlas.</span><span class="sxs-lookup"><span data-stu-id="87f14-884">It establishes a loosely coupled contract between components in order to communicate an opt-out request.</span></span> <span data-ttu-id="87f14-885">Tato možnost je obvykle důležitá, když dojde ke změně existující funkce.</span><span class="sxs-lookup"><span data-stu-id="87f14-885">This capability is typically important when a change is made to existing functionality.</span></span> <span data-ttu-id="87f14-886">Naopak pro nové funkce už existuje implicitní výslovný souhlas.</span><span class="sxs-lookup"><span data-stu-id="87f14-886">Conversely, there is already an implicit opt-in for new functionality.</span></span>

    <span data-ttu-id="87f14-887">S <xref:System.AppContext> , knihovny definují a zveřejňují přepínače kompatibility, zatímco kód, který na nich závisí, může nastavit tyto přepínače tak, aby ovlivnily chování knihovny.</span><span class="sxs-lookup"><span data-stu-id="87f14-887">With <xref:System.AppContext>, libraries define and expose compatibility switches, while code that depends on them can set those switches to affect the library behavior.</span></span> <span data-ttu-id="87f14-888">Ve výchozím nastavení knihovny poskytují nové funkce a mění je pouze (to znamená, že poskytují předchozí funkce), pokud je přepínač nastaven.</span><span class="sxs-lookup"><span data-stu-id="87f14-888">By default, libraries provide the new functionality, and they only alter it (that is, they provide the previous functionality) if the switch is set.</span></span>

    <span data-ttu-id="87f14-889">Aplikace (nebo knihovna) může deklarovat hodnotu přepínače (což je vždy <xref:System.Boolean> hodnota), kterou definuje závislá knihovna.</span><span class="sxs-lookup"><span data-stu-id="87f14-889">An application (or a library) can declare the value of a switch (which is always a <xref:System.Boolean> value) that a dependent library defines.</span></span> <span data-ttu-id="87f14-890">Přepínač je vždy implicitně `false` .</span><span class="sxs-lookup"><span data-stu-id="87f14-890">The switch is always implicitly `false`.</span></span> <span data-ttu-id="87f14-891">Nastavením přepínače `true` ho povolíte.</span><span class="sxs-lookup"><span data-stu-id="87f14-891">Setting the switch to `true` enables it.</span></span> <span data-ttu-id="87f14-892">Explicitním nastavením přepínače, aby bylo `false` zajištěno nové chování.</span><span class="sxs-lookup"><span data-stu-id="87f14-892">Explicitly setting the switch to `false` provides the new behavior.</span></span>

    ```csharp
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);
    ```

    ```vb
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", True)
    ```

    <span data-ttu-id="87f14-893">Knihovna musí ověřit, zda příjemce deklaroval hodnotu přepínače a následně na něj musí reagovat.</span><span class="sxs-lookup"><span data-stu-id="87f14-893">The library must check if a consumer has declared the value of the switch and then appropriately act on it.</span></span>

    ```csharp
    if (!AppContext.TryGetSwitch("Switch.AmazingLib.ThrowOnException", out shouldThrow))
    {
        // This is the case where the switch value was not set by the application.
        // The library can choose to get the value of shouldThrow by other means.
        // If no overrides nor default values are specified, the value should be 'false'.
        // A false value implies the latest behavior.
    }

    // The library can use the value of shouldThrow to throw exceptions or not.
    if (shouldThrow)
    {
        // old code
    }
    else
    {
        // new code
    }
    ```

    ```vb
    If Not AppContext.TryGetSwitch("Switch.AmazingLib.ThrowOnException", shouldThrow) Then
        ' This is the case where the switch value was not set by the application.
        ' The library can choose to get the value of shouldThrow by other means.
        ' If no overrides nor default values are specified, the value should be 'false'.
        ' A false value implies the latest behavior.
    End If

    ' The library can use the value of shouldThrow to throw exceptions or not.
    If shouldThrow Then
        ' old code
    Else
        ' new code
    End If
    ```

    <span data-ttu-id="87f14-894">Je výhodné použít pro přepínače konzistentní formát, protože se jedná o formální kontrakt, který je zpřístupněný knihovnou.</span><span class="sxs-lookup"><span data-stu-id="87f14-894">It's beneficial to use a consistent format for switches, since they are a formal contract exposed by a library.</span></span> <span data-ttu-id="87f14-895">Níže jsou uvedené dva zjevné formáty.</span><span class="sxs-lookup"><span data-stu-id="87f14-895">The following are two obvious formats.</span></span>

    - <span data-ttu-id="87f14-896">*Přepínač*. *obor názvů*. *přepínač*</span><span class="sxs-lookup"><span data-stu-id="87f14-896">*Switch*.*namespace*.*switchname*</span></span>

    - <span data-ttu-id="87f14-897">*Přepínač*. *Knihovna*. *přepínač*</span><span class="sxs-lookup"><span data-stu-id="87f14-897">*Switch*.*library*.*switchname*</span></span>

  - <span data-ttu-id="87f14-898">**Změny asynchronního vzoru založeného na úlohách (klepnutím)**</span><span class="sxs-lookup"><span data-stu-id="87f14-898">**Changes to the task-based asynchronous pattern (TAP)**</span></span>

    <span data-ttu-id="87f14-899">Pro aplikace, které cílí na .NET Framework 4,6, <xref:System.Threading.Tasks.Task> a objekty dědí jazykovou verzi <xref:System.Threading.Tasks.Task%601> a jazykovou verzi uživatelského rozhraní volajícího vlákna.</span><span class="sxs-lookup"><span data-stu-id="87f14-899">For apps that target the .NET Framework 4.6, <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects inherit the culture and UI culture of the calling thread.</span></span> <span data-ttu-id="87f14-900">Chování aplikací, které cílí na předchozí verze .NET Framework nebo které necílí na konkrétní verzi .NET Framework, není ovlivněno.</span><span class="sxs-lookup"><span data-stu-id="87f14-900">The behavior of apps that target previous versions of the .NET Framework, or that do not target a specific version of the .NET Framework, is unaffected.</span></span> <span data-ttu-id="87f14-901">Další informace naleznete v části "jazyková verze a asynchronní operace založené na úlohách" v <xref:System.Globalization.CultureInfo> tématu třídy.</span><span class="sxs-lookup"><span data-stu-id="87f14-901">For more information, see the "Culture and task-based asynchronous operations" section of the <xref:System.Globalization.CultureInfo> class topic.</span></span>

    <span data-ttu-id="87f14-902"><xref:System.Threading.AsyncLocal%601?displayProperty=nameWithType>Třída umožňuje znázornit ambientní data, která jsou lokální pro daný tok asynchronního řízení, jako je například `async` metoda.</span><span class="sxs-lookup"><span data-stu-id="87f14-902">The <xref:System.Threading.AsyncLocal%601?displayProperty=nameWithType> class allows you to represent ambient data that is local to a given asynchronous control flow, such as an `async` method.</span></span> <span data-ttu-id="87f14-903">Dá se použít k uchovávání dat napříč vlákny.</span><span class="sxs-lookup"><span data-stu-id="87f14-903">It can be used to persist data across threads.</span></span> <span data-ttu-id="87f14-904">Můžete také definovat metodu zpětného volání, která je upozorněna vždy, když se změní okolní data buď z důvodu <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=nameWithType> explicitního Změna vlastnosti, nebo protože vlákno zaznamenalo kontextový přechod.</span><span class="sxs-lookup"><span data-stu-id="87f14-904">You can also define a callback method that is notified whenever the ambient data changes either because the <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=nameWithType> property was explicitly changed, or because the thread encountered a context transition.</span></span>

    <span data-ttu-id="87f14-905"><xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=nameWithType> Do asynchronního vzoru založeného na úlohách (klepnutím) byly přidány tři praktické metody,, a, které budou vracet dokončené úkoly v určitém stavu.</span><span class="sxs-lookup"><span data-stu-id="87f14-905">Three convenience methods, <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=nameWithType>, have been added to the task-based asynchronous pattern (TAP) to return completed tasks in a particular state.</span></span>

    <span data-ttu-id="87f14-906"><xref:System.IO.Pipes.NamedPipeClientStream>Třída teď podporuje asynchronní komunikaci s jejím novým <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A> .</span><span class="sxs-lookup"><span data-stu-id="87f14-906">The <xref:System.IO.Pipes.NamedPipeClientStream> class now supports asynchronous communication with its new <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A>.</span></span> <span data-ttu-id="87f14-907">Metoda.</span><span class="sxs-lookup"><span data-stu-id="87f14-907">method.</span></span>

  - <span data-ttu-id="87f14-908">**EventSource teď podporuje zápis do protokolu událostí.**</span><span class="sxs-lookup"><span data-stu-id="87f14-908">**EventSource now supports writing to the Event log**</span></span>

    <span data-ttu-id="87f14-909">Nyní můžete použít <xref:System.Diagnostics.Tracing.EventSource> třídu k protokolování administrativních a provozních zpráv do protokolu událostí, a to i na všechny existující relace ETW, které byly vytvořeny v počítači.</span><span class="sxs-lookup"><span data-stu-id="87f14-909">You now can use the <xref:System.Diagnostics.Tracing.EventSource> class to log administrative or operational messages to the event log, in addition to any existing ETW sessions created on the machine.</span></span> <span data-ttu-id="87f14-910">V minulosti jste pro tuto funkci museli použít balíček NuGet Microsoft. Diagnostics. Tracing. EventSource.</span><span class="sxs-lookup"><span data-stu-id="87f14-910">In the past, you had to use the Microsoft.Diagnostics.Tracing.EventSource NuGet package for this functionality.</span></span> <span data-ttu-id="87f14-911">Tato funkce je teď integrovaná .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="87f14-911">This functionality is now built-into .NET Framework 4.6.</span></span>

    <span data-ttu-id="87f14-912">Balíček NuGet i .NET Framework 4,6 byly aktualizovány pomocí následujících funkcí:</span><span class="sxs-lookup"><span data-stu-id="87f14-912">Both the NuGet package and .NET Framework 4.6 have been updated with the following features:</span></span>

    - <span data-ttu-id="87f14-913">**Dynamické události**</span><span class="sxs-lookup"><span data-stu-id="87f14-913">**Dynamic events**</span></span>

      <span data-ttu-id="87f14-914">Povoluje události definované "průběžně" bez vytváření metod událostí.</span><span class="sxs-lookup"><span data-stu-id="87f14-914">Allows events defined "on the fly" without creating event methods.</span></span>

    - <span data-ttu-id="87f14-915">**Bohatá datová část**</span><span class="sxs-lookup"><span data-stu-id="87f14-915">**Rich payloads**</span></span>

      <span data-ttu-id="87f14-916">Povoluje jako datovou část speciálně definované třídy a pole a také primitivní typy, které mají být předány.</span><span class="sxs-lookup"><span data-stu-id="87f14-916">Allows specially attributed classes and arrays as well as primitive types to be passed as a payload</span></span>

    - <span data-ttu-id="87f14-917">**Sledování aktivit**</span><span class="sxs-lookup"><span data-stu-id="87f14-917">**Activity tracking**</span></span>

      <span data-ttu-id="87f14-918">Způsobí, že události spuštění a zastavení mezi nimi budou označovat události s ID, které představuje všechny aktuálně aktivní aktivity.</span><span class="sxs-lookup"><span data-stu-id="87f14-918">Causes Start and Stop events to tag events between them with an ID that represents all currently active activities.</span></span>

    <span data-ttu-id="87f14-919">Pro podporu těchto funkcí byla přetížená <xref:System.Diagnostics.Tracing.EventSource.Write%2A> Metoda přidána do <xref:System.Diagnostics.Tracing.EventSource> třídy.</span><span class="sxs-lookup"><span data-stu-id="87f14-919">To support these features, the overloaded <xref:System.Diagnostics.Tracing.EventSource.Write%2A> method has been added to the <xref:System.Diagnostics.Tracing.EventSource> class.</span></span>

- <span data-ttu-id="87f14-920">**Windows Presentation Foundation (WPF)**</span><span class="sxs-lookup"><span data-stu-id="87f14-920">**Windows Presentation Foundation (WPF)**</span></span>

  - <span data-ttu-id="87f14-921">**Vylepšení HDPI**</span><span class="sxs-lookup"><span data-stu-id="87f14-921">**HDPI improvements**</span></span>

    <span data-ttu-id="87f14-922">Podpora HDPI v subsystému WPF je teď v .NET Framework 4,6 lepší.</span><span class="sxs-lookup"><span data-stu-id="87f14-922">HDPI support in WPF is now better in the .NET Framework 4.6.</span></span> <span data-ttu-id="87f14-923">Byly provedeny změny rozložení při zaokrouhlování, aby se snížily instance oříznutí v ovládacích prvcích s ohraničením.</span><span class="sxs-lookup"><span data-stu-id="87f14-923">Changes have been made to layout rounding to reduce instances of clipping in controls with borders.</span></span> <span data-ttu-id="87f14-924">Ve výchozím nastavení je tato funkce povolená, jenom když <xref:System.Runtime.Versioning.TargetFrameworkAttribute> je nastavená na .net 4,6.</span><span class="sxs-lookup"><span data-stu-id="87f14-924">By default, this feature is enabled only if your <xref:System.Runtime.Versioning.TargetFrameworkAttribute> is set to .NET 4.6.</span></span>  <span data-ttu-id="87f14-925">Aplikace, které jsou cíleny na starší verze rozhraní, ale jsou spuštěny v .NET Framework 4,6 se mohou přihlásit k novému chování přidáním následujícího řádku do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) části app.config souboru:</span><span class="sxs-lookup"><span data-stu-id="87f14-925">Applications that target earlier versions of the framework but are running on the .NET Framework 4.6 can opt in to the new behavior by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app.config file:</span></span>

    ```xml
    <AppContextSwitchOverrides
    value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"
    />
    ```

    <span data-ttu-id="87f14-926">WPF Windows přecházející z více monitorů s různými nastaveními DPI (nastavení s více DPI) se teď kompletně vykreslují bez černých oblastí.</span><span class="sxs-lookup"><span data-stu-id="87f14-926">WPF windows straddling multiple monitors with different DPI settings (Multi-DPI setup) are now completely rendered without blacked-out regions.</span></span> <span data-ttu-id="87f14-927">Toto chování můžete odhlásit přidáním následujícího řádku do `<appSettings>` části souboru app.config, abyste zakázali toto nové chování:</span><span class="sxs-lookup"><span data-stu-id="87f14-927">You can opt out of this behavior by adding the following line to the `<appSettings>` section of the app.config file to disable this new behavior:</span></span>

    ```xml
    <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    ```

    <span data-ttu-id="87f14-928">Do se přidala podpora pro automatické načtení správného kurzoru na základě nastavení DPI <xref:System.Windows.Input.Cursor?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="87f14-928">Support for automatically loading the right cursor based on DPI setting has been added to  <xref:System.Windows.Input.Cursor?displayProperty=nameWithType>.</span></span>

  - <span data-ttu-id="87f14-929">**Dotykové ovládání je lepší**</span><span class="sxs-lookup"><span data-stu-id="87f14-929">**Touch is better**</span></span>

    <span data-ttu-id="87f14-930">Zákaznické zprávy o [připojení](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) tohoto dotykového ovládání vytvářejí nepředvídatelné chování, které se řeší v .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="87f14-930">Customer reports on [Connect](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) that touch produces unpredictable behavior have been addressed in the .NET Framework 4.6.</span></span> <span data-ttu-id="87f14-931">Prahová hodnota dvojitého kliknutí pro aplikace pro Windows Store a aplikace WPF je teď stejná jako u Windows 8.1 a vyšších.</span><span class="sxs-lookup"><span data-stu-id="87f14-931">The double tap threshold for Windows Store applications and WPF applications is now the same in Windows 8.1 and above.</span></span>

  - <span data-ttu-id="87f14-932">**Podpora transparentního podřízeného okna**</span><span class="sxs-lookup"><span data-stu-id="87f14-932">**Transparent child window support**</span></span>

    <span data-ttu-id="87f14-933">WPF v .NET Framework 4,6 podporuje transparentní podřízená okna v Windows 8.1 a vyšším.</span><span class="sxs-lookup"><span data-stu-id="87f14-933">WPF in the .NET Framework 4.6 supports transparent child windows in Windows 8.1 and above.</span></span> <span data-ttu-id="87f14-934">To umožňuje vytvořit v oknech nejvyšší úrovně neobdélníkové a průhledné podřízené okna.</span><span class="sxs-lookup"><span data-stu-id="87f14-934">This allows you to create non-rectangular and transparent child windows in your top-level windows.</span></span> <span data-ttu-id="87f14-935">Tuto funkci můžete povolit nastavením <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=nameWithType> vlastnosti na `true` .</span><span class="sxs-lookup"><span data-stu-id="87f14-935">You can enable this feature by setting the <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=nameWithType> property to `true`.</span></span>

- <span data-ttu-id="87f14-936">**Windows Communication Foundation (WCF)**</span><span class="sxs-lookup"><span data-stu-id="87f14-936">**Windows Communication Foundation (WCF)**</span></span>

  - <span data-ttu-id="87f14-937">**Podpora SSL**</span><span class="sxs-lookup"><span data-stu-id="87f14-937">**SSL support**</span></span>

    <span data-ttu-id="87f14-938">Služba WCF teď podporuje protokol SSL verze TLS 1,1 a TLS 1,2 kromě protokolu SSL 3,0 a TLS 1,0 při použití NetTcp s zabezpečením přenosu a ověřováním klientů.</span><span class="sxs-lookup"><span data-stu-id="87f14-938">WCF now supports SSL version TLS 1.1 and TLS 1.2, in addition to SSL 3.0 and TLS 1.0, when using NetTcp with transport security and client authentication.</span></span> <span data-ttu-id="87f14-939">Nyní je možné vybrat, který protokol se má použít, nebo zakázat staré méně zabezpečené protokoly.</span><span class="sxs-lookup"><span data-stu-id="87f14-939">It is now possible to select which protocol to use, or to disable old lesser secure protocols.</span></span> <span data-ttu-id="87f14-940">To lze provést buď nastavením <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> vlastnosti, nebo přidáním následujícího do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="87f14-940">This can be done either by setting the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> property or by adding the following to a configuration file.</span></span>

    ```xml
    <netTcpBinding>
        <binding>
          <security mode= "None|Transport|Message|TransportWithMessageCredential" >
              <transport clientCredentialType="None|Windows|Certificate"
                        protectionLevel="None|Sign|EncryptAndSign"
                        sslProtocols="Ssl3|Tls1|Tls11|Tls12">
                </transport>
          </security>
        </binding>
    </netTcpBinding>
    ```

  - <span data-ttu-id="87f14-941">**Posílání zpráv pomocí různých připojení HTTP**</span><span class="sxs-lookup"><span data-stu-id="87f14-941">**Sending messages using different HTTP connections**</span></span>

    <span data-ttu-id="87f14-942">WCF teď umožňuje uživatelům zajistit, aby se určité zprávy odesílaly pomocí různých základních připojení HTTP.</span><span class="sxs-lookup"><span data-stu-id="87f14-942">WCF now allows users to ensure certain messages are sent using different underlying HTTP connections.</span></span> <span data-ttu-id="87f14-943">Toto lze provést dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="87f14-943">There are two ways to do this:</span></span>

    - <span data-ttu-id="87f14-944">**Použití předpony názvu skupiny připojení**</span><span class="sxs-lookup"><span data-stu-id="87f14-944">**Using a connection group name prefix**</span></span>

      <span data-ttu-id="87f14-945">Uživatelé můžou zadat řetězec, který bude WCF používat jako předponu pro název skupiny připojení.</span><span class="sxs-lookup"><span data-stu-id="87f14-945">Users can specify a string that WCF will use as a prefix for the connection group name.</span></span> <span data-ttu-id="87f14-946">Dvě zprávy s různými předponami jsou odesílány pomocí různých základních připojení HTTP.</span><span class="sxs-lookup"><span data-stu-id="87f14-946">Two messages with different prefixes are sent using different underlying HTTP connections.</span></span> <span data-ttu-id="87f14-947">Předponu můžete nastavit přidáním páru klíč-hodnota k <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=nameWithType> vlastnosti zprávy.</span><span class="sxs-lookup"><span data-stu-id="87f14-947">You set the prefix by adding a key/value pair to the message's <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="87f14-948">Klíč je "HttpTransportConnectionGroupNamePrefix"; hodnota je požadovaná předpona.</span><span class="sxs-lookup"><span data-stu-id="87f14-948">The key is "HttpTransportConnectionGroupNamePrefix"; the value is the desired prefix.</span></span>

    - <span data-ttu-id="87f14-949">**Používání různých továrn kanálů**</span><span class="sxs-lookup"><span data-stu-id="87f14-949">**Using different channel factories**</span></span>

      <span data-ttu-id="87f14-950">Uživatelé taky můžou povolit funkci, která zajistí, že se zprávy odeslané pomocí kanálů vytvořených různými továrnami kanálů budou používat v různých podkladových připojeních HTTP.</span><span class="sxs-lookup"><span data-stu-id="87f14-950">Users can also enable a feature that ensures that messages sent using channels created by different channel factories will use different underlying HTTP connections.</span></span> <span data-ttu-id="87f14-951">Chcete-li povolit tuto funkci, musí uživatelé nastavit `appSetting` následující `true` :</span><span class="sxs-lookup"><span data-stu-id="87f14-951">To enable this feature, users must set the following `appSetting` to `true`:</span></span>

      ```xml
      <appSettings>
          <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />
      </appSettings>
      ```

- <span data-ttu-id="87f14-952">**Programovací model Windows Workflow Foundation (WWF)**</span><span class="sxs-lookup"><span data-stu-id="87f14-952">**Windows Workflow Foundation (WWF)**</span></span>

  <span data-ttu-id="87f14-953">Nyní můžete zadat počet sekund, po které bude služba pracovního postupu pojmout požadavek na operaci mimo pořadí, pokud před vypršením časového limitu žádosti existuje nevyřízená záložka bez protokolu.</span><span class="sxs-lookup"><span data-stu-id="87f14-953">You can now specify the number of seconds a workflow service will hold on to an out-of-order operation request when there is an outstanding "non-protocol" bookmark before timing out the request.</span></span> <span data-ttu-id="87f14-954">Záložka "non-Protocol" je záložka, která nesouvisí s nezpracovanými aktivitami příjmu.</span><span class="sxs-lookup"><span data-stu-id="87f14-954">A "non-protocol" bookmark is a bookmark that is not related to outstanding Receive activities.</span></span> <span data-ttu-id="87f14-955">Některé aktivity vytvářejí záložky bez protokolu v rámci jejich implementace, takže nemusí být zřejmé, že existuje záložka bez protokolu.</span><span class="sxs-lookup"><span data-stu-id="87f14-955">Some activities create non-protocol bookmarks within their implementation, so it may not be obvious that a non-protocol bookmark exists.</span></span> <span data-ttu-id="87f14-956">Mezi ně patří stav a výběr.</span><span class="sxs-lookup"><span data-stu-id="87f14-956">These include State and Pick.</span></span> <span data-ttu-id="87f14-957">Takže pokud máte službu pracovního postupu implementovanou se stavovým počítačem nebo obsahuje aktivitu vyskladnění, pravděpodobně budete mít záložky bez protokolu.</span><span class="sxs-lookup"><span data-stu-id="87f14-957">So if you have a workflow service implemented with a state machine or containing a Pick activity, you will most likely have non-protocol bookmarks.</span></span> <span data-ttu-id="87f14-958">Interval zadejte tak, že do části souboru app.config přidáte řádek podobný následujícímu `appSettings` :</span><span class="sxs-lookup"><span data-stu-id="87f14-958">You specify the interval by adding a line like the following to the `appSettings` section of your app.config file:</span></span>

  ```xml
  <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>
  ```

  <span data-ttu-id="87f14-959">Výchozí hodnota je 60 sekund.</span><span class="sxs-lookup"><span data-stu-id="87f14-959">The default value is 60 seconds.</span></span> <span data-ttu-id="87f14-960">Pokud `value` je hodnota nastavena na 0, žádosti mimo pořadí jsou okamžitě odmítnuty s chybou text, který vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="87f14-960">If `value` is set to 0, out-of-order requests are immediately rejected with a fault with text that looks like this:</span></span>

  ```console
  Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees.
  ```

  <span data-ttu-id="87f14-961">Jedná se o stejnou zprávu, kterou dostanete, pokud je přijata zpráva o operacích mimo pořadí a nejsou k dispozici žádné záložky bez protokolu.</span><span class="sxs-lookup"><span data-stu-id="87f14-961">This is the same message that you receive if an out-of-order operation message is received and there are no non-protocol bookmarks.</span></span>

  <span data-ttu-id="87f14-962">Pokud hodnota `FilterResumeTimeoutInSeconds` elementu je nenulová, neexistují žádné záložky bez protokolu a časový limit vyprší, operace se nezdařila se zprávou o vypršení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="87f14-962">If the value of the `FilterResumeTimeoutInSeconds` element is non-zero, there are non-protocol bookmarks, and the timeout interval expires, the operation fails with a timeout message.</span></span>

- <span data-ttu-id="87f14-963">**Transakce**</span><span class="sxs-lookup"><span data-stu-id="87f14-963">**Transactions**</span></span>

  <span data-ttu-id="87f14-964">Nyní můžete zahrnout identifikátor distribuované transakce pro transakci, která způsobila výjimku odvozenou od <xref:System.Transactions.TransactionException> vyvolání.</span><span class="sxs-lookup"><span data-stu-id="87f14-964">You can now include the distributed transaction identifier for the transaction that has caused an exception derived from <xref:System.Transactions.TransactionException> to be thrown.</span></span> <span data-ttu-id="87f14-965">Uděláte to tak, že do `appSettings` části souboru app.config přidáte následující klíč:</span><span class="sxs-lookup"><span data-stu-id="87f14-965">You do this by adding the following key to the `appSettings` section of your app.config file:</span></span>

  ```xml
  <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/>
  ```

  <span data-ttu-id="87f14-966">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="87f14-966">The default value is `false`.</span></span>

- <span data-ttu-id="87f14-967">**Sítě**</span><span class="sxs-lookup"><span data-stu-id="87f14-967">**Networking**</span></span>

  - <span data-ttu-id="87f14-968">**Opakované použití soketu**</span><span class="sxs-lookup"><span data-stu-id="87f14-968">**Socket reuse**</span></span>

    <span data-ttu-id="87f14-969">Windows 10 obsahuje nový síťový algoritmus s vysokou škálovatelností, který zajišťuje lepší využívání prostředků počítače tím, že znovu používá místní porty pro odchozí připojení TCP.</span><span class="sxs-lookup"><span data-stu-id="87f14-969">Windows 10 includes a new high-scalability networking algorithm that makes better use of machine resources by reusing local ports for outbound TCP connections.</span></span> <span data-ttu-id="87f14-970">.NET Framework 4,6 podporuje nový algoritmus a umožňuje aplikacím .NET využít nové chování.</span><span class="sxs-lookup"><span data-stu-id="87f14-970">.NET Framework 4.6 supports the new algorithm, enabling .NET apps to take advantage of the new behavior.</span></span> <span data-ttu-id="87f14-971">V předchozích verzích Windows se jednalo o umělý limit souběžného připojení (obvykle 16 384, výchozí velikost dynamického rozsahu portů), což může omezit škálovatelnost služby tím, že při zatížení způsobuje vyčerpání portů.</span><span class="sxs-lookup"><span data-stu-id="87f14-971">In previous versions of Windows, there was an artificial concurrent connection limit (typically 16,384, the default size of the dynamic port range), which could limit the scalability of a service by causing port exhaustion when under load.</span></span>

    <span data-ttu-id="87f14-972">V .NET Framework 4,6 byly přidány dvě rozhraní API, aby bylo možné znovu použít port, což efektivně odstraní limit 64 KB pro souběžná připojení:</span><span class="sxs-lookup"><span data-stu-id="87f14-972">In .NET Framework 4.6, two APIs have been added to enable port reuse, which effectively removes the 64 KB limit on concurrent connections:</span></span>

    - <span data-ttu-id="87f14-973"><xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType>Hodnota výčtu.</span><span class="sxs-lookup"><span data-stu-id="87f14-973">The <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> enumeration value.</span></span>

    - <span data-ttu-id="87f14-974"><xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType>Vlastnost.</span><span class="sxs-lookup"><span data-stu-id="87f14-974">The <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> property.</span></span>

    <span data-ttu-id="87f14-975">Ve výchozím nastavení <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> vlastnost je, `false` Pokud `HWRPortReuseOnSocketBind` hodnota `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` klíče registru není nastavená na 0x1.</span><span class="sxs-lookup"><span data-stu-id="87f14-975">By default, the <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> property is `false` unless the `HWRPortReuseOnSocketBind` value of the `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` registry key is set to 0x1.</span></span> <span data-ttu-id="87f14-976">Chcete-li povolit používání místních portů u připojení HTTP, nastavte <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> vlastnost na hodnotu `true` .</span><span class="sxs-lookup"><span data-stu-id="87f14-976">To enable local port reuse on HTTP connections, set the <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="87f14-977">To způsobí, že všechna odchozí připojení soketu TCP z <xref:System.Net.Http.HttpClient> a <xref:System.Net.HttpWebRequest> na používá novou možnost soketu Windows 10, [SO_REUSE_UNICASTPORT](/windows/desktop/WinSock/sol-socket-socket-options), která umožňuje opakované použití místního portu.</span><span class="sxs-lookup"><span data-stu-id="87f14-977">This causes all outgoing TCP socket connections from <xref:System.Net.Http.HttpClient> and <xref:System.Net.HttpWebRequest> to use a new Windows 10 socket option, [SO_REUSE_UNICASTPORT](/windows/desktop/WinSock/sol-socket-socket-options), that enables local port reuse.</span></span>

    <span data-ttu-id="87f14-978">Vývojáři, kteří vytvářejí pouze sokety, mohou určit <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> možnost při volání metody, například <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> tak, aby odchozí sokety opakovaně znovu vyvolaly místní porty během vytváření vazby.</span><span class="sxs-lookup"><span data-stu-id="87f14-978">Developers writing a sockets-only application can specify the <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> option when calling a method such as <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> so that outbound sockets reuse local ports during binding.</span></span>

  - <span data-ttu-id="87f14-979">**Podpora mezinárodních názvů domén a PunyCode**</span><span class="sxs-lookup"><span data-stu-id="87f14-979">**Support for international domain names and PunyCode**</span></span>

    <span data-ttu-id="87f14-980">Do třídy se přidala nová vlastnost, <xref:System.Uri.IdnHost%2A> která bude <xref:System.Uri> lépe podporovat názvy mezinárodních domén a Punycode.</span><span class="sxs-lookup"><span data-stu-id="87f14-980">A new property, <xref:System.Uri.IdnHost%2A>, has been added to the <xref:System.Uri> class to better support international domain names and PunyCode.</span></span>

- <span data-ttu-id="87f14-981">**Změna velikosti v ovládacích prvcích model Windows Forms.**</span><span class="sxs-lookup"><span data-stu-id="87f14-981">**Resizing in Windows Forms controls.**</span></span>

  <span data-ttu-id="87f14-982">Tato funkce byla rozšířena v .NET Framework 4,6, aby zahrnovala <xref:System.Windows.Forms.DomainUpDown> <xref:System.Windows.Forms.NumericUpDown> typy,, a <xref:System.Windows.Forms.DataGridViewComboBoxColumn> <xref:System.Windows.Forms.DataGridViewColumn> <xref:System.Windows.Forms.ToolStripSplitButton> a obdélník určený <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> vlastností použitou při vykreslování <xref:System.Drawing.Design.UITypeEditor> .</span><span class="sxs-lookup"><span data-stu-id="87f14-982">This feature has been expanded in .NET Framework 4.6 to include the <xref:System.Windows.Forms.DomainUpDown>, <xref:System.Windows.Forms.NumericUpDown>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.ToolStripSplitButton> types and the rectangle specified by the <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> property used when drawing a <xref:System.Drawing.Design.UITypeEditor>.</span></span>

  <span data-ttu-id="87f14-983">Toto je funkce výslovného souhlasu.</span><span class="sxs-lookup"><span data-stu-id="87f14-983">This is an opt-in feature.</span></span> <span data-ttu-id="87f14-984">Pokud ho chcete povolit, nastavte `EnableWindowsFormsHighDpiAutoResizing` element na `true` v souboru konfigurace aplikace (app.config):</span><span class="sxs-lookup"><span data-stu-id="87f14-984">To enable it, set the `EnableWindowsFormsHighDpiAutoResizing` element to `true` in the application configuration (app.config) file:</span></span>

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- <span data-ttu-id="87f14-985">**Podpora kódování znakových stránek**</span><span class="sxs-lookup"><span data-stu-id="87f14-985">**Support for code page encodings**</span></span>

  <span data-ttu-id="87f14-986">.NET Core primárně podporuje kódování Unicode a ve výchozím nastavení poskytuje omezené podpory pro kódování znakových stránek.</span><span class="sxs-lookup"><span data-stu-id="87f14-986">.NET Core primarily supports the Unicode encodings and by default provides limited support for code page encodings.</span></span> <span data-ttu-id="87f14-987">Můžete přidat podporu pro kódování znakových stránek, která jsou k dispozici v .NET Framework, ale nepodporovaná v .NET Core, registrací kódování znakové stránky pomocí <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="87f14-987">You can add support for code page encodings available in .NET Framework but unsupported in .NET Core by registering code page encodings with the <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="87f14-988">Další informace naleznete v tématu <xref:System.Text.CodePagesEncodingProvider?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="87f14-988">For more information, see <xref:System.Text.CodePagesEncodingProvider?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="87f14-989">**.NET Native**</span><span class="sxs-lookup"><span data-stu-id="87f14-989">**.NET Native**</span></span>

  <span data-ttu-id="87f14-990">Aplikace pro Windows pro Windows 10, které cílí na .NET Core a jsou napsané v jazyce C# nebo Visual Basic můžou využít novou technologii, která kompiluje aplikace do nativního kódu místo IL.</span><span class="sxs-lookup"><span data-stu-id="87f14-990">Windows apps for Windows 10 that target .NET Core and are written in C# or Visual Basic can take advantage of a new technology that compiles apps to native code rather than IL.</span></span> <span data-ttu-id="87f14-991">Vytváří aplikace s větším počtem časů spuštění a spuštění.</span><span class="sxs-lookup"><span data-stu-id="87f14-991">They produce apps characterized by faster startup and execution times.</span></span> <span data-ttu-id="87f14-992">Další informace najdete v tématu [kompilace aplikací pomocí .NET Native](../net-native/index.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-992">For more information, see [Compiling Apps with .NET Native](../net-native/index.md).</span></span> <span data-ttu-id="87f14-993">Přehled .NET Native, který prověřuje, jak se liší od kompilace JIT i NGEN a co znamená pro váš kód, naleznete v tématu [.NET Native a kompilace](../net-native/net-native-and-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-993">For an overview of .NET Native that examines how it differs from both JIT compilation and NGEN and what that means for your code, see [.NET Native and Compilation](../net-native/net-native-and-compilation.md).</span></span>

  <span data-ttu-id="87f14-994">Vaše aplikace jsou kompilovány do nativního kódu ve výchozím nastavení, když je kompilujete pomocí sady Visual Studio 2015 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="87f14-994">Your apps are compiled to native code by default when you compile them with Visual Studio 2015 or later.</span></span> <span data-ttu-id="87f14-995">Další informace najdete v tématu [Začínáme s .NET Native](../net-native/getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-995">For more information, see [Getting Started with .NET Native](../net-native/getting-started-with-net-native.md).</span></span>

  <span data-ttu-id="87f14-996">Pro podporu ladění aplikací .NET Native bylo přidáno několik nových rozhraní a výčtů do nespravovaného ladicího rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="87f14-996">To support debugging .NET Native apps, a number of new interfaces and enumerations have been added to the unmanaged debugging API.</span></span> <span data-ttu-id="87f14-997">Další informace naleznete v tématu [ladění (nespravované rozhraní API)](../unmanaged-api/debugging/index.md) .</span><span class="sxs-lookup"><span data-stu-id="87f14-997">For more information, see the [Debugging (Unmanaged API Reference)](../unmanaged-api/debugging/index.md) topic.</span></span>

- <span data-ttu-id="87f14-998">**Open Source .NET Framework balíčky**</span><span class="sxs-lookup"><span data-stu-id="87f14-998">**Open-source .NET Framework packages**</span></span>

  <span data-ttu-id="87f14-999">Balíčky .NET Core, jako jsou neměnné kolekce, [rozhraní API SIMD](https://www.nuget.org/packages/Microsoft.Bcl.Simd)a síťové rozhraní API, jako jsou ty, které se nacházejí v <xref:System.Net.Http> oboru názvů, jsou teď dostupné jako open source balíčky na [GitHubu](https://github.com/).</span><span class="sxs-lookup"><span data-stu-id="87f14-999">.NET Core packages such as the immutable collections, [SIMD APIs](https://www.nuget.org/packages/Microsoft.Bcl.Simd), and networking APIs such as those found in the <xref:System.Net.Http> namespace are now available as open-source packages on [GitHub](https://github.com/).</span></span> <span data-ttu-id="87f14-1000">Přístup k kódu naleznete v tématu [.NET na GitHubu](https://github.com/dotnet/runtime).</span><span class="sxs-lookup"><span data-stu-id="87f14-1000">To access the code, see [.NET on GitHub](https://github.com/dotnet/runtime).</span></span> <span data-ttu-id="87f14-1001">Další informace a o tom, jak přispívat do těchto balíčků, najdete v tématu [.NET Core a open source](../get-started/net-core-and-open-source.md), [Domovská stránka .NET na GitHubu](https://github.com/dotnet/home).</span><span class="sxs-lookup"><span data-stu-id="87f14-1001">For more information and how to contribute to these packages, see [.NET Core and Open-Source](../get-started/net-core-and-open-source.md), [.NET Home Page on GitHub](https://github.com/dotnet/home).</span></span>

<a name="v452"></a>

## <a name="whats-new-in-net-framework-452"></a><span data-ttu-id="87f14-1002">Co je nového v .NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="87f14-1002">What's new in .NET Framework 4.5.2</span></span>

- <span data-ttu-id="87f14-1003">**Nová rozhraní API pro aplikace ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="87f14-1003">**New APIs for ASP.NET apps.**</span></span> <span data-ttu-id="87f14-1004">Nové <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=nameWithType> metody a <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=nameWithType> umožňují kontrolovat a upravovat hlavičky odpovědí a stavový kód, protože odpověď se vyprazdňuje do klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="87f14-1004">The new <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=nameWithType> and <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=nameWithType> methods let you inspect and modify response headers and status code as the response is being flushed to the client app.</span></span> <span data-ttu-id="87f14-1005">Zvažte použití těchto metod namísto <xref:System.Web.HttpApplication.PreSendRequestHeaders> <xref:System.Web.HttpApplication.PreSendRequestContent> událostí a. jsou efektivnější a spolehlivé.</span><span class="sxs-lookup"><span data-stu-id="87f14-1005">Consider using these methods instead of the <xref:System.Web.HttpApplication.PreSendRequestHeaders> and <xref:System.Web.HttpApplication.PreSendRequestContent> events; they are more efficient and reliable.</span></span>

  <span data-ttu-id="87f14-1006"><xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=nameWithType>Metoda umožňuje naplánovat malé pracovní položky na pozadí.</span><span class="sxs-lookup"><span data-stu-id="87f14-1006">The <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=nameWithType> method lets you schedule small background work items.</span></span> <span data-ttu-id="87f14-1007">ASP.NET sleduje tyto položky a brání službě IIS v náhlém ukončení pracovního procesu, dokud nebudou dokončeny všechny pracovní položky na pozadí.</span><span class="sxs-lookup"><span data-stu-id="87f14-1007">ASP.NET tracks these items and prevents IIS from abruptly terminating the worker process until all background work items have completed.</span></span> <span data-ttu-id="87f14-1008">Tuto metodu nejde volat mimo doménu spravované aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="87f14-1008">This method can't be called outside an ASP.NET managed app domain.</span></span>

  <span data-ttu-id="87f14-1009">Nové <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=nameWithType> vlastnosti a <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=nameWithType> vrátí logické hodnoty, které určují, zda byly napsány hlavičky odpovědi.</span><span class="sxs-lookup"><span data-stu-id="87f14-1009">The new <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=nameWithType> and <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=nameWithType> properties return Boolean values that indicate whether the response headers have been written.</span></span> <span data-ttu-id="87f14-1010">Tyto vlastnosti můžete použít k tomu, abyste se ujistili, že volání rozhraní API <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=nameWithType> (která vyvolávají výjimky při zápisu hlaviček) budou úspěšná.</span><span class="sxs-lookup"><span data-stu-id="87f14-1010">You can use these properties to make sure that calls to APIs such as <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=nameWithType> (which throw exceptions if the headers have been written) will succeed.</span></span>

- <span data-ttu-id="87f14-1011">**Změna velikosti v ovládacích prvcích model Windows Forms.**</span><span class="sxs-lookup"><span data-stu-id="87f14-1011">**Resizing in Windows Forms controls.**</span></span> <span data-ttu-id="87f14-1012">Tato funkce se rozšířila.</span><span class="sxs-lookup"><span data-stu-id="87f14-1012">This feature has been expanded.</span></span> <span data-ttu-id="87f14-1013">Nyní můžete použít nastavení systému DPI pro změnu velikosti součástí následujících dalších ovládacích prvků (například šipky rozevíracího seznamu v polích se seznamem):</span><span class="sxs-lookup"><span data-stu-id="87f14-1013">You can now use the system DPI setting to resize components of the following additional controls (for example, the drop-down arrow in combo boxes):</span></span>

  - <xref:System.Windows.Forms.ComboBox>
  - <xref:System.Windows.Forms.ToolStripComboBox>
  - <xref:System.Windows.Forms.ToolStripMenuItem>
  - <xref:System.Windows.Forms.Cursor>
  - <xref:System.Windows.Forms.DataGridView>
  - <xref:System.Windows.Forms.DataGridViewComboBoxColumn>

  <span data-ttu-id="87f14-1014">Toto je funkce výslovného souhlasu.</span><span class="sxs-lookup"><span data-stu-id="87f14-1014">This is an opt-in feature.</span></span> <span data-ttu-id="87f14-1015">Pokud ho chcete povolit, nastavte `EnableWindowsFormsHighDpiAutoResizing` element na `true` v souboru konfigurace aplikace (app.config):</span><span class="sxs-lookup"><span data-stu-id="87f14-1015">To enable it, set the `EnableWindowsFormsHighDpiAutoResizing` element to `true` in the application configuration (app.config) file:</span></span>

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- <span data-ttu-id="87f14-1016">**Nová funkce pracovního postupu.**</span><span class="sxs-lookup"><span data-stu-id="87f14-1016">**New workflow feature.**</span></span> <span data-ttu-id="87f14-1017">Správce prostředků, který používá <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> metodu (a proto implementuje <xref:System.Transactions.IPromotableSinglePhaseNotification> rozhraní), může použít novou <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> metodu k vyžádání následujícího:</span><span class="sxs-lookup"><span data-stu-id="87f14-1017">A resource manager that's using the <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> method (and therefore implementing the <xref:System.Transactions.IPromotableSinglePhaseNotification> interface) can use the new <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> method to request the following:</span></span>

  - <span data-ttu-id="87f14-1018">Povýšit transakci na transakci Microsoft DTC (Distributed Transaction Coordinator) (MSDTC).</span><span class="sxs-lookup"><span data-stu-id="87f14-1018">Promote the transaction to a Microsoft Distributed Transaction Coordinator (MSDTC) transaction.</span></span>

  - <span data-ttu-id="87f14-1019">Nahraďte <xref:System.Transactions.IPromotableSinglePhaseNotification> <xref:System.Transactions.ISinglePhaseNotification> , což je trvalé zařazení, které podporuje jednotlivé fáze potvrzení.</span><span class="sxs-lookup"><span data-stu-id="87f14-1019">Replace <xref:System.Transactions.IPromotableSinglePhaseNotification> with an <xref:System.Transactions.ISinglePhaseNotification>, which is a durable enlistment that supports single phase commits.</span></span>

  <span data-ttu-id="87f14-1020">To se dá udělat v rámci stejné domény aplikace a nevyžaduje žádný dodatečný nespravovaný kód pro interakci se službou MSDTC, aby bylo možné provést povýšení.</span><span class="sxs-lookup"><span data-stu-id="87f14-1020">This can be done within the same app domain, and doesn't require any extra unmanaged code to interact with MSDTC to perform the promotion.</span></span> <span data-ttu-id="87f14-1021">Nová metoda může být volána pouze v případě, že existuje nedokončené volání <xref:System.Transactions?displayProperty=nameWithType> do <xref:System.Transactions.IPromotableSinglePhaseNotification> `Promote` metody, která je implementována prostřednictvím zařazení do propagačního objektu.</span><span class="sxs-lookup"><span data-stu-id="87f14-1021">The new method can be called only when there's an outstanding call from <xref:System.Transactions?displayProperty=nameWithType> to the <xref:System.Transactions.IPromotableSinglePhaseNotification>`Promote` method that's implemented by the promotable enlistment.</span></span>

- <span data-ttu-id="87f14-1022">**Vylepšení profilace.**</span><span class="sxs-lookup"><span data-stu-id="87f14-1022">**Profiling improvements.**</span></span> <span data-ttu-id="87f14-1023">Následující nová nespravovaná rozhraní API pro profilaci poskytují robustnější profilaci:</span><span class="sxs-lookup"><span data-stu-id="87f14-1023">The following new unmanaged profiling APIs provide more robust profiling:</span></span>

  - [<span data-ttu-id="87f14-1024">Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO</span><span class="sxs-lookup"><span data-stu-id="87f14-1024">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](../unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)
  - [<span data-ttu-id="87f14-1025">Výčet COR_PRF_HIGH_MONITOR</span><span class="sxs-lookup"><span data-stu-id="87f14-1025">COR_PRF_HIGH_MONITOR Enumeration</span></span>](../unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)
  - [<span data-ttu-id="87f14-1026">GetAssemblyReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="87f14-1026">GetAssemblyReferences Method</span></span>](../unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
  - [<span data-ttu-id="87f14-1027">GetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="87f14-1027">GetEventMask2 Method</span></span>](../unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
  - [<span data-ttu-id="87f14-1028">SetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="87f14-1028">SetEventMask2 Method</span></span>](../unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
  - [<span data-ttu-id="87f14-1029">AddAssemblyReference – metoda</span><span class="sxs-lookup"><span data-stu-id="87f14-1029">AddAssemblyReference Method</span></span>](../unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)

  <span data-ttu-id="87f14-1030">Předchozí `ICorProfiler` implementace podporovaly opožděné načítání závislých sestavení.</span><span class="sxs-lookup"><span data-stu-id="87f14-1030">Previous `ICorProfiler` implementations supported lazy loading of dependent assemblies.</span></span> <span data-ttu-id="87f14-1031">Nové rozhraní API pro profilování vyžadují závislá sestavení, která jsou vložená profilerem tak, aby se spustitelný hned, místo aby se načetla po úplné inicializaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="87f14-1031">The new profiling APIs require dependent assemblies that are injected by the profiler to be loadable immediately, instead of being loaded after the app is fully initialized.</span></span> <span data-ttu-id="87f14-1032">Tato změna neovlivní uživatele existujících `ICorProfiler` rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="87f14-1032">This change doesn't affect users of the existing `ICorProfiler` APIs.</span></span>

- <span data-ttu-id="87f14-1033">**Vylepšení ladění.**</span><span class="sxs-lookup"><span data-stu-id="87f14-1033">**Debugging improvements.**</span></span> <span data-ttu-id="87f14-1034">Následující nová nespravovaná ladicí rozhraní API poskytují lepší integraci s profilerem.</span><span class="sxs-lookup"><span data-stu-id="87f14-1034">The following new unmanaged debugging APIs provide better integration with a profiler.</span></span> <span data-ttu-id="87f14-1035">Teď můžete přistupovat k metadatům vloženým profilerem a také k místním proměnným a kódu vytvořeným požadavky kompilátoru ReJIT při ladění výpisu.</span><span class="sxs-lookup"><span data-stu-id="87f14-1035">You can now access metadata inserted by the profiler as well as local variables and code produced by compiler ReJIT requests when dump debugging.</span></span>

  - [<span data-ttu-id="87f14-1036">SetWriteableMetadataUpdateMode – metoda</span><span class="sxs-lookup"><span data-stu-id="87f14-1036">SetWriteableMetadataUpdateMode Method</span></span>](../unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
  - [<span data-ttu-id="87f14-1037">EnumerateLocalVariablesEx – metoda</span><span class="sxs-lookup"><span data-stu-id="87f14-1037">EnumerateLocalVariablesEx Method</span></span>](../unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)
  - [<span data-ttu-id="87f14-1038">GetLocalVariableEx – metoda</span><span class="sxs-lookup"><span data-stu-id="87f14-1038">GetLocalVariableEx Method</span></span>](../unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)
  - [<span data-ttu-id="87f14-1039">GetCodeEx – metoda</span><span class="sxs-lookup"><span data-stu-id="87f14-1039">GetCodeEx Method</span></span>](../unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)
  - [<span data-ttu-id="87f14-1040">GetActiveReJitRequestILCode – metoda</span><span class="sxs-lookup"><span data-stu-id="87f14-1040">GetActiveReJitRequestILCode Method</span></span>](../unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)
  - [<span data-ttu-id="87f14-1041">GetInstrumentedILMap – metoda</span><span class="sxs-lookup"><span data-stu-id="87f14-1041">GetInstrumentedILMap Method</span></span>](../unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)

- <span data-ttu-id="87f14-1042">**Změny trasování událostí.**</span><span class="sxs-lookup"><span data-stu-id="87f14-1042">**Event tracing changes.**</span></span> <span data-ttu-id="87f14-1043">.NET Framework 4.5.2 umožňuje trasování aktivit založené na trasování událostí pro Windows (ETW) pro větší plochu.</span><span class="sxs-lookup"><span data-stu-id="87f14-1043">.NET Framework 4.5.2 enables out-of-process, Event Tracing for Windows (ETW)-based activity tracing for a larger surface area.</span></span> <span data-ttu-id="87f14-1044">To umožňuje prodejcům pokročilého řízení spotřeby (APM) poskytovat odlehčené nástroje, které přesně sledují náklady na jednotlivé požadavky a aktivity, které procházejí vlákny.</span><span class="sxs-lookup"><span data-stu-id="87f14-1044">This enables Advanced Power Management (APM) vendors to provide lightweight tools that accurately track the costs of individual requests and activities that cross threads.</span></span>  <span data-ttu-id="87f14-1045">Tyto události jsou vyvolány pouze v případě, že je povolí řadič ETW. Proto změny neovlivní dříve psaný kód ETW nebo kód, který běží se zakázanou ETW.</span><span class="sxs-lookup"><span data-stu-id="87f14-1045">These events are raised only when ETW controllers enable them; therefore, the changes don't affect previously written ETW code or code that runs with ETW disabled.</span></span>

- <span data-ttu-id="87f14-1046">**Zvýšení úrovně transakce a její převedení na trvalý zařazení**</span><span class="sxs-lookup"><span data-stu-id="87f14-1046">**Promoting a transaction and converting it to a durable enlistment**</span></span>

  <span data-ttu-id="87f14-1047"><xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType>je nové rozhraní API přidané do .NET Framework 4.5.2 a 4,6:</span><span class="sxs-lookup"><span data-stu-id="87f14-1047"><xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> is a new API added to .NET Framework 4.5.2 and 4.6:</span></span>

  ```csharp
  [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]
  public Enlistment PromoteAndEnlistDurable(Guid resourceManagerIdentifier,
                                            IPromotableSinglePhaseNotification promotableNotification,
                                            ISinglePhaseNotification enlistmentNotification,
                                            EnlistmentOptions enlistmentOptions)
  ```

  ```vb
  <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")>
  public Function PromoteAndEnlistDurable(resourceManagerIdentifier As Guid,
                                          promotableNotification As IPromotableSinglePhaseNotification,
                                          enlistmentNotification As ISinglePhaseNotification,
                                          enlistmentOptions As EnlistmentOptions) As Enlistment
  ```

  <span data-ttu-id="87f14-1048">Metodu lze použít pro zařazení, které bylo dříve vytvořeno <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> v reakci na <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="87f14-1048">The method may be used by an enlistment that was previously created by <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> in response to the <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="87f14-1049">Žádá `System.Transactions` o povýšení transakce na transakci MSDTC a na "převést" zařazení do trvalého zařazení.</span><span class="sxs-lookup"><span data-stu-id="87f14-1049">It asks `System.Transactions` to promote the transaction to an MSDTC transaction and to "convert" the promotable enlistment to a durable enlistment.</span></span> <span data-ttu-id="87f14-1050">Po úspěšném dokončení této metody <xref:System.Transactions.IPromotableSinglePhaseNotification> již nebude odkazováno na rozhraní `System.Transactions` a veškerá budoucí oznámení budou doručena do poskytnutého <xref:System.Transactions.ISinglePhaseNotification> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="87f14-1050">After this method completes successfully, the <xref:System.Transactions.IPromotableSinglePhaseNotification> interface will no longer be referenced by `System.Transactions`, and any future notifications will arrive on the provided <xref:System.Transactions.ISinglePhaseNotification> interface.</span></span> <span data-ttu-id="87f14-1051">Příslušné zařazení musí působit jako trvalé zařazení, které podporuje protokolování a obnovení transakcí.</span><span class="sxs-lookup"><span data-stu-id="87f14-1051">The enlistment in question must act as a durable enlistment, supporting transaction logging and recovery.</span></span> <span data-ttu-id="87f14-1052">Podrobnosti najdete <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType> v tématu.</span><span class="sxs-lookup"><span data-stu-id="87f14-1052">Refer to <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType> for details.</span></span> <span data-ttu-id="87f14-1053">Zařazení navíc musí podporovat <xref:System.Transactions.ISinglePhaseNotification> .</span><span class="sxs-lookup"><span data-stu-id="87f14-1053">In addition, the enlistment must support <xref:System.Transactions.ISinglePhaseNotification>.</span></span>  <span data-ttu-id="87f14-1054">Tuto metodu lze volat *pouze* během zpracovávání <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> volání.</span><span class="sxs-lookup"><span data-stu-id="87f14-1054">This method can *only* be called while processing an <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> call.</span></span> <span data-ttu-id="87f14-1055">V takovém případě <xref:System.Transactions.TransactionException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="87f14-1055">If that is not the case, a <xref:System.Transactions.TransactionException> exception is thrown.</span></span>

<a name="v451"></a>

## <a name="whats-new-in-net-framework-451"></a><span data-ttu-id="87f14-1056">Co je nového ve .NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="87f14-1056">What's new in .NET Framework 4.5.1</span></span>

<span data-ttu-id="87f14-1057">**Aktualizace z dubna 2014**:</span><span class="sxs-lookup"><span data-stu-id="87f14-1057">**April 2014 updates**:</span></span>

- <span data-ttu-id="87f14-1058">[Visual Studio 2013 aktualizace 2](https://go.microsoft.com/fwlink/p/?LinkId=393658) obsahuje aktualizace šablon přenosných knihoven tříd pro podporu těchto scénářů:</span><span class="sxs-lookup"><span data-stu-id="87f14-1058">[Visual Studio 2013 Update 2](https://go.microsoft.com/fwlink/p/?LinkId=393658) includes updates to the Portable Class Library templates to support these scenarios:</span></span>

  - <span data-ttu-id="87f14-1059">Rozhraní prostředí Windows Runtime API můžete použít v přenosných knihovnách, které cílí na Windows 8.1, Windows Phone 8,1 a Windows Phone Silverlight 8,1.</span><span class="sxs-lookup"><span data-stu-id="87f14-1059">You can use Windows Runtime APIs in portable libraries that target Windows 8.1, Windows Phone 8.1, and Windows Phone Silverlight 8.1.</span></span>

  - <span data-ttu-id="87f14-1060">Když cílíte Windows 8.1 nebo Windows Phone 8,1, můžete do přenosných knihoven zahrnout XAML (typy Windows. UI. XAML).</span><span class="sxs-lookup"><span data-stu-id="87f14-1060">You can include XAML (Windows.UI.XAML types) in portable libraries when you target Windows 8.1 or Windows Phone 8.1.</span></span> <span data-ttu-id="87f14-1061">Podporovány jsou následující šablony XAML: prázdná stránka, slovník prostředků, ovládací prvek s šablonou a uživatelský ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="87f14-1061">The following XAML templates are supported:  Blank Page, Resource Dictionary, Templated Control, and User Control.</span></span>

  - <span data-ttu-id="87f14-1062">Můžete vytvořit přenosnou součást prostředí Windows Runtime (soubor. winmd) pro použití v aplikacích pro Store, které cílí na Windows 8.1 a Windows Phone 8,1.</span><span class="sxs-lookup"><span data-stu-id="87f14-1062">You can create a portable Windows Runtime component (.winmd file) for use in Store apps that target Windows 8.1 and Windows Phone 8.1.</span></span>

  - <span data-ttu-id="87f14-1063">Můžete změnit cíl knihovny tříd Windows Store nebo Windows Phone Store, jako je Přenosná knihovna tříd.</span><span class="sxs-lookup"><span data-stu-id="87f14-1063">You can retarget a Windows Store or Windows Phone Store class library like a Portable Class Library.</span></span>

  <span data-ttu-id="87f14-1064">Další informace o těchto změnách naleznete v tématu [Přenosná knihovna tříd](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-1064">For more information about these changes, see [Portable Class Library](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).</span></span>

- <span data-ttu-id="87f14-1065">Sada .NET Framework obsahu teď obsahuje dokumentaci pro .NET Native, což je předkompilace technologie pro sestavování a nasazování aplikací pro Windows.</span><span class="sxs-lookup"><span data-stu-id="87f14-1065">The .NET Framework content set now includes documentation for .NET Native, which is a precompilation technology for building and deploying Windows apps.</span></span> <span data-ttu-id="87f14-1066">.NET Native zkompiluje vaše aplikace přímo do nativního kódu, spíše než do mezilehlého jazyka (IL), pro lepší výkon.</span><span class="sxs-lookup"><span data-stu-id="87f14-1066">.NET Native compiles your apps directly to native code, rather than to intermediate language (IL), for better performance.</span></span> <span data-ttu-id="87f14-1067">Podrobnosti najdete v tématu [kompilace aplikací pomocí .NET Native](../net-native/index.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-1067">For details, see [Compiling Apps with .NET Native](../net-native/index.md).</span></span>

- <span data-ttu-id="87f14-1068">[Zdroj odkazů .NET Framework](https://referencesource.microsoft.com/) poskytuje nové prostředí pro procházení a vylepšené funkce.</span><span class="sxs-lookup"><span data-stu-id="87f14-1068">The [.NET Framework Reference Source](https://referencesource.microsoft.com/) provides a new browsing experience and enhanced functionality.</span></span> <span data-ttu-id="87f14-1069">Nyní můžete procházet zdrojový kód .NET Framework online, [stahovat reference](https://referencesource.microsoft.com/download.html) pro zobrazení v režimu offline a procházet zdroje (včetně oprav a aktualizací) během ladění.</span><span class="sxs-lookup"><span data-stu-id="87f14-1069">You can now browse through the .NET Framework source code online, [download the reference](https://referencesource.microsoft.com/download.html) for offline viewing, and step through the sources (including patches and updates) during debugging.</span></span> <span data-ttu-id="87f14-1070">Další informace najdete v blogu o [novém hledání zdroje odkazů .NET](https://devblogs.microsoft.com/dotnet/a-new-look-for-net-reference-source/).</span><span class="sxs-lookup"><span data-stu-id="87f14-1070">For more information, see the blog entry [A new look for .NET Reference Source](https://devblogs.microsoft.com/dotnet/a-new-look-for-net-reference-source/).</span></span>

<span data-ttu-id="87f14-1071">Mezi nové funkce a vylepšení základních tříd v .NET Framework 4.5.1 patří:</span><span class="sxs-lookup"><span data-stu-id="87f14-1071">New features and enhancements in the base classes in .NET Framework 4.5.1 include:</span></span>

- <span data-ttu-id="87f14-1072">Automatické přesměrování vazby pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="87f14-1072">Automatic binding redirection for assemblies.</span></span> <span data-ttu-id="87f14-1073">Počínaje Visual Studio 2013 se při kompilování aplikace, která cílí na .NET Framework 4.5.1, dají přesměrování vazby přidat do konfiguračního souboru aplikace, pokud vaše aplikace nebo její součásti odkazují na více verzí stejného sestavení.</span><span class="sxs-lookup"><span data-stu-id="87f14-1073">Starting with Visual Studio 2013, when you compile an app that targets the .NET Framework 4.5.1, binding redirects may be added to the app configuration file if your app or its components reference multiple versions of the same assembly.</span></span> <span data-ttu-id="87f14-1074">Tuto funkci můžete také povolit pro projekty, které cílí na starší verze .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="87f14-1074">You can also enable this feature for projects that target older versions of the .NET Framework.</span></span> <span data-ttu-id="87f14-1075">Další informace najdete v tématu [Postup: povolení a zákaz automatického přesměrování vazby](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-1075">For more information, see [How to: Enable and Disable Automatic Binding Redirection](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).</span></span>

- <span data-ttu-id="87f14-1076">Možnost shromažďovat diagnostické informace, které vývojářům pomůžou zlepšit výkon serverových a cloudových aplikací.</span><span class="sxs-lookup"><span data-stu-id="87f14-1076">Ability to collect diagnostics information to help developers improve the performance of server and cloud applications.</span></span> <span data-ttu-id="87f14-1077">Další informace naleznete v tématu <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> metody a <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> <xref:System.Diagnostics.Tracing.EventSource> třídy.</span><span class="sxs-lookup"><span data-stu-id="87f14-1077">For more information, see the <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> and <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> methods in the <xref:System.Diagnostics.Tracing.EventSource> class.</span></span>

- <span data-ttu-id="87f14-1078">Schopnost explicitně komprimovat haldu velkých objektů (LOH) během uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="87f14-1078">Ability to explicitly compact the large object heap (LOH) during garbage collection.</span></span> <span data-ttu-id="87f14-1079">Další informace najdete v tématu <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="87f14-1079">For more information, see the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> property.</span></span>

- <span data-ttu-id="87f14-1080">Další vylepšení výkonu, jako je například pozastavení aplikace ASP.NET, vícejazykové vylepšení JIT a rychlejší spuštění aplikace po aktualizaci .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="87f14-1080">Additional performance improvements such as ASP.NET app suspension, multi-core JIT improvements, and faster app startup after a .NET Framework update.</span></span> <span data-ttu-id="87f14-1081">Podrobnosti najdete v příspěvku na blogu [.NET Framework 4.5.1](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/) a v blogovém příspěvku o [pozastavení aplikace ASP.NET](https://devblogs.microsoft.com/dotnet/asp-net-app-suspend-responsive-shared-net-web-hosting/) .</span><span class="sxs-lookup"><span data-stu-id="87f14-1081">For details, see the [.NET Framework 4.5.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/) and the [ASP.NET app suspend](https://devblogs.microsoft.com/dotnet/asp-net-app-suspend-responsive-shared-net-web-hosting/) blog post.</span></span>

<span data-ttu-id="87f14-1082">Mezi vylepšení model Windows Forms patří:</span><span class="sxs-lookup"><span data-stu-id="87f14-1082">Improvements to Windows Forms include:</span></span>

- <span data-ttu-id="87f14-1083">Změna velikosti v ovládacích prvcích model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="87f14-1083">Resizing in Windows Forms controls.</span></span> <span data-ttu-id="87f14-1084">Pomocí nastavení rozlišení DPI systému můžete změnit velikost součástí ovládacích prvků (například ikony, které se zobrazí v mřížce vlastností), tím, že se přiřadíte k položce v konfiguračním souboru aplikace (app.config) pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="87f14-1084">You can use the system DPI setting to resize components of controls (for example, the icons that appear in a property grid) by opting in with an entry in the application configuration file (app.config) for your app.</span></span> <span data-ttu-id="87f14-1085">Tato funkce je aktuálně podporována v následujících ovládacích prvcích model Windows Forms:</span><span class="sxs-lookup"><span data-stu-id="87f14-1085">This feature is currently supported in the following Windows Forms controls:</span></span>

  - <xref:System.Windows.Forms.PropertyGrid>
  - <xref:System.Windows.Forms.TreeView>
  - <span data-ttu-id="87f14-1086">Některé aspekty <xref:System.Windows.Forms.DataGridView> (viz [nové funkce v 4.5.2](#v452) pro další podporované ovládací prvky)</span><span class="sxs-lookup"><span data-stu-id="87f14-1086">Some aspects of the <xref:System.Windows.Forms.DataGridView> (see [new features in 4.5.2](#v452) for additional controls supported)</span></span>

  <span data-ttu-id="87f14-1087">Chcete-li povolit tuto funkci, přidejte nový \<appSettings> prvek do konfiguračního souboru (app.config) a nastavte `EnableWindowsFormsHighDpiAutoResizing` element na `true` :</span><span class="sxs-lookup"><span data-stu-id="87f14-1087">To enable this feature, add a new \<appSettings> element to the configuration file (app.config) and set the `EnableWindowsFormsHighDpiAutoResizing` element to `true`:</span></span>

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

<span data-ttu-id="87f14-1088">Vylepšení při ladění .NET Frameworkch aplikací v Visual Studio 2013 zahrnují:</span><span class="sxs-lookup"><span data-stu-id="87f14-1088">Improvements when debugging your .NET Framework apps in Visual Studio 2013 include:</span></span>

- <span data-ttu-id="87f14-1089">Návratové hodnoty v ladicím programu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="87f14-1089">Return values in the Visual Studio debugger.</span></span> <span data-ttu-id="87f14-1090">Při ladění spravované aplikace v Visual Studio 2013 zobrazí okno Automatické hodnoty návratové typy a hodnoty pro metody.</span><span class="sxs-lookup"><span data-stu-id="87f14-1090">When you debug a managed app in Visual Studio 2013, the Autos window displays return types and values for methods.</span></span> <span data-ttu-id="87f14-1091">Tyto informace jsou k dispozici pro stolní počítače, Windows Store a aplikace Windows Phone.</span><span class="sxs-lookup"><span data-stu-id="87f14-1091">This information is available for desktop, Windows Store, and Windows Phone apps.</span></span> <span data-ttu-id="87f14-1092">Další informace naleznete v tématu [Kontrola vrácených hodnot volání metody](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/dn323257(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="87f14-1092">For more information, see [Examine return values of method calls](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/dn323257(v=vs.120)).</span></span>

- <span data-ttu-id="87f14-1093">Upravit a pokračovat pro 64 aplikace</span><span class="sxs-lookup"><span data-stu-id="87f14-1093">Edit and Continue for 64-bit apps.</span></span> <span data-ttu-id="87f14-1094">Visual Studio 2013 podporuje funkci upravit a pokračovat pro 64 spravované aplikace pro stolní počítače, Windows Store a Windows Phone.</span><span class="sxs-lookup"><span data-stu-id="87f14-1094">Visual Studio 2013 supports the Edit and Continue feature for 64-bit managed apps for desktop, Windows Store, and Windows Phone.</span></span> <span data-ttu-id="87f14-1095">Stávající omezení zůstávají v platnosti pro 32 i pro 64-bitové aplikace (viz poslední část článku [podporované změny kódu (C#)](/visualstudio/debugger/supported-code-changes-csharp) ).</span><span class="sxs-lookup"><span data-stu-id="87f14-1095">The existing limitations remain in effect for both 32-bit and 64-bit apps (see the last section of the [Supported Code Changes (C#)](/visualstudio/debugger/supported-code-changes-csharp) article).</span></span>

- <span data-ttu-id="87f14-1096">Asynchronní ladění.</span><span class="sxs-lookup"><span data-stu-id="87f14-1096">Async-aware debugging.</span></span> <span data-ttu-id="87f14-1097">Aby bylo snazší ladit asynchronní aplikace v Visual Studio 2013, zásobník volání skrývá kód infrastruktury poskytnutý kompilátory pro podporu asynchronního programování a také řetězení v logických nadřazených snímcích, takže můžete pořídit provádění logického programu podrobněji.</span><span class="sxs-lookup"><span data-stu-id="87f14-1097">To make it easier to debug asynchronous apps in Visual Studio 2013, the call stack hides the infrastructure code provided by compilers to support asynchronous programming, and also chains in logical parent frames so you can follow logical program execution more clearly.</span></span> <span data-ttu-id="87f14-1098">Okno úkoly nahrazuje okno paralelní úkoly a zobrazuje úkoly, které se vztahují k určité zarážce, a také zobrazí všechny další úkoly, které jsou v aplikaci aktuálně aktivní nebo naplánované.</span><span class="sxs-lookup"><span data-stu-id="87f14-1098">A Tasks window replaces the Parallel Tasks window and displays tasks that relate to a particular breakpoint, and also displays any other tasks that are currently active or scheduled in the app.</span></span> <span data-ttu-id="87f14-1099">O této funkci si můžete přečíst v části "asynchronní ladění" v [oznámení .NET Framework 4.5.1](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).</span><span class="sxs-lookup"><span data-stu-id="87f14-1099">You can read about this feature in the "Async-aware debugging" section of the [.NET Framework 4.5.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).</span></span>

- <span data-ttu-id="87f14-1100">Lepší podpora výjimek pro součásti prostředí Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="87f14-1100">Better exception support for Windows Runtime components.</span></span> <span data-ttu-id="87f14-1101">V Windows 8.1 výjimky, které vznikají v aplikacích pro Windows Store, uchovávají informace o chybě, která způsobila výjimku, i přes hranice jazyka.</span><span class="sxs-lookup"><span data-stu-id="87f14-1101">In Windows 8.1, exceptions that arise from Windows Store apps preserve information about the error that caused the exception, even across language boundaries.</span></span> <span data-ttu-id="87f14-1102">O této funkci si můžete přečíst v části vývoj aplikací pro Windows Store v [oznámení .NET Framework 4.5.1](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).</span><span class="sxs-lookup"><span data-stu-id="87f14-1102">You can read about this feature in the "Windows Store app development" section of the [.NET Framework 4.5.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).</span></span>

<span data-ttu-id="87f14-1103">Počínaje Visual Studio 2013 můžete použít [Nástroj pro optimalizaci spravovaného profilu (Mpgo.exe)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md) k optimalizaci aplikací pro Windows 8. x Store a aplikací klasické pracovní plochy.</span><span class="sxs-lookup"><span data-stu-id="87f14-1103">Starting with Visual Studio 2013, you can use the [Managed Profile Guided Optimization Tool (Mpgo.exe)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md) to optimize Windows 8.x Store apps as well as desktop apps.</span></span>

<span data-ttu-id="87f14-1104">Nové funkce v ASP.NET 4.5.1 najdete v tématu [ASP.NET and Web Tools for Visual Studio 2013 poznámky k verzi](/aspnet/visual-studio/overview/2013/release-notes).</span><span class="sxs-lookup"><span data-stu-id="87f14-1104">For new features in ASP.NET 4.5.1, see [ASP.NET and Web Tools for Visual Studio 2013 Release Notes](/aspnet/visual-studio/overview/2013/release-notes).</span></span>

<a name="v45"></a>

## <a name="whats-new-in-net-framework-45"></a><span data-ttu-id="87f14-1105">Co je nového v .NET Framework 4,5</span><span class="sxs-lookup"><span data-stu-id="87f14-1105">What's new in .NET Framework 4.5</span></span>

### <a name="base-classes"></a><span data-ttu-id="87f14-1106">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="87f14-1106">Base classes</span></span>

- <span data-ttu-id="87f14-1107">Schopnost snížit restart systému tím, že během nasazení detekuje a zavírá aplikace .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="87f14-1107">Ability to reduce system restarts by detecting and closing .NET Framework 4 applications during deployment.</span></span> <span data-ttu-id="87f14-1108">Viz [snížení počtu restartování systému během instalace .NET Framework 4,5](../deployment/reducing-system-restarts.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-1108">See [Reducing System Restarts During .NET Framework 4.5 Installations](../deployment/reducing-system-restarts.md).</span></span>

- <span data-ttu-id="87f14-1109">Podpora pro pole, která jsou větší než 2 gigabajty (GB) na 64-bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="87f14-1109">Support for arrays that are larger than 2 gigabytes (GB) on 64-bit platforms.</span></span> <span data-ttu-id="87f14-1110">Tato funkce se dá povolit v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="87f14-1110">This feature can be enabled in the application configuration file.</span></span> <span data-ttu-id="87f14-1111">Podívejte se na [ \<gcAllowVeryLargeObjects> element](../configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md), který také obsahuje další omezení velikosti objektu a velikosti pole.</span><span class="sxs-lookup"><span data-stu-id="87f14-1111">See the [\<gcAllowVeryLargeObjects> element](../configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md), which also lists other restrictions on object size and array size.</span></span>

- <span data-ttu-id="87f14-1112">Lepší výkon při uvolňování paměti na pozadí pro servery.</span><span class="sxs-lookup"><span data-stu-id="87f14-1112">Better performance through background garbage collection for servers.</span></span> <span data-ttu-id="87f14-1113">Pokud používáte systém uvolňování paměti serveru v .NET Framework 4,5, automatické uvolňování paměti na pozadí je povoleno.</span><span class="sxs-lookup"><span data-stu-id="87f14-1113">When you use server garbage collection in the .NET Framework 4.5, background garbage collection is automatically enabled.</span></span> <span data-ttu-id="87f14-1114">V tématu [základní informace o uvolňování paměti](../../standard/garbage-collection/fundamentals.md) najdete v části uvolňování paměti serveru na pozadí.</span><span class="sxs-lookup"><span data-stu-id="87f14-1114">See the Background Server Garbage Collection section of the [Fundamentals of Garbage Collection](../../standard/garbage-collection/fundamentals.md) topic.</span></span>

- <span data-ttu-id="87f14-1115">Kompilace JIT (just-in-time), která je volitelně dostupná pro procesory s více jádry ke zlepšení výkonu aplikace.</span><span class="sxs-lookup"><span data-stu-id="87f14-1115">Background just-in-time (JIT) compilation, which is optionally available on multi-core processors to improve application performance.</span></span> <span data-ttu-id="87f14-1116">Viz třída <xref:System.Runtime.ProfileOptimization>.</span><span class="sxs-lookup"><span data-stu-id="87f14-1116">See <xref:System.Runtime.ProfileOptimization>.</span></span>

- <span data-ttu-id="87f14-1117">Možnost omezit dobu, po kterou se modul regulárních výrazů pokusí přeložit regulární výraz předtím, než vyprší jeho časový limit. Podívejte se na <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="87f14-1117">Ability to limit how long the regular expression engine will attempt to resolve a regular expression before it times out. See the <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=nameWithType> property.</span></span>

- <span data-ttu-id="87f14-1118">Možnost definovat výchozí jazykovou verzi pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="87f14-1118">Ability to define the default culture for an application domain.</span></span> <span data-ttu-id="87f14-1119">Podívejte se na <xref:System.Globalization.CultureInfo> třídu.</span><span class="sxs-lookup"><span data-stu-id="87f14-1119">See the <xref:System.Globalization.CultureInfo> class.</span></span>

- <span data-ttu-id="87f14-1120">Podpora konzoly pro kódování Unicode (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="87f14-1120">Console support for Unicode (UTF-16) encoding.</span></span> <span data-ttu-id="87f14-1121">Podívejte se na <xref:System.Console> třídu.</span><span class="sxs-lookup"><span data-stu-id="87f14-1121">See the <xref:System.Console> class.</span></span>

- <span data-ttu-id="87f14-1122">Podpora správy verzí pro kulturní řazení řetězců a porovnávání dat.</span><span class="sxs-lookup"><span data-stu-id="87f14-1122">Support for versioning of cultural string ordering and comparison data.</span></span> <span data-ttu-id="87f14-1123">Podívejte se na <xref:System.Globalization.SortVersion> třídu.</span><span class="sxs-lookup"><span data-stu-id="87f14-1123">See the <xref:System.Globalization.SortVersion> class.</span></span>

- <span data-ttu-id="87f14-1124">Lepší výkon při načítání prostředků.</span><span class="sxs-lookup"><span data-stu-id="87f14-1124">Better performance when retrieving resources.</span></span> <span data-ttu-id="87f14-1125">Viz [balení a nasazení prostředků](../resources/packaging-and-deploying-resources-in-desktop-apps.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-1125">See [Packaging and Deploying Resources](../resources/packaging-and-deploying-resources-in-desktop-apps.md).</span></span>

- <span data-ttu-id="87f14-1126">Vylepšení komprese zip ke zmenšení velikosti komprimovaného souboru.</span><span class="sxs-lookup"><span data-stu-id="87f14-1126">Zip compression improvements to reduce the size of a compressed file.</span></span> <span data-ttu-id="87f14-1127">Viz <xref:System.IO.Compression?displayProperty=nameWithType> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="87f14-1127">See the <xref:System.IO.Compression?displayProperty=nameWithType> namespace.</span></span>

- <span data-ttu-id="87f14-1128">Možnost přizpůsobit kontext reflexe pro přepsání výchozího chování reflexe prostřednictvím <xref:System.Reflection.Context.CustomReflectionContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="87f14-1128">Ability to customize a reflection context to override default reflection behavior through the <xref:System.Reflection.Context.CustomReflectionContext> class.</span></span>

- <span data-ttu-id="87f14-1129">Podpora verze 2008 mezinárodních názvů domén v aplikacích (IDNA) standard, pokud <xref:System.Globalization.IdnMapping?displayProperty=nameWithType> je třída použita ve Windows 8.</span><span class="sxs-lookup"><span data-stu-id="87f14-1129">Support for the 2008 version of the Internationalized Domain Names in Applications (IDNA) standard when the <xref:System.Globalization.IdnMapping?displayProperty=nameWithType> class is used  on Windows 8.</span></span>

- <span data-ttu-id="87f14-1130">Delegování porovnání řetězců k operačnímu systému, které implementuje kódování Unicode 6,0, pokud je .NET Framework použito v systému Windows 8.</span><span class="sxs-lookup"><span data-stu-id="87f14-1130">Delegation of string comparison to the operating system, which implements Unicode 6.0, when the .NET Framework is used on Windows 8.</span></span> <span data-ttu-id="87f14-1131">Při spuštění na jiných platformách .NET Framework zahrnuje vlastní data porovnání řetězců, která implementují Unicode 5. x.</span><span class="sxs-lookup"><span data-stu-id="87f14-1131">When running on other platforms, the .NET Framework includes its own string comparison data, which implements Unicode 5.x.</span></span> <span data-ttu-id="87f14-1132">Podívejte se na <xref:System.String> třídu a oddíl poznámky <xref:System.Globalization.SortVersion> třídy.</span><span class="sxs-lookup"><span data-stu-id="87f14-1132">See the <xref:System.String> class and the Remarks section of the <xref:System.Globalization.SortVersion> class.</span></span>

- <span data-ttu-id="87f14-1133">Možnost vypočítat kódy hash pro řetězce na základě domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="87f14-1133">Ability to compute the hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="87f14-1134">Viz [ \<UseRandomizedStringHashAlgorithm> element](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-1134">See [\<UseRandomizedStringHashAlgorithm> Element](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).</span></span>

- <span data-ttu-id="87f14-1135">Podpora reflexe typu je rozdělena mezi <xref:System.Type> <xref:System.Reflection.TypeInfo> třídy a.</span><span class="sxs-lookup"><span data-stu-id="87f14-1135">Type reflection support split between <xref:System.Type> and <xref:System.Reflection.TypeInfo> classes.</span></span> <span data-ttu-id="87f14-1136">Podívejte [se na reflexi v .NET Framework pro aplikace pro Windows Store](../reflection-and-codedom/reflection-for-windows-store-apps.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-1136">See [Reflection in the .NET Framework for Windows Store Apps](../reflection-and-codedom/reflection-for-windows-store-apps.md).</span></span>

### <a name="managed-extensibility-framework-mef"></a><span data-ttu-id="87f14-1137">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="87f14-1137">Managed Extensibility Framework (MEF)</span></span>

<span data-ttu-id="87f14-1138">V .NET Framework 4,5 obsahuje Managed Extensibility Framework (MEF) tyto nové funkce:</span><span class="sxs-lookup"><span data-stu-id="87f14-1138">In the .NET Framework 4.5, the Managed Extensibility Framework (MEF) provides the following new features:</span></span>

- <span data-ttu-id="87f14-1139">Podpora pro obecné typy.</span><span class="sxs-lookup"><span data-stu-id="87f14-1139">Support for generic types.</span></span>

- <span data-ttu-id="87f14-1140">Programovací model založený na konvencích, který umožňuje vytvářet části na základě konvencí pojmenování, nikoli atributů.</span><span class="sxs-lookup"><span data-stu-id="87f14-1140">Convention-based programming model that enables you to create parts based on naming conventions rather than attributes.</span></span>

- <span data-ttu-id="87f14-1141">Více oborů.</span><span class="sxs-lookup"><span data-stu-id="87f14-1141">Multiple scopes.</span></span>

- <span data-ttu-id="87f14-1142">Podmnožina MEF, kterou můžete použít při vytváření aplikací pro Windows 8. x Store.</span><span class="sxs-lookup"><span data-stu-id="87f14-1142">A subset of MEF that you can use when you create Windows 8.x Store apps.</span></span> <span data-ttu-id="87f14-1143">Tato podmnožina je k dispozici jako [balíček ke stažení](https://www.nuget.org/packages/Microsoft.Composition) z galerie NuGet.</span><span class="sxs-lookup"><span data-stu-id="87f14-1143">This subset is available as a [downloadable package](https://www.nuget.org/packages/Microsoft.Composition) from the NuGet Gallery.</span></span> <span data-ttu-id="87f14-1144">Pokud chcete balíček nainstalovat, otevřete projekt v aplikaci Visual Studio, v nabídce **projekt** vyberte **Spravovat balíčky NuGet** a vyhledejte `Microsoft.Composition` balíček online.</span><span class="sxs-lookup"><span data-stu-id="87f14-1144">To install the package, open your project in Visual Studio, choose **Manage NuGet Packages** from the **Project** menu, and search online for the `Microsoft.Composition` package.</span></span>

<span data-ttu-id="87f14-1145">Další informace naleznete v tématu [Managed Extensibility Framework (MEF)](../mef/index.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-1145">For more information, see [Managed Extensibility Framework (MEF)](../mef/index.md).</span></span>

### <a name="asynchronous-file-operations"></a><span data-ttu-id="87f14-1146">Asynchronní operace se soubory</span><span class="sxs-lookup"><span data-stu-id="87f14-1146">Asynchronous file operations</span></span>

<span data-ttu-id="87f14-1147">V .NET Framework 4,5 byly do jazyků C# a Visual Basic přidány nové asynchronní funkce.</span><span class="sxs-lookup"><span data-stu-id="87f14-1147">In the .NET Framework 4.5, new asynchronous features were added to the C# and Visual Basic languages.</span></span> <span data-ttu-id="87f14-1148">Tyto funkce přidávají model založený na úlohách pro provádění asynchronních operací.</span><span class="sxs-lookup"><span data-stu-id="87f14-1148">These features add a task-based model for performing asynchronous operations.</span></span> <span data-ttu-id="87f14-1149">Chcete-li použít tento nový model, použijte asynchronní metody v I/O třídách.</span><span class="sxs-lookup"><span data-stu-id="87f14-1149">To use this new model, use the asynchronous methods in the I/O classes.</span></span> <span data-ttu-id="87f14-1150">Viz [asynchronní vstupně-výstupní operace se soubory](../../standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-1150">See [Asynchronous File I/O](../../standard/io/asynchronous-file-i-o.md).</span></span>

<a name="tools"></a>

### <a name="tools"></a><span data-ttu-id="87f14-1151">Nástroje</span><span class="sxs-lookup"><span data-stu-id="87f14-1151">Tools</span></span>

<span data-ttu-id="87f14-1152">V .NET Framework 4,5 vám generátor souborů prostředků (Resgen.exe) umožňuje vytvořit soubor. resw pro použití v aplikacích Windows 8. x Store ze souboru. Resources vloženého do sestavení .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="87f14-1152">In the .NET Framework 4.5, Resource File Generator (Resgen.exe) enables you to create a .resw file for use in Windows 8.x Store apps from a .resources file embedded in a .NET Framework assembly.</span></span> <span data-ttu-id="87f14-1153">Další informace najdete v tématu [Resgen.exe (generátor zdrojového souboru)](../tools/resgen-exe-resource-file-generator.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-1153">For more information, see [Resgen.exe (Resource File Generator)](../tools/resgen-exe-resource-file-generator.md).</span></span>

<span data-ttu-id="87f14-1154">Spravovaná optimalizace na základě profilu (Mpgo.exe) umožňuje zlepšit dobu spuštění aplikace, využití paměti (velikost pracovní sady) a propustnost optimalizací sestavení nativních imagí.</span><span class="sxs-lookup"><span data-stu-id="87f14-1154">Managed Profile Guided Optimization (Mpgo.exe) enables you to improve application startup time, memory utilization (working set size), and throughput by optimizing native image assemblies.</span></span> <span data-ttu-id="87f14-1155">Nástroj příkazového řádku generuje data profilu pro sestavení aplikace nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="87f14-1155">The command-line tool generates profile data for native image application assemblies.</span></span> <span data-ttu-id="87f14-1156">Viz [Mpgo.exe (Nástroj pro optimalizaci spravovaného profilu)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-1156">See [Mpgo.exe (Managed Profile Guided Optimization Tool)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md).</span></span> <span data-ttu-id="87f14-1157">Počínaje Visual Studio 2013 můžete použít Mpgo.exe k optimalizaci aplikací pro Store Windows 8. x a desktopových aplikací.</span><span class="sxs-lookup"><span data-stu-id="87f14-1157">Starting with Visual Studio 2013, you can use Mpgo.exe to optimize Windows 8.x Store apps as well as desktop apps.</span></span>

<a name="parallel"></a>

### <a name="parallel-computing"></a><span data-ttu-id="87f14-1158">Paralelní výpočetní prostředí</span><span class="sxs-lookup"><span data-stu-id="87f14-1158">Parallel computing</span></span>

<span data-ttu-id="87f14-1159">.NET Framework 4,5 obsahuje několik nových funkcí a vylepšení paralelního zpracování.</span><span class="sxs-lookup"><span data-stu-id="87f14-1159">The .NET Framework 4.5 provides several new features and improvements for parallel computing.</span></span> <span data-ttu-id="87f14-1160">Mezi ně patří Vylepšený výkon, zvýšené řízení, vylepšená podpora pro asynchronní programování, nová knihovna toku dat a vylepšená podpora pro paralelní ladění a analýzu výkonu.</span><span class="sxs-lookup"><span data-stu-id="87f14-1160">These include improved performance, increased control, improved support for asynchronous programming, a new dataflow library, and improved support for parallel debugging and performance analysis.</span></span> <span data-ttu-id="87f14-1161">Informace o [tom, co je nového pro paralelismus v .net 4,5](https://devblogs.microsoft.com/pfxteam/whats-new-for-parallelism-in-net-4-5/) , najdete v blogu věnovaném paralelnímu programování pomocí .NET.</span><span class="sxs-lookup"><span data-stu-id="87f14-1161">See the entry [What's New for Parallelism in .NET 4.5](https://devblogs.microsoft.com/pfxteam/whats-new-for-parallelism-in-net-4-5/) in the Parallel Programming with .NET blog.</span></span>

<a name="web"></a>

### <a name="web"></a><span data-ttu-id="87f14-1162">Web</span><span class="sxs-lookup"><span data-stu-id="87f14-1162">Web</span></span>

<span data-ttu-id="87f14-1163">ASP.NET 4,5 a 4.5.1 přidávají vazbu modelu pro webové formuláře, podporu WebSocket, asynchronní obslužné rutiny, vylepšení výkonu a mnoho dalších funkcí.</span><span class="sxs-lookup"><span data-stu-id="87f14-1163">ASP.NET 4.5 and 4.5.1 add model binding for Web Forms, WebSocket support, asynchronous handlers, performance enhancements, and many other features.</span></span> <span data-ttu-id="87f14-1164">Další informace naleznete v následujících zdrojích:</span><span class="sxs-lookup"><span data-stu-id="87f14-1164">For more information, see the following resources:</span></span>

- <span data-ttu-id="87f14-1165">[ASP.NET 4,5 a Visual Studio 2012](https://docs.microsoft.com/previous-versions/aspnet/hh420390(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="87f14-1165">[ASP.NET 4.5 and Visual Studio 2012](https://docs.microsoft.com/previous-versions/aspnet/hh420390(v=vs.110))</span></span>

- [<span data-ttu-id="87f14-1166">ASP.NET a webové nástroje pro Visual Studio 2013 – poznámky k verzi</span><span class="sxs-lookup"><span data-stu-id="87f14-1166">ASP.NET and Web Tools for Visual Studio 2013 Release Notes</span></span>](/aspnet/visual-studio/overview/2013/release-notes)

### <a name="networking"></a><span data-ttu-id="87f14-1167">Sítě<a name="networking"></a></span><span class="sxs-lookup"><span data-stu-id="87f14-1167">Networking <a name="networking"></a></span></span>

<span data-ttu-id="87f14-1168">.NET Framework 4,5 poskytuje nové programovací rozhraní pro aplikace HTTP.</span><span class="sxs-lookup"><span data-stu-id="87f14-1168">The .NET Framework 4.5 provides a new programming interface for HTTP applications.</span></span> <span data-ttu-id="87f14-1169">Další informace najdete v tématu nové <xref:System.Net.Http?displayProperty=nameWithType> <xref:System.Net.Http.Headers?displayProperty=nameWithType> obory názvů a.</span><span class="sxs-lookup"><span data-stu-id="87f14-1169">For more information, see the new <xref:System.Net.Http?displayProperty=nameWithType> and <xref:System.Net.Http.Headers?displayProperty=nameWithType> namespaces.</span></span>

<span data-ttu-id="87f14-1170">Podpora je také k dispozici pro nové programovací rozhraní pro příjem a interakci s připojením protokolu WebSocket pomocí existující <xref:System.Net.HttpListener> a související třídy.</span><span class="sxs-lookup"><span data-stu-id="87f14-1170">Support is also included for a new programming interface for accepting and interacting with a WebSocket connection by using the existing <xref:System.Net.HttpListener> and related classes.</span></span> <span data-ttu-id="87f14-1171">Další informace naleznete v tématu nový <xref:System.Net.WebSockets> obor názvů a <xref:System.Net.HttpListener> Třída.</span><span class="sxs-lookup"><span data-stu-id="87f14-1171">For more information, see the new <xref:System.Net.WebSockets> namespace and the <xref:System.Net.HttpListener> class.</span></span>

<span data-ttu-id="87f14-1172">Kromě toho .NET Framework 4,5 zahrnuje následující vylepšení sítě:</span><span class="sxs-lookup"><span data-stu-id="87f14-1172">In addition, the .NET Framework 4.5 includes the following networking improvements:</span></span>

- <span data-ttu-id="87f14-1173">Podpora identifikátoru URI kompatibilního se specifikací RFC.</span><span class="sxs-lookup"><span data-stu-id="87f14-1173">RFC-compliant URI support.</span></span> <span data-ttu-id="87f14-1174">Další informace naleznete v tématu <xref:System.Uri> a související třídy.</span><span class="sxs-lookup"><span data-stu-id="87f14-1174">For more information, see <xref:System.Uri> and related classes.</span></span>

- <span data-ttu-id="87f14-1175">Podpora pro analýzu mezinárodních názvů domén (IDN).</span><span class="sxs-lookup"><span data-stu-id="87f14-1175">Support for Internationalized Domain Name (IDN) parsing.</span></span> <span data-ttu-id="87f14-1176">Další informace naleznete v tématu <xref:System.Uri> a související třídy.</span><span class="sxs-lookup"><span data-stu-id="87f14-1176">For more information, see <xref:System.Uri> and related classes.</span></span>

- <span data-ttu-id="87f14-1177">Podpora mezinárodní adresy e-mailové adresy (EAI).</span><span class="sxs-lookup"><span data-stu-id="87f14-1177">Support for Email Address Internationalization (EAI).</span></span> <span data-ttu-id="87f14-1178">Další informace najdete v tématu <xref:System.Net.Mail> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="87f14-1178">For more information, see the <xref:System.Net.Mail> namespace.</span></span>

- <span data-ttu-id="87f14-1179">Vylepšená podpora protokolu IPv6.</span><span class="sxs-lookup"><span data-stu-id="87f14-1179">Improved IPv6 support.</span></span> <span data-ttu-id="87f14-1180">Další informace najdete v tématu <xref:System.Net.NetworkInformation> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="87f14-1180">For more information, see the <xref:System.Net.NetworkInformation> namespace.</span></span>

- <span data-ttu-id="87f14-1181">Podpora soketu s duálním režimem.</span><span class="sxs-lookup"><span data-stu-id="87f14-1181">Dual-mode socket support.</span></span> <span data-ttu-id="87f14-1182">Další informace naleznete v tématu <xref:System.Net.Sockets.Socket> třídy a <xref:System.Net.Sockets.TcpListener> .</span><span class="sxs-lookup"><span data-stu-id="87f14-1182">For more information, see the <xref:System.Net.Sockets.Socket> and <xref:System.Net.Sockets.TcpListener> classes.</span></span>

<a name="client"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="87f14-1183">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="87f14-1183">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="87f14-1184">V .NET Framework 4,5 Windows Presentation Foundation (WPF) obsahuje změny a vylepšení v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="87f14-1184">In the .NET Framework 4.5, Windows Presentation Foundation (WPF) contains changes and improvements in the following areas:</span></span>

- <span data-ttu-id="87f14-1185">Nový <xref:System.Windows.Controls.Ribbon.Ribbon> ovládací prvek, který umožňuje implementovat uživatelské rozhraní pásu karet, které je hostitelem panelu nástrojů pro rychlý přístup, nabídky aplikace a karet.</span><span class="sxs-lookup"><span data-stu-id="87f14-1185">The new <xref:System.Windows.Controls.Ribbon.Ribbon> control, which enables you to implement a ribbon user interface that hosts a Quick Access Toolbar, Application Menu, and tabs.</span></span>

- <span data-ttu-id="87f14-1186">Nové <xref:System.ComponentModel.INotifyDataErrorInfo> rozhraní, které podporuje synchronní a asynchronní ověřování dat.</span><span class="sxs-lookup"><span data-stu-id="87f14-1186">The new <xref:System.ComponentModel.INotifyDataErrorInfo> interface, which supports synchronous and asynchronous data validation.</span></span>

- <span data-ttu-id="87f14-1187">Nové funkce pro <xref:System.Windows.Controls.VirtualizingPanel> třídy a <xref:System.Windows.Threading.Dispatcher> .</span><span class="sxs-lookup"><span data-stu-id="87f14-1187">New features for the <xref:System.Windows.Controls.VirtualizingPanel> and <xref:System.Windows.Threading.Dispatcher> classes.</span></span>

- <span data-ttu-id="87f14-1188">Vylepšený výkon při zobrazování rozsáhlých sad seskupených dat a přístup k kolekcím na vláknech, která nejsou v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="87f14-1188">Improved performance when displaying large sets of grouped data, and by accessing collections on non-UI threads.</span></span>

- <span data-ttu-id="87f14-1189">Vázání dat na statické vlastnosti, datové vazby na vlastní typy, které implementují <xref:System.Reflection.ICustomTypeProvider> rozhraní a načítání informací o vazbách dat z výrazu vazby.</span><span class="sxs-lookup"><span data-stu-id="87f14-1189">Data binding to static properties, data binding to custom types that implement the <xref:System.Reflection.ICustomTypeProvider> interface, and retrieval of data binding information from a binding expression.</span></span>

- <span data-ttu-id="87f14-1190">Změna umístění dat při změně hodnot (živé tvarování).</span><span class="sxs-lookup"><span data-stu-id="87f14-1190">Repositioning of data as the values change (live shaping).</span></span>

- <span data-ttu-id="87f14-1191">Možnost kontrolovat, zda je kontext dat pro kontejner položek odpojen.</span><span class="sxs-lookup"><span data-stu-id="87f14-1191">Ability to check whether the data context for an item container is disconnected.</span></span>

- <span data-ttu-id="87f14-1192">Možnost nastavit dobu, která má uplynout mezi změnami vlastností a aktualizacemi zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="87f14-1192">Ability to set the amount of time that should elapse between property changes and data source updates.</span></span>

- <span data-ttu-id="87f14-1193">Vylepšená podpora pro implementaci slabých vzorů událostí.</span><span class="sxs-lookup"><span data-stu-id="87f14-1193">Improved support for implementing weak event patterns.</span></span> <span data-ttu-id="87f14-1194">Události nyní také mohou přijímat rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="87f14-1194">Also, events can now accept markup extensions.</span></span>

<a name="windows_communication_foundation"></a>

### <a name="windows-communication-foundation-wcf"></a><span data-ttu-id="87f14-1195">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="87f14-1195">Windows Communication Foundation (WCF)</span></span>

<span data-ttu-id="87f14-1196">V .NET Framework 4,5 byly přidány následující funkce, které zjednodušují psaní a údržbu aplikací Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="87f14-1196">In the .NET Framework 4.5, the following features have been added to make it simpler to write and maintain Windows Communication Foundation (WCF) applications:</span></span>

- <span data-ttu-id="87f14-1197">Zjednodušení generovaných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="87f14-1197">Simplification of generated configuration files.</span></span>

- <span data-ttu-id="87f14-1198">Podpora vývoje pro první kontrakt.</span><span class="sxs-lookup"><span data-stu-id="87f14-1198">Support for contract-first development.</span></span>

- <span data-ttu-id="87f14-1199">Možnost snazší konfigurace režimu kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="87f14-1199">Ability to configure ASP.NET compatibility mode more easily.</span></span>

- <span data-ttu-id="87f14-1200">Změny ve výchozích hodnotách vlastností přenosu snižují pravděpodobnost, že je budete muset nastavit.</span><span class="sxs-lookup"><span data-stu-id="87f14-1200">Changes in default transport property values to reduce the likelihood that you will have to set them.</span></span>

- <span data-ttu-id="87f14-1201">Aktualizuje <xref:System.Xml.XmlDictionaryReaderQuotas> třídu, aby se snížila pravděpodobnost, že bude nutné ručně nakonfigurovat kvóty pro čtečky slovníku XML.</span><span class="sxs-lookup"><span data-stu-id="87f14-1201">Updates to the <xref:System.Xml.XmlDictionaryReaderQuotas> class to reduce the likelihood that you will have to manually configure quotas for XML dictionary readers.</span></span>

- <span data-ttu-id="87f14-1202">Ověření konfiguračních souborů WCF nástrojem Visual Studio v rámci procesu sestavení, aby bylo možné zjistit chyby konfigurace před spuštěním aplikace.</span><span class="sxs-lookup"><span data-stu-id="87f14-1202">Validation of WCF configuration files by Visual Studio as part of the build process, so you can detect configuration errors before you run your application.</span></span>

- <span data-ttu-id="87f14-1203">Nová podpora asynchronního streamování.</span><span class="sxs-lookup"><span data-stu-id="87f14-1203">New asynchronous streaming support.</span></span>

- <span data-ttu-id="87f14-1204">Nové mapování protokolu HTTPS, které usnadňuje vystavení koncového bodu přes HTTPS pomocí Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="87f14-1204">New HTTPS protocol mapping to make it easier to expose an endpoint over HTTPS with Internet Information Services (IIS).</span></span>

- <span data-ttu-id="87f14-1205">Možnost generovat metadata v jednom dokumentu WSDL připojením `?singleWSDL` k adrese URL služby.</span><span class="sxs-lookup"><span data-stu-id="87f14-1205">Ability to generate metadata in a single WSDL document by appending `?singleWSDL` to the service URL.</span></span>

- <span data-ttu-id="87f14-1206">Podpora WebSockets podporuje true obousměrnou komunikaci přes porty 80 a 443 s charakteristikami výkonu podobným přenosu protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="87f14-1206">Websockets support to enable true bidirectional communication over ports 80 and 443 with performance characteristics similar to the TCP transport.</span></span>

- <span data-ttu-id="87f14-1207">Podpora konfigurace služeb v kódu.</span><span class="sxs-lookup"><span data-stu-id="87f14-1207">Support for configuring services in code.</span></span>

- <span data-ttu-id="87f14-1208">Popisy editoru XML.</span><span class="sxs-lookup"><span data-stu-id="87f14-1208">XML Editor tooltips.</span></span>

- <span data-ttu-id="87f14-1209"><xref:System.ServiceModel.ChannelFactory>Podpora ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="87f14-1209"><xref:System.ServiceModel.ChannelFactory> caching support.</span></span>

- <span data-ttu-id="87f14-1210">Podpora komprese binárního kodéru</span><span class="sxs-lookup"><span data-stu-id="87f14-1210">Binary encoder compression support.</span></span>

- <span data-ttu-id="87f14-1211">Podpora pro přenos UDP, který vývojářům umožňuje psát služby, které používají zprávy "oheň a zapomenout".</span><span class="sxs-lookup"><span data-stu-id="87f14-1211">Support for a UDP transport that enables developers to write services that use "fire and forget" messaging.</span></span> <span data-ttu-id="87f14-1212">Klient pošle zprávu službě a neočekává odpověď ze služby.</span><span class="sxs-lookup"><span data-stu-id="87f14-1212">A client sends a message to a service and expects no response from the service.</span></span>

- <span data-ttu-id="87f14-1213">Možnost podporovat více režimů ověřování na jednom koncovém bodu WCF při použití přenosu protokolu HTTP a zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="87f14-1213">Ability to support multiple authentication modes on a single WCF endpoint when using the HTTP transport and transport security.</span></span>

- <span data-ttu-id="87f14-1214">Podpora služeb WCF, které používají mezinárodní názvy domén (IDN).</span><span class="sxs-lookup"><span data-stu-id="87f14-1214">Support for WCF services that use internationalized domain names (IDNs).</span></span>

<span data-ttu-id="87f14-1215">Další informace najdete v tématu [co je nového v Windows Communication Foundation](../wcf/whats-new.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-1215">For more information, see [What's New in Windows Communication Foundation](../wcf/whats-new.md).</span></span>

<a name="windows_workflow_foundation"></a>

### <a name="windows-workflow-foundation-wf"></a><span data-ttu-id="87f14-1216">Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="87f14-1216">Windows Workflow Foundation (WF)</span></span>

<span data-ttu-id="87f14-1217">V .NET Framework 4,5 byly do programovací model Windows Workflow Foundation (WF) přidány některé nové funkce, včetně těchto:</span><span class="sxs-lookup"><span data-stu-id="87f14-1217">In the .NET Framework 4.5, several new features were added to Windows Workflow Foundation (WF), including:</span></span>

- <span data-ttu-id="87f14-1218">Pracovní postupy stavového stroje, které byly poprvé představeny jako součást .NET Framework 4.0.1 ([.NET Framework 4 Platform Update 1](https://docs.microsoft.com/archive/blogs/endpoint/microsoft-net-framework-4-platform-update-1)).</span><span class="sxs-lookup"><span data-stu-id="87f14-1218">State machine workflows, which were first introduced as part of .NET Framework 4.0.1 ([.NET Framework 4 Platform Update 1](https://docs.microsoft.com/archive/blogs/endpoint/microsoft-net-framework-4-platform-update-1)).</span></span> <span data-ttu-id="87f14-1219">Tato aktualizace obsahuje několik nových tříd a aktivit, které vývojářům umožnili vytvářet pracovní postupy stavového počítače.</span><span class="sxs-lookup"><span data-stu-id="87f14-1219">This update included several new classes and activities that enabled developers to create state machine workflows.</span></span> <span data-ttu-id="87f14-1220">Tyto třídy a aktivity byly aktualizovány, aby .NET Framework 4,5 zahrnovaly:</span><span class="sxs-lookup"><span data-stu-id="87f14-1220">These classes and activities were updated for the .NET Framework 4.5 to include:</span></span>

  - <span data-ttu-id="87f14-1221">Možnost nastavovat zarážky na stavech.</span><span class="sxs-lookup"><span data-stu-id="87f14-1221">The ability to set breakpoints on states.</span></span>

  - <span data-ttu-id="87f14-1222">Možnost Kopírovat a vkládat přechody v Návrháři postupu.</span><span class="sxs-lookup"><span data-stu-id="87f14-1222">The ability to copy and paste transitions in the workflow designer.</span></span>

  - <span data-ttu-id="87f14-1223">Podpora návrháře pro vytvoření přechodu na sdílené triggery</span><span class="sxs-lookup"><span data-stu-id="87f14-1223">Designer support for shared trigger transition creation.</span></span>

  - <span data-ttu-id="87f14-1224">Aktivity pro vytváření pracovních postupů stavového počítače, včetně: <xref:System.Activities.Statements.StateMachine> , <xref:System.Activities.Statements.State> a <xref:System.Activities.Statements.Transition> .</span><span class="sxs-lookup"><span data-stu-id="87f14-1224">Activities for creating state machine workflows, including: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, and <xref:System.Activities.Statements.Transition>.</span></span>

- <span data-ttu-id="87f14-1225">Rozšířené funkce Návrhář postupu provádění, například následující:</span><span class="sxs-lookup"><span data-stu-id="87f14-1225">Enhanced Workflow Designer features such as the following:</span></span>

  - <span data-ttu-id="87f14-1226">Rozšířené možnosti hledání pracovních postupů v aplikaci Visual Studio, včetně **rychlého hledání** a **hledání v souborech**.</span><span class="sxs-lookup"><span data-stu-id="87f14-1226">Enhanced workflow search capabilities in Visual Studio, including **Quick Find** and **Find in Files**.</span></span>

  - <span data-ttu-id="87f14-1227">Schopnost automaticky vytvořit aktivitu sekvence, když se do aktivity kontejneru přidá druhá podřízená aktivita, a zahrnout obě aktivity do aktivity sekvence.</span><span class="sxs-lookup"><span data-stu-id="87f14-1227">Ability to automatically create a Sequence activity when a second child activity is added to a container activity, and to include both activities in the Sequence activity.</span></span>

  - <span data-ttu-id="87f14-1228">Podpora posouvání, která umožňuje změnit viditelnou část pracovního postupu bez použití posuvníků.</span><span class="sxs-lookup"><span data-stu-id="87f14-1228">Panning support, which enables the visible portion of a workflow to be changed without using the scroll bars.</span></span>

  - <span data-ttu-id="87f14-1229">Nové zobrazení **Osnova dokumentu** , které zobrazuje součásti pracovního postupu v zobrazení osnovy ve stylu stromu a umožňuje v zobrazení **Osnova dokumentu** vybrat komponentu.</span><span class="sxs-lookup"><span data-stu-id="87f14-1229">A new **Document Outline** view that shows the components of a workflow in a tree-style outline view and lets you select a component in the **Document Outline** view.</span></span>

  - <span data-ttu-id="87f14-1230">Možnost přidávat poznámky k aktivitám.</span><span class="sxs-lookup"><span data-stu-id="87f14-1230">Ability to add annotations to activities.</span></span>

  - <span data-ttu-id="87f14-1231">Možnost definovat a spotřebovat delegáty aktivit pomocí návrháře pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="87f14-1231">Ability to define and consume activity delegates by using the workflow designer.</span></span>

  - <span data-ttu-id="87f14-1232">Automatické připojení a automatické vložení pro aktivity a přechody v pracovních postupech stavového stroje a vývojového diagramu.</span><span class="sxs-lookup"><span data-stu-id="87f14-1232">Auto-connect and auto-insert for activities and transitions in state machine and flowchart workflows.</span></span>

- <span data-ttu-id="87f14-1233">Úložiště informací o stavu zobrazení pracovního postupu v jednom prvku v souboru XAML, takže můžete snadno vyhledat a upravit informace o stavu zobrazení.</span><span class="sxs-lookup"><span data-stu-id="87f14-1233">Storage of the view state information for a workflow in a single element in the XAML file, so you can easily locate and edit the view state information.</span></span>

- <span data-ttu-id="87f14-1234">Aktivita kontejneru oboru NoPersistScope, která zabraňuje zachování podřízených aktivit.</span><span class="sxs-lookup"><span data-stu-id="87f14-1234">A NoPersistScope container activity to prevent child activities from persisting.</span></span>

- <span data-ttu-id="87f14-1235">Podpora pro výrazy jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="87f14-1235">Support for C# expressions:</span></span>

  - <span data-ttu-id="87f14-1236">Projekty pracovního postupu, které používají Visual Basic, budou používat výrazy Visual Basic a projekty pracovního postupu C# budou používat výrazy jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="87f14-1236">Workflow projects that use Visual Basic will use Visual Basic expressions, and C# workflow projects will use C# expressions.</span></span>

  - <span data-ttu-id="87f14-1237">Projekty pracovního postupu c#, které byly vytvořeny v aplikaci Visual Studio 2010 a které mají Visual Basic výrazy jsou kompatibilní s projekty pracovního postupu C#, které používají výrazy jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="87f14-1237">C# workflow projects that were created in Visual Studio 2010 and that have Visual Basic expressions are compatible with C# workflow projects that use C# expressions.</span></span>

- <span data-ttu-id="87f14-1238">Vylepšení správy verzí:</span><span class="sxs-lookup"><span data-stu-id="87f14-1238">Versioning enhancements:</span></span>

  - <span data-ttu-id="87f14-1239">Nová <xref:System.Activities.WorkflowIdentity> třída, která poskytuje mapování mezi trvalou instancí pracovního postupu a její definicí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="87f14-1239">The new  <xref:System.Activities.WorkflowIdentity> class, which provides a mapping between a persisted workflow instance and its workflow definition.</span></span>

  - <span data-ttu-id="87f14-1240">Souběžné spouštění více verzí pracovních postupů ve stejném hostiteli, včetně <xref:System.ServiceModel.Activities.WorkflowServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="87f14-1240">Side-by-side execution of multiple workflow versions in the same host, including <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>

  - <span data-ttu-id="87f14-1241">V případě dynamické aktualizace je možné změnit definici trvalé instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="87f14-1241">In Dynamic Update, the ability to modify the definition of a persisted workflow instance.</span></span>

- <span data-ttu-id="87f14-1242">Vývoj služby pracovního postupu prvního kontraktu, který poskytuje podporu pro automatické generování aktivit, které se shodují s existující smlouvou služby.</span><span class="sxs-lookup"><span data-stu-id="87f14-1242">Contract-first workflow service development, which provides support for automatically generating activities to match an existing service contract.</span></span>

<span data-ttu-id="87f14-1243">Další informace najdete v tématu [co je nového v programovací model Windows Workflow Foundation](../windows-workflow-foundation/whats-new-in-wf-in-dotnet.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-1243">For more information, see [What's New in Windows Workflow Foundation](../windows-workflow-foundation/whats-new-in-wf-in-dotnet.md).</span></span>

<a name="tailored"></a>

### <a name="net-for-windows-8x-store-apps"></a><span data-ttu-id="87f14-1244">Aplikace .NET pro Windows 8.x Store</span><span class="sxs-lookup"><span data-stu-id="87f14-1244">.NET for Windows 8.x Store apps</span></span>

<span data-ttu-id="87f14-1245">Aplikace pro Store ve Windows 8. x jsou navržené pro konkrétní faktory a využívají sílu operačního systému Windows.</span><span class="sxs-lookup"><span data-stu-id="87f14-1245">Windows 8.x Store apps are designed for specific form factors and leverage the power of the Windows operating system.</span></span> <span data-ttu-id="87f14-1246">K dispozici je podmnožina .NET Framework 4,5 nebo 4.5.1 pro sestavování aplikací Windows 8. x Store pro Windows pomocí jazyka C# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="87f14-1246">A subset of the .NET Framework 4.5 or 4.5.1 is available for building Windows 8.x Store apps for Windows by using C# or Visual Basic.</span></span> <span data-ttu-id="87f14-1247">Tato podmnožina se nazývá .NET pro aplikace Windows 8. x Store a je popsána v [přehledu](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)).</span><span class="sxs-lookup"><span data-stu-id="87f14-1247">This subset is called .NET for Windows 8.x Store apps and is discussed in an [overview](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)).</span></span>

### <a name="portable-class-libraries"></a><span data-ttu-id="87f14-1248">Přenositelné knihovny tříd<a name="portable"></a></span><span class="sxs-lookup"><span data-stu-id="87f14-1248">Portable Class Libraries <a name="portable"></a></span></span>

<span data-ttu-id="87f14-1249">Přenosná knihovna tříd projektu v aplikaci Visual Studio 2012 (a novějších verzích) umožňuje psát a sestavovat spravovaná sestavení, která fungují na více .NET Framework platformách.</span><span class="sxs-lookup"><span data-stu-id="87f14-1249">The Portable Class Library project in Visual Studio 2012 (and later versions) enables you to write and build managed assemblies that work on multiple .NET Framework platforms.</span></span> <span data-ttu-id="87f14-1250">Pomocí přenositelného projektu knihovny tříd zvolíte platformy (například Windows Phone a .NET pro aplikace pro Windows 8. x Store) k cíli.</span><span class="sxs-lookup"><span data-stu-id="87f14-1250">Using a Portable Class Library project, you choose the platforms (such as Windows Phone and .NET for Windows 8.x Store apps) to target.</span></span> <span data-ttu-id="87f14-1251">Dostupné typy a členy v projektu jsou automaticky omezeny na společné typy a členy napříč těmito platformami.</span><span class="sxs-lookup"><span data-stu-id="87f14-1251">The available types and members in your project are automatically restricted to the common types and members across these platforms.</span></span> <span data-ttu-id="87f14-1252">Další informace naleznete v tématu [Přenosná knihovna tříd](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).</span><span class="sxs-lookup"><span data-stu-id="87f14-1252">For more information, see [Portable Class Library](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="87f14-1253">Viz také</span><span class="sxs-lookup"><span data-stu-id="87f14-1253">See also</span></span>

- [<span data-ttu-id="87f14-1254">Rozhraní .NET Framework a nesvázaná vydání</span><span class="sxs-lookup"><span data-stu-id="87f14-1254">The .NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
- [<span data-ttu-id="87f14-1255">Co je nového v přístupnosti v .NET Framework</span><span class="sxs-lookup"><span data-stu-id="87f14-1255">What's new in accessibility in the .NET Framework</span></span>](whats-new-in-accessibility.md)
- [<span data-ttu-id="87f14-1256">Co je nového v aplikaci Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="87f14-1256">What's New in Visual Studio 2017</span></span>](/visualstudio/ide/whats-new-visual-studio-2017)
- [<span data-ttu-id="87f14-1257">Novinky v sadě Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="87f14-1257">What's New in Visual Studio 2019</span></span>](/visualstudio/ide/whats-new-visual-studio-2019)
- [<span data-ttu-id="87f14-1258">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="87f14-1258">ASP.NET</span></span>](/aspnet)
- [<span data-ttu-id="87f14-1259">Co je nového v jazyce C++ v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="87f14-1259">What's New for C++ in Visual Studio</span></span>](/cpp/what-s-new-for-visual-cpp-in-visual-studio)
