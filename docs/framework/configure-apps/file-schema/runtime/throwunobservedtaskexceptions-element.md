---
title: <ThrowUnobservedTaskExceptions> Prvek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cdce2181490d32212cd2629e98267e43bbe0d334
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189401"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="f535e-102">\<ThrowUnobservedTaskExceptions> Element</span><span class="sxs-lookup"><span data-stu-id="f535e-102">\<ThrowUnobservedTaskExceptions> Element</span></span>
<span data-ttu-id="f535e-103">Určuje, zda úloh neošetřené výjimky by měla ukončit spuštěnému procesu.</span><span class="sxs-lookup"><span data-stu-id="f535e-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
 <span data-ttu-id="f535e-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="f535e-104">\<configuration></span></span>  
<span data-ttu-id="f535e-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="f535e-105">\<runtime></span></span>  
<span data-ttu-id="f535e-106">\<ThrowUnobservedTaskExceptions></span><span class="sxs-lookup"><span data-stu-id="f535e-106">\<ThrowUnobservedTaskExceptions></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f535e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f535e-107">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f535e-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f535e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f535e-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f535e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f535e-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="f535e-110">Attributes</span></span>  
  
|<span data-ttu-id="f535e-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="f535e-111">Attribute</span></span>|<span data-ttu-id="f535e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f535e-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="f535e-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="f535e-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="f535e-114">Určuje, zda úloh neošetřené výjimky by měla ukončit spuštěný proces.</span><span class="sxs-lookup"><span data-stu-id="f535e-114">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="f535e-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="f535e-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="f535e-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f535e-116">Value</span></span>|<span data-ttu-id="f535e-117">Popis</span><span class="sxs-lookup"><span data-stu-id="f535e-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="f535e-118">Spuštěný proces pro nezpracovaná výjimka úlohy nebyl ukončen.</span><span class="sxs-lookup"><span data-stu-id="f535e-118">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="f535e-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="f535e-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="f535e-120">Ukončí běžící proces pro nezpracovaná výjimka úlohy.</span><span class="sxs-lookup"><span data-stu-id="f535e-120">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f535e-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f535e-121">Child Elements</span></span>  
 <span data-ttu-id="f535e-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="f535e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f535e-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f535e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f535e-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="f535e-124">Element</span></span>|<span data-ttu-id="f535e-125">Popis</span><span class="sxs-lookup"><span data-stu-id="f535e-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f535e-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f535e-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f535e-127">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f535e-127">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="f535e-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f535e-128">Remarks</span></span>  
 <span data-ttu-id="f535e-129">Pokud výjimka, která je přidružena <xref:System.Threading.Tasks.Task> nebyla dodržena, neexistuje žádné <xref:System.Threading.Tasks.Task.Wait%2A> operace nadřazeného objektu není připojen a <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> nebyla načtena vlastnost výjimka úlohy se považuje za asynchronního nepozorovaného.</span><span class="sxs-lookup"><span data-stu-id="f535e-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="f535e-130">V [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], pokud výchozí <xref:System.Threading.Tasks.Task> , který má asynchronního nepozorovaného výjimka je uvolněna, finalizační metoda vyvolá výjimku a ukončí proces.</span><span class="sxs-lookup"><span data-stu-id="f535e-130">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="f535e-131">Ukončení procesu se určuje podle načasování uvolňování paměti a finalizace.</span><span class="sxs-lookup"><span data-stu-id="f535e-131">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="f535e-132">Aby bylo snazší pro vývojářům umožňuje psát asynchronní kód založený na úkolech, [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] změní toto výchozí chování pro asynchronního nepozorovaného výjimky.</span><span class="sxs-lookup"><span data-stu-id="f535e-132">To make it easier for developers to write asynchronous code based on tasks, the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="f535e-133">Nepozorované výjimky způsobí <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> událost, ale ve výchozím nastavení, se proces neukončí.</span><span class="sxs-lookup"><span data-stu-id="f535e-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="f535e-134">Místo toho výjimka bude ignorována, jakmile se vyvolá událost, bez ohledu na to, zda obslužná rutina události dodržuje výjimku.</span><span class="sxs-lookup"><span data-stu-id="f535e-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="f535e-135">V [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], můžete použít [ \<throwunobservedtaskexceptions – > element](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) v konfiguračním souboru aplikace umožňuje [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] chování vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="f535e-135">In the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], you can use the [\<ThrowUnobservedTaskExceptions> element](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) in an application configuration file to enable the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="f535e-136">Můžete také určit chování výjimky v jednom z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="f535e-136">You can also specify the exception behavior in one of the following ways:</span></span>  
  
-   <span data-ttu-id="f535e-137">Nastavením proměnné prostředí `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span><span class="sxs-lookup"><span data-stu-id="f535e-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
-   <span data-ttu-id="f535e-138">Nastavením registru typu DWORD hodnota throwunobservedtaskexceptions – = 1 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework klíč.</span><span class="sxs-lookup"><span data-stu-id="f535e-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f535e-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="f535e-139">Example</span></span>  
 <span data-ttu-id="f535e-140">Následující příklad ukazuje, jak povolit vyvolání výjimek v úlohách pomocí konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f535e-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="f535e-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="f535e-141">Example</span></span>  
 <span data-ttu-id="f535e-142">Následující příklad ukazuje, jak je vyvolána nepozorovanou výjimku z úkolu.</span><span class="sxs-lookup"><span data-stu-id="f535e-142">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="f535e-143">Kód musí běžet jako vydané program fungovat správně.</span><span class="sxs-lookup"><span data-stu-id="f535e-143">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f535e-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f535e-144">See also</span></span>

- [<span data-ttu-id="f535e-145">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="f535e-145">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="f535e-146">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="f535e-146">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
