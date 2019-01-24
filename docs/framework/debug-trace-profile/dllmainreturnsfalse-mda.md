---
title: dllMainReturnsFalse – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c513ba06ac79eb3da229605120c4f59ab8d32665
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554540"
---
# <a name="dllmainreturnsfalse-mda"></a><span data-ttu-id="06d1c-102">dllMainReturnsFalse – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="06d1c-102">dllMainReturnsFalse MDA</span></span>
<span data-ttu-id="06d1c-103">`dllMainReturnsFalse` Pomocníka spravovaného ladění (MDA) se aktivuje, pokud spravovanou `DllMain` funkce uživatelské sestavení, volaná s důvodem DLL_PROCESS_ATTACH, vrátí hodnotu FALSE.</span><span class="sxs-lookup"><span data-stu-id="06d1c-103">The `dllMainReturnsFalse` managed debugging assistant (MDA) is activated if the managed `DllMain` function of a user assembly, called with reason DLL_PROCESS_ATTACH, returns FALSE.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="06d1c-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="06d1c-104">Symptoms</span></span>  
 <span data-ttu-id="06d1c-105">`DllMain` Funkce vrátila hodnotu FALSE, která udává, že ho nevykonala příkaz správně.</span><span class="sxs-lookup"><span data-stu-id="06d1c-105">The `DllMain` function returned FALSE, indicating that it did not execute properly.</span></span> <span data-ttu-id="06d1c-106">To může způsobit problémy s neurčeném, protože `DllMain` funkce obvykle obsahují důležité inicializační kód.</span><span class="sxs-lookup"><span data-stu-id="06d1c-106">This can cause undetermined issues because `DllMain` functions typically contain important initialization code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="06d1c-107">Příčina</span><span class="sxs-lookup"><span data-stu-id="06d1c-107">Cause</span></span>  
 <span data-ttu-id="06d1c-108">`DllMain` Volána s důvodem DLL_PROCESS_ATTACH inicializace knihovny DLL při zatížení.</span><span class="sxs-lookup"><span data-stu-id="06d1c-108">The `DllMain` function is called with reason DLL_PROCESS_ATTACH for DLL initialization upon load.</span></span> <span data-ttu-id="06d1c-109">Pokud vrátí hodnotu FALSE, znamená to, že inicializace knihovny DLL se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="06d1c-109">If it returns FALSE, it means that DLL initialization failed.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="06d1c-110">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="06d1c-110">Resolution</span></span>  
 <span data-ttu-id="06d1c-111">Analýza kódu `DllMain` funkce knihovny DLL se nezdařilo a určit příčinu selhání inicializace.</span><span class="sxs-lookup"><span data-stu-id="06d1c-111">Analyze the code of the `DllMain` function of the failed DLL and identify the cause of the initialization failure.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="06d1c-112">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="06d1c-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="06d1c-113">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="06d1c-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="06d1c-114">Pouze sestavy dat o vrácené hodnotě pro `DllMain`.</span><span class="sxs-lookup"><span data-stu-id="06d1c-114">It only reports data about the return value for `DllMain`.</span></span>  
  
## <a name="output"></a><span data-ttu-id="06d1c-115">Výstup</span><span class="sxs-lookup"><span data-stu-id="06d1c-115">Output</span></span>  
 <span data-ttu-id="06d1c-116">Zpráva, že `DllMain` funkci důvodem DLL_PROCESS_ATTACH, vrátila hodnotu FALSE.</span><span class="sxs-lookup"><span data-stu-id="06d1c-116">A message indicating that a `DllMain` function, called for reason DLL_PROCESS_ATTACH, returned FALSE.</span></span> <span data-ttu-id="06d1c-117">Všimněte si, že toto MDA aktivováno, pouze pokud `DllMain` je implementovaná ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="06d1c-117">Note that this MDA is activated only if `DllMain` is implemented in managed code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="06d1c-118">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="06d1c-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="06d1c-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06d1c-119">See also</span></span>
- [<span data-ttu-id="06d1c-120">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="06d1c-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
