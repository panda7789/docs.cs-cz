---
title: <add> z <baseAddressPrefixFilter>
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: e29db0b2412c9ccbfe83d000077e8d85332955ea
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926868"
---
# <a name="add-of-baseaddressprefixfilter"></a><span data-ttu-id="48038-102">\<add> of \<baseAddressPrefixFilter></span><span class="sxs-lookup"><span data-stu-id="48038-102">\<add> of \<baseAddressPrefixFilter></span></span>
<span data-ttu-id="48038-103">Představuje prvek konfigurace, který určuje předávací filtr, který poskytuje mechanismus pro výběr příslušných vazeb Internetová informační služba (IIS) při hostování aplikace Windows Communication Foundation (WCF) ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="48038-103">Represents a configuration element that specifies a pass-through filter, which provides a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
 <span data-ttu-id="48038-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="48038-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="48038-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="48038-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="48038-106">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="48038-106">\<baseAddressPrefixFilters></span></span>  
<span data-ttu-id="48038-107">\<add></span><span class="sxs-lookup"><span data-stu-id="48038-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48038-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48038-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
  </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48038-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="48038-109">Attributes and Elements</span></span>  
 <span data-ttu-id="48038-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="48038-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48038-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="48038-111">Attributes</span></span>  
  
|<span data-ttu-id="48038-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="48038-112">Attribute</span></span>|<span data-ttu-id="48038-113">Popis</span><span class="sxs-lookup"><span data-stu-id="48038-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="48038-114">prefix</span><span class="sxs-lookup"><span data-stu-id="48038-114">prefix</span></span>|<span data-ttu-id="48038-115">Identifikátor URI, který se používá k vyhledání části základní adresy.</span><span class="sxs-lookup"><span data-stu-id="48038-115">A URI that is used to match a part of a base address.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48038-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="48038-116">Child Elements</span></span>  
 <span data-ttu-id="48038-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="48038-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="48038-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="48038-118">Parent Elements</span></span>  
  
|<span data-ttu-id="48038-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="48038-119">Element</span></span>|<span data-ttu-id="48038-120">Popis</span><span class="sxs-lookup"><span data-stu-id="48038-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48038-121">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="48038-121">\<baseAddressPrefixFilters></span></span>](baseaddressprefixfilters.md)|<span data-ttu-id="48038-122">Kolekce elementů konfigurace, které určují předávací filtry, které poskytují mechanismus pro výběr příslušných vazeb služby IIS při hostování aplikace Windows Communication Foundation (WCF) ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="48038-122">A collection of configuration elements that specify pass-through filters, which provide a mechanism to pick the appropriate IIS bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48038-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="48038-123">Remarks</span></span>  
 <span data-ttu-id="48038-124">Filtr předpon poskytuje způsob, jak sdíleným poskytovatelům hostingu určit, které identifikátory URI bude služba používat.</span><span class="sxs-lookup"><span data-stu-id="48038-124">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="48038-125">Umožňuje sdíleným hostitelům hostovat více aplikací s různými základními adresami pro stejné schéma ve stejné lokalitě.</span><span class="sxs-lookup"><span data-stu-id="48038-125">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="48038-126">Webové stránky služby IIS jsou kontejnery pro virtuální aplikace, které obsahují virtuální adresáře.</span><span class="sxs-lookup"><span data-stu-id="48038-126">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="48038-127">Aplikace v lokalitě je k dispozici prostřednictvím jedné nebo více vazeb služby IIS.</span><span class="sxs-lookup"><span data-stu-id="48038-127">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="48038-128">Vazby služby IIS poskytují dvě informace: vazby protokolu a informace o vazbě.</span><span class="sxs-lookup"><span data-stu-id="48038-128">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="48038-129">Protokol vazby (například HTTP) definuje schéma, přes které probíhá komunikace, a informace o vazbě (například IP adresa, port, hostheader) obsahuje data, která se používají pro přístup k webu.</span><span class="sxs-lookup"><span data-stu-id="48038-129">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="48038-130">Služba IIS podporuje zadání více vazeb služby IIS pro každou lokalitu, což má za následek více základních adres pro každé schéma.</span><span class="sxs-lookup"><span data-stu-id="48038-130">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="48038-131">Vzhledem k tomu, že služba WCF hostovaná v rámci lokality umožňuje vytvořit vazbu pouze na jednu základní adresu pro každé schéma, můžete pomocí funkce filtru předpon vybrat požadovanou základní adresu hostované služby.</span><span class="sxs-lookup"><span data-stu-id="48038-131">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="48038-132">Příchozí základní adresy, které poskytuje služba IIS, se filtrují na základě volitelného filtru seznamu předpon.</span><span class="sxs-lookup"><span data-stu-id="48038-132">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="48038-133">Například váš web může obsahovat následující základní adresy.</span><span class="sxs-lookup"><span data-stu-id="48038-133">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="48038-134">Následující konfigurační soubor můžete použít k určení filtru předpony na úrovni domény AppDomain.</span><span class="sxs-lookup"><span data-stu-id="48038-134">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="48038-135">V tomto příkladu `http://test2.fabrikam.com:9000` jsou `net.tcp://test1.fabrikam.com:8000` jedinými základními adresami pro jejich příslušné systémy, které mohou být předány.</span><span class="sxs-lookup"><span data-stu-id="48038-135">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="48038-136">Ve výchozím nastavení, pokud není zadána předpona, jsou předány všechny adresy.</span><span class="sxs-lookup"><span data-stu-id="48038-136">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="48038-137">Zadání předpony umožňuje předávat odpovídající základní adresu pro toto schéma.</span><span class="sxs-lookup"><span data-stu-id="48038-137">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="48038-138">Filtr nepodporuje žádné zástupné znaky.</span><span class="sxs-lookup"><span data-stu-id="48038-138">The filter does not support any wildcards.</span></span> <span data-ttu-id="48038-139">Kromě toho adres BaseAddresses poskytované službou IIS může mít adresy svázané s jinými schématy, která nejsou přítomna `baseAddressPrefixFilters` v seznamu.</span><span class="sxs-lookup"><span data-stu-id="48038-139">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="48038-140">Tyto adresy nejsou vyfiltrovány.</span><span class="sxs-lookup"><span data-stu-id="48038-140">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48038-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="48038-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="48038-142">Hostování</span><span class="sxs-lookup"><span data-stu-id="48038-142">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
