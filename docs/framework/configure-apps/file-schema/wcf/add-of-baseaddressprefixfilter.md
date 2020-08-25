---
title: <add> z <baseAddressPrefixFilter>
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: 2572a6ee6763ae26fe5c56669e10f8c9aef8a280
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811792"
---
# <a name="add-of-baseaddressprefixfilter"></a><span data-ttu-id="c82b6-102">\<add> z \<baseAddressPrefixFilter></span><span class="sxs-lookup"><span data-stu-id="c82b6-102">\<add> of \<baseAddressPrefixFilter></span></span>
<span data-ttu-id="c82b6-103">Představuje prvek konfigurace, který určuje předávací filtr, který poskytuje mechanismus pro výběr příslušných vazeb Internetová informační služba (IIS) při hostování aplikace Windows Communication Foundation (WCF) ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="c82b6-103">Represents a configuration element that specifies a pass-through filter, which provides a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddressPrefixFilters>**](baseaddressprefixfilters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="c82b6-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="c82b6-104">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
  </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c82b6-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c82b6-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c82b6-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c82b6-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c82b6-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="c82b6-107">Attributes</span></span>  
  
|<span data-ttu-id="c82b6-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="c82b6-108">Attribute</span></span>|<span data-ttu-id="c82b6-109">Popis</span><span class="sxs-lookup"><span data-stu-id="c82b6-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c82b6-110">směr</span><span class="sxs-lookup"><span data-stu-id="c82b6-110">prefix</span></span>|<span data-ttu-id="c82b6-111">Identifikátor URI, který se používá k vyhledání části základní adresy.</span><span class="sxs-lookup"><span data-stu-id="c82b6-111">A URI that is used to match a part of a base address.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c82b6-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c82b6-112">Child Elements</span></span>  
 <span data-ttu-id="c82b6-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="c82b6-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c82b6-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c82b6-114">Parent Elements</span></span>  
  
|<span data-ttu-id="c82b6-115">Element</span><span class="sxs-lookup"><span data-stu-id="c82b6-115">Element</span></span>|<span data-ttu-id="c82b6-116">Popis</span><span class="sxs-lookup"><span data-stu-id="c82b6-116">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](baseaddressprefixfilters.md)|<span data-ttu-id="c82b6-117">Kolekce elementů konfigurace, které určují předávací filtry, které poskytují mechanismus pro výběr příslušných vazeb služby IIS při hostování aplikace Windows Communication Foundation (WCF) ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="c82b6-117">A collection of configuration elements that specify pass-through filters, which provide a mechanism to pick the appropriate IIS bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c82b6-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c82b6-118">Remarks</span></span>  
 <span data-ttu-id="c82b6-119">Filtr předpon poskytuje způsob, jak sdíleným poskytovatelům hostingu určit, které identifikátory URI bude služba používat.</span><span class="sxs-lookup"><span data-stu-id="c82b6-119">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="c82b6-120">Umožňuje sdíleným hostitelům hostovat více aplikací s různými základními adresami pro stejné schéma ve stejné lokalitě.</span><span class="sxs-lookup"><span data-stu-id="c82b6-120">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="c82b6-121">Webové stránky služby IIS jsou kontejnery pro virtuální aplikace, které obsahují virtuální adresáře.</span><span class="sxs-lookup"><span data-stu-id="c82b6-121">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="c82b6-122">Aplikace v lokalitě je k dispozici prostřednictvím jedné nebo více vazeb služby IIS.</span><span class="sxs-lookup"><span data-stu-id="c82b6-122">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="c82b6-123">Vazby služby IIS poskytují dvě informace: vazby protokolu a informace o vazbě.</span><span class="sxs-lookup"><span data-stu-id="c82b6-123">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="c82b6-124">Protokol vazby (například HTTP) definuje schéma, přes které probíhá komunikace, a informace o vazbě (například IP adresa, port, hostheader) obsahuje data, která se používají pro přístup k webu.</span><span class="sxs-lookup"><span data-stu-id="c82b6-124">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="c82b6-125">Služba IIS podporuje zadání více vazeb služby IIS pro každou lokalitu, což má za následek více základních adres pro každé schéma.</span><span class="sxs-lookup"><span data-stu-id="c82b6-125">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="c82b6-126">Vzhledem k tomu, že služba WCF hostovaná v rámci lokality umožňuje vytvořit vazbu pouze na jednu základní adresu pro každé schéma, můžete pomocí funkce filtru předpon vybrat požadovanou základní adresu hostované služby.</span><span class="sxs-lookup"><span data-stu-id="c82b6-126">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="c82b6-127">Příchozí základní adresy, které poskytuje služba IIS, se filtrují na základě volitelného filtru seznamu předpon.</span><span class="sxs-lookup"><span data-stu-id="c82b6-127">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="c82b6-128">Například váš web může obsahovat následující základní adresy:</span><span class="sxs-lookup"><span data-stu-id="c82b6-128">For example, your site can contain the following base addresses:</span></span>
  
```http
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="c82b6-129">Následující konfigurační soubor můžete použít k určení filtru předpony na úrovni domény AppDomain.</span><span class="sxs-lookup"><span data-stu-id="c82b6-129">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="c82b6-130">V tomto příkladu `net.tcp://test1.fabrikam.com:8000` `http://test2.fabrikam.com:9000` jsou jedinými základními adresami pro jejich příslušné systémy, které mohou být předány.</span><span class="sxs-lookup"><span data-stu-id="c82b6-130">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="c82b6-131">Ve výchozím nastavení, pokud není zadána předpona, jsou předány všechny adresy.</span><span class="sxs-lookup"><span data-stu-id="c82b6-131">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="c82b6-132">Zadání předpony umožňuje předávat odpovídající základní adresu pro toto schéma.</span><span class="sxs-lookup"><span data-stu-id="c82b6-132">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c82b6-133">Filtr nepodporuje žádné zástupné znaky.</span><span class="sxs-lookup"><span data-stu-id="c82b6-133">The filter does not support any wildcards.</span></span> <span data-ttu-id="c82b6-134">Kromě toho adres BaseAddresses poskytované službou IIS může mít adresy svázané s jinými schématy, která nejsou přítomna v `baseAddressPrefixFilters` seznamu.</span><span class="sxs-lookup"><span data-stu-id="c82b6-134">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="c82b6-135">Tyto adresy nejsou vyfiltrovány.</span><span class="sxs-lookup"><span data-stu-id="c82b6-135">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c82b6-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="c82b6-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="c82b6-137">Hosting</span><span class="sxs-lookup"><span data-stu-id="c82b6-137">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
