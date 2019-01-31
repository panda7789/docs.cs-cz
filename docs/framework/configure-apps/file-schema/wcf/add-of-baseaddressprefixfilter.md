---
title: <add> z <baseAddressPrefixFilter>
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: 9179abfb26229a845d9618afe30b088252c9c2db
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267652"
---
# <a name="add-of-baseaddressprefixfilter"></a><span data-ttu-id="605bf-102">\<add> of \<baseAddressPrefixFilter></span><span class="sxs-lookup"><span data-stu-id="605bf-102">\<add> of \<baseAddressPrefixFilter></span></span>
<span data-ttu-id="605bf-103">Představuje prvek konfigurace, který určuje průchozí filtr, který poskytuje mechanismus pro výběr příslušné vazby Internetové informační služby (IIS) při hostování aplikace Windows Communication Foundation (WCF) ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="605bf-103">Represents a configuration element that specifies a pass-through filter, which provides a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
 <span data-ttu-id="605bf-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="605bf-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="605bf-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="605bf-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="605bf-106">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="605bf-106">\<baseAddressPrefixFilters></span></span>  
<span data-ttu-id="605bf-107">\<add></span><span class="sxs-lookup"><span data-stu-id="605bf-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="605bf-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="605bf-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
  </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="605bf-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="605bf-109">Attributes and Elements</span></span>  
 <span data-ttu-id="605bf-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="605bf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="605bf-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="605bf-111">Attributes</span></span>  
  
|<span data-ttu-id="605bf-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="605bf-112">Attribute</span></span>|<span data-ttu-id="605bf-113">Popis</span><span class="sxs-lookup"><span data-stu-id="605bf-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="605bf-114">Předpona</span><span class="sxs-lookup"><span data-stu-id="605bf-114">prefix</span></span>|<span data-ttu-id="605bf-115">Identifikátor URI, který se používá tak, aby odpovídaly součást základní adresa.</span><span class="sxs-lookup"><span data-stu-id="605bf-115">A URI that is used to match a part of a base address.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="605bf-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="605bf-116">Child Elements</span></span>  
 <span data-ttu-id="605bf-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="605bf-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="605bf-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="605bf-118">Parent Elements</span></span>  
  
|<span data-ttu-id="605bf-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="605bf-119">Element</span></span>|<span data-ttu-id="605bf-120">Popis</span><span class="sxs-lookup"><span data-stu-id="605bf-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="605bf-121">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="605bf-121">\<baseAddressPrefixFilters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|<span data-ttu-id="605bf-122">Kolekci konfiguračních elementů určujících průchozí filtry, které poskytují mechanismus pro výběr příslušné vazby Internetové informační služby, při hostování aplikace Windows Communication Foundation (WCF) ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="605bf-122">A collection of configuration elements that specify pass-through filters, which provide a mechanism to pick the appropriate IIS bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="605bf-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="605bf-123">Remarks</span></span>  
 <span data-ttu-id="605bf-124">Filtr předponu poskytuje způsob pro sdílené poskytovatele hostingu k určení, které identifikátory URI se používá služba.</span><span class="sxs-lookup"><span data-stu-id="605bf-124">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="605bf-125">Umožňuje sdílené hostitele k hostování více aplikací s jinou bázové adresy pro stejné schéma na stejném místě.</span><span class="sxs-lookup"><span data-stu-id="605bf-125">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="605bf-126">Webové servery služby IIS jsou kontejnery pro virtuální aplikace, které obsahují virtuální adresáře.</span><span class="sxs-lookup"><span data-stu-id="605bf-126">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="605bf-127">Aplikace v síti přístupné prostřednictvím jednoho nebo více vazeb služby IIS.</span><span class="sxs-lookup"><span data-stu-id="605bf-127">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="605bf-128">Vazby služby IIS poskytuje dva druhy údajů: protokol vazby a informace o vazbě.</span><span class="sxs-lookup"><span data-stu-id="605bf-128">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="605bf-129">Vazba protokolu (třeba HTTP) definuje schéma, přes které probíhá komunikace a vazby informace (například IP adresy, portu, hostitel) obsahuje data sloužící k přístupu na web.</span><span class="sxs-lookup"><span data-stu-id="605bf-129">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="605bf-130">Služba IIS podporuje zadávání více vazeb služby IIS pro každou lokalitu, což vede k více bázové adresy pro každé schéma.</span><span class="sxs-lookup"><span data-stu-id="605bf-130">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="605bf-131">Protože služby WCF hostované na webu umožňuje vytváření vazby na pouze jednu základní adresu pro každé schéma, můžete použít předponu funkce filtru pro výběr vyžaduje základní adresa hostované služby.</span><span class="sxs-lookup"><span data-stu-id="605bf-131">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="605bf-132">Příchozí základní adresy poskytované službou IIS, jsou filtrované na základě seznamu filtru volitelné předpony.</span><span class="sxs-lookup"><span data-stu-id="605bf-132">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="605bf-133">Váš web může obsahovat například následující základní adresy.</span><span class="sxs-lookup"><span data-stu-id="605bf-133">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="605bf-134">Následující konfigurační soubor můžete použít k zadání předpony filtr na úrovni appdomain.</span><span class="sxs-lookup"><span data-stu-id="605bf-134">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
```xml  
<system.serviceModel>
  <serviceHostingEnvironment>
    <baseAddressPrefixFilters>
      <add prefix="net.tcp://test1.fabrikam.com:8000" />
      <add prefix="http://test2.fabrikam.com:9000" />
    </baseAddressPrefixFilters>
  </serviceHostingEnvironment>
</system.serviceModel>
```  
  
 <span data-ttu-id="605bf-135">V tomto příkladu `net.tcp://test1.fabrikam.com:8000` a `http://test2.fabrikam.com:9000` jsou pouze bázové adresy pro jejich odpovídajících schémata, které jsou povolené, které se budou předávat.</span><span class="sxs-lookup"><span data-stu-id="605bf-135">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="605bf-136">Ve výchozím nastavení Pokud není zadána předponu, všechny adresy se předaly.</span><span class="sxs-lookup"><span data-stu-id="605bf-136">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="605bf-137">Určení předpona, která umožňuje pouze odpovídající základní adresa pro toto schéma, které se budou předávat.</span><span class="sxs-lookup"><span data-stu-id="605bf-137">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="605bf-138">Tento filtr nepodporuje žádné zástupné znaky.</span><span class="sxs-lookup"><span data-stu-id="605bf-138">The filter does not support any wildcards.</span></span> <span data-ttu-id="605bf-139">Kromě toho baseAddresses poskytované službou IIS pravděpodobně adresy, které jsou vázány na jiná schémata není k dispozici v `baseAddressPrefixFilters` seznamu.</span><span class="sxs-lookup"><span data-stu-id="605bf-139">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="605bf-140">Tyto adresy nejsou odfiltrovány.</span><span class="sxs-lookup"><span data-stu-id="605bf-140">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="605bf-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="605bf-141">See also</span></span>
- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="605bf-142">Hostování</span><span class="sxs-lookup"><span data-stu-id="605bf-142">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
