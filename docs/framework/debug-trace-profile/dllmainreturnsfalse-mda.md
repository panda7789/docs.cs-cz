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
ms.openlocfilehash: adc05ae9bd357c142ff09de069aff446b5ea60e8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052860"
---
# <a name="dllmainreturnsfalse-mda"></a><span data-ttu-id="fab25-102">dllMainReturnsFalse – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="fab25-102">dllMainReturnsFalse MDA</span></span>
<span data-ttu-id="fab25-103">Pokud spravovaná`DllMain` funkce uživatelského sestavení, která je volána s důvodem DLL_PROCESS_ATTACH, vrátí hodnotu false, je aktivován pomocník spravovanéholadění(MDA).`dllMainReturnsFalse`</span><span class="sxs-lookup"><span data-stu-id="fab25-103">The `dllMainReturnsFalse` managed debugging assistant (MDA) is activated if the managed `DllMain` function of a user assembly, called with reason DLL_PROCESS_ATTACH, returns FALSE.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="fab25-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="fab25-104">Symptoms</span></span>  
 <span data-ttu-id="fab25-105">`DllMain` Funkce vrátila hodnotu false, což značí, že nebyla správně provedena.</span><span class="sxs-lookup"><span data-stu-id="fab25-105">The `DllMain` function returned FALSE, indicating that it did not execute properly.</span></span> <span data-ttu-id="fab25-106">To může způsobit neurčité problémy, `DllMain` protože funkce obvykle obsahují důležitý inicializační kód.</span><span class="sxs-lookup"><span data-stu-id="fab25-106">This can cause undetermined issues because `DllMain` functions typically contain important initialization code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="fab25-107">příčina</span><span class="sxs-lookup"><span data-stu-id="fab25-107">Cause</span></span>  
 <span data-ttu-id="fab25-108">`DllMain` Funkce je volána s důvodem DLL_PROCESS_ATTACH pro inicializaci knihovny DLL při načtení.</span><span class="sxs-lookup"><span data-stu-id="fab25-108">The `DllMain` function is called with reason DLL_PROCESS_ATTACH for DLL initialization upon load.</span></span> <span data-ttu-id="fab25-109">Pokud vrátí hodnotu FALSE, znamená to, že inicializace knihovny DLL se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="fab25-109">If it returns FALSE, it means that DLL initialization failed.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="fab25-110">Řešení</span><span class="sxs-lookup"><span data-stu-id="fab25-110">Resolution</span></span>  
 <span data-ttu-id="fab25-111">Analyzujte kód `DllMain` funkce neúspěšné knihovny DLL a Identifikujte příčinu selhání inicializace.</span><span class="sxs-lookup"><span data-stu-id="fab25-111">Analyze the code of the `DllMain` function of the failed DLL and identify the cause of the initialization failure.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="fab25-112">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="fab25-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="fab25-113">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="fab25-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="fab25-114">Pouze hlásí data o vrácené hodnotě `DllMain`.</span><span class="sxs-lookup"><span data-stu-id="fab25-114">It only reports data about the return value for `DllMain`.</span></span>  
  
## <a name="output"></a><span data-ttu-id="fab25-115">Výstup</span><span class="sxs-lookup"><span data-stu-id="fab25-115">Output</span></span>  
 <span data-ttu-id="fab25-116">Zpráva oznamující, že `DllMain` funkce volaná z důvodu DLL_PROCESS_ATTACH vrátila hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="fab25-116">A message indicating that a `DllMain` function, called for reason DLL_PROCESS_ATTACH, returned FALSE.</span></span> <span data-ttu-id="fab25-117">Všimněte si, že tato aplikace MDA je `DllMain` aktivována pouze v případě, že je implementována ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="fab25-117">Note that this MDA is activated only if `DllMain` is implemented in managed code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="fab25-118">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="fab25-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fab25-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fab25-119">See also</span></span>

- [<span data-ttu-id="fab25-120">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="fab25-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
