---
title: invalidIUnknown – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění invalidIUnknown – (MDA), který se aktivuje při předání neplatného ukazatele IUnknown do spravovaného kódu z nativního kódu.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
ms.openlocfilehash: 65d704463ed746390ff1710b590bf080013bf53d
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051724"
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="7939f-103">invalidIUnknown – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="7939f-103">invalidIUnknown MDA</span></span>
<span data-ttu-id="7939f-104">`invalidIUnknown`Pokud `IUnknown` je do spravovaného kódu z nativního kódu předán neplatný ukazatel, je aktivován pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="7939f-104">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="7939f-105">`IUnknown`Při dotazování na rozhraní se nezdařila operace vrácení `IUnknown` .</span><span class="sxs-lookup"><span data-stu-id="7939f-105">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="7939f-106">Příznaky</span><span class="sxs-lookup"><span data-stu-id="7939f-106">Symptoms</span></span>  
 <span data-ttu-id="7939f-107">Při zařazování ukazatele rozhraní modelu COM během zařazování argumentů dojde k neočekávané chybě.</span><span class="sxs-lookup"><span data-stu-id="7939f-107">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="7939f-108">Příčina</span><span class="sxs-lookup"><span data-stu-id="7939f-108">Cause</span></span>  
 <span data-ttu-id="7939f-109">Nesprávná `QueryInterface` implementace rozhraní COM předaných modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="7939f-109">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="7939f-110">Řešení</span><span class="sxs-lookup"><span data-stu-id="7939f-110">Resolution</span></span>  
 <span data-ttu-id="7939f-111">Opravte `QueryInterface` implementaci.</span><span class="sxs-lookup"><span data-stu-id="7939f-111">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="7939f-112">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="7939f-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="7939f-113">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="7939f-113">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="7939f-114">Výstup</span><span class="sxs-lookup"><span data-stu-id="7939f-114">Output</span></span>  
 <span data-ttu-id="7939f-115">Popis chyby.</span><span class="sxs-lookup"><span data-stu-id="7939f-115">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="7939f-116">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="7939f-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7939f-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="7939f-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="7939f-118">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="7939f-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="7939f-119">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="7939f-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
