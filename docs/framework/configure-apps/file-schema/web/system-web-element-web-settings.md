---
title: Element <system.web> (nastavení webu)
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
ms.openlocfilehash: b37b05bdf90630251cbfcf86751243a3a8b77663
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152838"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="39c21-102">\<system.web> Element (Nastavení webu)</span><span class="sxs-lookup"><span data-stu-id="39c21-102">\<system.web> Element (Web Settings)</span></span>
<span data-ttu-id="39c21-103">Obsahuje informace o tom, jak ASP.NET hostitelské vrstvy spravuje chování celého procesu.</span><span class="sxs-lookup"><span data-stu-id="39c21-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
[<span data-ttu-id="39c21-104">**\<>konfigurace**</span><span class="sxs-lookup"><span data-stu-id="39c21-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="39c21-105">&nbsp;&nbsp;**\<system.web>**</span><span class="sxs-lookup"><span data-stu-id="39c21-105">&nbsp;&nbsp;**\<system.web>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39c21-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39c21-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39c21-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="39c21-107">Attributes and Elements</span></span>  

<span data-ttu-id="39c21-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="39c21-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39c21-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="39c21-109">Attributes</span></span>  

<span data-ttu-id="39c21-110">Žádné.</span><span class="sxs-lookup"><span data-stu-id="39c21-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="39c21-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="39c21-111">Child Elements</span></span>  
  
|<span data-ttu-id="39c21-112">Element</span><span class="sxs-lookup"><span data-stu-id="39c21-112">Element</span></span>|<span data-ttu-id="39c21-113">Popis</span><span class="sxs-lookup"><span data-stu-id="39c21-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39c21-114">\<aplikacePool></span><span class="sxs-lookup"><span data-stu-id="39c21-114">\<applicationPool></span></span>](applicationpool-element-web-settings.md)|<span data-ttu-id="39c21-115">Určuje nastavení konfigurace fondů aplikací služby IIS v souboru aspnet.config.</span><span class="sxs-lookup"><span data-stu-id="39c21-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39c21-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="39c21-116">Parent Elements</span></span>  
  
|<span data-ttu-id="39c21-117">Element</span><span class="sxs-lookup"><span data-stu-id="39c21-117">Element</span></span>|<span data-ttu-id="39c21-118">Popis</span><span class="sxs-lookup"><span data-stu-id="39c21-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39c21-119">\<>konfigurace</span><span class="sxs-lookup"><span data-stu-id="39c21-119">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="39c21-120">Určuje kořenový prvek v každém konfiguračním souboru, který používá aplikace COMMON Language runtime a .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="39c21-120">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39c21-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="39c21-121">Remarks</span></span>  

<span data-ttu-id="39c21-122">Prvek `system.web` a jeho `applicationPool` podřízený prvek byly přidány do rozhraní .NET Framework od rozhraní .NET Framework 3.5 SP1.</span><span class="sxs-lookup"><span data-stu-id="39c21-122">The `system.web` element and its child `applicationPool` element were added to the .NET Framework as of .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="39c21-123">Při spuštění služby IIS 7.0 nebo novějších verzí v integrovaném režimu umožňuje tato kombinace prvků konfigurovat způsob správy vláken ASP.NET a způsob, jakým zařazuje požadavky do fronty, když je ASP.NET hostován ve fondu aplikací služby IIS.</span><span class="sxs-lookup"><span data-stu-id="39c21-123">When you run IIS 7.0 or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="39c21-124">Pokud spustíte službu IIS 7.0 nebo novější verze v klasickém režimu nebo režimu ISAPI, budou tato nastavení ignorována.</span><span class="sxs-lookup"><span data-stu-id="39c21-124">If you run IIS 7.0 or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39c21-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="39c21-125">Example</span></span>  

<span data-ttu-id="39c21-126">Následující příklad ukazuje, jak nakonfigurovat ASP.NET chování celého procesu v souboru aspnet.config, když je ASP.NET hostováno ve fondu aplikací služby IIS.</span><span class="sxs-lookup"><span data-stu-id="39c21-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="39c21-127">Příklad předpokládá, že službu IIS je spuštěna v integrovaném režimu a že aplikace používá rozhraní .NET Framework 3.5 SP1 nebo novější verzi.</span><span class="sxs-lookup"><span data-stu-id="39c21-127">The example assumes that IIS is running in Integrated mode and that the application is using the .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="39c21-128">K tomuto chování nedochází ve verzích rozhraní .NET Framework starších než rozhraní .NET Framework 3.5 SP1.</span><span class="sxs-lookup"><span data-stu-id="39c21-128">This behavior does not occur in versions of the .NET Framework earlier than the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="39c21-129">Hodnoty v příkladu jsou výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="39c21-129">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="39c21-130">Informace o elementu</span><span class="sxs-lookup"><span data-stu-id="39c21-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="39c21-131">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="39c21-131">Namespace</span></span>||  
|<span data-ttu-id="39c21-132">Název schématu</span><span class="sxs-lookup"><span data-stu-id="39c21-132">Schema Name</span></span>||  
|<span data-ttu-id="39c21-133">Ověřovací soubor</span><span class="sxs-lookup"><span data-stu-id="39c21-133">Validation File</span></span>||  
|<span data-ttu-id="39c21-134">Může být prázdný</span><span class="sxs-lookup"><span data-stu-id="39c21-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="39c21-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="39c21-135">See also</span></span>

- [<span data-ttu-id="39c21-136">\<applicationPool> Element (Nastavení webu)</span><span class="sxs-lookup"><span data-stu-id="39c21-136">\<applicationPool> Element (Web Settings)</span></span>](applicationpool-element-web-settings.md)
