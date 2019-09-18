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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6e3e64a720d12426fb066619b46c73402d1113e0
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052618"
---
# <a name="invalidfunctionpointerindelegate-mda"></a><span data-ttu-id="82e15-102">invalidFunctionPointerInDelegate – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="82e15-102">invalidFunctionPointerInDelegate MDA</span></span>
<span data-ttu-id="82e15-103">Pomocník `invalidFunctionPointerInDelegate` spravovaného ladění (MDA) je aktivován, pokud je předán neplatný ukazatel na funkci, aby bylo možné vytvořit delegáta nad ukazatelem nativní funkce.</span><span class="sxs-lookup"><span data-stu-id="82e15-103">The `invalidFunctionPointerInDelegate` managed debugging assistant (MDA) is activated when an invalid function pointer is passed in to construct a delegate over a native function pointer.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="82e15-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="82e15-104">Symptoms</span></span>  
 <span data-ttu-id="82e15-105">Při použití delegáta přes ukazatel na funkci došlo k narušení přístupu nebo neočekávanému poškození paměti.</span><span class="sxs-lookup"><span data-stu-id="82e15-105">Access violations or unexpected memory corruption when using a delegate over a function pointer.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="82e15-106">příčina</span><span class="sxs-lookup"><span data-stu-id="82e15-106">Cause</span></span>  
 <span data-ttu-id="82e15-107">Byl zadán neplatný ukazatel na funkci.</span><span class="sxs-lookup"><span data-stu-id="82e15-107">An invalid function pointer was specified.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="82e15-108">Řešení</span><span class="sxs-lookup"><span data-stu-id="82e15-108">Resolution</span></span>  
 <span data-ttu-id="82e15-109">Zadejte platný ukazatel na funkci.</span><span class="sxs-lookup"><span data-stu-id="82e15-109">Specify a valid function pointer</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="82e15-110">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="82e15-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="82e15-111">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="82e15-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="82e15-112">Výstup</span><span class="sxs-lookup"><span data-stu-id="82e15-112">Output</span></span>  
 <span data-ttu-id="82e15-113">Neplatný ukazatel na funkci.</span><span class="sxs-lookup"><span data-stu-id="82e15-113">The invalid function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="82e15-114">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="82e15-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="82e15-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82e15-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="82e15-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="82e15-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="82e15-117">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="82e15-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
