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
ms.openlocfilehash: edf1fe3ee5be631f7f3c42f4a6cdb17f1be722cf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216199"
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="691fb-102">raceOnRCWCleanup – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="691fb-102">raceOnRCWCleanup MDA</span></span>
<span data-ttu-id="691fb-103">Pokud modul CLR (Common Language Runtime) zjistí, že se používá [obálka](../../standard/native-interop/runtime-callable-wrapper.md) RCW (Runtime), je-li volání k vydání vyvoláno pomocí příkazu, jako je například metoda <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>, je aktivována pomocná aplikace `raceOnRCWCleanup` Managed Debugging Assistant (MDA).</span><span class="sxs-lookup"><span data-stu-id="691fb-103">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="691fb-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="691fb-104">Symptoms</span></span>  
 <span data-ttu-id="691fb-105">Porušení přístupu nebo poškození paměti během nebo po uvolnění RCW pomocí <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> nebo podobné metody.</span><span class="sxs-lookup"><span data-stu-id="691fb-105">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="691fb-106">Příčina</span><span class="sxs-lookup"><span data-stu-id="691fb-106">Cause</span></span>  
 <span data-ttu-id="691fb-107">RCW se používá v jiném vlákně nebo v uvolňování zásobníku vláken.</span><span class="sxs-lookup"><span data-stu-id="691fb-107">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="691fb-108">RCW, který se používá, nelze uvolnit.</span><span class="sxs-lookup"><span data-stu-id="691fb-108">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="691fb-109">Řešení</span><span class="sxs-lookup"><span data-stu-id="691fb-109">Resolution</span></span>  
 <span data-ttu-id="691fb-110">Neuvolňujte RCW, které by bylo možné použít v aktuálním nebo jiném vlákně.</span><span class="sxs-lookup"><span data-stu-id="691fb-110">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="691fb-111">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="691fb-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="691fb-112">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="691fb-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="691fb-113">Výstup</span><span class="sxs-lookup"><span data-stu-id="691fb-113">Output</span></span>  
 <span data-ttu-id="691fb-114">Zpráva popisující chybu</span><span class="sxs-lookup"><span data-stu-id="691fb-114">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="691fb-115">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="691fb-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="691fb-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="691fb-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="691fb-117">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="691fb-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="691fb-118">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="691fb-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
