---
title: "&lt;čítače výkonu&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <perfomanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 64afd62c6eeca7bce14e331fdc65fccfa3d02bce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltperformancecountersgt-element"></a><span data-ttu-id="a4a73-102">&lt;čítače výkonu&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="a4a73-102">&lt;performanceCounters&gt; Element</span></span>
<span data-ttu-id="a4a73-103">Určuje velikost globální paměť sdíleny čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="a4a73-103">Specifies the size of the global memory shared by performance counters.</span></span>  
  
 <span data-ttu-id="a4a73-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="a4a73-104">\<configuration></span></span>  
<span data-ttu-id="a4a73-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="a4a73-105">\<system.diagnostics></span></span>  
<span data-ttu-id="a4a73-106">\<čítače výkonu ></span><span class="sxs-lookup"><span data-stu-id="a4a73-106">\<performanceCounters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4a73-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4a73-107">Syntax</span></span>  
  
```xml  
<performanceCounters filemappingsize="524288" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4a73-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a4a73-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a4a73-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a4a73-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4a73-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="a4a73-110">Attributes</span></span>  
  
|<span data-ttu-id="a4a73-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="a4a73-111">Attribute</span></span>|<span data-ttu-id="a4a73-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a4a73-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a4a73-113">filemappingsize</span><span class="sxs-lookup"><span data-stu-id="a4a73-113">filemappingsize</span></span>|<span data-ttu-id="a4a73-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="a4a73-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="a4a73-115">Určuje velikost v bajtech globální paměť sdíleny čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="a4a73-115">Specifies the size, in bytes, of the global memory shared by performance counters.</span></span> <span data-ttu-id="a4a73-116">Výchozí hodnota je 524288.</span><span class="sxs-lookup"><span data-stu-id="a4a73-116">The default is 524288.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4a73-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a4a73-117">Child Elements</span></span>  
 <span data-ttu-id="a4a73-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="a4a73-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a4a73-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a4a73-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a4a73-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="a4a73-120">Element</span></span>|<span data-ttu-id="a4a73-121">Popis</span><span class="sxs-lookup"><span data-stu-id="a4a73-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="a4a73-122">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a4a73-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="a4a73-123">Určuje kořenový element pro konfigurační oddíl technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a4a73-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4a73-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4a73-124">Remarks</span></span>  
 <span data-ttu-id="a4a73-125">Čítače výkonu pomocí souboru mapované paměti nebo sdílené paměti, k vydávání dat výkonu.</span><span class="sxs-lookup"><span data-stu-id="a4a73-125">Performance counters use a memory mapped file, or shared memory, to publish performance data.</span></span>  <span data-ttu-id="a4a73-126">Velikost sdílené paměti určuje, kolik instancí lze najednou.</span><span class="sxs-lookup"><span data-stu-id="a4a73-126">The size of the shared memory determines how many instances can be used at once.</span></span>  <span data-ttu-id="a4a73-127">Existují dva typy sdílené paměti: globální sdílené paměti a samostatné sdílené paměti.</span><span class="sxs-lookup"><span data-stu-id="a4a73-127">There are two types of shared memory: global shared memory and separate shared memory.</span></span>  <span data-ttu-id="a4a73-128">Všechny kategorie čítače výkonu nainstalované rozhraní .NET Framework verze 1.0 nebo 1.1 používá globální sdílené paměti.</span><span class="sxs-lookup"><span data-stu-id="a4a73-128">The global shared memory is used by all performance counter categories installed with the .NET Framework versions 1.0 or 1.1.</span></span>  <span data-ttu-id="a4a73-129">Kategorie čítače výkonu nainstalované s rozhraním .NET Framework verze 2.0 pomocí každé kategorie čítače výkonu má svou vlastní paměti samostatné sdílené paměti.</span><span class="sxs-lookup"><span data-stu-id="a4a73-129">Performance counter categories installed with the .NET Framework version 2.0 use separate shared memory, with each performance counter category having its own memory.</span></span>  
  
 <span data-ttu-id="a4a73-130">Velikost globální sdílené paměti lze nastavit pouze s konfiguračním souborem.</span><span class="sxs-lookup"><span data-stu-id="a4a73-130">The size of global shared memory can be set only with a configuration file.</span></span>  <span data-ttu-id="a4a73-131">Výchozí velikost je kolik se 524,288, maximální velikost je 33,554,432 bajtů a minimální velikost je 32 768 bajtů.</span><span class="sxs-lookup"><span data-stu-id="a4a73-131">The default size is 524,288 byes, the maximum size is 33,554,432 bytes, and the minimum size is 32,768 bytes.</span></span>  <span data-ttu-id="a4a73-132">Vzhledem k tomu, že globální sdílené paměti sdílí všechny procesy a kategorií, určuje první creator velikost.</span><span class="sxs-lookup"><span data-stu-id="a4a73-132">Since the global shared memory is shared by all processes and categories, the first creator specifies the size.</span></span>  <span data-ttu-id="a4a73-133">Pokud definujete velikost v konfiguračním souboru aplikace, této velikosti se používá pouze pokud je první aplikaci, která způsobuje čítače výkonu pro spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="a4a73-133">If you define the size in your application configuration file, that size is only used if your application is the first application that causes the performance counters to execute.</span></span>  <span data-ttu-id="a4a73-134">Proto na správné místo k určení `filemappingsize` hodnota je souboru Machine.config.</span><span class="sxs-lookup"><span data-stu-id="a4a73-134">Therefore the correct location to specify the `filemappingsize` value is the Machine.config file.</span></span>  <span data-ttu-id="a4a73-135">Nelze uvolnit paměti v globální sdílené paměti podle jednotlivé čítače, takže nakonec vyčerpá globální sdílené paměti. Pokud jsou vytvořené velký počet instancí čítače výkonu s různými názvy.</span><span class="sxs-lookup"><span data-stu-id="a4a73-135">Memory in the global shared memory cannot be released by individual performance counters, so eventually global shared memory is exhausted if a large number of performance counter instances with different names are created.</span></span>  
  
 <span data-ttu-id="a4a73-136">Pro velikost samostatné sdílené paměti, klíče v registru hodnotu DWORD FileMappingSize HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<název kategorie >*\Performance odkazuje nejprve následovaný hodnota zadaná pro globální sdílené paměti v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="a4a73-136">For the size of separate shared memory, the DWORD FileMappingSize value in the registry key HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<category name>*\Performance is referenced first, followed by the value specified for the global shared memory in the configuration file.</span></span> <span data-ttu-id="a4a73-137">Pokud hodnota FileMappingSize neexistuje, pak velikost samostatné sdílené paměti je nastavena na čtvrtý jedna (1/4) globální nastavení v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="a4a73-137">If the FileMappingSize value does not exist, then the separate shared memory size is set to one fourth (1/4) the global setting in the configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4a73-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4a73-138">See Also</span></span>  
 <xref:System.Diagnostics.PerformanceCounter>  
 <xref:System.Diagnostics.PerformanceCounterCategory>  
 <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>  
 <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
