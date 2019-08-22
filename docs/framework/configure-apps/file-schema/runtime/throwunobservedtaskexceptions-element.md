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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 876452a0a56d10f169526138cdbbbd153572f457
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658840"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="d027b-102">\<ThrowUnobservedTaskExceptions – element ></span><span class="sxs-lookup"><span data-stu-id="d027b-102">\<ThrowUnobservedTaskExceptions> Element</span></span>
<span data-ttu-id="d027b-103">Určuje, zda výjimky neošetřených úloh mají ukončit běžící proces.</span><span class="sxs-lookup"><span data-stu-id="d027b-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
 <span data-ttu-id="d027b-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="d027b-104">\<configuration></span></span>  
<span data-ttu-id="d027b-105">\<> modulu runtime</span><span class="sxs-lookup"><span data-stu-id="d027b-105">\<runtime></span></span>  
<span data-ttu-id="d027b-106">\<ThrowUnobservedTaskExceptions></span><span class="sxs-lookup"><span data-stu-id="d027b-106">\<ThrowUnobservedTaskExceptions></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d027b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d027b-107">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d027b-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d027b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d027b-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d027b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d027b-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="d027b-110">Attributes</span></span>  
  
|<span data-ttu-id="d027b-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="d027b-111">Attribute</span></span>|<span data-ttu-id="d027b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d027b-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d027b-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="d027b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d027b-114">Určuje, zda mají být neošetřené výjimky úloh ukončeny spuštěným procesem.</span><span class="sxs-lookup"><span data-stu-id="d027b-114">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d027b-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="d027b-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="d027b-116">Value</span><span class="sxs-lookup"><span data-stu-id="d027b-116">Value</span></span>|<span data-ttu-id="d027b-117">Popis</span><span class="sxs-lookup"><span data-stu-id="d027b-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="d027b-118">Neukončí běžící proces pro neošetřenou výjimku úlohy.</span><span class="sxs-lookup"><span data-stu-id="d027b-118">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="d027b-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="d027b-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="d027b-120">Ukončí běžící proces pro neošetřenou výjimku úlohy.</span><span class="sxs-lookup"><span data-stu-id="d027b-120">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d027b-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d027b-121">Child Elements</span></span>  
 <span data-ttu-id="d027b-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="d027b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d027b-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d027b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d027b-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="d027b-124">Element</span></span>|<span data-ttu-id="d027b-125">Popis</span><span class="sxs-lookup"><span data-stu-id="d027b-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d027b-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d027b-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d027b-127">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="d027b-127">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="d027b-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d027b-128">Remarks</span></span>  
 <span data-ttu-id="d027b-129">Pokud nebyla pozorována výjimka, která je <xref:System.Threading.Tasks.Task> přidružena k objektu, není k dispozici žádná <xref:System.Threading.Tasks.Task.Wait%2A> operace, nadřazený objekt není připojen a <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> vlastnost nebyla přečtena. výjimka úlohy je považována za nepozorovanou.</span><span class="sxs-lookup"><span data-stu-id="d027b-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="d027b-130">V .NET Framework 4 ve výchozím nastavení, pokud <xref:System.Threading.Tasks.Task> má výjimku s nepozorovanou výjimkou uvolňování paměti, finalizační metoda vyvolá výjimku a ukončí proces.</span><span class="sxs-lookup"><span data-stu-id="d027b-130">In the .NET Framework 4, by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="d027b-131">Ukončení procesu je určeno časováním uvolňování paměti a dokončením.</span><span class="sxs-lookup"><span data-stu-id="d027b-131">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="d027b-132">Aby vývojáři usnadnili psaní asynchronního kódu založeného na úlohách, .NET Framework 4,5 mění toto výchozí chování pro nepozorované výjimky.</span><span class="sxs-lookup"><span data-stu-id="d027b-132">To make it easier for developers to write asynchronous code based on tasks, the .NET Framework 4.5 changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="d027b-133">Nepozorované výjimky stále způsobují <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> vyvolání události, ale ve výchozím nastavení se proces neukončí.</span><span class="sxs-lookup"><span data-stu-id="d027b-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="d027b-134">Místo toho je výjimka po vyvolání události ignorována bez ohledu na to, zda obslužná rutina události tuto výjimku dobere.</span><span class="sxs-lookup"><span data-stu-id="d027b-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="d027b-135">V .NET Framework 4,5 lze pomocí [ \<prvku > ThrowUnobservedTaskExceptions](throwunobservedtaskexceptions-element.md) v konfiguračním souboru aplikace povolit .NET Framework 4 chování při vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="d027b-135">In the .NET Framework 4.5, you can use the [\<ThrowUnobservedTaskExceptions> element](throwunobservedtaskexceptions-element.md) in an application configuration file to enable the .NET Framework 4 behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="d027b-136">Chování výjimky můžete určit také jedním z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="d027b-136">You can also specify the exception behavior in one of the following ways:</span></span>  
  
- <span data-ttu-id="d027b-137">Nastavením proměnné `COMPlus_ThrowUnobservedTaskExceptions` prostředí (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span><span class="sxs-lookup"><span data-stu-id="d027b-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
- <span data-ttu-id="d027b-138">Nastavením hodnoty DWORD registru ThrowUnobservedTaskExceptions = 1 v HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework klíč.</span><span class="sxs-lookup"><span data-stu-id="d027b-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d027b-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="d027b-139">Example</span></span>  
 <span data-ttu-id="d027b-140">Následující příklad ukazuje, jak povolit vyvolávání výjimek v úlohách pomocí konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="d027b-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="d027b-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="d027b-141">Example</span></span>  
 <span data-ttu-id="d027b-142">Následující příklad ukazuje, jak je vyvolána nepozorovaná výjimka z úlohy.</span><span class="sxs-lookup"><span data-stu-id="d027b-142">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="d027b-143">Kód musí být spuštěn jako vydaný program pro správné fungování.</span><span class="sxs-lookup"><span data-stu-id="d027b-143">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d027b-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d027b-144">See also</span></span>

- [<span data-ttu-id="d027b-145">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="d027b-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d027b-146">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="d027b-146">Configuration File Schema</span></span>](../index.md)
