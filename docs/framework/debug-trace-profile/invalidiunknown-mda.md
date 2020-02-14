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
ms.openlocfilehash: 5df9a3f506d8c2de6f1a3125459adc2d59d510bf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217369"
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="89f08-102">invalidIUnknown – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="89f08-102">invalidIUnknown MDA</span></span>
<span data-ttu-id="89f08-103">V případě, že je do spravovaného kódu z nativního kódu předán neplatný ukazatel `IUnknown`, je aktivován Pomocník s `invalidIUnknown` Managed Debugging Assistant (MDA).</span><span class="sxs-lookup"><span data-stu-id="89f08-103">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="89f08-104">`IUnknown` se při dotazování na rozhraní `IUnknown` nepodařilo vrátit úspěch.</span><span class="sxs-lookup"><span data-stu-id="89f08-104">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="89f08-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="89f08-105">Symptoms</span></span>  
 <span data-ttu-id="89f08-106">Při zařazování ukazatele rozhraní modelu COM během zařazování argumentů dojde k neočekávané chybě.</span><span class="sxs-lookup"><span data-stu-id="89f08-106">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="89f08-107">Příčina</span><span class="sxs-lookup"><span data-stu-id="89f08-107">Cause</span></span>  
 <span data-ttu-id="89f08-108">Nesprávná implementace `QueryInterface` v rozhraní COM předanému modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="89f08-108">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="89f08-109">Řešení</span><span class="sxs-lookup"><span data-stu-id="89f08-109">Resolution</span></span>  
 <span data-ttu-id="89f08-110">Opravte implementaci `QueryInterface`.</span><span class="sxs-lookup"><span data-stu-id="89f08-110">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="89f08-111">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="89f08-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="89f08-112">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="89f08-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="89f08-113">Výstup</span><span class="sxs-lookup"><span data-stu-id="89f08-113">Output</span></span>  
 <span data-ttu-id="89f08-114">Popis chyby.</span><span class="sxs-lookup"><span data-stu-id="89f08-114">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="89f08-115">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="89f08-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="89f08-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="89f08-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="89f08-117">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="89f08-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="89f08-118">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="89f08-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
