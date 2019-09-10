---
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: a22623c0856dd6d9b7c8c75e0b3feccc2d9350bd
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850197"
---
# <a name="baseaddressprefixfilters"></a><span data-ttu-id="29796-101">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="29796-101">\<baseAddressPrefixFilters></span></span>
<span data-ttu-id="29796-102">Představuje kolekci elementů konfigurace, které určují předávací filtry, které poskytují mechanismus pro výběr příslušných vazeb Internetová informační služba (IIS) při hostování aplikace Windows Communication Foundation (WCF) ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="29796-102">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="29796-103">\<baseAddressPrefixFilters > nerozpozná "localhost"; místo toho použijte plně kvalifikovaný název počítače.</span><span class="sxs-lookup"><span data-stu-id="29796-103">\<baseAddressPrefixFilters> does not recognize "localhost"; use the fully qualified machine name instead.</span></span>  
  
<span data-ttu-id="29796-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="29796-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="29796-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="29796-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="29796-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceHostingEnvironment >** ](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="29796-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="29796-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<baseAddressPrefixFilters >**</span><span class="sxs-lookup"><span data-stu-id="29796-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddressPrefixFilters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29796-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29796-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29796-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="29796-109">Attributes and Elements</span></span>  
 <span data-ttu-id="29796-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="29796-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29796-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="29796-111">Attributes</span></span>  
 <span data-ttu-id="29796-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="29796-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="29796-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="29796-113">Child Elements</span></span>  
  
|<span data-ttu-id="29796-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="29796-114">Element</span></span>|<span data-ttu-id="29796-115">Popis</span><span class="sxs-lookup"><span data-stu-id="29796-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29796-116">\<add></span><span class="sxs-lookup"><span data-stu-id="29796-116">\<add></span></span>](add-of-baseaddressprefixfilter.md)|<span data-ttu-id="29796-117">Přidá prvek konfigurace, který určuje filtr předpony pro základní adresy používané hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="29796-117">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="29796-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="29796-118">Parent Elements</span></span>  
  
|<span data-ttu-id="29796-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="29796-119">Element</span></span>|<span data-ttu-id="29796-120">Popis</span><span class="sxs-lookup"><span data-stu-id="29796-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29796-121">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="29796-121">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="29796-122">Definuje typ, který hostující prostředí služby vytvoří pro konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="29796-122">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29796-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29796-123">Remarks</span></span>  
 <span data-ttu-id="29796-124">Filtr předpon poskytuje způsob, jak sdíleným poskytovatelům hostingu určit, které identifikátory URI bude služba používat.</span><span class="sxs-lookup"><span data-stu-id="29796-124">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="29796-125">Umožňuje sdíleným hostitelům hostovat více aplikací s různými základními adresami pro stejné schéma ve stejné lokalitě.</span><span class="sxs-lookup"><span data-stu-id="29796-125">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="29796-126">Webové stránky služby IIS jsou kontejnery pro virtuální aplikace, které obsahují virtuální adresáře.</span><span class="sxs-lookup"><span data-stu-id="29796-126">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="29796-127">Aplikace v lokalitě je k dispozici prostřednictvím jedné nebo více vazeb služby IIS.</span><span class="sxs-lookup"><span data-stu-id="29796-127">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="29796-128">Vazby služby IIS poskytují dvě informace: vazby protokolu a informace o vazbě.</span><span class="sxs-lookup"><span data-stu-id="29796-128">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="29796-129">Protokol vazby (například HTTP) definuje schéma, přes které probíhá komunikace, a informace o vazbě (například IP adresa, port, hostheader) obsahuje data, která se používají pro přístup k webu.</span><span class="sxs-lookup"><span data-stu-id="29796-129">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="29796-130">Služba IIS podporuje zadání více vazeb služby IIS pro každou lokalitu, což má za následek více základních adres pro každé schéma.</span><span class="sxs-lookup"><span data-stu-id="29796-130">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="29796-131">Vzhledem k tomu, že služba WCF hostovaná v rámci lokality umožňuje vytvořit vazbu pouze na jednu základní adresu pro každé schéma, můžete pomocí funkce filtru předpon vybrat požadovanou základní adresu hostované služby.</span><span class="sxs-lookup"><span data-stu-id="29796-131">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="29796-132">Příchozí základní adresy, které poskytuje služba IIS, se filtrují na základě volitelného filtru seznamu předpon.</span><span class="sxs-lookup"><span data-stu-id="29796-132">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="29796-133">Například váš web může obsahovat následující základní adresy.</span><span class="sxs-lookup"><span data-stu-id="29796-133">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="29796-134">Následující konfigurační soubor můžete použít k určení filtru předpony na úrovni domény AppDomain.</span><span class="sxs-lookup"><span data-stu-id="29796-134">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="29796-135">V tomto příkladu `net.tcp://test1.fabrikam.com:8000` `http://test2.fabrikam.com:9000` jsou jedinými základními adresami pro příslušné režimy, které mohou být předány.</span><span class="sxs-lookup"><span data-stu-id="29796-135">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="29796-136">Ve výchozím nastavení, pokud není zadána předpona, jsou předány všechny adresy.</span><span class="sxs-lookup"><span data-stu-id="29796-136">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="29796-137">Zadání předpony umožňuje předávat odpovídající základní adresu pro toto schéma.</span><span class="sxs-lookup"><span data-stu-id="29796-137">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="29796-138">Filtr nepodporuje žádné zástupné znaky.</span><span class="sxs-lookup"><span data-stu-id="29796-138">The filter does not support any wildcards.</span></span> <span data-ttu-id="29796-139">Kromě toho adres BaseAddresses poskytované službou IIS může mít adresy svázané s jinými schématy, která nejsou přítomna `baseAddressPrefixFilters` v seznamu.</span><span class="sxs-lookup"><span data-stu-id="29796-139">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="29796-140">Tyto adresy nejsou vyfiltrovány.</span><span class="sxs-lookup"><span data-stu-id="29796-140">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29796-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29796-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="29796-142">Hostování</span><span class="sxs-lookup"><span data-stu-id="29796-142">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
