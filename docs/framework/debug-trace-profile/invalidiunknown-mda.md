---
title: "invalidIUnknown – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 04fdc96168823397296449ebc25ccdded1ea55c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="795cb-102">invalidIUnknown – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="795cb-102">invalidIUnknown MDA</span></span>
<span data-ttu-id="795cb-103">`invalidIUnknown` Pomocník spravovaného ladění (MDA) se aktivuje, když neplatný `IUnknown` ukazatel je předán do spravovaného kódu z nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="795cb-103">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="795cb-104">`IUnknown` Nevrátí úspěch při dotázána ohledně `IUnknown` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="795cb-104">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="795cb-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="795cb-105">Symptoms</span></span>  
 <span data-ttu-id="795cb-106">Při zařazování ukazatele rozhraní COM při zařazování argument dojde k neočekávané chybě.</span><span class="sxs-lookup"><span data-stu-id="795cb-106">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="795cb-107">příčina</span><span class="sxs-lookup"><span data-stu-id="795cb-107">Cause</span></span>  
 <span data-ttu-id="795cb-108">Nesprávné `QueryInterface` implementace na rozhraní COM předaný modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="795cb-108">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="795cb-109">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="795cb-109">Resolution</span></span>  
 <span data-ttu-id="795cb-110">Opravte `QueryInterface` implementace.</span><span class="sxs-lookup"><span data-stu-id="795cb-110">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="795cb-111">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="795cb-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="795cb-112">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="795cb-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="795cb-113">Výstup</span><span class="sxs-lookup"><span data-stu-id="795cb-113">Output</span></span>  
 <span data-ttu-id="795cb-114">Popis chyby.</span><span class="sxs-lookup"><span data-stu-id="795cb-114">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="795cb-115">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="795cb-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="795cb-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="795cb-116">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="795cb-117">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="795cb-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="795cb-118">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="795cb-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
