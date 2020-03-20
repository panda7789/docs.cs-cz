---
title: <add> z <baseAddressPrefixFilter>
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: 8fdae02b558708a9b3f4535123752dce12dd5cf5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153137"
---
# <a name="add-of-baseaddressprefixfilter"></a><span data-ttu-id="82426-102">\<přidat> \<baseAddressPrefixFilter></span><span class="sxs-lookup"><span data-stu-id="82426-102">\<add> of \<baseAddressPrefixFilter></span></span>
<span data-ttu-id="82426-103">Představuje konfigurační prvek, který určuje předávací filtr, který poskytuje mechanismus pro výběr vhodných vazeb Internetové informační služby (IIS) při hostování aplikace WCF (Windows Communication Foundation) ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="82426-103">Represents a configuration element that specifies a pass-through filter, which provides a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
<span data-ttu-id="82426-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="82426-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="82426-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="82426-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="82426-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="82426-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="82426-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddressPrefixFilters>**](baseaddressprefixfilters.md)</span><span class="sxs-lookup"><span data-stu-id="82426-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddressPrefixFilters>**](baseaddressprefixfilters.md)</span></span>\
<span data-ttu-id="82426-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<přidat>**</span><span class="sxs-lookup"><span data-stu-id="82426-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82426-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82426-109">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
  </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82426-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="82426-110">Attributes and Elements</span></span>  
 <span data-ttu-id="82426-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="82426-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82426-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="82426-112">Attributes</span></span>  
  
|<span data-ttu-id="82426-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="82426-113">Attribute</span></span>|<span data-ttu-id="82426-114">Popis</span><span class="sxs-lookup"><span data-stu-id="82426-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="82426-115">Předponu</span><span class="sxs-lookup"><span data-stu-id="82426-115">prefix</span></span>|<span data-ttu-id="82426-116">Identifikátor URI, který se používá k porovnejte část základní adresy.</span><span class="sxs-lookup"><span data-stu-id="82426-116">A URI that is used to match a part of a base address.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="82426-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="82426-117">Child Elements</span></span>  
 <span data-ttu-id="82426-118">Žádné.</span><span class="sxs-lookup"><span data-stu-id="82426-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="82426-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="82426-119">Parent Elements</span></span>  
  
|<span data-ttu-id="82426-120">Element</span><span class="sxs-lookup"><span data-stu-id="82426-120">Element</span></span>|<span data-ttu-id="82426-121">Popis</span><span class="sxs-lookup"><span data-stu-id="82426-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82426-122">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="82426-122">\<baseAddressPrefixFilters></span></span>](baseaddressprefixfilters.md)|<span data-ttu-id="82426-123">Kolekce konfiguračních prvků, které určují předávací filtry, které poskytují mechanismus pro výběr vhodných vazeb služby IIS při hostování aplikace WCF (Windows Communication Foundation) ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="82426-123">A collection of configuration elements that specify pass-through filters, which provide a mechanism to pick the appropriate IIS bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82426-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="82426-124">Remarks</span></span>  
 <span data-ttu-id="82426-125">Filtr předpony poskytuje poskytovatelům sdíleného hostingu způsob, jak určit, které identifikátory URI mají být službou používány.</span><span class="sxs-lookup"><span data-stu-id="82426-125">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="82426-126">Umožňuje sdíleným hostitelům hostovat více aplikací s různými základními adresami pro stejné schéma na stejném webu.</span><span class="sxs-lookup"><span data-stu-id="82426-126">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="82426-127">Weby služby IIS jsou kontejnery pro virtuální aplikace, které obsahují virtuální adresáře.</span><span class="sxs-lookup"><span data-stu-id="82426-127">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="82426-128">Aplikace v lokalitě je přístupná prostřednictvím jedné nebo více vazeb služby IIS.</span><span class="sxs-lookup"><span data-stu-id="82426-128">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="82426-129">Vazby iis poskytují dvě informace: závazný protokol a informace o vazbě.</span><span class="sxs-lookup"><span data-stu-id="82426-129">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="82426-130">Protokol vazby (například HTTP) definuje schéma, přes které dochází ke komunikaci, a informace o vazbě (například IP adresa, port, hlavička hostitele) obsahují data použitá pro přístup k webu.</span><span class="sxs-lookup"><span data-stu-id="82426-130">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="82426-131">IIS podporuje určení více vazeb iis pro každou lokalitu, což má za následek více základních adres pro každé schéma.</span><span class="sxs-lookup"><span data-stu-id="82426-131">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="82426-132">Vzhledem k tomu, že služba WCF hostovaná pod webem umožňuje vazbu pouze na jednu základní adresu pro každé schéma, můžete pomocí funkce filtru předpony vybrat požadovanou základní adresu hostované služby.</span><span class="sxs-lookup"><span data-stu-id="82426-132">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="82426-133">Příchozí základní adresy dodané službou IIS jsou filtrovány na základě volitelného filtru seznamu předponami.</span><span class="sxs-lookup"><span data-stu-id="82426-133">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="82426-134">Web může například obsahovat následující základní adresy:</span><span class="sxs-lookup"><span data-stu-id="82426-134">For example, your site can contain the following base addresses:</span></span>
  
```
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="82426-135">Následující konfigurační soubor můžete použít k určení filtru předpony na úrovni domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="82426-135">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="82426-136">V tomto `net.tcp://test1.fabrikam.com:8000` příkladu a `http://test2.fabrikam.com:9000` jsou pouze základní adresy pro jejich příslušné systémy, které mohou být předány.</span><span class="sxs-lookup"><span data-stu-id="82426-136">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="82426-137">Ve výchozím nastavení není zadána předpona, jsou předány všechny adresy.</span><span class="sxs-lookup"><span data-stu-id="82426-137">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="82426-138">Zadání předpony umožňuje pouze odpovídající základní adresu pro toto schéma, které mají být předány.</span><span class="sxs-lookup"><span data-stu-id="82426-138">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82426-139">Filtr nepodporuje žádné zástupné znaky.</span><span class="sxs-lookup"><span data-stu-id="82426-139">The filter does not support any wildcards.</span></span> <span data-ttu-id="82426-140">Kromě toho baseAddresses poskytované iIS může mít adresy vázané na jiná `baseAddressPrefixFilters` schémata, které nejsou k dispozici v seznamu.</span><span class="sxs-lookup"><span data-stu-id="82426-140">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="82426-141">Tyto adresy nejsou odfiltrovány.</span><span class="sxs-lookup"><span data-stu-id="82426-141">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82426-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="82426-142">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="82426-143">Hostování</span><span class="sxs-lookup"><span data-stu-id="82426-143">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
