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
ms.openlocfilehash: ea7f48ab61c16cb0430717074f1b1feab4827763
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052597"
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="23d87-102">invalidIUnknown – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="23d87-102">invalidIUnknown MDA</span></span>
<span data-ttu-id="23d87-103">Pokud je do spravovaného kódu z nativního kódu předán neplatný `IUnknown` ukazatel, je aktivován pomocník spravovanéholadění(MDA).`invalidIUnknown`</span><span class="sxs-lookup"><span data-stu-id="23d87-103">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="23d87-104">Při `IUnknown` dotazování `IUnknown` na rozhraní se nezdařila operace vrácení.</span><span class="sxs-lookup"><span data-stu-id="23d87-104">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="23d87-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="23d87-105">Symptoms</span></span>  
 <span data-ttu-id="23d87-106">Při zařazování ukazatele rozhraní modelu COM během zařazování argumentů dojde k neočekávané chybě.</span><span class="sxs-lookup"><span data-stu-id="23d87-106">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="23d87-107">příčina</span><span class="sxs-lookup"><span data-stu-id="23d87-107">Cause</span></span>  
 <span data-ttu-id="23d87-108">Nesprávná `QueryInterface` implementace rozhraní COM předaných modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="23d87-108">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="23d87-109">Řešení</span><span class="sxs-lookup"><span data-stu-id="23d87-109">Resolution</span></span>  
 <span data-ttu-id="23d87-110">Opravte `QueryInterface` implementaci.</span><span class="sxs-lookup"><span data-stu-id="23d87-110">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="23d87-111">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="23d87-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="23d87-112">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="23d87-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="23d87-113">Výstup</span><span class="sxs-lookup"><span data-stu-id="23d87-113">Output</span></span>  
 <span data-ttu-id="23d87-114">Popis chyby</span><span class="sxs-lookup"><span data-stu-id="23d87-114">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="23d87-115">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="23d87-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="23d87-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="23d87-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="23d87-117">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="23d87-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="23d87-118">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="23d87-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
