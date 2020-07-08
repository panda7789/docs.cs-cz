---
title: invalidFunctionPointerInDelegate – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění invalidFunctionPointerInDelegate (MDA), který je vyvolán, pokud je předán neplatný ukazatel na funkci pro vytvoření delegáta.
ms.date: 03/30/2017
helpviewer_keywords:
- invalidFunctionPointerInDelegate MDA
- managed debugging assistants (MDAs), invalid function pointer to delegates
- MDAs (managed debugging assistants), invalid function pointer to delegates
- function pointers, invalid
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- invalid function pointers
ms.assetid: 99ae44f1-783e-49a9-9009-24f54bbd0f09
ms.openlocfilehash: a17427d117c62ba782af3c9549c84623a3013b06
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051737"
---
# <a name="invalidfunctionpointerindelegate-mda"></a><span data-ttu-id="996ab-103">invalidFunctionPointerInDelegate – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="996ab-103">invalidFunctionPointerInDelegate MDA</span></span>
<span data-ttu-id="996ab-104">`invalidFunctionPointerInDelegate`Pomocník spravovaného ladění (MDA) je aktivován, pokud je předán neplatný ukazatel na funkci, aby bylo možné vytvořit delegáta nad ukazatelem nativní funkce.</span><span class="sxs-lookup"><span data-stu-id="996ab-104">The `invalidFunctionPointerInDelegate` managed debugging assistant (MDA) is activated when an invalid function pointer is passed in to construct a delegate over a native function pointer.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="996ab-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="996ab-105">Symptoms</span></span>  
 <span data-ttu-id="996ab-106">Při použití delegáta přes ukazatel na funkci došlo k narušení přístupu nebo neočekávanému poškození paměti.</span><span class="sxs-lookup"><span data-stu-id="996ab-106">Access violations or unexpected memory corruption when using a delegate over a function pointer.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="996ab-107">Příčina</span><span class="sxs-lookup"><span data-stu-id="996ab-107">Cause</span></span>  
 <span data-ttu-id="996ab-108">Byl zadán neplatný ukazatel na funkci.</span><span class="sxs-lookup"><span data-stu-id="996ab-108">An invalid function pointer was specified.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="996ab-109">Řešení</span><span class="sxs-lookup"><span data-stu-id="996ab-109">Resolution</span></span>  
 <span data-ttu-id="996ab-110">Zadejte platný ukazatel na funkci.</span><span class="sxs-lookup"><span data-stu-id="996ab-110">Specify a valid function pointer</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="996ab-111">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="996ab-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="996ab-112">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="996ab-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="996ab-113">Výstup</span><span class="sxs-lookup"><span data-stu-id="996ab-113">Output</span></span>  
 <span data-ttu-id="996ab-114">Neplatný ukazatel na funkci.</span><span class="sxs-lookup"><span data-stu-id="996ab-114">The invalid function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="996ab-115">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="996ab-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="996ab-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="996ab-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="996ab-117">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="996ab-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="996ab-118">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="996ab-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
