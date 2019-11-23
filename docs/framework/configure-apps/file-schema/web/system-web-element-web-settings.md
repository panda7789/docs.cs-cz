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
ms.openlocfilehash: 5c5c857d4494b6d78b819e56bae4213abc5e2035
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699095"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="206e3-102">\<element System. Web > (nastavení webu)</span><span class="sxs-lookup"><span data-stu-id="206e3-102">\<system.web> Element (Web Settings)</span></span>
<span data-ttu-id="206e3-103">Obsahuje informace o tom, jak vrstva hostování ASP.NET spravuje chování v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="206e3-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
[<span data-ttu-id="206e3-104">**Konfigurace \<>** </span><span class="sxs-lookup"><span data-stu-id="206e3-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="206e3-105">&nbsp;&nbsp; **\<System. web >**</span><span class="sxs-lookup"><span data-stu-id="206e3-105">&nbsp;&nbsp;**\<system.web>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="206e3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="206e3-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="206e3-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="206e3-107">Attributes and Elements</span></span>  

<span data-ttu-id="206e3-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="206e3-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="206e3-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="206e3-109">Attributes</span></span>  

<span data-ttu-id="206e3-110">Žádné.</span><span class="sxs-lookup"><span data-stu-id="206e3-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="206e3-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="206e3-111">Child Elements</span></span>  
  
|<span data-ttu-id="206e3-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="206e3-112">Element</span></span>|<span data-ttu-id="206e3-113">Popis</span><span class="sxs-lookup"><span data-stu-id="206e3-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="206e3-114">\<applicationPool></span><span class="sxs-lookup"><span data-stu-id="206e3-114">\<applicationPool></span></span>](applicationpool-element-web-settings.md)|<span data-ttu-id="206e3-115">Určuje nastavení konfigurace pro fondy aplikací služby IIS v souboru ASPNET. config.</span><span class="sxs-lookup"><span data-stu-id="206e3-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="206e3-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="206e3-116">Parent Elements</span></span>  
  
|<span data-ttu-id="206e3-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="206e3-117">Element</span></span>|<span data-ttu-id="206e3-118">Popis</span><span class="sxs-lookup"><span data-stu-id="206e3-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="206e3-119">Konfigurace \<></span><span class="sxs-lookup"><span data-stu-id="206e3-119">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="206e3-120">Určuje kořenový element v každém konfiguračním souboru, který je používán modulem CLR (Common Language Runtime) a .NET Framework aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="206e3-120">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="206e3-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="206e3-121">Remarks</span></span>  

<span data-ttu-id="206e3-122">Prvek `system.web` a jeho podřízený `applicationPool` prvek byl přidán do .NET Framework jako .NET Framework 3,5 SP1.</span><span class="sxs-lookup"><span data-stu-id="206e3-122">The `system.web` element and its child `applicationPool` element were added to the .NET Framework as of .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="206e3-123">Když spustíte službu IIS 7,0 nebo novější verze v integrovaném režimu, tato kombinace prvků vám umožní nakonfigurovat, jak ASP.NET spravuje vlákna a jak se budou požadavky do fronty ASP.NET hostovat v fondu aplikací služby IIS.</span><span class="sxs-lookup"><span data-stu-id="206e3-123">When you run IIS 7.0 or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="206e3-124">Pokud v klasickém režimu nebo v režimu rozhraní ISAPI spustíte službu IIS 7,0 nebo novější, budou tato nastavení ignorována.</span><span class="sxs-lookup"><span data-stu-id="206e3-124">If you run IIS 7.0 or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="206e3-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="206e3-125">Example</span></span>  

<span data-ttu-id="206e3-126">Následující příklad ukazuje, jak nakonfigurovat ASP.NET chování v rámci procesu v souboru ASPNET. config při hostování ASP.NET ve fondu aplikací služby IIS.</span><span class="sxs-lookup"><span data-stu-id="206e3-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="206e3-127">V příkladu se předpokládá, že služba IIS běží v integrovaném režimu a že aplikace používá .NET Framework 3,5 SP1 nebo novější verzi.</span><span class="sxs-lookup"><span data-stu-id="206e3-127">The example assumes that IIS is running in Integrated mode and that the application is using the .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="206e3-128">K tomuto chování nedochází ve verzích .NET Framework starších než .NET Framework 3,5 SP1.</span><span class="sxs-lookup"><span data-stu-id="206e3-128">This behavior does not occur in versions of the .NET Framework earlier than the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="206e3-129">Hodnoty v příkladu jsou výchozími hodnotami.</span><span class="sxs-lookup"><span data-stu-id="206e3-129">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="206e3-130">Informace o elementu</span><span class="sxs-lookup"><span data-stu-id="206e3-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="206e3-131">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="206e3-131">Namespace</span></span>||  
|<span data-ttu-id="206e3-132">Název schématu</span><span class="sxs-lookup"><span data-stu-id="206e3-132">Schema Name</span></span>||  
|<span data-ttu-id="206e3-133">Soubor ověření</span><span class="sxs-lookup"><span data-stu-id="206e3-133">Validation File</span></span>||  
|<span data-ttu-id="206e3-134">Může být prázdné</span><span class="sxs-lookup"><span data-stu-id="206e3-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="206e3-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="206e3-135">See also</span></span>

- [<span data-ttu-id="206e3-136">\<applicationPool > – element (nastavení webu)</span><span class="sxs-lookup"><span data-stu-id="206e3-136">\<applicationPool> Element (Web Settings)</span></span>](applicationpool-element-web-settings.md)
