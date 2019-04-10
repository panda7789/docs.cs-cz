---
title: <serviceHostingEnvironment>
ms.date: 03/30/2017
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
ms.openlocfilehash: 24cf36aba81b5bb31eaac475361e2d07bc6f8b12
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215986"
---
# <a name="servicehostingenvironment"></a><span data-ttu-id="5d5b0-101">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="5d5b0-101">\<serviceHostingEnvironment></span></span>
<span data-ttu-id="5d5b0-102">Tento prvek definuje typ, který vytvoří instanci hostitelským prostředím služby pro konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-102">This element defines the type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="5d5b0-103">Pokud tento prvek je prázdný, je použit výchozí typ.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-103">If this element is empty, the default type is used.</span></span> <span data-ttu-id="5d5b0-104">Tento prvek jde použít jenom na aplikace nebo na úrovni konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-104">This element can only be used at the application or machine level configuration files.</span></span>  
  
 <span data-ttu-id="5d5b0-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5d5b0-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="5d5b0-106">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="5d5b0-106">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d5b0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d5b0-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d5b0-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5d5b0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5d5b0-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d5b0-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="5d5b0-110">Attributes</span></span>  
  
|<span data-ttu-id="5d5b0-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="5d5b0-111">Attribute</span></span>|<span data-ttu-id="5d5b0-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5d5b0-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5d5b0-113">aspNetCompatibilityEnabled</span><span class="sxs-lookup"><span data-stu-id="5d5b0-113">aspNetCompatibilityEnabled</span></span>|<span data-ttu-id="5d5b0-114">Logická hodnota označující, zda režim kompatibility ASP.NET je zapnutý pro aktuální aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-114">A Boolean value indicating whether the ASP.NET compatibility mode has been turned on for the current application.</span></span> <span data-ttu-id="5d5b0-115">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-115">The default is `false`.</span></span><br /><br /> <span data-ttu-id="5d5b0-116">Když tento atribut je nastaven na `true`požadavků na služby Windows Communication Foundation (WCF) tok prostřednictvím kanálu HTTP technologie ASP.NET a komunikaci přes protokoly jiným protokolem než HTTP je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-116">When this attribute is set to `true`, requests to Windows Communication Foundation (WCF) services flow through the ASP.NET HTTP pipeline, and communication over non-HTTP protocols is prohibited.</span></span> <span data-ttu-id="5d5b0-117">Další informace najdete v tématu [služby WCF a ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="5d5b0-117">For more information, see [WCF Services and ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span></span>|  
|<span data-ttu-id="5d5b0-118">minFreeMemoryPercentageToActivateService</span><span class="sxs-lookup"><span data-stu-id="5d5b0-118">minFreeMemoryPercentageToActivateService</span></span>|<span data-ttu-id="5d5b0-119">Celé číslo určující minimální množství volné paměti, která má být k dispozici systému, před aktivací služby WCF.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-119">An integer that specifies the minimum amount of free memory that should be available to the system, before a WCF service can be activated.</span></span> <span data-ttu-id="5d5b0-120">**Upozornění:**  Zadání tohoto atributu společně s částečnou důvěryhodností v souboru web.config služby WCF způsobí <xref:System.Security.SecurityException> při spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-120">**Caution:**  Specifying this attribute along with partial trust in the web.config file of a WCF service will result in a <xref:System.Security.SecurityException> when the service is run.</span></span>|  
|<span data-ttu-id="5d5b0-121">multipleSiteBindingsEnabled</span><span class="sxs-lookup"><span data-stu-id="5d5b0-121">multipleSiteBindingsEnabled</span></span>|<span data-ttu-id="5d5b0-122">Logická hodnota, která určuje, zda je povoleno více vazeb služby IIS webu.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-122">A Boolean value that specifies whether multiple IIS bindings per site is enabled.</span></span><br /><br /> <span data-ttu-id="5d5b0-123">IIS se skládá z webů, které jsou kontejnery pro virtuální aplikace obsahující virtuální adresáře.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-123">IIS consists of web sites, which are containers for virtual applications containing virtual directories.</span></span> <span data-ttu-id="5d5b0-124">Aplikace v síti přístupné prostřednictvím jednoho nebo více vazeb služby IIS.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-124">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="5d5b0-125">Vazby služby IIS poskytuje dva druhy údajů: protokol vazby a informace o vazbě.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-125">An IIS binding provides two pieces of information: a binding protocol and binding information.</span></span> <span data-ttu-id="5d5b0-126">Vazba protokolu definuje schéma, přes které probíhá komunikace a informace o vazbě je informace, které slouží pro přístup k webu.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-126">Binding protocol defines the scheme over which communication occurs, and binding information is the information used to access the site.</span></span> <span data-ttu-id="5d5b0-127">Příklad vazby protokolu může být HTTP, kdežto informace o vazbě může obsahovat IP adresu, Port, hlavičku hostitele, atd.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-127">An example of a binding protocol can be HTTP, whereas binding information can contain an IP address, Port, host header, etc.</span></span><br /><br /> <span data-ttu-id="5d5b0-128">Služba IIS podporuje zadávání více vazeb služby IIS webu, což vede k více základních adres na jedno schéma.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-128">IIS supports specifying multiple IIS bindings per site, which results in multiple base addresses per scheme.</span></span> <span data-ttu-id="5d5b0-129">Hostované na webu služby Windows Communication Foundation (WCF) umožňuje však vazba pouze jedna vlastnost baseAddress jedno schéma.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-129">However, a Windows Communication Foundation (WCF) service hosted under a site allows binding to only one baseAddress per scheme.</span></span><br /><br /> <span data-ttu-id="5d5b0-130">Pokud chcete povolit více vazeb služby IIS webu pro službu Windows Communication Foundation (WCF), tento atribut nastavte na `true`.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-130">To enable multiple IIS bindings per site for a Windows Communication Foundation (WCF) service, set this attribute to `true`.</span></span> <span data-ttu-id="5d5b0-131">Všimněte si, že více vazeb webu se podporuje jenom pro protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-131">Notice that multiple site binding is supported only for the HTTP protocol.</span></span> <span data-ttu-id="5d5b0-132">Adresy koncových bodů v konfiguračním souboru musí být úplný identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-132">The address of endpoints in the configuration file needs to be a complete URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d5b0-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5d5b0-133">Child Elements</span></span>  
  
|<span data-ttu-id="5d5b0-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="5d5b0-134">Element</span></span>|<span data-ttu-id="5d5b0-135">Popis</span><span class="sxs-lookup"><span data-stu-id="5d5b0-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d5b0-136">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="5d5b0-136">\<baseAddressPrefixFilters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|<span data-ttu-id="5d5b0-137">Kolekci konfiguračních elementů určujících předponu filtry pro základní adresy použité hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-137">A collection of configuration elements that specify prefix filters for the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="5d5b0-138">\<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="5d5b0-138">\<serviceActivations></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceactivations.md)|<span data-ttu-id="5d5b0-139">Konfigurační oddíl, který popisuje nastavení aktivace.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-139">A configuration section that describes activation settings.</span></span>|  
|[<span data-ttu-id="5d5b0-140">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="5d5b0-140">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="5d5b0-141">Kolekce elementů konfigurace, které určují typ konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-141">A collection of configuration elements that identify the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5d5b0-142">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5d5b0-142">Parent Elements</span></span>  
  
|<span data-ttu-id="5d5b0-143">Prvek</span><span class="sxs-lookup"><span data-stu-id="5d5b0-143">Element</span></span>|<span data-ttu-id="5d5b0-144">Popis</span><span class="sxs-lookup"><span data-stu-id="5d5b0-144">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5d5b0-145">serviceModel</span><span class="sxs-lookup"><span data-stu-id="5d5b0-145">serviceModel</span></span>|<span data-ttu-id="5d5b0-146">Kořenový element všechny elementy konfigurace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5d5b0-146">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d5b0-147">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5d5b0-147">Remarks</span></span>  
 <span data-ttu-id="5d5b0-148">Ve výchozím nastavení služby WCF spuštění – souběžně s rozhraním ASP.NET v prostředí domény aplikace (AppDomain).</span><span class="sxs-lookup"><span data-stu-id="5d5b0-148">By default, WCF services run side-by-side with ASP.NET in hosted Application Domains (AppDomain).</span></span> <span data-ttu-id="5d5b0-149">I když WCF a ASP.NET mohou existovat vedle sebe v téže doméně AppDomain, WCF požadavky nejsou zpracovávány kanálu HTTP ASP.NET ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-149">Even though WCF and ASP.NET can coexist in the same AppDomain, WCF requests are not processed by the ASP.NET HTTP Pipeline by default.</span></span> <span data-ttu-id="5d5b0-150">Několik prvků platformy aplikace ASP.NET v důsledku toho nejsou k dispozici ke službám WCF.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-150">As a result, several elements of the ASP.NET application platform are not available to WCF services.</span></span> <span data-ttu-id="5d5b0-151">Patří mezi ně</span><span class="sxs-lookup"><span data-stu-id="5d5b0-151">These include</span></span>  
  
-   <span data-ttu-id="5d5b0-152">Autorizace souboru nebo adresy URL technologie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5d5b0-152">ASP.NET File/URL Authorization</span></span>  
  
-   <span data-ttu-id="5d5b0-153">ASP.NET Impersonation</span><span class="sxs-lookup"><span data-stu-id="5d5b0-153">ASP.NET Impersonation</span></span>  
  
-   <span data-ttu-id="5d5b0-154">Stav relace na základě souboru cookie</span><span class="sxs-lookup"><span data-stu-id="5d5b0-154">Cookie-based Session State</span></span>  
  
-   <span data-ttu-id="5d5b0-155">HttpContext.Current</span><span class="sxs-lookup"><span data-stu-id="5d5b0-155">HttpContext.Current</span></span>  
  
-   <span data-ttu-id="5d5b0-156">Kanál rozšiřitelnost prostřednictvím vlastních modulu HttpModule</span><span class="sxs-lookup"><span data-stu-id="5d5b0-156">Pipeline Extensibility via custom HttpModule</span></span>  
  
 <span data-ttu-id="5d5b0-157">Pokud vaše služby WCF potřebujete pracovat v rámci technologie ASP.NET a komunikovat jenom přes protokol HTTP, můžete použít režim kompatibility ASP.NET na WCF.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-157">If your WCF services need to function in the ASP.NET context, and communicate only over HTTP, you can use WCF’s ASP.NET compatibility mode.</span></span> <span data-ttu-id="5d5b0-158">Když je zapnutý tento režim `aspNetCompatibilityEnabled` atribut je nastaven na `true` na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-158">This mode is turned on when the `aspNetCompatibilityEnabled` attribute is set to `true` at the application level.</span></span> <span data-ttu-id="5d5b0-159">Implementace služby musí deklarovat své možnost spouštět pomocí režimu kompatibility <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-159">Service implementations must declare their ability to run in compatibility mode using the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> class.</span></span> <span data-ttu-id="5d5b0-160">Když je povolený režim kompatibility,</span><span class="sxs-lookup"><span data-stu-id="5d5b0-160">When the compatibility mode is enabled,</span></span>  
  
-   <span data-ttu-id="5d5b0-161">Autorizace souboru nebo adresy URL technologie ASP.NET je vynuceno před WCF autorizace.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-161">ASP.NET File/URL Authorization is enforced prior to WCF authorization.</span></span> <span data-ttu-id="5d5b0-162">Rozhodnutí o autorizaci vychází transportní vrstvy identitu požadavku.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-162">An authorization decision is based on the transport-level identity of the request.</span></span> <span data-ttu-id="5d5b0-163">Identit na úrovni zprávy jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-163">Identities at the message level are ignored.</span></span>  
  
-   <span data-ttu-id="5d5b0-164">Operací služby WCF start ke spuštění v kontextu zosobnění technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-164">WCF service operations start to execute in the ASP.NET impersonation context.</span></span> <span data-ttu-id="5d5b0-165">Pokud je pro konkrétní službu povolené zosobnění technologie ASP.NET a WCF zosobnění, platí kontextu zosobnění WCF.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-165">If both ASP.NET impersonation and WCF impersonation are enabled for a specific service, the WCF impersonation context applies.</span></span>  
  
-   <span data-ttu-id="5d5b0-166">HttpContext.Current je možné z kódu služby WCF a služeb bránit zveřejnění jiným protokolem než HTTP koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-166">HttpContext.Current can be used from WCF service code, and services are prevented from exposing non-HTTP endpoints.</span></span>  
  
-   <span data-ttu-id="5d5b0-167">WCF jsou zpracovány pomocí kanálu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-167">WCF requests are processed by the ASP.NET pipeline.</span></span> <span data-ttu-id="5d5b0-168">HttpModules, které jsou nakonfigurované tak, aby fungoval na příchozí požadavky může také zpracovat WCF žádosti.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-168">HttpModules that have been configured to act on incoming requests can also process WCF requests.</span></span> <span data-ttu-id="5d5b0-169">Může jít o komponenty platformy technologie ASP.NET (například <xref:System.Web.SessionState.SessionStateModule>), a také vlastní třetích stran moduly.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-169">These can include ASP.NET platform components (e.g., <xref:System.Web.SessionState.SessionStateModule>), as well as custom third party modules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d5b0-170">Příklad</span><span class="sxs-lookup"><span data-stu-id="5d5b0-170">Example</span></span>  
 <span data-ttu-id="5d5b0-171">Následující příklad kódu ukazuje, jak povolit režim kompatibility ASP.</span><span class="sxs-lookup"><span data-stu-id="5d5b0-171">The following code sample shows how to enable ASP Compatibility Mode.</span></span>  
  
## <a name="code"></a><span data-ttu-id="5d5b0-172">Kód</span><span class="sxs-lookup"><span data-stu-id="5d5b0-172">Code</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
```  
  
## <a name="see-also"></a><span data-ttu-id="5d5b0-173">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d5b0-173">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="5d5b0-174">Hostování</span><span class="sxs-lookup"><span data-stu-id="5d5b0-174">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
- [<span data-ttu-id="5d5b0-175">Služby WCF a ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5d5b0-175">WCF Services and ASP.NET</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
