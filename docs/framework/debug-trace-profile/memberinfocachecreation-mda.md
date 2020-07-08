---
title: memberInfoCacheCreation – pomocník spravovaného ladění (MDA)
description: Pochopení pomocníka spravovaného ladění memberInfoCacheCreation – (MDA) v rozhraní .NET, který se aktivuje při vytvoření mezipaměti MemberInfo.
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
ms.openlocfilehash: c48be7ac8632b8072981be01e01997ee8c34b6b3
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051139"
---
# <a name="memberinfocachecreation-mda"></a><span data-ttu-id="de2a2-103">memberInfoCacheCreation – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="de2a2-103">memberInfoCacheCreation MDA</span></span>
<span data-ttu-id="de2a2-104">`memberInfoCacheCreation`Při vytvoření mezipaměti se aktivuje pomocník spravovaného ladění (MDA) <xref:System.Reflection.MemberInfo> .</span><span class="sxs-lookup"><span data-stu-id="de2a2-104">The `memberInfoCacheCreation` managed debugging assistant (MDA) is activated when a <xref:System.Reflection.MemberInfo> cache is created.</span></span> <span data-ttu-id="de2a2-105">Toto je silné označení programu, který využívá funkce reflexe náročné na prostředky.</span><span class="sxs-lookup"><span data-stu-id="de2a2-105">This is a strong indication of a program that is making use of resource-expensive reflection features.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="de2a2-106">Příznaky</span><span class="sxs-lookup"><span data-stu-id="de2a2-106">Symptoms</span></span>  
 <span data-ttu-id="de2a2-107">Pracovní sada programu se zvyšuje, protože program používá reflexi náročné na prostředky.</span><span class="sxs-lookup"><span data-stu-id="de2a2-107">A program's working set increases because the program is using resource-expensive reflection.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="de2a2-108">Příčina</span><span class="sxs-lookup"><span data-stu-id="de2a2-108">Cause</span></span>  
 <span data-ttu-id="de2a2-109">Operace reflexe, které zahrnují <xref:System.Reflection.MemberInfo> objekty, se považují za prostředky nákladné, protože musí číst metadata, která jsou uložená na studených stránkách a obecně naznačují, že program používá určitý typ scénáře s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="de2a2-109">Reflection operations that involve <xref:System.Reflection.MemberInfo> objects are considered resource expensive because they must read metadata that is stored in cold pages and in general they indicate the program is using some type of late-bound scenario.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="de2a2-110">Řešení</span><span class="sxs-lookup"><span data-stu-id="de2a2-110">Resolution</span></span>  
 <span data-ttu-id="de2a2-111">Můžete určit, kde se v programu používá reflexe, povolením tohoto MDA a následným spuštěním kódu v ladicím programu nebo připojením k ladicímu programu při aktivaci MDA.</span><span class="sxs-lookup"><span data-stu-id="de2a2-111">You can determine where reflection is being used in your program by enabling this MDA and then running your code in a debugger or attaching with a debugger when the MDA is activated.</span></span> <span data-ttu-id="de2a2-112">V rámci ladicího programu obdržíte trasování zásobníku, kde se <xref:System.Reflection.MemberInfo> mezipaměť vytvořila, a odtud můžete určit, kde program používá reflexi.</span><span class="sxs-lookup"><span data-stu-id="de2a2-112">Under a debugger you will get a stack trace showing where the <xref:System.Reflection.MemberInfo> cache was created and from there you can determine where your program is using reflection.</span></span>  
  
 <span data-ttu-id="de2a2-113">Řešení je závislé na cílech kódu.</span><span class="sxs-lookup"><span data-stu-id="de2a2-113">The resolution is dependent on the objectives of the code.</span></span> <span data-ttu-id="de2a2-114">Tento MDA vás upozorní, že váš program má scénář s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="de2a2-114">This MDA alerts you that your program has a late-bound scenario.</span></span> <span data-ttu-id="de2a2-115">Možná budete chtít určit, jestli můžete dosadit scénář s nejstarším rozsahem, nebo zvážit výkon scénáře s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="de2a2-115">You might want to determine if you can substitute an early-bound scenario or consider the performance of the late bound scenario.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="de2a2-116">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="de2a2-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="de2a2-117">Tento MDA je aktivován pro každou <xref:System.Reflection.MemberInfo> vytvořenou mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="de2a2-117">This MDA is activated for every <xref:System.Reflection.MemberInfo> cache that is created.</span></span> <span data-ttu-id="de2a2-118">Dopad na výkon je zanedbatelný.</span><span class="sxs-lookup"><span data-stu-id="de2a2-118">The performance impact is negligible.</span></span>  
  
## <a name="output"></a><span data-ttu-id="de2a2-119">Výstup</span><span class="sxs-lookup"><span data-stu-id="de2a2-119">Output</span></span>  
 <span data-ttu-id="de2a2-120">Výstup aplikace MDA vytvoří zprávu oznamující, že <xref:System.Reflection.MemberInfo> byla vytvořena mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="de2a2-120">The MDA outputs a message indicating the <xref:System.Reflection.MemberInfo> cache was created.</span></span> <span data-ttu-id="de2a2-121">Použijte ladicí program k získání trasování zásobníku, kde program používá reflexi.</span><span class="sxs-lookup"><span data-stu-id="de2a2-121">Use a debugger to get a stack trace showing where your program is using reflection.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="de2a2-122">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="de2a2-122">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="de2a2-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="de2a2-123">Example</span></span>  
 <span data-ttu-id="de2a2-124">Tento vzorový kód aktivuje `memberInfoCacheCreation` MDA.</span><span class="sxs-lookup"><span data-stu-id="de2a2-124">This sample code will activate the `memberInfoCacheCreation` MDA.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="de2a2-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="de2a2-125">See also</span></span>

- <xref:System.Reflection.MemberInfo>
- [<span data-ttu-id="de2a2-126">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="de2a2-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
