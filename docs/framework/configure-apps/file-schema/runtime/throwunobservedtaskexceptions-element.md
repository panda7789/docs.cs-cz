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
ms.openlocfilehash: 99eef6b8c264e21df7f4ecf9fc79dc607d484a0a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115423"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="93033-102">\<element > ThrowUnobservedTaskExceptions</span><span class="sxs-lookup"><span data-stu-id="93033-102">\<ThrowUnobservedTaskExceptions> Element</span></span>
<span data-ttu-id="93033-103">Určuje, zda výjimky neošetřených úloh mají ukončit běžící proces.</span><span class="sxs-lookup"><span data-stu-id="93033-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
<span data-ttu-id="93033-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="93033-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="93033-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="93033-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="93033-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<ThrowUnobservedTaskExceptions >**</span><span class="sxs-lookup"><span data-stu-id="93033-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93033-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93033-107">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93033-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="93033-108">Attributes and Elements</span></span>  
 <span data-ttu-id="93033-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="93033-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93033-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="93033-110">Attributes</span></span>  
  
|<span data-ttu-id="93033-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="93033-111">Attribute</span></span>|<span data-ttu-id="93033-112">Popis</span><span class="sxs-lookup"><span data-stu-id="93033-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="93033-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="93033-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="93033-114">Určuje, zda mají být neošetřené výjimky úloh ukončeny spuštěným procesem.</span><span class="sxs-lookup"><span data-stu-id="93033-114">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="93033-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="93033-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="93033-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="93033-116">Value</span></span>|<span data-ttu-id="93033-117">Popis</span><span class="sxs-lookup"><span data-stu-id="93033-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="93033-118">Neukončí běžící proces pro neošetřenou výjimku úlohy.</span><span class="sxs-lookup"><span data-stu-id="93033-118">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="93033-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="93033-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="93033-120">Ukončí běžící proces pro neošetřenou výjimku úlohy.</span><span class="sxs-lookup"><span data-stu-id="93033-120">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93033-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="93033-121">Child Elements</span></span>  
 <span data-ttu-id="93033-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="93033-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="93033-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="93033-123">Parent Elements</span></span>  
  
|<span data-ttu-id="93033-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="93033-124">Element</span></span>|<span data-ttu-id="93033-125">Popis</span><span class="sxs-lookup"><span data-stu-id="93033-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="93033-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="93033-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="93033-127">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="93033-127">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="93033-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93033-128">Remarks</span></span>  
 <span data-ttu-id="93033-129">Pokud nebyla pozorována výjimka, která je přidružena k <xref:System.Threading.Tasks.Task>, není k dispozici žádná <xref:System.Threading.Tasks.Task.Wait%2A> operace, nadřazený objekt není připojen a vlastnost <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> nebyla přečtena. výjimka úlohy je považována za nepozorovanou.</span><span class="sxs-lookup"><span data-stu-id="93033-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="93033-130">V .NET Framework 4 ve výchozím nastavení, pokud je <xref:System.Threading.Tasks.Task> s nepozorovanou výjimkou uvolňování paměti, finalizační metoda vyvolá výjimku a ukončí proces.</span><span class="sxs-lookup"><span data-stu-id="93033-130">In the .NET Framework 4, by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="93033-131">Ukončení procesu je určeno časováním uvolňování paměti a dokončením.</span><span class="sxs-lookup"><span data-stu-id="93033-131">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="93033-132">Aby vývojáři usnadnili psaní asynchronního kódu založeného na úlohách, .NET Framework 4,5 mění toto výchozí chování pro nepozorované výjimky.</span><span class="sxs-lookup"><span data-stu-id="93033-132">To make it easier for developers to write asynchronous code based on tasks, the .NET Framework 4.5 changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="93033-133">Nepozorované výjimky stále způsobují vyvolání události <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException>, ale ve výchozím nastavení se proces neukončí.</span><span class="sxs-lookup"><span data-stu-id="93033-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="93033-134">Místo toho je výjimka po vyvolání události ignorována bez ohledu na to, zda obslužná rutina události tuto výjimku dobere.</span><span class="sxs-lookup"><span data-stu-id="93033-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="93033-135">V .NET Framework 4,5 lze pomocí [elementu\<ThrowUnobservedTaskExceptions >](throwunobservedtaskexceptions-element.md) v konfiguračním souboru aplikace povolit .NET Framework 4 chování při vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="93033-135">In the .NET Framework 4.5, you can use the [\<ThrowUnobservedTaskExceptions> element](throwunobservedtaskexceptions-element.md) in an application configuration file to enable the .NET Framework 4 behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="93033-136">Chování výjimky můžete určit také jedním z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="93033-136">You can also specify the exception behavior in one of the following ways:</span></span>  
  
- <span data-ttu-id="93033-137">Nastavením proměnné prostředí `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span><span class="sxs-lookup"><span data-stu-id="93033-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
- <span data-ttu-id="93033-138">Nastavením hodnoty DWORD registru ThrowUnobservedTaskExceptions = 1 v HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework klíč.</span><span class="sxs-lookup"><span data-stu-id="93033-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93033-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="93033-139">Example</span></span>  
 <span data-ttu-id="93033-140">Následující příklad ukazuje, jak povolit vyvolávání výjimek v úlohách pomocí konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="93033-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="93033-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="93033-141">Example</span></span>  
 <span data-ttu-id="93033-142">Následující příklad ukazuje, jak je vyvolána nepozorovaná výjimka z úlohy.</span><span class="sxs-lookup"><span data-stu-id="93033-142">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="93033-143">Kód musí být spuštěn jako vydaný program pro správné fungování.</span><span class="sxs-lookup"><span data-stu-id="93033-143">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="93033-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93033-144">See also</span></span>

- [<span data-ttu-id="93033-145">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="93033-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="93033-146">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="93033-146">Configuration File Schema</span></span>](../index.md)
