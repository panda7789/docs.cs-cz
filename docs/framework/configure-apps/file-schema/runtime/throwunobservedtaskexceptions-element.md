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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153812"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="79560-102">Element \<ThrowUnobservedTaskExceptions></span><span class="sxs-lookup"><span data-stu-id="79560-102">\<ThrowUnobservedTaskExceptions> Element</span></span>
<span data-ttu-id="79560-103">Určuje, zda výjimky neošetřených úloh mají ukončit běžící proces.</span><span class="sxs-lookup"><span data-stu-id="79560-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**  
  
## <a name="syntax"></a><span data-ttu-id="79560-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79560-104">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79560-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="79560-105">Attributes and Elements</span></span>  
 <span data-ttu-id="79560-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="79560-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79560-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="79560-107">Attributes</span></span>  
  
|<span data-ttu-id="79560-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="79560-108">Attribute</span></span>|<span data-ttu-id="79560-109">Popis</span><span class="sxs-lookup"><span data-stu-id="79560-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="79560-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="79560-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="79560-111">Určuje, zda mají být neošetřené výjimky úloh ukončeny spuštěným procesem.</span><span class="sxs-lookup"><span data-stu-id="79560-111">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="79560-112">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="79560-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="79560-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="79560-113">Value</span></span>|<span data-ttu-id="79560-114">Description</span><span class="sxs-lookup"><span data-stu-id="79560-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="79560-115">Neukončí běžící proces pro neošetřenou výjimku úlohy.</span><span class="sxs-lookup"><span data-stu-id="79560-115">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="79560-116">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="79560-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="79560-117">Ukončí běžící proces pro neošetřenou výjimku úlohy.</span><span class="sxs-lookup"><span data-stu-id="79560-117">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="79560-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="79560-118">Child Elements</span></span>  
 <span data-ttu-id="79560-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="79560-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="79560-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="79560-120">Parent Elements</span></span>  
  
|<span data-ttu-id="79560-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="79560-121">Element</span></span>|<span data-ttu-id="79560-122">Description</span><span class="sxs-lookup"><span data-stu-id="79560-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="79560-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="79560-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="79560-124">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="79560-124">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="79560-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="79560-125">Remarks</span></span>  
 <span data-ttu-id="79560-126">Pokud nebyla pozorována výjimka, která je přidružena k objektu, není k <xref:System.Threading.Tasks.Task> dispozici žádná <xref:System.Threading.Tasks.Task.Wait%2A> operace, nadřazený objekt není připojen a <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> vlastnost nebyla přečtena. výjimka úlohy je považována za nepozorovanou.</span><span class="sxs-lookup"><span data-stu-id="79560-126">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="79560-127">V .NET Framework 4 ve výchozím nastavení, pokud <xref:System.Threading.Tasks.Task> má výjimku s nepozorovanou výjimkou uvolňování paměti, finalizační metoda vyvolá výjimku a ukončí proces.</span><span class="sxs-lookup"><span data-stu-id="79560-127">In the .NET Framework 4, by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="79560-128">Ukončení procesu je určeno časováním uvolňování paměti a dokončením.</span><span class="sxs-lookup"><span data-stu-id="79560-128">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="79560-129">Aby vývojáři usnadnili psaní asynchronního kódu založeného na úlohách, .NET Framework 4,5 mění toto výchozí chování pro nepozorované výjimky.</span><span class="sxs-lookup"><span data-stu-id="79560-129">To make it easier for developers to write asynchronous code based on tasks, the .NET Framework 4.5 changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="79560-130">Nepozorované výjimky stále způsobují <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> vyvolání události, ale ve výchozím nastavení se proces neukončí.</span><span class="sxs-lookup"><span data-stu-id="79560-130">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="79560-131">Místo toho je výjimka po vyvolání události ignorována bez ohledu na to, zda obslužná rutina události tuto výjimku dobere.</span><span class="sxs-lookup"><span data-stu-id="79560-131">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="79560-132">V .NET Framework 4,5 lze použít [ \<ThrowUnobservedTaskExceptions> prvek](throwunobservedtaskexceptions-element.md) v konfiguračním souboru aplikace, chcete-li povolit chování .NET Framework 4 při vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="79560-132">In the .NET Framework 4.5, you can use the [\<ThrowUnobservedTaskExceptions> element](throwunobservedtaskexceptions-element.md) in an application configuration file to enable the .NET Framework 4 behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="79560-133">Chování výjimky můžete určit také jedním z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="79560-133">You can also specify the exception behavior in one of the following ways:</span></span>  
  
- <span data-ttu-id="79560-134">Nastavením proměnné prostředí `COMPlus_ThrowUnobservedTaskExceptions` ( `set COMPlus_ThrowUnobservedTaskExceptions=1` ).</span><span class="sxs-lookup"><span data-stu-id="79560-134">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
- <span data-ttu-id="79560-135">Nastavením hodnoty DWORD registru ThrowUnobservedTaskExceptions = 1 v HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft \\ . NETFramework klíč.</span><span class="sxs-lookup"><span data-stu-id="79560-135">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79560-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="79560-136">Example</span></span>  
 <span data-ttu-id="79560-137">Následující příklad ukazuje, jak povolit vyvolávání výjimek v úlohách pomocí konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="79560-137">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="79560-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="79560-138">Example</span></span>  
 <span data-ttu-id="79560-139">Následující příklad ukazuje, jak je vyvolána nepozorovaná výjimka z úlohy.</span><span class="sxs-lookup"><span data-stu-id="79560-139">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="79560-140">Kód musí být spuštěn jako vydaný program pro správné fungování.</span><span class="sxs-lookup"><span data-stu-id="79560-140">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="79560-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="79560-141">See also</span></span>

- [<span data-ttu-id="79560-142">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="79560-142">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="79560-143">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="79560-143">Configuration File Schema</span></span>](../index.md)
