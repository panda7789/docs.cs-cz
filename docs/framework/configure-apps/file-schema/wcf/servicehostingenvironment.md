---
title: <serviceHostingEnvironment>
ms.date: 03/30/2017
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
ms.openlocfilehash: 165dbed1b78d00f8d4dd3e482b9fee8a23db60da
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399617"
---
# <a name="servicehostingenvironment"></a><span data-ttu-id="ce9c0-101">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="ce9c0-101">\<serviceHostingEnvironment></span></span>
<span data-ttu-id="ce9c0-102">Tento prvek definuje typ, který hostující prostředí služby vytvoří pro konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-102">This element defines the type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="ce9c0-103">Pokud je tento prvek prázdný, je použit výchozí typ.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-103">If this element is empty, the default type is used.</span></span> <span data-ttu-id="ce9c0-104">Tento element lze použít pouze v konfiguračních souborech aplikace nebo na úrovni počítače.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-104">This element can only be used at the application or machine level configuration files.</span></span>  
  
<span data-ttu-id="ce9c0-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ce9c0-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ce9c0-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ce9c0-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ce9c0-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceHostingEnvironment >**</span><span class="sxs-lookup"><span data-stu-id="ce9c0-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceHostingEnvironment>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce9c0-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce9c0-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="Boolean"
                           minFreeMemoryPercentageToActivateService="Integer"
                           multipleSiteBindingsEnabled="Boolean">
  <baseAddressPrefixFilters>
    <add prefix="string" />
  </baseAddressPrefixFilters>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce9c0-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ce9c0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ce9c0-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce9c0-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="ce9c0-111">Attributes</span></span>  
  
|<span data-ttu-id="ce9c0-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="ce9c0-112">Attribute</span></span>|<span data-ttu-id="ce9c0-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ce9c0-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ce9c0-114">aspNetCompatibilityEnabled</span><span class="sxs-lookup"><span data-stu-id="ce9c0-114">aspNetCompatibilityEnabled</span></span>|<span data-ttu-id="ce9c0-115">Logická hodnota označující, zda byl v aktuální aplikaci zapnut režim kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-115">A Boolean value indicating whether the ASP.NET compatibility mode has been turned on for the current application.</span></span> <span data-ttu-id="ce9c0-116">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-116">The default is `false`.</span></span><br /><br /> <span data-ttu-id="ce9c0-117">Pokud je tento atribut nastaven na `true`hodnotu, požadavky na služby Windows Communication Foundation (WCF) tok prostřednictvím kanálu HTTP ASP.NET a komunikace přes protokoly bez protokolu HTTP je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-117">When this attribute is set to `true`, requests to Windows Communication Foundation (WCF) services flow through the ASP.NET HTTP pipeline, and communication over non-HTTP protocols is prohibited.</span></span> <span data-ttu-id="ce9c0-118">Další informace najdete v tématu [služby WCF a ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="ce9c0-118">For more information, see [WCF Services and ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md).</span></span>|  
|<span data-ttu-id="ce9c0-119">minFreeMemoryPercentageToActivateService</span><span class="sxs-lookup"><span data-stu-id="ce9c0-119">minFreeMemoryPercentageToActivateService</span></span>|<span data-ttu-id="ce9c0-120">Celé číslo, které určuje minimální velikost volné paměti, která by měla být k dispozici systému, než bude možné aktivovat službu WCF.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-120">An integer that specifies the minimum amount of free memory that should be available to the system, before a WCF service can be activated.</span></span> <span data-ttu-id="ce9c0-121">**Upozornění**  Zadání tohoto atributu společně s částečným vztahem důvěryhodnosti v souboru Web. config služby WCF bude mít za následek <xref:System.Security.SecurityException> spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-121">**Caution:**  Specifying this attribute along with partial trust in the web.config file of a WCF service will result in a <xref:System.Security.SecurityException> when the service is run.</span></span>|  
|<span data-ttu-id="ce9c0-122">multipleSiteBindingsEnabled</span><span class="sxs-lookup"><span data-stu-id="ce9c0-122">multipleSiteBindingsEnabled</span></span>|<span data-ttu-id="ce9c0-123">Logická hodnota, která určuje, zda je povoleno více vazeb služby IIS na jednom webu.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-123">A Boolean value that specifies whether multiple IIS bindings per site is enabled.</span></span><br /><br /> <span data-ttu-id="ce9c0-124">Služba IIS se skládá z webů, které jsou kontejnery pro virtuální aplikace obsahující virtuální adresáře.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-124">IIS consists of web sites, which are containers for virtual applications containing virtual directories.</span></span> <span data-ttu-id="ce9c0-125">Aplikace v lokalitě je k dispozici prostřednictvím jedné nebo více vazeb služby IIS.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-125">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="ce9c0-126">Vazba služby IIS poskytuje dvě části informací: protokol vazby a informace o vazbě.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-126">An IIS binding provides two pieces of information: a binding protocol and binding information.</span></span> <span data-ttu-id="ce9c0-127">Protokol vazby definuje schéma, přes které probíhá komunikace, a informace o vazbě, které slouží k přístupu k webu.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-127">Binding protocol defines the scheme over which communication occurs, and binding information is the information used to access the site.</span></span> <span data-ttu-id="ce9c0-128">Příkladem protokolu vazby může být HTTP, zatímco informace o vazbě můžou obsahovat IP adresu, port, hlavičku hostitele atd.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-128">An example of a binding protocol can be HTTP, whereas binding information can contain an IP address, Port, host header, etc.</span></span><br /><br /> <span data-ttu-id="ce9c0-129">Služba IIS podporuje zadání více vazeb služby IIS na jeden web, což vede k vytvoření více základních adres na schéma.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-129">IIS supports specifying multiple IIS bindings per site, which results in multiple base addresses per scheme.</span></span> <span data-ttu-id="ce9c0-130">Služba Windows Communication Foundation (WCF) hostovaná v lokalitě však umožňuje vytvořit vazbu pouze na jednu hodnotu baseAddress na schéma.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-130">However, a Windows Communication Foundation (WCF) service hosted under a site allows binding to only one baseAddress per scheme.</span></span><br /><br /> <span data-ttu-id="ce9c0-131">Chcete-li povolit více vazeb služby IIS na webu pro službu Windows Communication Foundation (WCF), nastavte tento `true`atribut na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-131">To enable multiple IIS bindings per site for a Windows Communication Foundation (WCF) service, set this attribute to `true`.</span></span> <span data-ttu-id="ce9c0-132">Všimněte si, že více vazeb webu je podporováno pouze pro protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-132">Notice that multiple site binding is supported only for the HTTP protocol.</span></span> <span data-ttu-id="ce9c0-133">Adresa koncových bodů v konfiguračním souboru musí být úplný identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-133">The address of endpoints in the configuration file needs to be a complete URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce9c0-134">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ce9c0-134">Child Elements</span></span>  
  
|<span data-ttu-id="ce9c0-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="ce9c0-135">Element</span></span>|<span data-ttu-id="ce9c0-136">Popis</span><span class="sxs-lookup"><span data-stu-id="ce9c0-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce9c0-137">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="ce9c0-137">\<baseAddressPrefixFilters></span></span>](baseaddressprefixfilters.md)|<span data-ttu-id="ce9c0-138">Kolekce elementů konfigurace, které určují filtry předpony pro základní adresy používané hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-138">A collection of configuration elements that specify prefix filters for the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="ce9c0-139">\<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="ce9c0-139">\<serviceActivations></span></span>](serviceactivations.md)|<span data-ttu-id="ce9c0-140">Konfigurační oddíl, který popisuje nastavení aktivace.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-140">A configuration section that describes activation settings.</span></span>|  
|[<span data-ttu-id="ce9c0-141">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="ce9c0-141">\<transportConfigurationTypes></span></span>](transportconfigurationtypes.md)|<span data-ttu-id="ce9c0-142">Kolekce elementů konfigurace, které identifikují typ konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-142">A collection of configuration elements that identify the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ce9c0-143">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ce9c0-143">Parent Elements</span></span>  
  
