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
ms.openlocfilehash: 6144bcbda69b2ba799e87c3e7fa2118fbe4d9bf6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673730"
---
# <a name="performancecounters-element"></a><span data-ttu-id="4bf62-102">\<čítače výkonu > – Element</span><span class="sxs-lookup"><span data-stu-id="4bf62-102">\<performanceCounters> Element</span></span>

<span data-ttu-id="4bf62-103">Určuje velikost globální paměť sdílenou čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="4bf62-103">Specifies the size of the global memory shared by performance counters.</span></span>

 <span data-ttu-id="4bf62-104">\<Konfigurace > \\</span><span class="sxs-lookup"><span data-stu-id="4bf62-104">\<configuration>\\</span></span>
<span data-ttu-id="4bf62-105">\<system.diagnostics>\\</span><span class="sxs-lookup"><span data-stu-id="4bf62-105">\<system.diagnostics>\\</span></span>
<span data-ttu-id="4bf62-106">\<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="4bf62-106">\<performanceCounters></span></span>

## <a name="syntax"></a><span data-ttu-id="4bf62-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4bf62-107">Syntax</span></span>

```xml
<performanceCounters filemappingsize="524288" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4bf62-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4bf62-108">Attributes and Elements</span></span>

<span data-ttu-id="4bf62-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4bf62-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4bf62-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="4bf62-110">Attributes</span></span>

|<span data-ttu-id="4bf62-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="4bf62-111">Attribute</span></span>|<span data-ttu-id="4bf62-112">Popis</span><span class="sxs-lookup"><span data-stu-id="4bf62-112">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="4bf62-113">filemappingsize</span><span class="sxs-lookup"><span data-stu-id="4bf62-113">filemappingsize</span></span>|<span data-ttu-id="4bf62-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="4bf62-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="4bf62-115">Určuje velikost v bajtech, globální paměti sdílí čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="4bf62-115">Specifies the size, in bytes, of the global memory shared by performance counters.</span></span> <span data-ttu-id="4bf62-116">Výchozí hodnota je 524288.</span><span class="sxs-lookup"><span data-stu-id="4bf62-116">The default is 524288.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="4bf62-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4bf62-117">Child Elements</span></span>

<span data-ttu-id="4bf62-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="4bf62-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4bf62-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4bf62-119">Parent Elements</span></span>

|<span data-ttu-id="4bf62-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="4bf62-120">Element</span></span>|<span data-ttu-id="4bf62-121">Popis</span><span class="sxs-lookup"><span data-stu-id="4bf62-121">Description</span></span>|
|-------------|-----------------|
|`Configuration`|<span data-ttu-id="4bf62-122">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4bf62-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`system.diagnostics`|<span data-ttu-id="4bf62-123">Určuje kořenový element části o konfiguraci technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4bf62-123">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4bf62-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4bf62-124">Remarks</span></span>

<span data-ttu-id="4bf62-125">Čítače výkonu pomocí souboru mapování paměti nebo sdílené paměti k vydávání dat výkonu.</span><span class="sxs-lookup"><span data-stu-id="4bf62-125">Performance counters use a memory mapped file, or shared memory, to publish performance data.</span></span>  <span data-ttu-id="4bf62-126">Velikost sdílené paměti určuje, kolik instancí je možné najednou.</span><span class="sxs-lookup"><span data-stu-id="4bf62-126">The size of the shared memory determines how many instances can be used at once.</span></span>  <span data-ttu-id="4bf62-127">Existují dva typy sdílené paměti: globální sdílené paměti a samostatné sdílené paměti.</span><span class="sxs-lookup"><span data-stu-id="4bf62-127">There are two types of shared memory: global shared memory and separate shared memory.</span></span>  <span data-ttu-id="4bf62-128">Všechny kategorie čítačů výkonu nainstalovaný v rozhraní .NET Framework verze 1.0 nebo 1.1 používá globální sdílenou paměť.</span><span class="sxs-lookup"><span data-stu-id="4bf62-128">The global shared memory is used by all performance counter categories installed with the .NET Framework versions 1.0 or 1.1.</span></span>  <span data-ttu-id="4bf62-129">Kategorie čítače výkonu nainstalovaná s použitím rozhraní .NET Framework verze 2.0 pomocí samostatné sdílené paměti, s každou kategorii čítače výkonu má svůj vlastní paměti.</span><span class="sxs-lookup"><span data-stu-id="4bf62-129">Performance counter categories installed with the .NET Framework version 2.0 use separate shared memory, with each performance counter category having its own memory.</span></span>

<span data-ttu-id="4bf62-130">Velikost globální sdílené paměti lze nastavit pouze s konfiguračním souborem.</span><span class="sxs-lookup"><span data-stu-id="4bf62-130">The size of global shared memory can be set only with a configuration file.</span></span>  <span data-ttu-id="4bf62-131">Výchozí velikost je 524,288 kolik, maximální velikost je 33,554,432 bajtů a minimální velikost je 32 768 bajtů.</span><span class="sxs-lookup"><span data-stu-id="4bf62-131">The default size is 524,288 byes, the maximum size is 33,554,432 bytes, and the minimum size is 32,768 bytes.</span></span>  <span data-ttu-id="4bf62-132">Protože globální sdílené paměti se sdílí všemi procesy a kategorií, určuje první Tvůrce velikost.</span><span class="sxs-lookup"><span data-stu-id="4bf62-132">Since the global shared memory is shared by all processes and categories, the first creator specifies the size.</span></span>  <span data-ttu-id="4bf62-133">Při definování velikost v konfiguračním souboru aplikace, tato velikost se používá pouze pokud je první aplikaci, která způsobí, že čítače výkonu ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="4bf62-133">If you define the size in your application configuration file, that size is only used if your application is the first application that causes the performance counters to execute.</span></span>  <span data-ttu-id="4bf62-134">Proto do správného umístění k určení `filemappingsize` hodnota je soubor Machine.config.</span><span class="sxs-lookup"><span data-stu-id="4bf62-134">Therefore the correct location to specify the `filemappingsize` value is the Machine.config file.</span></span>  <span data-ttu-id="4bf62-135">Nelze uvolnit paměť v globální sdílené paměti podle jednotlivých čítače, takže nakonec vyčerpá globální sdílené paměti, pokud se vytvoří velký počet instancí čítače výkonu s různými názvy.</span><span class="sxs-lookup"><span data-stu-id="4bf62-135">Memory in the global shared memory cannot be released by individual performance counters, so eventually global shared memory is exhausted if a large number of performance counter instances with different names are created.</span></span>

<span data-ttu-id="4bf62-136">Pro velikost samostatné sdílené paměti hodnotu DWORD FileMappingSize v registru klíč HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<název kategorie >* \Performance odkazuje nejprve za nímž následuje hodnota zadaná pro globální sdílené paměti v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="4bf62-136">For the size of separate shared memory, the DWORD FileMappingSize value in the registry key HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<category name>* \Performance is referenced first, followed by the value specified for the global shared memory in the configuration file.</span></span> <span data-ttu-id="4bf62-137">Pokud hodnota FileMappingSize neexistuje, je velikost samostatné sdílené paměti je nastavena na čtvrté jeden (1/4) globální nastavení v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="4bf62-137">If the FileMappingSize value does not exist, then the separate shared memory size is set to one fourth (1/4) the global setting in the configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="4bf62-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4bf62-138">See also</span></span>

- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
