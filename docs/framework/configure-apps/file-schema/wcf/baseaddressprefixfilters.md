---
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 55ffcfb5c0c84d68033d082cbe451696bd3c9dc2
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988350"
---
# <a name="baseaddressprefixfilters"></a><span data-ttu-id="b9a1e-101">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="b9a1e-101">\<baseAddressPrefixFilters></span></span>
<span data-ttu-id="b9a1e-102">Představuje kolekci elementů konfigurace, které určují předávací filtry, které poskytují mechanismus pro výběr příslušných vazeb Internetová informační služba (IIS) při hostování aplikace Windows Communication Foundation (WCF) ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="b9a1e-102">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="b9a1e-103">\<baseAddressPrefixFilters > nerozpozná "localhost", místo toho použijte plně kvalifikovaný název počítače.</span><span class="sxs-lookup"><span data-stu-id="b9a1e-103">\<baseAddressPrefixFilters> does not recognize "localhost", use the fully qualified machine name instead.</span></span>  
  
 <span data-ttu-id="b9a1e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b9a1e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b9a1e-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="b9a1e-105">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9a1e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9a1e-106">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9a1e-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b9a1e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b9a1e-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b9a1e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9a1e-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="b9a1e-109">Attributes</span></span>  
 <span data-ttu-id="b9a1e-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="b9a1e-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b9a1e-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b9a1e-111">Child Elements</span></span>  
  
|<span data-ttu-id="b9a1e-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="b9a1e-112">Element</span></span>|<span data-ttu-id="b9a1e-113">Popis</span><span class="sxs-lookup"><span data-stu-id="b9a1e-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9a1e-114">\<add></span><span class="sxs-lookup"><span data-stu-id="b9a1e-114">\<add></span></span>](add-of-baseaddressprefixfilter.md)|<span data-ttu-id="b9a1e-115">Přidá prvek konfigurace, který určuje filtr předpony pro základní adresy používané hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="b9a1e-115">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b9a1e-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b9a1e-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b9a1e-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="b9a1e-117">Element</span></span>|<span data-ttu-id="b9a1e-118">Popis</span><span class="sxs-lookup"><span data-stu-id="b9a1e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9a1e-119">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="b9a1e-119">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="b9a1e-120">Definuje typ, který hostující prostředí služby vytvoří pro konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="b9a1e-120">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9a1e-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b9a1e-121">Remarks</span></span>  
 <span data-ttu-id="b9a1e-122">Filtr předpon poskytuje způsob, jak sdíleným poskytovatelům hostingu určit, které identifikátory URI bude služba používat.</span><span class="sxs-lookup"><span data-stu-id="b9a1e-122">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="b9a1e-123">Umožňuje sdíleným hostitelům hostovat více aplikací s různými základními adresami pro stejné schéma ve stejné lokalitě.</span><span class="sxs-lookup"><span data-stu-id="b9a1e-123">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="b9a1e-124">Webové stránky služby IIS jsou kontejnery pro virtuální aplikace, které obsahují virtuální adresáře.</span><span class="sxs-lookup"><span data-stu-id="b9a1e-124">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="b9a1e-125">Aplikace v lokalitě je k dispozici prostřednictvím jedné nebo více vazeb služby IIS.</span><span class="sxs-lookup"><span data-stu-id="b9a1e-125">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="b9a1e-126">Vazby služby IIS poskytují dvě informace: vazby protokolu a informace o vazbě.</span><span class="sxs-lookup"><span data-stu-id="b9a1e-126">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="b9a1e-127">Protokol vazby (například HTTP) definuje schéma, přes které probíhá komunikace, a informace o vazbě (například IP adresa, port, hostheader) obsahuje data, která se používají pro přístup k webu.</span><span class="sxs-lookup"><span data-stu-id="b9a1e-127">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="b9a1e-128">Služba IIS podporuje zadání více vazeb služby IIS pro každou lokalitu, což má za následek více základních adres pro každé schéma.</span><span class="sxs-lookup"><span data-stu-id="b9a1e-128">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="b9a1e-129">Vzhledem k tomu, že služba WCF hostovaná v rámci lokality umožňuje vytvořit vazbu pouze na jednu základní adresu pro každé schéma, můžete pomocí funkce filtru předpon vybrat požadovanou základní adresu hostované služby.</span><span class="sxs-lookup"><span data-stu-id="b9a1e-129">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="b9a1e-130">Příchozí základní adresy, které poskytuje služba IIS, se filtrují na základě volitelného filtru seznamu předpon.</span><span class="sxs-lookup"><span data-stu-id="b9a1e-130">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="b9a1e-131">Například váš web může obsahovat následující základní adresy.</span><span class="sxs-lookup"><span data-stu-id="b9a1e-131">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="b9a1e-132">Následující konfigurační soubor můžete použít k určení filtru předpony na úrovni domény AppDomain.</span><span class="sxs-lookup"><span data-stu-id="b9a1e-132">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="b9a1e-133">V tomto příkladu `net.tcp://test1.fabrikam.com:8000` `http://test2.fabrikam.com:9000` jsou jedinými základními adresami pro příslušné režimy, které mohou být předány.</span><span class="sxs-lookup"><span data-stu-id="b9a1e-133">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="b9a1e-134">Ve výchozím nastavení, pokud není zadána předpona, jsou předány všechny adresy.</span><span class="sxs-lookup"><span data-stu-id="b9a1e-134">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="b9a1e-135">Zadání předpony umožňuje předávat odpovídající základní adresu pro toto schéma.</span><span class="sxs-lookup"><span data-stu-id="b9a1e-135">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9a1e-136">Filtr nepodporuje žádné zástupné znaky.</span><span class="sxs-lookup"><span data-stu-id="b9a1e-136">The filter does not support any wildcards.</span></span> <span data-ttu-id="b9a1e-137">Kromě toho adres BaseAddresses poskytované službou IIS může mít adresy svázané s jinými schématy, která nejsou přítomna `baseAddressPrefixFilters` v seznamu.</span><span class="sxs-lookup"><span data-stu-id="b9a1e-137">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="b9a1e-138">Tyto adresy nejsou vyfiltrovány.</span><span class="sxs-lookup"><span data-stu-id="b9a1e-138">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9a1e-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9a1e-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="b9a1e-140">Hostování</span><span class="sxs-lookup"><span data-stu-id="b9a1e-140">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
