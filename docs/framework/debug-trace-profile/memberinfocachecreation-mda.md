---
title: memberInfoCacheCreation – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- member info cache creation
- MemberInfoCacheCreation MDA
- reflection, run-time errors
- MDAs (managed debugging assistants), cache
- cache [.NET Framework], reflection
- managed debugging assistants (MDAs), cache
- MemberInfo cache
ms.assetid: 5abdad23-1335-4744-8acb-934002c0b6fe
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90f59f4d593a8aa077a6710cc0f5c1747ac1a3ad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103763"
---
# <a name="memberinfocachecreation-mda"></a><span data-ttu-id="afa97-102">memberInfoCacheCreation – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="afa97-102">memberInfoCacheCreation MDA</span></span>
<span data-ttu-id="afa97-103">`memberInfoCacheCreation` Pomocníka spravovaného ladění (MDA) se aktivuje při <xref:System.Reflection.MemberInfo> mezipaměť je vytvořená.</span><span class="sxs-lookup"><span data-stu-id="afa97-103">The `memberInfoCacheCreation` managed debugging assistant (MDA) is activated when a <xref:System.Reflection.MemberInfo> cache is created.</span></span> <span data-ttu-id="afa97-104">Toto je silné údaj o program, který provádí používání funkcí prostředků reflexe.</span><span class="sxs-lookup"><span data-stu-id="afa97-104">This is a strong indication of a program that is making use of resource-expensive reflection features.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="afa97-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="afa97-105">Symptoms</span></span>  
 <span data-ttu-id="afa97-106">Program pracovní sadu zvýšení vzhledem k tomu, že program používá prostředků reflexe.</span><span class="sxs-lookup"><span data-stu-id="afa97-106">A program's working set increases because the program is using resource-expensive reflection.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="afa97-107">Příčina</span><span class="sxs-lookup"><span data-stu-id="afa97-107">Cause</span></span>  
 <span data-ttu-id="afa97-108">Reflexe operací, které se týkají <xref:System.Reflection.MemberInfo> objekty jsou považovány za prostředek nákladné, protože je musí číst metadata, která je uložena v studenou stránky a obecně označují program používá nějaký typ scénář s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="afa97-108">Reflection operations that involve <xref:System.Reflection.MemberInfo> objects are considered resource expensive because they must read metadata that is stored in cold pages and in general they indicate the program is using some type of late-bound scenario.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="afa97-109">Řešení</span><span class="sxs-lookup"><span data-stu-id="afa97-109">Resolution</span></span>  
 <span data-ttu-id="afa97-110">Můžete určit, kde reflexe se používá ve svém programu povolením toto MDA a potom spuštěním kódu v ladicí program nebo připojení se ladicí program, když MDA aktivováno.</span><span class="sxs-lookup"><span data-stu-id="afa97-110">You can determine where reflection is being used in your program by enabling this MDA and then running your code in a debugger or attaching with a debugger when the MDA is activated.</span></span> <span data-ttu-id="afa97-111">V ladicím programu se zobrazí trasování zásobníku znázorňující, kde <xref:System.Reflection.MemberInfo> mezipaměti byla vytvořena a odtud můžete určit, kde je program pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="afa97-111">Under a debugger you will get a stack trace showing where the <xref:System.Reflection.MemberInfo> cache was created and from there you can determine where your program is using reflection.</span></span>  
  
 <span data-ttu-id="afa97-112">Rozlišení je závislá na cíli kód.</span><span class="sxs-lookup"><span data-stu-id="afa97-112">The resolution is dependent on the objectives of the code.</span></span> <span data-ttu-id="afa97-113">Toto MDA vás upozorní, že váš program obsahuje scénář s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="afa97-113">This MDA alerts you that your program has a late-bound scenario.</span></span> <span data-ttu-id="afa97-114">Můžete chtít určit, jestli můžete nahradit scénáři časné vazby nebo zvažte výkonu pozdní vazbou scénář.</span><span class="sxs-lookup"><span data-stu-id="afa97-114">You might want to determine if you can substitute an early-bound scenario or consider the performance of the late bound scenario.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="afa97-115">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="afa97-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="afa97-116">Je toto MDA aktivováno pro každý <xref:System.Reflection.MemberInfo> mezipaměti, který je vytvořen.</span><span class="sxs-lookup"><span data-stu-id="afa97-116">This MDA is activated for every <xref:System.Reflection.MemberInfo> cache that is created.</span></span> <span data-ttu-id="afa97-117">Je zanedbatelný dopad na výkon.</span><span class="sxs-lookup"><span data-stu-id="afa97-117">The performance impact is negligible.</span></span>  
  
## <a name="output"></a><span data-ttu-id="afa97-118">Výstup</span><span class="sxs-lookup"><span data-stu-id="afa97-118">Output</span></span>  
 <span data-ttu-id="afa97-119">MDA výstupy zpráva, <xref:System.Reflection.MemberInfo> mezipaměti byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="afa97-119">The MDA outputs a message indicating the <xref:System.Reflection.MemberInfo> cache was created.</span></span> <span data-ttu-id="afa97-120">Pomocí ladicího programu můžete získat trasování zásobníku znázorňující, kde je program pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="afa97-120">Use a debugger to get a stack trace showing where your program is using reflection.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="afa97-121">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="afa97-121">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="afa97-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="afa97-122">Example</span></span>  
 <span data-ttu-id="afa97-123">Tento ukázkový kód se budou aktivovat `memberInfoCacheCreation` MDA.</span><span class="sxs-lookup"><span data-stu-id="afa97-123">This sample code will activate the `memberInfoCacheCreation` MDA.</span></span>  
  
```csharp
using System;  
  
public class Exe  
{  
    public static void Main()  
    {  
        typeof(object).GetMethods();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="afa97-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="afa97-124">See also</span></span>

- <xref:System.Reflection.MemberInfo>
- [<span data-ttu-id="afa97-125">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="afa97-125">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
