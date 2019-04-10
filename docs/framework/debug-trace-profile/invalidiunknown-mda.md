---
title: invalidIUnknown – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 35560b966d5fba60ac35b2eb1e559e196fc868f5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223352"
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="e4dc3-102">invalidIUnknown – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="e4dc3-102">invalidIUnknown MDA</span></span>
<span data-ttu-id="e4dc3-103">`invalidIUnknown` Pomocníka spravovaného ladění (MDA) se aktivuje, když neplatný `IUnknown` předán ukazatel do spravovaného kódu z nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="e4dc3-103">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="e4dc3-104">`IUnknown` Nevrátí úspěch, když se dotázali `IUnknown` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e4dc3-104">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e4dc3-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="e4dc3-105">Symptoms</span></span>  
 <span data-ttu-id="e4dc3-106">Při zařazování při zařazování argument ukazatele rozhraní modelu COM, dojde k neočekávané chybě.</span><span class="sxs-lookup"><span data-stu-id="e4dc3-106">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e4dc3-107">Příčina</span><span class="sxs-lookup"><span data-stu-id="e4dc3-107">Cause</span></span>  
 <span data-ttu-id="e4dc3-108">Nesprávné `QueryInterface` implementace na rozhraní COM předán modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="e4dc3-108">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e4dc3-109">Řešení</span><span class="sxs-lookup"><span data-stu-id="e4dc3-109">Resolution</span></span>  
 <span data-ttu-id="e4dc3-110">Opravte `QueryInterface` implementace.</span><span class="sxs-lookup"><span data-stu-id="e4dc3-110">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e4dc3-111">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="e4dc3-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="e4dc3-112">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="e4dc3-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e4dc3-113">Výstup</span><span class="sxs-lookup"><span data-stu-id="e4dc3-113">Output</span></span>  
 <span data-ttu-id="e4dc3-114">Popis chyby.</span><span class="sxs-lookup"><span data-stu-id="e4dc3-114">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="e4dc3-115">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="e4dc3-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4dc3-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4dc3-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="e4dc3-117">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="e4dc3-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="e4dc3-118">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="e4dc3-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
