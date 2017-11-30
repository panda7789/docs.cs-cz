---
title: "Aktivace založená na konfiguraci v IIS a WAS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 116d7ec11f141e813aa960b28289031e0cfa8999
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="configuration-based-activation-in-iis-and-was"></a><span data-ttu-id="992f5-102">Aktivace založená na konfiguraci v IIS a WAS</span><span class="sxs-lookup"><span data-stu-id="992f5-102">Configuration-Based Activation in IIS and WAS</span></span>
<span data-ttu-id="992f5-103">Za normálních okolností při hostování [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby v rámci Internetové informační služby (IIS) nebo služby Aktivace procesů systému Windows (WAS), je nutné zadat soubor .svc.</span><span class="sxs-lookup"><span data-stu-id="992f5-103">Normally when hosting a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service under Internet Information Services (IIS) or Windows Process Activation Service (WAS), you must provide a .svc file.</span></span> <span data-ttu-id="992f5-104">Soubor .svc obsahuje název služby a objekt pro vytváření hostitele volitelné vlastní službu.</span><span class="sxs-lookup"><span data-stu-id="992f5-104">The .svc file contains the name of the service and an optional custom service host factory.</span></span> <span data-ttu-id="992f5-105">Tento další soubor přidá režijní náklady na možnosti správy.</span><span class="sxs-lookup"><span data-stu-id="992f5-105">This additional file adds manageability overhead.</span></span> <span data-ttu-id="992f5-106">Aktivace podle konfigurace funkce eliminuje požadavek na soubor .svc a proto přidružené režijní náklady.</span><span class="sxs-lookup"><span data-stu-id="992f5-106">The configuration-based activation feature removes the requirement to have a .svc file and therefore the associated overhead.</span></span>  
  
## <a name="configuration-based-activation"></a><span data-ttu-id="992f5-107">Aktivace podle konfigurace</span><span class="sxs-lookup"><span data-stu-id="992f5-107">Configuration-Based Activation</span></span>  
 <span data-ttu-id="992f5-108">Aktivace podle konfigurace trvá metadata, která umožňuje umístit do souboru .svc a umístí jej do souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="992f5-108">Configuration-based activation takes the metadata that used to be placed in the .svc file and places it in the Web.config file.</span></span> <span data-ttu-id="992f5-109">V rámci <`serviceHostingEnvironment`> elementu je <`serviceActivations`> elementu.</span><span class="sxs-lookup"><span data-stu-id="992f5-109">Within the<`serviceHostingEnvironment`> element there is a <`serviceActivations`> element.</span></span> <span data-ttu-id="992f5-110">V rámci <`serviceActivations`> element jsou jeden nebo více <`add`> elementy, jeden pro každou hostovanou službu.</span><span class="sxs-lookup"><span data-stu-id="992f5-110">Within the <`serviceActivations`> element are one or more <`add`> elements, one for each hosted service.</span></span> <span data-ttu-id="992f5-111"><`add`> Element obsahuje atributy, které umožňují nastavit relativní adresu pro službu a typ služby nebo vytváření hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="992f5-111">The <`add`> element contains attributes that let you set the relative address for the service and the service type or a service host factory.</span></span> <span data-ttu-id="992f5-112">Následující příklad kódu konfigurace ukazuje, jak se používá v této části.</span><span class="sxs-lookup"><span data-stu-id="992f5-112">The following configuration example code shows how this section is used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="992f5-113">Každý <`add`> element musí specifikovat, služby nebo atributu objektu pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="992f5-113">Each <`add`> element must specify a service or a factory attribute.</span></span> <span data-ttu-id="992f5-114">Zadání služby a objektu pro vytváření atributy je povoleno.</span><span class="sxs-lookup"><span data-stu-id="992f5-114">Specifying both service and factory attributes is allowed.</span></span>  
  
```xml  
<serviceHostingEnvironment>  
  <serviceActivations>  
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>  
  </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
 <span data-ttu-id="992f5-115">Pomocí této v souboru Web.config můžete umístit zdrojový kód služby v adresáři App_Code dodržela sestavení v adresáři Bin aplikace nebo aplikace.</span><span class="sxs-lookup"><span data-stu-id="992f5-115">With this in the Web.config file, you can place the service source code in the App_Code directory of the application or a complied assembly in the Bin directory of the application.</span></span>  
  
> [!NOTE]
>  -   <span data-ttu-id="992f5-116">Při použití aktivace podle konfigurace, vloženého kódu v souborů .svc není podporována.</span><span class="sxs-lookup"><span data-stu-id="992f5-116">When using configuration-based activation, inline code in .svc files is not supported.</span></span>  
> -   <span data-ttu-id="992f5-117">`relativeAddress` Musí být nastaven na relativní adresu jako "\<podadresář > / service.svc" nebo "~ /\<directory dílčí, service.svc".</span><span class="sxs-lookup"><span data-stu-id="992f5-117">The `relativeAddress` attribute must be set to a relative address such as "\<sub-directory>/service.svc" or "~/\<sub-directory/service.svc".</span></span>  
> -   <span data-ttu-id="992f5-118">Když si zaregistrujete relativní adresu, která nemá známou příponou spojené s použitím technologie WCF, je vyvolána výjimka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="992f5-118">A configuration exception is thrown if you register a relative address that does not have a known extension associated with WCF.</span></span>  
> -   <span data-ttu-id="992f5-119">Zadaná relativní adresa je relativní vůči kořenovému adresáři virtuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="992f5-119">The relative address specified is relative to the root of the virtual application.</span></span>  
> -   <span data-ttu-id="992f5-120">Kvůli model hierarchické konfigurace jsou registrované relativní adresy na počítači a lokalitou úrovni zděděny virtuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="992f5-120">Due to the hierarchical model of configuration, the registered relative addresses at machine and site level are inherited by virtual applications.</span></span>  
> -   <span data-ttu-id="992f5-121">Registrace v konfiguračním souboru mají přednost před nastavením v .svc .xamlx, XOML nebo jiný soubor.</span><span class="sxs-lookup"><span data-stu-id="992f5-121">Registrations in a configuration file take precedence over settings in a .svc, .xamlx, .xoml, or other file.</span></span>  
> -   <span data-ttu-id="992f5-122">Všechny ' \' (zpětná lomítka) v identifikátoru URI odeslaných do služby IIS / se budou automaticky převedeny na / (lomítko).</span><span class="sxs-lookup"><span data-stu-id="992f5-122">Any ‘\’ (backslashes) in a URI sent to IIS/WAS are automatically converted to a ‘/’ (forward slash).</span></span> <span data-ttu-id="992f5-123">Pokud relativní adresa se přidá, obsahuje ' \' a odeslat identifikátor URI, který používá relativní adresu služby IIS, zpětné lomítko je převeden na dopředné lomítko a služby IIS nesmí shodovat s relativní adresu.</span><span class="sxs-lookup"><span data-stu-id="992f5-123">If a relative address is added that contains a ‘\’ and you send IIS a URI that uses the relative address, the backslash is converted to a forward slash and IIS cannot match it to the relative address.</span></span> <span data-ttu-id="992f5-124">Služba IIS odesílá informace trasování, která označuje, že jsou nebyly nalezeny žádné shody.</span><span class="sxs-lookup"><span data-stu-id="992f5-124">IIS sends out trace information that indicates that there are no matches found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="992f5-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="992f5-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>  
 [<span data-ttu-id="992f5-126">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="992f5-126">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="992f5-127">Přehled hostování služeb pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="992f5-127">Hosting Workflow Services Overview</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 [<span data-ttu-id="992f5-128">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="992f5-128">\<serviceHostingEnvironment></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)  
 [<span data-ttu-id="992f5-129">Hostování funkcí systému Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="992f5-129">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
