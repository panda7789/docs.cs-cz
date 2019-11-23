---
title: Element <performanceCounters>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <performanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
ms.openlocfilehash: f52fdb2d5b0b7911de63f96663e70735d2f2496c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697158"
---
# <a name="performancecounters-element"></a><span data-ttu-id="3b9ce-102">\<element > čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="3b9ce-102">\<performanceCounters> Element</span></span>

<span data-ttu-id="3b9ce-103">Určuje velikost globální paměti sdílené čítači výkonu.</span><span class="sxs-lookup"><span data-stu-id="3b9ce-103">Specifies the size of the global memory shared by performance counters.</span></span>

[<span data-ttu-id="3b9ce-104">**Konfigurace \<>** </span><span class="sxs-lookup"><span data-stu-id="3b9ce-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="3b9ce-105">&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="3b9ce-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="3b9ce-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<čítače výkonu >**</span><span class="sxs-lookup"><span data-stu-id="3b9ce-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="3b9ce-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b9ce-107">Syntax</span></span>

```xml
<performanceCounters filemappingsize="524288" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3b9ce-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3b9ce-108">Attributes and Elements</span></span>

<span data-ttu-id="3b9ce-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3b9ce-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3b9ce-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="3b9ce-110">Attributes</span></span>

|<span data-ttu-id="3b9ce-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="3b9ce-111">Attribute</span></span>|<span data-ttu-id="3b9ce-112">Popis</span><span class="sxs-lookup"><span data-stu-id="3b9ce-112">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="3b9ce-113">filemappingsize</span><span class="sxs-lookup"><span data-stu-id="3b9ce-113">filemappingsize</span></span>|<span data-ttu-id="3b9ce-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="3b9ce-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="3b9ce-115">Určuje velikost globální paměti sdílené čítači výkonu (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="3b9ce-115">Specifies the size, in bytes, of the global memory shared by performance counters.</span></span> <span data-ttu-id="3b9ce-116">Výchozí hodnota je 524288.</span><span class="sxs-lookup"><span data-stu-id="3b9ce-116">The default is 524288.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="3b9ce-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3b9ce-117">Child Elements</span></span>

<span data-ttu-id="3b9ce-118">Žádné.</span><span class="sxs-lookup"><span data-stu-id="3b9ce-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3b9ce-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3b9ce-119">Parent Elements</span></span>

|<span data-ttu-id="3b9ce-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="3b9ce-120">Element</span></span>|<span data-ttu-id="3b9ce-121">Popis</span><span class="sxs-lookup"><span data-stu-id="3b9ce-121">Description</span></span>|
|-------------|-----------------|
|`Configuration`|<span data-ttu-id="3b9ce-122">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3b9ce-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`system.diagnostics`|<span data-ttu-id="3b9ce-123">Určuje kořenový element konfiguračního oddílu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3b9ce-123">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3b9ce-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3b9ce-124">Remarks</span></span>

<span data-ttu-id="3b9ce-125">Čítače výkonu k publikování údajů o výkonu používají soubor mapované paměti nebo sdílenou paměť.</span><span class="sxs-lookup"><span data-stu-id="3b9ce-125">Performance counters use a memory mapped file, or shared memory, to publish performance data.</span></span>  <span data-ttu-id="3b9ce-126">Velikost sdílené paměti určuje, kolik instancí lze najednou použít.</span><span class="sxs-lookup"><span data-stu-id="3b9ce-126">The size of the shared memory determines how many instances can be used at once.</span></span>  <span data-ttu-id="3b9ce-127">Existují dva typy sdílené paměti: globální sdílená paměť a samostatná sdílená paměť.</span><span class="sxs-lookup"><span data-stu-id="3b9ce-127">There are two types of shared memory: global shared memory and separate shared memory.</span></span>  <span data-ttu-id="3b9ce-128">Globální sdílená paměť je používána všemi kategoriemi čítače výkonu nainstalovanými s verzemi .NET Framework 1,0 nebo 1,1.</span><span class="sxs-lookup"><span data-stu-id="3b9ce-128">The global shared memory is used by all performance counter categories installed with the .NET Framework versions 1.0 or 1.1.</span></span>  <span data-ttu-id="3b9ce-129">Kategorie čítače výkonu nainstalované s .NET Framework verze 2,0 používají samostatnou sdílenou paměť, přičemž každá kategorie čítače výkonu má vlastní paměť.</span><span class="sxs-lookup"><span data-stu-id="3b9ce-129">Performance counter categories installed with the .NET Framework version 2.0 use separate shared memory, with each performance counter category having its own memory.</span></span>

<span data-ttu-id="3b9ce-130">Velikost globální sdílené paměti lze nastavit pouze pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="3b9ce-130">The size of global shared memory can be set only with a configuration file.</span></span>  <span data-ttu-id="3b9ce-131">Výchozí velikost je 524 288 byes, maximální velikost je 33 554 432 bajtů a minimální velikost je 32 768 bajtů.</span><span class="sxs-lookup"><span data-stu-id="3b9ce-131">The default size is 524,288 byes, the maximum size is 33,554,432 bytes, and the minimum size is 32,768 bytes.</span></span>  <span data-ttu-id="3b9ce-132">Vzhledem k tomu, že globální sdílená paměť je sdílena všemi procesy a kategorie, první tvůrce určuje velikost.</span><span class="sxs-lookup"><span data-stu-id="3b9ce-132">Since the global shared memory is shared by all processes and categories, the first creator specifies the size.</span></span>  <span data-ttu-id="3b9ce-133">Pokud definujete velikost v konfiguračním souboru aplikace, bude tato velikost použita pouze v případě, že je vaše aplikace první aplikací, která způsobuje, že jsou čítače výkonu provedeny.</span><span class="sxs-lookup"><span data-stu-id="3b9ce-133">If you define the size in your application configuration file, that size is only used if your application is the first application that causes the performance counters to execute.</span></span>  <span data-ttu-id="3b9ce-134">Proto je správné umístění pro určení `filemappingsize` hodnotu soubor Machine. config.</span><span class="sxs-lookup"><span data-stu-id="3b9ce-134">Therefore the correct location to specify the `filemappingsize` value is the Machine.config file.</span></span>  <span data-ttu-id="3b9ce-135">Paměť v globální sdílené paměti nemůže být uvolněna jednotlivými čítači výkonu, takže je nakonec vyčerpána globální sdílená paměť, pokud je vytvořen velký počet instancí čítače výkonu s různými názvy.</span><span class="sxs-lookup"><span data-stu-id="3b9ce-135">Memory in the global shared memory cannot be released by individual performance counters, so eventually global shared memory is exhausted if a large number of performance counter instances with different names are created.</span></span>

<span data-ttu-id="3b9ce-136">V případě velikosti samostatné sdílené paměti je hodnota DWORD FileMappingSize v klíči registru HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services\\ *\<název kategorie >* nejprve odkaz na \Performance, následovaný hodnotou zadanou pro globální sdílenou paměť v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="3b9ce-136">For the size of separate shared memory, the DWORD FileMappingSize value in the registry key HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<category name>* \Performance is referenced first, followed by the value specified for the global shared memory in the configuration file.</span></span> <span data-ttu-id="3b9ce-137">Pokud hodnota FileMappingSize neexistuje, je velikost samostatné sdílené paměti nastavena na jednu čtvrtou (1/4) globální nastavení konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="3b9ce-137">If the FileMappingSize value does not exist, then the separate shared memory size is set to one fourth (1/4) the global setting in the configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b9ce-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b9ce-138">See also</span></span>

- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
