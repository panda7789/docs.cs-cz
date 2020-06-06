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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152838"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="3d6e2-102">Element \<system.web> (nastavení webu)</span><span class="sxs-lookup"><span data-stu-id="3d6e2-102">\<system.web> Element (Web Settings)</span></span>
<span data-ttu-id="3d6e2-103">Obsahuje informace o tom, jak vrstva hostování ASP.NET spravuje chování v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="3d6e2-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.web>**  
  
## <a name="syntax"></a><span data-ttu-id="3d6e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d6e2-104">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d6e2-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3d6e2-105">Attributes and Elements</span></span>  

<span data-ttu-id="3d6e2-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3d6e2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d6e2-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="3d6e2-107">Attributes</span></span>  

<span data-ttu-id="3d6e2-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="3d6e2-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3d6e2-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3d6e2-109">Child Elements</span></span>  
  
|<span data-ttu-id="3d6e2-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="3d6e2-110">Element</span></span>|<span data-ttu-id="3d6e2-111">Description</span><span class="sxs-lookup"><span data-stu-id="3d6e2-111">Description</span></span>|  
|-------------|-----------------|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|<span data-ttu-id="3d6e2-112">Určuje nastavení konfigurace pro fondy aplikací služby IIS v souboru ASPNET. config.</span><span class="sxs-lookup"><span data-stu-id="3d6e2-112">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3d6e2-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3d6e2-113">Parent Elements</span></span>  
  
|<span data-ttu-id="3d6e2-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="3d6e2-114">Element</span></span>|<span data-ttu-id="3d6e2-115">Description</span><span class="sxs-lookup"><span data-stu-id="3d6e2-115">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="3d6e2-116">Určuje kořenový element v každém konfiguračním souboru, který je používán modulem CLR (Common Language Runtime) a .NET Framework aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="3d6e2-116">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d6e2-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3d6e2-117">Remarks</span></span>  

<span data-ttu-id="3d6e2-118">`system.web`Prvek a jeho podřízený `applicationPool` prvek byly přidány do .NET Framework v .NET Framework 3,5 SP1.</span><span class="sxs-lookup"><span data-stu-id="3d6e2-118">The `system.web` element and its child `applicationPool` element were added to the .NET Framework as of .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="3d6e2-119">Když spustíte službu IIS 7,0 nebo novější verze v integrovaném režimu, tato kombinace prvků vám umožní nakonfigurovat, jak ASP.NET spravuje vlákna a jak se budou požadavky do fronty ASP.NET hostovat v fondu aplikací služby IIS.</span><span class="sxs-lookup"><span data-stu-id="3d6e2-119">When you run IIS 7.0 or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="3d6e2-120">Pokud v klasickém režimu nebo v režimu rozhraní ISAPI spustíte službu IIS 7,0 nebo novější, budou tato nastavení ignorována.</span><span class="sxs-lookup"><span data-stu-id="3d6e2-120">If you run IIS 7.0 or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d6e2-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="3d6e2-121">Example</span></span>  

<span data-ttu-id="3d6e2-122">Následující příklad ukazuje, jak nakonfigurovat ASP.NET chování v rámci procesu v souboru ASPNET. config při hostování ASP.NET ve fondu aplikací služby IIS.</span><span class="sxs-lookup"><span data-stu-id="3d6e2-122">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="3d6e2-123">V příkladu se předpokládá, že služba IIS běží v integrovaném režimu a že aplikace používá .NET Framework 3,5 SP1 nebo novější verzi.</span><span class="sxs-lookup"><span data-stu-id="3d6e2-123">The example assumes that IIS is running in Integrated mode and that the application is using the .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="3d6e2-124">K tomuto chování nedochází ve verzích .NET Framework starších než .NET Framework 3,5 SP1.</span><span class="sxs-lookup"><span data-stu-id="3d6e2-124">This behavior does not occur in versions of the .NET Framework earlier than the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="3d6e2-125">Hodnoty v příkladu jsou výchozími hodnotami.</span><span class="sxs-lookup"><span data-stu-id="3d6e2-125">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="3d6e2-126">Informace o elementu</span><span class="sxs-lookup"><span data-stu-id="3d6e2-126">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3d6e2-127">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="3d6e2-127">Namespace</span></span>||  
|<span data-ttu-id="3d6e2-128">Název schématu</span><span class="sxs-lookup"><span data-stu-id="3d6e2-128">Schema Name</span></span>||  
|<span data-ttu-id="3d6e2-129">Soubor ověření</span><span class="sxs-lookup"><span data-stu-id="3d6e2-129">Validation File</span></span>||  
|<span data-ttu-id="3d6e2-130">Může být prázdné</span><span class="sxs-lookup"><span data-stu-id="3d6e2-130">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="3d6e2-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d6e2-131">See also</span></span>

- [<span data-ttu-id="3d6e2-132">\<applicationPool>– Element (nastavení webu)</span><span class="sxs-lookup"><span data-stu-id="3d6e2-132">\<applicationPool> Element (Web Settings)</span></span>](applicationpool-element-web-settings.md)
