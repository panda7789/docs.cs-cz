---
title: Element <ThrowUnobservedTaskExceptions>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
ms.openlocfilehash: de5a686bcbd88fc52173b488103f033575623d62
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153812"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="45cd8-102">\<Prvek> nepozorovaných úloh</span><span class="sxs-lookup"><span data-stu-id="45cd8-102">\<ThrowUnobservedTaskExceptions> Element</span></span>
<span data-ttu-id="45cd8-103">Určuje, zda mají neošetřené výjimky úloh ukončit spuštěný proces.</span><span class="sxs-lookup"><span data-stu-id="45cd8-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
<span data-ttu-id="45cd8-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="45cd8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="45cd8-105">&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="45cd8-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="45cd8-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**</span><span class="sxs-lookup"><span data-stu-id="45cd8-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45cd8-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45cd8-107">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45cd8-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="45cd8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="45cd8-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="45cd8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45cd8-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="45cd8-110">Attributes</span></span>  
  
|<span data-ttu-id="45cd8-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="45cd8-111">Attribute</span></span>|<span data-ttu-id="45cd8-112">Popis</span><span class="sxs-lookup"><span data-stu-id="45cd8-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="45cd8-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="45cd8-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="45cd8-114">Určuje, zda mají neošetřené výjimky úloh ukončit spuštěný proces.</span><span class="sxs-lookup"><span data-stu-id="45cd8-114">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="45cd8-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="45cd8-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="45cd8-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="45cd8-116">Value</span></span>|<span data-ttu-id="45cd8-117">Popis</span><span class="sxs-lookup"><span data-stu-id="45cd8-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="45cd8-118">Neukončí spuštěný proces pro výjimku neošetřené úlohy.</span><span class="sxs-lookup"><span data-stu-id="45cd8-118">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="45cd8-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="45cd8-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="45cd8-120">Ukončí spuštěný proces pro výjimku neošetřených úloh.</span><span class="sxs-lookup"><span data-stu-id="45cd8-120">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45cd8-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="45cd8-121">Child Elements</span></span>  
 <span data-ttu-id="45cd8-122">Žádné.</span><span class="sxs-lookup"><span data-stu-id="45cd8-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="45cd8-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="45cd8-123">Parent Elements</span></span>  
  
|<span data-ttu-id="45cd8-124">Element</span><span class="sxs-lookup"><span data-stu-id="45cd8-124">Element</span></span>|<span data-ttu-id="45cd8-125">Popis</span><span class="sxs-lookup"><span data-stu-id="45cd8-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="45cd8-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="45cd8-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="45cd8-127">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="45cd8-127">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="45cd8-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="45cd8-128">Remarks</span></span>  
 <span data-ttu-id="45cd8-129">Pokud nebyla dodržena <xref:System.Threading.Tasks.Task> výjimka, která je <xref:System.Threading.Tasks.Task.Wait%2A> přidružena k a, neexistuje <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> žádná operace, nadřazená možnost není připojena a vlastnost nebyla přečtena, je výjimka úkolu považována za nedodrženou.</span><span class="sxs-lookup"><span data-stu-id="45cd8-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="45cd8-130">V rozhraní .NET Framework 4 ve <xref:System.Threading.Tasks.Task> výchozím nastavení, pokud a, který má nepozorované výjimky je uvolněna, finalizační metoda vyvolá výjimku a ukončí proces.</span><span class="sxs-lookup"><span data-stu-id="45cd8-130">In the .NET Framework 4, by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="45cd8-131">Ukončení procesu je určena načasování uvolňování paměti a dokončení.</span><span class="sxs-lookup"><span data-stu-id="45cd8-131">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="45cd8-132">Chcete-li usnadnit vývojářům psát asynchronní kód na základě úkolů, rozhraní .NET Framework 4.5 změní toto výchozí chování pro nepozorované výjimky.</span><span class="sxs-lookup"><span data-stu-id="45cd8-132">To make it easier for developers to write asynchronous code based on tasks, the .NET Framework 4.5 changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="45cd8-133">Nepozorované výjimky <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> stále způsobit událost, která má být vyvolána, ale ve výchozím nastavení proces neukončí.</span><span class="sxs-lookup"><span data-stu-id="45cd8-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="45cd8-134">Místo toho je výjimka ignorována po vyvolání události, bez ohledu na to, zda obslužná rutina události dodržuje výjimku.</span><span class="sxs-lookup"><span data-stu-id="45cd8-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="45cd8-135">V rozhraní .NET Framework 4.5 můžete použít [ \<prvek> ThrowUnobservedTaskExceptions](throwunobservedtaskexceptions-element.md) v konfiguračním souboru aplikace k povolení chování rozhraní .NET Framework 4 vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="45cd8-135">In the .NET Framework 4.5, you can use the [\<ThrowUnobservedTaskExceptions> element](throwunobservedtaskexceptions-element.md) in an application configuration file to enable the .NET Framework 4 behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="45cd8-136">Chování výjimek můžete také určit jedním z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="45cd8-136">You can also specify the exception behavior in one of the following ways:</span></span>  
  
- <span data-ttu-id="45cd8-137">Nastavením proměnné `COMPlus_ThrowUnobservedTaskExceptions` prostředí`set COMPlus_ThrowUnobservedTaskExceptions=1`( ).</span><span class="sxs-lookup"><span data-stu-id="45cd8-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
- <span data-ttu-id="45cd8-138">Nastavením hodnoty DWORD registru ThrowUnobservedTaskExceptions = 1 v\\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft . NETFramework.</span><span class="sxs-lookup"><span data-stu-id="45cd8-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45cd8-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="45cd8-139">Example</span></span>  
 <span data-ttu-id="45cd8-140">Následující příklad ukazuje, jak povolit vyvolání výjimek v úlohách pomocí konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="45cd8-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="45cd8-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="45cd8-141">Example</span></span>  
 <span data-ttu-id="45cd8-142">Následující příklad ukazuje, jak je vyvolána nepozorovaná výjimka z úkolu.</span><span class="sxs-lookup"><span data-stu-id="45cd8-142">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="45cd8-143">Kód musí být spuštěn jako uvolněný program, aby fungoval správně.</span><span class="sxs-lookup"><span data-stu-id="45cd8-143">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="45cd8-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="45cd8-144">See also</span></span>

- [<span data-ttu-id="45cd8-145">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="45cd8-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="45cd8-146">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="45cd8-146">Configuration File Schema</span></span>](../index.md)
