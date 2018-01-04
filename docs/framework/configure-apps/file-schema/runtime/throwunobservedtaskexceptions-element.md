---
title: "&lt;Throwunobservedtaskexceptions –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 635270a6461b573663b7719843d81ff2b23e63dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltthrowunobservedtaskexceptionsgt-element"></a><span data-ttu-id="43fe2-102">&lt;Throwunobservedtaskexceptions –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="43fe2-102">&lt;ThrowUnobservedTaskExceptions&gt; Element</span></span>
<span data-ttu-id="43fe2-103">Určuje, zda úloha neošetřené výjimky by měl ukončit spuštěných procesů.</span><span class="sxs-lookup"><span data-stu-id="43fe2-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
 <span data-ttu-id="43fe2-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="43fe2-104">\<configuration></span></span>  
<span data-ttu-id="43fe2-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="43fe2-105">\<runtime></span></span>  
<span data-ttu-id="43fe2-106">\<Throwunobservedtaskexceptions – ></span><span class="sxs-lookup"><span data-stu-id="43fe2-106">\<ThrowUnobservedTaskExceptions></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43fe2-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43fe2-107">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43fe2-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="43fe2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="43fe2-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="43fe2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43fe2-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="43fe2-110">Attributes</span></span>  
  
|<span data-ttu-id="43fe2-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="43fe2-111">Attribute</span></span>|<span data-ttu-id="43fe2-112">Popis</span><span class="sxs-lookup"><span data-stu-id="43fe2-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="43fe2-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="43fe2-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="43fe2-114">Určuje, zda úloha neošetřené výjimky by měl ukončit běžící proces.</span><span class="sxs-lookup"><span data-stu-id="43fe2-114">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="43fe2-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="43fe2-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="43fe2-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="43fe2-116">Value</span></span>|<span data-ttu-id="43fe2-117">Popis</span><span class="sxs-lookup"><span data-stu-id="43fe2-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="43fe2-118">Nezavře běžící proces pro úloh neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="43fe2-118">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="43fe2-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="43fe2-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="43fe2-120">Ukončí běžící proces pro úloh neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="43fe2-120">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43fe2-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="43fe2-121">Child Elements</span></span>  
 <span data-ttu-id="43fe2-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="43fe2-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43fe2-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="43fe2-123">Parent Elements</span></span>  
  
|<span data-ttu-id="43fe2-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="43fe2-124">Element</span></span>|<span data-ttu-id="43fe2-125">Popis</span><span class="sxs-lookup"><span data-stu-id="43fe2-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="43fe2-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="43fe2-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="43fe2-127">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="43fe2-127">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="43fe2-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="43fe2-128">Remarks</span></span>  
 <span data-ttu-id="43fe2-129">Pokud výjimka, která je přidružena <xref:System.Threading.Tasks.Task> nebyla dodržena, není žádné <xref:System.Threading.Tasks.Task.Wait%2A> operace, nadřazený není připojený a <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> nebyla načtena vlastnost výjimku úlohy se považuje za zmeškané.</span><span class="sxs-lookup"><span data-stu-id="43fe2-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="43fe2-130">V [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], pomocí výchozí, pokud <xref:System.Threading.Tasks.Task> má zmeškané výjimkou je uvolnění z paměti, finalizační metodu vyvolá výjimku a ukončit proces.</span><span class="sxs-lookup"><span data-stu-id="43fe2-130">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="43fe2-131">Ukončení procesu je určen podle načasování uvolňování paměti a dokončení.</span><span class="sxs-lookup"><span data-stu-id="43fe2-131">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="43fe2-132">Aby bylo snazší pro vývojáře k zápisu asynchronní kódu založené na úlohy, [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] změní toto výchozí chování pro zmeškané výjimky.</span><span class="sxs-lookup"><span data-stu-id="43fe2-132">To make it easier for developers to write asynchronous code based on tasks, the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="43fe2-133">Nepozorovaná výjimky způsobí <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> událost, která má být vyvolána, ale ve výchozím nastavení, není ukončit proces.</span><span class="sxs-lookup"><span data-stu-id="43fe2-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="43fe2-134">Místo toho se výjimka ignoruje po událost se vyvolá, bez ohledu na to, jestli obslužná rutina události dodržuje výjimku.</span><span class="sxs-lookup"><span data-stu-id="43fe2-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="43fe2-135">V [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], můžete použít [ \<throwunobservedtaskexceptions – > element](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) v konfiguračním souboru aplikace, aby [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] chování došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="43fe2-135">In the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], you can use the [\<ThrowUnobservedTaskExceptions> element](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) in an application configuration file to enable the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="43fe2-136">Můžete také určit chování výjimka v jednom z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="43fe2-136">You can also specify the exception behavior in one of the following ways:</span></span>  
  
-   <span data-ttu-id="43fe2-137">Nastavením proměnné prostředí `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span><span class="sxs-lookup"><span data-stu-id="43fe2-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
-   <span data-ttu-id="43fe2-138">Nastavením registru DWORD hodnota throwunobservedtaskexceptions – = 1 v HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework klíč.</span><span class="sxs-lookup"><span data-stu-id="43fe2-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43fe2-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="43fe2-139">Example</span></span>  
 <span data-ttu-id="43fe2-140">Následující příklad ukazuje, jak povolit vyvolání výjimky v úlohách pomocí konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="43fe2-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="43fe2-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="43fe2-141">Example</span></span>  
 <span data-ttu-id="43fe2-142">Následující příklad ukazuje, jak je vyvolána zmeškané výjimka z úlohy.</span><span class="sxs-lookup"><span data-stu-id="43fe2-142">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="43fe2-143">Kód musí běžet jako vydaná program pracovat správně.</span><span class="sxs-lookup"><span data-stu-id="43fe2-143">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="43fe2-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="43fe2-144">See Also</span></span>  
 [<span data-ttu-id="43fe2-145">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="43fe2-145">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="43fe2-146">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="43fe2-146">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
