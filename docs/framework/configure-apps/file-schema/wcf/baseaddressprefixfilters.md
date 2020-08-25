---
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 635e4f02f4d286b63c4f4845563ba1953d23592a
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811896"
---
# \<baseAddressPrefixFilters>
<span data-ttu-id="5dd03-101">Představuje kolekci elementů konfigurace, které určují předávací filtry, které poskytují mechanismus pro výběr příslušných vazeb Internetová informační služba (IIS) při hostování aplikace Windows Communication Foundation (WCF) ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="5dd03-101">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="5dd03-102">\<baseAddressPrefixFilters> nerozpozná "localhost"; místo toho použijte plně kvalifikovaný název počítače.</span><span class="sxs-lookup"><span data-stu-id="5dd03-102">\<baseAddressPrefixFilters> does not recognize "localhost"; use the fully qualified machine name instead.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddressPrefixFilters>**  
  
## <a name="syntax"></a><span data-ttu-id="5dd03-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="5dd03-103">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5dd03-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5dd03-104">Attributes and Elements</span></span>  
 <span data-ttu-id="5dd03-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5dd03-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5dd03-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="5dd03-106">Attributes</span></span>  
 <span data-ttu-id="5dd03-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="5dd03-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5dd03-108">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5dd03-108">Child Elements</span></span>  
  
|<span data-ttu-id="5dd03-109">Element</span><span class="sxs-lookup"><span data-stu-id="5dd03-109">Element</span></span>|<span data-ttu-id="5dd03-110">Popis</span><span class="sxs-lookup"><span data-stu-id="5dd03-110">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-baseaddressprefixfilter.md)|<span data-ttu-id="5dd03-111">Přidá prvek konfigurace, který určuje filtr předpony pro základní adresy používané hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="5dd03-111">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5dd03-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5dd03-112">Parent Elements</span></span>  
  
|<span data-ttu-id="5dd03-113">Element</span><span class="sxs-lookup"><span data-stu-id="5dd03-113">Element</span></span>|<span data-ttu-id="5dd03-114">Popis</span><span class="sxs-lookup"><span data-stu-id="5dd03-114">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="5dd03-115">Definuje typ, který hostující prostředí služby vytvoří pro konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="5dd03-115">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5dd03-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5dd03-116">Remarks</span></span>  
 <span data-ttu-id="5dd03-117">Filtr předpon poskytuje způsob, jak sdíleným poskytovatelům hostingu určit, které identifikátory URI bude služba používat.</span><span class="sxs-lookup"><span data-stu-id="5dd03-117">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="5dd03-118">Umožňuje sdíleným hostitelům hostovat více aplikací s různými základními adresami pro stejné schéma ve stejné lokalitě.</span><span class="sxs-lookup"><span data-stu-id="5dd03-118">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="5dd03-119">Webové stránky služby IIS jsou kontejnery pro virtuální aplikace, které obsahují virtuální adresáře.</span><span class="sxs-lookup"><span data-stu-id="5dd03-119">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="5dd03-120">Aplikace v lokalitě je k dispozici prostřednictvím jedné nebo více vazeb služby IIS.</span><span class="sxs-lookup"><span data-stu-id="5dd03-120">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="5dd03-121">Vazby služby IIS poskytují dvě informace: vazby protokolu a informace o vazbě.</span><span class="sxs-lookup"><span data-stu-id="5dd03-121">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="5dd03-122">Protokol vazby (například HTTP) definuje schéma, přes které probíhá komunikace, a informace o vazbě (například IP adresa, port, hostheader) obsahuje data, která se používají pro přístup k webu.</span><span class="sxs-lookup"><span data-stu-id="5dd03-122">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="5dd03-123">Služba IIS podporuje zadání více vazeb služby IIS pro každou lokalitu, což má za následek více základních adres pro každé schéma.</span><span class="sxs-lookup"><span data-stu-id="5dd03-123">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="5dd03-124">Vzhledem k tomu, že služba WCF hostovaná v rámci lokality umožňuje vytvořit vazbu pouze na jednu základní adresu pro každé schéma, můžete pomocí funkce filtru předpon vybrat požadovanou základní adresu hostované služby.</span><span class="sxs-lookup"><span data-stu-id="5dd03-124">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="5dd03-125">Příchozí základní adresy, které poskytuje služba IIS, se filtrují na základě volitelného filtru seznamu předpon.</span><span class="sxs-lookup"><span data-stu-id="5dd03-125">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="5dd03-126">Například váš web může obsahovat následující základní adresy:</span><span class="sxs-lookup"><span data-stu-id="5dd03-126">For example, your site can contain the following base addresses:</span></span>
  
```http
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="5dd03-127">Následující konfigurační soubor můžete použít k určení filtru předpony na úrovni domény AppDomain.</span><span class="sxs-lookup"><span data-stu-id="5dd03-127">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="5dd03-128">V tomto příkladu `net.tcp://test1.fabrikam.com:8000` `http://test2.fabrikam.com:9000` jsou jedinými základními adresami pro příslušné režimy, které mohou být předány.</span><span class="sxs-lookup"><span data-stu-id="5dd03-128">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="5dd03-129">Ve výchozím nastavení, pokud není zadána předpona, jsou předány všechny adresy.</span><span class="sxs-lookup"><span data-stu-id="5dd03-129">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="5dd03-130">Zadání předpony umožňuje předávat odpovídající základní adresu pro toto schéma.</span><span class="sxs-lookup"><span data-stu-id="5dd03-130">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5dd03-131">Filtr nepodporuje žádné zástupné znaky.</span><span class="sxs-lookup"><span data-stu-id="5dd03-131">The filter does not support any wildcards.</span></span> <span data-ttu-id="5dd03-132">Kromě toho adres BaseAddresses poskytované službou IIS může mít adresy svázané s jinými schématy, která nejsou přítomna v `baseAddressPrefixFilters` seznamu.</span><span class="sxs-lookup"><span data-stu-id="5dd03-132">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="5dd03-133">Tyto adresy nejsou vyfiltrovány.</span><span class="sxs-lookup"><span data-stu-id="5dd03-133">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dd03-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="5dd03-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="5dd03-135">Hosting</span><span class="sxs-lookup"><span data-stu-id="5dd03-135">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
