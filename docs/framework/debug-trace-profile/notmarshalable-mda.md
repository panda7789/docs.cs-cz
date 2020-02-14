---
title: notMarshalable – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), interface pointer not marshalable
- interface pointer not marshalable MDA
- MDAs (managed debugging assistants), interface pointer not marshalable
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- marshalable interface pointers
- MDAs (managed debugging assistants), marshaling
- notMarshalable MDA
ms.assetid: 96e7b2c1-843f-4d64-b519-740c3a18b50a
ms.openlocfilehash: 45db0e70b2446fa6e3175409bcc3844042f0acc0
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217289"
---
# <a name="notmarshalable-mda"></a><span data-ttu-id="40453-102">notMarshalable – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="40453-102">notMarshalable MDA</span></span>
<span data-ttu-id="40453-103">Pokud modul CLR (Common Language Runtime) nalezne ukazatel rozhraní modelu COM bez platného registrovaného proxy/zástupné procedury nebo nesprávná implementace rozhraní `IMarshal` při pokusu o zařazování rozhraní napříč kontexty, aktivuje se Pomocník pro `notMarshalable` spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="40453-103">The `notMarshalable` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters a COM interface pointer without a valid registered proxy/stub or an incorrect `IMarshal` interface implementation while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="40453-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="40453-104">Symptoms</span></span>  
 <span data-ttu-id="40453-105">Volání nejsou obsluhovaná nebo se volání vyskytují v nesprávném kontextu ukazatelů rozhraní modelu COM.</span><span class="sxs-lookup"><span data-stu-id="40453-105">Calls are not serviced, or calls occur in the wrong context for COM interface pointers.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="40453-106">Příčina</span><span class="sxs-lookup"><span data-stu-id="40453-106">Cause</span></span>  
 <span data-ttu-id="40453-107">Při pokusu o zařazení rozhraní mezi kontexty není k dispozici žádné platné registrované proxy/zástupné procedury nebo nesprávná `IMarshal`.</span><span class="sxs-lookup"><span data-stu-id="40453-107">No valid registered proxy/stub or an incorrect `IMarshal` while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="40453-108">Řešení</span><span class="sxs-lookup"><span data-stu-id="40453-108">Resolution</span></span>  
 <span data-ttu-id="40453-109">Ujistěte se, že máte registrovanou zástupnou proceduru proxy a že implementace `IMarshal` je platná.</span><span class="sxs-lookup"><span data-stu-id="40453-109">Make sure you have a proxy stub registered and that the `IMarshal` implementation is valid.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="40453-110">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="40453-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="40453-111">Tento MDA nemá žádný vliv na modul runtime.</span><span class="sxs-lookup"><span data-stu-id="40453-111">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="40453-112">Výstup</span><span class="sxs-lookup"><span data-stu-id="40453-112">Output</span></span>  
 <span data-ttu-id="40453-113">Zpráva s popisem problému.</span><span class="sxs-lookup"><span data-stu-id="40453-113">A message describing the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="40453-114">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="40453-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="40453-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="40453-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="40453-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="40453-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="40453-117">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="40453-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
