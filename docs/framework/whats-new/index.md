---
title: Co je nového v .NET Framework
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.assetid: 1d971dd7-10fc-4692-8dac-30ca308fc0fa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3acfa0da0caa29b503f47f23b0e9042d73ef0657
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353387"
---
# <a name="whats-new-in-the-net-framework"></a><span data-ttu-id="fcb44-102">Co je nového v .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fcb44-102">What's new in the .NET Framework</span></span>

<span data-ttu-id="fcb44-103">Tento článek shrnuje klíčové nové funkce a vylepšení v následujících verzích .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="fcb44-103">This article summarizes key new features and improvements in the following versions of the .NET Framework:</span></span>

- [<span data-ttu-id="fcb44-104">.NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="fcb44-104">.NET Framework 4.8</span></span>](#v48)
- [<span data-ttu-id="fcb44-105">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="fcb44-105">.NET Framework 4.7.2</span></span>](#v472)
- [<span data-ttu-id="fcb44-106">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="fcb44-106">.NET Framework 4.7.1</span></span>](#v471)
- [<span data-ttu-id="fcb44-107">.NET Framework 4,7</span><span class="sxs-lookup"><span data-stu-id="fcb44-107">.NET Framework 4.7</span></span>](#v47)
- [<span data-ttu-id="fcb44-108">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="fcb44-108">.NET Framework 4.6.2</span></span>](#v462)
- [<span data-ttu-id="fcb44-109">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="fcb44-109">.NET Framework 4.6.1</span></span>](#v461)
- [<span data-ttu-id="fcb44-110">.NET 2015 a .NET Framework 4,6</span><span class="sxs-lookup"><span data-stu-id="fcb44-110">.NET 2015 and .NET Framework 4.6</span></span>](#v46)
- [<span data-ttu-id="fcb44-111">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="fcb44-111">.NET Framework 4.5.2</span></span>](#v452)
- [<span data-ttu-id="fcb44-112">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="fcb44-112">.NET Framework 4.5.1</span></span>](#v451)
- [<span data-ttu-id="fcb44-113">.NET Framework 4,5</span><span class="sxs-lookup"><span data-stu-id="fcb44-113">.NET Framework 4.5</span></span>](#v45)

<span data-ttu-id="fcb44-114">Tento článek neposkytuje úplné informace o každé nové funkci a může se změnit.</span><span class="sxs-lookup"><span data-stu-id="fcb44-114">This article does not provide comprehensive information about each new feature and is subject to change.</span></span> <span data-ttu-id="fcb44-115">Obecné informace o .NET Framework najdete v tématu [Začínáme](../get-started/index.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-115">For general information about the .NET Framework, see [Getting Started](../get-started/index.md).</span></span> <span data-ttu-id="fcb44-116">Podporované platformy najdete v tématu [požadavky na systém](../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-116">For supported platforms, see [System Requirements](../get-started/system-requirements.md).</span></span> <span data-ttu-id="fcb44-117">Odkazy na stažení a pokyny k instalaci najdete v [Průvodci instalací](../install/guide-for-developers.md)nástroje.</span><span class="sxs-lookup"><span data-stu-id="fcb44-117">For download links and installation instructions, see [Installation Guide](../install/guide-for-developers.md).</span></span>

> [!NOTE]
> <span data-ttu-id="fcb44-118">.NET Framework tým také uvolní funkce mimo pásmo s nástrojem NuGet, aby rozšířila podporu platforem a zavedla nové funkce, jako jsou neměnné kolekce a typy vektorů s podporou SIMD.</span><span class="sxs-lookup"><span data-stu-id="fcb44-118">The .NET Framework team also releases features out of band with NuGet to expand platform support and to introduce new functionality, such as immutable collections and SIMD-enabled vector types.</span></span> <span data-ttu-id="fcb44-119">Další informace najdete v tématech [Další knihovny tříd a rozhraní API](../additional-apis/index.md) a [.NET Framework a vzdálené verze](../get-started/the-net-framework-and-out-of-band-releases.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-119">For more information, see [Additional Class Libraries and APIs](../additional-apis/index.md) and [The .NET Framework and Out-of-Band Releases](../get-started/the-net-framework-and-out-of-band-releases.md).</span></span>
> <span data-ttu-id="fcb44-120">Podívejte se na [úplný seznam balíčků NuGet](https://www.nuget.org/profiles/dotnetframework) pro .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fcb44-120">See a [complete list of NuGet packages](https://www.nuget.org/profiles/dotnetframework) for the .NET Framework.</span></span>

<a name="v48" />

## <a name="introducing-net-framework-48"></a><span data-ttu-id="fcb44-121">Představujeme .NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="fcb44-121">Introducing .NET Framework 4.8</span></span>

<span data-ttu-id="fcb44-122">.NET Framework 4,8 sestaví na předchozích verzích .NET Framework 4. x přidáním mnoha nových oprav a několika nových funkcí a zbývajícím produktem.</span><span class="sxs-lookup"><span data-stu-id="fcb44-122">.NET Framework 4.8 builds on previous versions of the .NET Framework 4.x by adding many new fixes and several new features while remaining a very stable product.</span></span>

### <a name="downloading-and-installing-net-framework-48"></a><span data-ttu-id="fcb44-123">Stažení a instalace .NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="fcb44-123">Downloading and installing .NET Framework 4.8</span></span>

<span data-ttu-id="fcb44-124">.NET Framework 4,8 si můžete stáhnout z těchto umístění:</span><span class="sxs-lookup"><span data-stu-id="fcb44-124">You can download .NET Framework 4.8  from the following locations:</span></span>

- [<span data-ttu-id="fcb44-125">Webová instalační služba .NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="fcb44-125">.NET Framework 4.8 Web Installer</span></span>](https://go.microsoft.com/fwlink/?LinkId=2085155)

- [<span data-ttu-id="fcb44-126">.NET Framework 4,8 – offline instalační program</span><span class="sxs-lookup"><span data-stu-id="fcb44-126">NET Framework 4.8 Offline Installer</span></span>](https://go.microsoft.com/fwlink/?linkid=2088631)

<span data-ttu-id="fcb44-127">.NET Framework 4,8 lze nainstalovat do systému Windows 10, Windows 8.1, Windows 7 SP1 a odpovídajících serverových platforem od verze Windows Server 2008 R2 SP1.</span><span class="sxs-lookup"><span data-stu-id="fcb44-127">.NET Framework 4.8 can be installed on Windows 10, Windows 8.1, Windows 7 SP1, and the corresponding server platforms starting with Windows Server 2008 R2 SP1.</span></span> <span data-ttu-id="fcb44-128">.NET Framework 4,8 můžete nainstalovat buď pomocí webové instalační služby, nebo v offline instalačním programu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-128">You can install .NET Framework 4.8 by using either the web installer or the offline installer.</span></span> <span data-ttu-id="fcb44-129">Doporučeným způsobem pro většinu uživatelů je použití webové instalační služby.</span><span class="sxs-lookup"><span data-stu-id="fcb44-129">The recommended way for most users is to use the web installer.</span></span>

<span data-ttu-id="fcb44-130">Můžete cílit .NET Framework 4,8 v sadě Visual Studio 2012 nebo novější instalací sady [.NET Framework 4,8 Developer Pack](https://go.microsoft.com/fwlink/?LinkId=2085167).</span><span class="sxs-lookup"><span data-stu-id="fcb44-130">You can target .NET Framework 4.8 in Visual Studio 2012 or later by installing the [.NET Framework 4.8 Developer Pack](https://go.microsoft.com/fwlink/?LinkId=2085167).</span></span>

### <a name="whats-new-in-net-framework-48"></a><span data-ttu-id="fcb44-131">Co je nového v .NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="fcb44-131">What's new in .NET Framework 4.8</span></span>

<span data-ttu-id="fcb44-132">.NET Framework 4,8 zavádí nové funkce v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="fcb44-132">.NET Framework 4.8 introduces new features in the following areas:</span></span>

- [<span data-ttu-id="fcb44-133">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="fcb44-133">Base classes</span></span>](#core48)
- [<span data-ttu-id="fcb44-134">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="fcb44-134">Windows Communication Foundation (WCF)</span></span>](#wcf48)
- [<span data-ttu-id="fcb44-135">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="fcb44-135">Windows Presentation Foundation (WPF)</span></span>](#wpf48)
- [<span data-ttu-id="fcb44-136">Modul CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="fcb44-136">Common language runtime</span></span>](#clr48)

<span data-ttu-id="fcb44-137">Vylepšené přístupnost, která aplikaci umožňuje zajistit vhodné prostředí pro uživatele technologie pro usnadnění práce, je nadále hlavním cílem .NET Framework 4,8.</span><span class="sxs-lookup"><span data-stu-id="fcb44-137">Improved accessibility, which allows an application to provide an appropriate experience for users of Assistive Technology, continues to be a major focus of .NET Framework 4.8.</span></span> <span data-ttu-id="fcb44-138">Informace o vylepšeních usnadnění v .NET Framework 4,8 najdete v tématu [co je nového v přístupnosti v .NET Framework](whats-new-in-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-138">For information on accessibility improvements in .NET Framework 4.8, see [What's new in accessibility in the .NET Framework](whats-new-in-accessibility.md).</span></span>

<a name="core48" />

#### <a name="base-classes"></a><span data-ttu-id="fcb44-139">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="fcb44-139">Base classes</span></span>

<span data-ttu-id="fcb44-140">Byl **snížen dopad FIPS na kryptografii**.</span><span class="sxs-lookup"><span data-stu-id="fcb44-140">**Reduced FIPS impact on Cryptography**.</span></span> <span data-ttu-id="fcb44-141">V předchozích verzích .NET Framework spravované třídy zprostředkovatele kryptografických služeb, jako je například <xref:System.Security.Cryptography.SHA256Managed>, vyvolají <xref:System.Security.Cryptography.CryptographicException>, když jsou systémové šifrovací knihovny konfigurovány v režimu FIPS.</span><span class="sxs-lookup"><span data-stu-id="fcb44-141">In previous versions of the .NET Framework, managed cryptographic provider classes such as <xref:System.Security.Cryptography.SHA256Managed> throw a <xref:System.Security.Cryptography.CryptographicException> when the system cryptographic libraries are configured in “FIPS mode”.</span></span> <span data-ttu-id="fcb44-142">Tyto výjimky jsou vyvolány, protože spravované verze tříd zprostředkovatele kryptografických služeb, na rozdíl od systémových kryptografických knihoven, neprošly certifikací FIPS (Federal Information Processing Standards) 140-2.</span><span class="sxs-lookup"><span data-stu-id="fcb44-142">These exceptions are thrown because the managed versions of the cryptographic provider classes, unlike the system cryptographic libraries, have not undergone FIPS (Federal Information Processing Standards) 140-2 certification.</span></span> <span data-ttu-id="fcb44-143">Vzhledem k tomu, že někteří vývojáři mají své vývojové počítače v režimu FIPS, jsou výjimky obvykle vyvolány v produkčních systémech.</span><span class="sxs-lookup"><span data-stu-id="fcb44-143">Because few developers have their development machines in FIPS mode, the exceptions are commonly thrown in production systems.</span></span>

<span data-ttu-id="fcb44-144">Ve výchozím nastavení nejsou v aplikacích, které cílí na .NET Framework 4,8, následující spravované třídy kryptografie již v tomto případě vyvolávat <xref:System.Security.Cryptography.CryptographicException>:</span><span class="sxs-lookup"><span data-stu-id="fcb44-144">By default in applications that target .NET Framework 4.8, the following managed cryptography classes no longer throw a <xref:System.Security.Cryptography.CryptographicException> in this case:</span></span>

- <xref:System.Security.Cryptography.MD5Cng>
- <xref:System.Security.Cryptography.MD5CryptoServiceProvider>
- <xref:System.Security.Cryptography.RC2CryptoServiceProvider>
- <xref:System.Security.Cryptography.RijndaelManaged>
- <xref:System.Security.Cryptography.RIPEMD160Managed>
- <xref:System.Security.Cryptography.SHA256Managed>

<span data-ttu-id="fcb44-145">Místo toho tyto třídy přesměrují kryptografické operace do systémové knihovny kryptografie.</span><span class="sxs-lookup"><span data-stu-id="fcb44-145">Instead, these classes redirect cryptographic operations to a system cryptography library.</span></span> <span data-ttu-id="fcb44-146">Tato změna efektivně odstraňuje potenciálně matoucí rozdíl mezi vývojářskými prostředími a provozními prostředími a zpřístupňuje nativní komponenty a spravované komponenty v rámci stejných kryptografických zásad.</span><span class="sxs-lookup"><span data-stu-id="fcb44-146">This change effectively removes a potentially confusing difference between developer environments and production environments and makes native components and managed components operate under the same cryptographic policy.</span></span> <span data-ttu-id="fcb44-147">Aplikace, které závisí na těchto výjimkách, mohou obnovit předchozí chování nastavením přepínače AppContext `Switch.System.Security.Cryptography.UseLegacyFipsThrow` na `true`.</span><span class="sxs-lookup"><span data-stu-id="fcb44-147">Applications that depend on these exceptions can restore the previous behavior by setting the AppContext switch `Switch.System.Security.Cryptography.UseLegacyFipsThrow` to `true`.</span></span> <span data-ttu-id="fcb44-148">Další informace najdete v tématu [spravované kryptografické třídy nevyvolávají výjimku CryptographyException v režimu FIPS](../migration-guide/retargeting/4.7.2-4.8.md#managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode).</span><span class="sxs-lookup"><span data-stu-id="fcb44-148">For more information, see [Managed cryptography classes do not throw a CryptographyException in FIPS mode](../migration-guide/retargeting/4.7.2-4.8.md#managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode).</span></span>

<span data-ttu-id="fcb44-149">**Použití aktualizované verze ZLib**</span><span class="sxs-lookup"><span data-stu-id="fcb44-149">**Use of updated version of ZLib**</span></span>

<span data-ttu-id="fcb44-150">Počínaje .NET Framework 4,5 používá sestavení clrcompression. dll [ZLib](https://www.zlib.net), nativní externí knihovnu pro kompresi dat, aby bylo možné poskytnout implementaci pro algoritmus deflate.</span><span class="sxs-lookup"><span data-stu-id="fcb44-150">Starting with .NET Framework 4.5, the clrcompression.dll assembly uses [ZLib](https://www.zlib.net), a native external library for data compression, in order to provide an implementation for the deflate algorithm.</span></span> <span data-ttu-id="fcb44-151">.NET Framework 4,8 clrcompression. dll se aktualizuje tak, aby používal ZLib verzi 1.2.11, která zahrnuje několik klíčových vylepšení a oprav.</span><span class="sxs-lookup"><span data-stu-id="fcb44-151">The .NET Framework 4.8, clrcompression.dll is updated to use ZLib Version 1.2.11, which includes several key improvements and fixes.</span></span>

<a name="wcf48" />

#### <a name="windows-communication-foundation-wcf"></a><span data-ttu-id="fcb44-152">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="fcb44-152">Windows Communication Foundation (WCF)</span></span>

<span data-ttu-id="fcb44-153">**Úvod do ServiceHealthBehavior**</span><span class="sxs-lookup"><span data-stu-id="fcb44-153">**Introduction of ServiceHealthBehavior**</span></span>

<span data-ttu-id="fcb44-154">Nástroje pro orchestraci využívají koncové body stavu ke správě služeb na základě jejich stavu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-154">Health endpoints are widely used by orchestration tools to manage services based on their health status.</span></span> <span data-ttu-id="fcb44-155">Kontroly stavu lze také použít pomocí nástrojů pro monitorování ke sledování a poskytování oznámení o dostupnosti a výkonu služby.</span><span class="sxs-lookup"><span data-stu-id="fcb44-155">Health checks can also be used by monitoring tools to track and provide notifications about the availability and performance of a service.</span></span>

<span data-ttu-id="fcb44-156">**ServiceHealthBehavior** je chování služby WCF, které rozšiřuje <xref:System.ServiceModel.Description.IServiceBehavior>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-156">**ServiceHealthBehavior** is a WCF service behavior that extends <xref:System.ServiceModel.Description.IServiceBehavior>.</span></span>  <span data-ttu-id="fcb44-157">Při přidání do kolekce <xref:System.ServiceModel.Description.ServiceDescription.Behaviors?displayProperty=nameWithType> provede chování služby následující akce:</span><span class="sxs-lookup"><span data-stu-id="fcb44-157">When added to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors?displayProperty=nameWithType> collection, a service behavior does the following:</span></span>

- <span data-ttu-id="fcb44-158">Vrátí stav služby s kódy odpovědí HTTP.</span><span class="sxs-lookup"><span data-stu-id="fcb44-158">Returns service health status with HTTP response codes.</span></span> <span data-ttu-id="fcb44-159">V řetězci dotazu můžete zadat stavový kód HTTP pro požadavek na test stavu HTTP/GET.</span><span class="sxs-lookup"><span data-stu-id="fcb44-159">You can specify in a query string the HTTP status code for a HTTP/GET health probe request.</span></span>

- <span data-ttu-id="fcb44-160">Publikuje informace o stavu služby.</span><span class="sxs-lookup"><span data-stu-id="fcb44-160">Publishes information about service health.</span></span> <span data-ttu-id="fcb44-161">Podrobnosti konkrétní služby, včetně stavu služby, počtu omezení a kapacity, se dají zobrazit pomocí požadavku HTTP/GET s řetězcem dotazu `?health`.</span><span class="sxs-lookup"><span data-stu-id="fcb44-161">Service-specific details, including service state, throttle counts, and capacity can be displayed by using an HTTP/GET request with the `?health` query string.</span></span> <span data-ttu-id="fcb44-162">Usnadnění přístupu k těmto informacím je důležité při řešení potíží se službou WCF, která se nechová.</span><span class="sxs-lookup"><span data-stu-id="fcb44-162">Ease of access to such information is important when troubleshooting a misbehaving WCF service.</span></span>

<span data-ttu-id="fcb44-163">Existují dva způsoby, jak vystavit koncový bod stavu a publikovat informace o stavu služby WCF:</span><span class="sxs-lookup"><span data-stu-id="fcb44-163">There are two ways to expose the health endpoint and publish WCF service health information:</span></span>

- <span data-ttu-id="fcb44-164">Prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-164">Through code.</span></span> <span data-ttu-id="fcb44-165">Příklad:</span><span class="sxs-lookup"><span data-stu-id="fcb44-165">For example:</span></span>

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

- <span data-ttu-id="fcb44-166">Pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="fcb44-166">By using a configuration file.</span></span> <span data-ttu-id="fcb44-167">Příklad:</span><span class="sxs-lookup"><span data-stu-id="fcb44-167">For example:</span></span>

  ```xml
  <behaviors>
    <serviceBehaviors>
      <behavior name="DefaultBehavior">
        <serviceHealth httpsGetEnabled="true"/>
      </behavior>
    </serviceBehaviors>
  </behaviors>
  ```

<span data-ttu-id="fcb44-168">Na stav služby se dá zadat dotaz pomocí parametrů dotazu, jako je `OnServiceFailure`, `OnDispatcherFailure`, `OnListenerFailure`, `OnThrottlePercentExceeded`), a pro každý parametr dotazu se dá zadat kód odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="fcb44-168">A service's health status can be queried by using query parameters such as `OnServiceFailure`, `OnDispatcherFailure`, `OnListenerFailure`, `OnThrottlePercentExceeded`), and an HTTP response code can be specified for each query parameter.</span></span> <span data-ttu-id="fcb44-169">Pokud je pro parametr dotazu vynechání kódu odpovědi HTTP, ve výchozím nastavení se používá kód odpovědi HTTP 503.</span><span class="sxs-lookup"><span data-stu-id="fcb44-169">If the HTTP response code is omitted for a query parameter, a 503 HTTP response code is used by default.</span></span> <span data-ttu-id="fcb44-170">Příklad:</span><span class="sxs-lookup"><span data-stu-id="fcb44-170">For example:</span></span>

- <span data-ttu-id="fcb44-171">OnServiceFailure: `https://contoso:81/Service1?health&OnServiceFailure=450`</span><span class="sxs-lookup"><span data-stu-id="fcb44-171">OnServiceFailure: `https://contoso:81/Service1?health&OnServiceFailure=450`</span></span>

  <span data-ttu-id="fcb44-172">Kód stavu odpovědi HTTP 450 je vrácen, je-li [Třída ServiceHost. State](xref:System.ServiceModel.Channels.CommunicationObject.State) je větší než <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-172">A 450 HTTP response status code is returned when [ServiceHost.State](xref:System.ServiceModel.Channels.CommunicationObject.State) is greater than <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.</span></span>
<span data-ttu-id="fcb44-173">Parametry a příklady dotazů:</span><span class="sxs-lookup"><span data-stu-id="fcb44-173">Query parameters and examples:</span></span>

- <span data-ttu-id="fcb44-174">OnDispatcherFailure: `https://contoso:81/Service1?health&OnDispatcherFailure=455`</span><span class="sxs-lookup"><span data-stu-id="fcb44-174">OnDispatcherFailure: `https://contoso:81/Service1?health&OnDispatcherFailure=455`</span></span>

  <span data-ttu-id="fcb44-175">Stavový kód odpovědi HTTP 455 se vrátí, pokud je stav některého z přeslaných kanálů větší než <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-175">A 455 HTTP response status code is returned when the state of any of the channel dispatchers is greater than <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="fcb44-176">OnListenerFailure: `https://contoso:81/Service1?health&OnListenerFailure=465`</span><span class="sxs-lookup"><span data-stu-id="fcb44-176">OnListenerFailure: `https://contoso:81/Service1?health&OnListenerFailure=465`</span></span>

  <span data-ttu-id="fcb44-177">Stavový kód odpovědi HTTP 465 se vrátí, pokud je stav jakéhokoli naslouchacího procesu kanálu větší než <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-177">A 465 HTTP response status code is returned when the state of any of the channel listeners is greater than <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="fcb44-178">OnThrottlePercentExceeded: `https://contoso:81/Service1?health&OnThrottlePercentExceeded= 70:350,95:500`</span><span class="sxs-lookup"><span data-stu-id="fcb44-178">OnThrottlePercentExceeded: `https://contoso:81/Service1?health&OnThrottlePercentExceeded= 70:350,95:500`</span></span>

  <span data-ttu-id="fcb44-179">Určuje procento {1 – 100}, které aktivuje odpověď a kód odpovědi HTTP {200 – 599}.</span><span class="sxs-lookup"><span data-stu-id="fcb44-179">Specifies the percentage {1 – 100} that triggers the response and its HTTP response code {200 – 599}.</span></span> <span data-ttu-id="fcb44-180">V tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="fcb44-180">In this example:</span></span>

  - <span data-ttu-id="fcb44-181">Pokud je procento větší než 95, vrátí se kód odpovědi HTTP 500.</span><span class="sxs-lookup"><span data-stu-id="fcb44-181">If the percentage is greater than 95, a 500 HTTP response code is returned.</span></span>

  - <span data-ttu-id="fcb44-182">Pokud je vráceno procento nebo mezi 70 a 95, 350.</span><span class="sxs-lookup"><span data-stu-id="fcb44-182">If the percentage or between 70 and 95, 350 is returned.</span></span>

  - <span data-ttu-id="fcb44-183">V opačném případě se vrátí 200.</span><span class="sxs-lookup"><span data-stu-id="fcb44-183">Otherwise, 200 is returned.</span></span>

<span data-ttu-id="fcb44-184">Stav služby se dá zobrazit v HTML zadáním řetězce dotazu, jako je `https://contoso:81/Service1?health` nebo XML zadáním řetězce dotazu, jako je například `https://contoso:81/Service1?health&Xml`.</span><span class="sxs-lookup"><span data-stu-id="fcb44-184">The service health status can be displayed either in HTML by specifying a query string like `https://contoso:81/Service1?health` or in XML by specifying a query string like `https://contoso:81/Service1?health&Xml`.</span></span> <span data-ttu-id="fcb44-185">Řetězec dotazu, jako je například `https://contoso:81/Service1?health&NoContent`, vrátí prázdnou stránku HTML.</span><span class="sxs-lookup"><span data-stu-id="fcb44-185">A query string like `https://contoso:81/Service1?health&NoContent` returns an empty HTML page.</span></span>

<a name="wpf48" />

#### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="fcb44-186">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="fcb44-186">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="fcb44-187">**Vylepšení vysokého rozlišení DPI**</span><span class="sxs-lookup"><span data-stu-id="fcb44-187">**High DPI enhancements**</span></span>

<span data-ttu-id="fcb44-188">V .NET Framework 4,8 WPF přidává podporu pro sledování rozlišení DPI podle monitoru v2 a škálování ve smíšeném režimu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-188">In .NET Framework 4.8, WPF adds support for Per-Monitor V2 DPI Awareness and Mixed-Mode DPI scaling.</span></span> <span data-ttu-id="fcb44-189">Další informace o vývoji vysokého rozlišení DPI najdete v tématu [vývoj desktopových aplikací s vysokým rozlišením v systému Windows](/windows/win32/hidpi/high-dpi-desktop-application-development-on-windows) .</span><span class="sxs-lookup"><span data-stu-id="fcb44-189">See [High DPI Desktop Application Development on Windows](/windows/win32/hidpi/high-dpi-desktop-application-development-on-windows) for additional information about high DPI development.</span></span>

<span data-ttu-id="fcb44-190">.NET Framework 4,8 vylepšuje podporu hostovaných HWND a model Windows Forms spolupráce v aplikacích WPF s vysokým rozlišením DPI na platformách, které podporují škálování DPI ve smíšeném režimu (od aktualizace Windows 10. dubna 2018).</span><span class="sxs-lookup"><span data-stu-id="fcb44-190">.NET Framework 4.8 improves support for hosted HWNDs and Windows Forms interoperation in High-DPI WPF applications on platforms that support Mixed-Mode DPI scaling (starting with Windows 10 April 2018 Update).</span></span> <span data-ttu-id="fcb44-191">Když jsou hostované ovládací prvky HWND nebo model Windows Forms vytvořeny jako okna s rozlišením DPI ve smíšeném režimu pomocí volání [SetThreadDpiHostingBehavior](/windows/desktop/api/winuser/nf-winuser-setthreaddpihostingbehavior) a [SetThreadDpiAwarenessContext](/windows/desktop/api/winuser/nf-winuser-setthreaddpiawarenesscontext), mohou být hostovány v aplikaci WPF pro monitor v2 a mají velikost a správně škálovat.</span><span class="sxs-lookup"><span data-stu-id="fcb44-191">When hosted HWNDs or Windows Forms controls are created as Mixed-Mode DPI-scaled windows by calling [SetThreadDpiHostingBehavior](/windows/desktop/api/winuser/nf-winuser-setthreaddpihostingbehavior) and [SetThreadDpiAwarenessContext](/windows/desktop/api/winuser/nf-winuser-setthreaddpiawarenesscontext), they can be hosted in a Per-Monitor V2 WPF application and are sized and scaled appropriately.</span></span> <span data-ttu-id="fcb44-192">Takový hostovaný obsah se nevykresluje s nativním rozlišením DPI; operační systém místo toho škáluje hostovaný obsah na příslušnou velikost.</span><span class="sxs-lookup"><span data-stu-id="fcb44-192">Such hosted content is not rendered at the native DPI; instead, the operating system scales the hosted content to the appropriate size.</span></span> <span data-ttu-id="fcb44-193">Podpora režimu sledování DPI v rámci monitoru v2 také umožňuje hostování ovládacích prvků WPF (tj. nadřazených) v nativním okně aplikace s vysokým rozlišením DPI.</span><span class="sxs-lookup"><span data-stu-id="fcb44-193">The support for Per-Monitor v2 DPI awareness mode also allows WPF controls to be hosted (i.e., parented) in a native window in a high-DPI application.</span></span>

<span data-ttu-id="fcb44-194">Pokud chcete povolit podporu pro škálování ve smíšeném režimu s vysokým rozlišením DPI, můžete nastavit následující [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) přepínače konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="fcb44-194">To enable support for Mixed-Mode High DPI scaling, you can set the following [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switches the application configuration file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value = "Switch.System.Windows.DoNotScaleForDpiChanges=false; Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false"/>
</runtime>
```

<a name="clr48" />

#### <a name="common-language-runtime"></a><span data-ttu-id="fcb44-195">Modul CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="fcb44-195">Common language runtime</span></span>

<span data-ttu-id="fcb44-196">Modul runtime v .NET Framework 4,8 obsahuje následující změny a vylepšení:</span><span class="sxs-lookup"><span data-stu-id="fcb44-196">The runtime in .NET Framework 4.8 includes the following changes and improvements:</span></span>

<span data-ttu-id="fcb44-197">**Vylepšení kompilátoru JIT**.</span><span class="sxs-lookup"><span data-stu-id="fcb44-197">**Improvements to the JIT compiler**.</span></span> <span data-ttu-id="fcb44-198">Kompilátor JIT (just-in-time) v .NET Framework 4,8 je založen na kompilátoru JIT v rozhraní .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="fcb44-198">The Just-in-time (JIT) compiler in .NET Framework 4.8 is based on the JIT compiler in .NET Core 2.1.</span></span> <span data-ttu-id="fcb44-199">Mnohé z optimalizací a všechny opravy chyb provedené kompilátorem JIT .NET Core 2,1 jsou součástí kompilátoru .NET Framework 4,8 JIT.</span><span class="sxs-lookup"><span data-stu-id="fcb44-199">Many of the optimizations and all of the bug fixes made to the .NET Core 2.1 JIT compiler are included in the .NET Framework 4.8 JIT compiler.</span></span>

<span data-ttu-id="fcb44-200">**Vylepšení Ngen**.</span><span class="sxs-lookup"><span data-stu-id="fcb44-200">**NGEN improvements**.</span></span> <span data-ttu-id="fcb44-201">Modul runtime zlepšil správu paměti pro Image [generátoru nativních imagí](../tools/ngen-exe-native-image-generator.md) (NGen), takže data mapovaná z imagí Ngen nejsou rezidentní v paměti.</span><span class="sxs-lookup"><span data-stu-id="fcb44-201">The runtime has improved its memory management for [Native Image Generator](../tools/ngen-exe-native-image-generator.md) (NGEN) images so that data mapped from NGEN images are not memory-resident.</span></span> <span data-ttu-id="fcb44-202">Tím se snižuje plocha dostupná pro útoky, které se pokoušejí spustit libovolný kód úpravou paměti, která se spustí.</span><span class="sxs-lookup"><span data-stu-id="fcb44-202">This reduces the surface area available to attacks that attempt to execute arbitrary code by modifying memory that will be executed.</span></span>

<span data-ttu-id="fcb44-203">**Kontrola antimalwaru pro všechna sestavení**.</span><span class="sxs-lookup"><span data-stu-id="fcb44-203">**Antimalware scanning for all assemblies**.</span></span> <span data-ttu-id="fcb44-204">V předchozích verzích .NET Framework modul runtime prohledává všechna sestavení načtená z disku pomocí programu Windows Defender nebo antimalwarového softwaru jiného výrobce.</span><span class="sxs-lookup"><span data-stu-id="fcb44-204">In previous versions of the .NET Framework, the runtime scans all assemblies loaded from disk using either Windows Defender or third-party antimalware software.</span></span> <span data-ttu-id="fcb44-205">Nicméně sestavení načtená z jiných zdrojů, například metodou <xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType>, nejsou prohledávána a mohou potenciálně obsahovat nezjištěné malware.</span><span class="sxs-lookup"><span data-stu-id="fcb44-205">However, assemblies loaded from other sources, such as by the <xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType> method, are not scanned and can potentially contain undetected malware.</span></span> <span data-ttu-id="fcb44-206">Počínaje .NET Framework 4,8 spuštěným v systému Windows 10 spustí modul runtime kontrolu pomocí antimalwarových řešení, která implementují [rozhraní AMSI (antimalwarová kontrola)](/windows/desktop/AMSI/antimalware-scan-interface-portal).</span><span class="sxs-lookup"><span data-stu-id="fcb44-206">Starting with .NET Framework 4.8 running on Windows 10, the runtime triggers a scan by antimalware solutions that implement the [Antimalware Scan Interface (AMSI)](/windows/desktop/AMSI/antimalware-scan-interface-portal).</span></span>

<a name="v472" />

## <a name="whats-new-in-net-framework-472"></a><span data-ttu-id="fcb44-207">Co je nového v .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="fcb44-207">What's new in .NET Framework 4.7.2</span></span>

<span data-ttu-id="fcb44-208">.NET Framework 4.7.2 zahrnuje nové funkce v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="fcb44-208">.NET Framework 4.7.2 includes new features in the following areas:</span></span>

- [<span data-ttu-id="fcb44-209">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="fcb44-209">Base classes</span></span>](#core-472)
- [<span data-ttu-id="fcb44-210">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="fcb44-210">ASP.NET</span></span>](#asp-net472)
- [<span data-ttu-id="fcb44-211">Sítě</span><span class="sxs-lookup"><span data-stu-id="fcb44-211">Networking</span></span>](#net472)
- [<span data-ttu-id="fcb44-212">SQL</span><span class="sxs-lookup"><span data-stu-id="fcb44-212">SQL</span></span>](#sql472)
- [<span data-ttu-id="fcb44-213">WPF</span><span class="sxs-lookup"><span data-stu-id="fcb44-213">WPF</span></span>](#wpf472)
- [<span data-ttu-id="fcb44-214">ClickOnce</span><span class="sxs-lookup"><span data-stu-id="fcb44-214">ClickOnce</span></span>](#clickonce)

<span data-ttu-id="fcb44-215">Dalším cílem .NET Framework 4.7.2 je lepší přístupnost, která umožňuje aplikaci poskytovat vhodné prostředí pro uživatele technologie usnadnění.</span><span class="sxs-lookup"><span data-stu-id="fcb44-215">A continuing focus in .NET Framework 4.7.2 is improved accessibility, which allows an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="fcb44-216">Informace o vylepšeních usnadnění v .NET Framework 4.7.2 najdete v tématu [co je nového v přístupnosti v .NET Framework](whats-new-in-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-216">For information on accessibility improvements in .NET Framework 4.7.2, see [What's new in accessibility in the .NET Framework](whats-new-in-accessibility.md).</span></span>

<a name="core-472" />

#### <a name="base-classes"></a><span data-ttu-id="fcb44-217">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="fcb44-217">Base classes</span></span>

<span data-ttu-id="fcb44-218">.NET Framework 4.7.2 obsahuje velký počet kryptografických vylepšení, lepší podporu dekomprese pro archivy ZIP a další rozhraní API pro shromažďování dat.</span><span class="sxs-lookup"><span data-stu-id="fcb44-218">.NET Framework 4.7.2 features a large number of cryptographic enhancements, better decompression support for ZIP archives, and additional collection APIs.</span></span>

<span data-ttu-id="fcb44-219">**Nová přetížení RSA. Vytvořte a DSA. Vytvořeny**</span><span class="sxs-lookup"><span data-stu-id="fcb44-219">**New overloads of RSA.Create and DSA.Create**</span></span>

<span data-ttu-id="fcb44-220">Metody <xref:System.Security.Cryptography.DSA.Create(System.Security.Cryptography.DSAParameters)?displayProperty=nameWithType> a <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> umožňují zadávat klíčové parametry při vytváření instancí nového klíče <xref:System.Security.Cryptography.DSA> nebo <xref:System.Security.Cryptography.RSA>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-220">The <xref:System.Security.Cryptography.DSA.Create(System.Security.Cryptography.DSAParameters)?displayProperty=nameWithType> and <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> methods let you supply key parameters when instantiating a new <xref:System.Security.Cryptography.DSA> or <xref:System.Security.Cryptography.RSA> key.</span></span> <span data-ttu-id="fcb44-221">Umožňují nahradit kód podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="fcb44-221">They allow you to replace code like the following:</span></span>

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

<span data-ttu-id="fcb44-222">podobný kód:</span><span class="sxs-lookup"><span data-stu-id="fcb44-222">with code like this:</span></span>

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

<span data-ttu-id="fcb44-223">Metody <xref:System.Security.Cryptography.DSA.Create(System.Int32)?displayProperty=nameWithType> a <xref:System.Security.Cryptography.RSA.Create(System.Int32)?displayProperty=nameWithType> umožňují generovat nové klíče <xref:System.Security.Cryptography.DSA> nebo <xref:System.Security.Cryptography.RSA> s určitou velikostí klíče.</span><span class="sxs-lookup"><span data-stu-id="fcb44-223">The <xref:System.Security.Cryptography.DSA.Create(System.Int32)?displayProperty=nameWithType> and <xref:System.Security.Cryptography.RSA.Create(System.Int32)?displayProperty=nameWithType> methods let you generate new <xref:System.Security.Cryptography.DSA> or <xref:System.Security.Cryptography.RSA> keys with a specific key size.</span></span> <span data-ttu-id="fcb44-224">Příklad:</span><span class="sxs-lookup"><span data-stu-id="fcb44-224">For example:</span></span>

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

<span data-ttu-id="fcb44-225">**Konstruktory Rfc2898DeriveBytes přijímají název algoritmu hash.**</span><span class="sxs-lookup"><span data-stu-id="fcb44-225">**Rfc2898DeriveBytes constructors accept a hash algorithm name**</span></span>

<span data-ttu-id="fcb44-226">Třída <xref:System.Security.Cryptography.Rfc2898DeriveBytes> má tři nové konstruktory s parametrem <xref:System.Security.Cryptography.HashAlgorithmName>, který identifikuje algoritmus HMAC, který se má použít při odvozování klíčů.</span><span class="sxs-lookup"><span data-stu-id="fcb44-226">The <xref:System.Security.Cryptography.Rfc2898DeriveBytes> class has three new constructors with a <xref:System.Security.Cryptography.HashAlgorithmName> parameter that identifies the HMAC algorithm to use when deriving keys.</span></span> <span data-ttu-id="fcb44-227">Místo použití algoritmu SHA-1 by vývojáři měli používat HMAC založené na SHA-2, jako je SHA-256, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="fcb44-227">Instead of using SHA-1, developers should use a SHA-2-based HMAC like SHA-256, as shown in the following example:</span></span>

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

<span data-ttu-id="fcb44-228">**Podpora dočasných klíčů**</span><span class="sxs-lookup"><span data-stu-id="fcb44-228">**Support for ephemeral keys**</span></span>

<span data-ttu-id="fcb44-229">Import PFX může volitelně načíst soukromé klíče přímo z paměti a obejít pevný disk.</span><span class="sxs-lookup"><span data-stu-id="fcb44-229">PFX import can optionally load private keys directly from memory, bypassing the hard drive.</span></span><span data-ttu-id="fcb44-230"> Pokud je nový příznak <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> zadán v konstruktoru <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> nebo v jednom z přetížení metody <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.Import%2A?displayProperty=nameWithType>, privátní klíče budou načteny jako dočasné klíče.</span><span class="sxs-lookup"><span data-stu-id="fcb44-230"> When the new <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> flag is specified in an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> constructor or one of the overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.Import%2A?displayProperty=nameWithType> method, the private keys will be loaded as ephemeral keys.</span></span> <span data-ttu-id="fcb44-231">To brání tomu, aby se klíče na disku zobrazily.</span><span class="sxs-lookup"><span data-stu-id="fcb44-231">This prevents the keys from being visible on the disk.</span></span> <span data-ttu-id="fcb44-232">Naopak</span><span class="sxs-lookup"><span data-stu-id="fcb44-232">However:</span></span>

- <span data-ttu-id="fcb44-233">Vzhledem k tomu, že klíče nejsou trvale uložené na disku, certifikáty načtené pomocí tohoto příznaku nejsou vhodnými kandidáty k přidání do X509Store.</span><span class="sxs-lookup"><span data-stu-id="fcb44-233">Since the keys are not persisted to disk, certificates loaded with this flag are not good candidates to add to an X509Store.</span></span>

- <span data-ttu-id="fcb44-234">Klíče načtené tímto způsobem jsou téměř vždy načítány prostřednictvím služby Windows CNG.</span><span class="sxs-lookup"><span data-stu-id="fcb44-234">Keys loaded in this manner are almost always loaded via Windows CNG.</span></span> <span data-ttu-id="fcb44-235">Proto volající musí získat přístup k privátnímu klíči voláním metod rozšíření, jako je například [CERT. GetRSAPrivateKey ()](xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A).</span><span class="sxs-lookup"><span data-stu-id="fcb44-235">Therefore, callers must access the private key by calling extension methods, such as [cert.GetRSAPrivateKey()](xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A).</span></span> <span data-ttu-id="fcb44-236">Vlastnost <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> nefunguje.</span><span class="sxs-lookup"><span data-stu-id="fcb44-236">The <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> property does not function.</span></span>

- <span data-ttu-id="fcb44-237">Vzhledem k tomu, že starší vlastnost <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> nefunguje s certifikáty, vývojáři by měli před přechodem na dočasné klíče provést přísné testování.</span><span class="sxs-lookup"><span data-stu-id="fcb44-237">Since the legacy <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> property does not work with certificates, developers should perform rigorous testing before switching to ephemeral keys.</span></span>

<span data-ttu-id="fcb44-238">**Programové vytváření žádostí o podepsání certifikátu PKCS # 10 a certifikátů veřejných klíčů X. 509**</span><span class="sxs-lookup"><span data-stu-id="fcb44-238">**Programmatic creation of PKCS#10 certification signing requests and X.509 public key certificates**</span></span>

<span data-ttu-id="fcb44-239">Počínaje .NET Framework 4.7.2 můžou úlohy generovat žádosti o podepsání certifikátu (oddělení IT), které umožňují, aby se generování žádosti o certifikát připravilo na stávající nástroje.</span><span class="sxs-lookup"><span data-stu-id="fcb44-239">Starting with .NET Framework 4.7.2, workloads can generate certificate signing requests (CSRs), which allows certificate request generation to be staged into existing tooling.</span></span> <span data-ttu-id="fcb44-240">To je často užitečné v testovacích scénářích.</span><span class="sxs-lookup"><span data-stu-id="fcb44-240">This is frequently useful in test scenarios.</span></span>

<span data-ttu-id="fcb44-241">Další informace a příklady kódu naleznete v tématu "programové vytváření žádostí o podepsání certifikátu PKCS # 10 a" certifikátů veřejných klíčů X. 509 "na [blogu .NET](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).</span><span class="sxs-lookup"><span data-stu-id="fcb44-241">For more information and code examples, see "Programmatic creation of PKCS#10 certification signing requests and X.509 public key certificates" in the [.NET Blog](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).</span></span>

<span data-ttu-id="fcb44-242">**Noví členové SignerInfo**</span><span class="sxs-lookup"><span data-stu-id="fcb44-242">**New SignerInfo members**</span></span>

<span data-ttu-id="fcb44-243">Počínaje .NET Framework 4.7.2 třída <xref:System.Security.Cryptography.Pkcs.SignerInfo> zveřejňuje Další informace o podpisu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-243">Starting with .NET Framework 4.7.2, the <xref:System.Security.Cryptography.Pkcs.SignerInfo> class exposes more information about the signature.</span></span> <span data-ttu-id="fcb44-244">Můžete načíst hodnotu vlastnosti <xref:System.Security.Cryptography.Pkcs.SignerInfo.SignatureAlgorithm?displayProperty=fullName> a určit tak algoritmus podpisu, který používá podepisující osoba.</span><span class="sxs-lookup"><span data-stu-id="fcb44-244">You can retrieve the value of the <xref:System.Security.Cryptography.Pkcs.SignerInfo.SignatureAlgorithm?displayProperty=fullName> property to determine the signature algorithm used by the signer.</span></span> <span data-ttu-id="fcb44-245">pro získání kopie kryptografického podpisu pro tohoto podepsaného se dá volat <xref:System.Security.Cryptography.Pkcs.SignerInfo.GetSignature%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-245"><xref:System.Security.Cryptography.Pkcs.SignerInfo.GetSignature%2A?displayProperty=nameWithType> can be called to get a copy of the cryptographic signature for this signer.</span></span>

<span data-ttu-id="fcb44-246">**Otevření zabaleného datového proudu po odstranění CryptoStream**</span><span class="sxs-lookup"><span data-stu-id="fcb44-246">**Leaving a wrapped stream open after CryptoStream is disposed**</span></span>

<span data-ttu-id="fcb44-247">Počínaje .NET Framework 4.7.2 má třída <xref:System.Security.Cryptography.CryptoStream> další konstruktor, který umožňuje <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> zavřít zabalený datový proud.</span><span class="sxs-lookup"><span data-stu-id="fcb44-247">Starting with .NET Framework 4.7.2, the <xref:System.Security.Cryptography.CryptoStream> class has an additional constructor that allows <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> to not close the wrapped stream.</span></span><span data-ttu-id="fcb44-248"> Chcete-li nechat zabaleného datového proudu otevřený po zrušení instance <xref:System.Security.Cryptography.CryptoStream>, zavolejte nový konstruktor <xref:System.Security.Cryptography.CryptoStream> následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="fcb44-248"> To leave the wrapped stream open after the <xref:System.Security.Cryptography.CryptoStream> instance is disposed, call the new <xref:System.Security.Cryptography.CryptoStream> constructor as follows:</span></span>

```csharp
var cStream = new CryptoStream(stream, transform, mode, leaveOpen: true);
```

```vb
Dim cStream = New CryptoStream(stream, transform, mode, leaveOpen:=true)
```

<span data-ttu-id="fcb44-249">**Dekomprese změn v DeflateStream**</span><span class="sxs-lookup"><span data-stu-id="fcb44-249">**Decompression changes in DeflateStream**</span></span>

<span data-ttu-id="fcb44-250">Počínaje .NET Framework 4.7.2 se implementace operací dekomprese ve třídě <xref:System.IO.Compression.DeflateStream> změnila tak, aby ve výchozím nastavení používala nativní rozhraní API systému Windows.</span><span class="sxs-lookup"><span data-stu-id="fcb44-250">Starting with .NET Framework 4.7.2, the implementation of decompression operations in the <xref:System.IO.Compression.DeflateStream> class has changed to use native Windows APIs by default.</span></span> <span data-ttu-id="fcb44-251">Obvykle to vede k výraznému zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-251">Typically, this results in a substantial performance improvement.</span></span>

<span data-ttu-id="fcb44-252">Podpora dekomprese pomocí rozhraní Windows API je ve výchozím nastavení povolená pro aplikace, které cílí na .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="fcb44-252">Support for decompression by using Windows APIs is enabled by default for applications that target .NET Framework 4.7.2.</span></span> <span data-ttu-id="fcb44-253">Aplikace, které jsou cíleny na starší verze .NET Framework, ale jsou spuštěny v rámci .NET Framework 4.7.2, se můžou na toto chování vyjádřit přidáním následujícího [přepínače AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="fcb44-253">Applications that target earlier versions of .NET Framework but are running under .NET Framework 4.7.2 can opt into this behavior by adding the following [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the application configuration file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=false" />
```

<span data-ttu-id="fcb44-254">**Další rozhraní API pro shromažďování**</span><span class="sxs-lookup"><span data-stu-id="fcb44-254">**Additional collection APIs**</span></span>

<span data-ttu-id="fcb44-255">.NET Framework 4.7.2 přidá do typů <xref:System.Collections.Generic.SortedSet%601> a <xref:System.Collections.Generic.HashSet%601> řadu nových rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="fcb44-255">.NET Framework 4.7.2 adds a number of new APIs to the <xref:System.Collections.Generic.SortedSet%601> and <xref:System.Collections.Generic.HashSet%601> types.</span></span> <span data-ttu-id="fcb44-256">Mezi ně patří:</span><span class="sxs-lookup"><span data-stu-id="fcb44-256">These include:</span></span>

- <span data-ttu-id="fcb44-257">metody `TryGetValue`, které přesahují vzor try použitý v jiných typech kolekcí těchto dvou typů.</span><span class="sxs-lookup"><span data-stu-id="fcb44-257">`TryGetValue` methods, which extend the try pattern used in other collection types to these two types.</span></span> <span data-ttu-id="fcb44-258">Metody jsou:</span><span class="sxs-lookup"><span data-stu-id="fcb44-258">The methods are:</span></span>

  - [<span data-ttu-id="fcb44-259">Public bool HashSet – @ no__t-1T >. TryGetValue (T equalValue; out T actualValue)</span><span class="sxs-lookup"><span data-stu-id="fcb44-259">public bool HashSet\<T>.TryGetValue(T equalValue, out T actualValue)</span></span>](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)
  - [<span data-ttu-id="fcb44-260">Public bool SortedSet @ no__t-1T >. TryGetValue (T equalValue; out T actualValue)</span><span class="sxs-lookup"><span data-stu-id="fcb44-260">public bool SortedSet\<T>.TryGetValue(T equalValue, out T actualValue)</span></span>](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)

- <span data-ttu-id="fcb44-261">metody rozšíření `Enumerable.To*`, které převádějí kolekci na <xref:System.Collections.Generic.HashSet%601>:</span><span class="sxs-lookup"><span data-stu-id="fcb44-261">`Enumerable.To*` extension methods, which convert a collection to a <xref:System.Collections.Generic.HashSet%601>:</span></span>

  - [<span data-ttu-id="fcb44-262">public static HashSet – @ no__t-1TSource > ToHashSet @ no__t-2TSource > (this IEnumerable @ no__t-3TSource > Source)</span><span class="sxs-lookup"><span data-stu-id="fcb44-262">public static HashSet\<TSource> ToHashSet\<TSource>(this IEnumerable\<TSource> source)</span></span>](xref:System.Linq.Enumerable.ToHashSet%2A)
  - [<span data-ttu-id="fcb44-263">public static HashSet – @ no__t-1TSource > ToHashSet @ no__t-2TSource > (this IEnumerable @ no__t-3TSource > Source, IEqualityComparer @ no__t-4TSource > Comparer)</span><span class="sxs-lookup"><span data-stu-id="fcb44-263">public static HashSet\<TSource> ToHashSet\<TSource>(this IEnumerable\<TSource> source, IEqualityComparer\<TSource> comparer)</span></span>](xref:System.Linq.Enumerable.ToHashSet%2A)

- <span data-ttu-id="fcb44-264">Nové konstruktory <xref:System.Collections.Generic.HashSet%601>, které umožňují nastavit kapacitu kolekce, což vede k výhodám výkonu, když znáte velikost <xref:System.Collections.Generic.HashSet%601> předem:</span><span class="sxs-lookup"><span data-stu-id="fcb44-264">New <xref:System.Collections.Generic.HashSet%601> constructors that let you set the collection's capacity, which yields a performance benefit when you know the size of the <xref:System.Collections.Generic.HashSet%601> in advance:</span></span>

  - <span data-ttu-id="fcb44-265">[veřejné HashSet – (kapacita celé číslo)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32))</span><span class="sxs-lookup"><span data-stu-id="fcb44-265">[public HashSet(int capacity)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32))</span></span>
  - <span data-ttu-id="fcb44-266">[Public HashSet – (kapacita int, IEqualityComparer @ no__t-1T > Comparer)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32,System.Collections.Generic.IEqualityComparer%7B%600%7D))</span><span class="sxs-lookup"><span data-stu-id="fcb44-266">[public HashSet(int capacity, IEqualityComparer\<T> comparer)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32,System.Collections.Generic.IEqualityComparer%7B%600%7D))</span></span>

<span data-ttu-id="fcb44-267">Třída <xref:System.Collections.Concurrent.ConcurrentDictionary%602> obsahuje nová přetížení metod <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> a <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> k načtení hodnoty ze slovníku nebo k jejímu přidání, pokud nebyla nalezena, a pokud se má do slovníku přidat hodnota, pokud již existuje.</span><span class="sxs-lookup"><span data-stu-id="fcb44-267">The <xref:System.Collections.Concurrent.ConcurrentDictionary%602> class includes new overloads of the <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> and <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> methods to retrieve a value from the dictionary or to add it if it is not found, and to add a value to the dictionary or to update it if it already exists.</span></span>

```csharp
public TValue AddOrUpdate<TArg>(TKey key, Func<TKey, TArg, TValue> addValueFactory, Func<TKey, TValue, TArg, TValue> updateValueFactory, TArg factoryArgument)

public TValue GetOrAdd<TArg>(TKey key, Func<TKey, TArg, TValue> valueFactory, TArg factoryArgument)
```

```vb
Public AddOrUpdate(Of TArg)(key As TKey, addValueFactory As Func(Of TKey, TArg, TValue), updateValueFactory As Func(Of TKey, TValue, TArg, TValue), factoryArgument As TArg) As TValue

Public GetOrAdd(Of TArg)(key As TKey, valueFactory As Func(Of TKey, TArg, TValue), factoryArgument As TArg) As TValue
```

<a name="asp-net472" />

#### <a name="aspnet"></a><span data-ttu-id="fcb44-268">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="fcb44-268">ASP.NET</span></span>

<span data-ttu-id="fcb44-269">**Podpora pro vkládání závislostí ve webových formulářích**</span><span class="sxs-lookup"><span data-stu-id="fcb44-269">**Support for dependency injection in Web Forms**</span></span>

<span data-ttu-id="fcb44-270">[Vkládání závislostí (di)](/aspnet/core/fundamentals/dependency-injection#overview-of-dependency-injection) odděluje objekty a jejich závislosti tak, že kód objektu již není nutné změnit pouze proto, že došlo ke změně závislosti.</span><span class="sxs-lookup"><span data-stu-id="fcb44-270">[Dependency injection (DI)](/aspnet/core/fundamentals/dependency-injection#overview-of-dependency-injection) decouples objects and their dependencies so that an object's code no longer needs to be changed just because a dependency has changed.</span></span> <span data-ttu-id="fcb44-271">Při vývoji aplikací ASP.NET, které cílí na .NET Framework 4.7.2, můžete:</span><span class="sxs-lookup"><span data-stu-id="fcb44-271">When developing ASP.NET applications that target .NET Framework 4.7.2, you can:</span></span>

- <span data-ttu-id="fcb44-272">Použijte metodu setter založenou na rozhraních a na bázi konstruktoru v [obslužných rutinách a modulech](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [instancích stránky](xref:System.Web.UI.Page)a [uživatelských ovládacích prvcích](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) projektů webové aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fcb44-272">Use setter-based, interface-based, and constructor-based injection in [handlers and modules](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [Page instances](xref:System.Web.UI.Page), and [user controls](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) of ASP.NET web application projects.</span></span>

- <span data-ttu-id="fcb44-273">Používejte vkládání na základě rozhraní a založených na rozhraních v [obslužných rutinách a modulech](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [instancích stránky](xref:System.Web.UI.Page)a [uživatelských ovládacích prvcích](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) projektů webu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fcb44-273">Use setter-based and interface-based injection in [handlers and modules](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [Page instances](xref:System.Web.UI.Page), and [user controls](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) of ASP.NET web site projects.</span></span>

- <span data-ttu-id="fcb44-274">Připojte se k různým rozhraním injektáže pro vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="fcb44-274">Plug in different dependency injection frameworks.</span></span>

<span data-ttu-id="fcb44-275">**Podpora souborů cookie stejného webu**</span><span class="sxs-lookup"><span data-stu-id="fcb44-275">**Support for same-site cookies**</span></span>

<span data-ttu-id="fcb44-276">[SameSite](https://tools.ietf.org/html/draft-west-first-party-cookies-07) zabraňuje prohlížeči v posílání souborů cookie spolu s žádostí mezi weby.</span><span class="sxs-lookup"><span data-stu-id="fcb44-276">[SameSite](https://tools.ietf.org/html/draft-west-first-party-cookies-07) prevents a browser from sending a cookie along with a cross-site request.</span></span> <span data-ttu-id="fcb44-277">.NET Framework 4.7.2 přidá vlastnost <xref:System.Web.HttpCookie.SameSite?displayProperty=nameWithType>, jejíž hodnota je člen výčtu <xref:System.Web.SameSiteMode?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-277">.NET Framework 4.7.2 adds a <xref:System.Web.HttpCookie.SameSite?displayProperty=nameWithType> property whose value is a <xref:System.Web.SameSiteMode?displayProperty=nameWithType> enumeration member.</span></span> <span data-ttu-id="fcb44-278">Pokud je jeho hodnota <xref:System.Web.SameSiteMode.Strict?displayProperty=nameWithType> nebo <xref:System.Web.SameSiteMode.Lax?displayProperty=nameWithType>, ASP.NET přidá atribut `SameSite` do hlavičky Set-cookie.</span><span class="sxs-lookup"><span data-stu-id="fcb44-278">If its value is <xref:System.Web.SameSiteMode.Strict?displayProperty=nameWithType> or <xref:System.Web.SameSiteMode.Lax?displayProperty=nameWithType>, ASP.NET adds the `SameSite` attribute to the set-cookie header.</span></span> <span data-ttu-id="fcb44-279">Podpora SameSite se vztahuje na objekty @no__t 0 a také na soubory cookie <xref:System.Web.Security.FormsAuthentication> a <xref:System.Web.SessionState>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-279">SameSite support applies to <xref:System.Web.HttpCookie> objects, as well as to <xref:System.Web.Security.FormsAuthentication> and <xref:System.Web.SessionState> cookies.</span></span>

<span data-ttu-id="fcb44-280">SameSite pro objekt <xref:System.Web.HttpCookie> můžete nastavit následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="fcb44-280">You can set SameSite for an <xref:System.Web.HttpCookie> object as follows:</span></span>

```csharp
var c = new HttpCookie("secureCookie", "same origin");
c.SameSite = SameSiteMode.Lax;
```

```vb
Dim c As New HttpCookie("secureCookie", "same origin")
c.SameSite = SameSiteMode.Lax
```

<span data-ttu-id="fcb44-281">Soubory cookie SameSite můžete také nakonfigurovat na úrovni aplikace úpravou souboru Web. config:</span><span class="sxs-lookup"><span data-stu-id="fcb44-281">You can also configure SameSite cookies at the application level by modifying the web.config file:</span></span>

```xml
<system.web>
   <httpCookies sameSite="Strict" />
</system.web>
```

<span data-ttu-id="fcb44-282">Můžete přidat SameSite pro soubory cookie <xref:System.Web.Security.FormsAuthentication> a <xref:System.Web.SessionState> úpravou konfiguračního souboru Web:</span><span class="sxs-lookup"><span data-stu-id="fcb44-282">You can add SameSite for <xref:System.Web.Security.FormsAuthentication> and <xref:System.Web.SessionState> cookies by modifying the web config file:</span></span>

```xml
<system.web>
   <authentication mode="Forms">
      <forms cookieSameSite="Lax">
         <!-- ...   -->
      </forms>
   <authentication />
   <sessionSate cookieSameSite="Lax"></sessionState>
</system.web>
```

<a name="net472" />

#### <a name="networking"></a><span data-ttu-id="fcb44-283">Sítě</span><span class="sxs-lookup"><span data-stu-id="fcb44-283">Networking</span></span>

<span data-ttu-id="fcb44-284">**Implementace vlastností HttpClientHandler**</span><span class="sxs-lookup"><span data-stu-id="fcb44-284">**Implementation of HttpClientHandler properties**</span></span>

<span data-ttu-id="fcb44-285">.NET Framework 4.7.1 přidal do třídy <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> osm vlastností.</span><span class="sxs-lookup"><span data-stu-id="fcb44-285">.NET Framework 4.7.1 added eight properties to the <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="fcb44-286">Nicméně dvě vyvolaly <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-286">However, two threw a <xref:System.PlatformNotSupportedException>.</span></span> <span data-ttu-id="fcb44-287">.NET Framework 4.7.2 nyní poskytuje implementaci těchto vlastností.</span><span class="sxs-lookup"><span data-stu-id="fcb44-287">.NET Framework 4.7.2 now provides an implementation for these properties.</span></span> <span data-ttu-id="fcb44-288">Vlastnosti jsou:</span><span class="sxs-lookup"><span data-stu-id="fcb44-288">The properties are:</span></span>

- <xref:System.Net.Http.HttpClientHandler.CheckCertificateRevocationList>
- <xref:System.Net.Http.HttpClientHandler.SslProtocols>

<a name="sql472" />

#### <a name="sqlclient"></a><span data-ttu-id="fcb44-289">SQLClient</span><span class="sxs-lookup"><span data-stu-id="fcb44-289">SQLClient</span></span>

<span data-ttu-id="fcb44-290">**Podpora Azure Active Directory univerzálního ověřování a Multi-Factor Authentication**</span><span class="sxs-lookup"><span data-stu-id="fcb44-290">**Support for Azure Active Directory Universal Authentication and Multi-Factor authentication**</span></span>

<span data-ttu-id="fcb44-291">Rostoucí požadavky na dodržování předpisů a požadavky na zabezpečení vyžadují, aby spousta zákazníků používala vícefaktorové ověřování (MFA).</span><span class="sxs-lookup"><span data-stu-id="fcb44-291">Growing compliance and security demands require that many customers use multi-factor authentication (MFA).</span></span> <span data-ttu-id="fcb44-292">Kromě toho aktuální osvědčené postupy zabrání zahrnutí uživatelských hesel přímo v připojovacích řetězcích.</span><span class="sxs-lookup"><span data-stu-id="fcb44-292">In addition, current best practices discourage including user passwords directly in connection strings.</span></span> <span data-ttu-id="fcb44-293">Pro podporu těchto změn .NET Framework 4.7.2 rozšiřuje [připojovací řetězce SqlClient](xref:System.Data.SqlClient.SqlConnection.ConnectionString) přidáním nové hodnoty "Active Directory Interactive" pro stávající klíčové slovo "ověřování" pro podporu MFA a [ověřování Azure AD](/azure/sql-database/sql-database-aad-authentication-configure).</span><span class="sxs-lookup"><span data-stu-id="fcb44-293">To support these changes, .NET Framework 4.7.2 extends [SQLClient connection strings](xref:System.Data.SqlClient.SqlConnection.ConnectionString) by adding a new value, "Active Directory Interactive", for the existing "Authentication" keyword to support MFA and [Azure AD Authentication](/azure/sql-database/sql-database-aad-authentication-configure).</span></span> <span data-ttu-id="fcb44-294">Nová interaktivní metoda podporuje uživatele v rámci nativních a federovaných uživatelů Azure AD i uživatele typu Host služby Azure AD.</span><span class="sxs-lookup"><span data-stu-id="fcb44-294">The new interactive method supports native and federated Azure AD users as well as Azure AD guest users.</span></span> <span data-ttu-id="fcb44-295">Při použití této metody se pro databáze SQL podporuje ověřování MFA, které ukládá služba Azure AD.</span><span class="sxs-lookup"><span data-stu-id="fcb44-295">When this method is used, the MFA authentication imposed by Azure AD is supported for SQL databases.</span></span> <span data-ttu-id="fcb44-296">Kromě toho proces ověřování požaduje heslo uživatele, aby dodržoval osvědčené postupy zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="fcb44-296">In addition, the authentication process requests a user password to adhere to security best practices.</span></span>

<span data-ttu-id="fcb44-297">V předchozích verzích .NET Framework připojení SQL podporovalo pouze možnosti <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryPassword?displayProperty=nameWithType> a <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryIntegrated?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-297">In previous versions of the .NET Framework, SQL connectivity supported only the <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryPassword?displayProperty=nameWithType> and <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryIntegrated?displayProperty=nameWithType> options.</span></span> <span data-ttu-id="fcb44-298">Obě tyto součásti jsou součástí neinteraktivního [protokolu ADAL](/azure/active-directory/develop/active-directory-authentication-libraries), který nepodporuje vícefaktorové ověřování.</span><span class="sxs-lookup"><span data-stu-id="fcb44-298">Both of these are part of the non-interactive [ADAL protocol](/azure/active-directory/develop/active-directory-authentication-libraries), which does not support MFA.</span></span> <span data-ttu-id="fcb44-299">Díky nové možnosti <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryInteractive?displayProperty=nameWithType> podporuje konektivita SQL VÍCEFAKTOROVÉ ověřování a taky existující metody ověřování (heslo a integrované ověřování), které uživatelům umožňují zadat uživatelská hesla interaktivně, aniž by museli uchovávat hesla v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="fcb44-299">With the new <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryInteractive?displayProperty=nameWithType> option, SQL connectivity supports MFA as well as existing authentication methods (password and integrated authentication), which allows users to enter user passwords interactively without persisting passwords in the connection string.</span></span>

<span data-ttu-id="fcb44-300">Další informace a příklad najdete v tématu Podpora SQL--Azure AD Universal a Multi-Factor Authentication na [blogu .NET](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).</span><span class="sxs-lookup"><span data-stu-id="fcb44-300">For more information and an example, see "SQL -- Azure AD Universal and Multi-factor Authentication Support" in the [.NET Blog](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).</span></span>

<span data-ttu-id="fcb44-301">**Podpora pro Always Encrypted verze 2**</span><span class="sxs-lookup"><span data-stu-id="fcb44-301">**Support for Always Encrypted version 2**</span></span>

<span data-ttu-id="fcb44-302">NET Framework 4.7.2 přidává podporu pro Always Encrypted založenou na enklávy.</span><span class="sxs-lookup"><span data-stu-id="fcb44-302">NET Framework 4.7.2 adds supports for enclave-based Always Encrypted.</span></span> <span data-ttu-id="fcb44-303">Původní verze Always Encrypted je technologie šifrování na straně klienta, ve které šifrovací klíče nikdy nenechávají klienta.</span><span class="sxs-lookup"><span data-stu-id="fcb44-303">The original version of Always Encrypted is a client-side encryption technology in which encryption keys never leave the client.</span></span> <span data-ttu-id="fcb44-304">V Always Encrypted založeném na enklávy může klient volitelně odesílat šifrovací klíče na zabezpečený enklávy, což je zabezpečená výpočetní entita, kterou je možné považovat za součást SQL Server, ale SQL Server kód nemůže manipulovat.</span><span class="sxs-lookup"><span data-stu-id="fcb44-304">In enclave-based Always Encrypted, the client can optionally send the encryption keys to a secure enclave, which is a secure computational entity that can be considered part of SQL Server but that SQL Server code cannot tamper with.</span></span> <span data-ttu-id="fcb44-305">Pro podporu Always Encrypted založeného na enklávy, .NET Framework 4.7.2 přidá následující typy a členy do oboru názvů <xref:System.Data.SqlClient>:</span><span class="sxs-lookup"><span data-stu-id="fcb44-305">To support enclave-based Always Encrypted, .NET Framework 4.7.2 adds the following types and members to the <xref:System.Data.SqlClient> namespace:</span></span>

- <span data-ttu-id="fcb44-306"><xref:System.Data.SqlClient.SqlConnectionStringBuilder.EnclaveAttestationUrl?displayProperty=nameWithType>, který určuje identifikátor URI pro Always Encrypted založenou na enklávy.</span><span class="sxs-lookup"><span data-stu-id="fcb44-306"><xref:System.Data.SqlClient.SqlConnectionStringBuilder.EnclaveAttestationUrl?displayProperty=nameWithType>, which specifies the Uri for enclave-based Always Encrypted.</span></span>

- <span data-ttu-id="fcb44-307"><xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider>, což je abstraktní třída, ze které jsou odvozeni všichni poskytovatelé enklávy.</span><span class="sxs-lookup"><span data-stu-id="fcb44-307"><xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider>, which is an abstract class from which all enclave providers are derived.</span></span>

- <span data-ttu-id="fcb44-308"><xref:System.Data.SqlClient.SqlEnclaveSession>, který zapouzdřuje stav pro danou relaci enklávy.</span><span class="sxs-lookup"><span data-stu-id="fcb44-308"><xref:System.Data.SqlClient.SqlEnclaveSession>, which encapsulates the state for a given enclave session.</span></span>

- <span data-ttu-id="fcb44-309"><xref:System.Data.SqlClient.SqlEnclaveAttestationParameters>, který poskytuje parametry ověření identity používané SQL Server k získání informací potřebných ke spuštění konkrétního protokolu ověření identity.</span><span class="sxs-lookup"><span data-stu-id="fcb44-309"><xref:System.Data.SqlClient.SqlEnclaveAttestationParameters>, which provides the attestation parameters used by SQL Server to get information required to execute a particular Attestation Protocol.</span></span>

<span data-ttu-id="fcb44-310">Konfigurační soubor aplikace pak určí konkrétní implementaci abstraktní třídy <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider?displayProperty=nameWithType>, která poskytuje funkce pro poskytovatele enklávy.</span><span class="sxs-lookup"><span data-stu-id="fcb44-310">The application configuration file then specifies a concrete implementation of the abstract <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider?displayProperty=nameWithType> class that provides the functionality for the enclave provider.</span></span> <span data-ttu-id="fcb44-311">Příklad:</span><span class="sxs-lookup"><span data-stu-id="fcb44-311">For example:</span></span>

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

<span data-ttu-id="fcb44-312">Základní tok Always Encrypted založeného na enklávy:</span><span class="sxs-lookup"><span data-stu-id="fcb44-312">The basic flow of enclave-based Always Encrypted is:</span></span>

1. <span data-ttu-id="fcb44-313">Uživatel vytvoří připojení AlwaysEncrypted k SQL Server, která podporuje Always Encrypted založenou na enklávy.</span><span class="sxs-lookup"><span data-stu-id="fcb44-313">The user creates an AlwaysEncrypted connection to SQL Server that supported enclave-based Always Encrypted.</span></span> <span data-ttu-id="fcb44-314">Ovladač kontaktuje službu ověření identity, aby zajistil, že se připojí k pravé enklávy.</span><span class="sxs-lookup"><span data-stu-id="fcb44-314">The driver contacts the attestation service to ensure that it is connecting to right enclave.</span></span>

1. <span data-ttu-id="fcb44-315">Po ověření enklávy ovladač vytvoří zabezpečený kanál se zabezpečeným enklávy hostovaným na SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fcb44-315">Once the enclave has been attested, the driver establishes a secure channel with the secure enclave hosted on SQL Server.</span></span>

1. <span data-ttu-id="fcb44-316">Ovladač sdílí šifrovací klíče autorizované klientem s zabezpečeným enklávy po dobu trvání připojení SQL.</span><span class="sxs-lookup"><span data-stu-id="fcb44-316">The driver shares encryption keys authorized by the client with the secure enclave for the duration of the SQL connection.</span></span>

<a name="wpf472" />

#### <a name="windows-presentation-foundation"></a><span data-ttu-id="fcb44-317">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="fcb44-317">Windows Presentation Foundation</span></span>

<span data-ttu-id="fcb44-318">**Hledání třídách ResourceDictionaries podle zdroje**</span><span class="sxs-lookup"><span data-stu-id="fcb44-318">**Finding ResourceDictionaries by Source**</span></span>

<span data-ttu-id="fcb44-319">Počínaje .NET Framework 4.7.2 může diagnostický pomocník najít adresu @ no__t-0, která byla vytvořena z daného zdrojového identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="fcb44-319">Starting with .NET Framework 4.7.2, a diagnostic assistant can locate the <xref:System.Windows.Xps.Packaging.IXpsFixedPageReader.ResourceDictionaries> that have been created from a given source Uri.</span></span><span data-ttu-id="fcb44-320"> (Tato funkce se používá pro diagnostické asistenty, nikoli pro produkční aplikace.) Pomocník pro diagnostiku, jako je "Edit-and-Continue" sady Visual Studio, umožňuje svému uživateli upravit ResourceDictionary s záměrem, aby se změny projevily u běžící aplikace.</span><span class="sxs-lookup"><span data-stu-id="fcb44-320"> (This feature is for use by diagnostic assistants, not by production applications.) A diagnostic assistant such as Visual Studio’s “Edit-and-Continue” facility lets its user edit a ResourceDictionary with the intent that the changes be applied to the running application.</span></span> <span data-ttu-id="fcb44-321">V tomto kroku najdete všechny třídách ResourceDictionaries, které spuštěná aplikace vytvořila ze upravovaného slovníku.</span><span class="sxs-lookup"><span data-stu-id="fcb44-321">One step in achieving this is finding all the ResourceDictionaries that the running application has created from the dictionary that’s being edited.</span></span> <span data-ttu-id="fcb44-322">Například aplikace může deklarovat ResourceDictionary, jehož obsah je zkopírován z daného zdrojového identifikátoru URI:</span><span class="sxs-lookup"><span data-stu-id="fcb44-322">For example, an application can declare a ResourceDictionary whose content is copied from a given source URI:</span></span>

```xml
<ResourceDictionary Source="MyRD.xaml">
```

<span data-ttu-id="fcb44-323">Diagnostický pomocník, který upravuje původní kód v souboru *MyRD. xaml* can k vyhledání slovníku použijte novou funkci.</span><span class="sxs-lookup"><span data-stu-id="fcb44-323">A diagnostic assistant that edits the original markup in *MyRD.xaml* can use the new feature to locate the dictionary.</span></span><span data-ttu-id="fcb44-324"> Tato funkce je implementována novou statickou metodou <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetResourceDictionariesForSource%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-324"> The feature is implemented by a new static method, <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetResourceDictionariesForSource%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fcb44-325">Pomocník diagnostiky volá novou metodu pomocí absolutního identifikátoru URI, který identifikuje původní kód, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="fcb44-325">The diagnostic assistant calls the new method using an absolute Uri that identifies the original markup, as illustrated by the following code:</span></span>

```csharp
IEnumerable<ResourceDictionary> dictionaries = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(new Uri("pack://application:,,,/MyApp;component/MyRD.xaml"));
```

```vb
Dim dictionaries As IEnumerable(Of ResourceDictionary) = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(New Uri("pack://application:,,,/MyApp;component/MyRD.xaml"))
```

<span data-ttu-id="fcb44-326">Metoda vrátí prázdný Výčtový, pokud není hodnota @ no__t-0 povolená [@no__t](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)a je nastavena proměnná  environment-.</span><span class="sxs-lookup"><span data-stu-id="fcb44-326">The method returns an empty enumerable unless <xref:System.Windows.Diagnostics.VisualDiagnostics> is enabled and the [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) environment variable is set.</span></span>

<span data-ttu-id="fcb44-327">**Hledání vlastníků ResourceDictionary**</span><span class="sxs-lookup"><span data-stu-id="fcb44-327">**Finding ResourceDictionary owners**</span></span>

<span data-ttu-id="fcb44-328">Počínaje .NET Framework 4.7.2 může pomocník pro diagnostiku najít vlastníky daného <xref:Windows.UI.Xaml.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-328">Starting with .NET Framework 4.7.2, a diagnostic assistant can locate the owners of a given <xref:Windows.UI.Xaml.ResourceDictionary>.</span></span><span data-ttu-id="fcb44-329"> (Tato funkce je určena pro diagnostické asistenty, nikoli pro produkční aplikace.) Pokaždé, když je provedena změna <xref:Windows.UI.Xaml.ResourceDictionary>, WPF automaticky najde všechny odkazy na [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) , které mohou být ovlivněny změnou.</span><span class="sxs-lookup"><span data-stu-id="fcb44-329"> (The feature is for use by diagnostic assistants and not by production applications.) Whenever a change is made to a <xref:Windows.UI.Xaml.ResourceDictionary>, WPF automatically finds all [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) references that might be affected by the change.</span></span>

<span data-ttu-id="fcb44-330">Může to vést k tomu, že nástroj pro diagnostiku, jako je například "Edit-and-Continue" sady Visual Studio, může tuto funkci zvětšit a zpracovat odkazy [StaticResource](../wpf/advanced/staticresource-markup-extension.md) .</span><span class="sxs-lookup"><span data-stu-id="fcb44-330">A diagnostic assistant such as Visual Studio’s “Edit-and-Continue” facility may want extend this to handle [StaticResource](../wpf/advanced/staticresource-markup-extension.md) references.</span></span> <span data-ttu-id="fcb44-331">Prvním krokem v tomto procesu je vyhledání vlastníků slovníku; To znamená, že chcete najít všechny objekty, jejichž vlastnost `Resources` odkazuje na slovník (buď přímo, nebo nepřímo prostřednictvím vlastnosti <xref:System.Windows.ResourceDictionary.MergedDictionaries?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="fcb44-331">The first step in this process is to find the owners of the dictionary; that is, to find all the objects whose `Resources` property refers to the dictionary (either directly, or indirectly via the <xref:System.Windows.ResourceDictionary.MergedDictionaries?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="fcb44-332">Tři nové statické metody implementované na třídě <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics?displayProperty=nameWithType>, jeden pro každý ze základních typů s vlastností `Resources`, podporují tento krok:</span><span class="sxs-lookup"><span data-stu-id="fcb44-332">Three new static methods implemented on the <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics?displayProperty=nameWithType> class, one for each of the base types that has a `Resources` property, support this step:</span></span>

- [`public static IEnumerable<FrameworkElement> GetFrameworkElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkElementOwners%2A)

- [`public static IEnumerable<FrameworkContentElement> GetFrameworkContentElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkContentElementOwners%2A)

- [`public static IEnumerable<Application> GetApplicationOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetApplicationOwners%2A)

<span data-ttu-id="fcb44-333">Tyto metody vrátí prázdný vyčíslitelné, pokud není povolená hodnota @ no__t-0 a je nastavená proměnná [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) environment.</span><span class="sxs-lookup"><span data-stu-id="fcb44-333">These methods return an empty enumerable unless <xref:System.Windows.Diagnostics.VisualDiagnostics> is enabled and the [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) environment variable is set.</span></span>

<span data-ttu-id="fcb44-334">**Hledání odkazů na StaticResource**</span><span class="sxs-lookup"><span data-stu-id="fcb44-334">**Finding StaticResource references**</span></span>

<span data-ttu-id="fcb44-335">Diagnostika pomocníka teď může obdržet oznámení vždy, když se vyřeší odkaz na [StaticResource](../wpf/advanced/staticresource-markup-extension.md) .</span><span class="sxs-lookup"><span data-stu-id="fcb44-335">A diagnostic assistant can now receive a notification whenever a [StaticResource](../wpf/advanced/staticresource-markup-extension.md) reference is resolved.</span></span><span data-ttu-id="fcb44-336"> (Tato funkce se používá pro diagnostické asistenty, nikoli pro produkční aplikace.) Nástroj pro diagnostiku, jako je například zařízení "Edit-and-Continue" sady Visual Studio, může chtít aktualizovat všechna použití prostředku při změně hodnoty <xref:Windows.UI.Xaml.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-336"> (The feature is for use by diagnostic assistants, not by production applications.) A diagnostic assistant such as Visual Studio’s “Edit-and-Continue” facility may want to update all uses of a resource when its value in a <xref:Windows.UI.Xaml.ResourceDictionary> changes.</span></span> <span data-ttu-id="fcb44-337">WPF to provede automaticky pro [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) odkazy, ale záměrně to neudělá pro odkazy [StaticResource](../wpf/advanced/staticresource-markup-extension.md) .</span><span class="sxs-lookup"><span data-stu-id="fcb44-337">WPF does this automatically for [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) references, but it intentionally does not do so for [StaticResource](../wpf/advanced/staticresource-markup-extension.md) references.</span></span> <span data-ttu-id="fcb44-338">Od .NET Framework 4.7.2 může pomocník diagnostiky použít tato oznámení k vyhledání těchto použití statického prostředku.</span><span class="sxs-lookup"><span data-stu-id="fcb44-338">Starting with .NET Framework 4.7.2, the diagnostic assistant can use these notifications to locate those uses of the static resource.</span></span>

<span data-ttu-id="fcb44-339">Oznámení je implementováno novou událostí <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.StaticResourceResolved?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="fcb44-339">The notification is implemented by the new <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.StaticResourceResolved?displayProperty=nameWithType> event:</span></span>

```csharp
public static event EventHandler<StaticResourceResolvedEventArgs> StaticResourceResolved;
```

```vb
Public Shared Event StaticResourceResolved As EventHandler(Of StaticResourceResolvedEventArgs)
```

<span data-ttu-id="fcb44-340">Tato událost je vyvolána pokaždé, když modul runtime vyřeší odkaz [StaticResource](../wpf/advanced/staticresource-markup-extension.md) .</span><span class="sxs-lookup"><span data-stu-id="fcb44-340">This event is raised whenever the runtime resolves a [StaticResource](../wpf/advanced/staticresource-markup-extension.md) reference.</span></span><span data-ttu-id="fcb44-341"> Argumenty <xref:System.Windows.Diagnostics.StaticResourceResolvedEventArgs> popisují rozlišení a označují objekt a vlastnost, které hostují odkaz [StaticResource](../wpf/advanced/staticresource-markup-extension.md) a parametr @ no__t-2 a klíč, který se používá pro řešení:</span><span class="sxs-lookup"><span data-stu-id="fcb44-341"> The <xref:System.Windows.Diagnostics.StaticResourceResolvedEventArgs> arguments describe the resolution, and indicate the object and property that host the [StaticResource](../wpf/advanced/staticresource-markup-extension.md) reference and the <xref:Windows.UI.Xaml.ResourceDictionary> and key used for the resolution:</span></span>

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

<span data-ttu-id="fcb44-342">Událost není vyvolána (a jeho `add` přístupového objektu se ignoruje), pokud není povolená hodnota @ no__t-1 a je nastavená proměnná [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) environment.</span><span class="sxs-lookup"><span data-stu-id="fcb44-342">The event is not raised (and its `add` accessor is ignored) unless <xref:System.Windows.Diagnostics.VisualDiagnostics> is enabled and the [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) environment variable is set.</span></span>

#### <a name="clickonce"></a><span data-ttu-id="fcb44-343">ClickOnce</span><span class="sxs-lookup"><span data-stu-id="fcb44-343">ClickOnce</span></span>

<span data-ttu-id="fcb44-344">HDPI aplikace pro model Windows Forms, Windows Presentation Foundation (WPF) a Visual Studio Tools for Office (VSTO) se dají nasadit pomocí technologie ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="fcb44-344">HDPI-aware applications for Windows Forms, Windows Presentation Foundation (WPF), and Visual Studio Tools for Office (VSTO) can all be deployed by using ClickOnce.</span></span> <span data-ttu-id="fcb44-345">Pokud je v manifestu aplikace nalezen následující záznam, nasazení bude úspěšné v části .NET Framework 4.7.2:</span><span class="sxs-lookup"><span data-stu-id="fcb44-345">If the following entry is found in the application manifest, deployment will succeed under .NET Framework 4.7.2:</span></span>

```xml
<windowsSettings>
   <dpiAware xmlns="http://schemas.microsoft.com/SMI/2005/WindowsSettings">true</dpiAware>
</windowsSettings>
```

<span data-ttu-id="fcb44-346">V případě model Windows Forms aplikace není pro úspěšné nasazení ClickOnce předchozí alternativní řešení nastavení zvyšování rozlišení DPI v konfiguračním souboru aplikace, a ne jako manifest aplikace, již nutné.</span><span class="sxs-lookup"><span data-stu-id="fcb44-346">For Windows Forms application, the previous workaround of setting DPI awareness in the application configuration file rather than the application manifest is no longer necessary for ClickOnce deployment to succeed.</span></span>

<a name="v471" />

## <a name="whats-new-in-net-framework-471"></a><span data-ttu-id="fcb44-347">Co je nového v .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="fcb44-347">What's new in .NET Framework 4.7.1</span></span>

<span data-ttu-id="fcb44-348">.NET Framework 4.7.1 zahrnuje nové funkce v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="fcb44-348">.NET Framework 4.7.1 includes new features in the following areas:</span></span>

- [<span data-ttu-id="fcb44-349">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="fcb44-349">Base classes</span></span>](#core471)
- [<span data-ttu-id="fcb44-350">Modul CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="fcb44-350">Common language runtime (CLR)</span></span>](#clr)
- [<span data-ttu-id="fcb44-351">Sítě</span><span class="sxs-lookup"><span data-stu-id="fcb44-351">Networking</span></span>](#net471)
- [<span data-ttu-id="fcb44-352">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="fcb44-352">ASP.NET</span></span>](#asp-net471)

<span data-ttu-id="fcb44-353">Navíc je hlavní fokus v .NET Framework 4.7.1 vylepšený přístupnost, což aplikaci umožňuje zajistit vhodné prostředí pro uživatele technologie usnadnění.</span><span class="sxs-lookup"><span data-stu-id="fcb44-353">In addition, a major focus in .NET Framework 4.7.1 is improved accessibility, which allows an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="fcb44-354">Informace o vylepšeních usnadnění v .NET Framework 4.7.1 najdete v tématu [co je nového v přístupnosti v .NET Framework](whats-new-in-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-354">For information on accessibility improvements in .NET Framework 4.7.1, see [What's new in accessibility in the .NET Framework](whats-new-in-accessibility.md).</span></span>

<a name="core471" />

#### <a name="base-classes"></a><span data-ttu-id="fcb44-355">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="fcb44-355">Base classes</span></span>

<span data-ttu-id="fcb44-356">**Podpora pro .NET Standard 2,0**</span><span class="sxs-lookup"><span data-stu-id="fcb44-356">**Support for .NET Standard 2.0**</span></span>

<span data-ttu-id="fcb44-357">[.NET Standard](../../standard/net-standard.md) definuje sadu rozhraní API, která musí být k dispozici v každé implementaci rozhraní .NET, která podporuje tuto verzi standardu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-357">[.NET Standard](../../standard/net-standard.md) defines a set of APIs that must be available on each .NET implementation that supports that version of the standard.</span></span> <span data-ttu-id="fcb44-358">.NET Framework 4.7.1 plně podporuje .NET Standard 2,0 a přidává [asi 200 rozhraní API](https://github.com/dotnet/standard/blob/master/netstandard/src/ApiCompatBaseline.net461.txt) , která jsou definována v .NET Standard 2,0 a chybí v .NET Framework 4.6.1, 4.6.2 a 4,7.</span><span class="sxs-lookup"><span data-stu-id="fcb44-358">.NET Framework 4.7.1 fully supports .NET Standard 2.0 and adds [about 200 APIs](https://github.com/dotnet/standard/blob/master/netstandard/src/ApiCompatBaseline.net461.txt) that are defined in .NET Standard 2.0 and are missing from .NET Framework 4.6.1, 4.6.2, and 4.7.</span></span> <span data-ttu-id="fcb44-359">(Upozorňujeme, že tyto verze .NET Framework podporují .NET Standard 2,0 pouze v případě, že jsou do cílového systému nasazeny také další .NET Standard podpůrné soubory.) Další informace najdete v příspěvku na blogu o podpoře BCL-.NET Standard 2,0 v tématu [.NET Framework 4.7.1 runtime a funkce kompilátoru](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) .</span><span class="sxs-lookup"><span data-stu-id="fcb44-359">(Note that these versions of the .NET Framework support .NET Standard 2.0 only if additional .NET Standard support files are also deployed on the target system.) For more information, see "BCL - .NET Standard 2.0 Support" in the [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog post.</span></span>

<span data-ttu-id="fcb44-360">**Podpora pro sestavovatele konfigurace**</span><span class="sxs-lookup"><span data-stu-id="fcb44-360">**Support for configuration builders**</span></span>

<span data-ttu-id="fcb44-361">Tvůrci konfigurace umožňují vývojářům dynamicky vkládat a sestavovat nastavení konfigurace pro aplikace v době běhu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-361">Configuration builders allow developers to inject and build configuration settings for applications dynamically at run time.</span></span> <span data-ttu-id="fcb44-362">Vlastní tvůrci konfigurace lze použít k úpravě existujících dat v konfiguračním oddílu nebo k sestavení konfiguračního oddílu úplně od začátku.</span><span class="sxs-lookup"><span data-stu-id="fcb44-362">Custom configuration builders can be used to modify existing data in a configuration section or to build a configuration section entirely from scratch.</span></span> <span data-ttu-id="fcb44-363">Bez konfiguračních tvůrců, soubory. config jsou statické a jejich nastavení je definováno určitou dobu před spuštěním aplikace.</span><span class="sxs-lookup"><span data-stu-id="fcb44-363">Without configuration builders, .config files are static, and their settings are defined some time before an application is launched.</span></span>

<span data-ttu-id="fcb44-364">Chcete-li vytvořit vlastního tvůrce konfigurace, odvozujete svého tvůrce od abstraktní třídy <xref:System.Configuration.ConfigurationBuilder> a přepište jeho <xref:System.Configuration.ConfigurationBuilder.ProcessConfigurationSection%2A?displayProperty=nameWithType> a <xref:System.Configuration.ConfigurationBuilder.ProcessRawXml%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-364">To create a custom configuration builder, you derive your builder from the abstract <xref:System.Configuration.ConfigurationBuilder> class and override its <xref:System.Configuration.ConfigurationBuilder.ProcessConfigurationSection%2A?displayProperty=nameWithType> and <xref:System.Configuration.ConfigurationBuilder.ProcessRawXml%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fcb44-365">Můžete také definovat své sestavovatele v souboru. config.</span><span class="sxs-lookup"><span data-stu-id="fcb44-365">You also define your builders in your .config file.</span></span> <span data-ttu-id="fcb44-366">Další informace najdete v části "tvůrci konfigurace" v příspěvku na blogu [.NET Framework 4.7.1 ASP.NET a konfigurační funkce](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) .</span><span class="sxs-lookup"><span data-stu-id="fcb44-366">For more information, see the "Configuration Builders" section in the [.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog post.</span></span>

<span data-ttu-id="fcb44-367">**Detekce funkcí za běhu**</span><span class="sxs-lookup"><span data-stu-id="fcb44-367">**Run-time feature detection**</span></span>

<span data-ttu-id="fcb44-368">Třída <xref:System.Runtime.CompilerServices.RuntimeFeature?displayProperty=nameWithType> poskytuje mechanismus pro určení, zda je předdefinovaná funkce v dané implementaci rozhraní .NET podporována v době kompilace nebo v době běhu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-368">The <xref:System.Runtime.CompilerServices.RuntimeFeature?displayProperty=nameWithType> class provides a mechanism for determine whether a predefined feature is supported on a given .NET implementation at compile time or run time.</span></span> <span data-ttu-id="fcb44-369">V době kompilace může kompilátor ověřit, zda zadané pole existuje k určení, zda je funkce podporována. Pokud ano, může vygenerovat kód, který tuto funkci využívá.</span><span class="sxs-lookup"><span data-stu-id="fcb44-369">At compile time, a compiler can check whether a specified field exists to determine whether the feature is supported; if so, it can emit code that takes advantage of that feature.</span></span> <span data-ttu-id="fcb44-370">V době spuštění aplikace může volat metodu <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported%2A?displayProperty=nameWithType> před vygenerováním kódu za běhu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-370">At run time, an application can call the <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported%2A?displayProperty=nameWithType> method before emitting code at runtime.</span></span> <span data-ttu-id="fcb44-371">Další informace najdete v tématu [Přidání pomocné metody pro popis funkcí podporovaných modulem runtime](https://github.com/dotnet/corefx/issues/17116).</span><span class="sxs-lookup"><span data-stu-id="fcb44-371">For more information, see [Add helper method to describe features supported by the runtime](https://github.com/dotnet/corefx/issues/17116).</span></span>

<span data-ttu-id="fcb44-372">**Typy řazené kolekce členů mají hodnotu serializovat.**</span><span class="sxs-lookup"><span data-stu-id="fcb44-372">**Value tuple types are serializable**</span></span>

<span data-ttu-id="fcb44-373">Počínaje .NET Framework 4.7.1, <xref:System.ValueTuple?displayProperty=nameWithType> a přidružené obecné typy jsou označeny jako [serializovatelný](xref:System.SerializableAttribute), což umožňuje binární serializaci.</span><span class="sxs-lookup"><span data-stu-id="fcb44-373">Starting with .NET Framework 4.7.1, <xref:System.ValueTuple?displayProperty=nameWithType> and its associated generic types are marked as [Serializable](xref:System.SerializableAttribute), which allows binary serialization.</span></span> <span data-ttu-id="fcb44-374">To by mělo být pro snazší migraci typů řazené kolekce členů, například <xref:System.Tuple%603> a <xref:System.Tuple%604>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-374">This should make migrating Tuple types, such as <xref:System.Tuple%603> and <xref:System.Tuple%604>, to value tuple types easier.</span></span> <span data-ttu-id="fcb44-375">Další informace naleznete v příspěvku "Compiler--ValueTuple je serializovatelný" v příspěvku blogu [.NET Framework 4.7.1 runtime a funkce kompilátoru](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) .</span><span class="sxs-lookup"><span data-stu-id="fcb44-375">For more information, see "Compiler -- ValueTuple is Serializable" in the [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog post.</span></span>

<span data-ttu-id="fcb44-376">**Podpora odkazů jen pro čtení**</span><span class="sxs-lookup"><span data-stu-id="fcb44-376">**Support for read-only references**</span></span>

<span data-ttu-id="fcb44-377">.NET Framework 4.7.1 přidá <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-377">.NET Framework 4.7.1 adds the <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fcb44-378">Tento atribut používají kompilátory jazyka k označení členů, kteří mají návratový typ nebo parametry ref jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="fcb44-378">This attribute is used by language compilers to mark members that have read-only ref return types or parameters.</span></span> <span data-ttu-id="fcb44-379">Další informace najdete v příspěvku na blogu o kompilátoru – podpora pro ReadOnlyReferences v tématu [.NET Framework 4.7.1 runtime a funkce kompilátoru](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) .</span><span class="sxs-lookup"><span data-stu-id="fcb44-379">For more information, see "Compiler -- Support for ReadOnlyReferences" in the [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog post.</span></span> <span data-ttu-id="fcb44-380">Informace o vrácených hodnotách ref naleznete v tématu [ref Return Values a refC# Values (Guide)](../../csharp/programming-guide/classes-and-structs/ref-returns.md) a [ref Return (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/ref-return-values.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-380">For information on ref return values, see [Ref return values and ref locals (C# Guide)](../../csharp/programming-guide/classes-and-structs/ref-returns.md) and [Ref return values (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/ref-return-values.md).</span></span>

<a name="clr" />

#### <a name="common-language-runtime-clr"></a><span data-ttu-id="fcb44-381">Modul CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="fcb44-381">Common language runtime (CLR)</span></span>

<span data-ttu-id="fcb44-382">**Vylepšení výkonu shromažďování paměti**</span><span class="sxs-lookup"><span data-stu-id="fcb44-382">**Garbage collection performance improvements**</span></span>

<span data-ttu-id="fcb44-383">Změny uvolňování paměti (GC) v .NET Framework 4.7.1 vylepšit celkový výkon, obzvláště pro přidělení Large Object haldy (LOH).</span><span class="sxs-lookup"><span data-stu-id="fcb44-383">Changes to garbage collection (GC) in .NET Framework 4.7.1 improve overall performance, especially for Large Object Heap (LOH) allocations.</span></span> <span data-ttu-id="fcb44-384">V .NET Framework 4.7.1 se používají oddělené zámky pro objekty SOH (Small Object Heap) a přidělení LOH, což umožňuje přidělení LOH, když GC (BGC) rozloží SOH.</span><span class="sxs-lookup"><span data-stu-id="fcb44-384">In .NET Framework 4.7.1, separate locks are used for Small Object Heap (SOH) and LOH allocations, which allows LOH allocations to occur when Background GC (BGC) is sweeping the SOH.</span></span> <span data-ttu-id="fcb44-385">V důsledku toho by aplikace, které vytvářejí velký počet přidělení LOH, měly vidět snížení kolizí uzamčení přidělení a lepší výkon.</span><span class="sxs-lookup"><span data-stu-id="fcb44-385">As a result, applications that make a large number of LOH allocations should see a reduction in allocation lock contention and improved performance.</span></span> <span data-ttu-id="fcb44-386">Další informace najdete v části "prostředí runtime – vylepšení výkonu GC" v příspěvku blogu [.NET Framework 4.7.1 runtime a funkce kompilátoru](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) .</span><span class="sxs-lookup"><span data-stu-id="fcb44-386">For more information, see the "Runtime -- GC Performance Improvements" section in the [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog post.</span></span>

<a name="net471"/>

#### <a name="networking"></a><span data-ttu-id="fcb44-387">Sítě</span><span class="sxs-lookup"><span data-stu-id="fcb44-387">Networking</span></span>

<span data-ttu-id="fcb44-388">**Podpora SHA-2 pro Message. HashAlgorithm**</span><span class="sxs-lookup"><span data-stu-id="fcb44-388">**SHA-2 support for Message.HashAlgorithm**</span></span>

<span data-ttu-id="fcb44-389">V .NET Framework 4,7 a starších verzích vlastnost <xref:System.Messaging.Message.HashAlgorithm%2A?displayProperty=nameWithType> podporovala pouze hodnoty <xref:System.Messaging.HashAlgorithm.Md5?displayProperty=nameWithType> a <xref:System.Messaging.HashAlgorithm.Sha?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-389">In .NET Framework 4.7 and earlier versions, the <xref:System.Messaging.Message.HashAlgorithm%2A?displayProperty=nameWithType> property supported values of <xref:System.Messaging.HashAlgorithm.Md5?displayProperty=nameWithType> and <xref:System.Messaging.HashAlgorithm.Sha?displayProperty=nameWithType> only.</span></span> <span data-ttu-id="fcb44-390">Počínaje .NET Framework 4.7.1 jsou podporovány také <xref:System.Messaging.HashAlgorithm.Sha256?displayProperty=nameWithType>, <xref:System.Messaging.HashAlgorithm.Sha384?displayProperty=nameWithType> a <xref:System.Messaging.HashAlgorithm.Sha512?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-390">Starting with .NET Framework 4.7.1, <xref:System.Messaging.HashAlgorithm.Sha256?displayProperty=nameWithType>, <xref:System.Messaging.HashAlgorithm.Sha384?displayProperty=nameWithType>, and <xref:System.Messaging.HashAlgorithm.Sha512?displayProperty=nameWithType> are also supported.</span></span> <span data-ttu-id="fcb44-391">Určuje, zda je tato hodnota skutečně používána, záleží na službě MSMQ, protože instance <xref:System.Messaging.Message> neobsahuje žádné hodnoty hash, ale jednoduše předává hodnoty do služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="fcb44-391">Whether this value is actually used depends on MSMQ, since the <xref:System.Messaging.Message> instance itself does no hashing but simply passes on values to MSMQ.</span></span> <span data-ttu-id="fcb44-392">Další informace najdete v tomto příspěvku na blogu podpora SHA-2 pro Message. HashAlgorithm v části [.NET Framework 4.7.1 ASP.NET a konfigurační funkce](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) .</span><span class="sxs-lookup"><span data-stu-id="fcb44-392">For more information, see the "SHA-2 support for Message.HashAlgorithm" section in the [.NET Framework 4.7.1 ASP.NET and Configuration features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog post.</span></span>

<a name="asp-net471" />

#### <a name="aspnet"></a><span data-ttu-id="fcb44-393">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="fcb44-393">ASP.NET</span></span>

<span data-ttu-id="fcb44-394">**Kroky provádění v aplikacích ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="fcb44-394">**Execution steps in ASP.NET applications**</span></span>

<span data-ttu-id="fcb44-395">ASP.NET zpracovává požadavky v předdefinovaném kanálu, který zahrnuje 23 událostí.</span><span class="sxs-lookup"><span data-stu-id="fcb44-395">ASP.NET processes requests in a predefined pipeline that includes 23 events.</span></span> <span data-ttu-id="fcb44-396">ASP.NET spustí jednotlivé obslužné rutiny události jako krok provedení.</span><span class="sxs-lookup"><span data-stu-id="fcb44-396">ASP.NET executes each event handler as an execution step.</span></span> <span data-ttu-id="fcb44-397">Ve verzích ASP.NET až .NET Framework 4,7 nemůže ASP.NET z důvodu přepínání mezi nativními a spravovanými vlákny flowovat kontext spuštění.</span><span class="sxs-lookup"><span data-stu-id="fcb44-397">In versions of ASP.NET up to .NET Framework 4.7, ASP.NET can't flow the execution context due to switching between native and managed threads.</span></span> <span data-ttu-id="fcb44-398">Místo toho ASP.NET pouze selektivní toky <xref:System.Web.HttpContext>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-398">Instead, ASP.NET selectively flows only the <xref:System.Web.HttpContext>.</span></span> <span data-ttu-id="fcb44-399">Počínaje .NET Framework 4.7.1 metoda <xref:System.Web.HttpApplication.OnExecuteRequestStep(System.Action{System.Web.HttpContextBase,System.Action})?displayProperty=nameWithType> také umožňuje modulům obnovovat okolní data.</span><span class="sxs-lookup"><span data-stu-id="fcb44-399">Starting with .NET Framework 4.7.1, the <xref:System.Web.HttpApplication.OnExecuteRequestStep(System.Action{System.Web.HttpContextBase,System.Action})?displayProperty=nameWithType> method also allows modules to restore ambient data.</span></span> <span data-ttu-id="fcb44-400">Tato funkce je zaměřená na knihovny, které mají na starosti trasování, profilování, diagnostiku nebo transakce, například informace o toku spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="fcb44-400">This feature is targeted at libraries concerned with tracing, profiling, diagnostics, or transactions, for example, that care about the execution flow of the application.</span></span> <span data-ttu-id="fcb44-401">Další informace najdete v příspěvku na blogu věnovaném funkci "ASP.NET provádění kroku" v tématu [.NET Framework 4.7.1 ASP.NET a konfigurační funkce](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) .</span><span class="sxs-lookup"><span data-stu-id="fcb44-401">For more information, see the "ASP.NET Execution Step Feature" in the [.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog post.</span></span>

<span data-ttu-id="fcb44-402">**ASP.NET HttpCookie – analýza**</span><span class="sxs-lookup"><span data-stu-id="fcb44-402">**ASP.NET HttpCookie parsing**</span></span>

<span data-ttu-id="fcb44-403">.NET Framework 4.7.1 zahrnuje novou metodu <xref:System.Web.HttpCookie.TryParse%2A?displayProperty=nameWithType>, která poskytuje standardizovaný způsob, jak vytvořit objekt <xref:System.Web.HttpCookie> z řetězce a přesně přiřadit hodnoty souborů cookie, jako je datum a cesta vypršení platnosti.</span><span class="sxs-lookup"><span data-stu-id="fcb44-403">.NET Framework 4.7.1 includes a new method, <xref:System.Web.HttpCookie.TryParse%2A?displayProperty=nameWithType>, that provides a standardized way to create an <xref:System.Web.HttpCookie> object from a string and accurately assign cookie values such as expiration date and path.</span></span> <span data-ttu-id="fcb44-404">Další informace najdete v blogovém příspěvku "ASP.NET HttpCookie analyze" v blogu [.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) .</span><span class="sxs-lookup"><span data-stu-id="fcb44-404">For more information, see "ASP.NET HttpCookie parsing" in the [.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog post.</span></span>

<span data-ttu-id="fcb44-405">**Možnosti hash SHA-2 pro přihlašovací údaje ověřování ASP.NET Forms**</span><span class="sxs-lookup"><span data-stu-id="fcb44-405">**SHA-2 hash options for ASP.NET forms authentication credentials**</span></span>

<span data-ttu-id="fcb44-406">V .NET Framework 4,7 a starších verzích umožnili vývojářům ASP.NET ukládat přihlašovací údaje uživatele s hashými hesly v konfiguračních souborech pomocí MD5 nebo SHA1.</span><span class="sxs-lookup"><span data-stu-id="fcb44-406">In .NET Framework 4.7 and earlier versions, ASP.NET allowed developers to store user credentials with hashed passwords in configuration files using either MD5 or SHA1.</span></span> <span data-ttu-id="fcb44-407">Počínaje .NET Framework 4.7.1, ASP.NET podporuje také nové zabezpečené možnosti hash SHA-2, jako jsou SHA256, SHA384 a SHA512.</span><span class="sxs-lookup"><span data-stu-id="fcb44-407">Starting with .NET Framework 4.7.1, ASP.NET also supports new secure SHA-2 hash options such as SHA256, SHA384, and SHA512.</span></span> <span data-ttu-id="fcb44-408">SHA1 zůstává výchozí a v konfiguračním souboru webu lze definovat jiný algoritmus hash, který není výchozí.</span><span class="sxs-lookup"><span data-stu-id="fcb44-408">SHA1 remains the default, and a non-default hash algorithm can be defined in the web configuration file.</span></span> <span data-ttu-id="fcb44-409">Příklad:</span><span class="sxs-lookup"><span data-stu-id="fcb44-409">For example:</span></span>

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

<a name="v47" />

## <a name="whats-new-in-net-framework-47"></a><span data-ttu-id="fcb44-410">Co je nového v .NET Framework 4,7</span><span class="sxs-lookup"><span data-stu-id="fcb44-410">What's new in .NET Framework 4.7</span></span>

<span data-ttu-id="fcb44-411">.NET Framework 4,7 obsahuje nové funkce v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="fcb44-411">.NET Framework 4.7 includes new features in the following areas:</span></span>

- [<span data-ttu-id="fcb44-412">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="fcb44-412">Base classes</span></span>](#Core47)
- [<span data-ttu-id="fcb44-413">Sítě</span><span class="sxs-lookup"><span data-stu-id="fcb44-413">Networking</span></span>](#net47)
- [<span data-ttu-id="fcb44-414">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="fcb44-414">ASP.NET</span></span>](#ASP-NET47)
- [<span data-ttu-id="fcb44-415">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="fcb44-415">Windows Communication Foundation (WCF)</span></span>](#wcf47)
- [<span data-ttu-id="fcb44-416">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fcb44-416">Windows Forms</span></span>](#wf47)
- [<span data-ttu-id="fcb44-417">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="fcb44-417">Windows Presentation Foundation (WPF)</span></span>](#WPF47)

<span data-ttu-id="fcb44-418">Seznam nových rozhraní API přidaných do .NET Framework 4,7 najdete v článku [změny rozhraní api .NET Framework 4,7](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-418">For a list of new APIs added to .NET Framework 4.7, see [.NET Framework 4.7 API Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md) on GitHub.</span></span> <span data-ttu-id="fcb44-419">Seznam vylepšení funkcí a oprav chyb v .NET Framework 4,7 naleznete v části [.NET Framework 4,7 seznam změn](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-419">For a list of feature improvements and bug fixes in .NET Framework 4.7, see [.NET Framework 4.7 List of Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md) on GitHub.</span></span>  <span data-ttu-id="fcb44-420">Další informace najdete v tématu [oznámení .NET Framework 4,7](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-7/) na blogu .NET.</span><span class="sxs-lookup"><span data-stu-id="fcb44-420">For additional information, see [Announcing the .NET Framework 4.7](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-7/) in the .NET blog.</span></span>

<a name="Core47" />

#### <a name="base-classes"></a><span data-ttu-id="fcb44-421">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="fcb44-421">Base classes</span></span>

<span data-ttu-id="fcb44-422">.NET Framework 4,7 vylepšuje serializaci <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:</span><span class="sxs-lookup"><span data-stu-id="fcb44-422">.NET Framework 4.7 improves serialization by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:</span></span>

<span data-ttu-id="fcb44-423">**Vylepšená funkce s použitím kryptografie s eliptickou křivkou (ECC)** \*</span><span class="sxs-lookup"><span data-stu-id="fcb44-423">**Enhanced functionality with Elliptic Curve Cryptography (ECC)**\*</span></span>

<span data-ttu-id="fcb44-424">V .NET Framework 4,7 byly do tříd <xref:System.Security.Cryptography.ECDsa> a <xref:System.Security.Cryptography.ECDiffieHellman> přidány metody `ImportParameters(ECParameters)`, aby mohl objekt představovat již zavedený klíč.</span><span class="sxs-lookup"><span data-stu-id="fcb44-424">In .NET Framework 4.7, `ImportParameters(ECParameters)` methods were added to the <xref:System.Security.Cryptography.ECDsa> and <xref:System.Security.Cryptography.ECDiffieHellman> classes to allow for an object to represent an already-established key.</span></span> <span data-ttu-id="fcb44-425">K exportu klíče pomocí explicitních parametrů křivky byla také přidána metoda `ExportParameters(Boolean)`.</span><span class="sxs-lookup"><span data-stu-id="fcb44-425">An `ExportParameters(Boolean)` method was also added for exporting the key using explicit curve parameters.</span></span>

<span data-ttu-id="fcb44-426">.NET Framework 4,7 také přidává podporu pro další křivky (včetně sady křivek Brainpool) a přidala předdefinované definice pro usnadnění vytváření pomocí nových produkčních metod <xref:System.Security.Cryptography.ECDsa.Create%2A> a <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-426">.NET Framework 4.7 also adds support for additional curves (including the Brainpool curve suite), and has added predefined definitions for ease-of-creation through the new <xref:System.Security.Cryptography.ECDsa.Create%2A> and <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> factory methods.</span></span>

<span data-ttu-id="fcb44-427">Na GitHubu můžete vidět [příklad kryptografických vylepšení .NET Framework 4,7](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e) .</span><span class="sxs-lookup"><span data-stu-id="fcb44-427">You can see an [example of .NET Framework 4.7 cryptography improvements](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e) on GitHub.</span></span>

<span data-ttu-id="fcb44-428">**Lepší podpora kontrolních znaků DataContractJsonSerializer**</span><span class="sxs-lookup"><span data-stu-id="fcb44-428">**Better support for control characters by the DataContractJsonSerializer**</span></span>

<span data-ttu-id="fcb44-429">V .NET Framework 4,7 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> serializace řídicích znaků v souladu se standardem ECMAScript 6.</span><span class="sxs-lookup"><span data-stu-id="fcb44-429">In .NET Framework 4.7, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> serializes control characters in conformity with the ECMAScript 6 standard.</span></span> <span data-ttu-id="fcb44-430">Toto chování je ve výchozím nastavení povolené pro aplikace, které cílí na .NET Framework 4,7, a je funkce pro přihlášení k aplikacím, které běží v .NET Framework 4,7, ale cílí na předchozí verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fcb44-430">This behavior is enabled by default for applications that target .NET Framework 4.7, and is an opt-in feature for applications that are running under .NET Framework 4.7 but target a previous version of the .NET Framework.</span></span> <span data-ttu-id="fcb44-431">Další informace najdete v tématu [Změna cílení na změny v .NET Framework 4,7](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-431">For more information, see [Retargeting Changes in the .NET Framework 4.7](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).</span></span>

<a name="net47" />

#### <a name="networking"></a><span data-ttu-id="fcb44-432">Sítě</span><span class="sxs-lookup"><span data-stu-id="fcb44-432">Networking</span></span>

<span data-ttu-id="fcb44-433">.NET Framework 4,7 přidává následující funkci související se sítí:</span><span class="sxs-lookup"><span data-stu-id="fcb44-433">.NET Framework 4.7 adds the following network-related feature:</span></span>

<span data-ttu-id="fcb44-434">**Výchozí podpora operačního systému pro protokoly TLS**\*</span><span class="sxs-lookup"><span data-stu-id="fcb44-434">**Default operating system support for TLS protocols**\*</span></span>

<span data-ttu-id="fcb44-435">Zásobník protokolu TLS, který je používán součástmi <xref:System.Net.Security.SslStream?displayProperty=nameWithType> a v zásobníku nástroje, jako jsou HTTP, FTP a SMTP, umožňuje vývojářům používat výchozí protokoly TLS podporované operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="fcb44-435">The TLS stack, which is used by <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and up-stack components such as HTTP, FTP, and SMTP, allows developers to use the default TLS protocols supported by the operating system.</span></span> <span data-ttu-id="fcb44-436">Vývojáři už nemusejí mít pevně zakódování verze TLS.</span><span class="sxs-lookup"><span data-stu-id="fcb44-436">Developers need no longer hard-code a TLS version.</span></span>

<a name="ASP-NET47" />

#### <a name="aspnet"></a><span data-ttu-id="fcb44-437">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="fcb44-437">ASP.NET</span></span>

<span data-ttu-id="fcb44-438">V .NET Framework 4,7 obsahuje ASP.NET následující nové funkce:</span><span class="sxs-lookup"><span data-stu-id="fcb44-438">In .NET Framework 4.7, ASP.NET includes the following new features:</span></span>

<span data-ttu-id="fcb44-439">**Rozšiřitelnost mezipaměti objektů**</span><span class="sxs-lookup"><span data-stu-id="fcb44-439">**Object Cache Extensibility**</span></span>

<span data-ttu-id="fcb44-440">Počínaje .NET Framework 4,7 přidá ASP.NET novou sadu rozhraní API, která vývojářům umožní nahradit výchozí implementaci ASP.NET pro ukládání objektů do paměti a monitorování paměti.</span><span class="sxs-lookup"><span data-stu-id="fcb44-440">Starting with .NET Framework 4.7, ASP.NET adds a new set of APIs that allow developers to replace the default ASP.NET implementations for in-memory object caching and memory monitoring.</span></span> <span data-ttu-id="fcb44-441">Vývojáři teď můžou nahradit některou z následujících tří součástí, pokud ASP.NET implementace není adekvátní:</span><span class="sxs-lookup"><span data-stu-id="fcb44-441">Developers can now replace any of the following three components if the ASP.NET implementation is not adequate:</span></span>

- <span data-ttu-id="fcb44-442">**Úložiště mezipaměti objektů**.</span><span class="sxs-lookup"><span data-stu-id="fcb44-442">**Object Cache Store**.</span></span> <span data-ttu-id="fcb44-443">Při použití konfiguračního oddílu Noví poskytovatelé mezipaměti můžou vývojáři připojit nové implementace mezipaměti objektů pro aplikaci ASP.NET pomocí nového rozhraní **ICacheStoreProvider** .</span><span class="sxs-lookup"><span data-stu-id="fcb44-443">By using the new cache providers configuration section, developers can plug in new implementations of an object cache for an ASP.NET application by using the new **ICacheStoreProvider** interface.</span></span>

- <span data-ttu-id="fcb44-444">**Monitorování paměti**.</span><span class="sxs-lookup"><span data-stu-id="fcb44-444">**Memory monitoring**.</span></span> <span data-ttu-id="fcb44-445">Výchozí monitorování paměti v ASP.NET upozorní aplikace, když běží blízko nakonfigurovaného limitu privátních bajtů pro daný proces, nebo když má počítač nedostatek celkového dostupné fyzické paměti RAM.</span><span class="sxs-lookup"><span data-stu-id="fcb44-445">The default memory monitor in ASP.NET notifies applications when they are running close to the configured private bytes limit for the process, or when the machine is low on total available physical RAM.</span></span> <span data-ttu-id="fcb44-446">Když jsou tato omezení blízko, jsou aktivována oznámení.</span><span class="sxs-lookup"><span data-stu-id="fcb44-446">When these limits are near, notifications are fired.</span></span> <span data-ttu-id="fcb44-447">U některých aplikací se oznámení aktivují příliš blízko nakonfigurovaných limitů, aby bylo možné reakce na užitečné.</span><span class="sxs-lookup"><span data-stu-id="fcb44-447">For some applications, notifications are fired too close to the configured limits to allow for useful reactions.</span></span> <span data-ttu-id="fcb44-448">Vývojáři teď můžou zapisovat vlastní monitory paměti, které nahradí výchozí hodnotu pomocí vlastnosti <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-448">Developers can now write their own memory monitors to replace the default by using the <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=nameWithType> property.</span></span>

- <span data-ttu-id="fcb44-449">**Reakce na limit paměti**.</span><span class="sxs-lookup"><span data-stu-id="fcb44-449">**Memory Limit Reactions**.</span></span> <span data-ttu-id="fcb44-450">Ve výchozím nastavení se ASP.NET pokusí oříznout mezipaměť objektů a pravidelně volat <xref:System.GC.Collect%2A?displayProperty=nameWithType>, pokud je limit procesu privátního bajtu blízko.</span><span class="sxs-lookup"><span data-stu-id="fcb44-450">By default, ASP.NET attempts to trim the object cache and periodically call <xref:System.GC.Collect%2A?displayProperty=nameWithType> when the private byte process limit is near.</span></span> <span data-ttu-id="fcb44-451">U některých aplikací je frekvence volání <xref:System.GC.Collect%2A?displayProperty=nameWithType> nebo množství vyrovnávací paměti, které je oříznuté, neefektivní.</span><span class="sxs-lookup"><span data-stu-id="fcb44-451">For some applications, the frequency of calls to <xref:System.GC.Collect%2A?displayProperty=nameWithType> or the amount of cache that is trimmed are inefficient.</span></span> <span data-ttu-id="fcb44-452">Vývojáři teď můžou nahradit nebo doplnit výchozí chování tím, že se přihlásí k odběru **IObserver** implementace do monitorování paměti aplikace.</span><span class="sxs-lookup"><span data-stu-id="fcb44-452">Developers can now replace or supplement the default behavior by subscribing **IObserver** implementations to the application's memory monitor.</span></span>

<a name="wcf47" />

#### <a name="windows-communication-foundation-wcf"></a><span data-ttu-id="fcb44-453">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="fcb44-453">Windows Communication Foundation (WCF)</span></span>

<span data-ttu-id="fcb44-454">Windows Communication Foundation (WCF) přidá následující funkce a změny:</span><span class="sxs-lookup"><span data-stu-id="fcb44-454">Windows Communication Foundation (WCF) adds the following features and changes:</span></span>

<span data-ttu-id="fcb44-455">**Možnost konfigurovat výchozí nastavení zabezpečení zpráv na TLS 1,1 nebo TLS 1,2**</span><span class="sxs-lookup"><span data-stu-id="fcb44-455">**Ability to configure the default message security settings to TLS 1.1 or TLS 1.2**</span></span>

<span data-ttu-id="fcb44-456">Počínaje .NET Framework 4,7 umožňuje WCF nakonfigurovat kromě protokolu SSL 3,0 a TSL 1,0 i možnost TSL 1,1 nebo TLS 1,2 jako výchozí protokol zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="fcb44-456">Starting with .NET Framework 4.7, WCF allows you to configure TSL 1.1 or TLS 1.2 in addition to SSL 3.0 and TSL 1.0 as the default message security protocol.</span></span> <span data-ttu-id="fcb44-457">Toto je nastavení výslovného souhlasu; Pokud ho chcete povolit, musíte do konfiguračního souboru aplikace přidat následující položku:</span><span class="sxs-lookup"><span data-stu-id="fcb44-457">This is an opt-in setting; to enable it, you must add the following entry to your application configuration file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
</runtime>
```

<span data-ttu-id="fcb44-458">**Vylepšená spolehlivost aplikací WCF a serializace WCF**</span><span class="sxs-lookup"><span data-stu-id="fcb44-458">**Improved reliability of WCF applications and WCF serialization**</span></span>

<span data-ttu-id="fcb44-459">WCF zahrnuje řadu změn kódu, které eliminují konflikty časování, což zvyšuje výkon a spolehlivost možností serializace.</span><span class="sxs-lookup"><span data-stu-id="fcb44-459">WCF includes a number of code changes that eliminate race conditions, thereby improving performance and the reliability of serialization options.</span></span> <span data-ttu-id="fcb44-460">Mezi ně patří:</span><span class="sxs-lookup"><span data-stu-id="fcb44-460">These include:</span></span>

- <span data-ttu-id="fcb44-461">Lepší podpora pro kombinování asynchronního a synchronního kódu v voláních **Připojení SocketConnection bylo. BeginRead** a **Připojení SocketConnection bylo. Read**.</span><span class="sxs-lookup"><span data-stu-id="fcb44-461">Better support for mixing asynchronous and synchronous code in calls to **SocketConnection.BeginRead** and **SocketConnection.Read**.</span></span>
- <span data-ttu-id="fcb44-462">Lepší spolehlivost při přerušení připojení pomocí **SharedConnectionListener** a **DuplexChannelBinder**.</span><span class="sxs-lookup"><span data-stu-id="fcb44-462">Improved reliability when aborting a connection with **SharedConnectionListener** and **DuplexChannelBinder**.</span></span>
- <span data-ttu-id="fcb44-463">Zlepšená spolehlivost operací serializace při volání metody <xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-463">Improved reliability of serialization operations when calling the <xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=nameWithType> method.</span></span>
- <span data-ttu-id="fcb44-464">Lepší spolehlivost při odebírání nástroje Wait voláním metody **ChannelSynchronizer. RemoveWaiter** .</span><span class="sxs-lookup"><span data-stu-id="fcb44-464">Improved reliability when removing a waiter by calling the **ChannelSynchronizer.RemoveWaiter** method.</span></span>

<a name="wf47" />

#### <a name="windows-forms"></a><span data-ttu-id="fcb44-465">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fcb44-465">Windows Forms</span></span>

<span data-ttu-id="fcb44-466">V .NET Framework 4,7 model Windows Forms vylepšuje podporu pro monitory s vysokým rozlišením DPI.</span><span class="sxs-lookup"><span data-stu-id="fcb44-466">In .NET Framework 4.7, Windows Forms improves support for high DPI monitors.</span></span>

<span data-ttu-id="fcb44-467">**Podpora vysokého rozlišení DPI**</span><span class="sxs-lookup"><span data-stu-id="fcb44-467">**High DPI support**</span></span>

<span data-ttu-id="fcb44-468">Počínaje aplikacemi, které cílí na .NET Framework 4,7, .NET Framework funkce vysokého rozlišení DPI a podpora dynamického DPI pro model Windows Forms aplikace.</span><span class="sxs-lookup"><span data-stu-id="fcb44-468">Starting with applications that target .NET Framework 4.7, the .NET Framework features high DPI and dynamic DPI support for Windows Forms applications.</span></span> <span data-ttu-id="fcb44-469">Podpora vysokého rozlišení DPI vylepšuje rozložení a vzhled formulářů a ovládacích prvků na obrazovkách s vysokým rozlišením DPI.</span><span class="sxs-lookup"><span data-stu-id="fcb44-469">High DPI support improves the layout and appearance of forms and controls on high DPI monitors.</span></span> <span data-ttu-id="fcb44-470">Dynamické DPI mění rozložení a vzhled formulářů a ovládacích prvků, když uživatel změní v běžící aplikaci Měřítko DPI nebo zobrazení.</span><span class="sxs-lookup"><span data-stu-id="fcb44-470">Dynamic DPI changes the layout and appearance of forms and controls when the user changes the DPI or display scale factor of a running application.</span></span>

<span data-ttu-id="fcb44-471">Podpora vysokého rozlišení DPI je funkce výslovného souhlasu, kterou konfigurujete definováním oddílu [\<System. Windows. Forms. ConfigurationSection >](../configure-apps/file-schema/winforms/index.md) v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="fcb44-471">High DPI support is an opt-in feature that you configure by defining a [\<System.Windows.Forms.ConfigurationSection>](../configure-apps/file-schema/winforms/index.md) section in your application configuration file.</span></span> <span data-ttu-id="fcb44-472">Další informace o přidání podpory vysokého rozlišení DPI a dynamické podpory DPI do vaší aplikace model Windows Forms najdete [v tématu Podpora vysokého rozlišení DPI v model Windows Forms](../winforms/high-dpi-support-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-472">For more information on adding high DPI support and dynamic DPI support to your Windows Forms application, see [High DPI Support in Windows Forms](../winforms/high-dpi-support-in-windows-forms.md).</span></span>

<a name="WPF47" />

#### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="fcb44-473">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="fcb44-473">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="fcb44-474">V .NET Framework 4,7 zahrnuje WPF následující vylepšení:</span><span class="sxs-lookup"><span data-stu-id="fcb44-474">In .NET Framework 4.7, WPF includes the following enhancements:</span></span>

<span data-ttu-id="fcb44-475">**Podpora pro zásobník dotykového a stylusu založeného na WM_POINTER zprávách Windows**</span><span class="sxs-lookup"><span data-stu-id="fcb44-475">**Support for a touch/stylus stack based on Windows WM_POINTER messages**</span></span>

<span data-ttu-id="fcb44-476">Teď máte možnost použít na základě [zpráv WM_POINTER](https://docs.microsoft.com/previous-versions/windows/desktop/InputMsg/messages) místo platformy Windows Ink Services (Wispr) k dispozici tónovou nebo stylusovou sadu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-476">You now have the option of using a touch/stylus stack based on [WM_POINTER messages](https://docs.microsoft.com/previous-versions/windows/desktop/InputMsg/messages) instead of the Windows Ink Services Platform (WISP).</span></span> <span data-ttu-id="fcb44-477">Toto je funkce výslovného souhlasu v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fcb44-477">This is an opt-in feature in the .NET Framework.</span></span> <span data-ttu-id="fcb44-478">Další informace najdete v tématu [Změna cílení na změny v .NET Framework 4,7](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-478">For more information, see [Retargeting Changes in the .NET Framework 4.7](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).</span></span>

<span data-ttu-id="fcb44-479">**Nová implementace pro rozhraní API pro tisk WPF**</span><span class="sxs-lookup"><span data-stu-id="fcb44-479">**New implementation for WPF printing APIs**</span></span>

<span data-ttu-id="fcb44-480">Rozhraní API pro tisk v WPF ve třídě <xref:System.Printing.PrintQueue?displayProperty=nameWithType> volají [rozhraní API pro tisk dokumentu](/windows/desktop/printdocs/tailored-app-printing-api) Windows namísto zastaralých [tiskových rozhraní XPS](/windows/desktop/printdocs/xps-printing).</span><span class="sxs-lookup"><span data-stu-id="fcb44-480">WPF's printing APIs in the <xref:System.Printing.PrintQueue?displayProperty=nameWithType> class call the Windows [Print Document Package API](/windows/desktop/printdocs/tailored-app-printing-api) instead of the deprecated [XPS Print API](/windows/desktop/printdocs/xps-printing).</span></span> <span data-ttu-id="fcb44-481">Dopad této změny na kompatibilitu aplikací najdete v tématu [Změna cíle v .NET Framework 4,7](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-481">For the impact of this change on application compatibility, see [Retargeting Changes in the .NET Framework 4.7](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).</span></span>

<a name="v462" />

## <a name="whats-new-in-net-framework-462"></a><span data-ttu-id="fcb44-482">Co je nového v .NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="fcb44-482">What's new in .NET Framework 4.6.2</span></span>

<span data-ttu-id="fcb44-483">.NET Framework 4.6.2 zahrnuje nové funkce v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="fcb44-483">The .NET Framework 4.6.2 includes new features in the following areas:</span></span>

- [<span data-ttu-id="fcb44-484">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="fcb44-484">ASP.NET</span></span>](#ASPNET462)

- [<span data-ttu-id="fcb44-485">Kategorie znaků</span><span class="sxs-lookup"><span data-stu-id="fcb44-485">Character categories</span></span>](#Strings)

- [<span data-ttu-id="fcb44-486">Kryptografick</span><span class="sxs-lookup"><span data-stu-id="fcb44-486">Cryptography</span></span>](#Crypto462)

- [<span data-ttu-id="fcb44-487">SqlClient</span><span class="sxs-lookup"><span data-stu-id="fcb44-487">SqlClient</span></span>](#SQLClient)

- [<span data-ttu-id="fcb44-488">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="fcb44-488">Windows Communication Foundation</span></span>](#WCF)

- [<span data-ttu-id="fcb44-489">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="fcb44-489">Windows Presentation Foundation (WPF)</span></span>](#WPF462)

- [<span data-ttu-id="fcb44-490">Programovací model Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="fcb44-490">Windows Workflow Foundation (WF)</span></span>](#WF462)

- [<span data-ttu-id="fcb44-491">ClickOnce</span><span class="sxs-lookup"><span data-stu-id="fcb44-491">ClickOnce</span></span>](#clickonce-1)

- [<span data-ttu-id="fcb44-492">Převod aplikací model Windows Forms a WPF na aplikace pro UWP</span><span class="sxs-lookup"><span data-stu-id="fcb44-492">Converting Windows Forms and WPF apps to UWP apps</span></span>](#UWPConvert)

- [<span data-ttu-id="fcb44-493">Vylepšení ladění</span><span class="sxs-lookup"><span data-stu-id="fcb44-493">Debugging improvements</span></span>](#Debug462)

<span data-ttu-id="fcb44-494">Seznam nových rozhraní API přidaných do .NET Framework 4.6.2 najdete v tématu [.NET Framework změn rozhraní API 4.6.2](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-494">For a list of new APIs added to .NET Framework 4.6.2, see [.NET Framework 4.6.2 API Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) on GitHub.</span></span> <span data-ttu-id="fcb44-495">Seznam vylepšení funkcí a oprav chyb v .NET Framework 4.6.2 najdete v článku [.NET Framework 4.6.2 seznam změn](https://go.microsoft.com/fwlink/?LinkId=708778) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-495">For a list of feature improvements and bug fixes in .NET Framework 4.6.2, see [.NET Framework 4.6.2 List of Changes](https://go.microsoft.com/fwlink/?LinkId=708778) on GitHub.</span></span>  <span data-ttu-id="fcb44-496">Další informace najdete v tématu [oznámení .NET Framework 4.6.2](https://devblogs.microsoft.com/dotnet/announcing-net-framework-4-6-2/) na blogu .NET.</span><span class="sxs-lookup"><span data-stu-id="fcb44-496">For additional information, see [Announcing .NET Framework 4.6.2](https://devblogs.microsoft.com/dotnet/announcing-net-framework-4-6-2/) in the .NET blog.</span></span>

<a name="ASPNET462" />

### <a name="aspnet"></a><span data-ttu-id="fcb44-497">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="fcb44-497">ASP.NET</span></span>

<span data-ttu-id="fcb44-498">ASP.NET v .NET Framework 4.6.2 zahrnuje následující vylepšení:</span><span class="sxs-lookup"><span data-stu-id="fcb44-498">In the .NET Framework 4.6.2, ASP.NET includes the following enhancements:</span></span>

<span data-ttu-id="fcb44-499">**Vylepšená podpora pro lokalizované chybové zprávy v validátorech datových poznámek**</span><span class="sxs-lookup"><span data-stu-id="fcb44-499">**Improved support for localized error messages in data annotation validators**</span></span>

<span data-ttu-id="fcb44-500">Validátory datových poznámek umožňují provádět ověřování přidáním jednoho nebo více atributů do vlastnosti třídy.</span><span class="sxs-lookup"><span data-stu-id="fcb44-500">Data annotation validators enable you to perform validation by adding one or more attributes to a class property.</span></span> <span data-ttu-id="fcb44-501">Element <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> atributu definuje text chybové zprávy, pokud se ověření nepovede.</span><span class="sxs-lookup"><span data-stu-id="fcb44-501">The attribute's <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> element defines the text of the error message if validation fails.</span></span> <span data-ttu-id="fcb44-502">Počínaje .NET Framework 4.6.2, ASP.NET usnadňuje lokalizaci chybových zpráv.</span><span class="sxs-lookup"><span data-stu-id="fcb44-502">Starting with the .NET Framework 4.6.2, ASP.NET makes it easy to localize error messages.</span></span> <span data-ttu-id="fcb44-503">Chybové zprávy budou lokalizovány v těchto případech:</span><span class="sxs-lookup"><span data-stu-id="fcb44-503">Error messages will be localized if:</span></span>

1. <span data-ttu-id="fcb44-504">Hodnota <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> je uvedena v atributu ověřování.</span><span class="sxs-lookup"><span data-stu-id="fcb44-504">The <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> is provided in the validation attribute.</span></span>

2. <span data-ttu-id="fcb44-505">Soubor prostředků je uložen ve složce App_LocalResources.</span><span class="sxs-lookup"><span data-stu-id="fcb44-505">The resource file is stored in the App_LocalResources folder.</span></span>

3. <span data-ttu-id="fcb44-506">Název souboru lokalizovaných zdrojů má formát `DataAnnotation.Localization.{`*název*`}.resx`, kde *název* je název jazykové verze ve formátu *languageCode*`-`*Country/regionCode* nebo *languageCode*.</span><span class="sxs-lookup"><span data-stu-id="fcb44-506">The name of the localized resources file has the form `DataAnnotation.Localization.{`*name*`}.resx`, where *name* is a culture name in the format *languageCode*`-`*country/regionCode* or *languageCode*.</span></span>

4. <span data-ttu-id="fcb44-507">Klíčovým názvem prostředku je řetězec přiřazený k atributu <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> a jeho hodnota je lokalizovaná chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="fcb44-507">The key name of the resource is the string assigned to the <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> attribute,  and its value is the localized error message.</span></span>

<span data-ttu-id="fcb44-508">Například následující atribut poznámky k datům definuje chybovou zprávu výchozí jazykové verze pro neplatné hodnocení.</span><span class="sxs-lookup"><span data-stu-id="fcb44-508">For example, the following data annotation attribute defines the default culture's error message for an invalid rating.</span></span>

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

<span data-ttu-id="fcb44-509">Pak můžete vytvořit soubor prostředků, dataanotace. Localization. fr. resx, jehož klíč je řetězec chybové zprávy a jehož hodnota je lokalizovaná chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="fcb44-509">You can then create a resource file, DataAnnotation.Localization.fr.resx, whose key is the error message string and whose value is the localized error message.</span></span> <span data-ttu-id="fcb44-510">Soubor se musí nacházet ve složce `App.LocalResources`.</span><span class="sxs-lookup"><span data-stu-id="fcb44-510">The file must be found in the `App.LocalResources` folder.</span></span> <span data-ttu-id="fcb44-511">Například následující je klíč a jeho hodnota v lokalizované chybové zprávě jazyka francouzštiny (FR):</span><span class="sxs-lookup"><span data-stu-id="fcb44-511">For example, the following is the key and its value in a localized French (fr) language error message:</span></span>

| <span data-ttu-id="fcb44-512">Name</span><span class="sxs-lookup"><span data-stu-id="fcb44-512">Name</span></span>                                 | <span data-ttu-id="fcb44-513">Value</span><span class="sxs-lookup"><span data-stu-id="fcb44-513">Value</span></span>                                     |
| ------------------------------------ | ----------------------------------------- |
| <span data-ttu-id="fcb44-514">Hodnocení musí být v rozmezí od 1 do 10.</span><span class="sxs-lookup"><span data-stu-id="fcb44-514">The rating must be between 1 and 10.</span></span> | <span data-ttu-id="fcb44-515">La doit être tvoří meziplatformní 1 et 10.</span><span class="sxs-lookup"><span data-stu-id="fcb44-515">La note doit être comprise entre 1 et 10.</span></span> |

 <span data-ttu-id="fcb44-516">Lokalizace datových poznámek je navíc rozšiřitelná.</span><span class="sxs-lookup"><span data-stu-id="fcb44-516">In addition, data annotation localization is extensible.</span></span> <span data-ttu-id="fcb44-517">Vývojáři mohou připojit vlastní poskytovatele řetězcového lokalizátora implementací rozhraní @no__t 0 k uložení lokalizačního řetězce jinde než v souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="fcb44-517">Developers can plug in their own string localizer provider by implementing the <xref:System.Web.Globalization.IStringLocalizerProvider> interface to store localization string somewhere other than in a resource file.</span></span>

 <span data-ttu-id="fcb44-518">**Asynchronní podpora s poskytovateli úložiště stavu relace**</span><span class="sxs-lookup"><span data-stu-id="fcb44-518">**Async support with session-state store providers**</span></span>

 <span data-ttu-id="fcb44-519">ASP.NET teď umožňuje používat metody vracející úlohy s poskytovateli úložiště stavu relace, což aplikacím ASP.NET umožní získat výhody škálovatelnosti Async.</span><span class="sxs-lookup"><span data-stu-id="fcb44-519">ASP.NET now allows task-returning methods to be used with session-state store providers, thereby allowing ASP.NET apps to get the scalability benefits of async.</span></span> <span data-ttu-id="fcb44-520">Pro podporu asynchronních operací s poskytovateli úložiště stavu relace zahrnuje ASP.NET nové rozhraní <xref:System.Web.SessionState.ISessionStateModule?displayProperty=nameWithType>, které dědí z <xref:System.Web.IHttpModule> a umožňuje vývojářům implementovat vlastní modul stavu relace a zprostředkovatele asynchronních úložišť relací.</span><span class="sxs-lookup"><span data-stu-id="fcb44-520">To supports asynchronous operations with session state store providers, ASP.NET includes  a new interface, <xref:System.Web.SessionState.ISessionStateModule?displayProperty=nameWithType>, which inherits from <xref:System.Web.IHttpModule> and allows developers to implement their own session-state module and async session store providers.</span></span> <span data-ttu-id="fcb44-521">Rozhraní je definováno následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="fcb44-521">The interface is defined as follows:</span></span>

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

 <span data-ttu-id="fcb44-522">Kromě toho třída <xref:System.Web.SessionState.SessionStateUtility> zahrnuje dvě nové metody, <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> a <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A>, které lze použít k podpoře asynchronních operací.</span><span class="sxs-lookup"><span data-stu-id="fcb44-522">In addition, the <xref:System.Web.SessionState.SessionStateUtility> class includes two new methods, <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> and <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A>, that can be used to support asynchronous operations.</span></span>

 <span data-ttu-id="fcb44-523">**Asynchronní podpora pro poskytovatele výstupní mezipaměti**</span><span class="sxs-lookup"><span data-stu-id="fcb44-523">**Async support for output-cache providers**</span></span>

 <span data-ttu-id="fcb44-524">Počínaje .NET Framework 4.6.2 lze metody vracející úlohy použít s poskytovateli výstupní mezipaměti k zajištění výhod škálovatelnosti Async.</span><span class="sxs-lookup"><span data-stu-id="fcb44-524">Starting with the .NET Framework 4.6.2, task-returning methods can be used with output-cache providers to provide the scalability benefits of async.</span></span>  <span data-ttu-id="fcb44-525">Poskytovatelé, kteří implementují tyto metody, omezují blokování vláken na webovém serveru a zlepšují škálovatelnost služby ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fcb44-525">Providers that implement these methods reduce thread-blocking on a web server and improve the scalability of an ASP.NET service.</span></span>

 <span data-ttu-id="fcb44-526">Byla přidána následující rozhraní API pro podporu zprostředkovatelů asynchronní výstupní mezipaměti:</span><span class="sxs-lookup"><span data-stu-id="fcb44-526">The following APIs have been added to support asynchronous output-cache providers:</span></span>

- <span data-ttu-id="fcb44-527">Třída <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=nameWithType>, která dědí z <xref:System.Web.Caching.OutputCacheProvider?displayProperty=nameWithType> a umožňuje vývojářům implementovat asynchronního poskytovatele výstupní mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="fcb44-527">The <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=nameWithType> class, which inherits from <xref:System.Web.Caching.OutputCacheProvider?displayProperty=nameWithType> and allows developers to implement an asynchronous output-cache provider.</span></span>

- <span data-ttu-id="fcb44-528">Třída <xref:System.Web.Caching.OutputCacheUtility>, která poskytuje podpůrné metody pro konfiguraci výstupní mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="fcb44-528">The <xref:System.Web.Caching.OutputCacheUtility> class, which provides helper methods for configuring the output cache.</span></span>

- <span data-ttu-id="fcb44-529">18 nových metod ve třídě <xref:System.Web.HttpCachePolicy?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-529">18 new methods in the <xref:System.Web.HttpCachePolicy?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="fcb44-530">Mezi ně patří <xref:System.Web.HttpCachePolicy.GetCacheability%2A>, <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A>, <xref:System.Web.HttpCachePolicy.GetETag%2A>, <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetNoStore%2A>, <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A>, <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>, <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A>, 0, 1, 2, 3 a 4.</span><span class="sxs-lookup"><span data-stu-id="fcb44-530">These include <xref:System.Web.HttpCachePolicy.GetCacheability%2A>, <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A>, <xref:System.Web.HttpCachePolicy.GetETag%2A>, <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetNoStore%2A>, <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A>, <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>, <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetRevalidation%2A>, <xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A>, <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A>, <xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A>, and <xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A>.</span></span>

- <span data-ttu-id="fcb44-531">2 nové metody ve třídě <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=nameWithType>: <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> a <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-531">2 new methods in the <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=nameWithType> class:  <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> and <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A>.</span></span>

- <span data-ttu-id="fcb44-532">2 nové metody ve třídě <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=nameWithType>: <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> a <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-532">2 new methods in the <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=nameWithType> class: <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> and <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A>.</span></span>

- <span data-ttu-id="fcb44-533">2 nové metody ve třídě <xref:System.Web.HttpCacheVaryByParams?displayProperty=nameWithType>: <xref:System.Web.HttpCacheVaryByParams.GetParams%2A> a <xref:System.Web.HttpCacheVaryByParams.SetParams%2A>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-533">2 new methods in the <xref:System.Web.HttpCacheVaryByParams?displayProperty=nameWithType> class: <xref:System.Web.HttpCacheVaryByParams.GetParams%2A> and <xref:System.Web.HttpCacheVaryByParams.SetParams%2A>.</span></span>

- <span data-ttu-id="fcb44-534">Ve třídě <xref:System.Web.Caching.AggregateCacheDependency?displayProperty=nameWithType> se jedná o metodu <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-534">In the <xref:System.Web.Caching.AggregateCacheDependency?displayProperty=nameWithType> class, the <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A> method.</span></span>

- <span data-ttu-id="fcb44-535">V metodě <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> <xref:System.Web.Caching.CacheDependency>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-535">In the <xref:System.Web.Caching.CacheDependency>, the <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> method.</span></span>

<a name="Strings" />

### <a name="character-categories"></a><span data-ttu-id="fcb44-536">Kategorie znaků</span><span class="sxs-lookup"><span data-stu-id="fcb44-536">Character categories</span></span>

<span data-ttu-id="fcb44-537">Znaky v .NET Framework 4.6.2 jsou klasifikovány na základě [standardu Unicode verze 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/).</span><span class="sxs-lookup"><span data-stu-id="fcb44-537">Characters in the .NET Framework 4.6.2 are classified based on the [Unicode Standard, Version 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/).</span></span> <span data-ttu-id="fcb44-538">V .NET Framework 4,6 a .NET Framework 4.6.1 byly znaky klasifikovány na základě kategorií znaků Unicode 6,3.</span><span class="sxs-lookup"><span data-stu-id="fcb44-538">In .NET Framework 4.6 and .NET Framework 4.6.1, characters were classified based on Unicode 6.3 character categories.</span></span>

<span data-ttu-id="fcb44-539">Podpora pro sadu Unicode 8,0 je omezena na klasifikaci znaků pomocí třídy <xref:System.Globalization.CharUnicodeInfo> a na typy a metody, které jsou na ní závislé.</span><span class="sxs-lookup"><span data-stu-id="fcb44-539">Support for Unicode 8.0 is limited to the classification of characters by the <xref:System.Globalization.CharUnicodeInfo> class and to types and methods that rely on it.</span></span> <span data-ttu-id="fcb44-540">Mezi ně patří třída <xref:System.Globalization.StringInfo>, přetížená metoda <xref:System.Char.GetUnicodeCategory%2A?displayProperty=nameWithType> a [třídy znaků](../../standard/base-types/character-classes-in-regular-expressions.md) rozpoznávané modulem .NET Framework regulárních výrazů.</span><span class="sxs-lookup"><span data-stu-id="fcb44-540">These include the <xref:System.Globalization.StringInfo> class, the overloaded <xref:System.Char.GetUnicodeCategory%2A?displayProperty=nameWithType> method, and the [character classes](../../standard/base-types/character-classes-in-regular-expressions.md) recognized by the .NET Framework regular expression engine.</span></span>  <span data-ttu-id="fcb44-541">Porovnání znaků a řetězců a jejich řazení není ovlivněno touto změnou a nadále se spoléhá na základní operační systém nebo v systémech Windows 7 na znaková data, která poskytuje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fcb44-541">Character and string comparison and sorting is unaffected by this change and continues to rely on the underlying operating system or, on Windows 7 systems, on character data provided by the .NET Framework.</span></span>

<span data-ttu-id="fcb44-542">Změny v kategoriích znaků z Unicode 6,0 až Unicode 7,0 najdete na webu Unicode Consortium na [standardu Unicode verze 7.0.0](https://www.unicode.org/versions/Unicode7.0.0/) .</span><span class="sxs-lookup"><span data-stu-id="fcb44-542">For changes in character categories from Unicode 6.0 to Unicode 7.0, see [The Unicode Standard, Version 7.0.0](https://www.unicode.org/versions/Unicode7.0.0/) at The Unicode Consortium website.</span></span> <span data-ttu-id="fcb44-543">Změny z Unicode 7,0 na Unicode 8,0 najdete na webu Unicode Consortium na [standardu Unicode verze 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/) .</span><span class="sxs-lookup"><span data-stu-id="fcb44-543">For changes from Unicode 7.0 to Unicode 8.0, see [The Unicode Standard, Version 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/) at The Unicode Consortium website.</span></span>

<a name="Crypto462" />

### <a name="cryptography"></a><span data-ttu-id="fcb44-544">Kryptografick</span><span class="sxs-lookup"><span data-stu-id="fcb44-544">Cryptography</span></span>

<span data-ttu-id="fcb44-545">**Podpora pro certifikáty x509 obsahující FIPS 186-3 DSA**</span><span class="sxs-lookup"><span data-stu-id="fcb44-545">**Support for X509 certificates containing FIPS 186-3 DSA**</span></span>

<span data-ttu-id="fcb44-546">.NET Framework 4.6.2 přidává podporu certifikátů x509 (Digital Signature Algorithm), jejichž klíče překračují limit bitů FIPS 186-2 1024.</span><span class="sxs-lookup"><span data-stu-id="fcb44-546">The .NET Framework 4.6.2 adds support for DSA (Digital Signature Algorithm) X509 certificates whose keys exceed the FIPS 186-2 1024-bit limit.</span></span>

<span data-ttu-id="fcb44-547">Kromě podpory většího počtu klíčových velikostí FIPS 186-3 umožňuje .NET Framework 4.6.2 výpočetních signatur pomocí řady SHA-2 algoritmů hash (SHA256, SHA384 a SHA512).</span><span class="sxs-lookup"><span data-stu-id="fcb44-547">In addition to supporting the larger key sizes of FIPS 186-3, the .NET Framework 4.6.2 allows computing signatures with the SHA-2 family of hash algorithms (SHA256, SHA384, and SHA512).</span></span> <span data-ttu-id="fcb44-548">Podporu FIPS 186-3 poskytuje nová třída <xref:System.Security.Cryptography.DSACng?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-548">FIPS 186-3 support is provided by the new <xref:System.Security.Cryptography.DSACng?displayProperty=nameWithType> class.</span></span>

<span data-ttu-id="fcb44-549">V souladu s nedávnémi změnami třídy <xref:System.Security.Cryptography.RSA> v .NET Framework 4,6 a třídou <xref:System.Security.Cryptography.ECDsa> v .NET Framework 4.6.1 má abstraktní základní třída <xref:System.Security.Cryptography.DSA> v .NET Framework 4.6.2 další metody, které umožňují volajícím používat tuto funkci bez přetypování.</span><span class="sxs-lookup"><span data-stu-id="fcb44-549">In keeping with recent changes to the <xref:System.Security.Cryptography.RSA> class in .NET Framework 4.6 and the <xref:System.Security.Cryptography.ECDsa> class in .NET Framework 4.6.1, the <xref:System.Security.Cryptography.DSA> abstract base class in .NET Framework 4.6.2 has additional methods to allow callers to use this functionality without casting.</span></span> <span data-ttu-id="fcb44-550">Můžete zavolat metodu rozšíření <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=nameWithType> pro podepsání dat, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="fcb44-550">You can call the <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=nameWithType> extension method to sign data, as the following example shows.</span></span>

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

<span data-ttu-id="fcb44-551">A můžete zavolat metodu rozšíření <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=nameWithType> pro ověření podepsaných dat, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="fcb44-551">And you can call the <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=nameWithType> extension method to verify signed data, as the following example shows.</span></span>

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

<span data-ttu-id="fcb44-552">**Větší přehlednost pro vstupy pro rutiny odvození ECDiffieHellman klíčů**</span><span class="sxs-lookup"><span data-stu-id="fcb44-552">**Increased clarity for inputs to ECDiffieHellman key derivation routines**</span></span>

<span data-ttu-id="fcb44-553">.NET Framework 3,5 přidali podporu pro klíčovou smlouvu Diffie-Hellman s eliptickou křivkou se třemi různými rutinami funkce odvození klíče (KDF).</span><span class="sxs-lookup"><span data-stu-id="fcb44-553">.NET Framework 3.5 added support for Elliptic Curve Diffie-Hellman Key Agreement with three different Key Derivation Function (KDF) routines.</span></span> <span data-ttu-id="fcb44-554">Vstupy do rutin a samotné rutiny byly nakonfigurovány prostřednictvím vlastností objektu <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-554">The inputs to the routines, and the routines themselves, were configured via properties on the <xref:System.Security.Cryptography.ECDiffieHellmanCng> object.</span></span> <span data-ttu-id="fcb44-555">Ale vzhledem k tomu, že ne všechny rutiny čtou všechna vstupní vlastnost, existovala v minulosti pro vás rozsáhlá místnost pro nejasnost.</span><span class="sxs-lookup"><span data-stu-id="fcb44-555">But since not every routine read every input property, there was ample room for confusion on the past of the developer.</span></span>

<span data-ttu-id="fcb44-556">Pro vyřešení tohoto .NET Framework 4.6.2 byly do základní třídy <xref:System.Security.Cryptography.ECDiffieHellman> přidány následující tři metody, které jasně reprezentují tyto rutiny KDF a jejich vstupy:</span><span class="sxs-lookup"><span data-stu-id="fcb44-556">To address this in the .NET Framework 4.6.2, the following three methods have been added to the  <xref:System.Security.Cryptography.ECDiffieHellman> base class to more clearly represent these KDF routines and their inputs:</span></span>

|<span data-ttu-id="fcb44-557">Metoda ECDiffieHellman</span><span class="sxs-lookup"><span data-stu-id="fcb44-557">ECDiffieHellman method</span></span>|<span data-ttu-id="fcb44-558">Popis</span><span class="sxs-lookup"><span data-stu-id="fcb44-558">Description</span></span>|
|----------------------------|-----------------|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|<span data-ttu-id="fcb44-559">Odvozuje materiál klíče pomocí vzorce.</span><span class="sxs-lookup"><span data-stu-id="fcb44-559">Derives key material using the formula</span></span><br /><br /> <span data-ttu-id="fcb44-560">HASH (secretPrepend &#124; &#124; *×* &#124; &#124; secretAppend)</span><span class="sxs-lookup"><span data-stu-id="fcb44-560">HASH(secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)</span></span><br /><br /> <span data-ttu-id="fcb44-561">HASH (secretPrepend OrElse *×* OrElse secretAppend)</span><span class="sxs-lookup"><span data-stu-id="fcb44-561">HASH(secretPrepend OrElse *x* OrElse secretAppend)</span></span><br /><br /> <span data-ttu-id="fcb44-562">kde *x* je vypočtený výsledek algoritmu ES Diffie-Hellman.</span><span class="sxs-lookup"><span data-stu-id="fcb44-562">where *x* is the computed result of the EC Diffie-Hellman algorithm.</span></span>|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|<span data-ttu-id="fcb44-563">Odvozuje materiál klíče pomocí vzorce.</span><span class="sxs-lookup"><span data-stu-id="fcb44-563">Derives key material using the formula</span></span><br /><br /> <span data-ttu-id="fcb44-564">HMAC (hmacKey, secretPrepend &#124; &#124; *x* &#124; &#124; secretAppend)</span><span class="sxs-lookup"><span data-stu-id="fcb44-564">HMAC(hmacKey, secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)</span></span><br /><br /> <span data-ttu-id="fcb44-565">HMAC (hmacKey; secretPrepend OrElse *x* OrElse secretAppend)</span><span class="sxs-lookup"><span data-stu-id="fcb44-565">HMAC(hmacKey, secretPrepend OrElse *x* OrElse secretAppend)</span></span><br /><br /> <span data-ttu-id="fcb44-566">kde *x* je vypočtený výsledek algoritmu ES Diffie-Hellman.</span><span class="sxs-lookup"><span data-stu-id="fcb44-566">where *x* is the computed result of the EC Diffie-Hellman algorithm.</span></span>|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|<span data-ttu-id="fcb44-567">Odvodí klíč klíče pomocí algoritmu odvození náhodného použití funkce TLS.</span><span class="sxs-lookup"><span data-stu-id="fcb44-567">Derives key material using the TLS pseudo-random function (PRF) derivation algorithm.</span></span>|

<span data-ttu-id="fcb44-568">**Podpora trvalého symetrického šifrování s trvalým klíčem**</span><span class="sxs-lookup"><span data-stu-id="fcb44-568">**Support for persisted-key symmetric encryption**</span></span>

<span data-ttu-id="fcb44-569">Knihovna kryptografických služeb systému Windows (CNG) přidala podporu pro ukládání trvalých symetrických klíčů a používání hardwarových symetrických klíčů a .NET Framework 4.6.2 umožňuje vývojářům využít tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="fcb44-569">The Windows cryptography library (CNG) added support for storing persisted symmetric keys and using hardware-stored symmetric keys, and the .NET Framework 4.6.2 made it possible for developers to make use of this feature.</span></span>  <span data-ttu-id="fcb44-570">Vzhledem k tomu, že pojem názvů klíčů a poskytovatelů klíčů jsou specifické pro konkrétní implementaci, vyžaduje použití této funkce konstruktor konkrétních typů implementace namísto preferovaného přístupu k továrně (například volání `Aes.Create`).</span><span class="sxs-lookup"><span data-stu-id="fcb44-570">Since the notion of key names and key providers is implementation-specific, using this feature requires utilizing the constructor of the concrete implementation types instead of the preferred factory approach (such as calling `Aes.Create`).</span></span>

<span data-ttu-id="fcb44-571">Pro algoritmy AES (<xref:System.Security.Cryptography.AesCng>) a 3DES (<xref:System.Security.Cryptography.TripleDESCng>) existují trvalé podpory symetrického šifrování klíče.</span><span class="sxs-lookup"><span data-stu-id="fcb44-571">Persisted-key symmetric encryption support exists for the AES (<xref:System.Security.Cryptography.AesCng>) and 3DES (<xref:System.Security.Cryptography.TripleDESCng>) algorithms.</span></span> <span data-ttu-id="fcb44-572">Příklad:</span><span class="sxs-lookup"><span data-stu-id="fcb44-572">For example:</span></span>

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
                throw new InvalidOperationException("This is a sample, this case wasn’t handled...");
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
                Throw New InvalidOperationException("This is a sample, this case wasn’t handled...")
            End If
            Return encryptor.TransformFinalBlock(data, 0, data.Length)
        End Using
    End Using
End Function
```

<span data-ttu-id="fcb44-573">**Podpora SignedXml pro algoritmus hash SHA-2**</span><span class="sxs-lookup"><span data-stu-id="fcb44-573">**SignedXml support for SHA-2 hashing**</span></span>

<span data-ttu-id="fcb44-574">.NET Framework 4.6.2 přidává podporu ke třídě <xref:System.Security.Cryptography.Xml.SignedXml> pro metody podpisu RSA-SHA256, RSA-SHA384 a RSA-SHA512, SHA256, SHA384 a SHA512 referenční algoritmy Digest.</span><span class="sxs-lookup"><span data-stu-id="fcb44-574">The .NET Framework 4.6.2 adds support to  the <xref:System.Security.Cryptography.Xml.SignedXml> class for RSA-SHA256, RSA-SHA384, and RSA-SHA512 PKCS#1 signature methods, and SHA256, SHA384, and SHA512 reference digest algorithms.</span></span>

<span data-ttu-id="fcb44-575">Konstanty identifikátoru URI jsou zpřístupněny na <xref:System.Security.Cryptography.Xml.SignedXml>:</span><span class="sxs-lookup"><span data-stu-id="fcb44-575">The URI constants are all exposed on <xref:System.Security.Cryptography.Xml.SignedXml>:</span></span>

|<span data-ttu-id="fcb44-576">Pole SignedXml</span><span class="sxs-lookup"><span data-stu-id="fcb44-576">SignedXml field</span></span>|<span data-ttu-id="fcb44-577">Konstanta</span><span class="sxs-lookup"><span data-stu-id="fcb44-577">Constant</span></span>|
|---------------------|--------------|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url>|<span data-ttu-id="fcb44-578">"http://www.w3.org/2001/04/xmlenc#sha256"</span><span class="sxs-lookup"><span data-stu-id="fcb44-578">"http://www.w3.org/2001/04/xmlenc#sha256"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url>|<span data-ttu-id="fcb44-579">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"</span><span class="sxs-lookup"><span data-stu-id="fcb44-579">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url>|<span data-ttu-id="fcb44-580">"http://www.w3.org/2001/04/xmldsig-more#sha384"</span><span class="sxs-lookup"><span data-stu-id="fcb44-580">"http://www.w3.org/2001/04/xmldsig-more#sha384"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url>|<span data-ttu-id="fcb44-581">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"</span><span class="sxs-lookup"><span data-stu-id="fcb44-581">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url>|<span data-ttu-id="fcb44-582">"http://www.w3.org/2001/04/xmlenc#sha512"</span><span class="sxs-lookup"><span data-stu-id="fcb44-582">"http://www.w3.org/2001/04/xmlenc#sha512"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url>|<span data-ttu-id="fcb44-583">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"</span><span class="sxs-lookup"><span data-stu-id="fcb44-583">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"</span></span>|

 <span data-ttu-id="fcb44-584">Všechny programy, které zaregistrovaly vlastní obslužnou rutinu <xref:System.Security.Cryptography.SignatureDescription> do <xref:System.Security.Cryptography.CryptoConfig> pro přidání podpory pro tyto algoritmy, budou i nadále fungovat stejně jako v minulosti, ale vzhledem k tomu, že teď existují výchozí nastavení platformy, registrace <xref:System.Security.Cryptography.CryptoConfig> už není nutná.</span><span class="sxs-lookup"><span data-stu-id="fcb44-584">Any programs that have registered a custom <xref:System.Security.Cryptography.SignatureDescription> handler into <xref:System.Security.Cryptography.CryptoConfig> to add support for these algorithms will continue to function as they did in the past, but since there are now platform defaults, the <xref:System.Security.Cryptography.CryptoConfig> registration is no longer necessary.</span></span>

<a name="SQLClient" />

### <a name="sqlclient"></a><span data-ttu-id="fcb44-585">SqlClient</span><span class="sxs-lookup"><span data-stu-id="fcb44-585">SqlClient</span></span>

<span data-ttu-id="fcb44-586">.NET Framework Zprostředkovatel dat pro SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>) obsahuje následující nové funkce v .NET Frameworkch 4.6.2:</span><span class="sxs-lookup"><span data-stu-id="fcb44-586">.NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>) includes the following new features in the .NET Framework 4.6.2:</span></span>

<span data-ttu-id="fcb44-587">**Sdružování připojení a vypršení časových limitů pomocí databází SQL Azure**</span><span class="sxs-lookup"><span data-stu-id="fcb44-587">**Connection pooling and timeouts with Azure SQL databases**</span></span>

<span data-ttu-id="fcb44-588">Je-li povoleno sdružování připojení a dojde k vypršení časového limitu nebo jiné chyby přihlášení, je výjimka uložena do mezipaměti a při každém následném pokusu o připojení na dalších 5 sekund až 1 minutu je vyvolána výjimka v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="fcb44-588">When connection pooling is enabled and a timeout or other login error occurs, an exception is cached, and the cached exception is thrown on any subsequent connection attempt for the next 5 seconds  to 1 minute.</span></span>  <span data-ttu-id="fcb44-589">Další podrobnosti najdete v tématu věnovaném [sdružování připojení SQL Server (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-589">For more details, see [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span></span>

<span data-ttu-id="fcb44-590">Toto chování není vhodné při připojování k databázím Azure SQL, protože pokusy o připojení mohou selhat s přechodem k přechodným chybám, které se obvykle obnovují rychle.</span><span class="sxs-lookup"><span data-stu-id="fcb44-590">This behavior is not desirable when connecting to Azure SQL Databases, since connection attempts can fail with transient errors that are typically recovered quickly.</span></span> <span data-ttu-id="fcb44-591">Pro lepší optimalizaci možností opakovaného pokusu o připojení se při selhání připojení k databázím Azure SQL odstraní chování při blokování fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="fcb44-591">To better optimize the connection retry experience, the connection pool blocking period behavior is removed when connections to Azure SQL Databases fail.</span></span>

<span data-ttu-id="fcb44-592">Přidání nového klíčového slova `PoolBlockingPeriod` vám umožní vybrat dobu blokování, která nejlépe vyhovuje vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fcb44-592">The addition of the new `PoolBlockingPeriod` keyword lets you to select the blocking period best suited for your app.</span></span> <span data-ttu-id="fcb44-593">Mezi hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="fcb44-593">Values include:</span></span>

<xref:System.Data.SqlClient.PoolBlockingPeriod.Auto>

<span data-ttu-id="fcb44-594">Doba blokování fondu připojení pro aplikaci, která se připojuje k Azure SQL Database je zakázána a je povolená doba blokování fondu připojení pro aplikaci, která se připojuje k jakékoli jiné instanci SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fcb44-594">The connection pool blocking period for an application that connects to an Azure SQL Database is disabled, and the connection pool blocking period for an application that connects to any other SQL Server instance is enabled.</span></span> <span data-ttu-id="fcb44-595">Toto je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="fcb44-595">This is the default value.</span></span> <span data-ttu-id="fcb44-596">Pokud název koncového bodu serveru končí některým z následujících, považují se za databáze SQL Azure:</span><span class="sxs-lookup"><span data-stu-id="fcb44-596">If the Server endpoint name ends with any of the following, they are considered Azure SQL Databases:</span></span>

- <span data-ttu-id="fcb44-597">.database.windows.net</span><span class="sxs-lookup"><span data-stu-id="fcb44-597">.database.windows.net</span></span>

- <span data-ttu-id="fcb44-598">.database.chinacloudapi.cn</span><span class="sxs-lookup"><span data-stu-id="fcb44-598">.database.chinacloudapi.cn</span></span>

- <span data-ttu-id="fcb44-599">.database.usgovcloudapi.net</span><span class="sxs-lookup"><span data-stu-id="fcb44-599">.database.usgovcloudapi.net</span></span>

- <span data-ttu-id="fcb44-600">.database.cloudapi.de</span><span class="sxs-lookup"><span data-stu-id="fcb44-600">.database.cloudapi.de</span></span>

<xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock>

<span data-ttu-id="fcb44-601">Doba blokování fondu připojení je vždycky povolená.</span><span class="sxs-lookup"><span data-stu-id="fcb44-601">The connection pool blocking period is always enabled.</span></span>

<xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock>

<span data-ttu-id="fcb44-602">Doba blokování fondu připojení je vždycky zakázaná.</span><span class="sxs-lookup"><span data-stu-id="fcb44-602">The connection pool blocking period is always disabled.</span></span>

<span data-ttu-id="fcb44-603">**Vylepšení pro Always Encrypted**</span><span class="sxs-lookup"><span data-stu-id="fcb44-603">**Enhancements for Always Encrypted**</span></span>

<span data-ttu-id="fcb44-604">SQLClient přináší dvě vylepšení pro Always Encrypted:</span><span class="sxs-lookup"><span data-stu-id="fcb44-604">SQLClient introduces two enhancements for Always Encrypted:</span></span>

- <span data-ttu-id="fcb44-605">Pro zlepšení výkonu parametrizovaných dotazů proti šifrovaným databázovým sloupcům jsou metadata šifrování pro parametry dotazu nyní ukládána do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="fcb44-605">To improve performance of parameterized queries against encrypted database columns, encryption metadata for query parameters is now cached.</span></span> <span data-ttu-id="fcb44-606">Vlastnost <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=nameWithType> nastavená na hodnotu `true` (což je výchozí hodnota), pokud je stejný dotaz volán několikrát, klient načte metadata parametrů ze serveru pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="fcb44-606">With the <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=nameWithType> property set to `true` (which is the default value), if the same query is called multiple times, the client retrieves parameter metadata from the server only once.</span></span>

- <span data-ttu-id="fcb44-607">Položky šifrovacího klíče sloupce v mezipaměti klíčů jsou teď po konfigurovatelném časovém intervalu vyřazení, které nastavíte pomocí vlastnosti <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-607">Column encryption key entries in the key cache are now evicted after a configurable time interval, set using the <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=nameWithType> property.</span></span>

<a name="WCF" />

### <a name="windows-communication-foundation"></a><span data-ttu-id="fcb44-608">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="fcb44-608">Windows Communication Foundation</span></span>

<span data-ttu-id="fcb44-609">V .NET Framework 4.6.2 byly Windows Communication Foundation rozšířeny v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="fcb44-609">In the .NET Framework 4.6.2, Windows Communication Foundation has been enhanced in the following areas:</span></span>

<span data-ttu-id="fcb44-610">**Podpora zabezpečení přenosu WCF pro certifikáty uložené pomocí CNG**</span><span class="sxs-lookup"><span data-stu-id="fcb44-610">**WCF transport security support for certificates stored using CNG**</span></span>

<span data-ttu-id="fcb44-611">Zabezpečení přenosu WCF podporuje certifikáty uložené pomocí knihovny kryptografických služeb systému Windows (CNG).</span><span class="sxs-lookup"><span data-stu-id="fcb44-611">WCF transport security supports certificates stored using the Windows cryptography library (CNG).</span></span> <span data-ttu-id="fcb44-612">V .NET Framework 4.6.2 je tato podpora omezená na použití certifikátů s veřejným klíčem, který má exponent větší než 32 bitů.</span><span class="sxs-lookup"><span data-stu-id="fcb44-612">In the .NET Framework 4.6.2, this support is limited to using certificates with a public key that has an exponent no more than 32 bits in length.</span></span> <span data-ttu-id="fcb44-613">Když je aplikace cílena na .NET Framework 4.6.2, je tato funkce ve výchozím nastavení zapnutá.</span><span class="sxs-lookup"><span data-stu-id="fcb44-613">When an application targets the .NET Framework 4.6.2, this feature is on by default.</span></span>

<span data-ttu-id="fcb44-614">Pro aplikace, které cílí na .NET Framework 4.6.1 a starší, ale běží na .NET Framework 4.6.2, je možné tuto funkci povolit přidáním následujícího řádku do oddílu [\<runtime >](../configure-apps/file-schema/runtime/runtime-element.md) souboru App. config nebo Web. config.</span><span class="sxs-lookup"><span data-stu-id="fcb44-614">For applications that target the .NET Framework 4.6.1 and earlier but are running on the .NET Framework 4.6.2, this feature can be enabled by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app.config or web.config file.</span></span>

```xml
<AppContextSwitchOverrides
    value="Switch.System.ServiceModel.DisableCngCertificates=false"
/>
```

<span data-ttu-id="fcb44-615">To lze provést také programově s kódem podobným následujícímu:</span><span class="sxs-lookup"><span data-stu-id="fcb44-615">This can also be done programmatically with code like the following:</span></span>

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificates";
AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

<span data-ttu-id="fcb44-616">**Lepší podpora více pravidel úprav více letního času pomocí třídy DataContractJsonSerializer**</span><span class="sxs-lookup"><span data-stu-id="fcb44-616">**Better support for multiple daylight saving time adjustment rules by the DataContractJsonSerializer class**</span></span>

<span data-ttu-id="fcb44-617">Zákazníci mohou použít nastavení konfigurace aplikace k určení, zda třída <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> podporuje více pravidel úprav pro jedno časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="fcb44-617">Customers can use an application configuration setting to determine whether the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> class supports multiple adjustment rules for a single time zone.</span></span> <span data-ttu-id="fcb44-618">Toto je funkce výslovného souhlasu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-618">This is an opt-in feature.</span></span> <span data-ttu-id="fcb44-619">Pokud ho chcete povolit, přidejte do souboru App. config následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="fcb44-619">To enable it, add the following setting to your app.config file:</span></span>

```xml
<runtime>
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />
</runtime>
```

<span data-ttu-id="fcb44-620">Pokud je tato funkce povolena, objekt <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> používá typ <xref:System.TimeZoneInfo> místo typu <xref:System.TimeZone> k deserializaci dat data a času.</span><span class="sxs-lookup"><span data-stu-id="fcb44-620">When this feature is enabled, a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> object uses the <xref:System.TimeZoneInfo> type instead of the <xref:System.TimeZone> type to deserialize date and time data.</span></span> <span data-ttu-id="fcb44-621"><xref:System.TimeZoneInfo> podporuje více pravidel úprav, což umožňuje pracovat s historickými daty časových pásem;   <xref:System.TimeZone> není.</span><span class="sxs-lookup"><span data-stu-id="fcb44-621"><xref:System.TimeZoneInfo> supports multiple adjustment rules, which makes it possible to work with historic time zone data;   <xref:System.TimeZone> does not.</span></span>

<span data-ttu-id="fcb44-622">Další informace o struktuře <xref:System.TimeZoneInfo> a úpravách časových pásem najdete v tématu [Přehled časových pásem](../../standard/datetime/time-zone-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-622">For more information on the <xref:System.TimeZoneInfo> structure and time zone adjustments, see [Time Zone Overview](../../standard/datetime/time-zone-overview.md).</span></span>

<span data-ttu-id="fcb44-623">**NetNamedPipeBinding nejlepší shody**</span><span class="sxs-lookup"><span data-stu-id="fcb44-623">**NetNamedPipeBinding best match**</span></span>

<span data-ttu-id="fcb44-624">Služba WCF má nové nastavení aplikace, které lze nastavit na klientských aplikacích, aby bylo zajištěno, že se budou vždy připojovat ke službě naslouchat na identifikátoru URI, který nejlépe odpovídá tomu, kterou vyžádají.</span><span class="sxs-lookup"><span data-stu-id="fcb44-624">WCF has a new app setting that can be set on client applications to ensure they always connect to the service listening on the URI that best matches the one that they request.</span></span> <span data-ttu-id="fcb44-625">Nastavením této aplikace na `false` (výchozí) je možné, že klienti používají <xref:System.ServiceModel.NetNamedPipeBinding> k pokusu o připojení ke službě naslouchat v identifikátoru URI, který je podřetězcem požadovaného identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="fcb44-625">With this app setting set to `false` (the default), it is possible for clients using <xref:System.ServiceModel.NetNamedPipeBinding> to attempt to connect to a service listening on a URI that is a substring of the requested URI.</span></span>

<span data-ttu-id="fcb44-626">Například klient se pokusí připojit ke službě naslouchat na `net.pipe://localhost/Service1`, ale na tomto počítači, na kterém je spuštěná s oprávněním správce, naslouchá na `net.pipe://localhost`.</span><span class="sxs-lookup"><span data-stu-id="fcb44-626">For example, a client tries to connect to a service listening at `net.pipe://localhost/Service1`, but a different service on that machine running with administrator privilege is listening at `net.pipe://localhost`.</span></span> <span data-ttu-id="fcb44-627">Když je nastavení této aplikace nastaveno na `false`, klient se pokusí připojit k nesprávné službě.</span><span class="sxs-lookup"><span data-stu-id="fcb44-627">With this app setting set to `false`, the client would attempt to connect to the wrong service.</span></span> <span data-ttu-id="fcb44-628">Po nastavení nastavení aplikace na hodnotu `true` se klient vždy připojí k nejlépe vyhovující službě.</span><span class="sxs-lookup"><span data-stu-id="fcb44-628">After setting the app setting to `true`, the client will always connect to the best matching service.</span></span>

> [!NOTE]
> <span data-ttu-id="fcb44-629">Klienti používající <xref:System.ServiceModel.NetNamedPipeBinding> vyhledávací služby založené na základní adrese služby (pokud existuje), nikoli na celé adrese koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-629">Clients using <xref:System.ServiceModel.NetNamedPipeBinding> find services based on the service's base address (if it exists) rather than the full endpoint address.</span></span> <span data-ttu-id="fcb44-630">Chcete-li zajistit, aby toto nastavení vždy fungovalo, měla by služba používat jedinečnou základní adresu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-630">To ensure this setting always works the service should use a unique base address.</span></span>

<span data-ttu-id="fcb44-631">Chcete-li tuto změnu povolit, přidejte do souboru App. config nebo Web. config klientské aplikace následující nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="fcb44-631">To enable this change, add the following app setting to your client application's App.config or Web.config file:</span></span>

```xml
<configuration>
    <appSettings>
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />
    </appSettings>
</configuration>
```

<span data-ttu-id="fcb44-632">**SSL 3,0 není výchozím protokolem.**</span><span class="sxs-lookup"><span data-stu-id="fcb44-632">**SSL 3.0 is not a default protocol**</span></span>

<span data-ttu-id="fcb44-633">Pokud používáte NetTcp se zabezpečením přenosu a typem přihlašovacích údajů certifikátu, SSL 3,0 už není výchozím protokolem používaným pro vyjednávání zabezpečeného připojení.</span><span class="sxs-lookup"><span data-stu-id="fcb44-633">When using NetTcp with transport security and a credential type of certificate, SSL 3.0 is no longer a default protocol used for negotiating a secure connection.</span></span> <span data-ttu-id="fcb44-634">Ve většině případů by nemělo dojít k žádným dopadům na existující aplikace, protože TLS 1,0 je zahrnutý v seznamu protokolů pro NetTcp.</span><span class="sxs-lookup"><span data-stu-id="fcb44-634">In most cases, there should be no impact to existing apps, because TLS 1.0 is included in the protocol list for NetTcp.</span></span> <span data-ttu-id="fcb44-635">Všichni existující klienti by měli být schopni vyjednat připojení pomocí aspoň TLS 1,0.</span><span class="sxs-lookup"><span data-stu-id="fcb44-635">All existing clients should be able to negotiate a connection using at least TLS 1.0.</span></span> <span data-ttu-id="fcb44-636">Pokud se vyžaduje SSL3, použijte jeden z následujících konfiguračních mechanismů a přidejte ho do seznamu sjednaných protokolů.</span><span class="sxs-lookup"><span data-stu-id="fcb44-636">If Ssl3 is required, use one of the following configuration mechanisms to add it to the list of negotiated protocols.</span></span>

- <span data-ttu-id="fcb44-637"><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=nameWithType> Vlastnost</span><span class="sxs-lookup"><span data-stu-id="fcb44-637">The <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=nameWithType> property</span></span>

- <span data-ttu-id="fcb44-638"><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> Vlastnost</span><span class="sxs-lookup"><span data-stu-id="fcb44-638">The <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> property</span></span>

- <span data-ttu-id="fcb44-639">Část [\<transport >](../configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) [> oddílu \<netTcpBinding](../configure-apps/file-schema/wcf/nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="fcb44-639">The [\<transport>](../configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) section of the [\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md) section</span></span>

- <span data-ttu-id="fcb44-640">Část [\<sslStreamSecurity >](../configure-apps/file-schema/wcf/sslstreamsecurity.md) [> oddílu \<customBinding](../configure-apps/file-schema/wcf/custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="fcb44-640">The [\<sslStreamSecurity>](../configure-apps/file-schema/wcf/sslstreamsecurity.md) section of the [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md) section</span></span>

<a name="WPF462" />

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="fcb44-641">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="fcb44-641">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="fcb44-642">V .NET Framework 4.6.2 byly Windows Presentation Foundation rozšířeny v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="fcb44-642">In the .NET Framework 4.6.2, Windows Presentation Foundation has been enhanced in the following areas:</span></span>

<span data-ttu-id="fcb44-643">**Seskupení řazení**</span><span class="sxs-lookup"><span data-stu-id="fcb44-643">**Group sorting**</span></span>

<span data-ttu-id="fcb44-644">Aplikace, která používá objekt <xref:System.Windows.Data.CollectionView> k seskupení dat, teď může explicitně deklarovat způsob řazení skupin.</span><span class="sxs-lookup"><span data-stu-id="fcb44-644">An application that uses a <xref:System.Windows.Data.CollectionView> object to group data can now explicitly declare how to  sort the groups.</span></span> <span data-ttu-id="fcb44-645">Explicitní řazení řeší problém neintuitivního řazení, ke kterému dochází, když aplikace dynamicky přidává nebo odebírá skupiny nebo když změní hodnotu vlastností položek, které jsou součástí seskupení.</span><span class="sxs-lookup"><span data-stu-id="fcb44-645">Explicit sorting addresses the problem of non-intuitive ordering that occurs when an app dynamically adds or removes groups, or when it changes the value of item properties involved in grouping.</span></span> <span data-ttu-id="fcb44-646">Může také zvýšit výkon procesu vytváření skupiny přesunutím porovnání vlastností seskupení z řazení celé kolekce do řazení skupin.</span><span class="sxs-lookup"><span data-stu-id="fcb44-646">It can also improve the performance of the group creation process by moving comparisons of the grouping properties from the sort of the full collection to the sort of the groups.</span></span>

<span data-ttu-id="fcb44-647">Aby bylo možné podporovat řazení skupin, nové vlastnosti <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=nameWithType> a <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=nameWithType> popisují způsob řazení kolekce skupin vytvořených objektem <xref:System.ComponentModel.GroupDescription>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-647">To support group sorting, the new <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=nameWithType> and <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=nameWithType> properties describe how to sort the collection of groups produced by the <xref:System.ComponentModel.GroupDescription> object.</span></span> <span data-ttu-id="fcb44-648">To je analogické jako v případě, že identicky pojmenované vlastnosti <xref:System.Windows.Data.ListCollectionView> popisují způsob řazení datových položek.</span><span class="sxs-lookup"><span data-stu-id="fcb44-648">This is analogous to the way the identically named <xref:System.Windows.Data.ListCollectionView> properties describe how to sort the data items.</span></span>

<span data-ttu-id="fcb44-649">V nejběžnějších případech lze použít dvě nové statické vlastnosti třídy <xref:System.Windows.Data.PropertyGroupDescription> <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> a <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-649">Two new static properties of the <xref:System.Windows.Data.PropertyGroupDescription> class,  <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> and <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A>, can be used for the most common cases.</span></span>

<span data-ttu-id="fcb44-650">Například následující XAML seskupuje data podle stáří, řadí věkové skupiny ve vzestupném pořadí a seskupuje položky v rámci každé věkové skupiny podle příjmení.</span><span class="sxs-lookup"><span data-stu-id="fcb44-650">For example, the following XAML groups data by age, sort the age groups in ascending order, and group the items within each age group by last name.</span></span>

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

<span data-ttu-id="fcb44-651">**Podpora měkkých klávesnic**</span><span class="sxs-lookup"><span data-stu-id="fcb44-651">**Soft keyboard support**</span></span>

<span data-ttu-id="fcb44-652">Podpora měkkých klávesnic umožňuje sledovat fokus v aplikacích WPF automatickým vyvoláním a opuštěním nové softwarové klávesnice ve Windows 10, když je vstup dotykového ovládání přijat ovládacím prvkem, který může přebírat textový vstup.</span><span class="sxs-lookup"><span data-stu-id="fcb44-652">Soft Keyboard support enables focus tracking in a WPF applications by automatically invoking and dismissing the new Soft Keyboard in Windows 10 when the touch input is received by a control that can take textual input.</span></span>

<span data-ttu-id="fcb44-653">V předchozích verzích .NET Framework aplikace WPF nemůžou povolit sledování fokusu bez zakázání podpory gesta perem a dotykového ovládání WPF.</span><span class="sxs-lookup"><span data-stu-id="fcb44-653">In previous versions of the .NET Framework, WPF applications cannot opt into the focus tracking without disabling WPF pen/touch gesture support.</span></span>  <span data-ttu-id="fcb44-654">V důsledku toho musí aplikace WPF zvolit mezi plnou podporou WPF touch nebo se spoléhat na povýšení myší systému Windows.</span><span class="sxs-lookup"><span data-stu-id="fcb44-654">As a result, WPF applications must choose between full WPF touch support or rely on Windows mouse promotion.</span></span>

<span data-ttu-id="fcb44-655">**Rozlišení DPI pro monitor**</span><span class="sxs-lookup"><span data-stu-id="fcb44-655">**Per-monitor DPI**</span></span>

<span data-ttu-id="fcb44-656">Pro podporu nedávných rozmnožení prostředí s vysokým rozlišením DPI a hybridních DPI pro aplikace WPF se v .NET Framework 4.6.2 umožňuje sledovat jednotlivé monitory.</span><span class="sxs-lookup"><span data-stu-id="fcb44-656">To support the recent proliferation of high-DPI and hybrid-DPI environments for WPF apps, WPF in the .NET Framework 4.6.2 enables per-monitor awareness.</span></span> <span data-ttu-id="fcb44-657">Další informace o tom, jak povolit aplikaci WPF pro monitorování rozlišení DPI na monitoru, najdete v [ukázkách a v příručce pro vývojáře](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-657">See the [samples and developer guide](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) on GitHub for more information about how to enable your WPF app to become per-monitor DPI aware.</span></span>

<span data-ttu-id="fcb44-658">V předchozích verzích .NET Framework aplikace WPF používají systémovou rozlišení DPI.</span><span class="sxs-lookup"><span data-stu-id="fcb44-658">In previous versions of the .NET Framework, WPF apps are system-DPI aware.</span></span> <span data-ttu-id="fcb44-659">Jinými slovy, uživatelské rozhraní aplikace se podle potřeby škáluje operačním systémem, v závislosti na DPI monitoru, na kterém je aplikace vykreslená.</span><span class="sxs-lookup"><span data-stu-id="fcb44-659">In other words, the application's UI is scaled by the OS as appropriate, depending on the DPI of the monitor on which the app is rendered.</span></span> <span data-ttu-id="fcb44-660">,</span><span class="sxs-lookup"><span data-stu-id="fcb44-660">,</span></span>

<span data-ttu-id="fcb44-661">Pro aplikace běžící pod .NET Framework 4.6.2 můžete v aplikacích WPF zakázat změny rozlišení DPI podle monitoru přidáním příkazu konfigurace do oddílu [\<runtime >](../configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="fcb44-661">For apps running under the .NET Framework 4.6.2, you can disable per-monitor DPI changes in WPF apps by adding a configuration statement to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file, as follows:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Windows.DoNotScaleForDpiChanges=false"/>
</runtime>
```

<a name="WF462" />

### <a name="windows-workflow-foundation-wf"></a><span data-ttu-id="fcb44-662">Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="fcb44-662">Windows Workflow Foundation (WF)</span></span>

<span data-ttu-id="fcb44-663">V .NET Framework 4.6.2 bylo programovací model Windows Workflow Foundation vylepšeno v následující oblasti:</span><span class="sxs-lookup"><span data-stu-id="fcb44-663">In the .NET Framework 4.6.2, Windows Workflow Foundation has been enhanced in the following area:</span></span>

<span data-ttu-id="fcb44-664">**Podpora C# výrazů a IntelliSense v nově hostovaném návrháři WF**</span><span class="sxs-lookup"><span data-stu-id="fcb44-664">**Support for C# expressions and IntelliSense in the Re-hosted WF Designer**</span></span>

<span data-ttu-id="fcb44-665">Počínaje .NET Framework 4,5 podporuje C# WF výrazy v návrháři sady Visual Studio i v pracovních postupech kódu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-665">Starting with the .NET Framework 4.5, WF supports C# expressions in both the Visual Studio Designer and in code workflows.</span></span> <span data-ttu-id="fcb44-666">Opětovné hostování Návrhář postupu provádění je klíčovou funkcí WF, která umožňuje, aby se Návrhář postupu provádění v aplikaci mimo Visual Studio (například v WPF).</span><span class="sxs-lookup"><span data-stu-id="fcb44-666">The Re-hosted Workflow Designer is a key feature of WF that allows for the Workflow Designer to be in an application outside Visual Studio (for example, in WPF).</span></span>  <span data-ttu-id="fcb44-667">Programovací model Windows Workflow Foundation poskytuje možnost podporovat C# výrazy a IntelliSense v nově hostovaném Návrhář postupu provádění.</span><span class="sxs-lookup"><span data-stu-id="fcb44-667">Windows Workflow Foundation provides the ability to support C# expressions and IntelliSense in the Re-hosted Workflow Designer.</span></span> <span data-ttu-id="fcb44-668">Další informace najdete na [blogu programovací model Windows Workflow Foundation](https://go.microsoft.com/fwlink/?LinkID=809042&clcid=0x409).</span><span class="sxs-lookup"><span data-stu-id="fcb44-668">For more information, see the [Windows Workflow Foundation blog](https://go.microsoft.com/fwlink/?LinkID=809042&clcid=0x409).</span></span>

<span data-ttu-id="fcb44-669">Když zákazník znovu sestaví projekt pracovního postupu ze sady Visual Studio, `Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio` ve verzích .NET Framework před .NET Framework 4.6.2. technologie IntelliSense pro Návrháře WF je poškozena.</span><span class="sxs-lookup"><span data-stu-id="fcb44-669">`Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio` In versions of the .NET Framework prior to the .NET Framework 4.6.2, WF Designer IntelliSense is broken when a customer rebuilds a workflow project from Visual Studio.</span></span> <span data-ttu-id="fcb44-670">I když je sestavení projektu úspěšné, typy pracovních postupů nejsou v Návrháři nalezeny a upozornění z IntelliSense pro chybějící typy pracovních postupů se zobrazí v okně **Seznam chyb** .</span><span class="sxs-lookup"><span data-stu-id="fcb44-670">While the project build is successful, the workflow types are not found on the designer, and warnings from IntelliSense for the missing workflow types appear in the **Error List** window.</span></span> <span data-ttu-id="fcb44-671">.NET Framework 4.6.2 řeší tento problém a zpřístupňuje IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="fcb44-671">The .NET Framework 4.6.2 addresses this issue and makes IntelliSense available.</span></span>

<span data-ttu-id="fcb44-672">**Aplikace pracovního postupu V1 se sledováním pracovních postupů zapnuto v režimu FIPS**</span><span class="sxs-lookup"><span data-stu-id="fcb44-672">**Workflow V1 applications with Workflow Tracking on now run under FIPS-mode**</span></span>

<span data-ttu-id="fcb44-673">Počítače s povoleným režimem dodržování standardů FIPS teď můžou úspěšně spustit aplikaci ve stylu pracovního postupu verze 1 se sledováním pracovních postupů zapnutým.</span><span class="sxs-lookup"><span data-stu-id="fcb44-673">Machines with FIPS Compliance Mode enabled can now successfully run a workflow Version 1-style application with Workflow tracking on.</span></span> <span data-ttu-id="fcb44-674">Chcete-li povolit tento scénář, je nutné provést následující změnu souboru App. config:</span><span class="sxs-lookup"><span data-stu-id="fcb44-674">To enable this scenario, you must make the following change to your app.config file:</span></span>

```xml
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />
```

<span data-ttu-id="fcb44-675">Pokud tento scénář není povolený, bude při spuštění aplikace i nadále vygenerována výjimka se zprávou "Tato implementace není součástí ověřených kryptografických algoritmů standardu FIPS platformy Windows."</span><span class="sxs-lookup"><span data-stu-id="fcb44-675">If this scenario is not enabled, running the application continues to generate an exception with the message, "This implementation is not part of the Windows Platform FIPS validated cryptographic algorithms."</span></span>

<span data-ttu-id="fcb44-676">**Vylepšení pracovního postupu při použití dynamické aktualizace se sadou Visual Studio Návrhář postupu provádění**</span><span class="sxs-lookup"><span data-stu-id="fcb44-676">**Workflow Improvements when using Dynamic Update with Visual Studio Workflow Designer**</span></span>

<span data-ttu-id="fcb44-677">Návrháři aktivity Návrhář postupu provádění, vývojový diagram a jiní návrháři aktivit pracovního postupu nyní úspěšně načetli a zobrazili pracovní postupy, které byly uloženy po volání metody <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-677">The Workflow Designer, FlowChart Activity Designer, and other Workflow Activity Designers now successfully load and display workflows that have been saved after calling  the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fcb44-678">Ve verzích .NET Framework před .NET Framework 4.6.2 načítání souboru XAML v sadě Visual Studio pro pracovní postup, který byl uložen po volání <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>, může způsobit následující problémy:</span><span class="sxs-lookup"><span data-stu-id="fcb44-678">In versions of the .NET Framework before .NET Framework 4.6.2, loading a XAML file in Visual Studio for a workflow that has been saved after calling <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> can result in the following issues:</span></span>

- <span data-ttu-id="fcb44-679">Návrhář postupu provádění nemůže správně načíst soubor XAML (Pokud je <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=nameWithType> na konci řádku).</span><span class="sxs-lookup"><span data-stu-id="fcb44-679">The Workflow Designer can't load the XAML file correctly (when the <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=nameWithType> is at the end of the line).</span></span>

- <span data-ttu-id="fcb44-680">Návrhář aktivity vývojového diagramu nebo jiný Návrhář aktivity pracovního postupu může zobrazit všechny objekty ve výchozích umístěních na rozdíl od hodnot připojených vlastností.</span><span class="sxs-lookup"><span data-stu-id="fcb44-680">Flowchart Activity Designer or other Workflow Activity Designers may display all objects in their default locations as opposed to attached property values.</span></span>

<a name="clickonce-1" />

### <a name="clickonce"></a><span data-ttu-id="fcb44-681">ClickOnce</span><span class="sxs-lookup"><span data-stu-id="fcb44-681">ClickOnce</span></span>

<span data-ttu-id="fcb44-682">ClickOnce je aktualizovaná tak, aby podporovala TLS 1,1 a TLS 1,2 kromě protokolu 1,0, který už podporuje.</span><span class="sxs-lookup"><span data-stu-id="fcb44-682">ClickOnce has been updated to support TLS 1.1 and TLS 1.2 in addition to the 1.0 protocol, which it already supports.</span></span> <span data-ttu-id="fcb44-683">ClickOnce automaticky zjišťuje, který protokol je vyžadován; aby bylo možné povolit podporu TLS 1,1 a 1,2, nejsou v rámci aplikace ClickOnce nutné žádné další kroky.</span><span class="sxs-lookup"><span data-stu-id="fcb44-683">ClickOnce automatically detects which protocol is required; no extra steps within the ClickOnce application are required to enable TLS 1.1 and 1.2 support.</span></span>

<a name="UWPConvert" />

### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a><span data-ttu-id="fcb44-684">Převod aplikací model Windows Forms a WPF na aplikace pro UWP</span><span class="sxs-lookup"><span data-stu-id="fcb44-684">Converting Windows Forms and WPF apps to  UWP apps</span></span>

<span data-ttu-id="fcb44-685">Windows teď nabízí možnosti, jak přenést existující desktopové aplikace pro Windows, včetně WPF a model Windows Forms aplikací, do Univerzální platforma Windows (UWP).</span><span class="sxs-lookup"><span data-stu-id="fcb44-685">Windows now offers capabilities to bring existing Windows desktop apps, including WPF and Windows Forms apps, to the Universal Windows Platform (UWP).</span></span> <span data-ttu-id="fcb44-686">Tato technologie funguje jako most, protože vám umožní postupně migrovat stávající základ kódu na UWP. tím se vaše aplikace přinášejí všem zařízením s Windows 10.</span><span class="sxs-lookup"><span data-stu-id="fcb44-686">This technology acts as a bridge by enabling you to gradually migrate your existing code base to UWP, thereby bringing your app to all Windows 10 devices.</span></span>

<span data-ttu-id="fcb44-687">Převedená aplikace klasické pracovní plochy získala identitu aplikace podobnou identitě aplikací v aplikacích UWP, což zpřístupňuje rozhraní API UWP pro povolení funkcí, jako jsou živé dlaždice a oznámení.</span><span class="sxs-lookup"><span data-stu-id="fcb44-687">Converted desktop apps gain an app identity similar to the app identity of UWP apps, which makes UWP APIs accessible to enable features such as Live Tiles and notifications.</span></span> <span data-ttu-id="fcb44-688">Aplikace se i nadále chová stejně jako dřív a běží jako aplikace s plnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="fcb44-688">The app continues to behave as before and runs as a full trust app.</span></span> <span data-ttu-id="fcb44-689">Po převedení aplikace lze do stávajícího procesu úplného vztahu důvěryhodnosti přidat proces kontejneru aplikace a přidat adaptivní uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fcb44-689">Once the app is converted, an app container process can be added to the existing full trust process to add an adaptive user interface.</span></span> <span data-ttu-id="fcb44-690">Když se všechny funkce přesunou do procesu kontejneru aplikace, může se odebrat úplný proces důvěryhodnosti a nová aplikace pro UWP se dá zpřístupnit pro všechna zařízení s Windows 10.</span><span class="sxs-lookup"><span data-stu-id="fcb44-690">When all functionality is moved to the app container process, the full trust process can be removed and the new UWP app can be made available to all Windows 10 devices.</span></span>

<a name="Debug462" />

### <a name="debugging-improvements"></a><span data-ttu-id="fcb44-691">Vylepšení ladění</span><span class="sxs-lookup"><span data-stu-id="fcb44-691">Debugging improvements</span></span>

<span data-ttu-id="fcb44-692">*Rozhraní API pro nespravované ladění* bylo vylepšeno v .NET Framework 4.6.2, aby bylo možné provést další analýzu při vyvolání <xref:System.NullReferenceException>, aby bylo možné určit, která proměnná v jednom řádku zdrojového kódu je `null`.</span><span class="sxs-lookup"><span data-stu-id="fcb44-692">The *unmanaged debugging API* has been enhanced in the .NET Framework 4.6.2 to perform additional analysis when a <xref:System.NullReferenceException> is thrown so that it is possible to determine which variable in a single line of source code is `null`.</span></span>   <span data-ttu-id="fcb44-693">Pro podporu tohoto scénáře byla do nespravovaného ladicího rozhraní API přidána následující rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="fcb44-693">To support this scenario, the following APIs have been added to the unmanaged debugging API.</span></span>

- <span data-ttu-id="fcb44-694">Rozhraní [ICorDebugCode4](../unmanaged-api/debugging/icordebugcode4-interface.md), [ICorDebugVariableHome](../unmanaged-api/debugging/icordebugvariablehome-interface.md)a [ICorDebugVariableHomeEnum](../unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) , která zveřejňují nativní domy spravovaných proměnných.</span><span class="sxs-lookup"><span data-stu-id="fcb44-694">The [ICorDebugCode4](../unmanaged-api/debugging/icordebugcode4-interface.md), [ICorDebugVariableHome](../unmanaged-api/debugging/icordebugvariablehome-interface.md), and [ICorDebugVariableHomeEnum](../unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interfaces, which expose the native homes of managed variables.</span></span> <span data-ttu-id="fcb44-695">To umožňuje ladicím programům provádět některé analýzy toku kódu, když dojde k <xref:System.NullReferenceException> a chcete-li pracovat zpět k určení spravované proměnné, která odpovídá nativnímu umístění, které bylo `null`.</span><span class="sxs-lookup"><span data-stu-id="fcb44-695">This enables debuggers to do some code flow analysis when a  <xref:System.NullReferenceException> occurs and to work backwards to determine the managed variable that corresponds to the native location that was `null`.</span></span>

- <span data-ttu-id="fcb44-696">Metoda [ICorDebugType2:: GetTypeId.](../unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) poskytuje mapování pro ICorDebugType na [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md), což ladicímu programu umožňuje získat [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) bez instance ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="fcb44-696">The [ICorDebugType2::GetTypeID](../unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) method provides a mapping for ICorDebugType to [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md), which allows the debugger to obtain a [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) without an instance of the ICorDebugType.</span></span> <span data-ttu-id="fcb44-697">Existující rozhraní API na [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) se pak dají použít k určení rozložení třídy typu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-697">Existing APIs on [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) can then be used to determine the class layout of the type.</span></span>

<a name="v461" />

## <a name="whats-new-in-net-framework-461"></a><span data-ttu-id="fcb44-698">Co je nového v .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="fcb44-698">What's new in .NET Framework 4.6.1</span></span>

<span data-ttu-id="fcb44-699">.NET Framework 4.6.1 zahrnuje nové funkce v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="fcb44-699">The .NET Framework 4.6.1 includes new features in the following areas:</span></span>

- [<span data-ttu-id="fcb44-700">Kryptografick</span><span class="sxs-lookup"><span data-stu-id="fcb44-700">Cryptography</span></span>](#Crypto)

- [<span data-ttu-id="fcb44-701">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fcb44-701">ADO.NET</span></span>](#ADO.NET461)

- [<span data-ttu-id="fcb44-702">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="fcb44-702">Windows Presentation Foundation (WPF)</span></span>](#WPF461)

- [<span data-ttu-id="fcb44-703">Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="fcb44-703">Windows Workflow Foundation</span></span>](#WWF461)

- [<span data-ttu-id="fcb44-704">Profilace</span><span class="sxs-lookup"><span data-stu-id="fcb44-704">Profiling</span></span>](#Profile461)

- [<span data-ttu-id="fcb44-705">NGen</span><span class="sxs-lookup"><span data-stu-id="fcb44-705">NGen</span></span>](#NGEN461)

<span data-ttu-id="fcb44-706">Další informace o .NET Framework 4.6.1 najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="fcb44-706">For more information on the .NET Framework 4.6.1, see the following topics:</span></span>

- [<span data-ttu-id="fcb44-707">Seznam změn .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="fcb44-707">.NET Framework 4.6.1 list of changes</span></span>](https://go.microsoft.com/fwlink/?LinkId=622964)

- [<span data-ttu-id="fcb44-708">Kompatibilita aplikací v 4.6.1</span><span class="sxs-lookup"><span data-stu-id="fcb44-708">Application Compatibility in 4.6.1</span></span>](../migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)

- <span data-ttu-id="fcb44-709">[Rozdíl .NET Framework rozhraní API](https://go.microsoft.com/fwlink/?LinkId=622989) (na GitHubu)</span><span class="sxs-lookup"><span data-stu-id="fcb44-709">[.NET Framework API diff](https://go.microsoft.com/fwlink/?LinkId=622989) (on GitHub)</span></span>

<a name="Crypto" />

### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a><span data-ttu-id="fcb44-710">Kryptografick Podpora pro certifikáty x509 obsahující ECDSA</span><span class="sxs-lookup"><span data-stu-id="fcb44-710">Cryptography: Support for X509 certificates containing ECDSA</span></span>

<span data-ttu-id="fcb44-711">.NET Framework 4,6 přidal podporu algoritmem RSACng pro certifikáty x509.</span><span class="sxs-lookup"><span data-stu-id="fcb44-711">.NET Framework 4.6 added RSACng support for X509 certificates.</span></span> <span data-ttu-id="fcb44-712">.NET Framework 4.6.1 přidává podporu pro certifikáty x509 ECDSA (s eliptickou křivkou pro digitální podpis algoritmu).</span><span class="sxs-lookup"><span data-stu-id="fcb44-712">The .NET Framework 4.6.1 adds support for ECDSA (Elliptic Curve Digital Signature Algorithm) X509 certificates.</span></span>

<span data-ttu-id="fcb44-713">ECDSA nabízí lepší výkon a jedná se o bezpečnější algoritmus šifrování než RSA. poskytuje skvělou volbu toho, kde je výkon a škálovatelnost protokolu TLS (Transport Layer Security) obavy.</span><span class="sxs-lookup"><span data-stu-id="fcb44-713">ECDSA offers better performance and is a more secure cryptography algorithm than RSA, providing an excellent choice where Transport Layer Security (TLS) performance and scalability is a concern.</span></span> <span data-ttu-id="fcb44-714">Implementace .NET Framework zabalí volání do stávajících funkcí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="fcb44-714">The .NET Framework implementation wraps calls into existing Windows functionality.</span></span>

<span data-ttu-id="fcb44-715">Následující příklad kódu ukazuje, jak snadné je generovat signaturu pro datový proud bajtů pomocí nové podpory pro certifikáty ECDSA x509 zahrnuté do .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="fcb44-715">The following example code shows how easy it is to generate a signature for a byte stream by using the new  support for ECDSA  X509 certificates included in the .NET Framework 4.6.1.</span></span>

[!code-csharp[whatsnew.461.crypto#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#1)]
[!code-vb[whatsnew.461.crypto#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code461.vb#1)]

<span data-ttu-id="fcb44-716">To nabízí označený rozdíl na kód potřebný k vygenerování podpisu v .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="fcb44-716">This offers a marked contrast to the code needed to generate a signature in .NET Framework 4.6.</span></span>

[!code-csharp[whatsnew.461.crypto#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#2)]
[!code-vb[whatsnew.461.crypto#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code46.vb#2)]

<a name="ADO.NET461" />

### <a name="adonet"></a><span data-ttu-id="fcb44-717">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fcb44-717">ADO.NET</span></span>

<span data-ttu-id="fcb44-718">Do ADO.NET byly přidány následující:</span><span class="sxs-lookup"><span data-stu-id="fcb44-718">The following have been added to ADO.NET:</span></span>

<span data-ttu-id="fcb44-719">**Always Encrypted podpora pro klíče chráněné hardwarem**</span><span class="sxs-lookup"><span data-stu-id="fcb44-719">**Always Encrypted support for hardware protected keys**</span></span>

<span data-ttu-id="fcb44-720">ADO.NET teď podporuje nativně ukládání Always Encrypted hlavních klíčů sloupce v modulech zabezpečení hardwaru (HSM).</span><span class="sxs-lookup"><span data-stu-id="fcb44-720">ADO.NET now supports storing Always Encrypted column master keys natively in Hardware Security Modules (HSMs).</span></span> <span data-ttu-id="fcb44-721">Díky této podpoře můžou zákazníci využívat asymetrické klíče uložené v HSM, aniž by museli psát vlastní Zprostředkovatelé úložiště klíčů pro vlastní sloupce a zaregistrovali je v aplikacích.</span><span class="sxs-lookup"><span data-stu-id="fcb44-721">With this support, customers can leverage asymmetric keys stored in HSMs without having to write custom column master key store providers and registering them in applications.</span></span>

<span data-ttu-id="fcb44-722">Aby mohli uživatelé získat přístup k Always Encrypted chráněným pomocí hlavních klíčů, které jsou uložené v modulu hardwarového zabezpečení (HSM), musí si do aplikačních serverů nebo klientských počítačů nainstalovat poskytovatele kryptografických služeb na základě dodavatele modulu hardwarového zabezpečení (HSM).</span><span class="sxs-lookup"><span data-stu-id="fcb44-722">Customers need to install the HSM vendor-provided CSP provider or CNG key store providers on the app servers or client computers in order to access Always Encrypted data protected with column master keys stored in a HSM.</span></span>

<span data-ttu-id="fcb44-723">**Vylepšené chování při připojení <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> pro AlwaysOn**</span><span class="sxs-lookup"><span data-stu-id="fcb44-723">**Improved <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> connection behavior for AlwaysOn**</span></span>

<span data-ttu-id="fcb44-724">SqlClient nyní automaticky poskytuje rychlejší připojení ke skupině dostupnosti AlwaysOn (AG).</span><span class="sxs-lookup"><span data-stu-id="fcb44-724">SqlClient now automatically provides faster connections to an AlwaysOn Availability Group (AG).</span></span> <span data-ttu-id="fcb44-725">Transparentně detekuje, jestli se vaše aplikace připojuje ke skupině dostupnosti AlwaysOn (AG) v jiné podsíti, a rychle zjistí aktuální aktivní server a poskytuje připojení k serveru.</span><span class="sxs-lookup"><span data-stu-id="fcb44-725">It transparently detects whether your application is connecting to an AlwaysOn availability group (AG) on a different subnet and quickly discovers the current active server and provides a connection to the server.</span></span> <span data-ttu-id="fcb44-726">Před touto verzí musela aplikace nastavit připojovací řetězec tak, aby obsahovala `"MultisubnetFailover=true"` k označení toho, že se připojil ke skupině dostupnosti AlwaysOn.</span><span class="sxs-lookup"><span data-stu-id="fcb44-726">Prior to this release, an application had to set the connection string to include `"MultisubnetFailover=true"` to indicate that it was connecting to an AlwaysOn Availability Group.</span></span> <span data-ttu-id="fcb44-727">Bez nastavení klíčového slova Connection na `true` může při připojování ke skupině dostupnosti AlwaysOn dojít k vypršení časového limitu aplikace.</span><span class="sxs-lookup"><span data-stu-id="fcb44-727">Without setting the connection keyword to `true`, an application might experience a timeout while connecting to an AlwaysOn Availability Group.</span></span> <span data-ttu-id="fcb44-728">V této *verzi nemusí aplikace* nastavovat <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> na `true` již.</span><span class="sxs-lookup"><span data-stu-id="fcb44-728">With this release, an application does *not* need to set <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> to `true` anymore.</span></span> <span data-ttu-id="fcb44-729">Další informace o podpoře SqlClient pro skupiny dostupnosti Always On najdete v článku [Podpora SqlClient pro vysokou dostupnost a zotavení po havárii](../data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-729">For more information about SqlClient support for Always On Availability Groups, see [SqlClient Support for High Availability, Disaster Recovery](../data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).</span></span>

<a name="WPF461" />

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="fcb44-730">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="fcb44-730">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="fcb44-731">Windows Presentation Foundation zahrnuje řadu vylepšení a změn.</span><span class="sxs-lookup"><span data-stu-id="fcb44-731">Windows Presentation Foundation includes a number of improvements and changes.</span></span>

<span data-ttu-id="fcb44-732">**Vylepšený výkon**</span><span class="sxs-lookup"><span data-stu-id="fcb44-732">**Improved performance**</span></span>

<span data-ttu-id="fcb44-733">Zpoždění při vyvolávání událostí dotyku bylo opraveno .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="fcb44-733">The delay in firing touch events has been fixed in the .NET Framework 4.6.1.</span></span> <span data-ttu-id="fcb44-734">Navíc při psaní v ovládacím prvku <xref:System.Windows.Controls.RichTextBox> již nespojuje vlákno vykreslování během rychlého vstupu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-734">In addition, typing in a <xref:System.Windows.Controls.RichTextBox> control no longer ties up the render thread during fast input.</span></span>

<span data-ttu-id="fcb44-735">**Vylepšení kontroly pravopisu**</span><span class="sxs-lookup"><span data-stu-id="fcb44-735">**Spell checking improvements**</span></span>

<span data-ttu-id="fcb44-736">Kontrola pravopisu v subsystému WPF byla aktualizována na Windows 8.1 a novějších verzích, aby bylo možné využívat operační systém pro kontrolu pravopisu dalších jazyků.</span><span class="sxs-lookup"><span data-stu-id="fcb44-736">The spell checker in WPF has been updated on Windows 8.1 and later versions to leverage operating system support for spell-checking additional languages.</span></span>  <span data-ttu-id="fcb44-737">Před Windows 8.1 se ve verzích Windows nezměnily žádné funkce.</span><span class="sxs-lookup"><span data-stu-id="fcb44-737">There is no change in functionality on Windows versions prior to Windows 8.1.</span></span>

<span data-ttu-id="fcb44-738">Stejně jako v předchozích verzích .NET Framework byl zjištěn jazyk pro @no__t Ora <xref:System.Windows.Controls.RichTextBox> blok, a to hledáním informací v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="fcb44-738">As in previous versions of the .NET Framework, the language for a <xref:System.Windows.Controls.TextBox> control ora <xref:System.Windows.Controls.RichTextBox> block is detected by looking for information in the following order:</span></span>

- <span data-ttu-id="fcb44-739">`xml:lang`, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="fcb44-739">`xml:lang`, if it is present.</span></span>

- <span data-ttu-id="fcb44-740">Aktuální jazyk vstupu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-740">Current input language.</span></span>

- <span data-ttu-id="fcb44-741">Aktuální jazyková verze vlákna.</span><span class="sxs-lookup"><span data-stu-id="fcb44-741">Current thread culture.</span></span>

<span data-ttu-id="fcb44-742">Další informace o podpoře jazyků v subsystému WPF najdete v [blogovém příspěvku WPF o funkcích .NET Framework 4.6.1](https://go.microsoft.com/fwlink/?LinkID=691819).</span><span class="sxs-lookup"><span data-stu-id="fcb44-742">For additional information on language support in WPF, see the [WPF blog post on .NET Framework 4.6.1 features](https://go.microsoft.com/fwlink/?LinkID=691819).</span></span>

<span data-ttu-id="fcb44-743">**Další podpora pro vlastní slovníky pro jednotlivé uživatele**</span><span class="sxs-lookup"><span data-stu-id="fcb44-743">**Additional support for per-user custom dictionaries**</span></span>

<span data-ttu-id="fcb44-744">V .NET Framework 4.6.1 rozpozná WPF vlastní slovníky, které jsou zaregistrované globálně.</span><span class="sxs-lookup"><span data-stu-id="fcb44-744">In .NET Framework 4.6.1, WPF recognizes custom dictionaries that are registered globally.</span></span> <span data-ttu-id="fcb44-745">Tato funkce je kromě možnosti registrace pro jednotlivé ovládací prvky k dispozici.</span><span class="sxs-lookup"><span data-stu-id="fcb44-745">This capability is available in addition to the ability to register them per-control.</span></span>

<span data-ttu-id="fcb44-746">V předchozích verzích WPF vlastní slovníky nerozpoznaly vyloučená slova a seznamy automatických oprav.</span><span class="sxs-lookup"><span data-stu-id="fcb44-746">In previous versions of WPF, custom dictionaries did not recognize Excluded Words and AutoCorrect lists.</span></span> <span data-ttu-id="fcb44-747">Jsou podporovány v Windows 8.1 a Windows 10 prostřednictvím souborů, které lze umístit do adresáře `%AppData%\Microsoft\Spelling\<language tag>`.</span><span class="sxs-lookup"><span data-stu-id="fcb44-747">They are supported on Windows 8.1 and Windows 10 through the use of files that can be placed under the `%AppData%\Microsoft\Spelling\<language tag>` directory.</span></span>  <span data-ttu-id="fcb44-748">Následující pravidla se vztahují na tyto soubory:</span><span class="sxs-lookup"><span data-stu-id="fcb44-748">The following rules apply to these files:</span></span>

- <span data-ttu-id="fcb44-749">Soubory by měly mít přípony. dic (pro přidaná slova),. EXC (vyloučená slova) nebo. ACL (pro automatické opravy).</span><span class="sxs-lookup"><span data-stu-id="fcb44-749">The files should have extensions of .dic (for added words), .exc (for excluded words), or .acl (for AutoCorrect).</span></span>

- <span data-ttu-id="fcb44-750">Soubory by měly být UTF-16 LE prostého textu, který začíná znakem pořadí bajtů (BOM).</span><span class="sxs-lookup"><span data-stu-id="fcb44-750">The files should be UTF-16 LE plaintext that starts with the Byte Order Mark (BOM).</span></span>

- <span data-ttu-id="fcb44-751">Každý řádek by měl obsahovat slovo (v seznamech přidaných a vyloučených slov) nebo dvojici automatických slov oddělených svislým pruhem (&#124;"") (v seznamu Wordu pro automatické opravy).</span><span class="sxs-lookup"><span data-stu-id="fcb44-751">Each line should consist of a word (in the added and excluded word lists), or an autocorrect pair with the words separated by a vertical bar ("&#124;") (in the AutoCorrect word list).</span></span>

- <span data-ttu-id="fcb44-752">Tyto soubory jsou považovány za jen pro čtení a systém je nemění.</span><span class="sxs-lookup"><span data-stu-id="fcb44-752">These files are considered read-only and are not modified by the system.</span></span>

> [!NOTE]
> <span data-ttu-id="fcb44-753">Tyto nové formáty souborů nejsou přímo podporovány rozhraními API pro kontrolu pravopisu WPF a vlastní slovníky dodávané WPF v aplikacích by měly dál používat soubory. lex.</span><span class="sxs-lookup"><span data-stu-id="fcb44-753">These new file-formats are not directly supported by the WPF spell checking APIs, and the custom dictionaries supplied to WPF in applications should continue to use .lex files.</span></span>

<span data-ttu-id="fcb44-754">**Ukázky**</span><span class="sxs-lookup"><span data-stu-id="fcb44-754">**Samples**</span></span>

<span data-ttu-id="fcb44-755">V úložišti GitHub [Microsoft/WPF-Samples](https://github.com/Microsoft/WPF-Samples) je několik ukázek WPF.</span><span class="sxs-lookup"><span data-stu-id="fcb44-755">There are a number of WPF samples on the [Microsoft/WPF-Samples](https://github.com/Microsoft/WPF-Samples) GitHub repository.</span></span> <span data-ttu-id="fcb44-756">Nám pomůžou vylepšit naše ukázky odesláním žádosti o přijetí změn nebo otevřením [problému GitHubu](https://github.com/Microsoft/WPF-Samples/issues).</span><span class="sxs-lookup"><span data-stu-id="fcb44-756">Help us improve our samples by sending us a pull-request or opening a [GitHub issue](https://github.com/Microsoft/WPF-Samples/issues).</span></span>

<span data-ttu-id="fcb44-757">**Rozšíření DirectX**</span><span class="sxs-lookup"><span data-stu-id="fcb44-757">**DirectX extensions**</span></span>

<span data-ttu-id="fcb44-758">WPF obsahuje [balíček NuGet](https://go.microsoft.com/fwlink/?LinkID=691342) , který poskytuje nové implementace <xref:System.Windows.Interop.D3DImage>, které usnadňují spolupráci s obsahem DX10 a DX11.</span><span class="sxs-lookup"><span data-stu-id="fcb44-758">WPF includes a [NuGet package](https://go.microsoft.com/fwlink/?LinkID=691342) that provides new implementations of <xref:System.Windows.Interop.D3DImage> that make it easy for you to interoperate with DX10 and Dx11 content.</span></span> <span data-ttu-id="fcb44-759">Kód pro tento balíček je otevřený source a je dostupný [na GitHubu](https://github.com/Microsoft/WPFDXInterop).</span><span class="sxs-lookup"><span data-stu-id="fcb44-759">The code for this package has been open sourced and is available [on GitHub](https://github.com/Microsoft/WPFDXInterop).</span></span>

<a name="WWF461" />

### <a name="windows-workflow-foundation-transactions"></a><span data-ttu-id="fcb44-760">Programovací model Windows Workflow Foundation: Transakce</span><span class="sxs-lookup"><span data-stu-id="fcb44-760">Windows Workflow Foundation: Transactions</span></span>

<span data-ttu-id="fcb44-761">Metoda <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> nyní může použít jiný správce distribuovaných transakcí než MSDTC k povýšení transakce.</span><span class="sxs-lookup"><span data-stu-id="fcb44-761">The <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> method can now use a distributed transaction manager other than MSDTC to promote the transaction.</span></span> <span data-ttu-id="fcb44-762">To provedete tak, že zadáte identifikátor ID zvýšení transakce GUID k novému přetížení <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-762">You do this by specifying a GUID transaction promoter identifier to the  new <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> overload .</span></span> <span data-ttu-id="fcb44-763">Pokud je tato operace úspěšná, existují omezení na možnosti transakce.</span><span class="sxs-lookup"><span data-stu-id="fcb44-763">If this operation is successful, there are limitations placed on the capabilities of the transaction.</span></span> <span data-ttu-id="fcb44-764">Jakmile je vypsána podpora transakcí bez služby MSDTC, následující metody vyvolávají <xref:System.Transactions.TransactionPromotionException>, protože tyto metody vyžadují povýšení na MSDTC:</span><span class="sxs-lookup"><span data-stu-id="fcb44-764">Once a non-MSDTC transaction promoter is enlisted, the following methods throw a <xref:System.Transactions.TransactionPromotionException> because these methods require promotion to MSDTC:</span></span>

- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetDtcTransaction%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetExportCookie%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetTransmitterPropagationToken%2A?displayProperty=nameWithType>

<span data-ttu-id="fcb44-765">Jakmile je vyřazení transakce bez služby MSDTC, je nutné ji použít pro budoucí trvalé zařazení pomocí protokolů, které definuje.</span><span class="sxs-lookup"><span data-stu-id="fcb44-765">Once a non-MSDTC transaction promoter is enlisted, it must be used for future durable enlistments by using protocols that it defines.</span></span> <span data-ttu-id="fcb44-766">@No__t-0 vykonavatele transakce lze získat pomocí vlastnosti <xref:System.Transactions.Transaction.PromoterType%2A>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-766">The <xref:System.Guid> of the transaction promoter can be obtained by using the <xref:System.Transactions.Transaction.PromoterType%2A> property.</span></span> <span data-ttu-id="fcb44-767">V případě, že transakce propaguje, poskytuje vykonavatel transakce pole <xref:System.Byte>, které představuje povýšený token.</span><span class="sxs-lookup"><span data-stu-id="fcb44-767">When the transaction promotes, the transaction promoter provides a <xref:System.Byte> array that represents the promoted token.</span></span> <span data-ttu-id="fcb44-768">Aplikace může získat povýšený token pro transakci, která není povýšena MSDTC, s metodou <xref:System.Transactions.Transaction.GetPromotedToken%2A>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-768">An application can obtain the promoted token for a non-MSDTC promoted transaction with the <xref:System.Transactions.Transaction.GetPromotedToken%2A> method.</span></span>

<span data-ttu-id="fcb44-769">Uživatelé nového přetížení <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> musí následovat za konkrétní sekvencí volání, aby se operace povýšení úspěšně dokončila.</span><span class="sxs-lookup"><span data-stu-id="fcb44-769">Users of the new <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> overload must follow a specific call sequence in order for the promotion operation to complete successfully.</span></span> <span data-ttu-id="fcb44-770">Tato pravidla jsou popsána v dokumentaci metody.</span><span class="sxs-lookup"><span data-stu-id="fcb44-770">These rules are documented in the method's documentation.</span></span>

<a name="Profile461" />

### <a name="profiling"></a><span data-ttu-id="fcb44-771">Profilace</span><span class="sxs-lookup"><span data-stu-id="fcb44-771">Profiling</span></span>

<span data-ttu-id="fcb44-772">Nespravované rozhraní API profilování bylo vylepšeno následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="fcb44-772">The unmanaged profiling API has been enhanced as follows:</span></span>

- <span data-ttu-id="fcb44-773">Lepší podpora pro přístup k soubory PDB v rozhraní [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="fcb44-773">Better support for accessing PDBs in the [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) interface.</span></span>

  <span data-ttu-id="fcb44-774">V ASP.NET Core se sestavení stane mnohem častější, aby sestavení bylo zkompilováno v paměti pomocí Roslyn.</span><span class="sxs-lookup"><span data-stu-id="fcb44-774">In ASP.NET Core, it is becoming much more common for assemblies to be compiled in-memory by Roslyn.</span></span> <span data-ttu-id="fcb44-775">Pro vývojáře, kteří vytvářejí nástroje pro profilaci, to znamená, že soubory PDB, který historicky byly serializovány na disk, již nemusí být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="fcb44-775">For developers making profiling tools, this means that PDBs that historically were serialized on disk may no longer be present.</span></span> <span data-ttu-id="fcb44-776">Nástroje profileru často používají soubory PDB k mapování kódu zpět na zdrojové řádky pro úlohy, jako je pokrytí kódu nebo analýza výkonu po jednotlivých řádcích.</span><span class="sxs-lookup"><span data-stu-id="fcb44-776">Profiler tools often use PDBs to map code back to source lines for tasks such as code coverage or line-by-line performance analysis.</span></span> <span data-ttu-id="fcb44-777">Rozhraní [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) nyní obsahuje dvě nové metody, [ICorProfilerInfo7:: GetInMemorySymbolsLength](../unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) a [ICorProfilerInfo7:: ReadInMemorySymbols](../unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)k poskytnutí těchto nástrojů profileru s přístupem k datům PDB v paměti. Pomocí nových rozhraní API může Profiler získat obsah souboru PDB v paměti jako bajtové pole a pak ho zpracovat nebo serializovat na disk.</span><span class="sxs-lookup"><span data-stu-id="fcb44-777">The [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) interface now includes two new methods, [ICorProfilerInfo7::GetInMemorySymbolsLength](../unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) and [ICorProfilerInfo7::ReadInMemorySymbols](../unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md), to provide these profiler tools with access to the in-memory PDB data, By using the new APIs, a profiler can obtain the contents of an in-memory PDB as a byte array and then process it or serialize it to disk.</span></span>

- <span data-ttu-id="fcb44-778">Lepší instrumentaci pomocí rozhraní ICorProfiler.</span><span class="sxs-lookup"><span data-stu-id="fcb44-778">Better instrumentation with the ICorProfiler interface.</span></span>

  <span data-ttu-id="fcb44-779">Profilery, které používají funkci rozhraní ReJit API `ICorProfiler` pro dynamickou instrumentaci, teď můžou upravovat některá metadata.</span><span class="sxs-lookup"><span data-stu-id="fcb44-779">Profilers that are using the `ICorProfiler` APIs ReJit functionality for dynamic instrumentation can now modify some metadata.</span></span> <span data-ttu-id="fcb44-780">Dříve takové nástroje mohly instrumentaci IL kdykoli instrumentovat, ale metadata se dají upravovat jenom v době načtení modulu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-780">Previously such tools could instrument IL at any time, but metadata could only be modified at module load time.</span></span> <span data-ttu-id="fcb44-781">Vzhledem k tomu, že IL odkazuje na metadata, omezíme tak druhy instrumentace, které by bylo možné provést.</span><span class="sxs-lookup"><span data-stu-id="fcb44-781">Because IL refers to metadata, this limited the kinds of instrumentation that could be done.</span></span> <span data-ttu-id="fcb44-782">Některé z těchto omezení jsme převedli přidáním metody [ICorProfilerInfo7:: ApplyMetaData](../unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) pro podporu podmnožiny úprav metadat po načtení modulu, zejména přidáním nových `AssemblyRef`, `TypeRef`, `TypeSpec`, `MemberRef`, `MemberSpec` a `UserString` záznamů.</span><span class="sxs-lookup"><span data-stu-id="fcb44-782">We have lifted some of those limits by adding the [ICorProfilerInfo7::ApplyMetaData](../unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) method to support a subset of metadata edits after the module loads, in particular by adding new `AssemblyRef`, `TypeRef`, `TypeSpec`, `MemberRef`, `MemberSpec`, and `UserString` records.</span></span> <span data-ttu-id="fcb44-783">Tato změna přináší mnohem širší množství možností instrumentace.</span><span class="sxs-lookup"><span data-stu-id="fcb44-783">This change makes a much broader range of on-the-fly instrumentation possible.</span></span>

<a name="NGEN461" />

### <a name="native-image-generator-ngen-pdbs"></a><span data-ttu-id="fcb44-784">Generátor nativních bitových kopií (NGEN) soubory PDB</span><span class="sxs-lookup"><span data-stu-id="fcb44-784">Native Image Generator (NGEN) PDBs</span></span>

<span data-ttu-id="fcb44-785">Trasování událostí mezi počítači umožňuje zákazníkům profilovat program na počítači a a prohlédnout si data profilace pomocí mapování zdrojového řádku na počítači B. v předchozích verzích .NET Framework by uživatel zkopíroval všechny moduly a nativní bitové kopie z profilované počítač do analytického počítače, který obsahuje soubor. PDB pro vytvoření mapování zdrojové na nativní.</span><span class="sxs-lookup"><span data-stu-id="fcb44-785">Cross-machine event tracing allows customers to profile a program on Machine A and look at the profiling data with source line mapping on Machine B. Using previous versions of the .NET Framework, the user would copy all the modules and native images from the profiled machine to the analysis machine that contains the IL PDB to create the source-to-native mapping.</span></span> <span data-ttu-id="fcb44-786">I když tento proces může fungovat i v případě, že jsou soubory relativně malé, například pro telefonní aplikace, můžou být soubory velmi velké na stolních počítačích a vyžadovat delší dobu kopírování.</span><span class="sxs-lookup"><span data-stu-id="fcb44-786">While this process may work well when the files are relatively small, such as for phone applications, the files can be very large on desktop systems and require significant time to copy.</span></span>

<span data-ttu-id="fcb44-787">V případě Ngen soubory PDB může NGen vytvořit PDB, který obsahuje mapování IL-to-Native bez závislosti na souboru PDB IL.</span><span class="sxs-lookup"><span data-stu-id="fcb44-787">With Ngen PDBs, NGen can create a PDB that contains the IL-to-native mapping without a dependency on the IL PDB.</span></span> <span data-ttu-id="fcb44-788">V našem scénáři trasování událostí mezi počítači je potřeba zkopírovat soubor PDB nativní bitové kopie, který je vygenerovaný počítačem A na počítač B, a použít [rozhraní API pro přístup k rozhraní ladění](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) , aby se načetlo mapování typu source-to-Il a nativní Image typu Il-to-Native. připojení.</span><span class="sxs-lookup"><span data-stu-id="fcb44-788">In our cross-machine event tracing scenario, all that is needed is to copy the native image PDB that is generated by Machine A to Machine B and to use [Debug Interface Access APIs](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) to read the IL PDB's source-to-IL mapping and the native image PDB's IL-to-native mapping.</span></span> <span data-ttu-id="fcb44-789">Kombinování obou mapování poskytuje mapování zdrojové na nativní.</span><span class="sxs-lookup"><span data-stu-id="fcb44-789">Combining both mappings provides a source-to-native mapping.</span></span> <span data-ttu-id="fcb44-790">Vzhledem k tomu, že je soubor PDB nativní image mnohem menší než všechny moduly a nativní bitové kopie, proces kopírování z počítače A na počítač B je mnohem rychlejší.</span><span class="sxs-lookup"><span data-stu-id="fcb44-790">Since the native image PDB is much smaller than all the modules and native images, the process of copying from Machine A to Machine B is much faster.</span></span>

<a name="v46" />

## <a name="whats-new-in-net-2015"></a><span data-ttu-id="fcb44-791">Co je nového v .NET 2015</span><span class="sxs-lookup"><span data-stu-id="fcb44-791">What's new in .NET 2015</span></span>

<span data-ttu-id="fcb44-792">.NET 2015 zavádí .NET Framework 4,6 a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fcb44-792">.NET 2015 introduces the .NET Framework 4.6 and .NET Core.</span></span> <span data-ttu-id="fcb44-793">Některé nové funkce platí i pro i další funkce jsou specifické pro .NET Framework 4,6 nebo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fcb44-793">Some new features apply to both, and other features are specific to .NET Framework 4.6 or .NET Core.</span></span>

- <span data-ttu-id="fcb44-794">**ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="fcb44-794">**ASP.NET Core**</span></span>

  <span data-ttu-id="fcb44-795">.NET 2015 zahrnuje ASP.NET Core, což je implementace štíhlé aplikace .NET pro vytváření moderních cloudových aplikací.</span><span class="sxs-lookup"><span data-stu-id="fcb44-795">.NET 2015 includes ASP.NET Core, which is a lean .NET implementation for building modern cloud-based apps.</span></span> <span data-ttu-id="fcb44-796">ASP.NET Core je modulární, takže můžete zahrnout jenom ty funkce, které jsou potřeba ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fcb44-796">ASP.NET Core is modular so you can include only those features that are needed in your application.</span></span> <span data-ttu-id="fcb44-797">Dá se hostovat ve službě IIS nebo v místním prostředí ve vlastním procesu a můžete spouštět aplikace s různými verzemi .NET Framework na stejném serveru.</span><span class="sxs-lookup"><span data-stu-id="fcb44-797">It can be hosted on IIS or self-hosted in a custom process, and you can run apps with different versions of the .NET Framework on the same server.</span></span> <span data-ttu-id="fcb44-798">Obsahuje nový systém konfigurace prostředí, který je určený pro nasazení v cloudu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-798">It includes a new environment configuration system that is designed for cloud deployment.</span></span>

  <span data-ttu-id="fcb44-799">MVC, webové rozhraní API a webové stránky jsou sjednocené do jediného rozhraní s názvem MVC 6.</span><span class="sxs-lookup"><span data-stu-id="fcb44-799">MVC, Web API, and Web Pages are unified into a single framework called MVC 6.</span></span> <span data-ttu-id="fcb44-800">ASP.NET Core aplikace můžete vytvářet prostřednictvím nástrojů v aplikaci Visual Studio 2015 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="fcb44-800">You build ASP.NET Core apps through tools in Visual Studio 2015 or later.</span></span> <span data-ttu-id="fcb44-801">Stávající aplikace budou fungovat na novém .NET Framework. Chcete-li však vytvořit aplikaci, která používá MVC 6 nebo Signal 3, je nutné použít systém projektu v aplikaci Visual Studio 2015 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="fcb44-801">Your existing applications will work on the new .NET Framework; however to build an app that uses MVC 6 or SignalR 3, you must use the project system in Visual Studio 2015 or later.</span></span>

  <span data-ttu-id="fcb44-802">Informace najdete v tématu [ASP.NET Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="fcb44-802">For information, see [ASP.NET Core](/aspnet/core/).</span></span>

- <span data-ttu-id="fcb44-803">**ASP.NET aktualizace**</span><span class="sxs-lookup"><span data-stu-id="fcb44-803">**ASP.NET Updates**</span></span>

  - <span data-ttu-id="fcb44-804">**Rozhraní API založené na úlohách pro vyprazdňování asynchronních odpovědí**</span><span class="sxs-lookup"><span data-stu-id="fcb44-804">**Task-based API for Asynchronous Response Flushing**</span></span>

    <span data-ttu-id="fcb44-805">ASP.NET nyní poskytuje jednoduché rozhraní API založené na úlohách pro vyprazdňování asynchronních odpovědí <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=nameWithType>, které umožňuje asynchronní vyprázdnění odpovědí pomocí podpory `async/await` vašeho jazyka.</span><span class="sxs-lookup"><span data-stu-id="fcb44-805">ASP.NET now provides a simple task-based API for asynchronous response flushing, <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=nameWithType>, that allows responses to be flushed asynchronously by using your language's `async/await` support.</span></span>

  - <span data-ttu-id="fcb44-806">**Vazba modelu podporuje metody vracející úlohy**</span><span class="sxs-lookup"><span data-stu-id="fcb44-806">**Model binding supports task-returning methods**</span></span>

    <span data-ttu-id="fcb44-807">V .NET Framework 4,5 přidal ASP.NET funkci vazby modelu, která povolila rozšiřitelný přístup k datům na základě kódu, na stránky webových formulářů a uživatelské ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="fcb44-807">In the .NET Framework 4.5, ASP.NET added the Model Binding feature that enabled an extensible, code-focused approach to CRUD-based data operations in Web Forms pages and user controls.</span></span> <span data-ttu-id="fcb44-808">Systém vázání modelů teď podporuje @no__t metody vazby modelu, které vrací -0.</span><span class="sxs-lookup"><span data-stu-id="fcb44-808">The Model Binding system now supports <xref:System.Threading.Tasks.Task>-returning model binding methods.</span></span> <span data-ttu-id="fcb44-809">Tato funkce umožňuje vývojářům webových formulářů získat výhody škálovatelnosti v rámci asynchronního přenosu dat při použití novějších verzí systému ORMs, včetně Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="fcb44-809">This feature allows Web Forms developers to get the scalability benefits of async with the ease of the data-binding system when using newer versions of ORMs, including the Entity Framework.</span></span>

    <span data-ttu-id="fcb44-810">Asynchronní vazba modelu je řízena nastavením konfigurace @no__t 0.</span><span class="sxs-lookup"><span data-stu-id="fcb44-810">Async model binding is controlled by the `aspnet:EnableAsyncModelBinding` configuration setting.</span></span>

    ```xml
    <appSettings>
        <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />
    </appSettings>
    ```

    <span data-ttu-id="fcb44-811">U aplikací cílících na .NET Framework 4,6 je výchozí hodnota `true`.</span><span class="sxs-lookup"><span data-stu-id="fcb44-811">On apps the target the .NET Framework 4.6, it defaults to `true`.</span></span> <span data-ttu-id="fcb44-812">V aplikacích běžících na .NET Framework 4,6, které cílí na starší verzi .NET Framework, je ve výchozím nastavení `false`.</span><span class="sxs-lookup"><span data-stu-id="fcb44-812">On apps running on the .NET Framework 4.6 that target an earlier version of the .NET Framework, it is `false` by default.</span></span> <span data-ttu-id="fcb44-813">Dá se povolit nastavením nastavení konfigurace na `true`.</span><span class="sxs-lookup"><span data-stu-id="fcb44-813">It can be enabled by setting the configuration setting to `true`.</span></span>

  - <span data-ttu-id="fcb44-814">**Podpora HTTP/2 (Windows 10)**</span><span class="sxs-lookup"><span data-stu-id="fcb44-814">**HTTP/2 Support (Windows 10)**</span></span>

    <span data-ttu-id="fcb44-815">[Http/2](https://www.wikipedia.org/wiki/HTTP/2) je nová verze protokolu HTTP, která poskytuje mnohem lepší využití připojení (méně zpátečních cest mezi klientem a serverem). Výsledkem je načítání webových stránek s nižší latencí pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="fcb44-815">[HTTP/2](https://www.wikipedia.org/wiki/HTTP/2) is a new version of the HTTP protocol that provides much better connection utilization (fewer round-trips between client and server), resulting in lower latency web page loading for users.</span></span>  <span data-ttu-id="fcb44-816">Webové stránky (na rozdíl od služeb) využívají maximum HTTP/2, protože protokol je optimalizován pro více artefaktů, které jsou požadovány v rámci jednoho prostředí.</span><span class="sxs-lookup"><span data-stu-id="fcb44-816">Web pages (as opposed to services) benefit the most from HTTP/2, since the protocol optimizes for multiple artifacts being requested as part of a single experience.</span></span> <span data-ttu-id="fcb44-817">Do ASP.NET v .NET Framework 4,6 byla přidána podpora protokolu HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="fcb44-817">HTTP/2 support has been added to ASP.NET in .NET Framework 4.6.</span></span> <span data-ttu-id="fcb44-818">Vzhledem k tomu, že síťové funkce existují na více vrstvách, byly v systému Windows, ve službě IIS a v ASP.NET k dispozici nové funkce pro povolení protokolu HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="fcb44-818">Because networking functionality exists at multiple layers, new features were required in Windows, in IIS, and in ASP.NET to enable HTTP/2.</span></span> <span data-ttu-id="fcb44-819">Abyste mohli používat HTTP/2 s ASP.NET, musíte běžet na Windows 10.</span><span class="sxs-lookup"><span data-stu-id="fcb44-819">You must be running on Windows 10 to use HTTP/2 with ASP.NET.</span></span>

    <span data-ttu-id="fcb44-820">HTTP/2 se podporuje i ve výchozím nastavení pro aplikace Windows 10 Univerzální platforma Windows (UWP), které používají rozhraní API <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-820">HTTP/2 is also supported and on by default for Windows 10 Universal Windows Platform (UWP) apps that use the <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> API.</span></span>

    <span data-ttu-id="fcb44-821">Aby bylo možné používat funkci [PUSH_PROMISE](https://http2.github.io/http2-spec/#PUSH_PROMISE) v aplikacích ASP.NET, byla do třídy <xref:System.Web.HttpResponse> přidána nová metoda se dvěma přetíženími, <xref:System.Web.HttpResponse.PushPromise%28System.String%29> a <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-821">In order to provide a way to use the [PUSH_PROMISE](https://http2.github.io/http2-spec/#PUSH_PROMISE) feature in ASP.NET applications, a new method with two overloads, <xref:System.Web.HttpResponse.PushPromise%28System.String%29> and <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29>, has been added to the <xref:System.Web.HttpResponse> class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="fcb44-822">I když ASP.NET Core podporuje HTTP/2, podpora funkce PUSH Promise ještě není přidaná.</span><span class="sxs-lookup"><span data-stu-id="fcb44-822">While ASP.NET Core supports HTTP/2, support for the PUSH PROMISE feature has not yet been added.</span></span>

    <span data-ttu-id="fcb44-823">Prohlížeč a webový server (IIS v systému Windows) mají veškerou práci.</span><span class="sxs-lookup"><span data-stu-id="fcb44-823">The browser and the web server (IIS on Windows) do all the work.</span></span> <span data-ttu-id="fcb44-824">Nemusíte pro uživatele dělat těžkou zdvihání.</span><span class="sxs-lookup"><span data-stu-id="fcb44-824">You don't have to do any heavy-lifting for your users.</span></span>

    <span data-ttu-id="fcb44-825">Většina [hlavních prohlížečů podporuje HTTP/2](https://www.wikipedia.org/wiki/HTTP/2), takže pokud je server podporuje, bude vám vaše uživatelé moci podporu HTTP/2 využít.</span><span class="sxs-lookup"><span data-stu-id="fcb44-825">Most of the [major browsers support HTTP/2](https://www.wikipedia.org/wiki/HTTP/2), so it's likely that your users will benefit from HTTP/2 support if your server supports it.</span></span>

  - <span data-ttu-id="fcb44-826">**Podpora pro protokol vazby tokenů**</span><span class="sxs-lookup"><span data-stu-id="fcb44-826">**Support for the Token Binding Protocol**</span></span>

    <span data-ttu-id="fcb44-827">Microsoft a Google spolupracuje na novém přístupu k ověřování, který se nazývá [protokol vazby tokenů](https://github.com/TokenBinding/Internet-Drafts).</span><span class="sxs-lookup"><span data-stu-id="fcb44-827">Microsoft and Google have been collaborating on a new approach to authentication, called the [Token Binding Protocol](https://github.com/TokenBinding/Internet-Drafts).</span></span> <span data-ttu-id="fcb44-828">Místní je, že ověřovací tokeny (v mezipaměti prohlížeče) můžou být odcizené a používané podvodníky pro přístup k jiným zabezpečeným prostředkům (třeba k vašemu bankovnímu účtu) bez vyžadování hesla nebo jakýchkoli dalších privilegovaných znalostí.</span><span class="sxs-lookup"><span data-stu-id="fcb44-828">The premise is that authentication tokens (in your browser cache) can be stolen and used by criminals to access otherwise secure resources (e.g. your bank account) without requiring your password or any other privileged knowledge.</span></span> <span data-ttu-id="fcb44-829">Nový protokol se zaměřuje na zmírnění tohoto problému.</span><span class="sxs-lookup"><span data-stu-id="fcb44-829">The new protocol aims to mitigate this problem.</span></span>

    <span data-ttu-id="fcb44-830">Protokol vazby tokenu bude v systému Windows 10 implementován jako funkce prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="fcb44-830">The Token Binding Protocol will be implemented in Windows 10 as a browser feature.</span></span> <span data-ttu-id="fcb44-831">Aplikace ASP.NET se budou podílet na protokolu, aby ověřovací tokeny byly ověřené jako legitimní.</span><span class="sxs-lookup"><span data-stu-id="fcb44-831">ASP.NET apps will participate in the protocol, so that authentication tokens are validated to be legitimate.</span></span> <span data-ttu-id="fcb44-832">Implementace klienta a serveru vytvoří kompletní ochranu určenou protokolem.</span><span class="sxs-lookup"><span data-stu-id="fcb44-832">The client and the server implementations establish the end-to-end protection specified by the protocol.</span></span>

  - <span data-ttu-id="fcb44-833">**Algoritmy hash s náhodným řetězcem**</span><span class="sxs-lookup"><span data-stu-id="fcb44-833">**Randomized string hash algorithms**</span></span>

    <span data-ttu-id="fcb44-834">.NET Framework 4,5 představil [algoritmus hash s náhodným řetězcem](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-834">.NET Framework 4.5 introduced a [randomized string hash algorithm](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).</span></span> <span data-ttu-id="fcb44-835">ASP.NET ho ale nepodporuje, protože některé funkce ASP.NET jsou závislé na stabilním kódu hash.</span><span class="sxs-lookup"><span data-stu-id="fcb44-835">However, it was not supported by ASP.NET because of some ASP.NET features depended on a stable hash code.</span></span> <span data-ttu-id="fcb44-836">V .NET Framework 4,6 jsou nyní podporovány algoritmy hash s náhodným řetězcem.</span><span class="sxs-lookup"><span data-stu-id="fcb44-836">In .NET Framework 4.6, randomized string hash algorithms are now supported.</span></span> <span data-ttu-id="fcb44-837">Pokud chcete tuto funkci povolit, použijte nastavení konfigurace `aspnet:UseRandomizedStringHashAlgorithm`.</span><span class="sxs-lookup"><span data-stu-id="fcb44-837">To enable this feature, use the `aspnet:UseRandomizedStringHashAlgorithm` config setting.</span></span>

    ```xml
    <appSettings>
        <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />
    </appSettings>
    ```

- <span data-ttu-id="fcb44-838">**ADO.NET**</span><span class="sxs-lookup"><span data-stu-id="fcb44-838">**ADO.NET**</span></span>

  <span data-ttu-id="fcb44-839">Rozhraní ADO .NET teď podporuje funkci Always Encrypted dostupnou v SQL Server 2016 Community Technology Preview 2 (CTP2).</span><span class="sxs-lookup"><span data-stu-id="fcb44-839">ADO .NET now supports the Always Encrypted feature available in SQL Server 2016 Community Technology Preview 2 (CTP2).</span></span> <span data-ttu-id="fcb44-840">Pomocí Always Encrypted může SQL Server provádět operace s šifrovanými daty a nejlepší ze všech šifrovacích klíčů se nachází v rámci důvěryhodného prostředí zákazníka, nikoli na serveru.</span><span class="sxs-lookup"><span data-stu-id="fcb44-840">With Always Encrypted, SQL Server can perform operations on encrypted data, and best of all the encryption key resides with the application inside the customer’s trusted environment and not on the server.</span></span> <span data-ttu-id="fcb44-841">Always Encrypted zabezpečuje zákaznická data, takže specializující nemají přístup k datům ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-841">Always Encrypted secures customer data so DBAs do not have access to plain text data.</span></span> <span data-ttu-id="fcb44-842">Šifrování a dešifrování dat probíhá transparentně na úrovni ovladače a minimalizuje změny, které je třeba provést u existujících aplikací.</span><span class="sxs-lookup"><span data-stu-id="fcb44-842">Encryption and decryption of data happens transparently at the driver level, minimizing changes that have to be made to existing applications.</span></span> <span data-ttu-id="fcb44-843">Podrobnosti najdete v tématu [Always Encrypted (databázový stroj)](/sql/relational-databases/security/encryption/always-encrypted-database-engine) a [Always Encrypted (vývoj klientů)](/sql/relational-databases/security/encryption/always-encrypted-client-development).</span><span class="sxs-lookup"><span data-stu-id="fcb44-843">For details, see [Always Encrypted (Database Engine)](/sql/relational-databases/security/encryption/always-encrypted-database-engine) and [Always Encrypted (client development)](/sql/relational-databases/security/encryption/always-encrypted-client-development).</span></span>

- <span data-ttu-id="fcb44-844">**64 kompilátor JIT pro spravovaný kód**</span><span class="sxs-lookup"><span data-stu-id="fcb44-844">**64-bit JIT Compiler for managed code**</span></span>

  <span data-ttu-id="fcb44-845">.NET Framework 4,6 obsahuje novou verzi 64 kompilátoru JIT (původně kódu s názvem RyuJIT).</span><span class="sxs-lookup"><span data-stu-id="fcb44-845">.NET Framework 4.6 features a new version of the 64-bit JIT compiler (originally code-named RyuJIT).</span></span> <span data-ttu-id="fcb44-846">Nový 64 kompilátor poskytuje významné zlepšení výkonu oproti staršímu 64 kompilátoru JIT.</span><span class="sxs-lookup"><span data-stu-id="fcb44-846">The new 64-bit compiler provides significant performance improvements over the older 64-bit JIT compiler.</span></span> <span data-ttu-id="fcb44-847">Nový 64 kompilátor je povolen pro 64 procesy spuštěné nad .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="fcb44-847">The new 64-bit compiler is enabled for 64-bit processes running on top of .NET Framework 4.6.</span></span> <span data-ttu-id="fcb44-848">Vaše aplikace bude spuštěna v 64m procesu, pokud je kompilována jako 64-bit nebo AnyCPU a je spuštěna v operačním systému 64.</span><span class="sxs-lookup"><span data-stu-id="fcb44-848">Your app will run in a 64-bit process if it is compiled as 64-bit or AnyCPU and is running on a 64-bit operating system.</span></span> <span data-ttu-id="fcb44-849">I když jste se ujistili, že přechod na nový kompilátor je co možná transparentní, jsou možné změny v chování.</span><span class="sxs-lookup"><span data-stu-id="fcb44-849">While care has been taken to make the transition to the new compiler as transparent as possible, changes in behavior are possible.</span></span> <span data-ttu-id="fcb44-850">Rádi bychom slyšeli o všech problémech, se kterými se setkáte při použití nového kompilátoru JIT.</span><span class="sxs-lookup"><span data-stu-id="fcb44-850">We would like to hear directly about any issues encountered when using the new JIT compiler.</span></span> <span data-ttu-id="fcb44-851">Pokud narazíte na problém, který může souviset s novým 64 kompilátorem JIT, kontaktujte nás přes [Microsoft Connect](https://connect.microsoft.com/) .</span><span class="sxs-lookup"><span data-stu-id="fcb44-851">Please contact us through [Microsoft Connect](https://connect.microsoft.com/) if you encounter an issue that may be related to the new 64-bit JIT compiler.</span></span>

  <span data-ttu-id="fcb44-852">Nový 64 kompilátor JIT zahrnuje i funkce akcelerace SIMD hardwaru, pokud jsou párovány s typy SIMD v oboru názvů <xref:System.Numerics>, což může přinést dobré zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-852">The new 64-bit JIT compiler also includes hardware SIMD acceleration features when coupled with SIMD-enabled types in the <xref:System.Numerics> namespace, which can yield good performance improvements.</span></span>

- <span data-ttu-id="fcb44-853">**Vylepšení zavaděče sestavení**</span><span class="sxs-lookup"><span data-stu-id="fcb44-853">**Assembly loader improvements**</span></span>

  <span data-ttu-id="fcb44-854">Zavaděč sestavení nyní používá paměť efektivněji uvolněním sestavení IL po načtení odpovídající image NGEN.</span><span class="sxs-lookup"><span data-stu-id="fcb44-854">The assembly loader now uses memory more efficiently by unloading IL assemblies after a corresponding NGEN image is loaded.</span></span> <span data-ttu-id="fcb44-855">Tato změna snižuje virtuální paměť, což je zvláště užitečné pro velké 32ové aplikace (jako je například Visual Studio), a také šetří fyzickou paměť.</span><span class="sxs-lookup"><span data-stu-id="fcb44-855">This change decreases virtual memory, which is particularly beneficial for large 32-bit apps (such as Visual Studio), and also saves physical memory.</span></span>

- <span data-ttu-id="fcb44-856">**Změny knihovny základních tříd**</span><span class="sxs-lookup"><span data-stu-id="fcb44-856">**Base class library changes**</span></span>

  <span data-ttu-id="fcb44-857">K .NET Framework 4,6 bylo přidáno mnoho nových rozhraní API, které umožňuje použití klíčových scénářů.</span><span class="sxs-lookup"><span data-stu-id="fcb44-857">Many new APIs have been added around to .NET Framework 4.6 to enable key scenarios.</span></span> <span data-ttu-id="fcb44-858">Mezi ně patří tyto změny a dodatky:</span><span class="sxs-lookup"><span data-stu-id="fcb44-858">These include the following changes and additions:</span></span>

  - <span data-ttu-id="fcb44-859">**IReadOnlyCollection @ no__t-1T > implementace**</span><span class="sxs-lookup"><span data-stu-id="fcb44-859">**IReadOnlyCollection\<T> implementations**</span></span>

    <span data-ttu-id="fcb44-860">Další kolekce implementují <xref:System.Collections.Generic.IReadOnlyCollection%601>, například <xref:System.Collections.Generic.Queue%601> a <xref:System.Collections.Generic.Stack%601>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-860">Additional collections implement <xref:System.Collections.Generic.IReadOnlyCollection%601> such as <xref:System.Collections.Generic.Queue%601> and <xref:System.Collections.Generic.Stack%601>.</span></span>

  - <span data-ttu-id="fcb44-861">**CultureInfo. CurrentCulture a CultureInfo. CurrentUICulture**</span><span class="sxs-lookup"><span data-stu-id="fcb44-861">**CultureInfo.CurrentCulture and CultureInfo.CurrentUICulture**</span></span>

    <span data-ttu-id="fcb44-862">Vlastnosti <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> a <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> jsou nyní určeny pro čtení i zápis, nikoli jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="fcb44-862">The <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> properties are now read-write rather than read-only.</span></span> <span data-ttu-id="fcb44-863">Pokud k těmto vlastnostem přiřadíte nový objekt <xref:System.Globalization.CultureInfo>, změní se také aktuální jazyková verze vlákna definovaná vlastností `Thread.CurrentThread.CurrentCulture` a aktuální jazyková verze vlákna uživatelského rozhraní definovaná vlastnostmi `Thread.CurrentThread.CurrentUICulture`.</span><span class="sxs-lookup"><span data-stu-id="fcb44-863">If you assign a new <xref:System.Globalization.CultureInfo> object to these properties, the current thread culture defined by the `Thread.CurrentThread.CurrentCulture` property and the current UI thread culture defined by the `Thread.CurrentThread.CurrentUICulture` properties also change.</span></span>

  - <span data-ttu-id="fcb44-864">**Vylepšení uvolňování paměti (GC)**</span><span class="sxs-lookup"><span data-stu-id="fcb44-864">**Enhancements to garbage collection (GC)**</span></span>

    <span data-ttu-id="fcb44-865">Třída <xref:System.GC> nyní obsahuje metody <xref:System.GC.TryStartNoGCRegion%2A> a <xref:System.GC.EndNoGCRegion%2A>, které umožňují zakázat uvolňování paměti během provádění kritické cesty.</span><span class="sxs-lookup"><span data-stu-id="fcb44-865">The <xref:System.GC> class now includes <xref:System.GC.TryStartNoGCRegion%2A> and <xref:System.GC.EndNoGCRegion%2A> methods that allow you to disallow garbage collection during the execution of a critical path.</span></span>

    <span data-ttu-id="fcb44-866">Nové přetížení metody <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType> umožňuje řídit, zda je halda malých objektů i halda velkých objektů Swept a komprimována nebo Swept pouze.</span><span class="sxs-lookup"><span data-stu-id="fcb44-866">A new overload of the <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType> method allows you to control whether both the small object heap and the large object heap are swept and compacted or swept only.</span></span>

  - <span data-ttu-id="fcb44-867">**Typy s povolenou SIMD**</span><span class="sxs-lookup"><span data-stu-id="fcb44-867">**SIMD-enabled types**</span></span>

    <span data-ttu-id="fcb44-868">Obor názvů <xref:System.Numerics> nyní zahrnuje řadu typů s povoleným SIMD, například <xref:System.Numerics.Matrix3x2>, <xref:System.Numerics.Matrix4x4>, <xref:System.Numerics.Plane>, <xref:System.Numerics.Quaternion>, <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3> a <xref:System.Numerics.Vector4>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-868">The <xref:System.Numerics> namespace now includes a number of SIMD-enabled types, such as <xref:System.Numerics.Matrix3x2>, <xref:System.Numerics.Matrix4x4>, <xref:System.Numerics.Plane>, <xref:System.Numerics.Quaternion>, <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, and <xref:System.Numerics.Vector4>.</span></span>

    <span data-ttu-id="fcb44-869">Vzhledem k tomu, že nový 64 kompilátor JIT zahrnuje také funkce akcelerace hardwarového SIMD, existují obzvláště významná zlepšení výkonu při použití typů SIMD s novým 64 kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="fcb44-869">Because the new 64-bit JIT compiler also includes hardware SIMD acceleration features, there are especially significant performance improvements when using the SIMD-enabled types with the new 64-bit JIT compiler.</span></span>

  - <span data-ttu-id="fcb44-870">**Aktualizace kryptografie**</span><span class="sxs-lookup"><span data-stu-id="fcb44-870">**Cryptography updates**</span></span>

    <span data-ttu-id="fcb44-871">Rozhraní API pro <xref:System.Security.Cryptography?displayProperty=nameWithType> se aktualizuje tak, aby podporovalo [rozhraní API kryptografie Windows CNG](/windows/desktop/SecCNG/cng-reference).</span><span class="sxs-lookup"><span data-stu-id="fcb44-871">The <xref:System.Security.Cryptography?displayProperty=nameWithType> API is being updated to support the [Windows CNG cryptography APIs](/windows/desktop/SecCNG/cng-reference).</span></span> <span data-ttu-id="fcb44-872">Předchozí verze .NET Framework u implementace <xref:System.Security.Cryptography?displayProperty=nameWithType> zcela spoléhaly na [starší verzi rozhraní API kryptografie Windows](/windows/desktop/SecCrypto/cryptography-portal) .</span><span class="sxs-lookup"><span data-stu-id="fcb44-872">Previous versions of the .NET Framework have relied entirely on an [earlier version of the Windows Cryptography APIs](/windows/desktop/SecCrypto/cryptography-portal) as the basis for the <xref:System.Security.Cryptography?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="fcb44-873">Měli jsme požadavky na podporu rozhraní API CNG, protože podporuje [moderní kryptografické algoritmy](/windows/desktop/SecCNG/cng-features#suite-b-support), které jsou důležité pro určité kategorie aplikací.</span><span class="sxs-lookup"><span data-stu-id="fcb44-873">We have had requests to support the CNG API, since it supports [modern cryptography algorithms](/windows/desktop/SecCNG/cng-features#suite-b-support), which are important for certain categories of apps.</span></span>

    <span data-ttu-id="fcb44-874">.NET Framework 4,6 obsahuje následující nová vylepšení pro podporu kryptografických rozhraní API Windows CNG:</span><span class="sxs-lookup"><span data-stu-id="fcb44-874">.NET Framework 4.6 includes the following new enhancements to support the Windows CNG cryptography APIs:</span></span>

    - <span data-ttu-id="fcb44-875">Sada rozšiřujících metod pro certifikáty x509 `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` a `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`, která vrací implementaci založenou na CNG spíše než implementaci založenou na rozhraní CAPI, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="fcb44-875">A set of extension methods for X509 Certificates, `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` and `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`, that return a CNG-based implementation rather than a CAPI-based implementation when possible.</span></span> <span data-ttu-id="fcb44-876">(Některé čipové karty atd., stále vyžadují rozhraní CAPI a rozhraní API zařídí záložní verze.)</span><span class="sxs-lookup"><span data-stu-id="fcb44-876">(Some smartcards, etc., still require CAPI, and the APIs handle the fallback).</span></span>

    - <span data-ttu-id="fcb44-877">Třída <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType>, která poskytuje implementaci CNG algoritmu RSA.</span><span class="sxs-lookup"><span data-stu-id="fcb44-877">The <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> class, which provides a CNG implementation of the RSA algorithm.</span></span>

    - <span data-ttu-id="fcb44-878">Vylepšení rozhraní RSA API tak, aby běžné akce již nevyžadovaly přetypování.</span><span class="sxs-lookup"><span data-stu-id="fcb44-878">Enhancements to the RSA API so that common actions no longer require casting.</span></span> <span data-ttu-id="fcb44-879">Například šifrování dat pomocí objektu <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> vyžaduje v předchozích verzích .NET Framework kód podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-879">For example, encrypting data using an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> object requires code like the following in previous versions of the .NET Framework.</span></span>

      [!code-csharp[WhatsNew.Casting#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#1)]
      [!code-vb[WhatsNew.Casting#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#1)]

      <span data-ttu-id="fcb44-880">Kód, který používá nová rozhraní API kryptografie v .NET Framework 4,6, lze přepsat následujícím způsobem, aby se zabránilo přetypování.</span><span class="sxs-lookup"><span data-stu-id="fcb44-880">Code that uses the new cryptography APIs in .NET Framework 4.6 can be rewritten as follows to avoid the cast.</span></span>

      [!code-csharp[WhatsNew.Casting#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#2)]
      [!code-vb[WhatsNew.Casting#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#2)]

  - <span data-ttu-id="fcb44-881">**Podpora převodu dat a časů do nebo z času v systému UNIX**</span><span class="sxs-lookup"><span data-stu-id="fcb44-881">**Support for converting dates and times to or from Unix time**</span></span>

    <span data-ttu-id="fcb44-882">Do struktury <xref:System.DateTimeOffset> byly přidány následující nové metody pro podporu převodu hodnot data a času na nebo z času v systému UNIX:</span><span class="sxs-lookup"><span data-stu-id="fcb44-882">The following new methods have been added to the <xref:System.DateTimeOffset> structure to support converting date and time values to or from Unix time:</span></span>

    - <xref:System.DateTimeOffset.FromUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.FromUnixTimeMilliseconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeMilliseconds%2A?displayProperty=nameWithType>

  - <span data-ttu-id="fcb44-883">**Přepínače kompatibility**</span><span class="sxs-lookup"><span data-stu-id="fcb44-883">**Compatibility switches**</span></span>

    <span data-ttu-id="fcb44-884">Nová třída <xref:System.AppContext> přidává novou funkci kompatibility, která umožňuje zapisovačům knihoven poskytnout jednotný mechanismus pro odhlášení pro nové funkce pro své uživatele.</span><span class="sxs-lookup"><span data-stu-id="fcb44-884">The new <xref:System.AppContext> class adds a new compatibility feature that enables library writers to provide a uniform opt-out mechanism for new functionality for their users.</span></span> <span data-ttu-id="fcb44-885">Zřizuje volně spojenou smlouvu mezi součástmi za účelem sdělení žádosti o výslovný souhlas.</span><span class="sxs-lookup"><span data-stu-id="fcb44-885">It establishes a loosely-coupled contract between components in order to communicate an opt-out request.</span></span> <span data-ttu-id="fcb44-886">Tato možnost je obvykle důležitá, když dojde ke změně existující funkce.</span><span class="sxs-lookup"><span data-stu-id="fcb44-886">This capability is typically important when a change is made to existing functionality.</span></span> <span data-ttu-id="fcb44-887">Naopak pro nové funkce už existuje implicitní výslovný souhlas.</span><span class="sxs-lookup"><span data-stu-id="fcb44-887">Conversely, there is already an implicit opt-in for new functionality.</span></span>

    <span data-ttu-id="fcb44-888">Pomocí <xref:System.AppContext> knihovny definují a zveřejňují přepínače kompatibility, zatímco kód, který na nich závisí, může nastavit tyto přepínače tak, aby ovlivnily chování knihovny.</span><span class="sxs-lookup"><span data-stu-id="fcb44-888">With <xref:System.AppContext>, libraries define and expose compatibility switches, while code that depends on them can set those switches to affect the library behavior.</span></span> <span data-ttu-id="fcb44-889">Ve výchozím nastavení knihovny poskytují nové funkce a mění je pouze (to znamená, že poskytují předchozí funkce), pokud je přepínač nastaven.</span><span class="sxs-lookup"><span data-stu-id="fcb44-889">By default, libraries provide the new functionality, and they only alter it (that is, they provide the previous functionality) if the switch is set.</span></span>

    <span data-ttu-id="fcb44-890">Aplikace (nebo knihovna) může deklarovat hodnotu přepínače (což je vždy hodnota <xref:System.Boolean>), kterou definuje závislá knihovna.</span><span class="sxs-lookup"><span data-stu-id="fcb44-890">An application (or a library) can declare the value of a switch (which is always a <xref:System.Boolean> value) that a dependent library defines.</span></span> <span data-ttu-id="fcb44-891">Přepínač je vždy implicitně `false`.</span><span class="sxs-lookup"><span data-stu-id="fcb44-891">The switch is always implicitly `false`.</span></span> <span data-ttu-id="fcb44-892">Nastavení přepínače na @no__t – 0 povoluje.</span><span class="sxs-lookup"><span data-stu-id="fcb44-892">Setting the switch to `true` enables it.</span></span> <span data-ttu-id="fcb44-893">Explicitní nastavení přepínače na `false` poskytuje nové chování.</span><span class="sxs-lookup"><span data-stu-id="fcb44-893">Explicitly setting the switch to `false` provides the new behavior.</span></span>

    ```csharp
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);
    ```

    ```vb
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", True)
    ```

    <span data-ttu-id="fcb44-894">Knihovna musí ověřit, zda příjemce deklaroval hodnotu přepínače a následně na něj musí reagovat.</span><span class="sxs-lookup"><span data-stu-id="fcb44-894">The library must check if a consumer has declared the value of the switch and then appropriately act on it.</span></span>

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

    <span data-ttu-id="fcb44-895">Je výhodné použít pro přepínače konzistentní formát, protože se jedná o formální kontrakt, který je zpřístupněný knihovnou.</span><span class="sxs-lookup"><span data-stu-id="fcb44-895">It's beneficial to use a consistent format for switches, since they are a formal contract exposed by a library.</span></span> <span data-ttu-id="fcb44-896">Níže jsou uvedené dva zjevné formáty.</span><span class="sxs-lookup"><span data-stu-id="fcb44-896">The following are two obvious formats.</span></span>

    - <span data-ttu-id="fcb44-897">*Přepínač*. *obor názvů*.*switchName*</span><span class="sxs-lookup"><span data-stu-id="fcb44-897">*Switch*.*namespace*.*switchname*</span></span>

    - <span data-ttu-id="fcb44-898">*Přepínač*. *Knihovna*.*switchName*</span><span class="sxs-lookup"><span data-stu-id="fcb44-898">*Switch*.*library*.*switchname*</span></span>

  - <span data-ttu-id="fcb44-899">**Změny asynchronního vzoru založeného na úlohách (klepnutím)**</span><span class="sxs-lookup"><span data-stu-id="fcb44-899">**Changes to the task-based asynchronous pattern (TAP)**</span></span>

    <span data-ttu-id="fcb44-900">Pro aplikace, které cílí na .NET Framework 4,6, <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> objekty dědí jazykovou verzi a jazykovou verzi uživatelského rozhraní volajícího vlákna.</span><span class="sxs-lookup"><span data-stu-id="fcb44-900">For apps that target the .NET Framework 4.6, <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects inherit the culture and UI culture of the calling thread.</span></span> <span data-ttu-id="fcb44-901">Chování aplikací, které cílí na předchozí verze .NET Framework nebo které necílí na konkrétní verzi .NET Framework, není ovlivněno.</span><span class="sxs-lookup"><span data-stu-id="fcb44-901">The behavior of apps that target previous versions of the .NET Framework, or that do not target a specific version of the .NET Framework, is unaffected.</span></span> <span data-ttu-id="fcb44-902">Další informace naleznete v části "jazyková verze a asynchronní operace založené na úlohách" v tématu třídy <xref:System.Globalization.CultureInfo>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-902">For more information, see the "Culture and task-based asynchronous operations" section of the <xref:System.Globalization.CultureInfo> class topic.</span></span>

    <span data-ttu-id="fcb44-903">Třída <xref:System.Threading.AsyncLocal%601?displayProperty=nameWithType> umožňuje znázornit ambientní data, která jsou lokální pro daný tok asynchronního řízení, jako je například metoda `async`.</span><span class="sxs-lookup"><span data-stu-id="fcb44-903">The <xref:System.Threading.AsyncLocal%601?displayProperty=nameWithType> class allows you to represent ambient data that is local to a given asynchronous control flow, such as an `async` method.</span></span> <span data-ttu-id="fcb44-904">Dá se použít k uchovávání dat napříč vlákny.</span><span class="sxs-lookup"><span data-stu-id="fcb44-904">It can be used to persist data across threads.</span></span> <span data-ttu-id="fcb44-905">Můžete také definovat metodu zpětného volání, která je upozorněna vždy, když se změní okolní data buď z důvodu explicitní změny vlastnosti <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=nameWithType>, nebo protože vlákno zaznamenal přechod do kontextu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-905">You can also define a callback method that is notified whenever the ambient data changes either because the <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=nameWithType> property was explicitly changed, or because the thread encountered a context transition.</span></span>

    <span data-ttu-id="fcb44-906">Do asynchronního vzoru založeného na úlohách (klepnutím) se přidaly tři praktické metody, <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=nameWithType>, které vrátí dokončené úkoly v určitém stavu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-906">Three convenience methods, <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=nameWithType>, have been added to the task-based asynchronous pattern (TAP) to return completed tasks in a particular state.</span></span>

    <span data-ttu-id="fcb44-907">Třída <xref:System.IO.Pipes.NamedPipeClientStream> nyní podporuje asynchronní komunikaci s jejím novým <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-907">The <xref:System.IO.Pipes.NamedPipeClientStream> class now supports asynchronous communication with its new <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A>.</span></span> <span data-ttu-id="fcb44-908">Metoda.</span><span class="sxs-lookup"><span data-stu-id="fcb44-908">method.</span></span>

  - <span data-ttu-id="fcb44-909">**EventSource teď podporuje zápis do protokolu událostí.**</span><span class="sxs-lookup"><span data-stu-id="fcb44-909">**EventSource now supports writing to the Event log**</span></span>

    <span data-ttu-id="fcb44-910">Nyní můžete použít třídu <xref:System.Diagnostics.Tracing.EventSource> pro protokolování administrativních nebo provozních zpráv do protokolu událostí, a to i na všechny existující relace trasování událostí pro Windows vytvořené v počítači.</span><span class="sxs-lookup"><span data-stu-id="fcb44-910">You now can use the <xref:System.Diagnostics.Tracing.EventSource> class to log administrative or operational messages to the event log, in addition to any existing ETW sessions created on the machine.</span></span> <span data-ttu-id="fcb44-911">V minulosti jste pro tuto funkci museli použít balíček NuGet Microsoft. Diagnostics. Tracing. EventSource.</span><span class="sxs-lookup"><span data-stu-id="fcb44-911">In the past, you had to use the Microsoft.Diagnostics.Tracing.EventSource NuGet package for this functionality.</span></span> <span data-ttu-id="fcb44-912">Tato funkce je teď integrovaná .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="fcb44-912">This functionality is now built-into .NET Framework 4.6.</span></span>

    <span data-ttu-id="fcb44-913">Balíček NuGet i .NET Framework 4,6 byly aktualizovány pomocí následujících funkcí:</span><span class="sxs-lookup"><span data-stu-id="fcb44-913">Both the NuGet package and .NET Framework 4.6 have been updated with the following features:</span></span>

    - <span data-ttu-id="fcb44-914">**Dynamické události**</span><span class="sxs-lookup"><span data-stu-id="fcb44-914">**Dynamic events**</span></span>

      <span data-ttu-id="fcb44-915">Povoluje události definované "průběžně" bez vytváření metod událostí.</span><span class="sxs-lookup"><span data-stu-id="fcb44-915">Allows events defined "on the fly" without creating event methods.</span></span>

    - <span data-ttu-id="fcb44-916">**Bohatá datová část**</span><span class="sxs-lookup"><span data-stu-id="fcb44-916">**Rich payloads**</span></span>

      <span data-ttu-id="fcb44-917">Povoluje jako datovou část speciálně definované třídy a pole a také primitivní typy, které mají být předány.</span><span class="sxs-lookup"><span data-stu-id="fcb44-917">Allows specially attributed classes and arrays as well as primitive types to be passed as a payload</span></span>

    - <span data-ttu-id="fcb44-918">**Sledování aktivit**</span><span class="sxs-lookup"><span data-stu-id="fcb44-918">**Activity tracking**</span></span>

      <span data-ttu-id="fcb44-919">Způsobí, že události spuštění a zastavení mezi nimi budou označovat události s ID, které představuje všechny aktuálně aktivní aktivity.</span><span class="sxs-lookup"><span data-stu-id="fcb44-919">Causes Start and Stop events to tag events between them with an ID that represents all currently active activities.</span></span>

    <span data-ttu-id="fcb44-920">Pro podporu těchto funkcí byla přetížená metoda <xref:System.Diagnostics.Tracing.EventSource.Write%2A> přidána do třídy <xref:System.Diagnostics.Tracing.EventSource>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-920">To support these features, the overloaded <xref:System.Diagnostics.Tracing.EventSource.Write%2A> method has been added to the <xref:System.Diagnostics.Tracing.EventSource> class.</span></span>

- <span data-ttu-id="fcb44-921">**Windows Presentation Foundation (WPF)**</span><span class="sxs-lookup"><span data-stu-id="fcb44-921">**Windows Presentation Foundation (WPF)**</span></span>

  - <span data-ttu-id="fcb44-922">**Vylepšení HDPI**</span><span class="sxs-lookup"><span data-stu-id="fcb44-922">**HDPI improvements**</span></span>

    <span data-ttu-id="fcb44-923">Podpora HDPI v subsystému WPF je teď v .NET Framework 4,6 lepší.</span><span class="sxs-lookup"><span data-stu-id="fcb44-923">HDPI support in WPF is now better in the .NET Framework 4.6.</span></span> <span data-ttu-id="fcb44-924">Byly provedeny změny rozložení při zaokrouhlování, aby se snížily instance oříznutí v ovládacích prvcích s ohraničením.</span><span class="sxs-lookup"><span data-stu-id="fcb44-924">Changes have been made to layout rounding to reduce instances of clipping in controls with borders.</span></span> <span data-ttu-id="fcb44-925">Ve výchozím nastavení je tato funkce povolená jenom v případě, že je vaše <xref:System.Runtime.Versioning.TargetFrameworkAttribute> nastavená na .NET 4,6.</span><span class="sxs-lookup"><span data-stu-id="fcb44-925">By default, this feature is enabled only if your <xref:System.Runtime.Versioning.TargetFrameworkAttribute> is set to .NET 4.6.</span></span>  <span data-ttu-id="fcb44-926">Aplikace, které jsou cíleny na starší verze rozhraní, ale jsou spuštěny v .NET Framework 4,6 mohou odhlásit novému chování přidáním následujícího řádku do části [\<runtime >](../configure-apps/file-schema/runtime/runtime-element.md) souboru App. config:</span><span class="sxs-lookup"><span data-stu-id="fcb44-926">Applications that target earlier versions of the framework but are running on the .NET Framework 4.6 can opt in to the new behavior by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app.config file:</span></span>

    ```xml
    <AppContextSwitchOverrides
    value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"
    />
    ```

    <span data-ttu-id="fcb44-927">WPF Windows přecházející z více monitorů s různými nastaveními DPI (nastavení s více DPI) se teď kompletně vykreslují bez černých oblastí.</span><span class="sxs-lookup"><span data-stu-id="fcb44-927">WPF windows straddling multiple monitors with different DPI settings (Multi-DPI setup) are now completely rendered without blacked-out regions.</span></span> <span data-ttu-id="fcb44-928">Toto chování můžete odhlásit přidáním následujícího řádku do části `<appSettings>` souboru App. config, abyste toto nové chování zakázali:</span><span class="sxs-lookup"><span data-stu-id="fcb44-928">You can opt out of this behavior by adding the following line to the `<appSettings>` section of the app.config file to disable this new behavior:</span></span>

    ```xml
    <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    ```

    <span data-ttu-id="fcb44-929">Do <xref:System.Windows.Input.Cursor?displayProperty=nameWithType> se přidala podpora automatického načítání pravého kurzoru na základě nastavení DPI.</span><span class="sxs-lookup"><span data-stu-id="fcb44-929">Support for automatically loading the right cursor based on DPI setting has been added to  <xref:System.Windows.Input.Cursor?displayProperty=nameWithType>.</span></span>

  - <span data-ttu-id="fcb44-930">**Dotykové ovládání je lepší**</span><span class="sxs-lookup"><span data-stu-id="fcb44-930">**Touch is better**</span></span>

    <span data-ttu-id="fcb44-931">Zákaznické zprávy o [připojení](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) tohoto dotykového ovládání vytvářejí nepředvídatelné chování, které se řeší v .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="fcb44-931">Customer reports on [Connect](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) that touch produces unpredictable behavior have been addressed in the .NET Framework 4.6.</span></span> <span data-ttu-id="fcb44-932">Prahová hodnota dvojitého kliknutí pro aplikace pro Windows Store a aplikace WPF je teď stejná jako u Windows 8.1 a vyšších.</span><span class="sxs-lookup"><span data-stu-id="fcb44-932">The double tap threshold for Windows Store applications and WPF applications is now the same in Windows 8.1 and above.</span></span>

  - <span data-ttu-id="fcb44-933">**Podpora transparentního podřízeného okna**</span><span class="sxs-lookup"><span data-stu-id="fcb44-933">**Transparent child window support**</span></span>

    <span data-ttu-id="fcb44-934">WPF v .NET Framework 4,6 podporuje transparentní podřízená okna v Windows 8.1 a vyšším.</span><span class="sxs-lookup"><span data-stu-id="fcb44-934">WPF in the .NET Framework 4.6 supports transparent child windows in Windows 8.1 and above.</span></span> <span data-ttu-id="fcb44-935">To umožňuje vytvořit v oknech nejvyšší úrovně neobdélníkové a průhledné podřízené okna.</span><span class="sxs-lookup"><span data-stu-id="fcb44-935">This allows you to create non-rectangular and transparent child windows in your top-level windows.</span></span> <span data-ttu-id="fcb44-936">Tuto funkci můžete povolit nastavením vlastnosti <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=nameWithType> na `true`.</span><span class="sxs-lookup"><span data-stu-id="fcb44-936">You can enable this feature by setting the <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=nameWithType> property to `true`.</span></span>

- <span data-ttu-id="fcb44-937">**Windows Communication Foundation (WCF)**</span><span class="sxs-lookup"><span data-stu-id="fcb44-937">**Windows Communication Foundation (WCF)**</span></span>

  - <span data-ttu-id="fcb44-938">**Podpora SSL**</span><span class="sxs-lookup"><span data-stu-id="fcb44-938">**SSL support**</span></span>

    <span data-ttu-id="fcb44-939">Služba WCF teď podporuje protokol SSL verze TLS 1,1 a TLS 1,2 kromě protokolu SSL 3,0 a TLS 1,0 při použití NetTcp s zabezpečením přenosu a ověřováním klientů.</span><span class="sxs-lookup"><span data-stu-id="fcb44-939">WCF now supports SSL version TLS 1.1 and TLS 1.2, in addition to SSL 3.0 and TLS 1.0, when using NetTcp with transport security and client authentication.</span></span> <span data-ttu-id="fcb44-940">Nyní je možné vybrat, který protokol se má použít, nebo zakázat staré méně zabezpečené protokoly.</span><span class="sxs-lookup"><span data-stu-id="fcb44-940">It is now possible to select which protocol to use, or to disable old lesser secure protocols.</span></span> <span data-ttu-id="fcb44-941">To lze provést buď nastavením vlastnosti <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A>, nebo přidáním následujícího do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="fcb44-941">This can be done either by setting the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> property or by adding the following to a configuration file.</span></span>

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

  - <span data-ttu-id="fcb44-942">**Posílání zpráv pomocí různých připojení HTTP**</span><span class="sxs-lookup"><span data-stu-id="fcb44-942">**Sending messages using different HTTP connections**</span></span>

    <span data-ttu-id="fcb44-943">WCF teď umožňuje uživatelům zajistit, aby se určité zprávy odesílaly pomocí různých základních připojení HTTP.</span><span class="sxs-lookup"><span data-stu-id="fcb44-943">WCF now allows users to ensure certain messages are sent using different underlying HTTP connections.</span></span> <span data-ttu-id="fcb44-944">Chcete-li to provést dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="fcb44-944">There are two ways to do this:</span></span>

    - <span data-ttu-id="fcb44-945">**Použití předpony názvu skupiny připojení**</span><span class="sxs-lookup"><span data-stu-id="fcb44-945">**Using a connection group name prefix**</span></span>

      <span data-ttu-id="fcb44-946">Uživatelé můžou zadat řetězec, který bude WCF používat jako předponu pro název skupiny připojení.</span><span class="sxs-lookup"><span data-stu-id="fcb44-946">Users can specify a string that WCF will use as a prefix for the connection group name.</span></span> <span data-ttu-id="fcb44-947">Dvě zprávy s různými předponami jsou odesílány pomocí různých základních připojení HTTP.</span><span class="sxs-lookup"><span data-stu-id="fcb44-947">Two messages with different prefixes are sent using different underlying HTTP connections.</span></span> <span data-ttu-id="fcb44-948">Prefix nastavíte tak, že přidáte dvojici klíč/hodnota ke vlastnosti <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=nameWithType> zprávy.</span><span class="sxs-lookup"><span data-stu-id="fcb44-948">You set the prefix by adding a key/value pair to the message's <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="fcb44-949">Klíč je "HttpTransportConnectionGroupNamePrefix"; hodnota je požadovaná předpona.</span><span class="sxs-lookup"><span data-stu-id="fcb44-949">The key is "HttpTransportConnectionGroupNamePrefix"; the value is the desired prefix.</span></span>

    - <span data-ttu-id="fcb44-950">**Používání různých továrn kanálů**</span><span class="sxs-lookup"><span data-stu-id="fcb44-950">**Using different channel factories**</span></span>

      <span data-ttu-id="fcb44-951">Uživatelé taky můžou povolit funkci, která zajistí, že se zprávy odeslané pomocí kanálů vytvořených různými továrnami kanálů budou používat v různých podkladových připojeních HTTP.</span><span class="sxs-lookup"><span data-stu-id="fcb44-951">Users can also enable a feature that ensures that messages sent using channels created by different channel factories will use different underlying HTTP connections.</span></span> <span data-ttu-id="fcb44-952">Chcete-li povolit tuto funkci, musí uživatelé nastavit následující `appSetting` na `true`:</span><span class="sxs-lookup"><span data-stu-id="fcb44-952">To enable this feature, users must set the following `appSetting` to `true`:</span></span>

      ```xml
      <appSettings>
          <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />
      </appSettings>
      ```

- <span data-ttu-id="fcb44-953">**Programovací model Windows Workflow Foundation (WWF)**</span><span class="sxs-lookup"><span data-stu-id="fcb44-953">**Windows Workflow Foundation (WWF)**</span></span>

  <span data-ttu-id="fcb44-954">Nyní můžete zadat počet sekund, po které bude služba pracovního postupu pojmout požadavek na operaci mimo pořadí, pokud před vypršením časového limitu žádosti existuje nevyřízená záložka bez protokolu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-954">You can now specify the number of seconds a workflow service will hold on to an out-of-order operation request when there is an outstanding "non-protocol" bookmark before timing out the request.</span></span> <span data-ttu-id="fcb44-955">Záložka "non-Protocol" je záložka, která nesouvisí s nezpracovanými aktivitami příjmu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-955">A "non-protocol" bookmark is a bookmark that is not related to outstanding Receive activities.</span></span> <span data-ttu-id="fcb44-956">Některé aktivity vytvářejí záložky bez protokolu v rámci jejich implementace, takže nemusí být zřejmé, že existuje záložka bez protokolu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-956">Some activities create non-protocol bookmarks within their implementation, so it may not be obvious that a non-protocol bookmark exists.</span></span> <span data-ttu-id="fcb44-957">Mezi ně patří stav a výběr.</span><span class="sxs-lookup"><span data-stu-id="fcb44-957">These include State and Pick.</span></span> <span data-ttu-id="fcb44-958">Takže pokud máte službu pracovního postupu implementovanou se stavovým počítačem nebo obsahuje aktivitu vyskladnění, pravděpodobně budete mít záložky bez protokolu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-958">So if you have a workflow service implemented with a state machine or containing a Pick activity, you will most likely have non-protocol bookmarks.</span></span> <span data-ttu-id="fcb44-959">Interval určujete tak, že přidáte řádek podobný následujícímu `appSettings` souboru App. config:</span><span class="sxs-lookup"><span data-stu-id="fcb44-959">You specify the interval by adding a line like the following to the `appSettings` section of your app.config file:</span></span>

  ```xml
  <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>
  ```

  <span data-ttu-id="fcb44-960">Výchozí hodnota je 60 sekund.</span><span class="sxs-lookup"><span data-stu-id="fcb44-960">The default value is 60 seconds.</span></span> <span data-ttu-id="fcb44-961">Je-li hodnota `value` nastavená na hodnotu 0, žádosti mimo pořadí jsou okamžitě odmítnuty s chybou text, který vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="fcb44-961">If `value` is set to 0, out-of-order requests are immediately rejected with a fault with text that looks like this:</span></span>

  ```
  Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees.
  ```

  <span data-ttu-id="fcb44-962">Jedná se o stejnou zprávu, kterou dostanete, pokud je přijata zpráva o operacích mimo pořadí a nejsou k dispozici žádné záložky bez protokolu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-962">This is the same message that you receive if an out-of-order operation message is received and there are no non-protocol bookmarks.</span></span>

  <span data-ttu-id="fcb44-963">Pokud je hodnota elementu `FilterResumeTimeoutInSeconds` nenulová, neexistují žádné záložky bez protokolu a časový limit vyprší, operace se nezdařila s chybovou zprávou.</span><span class="sxs-lookup"><span data-stu-id="fcb44-963">If the value of the `FilterResumeTimeoutInSeconds` element is non-zero, there are non-protocol bookmarks, and the timeout interval expires, the operation fails with a timeout message.</span></span>

- <span data-ttu-id="fcb44-964">**Transakce**</span><span class="sxs-lookup"><span data-stu-id="fcb44-964">**Transactions**</span></span>

  <span data-ttu-id="fcb44-965">Nyní můžete zahrnout identifikátor distribuované transakce pro transakci, která způsobila výjimku odvozenou od <xref:System.Transactions.TransactionException>, která má být vyvolána.</span><span class="sxs-lookup"><span data-stu-id="fcb44-965">You can now include the distributed transaction identifier for the transaction that has caused an exception derived from <xref:System.Transactions.TransactionException> to be thrown.</span></span> <span data-ttu-id="fcb44-966">To provedete tak, že do části `appSettings` souboru App. config přidáte následující klíč:</span><span class="sxs-lookup"><span data-stu-id="fcb44-966">You do this by adding the following key to the `appSettings` section of your app.config file:</span></span>

  ```xml
  <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/>
  ```

  <span data-ttu-id="fcb44-967">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="fcb44-967">The default value is `false`.</span></span>

- <span data-ttu-id="fcb44-968">**Sítě**</span><span class="sxs-lookup"><span data-stu-id="fcb44-968">**Networking**</span></span>

  - <span data-ttu-id="fcb44-969">**Opakované použití soketu**</span><span class="sxs-lookup"><span data-stu-id="fcb44-969">**Socket reuse**</span></span>

    <span data-ttu-id="fcb44-970">Windows 10 obsahuje nový síťový algoritmus s vysokou škálovatelností, který zajišťuje lepší využívání prostředků počítače tím, že znovu používá místní porty pro odchozí připojení TCP.</span><span class="sxs-lookup"><span data-stu-id="fcb44-970">Windows 10 includes a new high-scalability networking algorithm that makes better use of machine resources by reusing local ports for outbound TCP connections.</span></span> <span data-ttu-id="fcb44-971">.NET Framework 4,6 podporuje nový algoritmus a umožňuje aplikacím .NET využít nové chování.</span><span class="sxs-lookup"><span data-stu-id="fcb44-971">.NET Framework 4.6 supports the new algorithm, enabling .NET apps to take advantage of the new behavior.</span></span> <span data-ttu-id="fcb44-972">V předchozích verzích Windows se jednalo o umělý limit souběžného připojení (obvykle 16 384, výchozí velikost dynamického rozsahu portů), což může omezit škálovatelnost služby tím, že při zatížení způsobuje vyčerpání portů.</span><span class="sxs-lookup"><span data-stu-id="fcb44-972">In previous versions of Windows, there was an artificial concurrent connection limit (typically 16,384, the default size of the dynamic port range), which could limit the scalability of a service by causing port exhaustion when under load.</span></span>

    <span data-ttu-id="fcb44-973">V .NET Framework 4,6 byly přidány dvě nová rozhraní API, která umožňují opakované použití portů, což efektivně odstraní limit 64 KB pro souběžná připojení:</span><span class="sxs-lookup"><span data-stu-id="fcb44-973">In the .NET Framework 4.6, two new APIs have been added to enable port reuse, which effectively removes the 64K limit on concurrent connections:</span></span>

    - <span data-ttu-id="fcb44-974">Hodnota výčtu <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-974">The <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> enumeration value.</span></span>

    - <span data-ttu-id="fcb44-975"><xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> Vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fcb44-975">The <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> property.</span></span>

    <span data-ttu-id="fcb44-976">Ve výchozím nastavení je vlastnost <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> `false`, pokud hodnota `HWRPortReuseOnSocketBind` klíče registru `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` není nastavená na 0x1.</span><span class="sxs-lookup"><span data-stu-id="fcb44-976">By default, the <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> property is `false` unless the `HWRPortReuseOnSocketBind` value of the `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` registry key is set to 0x1.</span></span> <span data-ttu-id="fcb44-977">Chcete-li povolit používání místních portů u připojení HTTP, nastavte vlastnost <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> na hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="fcb44-977">To enable local port reuse on HTTP connections, set the <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="fcb44-978">To způsobí, že všechna odchozí připojení soketu TCP z <xref:System.Net.Http.HttpClient> a <xref:System.Net.HttpWebRequest> bude používat novou možnost soketu Windows 10 [SO_REUSE_UNICASTPORT](/windows/desktop/WinSock/sol-socket-socket-options), která umožňuje použití místního portu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-978">This causes all outgoing TCP socket connections from <xref:System.Net.Http.HttpClient> and <xref:System.Net.HttpWebRequest> to use a new Windows 10 socket option, [SO_REUSE_UNICASTPORT](/windows/desktop/WinSock/sol-socket-socket-options), that enables local port reuse.</span></span>

    <span data-ttu-id="fcb44-979">Vývojáři, kteří vytvářejí aplikaci jenom Sockets, můžou při volání metody, jako je například <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType>, zadat možnost <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType>, aby odchozí sokety opakovaně při vytváření vazby znovu vyvolaly místní porty.</span><span class="sxs-lookup"><span data-stu-id="fcb44-979">Developers writing a sockets-only application can specify the <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> option when calling a method such as <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> so that outbound sockets reuse local ports during binding.</span></span>

  - <span data-ttu-id="fcb44-980">**Podpora mezinárodních názvů domén a PunyCode**</span><span class="sxs-lookup"><span data-stu-id="fcb44-980">**Support for international domain names and PunyCode**</span></span>

    <span data-ttu-id="fcb44-981">Do třídy <xref:System.Uri> byla přidána nová vlastnost, <xref:System.Uri.IdnHost%2A>, aby lépe podporovala mezinárodní názvy domén a PunyCode.</span><span class="sxs-lookup"><span data-stu-id="fcb44-981">A new property, <xref:System.Uri.IdnHost%2A>, has been added to the <xref:System.Uri> class to better support international domain names and PunyCode.</span></span>

- <span data-ttu-id="fcb44-982">**Změna velikosti v ovládacích prvcích model Windows Forms.**</span><span class="sxs-lookup"><span data-stu-id="fcb44-982">**Resizing in Windows Forms controls.**</span></span>

  <span data-ttu-id="fcb44-983">Tato funkce se rozšířila v .NET Framework 4,6, aby zahrnovala typy <xref:System.Windows.Forms.DomainUpDown>, <xref:System.Windows.Forms.NumericUpDown>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, <xref:System.Windows.Forms.DataGridViewColumn> a <xref:System.Windows.Forms.ToolStripSplitButton> a obdélník určený vlastností <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A>, který se používá při vykreslování <xref:System.Drawing.Design.UITypeEditor>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-983">This feature has been expanded in .NET Framework 4.6 to include the <xref:System.Windows.Forms.DomainUpDown>, <xref:System.Windows.Forms.NumericUpDown>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.ToolStripSplitButton> types and the rectangle specified by the <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> property used when drawing a <xref:System.Drawing.Design.UITypeEditor>.</span></span>

  <span data-ttu-id="fcb44-984">Toto je funkce výslovného souhlasu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-984">This is an opt-in feature.</span></span> <span data-ttu-id="fcb44-985">Chcete-li jej povolit, nastavte v souboru konfigurace aplikace (App. config) element `EnableWindowsFormsHighDpiAutoResizing` na hodnotu `true`:</span><span class="sxs-lookup"><span data-stu-id="fcb44-985">To enable it, set the `EnableWindowsFormsHighDpiAutoResizing` element to `true` in the application configuration (app.config) file:</span></span>

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- <span data-ttu-id="fcb44-986">**Podpora kódování znakových stránek**</span><span class="sxs-lookup"><span data-stu-id="fcb44-986">**Support for code page encodings**</span></span>

  <span data-ttu-id="fcb44-987">.NET Core primárně podporuje kódování Unicode a ve výchozím nastavení poskytuje omezené podpory pro kódování znakových stránek.</span><span class="sxs-lookup"><span data-stu-id="fcb44-987">.NET Core primarily supports the Unicode encodings and by default provides limited support for code page encodings.</span></span> <span data-ttu-id="fcb44-988">Můžete přidat podporu pro kódování znakových stránek, která jsou k dispozici v .NET Framework, ale nepodporovaná v .NET Core, registrací kódování znakové stránky pomocí metody <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-988">You can add support for code page encodings available in .NET Framework but unsupported in .NET Core by registering code page encodings with the <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fcb44-989">Další informace naleznete v tématu <xref:System.Text.CodePagesEncodingProvider?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-989">For more information, see <xref:System.Text.CodePagesEncodingProvider?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="fcb44-990">**.NET Native**</span><span class="sxs-lookup"><span data-stu-id="fcb44-990">**.NET Native**</span></span>

  <span data-ttu-id="fcb44-991">Aplikace pro Windows pro Windows 10, které cílí na .NET Core a C# jsou napsané v systému nebo Visual Basic můžou využít novou technologii, která kompiluje aplikace do nativního kódu místo Il.</span><span class="sxs-lookup"><span data-stu-id="fcb44-991">Windows apps for Windows 10 that target .NET Core and are written in C# or Visual Basic can take advantage of a new technology that compiles apps to native code rather than IL.</span></span> <span data-ttu-id="fcb44-992">Vytváří aplikace s větším počtem časů spuštění a spuštění.</span><span class="sxs-lookup"><span data-stu-id="fcb44-992">They produce apps characterized by faster startup and execution times.</span></span> <span data-ttu-id="fcb44-993">Další informace najdete v tématu [kompilace aplikací pomocí .NET Native](../net-native/index.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-993">For more information, see [Compiling Apps with .NET Native](../net-native/index.md).</span></span> <span data-ttu-id="fcb44-994">Přehled .NET Native, který prověřuje, jak se liší od kompilace JIT i NGEN a co znamená pro váš kód, naleznete v tématu [.NET Native a kompilace](../net-native/net-native-and-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-994">For an overview of .NET Native that examines how it differs from both JIT compilation and NGEN and what that means for your code, see [.NET Native and Compilation](../net-native/net-native-and-compilation.md).</span></span>

  <span data-ttu-id="fcb44-995">Vaše aplikace jsou kompilovány do nativního kódu ve výchozím nastavení, když je kompilujete pomocí sady Visual Studio 2015 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="fcb44-995">Your apps are compiled to native code by default when you compile them with Visual Studio 2015 or later.</span></span> <span data-ttu-id="fcb44-996">Další informace najdete v tématu [Začínáme s .NET Native](../net-native/getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-996">For more information, see [Getting Started with .NET Native](../net-native/getting-started-with-net-native.md).</span></span>

  <span data-ttu-id="fcb44-997">Pro podporu ladění aplikací .NET Native bylo přidáno několik nových rozhraní a výčtů do nespravovaného ladicího rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="fcb44-997">To support debugging .NET Native apps, a number of new interfaces and enumerations have been added to the unmanaged debugging API.</span></span> <span data-ttu-id="fcb44-998">Další informace naleznete v tématu [ladění (nespravované rozhraní API)](../unmanaged-api/debugging/index.md) .</span><span class="sxs-lookup"><span data-stu-id="fcb44-998">For more information, see the [Debugging (Unmanaged API Reference)](../unmanaged-api/debugging/index.md) topic.</span></span>

- <span data-ttu-id="fcb44-999">**Open Source .NET Framework balíčky**</span><span class="sxs-lookup"><span data-stu-id="fcb44-999">**Open-source .NET Framework packages**</span></span>

  <span data-ttu-id="fcb44-1000">Balíčky .NET Core, jako jsou neměnné kolekce, [rozhraní SIMD API](https://go.microsoft.com/fwlink/?LinkID=518639)a síťové rozhraní API, jako jsou ty, které se nacházejí v oboru názvů <xref:System.Net.Http>, jsou teď dostupné jako open source balíčky na [GitHubu](https://github.com/).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1000">.NET Core packages such as the immutable collections, [SIMD APIs](https://go.microsoft.com/fwlink/?LinkID=518639), and networking APIs such as those found in the <xref:System.Net.Http> namespace are now available as open source packages on [GitHub](https://github.com/).</span></span> <span data-ttu-id="fcb44-1001">Přístup k kódu naleznete v tématu [CoreFx na GitHubu](https://github.com/dotnet/corefx).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1001">To access the code, see [CoreFx on GitHub](https://github.com/dotnet/corefx).</span></span> <span data-ttu-id="fcb44-1002">Další informace a o tom, jak přispívat do těchto balíčků, najdete v tématu [.NET Core a open source](../get-started/net-core-and-open-source.md), [Domovská stránka .NET na GitHubu](https://github.com/dotnet/home).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1002">For more information and how to contribute to these packages, see [.NET Core and Open-Source](../get-started/net-core-and-open-source.md), [.NET Home Page on GitHub](https://github.com/dotnet/home).</span></span>

<a name="v452" />

## <a name="whats-new-in-net-framework-452"></a><span data-ttu-id="fcb44-1003">Co je nového v .NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="fcb44-1003">What's new in .NET Framework 4.5.2</span></span>

- <span data-ttu-id="fcb44-1004">**Nová rozhraní API pro aplikace ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="fcb44-1004">**New APIs for ASP.NET apps.**</span></span> <span data-ttu-id="fcb44-1005">Nové metody <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=nameWithType> a <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=nameWithType> umožňují kontrolovat a upravovat hlavičky odpovědí a stavový kód, protože odpověď se vyprazdňuje do klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1005">The new <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=nameWithType> and <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=nameWithType> methods let you inspect and modify response headers and status code as the response is being flushed to the client app.</span></span> <span data-ttu-id="fcb44-1006">Zvažte použití těchto metod namísto <xref:System.Web.HttpApplication.PreSendRequestHeaders> a <xref:System.Web.HttpApplication.PreSendRequestContent> událostí; jsou efektivnější a spolehlivé.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1006">Consider using these methods instead of the <xref:System.Web.HttpApplication.PreSendRequestHeaders> and <xref:System.Web.HttpApplication.PreSendRequestContent> events; they are more efficient and reliable.</span></span>

  <span data-ttu-id="fcb44-1007">Metoda <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=nameWithType> umožňuje naplánovat malé pracovní položky na pozadí.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1007">The <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=nameWithType> method lets you schedule small background work items.</span></span> <span data-ttu-id="fcb44-1008">ASP.NET sleduje tyto položky a brání službě IIS v náhlém ukončení pracovního procesu, dokud nebudou dokončeny všechny pracovní položky na pozadí.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1008">ASP.NET tracks these items and prevents IIS from abruptly terminating the worker process until all background work items have completed.</span></span> <span data-ttu-id="fcb44-1009">Tuto metodu nejde volat mimo doménu spravované aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1009">This method can't be called outside an ASP.NET managed app domain.</span></span>

  <span data-ttu-id="fcb44-1010">Nové vlastnosti <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=nameWithType> a <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=nameWithType> vrací logické hodnoty, které určují, zda byly hlavičky odpovědi zapsány.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1010">The new <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=nameWithType> and <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=nameWithType> properties return Boolean values that indicate whether the response headers have been written.</span></span> <span data-ttu-id="fcb44-1011">Tyto vlastnosti můžete použít k tomu, abyste se ujistili, že volání rozhraní API, jako je například <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=nameWithType> (vyvolávající výjimky, pokud byla hlavičky zapsána), budou úspěšné.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1011">You can use these properties to make sure that calls to APIs such as <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=nameWithType> (which throw exceptions if the headers have been written) will succeed.</span></span>

- <span data-ttu-id="fcb44-1012">**Změna velikosti v ovládacích prvcích model Windows Forms.**</span><span class="sxs-lookup"><span data-stu-id="fcb44-1012">**Resizing in Windows Forms controls.**</span></span> <span data-ttu-id="fcb44-1013">Tato funkce se rozšířila.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1013">This feature has been expanded.</span></span> <span data-ttu-id="fcb44-1014">Nyní můžete použít nastavení systému DPI pro změnu velikosti součástí následujících dalších ovládacích prvků (například šipky rozevíracího seznamu v polích se seznamem):</span><span class="sxs-lookup"><span data-stu-id="fcb44-1014">You can now use the system DPI setting to resize components of the following additional controls (for example, the drop-down arrow in combo boxes):</span></span>

  - <xref:System.Windows.Forms.ComboBox>
  - <xref:System.Windows.Forms.ToolStripComboBox>
  - <xref:System.Windows.Forms.ToolStripMenuItem>
  - <xref:System.Windows.Forms.Cursor>
  - <xref:System.Windows.Forms.DataGridView>
  - <xref:System.Windows.Forms.DataGridViewComboBoxColumn>

  <span data-ttu-id="fcb44-1015">Toto je funkce výslovného souhlasu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1015">This is an opt-in feature.</span></span> <span data-ttu-id="fcb44-1016">Chcete-li jej povolit, nastavte v souboru konfigurace aplikace (App. config) element `EnableWindowsFormsHighDpiAutoResizing` na hodnotu `true`:</span><span class="sxs-lookup"><span data-stu-id="fcb44-1016">To enable it, set the `EnableWindowsFormsHighDpiAutoResizing` element to `true` in the application configuration (app.config) file:</span></span>

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- <span data-ttu-id="fcb44-1017">**Nová funkce pracovního postupu.**</span><span class="sxs-lookup"><span data-stu-id="fcb44-1017">**New workflow feature.**</span></span> <span data-ttu-id="fcb44-1018">Správce prostředků, který používá metodu <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> (a proto implementuje rozhraní <xref:System.Transactions.IPromotableSinglePhaseNotification>), může použít novou metodu <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> k vyžádání následujícího:</span><span class="sxs-lookup"><span data-stu-id="fcb44-1018">A resource manager that's using the <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> method (and therefore implementing the <xref:System.Transactions.IPromotableSinglePhaseNotification> interface) can use the new <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> method to request the following:</span></span>

  - <span data-ttu-id="fcb44-1019">Povýšit transakci na transakci Microsoft DTC (Distributed Transaction Coordinator) (MSDTC).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1019">Promote the transaction to a Microsoft Distributed Transaction Coordinator (MSDTC) transaction.</span></span>

  - <span data-ttu-id="fcb44-1020">Nahraďte <xref:System.Transactions.IPromotableSinglePhaseNotification> pomocí <xref:System.Transactions.ISinglePhaseNotification>, což je trvalé zařazení, které podporuje jednotlivé fáze potvrzení.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1020">Replace <xref:System.Transactions.IPromotableSinglePhaseNotification> with an <xref:System.Transactions.ISinglePhaseNotification>, which is a durable enlistment that supports single phase commits.</span></span>

  <span data-ttu-id="fcb44-1021">To se dá udělat v rámci stejné domény aplikace a nevyžaduje žádný dodatečný nespravovaný kód pro interakci se službou MSDTC, aby bylo možné provést povýšení.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1021">This can be done within the same app domain, and doesn't require any extra unmanaged code to interact with MSDTC to perform the promotion.</span></span> <span data-ttu-id="fcb44-1022">Nová metoda může být volána pouze v případě, že existuje nedokončené volání metody <xref:System.Transactions?displayProperty=nameWithType> do metody <xref:System.Transactions.IPromotableSinglePhaseNotification> @ no__t-2, která je implementována pomocí zařazení.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1022">The new method can be called only when there's an outstanding call from <xref:System.Transactions?displayProperty=nameWithType> to the <xref:System.Transactions.IPromotableSinglePhaseNotification>`Promote` method that's implemented by the promotable enlistment.</span></span>

- <span data-ttu-id="fcb44-1023">**Vylepšení profilace.**</span><span class="sxs-lookup"><span data-stu-id="fcb44-1023">**Profiling improvements.**</span></span> <span data-ttu-id="fcb44-1024">Následující nová nespravovaná rozhraní API pro profilaci poskytují robustnější profilaci:</span><span class="sxs-lookup"><span data-stu-id="fcb44-1024">The following new unmanaged profiling APIs provide more robust profiling:</span></span>

  - [<span data-ttu-id="fcb44-1025">COR_PRF_ASSEMBLY_REFERENCE_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="fcb44-1025">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](../unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)
  - [<span data-ttu-id="fcb44-1026">COR_PRF_HIGH_MONITOR – výčet</span><span class="sxs-lookup"><span data-stu-id="fcb44-1026">COR_PRF_HIGH_MONITOR Enumeration</span></span>](../unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)
  - [<span data-ttu-id="fcb44-1027">GetAssemblyReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="fcb44-1027">GetAssemblyReferences Method</span></span>](../unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
  - [<span data-ttu-id="fcb44-1028">GetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="fcb44-1028">GetEventMask2 Method</span></span>](../unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
  - [<span data-ttu-id="fcb44-1029">SetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="fcb44-1029">SetEventMask2 Method</span></span>](../unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
  - [<span data-ttu-id="fcb44-1030">AddAssemblyReference – metoda</span><span class="sxs-lookup"><span data-stu-id="fcb44-1030">AddAssemblyReference Method</span></span>](../unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)

  <span data-ttu-id="fcb44-1031">Předchozí implementace `ICorProfiler` podporují opožděné načítání závislých sestavení.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1031">Previous `ICorProfiler` implementations supported lazy loading of dependent assemblies.</span></span> <span data-ttu-id="fcb44-1032">Nové rozhraní API pro profilování vyžadují závislá sestavení, která jsou vložená profilerem tak, aby se spustitelný hned, místo aby se načetla po úplné inicializaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1032">The new profiling APIs require dependent assemblies that are injected by the profiler to be loadable immediately, instead of being loaded after the app is fully initialized.</span></span> <span data-ttu-id="fcb44-1033">Tato změna neovlivní uživatele existujících rozhraní API `ICorProfiler`.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1033">This change doesn't affect users of the existing `ICorProfiler` APIs.</span></span>

- <span data-ttu-id="fcb44-1034">**Vylepšení ladění.**</span><span class="sxs-lookup"><span data-stu-id="fcb44-1034">**Debugging improvements.**</span></span> <span data-ttu-id="fcb44-1035">Následující nová nespravovaná ladicí rozhraní API poskytují lepší integraci s profilerem.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1035">The following new unmanaged debugging APIs provide better integration with a profiler.</span></span> <span data-ttu-id="fcb44-1036">Teď můžete přistupovat k metadatům vloženým profilerem a také k místním proměnným a kódu vytvořeným požadavky kompilátoru ReJIT při ladění výpisu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1036">You can now access metadata inserted by the profiler as well as local variables and code produced by compiler ReJIT requests when dump debugging.</span></span>

  - [<span data-ttu-id="fcb44-1037">SetWriteableMetadataUpdateMode – metoda</span><span class="sxs-lookup"><span data-stu-id="fcb44-1037">SetWriteableMetadataUpdateMode Method</span></span>](../unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
  - [<span data-ttu-id="fcb44-1038">EnumerateLocalVariablesEx – metoda</span><span class="sxs-lookup"><span data-stu-id="fcb44-1038">EnumerateLocalVariablesEx Method</span></span>](../unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)
  - [<span data-ttu-id="fcb44-1039">GetLocalVariableEx – metoda</span><span class="sxs-lookup"><span data-stu-id="fcb44-1039">GetLocalVariableEx Method</span></span>](../unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)
  - [<span data-ttu-id="fcb44-1040">GetCodeEx – metoda</span><span class="sxs-lookup"><span data-stu-id="fcb44-1040">GetCodeEx Method</span></span>](../unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)
  - [<span data-ttu-id="fcb44-1041">GetActiveReJitRequestILCode – metoda</span><span class="sxs-lookup"><span data-stu-id="fcb44-1041">GetActiveReJitRequestILCode Method</span></span>](../unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)
  - [<span data-ttu-id="fcb44-1042">GetInstrumentedILMap – metoda</span><span class="sxs-lookup"><span data-stu-id="fcb44-1042">GetInstrumentedILMap Method</span></span>](../unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)

- <span data-ttu-id="fcb44-1043">**Změny trasování událostí.**</span><span class="sxs-lookup"><span data-stu-id="fcb44-1043">**Event tracing changes.**</span></span> <span data-ttu-id="fcb44-1044">.NET Framework 4.5.2 umožňuje trasování aktivit založené na trasování událostí pro Windows (ETW) pro větší plochu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1044">.NET Framework 4.5.2 enables out-of-process, Event Tracing for Windows (ETW)-based activity tracing for a larger surface area.</span></span> <span data-ttu-id="fcb44-1045">To umožňuje prodejcům pokročilého řízení spotřeby (APM) poskytovat odlehčené nástroje, které přesně sledují náklady na jednotlivé požadavky a aktivity, které procházejí vlákny.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1045">This enables Advanced Power Management (APM) vendors to provide lightweight tools that accurately track the costs of individual requests and activities that cross threads.</span></span>  <span data-ttu-id="fcb44-1046">Tyto události jsou vyvolány pouze v případě, že je povolí řadič ETW. Proto změny neovlivní dříve psaný kód ETW nebo kód, který běží se zakázanou ETW.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1046">These events are raised only when ETW controllers enable them; therefore, the changes don't affect previously written ETW code or code that runs with ETW disabled.</span></span>

- <span data-ttu-id="fcb44-1047">**Zvýšení úrovně transakce a její převedení na trvalý zařazení**</span><span class="sxs-lookup"><span data-stu-id="fcb44-1047">**Promoting a transaction and converting it to a durable enlistment**</span></span>

  <span data-ttu-id="fcb44-1048"><xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> je nové rozhraní API přidané do .NET Framework 4.5.2 a 4,6:</span><span class="sxs-lookup"><span data-stu-id="fcb44-1048"><xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> is a new API added to .NET Framework 4.5.2 and 4.6:</span></span>

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

  <span data-ttu-id="fcb44-1049">Metodu lze použít pro zařazení, které bylo dříve vytvořeno pomocí <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> v reakci na metodu <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1049">The method may be used by an enlistment that was previously created by <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> in response to the <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fcb44-1050">Žádá `System.Transactions`, aby se transakce povýší na transakci MSDTC a na "převést" zařazení do trvalého zařazení.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1050">It asks `System.Transactions` to promote the transaction to an MSDTC transaction and to "convert" the promotable enlistment to a durable enlistment.</span></span> <span data-ttu-id="fcb44-1051">Po úspěšném dokončení této metody již nebude na rozhraní @no__t 0 odkazováno pomocí `System.Transactions` a veškerá budoucí oznámení budou doručena v zadaném rozhraní <xref:System.Transactions.ISinglePhaseNotification>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1051">After this method completes successfully, the <xref:System.Transactions.IPromotableSinglePhaseNotification> interface will no longer be referenced by `System.Transactions`, and any future notifications will arrive on the provided <xref:System.Transactions.ISinglePhaseNotification> interface.</span></span> <span data-ttu-id="fcb44-1052">Příslušné zařazení musí působit jako trvalé zařazení, které podporuje protokolování a obnovení transakcí.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1052">The enlistment in question must act as a durable enlistment, supporting transaction logging and recovery.</span></span> <span data-ttu-id="fcb44-1053">Podrobnosti najdete v <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1053">Refer to <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType> for details.</span></span> <span data-ttu-id="fcb44-1054">Zařazení navíc musí podporovat <xref:System.Transactions.ISinglePhaseNotification>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1054">In addition, the enlistment must support <xref:System.Transactions.ISinglePhaseNotification>.</span></span>  <span data-ttu-id="fcb44-1055">Tuto metodu lze volat *pouze* během zpracování volání <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1055">This method can *only* be called while processing an <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> call.</span></span> <span data-ttu-id="fcb44-1056">V takovém případě je vyvolána výjimka <xref:System.Transactions.TransactionException>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1056">If that is not the case, a <xref:System.Transactions.TransactionException> exception is thrown.</span></span>

<a name="v451" />

## <a name="whats-new-in-net-framework-451"></a><span data-ttu-id="fcb44-1057">Co je nového ve .NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="fcb44-1057">What's new in .NET Framework 4.5.1</span></span>

<span data-ttu-id="fcb44-1058">**Aktualizace z dubna 2014**:</span><span class="sxs-lookup"><span data-stu-id="fcb44-1058">**April 2014 updates**:</span></span>

- <span data-ttu-id="fcb44-1059">[Visual Studio 2013 aktualizace 2](https://go.microsoft.com/fwlink/p/?LinkId=393658) obsahuje aktualizace šablon přenosných knihoven tříd pro podporu těchto scénářů:</span><span class="sxs-lookup"><span data-stu-id="fcb44-1059">[Visual Studio 2013 Update 2](https://go.microsoft.com/fwlink/p/?LinkId=393658) includes updates to the Portable Class Library templates to support these scenarios:</span></span>

  - <span data-ttu-id="fcb44-1060">Rozhraní prostředí Windows Runtime API můžete použít v přenosných knihovnách, které cílí na Windows 8.1, Windows Phone 8,1 a Windows Phone Silverlight 8,1.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1060">You can use Windows Runtime APIs in portable libraries that target Windows 8.1, Windows Phone 8.1, and Windows Phone Silverlight 8.1.</span></span>

  - <span data-ttu-id="fcb44-1061">Když cílíte Windows 8.1 nebo Windows Phone 8,1, můžete do přenosných knihoven zahrnout XAML (typy Windows. UI. XAML).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1061">You can include XAML (Windows.UI.XAML types) in portable libraries when you target Windows 8.1 or Windows Phone 8.1.</span></span> <span data-ttu-id="fcb44-1062">Podporovány jsou následující šablony XAML:  Prázdná stránka, slovník prostředků, ovládací prvek bez vizuálního vzhledu a uživatelský ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1062">The following XAML templates are supported:  Blank Page, Resource Dictionary, Templated Control, and User Control.</span></span>

  - <span data-ttu-id="fcb44-1063">Můžete vytvořit přenosnou součást prostředí Windows Runtime (soubor. winmd) pro použití v aplikacích pro Store, které cílí na Windows 8.1 a Windows Phone 8,1.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1063">You can create a portable Windows Runtime component (.winmd file) for use in Store apps that target Windows 8.1 and Windows Phone 8.1.</span></span>

  - <span data-ttu-id="fcb44-1064">Můžete změnit cíl knihovny tříd Windows Store nebo Windows Phone Store, jako je Přenosná knihovna tříd.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1064">You can retarget a Windows Store or Windows Phone Store class library like a Portable Class Library.</span></span>

  <span data-ttu-id="fcb44-1065">Další informace o těchto změnách naleznete v tématu [Přenosná knihovna tříd](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1065">For more information about these changes, see [Portable Class Library](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).</span></span>

- <span data-ttu-id="fcb44-1066">Sada .NET Framework obsahu teď obsahuje dokumentaci pro .NET Native, což je předkompilace technologie pro sestavování a nasazování aplikací pro Windows.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1066">The .NET Framework content set now includes documentation for .NET Native, which is a precompilation technology for building and deploying Windows apps.</span></span> <span data-ttu-id="fcb44-1067">.NET Native zkompiluje vaše aplikace přímo do nativního kódu, spíše než do mezilehlého jazyka (IL), pro lepší výkon.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1067">.NET Native compiles your apps directly to native code, rather than to intermediate language (IL), for better performance.</span></span> <span data-ttu-id="fcb44-1068">Podrobnosti najdete v tématu [kompilace aplikací pomocí .NET Native](../net-native/index.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1068">For details, see [Compiling Apps with .NET Native](../net-native/index.md).</span></span>

- <span data-ttu-id="fcb44-1069">[Zdroj odkazů .NET Framework](https://referencesource.microsoft.com/) poskytuje nové prostředí pro procházení a vylepšené funkce.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1069">The [.NET Framework Reference Source](https://referencesource.microsoft.com/) provides a new browsing experience and enhanced functionality.</span></span> <span data-ttu-id="fcb44-1070">Nyní můžete procházet zdrojový kód .NET Framework online, [stahovat reference](https://referencesource.microsoft.com/download.html) pro zobrazení v režimu offline a procházet zdroje (včetně oprav a aktualizací) během ladění.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1070">You can now browse through the .NET Framework source code online, [download the reference](https://referencesource.microsoft.com/download.html) for offline viewing, and step through the sources (including patches and updates) during debugging.</span></span> <span data-ttu-id="fcb44-1071">Další informace najdete v blogu o [novém hledání zdroje odkazů .NET](https://devblogs.microsoft.com/dotnet/a-new-look-for-net-reference-source/).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1071">For more information, see the blog entry [A new look for .NET Reference Source](https://devblogs.microsoft.com/dotnet/a-new-look-for-net-reference-source/).</span></span>

<span data-ttu-id="fcb44-1072">Mezi nové funkce a vylepšení základních tříd v .NET Framework 4.5.1 patří:</span><span class="sxs-lookup"><span data-stu-id="fcb44-1072">New features and enhancements in the base classes in .NET Framework 4.5.1 include:</span></span>

- <span data-ttu-id="fcb44-1073">Automatické přesměrování vazby pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1073">Automatic binding redirection for assemblies.</span></span> <span data-ttu-id="fcb44-1074">Počínaje Visual Studio 2013 se při kompilování aplikace, která cílí na .NET Framework 4.5.1, dají přesměrování vazby přidat do konfiguračního souboru aplikace, pokud vaše aplikace nebo její součásti odkazují na více verzí stejného sestavení.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1074">Starting with Visual Studio 2013, when you compile an app that targets the .NET Framework 4.5.1, binding redirects may be added to the app configuration file if your app or its components reference multiple versions of the same assembly.</span></span> <span data-ttu-id="fcb44-1075">Tuto funkci můžete také povolit pro projekty, které cílí na starší verze .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1075">You can also enable this feature for projects that target older versions of the .NET Framework.</span></span> <span data-ttu-id="fcb44-1076">Další informace najdete v tématu [jak: Povolí nebo zakáže automatické přesměrování](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)vazby.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1076">For more information, see [How to: Enable and Disable Automatic Binding Redirection](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).</span></span>

- <span data-ttu-id="fcb44-1077">Možnost shromažďovat diagnostické informace, které vývojářům pomůžou zlepšit výkon serverových a cloudových aplikací.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1077">Ability to collect diagnostics information to help developers improve the performance of server and cloud applications.</span></span> <span data-ttu-id="fcb44-1078">Další informace naleznete v tématu metody <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> a <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> ve třídě <xref:System.Diagnostics.Tracing.EventSource>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1078">For more information, see the <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> and <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> methods in the <xref:System.Diagnostics.Tracing.EventSource> class.</span></span>

- <span data-ttu-id="fcb44-1079">Schopnost explicitně komprimovat haldu velkých objektů (LOH) během uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1079">Ability to explicitly compact the large object heap (LOH) during garbage collection.</span></span> <span data-ttu-id="fcb44-1080">Další informace najdete v tématu <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1080">For more information, see the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> property.</span></span>

- <span data-ttu-id="fcb44-1081">Další vylepšení výkonu, jako je například pozastavení aplikace ASP.NET, vícejazykové vylepšení JIT a rychlejší spuštění aplikace po aktualizaci .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1081">Additional performance improvements such as ASP.NET app suspension, multi-core JIT improvements, and faster app startup after a .NET Framework update.</span></span> <span data-ttu-id="fcb44-1082">Podrobnosti najdete v příspěvku na blogu [.NET Framework 4.5.1](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/) a v blogovém příspěvku o [pozastavení aplikace ASP.NET](https://devblogs.microsoft.com/dotnet/asp-net-app-suspend-responsive-shared-net-web-hosting/) .</span><span class="sxs-lookup"><span data-stu-id="fcb44-1082">For details, see the [.NET Framework 4.5.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/) and the [ASP.NET app suspend](https://devblogs.microsoft.com/dotnet/asp-net-app-suspend-responsive-shared-net-web-hosting/) blog post.</span></span>

<span data-ttu-id="fcb44-1083">Mezi vylepšení model Windows Forms patří:</span><span class="sxs-lookup"><span data-stu-id="fcb44-1083">Improvements to Windows Forms include:</span></span>

- <span data-ttu-id="fcb44-1084">Změna velikosti v ovládacích prvcích model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1084">Resizing in Windows Forms controls.</span></span> <span data-ttu-id="fcb44-1085">Můžete použít nastavení systému DPI pro změnu velikosti komponent ovládacích prvků (například ikony, které se zobrazí v mřížce vlastností), tím, že se přiřadíte k položce v konfiguračním souboru aplikace (App. config) pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1085">You can use the system DPI setting to resize components of controls (for example, the icons that appear in a property grid) by opting in with an entry in the application configuration file (app.config) for your app.</span></span> <span data-ttu-id="fcb44-1086">Tato funkce je aktuálně podporována v následujících ovládacích prvcích model Windows Forms:</span><span class="sxs-lookup"><span data-stu-id="fcb44-1086">This feature is currently supported in the following Windows Forms controls:</span></span>

  - <xref:System.Windows.Forms.PropertyGrid>
  - <xref:System.Windows.Forms.TreeView>
  - <span data-ttu-id="fcb44-1087">Některé aspekty <xref:System.Windows.Forms.DataGridView> (další podporované ovládací prvky najdete [v části nové funkce v 4.5.2](#v452) )</span><span class="sxs-lookup"><span data-stu-id="fcb44-1087">Some aspects of the <xref:System.Windows.Forms.DataGridView> (see [new features in 4.5.2](#v452) for additional controls supported)</span></span>

  <span data-ttu-id="fcb44-1088">Chcete-li povolit tuto funkci, přidejte nový prvek \<appSettings > do konfiguračního souboru (App. config) a nastavte prvek `EnableWindowsFormsHighDpiAutoResizing` na `true`:</span><span class="sxs-lookup"><span data-stu-id="fcb44-1088">To enable this feature, add a new \<appSettings> element to the configuration file (app.config) and set the `EnableWindowsFormsHighDpiAutoResizing` element to `true`:</span></span>

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

<span data-ttu-id="fcb44-1089">Vylepšení při ladění .NET Frameworkch aplikací v Visual Studio 2013 zahrnují:</span><span class="sxs-lookup"><span data-stu-id="fcb44-1089">Improvements when debugging your .NET Framework apps in Visual Studio 2013 include:</span></span>

- <span data-ttu-id="fcb44-1090">Návratové hodnoty v ladicím programu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1090">Return values in the Visual Studio debugger.</span></span> <span data-ttu-id="fcb44-1091">Při ladění spravované aplikace v Visual Studio 2013 zobrazí okno Automatické hodnoty návratové typy a hodnoty pro metody.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1091">When you debug a managed app in Visual Studio 2013, the Autos window displays return types and values for methods.</span></span> <span data-ttu-id="fcb44-1092">Tyto informace jsou k dispozici pro stolní počítače, Windows Store a aplikace Windows Phone.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1092">This information is available for desktop, Windows Store, and Windows Phone apps.</span></span> <span data-ttu-id="fcb44-1093">Další informace naleznete v tématu [Kontrola vrácených hodnot volání metody](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/dn323257(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1093">For more information, see [Examine return values of method calls](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/dn323257(v=vs.120)).</span></span>

- <span data-ttu-id="fcb44-1094">Upravit a pokračovat pro 64 aplikace</span><span class="sxs-lookup"><span data-stu-id="fcb44-1094">Edit and Continue for 64-bit apps.</span></span> <span data-ttu-id="fcb44-1095">Visual Studio 2013 podporuje funkci upravit a pokračovat pro 64 spravované aplikace pro stolní počítače, Windows Store a Windows Phone.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1095">Visual Studio 2013 supports the Edit and Continue feature for 64-bit managed apps for desktop, Windows Store, and Windows Phone.</span></span> <span data-ttu-id="fcb44-1096">Stávající omezení zůstávají v platnosti pro 32 i pro 64-bitové aplikace (viz poslední část článku [podporované změny kóduC#()](/visualstudio/debugger/supported-code-changes-csharp) ).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1096">The existing limitations remain in effect for both 32-bit and 64-bit apps (see the last section of the [Supported Code Changes (C#)](/visualstudio/debugger/supported-code-changes-csharp) article).</span></span>

- <span data-ttu-id="fcb44-1097">Asynchronní ladění.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1097">Async-aware debugging.</span></span> <span data-ttu-id="fcb44-1098">Aby bylo snazší ladit asynchronní aplikace v Visual Studio 2013, zásobník volání skrývá kód infrastruktury poskytnutý kompilátory pro podporu asynchronního programování a také řetězení v logických nadřazených snímcích, aby bylo možné sledovat provádění logických programů. zřejmě.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1098">To make it easier to debug asynchronous apps in Visual Studio 2013, the call stack hides the infrastructure code provided by compilers to support asynchronous programming, and also chains in logical parent frames so you can follow logical program execution more clearly.</span></span> <span data-ttu-id="fcb44-1099">Okno úkoly nahrazuje okno paralelní úkoly a zobrazuje úkoly, které se vztahují k určité zarážce, a také zobrazí všechny další úkoly, které jsou v aplikaci aktuálně aktivní nebo naplánované.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1099">A Tasks window replaces the Parallel Tasks window and displays tasks that relate to a particular breakpoint, and also displays any other tasks that are currently active or scheduled in the app.</span></span> <span data-ttu-id="fcb44-1100">O této funkci si můžete přečíst v části "asynchronní ladění" v [oznámení .NET Framework 4.5.1](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1100">You can read about this feature in the "Async-aware debugging" section of the [.NET Framework 4.5.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).</span></span>

- <span data-ttu-id="fcb44-1101">Lepší podpora výjimek pro součásti prostředí Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1101">Better exception support for Windows Runtime components.</span></span> <span data-ttu-id="fcb44-1102">V [!INCLUDE[win81](../../../includes/win81-md.md)] výjimky, které vznikají v aplikacích pro Windows Store, uchovávají informace o chybě, která způsobila výjimku, i přes hranice jazyka.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1102">In [!INCLUDE[win81](../../../includes/win81-md.md)], exceptions that arise from Windows Store apps preserve information about the error that caused the exception, even across language boundaries.</span></span> <span data-ttu-id="fcb44-1103">O této funkci si můžete přečíst v části vývoj aplikací pro Windows Store v [oznámení .NET Framework 4.5.1](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1103">You can read about this feature in the "Windows Store app development" section of the [.NET Framework 4.5.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).</span></span>

<span data-ttu-id="fcb44-1104">Počínaje Visual Studio 2013 můžete pomocí [nástroje optimalizace spravovaného profilu (nástroj Mpgo. exe)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md) optimalizovat aplikace [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] i aplikace klasické pracovní plochy.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1104">Starting with Visual Studio 2013, you can use the [Managed Profile Guided Optimization Tool (Mpgo.exe)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md) to optimize [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps as well as desktop apps.</span></span>

<span data-ttu-id="fcb44-1105">Nové funkce v ASP.NET 4.5.1 najdete v tématu [ASP.NET and Web Tools for Visual Studio 2013 poznámky k verzi](/aspnet/visual-studio/overview/2013/release-notes).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1105">For new features in ASP.NET 4.5.1, see [ASP.NET and Web Tools for Visual Studio 2013 Release Notes](/aspnet/visual-studio/overview/2013/release-notes).</span></span>

<a name="v45" />

## <a name="whats-new-in-net-framework-45"></a><span data-ttu-id="fcb44-1106">Co je nového v .NET Framework 4,5</span><span class="sxs-lookup"><span data-stu-id="fcb44-1106">What's new in .NET Framework 4.5</span></span>

### <a name="base-classes"></a><span data-ttu-id="fcb44-1107">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="fcb44-1107">Base classes</span></span>

- <span data-ttu-id="fcb44-1108">Schopnost snížit restart systému tím, že během nasazení detekuje a zavírá aplikace .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1108">Ability to reduce system restarts by detecting and closing .NET Framework 4 applications during deployment.</span></span> <span data-ttu-id="fcb44-1109">Viz [snížení počtu restartování systému během instalace .NET Framework 4,5](../deployment/reducing-system-restarts.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1109">See [Reducing System Restarts During .NET Framework 4.5 Installations](../deployment/reducing-system-restarts.md).</span></span>

- <span data-ttu-id="fcb44-1110">Podpora pro pole, která jsou větší než 2 gigabajty (GB) na 64-bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1110">Support for arrays that are larger than 2 gigabytes (GB) on 64-bit platforms.</span></span> <span data-ttu-id="fcb44-1111">Tato funkce se dá povolit v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1111">This feature can be enabled in the application configuration file.</span></span> <span data-ttu-id="fcb44-1112">Podívejte se na [prvek > \<gcAllowVeryLargeObjects](../configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md), který obsahuje také další omezení velikosti objektu a velikosti pole.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1112">See the [\<gcAllowVeryLargeObjects> element](../configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md), which also lists other restrictions on object size and array size.</span></span>

- <span data-ttu-id="fcb44-1113">Lepší výkon při uvolňování paměti na pozadí pro servery.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1113">Better performance through background garbage collection for servers.</span></span> <span data-ttu-id="fcb44-1114">Pokud používáte systém uvolňování paměti serveru v .NET Framework 4,5, automatické uvolňování paměti na pozadí je povoleno.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1114">When you use server garbage collection in the .NET Framework 4.5, background garbage collection is automatically enabled.</span></span> <span data-ttu-id="fcb44-1115">V tématu [základní informace o uvolňování paměti](../../standard/garbage-collection/fundamentals.md) najdete v části uvolňování paměti serveru na pozadí.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1115">See the Background Server Garbage Collection section of the [Fundamentals of Garbage Collection](../../standard/garbage-collection/fundamentals.md) topic.</span></span>

- <span data-ttu-id="fcb44-1116">Kompilace JIT (just-in-time), která je volitelně dostupná pro procesory s více jádry ke zlepšení výkonu aplikace.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1116">Background just-in-time (JIT) compilation, which is optionally available on multi-core processors to improve application performance.</span></span> <span data-ttu-id="fcb44-1117">Viz <xref:System.Runtime.ProfileOptimization>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1117">See <xref:System.Runtime.ProfileOptimization>.</span></span>

- <span data-ttu-id="fcb44-1118">Možnost omezit dobu, po kterou se modul regulárních výrazů pokusí přeložit regulární výraz předtím, než vyprší jeho časový limit. Podívejte se <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=nameWithType> na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1118">Ability to limit how long the regular expression engine will attempt to resolve a regular expression before it times out. See the <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=nameWithType> property.</span></span>

- <span data-ttu-id="fcb44-1119">Možnost definovat výchozí jazykovou verzi pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1119">Ability to define the default culture for an application domain.</span></span> <span data-ttu-id="fcb44-1120">Podívejte se na třídu <xref:System.Globalization.CultureInfo>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1120">See the <xref:System.Globalization.CultureInfo> class.</span></span>

- <span data-ttu-id="fcb44-1121">Podpora konzoly pro kódování Unicode (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1121">Console support for Unicode (UTF-16) encoding.</span></span> <span data-ttu-id="fcb44-1122">Podívejte se na třídu <xref:System.Console>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1122">See the <xref:System.Console> class.</span></span>

- <span data-ttu-id="fcb44-1123">Podpora správy verzí pro kulturní řazení řetězců a porovnávání dat.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1123">Support for versioning of cultural string ordering and comparison data.</span></span> <span data-ttu-id="fcb44-1124">Podívejte se na třídu <xref:System.Globalization.SortVersion>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1124">See the <xref:System.Globalization.SortVersion> class.</span></span>

- <span data-ttu-id="fcb44-1125">Lepší výkon při načítání prostředků.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1125">Better performance when retrieving resources.</span></span> <span data-ttu-id="fcb44-1126">Viz [balení a nasazení prostředků](../resources/packaging-and-deploying-resources-in-desktop-apps.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1126">See [Packaging and Deploying Resources](../resources/packaging-and-deploying-resources-in-desktop-apps.md).</span></span>

- <span data-ttu-id="fcb44-1127">Vylepšení komprese zip ke zmenšení velikosti komprimovaného souboru.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1127">Zip compression improvements to reduce the size of a compressed file.</span></span> <span data-ttu-id="fcb44-1128">Podívejte se na obor názvů <xref:System.IO.Compression?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1128">See the <xref:System.IO.Compression?displayProperty=nameWithType> namespace.</span></span>

- <span data-ttu-id="fcb44-1129">Možnost přizpůsobit kontext odrazu pro přepsání výchozího chování reflexe prostřednictvím třídy <xref:System.Reflection.Context.CustomReflectionContext>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1129">Ability to customize a reflection context to override default reflection behavior through the <xref:System.Reflection.Context.CustomReflectionContext> class.</span></span>

- <span data-ttu-id="fcb44-1130">Podpora verze 2008 mezinárodních názvů domén v aplikacích (IDNA) standard, pokud se třída <xref:System.Globalization.IdnMapping?displayProperty=nameWithType> používá v [!INCLUDE[win8](../../../includes/win8-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fcb44-1130">Support for the 2008 version of the Internationalized Domain Names in Applications (IDNA) standard when the <xref:System.Globalization.IdnMapping?displayProperty=nameWithType> class is used  on [!INCLUDE[win8](../../../includes/win8-md.md)].</span></span>

- <span data-ttu-id="fcb44-1131">Delegování porovnání řetězců k operačnímu systému, které implementuje kódování Unicode 6,0, pokud je .NET Framework použito v [!INCLUDE[win8](../../../includes/win8-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fcb44-1131">Delegation of string comparison to the operating system, which implements Unicode 6.0, when the .NET Framework is used on [!INCLUDE[win8](../../../includes/win8-md.md)].</span></span> <span data-ttu-id="fcb44-1132">Při spuštění na jiných platformách .NET Framework zahrnuje vlastní data porovnání řetězců, která implementují Unicode 5. x.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1132">When running on other platforms, the .NET Framework includes its own string comparison data, which implements Unicode 5.x.</span></span> <span data-ttu-id="fcb44-1133">Podívejte se na třídu <xref:System.String> a oddíl poznámky třídy <xref:System.Globalization.SortVersion>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1133">See the <xref:System.String> class and the Remarks section of the <xref:System.Globalization.SortVersion> class.</span></span>

- <span data-ttu-id="fcb44-1134">Možnost vypočítat kódy hash pro řetězce na základě domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1134">Ability to compute the hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="fcb44-1135">Viz [\<UseRandomizedStringHashAlgorithm > element](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1135">See [\<UseRandomizedStringHashAlgorithm> Element](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).</span></span>

- <span data-ttu-id="fcb44-1136">Podpora reflexe typu je rozdělená mezi <xref:System.Type> a třídy <xref:System.Reflection.TypeInfo>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1136">Type reflection support split between <xref:System.Type> and <xref:System.Reflection.TypeInfo> classes.</span></span> <span data-ttu-id="fcb44-1137">Podívejte [se na reflexi v .NET Framework pro aplikace pro Windows Store](../reflection-and-codedom/reflection-for-windows-store-apps.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1137">See [Reflection in the .NET Framework for Windows Store Apps](../reflection-and-codedom/reflection-for-windows-store-apps.md).</span></span>

### <a name="managed-extensibility-framework-mef"></a><span data-ttu-id="fcb44-1138">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="fcb44-1138">Managed Extensibility Framework (MEF)</span></span>

<span data-ttu-id="fcb44-1139">V .NET Framework 4,5 obsahuje Managed Extensibility Framework (MEF) tyto nové funkce:</span><span class="sxs-lookup"><span data-stu-id="fcb44-1139">In the .NET Framework 4.5, the Managed Extensibility Framework (MEF) provides the following new features:</span></span>

- <span data-ttu-id="fcb44-1140">Podpora pro obecné typy.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1140">Support for generic types.</span></span>

- <span data-ttu-id="fcb44-1141">Programovací model založený na konvencích, který umožňuje vytvářet části na základě konvencí pojmenování, nikoli atributů.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1141">Convention-based programming model that enables you to create parts based on naming conventions rather than attributes.</span></span>

- <span data-ttu-id="fcb44-1142">Více oborů.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1142">Multiple scopes.</span></span>

- <span data-ttu-id="fcb44-1143">Podmnožina MEF, kterou můžete použít při vytváření aplikací [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fcb44-1143">A subset of MEF that you can use when you create [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span> <span data-ttu-id="fcb44-1144">Tato podmnožina je k dispozici jako [balíček ke stažení](https://go.microsoft.com/fwlink/?LinkId=256238) z galerie NuGet.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1144">This subset is available as a [downloadable package](https://go.microsoft.com/fwlink/?LinkId=256238) from the NuGet Gallery.</span></span> <span data-ttu-id="fcb44-1145">Chcete-li nainstalovat balíček, otevřete projekt v aplikaci Visual Studio, v nabídce **projekt** vyberte možnost **Spravovat balíčky NuGet** a vyhledejte balíček `Microsoft.Composition` v online režimu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1145">To install the package, open your project in Visual Studio, choose **Manage NuGet Packages** from the **Project** menu, and search online for the `Microsoft.Composition` package.</span></span>

<span data-ttu-id="fcb44-1146">Další informace naleznete v tématu [Managed Extensibility Framework (MEF)](../mef/index.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1146">For more information, see [Managed Extensibility Framework (MEF)](../mef/index.md).</span></span>

### <a name="asynchronous-file-operations"></a><span data-ttu-id="fcb44-1147">Asynchronní operace se soubory</span><span class="sxs-lookup"><span data-stu-id="fcb44-1147">Asynchronous file operations</span></span>

<span data-ttu-id="fcb44-1148">V .NET Framework 4,5 byly do jazyků C# a Visual Basic přidány nové asynchronní funkce.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1148">In the .NET Framework 4.5, new asynchronous features were added to the C# and Visual Basic languages.</span></span> <span data-ttu-id="fcb44-1149">Tyto funkce přidávají model založený na úlohách pro provádění asynchronních operací.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1149">These features add a task-based model for performing asynchronous operations.</span></span> <span data-ttu-id="fcb44-1150">Chcete-li použít tento nový model, použijte asynchronní metody v I/O třídách.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1150">To use this new model, use the asynchronous methods in the I/O classes.</span></span> <span data-ttu-id="fcb44-1151">Viz [asynchronní vstupně-výstupní operace se soubory](../../standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1151">See [Asynchronous File I/O](../../standard/io/asynchronous-file-i-o.md).</span></span>

<a name="tools" />

### <a name="tools"></a><span data-ttu-id="fcb44-1152">Nástroje</span><span class="sxs-lookup"><span data-stu-id="fcb44-1152">Tools</span></span>

<span data-ttu-id="fcb44-1153">V .NET Framework 4,5 umožňuje generátor souboru prostředků (Resgen. exe) vytvořit soubor. resw pro použití v aplikacích [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] ze souboru. Resources vloženého do sestavení .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1153">In the .NET Framework 4.5, Resource File Generator (Resgen.exe) enables you to create a .resw file for use in [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps from a .resources file embedded in a .NET Framework assembly.</span></span> <span data-ttu-id="fcb44-1154">Další informace naleznete v tématu [Resgen. exe (generátor zdrojových souborů)](../tools/resgen-exe-resource-file-generator.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1154">For more information, see [Resgen.exe (Resource File Generator)](../tools/resgen-exe-resource-file-generator.md).</span></span>

<span data-ttu-id="fcb44-1155">Optimalizace na základě spravovaného profilu (nástroj Mpgo. exe) umožňuje zlepšit dobu spuštění aplikace, využití paměti (velikost pracovní sady) a propustnost optimalizací sestavení nativních imagí.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1155">Managed Profile Guided Optimization (Mpgo.exe) enables you to improve application startup time, memory utilization (working set size), and throughput by optimizing native image assemblies.</span></span> <span data-ttu-id="fcb44-1156">Nástroj příkazového řádku generuje data profilu pro sestavení aplikace nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1156">The command-line tool generates profile data for native image application assemblies.</span></span> <span data-ttu-id="fcb44-1157">Viz [nástroj Mpgo. exe (Nástroj pro optimalizaci spravovaného profilu)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1157">See [Mpgo.exe (Managed Profile Guided Optimization Tool)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md).</span></span> <span data-ttu-id="fcb44-1158">Počínaje Visual Studio 2013 můžete pomocí nástroj Mpgo. exe optimalizovat aplikace [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] i desktopové aplikace.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1158">Starting with Visual Studio 2013, you can use Mpgo.exe to optimize [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps as well as desktop apps.</span></span>

<a name="parallel" />

### <a name="parallel-computing"></a><span data-ttu-id="fcb44-1159">Paralelní výpočetní prostředí</span><span class="sxs-lookup"><span data-stu-id="fcb44-1159">Parallel computing</span></span>

<span data-ttu-id="fcb44-1160">.NET Framework 4,5 obsahuje několik nových funkcí a vylepšení paralelního zpracování.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1160">The .NET Framework 4.5 provides several new features and improvements for parallel computing.</span></span> <span data-ttu-id="fcb44-1161">Mezi ně patří Vylepšený výkon, zvýšené řízení, vylepšená podpora pro asynchronní programování, nová knihovna toku dat a vylepšená podpora pro paralelní ladění a analýzu výkonu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1161">These include improved performance, increased control, improved support for asynchronous programming, a new dataflow library, and improved support for parallel debugging and performance analysis.</span></span> <span data-ttu-id="fcb44-1162">Informace o [tom, co je nového pro paralelismus v .net 4,5](https://go.microsoft.com/fwlink/?LinkId=235061) , najdete v blogu věnovaném paralelnímu programování pomocí .NET.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1162">See the entry [What’s New for Parallelism in .NET 4.5](https://go.microsoft.com/fwlink/?LinkId=235061) in the Parallel Programming with .NET blog.</span></span>

<a name="web" />

### <a name="web"></a><span data-ttu-id="fcb44-1163">Web</span><span class="sxs-lookup"><span data-stu-id="fcb44-1163">Web</span></span>

<span data-ttu-id="fcb44-1164">ASP.NET 4,5 a 4.5.1 přidávají vazbu modelu pro webové formuláře, podporu WebSocket, asynchronní obslužné rutiny, vylepšení výkonu a mnoho dalších funkcí.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1164">ASP.NET 4.5 and 4.5.1 add model binding for Web Forms, WebSocket support, asynchronous handlers, performance enhancements, and many other features.</span></span> <span data-ttu-id="fcb44-1165">Další informace naleznete v následujících materiálech:</span><span class="sxs-lookup"><span data-stu-id="fcb44-1165">For more information, see the following resources:</span></span>

- <span data-ttu-id="fcb44-1166">[ASP.NET 4,5 a Visual Studio 2012](https://docs.microsoft.com/previous-versions/aspnet/hh420390(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="fcb44-1166">[ASP.NET 4.5 and Visual Studio 2012](https://docs.microsoft.com/previous-versions/aspnet/hh420390(v=vs.110))</span></span>

- [<span data-ttu-id="fcb44-1167">ASP.NET a webové nástroje pro Visual Studio 2013 – poznámky k verzi</span><span class="sxs-lookup"><span data-stu-id="fcb44-1167">ASP.NET and Web Tools for Visual Studio 2013 Release Notes</span></span>](/aspnet/visual-studio/overview/2013/release-notes)

### <a name="networking-a-namenetworking-"></a><span data-ttu-id="fcb44-1168">Síťové @no__t – 0</span><span class="sxs-lookup"><span data-stu-id="fcb44-1168">Networking <a name="networking" /></span></span>

<span data-ttu-id="fcb44-1169">.NET Framework 4,5 poskytuje nové programovací rozhraní pro aplikace HTTP.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1169">The .NET Framework 4.5 provides a new programming interface for HTTP applications.</span></span> <span data-ttu-id="fcb44-1170">Další informace najdete v tématu nové obory názvů <xref:System.Net.Http?displayProperty=nameWithType> a <xref:System.Net.Http.Headers?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1170">For more information, see the new <xref:System.Net.Http?displayProperty=nameWithType> and <xref:System.Net.Http.Headers?displayProperty=nameWithType> namespaces.</span></span>

<span data-ttu-id="fcb44-1171">Podpora je také k dispozici pro nové programovací rozhraní pro příjem a interakci s připojením protokolu WebSocket pomocí existující <xref:System.Net.HttpListener> a souvisejících tříd.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1171">Support is also included for a new programming interface for accepting and interacting with a WebSocket connection by using the existing <xref:System.Net.HttpListener> and related classes.</span></span> <span data-ttu-id="fcb44-1172">Další informace najdete v tématu nový obor názvů <xref:System.Net.WebSockets> a třída <xref:System.Net.HttpListener>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1172">For more information, see the new <xref:System.Net.WebSockets> namespace and the <xref:System.Net.HttpListener> class.</span></span>

<span data-ttu-id="fcb44-1173">Kromě toho .NET Framework 4,5 zahrnuje následující vylepšení sítě:</span><span class="sxs-lookup"><span data-stu-id="fcb44-1173">In addition, the .NET Framework 4.5 includes the following networking improvements:</span></span>

- <span data-ttu-id="fcb44-1174">Podpora identifikátoru URI kompatibilního se specifikací RFC.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1174">RFC-compliant URI support.</span></span> <span data-ttu-id="fcb44-1175">Další informace naleznete v tématu <xref:System.Uri> a související třídy.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1175">For more information, see <xref:System.Uri> and related classes.</span></span>

- <span data-ttu-id="fcb44-1176">Podpora pro analýzu mezinárodních názvů domén (IDN).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1176">Support for Internationalized Domain Name (IDN) parsing.</span></span> <span data-ttu-id="fcb44-1177">Další informace naleznete v tématu <xref:System.Uri> a související třídy.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1177">For more information, see <xref:System.Uri> and related classes.</span></span>

- <span data-ttu-id="fcb44-1178">Podpora mezinárodní adresy e-mailové adresy (EAI).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1178">Support for Email Address Internationalization (EAI).</span></span> <span data-ttu-id="fcb44-1179">Další informace najdete v oboru názvů <xref:System.Net.Mail>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1179">For more information, see the <xref:System.Net.Mail> namespace.</span></span>

- <span data-ttu-id="fcb44-1180">Vylepšená podpora protokolu IPv6.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1180">Improved IPv6 support.</span></span> <span data-ttu-id="fcb44-1181">Další informace najdete v oboru názvů <xref:System.Net.NetworkInformation>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1181">For more information, see the <xref:System.Net.NetworkInformation> namespace.</span></span>

- <span data-ttu-id="fcb44-1182">Podpora soketu s duálním režimem.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1182">Dual-mode socket support.</span></span> <span data-ttu-id="fcb44-1183">Další informace naleznete v <xref:System.Net.Sockets.Socket> tématu třídy a. <xref:System.Net.Sockets.TcpListener></span><span class="sxs-lookup"><span data-stu-id="fcb44-1183">For more information, see the <xref:System.Net.Sockets.Socket> and <xref:System.Net.Sockets.TcpListener> classes.</span></span>

<a name="client" />

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="fcb44-1184">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="fcb44-1184">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="fcb44-1185">V .NET Framework 4,5 Windows Presentation Foundation (WPF) obsahuje změny a vylepšení v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="fcb44-1185">In the .NET Framework 4.5, Windows Presentation Foundation (WPF) contains changes and improvements in the following areas:</span></span>

- <span data-ttu-id="fcb44-1186">Nový ovládací prvek <xref:System.Windows.Controls.Ribbon.Ribbon>, který umožňuje implementovat uživatelské rozhraní pásu karet, které je hostitelem panelu nástrojů pro rychlý přístup, nabídky aplikace a karet.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1186">The new <xref:System.Windows.Controls.Ribbon.Ribbon> control, which enables you to implement a ribbon user interface that hosts a Quick Access Toolbar, Application Menu, and tabs.</span></span>

- <span data-ttu-id="fcb44-1187">Nové rozhraní <xref:System.ComponentModel.INotifyDataErrorInfo>, které podporuje synchronní a asynchronní ověřování dat.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1187">The new <xref:System.ComponentModel.INotifyDataErrorInfo> interface, which supports synchronous and asynchronous data validation.</span></span>

- <span data-ttu-id="fcb44-1188">Nové funkce pro třídy <xref:System.Windows.Controls.VirtualizingPanel> a <xref:System.Windows.Threading.Dispatcher>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1188">New features for the <xref:System.Windows.Controls.VirtualizingPanel> and <xref:System.Windows.Threading.Dispatcher> classes.</span></span>

- <span data-ttu-id="fcb44-1189">Vylepšený výkon při zobrazování rozsáhlých sad seskupených dat a přístup k kolekcím na vláknech, která nejsou v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1189">Improved performance when displaying large sets of grouped data, and by accessing collections on non-UI threads.</span></span>

- <span data-ttu-id="fcb44-1190">Vázání dat na statické vlastnosti, datové vazby na vlastní typy, které implementují rozhraní <xref:System.Reflection.ICustomTypeProvider> a načítání informací o vazbě dat z výrazu vazby.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1190">Data binding to static properties, data binding to custom types that implement the <xref:System.Reflection.ICustomTypeProvider> interface, and retrieval of data binding information from a binding expression.</span></span>

- <span data-ttu-id="fcb44-1191">Změna umístění dat při změně hodnot (živé tvarování).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1191">Repositioning of data as the values change (live shaping).</span></span>

- <span data-ttu-id="fcb44-1192">Možnost kontrolovat, zda je kontext dat pro kontejner položek odpojen.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1192">Ability to check whether the data context for an item container is disconnected.</span></span>

- <span data-ttu-id="fcb44-1193">Možnost nastavit dobu, která má uplynout mezi změnami vlastností a aktualizacemi zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1193">Ability to set the amount of time that should elapse between property changes and data source updates.</span></span>

- <span data-ttu-id="fcb44-1194">Vylepšená podpora pro implementaci slabých vzorů událostí.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1194">Improved support for implementing weak event patterns.</span></span> <span data-ttu-id="fcb44-1195">Události nyní také mohou přijímat rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1195">Also, events can now accept markup extensions.</span></span>

<a name="windows_communication_foundation" />

### <a name="windows-communication-foundation-wcf"></a><span data-ttu-id="fcb44-1196">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="fcb44-1196">Windows Communication Foundation (WCF)</span></span>

<span data-ttu-id="fcb44-1197">V .NET Framework 4,5 byly přidány následující funkce, které zjednodušují psaní a údržbu aplikací Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="fcb44-1197">In the .NET Framework 4.5, the following features have been added to make it simpler to write and maintain Windows Communication Foundation (WCF) applications:</span></span>

- <span data-ttu-id="fcb44-1198">Zjednodušení generovaných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1198">Simplification of generated configuration files.</span></span>

- <span data-ttu-id="fcb44-1199">Podpora vývoje pro první kontrakt.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1199">Support for contract-first development.</span></span>

- <span data-ttu-id="fcb44-1200">Možnost snazší konfigurace režimu kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1200">Ability to configure ASP.NET compatibility mode more easily.</span></span>

- <span data-ttu-id="fcb44-1201">Změny ve výchozích hodnotách vlastností přenosu snižují pravděpodobnost, že je budete muset nastavit.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1201">Changes in default transport property values to reduce the likelihood that you will have to set them.</span></span>

- <span data-ttu-id="fcb44-1202">Aktualizuje třídu <xref:System.Xml.XmlDictionaryReaderQuotas>, aby se snížila pravděpodobnost, že bude nutné ručně nakonfigurovat kvóty pro čtečky slovníku XML.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1202">Updates to the <xref:System.Xml.XmlDictionaryReaderQuotas> class to reduce the likelihood that you will have to manually configure quotas for XML dictionary readers.</span></span>

- <span data-ttu-id="fcb44-1203">Ověření konfiguračních souborů WCF nástrojem Visual Studio v rámci procesu sestavení, aby bylo možné zjistit chyby konfigurace před spuštěním aplikace.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1203">Validation of WCF configuration files by Visual Studio as part of the build process, so you can detect configuration errors before you run your application.</span></span>

- <span data-ttu-id="fcb44-1204">Nová podpora asynchronního streamování.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1204">New asynchronous streaming support.</span></span>

- <span data-ttu-id="fcb44-1205">Nové mapování protokolu HTTPS, které usnadňuje vystavení koncového bodu přes HTTPS pomocí Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1205">New HTTPS protocol mapping to make it easier to expose an endpoint over HTTPS with Internet Information Services (IIS).</span></span>

- <span data-ttu-id="fcb44-1206">Možnost generovat metadata v jednom dokumentu WSDL připojením `?singleWSDL` k adrese URL služby.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1206">Ability to generate metadata in a single WSDL document by appending `?singleWSDL` to the service URL.</span></span>

- <span data-ttu-id="fcb44-1207">Podpora WebSockets podporuje true obousměrnou komunikaci přes porty 80 a 443 s charakteristikami výkonu podobným přenosu protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1207">Websockets support to enable true bidirectional communication over ports 80 and 443 with performance characteristics similar to the TCP transport.</span></span>

- <span data-ttu-id="fcb44-1208">Podpora konfigurace služeb v kódu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1208">Support for configuring services in code.</span></span>

- <span data-ttu-id="fcb44-1209">Popisy editoru XML.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1209">XML Editor tooltips.</span></span>

- <span data-ttu-id="fcb44-1210">Podpora ukládání do mezipaměti <xref:System.ServiceModel.ChannelFactory>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1210"><xref:System.ServiceModel.ChannelFactory> caching support.</span></span>

- <span data-ttu-id="fcb44-1211">Podpora komprese binárního kodéru</span><span class="sxs-lookup"><span data-stu-id="fcb44-1211">Binary encoder compression support.</span></span>

- <span data-ttu-id="fcb44-1212">Podpora pro přenos UDP, který vývojářům umožňuje psát služby, které používají zprávy "oheň a zapomenout".</span><span class="sxs-lookup"><span data-stu-id="fcb44-1212">Support for a UDP transport that enables developers to write services that use "fire and forget" messaging.</span></span> <span data-ttu-id="fcb44-1213">Klient pošle zprávu službě a neočekává odpověď ze služby.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1213">A client sends a message to a service and expects no response from the service.</span></span>

- <span data-ttu-id="fcb44-1214">Možnost podporovat více režimů ověřování na jednom koncovém bodu WCF při použití přenosu protokolu HTTP a zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1214">Ability to support multiple authentication modes on a single WCF endpoint when using the HTTP transport and transport security.</span></span>

- <span data-ttu-id="fcb44-1215">Podpora služeb WCF, které používají mezinárodní názvy domén (IDN).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1215">Support for WCF services that use internationalized domain names (IDNs).</span></span>

<span data-ttu-id="fcb44-1216">Další informace najdete v tématu [co je nového v Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=228173).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1216">For more information, see [What's New in Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=228173).</span></span>

<a name="windows_workflow_foundation" />

### <a name="windows-workflow-foundation-wf"></a><span data-ttu-id="fcb44-1217">Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="fcb44-1217">Windows Workflow Foundation (WF)</span></span>

<span data-ttu-id="fcb44-1218">V .NET Framework 4,5 byly do programovací model Windows Workflow Foundation (WF) přidány některé nové funkce, včetně těchto:</span><span class="sxs-lookup"><span data-stu-id="fcb44-1218">In the .NET Framework 4.5, several new features were added to Windows Workflow Foundation (WF), including:</span></span>

- <span data-ttu-id="fcb44-1219">Pracovní postupy stavového stroje, které byly poprvé představeny jako součást .NET Framework 4.0.1 ([.NET Framework 4 Platform Update 1](https://go.microsoft.com/fwlink/?LinkID=215092)).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1219">State machine workflows, which were first introduced as part of .NET Framework 4.0.1 ([.NET Framework 4 Platform Update 1](https://go.microsoft.com/fwlink/?LinkID=215092)).</span></span> <span data-ttu-id="fcb44-1220">Tato aktualizace obsahuje několik nových tříd a aktivit, které vývojářům umožnili vytvářet pracovní postupy stavového počítače.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1220">This update included several new classes and activities that enabled developers to create state machine workflows.</span></span> <span data-ttu-id="fcb44-1221">Tyto třídy a aktivity byly aktualizovány, aby .NET Framework 4,5 zahrnovaly:</span><span class="sxs-lookup"><span data-stu-id="fcb44-1221">These classes and activities were updated for the .NET Framework 4.5 to include:</span></span>

  - <span data-ttu-id="fcb44-1222">Možnost nastavovat zarážky na stavech.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1222">The ability to set breakpoints on states.</span></span>

  - <span data-ttu-id="fcb44-1223">Možnost Kopírovat a vkládat přechody v Návrháři postupu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1223">The ability to copy and paste transitions in the workflow designer.</span></span>

  - <span data-ttu-id="fcb44-1224">Podpora návrháře pro vytvoření přechodu na sdílené triggery</span><span class="sxs-lookup"><span data-stu-id="fcb44-1224">Designer support for shared trigger transition creation.</span></span>

  - <span data-ttu-id="fcb44-1225">Aktivity pro vytváření pracovních postupů stavového stroje, včetně: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State> a <xref:System.Activities.Statements.Transition>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1225">Activities for creating state machine workflows, including: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, and <xref:System.Activities.Statements.Transition>.</span></span>

- <span data-ttu-id="fcb44-1226">Rozšířené funkce Návrhář postupu provádění, například následující:</span><span class="sxs-lookup"><span data-stu-id="fcb44-1226">Enhanced Workflow Designer features such as the following:</span></span>

  - <span data-ttu-id="fcb44-1227">Rozšířené možnosti hledání pracovních postupů v aplikaci Visual Studio, včetně **rychlého hledání** a **hledání v souborech**.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1227">Enhanced workflow search capabilities in Visual Studio, including **Quick Find** and **Find in Files**.</span></span>

  - <span data-ttu-id="fcb44-1228">Schopnost automaticky vytvořit aktivitu sekvence, když se do aktivity kontejneru přidá druhá podřízená aktivita, a zahrnout obě aktivity do aktivity sekvence.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1228">Ability to automatically create a Sequence activity when a second child activity is added to a container activity, and to include both activities in the Sequence activity.</span></span>

  - <span data-ttu-id="fcb44-1229">Podpora posouvání, která umožňuje změnit viditelnou část pracovního postupu bez použití posuvníků.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1229">Panning support, which enables the visible portion of a workflow to be changed without using the scroll bars.</span></span>

  - <span data-ttu-id="fcb44-1230">Nové zobrazení **Osnova dokumentu** , které zobrazuje součásti pracovního postupu v zobrazení osnovy ve stylu stromu a umožňuje v zobrazení **Osnova dokumentu** vybrat komponentu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1230">A new **Document Outline** view that shows the components of a workflow in a tree-style outline view and lets you select a component in the **Document Outline** view.</span></span>

  - <span data-ttu-id="fcb44-1231">Možnost přidávat poznámky k aktivitám.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1231">Ability to add annotations to activities.</span></span>

  - <span data-ttu-id="fcb44-1232">Možnost definovat a spotřebovat delegáty aktivit pomocí návrháře pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1232">Ability to define and consume activity delegates by using the workflow designer.</span></span>

  - <span data-ttu-id="fcb44-1233">Automatické připojení a automatické vložení pro aktivity a přechody v pracovních postupech stavového stroje a vývojového diagramu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1233">Auto-connect and auto-insert for activities and transitions in state machine and flowchart workflows.</span></span>

- <span data-ttu-id="fcb44-1234">Úložiště informací o stavu zobrazení pracovního postupu v jednom prvku v souboru XAML, takže můžete snadno vyhledat a upravit informace o stavu zobrazení.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1234">Storage of the view state information for a workflow in a single element in the XAML file, so you can easily locate and edit the view state information.</span></span>

- <span data-ttu-id="fcb44-1235">Aktivita kontejneru oboru NoPersistScope, která zabraňuje zachování podřízených aktivit.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1235">A NoPersistScope container activity to prevent child activities from persisting.</span></span>

- <span data-ttu-id="fcb44-1236">Podpora pro C# výrazy:</span><span class="sxs-lookup"><span data-stu-id="fcb44-1236">Support for C# expressions:</span></span>

  - <span data-ttu-id="fcb44-1237">Projekty pracovního postupu, které používají Visual Basic, budou používat výrazy C# Visual Basic a projekty pracovního C# postupu budou používat výrazy.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1237">Workflow projects that use Visual Basic will use Visual Basic expressions, and C# workflow projects will use C# expressions.</span></span>

  - <span data-ttu-id="fcb44-1238">C#projekty pracovního postupu, které byly vytvořeny v aplikaci Visual Studio 2010 a které mají Visual Basic výrazy C# jsou kompatibilní s projekty C# pracovního postupu, které používají výrazy.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1238">C# workflow projects that were created in Visual Studio 2010 and that have Visual Basic expressions are compatible with C# workflow projects that use C# expressions.</span></span>

- <span data-ttu-id="fcb44-1239">Vylepšení správy verzí:</span><span class="sxs-lookup"><span data-stu-id="fcb44-1239">Versioning enhancements:</span></span>

  - <span data-ttu-id="fcb44-1240">Nová třída <xref:System.Activities.WorkflowIdentity>, která poskytuje mapování mezi trvalou instancí pracovního postupu a její definicí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1240">The new  <xref:System.Activities.WorkflowIdentity> class, which provides a mapping between a persisted workflow instance and its workflow definition.</span></span>

  - <span data-ttu-id="fcb44-1241">Souběžné spouštění více verzí pracovních postupů ve stejném hostiteli, včetně <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1241">Side-by-side execution of multiple workflow versions in the same host, including <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>

  - <span data-ttu-id="fcb44-1242">V případě dynamické aktualizace je možné změnit definici trvalé instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1242">In Dynamic Update, the ability to modify the definition of a persisted workflow instance.</span></span>

- <span data-ttu-id="fcb44-1243">Vývoj služby pracovního postupu prvního kontraktu, který poskytuje podporu pro automatické generování aktivit, které se shodují s existující smlouvou služby.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1243">Contract-first workflow service development, which provides support for automatically generating activities to match an existing service contract.</span></span>

<span data-ttu-id="fcb44-1244">Další informace najdete v tématu [co je nového v programovací model Windows Workflow Foundation](https://go.microsoft.com/fwlink/?LinkId=228176).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1244">For more information, see [What's New in Windows Workflow Foundation](https://go.microsoft.com/fwlink/?LinkId=228176).</span></span>

<a name="tailored" />

### [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]

<span data-ttu-id="fcb44-1245">aplikace [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] jsou navržené pro konkrétní faktory typu a využívají sílu operačního systému Windows.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1245">[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps are designed for specific form factors and leverage the power of the Windows operating system.</span></span> <span data-ttu-id="fcb44-1246">Podmnožina .NET Framework 4,5 nebo 4.5.1 je k dispozici pro vytváření aplikací [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] pro systém Windows C# pomocí nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1246">A subset of the .NET Framework 4.5 or 4.5.1 is available for building [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps for Windows by using C# or Visual Basic.</span></span> <span data-ttu-id="fcb44-1247">Tato podmnožina se nazývá [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] a je popsána v [přehledu](https://go.microsoft.com/fwlink/?LinkId=228491) na stránce Windows Dev Center.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1247">This subset is called [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] and is discussed in an [overview](https://go.microsoft.com/fwlink/?LinkId=228491) in the Windows Dev Center.</span></span>

### <a name="portable-class-libraries-a-nameportable-"></a><span data-ttu-id="fcb44-1248">Knihovny přenosných tříd <a name="portable" /></span><span class="sxs-lookup"><span data-stu-id="fcb44-1248">Portable Class Libraries <a name="portable" /></span></span>

<span data-ttu-id="fcb44-1249">Přenosná knihovna tříd projektu v aplikaci Visual Studio 2012 (a novějších verzích) umožňuje psát a sestavovat spravovaná sestavení, která fungují na více .NET Framework platformách.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1249">The Portable Class Library project in Visual Studio 2012 (and later versions) enables you to write and build managed assemblies that work on multiple .NET Framework platforms.</span></span> <span data-ttu-id="fcb44-1250">Pomocí přenositelného projektu knihovny tříd zvolíte platformy (například Windows Phone a [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]) k cíli.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1250">Using a Portable Class Library project, you choose the platforms (such as Windows Phone and [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]) to target.</span></span> <span data-ttu-id="fcb44-1251">Dostupné typy a členy v projektu jsou automaticky omezeny na společné typy a členy napříč těmito platformami.</span><span class="sxs-lookup"><span data-stu-id="fcb44-1251">The available types and members in your project are automatically restricted to the common types and members across these platforms.</span></span> <span data-ttu-id="fcb44-1252">Další informace naleznete v tématu [Přenosná knihovna tříd](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-1252">For more information, see [Portable Class Library](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fcb44-1253">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fcb44-1253">See also</span></span>

- [<span data-ttu-id="fcb44-1254">Rozhraní .NET Framework a nesvázaná vydání</span><span class="sxs-lookup"><span data-stu-id="fcb44-1254">The .NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
- [<span data-ttu-id="fcb44-1255">Co je nového v přístupnosti v .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fcb44-1255">What's new in accessibility in the .NET Framework</span></span>](whats-new-in-accessibility.md)
- [<span data-ttu-id="fcb44-1256">Co je nového v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="fcb44-1256">What's New in Visual Studio 2017</span></span>](/visualstudio/ide/whats-new-in-visual-studio)
- [<span data-ttu-id="fcb44-1257">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="fcb44-1257">ASP.NET</span></span>](/aspnet)
- [<span data-ttu-id="fcb44-1258">Co je nového v jazyce VisualC++</span><span class="sxs-lookup"><span data-stu-id="fcb44-1258">What’s New in Visual C++</span></span>](/cpp/what-s-new-for-visual-cpp-in-visual-studio)
