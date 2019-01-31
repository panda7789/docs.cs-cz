---
title: < System.web > – Element (nastavení webu)
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
ms.openlocfilehash: a8d0905dc64ae3e3c4977639ccf881a677de73a9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272809"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="25513-102">\<System.Web > – Element (nastavení webu)</span><span class="sxs-lookup"><span data-stu-id="25513-102">\<system.web> Element (Web Settings)</span></span>
<span data-ttu-id="25513-103">Obsahuje informace o jak spravuje chování v celém procesu vrstvy hostování technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="25513-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
 <span data-ttu-id="25513-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="25513-104">\<configuration></span></span>  
<span data-ttu-id="25513-105">\<System.Web > – Element (nastavení webu)</span><span class="sxs-lookup"><span data-stu-id="25513-105">\<system.web> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25513-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25513-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25513-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="25513-107">Attributes and Elements</span></span>  
 <span data-ttu-id="25513-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="25513-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25513-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="25513-109">Attributes</span></span>  
 <span data-ttu-id="25513-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="25513-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="25513-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="25513-111">Child Elements</span></span>  
  
|<span data-ttu-id="25513-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="25513-112">Element</span></span>|<span data-ttu-id="25513-113">Popis</span><span class="sxs-lookup"><span data-stu-id="25513-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25513-114">\<applicationPool></span><span class="sxs-lookup"><span data-stu-id="25513-114">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="25513-115">Určuje nastavení konfigurace pro fondy aplikací IIS v soubor aspnet.config.</span><span class="sxs-lookup"><span data-stu-id="25513-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="25513-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="25513-116">Parent Elements</span></span>  
  
|<span data-ttu-id="25513-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="25513-117">Element</span></span>|<span data-ttu-id="25513-118">Popis</span><span class="sxs-lookup"><span data-stu-id="25513-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25513-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="25513-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="25513-120">Určuje kořenový element v každém konfiguračním souboru, který je používán common language runtime a [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplikací.</span><span class="sxs-lookup"><span data-stu-id="25513-120">Specifies the root element in every configuration file that is used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25513-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25513-121">Remarks</span></span>  
 <span data-ttu-id="25513-122">`system.web` Elementu a jeho podřízené `applicationPool` element byly přidány do [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] od [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="25513-122">The `system.web` element and its child `applicationPool` element were added to the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] as of [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span></span> <span data-ttu-id="25513-123">Při spuštění [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] nebo novější verze v integrovaném režimu, tato kombinace elementu vám umožní nakonfigurovat jak spravuje vláken ASP.NET a jak se zařadí do fronty žádostí při technologie ASP.NET je hostovaná ve fondu aplikací služby IIS.</span><span class="sxs-lookup"><span data-stu-id="25513-123">When you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="25513-124">Pokud spustíte [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] nebo novější verze v režimu Classic nebo rozhraní ISAPI, tato nastavení ignorují.</span><span class="sxs-lookup"><span data-stu-id="25513-124">If you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25513-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="25513-125">Example</span></span>  
 <span data-ttu-id="25513-126">Následující příklad ukazuje, jak konfigurovat chování v celém procesu ASP.NET v souboru aspnet.config technologie ASP.NET je hostovaná ve fondu aplikací služby IIS.</span><span class="sxs-lookup"><span data-stu-id="25513-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="25513-127">Příklad předpokládá, že služba IIS pracuje v integrovaného režimu a že aplikace používá [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] nebo novější.</span><span class="sxs-lookup"><span data-stu-id="25513-127">The example assumes that IIS is running in Integrated mode and that the application is using the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] or a later version.</span></span> <span data-ttu-id="25513-128">K tomuto chování nedojde ve verzích [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] starší než [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="25513-128">This behavior does not occur in versions of the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] earlier than the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span></span> <span data-ttu-id="25513-129">Hodnoty v tomto příkladu jsou výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="25513-129">The values in the example are the default values.</span></span>  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"   
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="25513-130">Informace o elementu</span><span class="sxs-lookup"><span data-stu-id="25513-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="25513-131">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="25513-131">Namespace</span></span>||  
|<span data-ttu-id="25513-132">Název schématu</span><span class="sxs-lookup"><span data-stu-id="25513-132">Schema Name</span></span>||  
|<span data-ttu-id="25513-133">Soubor ověření</span><span class="sxs-lookup"><span data-stu-id="25513-133">Validation File</span></span>||  
|<span data-ttu-id="25513-134">Může být prázdné.</span><span class="sxs-lookup"><span data-stu-id="25513-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="25513-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25513-135">See also</span></span>
- [<span data-ttu-id="25513-136">\<applicationPool > – Element (nastavení webu)</span><span class="sxs-lookup"><span data-stu-id="25513-136">\<applicationPool> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)
