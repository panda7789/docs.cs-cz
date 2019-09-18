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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ddb6b0b5c2248d215245e0f881c8e7c91b13e480
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052432"
---
# <a name="notmarshalable-mda"></a><span data-ttu-id="e9514-102">notMarshalable – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="e9514-102">notMarshalable MDA</span></span>
<span data-ttu-id="e9514-103">Pomocník spravovaného ladění (MDA) je aktivován, pokud modul CLR (Common Language Runtime) nalezne ukazatel rozhraní modelu COM bez platného registrovaného proxy/zástupné `IMarshal` procedury nebo nesprávná implementace rozhraní při pokusu o `notMarshalable` zařazování rozhraní napříč kontexty.</span><span class="sxs-lookup"><span data-stu-id="e9514-103">The `notMarshalable` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters a COM interface pointer without a valid registered proxy/stub or an incorrect `IMarshal` interface implementation while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e9514-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="e9514-104">Symptoms</span></span>  
 <span data-ttu-id="e9514-105">Volání nejsou obsluhovaná nebo se volání vyskytují v nesprávném kontextu ukazatelů rozhraní modelu COM.</span><span class="sxs-lookup"><span data-stu-id="e9514-105">Calls are not serviced, or calls occur in the wrong context for COM interface pointers.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e9514-106">příčina</span><span class="sxs-lookup"><span data-stu-id="e9514-106">Cause</span></span>  
 <span data-ttu-id="e9514-107">Při pokusu o zařazování rozhraní napříč kontexty není k dispozici žádný platný registrovaný proxy/zástupný kód nebo nesprávný `IMarshal` .</span><span class="sxs-lookup"><span data-stu-id="e9514-107">No valid registered proxy/stub or an incorrect `IMarshal` while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e9514-108">Řešení</span><span class="sxs-lookup"><span data-stu-id="e9514-108">Resolution</span></span>  
 <span data-ttu-id="e9514-109">Ujistěte se, že máte registrovanou zástupnou proceduru `IMarshal` proxy a že je implementace platná.</span><span class="sxs-lookup"><span data-stu-id="e9514-109">Make sure you have a proxy stub registered and that the `IMarshal` implementation is valid.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e9514-110">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="e9514-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="e9514-111">Tento MDA nemá žádný vliv na modul runtime.</span><span class="sxs-lookup"><span data-stu-id="e9514-111">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e9514-112">Výstup</span><span class="sxs-lookup"><span data-stu-id="e9514-112">Output</span></span>  
 <span data-ttu-id="e9514-113">Zpráva s popisem problému.</span><span class="sxs-lookup"><span data-stu-id="e9514-113">A message describing the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="e9514-114">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="e9514-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e9514-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e9514-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="e9514-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="e9514-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="e9514-117">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="e9514-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
