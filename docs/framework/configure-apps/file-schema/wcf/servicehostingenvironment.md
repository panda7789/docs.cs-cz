---
title: <serviceHostingEnvironment>
ms.date: 03/30/2017
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
ms.openlocfilehash: 165dbed1b78d00f8d4dd3e482b9fee8a23db60da
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399617"
---
# \<serviceHostingEnvironment>
<span data-ttu-id="42601-101">Tento prvek definuje typ, který hostující prostředí služby vytvoří pro konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="42601-101">This element defines the type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="42601-102">Pokud je tento prvek prázdný, je použit výchozí typ.</span><span class="sxs-lookup"><span data-stu-id="42601-102">If this element is empty, the default type is used.</span></span> <span data-ttu-id="42601-103">Tento element lze použít pouze v konfiguračních souborech aplikace nebo na úrovni počítače.</span><span class="sxs-lookup"><span data-stu-id="42601-103">This element can only be used at the application or machine level configuration files.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceHostingEnvironment>**  
  
## <a name="syntax"></a><span data-ttu-id="42601-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42601-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42601-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="42601-105">Attributes and Elements</span></span>  
 <span data-ttu-id="42601-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="42601-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42601-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="42601-107">Attributes</span></span>  
  
|<span data-ttu-id="42601-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="42601-108">Attribute</span></span>|<span data-ttu-id="42601-109">Popis</span><span class="sxs-lookup"><span data-stu-id="42601-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="42601-110">aspNetCompatibilityEnabled</span><span class="sxs-lookup"><span data-stu-id="42601-110">aspNetCompatibilityEnabled</span></span>|<span data-ttu-id="42601-111">Logická hodnota označující, zda byl v aktuální aplikaci zapnut režim kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="42601-111">A Boolean value indicating whether the ASP.NET compatibility mode has been turned on for the current application.</span></span> <span data-ttu-id="42601-112">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="42601-112">The default is `false`.</span></span><br /><br /> <span data-ttu-id="42601-113">Pokud je tento atribut nastaven na hodnotu `true` , požadavky na služby Windows Communication Foundation (WCF) tok prostřednictvím kanálu HTTP ASP.NET a komunikace přes protokoly bez protokolu HTTP je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="42601-113">When this attribute is set to `true`, requests to Windows Communication Foundation (WCF) services flow through the ASP.NET HTTP pipeline, and communication over non-HTTP protocols is prohibited.</span></span> <span data-ttu-id="42601-114">Další informace najdete v tématu [služby WCF a ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="42601-114">For more information, see [WCF Services and ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md).</span></span>|  
|<span data-ttu-id="42601-115">Služby minFreeMemoryPercentageToActivateService</span><span class="sxs-lookup"><span data-stu-id="42601-115">minFreeMemoryPercentageToActivateService</span></span>|<span data-ttu-id="42601-116">Celé číslo, které určuje minimální velikost volné paměti, která by měla být k dispozici systému, než bude možné aktivovat službu WCF.</span><span class="sxs-lookup"><span data-stu-id="42601-116">An integer that specifies the minimum amount of free memory that should be available to the system, before a WCF service can be activated.</span></span> <span data-ttu-id="42601-117">**Upozornění:**  Zadání tohoto atributu společně s částečným vztahem důvěryhodnosti v souboru Web. config služby WCF bude mít za následek <xref:System.Security.SecurityException> spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="42601-117">**Caution:**  Specifying this attribute along with partial trust in the web.config file of a WCF service will result in a <xref:System.Security.SecurityException> when the service is run.</span></span>|  
|<span data-ttu-id="42601-118">multipleSiteBindingsEnabled</span><span class="sxs-lookup"><span data-stu-id="42601-118">multipleSiteBindingsEnabled</span></span>|<span data-ttu-id="42601-119">Logická hodnota, která určuje, zda je povoleno více vazeb služby IIS na jednom webu.</span><span class="sxs-lookup"><span data-stu-id="42601-119">A Boolean value that specifies whether multiple IIS bindings per site is enabled.</span></span><br /><br /> <span data-ttu-id="42601-120">Služba IIS se skládá z webů, které jsou kontejnery pro virtuální aplikace obsahující virtuální adresáře.</span><span class="sxs-lookup"><span data-stu-id="42601-120">IIS consists of web sites, which are containers for virtual applications containing virtual directories.</span></span> <span data-ttu-id="42601-121">Aplikace v lokalitě je k dispozici prostřednictvím jedné nebo více vazeb služby IIS.</span><span class="sxs-lookup"><span data-stu-id="42601-121">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="42601-122">Vazba služby IIS poskytuje dvě části informací: protokol vazby a informace o vazbě.</span><span class="sxs-lookup"><span data-stu-id="42601-122">An IIS binding provides two pieces of information: a binding protocol and binding information.</span></span> <span data-ttu-id="42601-123">Protokol vazby definuje schéma, přes které probíhá komunikace, a informace o vazbě, které slouží k přístupu k webu.</span><span class="sxs-lookup"><span data-stu-id="42601-123">Binding protocol defines the scheme over which communication occurs, and binding information is the information used to access the site.</span></span> <span data-ttu-id="42601-124">Příkladem protokolu vazby může být HTTP, zatímco informace o vazbě můžou obsahovat IP adresu, port, hlavičku hostitele atd.</span><span class="sxs-lookup"><span data-stu-id="42601-124">An example of a binding protocol can be HTTP, whereas binding information can contain an IP address, Port, host header, etc.</span></span><br /><br /> <span data-ttu-id="42601-125">Služba IIS podporuje zadání více vazeb služby IIS na jeden web, což vede k vytvoření více základních adres na schéma.</span><span class="sxs-lookup"><span data-stu-id="42601-125">IIS supports specifying multiple IIS bindings per site, which results in multiple base addresses per scheme.</span></span> <span data-ttu-id="42601-126">Služba Windows Communication Foundation (WCF) hostovaná v lokalitě však umožňuje vytvořit vazbu pouze na jednu hodnotu baseAddress na schéma.</span><span class="sxs-lookup"><span data-stu-id="42601-126">However, a Windows Communication Foundation (WCF) service hosted under a site allows binding to only one baseAddress per scheme.</span></span><br /><br /> <span data-ttu-id="42601-127">Chcete-li povolit více vazeb služby IIS na webu pro službu Windows Communication Foundation (WCF), nastavte tento atribut na hodnotu `true` .</span><span class="sxs-lookup"><span data-stu-id="42601-127">To enable multiple IIS bindings per site for a Windows Communication Foundation (WCF) service, set this attribute to `true`.</span></span> <span data-ttu-id="42601-128">Všimněte si, že více vazeb webu je podporováno pouze pro protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="42601-128">Notice that multiple site binding is supported only for the HTTP protocol.</span></span> <span data-ttu-id="42601-129">Adresa koncových bodů v konfiguračním souboru musí být úplný identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="42601-129">The address of endpoints in the configuration file needs to be a complete URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="42601-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="42601-130">Child Elements</span></span>  
  
|<span data-ttu-id="42601-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="42601-131">Element</span></span>|<span data-ttu-id="42601-132">Description</span><span class="sxs-lookup"><span data-stu-id="42601-132">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](baseaddressprefixfilters.md)|<span data-ttu-id="42601-133">Kolekce elementů konfigurace, které určují filtry předpony pro základní adresy používané hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="42601-133">A collection of configuration elements that specify prefix filters for the base addresses used by the service host.</span></span>|  
|[\<serviceActivations>](serviceactivations.md)|<span data-ttu-id="42601-134">Konfigurační oddíl, který popisuje nastavení aktivace.</span><span class="sxs-lookup"><span data-stu-id="42601-134">A configuration section that describes activation settings.</span></span>|  
|[\<transportConfigurationTypes>](transportconfigurationtypes.md)|<span data-ttu-id="42601-135">Kolekce elementů konfigurace, které identifikují typ konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="42601-135">A collection of configuration elements that identify the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="42601-136">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="42601-136">Parent Elements</span></span>  
  
|<span data-ttu-id="42601-137">Prvek</span><span class="sxs-lookup"><span data-stu-id="42601-137">Element</span></span>|<span data-ttu-id="42601-138">Description</span><span class="sxs-lookup"><span data-stu-id="42601-138">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="42601-139">serviceModel</span><span class="sxs-lookup"><span data-stu-id="42601-139">serviceModel</span></span>|<span data-ttu-id="42601-140">Kořenový element všech prvků konfigurace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="42601-140">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42601-141">Poznámky</span><span class="sxs-lookup"><span data-stu-id="42601-141">Remarks</span></span>  
 <span data-ttu-id="42601-142">Ve výchozím nastavení jsou služby WCF spouštěny souběžně s ASP.NET v doménách hostované aplikace (AppDomain).</span><span class="sxs-lookup"><span data-stu-id="42601-142">By default, WCF services run side-by-side with ASP.NET in hosted Application Domains (AppDomain).</span></span> <span data-ttu-id="42601-143">I když WCF a ASP.NET můžou existovat ve stejné doméně AppDomain, požadavky WCF nejsou ve výchozím nastavení zpracovávány kanálem HTTP ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="42601-143">Even though WCF and ASP.NET can coexist in the same AppDomain, WCF requests are not processed by the ASP.NET HTTP Pipeline by default.</span></span> <span data-ttu-id="42601-144">V důsledku toho nejsou služby WCF k dispozici několik prvků aplikace ASP.NET Application Platform.</span><span class="sxs-lookup"><span data-stu-id="42601-144">As a result, several elements of the ASP.NET application platform are not available to WCF services.</span></span> <span data-ttu-id="42601-145">Mezi ně patří</span><span class="sxs-lookup"><span data-stu-id="42601-145">These include</span></span>  
  
- <span data-ttu-id="42601-146">ASP.NET/autorizace adresy URL</span><span class="sxs-lookup"><span data-stu-id="42601-146">ASP.NET File/URL Authorization</span></span>  
  
- <span data-ttu-id="42601-147">Zosobnění technologie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="42601-147">ASP.NET Impersonation</span></span>  
  
- <span data-ttu-id="42601-148">Stav relace na základě souborů cookie</span><span class="sxs-lookup"><span data-stu-id="42601-148">Cookie-based Session State</span></span>  
  
- <span data-ttu-id="42601-149">HttpContext. Current</span><span class="sxs-lookup"><span data-stu-id="42601-149">HttpContext.Current</span></span>  
  
- <span data-ttu-id="42601-150">Rozšiřitelnost kanálu prostřednictvím vlastního HttpModuleu</span><span class="sxs-lookup"><span data-stu-id="42601-150">Pipeline Extensibility via custom HttpModule</span></span>  
  
 <span data-ttu-id="42601-151">Pokud vaše služby WCF potřebují fungovat v kontextu ASP.NET a komunikují pouze přes protokol HTTP, můžete použít režim kompatibility WCF ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="42601-151">If your WCF services need to function in the ASP.NET context, and communicate only over HTTP, you can use WCF’s ASP.NET compatibility mode.</span></span> <span data-ttu-id="42601-152">Tento režim je zapnutý, když `aspNetCompatibilityEnabled` je atribut nastavený na `true` úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="42601-152">This mode is turned on when the `aspNetCompatibilityEnabled` attribute is set to `true` at the application level.</span></span> <span data-ttu-id="42601-153">Implementace služeb musí deklarovat jejich schopnost spouštět v režimu kompatibility pomocí <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="42601-153">Service implementations must declare their ability to run in compatibility mode using the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> class.</span></span> <span data-ttu-id="42601-154">Pokud je povolen režim kompatibility,</span><span class="sxs-lookup"><span data-stu-id="42601-154">When the compatibility mode is enabled,</span></span>  
  
- <span data-ttu-id="42601-155">Před autorizací WCF se vynutila autorizace souboru nebo adresy URL ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="42601-155">ASP.NET File/URL Authorization is enforced prior to WCF authorization.</span></span> <span data-ttu-id="42601-156">Rozhodnutí o autorizaci vychází z identity na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="42601-156">An authorization decision is based on the transport-level identity of the request.</span></span> <span data-ttu-id="42601-157">Identity na úrovni zprávy se ignorují.</span><span class="sxs-lookup"><span data-stu-id="42601-157">Identities at the message level are ignored.</span></span>  
  
- <span data-ttu-id="42601-158">Operace služby WCF se začnou spouštět v kontextu zosobnění ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="42601-158">WCF service operations start to execute in the ASP.NET impersonation context.</span></span> <span data-ttu-id="42601-159">Pokud jsou pro konkrétní službu povolené zosobnění ASP.NET a zosobnění WCF, použije se kontext zosobnění WCF.</span><span class="sxs-lookup"><span data-stu-id="42601-159">If both ASP.NET impersonation and WCF impersonation are enabled for a specific service, the WCF impersonation context applies.</span></span>  
  
- <span data-ttu-id="42601-160">Vlastnost HttpContext. Current lze použít z kódu služby WCF. služby zabraňují úniku koncových bodů mimo HTTP.</span><span class="sxs-lookup"><span data-stu-id="42601-160">HttpContext.Current can be used from WCF service code, and services are prevented from exposing non-HTTP endpoints.</span></span>  
  
- <span data-ttu-id="42601-161">Požadavky služby WCF zpracovává kanál ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="42601-161">WCF requests are processed by the ASP.NET pipeline.</span></span> <span data-ttu-id="42601-162">HttpModules, které byly nakonfigurovány na zpracování příchozích požadavků, mohou také zpracovávat požadavky WCF.</span><span class="sxs-lookup"><span data-stu-id="42601-162">HttpModules that have been configured to act on incoming requests can also process WCF requests.</span></span> <span data-ttu-id="42601-163">Mezi ně můžou patřit komponenty platformy ASP.NET (například <xref:System.Web.SessionState.SessionStateModule> ) a také vlastní moduly třetích stran.</span><span class="sxs-lookup"><span data-stu-id="42601-163">These can include ASP.NET platform components (e.g., <xref:System.Web.SessionState.SessionStateModule>), as well as custom third party modules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42601-164">Příklad</span><span class="sxs-lookup"><span data-stu-id="42601-164">Example</span></span>  
 <span data-ttu-id="42601-165">Následující ukázka kódu ukazuje, jak povolit režim kompatibility ASP.</span><span class="sxs-lookup"><span data-stu-id="42601-165">The following code sample shows how to enable ASP Compatibility Mode.</span></span>  
  
## <a name="code"></a><span data-ttu-id="42601-166">Kód</span><span class="sxs-lookup"><span data-stu-id="42601-166">Code</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
```  
  
## <a name="see-also"></a><span data-ttu-id="42601-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="42601-167">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="42601-168">Hosting</span><span class="sxs-lookup"><span data-stu-id="42601-168">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
- [<span data-ttu-id="42601-169">Služby WCF a ASP.NET</span><span class="sxs-lookup"><span data-stu-id="42601-169">WCF Services and ASP.NET</span></span>](../../../wcf/feature-details/wcf-services-and-aspnet.md)
