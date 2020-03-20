---
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 0673507b72690c3a5c7dcc35442c05e378dba43c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153032"
---
# <a name="baseaddressprefixfilters"></a><span data-ttu-id="57ae2-101">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="57ae2-101">\<baseAddressPrefixFilters></span></span>
<span data-ttu-id="57ae2-102">Představuje kolekci konfiguračních prvků, které určují průchod filtry, které poskytují mechanismus pro výběr příslušných vazeb Internetové informační služby (IIS) při hostování aplikace WCF (Windows Communication Foundation) ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="57ae2-102">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="57ae2-103">\<baseAddressPrefixFilters> nerozpozná "localhost"; místo toho použijte plně kvalifikovaný název počítače.</span><span class="sxs-lookup"><span data-stu-id="57ae2-103">\<baseAddressPrefixFilters> does not recognize "localhost"; use the fully qualified machine name instead.</span></span>  
  
<span data-ttu-id="57ae2-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="57ae2-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="57ae2-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="57ae2-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="57ae2-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="57ae2-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="57ae2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddressPrefixFilters>**</span><span class="sxs-lookup"><span data-stu-id="57ae2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddressPrefixFilters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57ae2-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57ae2-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57ae2-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="57ae2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="57ae2-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="57ae2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57ae2-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="57ae2-111">Attributes</span></span>  
 <span data-ttu-id="57ae2-112">Žádné.</span><span class="sxs-lookup"><span data-stu-id="57ae2-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="57ae2-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="57ae2-113">Child Elements</span></span>  
  
|<span data-ttu-id="57ae2-114">Element</span><span class="sxs-lookup"><span data-stu-id="57ae2-114">Element</span></span>|<span data-ttu-id="57ae2-115">Popis</span><span class="sxs-lookup"><span data-stu-id="57ae2-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57ae2-116">\<přidat></span><span class="sxs-lookup"><span data-stu-id="57ae2-116">\<add></span></span>](add-of-baseaddressprefixfilter.md)|<span data-ttu-id="57ae2-117">Přidá konfigurační prvek, který určuje filtr předpony pro základní adresy používané hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="57ae2-117">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="57ae2-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="57ae2-118">Parent Elements</span></span>  
  
|<span data-ttu-id="57ae2-119">Element</span><span class="sxs-lookup"><span data-stu-id="57ae2-119">Element</span></span>|<span data-ttu-id="57ae2-120">Popis</span><span class="sxs-lookup"><span data-stu-id="57ae2-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57ae2-121">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="57ae2-121">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="57ae2-122">Definuje typ, který konsteaci prostředí hostování služby pro konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="57ae2-122">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57ae2-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="57ae2-123">Remarks</span></span>  
 <span data-ttu-id="57ae2-124">Filtr předpony poskytuje poskytovatelům sdíleného hostingu způsob, jak určit, které identifikátory URI mají být službou používány.</span><span class="sxs-lookup"><span data-stu-id="57ae2-124">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="57ae2-125">Umožňuje sdíleným hostitelům hostovat více aplikací s různými základními adresami pro stejné schéma na stejném webu.</span><span class="sxs-lookup"><span data-stu-id="57ae2-125">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="57ae2-126">Weby služby IIS jsou kontejnery pro virtuální aplikace, které obsahují virtuální adresáře.</span><span class="sxs-lookup"><span data-stu-id="57ae2-126">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="57ae2-127">Aplikace v lokalitě je přístupná prostřednictvím jedné nebo více vazeb služby IIS.</span><span class="sxs-lookup"><span data-stu-id="57ae2-127">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="57ae2-128">Vazby iis poskytují dvě informace: závazný protokol a informace o vazbě.</span><span class="sxs-lookup"><span data-stu-id="57ae2-128">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="57ae2-129">Protokol vazby (například HTTP) definuje schéma, přes které dochází ke komunikaci, a informace o vazbě (například IP adresa, port, hlavička hostitele) obsahují data použitá pro přístup k webu.</span><span class="sxs-lookup"><span data-stu-id="57ae2-129">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="57ae2-130">IIS podporuje určení více vazeb iis pro každou lokalitu, což má za následek více základních adres pro každé schéma.</span><span class="sxs-lookup"><span data-stu-id="57ae2-130">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="57ae2-131">Vzhledem k tomu, že služba WCF hostovaná pod webem umožňuje vazbu pouze na jednu základní adresu pro každé schéma, můžete pomocí funkce filtru předpony vybrat požadovanou základní adresu hostované služby.</span><span class="sxs-lookup"><span data-stu-id="57ae2-131">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="57ae2-132">Příchozí základní adresy dodané službou IIS jsou filtrovány na základě volitelného filtru seznamu předponami.</span><span class="sxs-lookup"><span data-stu-id="57ae2-132">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="57ae2-133">Web může například obsahovat následující základní adresy:</span><span class="sxs-lookup"><span data-stu-id="57ae2-133">For example, your site can contain the following base addresses:</span></span>
  
```
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="57ae2-134">Následující konfigurační soubor můžete použít k určení filtru předpony na úrovni domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="57ae2-134">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="57ae2-135">V tomto `net.tcp://test1.fabrikam.com:8000` příkladu a `http://test2.fabrikam.com:9000` jsou pouze základní adresy pro jejich příslušná schémata, které mohou být předány.</span><span class="sxs-lookup"><span data-stu-id="57ae2-135">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="57ae2-136">Ve výchozím nastavení není zadána předpona, jsou předány všechny adresy.</span><span class="sxs-lookup"><span data-stu-id="57ae2-136">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="57ae2-137">Zadání předpony umožňuje pouze odpovídající základní adresu pro toto schéma, které mají být předány.</span><span class="sxs-lookup"><span data-stu-id="57ae2-137">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="57ae2-138">Filtr nepodporuje žádné zástupné znaky.</span><span class="sxs-lookup"><span data-stu-id="57ae2-138">The filter does not support any wildcards.</span></span> <span data-ttu-id="57ae2-139">Kromě toho baseAddresses poskytované iIS může mít adresy vázané na jiná `baseAddressPrefixFilters` schémata, které nejsou k dispozici v seznamu.</span><span class="sxs-lookup"><span data-stu-id="57ae2-139">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="57ae2-140">Tyto adresy nejsou odfiltrovány.</span><span class="sxs-lookup"><span data-stu-id="57ae2-140">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57ae2-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="57ae2-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="57ae2-142">Hostování</span><span class="sxs-lookup"><span data-stu-id="57ae2-142">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
