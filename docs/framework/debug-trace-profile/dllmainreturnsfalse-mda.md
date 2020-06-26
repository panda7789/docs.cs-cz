---
title: dllMainReturnsFalse – pomocník spravovaného ladění (MDA)
description: Přečtěte si o Pomocníkovi spravovaném ladění dllMainReturnsFalse – v .NET. Tato knihovna MDA je aktivována, pokud selhala inicializace knihovny DLL.
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
ms.openlocfilehash: 21d5e37d6823876e07cf5b2cbb881c1cf8b47b11
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416054"
---
# <a name="dllmainreturnsfalse-mda"></a><span data-ttu-id="8126f-104">dllMainReturnsFalse – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="8126f-104">dllMainReturnsFalse MDA</span></span>
<span data-ttu-id="8126f-105">`dllMainReturnsFalse`Pomocník spravovaného ladění (MDA) je aktivován, pokud je spravovaná `DllMain` funkce uživatelského sestavení volána s důvodem DLL_PROCESS_ATTACH, vrátí hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="8126f-105">The `dllMainReturnsFalse` managed debugging assistant (MDA) is activated if the managed `DllMain` function of a user assembly, called with reason DLL_PROCESS_ATTACH, returns FALSE.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="8126f-106">Příznaky</span><span class="sxs-lookup"><span data-stu-id="8126f-106">Symptoms</span></span>  
 <span data-ttu-id="8126f-107">`DllMain`Funkce vrátila hodnotu false, což značí, že nebyla správně provedena.</span><span class="sxs-lookup"><span data-stu-id="8126f-107">The `DllMain` function returned FALSE, indicating that it did not execute properly.</span></span> <span data-ttu-id="8126f-108">To může způsobit neurčité problémy `DllMain` , protože funkce obvykle obsahují důležitý inicializační kód.</span><span class="sxs-lookup"><span data-stu-id="8126f-108">This can cause undetermined issues because `DllMain` functions typically contain important initialization code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="8126f-109">Příčina</span><span class="sxs-lookup"><span data-stu-id="8126f-109">Cause</span></span>  
 <span data-ttu-id="8126f-110">`DllMain`Funkce je volána s důvodem DLL_PROCESS_ATTACH pro inicializaci knihovny DLL při načtení.</span><span class="sxs-lookup"><span data-stu-id="8126f-110">The `DllMain` function is called with reason DLL_PROCESS_ATTACH for DLL initialization upon load.</span></span> <span data-ttu-id="8126f-111">Pokud vrátí hodnotu FALSE, znamená to, že inicializace knihovny DLL se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="8126f-111">If it returns FALSE, it means that DLL initialization failed.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="8126f-112">Řešení</span><span class="sxs-lookup"><span data-stu-id="8126f-112">Resolution</span></span>  
 <span data-ttu-id="8126f-113">Analyzujte kód `DllMain` funkce neúspěšné knihovny DLL a Identifikujte příčinu selhání inicializace.</span><span class="sxs-lookup"><span data-stu-id="8126f-113">Analyze the code of the `DllMain` function of the failed DLL and identify the cause of the initialization failure.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="8126f-114">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="8126f-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="8126f-115">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="8126f-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="8126f-116">Pouze hlásí data o vrácené hodnotě `DllMain` .</span><span class="sxs-lookup"><span data-stu-id="8126f-116">It only reports data about the return value for `DllMain`.</span></span>  
  
## <a name="output"></a><span data-ttu-id="8126f-117">Výstup</span><span class="sxs-lookup"><span data-stu-id="8126f-117">Output</span></span>  
 <span data-ttu-id="8126f-118">Zpráva oznamující, že `DllMain` funkce, která je volána z důvodu DLL_PROCESS_ATTACH, vrátila hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="8126f-118">A message indicating that a `DllMain` function, called for reason DLL_PROCESS_ATTACH, returned FALSE.</span></span> <span data-ttu-id="8126f-119">Všimněte si, že tato aplikace MDA je aktivována pouze `DllMain` v případě, že je implementována ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="8126f-119">Note that this MDA is activated only if `DllMain` is implemented in managed code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="8126f-120">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="8126f-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8126f-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="8126f-121">See also</span></span>

- [<span data-ttu-id="8126f-122">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="8126f-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
