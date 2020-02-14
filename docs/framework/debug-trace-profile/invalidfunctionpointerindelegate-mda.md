---
title: invalidFunctionPointerInDelegate – pomocník spravovaného ladění (MDA)
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
ms.openlocfilehash: 723f51e14c314bde40c34d629ba7fc4f6276c633
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217376"
---
# <a name="invalidfunctionpointerindelegate-mda"></a><span data-ttu-id="3b38d-102">invalidFunctionPointerInDelegate – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="3b38d-102">invalidFunctionPointerInDelegate MDA</span></span>
<span data-ttu-id="3b38d-103">V případě, že je předán neplatný ukazatel na funkci pro vytvoření delegáta přes ukazatel nativní funkce, je aktivován Pomocník s `invalidFunctionPointerInDelegate` spravované ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="3b38d-103">The `invalidFunctionPointerInDelegate` managed debugging assistant (MDA) is activated when an invalid function pointer is passed in to construct a delegate over a native function pointer.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="3b38d-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="3b38d-104">Symptoms</span></span>  
 <span data-ttu-id="3b38d-105">Při použití delegáta přes ukazatel na funkci došlo k narušení přístupu nebo neočekávanému poškození paměti.</span><span class="sxs-lookup"><span data-stu-id="3b38d-105">Access violations or unexpected memory corruption when using a delegate over a function pointer.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="3b38d-106">Příčina</span><span class="sxs-lookup"><span data-stu-id="3b38d-106">Cause</span></span>  
 <span data-ttu-id="3b38d-107">Byl zadán neplatný ukazatel na funkci.</span><span class="sxs-lookup"><span data-stu-id="3b38d-107">An invalid function pointer was specified.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="3b38d-108">Řešení</span><span class="sxs-lookup"><span data-stu-id="3b38d-108">Resolution</span></span>  
 <span data-ttu-id="3b38d-109">Zadejte platný ukazatel na funkci.</span><span class="sxs-lookup"><span data-stu-id="3b38d-109">Specify a valid function pointer</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="3b38d-110">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="3b38d-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="3b38d-111">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="3b38d-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="3b38d-112">Výstup</span><span class="sxs-lookup"><span data-stu-id="3b38d-112">Output</span></span>  
 <span data-ttu-id="3b38d-113">Neplatný ukazatel na funkci.</span><span class="sxs-lookup"><span data-stu-id="3b38d-113">The invalid function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="3b38d-114">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="3b38d-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b38d-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b38d-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="3b38d-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="3b38d-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="3b38d-117">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="3b38d-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
