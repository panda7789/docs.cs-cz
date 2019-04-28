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
ms.openlocfilehash: 30db07ddf935b5ce13b1fe4212f7f6a40270ae93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61753696"
---
# <a name="notmarshalable-mda"></a><span data-ttu-id="1e22a-102">notMarshalable – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="1e22a-102">notMarshalable MDA</span></span>
<span data-ttu-id="1e22a-103">`notMarshalable` Pomocníka spravovaného ladění (MDA) se aktivuje, když modul CLR (CLR) setká ukazatele rozhraní modelu COM bez platné registrované proxy/zástupné procedury nebo nesprávné `IMarshal` při pokusu o implementace rozhraní zařazování rozhraní napříč kontexty.</span><span class="sxs-lookup"><span data-stu-id="1e22a-103">The `notMarshalable` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters a COM interface pointer without a valid registered proxy/stub or an incorrect `IMarshal` interface implementation while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1e22a-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="1e22a-104">Symptoms</span></span>  
 <span data-ttu-id="1e22a-105">Volání nejsou obsluhovány nebo v chybném kontextu pro ukazatele rozhraní modelu COM dojde k volání.</span><span class="sxs-lookup"><span data-stu-id="1e22a-105">Calls are not serviced, or calls occur in the wrong context for COM interface pointers.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1e22a-106">Příčina</span><span class="sxs-lookup"><span data-stu-id="1e22a-106">Cause</span></span>  
 <span data-ttu-id="1e22a-107">Žádný platný registrované proxy nebo zástupné procedury nebo nesprávné `IMarshal` při pokusu o zařazení rozhraní napříč kontexty.</span><span class="sxs-lookup"><span data-stu-id="1e22a-107">No valid registered proxy/stub or an incorrect `IMarshal` while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1e22a-108">Řešení</span><span class="sxs-lookup"><span data-stu-id="1e22a-108">Resolution</span></span>  
 <span data-ttu-id="1e22a-109">Ujistěte se, že máte proxy zástupné procedury zaregistrované a že `IMarshal` implementace je platný.</span><span class="sxs-lookup"><span data-stu-id="1e22a-109">Make sure you have a proxy stub registered and that the `IMarshal` implementation is valid.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1e22a-110">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="1e22a-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="1e22a-111">Toto MDA nemá žádný vliv na modul runtime.</span><span class="sxs-lookup"><span data-stu-id="1e22a-111">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1e22a-112">Výstup</span><span class="sxs-lookup"><span data-stu-id="1e22a-112">Output</span></span>  
 <span data-ttu-id="1e22a-113">Zprávu s popisem problému.</span><span class="sxs-lookup"><span data-stu-id="1e22a-113">A message describing the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="1e22a-114">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="1e22a-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1e22a-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e22a-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="1e22a-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="1e22a-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="1e22a-117">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="1e22a-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
