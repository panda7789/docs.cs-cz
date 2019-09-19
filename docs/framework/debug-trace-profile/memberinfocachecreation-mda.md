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
ms.openlocfilehash: d3b65ecc226c1caf7b53d746f0583e1f57c7d8c1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052467"
---
# <a name="memberinfocachecreation-mda"></a><span data-ttu-id="cf674-102">memberInfoCacheCreation – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="cf674-102">memberInfoCacheCreation MDA</span></span>
<span data-ttu-id="cf674-103">Při vytvoření `memberInfoCacheCreation` mezipamětiseaktivujepomocníkspravovanéholadění<xref:System.Reflection.MemberInfo> (MDA).</span><span class="sxs-lookup"><span data-stu-id="cf674-103">The `memberInfoCacheCreation` managed debugging assistant (MDA) is activated when a <xref:System.Reflection.MemberInfo> cache is created.</span></span> <span data-ttu-id="cf674-104">Toto je silné označení programu, který využívá funkce reflexe náročné na prostředky.</span><span class="sxs-lookup"><span data-stu-id="cf674-104">This is a strong indication of a program that is making use of resource-expensive reflection features.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="cf674-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="cf674-105">Symptoms</span></span>  
 <span data-ttu-id="cf674-106">Pracovní sada programu se zvyšuje, protože program používá reflexi náročné na prostředky.</span><span class="sxs-lookup"><span data-stu-id="cf674-106">A program's working set increases because the program is using resource-expensive reflection.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="cf674-107">příčina</span><span class="sxs-lookup"><span data-stu-id="cf674-107">Cause</span></span>  
 <span data-ttu-id="cf674-108">Operace reflexe <xref:System.Reflection.MemberInfo> , které zahrnují objekty, se považují za prostředky nákladné, protože musí číst metadata, která jsou uložená na studených stránkách a obecně naznačují, že program používá určitý typ scénáře s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="cf674-108">Reflection operations that involve <xref:System.Reflection.MemberInfo> objects are considered resource expensive because they must read metadata that is stored in cold pages and in general they indicate the program is using some type of late-bound scenario.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="cf674-109">Řešení</span><span class="sxs-lookup"><span data-stu-id="cf674-109">Resolution</span></span>  
 <span data-ttu-id="cf674-110">Můžete určit, kde se v programu používá reflexe, povolením tohoto MDA a následným spuštěním kódu v ladicím programu nebo připojením k ladicímu programu při aktivaci MDA.</span><span class="sxs-lookup"><span data-stu-id="cf674-110">You can determine where reflection is being used in your program by enabling this MDA and then running your code in a debugger or attaching with a debugger when the MDA is activated.</span></span> <span data-ttu-id="cf674-111">V rámci ladicího programu obdržíte trasování zásobníku, kde <xref:System.Reflection.MemberInfo> se mezipaměť vytvořila, a odtud můžete určit, kde program používá reflexi.</span><span class="sxs-lookup"><span data-stu-id="cf674-111">Under a debugger you will get a stack trace showing where the <xref:System.Reflection.MemberInfo> cache was created and from there you can determine where your program is using reflection.</span></span>  
  
 <span data-ttu-id="cf674-112">Řešení je závislé na cílech kódu.</span><span class="sxs-lookup"><span data-stu-id="cf674-112">The resolution is dependent on the objectives of the code.</span></span> <span data-ttu-id="cf674-113">Tento MDA vás upozorní, že váš program má scénář s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="cf674-113">This MDA alerts you that your program has a late-bound scenario.</span></span> <span data-ttu-id="cf674-114">Možná budete chtít určit, jestli můžete dosadit scénář s nejstarším rozsahem, nebo zvážit výkon scénáře s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="cf674-114">You might want to determine if you can substitute an early-bound scenario or consider the performance of the late bound scenario.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="cf674-115">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="cf674-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="cf674-116">Tento MDA je aktivován pro každou <xref:System.Reflection.MemberInfo> vytvořenou mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="cf674-116">This MDA is activated for every <xref:System.Reflection.MemberInfo> cache that is created.</span></span> <span data-ttu-id="cf674-117">Dopad na výkon je zanedbatelný.</span><span class="sxs-lookup"><span data-stu-id="cf674-117">The performance impact is negligible.</span></span>  
  
## <a name="output"></a><span data-ttu-id="cf674-118">Výstup</span><span class="sxs-lookup"><span data-stu-id="cf674-118">Output</span></span>  
 <span data-ttu-id="cf674-119">Výstup aplikace MDA vytvoří zprávu oznamující, <xref:System.Reflection.MemberInfo> že byla vytvořena mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="cf674-119">The MDA outputs a message indicating the <xref:System.Reflection.MemberInfo> cache was created.</span></span> <span data-ttu-id="cf674-120">Použijte ladicí program k získání trasování zásobníku, kde program používá reflexi.</span><span class="sxs-lookup"><span data-stu-id="cf674-120">Use a debugger to get a stack trace showing where your program is using reflection.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="cf674-121">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="cf674-121">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="cf674-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="cf674-122">Example</span></span>  
 <span data-ttu-id="cf674-123">Tento vzorový kód aktivuje `memberInfoCacheCreation` MDA.</span><span class="sxs-lookup"><span data-stu-id="cf674-123">This sample code will activate the `memberInfoCacheCreation` MDA.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cf674-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cf674-124">See also</span></span>

- <xref:System.Reflection.MemberInfo>
- [<span data-ttu-id="cf674-125">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="cf674-125">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
