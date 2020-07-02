---
title: notMarshalable – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění notMarshalable, který se může aktivovat v případě, že volání nejsou obsluhovaná nebo se nevyskytují v nesprávném kontextu ukazatelů rozhraní modelu COM.
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
ms.openlocfilehash: b464d914a8d83504daaf4cb276914da7798262dc
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803791"
---
# <a name="notmarshalable-mda"></a><span data-ttu-id="98ef4-103">notMarshalable – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="98ef4-103">notMarshalable MDA</span></span>
<span data-ttu-id="98ef4-104">`notMarshalable`Pokud modul CLR (Common Language Runtime) nalezne ukazatel rozhraní modelu COM bez platného registrovaného proxy/zástupné procedury nebo nesprávná `IMarshal` implementace rozhraní při pokusu o zařazování rozhraní napříč kontexty, aktivuje se pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="98ef4-104">The `notMarshalable` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters a COM interface pointer without a valid registered proxy/stub or an incorrect `IMarshal` interface implementation while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="98ef4-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="98ef4-105">Symptoms</span></span>  
 <span data-ttu-id="98ef4-106">Volání nejsou obsluhovaná nebo se volání vyskytují v nesprávném kontextu ukazatelů rozhraní modelu COM.</span><span class="sxs-lookup"><span data-stu-id="98ef4-106">Calls are not serviced, or calls occur in the wrong context for COM interface pointers.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="98ef4-107">Příčina</span><span class="sxs-lookup"><span data-stu-id="98ef4-107">Cause</span></span>  
 <span data-ttu-id="98ef4-108">`IMarshal`Při pokusu o zařazování rozhraní napříč kontexty není k dispozici žádný platný registrovaný proxy/zástupný kód nebo nesprávný.</span><span class="sxs-lookup"><span data-stu-id="98ef4-108">No valid registered proxy/stub or an incorrect `IMarshal` while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="98ef4-109">Řešení</span><span class="sxs-lookup"><span data-stu-id="98ef4-109">Resolution</span></span>  
 <span data-ttu-id="98ef4-110">Ujistěte se, že máte registrovanou zástupnou proceduru proxy a že `IMarshal` je implementace platná.</span><span class="sxs-lookup"><span data-stu-id="98ef4-110">Make sure you have a proxy stub registered and that the `IMarshal` implementation is valid.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="98ef4-111">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="98ef4-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="98ef4-112">Tento MDA nemá žádný vliv na modul runtime.</span><span class="sxs-lookup"><span data-stu-id="98ef4-112">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="98ef4-113">Výstup</span><span class="sxs-lookup"><span data-stu-id="98ef4-113">Output</span></span>  
 <span data-ttu-id="98ef4-114">Zpráva s popisem problému.</span><span class="sxs-lookup"><span data-stu-id="98ef4-114">A message describing the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="98ef4-115">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="98ef4-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="98ef4-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="98ef4-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="98ef4-117">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="98ef4-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="98ef4-118">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="98ef4-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
