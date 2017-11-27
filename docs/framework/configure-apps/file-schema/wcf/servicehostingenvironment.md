---
title: '&lt;serviceHostingEnvironment&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5770cb8fd68eb68145f3f7fbcf197302883efe9f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltservicehostingenvironmentgt"></a><span data-ttu-id="1ffe1-102">&lt;serviceHostingEnvironment&gt;</span><span class="sxs-lookup"><span data-stu-id="1ffe1-102">&lt;serviceHostingEnvironment&gt;</span></span>
<span data-ttu-id="1ffe1-103">Tento element definuje typ, který vytvoří instanci služby hostování prostředí konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-103">This element defines the type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="1ffe1-104">Pokud tento element je prázdné, použije se výchozí typ.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-104">If this element is empty, the default type is used.</span></span> <span data-ttu-id="1ffe1-105">Tento element dá použít jenom na aplikace či soubory konfiguraci na úrovni počítačů.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-105">This element can only be used at the application or machine level configuration files.</span></span>  
  
 <span data-ttu-id="1ffe1-106">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1ffe1-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="1ffe1-107">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="1ffe1-107">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ffe1-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ffe1-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="Boolean" 
                           minFreeMemoryPercentageToActivateService="Integer" 
                           multipleSiteBindingsEnabled="Boolean">
  <baseAddressPrefixFilters>
    <add prefix="string" />
  </baseAddressPrefixFilters>
  <serviceActivations>
    <add factory="String" service="String" />
  </serviceActivations>
  <transportConfigurationTypes>
    <add name="String" transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ffe1-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1ffe1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1ffe1-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ffe1-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="1ffe1-111">Attributes</span></span>  
  
