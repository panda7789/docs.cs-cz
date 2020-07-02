---
title: raceOnRCWCleanup – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění raceOnRCWCleanup – (MDA), který se aktivuje, pokud se RCW používá v jiném vlákně nebo na uvolňování zásobníku vláken v rozhraní .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
ms.openlocfilehash: e86ef96bebb648c7927ae5fec8b68fc4429b268b
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803648"
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="f28a4-103">raceOnRCWCleanup – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="f28a4-103">raceOnRCWCleanup MDA</span></span>
<span data-ttu-id="f28a4-104">`raceOnRCWCleanup`Pomocník spravovaného ladění (MDA) je aktivován, když modul CLR (Common Language Runtime) zjistí, že se používá obálka s voláním [za běhu](../../standard/native-interop/runtime-callable-wrapper.md) (RCW), když volání uvolní, je provedeno pomocí příkazu, jako je například <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="f28a4-104">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f28a4-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="f28a4-105">Symptoms</span></span>  
 <span data-ttu-id="f28a4-106">Porušení přístupu nebo poškození paměti během nebo po uvolnění RCW pomocí <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> nebo podobné metody.</span><span class="sxs-lookup"><span data-stu-id="f28a4-106">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f28a4-107">Příčina</span><span class="sxs-lookup"><span data-stu-id="f28a4-107">Cause</span></span>  
 <span data-ttu-id="f28a4-108">RCW se používá v jiném vlákně nebo v uvolňování zásobníku vláken.</span><span class="sxs-lookup"><span data-stu-id="f28a4-108">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="f28a4-109">RCW, který se používá, nelze uvolnit.</span><span class="sxs-lookup"><span data-stu-id="f28a4-109">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f28a4-110">Řešení</span><span class="sxs-lookup"><span data-stu-id="f28a4-110">Resolution</span></span>  
 <span data-ttu-id="f28a4-111">Neuvolňujte RCW, které by bylo možné použít v aktuálním nebo jiném vlákně.</span><span class="sxs-lookup"><span data-stu-id="f28a4-111">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f28a4-112">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="f28a4-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="f28a4-113">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="f28a4-113">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f28a4-114">Výstup</span><span class="sxs-lookup"><span data-stu-id="f28a4-114">Output</span></span>  
 <span data-ttu-id="f28a4-115">Zpráva popisující chybu</span><span class="sxs-lookup"><span data-stu-id="f28a4-115">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="f28a4-116">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="f28a4-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f28a4-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f28a4-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="f28a4-118">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="f28a4-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="f28a4-119">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="f28a4-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
