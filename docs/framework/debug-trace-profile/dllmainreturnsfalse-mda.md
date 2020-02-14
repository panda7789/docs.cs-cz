---
title: dllMainReturnsFalse – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
ms.openlocfilehash: 0b413521e0a2dc06c2ff0be642f080eaf541202f
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216446"
---
# <a name="dllmainreturnsfalse-mda"></a><span data-ttu-id="538d7-102">dllMainReturnsFalse – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="538d7-102">dllMainReturnsFalse MDA</span></span>
<span data-ttu-id="538d7-103">Pokud se funkce spravovaného `DllMain` uživatelského sestavení, která se volá s důvodem DLL_PROCESS_ATTACH, vrátí hodnotu FALSE, aktivuje se pomocníka spravovaného ladění `dllMainReturnsFalse` (MDA).</span><span class="sxs-lookup"><span data-stu-id="538d7-103">The `dllMainReturnsFalse` managed debugging assistant (MDA) is activated if the managed `DllMain` function of a user assembly, called with reason DLL_PROCESS_ATTACH, returns FALSE.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="538d7-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="538d7-104">Symptoms</span></span>  
 <span data-ttu-id="538d7-105">Funkce `DllMain` vrátila hodnotu FALSE, která značí, že nebyla správně provedena.</span><span class="sxs-lookup"><span data-stu-id="538d7-105">The `DllMain` function returned FALSE, indicating that it did not execute properly.</span></span> <span data-ttu-id="538d7-106">To může způsobit neurčité problémy, protože `DllMain` funkce obvykle obsahují důležitý inicializační kód.</span><span class="sxs-lookup"><span data-stu-id="538d7-106">This can cause undetermined issues because `DllMain` functions typically contain important initialization code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="538d7-107">Příčina</span><span class="sxs-lookup"><span data-stu-id="538d7-107">Cause</span></span>  
 <span data-ttu-id="538d7-108">Funkce `DllMain` je volána s důvodem DLL_PROCESS_ATTACH pro inicializaci knihovny DLL při načtení.</span><span class="sxs-lookup"><span data-stu-id="538d7-108">The `DllMain` function is called with reason DLL_PROCESS_ATTACH for DLL initialization upon load.</span></span> <span data-ttu-id="538d7-109">Pokud vrátí hodnotu FALSE, znamená to, že inicializace knihovny DLL se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="538d7-109">If it returns FALSE, it means that DLL initialization failed.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="538d7-110">Řešení</span><span class="sxs-lookup"><span data-stu-id="538d7-110">Resolution</span></span>  
 <span data-ttu-id="538d7-111">Analyzujte kód `DllMain` funkce knihovny DLL, která selhala, a Identifikujte příčinu selhání inicializace.</span><span class="sxs-lookup"><span data-stu-id="538d7-111">Analyze the code of the `DllMain` function of the failed DLL and identify the cause of the initialization failure.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="538d7-112">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="538d7-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="538d7-113">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="538d7-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="538d7-114">Pouze hlásí data o vrácené hodnotě pro `DllMain`.</span><span class="sxs-lookup"><span data-stu-id="538d7-114">It only reports data about the return value for `DllMain`.</span></span>  
  
## <a name="output"></a><span data-ttu-id="538d7-115">Výstup</span><span class="sxs-lookup"><span data-stu-id="538d7-115">Output</span></span>  
 <span data-ttu-id="538d7-116">Zpráva oznamující, že funkce `DllMain` volaná pro DLL_PROCESS_ATTACH důvodu vrátila hodnotu FALSE.</span><span class="sxs-lookup"><span data-stu-id="538d7-116">A message indicating that a `DllMain` function, called for reason DLL_PROCESS_ATTACH, returned FALSE.</span></span> <span data-ttu-id="538d7-117">Všimněte si, že tento MDA je aktivován pouze v případě, že je implementováno `DllMain` ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="538d7-117">Note that this MDA is activated only if `DllMain` is implemented in managed code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="538d7-118">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="538d7-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="538d7-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="538d7-119">See also</span></span>

- [<span data-ttu-id="538d7-120">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="538d7-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
