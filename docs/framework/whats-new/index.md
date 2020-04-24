---
title: Novinky v rozhraní .NET Framework
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.assetid: 1d971dd7-10fc-4692-8dac-30ca308fc0fa
ms.openlocfilehash: f56ba7d68be107e697d3f732767f0a5f11c1a622
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644218"
---
# <a name="whats-new-in-net-framework"></a><span data-ttu-id="75ebc-102">Co je nového v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="75ebc-102">What's new in .NET Framework</span></span>

<span data-ttu-id="75ebc-103">Tento článek shrnuje klíčové nové funkce a vylepšení v následujících verzích rozhraní .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="75ebc-103">This article summarizes key new features and improvements in the following versions of the .NET Framework:</span></span>

- [<span data-ttu-id="75ebc-104">Rozhraní .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="75ebc-104">.NET Framework 4.8</span></span>](#v48)
- [<span data-ttu-id="75ebc-105">Rozhraní .NET 4.7.2</span><span class="sxs-lookup"><span data-stu-id="75ebc-105">.NET Framework 4.7.2</span></span>](#v472)
- [<span data-ttu-id="75ebc-106">Rozhraní .NET 4.7.1</span><span class="sxs-lookup"><span data-stu-id="75ebc-106">.NET Framework 4.7.1</span></span>](#v471)
- [<span data-ttu-id="75ebc-107">Rozhraní .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="75ebc-107">.NET Framework 4.7</span></span>](#v47)
- [<span data-ttu-id="75ebc-108">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="75ebc-108">.NET Framework 4.6.2</span></span>](#v462)
- [<span data-ttu-id="75ebc-109">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="75ebc-109">.NET Framework 4.6.1</span></span>](#v461)
- [<span data-ttu-id="75ebc-110">.NET 2015 a .NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="75ebc-110">.NET 2015 and .NET Framework 4.6</span></span>](#v46)
- [<span data-ttu-id="75ebc-111">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="75ebc-111">.NET Framework 4.5.2</span></span>](#v452)
- [<span data-ttu-id="75ebc-112">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="75ebc-112">.NET Framework 4.5.1</span></span>](#v451)
- [<span data-ttu-id="75ebc-113">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="75ebc-113">.NET Framework 4.5</span></span>](#v45)

<span data-ttu-id="75ebc-114">Tento článek neposkytuje komplexní informace o každé nové funkci a může se změnit.</span><span class="sxs-lookup"><span data-stu-id="75ebc-114">This article does not provide comprehensive information about each new feature and is subject to change.</span></span> <span data-ttu-id="75ebc-115">Obecné informace o rozhraní .NET Framework naleznete v tématu [Začínáme](../get-started/index.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-115">For general information about the .NET Framework, see [Getting Started](../get-started/index.md).</span></span> <span data-ttu-id="75ebc-116">Podporované platformy naleznete v [tématu Systémové požadavky](../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-116">For supported platforms, see [System Requirements](../get-started/system-requirements.md).</span></span> <span data-ttu-id="75ebc-117">Odkazy ke stažení a pokyny k instalaci naleznete v [příručce k instalaci](../install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-117">For download links and installation instructions, see [Installation Guide](../install/guide-for-developers.md).</span></span>

> [!NOTE]
> <span data-ttu-id="75ebc-118">Tým rozhraní .NET Framework také vydává funkce mimo pásmo s NuGet rozšířit podporu platformy a zavést nové funkce, jako jsou neměnné kolekce a simd povoleno vektorové typy.</span><span class="sxs-lookup"><span data-stu-id="75ebc-118">The .NET Framework team also releases features out of band with NuGet to expand platform support and to introduce new functionality, such as immutable collections and SIMD-enabled vector types.</span></span> <span data-ttu-id="75ebc-119">Další informace naleznete [v tématu Další knihovny tříd a rozhraní API](../additional-apis/index.md) a rozhraní [.NET Framework a Out-of-Band releases](../get-started/the-net-framework-and-out-of-band-releases.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-119">For more information, see [Additional Class Libraries and APIs](../additional-apis/index.md) and [The .NET Framework and Out-of-Band Releases](../get-started/the-net-framework-and-out-of-band-releases.md).</span></span>
> <span data-ttu-id="75ebc-120">Podívejte se na [úplný seznam balíčků NuGet](https://www.nuget.org/profiles/dotnetframework) pro rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="75ebc-120">See a [complete list of NuGet packages](https://www.nuget.org/profiles/dotnetframework) for the .NET Framework.</span></span>

<a name="v48" />

## <a name="introducing-net-framework-48"></a><span data-ttu-id="75ebc-121">Představujeme rozhraní .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="75ebc-121">Introducing .NET Framework 4.8</span></span>

<span data-ttu-id="75ebc-122">Rozhraní .NET Framework 4.8 vychází z předchozích verzí rozhraní .NET Framework 4.x přidáním mnoha nových oprav a několika nových funkcí a zároveň zůstává velmi stabilním produktem.</span><span class="sxs-lookup"><span data-stu-id="75ebc-122">.NET Framework 4.8 builds on previous versions of the .NET Framework 4.x by adding many new fixes and several new features while remaining a very stable product.</span></span>

### <a name="downloading-and-installing-net-framework-48"></a><span data-ttu-id="75ebc-123">Stahování a instalace rozhraní .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="75ebc-123">Downloading and installing .NET Framework 4.8</span></span>

<span data-ttu-id="75ebc-124">Rozhraní .NET Framework 4.8 si můžete stáhnout z následujících umístění:</span><span class="sxs-lookup"><span data-stu-id="75ebc-124">You can download .NET Framework 4.8  from the following locations:</span></span>

- [<span data-ttu-id="75ebc-125">Instalační služba rozhraní .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="75ebc-125">.NET Framework 4.8 Web Installer</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)

- [<span data-ttu-id="75ebc-126">Net Framework 4.8 Offline instalační program</span><span class="sxs-lookup"><span data-stu-id="75ebc-126">NET Framework 4.8 Offline Installer</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)

<span data-ttu-id="75ebc-127">Rozhraní .NET Framework 4.8 lze nainstalovat do systému Windows 10, Windows 8.1, Windows 7 SP1 a odpovídajících serverových platforem počínaje aktualizací Windows Server 2008 R2 SP1.</span><span class="sxs-lookup"><span data-stu-id="75ebc-127">.NET Framework 4.8 can be installed on Windows 10, Windows 8.1, Windows 7 SP1, and the corresponding server platforms starting with Windows Server 2008 R2 SP1.</span></span> <span data-ttu-id="75ebc-128">Rozhraní .NET Framework 4.8 můžete nainstalovat pomocí webového instalačního programu nebo offline instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-128">You can install .NET Framework 4.8 by using either the web installer or the offline installer.</span></span> <span data-ttu-id="75ebc-129">Doporučeným způsobem pro většinu uživatelů je použití webového instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-129">The recommended way for most users is to use the web installer.</span></span>

<span data-ttu-id="75ebc-130">Rozhraní .NET Framework 4.8 v sadě Visual Studio 2012 nebo novější můžete cílit instalací [sady .NET Framework 4.8 Developer Pack](https://go.microsoft.com/fwlink/?LinkId=2085167).</span><span class="sxs-lookup"><span data-stu-id="75ebc-130">You can target .NET Framework 4.8 in Visual Studio 2012 or later by installing the [.NET Framework 4.8 Developer Pack](https://go.microsoft.com/fwlink/?LinkId=2085167).</span></span>

### <a name="whats-new-in-net-framework-48"></a><span data-ttu-id="75ebc-131">Co je nového v rozhraní .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="75ebc-131">What's new in .NET Framework 4.8</span></span>

<span data-ttu-id="75ebc-132">Rozhraní .NET Framework 4.8 zavádí nové funkce v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="75ebc-132">.NET Framework 4.8 introduces new features in the following areas:</span></span>

- [<span data-ttu-id="75ebc-133">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="75ebc-133">Base classes</span></span>](#core48)
- [<span data-ttu-id="75ebc-134">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="75ebc-134">Windows Communication Foundation (WCF)</span></span>](#wcf48)
- [<span data-ttu-id="75ebc-135">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="75ebc-135">Windows Presentation Foundation (WPF)</span></span>](#wpf48)
- [<span data-ttu-id="75ebc-136">Běžný jazyk runtime</span><span class="sxs-lookup"><span data-stu-id="75ebc-136">Common language runtime</span></span>](#clr48)

<span data-ttu-id="75ebc-137">Vylepšená přístupnost, která umožňuje aplikaci poskytovat odpovídající prostředí pro uživatele asistenční technologie, je i nadále hlavním zaměřením rozhraní .NET Framework 4.8.</span><span class="sxs-lookup"><span data-stu-id="75ebc-137">Improved accessibility, which allows an application to provide an appropriate experience for users of Assistive Technology, continues to be a major focus of .NET Framework 4.8.</span></span> <span data-ttu-id="75ebc-138">Informace o vylepšení usnadnění v rozhraní .NET Framework 4.8 naleznete [v tématu Co je nového v usnadnění přístupnosti v rozhraní .NET Framework](whats-new-in-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-138">For information on accessibility improvements in .NET Framework 4.8, see [What's new in accessibility in the .NET Framework](whats-new-in-accessibility.md).</span></span>

<a name="core48" />

#### <a name="base-classes"></a><span data-ttu-id="75ebc-139">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="75ebc-139">Base classes</span></span>

<span data-ttu-id="75ebc-140">**Snížený dopad FIPS na kryptografii**.</span><span class="sxs-lookup"><span data-stu-id="75ebc-140">**Reduced FIPS impact on Cryptography**.</span></span> <span data-ttu-id="75ebc-141">V předchozích verzích rozhraní .NET Framework byly <xref:System.Security.Cryptography.SHA256Managed> spravovány <xref:System.Security.Cryptography.CryptographicException> třídy zprostředkovatele kryptografických služeb, například throw a když jsou systémové kryptografické knihovny konfigurovány v režimu FIPS.</span><span class="sxs-lookup"><span data-stu-id="75ebc-141">In previous versions of the .NET Framework, managed cryptographic provider classes such as <xref:System.Security.Cryptography.SHA256Managed> throw a <xref:System.Security.Cryptography.CryptographicException> when the system cryptographic libraries are configured in “FIPS mode”.</span></span> <span data-ttu-id="75ebc-142">Tyto výjimky jsou vyvolány, protože spravované verze tříd kryptografického zprostředkovatele, na rozdíl od systémových kryptografických knihoven, neprošly certifikací FIPS (Federal Information Processing Standards) 140-2.</span><span class="sxs-lookup"><span data-stu-id="75ebc-142">These exceptions are thrown because the managed versions of the cryptographic provider classes, unlike the system cryptographic libraries, have not undergone FIPS (Federal Information Processing Standards) 140-2 certification.</span></span> <span data-ttu-id="75ebc-143">Vzhledem k tomu, že několik vývojářů má své vývojové počítače v režimu FIPS, výjimky jsou běžně vyvolány v produkčních systémech.</span><span class="sxs-lookup"><span data-stu-id="75ebc-143">Because few developers have their development machines in FIPS mode, the exceptions are commonly thrown in production systems.</span></span>

<span data-ttu-id="75ebc-144">Ve výchozím nastavení v aplikacích, které cílí na rozhraní .NET <xref:System.Security.Cryptography.CryptographicException> Framework 4.8, následující spravované třídy kryptografie již v tomto případě nepřihazují:</span><span class="sxs-lookup"><span data-stu-id="75ebc-144">By default in applications that target .NET Framework 4.8, the following managed cryptography classes no longer throw a <xref:System.Security.Cryptography.CryptographicException> in this case:</span></span>

- <xref:System.Security.Cryptography.MD5Cng>
- <xref:System.Security.Cryptography.MD5CryptoServiceProvider>
- <xref:System.Security.Cryptography.RC2CryptoServiceProvider>
- <xref:System.Security.Cryptography.RijndaelManaged>
- <xref:System.Security.Cryptography.RIPEMD160Managed>
- <xref:System.Security.Cryptography.SHA256Managed>

<span data-ttu-id="75ebc-145">Místo toho tyto třídy přesměrovat kryptografické operace do knihovny kryptografické systému.</span><span class="sxs-lookup"><span data-stu-id="75ebc-145">Instead, these classes redirect cryptographic operations to a system cryptography library.</span></span> <span data-ttu-id="75ebc-146">Tato změna účinně odstraňuje potenciálně matoucí rozdíl mezi vývojářskými prostředími a produkčními prostředími a umožňuje nativní mařivé součásti a spravované součásti pracovat v rámci stejné kryptografické zásady.</span><span class="sxs-lookup"><span data-stu-id="75ebc-146">This change effectively removes a potentially confusing difference between developer environments and production environments and makes native components and managed components operate under the same cryptographic policy.</span></span> <span data-ttu-id="75ebc-147">Aplikace, které závisí na těchto výjimkách můžete obnovit `Switch.System.Security.Cryptography.UseLegacyFipsThrow` předchozí `true`chování nastavením AppContext přepínač na .</span><span class="sxs-lookup"><span data-stu-id="75ebc-147">Applications that depend on these exceptions can restore the previous behavior by setting the AppContext switch `Switch.System.Security.Cryptography.UseLegacyFipsThrow` to `true`.</span></span> <span data-ttu-id="75ebc-148">Další informace naleznete v tématu [Spravované kryptografické třídy nevyvolání cryptographyException v režimu FIPS](../migration-guide/retargeting/4.7.2-4.8.md#managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode).</span><span class="sxs-lookup"><span data-stu-id="75ebc-148">For more information, see [Managed cryptography classes do not throw a CryptographyException in FIPS mode](../migration-guide/retargeting/4.7.2-4.8.md#managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode).</span></span>

<span data-ttu-id="75ebc-149">**Použití aktualizované verze ZLib**</span><span class="sxs-lookup"><span data-stu-id="75ebc-149">**Use of updated version of ZLib**</span></span>

<span data-ttu-id="75ebc-150">Počínaje rozhraním .NET Framework 4.5 používá sestavení clrcompression.dll [ZLib](https://www.zlib.net), nativní externí knihovnu pro kompresi dat, aby bylo možné poskytnout implementaci pro algoritmus deflate.</span><span class="sxs-lookup"><span data-stu-id="75ebc-150">Starting with .NET Framework 4.5, the clrcompression.dll assembly uses [ZLib](https://www.zlib.net), a native external library for data compression, in order to provide an implementation for the deflate algorithm.</span></span> <span data-ttu-id="75ebc-151">Rozhraní .NET Framework 4.8, clrcompression.dll je aktualizován o použití ZLib verze 1.2.11, který obsahuje několik klíčových vylepšení a oprav.</span><span class="sxs-lookup"><span data-stu-id="75ebc-151">The .NET Framework 4.8, clrcompression.dll is updated to use ZLib Version 1.2.11, which includes several key improvements and fixes.</span></span>

<a name="wcf48" />

#### <a name="windows-communication-foundation-wcf"></a><span data-ttu-id="75ebc-152">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="75ebc-152">Windows Communication Foundation (WCF)</span></span>

<span data-ttu-id="75ebc-153">**Zavedení servicehealthbehavior**</span><span class="sxs-lookup"><span data-stu-id="75ebc-153">**Introduction of ServiceHealthBehavior**</span></span>

<span data-ttu-id="75ebc-154">Koncové body stavu jsou široce používány orchestračními nástroji ke správě služeb na základě jejich stavu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-154">Health endpoints are widely used by orchestration tools to manage services based on their health status.</span></span> <span data-ttu-id="75ebc-155">Kontroly stavu lze také použít pomocí nástrojů pro sledování ke sledování a poskytování oznámení o dostupnosti a výkonu služby.</span><span class="sxs-lookup"><span data-stu-id="75ebc-155">Health checks can also be used by monitoring tools to track and provide notifications about the availability and performance of a service.</span></span>

<span data-ttu-id="75ebc-156">**ServiceHealthBehavior** je chování služby WCF, které rozšiřuje <xref:System.ServiceModel.Description.IServiceBehavior>.</span><span class="sxs-lookup"><span data-stu-id="75ebc-156">**ServiceHealthBehavior** is a WCF service behavior that extends <xref:System.ServiceModel.Description.IServiceBehavior>.</span></span>  <span data-ttu-id="75ebc-157">Při přidání <xref:System.ServiceModel.Description.ServiceDescription.Behaviors?displayProperty=nameWithType> do kolekce chování služby provádí následující akce:</span><span class="sxs-lookup"><span data-stu-id="75ebc-157">When added to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors?displayProperty=nameWithType> collection, a service behavior does the following:</span></span>

- <span data-ttu-id="75ebc-158">Vrátí stav služby s kódy odpovědí HTTP.</span><span class="sxs-lookup"><span data-stu-id="75ebc-158">Returns service health status with HTTP response codes.</span></span> <span data-ttu-id="75ebc-159">V řetězci dotazu můžete zadat stavový kód HTTP pro požadavek sondy stavu HTTP/GET.</span><span class="sxs-lookup"><span data-stu-id="75ebc-159">You can specify in a query string the HTTP status code for a HTTP/GET health probe request.</span></span>

- <span data-ttu-id="75ebc-160">Publikuje informace o stavu služby.</span><span class="sxs-lookup"><span data-stu-id="75ebc-160">Publishes information about service health.</span></span> <span data-ttu-id="75ebc-161">Podrobnosti specifické pro službu, včetně stavu služby, počty omezení a kapacity `?health` lze zobrazit pomocí požadavku HTTP/GET s řetězcem dotazu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-161">Service-specific details, including service state, throttle counts, and capacity can be displayed by using an HTTP/GET request with the `?health` query string.</span></span> <span data-ttu-id="75ebc-162">Snadný přístup k těmto informacím je důležité při řešení potíží s nechová WCF služby.</span><span class="sxs-lookup"><span data-stu-id="75ebc-162">Ease of access to such information is important when troubleshooting a misbehaving WCF service.</span></span>

<span data-ttu-id="75ebc-163">Existují dva způsoby, jak vystavit koncový bod stavu a publikovat informace o stavu služby WCF:</span><span class="sxs-lookup"><span data-stu-id="75ebc-163">There are two ways to expose the health endpoint and publish WCF service health information:</span></span>

- <span data-ttu-id="75ebc-164">Prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-164">Through code.</span></span> <span data-ttu-id="75ebc-165">Příklad:</span><span class="sxs-lookup"><span data-stu-id="75ebc-165">For example:</span></span>

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

- <span data-ttu-id="75ebc-166">Pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="75ebc-166">By using a configuration file.</span></span> <span data-ttu-id="75ebc-167">Příklad:</span><span class="sxs-lookup"><span data-stu-id="75ebc-167">For example:</span></span>

  ```xml
  <behaviors>
    <serviceBehaviors>
      <behavior name="DefaultBehavior">
        <serviceHealth httpsGetEnabled="true"/>
      </behavior>
    </serviceBehaviors>
  </behaviors>
  ```

<span data-ttu-id="75ebc-168">Stav služby lze dotazovat pomocí parametrů dotazu, `OnServiceFailure` `OnDispatcherFailure`jako `OnListenerFailure` `OnThrottlePercentExceeded`je například , , , a kód odpovědi HTTP lze zadat pro každý parametr dotazu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-168">A service's health status can be queried by using query parameters such as `OnServiceFailure`, `OnDispatcherFailure`, `OnListenerFailure`, `OnThrottlePercentExceeded`), and an HTTP response code can be specified for each query parameter.</span></span> <span data-ttu-id="75ebc-169">Pokud je pro parametr dotazu vynechán kód odpovědi HTTP, použije se ve výchozím nastavení kód odpovědi 503 HTTP.</span><span class="sxs-lookup"><span data-stu-id="75ebc-169">If the HTTP response code is omitted for a query parameter, a 503 HTTP response code is used by default.</span></span> <span data-ttu-id="75ebc-170">Příklad:</span><span class="sxs-lookup"><span data-stu-id="75ebc-170">For example:</span></span>

- <span data-ttu-id="75ebc-171">Selhání služby:`https://contoso:81/Service1?health&OnServiceFailure=450`</span><span class="sxs-lookup"><span data-stu-id="75ebc-171">OnServiceFailure: `https://contoso:81/Service1?health&OnServiceFailure=450`</span></span>

  <span data-ttu-id="75ebc-172">Stavový kód odpovědi 450 HTTP je vrácen, <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>když [ServiceHost.State](xref:System.ServiceModel.Channels.CommunicationObject.State) je větší než .</span><span class="sxs-lookup"><span data-stu-id="75ebc-172">A 450 HTTP response status code is returned when [ServiceHost.State](xref:System.ServiceModel.Channels.CommunicationObject.State) is greater than <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.</span></span>
<span data-ttu-id="75ebc-173">Parametry dotazu a příklady:</span><span class="sxs-lookup"><span data-stu-id="75ebc-173">Query parameters and examples:</span></span>

- <span data-ttu-id="75ebc-174">OnDispatcherSelhání:`https://contoso:81/Service1?health&OnDispatcherFailure=455`</span><span class="sxs-lookup"><span data-stu-id="75ebc-174">OnDispatcherFailure: `https://contoso:81/Service1?health&OnDispatcherFailure=455`</span></span>

  <span data-ttu-id="75ebc-175">Stavový kód 455 HTTP je vrácen, pokud je stav některého z dispečerů kanálu větší než <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="75ebc-175">A 455 HTTP response status code is returned when the state of any of the channel dispatchers is greater than <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="75ebc-176">Selhání naslouchací hospodařící síly:`https://contoso:81/Service1?health&OnListenerFailure=465`</span><span class="sxs-lookup"><span data-stu-id="75ebc-176">OnListenerFailure: `https://contoso:81/Service1?health&OnListenerFailure=465`</span></span>

  <span data-ttu-id="75ebc-177">Stavový kód odpovědi 465 HTTP je vrácen, pokud je stav <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>některého z posluchačů kanálu větší než .</span><span class="sxs-lookup"><span data-stu-id="75ebc-177">A 465 HTTP response status code is returned when the state of any of the channel listeners is greater than <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="75ebc-178">OnThrottlePercentExceeded:`https://contoso:81/Service1?health&OnThrottlePercentExceeded= 70:350,95:500`</span><span class="sxs-lookup"><span data-stu-id="75ebc-178">OnThrottlePercentExceeded: `https://contoso:81/Service1?health&OnThrottlePercentExceeded= 70:350,95:500`</span></span>

  <span data-ttu-id="75ebc-179">Určuje procento {1 – 100}, které aktivuje odpověď a její kód odpovědi HTTP {200 – 599}.</span><span class="sxs-lookup"><span data-stu-id="75ebc-179">Specifies the percentage {1 – 100} that triggers the response and its HTTP response code {200 – 599}.</span></span> <span data-ttu-id="75ebc-180">V tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="75ebc-180">In this example:</span></span>

  - <span data-ttu-id="75ebc-181">Pokud je procento větší než 95, je vrácen kód odpovědi 500 HTTP.</span><span class="sxs-lookup"><span data-stu-id="75ebc-181">If the percentage is greater than 95, a 500 HTTP response code is returned.</span></span>

  - <span data-ttu-id="75ebc-182">Pokud procento nebo mezi 70 a 95, 350 je vrácena.</span><span class="sxs-lookup"><span data-stu-id="75ebc-182">If the percentage or between 70 and 95, 350 is returned.</span></span>

  - <span data-ttu-id="75ebc-183">V opačném případě je vráceno 200.</span><span class="sxs-lookup"><span data-stu-id="75ebc-183">Otherwise, 200 is returned.</span></span>

<span data-ttu-id="75ebc-184">Stav služby lze zobrazit buď v HTML zadáním `https://contoso:81/Service1?health` řetězce dotazu jako nebo ve `https://contoso:81/Service1?health&Xml`formátu XML zadáním řetězce dotazu, jako je .</span><span class="sxs-lookup"><span data-stu-id="75ebc-184">The service health status can be displayed either in HTML by specifying a query string like `https://contoso:81/Service1?health` or in XML by specifying a query string like `https://contoso:81/Service1?health&Xml`.</span></span> <span data-ttu-id="75ebc-185">Řetězec dotazu, jako `https://contoso:81/Service1?health&NoContent` je tomu však vrátí prázdnou stránku HTML.</span><span class="sxs-lookup"><span data-stu-id="75ebc-185">A query string like `https://contoso:81/Service1?health&NoContent` returns an empty HTML page.</span></span>

<a name="wpf48" />

#### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="75ebc-186">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="75ebc-186">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="75ebc-187">**Vylepšení vysokého dpi**</span><span class="sxs-lookup"><span data-stu-id="75ebc-187">**High DPI enhancements**</span></span>

<span data-ttu-id="75ebc-188">V rozhraní .NET Framework 4.8 wpf přidává podporu pro sledování V2 DPI povědomí a škálování DPI ve smíšeném režimu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-188">In .NET Framework 4.8, WPF adds support for Per-Monitor V2 DPI Awareness and Mixed-Mode DPI scaling.</span></span> <span data-ttu-id="75ebc-189">Další informace o [vývoji vysokého výkonu dpi desktopových aplikací v systému Windows](/windows/win32/hidpi/high-dpi-desktop-application-development-on-windows) naleznete v tématu Vývoj aplikací pro stolní počítače S Vysokým obsahem DPI.</span><span class="sxs-lookup"><span data-stu-id="75ebc-189">See [High DPI Desktop Application Development on Windows](/windows/win32/hidpi/high-dpi-desktop-application-development-on-windows) for additional information about high DPI development.</span></span>

<span data-ttu-id="75ebc-190">Rozhraní .NET Framework 4.8 zlepšuje podporu hostovaných HWND a Windows Forms interoperace v aplikacích WPF s vysokým dpi na platformách, které podporují škálování DPI ve smíšeném režimu (počínaje aktualizací Windows 10 duben 2018).</span><span class="sxs-lookup"><span data-stu-id="75ebc-190">.NET Framework 4.8 improves support for hosted HWNDs and Windows Forms interoperation in High-DPI WPF applications on platforms that support Mixed-Mode DPI scaling (starting with Windows 10 April 2018 Update).</span></span> <span data-ttu-id="75ebc-191">Při hostované HWNDs nebo Windows Forms ovládací prvky jsou vytvořeny jako okna s použitím míchaného režimu DPI pomocí volání [SetThreadDpiHostingBehavior](/windows/desktop/api/winuser/nf-winuser-setthreaddpihostingbehavior) a [SetThreadDpiAwarenessContext](/windows/desktop/api/winuser/nf-winuser-setthreaddpiawarenesscontext), mohou být hostovány v aplikaci V2 WPF per-monitor a jsou velikosti a škálování odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="75ebc-191">When hosted HWNDs or Windows Forms controls are created as Mixed-Mode DPI-scaled windows by calling [SetThreadDpiHostingBehavior](/windows/desktop/api/winuser/nf-winuser-setthreaddpihostingbehavior) and [SetThreadDpiAwarenessContext](/windows/desktop/api/winuser/nf-winuser-setthreaddpiawarenesscontext), they can be hosted in a Per-Monitor V2 WPF application and are sized and scaled appropriately.</span></span> <span data-ttu-id="75ebc-192">Takový hostovaný obsah není vykreslen v nativním DPI; místo toho operační systém škáluje hostovaný obsah na příslušnou velikost.</span><span class="sxs-lookup"><span data-stu-id="75ebc-192">Such hosted content is not rendered at the native DPI; instead, the operating system scales the hosted content to the appropriate size.</span></span> <span data-ttu-id="75ebc-193">Podpora pro režim povědomí DPI v2 monitorování také umožňuje WPF ovládací prvky, které mají být hostovány (tj. nadřazené) v nativním okně v aplikaci s vysokým DPI.</span><span class="sxs-lookup"><span data-stu-id="75ebc-193">The support for Per-Monitor v2 DPI awareness mode also allows WPF controls to be hosted (i.e., parented) in a native window in a high-DPI application.</span></span>

<span data-ttu-id="75ebc-194">Chcete-li povolit podporu škálování s vysokým dpi ve smíšeném režimu, můžete nastavit následující přepínače [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) v konfiguračním souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="75ebc-194">To enable support for Mixed-Mode High DPI scaling, you can set the following [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switches the application configuration file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value = "Switch.System.Windows.DoNotScaleForDpiChanges=false; Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false"/>
</runtime>
```

<a name="clr48" />

#### <a name="common-language-runtime"></a><span data-ttu-id="75ebc-195">Běžný jazyk runtime</span><span class="sxs-lookup"><span data-stu-id="75ebc-195">Common language runtime</span></span>

<span data-ttu-id="75ebc-196">Runtime v rozhraní .NET Framework 4.8 obsahuje následující změny a vylepšení:</span><span class="sxs-lookup"><span data-stu-id="75ebc-196">The runtime in .NET Framework 4.8 includes the following changes and improvements:</span></span>

<span data-ttu-id="75ebc-197">**Vylepšení kompilátoru JIT**.</span><span class="sxs-lookup"><span data-stu-id="75ebc-197">**Improvements to the JIT compiler**.</span></span> <span data-ttu-id="75ebc-198">Kompilátor Just-in-time (JIT) v rozhraní .NET Framework 4.8 je založen na kompilátoru JIT v rozhraní .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="75ebc-198">The Just-in-time (JIT) compiler in .NET Framework 4.8 is based on the JIT compiler in .NET Core 2.1.</span></span> <span data-ttu-id="75ebc-199">Mnoho optimalizací a všechny opravy chyb provedené v kompilátoru .NET Core 2.1 JIT jsou zahrnuty v kompilátoru .NET Framework 4.8 JIT.</span><span class="sxs-lookup"><span data-stu-id="75ebc-199">Many of the optimizations and all of the bug fixes made to the .NET Core 2.1 JIT compiler are included in the .NET Framework 4.8 JIT compiler.</span></span>

<span data-ttu-id="75ebc-200">**zlepšení NGEN**.</span><span class="sxs-lookup"><span data-stu-id="75ebc-200">**NGEN improvements**.</span></span> <span data-ttu-id="75ebc-201">Doba runtime zlepšila správu paměti pro [nativní image generátoru](../tools/ngen-exe-native-image-generator.md) (NGEN) obrázky tak, aby data mapovaná z ngen bitové kopie nejsou rezidentní paměti.</span><span class="sxs-lookup"><span data-stu-id="75ebc-201">The runtime has improved its memory management for [Native Image Generator](../tools/ngen-exe-native-image-generator.md) (NGEN) images so that data mapped from NGEN images are not memory-resident.</span></span> <span data-ttu-id="75ebc-202">To snižuje plochu k dispozici pro útoky, které se pokoušejí spustit libovolný kód úpravou paměti, která bude spuštěna.</span><span class="sxs-lookup"><span data-stu-id="75ebc-202">This reduces the surface area available to attacks that attempt to execute arbitrary code by modifying memory that will be executed.</span></span>

<span data-ttu-id="75ebc-203">**Antimalwarové skenování pro všechna sestavení**.</span><span class="sxs-lookup"><span data-stu-id="75ebc-203">**Antimalware scanning for all assemblies**.</span></span> <span data-ttu-id="75ebc-204">V předchozích verzích rozhraní .NET Framework modul runtime prohledá všechna sestavení načtená z disku pomocí programu Windows Defender nebo antimalwarového softwaru jiného výrobce.</span><span class="sxs-lookup"><span data-stu-id="75ebc-204">In previous versions of the .NET Framework, the runtime scans all assemblies loaded from disk using either Windows Defender or third-party antimalware software.</span></span> <span data-ttu-id="75ebc-205">Sestavení načtená z jiných zdrojů, například <xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType> metodou, však nejsou kontrolována a mohou potenciálně obsahovat nezjištěný malware.</span><span class="sxs-lookup"><span data-stu-id="75ebc-205">However, assemblies loaded from other sources, such as by the <xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType> method, are not scanned and can potentially contain undetected malware.</span></span> <span data-ttu-id="75ebc-206">Počínaje rozhraním .NET Framework 4.8 spuštěným v systému Windows 10 modul runtime spustí kontrolu antimalwarovými řešeními, která implementují [rozhraní AMSI (Antimalware Scan Interface).](/windows/desktop/AMSI/antimalware-scan-interface-portal)</span><span class="sxs-lookup"><span data-stu-id="75ebc-206">Starting with .NET Framework 4.8 running on Windows 10, the runtime triggers a scan by antimalware solutions that implement the [Antimalware Scan Interface (AMSI)](/windows/desktop/AMSI/antimalware-scan-interface-portal).</span></span>

<a name="v472" />

## <a name="whats-new-in-net-framework-472"></a><span data-ttu-id="75ebc-207">Co je nového v rozhraní .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="75ebc-207">What's new in .NET Framework 4.7.2</span></span>

<span data-ttu-id="75ebc-208">Rozhraní .NET Framework 4.7.2 obsahuje nové funkce v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="75ebc-208">.NET Framework 4.7.2 includes new features in the following areas:</span></span>

- [<span data-ttu-id="75ebc-209">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="75ebc-209">Base classes</span></span>](#core-472)
- [<span data-ttu-id="75ebc-210">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="75ebc-210">ASP.NET</span></span>](#asp-net472)
- [<span data-ttu-id="75ebc-211">Sítě</span><span class="sxs-lookup"><span data-stu-id="75ebc-211">Networking</span></span>](#net472)
- [<span data-ttu-id="75ebc-212">SQL</span><span class="sxs-lookup"><span data-stu-id="75ebc-212">SQL</span></span>](#sql472)
- [<span data-ttu-id="75ebc-213">WPF</span><span class="sxs-lookup"><span data-stu-id="75ebc-213">WPF</span></span>](#wpf472)
- [<span data-ttu-id="75ebc-214">ClickOnce</span><span class="sxs-lookup"><span data-stu-id="75ebc-214">ClickOnce</span></span>](#clickonce)

<span data-ttu-id="75ebc-215">Trvalé zaměření v rozhraní .NET Framework 4.7.2 je lepší usnadnění přístupu, což umožňuje aplikaci poskytovat odpovídající prostředí pro uživatele asistenční technologie.</span><span class="sxs-lookup"><span data-stu-id="75ebc-215">A continuing focus in .NET Framework 4.7.2 is improved accessibility, which allows an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="75ebc-216">Informace o vylepšení usnadnění v rozhraní .NET Framework 4.7.2 naleznete [v tématu Co je nového v usnadnění přístupnosti v rozhraní .NET Framework](whats-new-in-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-216">For information on accessibility improvements in .NET Framework 4.7.2, see [What's new in accessibility in the .NET Framework](whats-new-in-accessibility.md).</span></span>

<a name="core-472" />

#### <a name="base-classes"></a><span data-ttu-id="75ebc-217">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="75ebc-217">Base classes</span></span>

<span data-ttu-id="75ebc-218">Rozhraní .NET Framework 4.7.2 obsahuje velké množství kryptografických vylepšení, lepší podporu dekomprese archivů ZIP a další rozhraní API kolekce.</span><span class="sxs-lookup"><span data-stu-id="75ebc-218">.NET Framework 4.7.2 features a large number of cryptographic enhancements, better decompression support for ZIP archives, and additional collection APIs.</span></span>

<span data-ttu-id="75ebc-219">**Nové přetížení RSA. Vytvořit a DSA. Vytvořit**</span><span class="sxs-lookup"><span data-stu-id="75ebc-219">**New overloads of RSA.Create and DSA.Create**</span></span>

<span data-ttu-id="75ebc-220">Metody <xref:System.Security.Cryptography.DSA.Create(System.Security.Cryptography.DSAParameters)?displayProperty=nameWithType> <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> a umožňují zadat klíčové parametry při vytváření <xref:System.Security.Cryptography.DSA> <xref:System.Security.Cryptography.RSA> instancí nového nebo klíče.</span><span class="sxs-lookup"><span data-stu-id="75ebc-220">The <xref:System.Security.Cryptography.DSA.Create(System.Security.Cryptography.DSAParameters)?displayProperty=nameWithType> and <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> methods let you supply key parameters when instantiating a new <xref:System.Security.Cryptography.DSA> or <xref:System.Security.Cryptography.RSA> key.</span></span> <span data-ttu-id="75ebc-221">Umožňují nahradit kód takto:</span><span class="sxs-lookup"><span data-stu-id="75ebc-221">They allow you to replace code like the following:</span></span>

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

<span data-ttu-id="75ebc-222">s kódem, jako je tento:</span><span class="sxs-lookup"><span data-stu-id="75ebc-222">with code like this:</span></span>

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

<span data-ttu-id="75ebc-223">Metody <xref:System.Security.Cryptography.DSA.Create(System.Int32)?displayProperty=nameWithType> <xref:System.Security.Cryptography.RSA.Create(System.Int32)?displayProperty=nameWithType> a umožňují generovat <xref:System.Security.Cryptography.DSA> <xref:System.Security.Cryptography.RSA> nové nebo klíče s určitou velikostí klíče.</span><span class="sxs-lookup"><span data-stu-id="75ebc-223">The <xref:System.Security.Cryptography.DSA.Create(System.Int32)?displayProperty=nameWithType> and <xref:System.Security.Cryptography.RSA.Create(System.Int32)?displayProperty=nameWithType> methods let you generate new <xref:System.Security.Cryptography.DSA> or <xref:System.Security.Cryptography.RSA> keys with a specific key size.</span></span> <span data-ttu-id="75ebc-224">Příklad:</span><span class="sxs-lookup"><span data-stu-id="75ebc-224">For example:</span></span>

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

<span data-ttu-id="75ebc-225">**Konstruktory Rfc2898DeriveBytes přijímají název algoritmu hash**</span><span class="sxs-lookup"><span data-stu-id="75ebc-225">**Rfc2898DeriveBytes constructors accept a hash algorithm name**</span></span>

<span data-ttu-id="75ebc-226">Třída <xref:System.Security.Cryptography.Rfc2898DeriveBytes> má tři nové konstruktory s parametrem, <xref:System.Security.Cryptography.HashAlgorithmName> který identifikuje algoritmus HMAC pro použití při odvození klíčů.</span><span class="sxs-lookup"><span data-stu-id="75ebc-226">The <xref:System.Security.Cryptography.Rfc2898DeriveBytes> class has three new constructors with a <xref:System.Security.Cryptography.HashAlgorithmName> parameter that identifies the HMAC algorithm to use when deriving keys.</span></span> <span data-ttu-id="75ebc-227">Namísto použití SHA-1 by vývojáři měli používat hmac založený na SHA-2, jako je SHA-256, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="75ebc-227">Instead of using SHA-1, developers should use a SHA-2-based HMAC like SHA-256, as shown in the following example:</span></span>

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

<span data-ttu-id="75ebc-228">**Podpora dočasných kláves**</span><span class="sxs-lookup"><span data-stu-id="75ebc-228">**Support for ephemeral keys**</span></span>

<span data-ttu-id="75ebc-229">Import PFX může volitelně načíst soukromé klíče přímo z paměti, obcházet pevný disk.</span><span class="sxs-lookup"><span data-stu-id="75ebc-229">PFX import can optionally load private keys directly from memory, bypassing the hard drive.</span></span><span data-ttu-id="75ebc-230">Při nový <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> příznak je <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> zadán v konstruktoru nebo <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.Import%2A?displayProperty=nameWithType> jeden z přetížení metody, soukromé klíče budou načteny jako dočasné klíče.</span><span class="sxs-lookup"><span data-stu-id="75ebc-230"> When the new <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> flag is specified in an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> constructor or one of the overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.Import%2A?displayProperty=nameWithType> method, the private keys will be loaded as ephemeral keys.</span></span> <span data-ttu-id="75ebc-231">Tím zabráníte, aby byly klíče viditelné na disku.</span><span class="sxs-lookup"><span data-stu-id="75ebc-231">This prevents the keys from being visible on the disk.</span></span> <span data-ttu-id="75ebc-232">Nicméně:</span><span class="sxs-lookup"><span data-stu-id="75ebc-232">However:</span></span>

- <span data-ttu-id="75ebc-233">Vzhledem k tomu, že klíče nejsou trvalé na disk, certifikáty načtené tímto příznakem nejsou vhodné kandidáty přidat do X509Store.</span><span class="sxs-lookup"><span data-stu-id="75ebc-233">Since the keys are not persisted to disk, certificates loaded with this flag are not good candidates to add to an X509Store.</span></span>

- <span data-ttu-id="75ebc-234">Klíče načtené tímto způsobem jsou téměř vždy načteny přes Windows CNG.</span><span class="sxs-lookup"><span data-stu-id="75ebc-234">Keys loaded in this manner are almost always loaded via Windows CNG.</span></span> <span data-ttu-id="75ebc-235">Proto volající musí přistupovat k soukromému klíči voláním rozšiřujících metod, jako je [například cert. GetRSAPrivateKey()](xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A).</span><span class="sxs-lookup"><span data-stu-id="75ebc-235">Therefore, callers must access the private key by calling extension methods, such as [cert.GetRSAPrivateKey()](xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A).</span></span> <span data-ttu-id="75ebc-236">Vlastnost <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> nefunguje.</span><span class="sxs-lookup"><span data-stu-id="75ebc-236">The <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> property does not function.</span></span>

- <span data-ttu-id="75ebc-237">Vzhledem <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> k tomu, že starší vlastnost nefunguje s certifikáty, vývojáři by měli před přepnutím na dočasné klíče provádět přísné testování.</span><span class="sxs-lookup"><span data-stu-id="75ebc-237">Since the legacy <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> property does not work with certificates, developers should perform rigorous testing before switching to ephemeral keys.</span></span>

<span data-ttu-id="75ebc-238">**Programové vytváření žádostí o podpis podpisu certifikace PKCS# 10 a certifikátů veřejného klíče X.509**</span><span class="sxs-lookup"><span data-stu-id="75ebc-238">**Programmatic creation of PKCS#10 certification signing requests and X.509 public key certificates**</span></span>

<span data-ttu-id="75ebc-239">Počínaje rozhraním .NET Framework 4.7.2 mohou úlohy generovat žádosti o podepisování certifikátů (CSRs), což umožňuje, aby generování žádostí o certifikát bylo připraveno do existujících nástrojů.</span><span class="sxs-lookup"><span data-stu-id="75ebc-239">Starting with .NET Framework 4.7.2, workloads can generate certificate signing requests (CSRs), which allows certificate request generation to be staged into existing tooling.</span></span> <span data-ttu-id="75ebc-240">To je často užitečné v testovacích scénářích.</span><span class="sxs-lookup"><span data-stu-id="75ebc-240">This is frequently useful in test scenarios.</span></span>

<span data-ttu-id="75ebc-241">Další informace a příklady kódu naleznete v tématu Programatické vytváření žádostí o podpis certifikátu PKCS#10 a certifikátů veřejného klíče X.509 v [blogu .NET](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).</span><span class="sxs-lookup"><span data-stu-id="75ebc-241">For more information and code examples, see "Programmatic creation of PKCS#10 certification signing requests and X.509 public key certificates" in the [.NET Blog](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).</span></span>

<span data-ttu-id="75ebc-242">**Noví členové SignerInfo**</span><span class="sxs-lookup"><span data-stu-id="75ebc-242">**New SignerInfo members**</span></span>

<span data-ttu-id="75ebc-243">Počínaje rozhraním .NET Framework <xref:System.Security.Cryptography.Pkcs.SignerInfo> 4.7.2, třída zveřejňuje další informace o podpisu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-243">Starting with .NET Framework 4.7.2, the <xref:System.Security.Cryptography.Pkcs.SignerInfo> class exposes more information about the signature.</span></span> <span data-ttu-id="75ebc-244">Můžete načíst hodnotu <xref:System.Security.Cryptography.Pkcs.SignerInfo.SignatureAlgorithm?displayProperty=fullName> vlastnosti k určení podpisu algoritmus používaný podepisující osoby.</span><span class="sxs-lookup"><span data-stu-id="75ebc-244">You can retrieve the value of the <xref:System.Security.Cryptography.Pkcs.SignerInfo.SignatureAlgorithm?displayProperty=fullName> property to determine the signature algorithm used by the signer.</span></span> <span data-ttu-id="75ebc-245"><xref:System.Security.Cryptography.Pkcs.SignerInfo.GetSignature%2A?displayProperty=nameWithType>můžete být voláni, abyste získali kopii kryptografického podpisu pro tohoto podepisujícího.</span><span class="sxs-lookup"><span data-stu-id="75ebc-245"><xref:System.Security.Cryptography.Pkcs.SignerInfo.GetSignature%2A?displayProperty=nameWithType> can be called to get a copy of the cryptographic signature for this signer.</span></span>

<span data-ttu-id="75ebc-246">**Ponechání zabaleného datového proudu otevřeného po vyřazení CryptoStream**</span><span class="sxs-lookup"><span data-stu-id="75ebc-246">**Leaving a wrapped stream open after CryptoStream is disposed**</span></span>

<span data-ttu-id="75ebc-247">Počínaje rozhraním .NET Framework 4.7.2 má <xref:System.Security.Cryptography.CryptoStream> třída <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> další konstruktor, který umožňuje nezavírat zalomený datový proud.</span><span class="sxs-lookup"><span data-stu-id="75ebc-247">Starting with .NET Framework 4.7.2, the <xref:System.Security.Cryptography.CryptoStream> class has an additional constructor that allows <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> to not close the wrapped stream.</span></span><span data-ttu-id="75ebc-248">Chcete-li po nechat zabalený datový proud otevřený po uvolnění <xref:System.Security.Cryptography.CryptoStream> instance, zavolejte nový <xref:System.Security.Cryptography.CryptoStream> konstruktor takto:</span><span class="sxs-lookup"><span data-stu-id="75ebc-248"> To leave the wrapped stream open after the <xref:System.Security.Cryptography.CryptoStream> instance is disposed, call the new <xref:System.Security.Cryptography.CryptoStream> constructor as follows:</span></span>

```csharp
var cStream = new CryptoStream(stream, transform, mode, leaveOpen: true);
```

```vb
Dim cStream = New CryptoStream(stream, transform, mode, leaveOpen:=true)
```

<span data-ttu-id="75ebc-249">**Dekompresní změny v DeflateStream**</span><span class="sxs-lookup"><span data-stu-id="75ebc-249">**Decompression changes in DeflateStream**</span></span>

<span data-ttu-id="75ebc-250">Počínaje rozhraním .NET Framework 4.7.2 se implementace <xref:System.IO.Compression.DeflateStream> dekompresních operací ve třídě ve výchozím nastavení změnila na nativní rozhraní API systému Windows.</span><span class="sxs-lookup"><span data-stu-id="75ebc-250">Starting with .NET Framework 4.7.2, the implementation of decompression operations in the <xref:System.IO.Compression.DeflateStream> class has changed to use native Windows APIs by default.</span></span> <span data-ttu-id="75ebc-251">Obvykle to má za následek podstatné zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-251">Typically, this results in a substantial performance improvement.</span></span>

<span data-ttu-id="75ebc-252">Podpora dekomprese pomocí rozhraní API systému Windows je ve výchozím nastavení povolena pro aplikace, které cílí na rozhraní .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="75ebc-252">Support for decompression by using Windows APIs is enabled by default for applications that target .NET Framework 4.7.2.</span></span> <span data-ttu-id="75ebc-253">Aplikace, které cílí na starší verze rozhraní .NET Framework, ale jsou spuštěny v rozhraní .NET Framework 4.7.2, se mohou do tohoto chování přihlásit přidáním následujícího [přepínače AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="75ebc-253">Applications that target earlier versions of .NET Framework but are running under .NET Framework 4.7.2 can opt into this behavior by adding the following [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the application configuration file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=false" />
```

<span data-ttu-id="75ebc-254">**Další kolekce API**</span><span class="sxs-lookup"><span data-stu-id="75ebc-254">**Additional collection APIs**</span></span>

<span data-ttu-id="75ebc-255">Rozhraní .NET Framework 4.7.2 přidává do <xref:System.Collections.Generic.SortedSet%601> typů <xref:System.Collections.Generic.HashSet%601> a řadu nových rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="75ebc-255">.NET Framework 4.7.2 adds a number of new APIs to the <xref:System.Collections.Generic.SortedSet%601> and <xref:System.Collections.Generic.HashSet%601> types.</span></span> <span data-ttu-id="75ebc-256">Mezi ně patří:</span><span class="sxs-lookup"><span data-stu-id="75ebc-256">These include:</span></span>

- <span data-ttu-id="75ebc-257">`TryGetValue`metody, které rozšiřují vzor try používaný v jiných typech kolekcí na tyto dva typy.</span><span class="sxs-lookup"><span data-stu-id="75ebc-257">`TryGetValue` methods, which extend the try pattern used in other collection types to these two types.</span></span> <span data-ttu-id="75ebc-258">Existují tyto metody:</span><span class="sxs-lookup"><span data-stu-id="75ebc-258">The methods are:</span></span>

  - [<span data-ttu-id="75ebc-259">veřejné bool HashSet\<T>. TryGetValue(T equalValue, out T actualValue)</span><span class="sxs-lookup"><span data-stu-id="75ebc-259">public bool HashSet\<T>.TryGetValue(T equalValue, out T actualValue)</span></span>](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)
  - [<span data-ttu-id="75ebc-260">veřejné bool SortedSet\<T>. TryGetValue(T equalValue, out T actualValue)</span><span class="sxs-lookup"><span data-stu-id="75ebc-260">public bool SortedSet\<T>.TryGetValue(T equalValue, out T actualValue)</span></span>](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)

- <span data-ttu-id="75ebc-261">`Enumerable.To*`metody rozšíření, které převedou <xref:System.Collections.Generic.HashSet%601>kolekci na :</span><span class="sxs-lookup"><span data-stu-id="75ebc-261">`Enumerable.To*` extension methods, which convert a collection to a <xref:System.Collections.Generic.HashSet%601>:</span></span>

  - [<span data-ttu-id="75ebc-262">veřejné statické HashSet\<TSource>\<ToHashSet TSource\<> (tento IEnumerable TSource> zdroj)</span><span class="sxs-lookup"><span data-stu-id="75ebc-262">public static HashSet\<TSource> ToHashSet\<TSource>(this IEnumerable\<TSource> source)</span></span>](xref:System.Linq.Enumerable.ToHashSet%2A)
  - [<span data-ttu-id="75ebc-263">veřejné\<statické HashSet TSource>\<ToHashSet TSource\<> (tento IEnumerable\<TSource> zdroj, IEqualityComparer TSource> porovnávání)</span><span class="sxs-lookup"><span data-stu-id="75ebc-263">public static HashSet\<TSource> ToHashSet\<TSource>(this IEnumerable\<TSource> source, IEqualityComparer\<TSource> comparer)</span></span>](xref:System.Linq.Enumerable.ToHashSet%2A)

- <span data-ttu-id="75ebc-264">Nové <xref:System.Collections.Generic.HashSet%601> konstruktory, které umožňují nastavit kapacitu kolekce, což přináší výhodu výkonu, <xref:System.Collections.Generic.HashSet%601> když znáte velikost předem:</span><span class="sxs-lookup"><span data-stu-id="75ebc-264">New <xref:System.Collections.Generic.HashSet%601> constructors that let you set the collection's capacity, which yields a performance benefit when you know the size of the <xref:System.Collections.Generic.HashSet%601> in advance:</span></span>

  - <span data-ttu-id="75ebc-265">[veřejná HashSet(int kapacita)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32))</span><span class="sxs-lookup"><span data-stu-id="75ebc-265">[public HashSet(int capacity)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32))</span></span>
  - <span data-ttu-id="75ebc-266">[veřejné HashSet (int kapacita, IEqualityComparer\<T> porovnávání)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32,System.Collections.Generic.IEqualityComparer%7B%600%7D))</span><span class="sxs-lookup"><span data-stu-id="75ebc-266">[public HashSet(int capacity, IEqualityComparer\<T> comparer)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32,System.Collections.Generic.IEqualityComparer%7B%600%7D))</span></span>

<span data-ttu-id="75ebc-267">Třída <xref:System.Collections.Concurrent.ConcurrentDictionary%602> obsahuje nové přetížení <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> a <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> metody načíst hodnotu ze slovníku nebo přidat, pokud není nalezen a přidat hodnotu do slovníku nebo aktualizovat, pokud již existuje.</span><span class="sxs-lookup"><span data-stu-id="75ebc-267">The <xref:System.Collections.Concurrent.ConcurrentDictionary%602> class includes new overloads of the <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> and <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> methods to retrieve a value from the dictionary or to add it if it is not found, and to add a value to the dictionary or to update it if it already exists.</span></span>

```csharp
public TValue AddOrUpdate<TArg>(TKey key, Func<TKey, TArg, TValue> addValueFactory, Func<TKey, TValue, TArg, TValue> updateValueFactory, TArg factoryArgument)

public TValue GetOrAdd<TArg>(TKey key, Func<TKey, TArg, TValue> valueFactory, TArg factoryArgument)
```

```vb
Public AddOrUpdate(Of TArg)(key As TKey, addValueFactory As Func(Of TKey, TArg, TValue), updateValueFactory As Func(Of TKey, TValue, TArg, TValue), factoryArgument As TArg) As TValue

Public GetOrAdd(Of TArg)(key As TKey, valueFactory As Func(Of TKey, TArg, TValue), factoryArgument As TArg) As TValue
```

<a name="asp-net472" />

#### <a name="aspnet"></a><span data-ttu-id="75ebc-268">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="75ebc-268">ASP.NET</span></span>

<span data-ttu-id="75ebc-269">**Podpora vkládání závislostí ve webových formulářích**</span><span class="sxs-lookup"><span data-stu-id="75ebc-269">**Support for dependency injection in Web Forms**</span></span>

<span data-ttu-id="75ebc-270">[Vkládání závislostí (DI)](/aspnet/core/fundamentals/dependency-injection#overview-of-dependency-injection) odděluje objekty a jejich závislosti tak, aby kód objektu již není třeba změnit jen proto, že se změnila závislost.</span><span class="sxs-lookup"><span data-stu-id="75ebc-270">[Dependency injection (DI)](/aspnet/core/fundamentals/dependency-injection#overview-of-dependency-injection) decouples objects and their dependencies so that an object's code no longer needs to be changed just because a dependency has changed.</span></span> <span data-ttu-id="75ebc-271">Při vývoji ASP.NET aplikací, které cílí na rozhraní .NET Framework 4.7.2, můžete:</span><span class="sxs-lookup"><span data-stu-id="75ebc-271">When developing ASP.NET applications that target .NET Framework 4.7.2, you can:</span></span>

- <span data-ttu-id="75ebc-272">Použijte setter založené, založené na rozhraní a vkládání na základě konstruktoru v [obslužné rutiny a moduly](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [Page instance](xref:System.Web.UI.Page)a [uživatelské ovládací prvky](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) ASP.NET projekty webových aplikací.</span><span class="sxs-lookup"><span data-stu-id="75ebc-272">Use setter-based, interface-based, and constructor-based injection in [handlers and modules](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [Page instances](xref:System.Web.UI.Page), and [user controls](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) of ASP.NET web application projects.</span></span>

- <span data-ttu-id="75ebc-273">Použití vkládání založené na setteru a rozhraní v [obslužných rutinách a modulech](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [instancích Page](xref:System.Web.UI.Page)a [uživatelských ovládacích prvcích](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) ASP.NET projekty webu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-273">Use setter-based and interface-based injection in [handlers and modules](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [Page instances](xref:System.Web.UI.Page), and [user controls](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) of ASP.NET web site projects.</span></span>

- <span data-ttu-id="75ebc-274">Připojte různé rámce vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="75ebc-274">Plug in different dependency injection frameworks.</span></span>

<span data-ttu-id="75ebc-275">**Podpora souborů cookie stejného webu**</span><span class="sxs-lookup"><span data-stu-id="75ebc-275">**Support for same-site cookies**</span></span>

<span data-ttu-id="75ebc-276">[SameSite](https://tools.ietf.org/html/draft-west-first-party-cookies-07) brání prohlížeči v odesílání souboru cookie spolu s požadavkem na více stránek.</span><span class="sxs-lookup"><span data-stu-id="75ebc-276">[SameSite](https://tools.ietf.org/html/draft-west-first-party-cookies-07) prevents a browser from sending a cookie along with a cross-site request.</span></span> <span data-ttu-id="75ebc-277">Rozhraní .NET Framework 4.7.2 přidá <xref:System.Web.HttpCookie.SameSite?displayProperty=nameWithType> <xref:System.Web.SameSiteMode?displayProperty=nameWithType> vlastnost, jejíž hodnota je člen výčtu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-277">.NET Framework 4.7.2 adds a <xref:System.Web.HttpCookie.SameSite?displayProperty=nameWithType> property whose value is a <xref:System.Web.SameSiteMode?displayProperty=nameWithType> enumeration member.</span></span> <span data-ttu-id="75ebc-278">Pokud je <xref:System.Web.SameSiteMode.Strict?displayProperty=nameWithType> jeho <xref:System.Web.SameSiteMode.Lax?displayProperty=nameWithType>hodnota nebo `SameSite` , ASP.NET přidá atribut do hlavičky set-cookie.</span><span class="sxs-lookup"><span data-stu-id="75ebc-278">If its value is <xref:System.Web.SameSiteMode.Strict?displayProperty=nameWithType> or <xref:System.Web.SameSiteMode.Lax?displayProperty=nameWithType>, ASP.NET adds the `SameSite` attribute to the set-cookie header.</span></span> <span data-ttu-id="75ebc-279">Podpora Stejnéstránky se <xref:System.Web.HttpCookie> vztahuje na objekty, stejně jako na <xref:System.Web.Security.FormsAuthentication> a <xref:System.Web.SessionState> cookies.</span><span class="sxs-lookup"><span data-stu-id="75ebc-279">SameSite support applies to <xref:System.Web.HttpCookie> objects, as well as to <xref:System.Web.Security.FormsAuthentication> and <xref:System.Web.SessionState> cookies.</span></span>

<span data-ttu-id="75ebc-280">Můžete nastavit SameSite <xref:System.Web.HttpCookie> pro objekt takto:</span><span class="sxs-lookup"><span data-stu-id="75ebc-280">You can set SameSite for an <xref:System.Web.HttpCookie> object as follows:</span></span>

```csharp
var c = new HttpCookie("secureCookie", "same origin");
c.SameSite = SameSiteMode.Lax;
```

```vb
Dim c As New HttpCookie("secureCookie", "same origin")
c.SameSite = SameSiteMode.Lax
```

<span data-ttu-id="75ebc-281">Soubory cookie SameSite můžete také nakonfigurovat na úrovni aplikace úpravou souboru web.config:</span><span class="sxs-lookup"><span data-stu-id="75ebc-281">You can also configure SameSite cookies at the application level by modifying the web.config file:</span></span>

```xml
<system.web>
   <httpCookies sameSite="Strict" />
</system.web>
```

<span data-ttu-id="75ebc-282">Můžete přidat SameSite <xref:System.Web.Security.FormsAuthentication> <xref:System.Web.SessionState> pro a cookies úpravou webového konfiguračního souboru:</span><span class="sxs-lookup"><span data-stu-id="75ebc-282">You can add SameSite for <xref:System.Web.Security.FormsAuthentication> and <xref:System.Web.SessionState> cookies by modifying the web config file:</span></span>

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

<a name="net472" />

#### <a name="networking"></a><span data-ttu-id="75ebc-283">Sítě</span><span class="sxs-lookup"><span data-stu-id="75ebc-283">Networking</span></span>

<span data-ttu-id="75ebc-284">**Implementace vlastností HttpClientHandler**</span><span class="sxs-lookup"><span data-stu-id="75ebc-284">**Implementation of HttpClientHandler properties**</span></span>

<span data-ttu-id="75ebc-285">Rozhraní .NET Framework 4.7.1 <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> přidalo do třídy osm vlastností.</span><span class="sxs-lookup"><span data-stu-id="75ebc-285">.NET Framework 4.7.1 added eight properties to the <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="75ebc-286">Nicméně, dva <xref:System.PlatformNotSupportedException>hodil .</span><span class="sxs-lookup"><span data-stu-id="75ebc-286">However, two threw a <xref:System.PlatformNotSupportedException>.</span></span> <span data-ttu-id="75ebc-287">Rozhraní .NET Framework 4.7.2 nyní poskytuje implementaci těchto vlastností.</span><span class="sxs-lookup"><span data-stu-id="75ebc-287">.NET Framework 4.7.2 now provides an implementation for these properties.</span></span> <span data-ttu-id="75ebc-288">Mezi vlastnosti patří:</span><span class="sxs-lookup"><span data-stu-id="75ebc-288">The properties are:</span></span>

- <xref:System.Net.Http.HttpClientHandler.CheckCertificateRevocationList>
- <xref:System.Net.Http.HttpClientHandler.SslProtocols>

<a name="sql472" />

#### <a name="sqlclient"></a><span data-ttu-id="75ebc-289">SQLClient</span><span class="sxs-lookup"><span data-stu-id="75ebc-289">SQLClient</span></span>

<span data-ttu-id="75ebc-290">**Podpora univerzálního ověřování azure služby Azure AD a vícefaktorového ověřování**</span><span class="sxs-lookup"><span data-stu-id="75ebc-290">**Support for Azure Active Directory Universal Authentication and Multi-Factor authentication**</span></span>

<span data-ttu-id="75ebc-291">Rostoucí požadavky na dodržování předpisů a zabezpečení vyžadují, aby mnoho zákazníků používalo vícefaktorové ověřování (MFA).</span><span class="sxs-lookup"><span data-stu-id="75ebc-291">Growing compliance and security demands require that many customers use multi-factor authentication (MFA).</span></span> <span data-ttu-id="75ebc-292">Kromě toho aktuální osvědčené postupy odradit včetně uživatelských hesel přímo v připojovacích řetězcích.</span><span class="sxs-lookup"><span data-stu-id="75ebc-292">In addition, current best practices discourage including user passwords directly in connection strings.</span></span> <span data-ttu-id="75ebc-293">Pro podporu těchto změn rozšiřuje rozhraní .NET Framework 4.7.2 [připojovací řetězce SQLClient](xref:System.Data.SqlClient.SqlConnection.ConnectionString) přidáním nové hodnoty Active Directory Interactive pro existující klíčové slovo Ověřování pro podporu ověřování vícefaktorové ověřování a [ověřování Azure AD](/azure/sql-database/sql-database-aad-authentication-configure).</span><span class="sxs-lookup"><span data-stu-id="75ebc-293">To support these changes, .NET Framework 4.7.2 extends [SQLClient connection strings](xref:System.Data.SqlClient.SqlConnection.ConnectionString) by adding a new value, "Active Directory Interactive", for the existing "Authentication" keyword to support MFA and [Azure AD Authentication](/azure/sql-database/sql-database-aad-authentication-configure).</span></span> <span data-ttu-id="75ebc-294">Nová interaktivní metoda podporuje nativní a federované uživatele Azure AD, stejně jako uživatele hosta Azure AD.</span><span class="sxs-lookup"><span data-stu-id="75ebc-294">The new interactive method supports native and federated Azure AD users as well as Azure AD guest users.</span></span> <span data-ttu-id="75ebc-295">Při použití této metody ověřování MFA uložené službou Azure AD je podporována pro databáze SQL.</span><span class="sxs-lookup"><span data-stu-id="75ebc-295">When this method is used, the MFA authentication imposed by Azure AD is supported for SQL databases.</span></span> <span data-ttu-id="75ebc-296">Kromě toho proces ověřování požaduje heslo uživatele dodržovat doporučené postupy zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="75ebc-296">In addition, the authentication process requests a user password to adhere to security best practices.</span></span>

<span data-ttu-id="75ebc-297">V předchozích verzích rozhraní .NET Framework <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryPassword?displayProperty=nameWithType> připojení <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryIntegrated?displayProperty=nameWithType> SQL podporovalo pouze možnosti a.</span><span class="sxs-lookup"><span data-stu-id="75ebc-297">In previous versions of the .NET Framework, SQL connectivity supported only the <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryPassword?displayProperty=nameWithType> and <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryIntegrated?displayProperty=nameWithType> options.</span></span> <span data-ttu-id="75ebc-298">Oba tyto jsou součástí neinteraktivní protokol [ADAL](/azure/active-directory/develop/active-directory-authentication-libraries), který nepodporuje vícefaktorové.</span><span class="sxs-lookup"><span data-stu-id="75ebc-298">Both of these are part of the non-interactive [ADAL protocol](/azure/active-directory/develop/active-directory-authentication-libraries), which does not support MFA.</span></span> <span data-ttu-id="75ebc-299">S novou <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryInteractive?displayProperty=nameWithType> možností, sql připojení podporuje Vícefaktorové ověřování, stejně jako existující metody ověřování (heslo a integrované ověřování), který umožňuje uživatelům zadávat uživatelská hesla interaktivně bez uchování hesla v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="75ebc-299">With the new <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryInteractive?displayProperty=nameWithType> option, SQL connectivity supports MFA as well as existing authentication methods (password and integrated authentication), which allows users to enter user passwords interactively without persisting passwords in the connection string.</span></span>

<span data-ttu-id="75ebc-300">Další informace a příklad naleznete v tématu SQL -- Azure AD Univerzální a vícefaktorové ověřování Support" v [.NET Blog](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).</span><span class="sxs-lookup"><span data-stu-id="75ebc-300">For more information and an example, see "SQL -- Azure AD Universal and Multi-factor Authentication Support" in the [.NET Blog](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).</span></span>

<span data-ttu-id="75ebc-301">**Podpora pro vždy šifrované verze 2**</span><span class="sxs-lookup"><span data-stu-id="75ebc-301">**Support for Always Encrypted version 2**</span></span>

<span data-ttu-id="75ebc-302">NET Framework 4.7.2 přidává podpěry pro enklávu vždy šifrované.</span><span class="sxs-lookup"><span data-stu-id="75ebc-302">NET Framework 4.7.2 adds supports for enclave-based Always Encrypted.</span></span> <span data-ttu-id="75ebc-303">Původní verze always encrypted je technologie šifrování na straně klienta, ve které šifrovací klíče nikdy neopustí klienta.</span><span class="sxs-lookup"><span data-stu-id="75ebc-303">The original version of Always Encrypted is a client-side encryption technology in which encryption keys never leave the client.</span></span> <span data-ttu-id="75ebc-304">V enklávě založené vždy šifrované, klient může volitelně odeslat šifrovací klíče do zabezpečené enklávy, což je zabezpečené výpočetní entity, které lze považovat za součást SQL Server, ale že kód SQL Server nelze manipulovat s.</span><span class="sxs-lookup"><span data-stu-id="75ebc-304">In enclave-based Always Encrypted, the client can optionally send the encryption keys to a secure enclave, which is a secure computational entity that can be considered part of SQL Server but that SQL Server code cannot tamper with.</span></span> <span data-ttu-id="75ebc-305">Pro podporu enklávy založené vždy šifrované, .NET Framework 4.7.2 přidá následující typy a členy <xref:System.Data.SqlClient> do oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="75ebc-305">To support enclave-based Always Encrypted, .NET Framework 4.7.2 adds the following types and members to the <xref:System.Data.SqlClient> namespace:</span></span>

- <span data-ttu-id="75ebc-306"><xref:System.Data.SqlClient.SqlConnectionStringBuilder.EnclaveAttestationUrl?displayProperty=nameWithType>, který určuje Uri pro enklávu vždy šifrované.</span><span class="sxs-lookup"><span data-stu-id="75ebc-306"><xref:System.Data.SqlClient.SqlConnectionStringBuilder.EnclaveAttestationUrl?displayProperty=nameWithType>, which specifies the Uri for enclave-based Always Encrypted.</span></span>

- <span data-ttu-id="75ebc-307"><xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider>, což je abstraktní třída, ze které jsou odvozeny všechny zprostředkovatele enklávy.</span><span class="sxs-lookup"><span data-stu-id="75ebc-307"><xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider>, which is an abstract class from which all enclave providers are derived.</span></span>

- <span data-ttu-id="75ebc-308"><xref:System.Data.SqlClient.SqlEnclaveSession>, který zapouzdřuje stav pro danou enklávu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-308"><xref:System.Data.SqlClient.SqlEnclaveSession>, which encapsulates the state for a given enclave session.</span></span>

- <span data-ttu-id="75ebc-309"><xref:System.Data.SqlClient.SqlEnclaveAttestationParameters>, který poskytuje parametry atestace používané sql serverem k získání informací potřebných ke spuštění určitého protokolu osazení.</span><span class="sxs-lookup"><span data-stu-id="75ebc-309"><xref:System.Data.SqlClient.SqlEnclaveAttestationParameters>, which provides the attestation parameters used by SQL Server to get information required to execute a particular Attestation Protocol.</span></span>

<span data-ttu-id="75ebc-310">Konfigurační soubor aplikace pak určuje <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider?displayProperty=nameWithType> konkrétní implementaci abstraktní třídy, která poskytuje funkce pro zprostředkovatele enklávy.</span><span class="sxs-lookup"><span data-stu-id="75ebc-310">The application configuration file then specifies a concrete implementation of the abstract <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider?displayProperty=nameWithType> class that provides the functionality for the enclave provider.</span></span> <span data-ttu-id="75ebc-311">Příklad:</span><span class="sxs-lookup"><span data-stu-id="75ebc-311">For example:</span></span>

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

<span data-ttu-id="75ebc-312">Základní tok enklávy vždy šifrované je:</span><span class="sxs-lookup"><span data-stu-id="75ebc-312">The basic flow of enclave-based Always Encrypted is:</span></span>

1. <span data-ttu-id="75ebc-313">Uživatel vytvoří alwaysencrypted připojení k SQL Server, který podporoval enklávy založené vždy šifrované.</span><span class="sxs-lookup"><span data-stu-id="75ebc-313">The user creates an AlwaysEncrypted connection to SQL Server that supported enclave-based Always Encrypted.</span></span> <span data-ttu-id="75ebc-314">Řidič kontaktuje atestační službu, aby se ujistil, že se připojuje k pravé enklávě.</span><span class="sxs-lookup"><span data-stu-id="75ebc-314">The driver contacts the attestation service to ensure that it is connecting to right enclave.</span></span>

1. <span data-ttu-id="75ebc-315">Po otestování enklávy ovladač vytvoří zabezpečený kanál se zabezpečenou enklávou hostovoci hostovoci na serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="75ebc-315">Once the enclave has been attested, the driver establishes a secure channel with the secure enclave hosted on SQL Server.</span></span>

1. <span data-ttu-id="75ebc-316">Ovladač sdílí šifrovací klíče autorizované klientem se zabezpečenou enklávou po dobu trvání připojení SQL.</span><span class="sxs-lookup"><span data-stu-id="75ebc-316">The driver shares encryption keys authorized by the client with the secure enclave for the duration of the SQL connection.</span></span>

<a name="wpf472" />

#### <a name="windows-presentation-foundation"></a><span data-ttu-id="75ebc-317">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="75ebc-317">Windows Presentation Foundation</span></span>

<span data-ttu-id="75ebc-318">**Hledání ResourceDictionaries podle zdroje**</span><span class="sxs-lookup"><span data-stu-id="75ebc-318">**Finding ResourceDictionaries by Source**</span></span>

<span data-ttu-id="75ebc-319">Počínaje rozhraním .NET Framework 4.7.2 může <xref:System.Windows.Xps.Packaging.IXpsFixedPageReader.ResourceDictionaries> diagnostický pomocník vyhledat ty, které byly vytvořeny z daného zdroje Uri.</span><span class="sxs-lookup"><span data-stu-id="75ebc-319">Starting with .NET Framework 4.7.2, a diagnostic assistant can locate the <xref:System.Windows.Xps.Packaging.IXpsFixedPageReader.ResourceDictionaries> that have been created from a given source Uri.</span></span><span data-ttu-id="75ebc-320">(Tato funkce je určena diagnostickými asistenty, nikoli produkčními aplikacemi.) Diagnostický asistent, jako je například visual studio "Upravit a pokračovat" zařízení umožňuje jeho uživateli upravit ResourceDictionary s úmyslem, že změny se použijí na spuštěné aplikace.</span><span class="sxs-lookup"><span data-stu-id="75ebc-320"> (This feature is for use by diagnostic assistants, not by production applications.) A diagnostic assistant such as Visual Studio’s “Edit-and-Continue” facility lets its user edit a ResourceDictionary with the intent that the changes be applied to the running application.</span></span> <span data-ttu-id="75ebc-321">Jedním z kroků v dosažení tohoto je nalezení všech ResourceDictionaries, které spuštěná aplikace vytvořila ze slovníku, který je upravován.</span><span class="sxs-lookup"><span data-stu-id="75ebc-321">One step in achieving this is finding all the ResourceDictionaries that the running application has created from the dictionary that’s being edited.</span></span> <span data-ttu-id="75ebc-322">Aplikace může například deklarovat ResourceDictionary, jehož obsah je zkopírován z daného zdroje URI:</span><span class="sxs-lookup"><span data-stu-id="75ebc-322">For example, an application can declare a ResourceDictionary whose content is copied from a given source URI:</span></span>

```xml
<ResourceDictionary Source="MyRD.xaml" />
```

<span data-ttu-id="75ebc-323">Diagnostický pomocník, který uetuje původní značky v *MyRD.xaml* můžete použít novou funkci k vyhledání slovníku.</span><span class="sxs-lookup"><span data-stu-id="75ebc-323">A diagnostic assistant that edits the original markup in *MyRD.xaml* can use the new feature to locate the dictionary.</span></span><span data-ttu-id="75ebc-324">Tato funkce je implementována <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetResourceDictionariesForSource%2A?displayProperty=nameWithType>novou statickou metodou .</span><span class="sxs-lookup"><span data-stu-id="75ebc-324"> The feature is implemented by a new static method, <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetResourceDictionariesForSource%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="75ebc-325">Diagnostický asistent volá novou metodu pomocí absolutní Uri, který identifikuje původní značky, jak je znázorněno na následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="75ebc-325">The diagnostic assistant calls the new method using an absolute Uri that identifies the original markup, as illustrated by the following code:</span></span>

```csharp
IEnumerable<ResourceDictionary> dictionaries = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(new Uri("pack://application:,,,/MyApp;component/MyRD.xaml"));
```

```vb
Dim dictionaries As IEnumerable(Of ResourceDictionary) = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(New Uri("pack://application:,,,/MyApp;component/MyRD.xaml"))
```

<span data-ttu-id="75ebc-326">Metoda vrátí prázdný výčt, <xref:System.Windows.Diagnostics.VisualDiagnostics> pokud není [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  povolena a je nastavena proměnná prostředí.</span><span class="sxs-lookup"><span data-stu-id="75ebc-326">The method returns an empty enumerable unless <xref:System.Windows.Diagnostics.VisualDiagnostics> is enabled and the [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) environment variable is set.</span></span>

<span data-ttu-id="75ebc-327">**Hledání resourcedictionary vlastníků**</span><span class="sxs-lookup"><span data-stu-id="75ebc-327">**Finding ResourceDictionary owners**</span></span>

<span data-ttu-id="75ebc-328">Počínaje rozhraním .NET Framework 4.7.2 může diagnostický asistent <xref:Windows.UI.Xaml.ResourceDictionary>vyhledat vlastníky daného .</span><span class="sxs-lookup"><span data-stu-id="75ebc-328">Starting with .NET Framework 4.7.2, a diagnostic assistant can locate the owners of a given <xref:Windows.UI.Xaml.ResourceDictionary>.</span></span><span data-ttu-id="75ebc-329">(Tato funkce je určena pro diagnostické asistenty a nikoli pro produkční aplikace.) Vždy, když je <xref:Windows.UI.Xaml.ResourceDictionary>provedena změna , WPF automaticky vyhledá všechny [odkazy DynamicResource,](../wpf/advanced/dynamicresource-markup-extension.md) které mohou být ovlivněny změnou.</span><span class="sxs-lookup"><span data-stu-id="75ebc-329"> (The feature is for use by diagnostic assistants and not by production applications.) Whenever a change is made to a <xref:Windows.UI.Xaml.ResourceDictionary>, WPF automatically finds all [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) references that might be affected by the change.</span></span>

<span data-ttu-id="75ebc-330">Diagnostický asistent, jako je například visual studio "Upravit a pokračovat" zařízení může chtít rozšířit to pro zpracování [staticresource](../wpf/advanced/staticresource-markup-extension.md) odkazy.</span><span class="sxs-lookup"><span data-stu-id="75ebc-330">A diagnostic assistant such as Visual Studio's "Edit-and-Continue" facility may want to extend this to handle [StaticResource](../wpf/advanced/staticresource-markup-extension.md) references.</span></span> <span data-ttu-id="75ebc-331">Prvním krokem v tomto procesu je najít vlastníky slovníku; to znamená najít všechny objekty, jejichž `Resources` vlastnost odkazuje na slovník (buď <xref:System.Windows.ResourceDictionary.MergedDictionaries?displayProperty=nameWithType> přímo, nebo nepřímo prostřednictvím vlastnosti).</span><span class="sxs-lookup"><span data-stu-id="75ebc-331">The first step in this process is to find the owners of the dictionary; that is, to find all the objects whose `Resources` property refers to the dictionary (either directly, or indirectly via the <xref:System.Windows.ResourceDictionary.MergedDictionaries?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="75ebc-332">Tři nové statické metody <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics?displayProperty=nameWithType> implementované na třídu, jeden `Resources` pro každý základní typy, které má vlastnost, podporují tento krok:</span><span class="sxs-lookup"><span data-stu-id="75ebc-332">Three new static methods implemented on the <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics?displayProperty=nameWithType> class, one for each of the base types that has a `Resources` property, support this step:</span></span>

- [`public static IEnumerable<FrameworkElement> GetFrameworkElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkElementOwners%2A)

- [`public static IEnumerable<FrameworkContentElement> GetFrameworkContentElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkContentElementOwners%2A)

- [`public static IEnumerable<Application> GetApplicationOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetApplicationOwners%2A)

<span data-ttu-id="75ebc-333">Tyto metody vrátí prázdný výčt, <xref:System.Windows.Diagnostics.VisualDiagnostics> pokud [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  není povolena a je nastavena proměnná prostředí.</span><span class="sxs-lookup"><span data-stu-id="75ebc-333">These methods return an empty enumerable unless <xref:System.Windows.Diagnostics.VisualDiagnostics> is enabled and the [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) environment variable is set.</span></span>

<span data-ttu-id="75ebc-334">**Hledání odkazů na statickou prostředek**</span><span class="sxs-lookup"><span data-stu-id="75ebc-334">**Finding StaticResource references**</span></span>

<span data-ttu-id="75ebc-335">Diagnostický pomocník nyní může přijímat oznámení při každém vyřešení odkazu [staticresource.](../wpf/advanced/staticresource-markup-extension.md)</span><span class="sxs-lookup"><span data-stu-id="75ebc-335">A diagnostic assistant can now receive a notification whenever a [StaticResource](../wpf/advanced/staticresource-markup-extension.md) reference is resolved.</span></span><span data-ttu-id="75ebc-336">(Funkce je určena pro diagnostické asistenty, nikoli produkční aplikace.) Diagnostický asistent, jako je například visual studio "Upravit a pokračovat" zařízení může chtít aktualizovat <xref:Windows.UI.Xaml.ResourceDictionary> všechna použití prostředku při jeho hodnota v změně.</span><span class="sxs-lookup"><span data-stu-id="75ebc-336"> (The feature is for use by diagnostic assistants, not by production applications.) A diagnostic assistant such as Visual Studio’s “Edit-and-Continue” facility may want to update all uses of a resource when its value in a <xref:Windows.UI.Xaml.ResourceDictionary> changes.</span></span> <span data-ttu-id="75ebc-337">WPF to provádí automaticky pro [odkazy DynamicResource,](../wpf/advanced/dynamicresource-markup-extension.md) ale záměrně tak nečiní pro [odkazy StaticResource.](../wpf/advanced/staticresource-markup-extension.md)</span><span class="sxs-lookup"><span data-stu-id="75ebc-337">WPF does this automatically for [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) references, but it intentionally does not do so for [StaticResource](../wpf/advanced/staticresource-markup-extension.md) references.</span></span> <span data-ttu-id="75ebc-338">Počínaje rozhraním .NET Framework 4.7.2 může diagnostický pomocník použít tato oznámení k vyhledání těchto použití statického prostředku.</span><span class="sxs-lookup"><span data-stu-id="75ebc-338">Starting with .NET Framework 4.7.2, the diagnostic assistant can use these notifications to locate those uses of the static resource.</span></span>

<span data-ttu-id="75ebc-339">Oznámení je implementováno <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.StaticResourceResolved?displayProperty=nameWithType> novou událostí:</span><span class="sxs-lookup"><span data-stu-id="75ebc-339">The notification is implemented by the new <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.StaticResourceResolved?displayProperty=nameWithType> event:</span></span>

```csharp
public static event EventHandler<StaticResourceResolvedEventArgs> StaticResourceResolved;
```

```vb
Public Shared Event StaticResourceResolved As EventHandler(Of StaticResourceResolvedEventArgs)
```

<span data-ttu-id="75ebc-340">Tato událost je vyvolána vždy, když runtime řeší odkaz [StaticResource.](../wpf/advanced/staticresource-markup-extension.md)</span><span class="sxs-lookup"><span data-stu-id="75ebc-340">This event is raised whenever the runtime resolves a [StaticResource](../wpf/advanced/staticresource-markup-extension.md) reference.</span></span><span data-ttu-id="75ebc-341">Argumenty <xref:System.Windows.Diagnostics.StaticResourceResolvedEventArgs> popisují řešení a označují objekt a vlastnost, které jsou <xref:Windows.UI.Xaml.ResourceDictionary> hostitelem [staticresource](../wpf/advanced/staticresource-markup-extension.md) odkaz a a klíč použitý pro řešení:</span><span class="sxs-lookup"><span data-stu-id="75ebc-341"> The <xref:System.Windows.Diagnostics.StaticResourceResolvedEventArgs> arguments describe the resolution, and indicate the object and property that host the [StaticResource](../wpf/advanced/staticresource-markup-extension.md) reference and the <xref:Windows.UI.Xaml.ResourceDictionary> and key used for the resolution:</span></span>

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

<span data-ttu-id="75ebc-342">Událost není vyvolána (a `add` jeho přistupující ho je ignorován), pokud <xref:System.Windows.Diagnostics.VisualDiagnostics> není povolena a [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  je nastavena proměnná prostředí.</span><span class="sxs-lookup"><span data-stu-id="75ebc-342">The event is not raised (and its `add` accessor is ignored) unless <xref:System.Windows.Diagnostics.VisualDiagnostics> is enabled and the [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) environment variable is set.</span></span>

#### <a name="clickonce"></a><span data-ttu-id="75ebc-343">ClickOnce</span><span class="sxs-lookup"><span data-stu-id="75ebc-343">ClickOnce</span></span>

<span data-ttu-id="75ebc-344">Aplikace podporující HDPI pro Windows Forms, Windows Presentation Foundation (WPF) a Visual Studio Tools for Office (VSTO) lze nasadit pomocí ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="75ebc-344">HDPI-aware applications for Windows Forms, Windows Presentation Foundation (WPF), and Visual Studio Tools for Office (VSTO) can all be deployed by using ClickOnce.</span></span> <span data-ttu-id="75ebc-345">Pokud je v manifestu aplikace nalezena následující položka, nasazení bude úspěšné v rámci rozhraní .NET Framework 4.7.2:</span><span class="sxs-lookup"><span data-stu-id="75ebc-345">If the following entry is found in the application manifest, deployment will succeed under .NET Framework 4.7.2:</span></span>

```xml
<windowsSettings>
   <dpiAware xmlns="http://schemas.microsoft.com/SMI/2005/WindowsSettings">true</dpiAware>
</windowsSettings>
```

<span data-ttu-id="75ebc-346">Pro aplikaci Windows Forms předchozí řešení nastavení povědomí O DPI v konfiguračním souboru aplikace, nikoli manifest u aplikace již není nutné pro nasazení ClickOnce úspěšné.</span><span class="sxs-lookup"><span data-stu-id="75ebc-346">For Windows Forms application, the previous workaround of setting DPI awareness in the application configuration file rather than the application manifest is no longer necessary for ClickOnce deployment to succeed.</span></span>

<a name="v471" />

## <a name="whats-new-in-net-framework-471"></a><span data-ttu-id="75ebc-347">Co je nového v rozhraní .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="75ebc-347">What's new in .NET Framework 4.7.1</span></span>

<span data-ttu-id="75ebc-348">Rozhraní .NET Framework 4.7.1 obsahuje nové funkce v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="75ebc-348">.NET Framework 4.7.1 includes new features in the following areas:</span></span>

- [<span data-ttu-id="75ebc-349">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="75ebc-349">Base classes</span></span>](#core471)
- [<span data-ttu-id="75ebc-350">Běžný jazyk runtime (CLR)</span><span class="sxs-lookup"><span data-stu-id="75ebc-350">Common language runtime (CLR)</span></span>](#clr)
- [<span data-ttu-id="75ebc-351">Sítě</span><span class="sxs-lookup"><span data-stu-id="75ebc-351">Networking</span></span>](#net471)
- [<span data-ttu-id="75ebc-352">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="75ebc-352">ASP.NET</span></span>](#asp-net471)

<span data-ttu-id="75ebc-353">Kromě toho hlavní zaměření v rozhraní .NET Framework 4.7.1 je lepší přístupnost, která umožňuje aplikaci poskytovat odpovídající prostředí pro uživatele asistenční technologie.</span><span class="sxs-lookup"><span data-stu-id="75ebc-353">In addition, a major focus in .NET Framework 4.7.1 is improved accessibility, which allows an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="75ebc-354">Informace o vylepšení usnadnění v rozhraní .NET Framework 4.7.1 naleznete [v tématu Co je nového v usnadnění přístupnosti v rozhraní .NET Framework](whats-new-in-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-354">For information on accessibility improvements in .NET Framework 4.7.1, see [What's new in accessibility in the .NET Framework](whats-new-in-accessibility.md).</span></span>

<a name="core471" />

#### <a name="base-classes"></a><span data-ttu-id="75ebc-355">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="75ebc-355">Base classes</span></span>

<span data-ttu-id="75ebc-356">**Podpora pro standard .NET 2.0**</span><span class="sxs-lookup"><span data-stu-id="75ebc-356">**Support for .NET Standard 2.0**</span></span>

<span data-ttu-id="75ebc-357">[Standard .NET](../../standard/net-standard.md) definuje sadu rozhraní API, která musí být k dispozici pro každou implementaci rozhraní .NET, která podporuje tuto verzi standardu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-357">[.NET Standard](../../standard/net-standard.md) defines a set of APIs that must be available on each .NET implementation that supports that version of the standard.</span></span> <span data-ttu-id="75ebc-358">Rozhraní .NET Framework 4.7.1 plně podporuje rozhraní .NET Standard 2.0 a přidává [přibližně 200 rozhraní API,](https://github.com/dotnet/standard/blob/master/src/netstandard/src/ApiCompatBaseline.net461.txt) která jsou definována v rozhraní .NET Standard 2.0 a chybí v rozhraní .NET Framework 4.6.1, 4.6.2 a 4.7.</span><span class="sxs-lookup"><span data-stu-id="75ebc-358">.NET Framework 4.7.1 fully supports .NET Standard 2.0 and adds [about 200 APIs](https://github.com/dotnet/standard/blob/master/src/netstandard/src/ApiCompatBaseline.net461.txt) that are defined in .NET Standard 2.0 and are missing from .NET Framework 4.6.1, 4.6.2, and 4.7.</span></span> <span data-ttu-id="75ebc-359">(Všimněte si, že tyto verze rozhraní .NET Framework podporují rozhraní .NET Standard 2.0 pouze v případě, že jsou v cílovém systému nasazeny také další soubory podpory standardu .NET.) Další informace naleznete v tématu "BCL - .NET Standard 2.0 Support" v blogu [.NET Framework 4.7.1 Runtime a Compiler Features.](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/)</span><span class="sxs-lookup"><span data-stu-id="75ebc-359">(Note that these versions of the .NET Framework support .NET Standard 2.0 only if additional .NET Standard support files are also deployed on the target system.) For more information, see "BCL - .NET Standard 2.0 Support" in the [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog post.</span></span>

<span data-ttu-id="75ebc-360">**Podpora pro tvůrce konfigurací**</span><span class="sxs-lookup"><span data-stu-id="75ebc-360">**Support for configuration builders**</span></span>

<span data-ttu-id="75ebc-361">Tvůrce konfigurace umožňují vývojářům injektáponovat a vytvářet nastavení konfigurace pro aplikace dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-361">Configuration builders allow developers to inject and build configuration settings for applications dynamically at run time.</span></span> <span data-ttu-id="75ebc-362">Vlastní konfigurátory konfigurace lze použít k úpravě existujících dat v konfigurační části nebo k vytvoření oddílu konfigurace zcela od začátku.</span><span class="sxs-lookup"><span data-stu-id="75ebc-362">Custom configuration builders can be used to modify existing data in a configuration section or to build a configuration section entirely from scratch.</span></span> <span data-ttu-id="75ebc-363">Bez konfigurátorů jsou soubory .config statické a jejich nastavení jsou definována někdy před spuštěním aplikace.</span><span class="sxs-lookup"><span data-stu-id="75ebc-363">Without configuration builders, .config files are static, and their settings are defined some time before an application is launched.</span></span>

<span data-ttu-id="75ebc-364">Chcete-li vytvořit vlastní tvůrce konfigurace, odvodit tvůrce z abstraktní <xref:System.Configuration.ConfigurationBuilder> třídy a přepsat jeho <xref:System.Configuration.ConfigurationBuilder.ProcessConfigurationSection%2A?displayProperty=nameWithType> a <xref:System.Configuration.ConfigurationBuilder.ProcessRawXml%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="75ebc-364">To create a custom configuration builder, you derive your builder from the abstract <xref:System.Configuration.ConfigurationBuilder> class and override its <xref:System.Configuration.ConfigurationBuilder.ProcessConfigurationSection%2A?displayProperty=nameWithType> and <xref:System.Configuration.ConfigurationBuilder.ProcessRawXml%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="75ebc-365">V souboru .config také definujete své tvůrce.</span><span class="sxs-lookup"><span data-stu-id="75ebc-365">You also define your builders in your .config file.</span></span> <span data-ttu-id="75ebc-366">Další informace naleznete v části "Konfigurační stavitelé" v příspěvku blogu [.NET Framework 4.7.1 ASP.NET a funkce konfigurace.](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/)</span><span class="sxs-lookup"><span data-stu-id="75ebc-366">For more information, see the "Configuration Builders" section in the [.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog post.</span></span>

<span data-ttu-id="75ebc-367">**Detekce funkcí za běhu**</span><span class="sxs-lookup"><span data-stu-id="75ebc-367">**Run-time feature detection**</span></span>

<span data-ttu-id="75ebc-368">Třída <xref:System.Runtime.CompilerServices.RuntimeFeature?displayProperty=nameWithType> poskytuje mechanismus pro určení, zda je předdefinovaná funkce podporována v dané implementaci rozhraní .NET v době kompilace nebo běhu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-368">The <xref:System.Runtime.CompilerServices.RuntimeFeature?displayProperty=nameWithType> class provides a mechanism for determine whether a predefined feature is supported on a given .NET implementation at compile time or run time.</span></span> <span data-ttu-id="75ebc-369">V době kompilace může kompilátor zkontrolovat, zda existuje zadané pole, aby zjistil, zda je funkce podporována; Pokud ano, může vyzařovat kód, který využívá této funkce.</span><span class="sxs-lookup"><span data-stu-id="75ebc-369">At compile time, a compiler can check whether a specified field exists to determine whether the feature is supported; if so, it can emit code that takes advantage of that feature.</span></span> <span data-ttu-id="75ebc-370">Za běhu aplikace může volat <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported%2A?displayProperty=nameWithType> metodu před vyzařováním kódu za běhu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-370">At run time, an application can call the <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported%2A?displayProperty=nameWithType> method before emitting code at runtime.</span></span> <span data-ttu-id="75ebc-371">Další informace naleznete [v tématu Přidání pomocné metody k popisu funkcí podporovaných modulem runtime](https://github.com/dotnet/corefx/issues/17116).</span><span class="sxs-lookup"><span data-stu-id="75ebc-371">For more information, see [Add helper method to describe features supported by the runtime](https://github.com/dotnet/corefx/issues/17116).</span></span>

<span data-ttu-id="75ebc-372">**Typy řazené kolekce členů hodnoty lze serializovat**</span><span class="sxs-lookup"><span data-stu-id="75ebc-372">**Value tuple types are serializable**</span></span>

<span data-ttu-id="75ebc-373">Počínaje rozhraním .NET Framework 4.7.1 <xref:System.ValueTuple?displayProperty=nameWithType> a přidruženými obecnými typy jsou označeny jako [serializovatelné](xref:System.SerializableAttribute), což umožňuje binární serializaci.</span><span class="sxs-lookup"><span data-stu-id="75ebc-373">Starting with .NET Framework 4.7.1, <xref:System.ValueTuple?displayProperty=nameWithType> and its associated generic types are marked as [Serializable](xref:System.SerializableAttribute), which allows binary serialization.</span></span> <span data-ttu-id="75ebc-374">To by mělo usnadnit migraci <xref:System.Tuple%603> typů <xref:System.Tuple%604>tuple, například a , hodnotu řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="75ebc-374">This should make migrating Tuple types, such as <xref:System.Tuple%603> and <xref:System.Tuple%604>, to value tuple types easier.</span></span> <span data-ttu-id="75ebc-375">Další informace naleznete v tématu "Kompilátor – ValueTuple je serializovatelný" v [.NET Framework 4.7.1 Runtime a compiler funkce](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blogu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-375">For more information, see "Compiler -- ValueTuple is Serializable" in the [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog post.</span></span>

<span data-ttu-id="75ebc-376">**Podpora odkazů jen pro čtení**</span><span class="sxs-lookup"><span data-stu-id="75ebc-376">**Support for read-only references**</span></span>

<span data-ttu-id="75ebc-377">Rozhraní .NET Framework 4.7.1 přidává rozhraní <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="75ebc-377">.NET Framework 4.7.1 adds the <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="75ebc-378">Tento atribut se používá kompilátory jazyka označit členy, kteří mají jen pro čtení ref návratové typy nebo parametry.</span><span class="sxs-lookup"><span data-stu-id="75ebc-378">This attribute is used by language compilers to mark members that have read-only ref return types or parameters.</span></span> <span data-ttu-id="75ebc-379">Další informace naleznete v tématu "Kompilátor -- podpora pro ReadOnlyReferences" v [.NET Framework 4.7.1 Runtime a compiler funkce](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blogu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-379">For more information, see "Compiler -- Support for ReadOnlyReferences" in the [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog post.</span></span> <span data-ttu-id="75ebc-380">Informace o vrácené hodnoty ref naleznete v [tématu ref vrácené hodnoty a ref locals (C# Guide)](../../csharp/programming-guide/classes-and-structs/ref-returns.md) a [ref vrácené hodnoty (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/ref-return-values.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-380">For information on ref return values, see [Ref return values and ref locals (C# Guide)](../../csharp/programming-guide/classes-and-structs/ref-returns.md) and [Ref return values (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/ref-return-values.md).</span></span>

<a name="clr" />

#### <a name="common-language-runtime-clr"></a><span data-ttu-id="75ebc-381">Common language runtime (CLR)</span><span class="sxs-lookup"><span data-stu-id="75ebc-381">Common language runtime (CLR)</span></span>

<span data-ttu-id="75ebc-382">**Vylepšení výkonu uvolňování paměti**</span><span class="sxs-lookup"><span data-stu-id="75ebc-382">**Garbage collection performance improvements**</span></span>

<span data-ttu-id="75ebc-383">Změny uvolňování paměti (GC) v rozhraní .NET Framework 4.7.1 zlepšit celkový výkon, zejména pro přidělení haldy velkých objektů (LOH).</span><span class="sxs-lookup"><span data-stu-id="75ebc-383">Changes to garbage collection (GC) in .NET Framework 4.7.1 improve overall performance, especially for large object heap (LOH) allocations.</span></span> <span data-ttu-id="75ebc-384">V rozhraní .NET Framework 4.7.1 samostatné zámky se používají pro malé objekty haldy (SOH) a LOH přidělení, který umožňuje přidělení LOH dojít při pozadí GC je zametání SOH.</span><span class="sxs-lookup"><span data-stu-id="75ebc-384">In .NET Framework 4.7.1, separate locks are used for small object heap (SOH) and LOH allocations, which allows LOH allocations to occur when background GC is sweeping the SOH.</span></span> <span data-ttu-id="75ebc-385">V důsledku toho aplikace, které dělají velký počet přidělení LOH by měl vidět snížení konfliktu zámek přidělení a lepší výkon.</span><span class="sxs-lookup"><span data-stu-id="75ebc-385">As a result, applications that make a large number of LOH allocations should see a reduction in allocation lock contention and improved performance.</span></span> <span data-ttu-id="75ebc-386">Další informace naleznete v části "Runtime -- GC vylepšení výkonu" v [.NET Framework 4.7.1 Runtime a compiler funkce](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blogu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-386">For more information, see the "Runtime -- GC Performance Improvements" section in the [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog post.</span></span>

<a name="net471"/>

#### <a name="networking"></a><span data-ttu-id="75ebc-387">Sítě</span><span class="sxs-lookup"><span data-stu-id="75ebc-387">Networking</span></span>

<span data-ttu-id="75ebc-388">**Sha-2 podpora message.hashAlgorithm**</span><span class="sxs-lookup"><span data-stu-id="75ebc-388">**SHA-2 support for Message.HashAlgorithm**</span></span>

<span data-ttu-id="75ebc-389">V rozhraní .NET Framework 4.7 <xref:System.Messaging.Message.HashAlgorithm%2A?displayProperty=nameWithType> a starších <xref:System.Messaging.HashAlgorithm.Md5?displayProperty=nameWithType> <xref:System.Messaging.HashAlgorithm.Sha?displayProperty=nameWithType> verzích vlastnost podporuje hodnoty a pouze.</span><span class="sxs-lookup"><span data-stu-id="75ebc-389">In .NET Framework 4.7 and earlier versions, the <xref:System.Messaging.Message.HashAlgorithm%2A?displayProperty=nameWithType> property supported values of <xref:System.Messaging.HashAlgorithm.Md5?displayProperty=nameWithType> and <xref:System.Messaging.HashAlgorithm.Sha?displayProperty=nameWithType> only.</span></span> <span data-ttu-id="75ebc-390">Počínaje rozhraním .NET Framework 4.7.1, <xref:System.Messaging.HashAlgorithm.Sha256?displayProperty=nameWithType>, <xref:System.Messaging.HashAlgorithm.Sha384?displayProperty=nameWithType>, a <xref:System.Messaging.HashAlgorithm.Sha512?displayProperty=nameWithType> jsou také podporovány.</span><span class="sxs-lookup"><span data-stu-id="75ebc-390">Starting with .NET Framework 4.7.1, <xref:System.Messaging.HashAlgorithm.Sha256?displayProperty=nameWithType>, <xref:System.Messaging.HashAlgorithm.Sha384?displayProperty=nameWithType>, and <xref:System.Messaging.HashAlgorithm.Sha512?displayProperty=nameWithType> are also supported.</span></span> <span data-ttu-id="75ebc-391">Zda je tato hodnota skutečně použita, závisí <xref:System.Messaging.Message> na službě MSMQ, protože samotná instance neprovádí žádné hodnoty, ale jednoduše předává hodnoty službě MSMQ.</span><span class="sxs-lookup"><span data-stu-id="75ebc-391">Whether this value is actually used depends on MSMQ, since the <xref:System.Messaging.Message> instance itself does no hashing but simply passes on values to MSMQ.</span></span> <span data-ttu-id="75ebc-392">Další informace naleznete v části "Podpora SHA-2 pro Message.HashAlgorithm" v [rozhraní .NET Framework 4.7.1 ASP.NET a funkce konfigurace](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blogu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-392">For more information, see the "SHA-2 support for Message.HashAlgorithm" section in the [.NET Framework 4.7.1 ASP.NET and Configuration features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog post.</span></span>

<a name="asp-net471" />

#### <a name="aspnet"></a><span data-ttu-id="75ebc-393">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="75ebc-393">ASP.NET</span></span>

<span data-ttu-id="75ebc-394">**Kroky spuštění v ASP.NET aplikacích**</span><span class="sxs-lookup"><span data-stu-id="75ebc-394">**Execution steps in ASP.NET applications**</span></span>

<span data-ttu-id="75ebc-395">ASP.NET zpracovává požadavky v předdefinovaném kanálu, který zahrnuje 23 událostí.</span><span class="sxs-lookup"><span data-stu-id="75ebc-395">ASP.NET processes requests in a predefined pipeline that includes 23 events.</span></span> <span data-ttu-id="75ebc-396">ASP.NET provede každou obslužnou rutinu události jako krok spuštění.</span><span class="sxs-lookup"><span data-stu-id="75ebc-396">ASP.NET executes each event handler as an execution step.</span></span> <span data-ttu-id="75ebc-397">Ve verzích ASP.NET až .NET Framework 4.7, ASP.NET nemůže tok kontextu spuštění z důvodu přepínání mezi nativní a spravované podprocesy.</span><span class="sxs-lookup"><span data-stu-id="75ebc-397">In versions of ASP.NET up to .NET Framework 4.7, ASP.NET can't flow the execution context due to switching between native and managed threads.</span></span> <span data-ttu-id="75ebc-398">Místo toho ASP.NET selektivně proudí pouze <xref:System.Web.HttpContext>.</span><span class="sxs-lookup"><span data-stu-id="75ebc-398">Instead, ASP.NET selectively flows only the <xref:System.Web.HttpContext>.</span></span> <span data-ttu-id="75ebc-399">Počínaje rozhraním .NET Framework 4.7.1 <xref:System.Web.HttpApplication.OnExecuteRequestStep(System.Action{System.Web.HttpContextBase,System.Action})?displayProperty=nameWithType> metoda také umožňuje modulům obnovit okolní data.</span><span class="sxs-lookup"><span data-stu-id="75ebc-399">Starting with .NET Framework 4.7.1, the <xref:System.Web.HttpApplication.OnExecuteRequestStep(System.Action{System.Web.HttpContextBase,System.Action})?displayProperty=nameWithType> method also allows modules to restore ambient data.</span></span> <span data-ttu-id="75ebc-400">Tato funkce je zaměřena na knihovny týkající se trasování, profilování, diagnostiky nebo transakcí, které se starají o tok provádění aplikace.</span><span class="sxs-lookup"><span data-stu-id="75ebc-400">This feature is targeted at libraries concerned with tracing, profiling, diagnostics, or transactions, for example, that care about the execution flow of the application.</span></span> <span data-ttu-id="75ebc-401">Další informace naleznete v příspěvku blogu "ASP.NET spuštění kroku" v [ASP.NET rozhraní .NET Framework 4.7.1 a funkce konfigurace.](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/)</span><span class="sxs-lookup"><span data-stu-id="75ebc-401">For more information, see the "ASP.NET Execution Step Feature" in the [.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog post.</span></span>

<span data-ttu-id="75ebc-402">**ASP.NET analýza httpcookie**</span><span class="sxs-lookup"><span data-stu-id="75ebc-402">**ASP.NET HttpCookie parsing**</span></span>

<span data-ttu-id="75ebc-403">Rozhraní .NET Framework 4.7.1 <xref:System.Web.HttpCookie.TryParse%2A?displayProperty=nameWithType>obsahuje novou metodu , která <xref:System.Web.HttpCookie> poskytuje standardizovaný způsob vytvoření objektu z řetězce a přesné přiřazení hodnot souborů cookie, jako je datum vypršení platnosti a cesta.</span><span class="sxs-lookup"><span data-stu-id="75ebc-403">.NET Framework 4.7.1 includes a new method, <xref:System.Web.HttpCookie.TryParse%2A?displayProperty=nameWithType>, that provides a standardized way to create an <xref:System.Web.HttpCookie> object from a string and accurately assign cookie values such as expiration date and path.</span></span> <span data-ttu-id="75ebc-404">Další informace naleznete v tématu "ASP.NET httpcookie analýzy" v [rozhraní .NET Framework 4.7.1 ASP.NET a funkce konfigurace](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blogu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-404">For more information, see "ASP.NET HttpCookie parsing" in the [.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog post.</span></span>

<span data-ttu-id="75ebc-405">**Možnosti hash SHA-2 pro přihlašovací údaje pro ověřování ASP.NET formulářů**</span><span class="sxs-lookup"><span data-stu-id="75ebc-405">**SHA-2 hash options for ASP.NET forms authentication credentials**</span></span>

<span data-ttu-id="75ebc-406">V rozhraní .NET Framework 4.7 a starších verzích ASP.NET vývojářům povolily ukládat pověření uživatelů s zahálčenými hesly v konfiguračních souborech pomocí MD5 nebo SHA1.</span><span class="sxs-lookup"><span data-stu-id="75ebc-406">In .NET Framework 4.7 and earlier versions, ASP.NET allowed developers to store user credentials with hashed passwords in configuration files using either MD5 or SHA1.</span></span> <span data-ttu-id="75ebc-407">Počínaje rozhraním .NET Framework 4.7.1 podporuje ASP.NET také nové zabezpečené možnosti hash SHA-2, jako jsou SHA256, SHA384 a SHA512.</span><span class="sxs-lookup"><span data-stu-id="75ebc-407">Starting with .NET Framework 4.7.1, ASP.NET also supports new secure SHA-2 hash options such as SHA256, SHA384, and SHA512.</span></span> <span data-ttu-id="75ebc-408">SHA1 zůstává výchozí a výchozí algoritmus hash, který není výchozí, lze definovat v konfiguračním souboru webu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-408">SHA1 remains the default, and a non-default hash algorithm can be defined in the web configuration file.</span></span> <span data-ttu-id="75ebc-409">Příklad:</span><span class="sxs-lookup"><span data-stu-id="75ebc-409">For example:</span></span>

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

## <a name="whats-new-in-net-framework-47"></a><span data-ttu-id="75ebc-410">Co je nového v rozhraní .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="75ebc-410">What's new in .NET Framework 4.7</span></span>

<span data-ttu-id="75ebc-411">Rozhraní .NET Framework 4.7 obsahuje nové funkce v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="75ebc-411">.NET Framework 4.7 includes new features in the following areas:</span></span>

- [<span data-ttu-id="75ebc-412">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="75ebc-412">Base classes</span></span>](#Core47)
- [<span data-ttu-id="75ebc-413">Sítě</span><span class="sxs-lookup"><span data-stu-id="75ebc-413">Networking</span></span>](#net47)
- [<span data-ttu-id="75ebc-414">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="75ebc-414">ASP.NET</span></span>](#ASP-NET47)
- [<span data-ttu-id="75ebc-415">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="75ebc-415">Windows Communication Foundation (WCF)</span></span>](#wcf47)
- [<span data-ttu-id="75ebc-416">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="75ebc-416">Windows Forms</span></span>](#wf47)
- [<span data-ttu-id="75ebc-417">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="75ebc-417">Windows Presentation Foundation (WPF)</span></span>](#WPF47)

<span data-ttu-id="75ebc-418">Seznam nových rozhraní API přidaných do rozhraní .NET Framework 4.7 najdete v [tématu .NET Framework 4.7 API Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md) on GitHub.</span><span class="sxs-lookup"><span data-stu-id="75ebc-418">For a list of new APIs added to .NET Framework 4.7, see [.NET Framework 4.7 API Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md) on GitHub.</span></span> <span data-ttu-id="75ebc-419">Seznam vylepšení funkcí a oprav chyb v rozhraní .NET Framework 4.7 najdete v [tématu .NET Framework 4.7 Seznam změn](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-419">For a list of feature improvements and bug fixes in .NET Framework 4.7, see [.NET Framework 4.7 List of Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md) on GitHub.</span></span> <span data-ttu-id="75ebc-420">Další informace naleznete [v tématu Oznámení rozhraní .NET Framework 4.7](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-7/) v blogu .NET.</span><span class="sxs-lookup"><span data-stu-id="75ebc-420">For more information, see [Announcing the .NET Framework 4.7](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-7/) in the .NET blog.</span></span>

<a name="Core47" />

#### <a name="base-classes"></a><span data-ttu-id="75ebc-421">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="75ebc-421">Base classes</span></span>

<span data-ttu-id="75ebc-422">Rozhraní .NET Framework 4.7 vylepšuje <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>serializaci pomocí rozhraní :</span><span class="sxs-lookup"><span data-stu-id="75ebc-422">.NET Framework 4.7 improves serialization by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:</span></span>

<span data-ttu-id="75ebc-423">**Vylepšená funkce s kryptografií eliptické křivky (ECC)**\*</span><span class="sxs-lookup"><span data-stu-id="75ebc-423">**Enhanced functionality with Elliptic Curve Cryptography (ECC)**\*</span></span>

<span data-ttu-id="75ebc-424">V rozhraní .NET Framework `ImportParameters(ECParameters)` 4.7 <xref:System.Security.Cryptography.ECDsa> byly <xref:System.Security.Cryptography.ECDiffieHellman> do tříd a třídy přidány metody, které umožňují, aby objekt představoval již zavedený klíč.</span><span class="sxs-lookup"><span data-stu-id="75ebc-424">In .NET Framework 4.7, `ImportParameters(ECParameters)` methods were added to the <xref:System.Security.Cryptography.ECDsa> and <xref:System.Security.Cryptography.ECDiffieHellman> classes to allow for an object to represent an already-established key.</span></span> <span data-ttu-id="75ebc-425">Byla `ExportParameters(Boolean)` také přidána metoda pro export klíče pomocí explicitních parametrů křivky.</span><span class="sxs-lookup"><span data-stu-id="75ebc-425">An `ExportParameters(Boolean)` method was also added for exporting the key using explicit curve parameters.</span></span>

<span data-ttu-id="75ebc-426">Rozhraní .NET Framework 4.7 také přidává podporu pro další křivky (včetně sady brainpoolových křivek) <xref:System.Security.Cryptography.ECDsa.Create%2A> a <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> přidal předdefinované definice pro snadné vytváření prostřednictvím nových a výrobních metod.</span><span class="sxs-lookup"><span data-stu-id="75ebc-426">.NET Framework 4.7 also adds support for additional curves (including the Brainpool curve suite), and has added predefined definitions for ease-of-creation through the new <xref:System.Security.Cryptography.ECDsa.Create%2A> and <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> factory methods.</span></span>

<span data-ttu-id="75ebc-427">Můžete vidět [příklad vylepšení kryptografie rozhraní .NET Framework 4.7](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-427">You can see an [example of .NET Framework 4.7 cryptography improvements](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e) on GitHub.</span></span>

<span data-ttu-id="75ebc-428">**Lepší podpora řídicích znaků pomocí datacontractjsonserializer**</span><span class="sxs-lookup"><span data-stu-id="75ebc-428">**Better support for control characters by the DataContractJsonSerializer**</span></span>

<span data-ttu-id="75ebc-429">V rozhraní .NET Framework <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 4.7 třída serializuje řídicí znaky v souladu se standardem ECMAScript 6.</span><span class="sxs-lookup"><span data-stu-id="75ebc-429">In .NET Framework 4.7, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> class serializes control characters in conformity with the ECMAScript 6 standard.</span></span> <span data-ttu-id="75ebc-430">Toto chování je ve výchozím nastavení povoleno pro aplikace, které cílí na rozhraní .NET Framework 4.7, a je funkcí pro přihlášení pro aplikace, které jsou spuštěny v rámci rozhraní .NET Framework 4.7, ale zaměřují se na předchozí verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="75ebc-430">This behavior is enabled by default for applications that target .NET Framework 4.7, and is an opt-in feature for applications that are running under .NET Framework 4.7 but target a previous version of .NET Framework.</span></span> <span data-ttu-id="75ebc-431">Další informace naleznete v části [Kompatibilita aplikací.](../migration-guide/application-compatibility.md)</span><span class="sxs-lookup"><span data-stu-id="75ebc-431">For more information, see the [Application compatibility](../migration-guide/application-compatibility.md) section.</span></span>

<a name="net47" />

#### <a name="networking"></a><span data-ttu-id="75ebc-432">Sítě</span><span class="sxs-lookup"><span data-stu-id="75ebc-432">Networking</span></span>

<span data-ttu-id="75ebc-433">Rozhraní .NET Framework 4.7 přidává následující funkci související se sítí:</span><span class="sxs-lookup"><span data-stu-id="75ebc-433">.NET Framework 4.7 adds the following network-related feature:</span></span>

<span data-ttu-id="75ebc-434">**Výchozí podpora operačního systému pro protokoly TLS**\*</span><span class="sxs-lookup"><span data-stu-id="75ebc-434">**Default operating system support for TLS protocols**\*</span></span>

<span data-ttu-id="75ebc-435">Zásobník TLS, který je <xref:System.Net.Security.SslStream?displayProperty=nameWithType> používán a up-stack komponenty, jako je NAPŘÍKLAD HTTP, FTP a SMTP, umožňuje vývojářům používat výchozí protokoly TLS podporované operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="75ebc-435">The TLS stack, which is used by <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and up-stack components such as HTTP, FTP, and SMTP, allows developers to use the default TLS protocols supported by the operating system.</span></span> <span data-ttu-id="75ebc-436">Vývojáři již nemusí pevně kódovat verzi TLS.</span><span class="sxs-lookup"><span data-stu-id="75ebc-436">Developers need no longer hard-code a TLS version.</span></span>

<a name="ASP-NET47" />

#### <a name="aspnet"></a><span data-ttu-id="75ebc-437">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="75ebc-437">ASP.NET</span></span>

<span data-ttu-id="75ebc-438">V rozhraní .NET Framework 4.7 obsahuje ASP.NET následující nové funkce:</span><span class="sxs-lookup"><span data-stu-id="75ebc-438">In .NET Framework 4.7, ASP.NET includes the following new features:</span></span>

<span data-ttu-id="75ebc-439">**Rozšiřitelnost mezipaměti objektů**</span><span class="sxs-lookup"><span data-stu-id="75ebc-439">**Object Cache Extensibility**</span></span>

<span data-ttu-id="75ebc-440">Počínaje rozhraním .NET Framework 4.7 přidá ASP.NET novou sadu rozhraní API, která vývojářům umožňují nahradit výchozí ASP.NET implementace pro ukládání objektů v paměti do mezipaměti a monitorování paměti.</span><span class="sxs-lookup"><span data-stu-id="75ebc-440">Starting with .NET Framework 4.7, ASP.NET adds a new set of APIs that allow developers to replace the default ASP.NET implementations for in-memory object caching and memory monitoring.</span></span> <span data-ttu-id="75ebc-441">Vývojáři nyní mohou nahradit některou z následujících tří součástí, pokud ASP.NET implementace není dostatečná:</span><span class="sxs-lookup"><span data-stu-id="75ebc-441">Developers can now replace any of the following three components if the ASP.NET implementation is not adequate:</span></span>

- <span data-ttu-id="75ebc-442">**Úložiště mezipaměti objektů**.</span><span class="sxs-lookup"><span data-stu-id="75ebc-442">**Object Cache Store**.</span></span> <span data-ttu-id="75ebc-443">Pomocí nové části konfigurace zprostředkovatelů mezipaměti mohou vývojáři připojit nové implementace mezipaměti objektů pro ASP.NET aplikaci pomocí nového rozhraní **ICacheStoreProvider.**</span><span class="sxs-lookup"><span data-stu-id="75ebc-443">By using the new cache providers configuration section, developers can plug in new implementations of an object cache for an ASP.NET application by using the new **ICacheStoreProvider** interface.</span></span>

- <span data-ttu-id="75ebc-444">**Monitorování paměti**.</span><span class="sxs-lookup"><span data-stu-id="75ebc-444">**Memory monitoring**.</span></span> <span data-ttu-id="75ebc-445">Výchozí monitorování paměti v ASP.NET upozorní aplikace, když jsou spuštěny v blízkosti nakonfigurované hospodařilo limit u soukromých bajtů pro proces, nebo když je počítač nedostatek celkové dostupné fyzické paměti RAM.</span><span class="sxs-lookup"><span data-stu-id="75ebc-445">The default memory monitor in ASP.NET notifies applications when they are running close to the configured private bytes limit for the process, or when the machine is low on total available physical RAM.</span></span> <span data-ttu-id="75ebc-446">Pokud jsou tato omezení blízko, oznámení jsou aktivována.</span><span class="sxs-lookup"><span data-stu-id="75ebc-446">When these limits are near, notifications are fired.</span></span> <span data-ttu-id="75ebc-447">U některých aplikací jsou oznámení aktivována příliš blízko nakonfigurovaných limitů, aby bylo možné užitečné reakce.</span><span class="sxs-lookup"><span data-stu-id="75ebc-447">For some applications, notifications are fired too close to the configured limits to allow for useful reactions.</span></span> <span data-ttu-id="75ebc-448">Vývojáři nyní mohou psát vlastní monitory paměti <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=nameWithType> nahradit výchozí pomocí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="75ebc-448">Developers can now write their own memory monitors to replace the default by using the <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=nameWithType> property.</span></span>

- <span data-ttu-id="75ebc-449">**Reakce limitu paměti**.</span><span class="sxs-lookup"><span data-stu-id="75ebc-449">**Memory Limit Reactions**.</span></span> <span data-ttu-id="75ebc-450">Ve výchozím nastavení ASP.NET pokusí oříznout mezipaměť <xref:System.GC.Collect%2A?displayProperty=nameWithType> objektů a pravidelně volat, když je blízko limitu soukromého bajtového procesu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-450">By default, ASP.NET attempts to trim the object cache and periodically call <xref:System.GC.Collect%2A?displayProperty=nameWithType> when the private byte process limit is near.</span></span> <span data-ttu-id="75ebc-451">U některých aplikací jsou <xref:System.GC.Collect%2A?displayProperty=nameWithType> neefektivní četnost volání nebo množství mezipaměti, která je oříznuta.</span><span class="sxs-lookup"><span data-stu-id="75ebc-451">For some applications, the frequency of calls to <xref:System.GC.Collect%2A?displayProperty=nameWithType> or the amount of cache that is trimmed are inefficient.</span></span> <span data-ttu-id="75ebc-452">Vývojáři nyní můžete nahradit nebo doplnit výchozí chování přihlášením **iObserver** implementace na monitoru paměti aplikace.</span><span class="sxs-lookup"><span data-stu-id="75ebc-452">Developers can now replace or supplement the default behavior by subscribing **IObserver** implementations to the application's memory monitor.</span></span>

<a name="wcf47" />

#### <a name="windows-communication-foundation-wcf"></a><span data-ttu-id="75ebc-453">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="75ebc-453">Windows Communication Foundation (WCF)</span></span>

<span data-ttu-id="75ebc-454">Windows Communication Foundation (WCF) přidává následující funkce a změny:</span><span class="sxs-lookup"><span data-stu-id="75ebc-454">Windows Communication Foundation (WCF) adds the following features and changes:</span></span>

<span data-ttu-id="75ebc-455">**Možnost konfigurace výchozího nastavení zabezpečení zprávy na TLS 1.1 nebo TLS 1.2**</span><span class="sxs-lookup"><span data-stu-id="75ebc-455">**Ability to configure the default message security settings to TLS 1.1 or TLS 1.2**</span></span>

<span data-ttu-id="75ebc-456">Počínaje rozhraním .NET Framework 4.7 umožňuje wcf konfigurovat tsl 1.1 nebo TLS 1.2 kromě SSL 3.0 a TSL 1.0 jako výchozí protokol zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="75ebc-456">Starting with .NET Framework 4.7, WCF allows you to configure TSL 1.1 or TLS 1.2 in addition to SSL 3.0 and TSL 1.0 as the default message security protocol.</span></span> <span data-ttu-id="75ebc-457">Toto je nastavení opt-in; Chcete-li jej povolit, musíte do konfiguračního souboru aplikace přidat následující položku:</span><span class="sxs-lookup"><span data-stu-id="75ebc-457">This is an opt-in setting; to enable it, you must add the following entry to your application configuration file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
</runtime>
```

<span data-ttu-id="75ebc-458">**Vylepšená spolehlivost aplikací WCF a serializace WCF**</span><span class="sxs-lookup"><span data-stu-id="75ebc-458">**Improved reliability of WCF applications and WCF serialization**</span></span>

<span data-ttu-id="75ebc-459">WCF obsahuje řadu změn kódu, které eliminují podmínky časování, čímž se zlepší výkon a spolehlivost možností serializace.</span><span class="sxs-lookup"><span data-stu-id="75ebc-459">WCF includes a number of code changes that eliminate race conditions, thereby improving performance and the reliability of serialization options.</span></span> <span data-ttu-id="75ebc-460">Mezi ně patří:</span><span class="sxs-lookup"><span data-stu-id="75ebc-460">These include:</span></span>

- <span data-ttu-id="75ebc-461">Lepší podpora pro míchání asynchronního a synchronního kódu při volání **SocketConnection.BeginRead** a **SocketConnection.Read**.</span><span class="sxs-lookup"><span data-stu-id="75ebc-461">Better support for mixing asynchronous and synchronous code in calls to **SocketConnection.BeginRead** and **SocketConnection.Read**.</span></span>
- <span data-ttu-id="75ebc-462">Vylepšená spolehlivost při přerušení připojení s **SharedConnectionListener** a **DuplexChannelBinder**.</span><span class="sxs-lookup"><span data-stu-id="75ebc-462">Improved reliability when aborting a connection with **SharedConnectionListener** and **DuplexChannelBinder**.</span></span>
- <span data-ttu-id="75ebc-463">Vylepšená spolehlivost operací serializace <xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=nameWithType> při volání metody.</span><span class="sxs-lookup"><span data-stu-id="75ebc-463">Improved reliability of serialization operations when calling the <xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=nameWithType> method.</span></span>
- <span data-ttu-id="75ebc-464">Lepší spolehlivost při odebírání číšníka voláním **ChannelSynchronizer.RemoveWaiter** metoda.</span><span class="sxs-lookup"><span data-stu-id="75ebc-464">Improved reliability when removing a waiter by calling the **ChannelSynchronizer.RemoveWaiter** method.</span></span>

<a name="wf47" />

#### <a name="windows-forms"></a><span data-ttu-id="75ebc-465">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="75ebc-465">Windows Forms</span></span>

<span data-ttu-id="75ebc-466">V rozhraní .NET Framework 4.7 windows forms zlepšuje podporu pro monitorování s vysokým obsahem DPI.</span><span class="sxs-lookup"><span data-stu-id="75ebc-466">In .NET Framework 4.7, Windows Forms improves support for high DPI monitors.</span></span>

<span data-ttu-id="75ebc-467">**Vysoká podpora DPI**</span><span class="sxs-lookup"><span data-stu-id="75ebc-467">**High DPI support**</span></span>

<span data-ttu-id="75ebc-468">Počínaje aplikacemi, které cílí na rozhraní .NET Framework 4.7, nabízí rozhraní .NET Framework vysokou podporu DPI a dynamickou podporu DPI pro aplikace Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="75ebc-468">Starting with applications that target .NET Framework 4.7, the .NET Framework features high DPI and dynamic DPI support for Windows Forms applications.</span></span> <span data-ttu-id="75ebc-469">Vysoká podpora DPI zlepšuje rozložení a vzhled formulářů a ovládacích prvků na monitorech s vysokým obsahem DPI.</span><span class="sxs-lookup"><span data-stu-id="75ebc-469">High DPI support improves the layout and appearance of forms and controls on high DPI monitors.</span></span> <span data-ttu-id="75ebc-470">Dynamické DPI změní rozložení a vzhled formulářů a ovládacích prvků, když uživatel změní faktor dpi nebo měřítko zobrazení spuštěné aplikace.</span><span class="sxs-lookup"><span data-stu-id="75ebc-470">Dynamic DPI changes the layout and appearance of forms and controls when the user changes the DPI or display scale factor of a running application.</span></span>

<span data-ttu-id="75ebc-471">Vysoká podpora DPI je funkce přihlášení, kterou nakonfigurujete definováním oddílu [ \<System.Windows.Forms.ConfigurationSection>](../configure-apps/file-schema/winforms/index.md) v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="75ebc-471">High DPI support is an opt-in feature that you configure by defining a [\<System.Windows.Forms.ConfigurationSection>](../configure-apps/file-schema/winforms/index.md) section in your application configuration file.</span></span> <span data-ttu-id="75ebc-472">Další informace o přidání vysoké podpory DPI a dynamické podpory DPI do aplikace Windows Forms naleznete [v tématu Vysoká podpora DPI ve Windows Forms](../winforms/high-dpi-support-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-472">For more information on adding high DPI support and dynamic DPI support to your Windows Forms application, see [High DPI Support in Windows Forms](../winforms/high-dpi-support-in-windows-forms.md).</span></span>

<a name="WPF47" />

#### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="75ebc-473">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="75ebc-473">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="75ebc-474">V rozhraní .NET Framework 4.7 obsahuje wpf následující vylepšení:</span><span class="sxs-lookup"><span data-stu-id="75ebc-474">In .NET Framework 4.7, WPF includes the following enhancements:</span></span>

<span data-ttu-id="75ebc-475">**Podpora balíčku dotykového stylu založeného na zprávách WM_POINTER Windows**</span><span class="sxs-lookup"><span data-stu-id="75ebc-475">**Support for a touch/stylus stack based on Windows WM_POINTER messages**</span></span>

<span data-ttu-id="75ebc-476">Nyní máte možnost použít balíček dotykového pera založený na [WM_POINTER zpráv](https://docs.microsoft.com/previous-versions/windows/desktop/InputMsg/messages) namísto platformy WISP (Windows Ink Services Platform).</span><span class="sxs-lookup"><span data-stu-id="75ebc-476">You now have the option of using a touch/stylus stack based on [WM_POINTER messages](https://docs.microsoft.com/previous-versions/windows/desktop/InputMsg/messages) instead of the Windows Ink Services Platform (WISP).</span></span> <span data-ttu-id="75ebc-477">Toto je funkce opt-in v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="75ebc-477">This is an opt-in feature in .NET Framework.</span></span> <span data-ttu-id="75ebc-478">Další informace naleznete v části [Kompatibilita aplikací.](../migration-guide/application-compatibility.md)</span><span class="sxs-lookup"><span data-stu-id="75ebc-478">For more information, see the [Application compatibility](../migration-guide/application-compatibility.md) section.</span></span>

<span data-ttu-id="75ebc-479">**Nová implementace pro wpf tisková API**</span><span class="sxs-lookup"><span data-stu-id="75ebc-479">**New implementation for WPF printing APIs**</span></span>

<span data-ttu-id="75ebc-480">Rozhraní API pro tisk wpf ve <xref:System.Printing.PrintQueue?displayProperty=nameWithType> třídě volání rozhraní API balíčku [tiskových dokumentů](/windows/desktop/printdocs/tailored-app-printing-api) systému Windows namísto zastaralé rozhraní [XPS Print API](/windows/desktop/printdocs/xps-printing).</span><span class="sxs-lookup"><span data-stu-id="75ebc-480">WPF's printing APIs in the <xref:System.Printing.PrintQueue?displayProperty=nameWithType> class call the Windows [Print Document Package API](/windows/desktop/printdocs/tailored-app-printing-api) instead of the deprecated [XPS Print API](/windows/desktop/printdocs/xps-printing).</span></span> <span data-ttu-id="75ebc-481">Dopad této změny na kompatibilitu aplikací naleznete v části [Kompatibilita aplikací.](../migration-guide/application-compatibility.md)</span><span class="sxs-lookup"><span data-stu-id="75ebc-481">For the impact of this change on application compatibility, see the [Application compatibility](../migration-guide/application-compatibility.md) section.</span></span>

<a name="v462" />

## <a name="whats-new-in-net-framework-462"></a><span data-ttu-id="75ebc-482">Co je nového v rozhraní .NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="75ebc-482">What's new in .NET Framework 4.6.2</span></span>

<span data-ttu-id="75ebc-483">Rozhraní .NET Framework 4.6.2 obsahuje nové funkce v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="75ebc-483">The .NET Framework 4.6.2 includes new features in the following areas:</span></span>

- [<span data-ttu-id="75ebc-484">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="75ebc-484">ASP.NET</span></span>](#ASPNET462)

- [<span data-ttu-id="75ebc-485">Kategorie znaků</span><span class="sxs-lookup"><span data-stu-id="75ebc-485">Character categories</span></span>](#Strings)

- [<span data-ttu-id="75ebc-486">Kryptografie</span><span class="sxs-lookup"><span data-stu-id="75ebc-486">Cryptography</span></span>](#Crypto462)

- [<span data-ttu-id="75ebc-487">Sqlclient</span><span class="sxs-lookup"><span data-stu-id="75ebc-487">SqlClient</span></span>](#SQLClient)

- [<span data-ttu-id="75ebc-488">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="75ebc-488">Windows Communication Foundation</span></span>](#WCF)

- [<span data-ttu-id="75ebc-489">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="75ebc-489">Windows Presentation Foundation (WPF)</span></span>](#WPF462)

- [<span data-ttu-id="75ebc-490">Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="75ebc-490">Windows Workflow Foundation (WF)</span></span>](#WF462)

- [<span data-ttu-id="75ebc-491">ClickOnce</span><span class="sxs-lookup"><span data-stu-id="75ebc-491">ClickOnce</span></span>](#clickonce-1)

- [<span data-ttu-id="75ebc-492">Převod formulářů pro Windows a aplikací WPF na aplikace UPW</span><span class="sxs-lookup"><span data-stu-id="75ebc-492">Converting Windows Forms and WPF apps to UWP apps</span></span>](#UWPConvert)

- [<span data-ttu-id="75ebc-493">Vylepšení ladění</span><span class="sxs-lookup"><span data-stu-id="75ebc-493">Debugging improvements</span></span>](#Debug462)

<span data-ttu-id="75ebc-494">Seznam nových rozhraní API přidaných do rozhraní .NET Framework 4.6.2 najdete v [tématu .NET Framework 4.6.2 API Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-494">For a list of new APIs added to .NET Framework 4.6.2, see [.NET Framework 4.6.2 API Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) on GitHub.</span></span> <span data-ttu-id="75ebc-495">Seznam vylepšení funkcí a oprav chyb v rozhraní .NET Framework 4.6.2 najdete v [tématu .NET Framework 4.6.2 Seznam změn](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-changes.md) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-495">For a list of feature improvements and bug fixes in .NET Framework 4.6.2, see [.NET Framework 4.6.2 List of Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-changes.md) on GitHub.</span></span> <span data-ttu-id="75ebc-496">Další informace naleznete [v tématu Oznámení rozhraní .NET Framework 4.6.2](https://devblogs.microsoft.com/dotnet/announcing-net-framework-4-6-2/) v blogu .NET.</span><span class="sxs-lookup"><span data-stu-id="75ebc-496">For more information, see [Announcing .NET Framework 4.6.2](https://devblogs.microsoft.com/dotnet/announcing-net-framework-4-6-2/) in the .NET blog.</span></span>

<a name="ASPNET462" />

### <a name="aspnet"></a><span data-ttu-id="75ebc-497">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="75ebc-497">ASP.NET</span></span>

<span data-ttu-id="75ebc-498">V rozhraní .NET Framework 4.6.2 obsahuje ASP.NET následující vylepšení:</span><span class="sxs-lookup"><span data-stu-id="75ebc-498">In the .NET Framework 4.6.2, ASP.NET includes the following enhancements:</span></span>

<span data-ttu-id="75ebc-499">**Vylepšená podpora lokalizovaných chybových zpráv v validátorech anotací dat**</span><span class="sxs-lookup"><span data-stu-id="75ebc-499">**Improved support for localized error messages in data annotation validators**</span></span>

<span data-ttu-id="75ebc-500">Validátory anotace umožňují provést ověření přidáním jednoho nebo více atributů do vlastnosti třídy.</span><span class="sxs-lookup"><span data-stu-id="75ebc-500">Data annotation validators enable you to perform validation by adding one or more attributes to a class property.</span></span> <span data-ttu-id="75ebc-501">Prvek atributu <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> definuje text chybové zprávy, pokud se ověření nezdaří.</span><span class="sxs-lookup"><span data-stu-id="75ebc-501">The attribute's <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> element defines the text of the error message if validation fails.</span></span> <span data-ttu-id="75ebc-502">Počínaje rozhraním .NET Framework 4.6.2 ASP.NET usnadňuje lokalizaci chybových zpráv.</span><span class="sxs-lookup"><span data-stu-id="75ebc-502">Starting with the .NET Framework 4.6.2, ASP.NET makes it easy to localize error messages.</span></span> <span data-ttu-id="75ebc-503">Chybové zprávy budou lokalizovány, pokud:</span><span class="sxs-lookup"><span data-stu-id="75ebc-503">Error messages will be localized if:</span></span>

1. <span data-ttu-id="75ebc-504">Je <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> k dispozici v atributu ověření.</span><span class="sxs-lookup"><span data-stu-id="75ebc-504">The <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> is provided in the validation attribute.</span></span>

2. <span data-ttu-id="75ebc-505">Soubor prostředků je uložen ve složce App_LocalResources.</span><span class="sxs-lookup"><span data-stu-id="75ebc-505">The resource file is stored in the App_LocalResources folder.</span></span>

3. <span data-ttu-id="75ebc-506">Název souboru lokalizovaných prostředků má `DataAnnotation.Localization.{` *název*`}.resx`formuláře , kde *název* je název jazykové verze ve formátu *languageCode*`-`*country/regionCode* nebo *languageCode*.</span><span class="sxs-lookup"><span data-stu-id="75ebc-506">The name of the localized resources file has the form `DataAnnotation.Localization.{`*name*`}.resx`, where *name* is a culture name in the format *languageCode*`-`*country/regionCode* or *languageCode*.</span></span>

4. <span data-ttu-id="75ebc-507">Název klíče prostředku je řetězec přiřazený <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> atributu a jeho hodnota je lokalizovaná chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="75ebc-507">The key name of the resource is the string assigned to the <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> attribute,  and its value is the localized error message.</span></span>

<span data-ttu-id="75ebc-508">Například následující atribut anotace dat definuje chybovou zprávu výchozí jazykové verze pro neplatné hodnocení.</span><span class="sxs-lookup"><span data-stu-id="75ebc-508">For example, the following data annotation attribute defines the default culture's error message for an invalid rating.</span></span>

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

<span data-ttu-id="75ebc-509">Potom můžete vytvořit soubor prostředků, DataAnnotation.Localization.fr.resx, jehož klíč je řetězec chybové zprávy a jehož hodnota je lokalizovaná chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="75ebc-509">You can then create a resource file, DataAnnotation.Localization.fr.resx, whose key is the error message string and whose value is the localized error message.</span></span> <span data-ttu-id="75ebc-510">Soubor musí být nalezen `App.LocalResources` ve složce.</span><span class="sxs-lookup"><span data-stu-id="75ebc-510">The file must be found in the `App.LocalResources` folder.</span></span> <span data-ttu-id="75ebc-511">Například následující je klíč a jeho hodnota v lokalizované francouzštině (fr) chybová zpráva:</span><span class="sxs-lookup"><span data-stu-id="75ebc-511">For example, the following is the key and its value in a localized French (fr) language error message:</span></span>

| <span data-ttu-id="75ebc-512">Název</span><span class="sxs-lookup"><span data-stu-id="75ebc-512">Name</span></span>                                 | <span data-ttu-id="75ebc-513">Hodnota</span><span class="sxs-lookup"><span data-stu-id="75ebc-513">Value</span></span>                                     |
| ------------------------------------ | ----------------------------------------- |
| <span data-ttu-id="75ebc-514">Hodnocení musí být mezi 1 a 10.</span><span class="sxs-lookup"><span data-stu-id="75ebc-514">The rating must be between 1 and 10.</span></span> | <span data-ttu-id="75ebc-515">La note doit être tvoří entre 1 et 10.</span><span class="sxs-lookup"><span data-stu-id="75ebc-515">La note doit être comprise entre 1 et 10.</span></span> |

 <span data-ttu-id="75ebc-516">Kromě toho je lokalizace anotace dat rozšiřitelná.</span><span class="sxs-lookup"><span data-stu-id="75ebc-516">In addition, data annotation localization is extensible.</span></span> <span data-ttu-id="75ebc-517">Vývojáři mohou připojit své vlastní zprostředkovatele <xref:System.Web.Globalization.IStringLocalizerProvider> lokalizátoru řetězce implementací rozhraní pro uložení lokalizačního řetězce někde jinde než v souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="75ebc-517">Developers can plug in their own string localizer provider by implementing the <xref:System.Web.Globalization.IStringLocalizerProvider> interface to store localization string somewhere other than in a resource file.</span></span>

 <span data-ttu-id="75ebc-518">**Asynchronní podpora s poskytovateli úložiště stavu relace**</span><span class="sxs-lookup"><span data-stu-id="75ebc-518">**Async support with session-state store providers**</span></span>

 <span data-ttu-id="75ebc-519">ASP.NET nyní umožňuje metody vrácení úloh, které mají být použity s poskytovateli úložiště stavu relace, což umožňuje ASP.NET aplikacím získat výhody škálovatelnosti asynchronní.</span><span class="sxs-lookup"><span data-stu-id="75ebc-519">ASP.NET now allows task-returning methods to be used with session-state store providers, thereby allowing ASP.NET apps to get the scalability benefits of async.</span></span> <span data-ttu-id="75ebc-520">Chcete-li podporuje asynchronní operace s poskytovateli úložiště <xref:System.Web.SessionState.ISessionStateModule?displayProperty=nameWithType>stavu relace, <xref:System.Web.IHttpModule> ASP.NET obsahuje nové rozhraní , které dědí z a umožňuje vývojářům implementovat vlastní modul stavu relace a zprostředkovatele úložiště asynchronních relací.</span><span class="sxs-lookup"><span data-stu-id="75ebc-520">To supports asynchronous operations with session state store providers, ASP.NET includes  a new interface, <xref:System.Web.SessionState.ISessionStateModule?displayProperty=nameWithType>, which inherits from <xref:System.Web.IHttpModule> and allows developers to implement their own session-state module and async session store providers.</span></span> <span data-ttu-id="75ebc-521">Rozhraní je definováno takto:</span><span class="sxs-lookup"><span data-stu-id="75ebc-521">The interface is defined as follows:</span></span>

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

 <span data-ttu-id="75ebc-522">Kromě toho <xref:System.Web.SessionState.SessionStateUtility> třída obsahuje dvě <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> nové <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A>metody a , které lze použít pro podporu asynchronních operací.</span><span class="sxs-lookup"><span data-stu-id="75ebc-522">In addition, the <xref:System.Web.SessionState.SessionStateUtility> class includes two new methods, <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> and <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A>, that can be used to support asynchronous operations.</span></span>

 <span data-ttu-id="75ebc-523">**Asynchronní podpora pro poskytovatele výstupní mezipaměti**</span><span class="sxs-lookup"><span data-stu-id="75ebc-523">**Async support for output-cache providers**</span></span>

 <span data-ttu-id="75ebc-524">Počínaje rozhraním .NET Framework 4.6.2 lze metody vracení úloh použít s poskytovateli výstupní mezipaměti k poskytování výhod škálovatelnosti asynchronní.</span><span class="sxs-lookup"><span data-stu-id="75ebc-524">Starting with the .NET Framework 4.6.2, task-returning methods can be used with output-cache providers to provide the scalability benefits of async.</span></span>  <span data-ttu-id="75ebc-525">Zprostředkovatelé, kteří implementují tyto metody snížit blokování vláken na webovém serveru a zlepšit škálovatelnost ASP.NET služby.</span><span class="sxs-lookup"><span data-stu-id="75ebc-525">Providers that implement these methods reduce thread-blocking on a web server and improve the scalability of an ASP.NET service.</span></span>

 <span data-ttu-id="75ebc-526">Pro podporu asynchronních poskytovatelů výstupní mezipaměti byla přidána následující řešení API:</span><span class="sxs-lookup"><span data-stu-id="75ebc-526">The following APIs have been added to support asynchronous output-cache providers:</span></span>

- <span data-ttu-id="75ebc-527">Třída, <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=nameWithType> která dědí <xref:System.Web.Caching.OutputCacheProvider?displayProperty=nameWithType> od a umožňuje vývojářům implementovat zprostředkovatele asynchronní výstupní mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="75ebc-527">The <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=nameWithType> class, which inherits from <xref:System.Web.Caching.OutputCacheProvider?displayProperty=nameWithType> and allows developers to implement an asynchronous output-cache provider.</span></span>

- <span data-ttu-id="75ebc-528">Třída, <xref:System.Web.Caching.OutputCacheUtility> která poskytuje pomocné metody pro konfiguraci výstupní mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="75ebc-528">The <xref:System.Web.Caching.OutputCacheUtility> class, which provides helper methods for configuring the output cache.</span></span>

- <span data-ttu-id="75ebc-529">18 nových metod <xref:System.Web.HttpCachePolicy?displayProperty=nameWithType> ve třídě.</span><span class="sxs-lookup"><span data-stu-id="75ebc-529">18 new methods in the <xref:System.Web.HttpCachePolicy?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="75ebc-530">Patří <xref:System.Web.HttpCachePolicy.GetCacheability%2A>mezi <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A> <xref:System.Web.HttpCachePolicy.GetETag%2A>ně <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A> <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A> <xref:System.Web.HttpCachePolicy.GetNoStore%2A>, <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A> <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>, <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A> <xref:System.Web.HttpCachePolicy.GetRevalidation%2A>, <xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A> <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A>, <xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A>, <xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A>, , , , , , , a .</span><span class="sxs-lookup"><span data-stu-id="75ebc-530">These include <xref:System.Web.HttpCachePolicy.GetCacheability%2A>, <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A>, <xref:System.Web.HttpCachePolicy.GetETag%2A>, <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetNoStore%2A>, <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A>, <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>, <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetRevalidation%2A>, <xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A>, <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A>, <xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A>, and <xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A>.</span></span>

- <span data-ttu-id="75ebc-531">2 nové metody <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=nameWithType> ve <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A>třídě: a .</span><span class="sxs-lookup"><span data-stu-id="75ebc-531">2 new methods in the <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=nameWithType> class:  <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> and <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A>.</span></span>

- <span data-ttu-id="75ebc-532">2 nové metody <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=nameWithType> ve <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A>třídě: a .</span><span class="sxs-lookup"><span data-stu-id="75ebc-532">2 new methods in the <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=nameWithType> class: <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> and <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A>.</span></span>

- <span data-ttu-id="75ebc-533">2 nové metody <xref:System.Web.HttpCacheVaryByParams?displayProperty=nameWithType> ve <xref:System.Web.HttpCacheVaryByParams.GetParams%2A> <xref:System.Web.HttpCacheVaryByParams.SetParams%2A>třídě: a .</span><span class="sxs-lookup"><span data-stu-id="75ebc-533">2 new methods in the <xref:System.Web.HttpCacheVaryByParams?displayProperty=nameWithType> class: <xref:System.Web.HttpCacheVaryByParams.GetParams%2A> and <xref:System.Web.HttpCacheVaryByParams.SetParams%2A>.</span></span>

- <span data-ttu-id="75ebc-534">Ve <xref:System.Web.Caching.AggregateCacheDependency?displayProperty=nameWithType> třídě <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="75ebc-534">In the <xref:System.Web.Caching.AggregateCacheDependency?displayProperty=nameWithType> class, the <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A> method.</span></span>

- <span data-ttu-id="75ebc-535">V <xref:System.Web.Caching.CacheDependency>, <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="75ebc-535">In the <xref:System.Web.Caching.CacheDependency>, the <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> method.</span></span>

<a name="Strings" />

### <a name="character-categories"></a><span data-ttu-id="75ebc-536">Kategorie znaků</span><span class="sxs-lookup"><span data-stu-id="75ebc-536">Character categories</span></span>

<span data-ttu-id="75ebc-537">Znaky v rozhraní .NET Framework 4.6.2 jsou klasifikovány na základě [standardu Unicode verze 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/).</span><span class="sxs-lookup"><span data-stu-id="75ebc-537">Characters in the .NET Framework 4.6.2 are classified based on the [Unicode Standard, Version 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/).</span></span> <span data-ttu-id="75ebc-538">V rozhraních .NET Framework 4.6 a .NET Framework 4.6.1 byly znaky klasifikovány na základě kategorií znaků Unicode 6.3.</span><span class="sxs-lookup"><span data-stu-id="75ebc-538">In .NET Framework 4.6 and .NET Framework 4.6.1, characters were classified based on Unicode 6.3 character categories.</span></span>

<span data-ttu-id="75ebc-539">Podpora unicode 8.0 je omezena na klasifikaci znaků podle <xref:System.Globalization.CharUnicodeInfo> třídy a na typy a metody, které jsou na něm závislé.</span><span class="sxs-lookup"><span data-stu-id="75ebc-539">Support for Unicode 8.0 is limited to the classification of characters by the <xref:System.Globalization.CharUnicodeInfo> class and to types and methods that rely on it.</span></span> <span data-ttu-id="75ebc-540">Patří mezi <xref:System.Globalization.StringInfo> ně třída, <xref:System.Char.GetUnicodeCategory%2A?displayProperty=nameWithType> přetížená metoda a [třídy znaků](../../standard/base-types/character-classes-in-regular-expressions.md) rozpoznané modulem regulárních výrazů rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="75ebc-540">These include the <xref:System.Globalization.StringInfo> class, the overloaded <xref:System.Char.GetUnicodeCategory%2A?displayProperty=nameWithType> method, and the [character classes](../../standard/base-types/character-classes-in-regular-expressions.md) recognized by the .NET Framework regular expression engine.</span></span>  <span data-ttu-id="75ebc-541">Porovnání a řazení znaků a řetězců není touto změnou ovlivněno a nadále se spoléhá na základní operační systém nebo v systémech Windows 7 na znaková data poskytovaná rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="75ebc-541">Character and string comparison and sorting is unaffected by this change and continues to rely on the underlying operating system or, on Windows 7 systems, on character data provided by the .NET Framework.</span></span>

<span data-ttu-id="75ebc-542">Změny v kategoriích znaků z Unicode 6.0 na Unicode 7.0 naleznete v [tématu Unicode Standard, verze 7.0.0](https://www.unicode.org/versions/Unicode7.0.0/) na webu Unicode Consortium.</span><span class="sxs-lookup"><span data-stu-id="75ebc-542">For changes in character categories from Unicode 6.0 to Unicode 7.0, see [The Unicode Standard, Version 7.0.0](https://www.unicode.org/versions/Unicode7.0.0/) at The Unicode Consortium website.</span></span> <span data-ttu-id="75ebc-543">Změny z Unicode 7.0 na Unicode 8.0 naleznete v [tématu Unicode Standard, verze 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/) na webu Unicode Consortium.</span><span class="sxs-lookup"><span data-stu-id="75ebc-543">For changes from Unicode 7.0 to Unicode 8.0, see [The Unicode Standard, Version 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/) at The Unicode Consortium website.</span></span>

<a name="Crypto462" />

### <a name="cryptography"></a><span data-ttu-id="75ebc-544">Kryptografie</span><span class="sxs-lookup"><span data-stu-id="75ebc-544">Cryptography</span></span>

<span data-ttu-id="75ebc-545">**Podpora certifikátů X509 obsahujících FIPS 186-3 DSA**</span><span class="sxs-lookup"><span data-stu-id="75ebc-545">**Support for X509 certificates containing FIPS 186-3 DSA**</span></span>

<span data-ttu-id="75ebc-546">Rozhraní .NET Framework 4.6.2 přidává podporu pro certifikáty DSA (Digital Signature Algorithm) X509, jejichž klíče překračují limit 186-2 1024 bit.</span><span class="sxs-lookup"><span data-stu-id="75ebc-546">The .NET Framework 4.6.2 adds support for DSA (Digital Signature Algorithm) X509 certificates whose keys exceed the FIPS 186-2 1024-bit limit.</span></span>

<span data-ttu-id="75ebc-547">Kromě podpory větší velikosti klíčů FIPS 186-3 umožňuje rozhraní .NET Framework 4.6.2 výpočetní podpisy s rodinou algoritmů hash SHA-2 (SHA256, SHA384 a SHA512).</span><span class="sxs-lookup"><span data-stu-id="75ebc-547">In addition to supporting the larger key sizes of FIPS 186-3, the .NET Framework 4.6.2 allows computing signatures with the SHA-2 family of hash algorithms (SHA256, SHA384, and SHA512).</span></span> <span data-ttu-id="75ebc-548">Fips 186-3 podpora je poskytována novou <xref:System.Security.Cryptography.DSACng?displayProperty=nameWithType> třídou.</span><span class="sxs-lookup"><span data-stu-id="75ebc-548">FIPS 186-3 support is provided by the new <xref:System.Security.Cryptography.DSACng?displayProperty=nameWithType> class.</span></span>

<span data-ttu-id="75ebc-549">V souladu s nedávnými změnami <xref:System.Security.Cryptography.RSA> třídy v <xref:System.Security.Cryptography.ECDsa> rozhraní .NET Framework 4.6 a <xref:System.Security.Cryptography.DSA> třídy v rozhraní .NET Framework 4.6.1 má abstraktní základní třída v rozhraní .NET Framework 4.6.2 další metody, které volajícím umožňují používat tuto funkci bez přetypování.</span><span class="sxs-lookup"><span data-stu-id="75ebc-549">In keeping with recent changes to the <xref:System.Security.Cryptography.RSA> class in .NET Framework 4.6 and the <xref:System.Security.Cryptography.ECDsa> class in .NET Framework 4.6.1, the <xref:System.Security.Cryptography.DSA> abstract base class in .NET Framework 4.6.2 has additional methods to allow callers to use this functionality without casting.</span></span> <span data-ttu-id="75ebc-550">Můžete volat <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=nameWithType> metodu rozšíření k podepsání dat, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="75ebc-550">You can call the <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=nameWithType> extension method to sign data, as the following example shows.</span></span>

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

<span data-ttu-id="75ebc-551">A můžete volat <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=nameWithType> metodu rozšíření k ověření podepsaných dat, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="75ebc-551">And you can call the <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=nameWithType> extension method to verify signed data, as the following example shows.</span></span>

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

<span data-ttu-id="75ebc-552">**Zvýšená srozumitelnost pro vstupy do rutin odvození klíčů ECDiffieHellman**</span><span class="sxs-lookup"><span data-stu-id="75ebc-552">**Increased clarity for inputs to ECDiffieHellman key derivation routines**</span></span>

<span data-ttu-id="75ebc-553">.NET Framework 3.5 přidal podporu pro dohodu elliptic Curve Diffie-Hellman Key Agreement se třemi různými rutinami funkce Odvození klíče (KDF).</span><span class="sxs-lookup"><span data-stu-id="75ebc-553">.NET Framework 3.5 added support for Elliptic Curve Diffie-Hellman Key Agreement with three different Key Derivation Function (KDF) routines.</span></span> <span data-ttu-id="75ebc-554">Vstupy do rutiny a rutiny samotné, byly konfigurovány <xref:System.Security.Cryptography.ECDiffieHellmanCng> prostřednictvím vlastností na objektu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-554">The inputs to the routines, and the routines themselves, were configured via properties on the <xref:System.Security.Cryptography.ECDiffieHellmanCng> object.</span></span> <span data-ttu-id="75ebc-555">Ale protože ne každý rutinní číst každý vstup vlastnosti, tam byl dostatečný prostor pro zmatek v minulosti developera.</span><span class="sxs-lookup"><span data-stu-id="75ebc-555">But since not every routine read every input property, there was ample room for confusion on the past of the developer.</span></span>

<span data-ttu-id="75ebc-556">Chcete-li tento problém vyřešit v rozhraní .NET Framework 4.6.2, byly přidány následující tři metody do <xref:System.Security.Cryptography.ECDiffieHellman> základní třídy jasněji reprezentovat tyto Rutiny KDF a jejich vstupy:</span><span class="sxs-lookup"><span data-stu-id="75ebc-556">To address this in the .NET Framework 4.6.2, the following three methods have been added to the  <xref:System.Security.Cryptography.ECDiffieHellman> base class to more clearly represent these KDF routines and their inputs:</span></span>

|<span data-ttu-id="75ebc-557">Metoda ECDiffieHellman</span><span class="sxs-lookup"><span data-stu-id="75ebc-557">ECDiffieHellman method</span></span>|<span data-ttu-id="75ebc-558">Popis</span><span class="sxs-lookup"><span data-stu-id="75ebc-558">Description</span></span>|
|----------------------------|-----------------|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|<span data-ttu-id="75ebc-559">Odvozuje klíčový materiál pomocí vzorce</span><span class="sxs-lookup"><span data-stu-id="75ebc-559">Derives key material using the formula</span></span><br /><br /> <span data-ttu-id="75ebc-560">HASH (secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)</span><span class="sxs-lookup"><span data-stu-id="75ebc-560">HASH(secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)</span></span><br /><br /> <span data-ttu-id="75ebc-561">HASH(secretPrepend OrElse *x* OrElse secretAppend)</span><span class="sxs-lookup"><span data-stu-id="75ebc-561">HASH(secretPrepend OrElse *x* OrElse secretAppend)</span></span><br /><br /> <span data-ttu-id="75ebc-562">kde *x* je vypočítaný výsledek algoritmu EC Diffie-Hellman.</span><span class="sxs-lookup"><span data-stu-id="75ebc-562">where *x* is the computed result of the EC Diffie-Hellman algorithm.</span></span>|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|<span data-ttu-id="75ebc-563">Odvozuje klíčový materiál pomocí vzorce</span><span class="sxs-lookup"><span data-stu-id="75ebc-563">Derives key material using the formula</span></span><br /><br /> <span data-ttu-id="75ebc-564">HMAC(hmacKey, secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)</span><span class="sxs-lookup"><span data-stu-id="75ebc-564">HMAC(hmacKey, secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)</span></span><br /><br /> <span data-ttu-id="75ebc-565">HMAC(hmacKey, secretPrepend OrElse *x* OrElse secretAppend)</span><span class="sxs-lookup"><span data-stu-id="75ebc-565">HMAC(hmacKey, secretPrepend OrElse *x* OrElse secretAppend)</span></span><br /><br /> <span data-ttu-id="75ebc-566">kde *x* je vypočítaný výsledek algoritmu EC Diffie-Hellman.</span><span class="sxs-lookup"><span data-stu-id="75ebc-566">where *x* is the computed result of the EC Diffie-Hellman algorithm.</span></span>|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|<span data-ttu-id="75ebc-567">Odvozuje klíčový materiál pomocí algoritmu odvození pseudonáhodné funkce TLS (PRF).</span><span class="sxs-lookup"><span data-stu-id="75ebc-567">Derives key material using the TLS pseudo-random function (PRF) derivation algorithm.</span></span>|

<span data-ttu-id="75ebc-568">**Podpora symetrického šifrování trvalého klíče**</span><span class="sxs-lookup"><span data-stu-id="75ebc-568">**Support for persisted-key symmetric encryption**</span></span>

<span data-ttu-id="75ebc-569">Knihovna kryptografie systému Windows (CNG) přidala podporu pro ukládání trvalých symetrických klíčů a použití hardwarově uložených symetrických klíčů a rozhraní .NET Framework 4.6.2 umožnilo vývojářům tuto funkci využívat.</span><span class="sxs-lookup"><span data-stu-id="75ebc-569">The Windows cryptography library (CNG) added support for storing persisted symmetric keys and using hardware-stored symmetric keys, and the .NET Framework 4.6.2 made it possible for developers to make use of this feature.</span></span>  <span data-ttu-id="75ebc-570">Vzhledem k tomu, že pojem názvy klíčů a zprostředkovatelé klíčů je specifické pro implementaci, použití této `Aes.Create`funkce vyžaduje využití konstruktoru konkrétní typy implementace namísto upřednostňované tovární přístup (například volání ).</span><span class="sxs-lookup"><span data-stu-id="75ebc-570">Since the notion of key names and key providers is implementation-specific, using this feature requires utilizing the constructor of the concrete implementation types instead of the preferred factory approach (such as calling `Aes.Create`).</span></span>

<span data-ttu-id="75ebc-571">Pro algoritmy AES (<xref:System.Security.Cryptography.AesCng>) a 3DES (<xref:System.Security.Cryptography.TripleDESCng>) existuje podpora symetrického šifrování s trvalým klíčem.</span><span class="sxs-lookup"><span data-stu-id="75ebc-571">Persisted-key symmetric encryption support exists for the AES (<xref:System.Security.Cryptography.AesCng>) and 3DES (<xref:System.Security.Cryptography.TripleDESCng>) algorithms.</span></span> <span data-ttu-id="75ebc-572">Příklad:</span><span class="sxs-lookup"><span data-stu-id="75ebc-572">For example:</span></span>

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

<span data-ttu-id="75ebc-573">**Podpora SignedXml pro sha-2 hashing**</span><span class="sxs-lookup"><span data-stu-id="75ebc-573">**SignedXml support for SHA-2 hashing**</span></span>

<span data-ttu-id="75ebc-574">Rozhraní .NET Framework 4.6.2 <xref:System.Security.Cryptography.Xml.SignedXml> přidává podporu do třídy pro rsa-SHA256, RSA-SHA384 a RSA-SHA512 PKCS#1 podpisové metody a SHA256, SHA384 a SHA512 referenční algoritmy digest.</span><span class="sxs-lookup"><span data-stu-id="75ebc-574">The .NET Framework 4.6.2 adds support to  the <xref:System.Security.Cryptography.Xml.SignedXml> class for RSA-SHA256, RSA-SHA384, and RSA-SHA512 PKCS#1 signature methods, and SHA256, SHA384, and SHA512 reference digest algorithms.</span></span>

<span data-ttu-id="75ebc-575">Všechny konstanty URI jsou <xref:System.Security.Cryptography.Xml.SignedXml>vystaveny na :</span><span class="sxs-lookup"><span data-stu-id="75ebc-575">The URI constants are all exposed on <xref:System.Security.Cryptography.Xml.SignedXml>:</span></span>

|<span data-ttu-id="75ebc-576">Pole SignedXml</span><span class="sxs-lookup"><span data-stu-id="75ebc-576">SignedXml field</span></span>|<span data-ttu-id="75ebc-577">Trvalé</span><span class="sxs-lookup"><span data-stu-id="75ebc-577">Constant</span></span>|
|---------------------|--------------|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url>|<span data-ttu-id="75ebc-578">"http://www.w3.org/2001/04/xmlenc#sha256"</span><span class="sxs-lookup"><span data-stu-id="75ebc-578">"http://www.w3.org/2001/04/xmlenc#sha256"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url>|<span data-ttu-id="75ebc-579">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"</span><span class="sxs-lookup"><span data-stu-id="75ebc-579">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url>|<span data-ttu-id="75ebc-580">"http://www.w3.org/2001/04/xmldsig-more#sha384"</span><span class="sxs-lookup"><span data-stu-id="75ebc-580">"http://www.w3.org/2001/04/xmldsig-more#sha384"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url>|<span data-ttu-id="75ebc-581">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"</span><span class="sxs-lookup"><span data-stu-id="75ebc-581">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url>|<span data-ttu-id="75ebc-582">"http://www.w3.org/2001/04/xmlenc#sha512"</span><span class="sxs-lookup"><span data-stu-id="75ebc-582">"http://www.w3.org/2001/04/xmlenc#sha512"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url>|<span data-ttu-id="75ebc-583">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"</span><span class="sxs-lookup"><span data-stu-id="75ebc-583">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"</span></span>|

 <span data-ttu-id="75ebc-584">Všechny programy, které <xref:System.Security.Cryptography.SignatureDescription> zaregistrovaly <xref:System.Security.Cryptography.CryptoConfig> vlastní obslužnou rutinu <xref:System.Security.Cryptography.CryptoConfig> do přidat podporu pro tyto algoritmy bude i nadále fungovat jako tomu bylo v minulosti, ale protože existují nyní výchozí platformy, registrace již není nutné.</span><span class="sxs-lookup"><span data-stu-id="75ebc-584">Any programs that have registered a custom <xref:System.Security.Cryptography.SignatureDescription> handler into <xref:System.Security.Cryptography.CryptoConfig> to add support for these algorithms will continue to function as they did in the past, but since there are now platform defaults, the <xref:System.Security.Cryptography.CryptoConfig> registration is no longer necessary.</span></span>

<a name="SQLClient" />

### <a name="sqlclient"></a><span data-ttu-id="75ebc-585">Sqlclient</span><span class="sxs-lookup"><span data-stu-id="75ebc-585">SqlClient</span></span>

<span data-ttu-id="75ebc-586">Zprostředkovatel dat rozhraní .NET<xref:System.Data.SqlClient?displayProperty=nameWithType>Framework pro SQL Server ( ) obsahuje následující nové funkce v rozhraní .NET Framework 4.6.2:</span><span class="sxs-lookup"><span data-stu-id="75ebc-586">.NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>) includes the following new features in the .NET Framework 4.6.2:</span></span>

<span data-ttu-id="75ebc-587">**Sdružování připojení a časové limity s databázemi Azure SQL**</span><span class="sxs-lookup"><span data-stu-id="75ebc-587">**Connection pooling and timeouts with Azure SQL databases**</span></span>

<span data-ttu-id="75ebc-588">Je-li povoleno sdružování připojení a dojde k vypršení časového limitu nebo jiné chybě přihlášení, je výjimka uložena do mezipaměti a výjimka uložená v mezipaměti je vyvolána při každém následném pokusu o připojení pro dalších 5 sekund až 1 minutu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-588">When connection pooling is enabled and a timeout or other login error occurs, an exception is cached, and the cached exception is thrown on any subsequent connection attempt for the next 5 seconds to 1 minute.</span></span> <span data-ttu-id="75ebc-589">Další informace naleznete v tématu [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-589">For more information, see [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span></span>

<span data-ttu-id="75ebc-590">Toto chování není žádoucí při připojování k Azure SQL Databases, protože pokusy o připojení může selhat s přechodnými chybami, které se obvykle rychle obnovují.</span><span class="sxs-lookup"><span data-stu-id="75ebc-590">This behavior is not desirable when connecting to Azure SQL Databases, since connection attempts can fail with transient errors that are typically recovered quickly.</span></span> <span data-ttu-id="75ebc-591">Chcete-li lépe optimalizovat prostředí opakování připojení, chování období blokování fondu připojení se odebere, když se nezdaří připojení k databázím Azure SQL Databases.</span><span class="sxs-lookup"><span data-stu-id="75ebc-591">To better optimize the connection retry experience, the connection pool blocking period behavior is removed when connections to Azure SQL Databases fail.</span></span>

<span data-ttu-id="75ebc-592">Přidání nového `PoolBlockingPeriod` klíčového slova umožňuje vybrat období blokování, které je pro vaši aplikaci nejvhodnější.</span><span class="sxs-lookup"><span data-stu-id="75ebc-592">The addition of the new `PoolBlockingPeriod` keyword lets you select the blocking period best suited for your app.</span></span> <span data-ttu-id="75ebc-593">Mezi tyto hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="75ebc-593">Values include:</span></span>

<xref:System.Data.SqlClient.PoolBlockingPeriod.Auto>

<span data-ttu-id="75ebc-594">Doba blokování fondu připojení pro aplikaci, která se připojuje k databázi Azure SQL, je zakázána a je povolena doba blokování fondu připojení pro aplikaci, která se připojuje k jakékoli jiné instanci serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="75ebc-594">The connection pool blocking period for an application that connects to an Azure SQL Database is disabled, and the connection pool blocking period for an application that connects to any other SQL Server instance is enabled.</span></span> <span data-ttu-id="75ebc-595">Toto je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="75ebc-595">This is the default value.</span></span> <span data-ttu-id="75ebc-596">Pokud název koncového bodu serveru končí některou z následujících, jsou považovány za Azure SQL Databases:</span><span class="sxs-lookup"><span data-stu-id="75ebc-596">If the Server endpoint name ends with any of the following, they are considered Azure SQL Databases:</span></span>

- <span data-ttu-id="75ebc-597">.database.windows.net</span><span class="sxs-lookup"><span data-stu-id="75ebc-597">.database.windows.net</span></span>

- <span data-ttu-id="75ebc-598">.database.chinacloudapi.cn</span><span class="sxs-lookup"><span data-stu-id="75ebc-598">.database.chinacloudapi.cn</span></span>

- <span data-ttu-id="75ebc-599">.database.usgovcloudapi.net</span><span class="sxs-lookup"><span data-stu-id="75ebc-599">.database.usgovcloudapi.net</span></span>

- <span data-ttu-id="75ebc-600">.database.cloudapi.de</span><span class="sxs-lookup"><span data-stu-id="75ebc-600">.database.cloudapi.de</span></span>

<xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock>

<span data-ttu-id="75ebc-601">Doba blokování fondu připojení je vždy povolena.</span><span class="sxs-lookup"><span data-stu-id="75ebc-601">The connection pool blocking period is always enabled.</span></span>

<xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock>

<span data-ttu-id="75ebc-602">Doba blokování fondu připojení je vždy zakázána.</span><span class="sxs-lookup"><span data-stu-id="75ebc-602">The connection pool blocking period is always disabled.</span></span>

<span data-ttu-id="75ebc-603">**Vylepšení pro vždy šifrované**</span><span class="sxs-lookup"><span data-stu-id="75ebc-603">**Enhancements for Always Encrypted**</span></span>

<span data-ttu-id="75ebc-604">SQLClient zavádí dvě vylepšení pro vždy šifrované:</span><span class="sxs-lookup"><span data-stu-id="75ebc-604">SQLClient introduces two enhancements for Always Encrypted:</span></span>

- <span data-ttu-id="75ebc-605">Chcete-li zlepšit výkon parametrizovaných dotazů proti šifrovaným databázovým sloupcům, jsou nyní uložena do mezipaměti metadata šifrování pro parametry dotazu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-605">To improve performance of parameterized queries against encrypted database columns, encryption metadata for query parameters is now cached.</span></span> <span data-ttu-id="75ebc-606">S <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=nameWithType> vlastností `true` nastavenou na (což je výchozí hodnota), pokud je stejný dotaz volán vícekrát, klient načte metadata parametru ze serveru pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="75ebc-606">With the <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=nameWithType> property set to `true` (which is the default value), if the same query is called multiple times, the client retrieves parameter metadata from the server only once.</span></span>

- <span data-ttu-id="75ebc-607">Položky šifrovacího klíče sloupce v mezipaměti klíčů jsou nyní <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=nameWithType> vyřazeny po konfigurovatelném časovém intervalu nastaveném pomocí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="75ebc-607">Column encryption key entries in the key cache are now evicted after a configurable time interval, set using the <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=nameWithType> property.</span></span>

<a name="WCF" />

### <a name="windows-communication-foundation"></a><span data-ttu-id="75ebc-608">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="75ebc-608">Windows Communication Foundation</span></span>

<span data-ttu-id="75ebc-609">V rozhraní .NET Framework 4.6.2 byla nadace Windows Communication Foundation vylepšena v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="75ebc-609">In the .NET Framework 4.6.2, Windows Communication Foundation has been enhanced in the following areas:</span></span>

<span data-ttu-id="75ebc-610">**WCF podpora zabezpečení přenosu pro certifikáty uložené pomocí CNG**</span><span class="sxs-lookup"><span data-stu-id="75ebc-610">**WCF transport security support for certificates stored using CNG**</span></span>

<span data-ttu-id="75ebc-611">WCF zabezpečení přenosu podporuje certifikáty uložené pomocí knihovny kryptografie systému Windows (CNG).</span><span class="sxs-lookup"><span data-stu-id="75ebc-611">WCF transport security supports certificates stored using the Windows cryptography library (CNG).</span></span> <span data-ttu-id="75ebc-612">V rozhraní .NET Framework 4.6.2 je tato podpora omezena na použití certifikátů s veřejným klíčem, který má exponent ne více než 32 bitů na délku.</span><span class="sxs-lookup"><span data-stu-id="75ebc-612">In the .NET Framework 4.6.2, this support is limited to using certificates with a public key that has an exponent no more than 32 bits in length.</span></span> <span data-ttu-id="75ebc-613">Pokud aplikace cílí na rozhraní .NET Framework 4.6.2, je tato funkce ve výchozím nastavení zapnutá.</span><span class="sxs-lookup"><span data-stu-id="75ebc-613">When an application targets the .NET Framework 4.6.2, this feature is on by default.</span></span>

<span data-ttu-id="75ebc-614">U aplikací, které cílí na rozhraní .NET Framework 4.6.1 a starší, ale jsou spuštěny v rozhraní .NET Framework 4.6.2, lze tuto funkci povolit přidáním následujícího řádku do sekce [ \<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) souboru app.config nebo web.config.</span><span class="sxs-lookup"><span data-stu-id="75ebc-614">For applications that target the .NET Framework 4.6.1 and earlier but are running on the .NET Framework 4.6.2, this feature can be enabled by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app.config or web.config file.</span></span>

```xml
<AppContextSwitchOverrides
    value="Switch.System.ServiceModel.DisableCngCertificates=false"
/>
```

<span data-ttu-id="75ebc-615">To lze také provést programově s kódem, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="75ebc-615">This can also be done programmatically with code like the following:</span></span>

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificates";
AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

<span data-ttu-id="75ebc-616">**Lepší podpora pro více pravidel úprav letního času podle třídy DataContractJsonSerializer**</span><span class="sxs-lookup"><span data-stu-id="75ebc-616">**Better support for multiple daylight saving time adjustment rules by the DataContractJsonSerializer class**</span></span>

<span data-ttu-id="75ebc-617">Zákazníci mohou pomocí nastavení konfigurace <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> aplikace určit, zda třída podporuje více pravidel úprav pro jedno časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="75ebc-617">Customers can use an application configuration setting to determine whether the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> class supports multiple adjustment rules for a single time zone.</span></span> <span data-ttu-id="75ebc-618">Jedná se o funkci opt-in.</span><span class="sxs-lookup"><span data-stu-id="75ebc-618">This is an opt-in feature.</span></span> <span data-ttu-id="75ebc-619">Chcete-li jej povolit, přidejte do souboru app.config následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="75ebc-619">To enable it, add the following setting to your app.config file:</span></span>

```xml
<runtime>
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />
</runtime>
```

<span data-ttu-id="75ebc-620">Pokud je tato funkce <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> povolena, objekt používá <xref:System.TimeZoneInfo> typ namísto <xref:System.TimeZone> typu k rekonstrukci dat data a času.</span><span class="sxs-lookup"><span data-stu-id="75ebc-620">When this feature is enabled, a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> object uses the <xref:System.TimeZoneInfo> type instead of the <xref:System.TimeZone> type to deserialize date and time data.</span></span> <span data-ttu-id="75ebc-621"><xref:System.TimeZoneInfo>podporuje více pravidel úprav, která umožňují pracovat s historickými daty časových pásem;   <xref:System.TimeZone> není.</span><span class="sxs-lookup"><span data-stu-id="75ebc-621"><xref:System.TimeZoneInfo> supports multiple adjustment rules, which makes it possible to work with historic time zone data;   <xref:System.TimeZone> does not.</span></span>

<span data-ttu-id="75ebc-622">Další informace o <xref:System.TimeZoneInfo> struktuře a úpravách časového pásma naleznete v [tématu Přehled časového pásma](../../standard/datetime/time-zone-overview.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-622">For more information on the <xref:System.TimeZoneInfo> structure and time zone adjustments, see [Time Zone Overview](../../standard/datetime/time-zone-overview.md).</span></span>

<span data-ttu-id="75ebc-623">**NetNamedPipeBinding nejlepší shoda**</span><span class="sxs-lookup"><span data-stu-id="75ebc-623">**NetNamedPipeBinding best match**</span></span>

<span data-ttu-id="75ebc-624">WCF má nové nastavení aplikace, které lze nastavit na klientských aplikacích, aby bylo zajištěno, že se vždy připojí ke službě naslouchání na identifikátoru URI, který nejlépe odpovídá tomu, který požadují.</span><span class="sxs-lookup"><span data-stu-id="75ebc-624">WCF has a new app setting that can be set on client applications to ensure they always connect to the service listening on the URI that best matches the one that they request.</span></span> <span data-ttu-id="75ebc-625">S tímto nastavením aplikace nastaveným na `false` (výchozí), je možné, že se klienti, kteří se pokoušejí <xref:System.ServiceModel.NetNamedPipeBinding> připojit ke službě naslouchající na identifikátoru URI, který je podřetězcem požadovaného identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="75ebc-625">With this app setting set to `false` (the default), it is possible for clients using <xref:System.ServiceModel.NetNamedPipeBinding> to attempt to connect to a service listening on a URI that is a substring of the requested URI.</span></span>

<span data-ttu-id="75ebc-626">Klient se například pokusí připojit ke `net.pipe://localhost/Service1`službě naslouchající v , ale jiná `net.pipe://localhost`služba v tomto počítači spuštěná s oprávněním správce naslouchá na .</span><span class="sxs-lookup"><span data-stu-id="75ebc-626">For example, a client tries to connect to a service listening at `net.pipe://localhost/Service1`, but a different service on that machine running with administrator privilege is listening at `net.pipe://localhost`.</span></span> <span data-ttu-id="75ebc-627">S tímto nastavením aplikace nastaveným na `false`, by se klient pokusil připojit k nesprávné službě.</span><span class="sxs-lookup"><span data-stu-id="75ebc-627">With this app setting set to `false`, the client would attempt to connect to the wrong service.</span></span> <span data-ttu-id="75ebc-628">Po nastavení aplikace `true`na , bude klient vždy připojit k nejlepší odpovídající služby.</span><span class="sxs-lookup"><span data-stu-id="75ebc-628">After setting the app setting to `true`, the client will always connect to the best matching service.</span></span>

> [!NOTE]
> <span data-ttu-id="75ebc-629">Klienti <xref:System.ServiceModel.NetNamedPipeBinding> pomocí najít služby založené na základní adresu služby (pokud existuje) spíše než úplnou adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-629">Clients using <xref:System.ServiceModel.NetNamedPipeBinding> find services based on the service's base address (if it exists) rather than the full endpoint address.</span></span> <span data-ttu-id="75ebc-630">Chcete-li zajistit, že toto nastavení vždy funguje, služba by měla používat jedinečnou základní adresu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-630">To ensure this setting always works the service should use a unique base address.</span></span>

<span data-ttu-id="75ebc-631">Chcete-li tuto změnu povolit, přidejte do souboru App.config nebo Web.config klientské aplikace následující nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="75ebc-631">To enable this change, add the following app setting to your client application's App.config or Web.config file:</span></span>

```xml
<configuration>
    <appSettings>
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />
    </appSettings>
</configuration>
```

<span data-ttu-id="75ebc-632">**SSL 3.0 není výchozí protokol**</span><span class="sxs-lookup"><span data-stu-id="75ebc-632">**SSL 3.0 is not a default protocol**</span></span>

<span data-ttu-id="75ebc-633">Při použití protokolu NetTcp se zabezpečením přenosu a typem pověření certifikátu již není protokol SSL 3.0 výchozím protokolem používaným pro vyjednávání zabezpečeného připojení.</span><span class="sxs-lookup"><span data-stu-id="75ebc-633">When using NetTcp with transport security and a credential type of certificate, SSL 3.0 is no longer a default protocol used for negotiating a secure connection.</span></span> <span data-ttu-id="75ebc-634">Ve většině případů by nemělo být žádné dopad na existující aplikace, protože TLS 1.0 je zahrnuta v seznamu protokolů pro NetTcp.</span><span class="sxs-lookup"><span data-stu-id="75ebc-634">In most cases, there should be no impact to existing apps, because TLS 1.0 is included in the protocol list for NetTcp.</span></span> <span data-ttu-id="75ebc-635">Všichni stávající klienti by měli být schopni vyjednat připojení pomocí alespoň TLS 1.0.</span><span class="sxs-lookup"><span data-stu-id="75ebc-635">All existing clients should be able to negotiate a connection using at least TLS 1.0.</span></span> <span data-ttu-id="75ebc-636">Pokud je vyžadováno Ssl3, použijte jeden z následujících konfiguračních mechanismů k jeho přidání do seznamu vyjednaných protokolů.</span><span class="sxs-lookup"><span data-stu-id="75ebc-636">If Ssl3 is required, use one of the following configuration mechanisms to add it to the list of negotiated protocols.</span></span>

- <span data-ttu-id="75ebc-637">Vlastnost <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="75ebc-637">The <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=nameWithType> property</span></span>

- <span data-ttu-id="75ebc-638">Vlastnost <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="75ebc-638">The <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> property</span></span>

- <span data-ttu-id="75ebc-639">Oddíl [ \<Transport>](../configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) oddílu [ \<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="75ebc-639">The [\<transport>](../configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) section of the [\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md) section</span></span>

- <span data-ttu-id="75ebc-640">Oddíl [ \<sslStreamSecurity>](../configure-apps/file-schema/wcf/sslstreamsecurity.md) oddílu [ \<customBinding>](../configure-apps/file-schema/wcf/custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="75ebc-640">The [\<sslStreamSecurity>](../configure-apps/file-schema/wcf/sslstreamsecurity.md) section of the [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md) section</span></span>

<a name="WPF462" />

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="75ebc-641">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="75ebc-641">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="75ebc-642">V rozhraní .NET Framework 4.6.2 byla nadace Windows Presentation Foundation vylepšena v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="75ebc-642">In the .NET Framework 4.6.2, Windows Presentation Foundation has been enhanced in the following areas:</span></span>

<span data-ttu-id="75ebc-643">**Řazení skupin**</span><span class="sxs-lookup"><span data-stu-id="75ebc-643">**Group sorting**</span></span>

<span data-ttu-id="75ebc-644">Aplikace, která <xref:System.Windows.Data.CollectionView> používá objekt k seskupení dat nyní můžete explicitně deklarovat, jak třídit skupiny.</span><span class="sxs-lookup"><span data-stu-id="75ebc-644">An application that uses a <xref:System.Windows.Data.CollectionView> object to group data can now explicitly declare how to  sort the groups.</span></span> <span data-ttu-id="75ebc-645">Explicitní řazení řeší problém neintuitivnířazení, ke kterému dochází, když aplikace dynamicky přidává nebo odebere skupiny nebo když změní hodnotu vlastností položky, které se účastní seskupování.</span><span class="sxs-lookup"><span data-stu-id="75ebc-645">Explicit sorting addresses the problem of non-intuitive ordering that occurs when an app dynamically adds or removes groups, or when it changes the value of item properties involved in grouping.</span></span> <span data-ttu-id="75ebc-646">Může také zlepšit výkon procesu vytváření skupiny přesunutím porovnání vlastností seskupení z druhu úplné kolekce na druh skupin.</span><span class="sxs-lookup"><span data-stu-id="75ebc-646">It can also improve the performance of the group creation process by moving comparisons of the grouping properties from the sort of the full collection to the sort of the groups.</span></span>

<span data-ttu-id="75ebc-647">Pro podporu řazení skupin, <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=nameWithType> <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=nameWithType> nové a vlastnosti popisují, jak <xref:System.ComponentModel.GroupDescription> seřadit kolekci skupin vytvořených objektem.</span><span class="sxs-lookup"><span data-stu-id="75ebc-647">To support group sorting, the new <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=nameWithType> and <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=nameWithType> properties describe how to sort the collection of groups produced by the <xref:System.ComponentModel.GroupDescription> object.</span></span> <span data-ttu-id="75ebc-648">To je obdobou způsobu, jakým <xref:System.Windows.Data.ListCollectionView> identicky pojmenované vlastnosti popisují, jak třídit datové položky.</span><span class="sxs-lookup"><span data-stu-id="75ebc-648">This is analogous to the way the identically named <xref:System.Windows.Data.ListCollectionView> properties describe how to sort the data items.</span></span>

<span data-ttu-id="75ebc-649">Dvě nové statické <xref:System.Windows.Data.PropertyGroupDescription> vlastnosti <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A>třídy a , lze použít pro nejběžnější případy.</span><span class="sxs-lookup"><span data-stu-id="75ebc-649">Two new static properties of the <xref:System.Windows.Data.PropertyGroupDescription> class,  <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> and <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A>, can be used for the most common cases.</span></span>

<span data-ttu-id="75ebc-650">Například následující XAML seskupí data podle věku, seřadí věkové skupiny ve vzestupném pořadí a seskupí položky v rámci každé věkové skupiny podle příjmení.</span><span class="sxs-lookup"><span data-stu-id="75ebc-650">For example, the following XAML groups data by age, sort the age groups in ascending order, and group the items within each age group by last name.</span></span>

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

<span data-ttu-id="75ebc-651">**Podpora dotykové klávesnice**</span><span class="sxs-lookup"><span data-stu-id="75ebc-651">**Touch keyboard support**</span></span>

<span data-ttu-id="75ebc-652">Podpora dotykové klávesnice umožňuje sledování fokusu v aplikacích WPF automatickým vyvoláním a zavřením dotykové klávesnice v systému Windows 10, když je dotykový vstup přijat ovládacím prvkem, který může přijímat textový vstup.</span><span class="sxs-lookup"><span data-stu-id="75ebc-652">Touch keyboard support enables focus tracking in WPF applications by automatically invoking and dismissing the touch Keyboard in Windows 10 when the touch input is received by a control that can take textual input.</span></span>

<span data-ttu-id="75ebc-653">V předchozích verzích rozhraní .NET Framework se aplikace WPF nemohou přihlásit do sledování fokusu bez zakázání podpory gest a gest y pro pera wpf.</span><span class="sxs-lookup"><span data-stu-id="75ebc-653">In previous versions of .NET Framework, WPF applications can't opt into the focus tracking without disabling WPF pen/touch gesture support.</span></span> <span data-ttu-id="75ebc-654">V důsledku toho wpf aplikace musí vybrat mezi plnou podporou Dotykové ovládání WPF nebo spoléhat na propagaci myši systému Windows.</span><span class="sxs-lookup"><span data-stu-id="75ebc-654">As a result, WPF applications must choose between full WPF touch support or rely on Windows mouse promotion.</span></span>

<span data-ttu-id="75ebc-655">**DPI pro jeden monitor**</span><span class="sxs-lookup"><span data-stu-id="75ebc-655">**Per-monitor DPI**</span></span>

<span data-ttu-id="75ebc-656">Pro podporu nedávného rozšíření prostředí s vysokým dpi a hybridního DPI pro aplikace WPF wpf, WPF v rozhraní .NET Framework 4.6.2 umožňuje povědomí na monitoru.</span><span class="sxs-lookup"><span data-stu-id="75ebc-656">To support the recent proliferation of high-DPI and hybrid-DPI environments for WPF apps, WPF in the .NET Framework 4.6.2 enables per-monitor awareness.</span></span> <span data-ttu-id="75ebc-657">Další informace o tom, jak povolit aplikaci WPF na monitoru DPI, najdete v [ukázkách a vývojářském průvodci](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-657">See the [samples and developer guide](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) on GitHub for more information about how to enable your WPF app to become per-monitor DPI aware.</span></span>

<span data-ttu-id="75ebc-658">V předchozích verzích rozhraní .NET Framework jsou aplikace WPF informovány o systému DPI.</span><span class="sxs-lookup"><span data-stu-id="75ebc-658">In previous versions of the .NET Framework, WPF apps are system-DPI aware.</span></span> <span data-ttu-id="75ebc-659">Jinými slovy, ujtoulovaná uontaje operačního programu podle potřeby pomocí operačního programu v závislosti na DPI monitoru, na kterém je aplikace vykreslena.</span><span class="sxs-lookup"><span data-stu-id="75ebc-659">In other words, the application's UI is scaled by the OS as appropriate, depending on the DPI of the monitor on which the app is rendered.</span></span>

<span data-ttu-id="75ebc-660">U aplikací spuštěných v rámci rozhraní .NET Framework 4.6.2 můžete zakázat změny DPI na monitorování v aplikacích WPF přidáním příkazu konfigurace do sekce [ \<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace, a to následovně:</span><span class="sxs-lookup"><span data-stu-id="75ebc-660">For apps running under the .NET Framework 4.6.2, you can disable per-monitor DPI changes in WPF apps by adding a configuration statement to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file, as follows:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Windows.DoNotScaleForDpiChanges=false"/>
</runtime>
```

<a name="WF462" />

### <a name="windows-workflow-foundation-wf"></a><span data-ttu-id="75ebc-661">Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="75ebc-661">Windows Workflow Foundation (WF)</span></span>

<span data-ttu-id="75ebc-662">V rozhraní .NET Framework 4.6.2 byla nadace Windows Workflow Foundation vylepšena v následující oblasti:</span><span class="sxs-lookup"><span data-stu-id="75ebc-662">In the .NET Framework 4.6.2, Windows Workflow Foundation has been enhanced in the following area:</span></span>

<span data-ttu-id="75ebc-663">**Podpora výrazů jazyka C# a technologie IntelliSense v návrháři služby WF s rehosted**</span><span class="sxs-lookup"><span data-stu-id="75ebc-663">**Support for C# expressions and IntelliSense in the Rehosted WF Designer**</span></span>

<span data-ttu-id="75ebc-664">Počínaje rozhraním .NET Framework 4.5 podporuje wf# výrazy v návrháři Visual Studio i v pracovních postupech kódu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-664">Starting with .NET Framework 4.5, WF supports C# expressions in both the Visual Studio Designer and in code workflows.</span></span> <span data-ttu-id="75ebc-665">Rehosted Workflow Designer je klíčovou funkcí wf, který umožňuje Návrháře pracovních postupů být v aplikaci mimo Visual Studio (například v WPF).</span><span class="sxs-lookup"><span data-stu-id="75ebc-665">The Rehosted Workflow Designer is a key feature of WF that allows for the Workflow Designer to be in an application outside Visual Studio (for example, in WPF).</span></span>  <span data-ttu-id="75ebc-666">Windows Workflow Foundation poskytuje možnost podporovat výrazy Jazyka C# a technologie IntelliSense v návrháři pracovních postupů rehosted.</span><span class="sxs-lookup"><span data-stu-id="75ebc-666">Windows Workflow Foundation provides the ability to support C# expressions and IntelliSense in the Rehosted Workflow Designer.</span></span> <span data-ttu-id="75ebc-667">Další informace naleznete v [blogu Windows Workflow Foundation](https://docs.microsoft.com/archive/blogs/workflowteam/building-c-expressions-support-and-intellisense-in-the-rehosted-workflow-designer).</span><span class="sxs-lookup"><span data-stu-id="75ebc-667">For more information, see the [Windows Workflow Foundation blog](https://docs.microsoft.com/archive/blogs/workflowteam/building-c-expressions-support-and-intellisense-in-the-rehosted-workflow-designer).</span></span>

<span data-ttu-id="75ebc-668">`Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio`Ve verzích rozhraní .NET Framework před verzí 4.6.2 je návrhář WF IntelliSense přerušen, když zákazník znovu vytvoří projekt pracovního postupu z aplikace Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="75ebc-668">`Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio` In versions of the .NET Framework prior to 4.6.2, WF Designer IntelliSense is broken when a customer rebuilds a workflow project from Visual Studio.</span></span> <span data-ttu-id="75ebc-669">Při sestavení projektu je úspěšné, typy pracovních postupů nejsou nalezeny v návrháři a upozornění z IntelliSense pro chybějící typy pracovních postupů se zobrazí v okně **Seznam chyb.**</span><span class="sxs-lookup"><span data-stu-id="75ebc-669">While the project build is successful, the workflow types are not found on the designer, and warnings from IntelliSense for the missing workflow types appear in the **Error List** window.</span></span> <span data-ttu-id="75ebc-670">Rozhraní .NET Framework 4.6.2 řeší tento problém a zpřístupňuje technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="75ebc-670">.NET Framework 4.6.2 addresses this issue and makes IntelliSense available.</span></span>

<span data-ttu-id="75ebc-671">**Aplikace Workflow V1 s funkcemi Sledování pracovního postupu jsou nyní spuštěny v režimu FIPS**</span><span class="sxs-lookup"><span data-stu-id="75ebc-671">**Workflow V1 applications with Workflow Tracking on now run under FIPS-mode**</span></span>

<span data-ttu-id="75ebc-672">Počítače s povoleným režimem dodržování předpisů FIPS nyní mohou úspěšně spustit pracovní postup verze 1 stylu aplikace se zapnutým sledováním pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-672">Machines with FIPS Compliance Mode enabled can now successfully run a workflow Version 1-style application with Workflow tracking on.</span></span> <span data-ttu-id="75ebc-673">Chcete-li tento scénář povolit, je nutné provést následující změny souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="75ebc-673">To enable this scenario, you must make the following change to your app.config file:</span></span>

```xml
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />
```

<span data-ttu-id="75ebc-674">Pokud tento scénář není povolena, spuštění aplikace nadále generovat výjimku se zprávou "Tato implementace není součástí platformy Windows FIPS ověřené kryptografické algoritmy."</span><span class="sxs-lookup"><span data-stu-id="75ebc-674">If this scenario is not enabled, running the application continues to generate an exception with the message, "This implementation is not part of the Windows Platform FIPS validated cryptographic algorithms."</span></span>

<span data-ttu-id="75ebc-675">**Vylepšení pracovního postupu při použití dynamické aktualizace s návrhářem pracovních postupů sady Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="75ebc-675">**Workflow Improvements when using Dynamic Update with Visual Studio Workflow Designer**</span></span>

<span data-ttu-id="75ebc-676">Návrhář pracovních postupů, Návrhář aktivit vývojového diagramu a další návrháři aktivit pracovního <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> postupu nyní úspěšně načítají a zobrazují pracovní postupy, které byly uloženy po volání metody.</span><span class="sxs-lookup"><span data-stu-id="75ebc-676">The Workflow Designer, FlowChart Activity Designer, and other Workflow Activity Designers now successfully load and display workflows that have been saved after calling  the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="75ebc-677">Ve verzích rozhraní .NET Framework před rozhraním .NET Framework 4.6.2 může načtení souboru <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> XAML v sadě Visual Studio pro pracovní postup, který byl uložen po volání, mít za následek následující problémy:</span><span class="sxs-lookup"><span data-stu-id="75ebc-677">In versions of the .NET Framework before .NET Framework 4.6.2, loading a XAML file in Visual Studio for a workflow that has been saved after calling <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> can result in the following issues:</span></span>

- <span data-ttu-id="75ebc-678">Návrhář pracovního postupu nemůže správně načíst soubor <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=nameWithType> XAML (pokud je na konci řádku).</span><span class="sxs-lookup"><span data-stu-id="75ebc-678">The Workflow Designer can't load the XAML file correctly (when the <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=nameWithType> is at the end of the line).</span></span>

- <span data-ttu-id="75ebc-679">Návrhář aktivit vývojového diagramu nebo jiné návrháři aktivit pracovního postupu mohou zobrazit všechny objekty ve výchozích umístěních na rozdíl od připojených hodnot vlastností.</span><span class="sxs-lookup"><span data-stu-id="75ebc-679">Flowchart Activity Designer or other Workflow Activity Designers may display all objects in their default locations as opposed to attached property values.</span></span>

<a name="clickonce-1" />

### <a name="clickonce"></a><span data-ttu-id="75ebc-680">ClickOnce</span><span class="sxs-lookup"><span data-stu-id="75ebc-680">ClickOnce</span></span>

<span data-ttu-id="75ebc-681">ClickOnce byl aktualizován na podporu TLS 1.1 a TLS 1.2 kromě protokolu 1.0, který již podporuje.</span><span class="sxs-lookup"><span data-stu-id="75ebc-681">ClickOnce has been updated to support TLS 1.1 and TLS 1.2 in addition to the 1.0 protocol, which it already supports.</span></span> <span data-ttu-id="75ebc-682">ClickOnce automaticky detekuje, který protokol je vyžadován; žádné další kroky v rámci clickonce aplikace jsou nutné pro povolení tls 1.1 a 1.2 podporu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-682">ClickOnce automatically detects which protocol is required; no extra steps within the ClickOnce application are required to enable TLS 1.1 and 1.2 support.</span></span>

<a name="UWPConvert" />

### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a><span data-ttu-id="75ebc-683">Převod formulářů pro Windows a aplikací WPF na aplikace UPW</span><span class="sxs-lookup"><span data-stu-id="75ebc-683">Converting Windows Forms and WPF apps to  UWP apps</span></span>

<span data-ttu-id="75ebc-684">Systém Windows nyní nabízí funkce, které přinášejí stávající desktopové aplikace pro Windows, včetně aplikací WPF a Windows Forms, na univerzální platformu Windows (UPW).</span><span class="sxs-lookup"><span data-stu-id="75ebc-684">Windows now offers capabilities to bring existing Windows desktop apps, including WPF and Windows Forms apps, to the Universal Windows Platform (UWP).</span></span> <span data-ttu-id="75ebc-685">Tato technologie funguje jako most tím, že umožňuje postupně migrovat stávající základ kódu do UPW, a tím přenést vaši aplikaci do všech zařízení s Windows 10.</span><span class="sxs-lookup"><span data-stu-id="75ebc-685">This technology acts as a bridge by enabling you to gradually migrate your existing code base to UWP, thereby bringing your app to all Windows 10 devices.</span></span>

<span data-ttu-id="75ebc-686">Převedené aplikace klasické pracovní plochy získají identitu aplikace podobnou identitě aplikace UPW, což zpřístupňuje api UPW, která umožňuje funkce, jako jsou živé dlaždice a oznámení.</span><span class="sxs-lookup"><span data-stu-id="75ebc-686">Converted desktop apps gain an app identity similar to the app identity of UWP apps, which makes UWP APIs accessible to enable features such as Live Tiles and notifications.</span></span> <span data-ttu-id="75ebc-687">Aplikace se nadále chová jako dříve a běží jako aplikace s úplným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="75ebc-687">The app continues to behave as before and runs as a full trust app.</span></span> <span data-ttu-id="75ebc-688">Po převodu aplikace lze do existujícího procesu úplné důvěryhodnosti přidat adaptivní uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="75ebc-688">Once the app is converted, an app container process can be added to the existing full trust process to add an adaptive user interface.</span></span> <span data-ttu-id="75ebc-689">Když se všechny funkce přesunou do procesu kontejneru aplikace, můžete odebrat proces úplné důvěryhodnosti a novou aplikaci UPW lze zpřístupnit všem zařízením s Windows 10.</span><span class="sxs-lookup"><span data-stu-id="75ebc-689">When all functionality is moved to the app container process, the full trust process can be removed and the new UWP app can be made available to all Windows 10 devices.</span></span>

<a name="Debug462" />

### <a name="debugging-improvements"></a><span data-ttu-id="75ebc-690">Vylepšení ladění</span><span class="sxs-lookup"><span data-stu-id="75ebc-690">Debugging improvements</span></span>

<span data-ttu-id="75ebc-691">*Nespravované rozhraní API ladění* bylo vylepšeno v rozhraní .NET Framework 4.6.2 <xref:System.NullReferenceException> k provedení další analýzy při vyvolání, aby bylo `null`možné určit, která proměnná v jednom řádku zdrojového kódu je .</span><span class="sxs-lookup"><span data-stu-id="75ebc-691">The *unmanaged debugging API* has been enhanced in the .NET Framework 4.6.2 to perform additional analysis when a <xref:System.NullReferenceException> is thrown so that it is possible to determine which variable in a single line of source code is `null`.</span></span>   <span data-ttu-id="75ebc-692">Pro podporu tohoto scénáře byla do nespravovaného rozhraní API ladění přidána následující rozhraní API rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="75ebc-692">To support this scenario, the following APIs have been added to the unmanaged debugging API.</span></span>

- <span data-ttu-id="75ebc-693">[Rozhraní ICorDebugCode4](../unmanaged-api/debugging/icordebugcode4-interface.md), [ICorDebugVariableHome](../unmanaged-api/debugging/icordebugvariablehome-interface.md)a [ICorDebugVariableHomeEnum,](../unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) které zveřejňují nativní domovy spravovaných proměnných.</span><span class="sxs-lookup"><span data-stu-id="75ebc-693">The [ICorDebugCode4](../unmanaged-api/debugging/icordebugcode4-interface.md), [ICorDebugVariableHome](../unmanaged-api/debugging/icordebugvariablehome-interface.md), and [ICorDebugVariableHomeEnum](../unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interfaces, which expose the native homes of managed variables.</span></span> <span data-ttu-id="75ebc-694">To umožňuje ladicím programům provést analýzu toku kódu, <xref:System.NullReferenceException> když dojde k a pracovat zpětně, `null`k určení spravované proměnné, která odpovídá nativnímu umístění, které bylo .</span><span class="sxs-lookup"><span data-stu-id="75ebc-694">This enables debuggers to do some code flow analysis when a  <xref:System.NullReferenceException> occurs and to work backwards to determine the managed variable that corresponds to the native location that was `null`.</span></span>

- <span data-ttu-id="75ebc-695">[Metoda ICorDebugType2::GetTypeID](../unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) poskytuje mapování pro ICorDebugType na [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md), který umožňuje ladicímu programu získat [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) bez instance ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="75ebc-695">The [ICorDebugType2::GetTypeID](../unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) method provides a mapping for ICorDebugType to [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md), which allows the debugger to obtain a [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) without an instance of the ICorDebugType.</span></span> <span data-ttu-id="75ebc-696">Existující rozhraní API na [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) pak lze určit rozložení třídy typu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-696">Existing APIs on [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) can then be used to determine the class layout of the type.</span></span>

<a name="v461" />

## <a name="whats-new-in-net-framework-461"></a><span data-ttu-id="75ebc-697">Co je nového v rozhraní .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="75ebc-697">What's new in .NET Framework 4.6.1</span></span>

<span data-ttu-id="75ebc-698">Rozhraní .NET Framework 4.6.1 obsahuje nové funkce v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="75ebc-698">The .NET Framework 4.6.1 includes new features in the following areas:</span></span>

- [<span data-ttu-id="75ebc-699">Kryptografie</span><span class="sxs-lookup"><span data-stu-id="75ebc-699">Cryptography</span></span>](#Crypto)

- [<span data-ttu-id="75ebc-700">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="75ebc-700">ADO.NET</span></span>](#ADO.NET461)

- [<span data-ttu-id="75ebc-701">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="75ebc-701">Windows Presentation Foundation (WPF)</span></span>](#WPF461)

- [<span data-ttu-id="75ebc-702">Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="75ebc-702">Windows Workflow Foundation</span></span>](#WWF461)

- [<span data-ttu-id="75ebc-703">Profilace</span><span class="sxs-lookup"><span data-stu-id="75ebc-703">Profiling</span></span>](#Profile461)

- [<span data-ttu-id="75ebc-704">Ngen</span><span class="sxs-lookup"><span data-stu-id="75ebc-704">NGen</span></span>](#NGEN461)

<span data-ttu-id="75ebc-705">Další informace o rozhraní .NET Framework 4.6.1 naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="75ebc-705">For more information on the .NET Framework 4.6.1, see the following topics:</span></span>

- [<span data-ttu-id="75ebc-706">.NET Framework 4.6.1 seznam změn</span><span class="sxs-lookup"><span data-stu-id="75ebc-706">.NET Framework 4.6.1 list of changes</span></span>](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-changes.md)

- [<span data-ttu-id="75ebc-707">Kompatibilita aplikací v 4.6.1</span><span class="sxs-lookup"><span data-stu-id="75ebc-707">Application Compatibility in 4.6.1</span></span>](../migration-guide/application-compatibility.md)

- <span data-ttu-id="75ebc-708">[.NET Framework API diff](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-api-changes.md) (na GitHubu)</span><span class="sxs-lookup"><span data-stu-id="75ebc-708">[.NET Framework API diff](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-api-changes.md) (on GitHub)</span></span>

<a name="Crypto" />

### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a><span data-ttu-id="75ebc-709">Kryptografie: Podpora certifikátů X509 obsahujících ECDSA</span><span class="sxs-lookup"><span data-stu-id="75ebc-709">Cryptography: Support for X509 certificates containing ECDSA</span></span>

<span data-ttu-id="75ebc-710">Rozhraní .NET Framework 4.6 přidalo podporu RSACng pro certifikáty X509.</span><span class="sxs-lookup"><span data-stu-id="75ebc-710">.NET Framework 4.6 added RSACng support for X509 certificates.</span></span> <span data-ttu-id="75ebc-711">Rozhraní .NET Framework 4.6.1 přidává podporu pro certifikáty ECDSA (Eliptický oblouk digitálního podpisu) X509.</span><span class="sxs-lookup"><span data-stu-id="75ebc-711">The .NET Framework 4.6.1 adds support for ECDSA (Elliptic Curve Digital Signature Algorithm) X509 certificates.</span></span>

<span data-ttu-id="75ebc-712">ECDSA nabízí lepší výkon a je bezpečnější kryptografický algoritmus než RSA, poskytuje vynikající volbu, kde je problém emitovat výkon a škálovatelnost transportní vrstvy (TLS).</span><span class="sxs-lookup"><span data-stu-id="75ebc-712">ECDSA offers better performance and is a more secure cryptography algorithm than RSA, providing an excellent choice where Transport Layer Security (TLS) performance and scalability is a concern.</span></span> <span data-ttu-id="75ebc-713">Implementace rozhraní .NET Framework zalomí volání do existujícífunkce systému Windows.</span><span class="sxs-lookup"><span data-stu-id="75ebc-713">The .NET Framework implementation wraps calls into existing Windows functionality.</span></span>

<span data-ttu-id="75ebc-714">Následující ukázkový kód ukazuje, jak snadné je generovat podpis pro bajtový datový proud pomocí nové podpory certifikátů ECDSA X509 zahrnutých v rozhraní .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="75ebc-714">The following example code shows how easy it is to generate a signature for a byte stream by using the new  support for ECDSA  X509 certificates included in the .NET Framework 4.6.1.</span></span>

[!code-csharp[whatsnew.461.crypto#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#1)]
[!code-vb[whatsnew.461.crypto#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code461.vb#1)]

<span data-ttu-id="75ebc-715">To nabízí výrazný kontrast ke kódu potřebnému ke generování podpisu v rozhraní .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="75ebc-715">This offers a marked contrast to the code needed to generate a signature in .NET Framework 4.6.</span></span>

[!code-csharp[whatsnew.461.crypto#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#2)]
[!code-vb[whatsnew.461.crypto#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code46.vb#2)]

<a name="ADO.NET461" />

### <a name="adonet"></a><span data-ttu-id="75ebc-716">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="75ebc-716">ADO.NET</span></span>

<span data-ttu-id="75ebc-717">Do ADO.NET byly přidány nové:</span><span class="sxs-lookup"><span data-stu-id="75ebc-717">The following have been added to ADO.NET:</span></span>

<span data-ttu-id="75ebc-718">**Vždy šifrovaná podpora hardwarově chráněných klíčů**</span><span class="sxs-lookup"><span data-stu-id="75ebc-718">**Always Encrypted support for hardware protected keys**</span></span>

<span data-ttu-id="75ebc-719">ADO.NET nyní podporuje ukládání vždy šifrované klíče hlavního sloupce nativně v modulech hardwarového zabezpečení (HSM).</span><span class="sxs-lookup"><span data-stu-id="75ebc-719">ADO.NET now supports storing Always Encrypted column master keys natively in Hardware Security Modules (HSMs).</span></span> <span data-ttu-id="75ebc-720">Díky této podpoře mohou zákazníci využívat asymetrické klíče uložené v objektech zabezpečení, aniž by museli psát vlastní zprostředkovatele úložiště hlavních klíčů sloupců a registrovat je v aplikacích.</span><span class="sxs-lookup"><span data-stu-id="75ebc-720">With this support, customers can leverage asymmetric keys stored in HSMs without having to write custom column master key store providers and registering them in applications.</span></span>

<span data-ttu-id="75ebc-721">Zákazníci musí nainstalovat zprostředkovatele zprostředkovatele zprostředkovatele zprostředkovatele zprostředkovatele zprostředkovatele zprostředkovatele zprostředkovatele csp poskytovaného dodavatelem nebo zprostředkovatele klíčů CNG na aplikační servery nebo klientské počítače, aby měli přístup k vždy šifrovaným datům chráněným hlavními klíči sloupců uloženými v serveru zabezpečení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="75ebc-721">Customers need to install the HSM vendor-provided CSP provider or CNG key store providers on the app servers or client computers in order to access Always Encrypted data protected with column master keys stored in a HSM.</span></span>

<span data-ttu-id="75ebc-722">**Vylepšené <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> chování připojení pro AlwaysOn**</span><span class="sxs-lookup"><span data-stu-id="75ebc-722">**Improved <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> connection behavior for AlwaysOn**</span></span>

<span data-ttu-id="75ebc-723">SqlClient nyní automaticky poskytuje rychlejší připojení k AlwaysOn dostupnost skupiny (AG).</span><span class="sxs-lookup"><span data-stu-id="75ebc-723">SqlClient now automatically provides faster connections to an AlwaysOn Availability Group (AG).</span></span> <span data-ttu-id="75ebc-724">Transparentně zjistí, zda se vaše aplikace připojuje ke skupině dostupnosti AlwaysOn (AG) v jiné podsíti a rychle zjišťuje aktuální aktivní server a poskytuje připojení k serveru.</span><span class="sxs-lookup"><span data-stu-id="75ebc-724">It transparently detects whether your application is connecting to an AlwaysOn availability group (AG) on a different subnet and quickly discovers the current active server and provides a connection to the server.</span></span> <span data-ttu-id="75ebc-725">Před vydáním této verze aplikace musela nastavit `"MultisubnetFailover=true"` připojovací řetězec tak, aby označoval, že se připojuje ke skupině dostupnosti AlwaysOn.</span><span class="sxs-lookup"><span data-stu-id="75ebc-725">Prior to this release, an application had to set the connection string to include `"MultisubnetFailover=true"` to indicate that it was connecting to an AlwaysOn Availability Group.</span></span> <span data-ttu-id="75ebc-726">Bez nastavení klíčového `true`slova připojení na aplikace může dojít k časový limit při připojování k AlwaysOn dostupnost skupiny.</span><span class="sxs-lookup"><span data-stu-id="75ebc-726">Without setting the connection keyword to `true`, an application might experience a timeout while connecting to an AlwaysOn Availability Group.</span></span> <span data-ttu-id="75ebc-727">V této verzi aplikace *not* již není <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> `true` nutné nastavit.</span><span class="sxs-lookup"><span data-stu-id="75ebc-727">With this release, an application does *not* need to set <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> to `true` anymore.</span></span> <span data-ttu-id="75ebc-728">Další informace o podpoře sqlclientu pro skupiny dostupnosti always on naleznete v tématu [Podpora sqlclientu pro vysokou dostupnost, zotavení po havárii](../data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-728">For more information about SqlClient support for Always On Availability Groups, see [SqlClient Support for High Availability, Disaster Recovery](../data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).</span></span>

<a name="WPF461" />

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="75ebc-729">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="75ebc-729">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="75ebc-730">Windows Presentation Foundation obsahuje řadu vylepšení a změn.</span><span class="sxs-lookup"><span data-stu-id="75ebc-730">Windows Presentation Foundation includes a number of improvements and changes.</span></span>

<span data-ttu-id="75ebc-731">**Vyšší výkon**</span><span class="sxs-lookup"><span data-stu-id="75ebc-731">**Improved performance**</span></span>

<span data-ttu-id="75ebc-732">Zpoždění při spouštění dotykových událostí bylo opraveno v rozhraní .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="75ebc-732">The delay in firing touch events has been fixed in the .NET Framework 4.6.1.</span></span> <span data-ttu-id="75ebc-733">Kromě toho zadáníovládacího <xref:System.Windows.Controls.RichTextBox> prvku již nenaváže vlákno vykreslení během rychlého zadávání.</span><span class="sxs-lookup"><span data-stu-id="75ebc-733">In addition, typing in a <xref:System.Windows.Controls.RichTextBox> control no longer ties up the render thread during fast input.</span></span>

<span data-ttu-id="75ebc-734">**Vylepšení kontroly pravopisu**</span><span class="sxs-lookup"><span data-stu-id="75ebc-734">**Spell checking improvements**</span></span>

<span data-ttu-id="75ebc-735">Kontrola pravopisu ve WPF byla aktualizována v systému Windows 8.1 a novějších verzích, aby využila podporu operačního systému pro kontrolu pravopisu dalších jazyků.</span><span class="sxs-lookup"><span data-stu-id="75ebc-735">The spell checker in WPF has been updated on Windows 8.1 and later versions to leverage operating system support for spell-checking additional languages.</span></span>  <span data-ttu-id="75ebc-736">Před Windows 8.1 nedojde k žádné změně funkčnosti ve verzích systému Windows.</span><span class="sxs-lookup"><span data-stu-id="75ebc-736">There is no change in functionality on Windows versions prior to Windows 8.1.</span></span>

<span data-ttu-id="75ebc-737">Stejně jako v předchozích verzích rozhraní <xref:System.Windows.Controls.TextBox> .NET <xref:System.Windows.Controls.RichTextBox> Framework je jazyk pro řídicí blok ora zjištěn hledáním informací v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="75ebc-737">As in previous versions of the .NET Framework, the language for a <xref:System.Windows.Controls.TextBox> control ora <xref:System.Windows.Controls.RichTextBox> block is detected by looking for information in the following order:</span></span>

- <span data-ttu-id="75ebc-738">`xml:lang`, pokud je přítomen.</span><span class="sxs-lookup"><span data-stu-id="75ebc-738">`xml:lang`, if it is present.</span></span>

- <span data-ttu-id="75ebc-739">Aktuální jazyk zadávání.</span><span class="sxs-lookup"><span data-stu-id="75ebc-739">Current input language.</span></span>

- <span data-ttu-id="75ebc-740">Aktuální jazyková verze vlákna.</span><span class="sxs-lookup"><span data-stu-id="75ebc-740">Current thread culture.</span></span>

<span data-ttu-id="75ebc-741">Další informace o jazykové podpoře ve WPF naleznete v [příspěvku blogu WPF na rozhraní .NET Framework 4.6.1 .](https://devblogs.microsoft.com/wpf/wpf-in-net-4-6-1/)</span><span class="sxs-lookup"><span data-stu-id="75ebc-741">For more information on language support in WPF, see the [WPF blog post on .NET Framework 4.6.1 features](https://devblogs.microsoft.com/wpf/wpf-in-net-4-6-1/).</span></span>

<span data-ttu-id="75ebc-742">**Další podpora pro vlastní slovníky pro jednotlivé uživatele**</span><span class="sxs-lookup"><span data-stu-id="75ebc-742">**Additional support for per-user custom dictionaries**</span></span>

<span data-ttu-id="75ebc-743">V rozhraní .NET Framework 4.6.1 WPF rozpozná vlastní slovníky, které jsou registrovány globálně.</span><span class="sxs-lookup"><span data-stu-id="75ebc-743">In .NET Framework 4.6.1, WPF recognizes custom dictionaries that are registered globally.</span></span> <span data-ttu-id="75ebc-744">Tato funkce je k dispozici kromě možnosti zaregistrovat je na ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="75ebc-744">This capability is available in addition to the ability to register them per-control.</span></span>

<span data-ttu-id="75ebc-745">V předchozích verzích WPF vlastní slovníky nerozpoznaly seznamy vyloučených slov a automatických oprav.</span><span class="sxs-lookup"><span data-stu-id="75ebc-745">In previous versions of WPF, custom dictionaries did not recognize Excluded Words and AutoCorrect lists.</span></span> <span data-ttu-id="75ebc-746">Jsou podporovány v systémech Windows 8.1 a Windows 10 pomocí `%AppData%\Microsoft\Spelling\<language tag>` souborů, které mohou být umístěny pod adresářem.</span><span class="sxs-lookup"><span data-stu-id="75ebc-746">They are supported on Windows 8.1 and Windows 10 through the use of files that can be placed under the `%AppData%\Microsoft\Spelling\<language tag>` directory.</span></span>  <span data-ttu-id="75ebc-747">Pro tyto soubory platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="75ebc-747">The following rules apply to these files:</span></span>

- <span data-ttu-id="75ebc-748">Soubory by měly mít přípony .dic (pro přidaná slova), .exc (pro vyloučená slova) nebo .acl (pro automatické opravy).</span><span class="sxs-lookup"><span data-stu-id="75ebc-748">The files should have extensions of .dic (for added words), .exc (for excluded words), or .acl (for AutoCorrect).</span></span>

- <span data-ttu-id="75ebc-749">Soubory by měly být UTF-16 LE ve formátu prostého textu, který začíná označením objednávky bajtů (BOM).</span><span class="sxs-lookup"><span data-stu-id="75ebc-749">The files should be UTF-16 LE plaintext that starts with the Byte Order Mark (BOM).</span></span>

- <span data-ttu-id="75ebc-750">Každý řádek by se měl skládat ze slova (v seznamech slov s přidanými a vyloučenými slovy) nebo z dvojice automatických oprav se slovy oddělenými svislým pruhem ("&#124;") (v seznamu slov Automatické opravy).</span><span class="sxs-lookup"><span data-stu-id="75ebc-750">Each line should consist of a word (in the added and excluded word lists), or an autocorrect pair with the words separated by a vertical bar ("&#124;") (in the AutoCorrect word list).</span></span>

- <span data-ttu-id="75ebc-751">Tyto soubory jsou považovány za jen pro čtení a nejsou systémem změněny.</span><span class="sxs-lookup"><span data-stu-id="75ebc-751">These files are considered read-only and are not modified by the system.</span></span>

> [!NOTE]
> <span data-ttu-id="75ebc-752">Tyto nové formáty souborů nejsou přímo podporovány WPF kontrolu pravopisu API a vlastní slovníky dodané WPF v aplikacích by měl y nadále používat soubory .lex.</span><span class="sxs-lookup"><span data-stu-id="75ebc-752">These new file-formats are not directly supported by the WPF spell checking APIs, and the custom dictionaries supplied to WPF in applications should continue to use .lex files.</span></span>

<span data-ttu-id="75ebc-753">**Ukázky**</span><span class="sxs-lookup"><span data-stu-id="75ebc-753">**Samples**</span></span>

<span data-ttu-id="75ebc-754">Existuje několik wpf ukázky v úložišti [GitHub Microsoft/WPF-Samples.](https://github.com/Microsoft/WPF-Samples)</span><span class="sxs-lookup"><span data-stu-id="75ebc-754">There are a number of WPF samples on the [Microsoft/WPF-Samples](https://github.com/Microsoft/WPF-Samples) GitHub repository.</span></span> <span data-ttu-id="75ebc-755">Pomozte nám vylepšit naše ukázky tím, že nám pošlete žádost o přijetí nebo otevřete [problém githubu](https://github.com/Microsoft/WPF-Samples/issues).</span><span class="sxs-lookup"><span data-stu-id="75ebc-755">Help us improve our samples by sending us a pull-request or opening a [GitHub issue](https://github.com/Microsoft/WPF-Samples/issues).</span></span>

<span data-ttu-id="75ebc-756">**Rozšíření DirectX**</span><span class="sxs-lookup"><span data-stu-id="75ebc-756">**DirectX extensions**</span></span>

<span data-ttu-id="75ebc-757">WPF obsahuje [balíček NuGet,](https://www.nuget.org/packages/Microsoft.Wpf.Interop.DirectX-x86/) který <xref:System.Windows.Interop.D3DImage> poskytuje nové implementace, které usnadňují práci s obsahem DX10 a Dx11.</span><span class="sxs-lookup"><span data-stu-id="75ebc-757">WPF includes a [NuGet package](https://www.nuget.org/packages/Microsoft.Wpf.Interop.DirectX-x86/) that provides new implementations of <xref:System.Windows.Interop.D3DImage> that make it easy for you to interoperate with DX10 and Dx11 content.</span></span> <span data-ttu-id="75ebc-758">Kód pro tento balíček byl open sourced a je k dispozici [na GitHubu](https://github.com/Microsoft/WPFDXInterop).</span><span class="sxs-lookup"><span data-stu-id="75ebc-758">The code for this package has been open sourced and is available [on GitHub](https://github.com/Microsoft/WPFDXInterop).</span></span>

<a name="WWF461" />

### <a name="windows-workflow-foundation-transactions"></a><span data-ttu-id="75ebc-759">Windows Workflow Foundation: Transakce</span><span class="sxs-lookup"><span data-stu-id="75ebc-759">Windows Workflow Foundation: Transactions</span></span>

<span data-ttu-id="75ebc-760">Metoda <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> nyní můžete použít správce distribuovaných transakcí než MSDTC k propagaci transakce.</span><span class="sxs-lookup"><span data-stu-id="75ebc-760">The <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> method can now use a distributed transaction manager other than MSDTC to promote the transaction.</span></span> <span data-ttu-id="75ebc-761">To provést zadáním identifikátoru propagátoru <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> transakcí GUID pro nové přetížení .</span><span class="sxs-lookup"><span data-stu-id="75ebc-761">You do this by specifying a GUID transaction promoter identifier to the  new <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> overload .</span></span> <span data-ttu-id="75ebc-762">Pokud je tato operace úspěšná, existují omezení na možnosti transakce.</span><span class="sxs-lookup"><span data-stu-id="75ebc-762">If this operation is successful, there are limitations placed on the capabilities of the transaction.</span></span> <span data-ttu-id="75ebc-763">Jakmile je zapsán propagátor transakcí jiné než MSDTC, následující metody <xref:System.Transactions.TransactionPromotionException> vyvolat, protože tyto metody vyžadují povýšení na MSDTC:</span><span class="sxs-lookup"><span data-stu-id="75ebc-763">Once a non-MSDTC transaction promoter is enlisted, the following methods throw a <xref:System.Transactions.TransactionPromotionException> because these methods require promotion to MSDTC:</span></span>

- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetDtcTransaction%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetExportCookie%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetTransmitterPropagationToken%2A?displayProperty=nameWithType>

<span data-ttu-id="75ebc-764">Jakmile je zapsán propagátor transakcí jiné než MSDTC, musí být použit pro budoucí trvalé zařazení pomocí protokolů, které definuje.</span><span class="sxs-lookup"><span data-stu-id="75ebc-764">Once a non-MSDTC transaction promoter is enlisted, it must be used for future durable enlistments by using protocols that it defines.</span></span> <span data-ttu-id="75ebc-765">Pořadatele <xref:System.Guid> transakcí lze získat pomocí <xref:System.Transactions.Transaction.PromoterType%2A> nemovitosti.</span><span class="sxs-lookup"><span data-stu-id="75ebc-765">The <xref:System.Guid> of the transaction promoter can be obtained by using the <xref:System.Transactions.Transaction.PromoterType%2A> property.</span></span> <span data-ttu-id="75ebc-766">Když transakce propaguje, promotér transakcí poskytuje <xref:System.Byte> pole, které představuje propagovaný token.</span><span class="sxs-lookup"><span data-stu-id="75ebc-766">When the transaction promotes, the transaction promoter provides a <xref:System.Byte> array that represents the promoted token.</span></span> <span data-ttu-id="75ebc-767">Aplikace může získat povýšený token pro transakci, která není <xref:System.Transactions.Transaction.GetPromotedToken%2A> podporována msdtc s metodou.</span><span class="sxs-lookup"><span data-stu-id="75ebc-767">An application can obtain the promoted token for a non-MSDTC promoted transaction with the <xref:System.Transactions.Transaction.GetPromotedToken%2A> method.</span></span>

<span data-ttu-id="75ebc-768">Uživatelé nové <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> přetížení musí následovat konkrétní pořadí volání, aby operace povýšení úspěšně dokončit.</span><span class="sxs-lookup"><span data-stu-id="75ebc-768">Users of the new <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> overload must follow a specific call sequence in order for the promotion operation to complete successfully.</span></span> <span data-ttu-id="75ebc-769">Tato pravidla jsou popsána v dokumentaci metody.</span><span class="sxs-lookup"><span data-stu-id="75ebc-769">These rules are documented in the method's documentation.</span></span>

<a name="Profile461" />

### <a name="profiling"></a><span data-ttu-id="75ebc-770">Profilace</span><span class="sxs-lookup"><span data-stu-id="75ebc-770">Profiling</span></span>

<span data-ttu-id="75ebc-771">Nespravované profilování rozhraní API byla rozšířena takto:</span><span class="sxs-lookup"><span data-stu-id="75ebc-771">The unmanaged profiling API has been enhanced as follows:</span></span>

- <span data-ttu-id="75ebc-772">Lepší podpora pro přístup k PDBs v rozhraní [ICorProfilerInfo7.](../unmanaged-api/profiling/icorprofilerinfo7-interface.md)</span><span class="sxs-lookup"><span data-stu-id="75ebc-772">Better support for accessing PDBs in the [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) interface.</span></span>

  <span data-ttu-id="75ebc-773">V ASP.NET Core, je stále běžnější pro sestavení, které mají být kompilovány v paměti Roslyn.</span><span class="sxs-lookup"><span data-stu-id="75ebc-773">In ASP.NET Core, it is becoming much more common for assemblies to be compiled in-memory by Roslyn.</span></span> <span data-ttu-id="75ebc-774">Pro vývojáře, kteří provádějí nástroje pro profilování, to znamená, že objekty PDB, které byly historicky serializovány na disku, již nemusí být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="75ebc-774">For developers making profiling tools, this means that PDBs that historically were serialized on disk may no longer be present.</span></span> <span data-ttu-id="75ebc-775">Nástroje profileru často používají objekty PDB k mapování kódu zpět na zdrojové řádky pro úkoly, jako je pokrytí kódu nebo analýza výkonu řádek po řádku.</span><span class="sxs-lookup"><span data-stu-id="75ebc-775">Profiler tools often use PDBs to map code back to source lines for tasks such as code coverage or line-by-line performance analysis.</span></span> <span data-ttu-id="75ebc-776">[Rozhraní ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) nyní obsahuje dvě nové metody, [ICorProfilerInfo7::GetInMemorySymbolsLength](../unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) a [ICorProfilerInfo7::ReadInMemorySymbols](../unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md), aby tyto nástroje profileru poskytovaly přístup k datům PDB v paměti, pomocí nových rozhraní API může profiler získat obsah pdb v paměti jako bajtové pole a potom jej zpracovat nebo serializovat na disk.</span><span class="sxs-lookup"><span data-stu-id="75ebc-776">The [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) interface now includes two new methods, [ICorProfilerInfo7::GetInMemorySymbolsLength](../unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) and [ICorProfilerInfo7::ReadInMemorySymbols](../unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md), to provide these profiler tools with access to the in-memory PDB data, By using the new APIs, a profiler can obtain the contents of an in-memory PDB as a byte array and then process it or serialize it to disk.</span></span>

- <span data-ttu-id="75ebc-777">Lepší instrumentace s rozhraním ICorProfiler.</span><span class="sxs-lookup"><span data-stu-id="75ebc-777">Better instrumentation with the ICorProfiler interface.</span></span>

  <span data-ttu-id="75ebc-778">Profilovací programy, `ICorProfiler` které používají funkce ReJit api pro dynamické instrumentace nyní můžete upravit některá metadata.</span><span class="sxs-lookup"><span data-stu-id="75ebc-778">Profilers that are using the `ICorProfiler` APIs ReJit functionality for dynamic instrumentation can now modify some metadata.</span></span> <span data-ttu-id="75ebc-779">Dříve tyto nástroje mohly kdykoli instrumentovat IL, ale metadata mohla být změněna pouze v době načítání modulu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-779">Previously such tools could instrument IL at any time, but metadata could only be modified at module load time.</span></span> <span data-ttu-id="75ebc-780">Vzhledem k tomu, že IL odkazuje na metadata, to omezené druhy instrumentace, které by bylo možné provést.</span><span class="sxs-lookup"><span data-stu-id="75ebc-780">Because IL refers to metadata, this limited the kinds of instrumentation that could be done.</span></span> <span data-ttu-id="75ebc-781">Některé z těchto limitů jsme zrušili přidáním metody [ICorProfilerInfo7::ApplyMetaData](../unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) pro podporu podmnožiny úprav metadat `AssemblyRef` `TypeRef`po `TypeSpec` `MemberRef`načtení modulu, zejména přidáním nových záznamů , , `MemberSpec`, , a `UserString` záznamů.</span><span class="sxs-lookup"><span data-stu-id="75ebc-781">We have lifted some of those limits by adding the [ICorProfilerInfo7::ApplyMetaData](../unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) method to support a subset of metadata edits after the module loads, in particular by adding new `AssemblyRef`, `TypeRef`, `TypeSpec`, `MemberRef`, `MemberSpec`, and `UserString` records.</span></span> <span data-ttu-id="75ebc-782">Tato změna umožňuje mnohem širší škálu přístrojových nástrojů za chodu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-782">This change makes a much broader range of on-the-fly instrumentation possible.</span></span>

<a name="NGEN461" />

### <a name="native-image-generator-ngen-pdbs"></a><span data-ttu-id="75ebc-783">Nativní obrazgenerátor (NGEN) PDBs</span><span class="sxs-lookup"><span data-stu-id="75ebc-783">Native Image Generator (NGEN) PDBs</span></span>

<span data-ttu-id="75ebc-784">Trasování událostí mezi počítači umožňuje zákazníkům profilovat program v počítači A a podívat se na data profilování pomocí mapování zdrojové čáry v počítači B. Pomocí předchozích verzí rozhraní .NET Framework by uživatel zkopíroval všechny moduly a nativní bitové kopie z profilovaného počítače do analytického počítače, který obsahuje dDB IL a vytvořil mapování ze zdroje na nativní.</span><span class="sxs-lookup"><span data-stu-id="75ebc-784">Cross-machine event tracing allows customers to profile a program on Machine A and look at the profiling data with source line mapping on Machine B. Using previous versions of the .NET Framework, the user would copy all the modules and native images from the profiled machine to the analysis machine that contains the IL PDB to create the source-to-native mapping.</span></span> <span data-ttu-id="75ebc-785">Zatímco tento proces může fungovat dobře, když jsou soubory relativně malé, například pro telefonní aplikace, soubory mohou být velmi velké na stolních systémech a vyžadují značný čas ke kopírování.</span><span class="sxs-lookup"><span data-stu-id="75ebc-785">While this process may work well when the files are relatively small, such as for phone applications, the files can be very large on desktop systems and require significant time to copy.</span></span>

<span data-ttu-id="75ebc-786">S Ngen PDBs NGen můžete vytvořit PDB, který obsahuje il-to-nativní mapování bez závislosti na IL PDB.</span><span class="sxs-lookup"><span data-stu-id="75ebc-786">With Ngen PDBs, NGen can create a PDB that contains the IL-to-native mapping without a dependency on the IL PDB.</span></span> <span data-ttu-id="75ebc-787">V našem scénáři trasování událostí mezi počítači je potřeba pouze zkopírovat nativní pdb bitové kopie, která je generována počítačem A do počítače B, a použít [rozhraní API pro přístup k ladění k](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) čtení mapování zdroje-IL pdb a mapování IL-TO-NAtivního obrázku PDB.</span><span class="sxs-lookup"><span data-stu-id="75ebc-787">In our cross-machine event tracing scenario, all that is needed is to copy the native image PDB that is generated by Machine A to Machine B and to use [Debug Interface Access APIs](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) to read the IL PDB's source-to-IL mapping and the native image PDB's IL-to-native mapping.</span></span> <span data-ttu-id="75ebc-788">Kombinace obou mapování poskytuje mapování zdroj na nativní.</span><span class="sxs-lookup"><span data-stu-id="75ebc-788">Combining both mappings provides a source-to-native mapping.</span></span> <span data-ttu-id="75ebc-789">Vzhledem k tomu, že nativní obraz PDB je mnohem menší než všechny moduly a nativní obrázky, proces kopírování z počítače A do počítače B je mnohem rychlejší.</span><span class="sxs-lookup"><span data-stu-id="75ebc-789">Since the native image PDB is much smaller than all the modules and native images, the process of copying from Machine A to Machine B is much faster.</span></span>

<a name="v46" />

## <a name="whats-new-in-net-2015"></a><span data-ttu-id="75ebc-790">Co je nového v rozhraní .NET 2015</span><span class="sxs-lookup"><span data-stu-id="75ebc-790">What's new in .NET 2015</span></span>

<span data-ttu-id="75ebc-791">.NET 2015 zavádí rozhraní .NET Framework 4.6 a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="75ebc-791">.NET 2015 introduces the .NET Framework 4.6 and .NET Core.</span></span> <span data-ttu-id="75ebc-792">Některé nové funkce platí pro oba a další funkce jsou specifické pro rozhraní .NET Framework 4.6 nebo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="75ebc-792">Some new features apply to both, and other features are specific to .NET Framework 4.6 or .NET Core.</span></span>

- <span data-ttu-id="75ebc-793">**ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="75ebc-793">**ASP.NET Core**</span></span>

  <span data-ttu-id="75ebc-794">.NET 2015 obsahuje ASP.NET Core, což je štíhlá implementace .NET pro vytváření moderních cloudových aplikací.</span><span class="sxs-lookup"><span data-stu-id="75ebc-794">.NET 2015 includes ASP.NET Core, which is a lean .NET implementation for building modern cloud-based apps.</span></span> <span data-ttu-id="75ebc-795">ASP.NET Core je modulární, takže můžete zahrnout pouze ty funkce, které jsou potřebné ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="75ebc-795">ASP.NET Core is modular so you can include only those features that are needed in your application.</span></span> <span data-ttu-id="75ebc-796">Může být hostován ve službě IIS nebo hostován samostatně ve vlastním procesu a můžete spouštět aplikace s různými verzemi rozhraní .NET Framework na stejném serveru.</span><span class="sxs-lookup"><span data-stu-id="75ebc-796">It can be hosted on IIS or self-hosted in a custom process, and you can run apps with different versions of the .NET Framework on the same server.</span></span> <span data-ttu-id="75ebc-797">Obsahuje nový konfigurační systém prostředí, který je určen pro nasazení v cloudu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-797">It includes a new environment configuration system that is designed for cloud deployment.</span></span>

  <span data-ttu-id="75ebc-798">MVC, Web API a webové stránky jsou sjednoceny do jedné architektury s názvem MVC 6.</span><span class="sxs-lookup"><span data-stu-id="75ebc-798">MVC, Web API, and Web Pages are unified into a single framework called MVC 6.</span></span> <span data-ttu-id="75ebc-799">Aplikace ASP.NET Core se vytvářejí pomocí nástrojů ve Visual Studiu 2015 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="75ebc-799">You build ASP.NET Core apps through tools in Visual Studio 2015 or later.</span></span> <span data-ttu-id="75ebc-800">Vaše stávající aplikace budou fungovat na novém rozhraní .NET Framework. ale chcete-li vytvořit aplikaci, která používá MVC 6 nebo SignalR 3, musíte použít systém projektu v sadě Visual Studio 2015 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="75ebc-800">Your existing applications will work on the new .NET Framework; however to build an app that uses MVC 6 or SignalR 3, you must use the project system in Visual Studio 2015 or later.</span></span>

  <span data-ttu-id="75ebc-801">Další informace naleznete [v tématu ASP.NET Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="75ebc-801">For information, see [ASP.NET Core](/aspnet/core/).</span></span>

- <span data-ttu-id="75ebc-802">**aktualizace ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="75ebc-802">**ASP.NET Updates**</span></span>

  - <span data-ttu-id="75ebc-803">**Rozhraní API založené na úlohách pro vyprázdnění asynchronní odezvy**</span><span class="sxs-lookup"><span data-stu-id="75ebc-803">**Task-based API for Asynchronous Response Flushing**</span></span>

    <span data-ttu-id="75ebc-804">ASP.NET nyní poskytuje jednoduché rozhraní API založené na úlohách <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=nameWithType>pro vyprázdnění asynchronní odpovědi , , který `async/await` umožňuje odpovědi vyprázdnění asynchronně pomocí podpory jazyka.</span><span class="sxs-lookup"><span data-stu-id="75ebc-804">ASP.NET now provides a simple task-based API for asynchronous response flushing, <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=nameWithType>, that allows responses to be flushed asynchronously by using your language's `async/await` support.</span></span>

  - <span data-ttu-id="75ebc-805">**Vazba modelu podporuje metody vrácení úloh.**</span><span class="sxs-lookup"><span data-stu-id="75ebc-805">**Model binding supports task-returning methods**</span></span>

    <span data-ttu-id="75ebc-806">V rozhraní .NET Framework 4.5 ASP.NET přidal funkci Vazby modelu, která umožňovala rozšiřitelný přístup zaměřený na kód k datovým operacím založeným na CRUD na stránkách webových formulářů a uživatelských ovládacích prvcích.</span><span class="sxs-lookup"><span data-stu-id="75ebc-806">In the .NET Framework 4.5, ASP.NET added the Model Binding feature that enabled an extensible, code-focused approach to CRUD-based data operations in Web Forms pages and user controls.</span></span> <span data-ttu-id="75ebc-807">Model vazby systému nyní podporuje <xref:System.Threading.Tasks.Task>metody vazby modelu -returning.</span><span class="sxs-lookup"><span data-stu-id="75ebc-807">The Model Binding system now supports <xref:System.Threading.Tasks.Task>-returning model binding methods.</span></span> <span data-ttu-id="75ebc-808">Tato funkce umožňuje vývojářům webových formulářů získat výhody asynchronnosti s snadnou součástí systému datových vazeb při použití novějších verzí ormů, včetně entity Framework.</span><span class="sxs-lookup"><span data-stu-id="75ebc-808">This feature allows Web Forms developers to get the scalability benefits of async with the ease of the data-binding system when using newer versions of ORMs, including the Entity Framework.</span></span>

    <span data-ttu-id="75ebc-809">Asynchronní vazba modelu `aspnet:EnableAsyncModelBinding` je řízena nastavením konfigurace.</span><span class="sxs-lookup"><span data-stu-id="75ebc-809">Async model binding is controlled by the `aspnet:EnableAsyncModelBinding` configuration setting.</span></span>

    ```xml
    <appSettings>
        <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />
    </appSettings>
    ```

    <span data-ttu-id="75ebc-810">V aplikacích, které cílí na rozhraní .NET Framework 4.6, je výchozí . `true`</span><span class="sxs-lookup"><span data-stu-id="75ebc-810">On apps the target the .NET Framework 4.6, it defaults to `true`.</span></span> <span data-ttu-id="75ebc-811">V aplikacích spuštěných v rozhraní .NET Framework 4.6, které `false` cílí na starší verzi rozhraní .NET Framework, je ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="75ebc-811">On apps running on the .NET Framework 4.6 that target an earlier version of the .NET Framework, it is `false` by default.</span></span> <span data-ttu-id="75ebc-812">To může být povoleno nastavením `true`nastavení konfigurace na .</span><span class="sxs-lookup"><span data-stu-id="75ebc-812">It can be enabled by setting the configuration setting to `true`.</span></span>

  - <span data-ttu-id="75ebc-813">**Podpora HTTP/2 (Windows 10)**</span><span class="sxs-lookup"><span data-stu-id="75ebc-813">**HTTP/2 Support (Windows 10)**</span></span>

    <span data-ttu-id="75ebc-814">[HTTP/2](https://www.wikipedia.org/wiki/HTTP/2) je nová verze protokolu HTTP, která poskytuje mnohem lepší využití připojení (méně zpátečních cest mezi klientem a serverem), což má za následek nižší latenci načítání webových stránek pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="75ebc-814">[HTTP/2](https://www.wikipedia.org/wiki/HTTP/2) is a new version of the HTTP protocol that provides much better connection utilization (fewer round-trips between client and server), resulting in lower latency web page loading for users.</span></span>  <span data-ttu-id="75ebc-815">Webové stránky (na rozdíl od služeb) mají největší prospěch z protokolu HTTP/2, protože protokol optimalizuje pro více artefaktů požadovaných jako součást jednoho prostředí.</span><span class="sxs-lookup"><span data-stu-id="75ebc-815">Web pages (as opposed to services) benefit the most from HTTP/2, since the protocol optimizes for multiple artifacts being requested as part of a single experience.</span></span> <span data-ttu-id="75ebc-816">Podpora HTTP/2 byla přidána do ASP.NET v rozhraní .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="75ebc-816">HTTP/2 support has been added to ASP.NET in .NET Framework 4.6.</span></span> <span data-ttu-id="75ebc-817">Vzhledem k tomu, že síťové funkce existují ve více vrstvách, byly vyžadovány nové funkce v systému Windows, ve službě IIS a v ASP.NET povolit protokol HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="75ebc-817">Because networking functionality exists at multiple layers, new features were required in Windows, in IIS, and in ASP.NET to enable HTTP/2.</span></span> <span data-ttu-id="75ebc-818">Chcete-li používat protokol HTTP/2 s ASP.NET, musíte být spuštěni ve Windows 10.</span><span class="sxs-lookup"><span data-stu-id="75ebc-818">You must be running on Windows 10 to use HTTP/2 with ASP.NET.</span></span>

    <span data-ttu-id="75ebc-819">HTTP/2 je také podporována a zapnuta ve výchozím nastavení pro Windows <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> 10 Univerzální platforma Windows (UPW) aplikace, které používají rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="75ebc-819">HTTP/2 is also supported and on by default for Windows 10 Universal Windows Platform (UWP) apps that use the <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> API.</span></span>

    <span data-ttu-id="75ebc-820">Aby bylo možné poskytnout způsob, jak používat [PUSH_PROMISE](https://http2.github.io/http2-spec/#PUSH_PROMISE) funkce v ASP.NET <xref:System.Web.HttpResponse.PushPromise%28System.String%29> aplikace, byla do <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29> <xref:System.Web.HttpResponse> třídy přidána nová metoda se dvěma přetíženími a , .</span><span class="sxs-lookup"><span data-stu-id="75ebc-820">In order to provide a way to use the [PUSH_PROMISE](https://http2.github.io/http2-spec/#PUSH_PROMISE) feature in ASP.NET applications, a new method with two overloads, <xref:System.Web.HttpResponse.PushPromise%28System.String%29> and <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29>, has been added to the <xref:System.Web.HttpResponse> class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="75ebc-821">Zatímco ASP.NET Core podporuje HTTP/2, podpora funkce PUSH PROMISE ještě nebyla přidána.</span><span class="sxs-lookup"><span data-stu-id="75ebc-821">While ASP.NET Core supports HTTP/2, support for the PUSH PROMISE feature has not yet been added.</span></span>

    <span data-ttu-id="75ebc-822">Prohlížeč a webový server (IIS v systému Windows) provést veškerou práci.</span><span class="sxs-lookup"><span data-stu-id="75ebc-822">The browser and the web server (IIS on Windows) do all the work.</span></span> <span data-ttu-id="75ebc-823">Nemusíte dělat žádné těžké zvedání pro vaše uživatele.</span><span class="sxs-lookup"><span data-stu-id="75ebc-823">You don't have to do any heavy-lifting for your users.</span></span>

    <span data-ttu-id="75ebc-824">Většina [hlavních prohlížečů podporuje protokol HTTP/2](https://www.wikipedia.org/wiki/HTTP/2), takže je pravděpodobné, že uživatelé budou mít prospěch z podpory HTTP/2, pokud ji váš server podporuje.</span><span class="sxs-lookup"><span data-stu-id="75ebc-824">Most of the [major browsers support HTTP/2](https://www.wikipedia.org/wiki/HTTP/2), so it's likely that your users will benefit from HTTP/2 support if your server supports it.</span></span>

  - <span data-ttu-id="75ebc-825">**Podpora protokolu tokenové vazby**</span><span class="sxs-lookup"><span data-stu-id="75ebc-825">**Support for the Token Binding Protocol**</span></span>

    <span data-ttu-id="75ebc-826">Společnosti Microsoft a Google spolupracují na novém přístupu k ověřování, který se nazývá [Token Binding Protocol](https://github.com/TokenBinding/Internet-Drafts).</span><span class="sxs-lookup"><span data-stu-id="75ebc-826">Microsoft and Google have been collaborating on a new approach to authentication, called the [Token Binding Protocol](https://github.com/TokenBinding/Internet-Drafts).</span></span> <span data-ttu-id="75ebc-827">Předpokladem je, že ověřovací tokeny (v mezipaměti prohlížeče) mohou být ukradeny a používány zločinci pro přístup k jinak zabezpečeným prostředkům (například k vašemu bankovnímu účtu) bez nutnosti hesla nebo jiných privilegovaných znalostí.</span><span class="sxs-lookup"><span data-stu-id="75ebc-827">The premise is that authentication tokens (in your browser cache) can be stolen and used by criminals to access otherwise secure resources (for example, your bank account) without requiring your password or any other privileged knowledge.</span></span> <span data-ttu-id="75ebc-828">Nový protokol má za cíl zmírnit tento problém.</span><span class="sxs-lookup"><span data-stu-id="75ebc-828">The new protocol aims to mitigate this problem.</span></span>

    <span data-ttu-id="75ebc-829">Token Binding Protocol bude implementován ve Windows 10 jako funkce prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="75ebc-829">The Token Binding Protocol will be implemented in Windows 10 as a browser feature.</span></span> <span data-ttu-id="75ebc-830">ASP.NET aplikace se budou účastnit protokolu, takže ověřovací tokeny jsou ověřeny jako legitimní.</span><span class="sxs-lookup"><span data-stu-id="75ebc-830">ASP.NET apps will participate in the protocol, so that authentication tokens are validated to be legitimate.</span></span> <span data-ttu-id="75ebc-831">Implementace klienta a serveru vytvářejí ochranu mezi koncovými částmi určenou protokolem.</span><span class="sxs-lookup"><span data-stu-id="75ebc-831">The client and the server implementations establish the end-to-end protection specified by the protocol.</span></span>

  - <span data-ttu-id="75ebc-832">**Randomizované algoritmy hash řetězce**</span><span class="sxs-lookup"><span data-stu-id="75ebc-832">**Randomized string hash algorithms**</span></span>

    <span data-ttu-id="75ebc-833">Rozhraní .NET Framework 4.5 zavedlo [algoritmus hash randomizovaného řetězce](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-833">.NET Framework 4.5 introduced a [randomized string hash algorithm](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).</span></span> <span data-ttu-id="75ebc-834">Však to nebylo podporováno ASP.NET z důvodu některých ASP.NET funkce závisí na stabilní hash kód.</span><span class="sxs-lookup"><span data-stu-id="75ebc-834">However, it was not supported by ASP.NET because of some ASP.NET features depended on a stable hash code.</span></span> <span data-ttu-id="75ebc-835">V rozhraní .NET Framework 4.6 jsou nyní podporovány algoritmy hash randomizovaných řetězců.</span><span class="sxs-lookup"><span data-stu-id="75ebc-835">In .NET Framework 4.6, randomized string hash algorithms are now supported.</span></span> <span data-ttu-id="75ebc-836">Chcete-li tuto funkci `aspnet:UseRandomizedStringHashAlgorithm` povolit, použijte nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="75ebc-836">To enable this feature, use the `aspnet:UseRandomizedStringHashAlgorithm` config setting.</span></span>

    ```xml
    <appSettings>
        <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />
    </appSettings>
    ```

- <span data-ttu-id="75ebc-837">**ADO.NET**</span><span class="sxs-lookup"><span data-stu-id="75ebc-837">**ADO.NET**</span></span>

  <span data-ttu-id="75ebc-838">Rozhraní ADO .NET nyní podporuje funkci Vždy šifrované dostupné v SQL Serveru 2016 Community Technology Preview 2 (CTP2).</span><span class="sxs-lookup"><span data-stu-id="75ebc-838">ADO .NET now supports the Always Encrypted feature available in SQL Server 2016 Community Technology Preview 2 (CTP2).</span></span> <span data-ttu-id="75ebc-839">S vždy šifrované, SQL Server může provádět operace na šifrovaná data a nejlepší ze všech šifrovací klíč se nachází s aplikací uvnitř důvěryhodného prostředí zákazníka a nikoli na serveru.</span><span class="sxs-lookup"><span data-stu-id="75ebc-839">With Always Encrypted, SQL Server can perform operations on encrypted data, and best of all the encryption key resides with the application inside the customer’s trusted environment and not on the server.</span></span> <span data-ttu-id="75ebc-840">Vždy šifrované zabezpečuje zákaznická data, takže dba nemají přístup k datům ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-840">Always Encrypted secures customer data so DBAs do not have access to plain text data.</span></span> <span data-ttu-id="75ebc-841">Šifrování a dešifrování dat probíhá transparentně na úrovni ovladače, což minimalizuje změny, které je třeba provést u stávajících aplikací.</span><span class="sxs-lookup"><span data-stu-id="75ebc-841">Encryption and decryption of data happens transparently at the driver level, minimizing changes that have to be made to existing applications.</span></span> <span data-ttu-id="75ebc-842">Podrobnosti naleznete [v tématech Vždy šifrované (Database Engine)](/sql/relational-databases/security/encryption/always-encrypted-database-engine) a [vždy šifrované (vývoj klienta)](/sql/relational-databases/security/encryption/always-encrypted-client-development).</span><span class="sxs-lookup"><span data-stu-id="75ebc-842">For details, see [Always Encrypted (Database Engine)](/sql/relational-databases/security/encryption/always-encrypted-database-engine) and [Always Encrypted (client development)](/sql/relational-databases/security/encryption/always-encrypted-client-development).</span></span>

- <span data-ttu-id="75ebc-843">**64bitový kompilátor JIT pro spravovaný kód**</span><span class="sxs-lookup"><span data-stu-id="75ebc-843">**64-bit JIT Compiler for managed code**</span></span>

  <span data-ttu-id="75ebc-844">Rozhraní .NET Framework 4.6 obsahuje novou verzi 64bitového kompilátoru JIT (původně s kódovým názvem RyuJIT).</span><span class="sxs-lookup"><span data-stu-id="75ebc-844">.NET Framework 4.6 features a new version of the 64-bit JIT compiler (originally code-named RyuJIT).</span></span> <span data-ttu-id="75ebc-845">Nový 64bitový kompilátor poskytuje významné zlepšení výkonu oproti staršímu 64bitovému kompilátoru JIT.</span><span class="sxs-lookup"><span data-stu-id="75ebc-845">The new 64-bit compiler provides significant performance improvements over the older 64-bit JIT compiler.</span></span> <span data-ttu-id="75ebc-846">Nový 64bitový kompilátor je povolen pro 64bitové procesy spuštěné nad rozhraním .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="75ebc-846">The new 64-bit compiler is enabled for 64-bit processes running on top of .NET Framework 4.6.</span></span> <span data-ttu-id="75ebc-847">Vaše aplikace poběží v 64bitovém procesu, pokud je zkompilován jako 64bitový nebo AnyCPU a běží na 64bitovém operačním systému.</span><span class="sxs-lookup"><span data-stu-id="75ebc-847">Your app will run in a 64-bit process if it is compiled as 64-bit or AnyCPU and is running on a 64-bit operating system.</span></span> <span data-ttu-id="75ebc-848">Zatímco byla věnována pozornost tomu, aby přechod na nový kompilátor byl co nejtransparentnější, změny v chování jsou možné.</span><span class="sxs-lookup"><span data-stu-id="75ebc-848">While care has been taken to make the transition to the new compiler as transparent as possible, changes in behavior are possible.</span></span>

  <span data-ttu-id="75ebc-849">Nový 64bitový kompilátor JIT také obsahuje funkce akcelerace hardwarových SIMD ve spojení s typy s podporou SIMD v <xref:System.Numerics> oboru názvů, což může přinést dobré zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-849">The new 64-bit JIT compiler also includes hardware SIMD acceleration features when coupled with SIMD-enabled types in the <xref:System.Numerics> namespace, which can yield good performance improvements.</span></span>

- <span data-ttu-id="75ebc-850">**Vylepšení montážního nakladače**</span><span class="sxs-lookup"><span data-stu-id="75ebc-850">**Assembly loader improvements**</span></span>

  <span data-ttu-id="75ebc-851">Nakladač sestavy nyní používá paměť efektivněji uvolněním sestavení IL po načtení odpovídajícího obrazu NGEN.</span><span class="sxs-lookup"><span data-stu-id="75ebc-851">The assembly loader now uses memory more efficiently by unloading IL assemblies after a corresponding NGEN image is loaded.</span></span> <span data-ttu-id="75ebc-852">Tato změna snižuje virtuální paměť, což je výhodné zejména pro velké 32bitové aplikace (například Visual Studio) a také šetří fyzickou paměť.</span><span class="sxs-lookup"><span data-stu-id="75ebc-852">This change decreases virtual memory, which is particularly beneficial for large 32-bit apps (such as Visual Studio), and also saves physical memory.</span></span>

- <span data-ttu-id="75ebc-853">**Změny knihovny základních tříd**</span><span class="sxs-lookup"><span data-stu-id="75ebc-853">**Base class library changes**</span></span>

  <span data-ttu-id="75ebc-854">Mnoho nových rozhraní API byly přidány kolem rozhraní .NET Framework 4.6 povolit klíčové scénáře.</span><span class="sxs-lookup"><span data-stu-id="75ebc-854">Many new APIs have been added around to .NET Framework 4.6 to enable key scenarios.</span></span> <span data-ttu-id="75ebc-855">Patří mezi ně následující změny a dodatky:</span><span class="sxs-lookup"><span data-stu-id="75ebc-855">These include the following changes and additions:</span></span>

  - <span data-ttu-id="75ebc-856">**Implementace>\<IReadOnlyCollection**</span><span class="sxs-lookup"><span data-stu-id="75ebc-856">**IReadOnlyCollection\<T> implementations**</span></span>

    <span data-ttu-id="75ebc-857">Další kolekce <xref:System.Collections.Generic.IReadOnlyCollection%601> implementovat, jako <xref:System.Collections.Generic.Queue%601> je například a <xref:System.Collections.Generic.Stack%601>.</span><span class="sxs-lookup"><span data-stu-id="75ebc-857">Additional collections implement <xref:System.Collections.Generic.IReadOnlyCollection%601> such as <xref:System.Collections.Generic.Queue%601> and <xref:System.Collections.Generic.Stack%601>.</span></span>

  - <span data-ttu-id="75ebc-858">**CultureInfo.CurrentCulture a CultureInfo.CurrentUICulture**</span><span class="sxs-lookup"><span data-stu-id="75ebc-858">**CultureInfo.CurrentCulture and CultureInfo.CurrentUICulture**</span></span>

    <span data-ttu-id="75ebc-859"><xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> Vlastnosti <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> a jsou nyní spíše pro čtení a zápis než jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="75ebc-859">The <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> properties are now read-write rather than read-only.</span></span> <span data-ttu-id="75ebc-860">Pokud těmto vlastnostem přiřadíte nový <xref:System.Globalization.CultureInfo> objekt, změní `Thread.CurrentThread.CurrentCulture` se také aktuální jazyková verze `Thread.CurrentThread.CurrentUICulture` vlákna definovaná vlastností a aktuální jazykovou verzí vlákna uživatelského rozhraní definovanou vlastnostmi.</span><span class="sxs-lookup"><span data-stu-id="75ebc-860">If you assign a new <xref:System.Globalization.CultureInfo> object to these properties, the current thread culture defined by the `Thread.CurrentThread.CurrentCulture` property and the current UI thread culture defined by the `Thread.CurrentThread.CurrentUICulture` properties also change.</span></span>

  - <span data-ttu-id="75ebc-861">**Vylepšení uvolňování paměti (GC)**</span><span class="sxs-lookup"><span data-stu-id="75ebc-861">**Enhancements to garbage collection (GC)**</span></span>

    <span data-ttu-id="75ebc-862">Třída <xref:System.GC> nyní <xref:System.GC.TryStartNoGCRegion%2A> obsahuje <xref:System.GC.EndNoGCRegion%2A> a metody, které umožňují zakázat uvolňování paměti během provádění kritické cesty.</span><span class="sxs-lookup"><span data-stu-id="75ebc-862">The <xref:System.GC> class now includes <xref:System.GC.TryStartNoGCRegion%2A> and <xref:System.GC.EndNoGCRegion%2A> methods that allow you to disallow garbage collection during the execution of a critical path.</span></span>

    <span data-ttu-id="75ebc-863">Nové přetížení <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType> metody umožňuje určit, zda haldy malý objekt a haldy velkých objektů jsou zametány a komprimovány nebo pouze zatažené.</span><span class="sxs-lookup"><span data-stu-id="75ebc-863">A new overload of the <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType> method allows you to control whether both the small object heap and the large object heap are swept and compacted or swept only.</span></span>

  - <span data-ttu-id="75ebc-864">**Typy s podporou SIMD**</span><span class="sxs-lookup"><span data-stu-id="75ebc-864">**SIMD-enabled types**</span></span>

    <span data-ttu-id="75ebc-865">Obor <xref:System.Numerics> názvů nyní obsahuje několik typů s podporou <xref:System.Numerics.Matrix3x2>SIMD, například <xref:System.Numerics.Matrix4x4>, <xref:System.Numerics.Plane>, <xref:System.Numerics.Quaternion>, <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, a <xref:System.Numerics.Vector4>.</span><span class="sxs-lookup"><span data-stu-id="75ebc-865">The <xref:System.Numerics> namespace now includes a number of SIMD-enabled types, such as <xref:System.Numerics.Matrix3x2>, <xref:System.Numerics.Matrix4x4>, <xref:System.Numerics.Plane>, <xref:System.Numerics.Quaternion>, <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, and <xref:System.Numerics.Vector4>.</span></span>

    <span data-ttu-id="75ebc-866">Vzhledem k tomu, že nový 64bitový kompilátor JIT obsahuje také funkce akcelerace hardwarových SIMD, existují obzvláště významná vylepšení výkonu při použití typů s podporou SIMD s novým 64bitovým kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="75ebc-866">Because the new 64-bit JIT compiler also includes hardware SIMD acceleration features, there are especially significant performance improvements when using the SIMD-enabled types with the new 64-bit JIT compiler.</span></span>

  - <span data-ttu-id="75ebc-867">**Aktualizace kryptografie**</span><span class="sxs-lookup"><span data-stu-id="75ebc-867">**Cryptography updates**</span></span>

    <span data-ttu-id="75ebc-868">Rozhraní <xref:System.Security.Cryptography?displayProperty=nameWithType> API je aktualizováno tak, aby podporovalo [rozhraní API kryptografie Windows CNG](/windows/desktop/SecCNG/cng-reference).</span><span class="sxs-lookup"><span data-stu-id="75ebc-868">The <xref:System.Security.Cryptography?displayProperty=nameWithType> API is being updated to support the [Windows CNG cryptography APIs](/windows/desktop/SecCNG/cng-reference).</span></span> <span data-ttu-id="75ebc-869">Předchozí verze rozhraní .NET Framework se spoléhaly výhradně na [starší verzi rozhraní API kryptografie systému Windows](/windows/desktop/SecCrypto/cryptography-portal) jako základ pro <xref:System.Security.Cryptography?displayProperty=nameWithType> implementaci.</span><span class="sxs-lookup"><span data-stu-id="75ebc-869">Previous versions of the .NET Framework have relied entirely on an [earlier version of the Windows Cryptography APIs](/windows/desktop/SecCrypto/cryptography-portal) as the basis for the <xref:System.Security.Cryptography?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="75ebc-870">Měli jsme požadavky na podporu Rozhraní API Na CNG, protože podporuje [moderní kryptografické algoritmy](/windows/desktop/SecCNG/cng-features#suite-b-support), které jsou důležité pro určité kategorie aplikací.</span><span class="sxs-lookup"><span data-stu-id="75ebc-870">We have had requests to support the CNG API, since it supports [modern cryptography algorithms](/windows/desktop/SecCNG/cng-features#suite-b-support), which are important for certain categories of apps.</span></span>

    <span data-ttu-id="75ebc-871">Rozhraní .NET Framework 4.6 obsahuje následující nová vylepšení pro podporu rozhraní API kryptografie systému Windows CNG:</span><span class="sxs-lookup"><span data-stu-id="75ebc-871">.NET Framework 4.6 includes the following new enhancements to support the Windows CNG cryptography APIs:</span></span>

    - <span data-ttu-id="75ebc-872">Sada rozšiřujících metod pro certifikáty X509 a `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`, které vracejí implementaci založenou na CNG, nikoli implementaci založenou na CAPI, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="75ebc-872">A set of extension methods for X509 Certificates, `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` and `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`, that return a CNG-based implementation rather than a CAPI-based implementation when possible.</span></span> <span data-ttu-id="75ebc-873">(Některé čipové karty atd., stále vyžadují CAPI a api zpracovat záložní).</span><span class="sxs-lookup"><span data-stu-id="75ebc-873">(Some smartcards, etc., still require CAPI, and the APIs handle the fallback).</span></span>

    - <span data-ttu-id="75ebc-874">Třída, <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> která poskytuje cng implementaci algoritmu RSA.</span><span class="sxs-lookup"><span data-stu-id="75ebc-874">The <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> class, which provides a CNG implementation of the RSA algorithm.</span></span>

    - <span data-ttu-id="75ebc-875">Vylepšení rsa rozhraní API tak, aby běžné akce již nevyžadují přetypování.</span><span class="sxs-lookup"><span data-stu-id="75ebc-875">Enhancements to the RSA API so that common actions no longer require casting.</span></span> <span data-ttu-id="75ebc-876">Například šifrování dat pomocí <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> objektu vyžaduje kód, jako je následující v předchozích verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="75ebc-876">For example, encrypting data using an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> object requires code like the following in previous versions of the .NET Framework.</span></span>

      [!code-csharp[WhatsNew.Casting#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#1)]
      [!code-vb[WhatsNew.Casting#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#1)]

      <span data-ttu-id="75ebc-877">Kód, který používá nová rozhraní API kryptografie v rozhraní .NET Framework 4.6 lze přepsat následujícím způsobem, aby se zabránilo přetypování.</span><span class="sxs-lookup"><span data-stu-id="75ebc-877">Code that uses the new cryptography APIs in .NET Framework 4.6 can be rewritten as follows to avoid the cast.</span></span>

      [!code-csharp[WhatsNew.Casting#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#2)]
      [!code-vb[WhatsNew.Casting#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#2)]

  - <span data-ttu-id="75ebc-878">**Podpora pro převod dat a časů do nebo z Unixu**</span><span class="sxs-lookup"><span data-stu-id="75ebc-878">**Support for converting dates and times to or from Unix time**</span></span>

    <span data-ttu-id="75ebc-879">Do <xref:System.DateTimeOffset> struktury byly přidány následující nové metody, které podporují převod hodnot data a času na čas unixu nebo z něj:</span><span class="sxs-lookup"><span data-stu-id="75ebc-879">The following new methods have been added to the <xref:System.DateTimeOffset> structure to support converting date and time values to or from Unix time:</span></span>

    - <xref:System.DateTimeOffset.FromUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.FromUnixTimeMilliseconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeMilliseconds%2A?displayProperty=nameWithType>

  - <span data-ttu-id="75ebc-880">**Přepínače kompatibility**</span><span class="sxs-lookup"><span data-stu-id="75ebc-880">**Compatibility switches**</span></span>

    <span data-ttu-id="75ebc-881">Třída <xref:System.AppContext> přidává novou funkci kompatibility, která umožňuje autorům knihovny poskytnout jednotný mechanismus odhlášení pro nové funkce pro své uživatele.</span><span class="sxs-lookup"><span data-stu-id="75ebc-881">The <xref:System.AppContext> class adds a new compatibility feature that enables library writers to provide a uniform opt-out mechanism for new functionality for their users.</span></span> <span data-ttu-id="75ebc-882">Stanoví volně vázanou smlouvu mezi součástmi za účelem sdělení žádosti o výjimku.</span><span class="sxs-lookup"><span data-stu-id="75ebc-882">It establishes a loosely coupled contract between components in order to communicate an opt-out request.</span></span> <span data-ttu-id="75ebc-883">Tato funkce je obvykle důležité při změně existující funkce.</span><span class="sxs-lookup"><span data-stu-id="75ebc-883">This capability is typically important when a change is made to existing functionality.</span></span> <span data-ttu-id="75ebc-884">Naopak již existuje implicitní přihlášení pro nové funkce.</span><span class="sxs-lookup"><span data-stu-id="75ebc-884">Conversely, there is already an implicit opt-in for new functionality.</span></span>

    <span data-ttu-id="75ebc-885">S <xref:System.AppContext>, knihovny definovat a vystavit přepínače kompatibility, zatímco kód, který závisí na nich můžete nastavit tyto přepínače ovlivnit chování knihovny.</span><span class="sxs-lookup"><span data-stu-id="75ebc-885">With <xref:System.AppContext>, libraries define and expose compatibility switches, while code that depends on them can set those switches to affect the library behavior.</span></span> <span data-ttu-id="75ebc-886">Ve výchozím nastavení knihovny poskytují nové funkce a mění je pouze (to znamená, že poskytují předchozí funkce) pokud je přepínač nastaven.</span><span class="sxs-lookup"><span data-stu-id="75ebc-886">By default, libraries provide the new functionality, and they only alter it (that is, they provide the previous functionality) if the switch is set.</span></span>

    <span data-ttu-id="75ebc-887">Aplikace (nebo knihovna) může deklarovat hodnotu <xref:System.Boolean> přepínače (což je vždy hodnota), kterou definuje závislá knihovna.</span><span class="sxs-lookup"><span data-stu-id="75ebc-887">An application (or a library) can declare the value of a switch (which is always a <xref:System.Boolean> value) that a dependent library defines.</span></span> <span data-ttu-id="75ebc-888">Přepínač je vždy `false`implicitně .</span><span class="sxs-lookup"><span data-stu-id="75ebc-888">The switch is always implicitly `false`.</span></span> <span data-ttu-id="75ebc-889">Nastavení přepínače `true` na umožňuje.</span><span class="sxs-lookup"><span data-stu-id="75ebc-889">Setting the switch to `true` enables it.</span></span> <span data-ttu-id="75ebc-890">Explicitně nastavení `false` přepínače poskytuje nové chování.</span><span class="sxs-lookup"><span data-stu-id="75ebc-890">Explicitly setting the switch to `false` provides the new behavior.</span></span>

    ```csharp
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);
    ```

    ```vb
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", True)
    ```

    <span data-ttu-id="75ebc-891">Knihovna musí zkontrolovat, zda spotřebitel deklaroval hodnotu přepínače, a poté na něj vhodně jednat.</span><span class="sxs-lookup"><span data-stu-id="75ebc-891">The library must check if a consumer has declared the value of the switch and then appropriately act on it.</span></span>

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

    <span data-ttu-id="75ebc-892">Je výhodné používat konzistentní formát pro přepínače, protože se jedná o formální smlouvu vystavenou knihovnou.</span><span class="sxs-lookup"><span data-stu-id="75ebc-892">It's beneficial to use a consistent format for switches, since they are a formal contract exposed by a library.</span></span> <span data-ttu-id="75ebc-893">Následují dva zřejmé formáty.</span><span class="sxs-lookup"><span data-stu-id="75ebc-893">The following are two obvious formats.</span></span>

    - <span data-ttu-id="75ebc-894">*Přepněte*. *oboru názvů*. *název přepínače*</span><span class="sxs-lookup"><span data-stu-id="75ebc-894">*Switch*.*namespace*.*switchname*</span></span>

    - <span data-ttu-id="75ebc-895">*Přepněte*. *knihovny*. *název přepínače*</span><span class="sxs-lookup"><span data-stu-id="75ebc-895">*Switch*.*library*.*switchname*</span></span>

  - <span data-ttu-id="75ebc-896">**Změny asynchronního vzoru založeného na úlohách (TAP)**</span><span class="sxs-lookup"><span data-stu-id="75ebc-896">**Changes to the task-based asynchronous pattern (TAP)**</span></span>

    <span data-ttu-id="75ebc-897">Pro aplikace, které cílí na <xref:System.Threading.Tasks.Task> rozhraní <xref:System.Threading.Tasks.Task%601> .NET Framework 4.6 a objekty dědí jazykovou verzi a jazykovou verzi uživatelského rozhraní volajícího vlákna.</span><span class="sxs-lookup"><span data-stu-id="75ebc-897">For apps that target the .NET Framework 4.6, <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects inherit the culture and UI culture of the calling thread.</span></span> <span data-ttu-id="75ebc-898">Chování aplikací, které cílí na předchozí verze rozhraní .NET Framework nebo které necílí na konkrétní verzi rozhraní .NET Framework, není ovlivněno.</span><span class="sxs-lookup"><span data-stu-id="75ebc-898">The behavior of apps that target previous versions of the .NET Framework, or that do not target a specific version of the .NET Framework, is unaffected.</span></span> <span data-ttu-id="75ebc-899">Další informace naleznete v části "Jazykové verze a úlohy asynchronní operace" v tématu <xref:System.Globalization.CultureInfo> třídy.</span><span class="sxs-lookup"><span data-stu-id="75ebc-899">For more information, see the "Culture and task-based asynchronous operations" section of the <xref:System.Globalization.CultureInfo> class topic.</span></span>

    <span data-ttu-id="75ebc-900">Třída <xref:System.Threading.AsyncLocal%601?displayProperty=nameWithType> umožňuje reprezentovat okolní data, která je místní pro daný tok `async` asynchronního řízení, jako je například metoda.</span><span class="sxs-lookup"><span data-stu-id="75ebc-900">The <xref:System.Threading.AsyncLocal%601?displayProperty=nameWithType> class allows you to represent ambient data that is local to a given asynchronous control flow, such as an `async` method.</span></span> <span data-ttu-id="75ebc-901">Lze použít k uchování dat ve vláknech.</span><span class="sxs-lookup"><span data-stu-id="75ebc-901">It can be used to persist data across threads.</span></span> <span data-ttu-id="75ebc-902">Můžete také definovat metodu zpětného volání, která je upozorňována vždy, když se změní okolní data, protože <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=nameWithType> vlastnost byla explicitně změněna, nebo proto, že vlákno narazilo na přechod kontextu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-902">You can also define a callback method that is notified whenever the ambient data changes either because the <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=nameWithType> property was explicitly changed, or because the thread encountered a context transition.</span></span>

    <span data-ttu-id="75ebc-903">Do asynchronního vzoru založeného na úlohách (TAP) byly přidány tři metody pohodlí <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=nameWithType>, a <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=nameWithType>, které mají vrátit dokončené úkoly v určitém stavu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-903">Three convenience methods, <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=nameWithType>, have been added to the task-based asynchronous pattern (TAP) to return completed tasks in a particular state.</span></span>

    <span data-ttu-id="75ebc-904">Třída <xref:System.IO.Pipes.NamedPipeClientStream> nyní podporuje asynchronní komunikaci <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A>s novým .</span><span class="sxs-lookup"><span data-stu-id="75ebc-904">The <xref:System.IO.Pipes.NamedPipeClientStream> class now supports asynchronous communication with its new <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A>.</span></span> <span data-ttu-id="75ebc-905">Metoda.</span><span class="sxs-lookup"><span data-stu-id="75ebc-905">method.</span></span>

  - <span data-ttu-id="75ebc-906">**EventSource nyní podporuje zápis do protokolu událostí**</span><span class="sxs-lookup"><span data-stu-id="75ebc-906">**EventSource now supports writing to the Event log**</span></span>

    <span data-ttu-id="75ebc-907">Nyní můžete použít <xref:System.Diagnostics.Tracing.EventSource> třídu k protokolování administrativních nebo provozních zpráv do protokolu událostí, kromě všech existujících relací ETW vytvořených v počítači.</span><span class="sxs-lookup"><span data-stu-id="75ebc-907">You now can use the <xref:System.Diagnostics.Tracing.EventSource> class to log administrative or operational messages to the event log, in addition to any existing ETW sessions created on the machine.</span></span> <span data-ttu-id="75ebc-908">V minulosti jste museli použít Microsoft.Diagnostics.Tracing.EventSource NuGet balíček pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="75ebc-908">In the past, you had to use the Microsoft.Diagnostics.Tracing.EventSource NuGet package for this functionality.</span></span> <span data-ttu-id="75ebc-909">Tato funkce je nyní integrována do rozhraní .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="75ebc-909">This functionality is now built-into .NET Framework 4.6.</span></span>

    <span data-ttu-id="75ebc-910">Balíček NuGet i rozhraní .NET Framework 4.6 byly aktualizovány následujícími funkcemi:</span><span class="sxs-lookup"><span data-stu-id="75ebc-910">Both the NuGet package and .NET Framework 4.6 have been updated with the following features:</span></span>

    - <span data-ttu-id="75ebc-911">**Dynamické události**</span><span class="sxs-lookup"><span data-stu-id="75ebc-911">**Dynamic events**</span></span>

      <span data-ttu-id="75ebc-912">Umožňuje události definované "průběžně" bez vytváření metod událostí.</span><span class="sxs-lookup"><span data-stu-id="75ebc-912">Allows events defined "on the fly" without creating event methods.</span></span>

    - <span data-ttu-id="75ebc-913">**Bohatá návratnost**</span><span class="sxs-lookup"><span data-stu-id="75ebc-913">**Rich payloads**</span></span>

      <span data-ttu-id="75ebc-914">Umožňuje předat speciálně přiřazené třídy a pole a primitivní typy jako datovou část.</span><span class="sxs-lookup"><span data-stu-id="75ebc-914">Allows specially attributed classes and arrays as well as primitive types to be passed as a payload</span></span>

    - <span data-ttu-id="75ebc-915">**Sledování aktivity**</span><span class="sxs-lookup"><span data-stu-id="75ebc-915">**Activity tracking**</span></span>

      <span data-ttu-id="75ebc-916">Způsobí, že události Start a Stop označí události mezi nimi id, které představuje všechny aktuálně aktivní aktivity.</span><span class="sxs-lookup"><span data-stu-id="75ebc-916">Causes Start and Stop events to tag events between them with an ID that represents all currently active activities.</span></span>

    <span data-ttu-id="75ebc-917">Pro podporu těchto funkcí <xref:System.Diagnostics.Tracing.EventSource.Write%2A> byla přetížená metoda <xref:System.Diagnostics.Tracing.EventSource> přidána do třídy.</span><span class="sxs-lookup"><span data-stu-id="75ebc-917">To support these features, the overloaded <xref:System.Diagnostics.Tracing.EventSource.Write%2A> method has been added to the <xref:System.Diagnostics.Tracing.EventSource> class.</span></span>

- <span data-ttu-id="75ebc-918">**Windows Presentation Foundation (WPF)**</span><span class="sxs-lookup"><span data-stu-id="75ebc-918">**Windows Presentation Foundation (WPF)**</span></span>

  - <span data-ttu-id="75ebc-919">**Vylepšení HDPI**</span><span class="sxs-lookup"><span data-stu-id="75ebc-919">**HDPI improvements**</span></span>

    <span data-ttu-id="75ebc-920">Podpora HDPI v WPF je nyní lepší v rozhraní .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="75ebc-920">HDPI support in WPF is now better in the .NET Framework 4.6.</span></span> <span data-ttu-id="75ebc-921">Byly provedeny změny zaokrouhlení rozložení, aby se snížilpočet výskytů oříznutí v ovládacích prvcích s ohraničením.</span><span class="sxs-lookup"><span data-stu-id="75ebc-921">Changes have been made to layout rounding to reduce instances of clipping in controls with borders.</span></span> <span data-ttu-id="75ebc-922">Ve výchozím nastavení je tato <xref:System.Runtime.Versioning.TargetFrameworkAttribute> funkce povolena pouze v případě, že je nastavena na hodnotu .NET 4.6.</span><span class="sxs-lookup"><span data-stu-id="75ebc-922">By default, this feature is enabled only if your <xref:System.Runtime.Versioning.TargetFrameworkAttribute> is set to .NET 4.6.</span></span>  <span data-ttu-id="75ebc-923">Aplikace, které cílí na starší verze rozhraní, ale jsou spuštěny v rozhraní .NET Framework 4.6, se mohou přihlásit k novému chování přidáním následujícího řádku do sekce [ \<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="75ebc-923">Applications that target earlier versions of the framework but are running on the .NET Framework 4.6 can opt in to the new behavior by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app.config file:</span></span>

    ```xml
    <AppContextSwitchOverrides
    value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"
    />
    ```

    <span data-ttu-id="75ebc-924">WPF okna tažné více monitorů s různými nastaveními DPI (Nastavení Více DPI) jsou nyní zcela vykresleny bez zatemnění oblastí.</span><span class="sxs-lookup"><span data-stu-id="75ebc-924">WPF windows straddling multiple monitors with different DPI settings (Multi-DPI setup) are now completely rendered without blacked-out regions.</span></span> <span data-ttu-id="75ebc-925">Toto chování můžete odhlásit tak, že `<appSettings>` do části souboru app.config zakážete následující řádek:</span><span class="sxs-lookup"><span data-stu-id="75ebc-925">You can opt out of this behavior by adding the following line to the `<appSettings>` section of the app.config file to disable this new behavior:</span></span>

    ```xml
    <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    ```

    <span data-ttu-id="75ebc-926">Do aplikace byla přidána podpora automatického načítání <xref:System.Windows.Input.Cursor?displayProperty=nameWithType>pravého kurzoru na základě nastavení DPI.</span><span class="sxs-lookup"><span data-stu-id="75ebc-926">Support for automatically loading the right cursor based on DPI setting has been added to  <xref:System.Windows.Input.Cursor?displayProperty=nameWithType>.</span></span>

  - <span data-ttu-id="75ebc-927">**Dotek je lepší**</span><span class="sxs-lookup"><span data-stu-id="75ebc-927">**Touch is better**</span></span>

    <span data-ttu-id="75ebc-928">V rozhraní .NET Framework 4.6 byly vyřešeny zákaznické zprávy o [připojení,](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) které dotykem vytváří nepředvídatelné chování.</span><span class="sxs-lookup"><span data-stu-id="75ebc-928">Customer reports on [Connect](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) that touch produces unpredictable behavior have been addressed in the .NET Framework 4.6.</span></span> <span data-ttu-id="75ebc-929">Prahová hodnota dvojitého klepnutí pro aplikace pro Windows Store a WPF je teď stejná ve Windows 8.1 a vyšší.</span><span class="sxs-lookup"><span data-stu-id="75ebc-929">The double tap threshold for Windows Store applications and WPF applications is now the same in Windows 8.1 and above.</span></span>

  - <span data-ttu-id="75ebc-930">**Průhledná podřízená podpora okna**</span><span class="sxs-lookup"><span data-stu-id="75ebc-930">**Transparent child window support**</span></span>

    <span data-ttu-id="75ebc-931">WPF v rozhraní .NET Framework 4.6 podporuje transparentní podřízená okna ve Windows 8.1 a vyšší.</span><span class="sxs-lookup"><span data-stu-id="75ebc-931">WPF in the .NET Framework 4.6 supports transparent child windows in Windows 8.1 and above.</span></span> <span data-ttu-id="75ebc-932">To umožňuje vytvářet neobdélníková a průhledná podřízená okna v oknech nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="75ebc-932">This allows you to create non-rectangular and transparent child windows in your top-level windows.</span></span> <span data-ttu-id="75ebc-933">Tuto funkci můžete povolit <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=nameWithType> nastavením vlastnosti na . `true`</span><span class="sxs-lookup"><span data-stu-id="75ebc-933">You can enable this feature by setting the <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=nameWithType> property to `true`.</span></span>

- <span data-ttu-id="75ebc-934">**Windows Communication Foundation (WCF)**</span><span class="sxs-lookup"><span data-stu-id="75ebc-934">**Windows Communication Foundation (WCF)**</span></span>

  - <span data-ttu-id="75ebc-935">**Podpora pro SSL**</span><span class="sxs-lookup"><span data-stu-id="75ebc-935">**SSL support**</span></span>

    <span data-ttu-id="75ebc-936">WCF nyní podporuje SSL verze TLS 1.1 a TLS 1.2, kromě SSL 3.0 a TLS 1.0, při použití NetTcp s zabezpečením přenosu a ověřování klienta.</span><span class="sxs-lookup"><span data-stu-id="75ebc-936">WCF now supports SSL version TLS 1.1 and TLS 1.2, in addition to SSL 3.0 and TLS 1.0, when using NetTcp with transport security and client authentication.</span></span> <span data-ttu-id="75ebc-937">Nyní je možné vybrat, který protokol použít, nebo zakázat staré méně zabezpečené protokoly.</span><span class="sxs-lookup"><span data-stu-id="75ebc-937">It is now possible to select which protocol to use, or to disable old lesser secure protocols.</span></span> <span data-ttu-id="75ebc-938">To lze provést nastavením <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> vlastnosti nebo přidáním následujícího do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="75ebc-938">This can be done either by setting the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> property or by adding the following to a configuration file.</span></span>

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

  - <span data-ttu-id="75ebc-939">**Odesílání zpráv pomocí různých připojení HTTP**</span><span class="sxs-lookup"><span data-stu-id="75ebc-939">**Sending messages using different HTTP connections**</span></span>

    <span data-ttu-id="75ebc-940">WCF nyní umožňuje uživatelům zajistit, že některé zprávy jsou odesílány pomocí různých základních připojení HTTP.</span><span class="sxs-lookup"><span data-stu-id="75ebc-940">WCF now allows users to ensure certain messages are sent using different underlying HTTP connections.</span></span> <span data-ttu-id="75ebc-941">Toto lze provést dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="75ebc-941">There are two ways to do this:</span></span>

    - <span data-ttu-id="75ebc-942">**Použití předpony názvu skupiny připojení**</span><span class="sxs-lookup"><span data-stu-id="75ebc-942">**Using a connection group name prefix**</span></span>

      <span data-ttu-id="75ebc-943">Uživatelé mohou zadat řetězec, který wcf použije jako předponu pro název skupiny připojení.</span><span class="sxs-lookup"><span data-stu-id="75ebc-943">Users can specify a string that WCF will use as a prefix for the connection group name.</span></span> <span data-ttu-id="75ebc-944">Dvě zprávy s různými předponami jsou odesílány pomocí různých základních připojení HTTP.</span><span class="sxs-lookup"><span data-stu-id="75ebc-944">Two messages with different prefixes are sent using different underlying HTTP connections.</span></span> <span data-ttu-id="75ebc-945">Předponu nastavíte přidáním páru klíč/hodnota <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=nameWithType> do vlastnosti zprávy.</span><span class="sxs-lookup"><span data-stu-id="75ebc-945">You set the prefix by adding a key/value pair to the message's <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="75ebc-946">Klíč je "HttpTransportConnectionGroupNamePrefix"; hodnota je požadovaná předpona.</span><span class="sxs-lookup"><span data-stu-id="75ebc-946">The key is "HttpTransportConnectionGroupNamePrefix"; the value is the desired prefix.</span></span>

    - <span data-ttu-id="75ebc-947">**Použití různých továren kanálů**</span><span class="sxs-lookup"><span data-stu-id="75ebc-947">**Using different channel factories**</span></span>

      <span data-ttu-id="75ebc-948">Uživatelé mohou také povolit funkci, která zajišťuje, že zprávy odeslané pomocí kanálů vytvořených různými továrnami kanálů budou používat různá základní připojení HTTP.</span><span class="sxs-lookup"><span data-stu-id="75ebc-948">Users can also enable a feature that ensures that messages sent using channels created by different channel factories will use different underlying HTTP connections.</span></span> <span data-ttu-id="75ebc-949">Chcete-li tuto funkci povolit, `true`musí uživatelé nastavit následující: `appSetting`</span><span class="sxs-lookup"><span data-stu-id="75ebc-949">To enable this feature, users must set the following `appSetting` to `true`:</span></span>

      ```xml
      <appSettings>
          <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />
      </appSettings>
      ```

- <span data-ttu-id="75ebc-950">**Nadace pracovního postupu systému Windows (WWF)**</span><span class="sxs-lookup"><span data-stu-id="75ebc-950">**Windows Workflow Foundation (WWF)**</span></span>

  <span data-ttu-id="75ebc-951">Nyní můžete určit počet sekund, po které bude služba pracovního postupu držet požadavek na operaci mimo pořadí, pokud je před vypršením požadavku nevyřešená záložka "bez protokolu".</span><span class="sxs-lookup"><span data-stu-id="75ebc-951">You can now specify the number of seconds a workflow service will hold on to an out-of-order operation request when there is an outstanding "non-protocol" bookmark before timing out the request.</span></span> <span data-ttu-id="75ebc-952">Záložka "non-protokol" je záložka, která nesouvisí s nevyřízenými aktivitami příjmu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-952">A "non-protocol" bookmark is a bookmark that is not related to outstanding Receive activities.</span></span> <span data-ttu-id="75ebc-953">Některé aktivity vytvářejí záložky bez protokolu v rámci jejich implementace, takže nemusí být zřejmé, že existuje záložka bez protokolu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-953">Some activities create non-protocol bookmarks within their implementation, so it may not be obvious that a non-protocol bookmark exists.</span></span> <span data-ttu-id="75ebc-954">Patří mezi ně stát a pick.</span><span class="sxs-lookup"><span data-stu-id="75ebc-954">These include State and Pick.</span></span> <span data-ttu-id="75ebc-955">Pokud tedy máte službu pracovního postupu implementovanou se stavovým počítačem nebo obsahující aktivitu vyskladnění, budete mít s největší pravděpodobností záložky bez protokolu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-955">So if you have a workflow service implemented with a state machine or containing a Pick activity, you will most likely have non-protocol bookmarks.</span></span> <span data-ttu-id="75ebc-956">Interval určíte přidáním řádku, jako `appSettings` je následující, do oddílu souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="75ebc-956">You specify the interval by adding a line like the following to the `appSettings` section of your app.config file:</span></span>

  ```xml
  <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>
  ```

  <span data-ttu-id="75ebc-957">Výchozí hodnota je 60 sekund.</span><span class="sxs-lookup"><span data-stu-id="75ebc-957">The default value is 60 seconds.</span></span> <span data-ttu-id="75ebc-958">Pokud `value` je nastavena na 0, požadavky mimo pořadí jsou okamžitě odmítnuty s chybou s textem, který vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="75ebc-958">If `value` is set to 0, out-of-order requests are immediately rejected with a fault with text that looks like this:</span></span>

  ```console
  Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees.
  ```

  <span data-ttu-id="75ebc-959">Jedná se o stejnou zprávu, kterou obdržíte, pokud je přijata zpráva operace mimo pořadí a neexistují žádné záložky bez protokolu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-959">This is the same message that you receive if an out-of-order operation message is received and there are no non-protocol bookmarks.</span></span>

  <span data-ttu-id="75ebc-960">Pokud je hodnota `FilterResumeTimeoutInSeconds` prvku nenulová, existují záložky bez protokolu a vyprší časový limit, operace se nezdaří se zprávou časového limitu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-960">If the value of the `FilterResumeTimeoutInSeconds` element is non-zero, there are non-protocol bookmarks, and the timeout interval expires, the operation fails with a timeout message.</span></span>

- <span data-ttu-id="75ebc-961">**Transakce**</span><span class="sxs-lookup"><span data-stu-id="75ebc-961">**Transactions**</span></span>

  <span data-ttu-id="75ebc-962">Nyní můžete zahrnout identifikátor distribuované transakce pro transakci, <xref:System.Transactions.TransactionException> která způsobila výjimku odvozenou z vyvolat.</span><span class="sxs-lookup"><span data-stu-id="75ebc-962">You can now include the distributed transaction identifier for the transaction that has caused an exception derived from <xref:System.Transactions.TransactionException> to be thrown.</span></span> <span data-ttu-id="75ebc-963">To provést přidáním následujícího `appSettings` klíče do části souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="75ebc-963">You do this by adding the following key to the `appSettings` section of your app.config file:</span></span>

  ```xml
  <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/>
  ```

  <span data-ttu-id="75ebc-964">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="75ebc-964">The default value is `false`.</span></span>

- <span data-ttu-id="75ebc-965">**Sítě**</span><span class="sxs-lookup"><span data-stu-id="75ebc-965">**Networking**</span></span>

  - <span data-ttu-id="75ebc-966">**Opětovné použití soketu**</span><span class="sxs-lookup"><span data-stu-id="75ebc-966">**Socket reuse**</span></span>

    <span data-ttu-id="75ebc-967">Systém Windows 10 obsahuje nový síťový algoritmus s vysokou škálovatelností, který lépe využívá prostředky počítače opětovným použitím místních portů pro odchozí připojení TCP.</span><span class="sxs-lookup"><span data-stu-id="75ebc-967">Windows 10 includes a new high-scalability networking algorithm that makes better use of machine resources by reusing local ports for outbound TCP connections.</span></span> <span data-ttu-id="75ebc-968">Rozhraní .NET Framework 4.6 podporuje nový algoritmus, který umožňuje aplikacím .NET využít výhod nového chování.</span><span class="sxs-lookup"><span data-stu-id="75ebc-968">.NET Framework 4.6 supports the new algorithm, enabling .NET apps to take advantage of the new behavior.</span></span> <span data-ttu-id="75ebc-969">V předchozích verzích systému Windows byl umělý limit souběžného připojení (obvykle 16 384, výchozí velikost dynamického rozsahu portů), což může omezit škálovatelnost služby tím, že způsobí vyčerpání portu při zatížení.</span><span class="sxs-lookup"><span data-stu-id="75ebc-969">In previous versions of Windows, there was an artificial concurrent connection limit (typically 16,384, the default size of the dynamic port range), which could limit the scalability of a service by causing port exhaustion when under load.</span></span>

    <span data-ttu-id="75ebc-970">V rozhraní .NET Framework 4.6 byla přidána dvě rozhraní API, která umožňují opakované použití portu, což účinně odebere limit 64 kB pro souběžná připojení:</span><span class="sxs-lookup"><span data-stu-id="75ebc-970">In .NET Framework 4.6, two APIs have been added to enable port reuse, which effectively removes the 64 KB limit on concurrent connections:</span></span>

    - <span data-ttu-id="75ebc-971">Hodnota <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> výčtu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-971">The <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> enumeration value.</span></span>

    - <span data-ttu-id="75ebc-972">Pozemek. <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="75ebc-972">The <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> property.</span></span>

    <span data-ttu-id="75ebc-973">Ve výchozím <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> nastavení `false` je `HWRPortReuseOnSocketBind` vlastnost, `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` pokud je hodnota klíče registru nastavena na 0x1.</span><span class="sxs-lookup"><span data-stu-id="75ebc-973">By default, the <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> property is `false` unless the `HWRPortReuseOnSocketBind` value of the `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` registry key is set to 0x1.</span></span> <span data-ttu-id="75ebc-974">Chcete-li povolit opakované použití místního <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> `true`portu v připojeních HTTP, nastavte vlastnost na .</span><span class="sxs-lookup"><span data-stu-id="75ebc-974">To enable local port reuse on HTTP connections, set the <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="75ebc-975">To způsobí, že všechna odchozí <xref:System.Net.Http.HttpClient> <xref:System.Net.HttpWebRequest> připojení soketu TCP z a použít novou možnost soketu systému Windows 10, [SO_REUSE_UNICASTPORT](/windows/desktop/WinSock/sol-socket-socket-options), který umožňuje opětovné použití místního portu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-975">This causes all outgoing TCP socket connections from <xref:System.Net.Http.HttpClient> and <xref:System.Net.HttpWebRequest> to use a new Windows 10 socket option, [SO_REUSE_UNICASTPORT](/windows/desktop/WinSock/sol-socket-socket-options), that enables local port reuse.</span></span>

    <span data-ttu-id="75ebc-976">Vývojáři, kteří píší pouze sokety aplikace můžete určit <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> možnost při volání metody, například <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> tak, aby odchozí sokety znovu použít místní porty během vazby.</span><span class="sxs-lookup"><span data-stu-id="75ebc-976">Developers writing a sockets-only application can specify the <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> option when calling a method such as <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> so that outbound sockets reuse local ports during binding.</span></span>

  - <span data-ttu-id="75ebc-977">**Podpora mezinárodních doménových jmen a PunyCode**</span><span class="sxs-lookup"><span data-stu-id="75ebc-977">**Support for international domain names and PunyCode**</span></span>

    <span data-ttu-id="75ebc-978">Do <xref:System.Uri> třídy <xref:System.Uri.IdnHost%2A>byla přidána nová vlastnost , která má lépe podporovat mezinárodní názvy domén a PunyCode.</span><span class="sxs-lookup"><span data-stu-id="75ebc-978">A new property, <xref:System.Uri.IdnHost%2A>, has been added to the <xref:System.Uri> class to better support international domain names and PunyCode.</span></span>

- <span data-ttu-id="75ebc-979">**Změna velikosti ovládacích prvků v systému Windows Forms.**</span><span class="sxs-lookup"><span data-stu-id="75ebc-979">**Resizing in Windows Forms controls.**</span></span>

  <span data-ttu-id="75ebc-980">Tato funkce byla rozšířena v rozhraní .NET <xref:System.Windows.Forms.DomainUpDown> <xref:System.Windows.Forms.NumericUpDown>Framework <xref:System.Windows.Forms.DataGridViewComboBoxColumn> <xref:System.Windows.Forms.DataGridViewColumn> 4.6 tak, aby zahrnovala typy , , a a <xref:System.Windows.Forms.ToolStripSplitButton> obdélník určený <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> vlastností použitou při kreslení . <xref:System.Drawing.Design.UITypeEditor></span><span class="sxs-lookup"><span data-stu-id="75ebc-980">This feature has been expanded in .NET Framework 4.6 to include the <xref:System.Windows.Forms.DomainUpDown>, <xref:System.Windows.Forms.NumericUpDown>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.ToolStripSplitButton> types and the rectangle specified by the <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> property used when drawing a <xref:System.Drawing.Design.UITypeEditor>.</span></span>

  <span data-ttu-id="75ebc-981">Jedná se o funkci opt-in.</span><span class="sxs-lookup"><span data-stu-id="75ebc-981">This is an opt-in feature.</span></span> <span data-ttu-id="75ebc-982">Chcete-li jej `EnableWindowsFormsHighDpiAutoResizing` povolit, nastavte prvek v `true` souboru konfigurace aplikace (app.config):</span><span class="sxs-lookup"><span data-stu-id="75ebc-982">To enable it, set the `EnableWindowsFormsHighDpiAutoResizing` element to `true` in the application configuration (app.config) file:</span></span>

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- <span data-ttu-id="75ebc-983">**Podpora kódování znakových stránek**</span><span class="sxs-lookup"><span data-stu-id="75ebc-983">**Support for code page encodings**</span></span>

  <span data-ttu-id="75ebc-984">.NET Core primárně podporuje kódování Unicode a ve výchozím nastavení poskytuje omezenou podporu kódování znakových stránek.</span><span class="sxs-lookup"><span data-stu-id="75ebc-984">.NET Core primarily supports the Unicode encodings and by default provides limited support for code page encodings.</span></span> <span data-ttu-id="75ebc-985">Můžete přidat podporu pro kódování znakových stránek, které jsou k dispozici v rozhraní .NET Framework, ale nejsou podporovány v rozhraní .NET Core registrací kódování znakové stránky pomocí <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="75ebc-985">You can add support for code page encodings available in .NET Framework but unsupported in .NET Core by registering code page encodings with the <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="75ebc-986">Další informace naleznete v tématu <xref:System.Text.CodePagesEncodingProvider?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="75ebc-986">For more information, see <xref:System.Text.CodePagesEncodingProvider?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="75ebc-987">**.NET Native**</span><span class="sxs-lookup"><span data-stu-id="75ebc-987">**.NET Native**</span></span>

  <span data-ttu-id="75ebc-988">Aplikace pro Windows pro Windows 10, které cílí na .NET Core a jsou zapsány v Jazyce C# nebo Visual Basicu, můžou využít novou technologii, která kompiluje aplikace do nativního kódu, nikoli do IL.</span><span class="sxs-lookup"><span data-stu-id="75ebc-988">Windows apps for Windows 10 that target .NET Core and are written in C# or Visual Basic can take advantage of a new technology that compiles apps to native code rather than IL.</span></span> <span data-ttu-id="75ebc-989">Vyrábějí aplikace charakterizované rychlejším spouštěním a spouštěním.</span><span class="sxs-lookup"><span data-stu-id="75ebc-989">They produce apps characterized by faster startup and execution times.</span></span> <span data-ttu-id="75ebc-990">Další informace naleznete [v tématu Kompilace aplikací s nativním rozhraním .NET](../net-native/index.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-990">For more information, see [Compiling Apps with .NET Native](../net-native/index.md).</span></span> <span data-ttu-id="75ebc-991">Přehled nativní .NET, který zkoumá, jak se liší od kompilace JIT a NGEN a co to znamená pro váš kód, naleznete [v tématu .NET Native a Kompilace](../net-native/net-native-and-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-991">For an overview of .NET Native that examines how it differs from both JIT compilation and NGEN and what that means for your code, see [.NET Native and Compilation](../net-native/net-native-and-compilation.md).</span></span>

  <span data-ttu-id="75ebc-992">Vaše aplikace se ve výchozím nastavení kompitují do nativního kódu, když je zkompilujete pomocí Visual Studia 2015 nebo novějšího.</span><span class="sxs-lookup"><span data-stu-id="75ebc-992">Your apps are compiled to native code by default when you compile them with Visual Studio 2015 or later.</span></span> <span data-ttu-id="75ebc-993">Další informace naleznete [v tématu Začínáme s nativním programem .NET](../net-native/getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-993">For more information, see [Getting Started with .NET Native](../net-native/getting-started-with-net-native.md).</span></span>

  <span data-ttu-id="75ebc-994">Pro podporu ladění nativních aplikací .NET byla do nespravovaného rozhraní API ladění přidána řada nových rozhraní a výčtů.</span><span class="sxs-lookup"><span data-stu-id="75ebc-994">To support debugging .NET Native apps, a number of new interfaces and enumerations have been added to the unmanaged debugging API.</span></span> <span data-ttu-id="75ebc-995">Další informace naleznete v tématu [Ladění (Unmanaged API Reference).](../unmanaged-api/debugging/index.md)</span><span class="sxs-lookup"><span data-stu-id="75ebc-995">For more information, see the [Debugging (Unmanaged API Reference)](../unmanaged-api/debugging/index.md) topic.</span></span>

- <span data-ttu-id="75ebc-996">**Balíčky rozhraní Open source .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="75ebc-996">**Open-source .NET Framework packages**</span></span>

  <span data-ttu-id="75ebc-997">Balíčky .NET Core, jako jsou neměnné kolekce, [rozhraní API SIMD](https://www.nuget.org/packages/Microsoft.Bcl.Simd)a <xref:System.Net.Http> síťová rozhraní API, jako jsou například ty, které se nacházejí v oboru názvů, jsou nyní k dispozici jako balíčky s otevřeným zdrojovým kódem na [GitHubu](https://github.com/).</span><span class="sxs-lookup"><span data-stu-id="75ebc-997">.NET Core packages such as the immutable collections, [SIMD APIs](https://www.nuget.org/packages/Microsoft.Bcl.Simd), and networking APIs such as those found in the <xref:System.Net.Http> namespace are now available as open-source packages on [GitHub](https://github.com/).</span></span> <span data-ttu-id="75ebc-998">Chcete-li získat přístup ke kódu, přečtěte si [stránku .NET na GitHubu](https://github.com/dotnet/runtime).</span><span class="sxs-lookup"><span data-stu-id="75ebc-998">To access the code, see [.NET on GitHub](https://github.com/dotnet/runtime).</span></span> <span data-ttu-id="75ebc-999">Další informace a způsob, jak přispět k těmto balíčkům, najdete v tématu [.NET Core a Open-Source](../get-started/net-core-and-open-source.md), [.NET Home Page na GitHubu](https://github.com/dotnet/home).</span><span class="sxs-lookup"><span data-stu-id="75ebc-999">For more information and how to contribute to these packages, see [.NET Core and Open-Source](../get-started/net-core-and-open-source.md), [.NET Home Page on GitHub](https://github.com/dotnet/home).</span></span>

<a name="v452" />

## <a name="whats-new-in-net-framework-452"></a><span data-ttu-id="75ebc-1000">Co je nového v rozhraní .NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="75ebc-1000">What's new in .NET Framework 4.5.2</span></span>

- <span data-ttu-id="75ebc-1001">**Nová api pro ASP.NET aplikace.**</span><span class="sxs-lookup"><span data-stu-id="75ebc-1001">**New APIs for ASP.NET apps.**</span></span> <span data-ttu-id="75ebc-1002">Nové <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=nameWithType> a <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=nameWithType> metody umožňují kontrolovat a upravovat hlavičky odpovědí a stavový kód, protože odpověď je vyprázdněna do klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1002">The new <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=nameWithType> and <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=nameWithType> methods let you inspect and modify response headers and status code as the response is being flushed to the client app.</span></span> <span data-ttu-id="75ebc-1003">Zvažte použití těchto <xref:System.Web.HttpApplication.PreSendRequestHeaders> metod <xref:System.Web.HttpApplication.PreSendRequestContent> namísto a události; jsou účinnější a spolehlivější.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1003">Consider using these methods instead of the <xref:System.Web.HttpApplication.PreSendRequestHeaders> and <xref:System.Web.HttpApplication.PreSendRequestContent> events; they are more efficient and reliable.</span></span>

  <span data-ttu-id="75ebc-1004">Metoda <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=nameWithType> umožňuje naplánovat malé pracovní položky na pozadí.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1004">The <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=nameWithType> method lets you schedule small background work items.</span></span> <span data-ttu-id="75ebc-1005">ASP.NET sleduje tyto položky a zabrání iis z náhlé ukončení pracovního procesu, dokud všechny pracovní položky na pozadí byly dokončeny.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1005">ASP.NET tracks these items and prevents IIS from abruptly terminating the worker process until all background work items have completed.</span></span> <span data-ttu-id="75ebc-1006">Tuto metodu nelze volat mimo doménu ASP.NET spravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1006">This method can't be called outside an ASP.NET managed app domain.</span></span>

  <span data-ttu-id="75ebc-1007">Nové <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=nameWithType> a <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=nameWithType> vlastnosti vrátí logické hodnoty, které označují, zda byly zapsány hlavičky odpovědí.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1007">The new <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=nameWithType> and <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=nameWithType> properties return Boolean values that indicate whether the response headers have been written.</span></span> <span data-ttu-id="75ebc-1008">Tyto vlastnosti můžete použít k ujistěte se, že volání rozhraní API, jako <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=nameWithType> je například (které vyvolat výjimky, pokud záhlaví byly zapsány) bude úspěšné.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1008">You can use these properties to make sure that calls to APIs such as <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=nameWithType> (which throw exceptions if the headers have been written) will succeed.</span></span>

- <span data-ttu-id="75ebc-1009">**Změna velikosti ovládacích prvků v systému Windows Forms.**</span><span class="sxs-lookup"><span data-stu-id="75ebc-1009">**Resizing in Windows Forms controls.**</span></span> <span data-ttu-id="75ebc-1010">Tato funkce byla rozbalena.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1010">This feature has been expanded.</span></span> <span data-ttu-id="75ebc-1011">Nyní můžete použít nastavení systémového DPI ke změně velikosti součástí následujících dalších ovládacích prvků (například rozevírací šipka v polích se seznamem):</span><span class="sxs-lookup"><span data-stu-id="75ebc-1011">You can now use the system DPI setting to resize components of the following additional controls (for example, the drop-down arrow in combo boxes):</span></span>

  - <xref:System.Windows.Forms.ComboBox>
  - <xref:System.Windows.Forms.ToolStripComboBox>
  - <xref:System.Windows.Forms.ToolStripMenuItem>
  - <xref:System.Windows.Forms.Cursor>
  - <xref:System.Windows.Forms.DataGridView>
  - <xref:System.Windows.Forms.DataGridViewComboBoxColumn>

  <span data-ttu-id="75ebc-1012">Jedná se o funkci opt-in.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1012">This is an opt-in feature.</span></span> <span data-ttu-id="75ebc-1013">Chcete-li jej `EnableWindowsFormsHighDpiAutoResizing` povolit, nastavte prvek v `true` souboru konfigurace aplikace (app.config):</span><span class="sxs-lookup"><span data-stu-id="75ebc-1013">To enable it, set the `EnableWindowsFormsHighDpiAutoResizing` element to `true` in the application configuration (app.config) file:</span></span>

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- <span data-ttu-id="75ebc-1014">**Nová funkce pracovního postupu.**</span><span class="sxs-lookup"><span data-stu-id="75ebc-1014">**New workflow feature.**</span></span> <span data-ttu-id="75ebc-1015">Správce prostředků, který používá <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> metodu (a <xref:System.Transactions.IPromotableSinglePhaseNotification> proto implementuje <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> rozhraní) můžete použít novou metodu požádat o následující:</span><span class="sxs-lookup"><span data-stu-id="75ebc-1015">A resource manager that's using the <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> method (and therefore implementing the <xref:System.Transactions.IPromotableSinglePhaseNotification> interface) can use the new <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> method to request the following:</span></span>

  - <span data-ttu-id="75ebc-1016">Převést transakci na transakci koordinátora distribuovaných transakcí (MSDTC) společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1016">Promote the transaction to a Microsoft Distributed Transaction Coordinator (MSDTC) transaction.</span></span>

  - <span data-ttu-id="75ebc-1017">Nahradit <xref:System.Transactions.IPromotableSinglePhaseNotification> <xref:System.Transactions.ISinglePhaseNotification>, což je trvalé zařazení, které podporuje jednofázové potvrzení.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1017">Replace <xref:System.Transactions.IPromotableSinglePhaseNotification> with an <xref:System.Transactions.ISinglePhaseNotification>, which is a durable enlistment that supports single phase commits.</span></span>

  <span data-ttu-id="75ebc-1018">To lze provést v rámci stejné domény aplikace a nevyžaduje žádné další nespravovaný kód pro interakci s MSDTC k provedení propagace.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1018">This can be done within the same app domain, and doesn't require any extra unmanaged code to interact with MSDTC to perform the promotion.</span></span> <span data-ttu-id="75ebc-1019">Nová metoda může být volána pouze v <xref:System.Transactions?displayProperty=nameWithType> případě, <xref:System.Transactions.IPromotableSinglePhaseNotification> `Promote` že je vynikající volání z na metodu, která je implementována promotable zařazení.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1019">The new method can be called only when there's an outstanding call from <xref:System.Transactions?displayProperty=nameWithType> to the <xref:System.Transactions.IPromotableSinglePhaseNotification>`Promote` method that's implemented by the promotable enlistment.</span></span>

- <span data-ttu-id="75ebc-1020">**Vylepšení profilování.**</span><span class="sxs-lookup"><span data-stu-id="75ebc-1020">**Profiling improvements.**</span></span> <span data-ttu-id="75ebc-1021">Následující nová nespravovaná profilovací prostředí API poskytují robustnější profilování:</span><span class="sxs-lookup"><span data-stu-id="75ebc-1021">The following new unmanaged profiling APIs provide more robust profiling:</span></span>

  - [<span data-ttu-id="75ebc-1022">COR_PRF_ASSEMBLY_REFERENCE_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="75ebc-1022">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](../unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)
  - [<span data-ttu-id="75ebc-1023">Výčet COR_PRF_HIGH_MONITOR</span><span class="sxs-lookup"><span data-stu-id="75ebc-1023">COR_PRF_HIGH_MONITOR Enumeration</span></span>](../unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)
  - [<span data-ttu-id="75ebc-1024">Metoda GetAssemblyReferences</span><span class="sxs-lookup"><span data-stu-id="75ebc-1024">GetAssemblyReferences Method</span></span>](../unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
  - [<span data-ttu-id="75ebc-1025">Metoda GetEventMask2</span><span class="sxs-lookup"><span data-stu-id="75ebc-1025">GetEventMask2 Method</span></span>](../unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
  - [<span data-ttu-id="75ebc-1026">Metoda SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="75ebc-1026">SetEventMask2 Method</span></span>](../unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
  - [<span data-ttu-id="75ebc-1027">Metoda AddAssemblyReference</span><span class="sxs-lookup"><span data-stu-id="75ebc-1027">AddAssemblyReference Method</span></span>](../unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)

  <span data-ttu-id="75ebc-1028">Předchozí `ICorProfiler` implementace podporovaly opožděné načítání závislých sestavení.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1028">Previous `ICorProfiler` implementations supported lazy loading of dependent assemblies.</span></span> <span data-ttu-id="75ebc-1029">Nová profilovací prostředí API vyžadují závislá sestavení, která jsou vložena profilerem, aby byla okamžitě načítatelná, namísto toho, aby byla načtena po úplné inicializování aplikace.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1029">The new profiling APIs require dependent assemblies that are injected by the profiler to be loadable immediately, instead of being loaded after the app is fully initialized.</span></span> <span data-ttu-id="75ebc-1030">Tato změna nemá vliv na `ICorProfiler` uživatele existujících api.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1030">This change doesn't affect users of the existing `ICorProfiler` APIs.</span></span>

- <span data-ttu-id="75ebc-1031">**Vylepšení ladění.**</span><span class="sxs-lookup"><span data-stu-id="75ebc-1031">**Debugging improvements.**</span></span> <span data-ttu-id="75ebc-1032">Následující nová nespravovaná ladění API poskytují lepší integraci s profilerem.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1032">The following new unmanaged debugging APIs provide better integration with a profiler.</span></span> <span data-ttu-id="75ebc-1033">Nyní můžete přistupovat k metadatům vloženým profilerem, stejně jako k místním proměnným a kódu vytvořenému požadavky rejitkompozátoru při ladění výpisu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1033">You can now access metadata inserted by the profiler as well as local variables and code produced by compiler ReJIT requests when dump debugging.</span></span>

  - [<span data-ttu-id="75ebc-1034">Metoda SetWriteableMetadataUpdateMode</span><span class="sxs-lookup"><span data-stu-id="75ebc-1034">SetWriteableMetadataUpdateMode Method</span></span>](../unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
  - [<span data-ttu-id="75ebc-1035">Metoda EnumerateLocalVariablesEx</span><span class="sxs-lookup"><span data-stu-id="75ebc-1035">EnumerateLocalVariablesEx Method</span></span>](../unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)
  - [<span data-ttu-id="75ebc-1036">Metoda GetLocalVariableEx</span><span class="sxs-lookup"><span data-stu-id="75ebc-1036">GetLocalVariableEx Method</span></span>](../unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)
  - [<span data-ttu-id="75ebc-1037">Metoda GetCodeEx</span><span class="sxs-lookup"><span data-stu-id="75ebc-1037">GetCodeEx Method</span></span>](../unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)
  - [<span data-ttu-id="75ebc-1038">Metoda GetActiveReJitRequestILCode</span><span class="sxs-lookup"><span data-stu-id="75ebc-1038">GetActiveReJitRequestILCode Method</span></span>](../unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)
  - [<span data-ttu-id="75ebc-1039">Metoda GetInstrumentedILMap</span><span class="sxs-lookup"><span data-stu-id="75ebc-1039">GetInstrumentedILMap Method</span></span>](../unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)

- <span data-ttu-id="75ebc-1040">**Změny trasování událostí.**</span><span class="sxs-lookup"><span data-stu-id="75ebc-1040">**Event tracing changes.**</span></span> <span data-ttu-id="75ebc-1041">Rozhraní .NET Framework 4.5.2 umožňuje trasování aktivit mimo proces, trasování událostí pro Windows (ETW) pro větší plochu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1041">.NET Framework 4.5.2 enables out-of-process, Event Tracing for Windows (ETW)-based activity tracing for a larger surface area.</span></span> <span data-ttu-id="75ebc-1042">To umožňuje dodavatelům advanced power managementu (APM) poskytovat zjednodušené nástroje, které přesně sledují náklady na jednotlivé požadavky a aktivity, které protínají vlákna.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1042">This enables Advanced Power Management (APM) vendors to provide lightweight tools that accurately track the costs of individual requests and activities that cross threads.</span></span>  <span data-ttu-id="75ebc-1043">Tyto události jsou vyvolány pouze v případě, že řadiče ETW povolit; proto změny nemají vliv na dříve zapsaný kód ETW nebo kód, který běží s ETW zakázáno.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1043">These events are raised only when ETW controllers enable them; therefore, the changes don't affect previously written ETW code or code that runs with ETW disabled.</span></span>

- <span data-ttu-id="75ebc-1044">**Propagace transakce a její převedení na trvalé zařazení**</span><span class="sxs-lookup"><span data-stu-id="75ebc-1044">**Promoting a transaction and converting it to a durable enlistment**</span></span>

  <span data-ttu-id="75ebc-1045"><xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType>je nové rozhraní API přidané do rozhraní .NET Framework 4.5.2 a 4.6:</span><span class="sxs-lookup"><span data-stu-id="75ebc-1045"><xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> is a new API added to .NET Framework 4.5.2 and 4.6:</span></span>

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

  <span data-ttu-id="75ebc-1046">Metoda může být použita zařazení, který byl <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> dříve vytvořen <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> v reakci na metodu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1046">The method may be used by an enlistment that was previously created by <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> in response to the <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="75ebc-1047">Požádá `System.Transactions` o podporu transakce na transakci MSDTC a "převést" promotable zařazení na trvalé zařazení.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1047">It asks `System.Transactions` to promote the transaction to an MSDTC transaction and to "convert" the promotable enlistment to a durable enlistment.</span></span> <span data-ttu-id="75ebc-1048">Po úspěšném dokončení této <xref:System.Transactions.IPromotableSinglePhaseNotification> metody již nebude rozhraní `System.Transactions`odkazováno aplikacemi a všechna budoucí <xref:System.Transactions.ISinglePhaseNotification> oznámení budou doručena do poskytnutého rozhraní.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1048">After this method completes successfully, the <xref:System.Transactions.IPromotableSinglePhaseNotification> interface will no longer be referenced by `System.Transactions`, and any future notifications will arrive on the provided <xref:System.Transactions.ISinglePhaseNotification> interface.</span></span> <span data-ttu-id="75ebc-1049">Dotyčné zařazení musí působit jako trvalé zařazení, které podporuje protokolování transakcí a obnovení.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1049">The enlistment in question must act as a durable enlistment, supporting transaction logging and recovery.</span></span> <span data-ttu-id="75ebc-1050">Podrobnosti <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType> naleznete v části Podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1050">Refer to <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType> for details.</span></span> <span data-ttu-id="75ebc-1051">Kromě toho musí zařazení podporovat <xref:System.Transactions.ISinglePhaseNotification>.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1051">In addition, the enlistment must support <xref:System.Transactions.ISinglePhaseNotification>.</span></span>  <span data-ttu-id="75ebc-1052">Tato metoda může být volána *pouze* při zpracování <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> volání.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1052">This method can *only* be called while processing an <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> call.</span></span> <span data-ttu-id="75ebc-1053">Pokud tomu tak není, <xref:System.Transactions.TransactionException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1053">If that is not the case, a <xref:System.Transactions.TransactionException> exception is thrown.</span></span>

<a name="v451" />

## <a name="whats-new-in-net-framework-451"></a><span data-ttu-id="75ebc-1054">Co je nového v rozhraní .NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="75ebc-1054">What's new in .NET Framework 4.5.1</span></span>

<span data-ttu-id="75ebc-1055">**Aktualizace z dubna 2014**:</span><span class="sxs-lookup"><span data-stu-id="75ebc-1055">**April 2014 updates**:</span></span>

- <span data-ttu-id="75ebc-1056">[Visual Studio 2013 Update 2](https://go.microsoft.com/fwlink/p/?LinkId=393658) obsahuje aktualizace šablon knihovny přenosných tříd pro podporu těchto scénářů:</span><span class="sxs-lookup"><span data-stu-id="75ebc-1056">[Visual Studio 2013 Update 2](https://go.microsoft.com/fwlink/p/?LinkId=393658) includes updates to the Portable Class Library templates to support these scenarios:</span></span>

  - <span data-ttu-id="75ebc-1057">V přenosných knihovnách, které cílí na Windows 8.1, Windows Phone 8.1 a Windows Phone Silverlight 8.1, můžete použít soubory WINDOWS Runtime.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1057">You can use Windows Runtime APIs in portable libraries that target Windows 8.1, Windows Phone 8.1, and Windows Phone Silverlight 8.1.</span></span>

  - <span data-ttu-id="75ebc-1058">XAML (typy Windows.UI.XAML) můžete zahrnout do přenosných knihoven, když cílíte na Windows 8.1 nebo Windows Phone 8.1.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1058">You can include XAML (Windows.UI.XAML types) in portable libraries when you target Windows 8.1 or Windows Phone 8.1.</span></span> <span data-ttu-id="75ebc-1059">Podporovány jsou následující šablony XAML: Prázdná stránka, Slovník prostředků, Ovládací prvek šablony a Uživatelské řízení.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1059">The following XAML templates are supported:  Blank Page, Resource Dictionary, Templated Control, and User Control.</span></span>

  - <span data-ttu-id="75ebc-1060">Můžete vytvořit přenosnou komponentu Prostředí Windows Runtime (.soubor winmd) pro použití v aplikacích pro Store, které cílí na Windows 8.1 a Windows Phone 8.1.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1060">You can create a portable Windows Runtime component (.winmd file) for use in Store apps that target Windows 8.1 and Windows Phone 8.1.</span></span>

  - <span data-ttu-id="75ebc-1061">Můžete znovu zacílit na knihovnu tříd pro Windows Store nebo Windows Phone Store, jako je knihovna přenosných tříd.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1061">You can retarget a Windows Store or Windows Phone Store class library like a Portable Class Library.</span></span>

  <span data-ttu-id="75ebc-1062">Další informace o těchto změnách naleznete v [tématu Portable Class Library](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1062">For more information about these changes, see [Portable Class Library](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).</span></span>

- <span data-ttu-id="75ebc-1063">Sada obsahu rozhraní .NET Framework nyní obsahuje dokumentaci pro nativní rozhraní .NET, což je technologie předkompilace pro vytváření a nasazování aplikací pro Windows.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1063">The .NET Framework content set now includes documentation for .NET Native, which is a precompilation technology for building and deploying Windows apps.</span></span> <span data-ttu-id="75ebc-1064">.NET Native zkompiluje vaše aplikace přímo do nativního kódu, nikoli do zprostředkujícího jazyka (IL), pro lepší výkon.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1064">.NET Native compiles your apps directly to native code, rather than to intermediate language (IL), for better performance.</span></span> <span data-ttu-id="75ebc-1065">Podrobnosti naleznete v [tématu Kompilace aplikací s nativním rozhraním .NET](../net-native/index.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1065">For details, see [Compiling Apps with .NET Native](../net-native/index.md).</span></span>

- <span data-ttu-id="75ebc-1066">[Referenční zdroj rozhraní .NET Framework](https://referencesource.microsoft.com/) poskytuje nové možnosti procházení a rozšířené funkce.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1066">The [.NET Framework Reference Source](https://referencesource.microsoft.com/) provides a new browsing experience and enhanced functionality.</span></span> <span data-ttu-id="75ebc-1067">Nyní můžete procházet zdrojový kód rozhraní .NET Framework online, [stáhnout odkaz](https://referencesource.microsoft.com/download.html) pro prohlížení offline a krokovat zdroje (včetně oprav a aktualizací) během ladění.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1067">You can now browse through the .NET Framework source code online, [download the reference](https://referencesource.microsoft.com/download.html) for offline viewing, and step through the sources (including patches and updates) during debugging.</span></span> <span data-ttu-id="75ebc-1068">Další informace naleznete v položce blogu [Nový vzhled pro referenční zdroj .NET](https://devblogs.microsoft.com/dotnet/a-new-look-for-net-reference-source/).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1068">For more information, see the blog entry [A new look for .NET Reference Source](https://devblogs.microsoft.com/dotnet/a-new-look-for-net-reference-source/).</span></span>

<span data-ttu-id="75ebc-1069">Mezi nové funkce a vylepšení základních tříd v rozhraní .NET Framework 4.5.1 patří:</span><span class="sxs-lookup"><span data-stu-id="75ebc-1069">New features and enhancements in the base classes in .NET Framework 4.5.1 include:</span></span>

- <span data-ttu-id="75ebc-1070">Automatické přesměrování vazeb pro sestavy.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1070">Automatic binding redirection for assemblies.</span></span> <span data-ttu-id="75ebc-1071">Počínaje Visual Studio 2013, když zkompilujete aplikaci, která se zaměřuje na rozhraní .NET Framework 4.5.1, přesměrování vazby může být přidána do konfiguračního souboru aplikace, pokud vaše aplikace nebo její součásti odkazují na více verzí stejného sestavení.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1071">Starting with Visual Studio 2013, when you compile an app that targets the .NET Framework 4.5.1, binding redirects may be added to the app configuration file if your app or its components reference multiple versions of the same assembly.</span></span> <span data-ttu-id="75ebc-1072">Tuto funkci můžete povolit také pro projekty, které cílí na starší verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1072">You can also enable this feature for projects that target older versions of the .NET Framework.</span></span> <span data-ttu-id="75ebc-1073">Další informace naleznete v [tématu How to: Enable and Disable Automatic Binding Redirection](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1073">For more information, see [How to: Enable and Disable Automatic Binding Redirection](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).</span></span>

- <span data-ttu-id="75ebc-1074">Schopnost shromažďovat diagnostické informace, které vývojářům pomáhají zlepšit výkon serverových a cloudových aplikací.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1074">Ability to collect diagnostics information to help developers improve the performance of server and cloud applications.</span></span> <span data-ttu-id="75ebc-1075">Další informace naleznete <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> v <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> tématu <xref:System.Diagnostics.Tracing.EventSource> a metody ve třídě.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1075">For more information, see the <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> and <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> methods in the <xref:System.Diagnostics.Tracing.EventSource> class.</span></span>

- <span data-ttu-id="75ebc-1076">Možnost explicitně komprimovat haldy velkých objektů (LOH) během uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1076">Ability to explicitly compact the large object heap (LOH) during garbage collection.</span></span> <span data-ttu-id="75ebc-1077">Další informace naleznete <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> v ubytovacím zařízení.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1077">For more information, see the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> property.</span></span>

- <span data-ttu-id="75ebc-1078">Další vylepšení výkonu, jako je ASP.NET pozastavení aplikace, vylepšení JIT s více jádry a rychlejší spuštění aplikace po aktualizaci rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1078">Additional performance improvements such as ASP.NET app suspension, multi-core JIT improvements, and faster app startup after a .NET Framework update.</span></span> <span data-ttu-id="75ebc-1079">Podrobnosti najdete v [oznámení .NET Framework 4.5.1](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/) a [ASP.NET aplikace pozastavit](https://devblogs.microsoft.com/dotnet/asp-net-app-suspend-responsive-shared-net-web-hosting/) příspěvek blogu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1079">For details, see the [.NET Framework 4.5.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/) and the [ASP.NET app suspend](https://devblogs.microsoft.com/dotnet/asp-net-app-suspend-responsive-shared-net-web-hosting/) blog post.</span></span>

<span data-ttu-id="75ebc-1080">Mezi vylepšení formulářů Windows patří:</span><span class="sxs-lookup"><span data-stu-id="75ebc-1080">Improvements to Windows Forms include:</span></span>

- <span data-ttu-id="75ebc-1081">Změna velikosti ovládacích prvků v systému Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1081">Resizing in Windows Forms controls.</span></span> <span data-ttu-id="75ebc-1082">Nastavení systémového DPI můžete použít ke změně velikosti součástí ovládacích prvků (například ikon, které se zobrazují v mřížce vlastností) tak, že se přihlásíte pomocí položky v konfiguračním souboru aplikace (app.config) pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1082">You can use the system DPI setting to resize components of controls (for example, the icons that appear in a property grid) by opting in with an entry in the application configuration file (app.config) for your app.</span></span> <span data-ttu-id="75ebc-1083">Tato funkce je aktuálně podporována v následujících ovládacích prvcích systému Windows:</span><span class="sxs-lookup"><span data-stu-id="75ebc-1083">This feature is currently supported in the following Windows Forms controls:</span></span>

  - <xref:System.Windows.Forms.PropertyGrid>
  - <xref:System.Windows.Forms.TreeView>
  - <span data-ttu-id="75ebc-1084">Některé aspekty <xref:System.Windows.Forms.DataGridView> (viz [nové funkce v 4.5.2](#v452) pro další podporované ovládací prvky)</span><span class="sxs-lookup"><span data-stu-id="75ebc-1084">Some aspects of the <xref:System.Windows.Forms.DataGridView> (see [new features in 4.5.2](#v452) for additional controls supported)</span></span>

  <span data-ttu-id="75ebc-1085">Chcete-li tuto funkci \<povolit, přidejte do konfiguračního souboru `EnableWindowsFormsHighDpiAutoResizing` (app.config) nový prvek nastavení aplikaceNastavení> a nastavte prvek na `true`:</span><span class="sxs-lookup"><span data-stu-id="75ebc-1085">To enable this feature, add a new \<appSettings> element to the configuration file (app.config) and set the `EnableWindowsFormsHighDpiAutoResizing` element to `true`:</span></span>

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

<span data-ttu-id="75ebc-1086">Mezi vylepšení při ladění aplikací rozhraní .NET Framework ve Visual Studiu 2013 patří:</span><span class="sxs-lookup"><span data-stu-id="75ebc-1086">Improvements when debugging your .NET Framework apps in Visual Studio 2013 include:</span></span>

- <span data-ttu-id="75ebc-1087">Vrátí hodnoty v ladicím programu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1087">Return values in the Visual Studio debugger.</span></span> <span data-ttu-id="75ebc-1088">Při ladění spravované aplikace ve Visual Studiu 2013 se v okně Autos zobrazí návratové typy a hodnoty pro metody.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1088">When you debug a managed app in Visual Studio 2013, the Autos window displays return types and values for methods.</span></span> <span data-ttu-id="75ebc-1089">Tyto informace jsou dostupné pro desktopové aplikace, aplikace pro Windows Store a Windows Phone.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1089">This information is available for desktop, Windows Store, and Windows Phone apps.</span></span> <span data-ttu-id="75ebc-1090">Další informace naleznete v [tématu Prozkoumání vrácených hodnot volání metody](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/dn323257(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1090">For more information, see [Examine return values of method calls](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/dn323257(v=vs.120)).</span></span>

- <span data-ttu-id="75ebc-1091">Upravujte a pokračujte u 64bitových aplikací.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1091">Edit and Continue for 64-bit apps.</span></span> <span data-ttu-id="75ebc-1092">Visual Studio 2013 podporuje funkci Úpravy a pokračovat pro 64bitové spravované aplikace pro stolní počítače, Windows Store a Windows Phone.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1092">Visual Studio 2013 supports the Edit and Continue feature for 64-bit managed apps for desktop, Windows Store, and Windows Phone.</span></span> <span data-ttu-id="75ebc-1093">Existující omezení zůstávají v platnosti pro 32bitové i 64bitové aplikace (viz poslední část článku [Podporované změny kódu (C#).](/visualstudio/debugger/supported-code-changes-csharp)</span><span class="sxs-lookup"><span data-stu-id="75ebc-1093">The existing limitations remain in effect for both 32-bit and 64-bit apps (see the last section of the [Supported Code Changes (C#)](/visualstudio/debugger/supported-code-changes-csharp) article).</span></span>

- <span data-ttu-id="75ebc-1094">Ladění podporující asynchronní.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1094">Async-aware debugging.</span></span> <span data-ttu-id="75ebc-1095">Chcete-li usnadnit ladění asynchronních aplikací v sadě Visual Studio 2013, zásobník volání skryje kód infrastruktury poskytovaný kompilátory pro podporu asynchronního programování a také řetězy v logických nadřazených rámcích, takže můžete sledovat provádění logického programu jasněji.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1095">To make it easier to debug asynchronous apps in Visual Studio 2013, the call stack hides the infrastructure code provided by compilers to support asynchronous programming, and also chains in logical parent frames so you can follow logical program execution more clearly.</span></span> <span data-ttu-id="75ebc-1096">Okno Úkoly nahrazuje okno Paralelní úkoly a zobrazuje úkoly, které se vztahují k určité zarážky, a také zobrazuje všechny další úkoly, které jsou aktuálně aktivní nebo naplánované v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1096">A Tasks window replaces the Parallel Tasks window and displays tasks that relate to a particular breakpoint, and also displays any other tasks that are currently active or scheduled in the app.</span></span> <span data-ttu-id="75ebc-1097">O této funkci si můžete přečíst v části Ladění podporující asynchronní informace [v oznámení rozhraní .NET Framework 4.5.1](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1097">You can read about this feature in the "Async-aware debugging" section of the [.NET Framework 4.5.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).</span></span>

- <span data-ttu-id="75ebc-1098">Lepší podpora výjimek pro součásti prostředí Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1098">Better exception support for Windows Runtime components.</span></span> <span data-ttu-id="75ebc-1099">Výjimky, které vyvstávají z aplikací pro Windows Store, ve Windows 8.1 zachovávají informace o chybě, která výjimku způsobila, a to i přes hranice jazyka.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1099">In Windows 8.1, exceptions that arise from Windows Store apps preserve information about the error that caused the exception, even across language boundaries.</span></span> <span data-ttu-id="75ebc-1100">O této funkci si můžete přečíst v části Vývoj aplikací pro Windows Store v [oznámení .NET Framework 4.5.1](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1100">You can read about this feature in the "Windows Store app development" section of the [.NET Framework 4.5.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).</span></span>

<span data-ttu-id="75ebc-1101">Počínaje Visual Studio 2013, můžete použít [nástroj pro optimalizaci spravovaného profilu s asistencí (Mpgo.exe)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md) k optimalizaci aplikací pro Windows 8.x Store i aplikací klasické pracovní plochy.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1101">Starting with Visual Studio 2013, you can use the [Managed Profile Guided Optimization Tool (Mpgo.exe)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md) to optimize Windows 8.x Store apps as well as desktop apps.</span></span>

<span data-ttu-id="75ebc-1102">Nové funkce v ASP.NET 4.5.1 najdete v [tématu ASP.NET a webových nástrojů pro poznámky k verzi sady Visual Studio 2013](/aspnet/visual-studio/overview/2013/release-notes).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1102">For new features in ASP.NET 4.5.1, see [ASP.NET and Web Tools for Visual Studio 2013 Release Notes](/aspnet/visual-studio/overview/2013/release-notes).</span></span>

<a name="v45" />

## <a name="whats-new-in-net-framework-45"></a><span data-ttu-id="75ebc-1103">Co je nového v rozhraní .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="75ebc-1103">What's new in .NET Framework 4.5</span></span>

### <a name="base-classes"></a><span data-ttu-id="75ebc-1104">Základní třídy</span><span class="sxs-lookup"><span data-stu-id="75ebc-1104">Base classes</span></span>

- <span data-ttu-id="75ebc-1105">Možnost snížit restartování systému zjišťováním a zavíráním aplikací rozhraní .NET Framework 4 během nasazení.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1105">Ability to reduce system restarts by detecting and closing .NET Framework 4 applications during deployment.</span></span> <span data-ttu-id="75ebc-1106">Viz [Snížení restartování systému během instalace rozhraní .NET Framework 4.5](../deployment/reducing-system-restarts.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1106">See [Reducing System Restarts During .NET Framework 4.5 Installations](../deployment/reducing-system-restarts.md).</span></span>

- <span data-ttu-id="75ebc-1107">Podpora pro pole, která jsou větší než 2 gigabajty (GB) na 64bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1107">Support for arrays that are larger than 2 gigabytes (GB) on 64-bit platforms.</span></span> <span data-ttu-id="75ebc-1108">Tuto funkci lze povolit v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1108">This feature can be enabled in the application configuration file.</span></span> <span data-ttu-id="75ebc-1109">Viz [ \<gcAllowVeryLargeObjects> element](../configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md), který také uvádí další omezení velikosti objektu a velikosti pole.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1109">See the [\<gcAllowVeryLargeObjects> element](../configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md), which also lists other restrictions on object size and array size.</span></span>

- <span data-ttu-id="75ebc-1110">Lepší výkon prostřednictvím uvolňování paměti na pozadí pro servery.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1110">Better performance through background garbage collection for servers.</span></span> <span data-ttu-id="75ebc-1111">Při použití uvolňování paměti serveru v rozhraní .NET Framework 4.5 je automaticky povoleno uvolňování paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1111">When you use server garbage collection in the .NET Framework 4.5, background garbage collection is automatically enabled.</span></span> <span data-ttu-id="75ebc-1112">Viz část Uvolňování paměti serveru na pozadí [v tématu Základy uvolňování paměti.](../../standard/garbage-collection/fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="75ebc-1112">See the Background Server Garbage Collection section of the [Fundamentals of Garbage Collection](../../standard/garbage-collection/fundamentals.md) topic.</span></span>

- <span data-ttu-id="75ebc-1113">Kompilace just-in-time (JIT) na pozadí, která je volitelně k dispozici na vícejádrových procesorech pro zlepšení výkonu aplikací.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1113">Background just-in-time (JIT) compilation, which is optionally available on multi-core processors to improve application performance.</span></span> <span data-ttu-id="75ebc-1114">Viz třída <xref:System.Runtime.ProfileOptimization>.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1114">See <xref:System.Runtime.ProfileOptimization>.</span></span>

- <span data-ttu-id="75ebc-1115">Možnost omezit, jak dlouho se modul regulárních výrazů pokusí vyřešit regulární výraz před jeho časovým limitem. Podívejte <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=nameWithType> se na nemovitost.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1115">Ability to limit how long the regular expression engine will attempt to resolve a regular expression before it times out. See the <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=nameWithType> property.</span></span>

- <span data-ttu-id="75ebc-1116">Možnost definovat výchozí jazykovou verzi pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1116">Ability to define the default culture for an application domain.</span></span> <span data-ttu-id="75ebc-1117">Podívejte <xref:System.Globalization.CultureInfo> se na třídu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1117">See the <xref:System.Globalization.CultureInfo> class.</span></span>

- <span data-ttu-id="75ebc-1118">Podpora konzoly pro kódování Unicode (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1118">Console support for Unicode (UTF-16) encoding.</span></span> <span data-ttu-id="75ebc-1119">Podívejte <xref:System.Console> se na třídu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1119">See the <xref:System.Console> class.</span></span>

- <span data-ttu-id="75ebc-1120">Podpora pro správu verzí pořadí kulturních řetězců a data porovnání.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1120">Support for versioning of cultural string ordering and comparison data.</span></span> <span data-ttu-id="75ebc-1121">Podívejte <xref:System.Globalization.SortVersion> se na třídu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1121">See the <xref:System.Globalization.SortVersion> class.</span></span>

- <span data-ttu-id="75ebc-1122">Lepší výkon při načítání prostředků.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1122">Better performance when retrieving resources.</span></span> <span data-ttu-id="75ebc-1123">Viz [Balení a nasazení prostředků](../resources/packaging-and-deploying-resources-in-desktop-apps.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1123">See [Packaging and Deploying Resources](../resources/packaging-and-deploying-resources-in-desktop-apps.md).</span></span>

- <span data-ttu-id="75ebc-1124">Vylepšení komprese zip zmenšit velikost komprimovaného souboru.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1124">Zip compression improvements to reduce the size of a compressed file.</span></span> <span data-ttu-id="75ebc-1125">Podívejte <xref:System.IO.Compression?displayProperty=nameWithType> se na obor názvů.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1125">See the <xref:System.IO.Compression?displayProperty=nameWithType> namespace.</span></span>

- <span data-ttu-id="75ebc-1126">Možnost přizpůsobit kontext reflexe přepsat výchozí chování <xref:System.Reflection.Context.CustomReflectionContext> odrazu prostřednictvím třídy.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1126">Ability to customize a reflection context to override default reflection behavior through the <xref:System.Reflection.Context.CustomReflectionContext> class.</span></span>

- <span data-ttu-id="75ebc-1127">Podpora pro 2008 verze standardu Internationalized Domain Names in Applications <xref:System.Globalization.IdnMapping?displayProperty=nameWithType> (IDNA) při použití třídy v systému Windows 8.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1127">Support for the 2008 version of the Internationalized Domain Names in Applications (IDNA) standard when the <xref:System.Globalization.IdnMapping?displayProperty=nameWithType> class is used  on Windows 8.</span></span>

- <span data-ttu-id="75ebc-1128">Delegování porovnání řetězců s operačním systémem, který implementuje Unicode 6.0, při použití rozhraní .NET Framework v systému Windows 8.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1128">Delegation of string comparison to the operating system, which implements Unicode 6.0, when the .NET Framework is used on Windows 8.</span></span> <span data-ttu-id="75ebc-1129">Při spuštění na jiných platformách obsahuje rozhraní .NET Framework vlastní data pro porovnání řetězců, která implementuje unicode 5.x.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1129">When running on other platforms, the .NET Framework includes its own string comparison data, which implements Unicode 5.x.</span></span> <span data-ttu-id="75ebc-1130">Viz <xref:System.String> oddíl y třídy <xref:System.Globalization.SortVersion> a poznámky.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1130">See the <xref:System.String> class and the Remarks section of the <xref:System.Globalization.SortVersion> class.</span></span>

- <span data-ttu-id="75ebc-1131">Možnost vypočítat kódy hash pro řetězce na základě domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1131">Ability to compute the hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="75ebc-1132">Viz [ \<UseRandomizedStringHashAlgorithm> Element](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1132">See [\<UseRandomizedStringHashAlgorithm> Element](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).</span></span>

- <span data-ttu-id="75ebc-1133">Podpora odrazu <xref:System.Type> typu <xref:System.Reflection.TypeInfo> rozdělit mezi a třídy.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1133">Type reflection support split between <xref:System.Type> and <xref:System.Reflection.TypeInfo> classes.</span></span> <span data-ttu-id="75ebc-1134">Viz [Reflexe v rozhraní .NET Framework pro aplikace pro Windows Store](../reflection-and-codedom/reflection-for-windows-store-apps.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1134">See [Reflection in the .NET Framework for Windows Store Apps](../reflection-and-codedom/reflection-for-windows-store-apps.md).</span></span>

### <a name="managed-extensibility-framework-mef"></a><span data-ttu-id="75ebc-1135">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="75ebc-1135">Managed Extensibility Framework (MEF)</span></span>

<span data-ttu-id="75ebc-1136">V rozhraní .NET Framework 4.5 poskytuje rozhraní MEF spravované rozšiřitelnosti následující nové funkce:</span><span class="sxs-lookup"><span data-stu-id="75ebc-1136">In the .NET Framework 4.5, the Managed Extensibility Framework (MEF) provides the following new features:</span></span>

- <span data-ttu-id="75ebc-1137">Podpora pro obecné typy.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1137">Support for generic types.</span></span>

- <span data-ttu-id="75ebc-1138">Programovací model založený na konvencích, který umožňuje vytvářet součásti založené na konvencích pojmenování, nikoli na atributech.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1138">Convention-based programming model that enables you to create parts based on naming conventions rather than attributes.</span></span>

- <span data-ttu-id="75ebc-1139">Více oborů.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1139">Multiple scopes.</span></span>

- <span data-ttu-id="75ebc-1140">Podmnožina MEF, kterou můžete použít při vytváření aplikací pro Windows 8.x Store.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1140">A subset of MEF that you can use when you create Windows 8.x Store apps.</span></span> <span data-ttu-id="75ebc-1141">Tato podmnožina je k dispozici jako [balíček ke stažení](https://www.nuget.org/packages/Microsoft.Composition) z Galerie NuGet.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1141">This subset is available as a [downloadable package](https://www.nuget.org/packages/Microsoft.Composition) from the NuGet Gallery.</span></span> <span data-ttu-id="75ebc-1142">Chcete-li nainstalovat balíček, otevřete projekt v sadě Visual Studio, zvolte `Microsoft.Composition` Spravovat **balíčky NuGet** z nabídky **Project** a vyhledejte balíček online.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1142">To install the package, open your project in Visual Studio, choose **Manage NuGet Packages** from the **Project** menu, and search online for the `Microsoft.Composition` package.</span></span>

<span data-ttu-id="75ebc-1143">Další informace naleznete [v tématu Managed Extensibility Framework (MEF)](../mef/index.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1143">For more information, see [Managed Extensibility Framework (MEF)](../mef/index.md).</span></span>

### <a name="asynchronous-file-operations"></a><span data-ttu-id="75ebc-1144">Asynchronní operace se soubory</span><span class="sxs-lookup"><span data-stu-id="75ebc-1144">Asynchronous file operations</span></span>

<span data-ttu-id="75ebc-1145">V rozhraní .NET Framework 4.5 byly do jazyků Jazyka C# a Visual Basic přidány nové asynchronní funkce.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1145">In the .NET Framework 4.5, new asynchronous features were added to the C# and Visual Basic languages.</span></span> <span data-ttu-id="75ebc-1146">Tyto funkce přidat model založený na úlohách pro provádění asynchronních operací.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1146">These features add a task-based model for performing asynchronous operations.</span></span> <span data-ttu-id="75ebc-1147">Chcete-li použít tento nový model, použijte asynchronní metody ve třídách V/V.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1147">To use this new model, use the asynchronous methods in the I/O classes.</span></span> <span data-ttu-id="75ebc-1148">Viz [Vodaná vstupně-videa a synchronního souboru](../../standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1148">See [Asynchronous File I/O](../../standard/io/asynchronous-file-i-o.md).</span></span>

<a name="tools" />

### <a name="tools"></a><span data-ttu-id="75ebc-1149">nástroje</span><span class="sxs-lookup"><span data-stu-id="75ebc-1149">Tools</span></span>

<span data-ttu-id="75ebc-1150">V rozhraní .NET Framework 4.5 umožňuje generátor souborů prostředků (Resgen.exe) vytvořit soubor Resw pro použití v aplikacích pro Windows 8.x Store ze souboru .resources vloženého do sestavení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1150">In the .NET Framework 4.5, Resource File Generator (Resgen.exe) enables you to create a .resw file for use in Windows 8.x Store apps from a .resources file embedded in a .NET Framework assembly.</span></span> <span data-ttu-id="75ebc-1151">Další informace naleznete v [tématu Resgen.exe (Resource File Generator).](../tools/resgen-exe-resource-file-generator.md)</span><span class="sxs-lookup"><span data-stu-id="75ebc-1151">For more information, see [Resgen.exe (Resource File Generator)](../tools/resgen-exe-resource-file-generator.md).</span></span>

<span data-ttu-id="75ebc-1152">Optimalizace s asistencí spravovaného profilu (Mpgo.exe) umožňuje zlepšit dobu spuštění aplikace, využití paměti (velikost pracovní sady) a propustnost optimalizací nativních sestav bitových obrázků.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1152">Managed Profile Guided Optimization (Mpgo.exe) enables you to improve application startup time, memory utilization (working set size), and throughput by optimizing native image assemblies.</span></span> <span data-ttu-id="75ebc-1153">Nástroj příkazového řádku generuje data profilu pro nativní sestavení aplikací obrazu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1153">The command-line tool generates profile data for native image application assemblies.</span></span> <span data-ttu-id="75ebc-1154">Viz [Mpgo.exe (Nástroj pro řízenou optimalizaci profilu)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1154">See [Mpgo.exe (Managed Profile Guided Optimization Tool)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md).</span></span> <span data-ttu-id="75ebc-1155">Počínaje Visual Studio 2013, můžete použít Mpgo.exe k optimalizaci aplikací pro Windows 8.x Store, stejně jako desktopové aplikace.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1155">Starting with Visual Studio 2013, you can use Mpgo.exe to optimize Windows 8.x Store apps as well as desktop apps.</span></span>

<a name="parallel" />

### <a name="parallel-computing"></a><span data-ttu-id="75ebc-1156">Paralelní výpočetní technika</span><span class="sxs-lookup"><span data-stu-id="75ebc-1156">Parallel computing</span></span>

<span data-ttu-id="75ebc-1157">Rozhraní .NET Framework 4.5 poskytuje několik nových funkcí a vylepšení pro paralelní výpočty.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1157">The .NET Framework 4.5 provides several new features and improvements for parallel computing.</span></span> <span data-ttu-id="75ebc-1158">Patří mezi ně lepší výkon, lepší řízení, vylepšená podpora asynchronního programování, nová knihovna toku dat a vylepšená podpora paralelního ladění a analýzy výkonu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1158">These include improved performance, increased control, improved support for asynchronous programming, a new dataflow library, and improved support for parallel debugging and performance analysis.</span></span> <span data-ttu-id="75ebc-1159">Podívejte se na položku [Co je nového pro paralelismus v rozhraní .NET 4.5](https://devblogs.microsoft.com/pfxteam/whats-new-for-parallelism-in-net-4-5/) v paralelním programování s .NET blog.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1159">See the entry [What’s New for Parallelism in .NET 4.5](https://devblogs.microsoft.com/pfxteam/whats-new-for-parallelism-in-net-4-5/) in the Parallel Programming with .NET blog.</span></span>

<a name="web" />

### <a name="web"></a><span data-ttu-id="75ebc-1160">Web</span><span class="sxs-lookup"><span data-stu-id="75ebc-1160">Web</span></span>

<span data-ttu-id="75ebc-1161">ASP.NET 4.5 a 4.5.1 přidat vazbu modelu pro webové formuláře, podporu WebSocket, asynchronní obslužné rutiny, vylepšení výkonu a mnoho dalších funkcí.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1161">ASP.NET 4.5 and 4.5.1 add model binding for Web Forms, WebSocket support, asynchronous handlers, performance enhancements, and many other features.</span></span> <span data-ttu-id="75ebc-1162">Další informace najdete v následujících materiálech:</span><span class="sxs-lookup"><span data-stu-id="75ebc-1162">For more information, see the following resources:</span></span>

- <span data-ttu-id="75ebc-1163">[ASP.NET 4.5 a Visual Studio 2012](https://docs.microsoft.com/previous-versions/aspnet/hh420390(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="75ebc-1163">[ASP.NET 4.5 and Visual Studio 2012](https://docs.microsoft.com/previous-versions/aspnet/hh420390(v=vs.110))</span></span>

- [<span data-ttu-id="75ebc-1164">ASP.NET a webové nástroje pro Visual Studio 2013 – poznámky k verzi</span><span class="sxs-lookup"><span data-stu-id="75ebc-1164">ASP.NET and Web Tools for Visual Studio 2013 Release Notes</span></span>](/aspnet/visual-studio/overview/2013/release-notes)

### <a name="networking"></a><span data-ttu-id="75ebc-1165">Sítí<a name="networking" /></span><span class="sxs-lookup"><span data-stu-id="75ebc-1165">Networking <a name="networking" /></span></span>

<span data-ttu-id="75ebc-1166">Rozhraní .NET Framework 4.5 poskytuje nové programovací rozhraní pro aplikace HTTP.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1166">The .NET Framework 4.5 provides a new programming interface for HTTP applications.</span></span> <span data-ttu-id="75ebc-1167">Další informace naleznete v <xref:System.Net.Http?displayProperty=nameWithType> <xref:System.Net.Http.Headers?displayProperty=nameWithType> nových oborech názvů a oborech názvů.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1167">For more information, see the new <xref:System.Net.Http?displayProperty=nameWithType> and <xref:System.Net.Http.Headers?displayProperty=nameWithType> namespaces.</span></span>

<span data-ttu-id="75ebc-1168">Podpora je také součástí pro nové programovací rozhraní pro přijetí a <xref:System.Net.HttpListener> interakci s připojením WebSocket pomocí existující a související třídy.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1168">Support is also included for a new programming interface for accepting and interacting with a WebSocket connection by using the existing <xref:System.Net.HttpListener> and related classes.</span></span> <span data-ttu-id="75ebc-1169">Další informace naleznete v <xref:System.Net.WebSockets> novém oboru <xref:System.Net.HttpListener> názvů a třídě.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1169">For more information, see the new <xref:System.Net.WebSockets> namespace and the <xref:System.Net.HttpListener> class.</span></span>

<span data-ttu-id="75ebc-1170">Rozhraní .NET Framework 4.5 navíc obsahuje následující vylepšení sítě:</span><span class="sxs-lookup"><span data-stu-id="75ebc-1170">In addition, the .NET Framework 4.5 includes the following networking improvements:</span></span>

- <span data-ttu-id="75ebc-1171">Podpora identifikátoru URI kompatibilního s rfc.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1171">RFC-compliant URI support.</span></span> <span data-ttu-id="75ebc-1172">Další informace naleznete <xref:System.Uri> v tématu a související třídy.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1172">For more information, see <xref:System.Uri> and related classes.</span></span>

- <span data-ttu-id="75ebc-1173">Podpora pro internacionalizovanou analýzu názvu domény (IDN).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1173">Support for Internationalized Domain Name (IDN) parsing.</span></span> <span data-ttu-id="75ebc-1174">Další informace naleznete <xref:System.Uri> v tématu a související třídy.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1174">For more information, see <xref:System.Uri> and related classes.</span></span>

- <span data-ttu-id="75ebc-1175">Podpora internacionalizace e-mailových adres (EAI).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1175">Support for Email Address Internationalization (EAI).</span></span> <span data-ttu-id="75ebc-1176">Další informace naleznete <xref:System.Net.Mail> v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1176">For more information, see the <xref:System.Net.Mail> namespace.</span></span>

- <span data-ttu-id="75ebc-1177">Vylepšená podpora IPv6.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1177">Improved IPv6 support.</span></span> <span data-ttu-id="75ebc-1178">Další informace naleznete <xref:System.Net.NetworkInformation> v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1178">For more information, see the <xref:System.Net.NetworkInformation> namespace.</span></span>

- <span data-ttu-id="75ebc-1179">Podpora dvourežimových soketů.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1179">Dual-mode socket support.</span></span> <span data-ttu-id="75ebc-1180">Další informace naleznete <xref:System.Net.Sockets.Socket> v <xref:System.Net.Sockets.TcpListener> tématu a třídy.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1180">For more information, see the <xref:System.Net.Sockets.Socket> and <xref:System.Net.Sockets.TcpListener> classes.</span></span>

<a name="client" />

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="75ebc-1181">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="75ebc-1181">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="75ebc-1182">V rozhraní .NET Framework 4.5 obsahuje Nadace WPF (Windows Presentation Foundation) změny a vylepšení v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="75ebc-1182">In the .NET Framework 4.5, Windows Presentation Foundation (WPF) contains changes and improvements in the following areas:</span></span>

- <span data-ttu-id="75ebc-1183">Nový <xref:System.Windows.Controls.Ribbon.Ribbon> ovládací prvek, který umožňuje implementovat uživatelské rozhraní pásu karet, které je hostitelem panelu nástrojů rychlý přístup, nabídky aplikací a karet.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1183">The new <xref:System.Windows.Controls.Ribbon.Ribbon> control, which enables you to implement a ribbon user interface that hosts a Quick Access Toolbar, Application Menu, and tabs.</span></span>

- <span data-ttu-id="75ebc-1184">Nové <xref:System.ComponentModel.INotifyDataErrorInfo> rozhraní, které podporuje synchronní a asynchronní ověřování dat.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1184">The new <xref:System.ComponentModel.INotifyDataErrorInfo> interface, which supports synchronous and asynchronous data validation.</span></span>

- <span data-ttu-id="75ebc-1185">Nové funkce <xref:System.Windows.Controls.VirtualizingPanel> pro <xref:System.Windows.Threading.Dispatcher> třídy a.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1185">New features for the <xref:System.Windows.Controls.VirtualizingPanel> and <xref:System.Windows.Threading.Dispatcher> classes.</span></span>

- <span data-ttu-id="75ebc-1186">Vyšší výkon při zobrazení velkých sad seskupených dat a přístup u kolekcí v podprocesech mimo uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1186">Improved performance when displaying large sets of grouped data, and by accessing collections on non-UI threads.</span></span>

- <span data-ttu-id="75ebc-1187">Datová vazba na statické vlastnosti, <xref:System.Reflection.ICustomTypeProvider> datová vazba na vlastní typy, které implementují rozhraní, a načítání informací o datové vazbě z výrazu vazby.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1187">Data binding to static properties, data binding to custom types that implement the <xref:System.Reflection.ICustomTypeProvider> interface, and retrieval of data binding information from a binding expression.</span></span>

- <span data-ttu-id="75ebc-1188">Změna umístění dat při změně hodnot (živé tvarování).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1188">Repositioning of data as the values change (live shaping).</span></span>

- <span data-ttu-id="75ebc-1189">Možnost zkontrolovat, zda je odpojen kontext dat pro kontejner položek.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1189">Ability to check whether the data context for an item container is disconnected.</span></span>

- <span data-ttu-id="75ebc-1190">Možnost nastavit dobu, která by měla uplynout mezi změnami vlastností a aktualizacemi zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1190">Ability to set the amount of time that should elapse between property changes and data source updates.</span></span>

- <span data-ttu-id="75ebc-1191">Vylepšená podpora pro implementaci vzorů slabých událostí.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1191">Improved support for implementing weak event patterns.</span></span> <span data-ttu-id="75ebc-1192">Události mohou nyní přijímat rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1192">Also, events can now accept markup extensions.</span></span>

<a name="windows_communication_foundation" />

### <a name="windows-communication-foundation-wcf"></a><span data-ttu-id="75ebc-1193">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="75ebc-1193">Windows Communication Foundation (WCF)</span></span>

<span data-ttu-id="75ebc-1194">V rozhraní .NET Framework 4.5 byly přidány následující funkce, které usnadňují psaní a údržbu aplikací WCF (Windows Communication Foundation):</span><span class="sxs-lookup"><span data-stu-id="75ebc-1194">In the .NET Framework 4.5, the following features have been added to make it simpler to write and maintain Windows Communication Foundation (WCF) applications:</span></span>

- <span data-ttu-id="75ebc-1195">Zjednodušení generovaných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1195">Simplification of generated configuration files.</span></span>

- <span data-ttu-id="75ebc-1196">Podpora pro vývoj na prvním místě smlouvy.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1196">Support for contract-first development.</span></span>

- <span data-ttu-id="75ebc-1197">Možnost snadněji konfigurovat režim kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1197">Ability to configure ASP.NET compatibility mode more easily.</span></span>

- <span data-ttu-id="75ebc-1198">Změny výchozíhodnoty vlastnosti přenosu snížit pravděpodobnost, že budete muset nastavit.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1198">Changes in default transport property values to reduce the likelihood that you will have to set them.</span></span>

- <span data-ttu-id="75ebc-1199">Aktualizace <xref:System.Xml.XmlDictionaryReaderQuotas> třídy snížit pravděpodobnost, že budete muset ručně nakonfigurovat kvóty pro čtečky slovníku XML.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1199">Updates to the <xref:System.Xml.XmlDictionaryReaderQuotas> class to reduce the likelihood that you will have to manually configure quotas for XML dictionary readers.</span></span>

- <span data-ttu-id="75ebc-1200">Ověření konfiguračních souborů WCF pomocí sady Visual Studio jako součást procesu sestavení, takže můžete zjistit chyby konfigurace před spuštěním aplikace.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1200">Validation of WCF configuration files by Visual Studio as part of the build process, so you can detect configuration errors before you run your application.</span></span>

- <span data-ttu-id="75ebc-1201">Nová podpora asynchronního streamování.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1201">New asynchronous streaming support.</span></span>

- <span data-ttu-id="75ebc-1202">Nové mapování protokolu HTTPS, které usnadňuje vystavení koncového bodu prostřednictvím protokolu HTTPS pomocí Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1202">New HTTPS protocol mapping to make it easier to expose an endpoint over HTTPS with Internet Information Services (IIS).</span></span>

- <span data-ttu-id="75ebc-1203">Možnost generovat metadata v jednom dokumentu WSDL připojením `?singleWSDL` k adrese URL služby.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1203">Ability to generate metadata in a single WSDL document by appending `?singleWSDL` to the service URL.</span></span>

- <span data-ttu-id="75ebc-1204">Websockets podpora povolit skutečnou obousměrnou komunikaci přes porty 80 a 443 s charakteristikami výkonu podobné přenosu TCP.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1204">Websockets support to enable true bidirectional communication over ports 80 and 443 with performance characteristics similar to the TCP transport.</span></span>

- <span data-ttu-id="75ebc-1205">Podpora konfigurace služeb v kódu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1205">Support for configuring services in code.</span></span>

- <span data-ttu-id="75ebc-1206">Popisky editoru XML.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1206">XML Editor tooltips.</span></span>

- <span data-ttu-id="75ebc-1207"><xref:System.ServiceModel.ChannelFactory>podpora ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1207"><xref:System.ServiceModel.ChannelFactory> caching support.</span></span>

- <span data-ttu-id="75ebc-1208">Podpora komprese binárního kodéru.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1208">Binary encoder compression support.</span></span>

- <span data-ttu-id="75ebc-1209">Podpora přenosu UDP, který umožňuje vývojářům psát služby, které používají zprávy "fire and forget".</span><span class="sxs-lookup"><span data-stu-id="75ebc-1209">Support for a UDP transport that enables developers to write services that use "fire and forget" messaging.</span></span> <span data-ttu-id="75ebc-1210">Klient odešle zprávu službě a očekává žádnou odpověď ze služby.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1210">A client sends a message to a service and expects no response from the service.</span></span>

- <span data-ttu-id="75ebc-1211">Možnost podporovat více režimů ověřování na jednom koncovém bodu WCF při použití zabezpečení přenosu http a přenosu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1211">Ability to support multiple authentication modes on a single WCF endpoint when using the HTTP transport and transport security.</span></span>

- <span data-ttu-id="75ebc-1212">Podpora služeb WCF, které používají mezinárodní názvy domén (IDNs).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1212">Support for WCF services that use internationalized domain names (IDNs).</span></span>

<span data-ttu-id="75ebc-1213">Další informace naleznete [v tématu What's New in Windows Communication Foundation](../wcf/whats-new.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1213">For more information, see [What's New in Windows Communication Foundation](../wcf/whats-new.md).</span></span>

<a name="windows_workflow_foundation" />

### <a name="windows-workflow-foundation-wf"></a><span data-ttu-id="75ebc-1214">Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="75ebc-1214">Windows Workflow Foundation (WF)</span></span>

<span data-ttu-id="75ebc-1215">V rozhraní .NET Framework 4.5 bylo do nadace Windows Workflow Foundation (WF) přidáno několik nových funkcí, včetně:</span><span class="sxs-lookup"><span data-stu-id="75ebc-1215">In the .NET Framework 4.5, several new features were added to Windows Workflow Foundation (WF), including:</span></span>

- <span data-ttu-id="75ebc-1216">Pracovní postupy stavového počítače, které byly poprvé zavedeny jako součást rozhraní .NET Framework 4.0.1 ([.NET Framework 4 Platform Update 1](https://docs.microsoft.com/archive/blogs/endpoint/microsoft-net-framework-4-platform-update-1)).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1216">State machine workflows, which were first introduced as part of .NET Framework 4.0.1 ([.NET Framework 4 Platform Update 1](https://docs.microsoft.com/archive/blogs/endpoint/microsoft-net-framework-4-platform-update-1)).</span></span> <span data-ttu-id="75ebc-1217">Tato aktualizace zahrnovala několik nových tříd a aktivit, které vývojářům umožnily vytvářet pracovní postupy stavového počítače.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1217">This update included several new classes and activities that enabled developers to create state machine workflows.</span></span> <span data-ttu-id="75ebc-1218">Tyto třídy a aktivity byly aktualizovány pro rozhraní .NET Framework 4.5 tak, aby zahrnovaly:</span><span class="sxs-lookup"><span data-stu-id="75ebc-1218">These classes and activities were updated for the .NET Framework 4.5 to include:</span></span>

  - <span data-ttu-id="75ebc-1219">Schopnost nastavit zarážky na stavy.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1219">The ability to set breakpoints on states.</span></span>

  - <span data-ttu-id="75ebc-1220">Možnost kopírovat a vkládat přechody v návrháři pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1220">The ability to copy and paste transitions in the workflow designer.</span></span>

  - <span data-ttu-id="75ebc-1221">Podpora návrháře pro vytvoření přechodu sdílené aktivační události.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1221">Designer support for shared trigger transition creation.</span></span>

  - <span data-ttu-id="75ebc-1222">Aktivity pro vytváření pracovních <xref:System.Activities.Statements.StateMachine>postupů <xref:System.Activities.Statements.State>stavového počítače, včetně: , a <xref:System.Activities.Statements.Transition>.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1222">Activities for creating state machine workflows, including: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, and <xref:System.Activities.Statements.Transition>.</span></span>

- <span data-ttu-id="75ebc-1223">Vylepšené funkce návrháře pracovních postupů, jako jsou následující:</span><span class="sxs-lookup"><span data-stu-id="75ebc-1223">Enhanced Workflow Designer features such as the following:</span></span>

  - <span data-ttu-id="75ebc-1224">Vylepšené možnosti hledání pracovních postupů v sadě Visual Studio, včetně **rychlého hledání** a **hledání v souborech**.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1224">Enhanced workflow search capabilities in Visual Studio, including **Quick Find** and **Find in Files**.</span></span>

  - <span data-ttu-id="75ebc-1225">Možnost automaticky vytvořit sequence aktivitu při přidání druhé podřízené aktivity do aktivity kontejneru a zahrnout obě aktivity do aktivity Sekvence.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1225">Ability to automatically create a Sequence activity when a second child activity is added to a container activity, and to include both activities in the Sequence activity.</span></span>

  - <span data-ttu-id="75ebc-1226">Podpora posouvání, která umožňuje změnu viditelné části pracovního postupu bez použití posuvníků.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1226">Panning support, which enables the visible portion of a workflow to be changed without using the scroll bars.</span></span>

  - <span data-ttu-id="75ebc-1227">Nové zobrazení **osnovy dokumentu,** které zobrazuje součásti pracovního postupu v zobrazení osnovy ve stromovém stylu a umožňuje vybrat komponentu v zobrazení **Osnova dokumentu.**</span><span class="sxs-lookup"><span data-stu-id="75ebc-1227">A new **Document Outline** view that shows the components of a workflow in a tree-style outline view and lets you select a component in the **Document Outline** view.</span></span>

  - <span data-ttu-id="75ebc-1228">Možnost přidávat poznámky k aktivitám.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1228">Ability to add annotations to activities.</span></span>

  - <span data-ttu-id="75ebc-1229">Možnost definovat a využívat delegáty aktivit pomocí návrháře pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1229">Ability to define and consume activity delegates by using the workflow designer.</span></span>

  - <span data-ttu-id="75ebc-1230">Automatické připojení a automatické vkládání pro aktivity a přechody v pracovních postupech stavového počítače a vývojového diagramu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1230">Auto-connect and auto-insert for activities and transitions in state machine and flowchart workflows.</span></span>

- <span data-ttu-id="75ebc-1231">Uložení informací o stavu zobrazení pracovního postupu v jediném prvku v souboru XAML, takže můžete snadno vyhledat a upravit informace o stavu zobrazení.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1231">Storage of the view state information for a workflow in a single element in the XAML file, so you can easily locate and edit the view state information.</span></span>

- <span data-ttu-id="75ebc-1232">A NoPersistScope kontejneru aktivity zabránit podřízené aktivity z trvalé.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1232">A NoPersistScope container activity to prevent child activities from persisting.</span></span>

- <span data-ttu-id="75ebc-1233">Podpora výrazů jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="75ebc-1233">Support for C# expressions:</span></span>

  - <span data-ttu-id="75ebc-1234">Projekty pracovního postupu, které používají visual basic, budou používat výrazy jazyka Visual Basic a projekty pracovního postupu jazyka C# budou používat výrazy jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1234">Workflow projects that use Visual Basic will use Visual Basic expressions, and C# workflow projects will use C# expressions.</span></span>

  - <span data-ttu-id="75ebc-1235">C# projekty pracovního postupu, které byly vytvořeny v sadě Visual Studio 2010 a které mají výrazy jazyka Visual Basic jsou kompatibilní s c# workflow projekty, které používají výrazy Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1235">C# workflow projects that were created in Visual Studio 2010 and that have Visual Basic expressions are compatible with C# workflow projects that use C# expressions.</span></span>

- <span data-ttu-id="75ebc-1236">Vylepšení správy verzí:</span><span class="sxs-lookup"><span data-stu-id="75ebc-1236">Versioning enhancements:</span></span>

  - <span data-ttu-id="75ebc-1237">Nová <xref:System.Activities.WorkflowIdentity> třída, která poskytuje mapování mezi trvalou instanci pracovního postupu a její definicí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1237">The new  <xref:System.Activities.WorkflowIdentity> class, which provides a mapping between a persisted workflow instance and its workflow definition.</span></span>

  - <span data-ttu-id="75ebc-1238">Souběžné provádění více verzí pracovního postupu ve stejném <xref:System.ServiceModel.Activities.WorkflowServiceHost>hostiteli, včetně .</span><span class="sxs-lookup"><span data-stu-id="75ebc-1238">Side-by-side execution of multiple workflow versions in the same host, including <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>

  - <span data-ttu-id="75ebc-1239">V dynamické aktualizaci možnost upravit definici instance trvalého pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1239">In Dynamic Update, the ability to modify the definition of a persisted workflow instance.</span></span>

- <span data-ttu-id="75ebc-1240">Vývoj služby pracovního postupu na prvním místě smlouvy, který poskytuje podporu pro automatické generování aktivit tak, aby odpovídaly existující servisní smlouvě.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1240">Contract-first workflow service development, which provides support for automatically generating activities to match an existing service contract.</span></span>

<span data-ttu-id="75ebc-1241">Další informace naleznete [v tématu What's New in Windows Workflow Foundation](../windows-workflow-foundation/whats-new-in-wf-in-dotnet.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1241">For more information, see [What's New in Windows Workflow Foundation](../windows-workflow-foundation/whats-new-in-wf-in-dotnet.md).</span></span>

<a name="tailored" />

### <a name="net-for-windows-8x-store-apps"></a><span data-ttu-id="75ebc-1242">Aplikace .NET pro Windows 8.x Store</span><span class="sxs-lookup"><span data-stu-id="75ebc-1242">.NET for Windows 8.x Store apps</span></span>

<span data-ttu-id="75ebc-1243">Aplikace pro Windows 8.x Store jsou navržené pro konkrétní tvarové faktory a využívají výkon operačního systému Windows.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1243">Windows 8.x Store apps are designed for specific form factors and leverage the power of the Windows operating system.</span></span> <span data-ttu-id="75ebc-1244">Podmnožina rozhraní .NET Framework 4.5 nebo 4.5.1 je k dispozici pro vytváření aplikací pro Windows 8.x Store pro Windows pomocí C# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1244">A subset of the .NET Framework 4.5 or 4.5.1 is available for building Windows 8.x Store apps for Windows by using C# or Visual Basic.</span></span> <span data-ttu-id="75ebc-1245">Tato podmnožina se nazývá .NET pro aplikace pro Windows 8.x Store a je popsána v [přehledu](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1245">This subset is called .NET for Windows 8.x Store apps and is discussed in an [overview](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)).</span></span>

### <a name="portable-class-libraries"></a><span data-ttu-id="75ebc-1246">Knihovny přenosných tříd<a name="portable" /></span><span class="sxs-lookup"><span data-stu-id="75ebc-1246">Portable Class Libraries <a name="portable" /></span></span>

<span data-ttu-id="75ebc-1247">Projekt knihovny přenosných tříd v sadě Visual Studio 2012 (a novějších verzích) umožňuje psát a vytvářet spravovaná sestavení, která fungují na více platformách rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1247">The Portable Class Library project in Visual Studio 2012 (and later versions) enables you to write and build managed assemblies that work on multiple .NET Framework platforms.</span></span> <span data-ttu-id="75ebc-1248">Pomocí projektu knihovny přenosných tříd zvolíte platformy (například Windows Phone a .NET pro aplikace pro Windows 8.x Store), na které chcete cílit.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1248">Using a Portable Class Library project, you choose the platforms (such as Windows Phone and .NET for Windows 8.x Store apps) to target.</span></span> <span data-ttu-id="75ebc-1249">Dostupné typy a členy v projektu jsou automaticky omezeny na běžné typy a členy napříč těmito platformami.</span><span class="sxs-lookup"><span data-stu-id="75ebc-1249">The available types and members in your project are automatically restricted to the common types and members across these platforms.</span></span> <span data-ttu-id="75ebc-1250">Další informace naleznete [v tématu Portable Class Library](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).</span><span class="sxs-lookup"><span data-stu-id="75ebc-1250">For more information, see [Portable Class Library](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="75ebc-1251">Viz také</span><span class="sxs-lookup"><span data-stu-id="75ebc-1251">See also</span></span>

- [<span data-ttu-id="75ebc-1252">Rozhraní .NET Framework a nesvázaná vydání</span><span class="sxs-lookup"><span data-stu-id="75ebc-1252">The .NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
- [<span data-ttu-id="75ebc-1253">Co je nového v usnadnění v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="75ebc-1253">What's new in accessibility in the .NET Framework</span></span>](whats-new-in-accessibility.md)
- [<span data-ttu-id="75ebc-1254">Co je nového ve Visual Studiu 2017</span><span class="sxs-lookup"><span data-stu-id="75ebc-1254">What's New in Visual Studio 2017</span></span>](/visualstudio/ide/whats-new-visual-studio-2017)
- [<span data-ttu-id="75ebc-1255">Co je nového ve Visual Studiu 2019</span><span class="sxs-lookup"><span data-stu-id="75ebc-1255">What's New in Visual Studio 2019</span></span>](/visualstudio/ide/whats-new-visual-studio-2019)
- [<span data-ttu-id="75ebc-1256">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="75ebc-1256">ASP.NET</span></span>](/aspnet)
- [<span data-ttu-id="75ebc-1257">Co je nového pro C++ v Sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="75ebc-1257">What's New for C++ in Visual Studio</span></span>](/cpp/what-s-new-for-visual-cpp-in-visual-studio)