|<span data-ttu-id="1ffe1-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="1ffe1-112">Attribute</span></span>|<span data-ttu-id="1ffe1-113">Popis</span><span class="sxs-lookup"><span data-stu-id="1ffe1-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1ffe1-114">aspNetCompatibilityEnabled</span><span class="sxs-lookup"><span data-stu-id="1ffe1-114">aspNetCompatibilityEnabled</span></span>|<span data-ttu-id="1ffe1-115">Logickou hodnotu udávající, zda je režim kompatibility ASP.NET je zapnutý pro aktuální aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-115">A Boolean value indicating whether the ASP.NET compatibility mode has been turned on for the current application.</span></span> <span data-ttu-id="1ffe1-116">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-116">The default is `false`.</span></span><br /><br /> <span data-ttu-id="1ffe1-117">Když tento atribut je nastaven na `true`, požadavky na [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] služby procházet skrz kanál protokolu HTTP technologie ASP.NET a komunikaci v rámci jiných protokolů než HTTP je zakázáno.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-117">When this attribute is set to `true`, requests to [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services flow through the ASP.NET HTTP pipeline, and communication over non-HTTP protocols is prohibited.</span></span> <span data-ttu-id="1ffe1-118">Další informace najdete v tématu [služby WCF a ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="1ffe1-118">For more information, see [WCF Services and ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span></span>|  
|<span data-ttu-id="1ffe1-119">minFreeMemoryPercentageToActivateService</span><span class="sxs-lookup"><span data-stu-id="1ffe1-119">minFreeMemoryPercentageToActivateService</span></span>|<span data-ttu-id="1ffe1-120">Celé číslo, které určuje minimální množství volné paměti, která by měla být k dispozici systému, než [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby je možné aktivovat.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-120">An integer that specifies the minimum amount of free memory that should be available to the system, before a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service can be activated.</span></span> <span data-ttu-id="1ffe1-121">**Upozornění:** zadání tohoto atributu společně s částečnou důvěryhodností v souboru web.config [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] v důsledku toho služba <xref:System.Security.SecurityException> spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-121">**Caution:**  Specifying this attribute along with partial trust in the web.config file of a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service will result in a <xref:System.Security.SecurityException> when the service is run.</span></span>|  
|<span data-ttu-id="1ffe1-122">multipleSiteBindingsEnabled</span><span class="sxs-lookup"><span data-stu-id="1ffe1-122">multipleSiteBindingsEnabled</span></span>|<span data-ttu-id="1ffe1-123">Logická hodnota, která určuje, zda je povoleno více vazby služby IIS na webu.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-123">A Boolean value that specifies whether multiple IIS bindings per site is enabled.</span></span><br /><br /> <span data-ttu-id="1ffe1-124">IIS se skládá z webů, které jsou kontejnery pro virtuální aplikace obsahující virtuální adresáře.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-124">IIS consists of web sites, which are containers for virtual applications containing virtual directories.</span></span> <span data-ttu-id="1ffe1-125">Aplikace v síti je přístupná přes jeden nebo více vazby služby IIS.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-125">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="1ffe1-126">Vazbu služby IIS poskytuje dva kusy informací: protokol vazby a informace o vazbě.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-126">An IIS binding provides two pieces of information: a binding protocol and binding information.</span></span> <span data-ttu-id="1ffe1-127">Vytvoření vazby protokolu definuje schéma, přes který probíhá komunikace a informace o vazbě je informace, které slouží pro přístup k webu.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-127">Binding protocol defines the scheme over which communication occurs, and binding information is the information used to access the site.</span></span> <span data-ttu-id="1ffe1-128">Příklad vazby protokolu může být protokolu HTTP, kdežto informace o vazbě může obsahovat IP adresu, Port, Hlavička hostitele, atd.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-128">An example of a binding protocol can be HTTP, whereas binding information can contain an IP address, Port, host header, etc.</span></span><br /><br /> <span data-ttu-id="1ffe1-129">Služba IIS podporuje zadání více vazby služby IIS na webu, což vede k více základní adresy na schéma.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-129">IIS supports specifying multiple IIS bindings per site, which results in multiple base addresses per scheme.</span></span> <span data-ttu-id="1ffe1-130">Ale [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] služba hostovaná na webu umožňuje vazbu na jedinou baseAddress na schéma.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-130">However, a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service hosted under a site allows binding to only one baseAddress per scheme.</span></span><br /><br /> <span data-ttu-id="1ffe1-131">Chcete-li povolit více vazby služby IIS na webovém serveru [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] služby, nastavte tento atribut na `true`.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-131">To enable multiple IIS bindings per site for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service, set this attribute to `true`.</span></span> <span data-ttu-id="1ffe1-132">Všimněte si, že více vazba webu je podporována pouze pro protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-132">Notice that multiple site binding is supported only for the HTTP protocol.</span></span> <span data-ttu-id="1ffe1-133">Adresy koncových bodů v konfiguračním souboru musí být úplný identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-133">The address of endpoints in the configuration file needs to be a complete URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ffe1-134">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1ffe1-134">Child Elements</span></span>  
  
|<span data-ttu-id="1ffe1-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="1ffe1-135">Element</span></span>|<span data-ttu-id="1ffe1-136">Popis</span><span class="sxs-lookup"><span data-stu-id="1ffe1-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ffe1-137">\<baseAddressPrefixFilters ></span><span class="sxs-lookup"><span data-stu-id="1ffe1-137">\<baseAddressPrefixFilters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|<span data-ttu-id="1ffe1-138">Kolekci elementů konfigurace, které zadejte předponu filtry pro základní adresy používané hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-138">A collection of configuration elements that specify prefix filters for the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="1ffe1-139">\<serviceActivations ></span><span class="sxs-lookup"><span data-stu-id="1ffe1-139">\<serviceActivations></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceactivations.md)|<span data-ttu-id="1ffe1-140">Konfigurační oddíl, který popisuje nastavení aktivace.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-140">A configuration section that describes activation settings.</span></span>|  
|[<span data-ttu-id="1ffe1-141">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="1ffe1-141">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="1ffe1-142">Kolekce konfigurační prvky, které identifikují typ konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-142">A collection of configuration elements that identify the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1ffe1-143">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1ffe1-143">Parent Elements</span></span>  
  
|<span data-ttu-id="1ffe1-144">Prvek</span><span class="sxs-lookup"><span data-stu-id="1ffe1-144">Element</span></span>|<span data-ttu-id="1ffe1-145">Popis</span><span class="sxs-lookup"><span data-stu-id="1ffe1-145">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1ffe1-146">ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1ffe1-146">serviceModel</span></span>|<span data-ttu-id="1ffe1-147">Kořenový element všechny konfigurační prvky Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1ffe1-147">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ffe1-148">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1ffe1-148">Remarks</span></span>  
 <span data-ttu-id="1ffe1-149">Ve výchozím nastavení služeb WCF spuštění-souběžného s technologií ASP.NET v aplikační domény hostované (AppDomain).</span><span class="sxs-lookup"><span data-stu-id="1ffe1-149">By default, WCF services run side-by-side with ASP.NET in hosted Application Domains (AppDomain).</span></span> <span data-ttu-id="1ffe1-150">I když do stejné domény aplikace můžou existovat společně WCF a ASP.NET, WCF požadavky nejsou zpracovává HTTP kanálu ASP.NET ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-150">Even though WCF and ASP.NET can coexist in the same AppDomain, WCF requests are not processed by the ASP.NET HTTP Pipeline by default.</span></span> <span data-ttu-id="1ffe1-151">Několik prvky platformu aplikací ASP.NET v důsledku toho nejsou k dispozici pro služby WCF.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-151">As a result, several elements of the ASP.NET application platform are not available to WCF services.</span></span> <span data-ttu-id="1ffe1-152">Mezi ně patří</span><span class="sxs-lookup"><span data-stu-id="1ffe1-152">These include</span></span>  
  
-   <span data-ttu-id="1ffe1-153">Autorizace ASP.NET soubor nebo adresa URL</span><span class="sxs-lookup"><span data-stu-id="1ffe1-153">ASP.NET File/URL Authorization</span></span>  
  
-   <span data-ttu-id="1ffe1-154">Zosobnění technologie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="1ffe1-154">ASP.NET Impersonation</span></span>  
  
-   <span data-ttu-id="1ffe1-155">Stav relace na základě souborů cookie</span><span class="sxs-lookup"><span data-stu-id="1ffe1-155">Cookie-based Session State</span></span>  
  
-   <span data-ttu-id="1ffe1-156">HttpContext.Current</span><span class="sxs-lookup"><span data-stu-id="1ffe1-156">HttpContext.Current</span></span>  
  
-   <span data-ttu-id="1ffe1-157">Rozšiřitelnost kanálů prostřednictvím vlastního modulu HTTP</span><span class="sxs-lookup"><span data-stu-id="1ffe1-157">Pipeline Extensibility via custom HttpModule</span></span>  
  
 <span data-ttu-id="1ffe1-158">Pokud potřebujete služby WCF je funkce v rámci ASP.NET a komunikovat pouze prostřednictvím protokolu HTTP, můžete použít režim kompatibility ASP.NET na WCF.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-158">If your WCF services need to function in the ASP.NET context, and communicate only over HTTP, you can use WCF’s ASP.NET compatibility mode.</span></span> <span data-ttu-id="1ffe1-159">Tento režim zapnutý, když `aspNetCompatibilityEnabled` je nastavena na hodnotu `true` na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-159">This mode is turned on when the `aspNetCompatibilityEnabled` attribute is set to `true` at the application level.</span></span> <span data-ttu-id="1ffe1-160">Implementace služby, musí deklarovat schopnost spustit v režimu kompatibility pomocí <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-160">Service implementations must declare their ability to run in compatibility mode using the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> class.</span></span> <span data-ttu-id="1ffe1-161">Když je povolený režim kompatibility,</span><span class="sxs-lookup"><span data-stu-id="1ffe1-161">When the compatibility mode is enabled,</span></span>  
  
-   <span data-ttu-id="1ffe1-162">Autorizace ASP.NET soubor nebo adresa URL se vynucuje před WCF autorizace.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-162">ASP.NET File/URL Authorization is enforced prior to WCF authorization.</span></span> <span data-ttu-id="1ffe1-163">Rozhodnutí o autorizaci vychází transportní vrstvy identitu požadavku.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-163">An authorization decision is based on the transport-level identity of the request.</span></span> <span data-ttu-id="1ffe1-164">Identity na úrovni zpráv se ignorují.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-164">Identities at the message level are ignored.</span></span>  
  
-   <span data-ttu-id="1ffe1-165">Operací služby WCF začít spuštěn v kontextu zosobnění technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-165">WCF service operations start to execute in the ASP.NET impersonation context.</span></span> <span data-ttu-id="1ffe1-166">Pokud zosobnění technologie ASP.NET a WCF zosobnění jsou povolené pro konkrétní službu, platí kontextu zosobnění WCF.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-166">If both ASP.NET impersonation and WCF impersonation are enabled for a specific service, the WCF impersonation context applies.</span></span>  
  
-   <span data-ttu-id="1ffe1-167">HttpContext.Current lze z kódu služby WCF a služby se vám bránit vystavení koncové body jiným protokolem než HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-167">HttpContext.Current can be used from WCF service code, and services are prevented from exposing non-HTTP endpoints.</span></span>  
  
-   <span data-ttu-id="1ffe1-168">Zpracovává požadavky WCF kanálu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-168">WCF requests are processed by the ASP.NET pipeline.</span></span> <span data-ttu-id="1ffe1-169">HttpModules, které byly nakonfigurovány tak, aby fungoval na příchozí požadavky může také zpracovat WCF žádosti.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-169">HttpModules that have been configured to act on incoming requests can also process WCF requests.</span></span> <span data-ttu-id="1ffe1-170">Patří mezi komponenty platformy ASP.NET (například <xref:System.Web.SessionState.SessionStateModule>), a také moduly vlastní třetích stran.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-170">These can include ASP.NET platform components (e.g., <xref:System.Web.SessionState.SessionStateModule>), as well as custom third party modules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ffe1-171">Příklad</span><span class="sxs-lookup"><span data-stu-id="1ffe1-171">Example</span></span>  
 <span data-ttu-id="1ffe1-172">Následující příklad kódu ukazuje, jak povolit režim kompatibility ASP.</span><span class="sxs-lookup"><span data-stu-id="1ffe1-172">The following code sample shows how to enable ASP Compatibility Mode.</span></span>  
  
## <a name="code"></a><span data-ttu-id="1ffe1-173">Kód</span><span class="sxs-lookup"><span data-stu-id="1ffe1-173">Code</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ffe1-174">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ffe1-174">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="1ffe1-175">Hostování</span><span class="sxs-lookup"><span data-stu-id="1ffe1-175">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)  
 [<span data-ttu-id="1ffe1-176">Služby WCF a ASP.NET</span><span class="sxs-lookup"><span data-stu-id="1ffe1-176">WCF Services and ASP.NET</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