|<span data-ttu-id="ce9c0-144">Prvek</span><span class="sxs-lookup"><span data-stu-id="ce9c0-144">Element</span></span>|<span data-ttu-id="ce9c0-145">Popis</span><span class="sxs-lookup"><span data-stu-id="ce9c0-145">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ce9c0-146">serviceModel</span><span class="sxs-lookup"><span data-stu-id="ce9c0-146">serviceModel</span></span>|<span data-ttu-id="ce9c0-147">Kořenový element všech prvků konfigurace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ce9c0-147">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce9c0-148">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ce9c0-148">Remarks</span></span>  
 <span data-ttu-id="ce9c0-149">Ve výchozím nastavení jsou služby WCF spouštěny souběžně s ASP.NET v doménách hostované aplikace (AppDomain).</span><span class="sxs-lookup"><span data-stu-id="ce9c0-149">By default, WCF services run side-by-side with ASP.NET in hosted Application Domains (AppDomain).</span></span> <span data-ttu-id="ce9c0-150">I když WCF a ASP.NET můžou existovat ve stejné doméně AppDomain, požadavky WCF nejsou ve výchozím nastavení zpracovávány kanálem HTTP ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-150">Even though WCF and ASP.NET can coexist in the same AppDomain, WCF requests are not processed by the ASP.NET HTTP Pipeline by default.</span></span> <span data-ttu-id="ce9c0-151">V důsledku toho nejsou služby WCF k dispozici několik prvků aplikace ASP.NET Application Platform.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-151">As a result, several elements of the ASP.NET application platform are not available to WCF services.</span></span> <span data-ttu-id="ce9c0-152">Mezi ně patří</span><span class="sxs-lookup"><span data-stu-id="ce9c0-152">These include</span></span>  
  
- <span data-ttu-id="ce9c0-153">ASP.NET/autorizace adresy URL</span><span class="sxs-lookup"><span data-stu-id="ce9c0-153">ASP.NET File/URL Authorization</span></span>  
  
