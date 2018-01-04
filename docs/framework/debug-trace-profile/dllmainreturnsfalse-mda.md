---
title: "dllMainReturnsFalse – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eb5de2b1c41d102fbf9fc47db0ff3d8bd72a3bcd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="dllmainreturnsfalse-mda"></a><span data-ttu-id="7da3a-102">dllMainReturnsFalse – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="7da3a-102">dllMainReturnsFalse MDA</span></span>
<span data-ttu-id="7da3a-103">`dllMainReturnsFalse` Pomocník spravovaného ladění (MDA) se aktivuje, pokud spravovaný `DllMain` funkce uživatelského sestavení, volána s důvod DLL_PROCESS_ATTACH, vrátí hodnotu FALSE.</span><span class="sxs-lookup"><span data-stu-id="7da3a-103">The `dllMainReturnsFalse` managed debugging assistant (MDA) is activated if the managed `DllMain` function of a user assembly, called with reason DLL_PROCESS_ATTACH, returns FALSE.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="7da3a-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="7da3a-104">Symptoms</span></span>  
 <span data-ttu-id="7da3a-105">`DllMain` Funkce vrátila hodnotu FALSE, která udává, že ho neproběhlo správně.</span><span class="sxs-lookup"><span data-stu-id="7da3a-105">The `DllMain` function returned FALSE, indicating that it did not execute properly.</span></span> <span data-ttu-id="7da3a-106">Protože to může způsobit problémy s neurčená `DllMain` funkce obvykle obsahují důležité inicializace kódu.</span><span class="sxs-lookup"><span data-stu-id="7da3a-106">This can cause undetermined issues because `DllMain` functions typically contain important initialization code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="7da3a-107">příčina</span><span class="sxs-lookup"><span data-stu-id="7da3a-107">Cause</span></span>  
 <span data-ttu-id="7da3a-108">`DllMain` Funkce je volána s důvod DLL_PROCESS_ATTACH inicializace knihovny DLL při zatížení.</span><span class="sxs-lookup"><span data-stu-id="7da3a-108">The `DllMain` function is called with reason DLL_PROCESS_ATTACH for DLL initialization upon load.</span></span> <span data-ttu-id="7da3a-109">Pokud vrátí hodnotu FALSE, znamená to, že DLL inicializace se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="7da3a-109">If it returns FALSE, it means that DLL initialization failed.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="7da3a-110">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="7da3a-110">Resolution</span></span>  
 <span data-ttu-id="7da3a-111">Analýza kódu `DllMain` funkce selhání knihovny DLL a určete příčinu selhání inicializace.</span><span class="sxs-lookup"><span data-stu-id="7da3a-111">Analyze the code of the `DllMain` function of the failed DLL and identify the cause of the initialization failure.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="7da3a-112">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="7da3a-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="7da3a-113">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="7da3a-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="7da3a-114">Pouze sestavy data o návratovou hodnotu pro `DllMain`.</span><span class="sxs-lookup"><span data-stu-id="7da3a-114">It only reports data about the return value for `DllMain`.</span></span>  
  
## <a name="output"></a><span data-ttu-id="7da3a-115">Výstup</span><span class="sxs-lookup"><span data-stu-id="7da3a-115">Output</span></span>  
 <span data-ttu-id="7da3a-116">Zpráva, že `DllMain` volaná z důvodu DLL_PROCESS_ATTACH, funkce vrátí hodnotu FALSE.</span><span class="sxs-lookup"><span data-stu-id="7da3a-116">A message indicating that a `DllMain` function, called for reason DLL_PROCESS_ATTACH, returned FALSE.</span></span> <span data-ttu-id="7da3a-117">Všimněte si, že je tento MDA aktivovat pouze v případě, `DllMain` se implementují ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="7da3a-117">Note that this MDA is activated only if `DllMain` is implemented in managed code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="7da3a-118">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="7da3a-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7da3a-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="7da3a-119">See Also</span></span>  
 [<span data-ttu-id="7da3a-120">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="7da3a-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
