---
title: raceOnRCWCleanup – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ca3b28d0d27af0a752de894f5856b76939b01e09
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967245"
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="646fc-102">raceOnRCWCleanup – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="646fc-102">raceOnRCWCleanup MDA</span></span>
<span data-ttu-id="646fc-103">Pomocník spravovaného ladění (MDA) je aktivován, když modul CLR (Common Language Runtime) zjistí, že se používá obálka s voláním [za běhu](../../standard/native-interop/runtime-callable-wrapper.md) (RCW), když volání uvolní, je provedeno pomocí příkazu, <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> jako je například metoda. `raceOnRCWCleanup`</span><span class="sxs-lookup"><span data-stu-id="646fc-103">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="646fc-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="646fc-104">Symptoms</span></span>  
 <span data-ttu-id="646fc-105">Porušení přístupu nebo poškození paměti během nebo po uvolnění RCW pomocí <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> nebo podobné metody.</span><span class="sxs-lookup"><span data-stu-id="646fc-105">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="646fc-106">příčina</span><span class="sxs-lookup"><span data-stu-id="646fc-106">Cause</span></span>  
 <span data-ttu-id="646fc-107">RCW se používá v jiném vlákně nebo v uvolňování zásobníku vláken.</span><span class="sxs-lookup"><span data-stu-id="646fc-107">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="646fc-108">RCW, který se používá, nelze uvolnit.</span><span class="sxs-lookup"><span data-stu-id="646fc-108">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="646fc-109">Řešení</span><span class="sxs-lookup"><span data-stu-id="646fc-109">Resolution</span></span>  
 <span data-ttu-id="646fc-110">Neuvolňujte RCW, které by bylo možné použít v aktuálním nebo jiném vlákně.</span><span class="sxs-lookup"><span data-stu-id="646fc-110">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="646fc-111">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="646fc-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="646fc-112">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="646fc-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="646fc-113">Výstup</span><span class="sxs-lookup"><span data-stu-id="646fc-113">Output</span></span>  
 <span data-ttu-id="646fc-114">Zpráva popisující chybu</span><span class="sxs-lookup"><span data-stu-id="646fc-114">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="646fc-115">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="646fc-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="646fc-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="646fc-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="646fc-117">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="646fc-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="646fc-118">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="646fc-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