- <span data-ttu-id="ce9c0-154">Zosobnění ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ce9c0-154">ASP.NET Impersonation</span></span>  
  
- <span data-ttu-id="ce9c0-155">Stav relace na základě souborů cookie</span><span class="sxs-lookup"><span data-stu-id="ce9c0-155">Cookie-based Session State</span></span>  
  
- <span data-ttu-id="ce9c0-156">HttpContext.Current</span><span class="sxs-lookup"><span data-stu-id="ce9c0-156">HttpContext.Current</span></span>  
  
- <span data-ttu-id="ce9c0-157">Rozšiřitelnost kanálu prostřednictvím vlastního HttpModuleu</span><span class="sxs-lookup"><span data-stu-id="ce9c0-157">Pipeline Extensibility via custom HttpModule</span></span>  
  
 <span data-ttu-id="ce9c0-158">Pokud vaše služby WCF potřebují fungovat v kontextu ASP.NET a komunikují pouze přes protokol HTTP, můžete použít režim kompatibility WCF ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-158">If your WCF services need to function in the ASP.NET context, and communicate only over HTTP, you can use WCF’s ASP.NET compatibility mode.</span></span> <span data-ttu-id="ce9c0-159">Tento režim je zapnutý, když `aspNetCompatibilityEnabled` je atribut `true` nastavený na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-159">This mode is turned on when the `aspNetCompatibilityEnabled` attribute is set to `true` at the application level.</span></span> <span data-ttu-id="ce9c0-160">Implementace služeb musí deklarovat jejich schopnost spouštět v režimu kompatibility pomocí <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-160">Service implementations must declare their ability to run in compatibility mode using the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> class.</span></span> <span data-ttu-id="ce9c0-161">Pokud je povolen režim kompatibility,</span><span class="sxs-lookup"><span data-stu-id="ce9c0-161">When the compatibility mode is enabled,</span></span>  
  
- <span data-ttu-id="ce9c0-162">Před autorizací WCF se vynutila autorizace souboru nebo adresy URL ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-162">ASP.NET File/URL Authorization is enforced prior to WCF authorization.</span></span> <span data-ttu-id="ce9c0-163">Rozhodnutí o autorizaci vychází z identity na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-163">An authorization decision is based on the transport-level identity of the request.</span></span> <span data-ttu-id="ce9c0-164">Identity na úrovni zprávy se ignorují.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-164">Identities at the message level are ignored.</span></span>  
  
- <span data-ttu-id="ce9c0-165">Operace služby WCF se začnou spouštět v kontextu zosobnění ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-165">WCF service operations start to execute in the ASP.NET impersonation context.</span></span> <span data-ttu-id="ce9c0-166">Pokud jsou pro konkrétní službu povolené zosobnění ASP.NET a zosobnění WCF, použije se kontext zosobnění WCF.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-166">If both ASP.NET impersonation and WCF impersonation are enabled for a specific service, the WCF impersonation context applies.</span></span>  
  
- <span data-ttu-id="ce9c0-167">Vlastnost HttpContext. Current lze použít z kódu služby WCF. služby zabraňují úniku koncových bodů mimo HTTP.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-167">HttpContext.Current can be used from WCF service code, and services are prevented from exposing non-HTTP endpoints.</span></span>  
  
- <span data-ttu-id="ce9c0-168">Požadavky služby WCF zpracovává kanál ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-168">WCF requests are processed by the ASP.NET pipeline.</span></span> <span data-ttu-id="ce9c0-169">HttpModules, které byly nakonfigurovány na zpracování příchozích požadavků, mohou také zpracovávat požadavky WCF.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-169">HttpModules that have been configured to act on incoming requests can also process WCF requests.</span></span> <span data-ttu-id="ce9c0-170">Mezi ně můžou patřit komponenty platformy ASP.NET ( <xref:System.Web.SessionState.SessionStateModule>například) a také vlastní moduly třetích stran.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-170">These can include ASP.NET platform components (e.g., <xref:System.Web.SessionState.SessionStateModule>), as well as custom third party modules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce9c0-171">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce9c0-171">Example</span></span>  
 <span data-ttu-id="ce9c0-172">Následující ukázka kódu ukazuje, jak povolit režim kompatibility ASP.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-172">The following code sample shows how to enable ASP Compatibility Mode.</span></span>  
  
## <a name="code"></a><span data-ttu-id="ce9c0-173">Kód</span><span class="sxs-lookup"><span data-stu-id="ce9c0-173">Code</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
```  
  
## <a name="see-also"></a><span data-ttu-id="ce9c0-174">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce9c0-174">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="ce9c0-175">Hostování</span><span class="sxs-lookup"><span data-stu-id="ce9c0-175">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
- [<span data-ttu-id="ce9c0-176">Služby WCF a ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ce9c0-176">WCF Services and ASP.NET</span></span>](../../../wcf/feature-details/wcf-services-and-aspnet.md)
