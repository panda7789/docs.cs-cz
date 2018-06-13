---
title: '&lt;add&gt; – &lt;baseAddressPrefixFilter&gt;'
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: e4408488036be210e3a8b9cf8b8f8f8c2e669a1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365186"
---
# <a name="ltaddgt-of-ltbaseaddressprefixfiltergt"></a><span data-ttu-id="f1553-102">&lt;add&gt; – &lt;baseAddressPrefixFilter&gt;</span><span class="sxs-lookup"><span data-stu-id="f1553-102">&lt;add&gt; of &lt;baseAddressPrefixFilter&gt;</span></span>
<span data-ttu-id="f1553-103">Představuje konfiguraci element, který určuje průchozí filtr, který poskytuje mechanismus pro hostování aplikací Windows Communication Foundation (WCF) ve službě IIS, vyberte odpovídající vazby Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="f1553-103">Represents a configuration element that specifies a pass-through filter, which provides a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
 <span data-ttu-id="f1553-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f1553-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f1553-105">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="f1553-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="f1553-106">\<baseAddressPrefixFilters ></span><span class="sxs-lookup"><span data-stu-id="f1553-106">\<baseAddressPrefixFilters></span></span>  
<span data-ttu-id="f1553-107">\<add></span><span class="sxs-lookup"><span data-stu-id="f1553-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1553-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1553-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="string"/>  
     </baseAddressPrefixFilters>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1553-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f1553-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f1553-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f1553-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1553-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="f1553-111">Attributes</span></span>  
  
|<span data-ttu-id="f1553-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="f1553-112">Attribute</span></span>|<span data-ttu-id="f1553-113">Popis</span><span class="sxs-lookup"><span data-stu-id="f1553-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f1553-114">Předpona</span><span class="sxs-lookup"><span data-stu-id="f1553-114">prefix</span></span>|<span data-ttu-id="f1553-115">Identifikátor URI, který se používá k porovnání součástí základní adresu.</span><span class="sxs-lookup"><span data-stu-id="f1553-115">A URI that is used to match a part of a base address.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1553-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f1553-116">Child Elements</span></span>  
 <span data-ttu-id="f1553-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="f1553-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f1553-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f1553-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f1553-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="f1553-119">Element</span></span>|<span data-ttu-id="f1553-120">Popis</span><span class="sxs-lookup"><span data-stu-id="f1553-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1553-121">\<baseAddressPrefixFilters ></span><span class="sxs-lookup"><span data-stu-id="f1553-121">\<baseAddressPrefixFilters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|<span data-ttu-id="f1553-122">Kolekci elementů konfigurace, které určují průchozí filtrů, které poskytují mechanismus při hostování aplikace Windows Communication Foundation (WCF) ve službě IIS, vyberte odpovídající vazby služby IIS.</span><span class="sxs-lookup"><span data-stu-id="f1553-122">A collection of configuration elements that specify pass-through filters, which provide a mechanism to pick the appropriate IIS bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1553-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f1553-123">Remarks</span></span>  
 <span data-ttu-id="f1553-124">Předpona filtr poskytuje způsob, jak sdílené poskytovatelům hostingu zadejte identifikátory, které mají být použita služba.</span><span class="sxs-lookup"><span data-stu-id="f1553-124">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="f1553-125">Umožňuje sdílené hostitele k hostování více aplikací s jiné základní adresy pro stejné schéma ve stejné lokalitě.</span><span class="sxs-lookup"><span data-stu-id="f1553-125">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="f1553-126">Webové servery služby IIS jsou kontejnery pro virtuální aplikace, které obsahují virtuální adresáře.</span><span class="sxs-lookup"><span data-stu-id="f1553-126">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="f1553-127">Aplikace v síti je přístupná přes jeden nebo více vazby služby IIS.</span><span class="sxs-lookup"><span data-stu-id="f1553-127">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="f1553-128">Vazby služby IIS poskytují dva kusy informací: protokol vazby a informace o vazbě.</span><span class="sxs-lookup"><span data-stu-id="f1553-128">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="f1553-129">Vazba protokol (například HTTP) definuje schéma, přes který probíhá komunikace a vazby informace (například IP adresu, Port, hostitel) obsahuje data používá pro přístup k webu.</span><span class="sxs-lookup"><span data-stu-id="f1553-129">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="f1553-130">Služba IIS podporuje zadání více vazby služby IIS pro každou lokalitu, což vede k více základní adresy pro každé schéma.</span><span class="sxs-lookup"><span data-stu-id="f1553-130">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="f1553-131">Protože služby WCF hostované na webu umožňuje vazby pouze jeden základní adresu pro každé schéma, můžete použít funkci filtru předponu a vyberte požadované základní adresu hostované služby.</span><span class="sxs-lookup"><span data-stu-id="f1553-131">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="f1553-132">Příchozí základní adresy poskytované službou IIS, jsou filtrovány na základě seznamu filtru volitelné předponu.</span><span class="sxs-lookup"><span data-stu-id="f1553-132">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="f1553-133">Například váš web může obsahovat následující základní adresy.</span><span class="sxs-lookup"><span data-stu-id="f1553-133">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="f1553-134">Následující konfigurační soubor můžete použít k zadání předpony filtru na úrovni domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1553-134">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="f1553-135">V tomto příkladu `net.tcp://test1.fabrikam.com:8000` a `http://test2.fabrikam.com:9000` jsou pouze základní adresy pro jejich příslušných systémů, které mohou být předána.</span><span class="sxs-lookup"><span data-stu-id="f1553-135">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="f1553-136">Ve výchozím nastavení Pokud není zadána předponu, všechny adresy se předaly.</span><span class="sxs-lookup"><span data-stu-id="f1553-136">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="f1553-137">Umožňuje zadat předponu pouze odpovídající základní adresu pro tento schéma, které se budou předávat.</span><span class="sxs-lookup"><span data-stu-id="f1553-137">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1553-138">Filtr nepodporuje žádné zástupné znaky.</span><span class="sxs-lookup"><span data-stu-id="f1553-138">The filter does not support any wildcards.</span></span> <span data-ttu-id="f1553-139">Kromě toho baseAddresses poskytované službou IIS pravděpodobně adresy vázaný na jiná schémata nejsou k dispozici v `baseAddressPrefixFilters` seznamu.</span><span class="sxs-lookup"><span data-stu-id="f1553-139">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="f1553-140">Tyto adresy nejsou odfiltrována.</span><span class="sxs-lookup"><span data-stu-id="f1553-140">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1553-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1553-141">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="f1553-142">Hostování</span><span class="sxs-lookup"><span data-stu-id="f1553-142">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
