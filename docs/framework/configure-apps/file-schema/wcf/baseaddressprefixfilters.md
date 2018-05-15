---
title: '&lt;baseAddressPrefixFilters&gt;'
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 8fffcd02b1c08172b184225f13a1852414cf429a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltbaseaddressprefixfiltersgt"></a><span data-ttu-id="68e88-102">&lt;baseAddressPrefixFilters&gt;</span><span class="sxs-lookup"><span data-stu-id="68e88-102">&lt;baseAddressPrefixFilters&gt;</span></span>
<span data-ttu-id="68e88-103">Představuje kolekci konfigurace, která elementy, které určují předávat filtrů, které poskytují mechanismus vyberte odpovídající vazby Internetové informační služby (IIS), při hostování aplikace Windows Communication Foundation (WCF) ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="68e88-103">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="68e88-104">\<baseAddressPrefixFilters > neobsahuje rozpoznat "localhost", místo toho použijte název plně kvalifikovaný počítače.</span><span class="sxs-lookup"><span data-stu-id="68e88-104">\<baseAddressPrefixFilters> does not recognize "localhost", use the fully qualified machine name instead.</span></span>  
  
 <span data-ttu-id="68e88-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="68e88-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="68e88-106">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="68e88-106">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68e88-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68e88-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="string"/>  
     </baseAddressPrefixFilters>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68e88-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="68e88-108">Attributes and Elements</span></span>  
 <span data-ttu-id="68e88-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="68e88-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68e88-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="68e88-110">Attributes</span></span>  
 <span data-ttu-id="68e88-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="68e88-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="68e88-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="68e88-112">Child Elements</span></span>  
  
|<span data-ttu-id="68e88-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="68e88-113">Element</span></span>|<span data-ttu-id="68e88-114">Popis</span><span class="sxs-lookup"><span data-stu-id="68e88-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68e88-115">\<add></span><span class="sxs-lookup"><span data-stu-id="68e88-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddressprefixfilter.md)|<span data-ttu-id="68e88-116">Přidá element konfigurace, který určuje předponu filtr pro základní adresy používané hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="68e88-116">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="68e88-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="68e88-117">Parent Elements</span></span>  
  
|<span data-ttu-id="68e88-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="68e88-118">Element</span></span>|<span data-ttu-id="68e88-119">Popis</span><span class="sxs-lookup"><span data-stu-id="68e88-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68e88-120">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="68e88-120">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="68e88-121">Definuje typ, který vytvoří instanci služby hostování prostředí konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="68e88-121">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68e88-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="68e88-122">Remarks</span></span>  
 <span data-ttu-id="68e88-123">Předpona filtr poskytuje způsob, jak sdílené poskytovatelům hostingu zadejte identifikátory, které mají být použita služba.</span><span class="sxs-lookup"><span data-stu-id="68e88-123">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="68e88-124">Umožňuje sdílené hostitele k hostování více aplikací s jiné základní adresy pro stejné schéma ve stejné lokalitě.</span><span class="sxs-lookup"><span data-stu-id="68e88-124">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="68e88-125">Webové servery služby IIS jsou kontejnery pro virtuální aplikace, které obsahují virtuální adresáře.</span><span class="sxs-lookup"><span data-stu-id="68e88-125">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="68e88-126">Aplikace v síti je přístupná přes jeden nebo více vazby služby IIS.</span><span class="sxs-lookup"><span data-stu-id="68e88-126">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="68e88-127">Vazby služby IIS poskytují dva kusy informací: protokol vazby a informace o vazbě.</span><span class="sxs-lookup"><span data-stu-id="68e88-127">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="68e88-128">Vazba protokol (například HTTP) definuje schéma, přes který probíhá komunikace a vazby informace (například IP adresu, Port, hostitel) obsahuje data používá pro přístup k webu.</span><span class="sxs-lookup"><span data-stu-id="68e88-128">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="68e88-129">Služba IIS podporuje zadání více vazby služby IIS pro každou lokalitu, což vede k více základní adresy pro každé schéma.</span><span class="sxs-lookup"><span data-stu-id="68e88-129">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="68e88-130">Protože [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služba hostovaná na webu umožňuje vazby pouze jeden základní adresu pro každé schéma, můžete použít funkci filtru předponu a vyberte požadované základní adresu hostované služby.</span><span class="sxs-lookup"><span data-stu-id="68e88-130">Because a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="68e88-131">Příchozí základní adresy poskytované službou IIS, jsou filtrovány na základě seznamu filtru volitelné předponu.</span><span class="sxs-lookup"><span data-stu-id="68e88-131">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="68e88-132">Například váš web může obsahovat následující základní adresy.</span><span class="sxs-lookup"><span data-stu-id="68e88-132">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="68e88-133">Následující konfigurační soubor můžete použít k zadání předpony filtru na úrovni domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="68e88-133">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="net.tcp://test1.fabrikam.com:8000"/>  
        <add prefix="http://test2.fabrikam.com:9000"/>  
    </baseAddressPrefixFilters>  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="68e88-134">V tomto příkladu `net.tcp://test1.fabrikam.com:8000` a `http://test2.fabrikam.com:9000` jsou pouze základní adresy pro příslušné schémat, které mohou být předána.</span><span class="sxs-lookup"><span data-stu-id="68e88-134">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="68e88-135">Ve výchozím nastavení Pokud není zadána předponu, všechny adresy se předaly.</span><span class="sxs-lookup"><span data-stu-id="68e88-135">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="68e88-136">Umožňuje zadat předponu pouze odpovídající základní adresu pro tento schéma, které se budou předávat.</span><span class="sxs-lookup"><span data-stu-id="68e88-136">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68e88-137">Filtr nepodporuje žádné zástupné znaky.</span><span class="sxs-lookup"><span data-stu-id="68e88-137">The filter does not support any wildcards.</span></span> <span data-ttu-id="68e88-138">Kromě toho baseAddresses poskytované službou IIS pravděpodobně adresy vázaný na jiná schémata nejsou k dispozici v `baseAddressPrefixFilters` seznamu.</span><span class="sxs-lookup"><span data-stu-id="68e88-138">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="68e88-139">Tyto adresy nejsou odfiltrována.</span><span class="sxs-lookup"><span data-stu-id="68e88-139">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68e88-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="68e88-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="68e88-141">Hostování</span><span class="sxs-lookup"><span data-stu-id="68e88-141">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
