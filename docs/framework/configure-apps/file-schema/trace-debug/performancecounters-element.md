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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697158"
---
# <a name="performancecounters-element"></a><span data-ttu-id="b6a28-102">Element \<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="b6a28-102">\<performanceCounters> Element</span></span>

<span data-ttu-id="b6a28-103">Určuje velikost globální paměti sdílené čítači výkonu.</span><span class="sxs-lookup"><span data-stu-id="b6a28-103">Specifies the size of the global memory shared by performance counters.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**  

## <a name="syntax"></a><span data-ttu-id="b6a28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6a28-104">Syntax</span></span>

```xml
<performanceCounters filemappingsize="524288" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b6a28-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b6a28-105">Attributes and Elements</span></span>

<span data-ttu-id="b6a28-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b6a28-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b6a28-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="b6a28-107">Attributes</span></span>

|<span data-ttu-id="b6a28-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="b6a28-108">Attribute</span></span>|<span data-ttu-id="b6a28-109">Popis</span><span class="sxs-lookup"><span data-stu-id="b6a28-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="b6a28-110">filemappingsize</span><span class="sxs-lookup"><span data-stu-id="b6a28-110">filemappingsize</span></span>|<span data-ttu-id="b6a28-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="b6a28-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="b6a28-112">Určuje velikost globální paměti sdílené čítači výkonu (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="b6a28-112">Specifies the size, in bytes, of the global memory shared by performance counters.</span></span> <span data-ttu-id="b6a28-113">Výchozí hodnota je 524288.</span><span class="sxs-lookup"><span data-stu-id="b6a28-113">The default is 524288.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="b6a28-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b6a28-114">Child Elements</span></span>

<span data-ttu-id="b6a28-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="b6a28-115">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b6a28-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b6a28-116">Parent Elements</span></span>

|<span data-ttu-id="b6a28-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="b6a28-117">Element</span></span>|<span data-ttu-id="b6a28-118">Description</span><span class="sxs-lookup"><span data-stu-id="b6a28-118">Description</span></span>|
|-------------|-----------------|
|`Configuration`|<span data-ttu-id="b6a28-119">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b6a28-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`system.diagnostics`|<span data-ttu-id="b6a28-120">Určuje kořenový element konfiguračního oddílu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b6a28-120">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b6a28-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b6a28-121">Remarks</span></span>

<span data-ttu-id="b6a28-122">Čítače výkonu k publikování údajů o výkonu používají soubor mapované paměti nebo sdílenou paměť.</span><span class="sxs-lookup"><span data-stu-id="b6a28-122">Performance counters use a memory mapped file, or shared memory, to publish performance data.</span></span>  <span data-ttu-id="b6a28-123">Velikost sdílené paměti určuje, kolik instancí lze najednou použít.</span><span class="sxs-lookup"><span data-stu-id="b6a28-123">The size of the shared memory determines how many instances can be used at once.</span></span>  <span data-ttu-id="b6a28-124">Existují dva typy sdílené paměti: globální sdílená paměť a samostatná sdílená paměť.</span><span class="sxs-lookup"><span data-stu-id="b6a28-124">There are two types of shared memory: global shared memory and separate shared memory.</span></span>  <span data-ttu-id="b6a28-125">Globální sdílená paměť je používána všemi kategoriemi čítače výkonu nainstalovanými s verzemi .NET Framework 1,0 nebo 1,1.</span><span class="sxs-lookup"><span data-stu-id="b6a28-125">The global shared memory is used by all performance counter categories installed with the .NET Framework versions 1.0 or 1.1.</span></span>  <span data-ttu-id="b6a28-126">Kategorie čítače výkonu nainstalované s .NET Framework verze 2,0 používají samostatnou sdílenou paměť, přičemž každá kategorie čítače výkonu má vlastní paměť.</span><span class="sxs-lookup"><span data-stu-id="b6a28-126">Performance counter categories installed with the .NET Framework version 2.0 use separate shared memory, with each performance counter category having its own memory.</span></span>

<span data-ttu-id="b6a28-127">Velikost globální sdílené paměti lze nastavit pouze pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="b6a28-127">The size of global shared memory can be set only with a configuration file.</span></span>  <span data-ttu-id="b6a28-128">Výchozí velikost je 524 288 byes, maximální velikost je 33 554 432 bajtů a minimální velikost je 32 768 bajtů.</span><span class="sxs-lookup"><span data-stu-id="b6a28-128">The default size is 524,288 byes, the maximum size is 33,554,432 bytes, and the minimum size is 32,768 bytes.</span></span>  <span data-ttu-id="b6a28-129">Vzhledem k tomu, že globální sdílená paměť je sdílena všemi procesy a kategorie, první tvůrce určuje velikost.</span><span class="sxs-lookup"><span data-stu-id="b6a28-129">Since the global shared memory is shared by all processes and categories, the first creator specifies the size.</span></span>  <span data-ttu-id="b6a28-130">Pokud definujete velikost v konfiguračním souboru aplikace, bude tato velikost použita pouze v případě, že je vaše aplikace první aplikací, která způsobuje, že jsou čítače výkonu provedeny.</span><span class="sxs-lookup"><span data-stu-id="b6a28-130">If you define the size in your application configuration file, that size is only used if your application is the first application that causes the performance counters to execute.</span></span>  <span data-ttu-id="b6a28-131">Proto je správné umístění pro určení `filemappingsize` hodnoty soubor Machine. config.</span><span class="sxs-lookup"><span data-stu-id="b6a28-131">Therefore the correct location to specify the `filemappingsize` value is the Machine.config file.</span></span>  <span data-ttu-id="b6a28-132">Paměť v globální sdílené paměti nemůže být uvolněna jednotlivými čítači výkonu, takže je nakonec vyčerpána globální sdílená paměť, pokud je vytvořen velký počet instancí čítače výkonu s různými názvy.</span><span class="sxs-lookup"><span data-stu-id="b6a28-132">Memory in the global shared memory cannot be released by individual performance counters, so eventually global shared memory is exhausted if a large number of performance counter instances with different names are created.</span></span>

<span data-ttu-id="b6a28-133">V případě velikosti samostatné sdílené paměti je nejprve odkazována hodnota DWORD FileMappingSize v HKEY_LOCAL_MACHINE klíči registru \\ *\<category name>* , za kterou následuje hodnota zadaná pro globální sdílenou paměť v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="b6a28-133">For the size of separate shared memory, the DWORD FileMappingSize value in the registry key HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<category name>* \Performance is referenced first, followed by the value specified for the global shared memory in the configuration file.</span></span> <span data-ttu-id="b6a28-134">Pokud hodnota FileMappingSize neexistuje, je velikost samostatné sdílené paměti nastavena na jednu čtvrtou (1/4) globální nastavení konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="b6a28-134">If the FileMappingSize value does not exist, then the separate shared memory size is set to one fourth (1/4) the global setting in the configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6a28-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="b6a28-135">See also</span></span>

- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
