---
title: "memberInfoCacheCreation – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member info cache creation
- MemberInfoCacheCreation MDA
- reflection, run-time errors
- MDAs (managed debugging assistants), cache
- cache [.NET Framework], reflection
- managed debugging assistants (MDAs), cache
- MemberInfo cache
ms.assetid: 5abdad23-1335-4744-8acb-934002c0b6fe
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d82e77e2a47a9b0feb36ca054c0abcff2721940
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="memberinfocachecreation-mda"></a><span data-ttu-id="663d7-102">memberInfoCacheCreation – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="663d7-102">memberInfoCacheCreation MDA</span></span>
<span data-ttu-id="663d7-103">`memberInfoCacheCreation` Pomocník spravovaného ladění (MDA) se aktivuje při <xref:System.Reflection.MemberInfo> mezipaměť je vytvořená.</span><span class="sxs-lookup"><span data-stu-id="663d7-103">The `memberInfoCacheCreation` managed debugging assistant (MDA) is activated when a <xref:System.Reflection.MemberInfo> cache is created.</span></span> <span data-ttu-id="663d7-104">To se silné informace o programu, který je zajistit použití nákladných prostředků reflexe funkcí.</span><span class="sxs-lookup"><span data-stu-id="663d7-104">This is a strong indication of a program that is making use of resource-expensive reflection features.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="663d7-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="663d7-105">Symptoms</span></span>  
 <span data-ttu-id="663d7-106">Program je sada zvyšuje pracovat, protože program je pomocí reflexe nákladných prostředků.</span><span class="sxs-lookup"><span data-stu-id="663d7-106">A program's working set increases because the program is using resource-expensive reflection.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="663d7-107">příčina</span><span class="sxs-lookup"><span data-stu-id="663d7-107">Cause</span></span>  
 <span data-ttu-id="663d7-108">Reflexe operace, které zahrnují <xref:System.Reflection.MemberInfo> objekty jsou považovány za prostředků náročná, protože budou musí přečíst metadata, která je uložena v cold stránky a obecně indikují program používá nějaký typ scénář pozdní vazbu.</span><span class="sxs-lookup"><span data-stu-id="663d7-108">Reflection operations that involve <xref:System.Reflection.MemberInfo> objects are considered resource expensive because they must read metadata that is stored in cold pages and in general they indicate the program is using some type of late-bound scenario.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="663d7-109">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="663d7-109">Resolution</span></span>  
 <span data-ttu-id="663d7-110">Můžete určit, kde se reflexe používá v programu povolením této (mda) a potom spuštěním kódu v ladicí program nebo připojení s ladicí program, když je aktivován (mda).</span><span class="sxs-lookup"><span data-stu-id="663d7-110">You can determine where reflection is being used in your program by enabling this MDA and then running your code in a debugger or attaching with a debugger when the MDA is activated.</span></span> <span data-ttu-id="663d7-111">V části ladicí program bude získejte trasování zásobníku ukazující, kde <xref:System.Reflection.MemberInfo> mezipaměti byl vytvořen a z ní můžete určit, kde je váš program pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="663d7-111">Under a debugger you will get a stack trace showing where the <xref:System.Reflection.MemberInfo> cache was created and from there you can determine where your program is using reflection.</span></span>  
  
 <span data-ttu-id="663d7-112">Řešení je závislé na cílech kódu.</span><span class="sxs-lookup"><span data-stu-id="663d7-112">The resolution is dependent on the objectives of the code.</span></span> <span data-ttu-id="663d7-113">Tato MDA vás upozorní, že má program scénáři pozdní vazbu.</span><span class="sxs-lookup"><span data-stu-id="663d7-113">This MDA alerts you that your program has a late-bound scenario.</span></span> <span data-ttu-id="663d7-114">Můžete chtít zjistit, zda můžete nahradit scénářem časné vazby či zvažte výkon pozdní vázané scénáře.</span><span class="sxs-lookup"><span data-stu-id="663d7-114">You might want to determine if you can substitute an early-bound scenario or consider the performance of the late bound scenario.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="663d7-115">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="663d7-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="663d7-116">Tato MDA se aktivuje na každých <xref:System.Reflection.MemberInfo> mezipaměti, který je vytvořen.</span><span class="sxs-lookup"><span data-stu-id="663d7-116">This MDA is activated for every <xref:System.Reflection.MemberInfo> cache that is created.</span></span> <span data-ttu-id="663d7-117">Dopad na výkon je nepatrné.</span><span class="sxs-lookup"><span data-stu-id="663d7-117">The performance impact is negligible.</span></span>  
  
## <a name="output"></a><span data-ttu-id="663d7-118">Výstup</span><span class="sxs-lookup"><span data-stu-id="663d7-118">Output</span></span>  
 <span data-ttu-id="663d7-119">MDA výstupy zpráva označující <xref:System.Reflection.MemberInfo> mezipaměti byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="663d7-119">The MDA outputs a message indicating the <xref:System.Reflection.MemberInfo> cache was created.</span></span> <span data-ttu-id="663d7-120">Získejte trasování zásobníku znázorňující, kde je váš program pomocí reflexe pomocí ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="663d7-120">Use a debugger to get a stack trace showing where your program is using reflection.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="663d7-121">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="663d7-121">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="663d7-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="663d7-122">Example</span></span>  
 <span data-ttu-id="663d7-123">Tento ukázkový kód se budou aktivovat `memberInfoCacheCreation` (mda).</span><span class="sxs-lookup"><span data-stu-id="663d7-123">This sample code will activate the `memberInfoCacheCreation` MDA.</span></span>  
  
```  
using System;  
  
public class Exe  
{  
    public static void Main()  
    {  
        typeof(object).GetMethods();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="663d7-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="663d7-124">See Also</span></span>  
 <xref:System.Reflection.MemberInfo>  
 [<span data-ttu-id="663d7-125">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="663d7-125">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
