---
title: '&lt;baseAddressPrefixFilters&gt;'
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 04579980201b397e7ed92f55ffcb19e54de18aaa
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149225"
---
# <a name="ltbaseaddressprefixfiltersgt"></a><span data-ttu-id="b5e57-102">&lt;baseAddressPrefixFilters&gt;</span><span class="sxs-lookup"><span data-stu-id="b5e57-102">&lt;baseAddressPrefixFilters&gt;</span></span>
<span data-ttu-id="b5e57-103">Představuje kolekci konfigurace, které prvky, které určují předávání filtry, které poskytují mechanismus pro výběr příslušné vazby Internetové informační služby (IIS) při hostování aplikace Windows Communication Foundation (WCF) ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="b5e57-103">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="b5e57-104">\<baseAddressPrefixFilters > neobsahuje rozpoznat "localhost", použijte místo toho plně kvalifikovaný název počítače.</span><span class="sxs-lookup"><span data-stu-id="b5e57-104">\<baseAddressPrefixFilters> does not recognize "localhost", use the fully qualified machine name instead.</span></span>  
  
 <span data-ttu-id="b5e57-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b5e57-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="b5e57-106">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="b5e57-106">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5e57-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5e57-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5e57-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b5e57-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b5e57-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b5e57-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5e57-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="b5e57-110">Attributes</span></span>  
 <span data-ttu-id="b5e57-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="b5e57-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b5e57-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b5e57-112">Child Elements</span></span>  
  
|<span data-ttu-id="b5e57-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="b5e57-113">Element</span></span>|<span data-ttu-id="b5e57-114">Popis</span><span class="sxs-lookup"><span data-stu-id="b5e57-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5e57-115">\<add></span><span class="sxs-lookup"><span data-stu-id="b5e57-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddressprefixfilter.md)|<span data-ttu-id="b5e57-116">Přidá prvek konfigurace, který určuje předponu filtr pro základní adresy použité hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="b5e57-116">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b5e57-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b5e57-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b5e57-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="b5e57-118">Element</span></span>|<span data-ttu-id="b5e57-119">Popis</span><span class="sxs-lookup"><span data-stu-id="b5e57-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5e57-120">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="b5e57-120">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="b5e57-121">Definuje typ, který vytvoří instanci hostitelským prostředím služby pro konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="b5e57-121">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5e57-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b5e57-122">Remarks</span></span>  
 <span data-ttu-id="b5e57-123">Filtr předponu poskytuje způsob pro sdílené poskytovatele hostingu k určení, které identifikátory URI se používá služba.</span><span class="sxs-lookup"><span data-stu-id="b5e57-123">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="b5e57-124">Umožňuje sdílené hostitele k hostování více aplikací s jinou bázové adresy pro stejné schéma na stejném místě.</span><span class="sxs-lookup"><span data-stu-id="b5e57-124">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="b5e57-125">Webové servery služby IIS jsou kontejnery pro virtuální aplikace, které obsahují virtuální adresáře.</span><span class="sxs-lookup"><span data-stu-id="b5e57-125">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="b5e57-126">Aplikace v síti přístupné prostřednictvím jedné nebo více vazeb služby IIS.</span><span class="sxs-lookup"><span data-stu-id="b5e57-126">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="b5e57-127">Vazby služby IIS poskytuje dva druhy údajů: protokol vazby a informace o vazbě.</span><span class="sxs-lookup"><span data-stu-id="b5e57-127">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="b5e57-128">Vazba protokolu (třeba HTTP) definuje schéma, přes které probíhá komunikace a vazby informace (například IP adresy, portu, hostitel) obsahuje data sloužící k přístupu na web.</span><span class="sxs-lookup"><span data-stu-id="b5e57-128">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="b5e57-129">Služba IIS podporuje zadávání více vazeb služby IIS pro každou lokalitu, což vede k více bázové adresy pro každé schéma.</span><span class="sxs-lookup"><span data-stu-id="b5e57-129">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="b5e57-130">Protože služby WCF hostované na webu umožňuje vytváření vazby na pouze jednu základní adresu pro každé schéma, můžete použít předponu funkce filtru pro výběr vyžaduje základní adresa hostované služby.</span><span class="sxs-lookup"><span data-stu-id="b5e57-130">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="b5e57-131">Příchozí základní adresy poskytované službou IIS, jsou filtrované na základě seznamu filtru volitelné předpony.</span><span class="sxs-lookup"><span data-stu-id="b5e57-131">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="b5e57-132">Váš web může obsahovat například následující základní adresy.</span><span class="sxs-lookup"><span data-stu-id="b5e57-132">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="b5e57-133">Následující konfigurační soubor můžete použít k zadání předpony filtr na úrovni appdomain.</span><span class="sxs-lookup"><span data-stu-id="b5e57-133">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="b5e57-134">V tomto příkladu `net.tcp://test1.fabrikam.com:8000` a `http://test2.fabrikam.com:9000` jsou pouze bázové adresy pro příslušné schémata, které jsou povolené, které se budou předávat.</span><span class="sxs-lookup"><span data-stu-id="b5e57-134">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="b5e57-135">Ve výchozím nastavení Pokud není zadána předponu, všechny adresy se předaly.</span><span class="sxs-lookup"><span data-stu-id="b5e57-135">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="b5e57-136">Určení předpona, která umožňuje pouze odpovídající základní adresa pro toto schéma, které se budou předávat.</span><span class="sxs-lookup"><span data-stu-id="b5e57-136">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5e57-137">Tento filtr nepodporuje žádné zástupné znaky.</span><span class="sxs-lookup"><span data-stu-id="b5e57-137">The filter does not support any wildcards.</span></span> <span data-ttu-id="b5e57-138">Kromě toho baseAddresses poskytované službou IIS pravděpodobně adresy, které jsou vázány na jiná schémata není k dispozici v `baseAddressPrefixFilters` seznamu.</span><span class="sxs-lookup"><span data-stu-id="b5e57-138">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="b5e57-139">Tyto adresy nejsou odfiltrovány.</span><span class="sxs-lookup"><span data-stu-id="b5e57-139">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5e57-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5e57-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="b5e57-141">Hostování</span><span class="sxs-lookup"><span data-stu-id="b5e57-141">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
