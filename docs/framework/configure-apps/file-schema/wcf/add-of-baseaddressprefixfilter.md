---
title: '&lt;add&gt; – &lt;baseAddressPrefixFilter&gt;'
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: 549574d0d6585a857f3e0979e814c827139c7536
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltbaseaddressprefixfiltergt"></a><span data-ttu-id="ab35f-102">&lt;add&gt; – &lt;baseAddressPrefixFilter&gt;</span><span class="sxs-lookup"><span data-stu-id="ab35f-102">&lt;add&gt; of &lt;baseAddressPrefixFilter&gt;</span></span>
<span data-ttu-id="ab35f-103">Představuje konfiguraci element, který určuje průchozí filtr, který poskytuje mechanismus pro hostování aplikací Windows Communication Foundation (WCF) ve službě IIS, vyberte odpovídající vazby Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="ab35f-103">Represents a configuration element that specifies a pass-through filter, which provides a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
 <span data-ttu-id="ab35f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ab35f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ab35f-105">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="ab35f-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="ab35f-106">\<baseAddressPrefixFilters ></span><span class="sxs-lookup"><span data-stu-id="ab35f-106">\<baseAddressPrefixFilters></span></span>  
<span data-ttu-id="ab35f-107">\<add></span><span class="sxs-lookup"><span data-stu-id="ab35f-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab35f-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab35f-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="string"/>  
     </baseAddressPrefixFilters>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab35f-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ab35f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ab35f-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ab35f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab35f-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="ab35f-111">Attributes</span></span>  
  
|<span data-ttu-id="ab35f-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="ab35f-112">Attribute</span></span>|<span data-ttu-id="ab35f-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ab35f-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ab35f-114">Předpona</span><span class="sxs-lookup"><span data-stu-id="ab35f-114">prefix</span></span>|<span data-ttu-id="ab35f-115">Identifikátor URI, který se používá k porovnání součástí základní adresu.</span><span class="sxs-lookup"><span data-stu-id="ab35f-115">A URI that is used to match a part of a base address.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ab35f-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ab35f-116">Child Elements</span></span>  
 <span data-ttu-id="ab35f-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="ab35f-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ab35f-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ab35f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ab35f-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="ab35f-119">Element</span></span>|<span data-ttu-id="ab35f-120">Popis</span><span class="sxs-lookup"><span data-stu-id="ab35f-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab35f-121">\<baseAddressPrefixFilters ></span><span class="sxs-lookup"><span data-stu-id="ab35f-121">\<baseAddressPrefixFilters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|<span data-ttu-id="ab35f-122">Kolekci elementů konfigurace, které určují průchozí filtrů, které poskytují mechanismus při hostování aplikace Windows Communication Foundation (WCF) ve službě IIS, vyberte odpovídající vazby služby IIS.</span><span class="sxs-lookup"><span data-stu-id="ab35f-122">A collection of configuration elements that specify pass-through filters, which provide a mechanism to pick the appropriate IIS bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab35f-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ab35f-123">Remarks</span></span>  
 <span data-ttu-id="ab35f-124">Předpona filtr poskytuje způsob, jak sdílené poskytovatelům hostingu zadejte identifikátory, které mají být použita služba.</span><span class="sxs-lookup"><span data-stu-id="ab35f-124">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="ab35f-125">Umožňuje sdílené hostitele k hostování více aplikací s jiné základní adresy pro stejné schéma ve stejné lokalitě.</span><span class="sxs-lookup"><span data-stu-id="ab35f-125">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="ab35f-126">Webové servery služby IIS jsou kontejnery pro virtuální aplikace, které obsahují virtuální adresáře.</span><span class="sxs-lookup"><span data-stu-id="ab35f-126">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="ab35f-127">Aplikace v síti je přístupná přes jeden nebo více vazby služby IIS.</span><span class="sxs-lookup"><span data-stu-id="ab35f-127">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="ab35f-128">Vazby služby IIS poskytují dva kusy informací: protokol vazby a informace o vazbě.</span><span class="sxs-lookup"><span data-stu-id="ab35f-128">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="ab35f-129">Vazba protokol (například HTTP) definuje schéma, přes který probíhá komunikace a vazby informace (například IP adresu, Port, hostitel) obsahuje data používá pro přístup k webu.</span><span class="sxs-lookup"><span data-stu-id="ab35f-129">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="ab35f-130">Služba IIS podporuje zadání více vazby služby IIS pro každou lokalitu, což vede k více základní adresy pro každé schéma.</span><span class="sxs-lookup"><span data-stu-id="ab35f-130">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="ab35f-131">Protože [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služba hostovaná na webu umožňuje vazby pouze jeden základní adresu pro každé schéma, můžete použít funkci filtru předponu a vyberte požadované základní adresu hostované služby.</span><span class="sxs-lookup"><span data-stu-id="ab35f-131">Because a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="ab35f-132">Příchozí základní adresy poskytované službou IIS, jsou filtrovány na základě seznamu filtru volitelné předponu.</span><span class="sxs-lookup"><span data-stu-id="ab35f-132">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="ab35f-133">Například váš web může obsahovat následující základní adresy.</span><span class="sxs-lookup"><span data-stu-id="ab35f-133">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="ab35f-134">Následující konfigurační soubor můžete použít k zadání předpony filtru na úrovni domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="ab35f-134">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="ab35f-135">V tomto příkladu `net.tcp://test1.fabrikam.com:8000` a `http://test2.fabrikam.com:9000` jsou pouze základní adresy pro jejich příslušných systémů, které mohou být předána.</span><span class="sxs-lookup"><span data-stu-id="ab35f-135">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="ab35f-136">Ve výchozím nastavení Pokud není zadána předponu, všechny adresy se předaly.</span><span class="sxs-lookup"><span data-stu-id="ab35f-136">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="ab35f-137">Umožňuje zadat předponu pouze odpovídající základní adresu pro tento schéma, které se budou předávat.</span><span class="sxs-lookup"><span data-stu-id="ab35f-137">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab35f-138">Filtr nepodporuje žádné zástupné znaky.</span><span class="sxs-lookup"><span data-stu-id="ab35f-138">The filter does not support any wildcards.</span></span> <span data-ttu-id="ab35f-139">Kromě toho baseAddresses poskytované službou IIS pravděpodobně adresy vázaný na jiná schémata nejsou k dispozici v `baseAddressPrefixFilters` seznamu.</span><span class="sxs-lookup"><span data-stu-id="ab35f-139">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="ab35f-140">Tyto adresy nejsou odfiltrována.</span><span class="sxs-lookup"><span data-stu-id="ab35f-140">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab35f-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab35f-141">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="ab35f-142">Hostování</span><span class="sxs-lookup"><span data-stu-id="ab35f-142">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
