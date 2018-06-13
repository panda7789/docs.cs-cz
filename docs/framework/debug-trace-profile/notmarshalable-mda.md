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
ms.openlocfilehash: c52f104228db0b9e7f664ee7c1de393aa696c71a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386727"
---
# <a name="notmarshalable-mda"></a><span data-ttu-id="a1a8a-102">notMarshalable – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="a1a8a-102">notMarshalable MDA</span></span>
<span data-ttu-id="a1a8a-103">`notMarshalable` Pomocník spravovaného ladění (MDA) se aktivuje, když se modul CLR (CLR) setká ukazatele rozhraní modelu COM bez platné registrované proxy nebo zástupnou proceduru nebo nesprávné `IMarshal` implementace při pokusu o rozhraní zařazování rozhraní mezi kontexty.</span><span class="sxs-lookup"><span data-stu-id="a1a8a-103">The `notMarshalable` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters a COM interface pointer without a valid registered proxy/stub or an incorrect `IMarshal` interface implementation while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a1a8a-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="a1a8a-104">Symptoms</span></span>  
 <span data-ttu-id="a1a8a-105">Nejsou servis volání nebo volání, ke kterým došlo v nesprávný kontext ukazatele rozhraní COM.</span><span class="sxs-lookup"><span data-stu-id="a1a8a-105">Calls are not serviced, or calls occur in the wrong context for COM interface pointers.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a1a8a-106">příčina</span><span class="sxs-lookup"><span data-stu-id="a1a8a-106">Cause</span></span>  
 <span data-ttu-id="a1a8a-107">Žádný platný registrované proxy/stub nebo nesprávné `IMarshal` při pokusu o zařazování rozhraní mezi kontexty.</span><span class="sxs-lookup"><span data-stu-id="a1a8a-107">No valid registered proxy/stub or an incorrect `IMarshal` while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a1a8a-108">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="a1a8a-108">Resolution</span></span>  
 <span data-ttu-id="a1a8a-109">Zajistěte, aby byla proxy se zakázaným inzerováním zaregistrován a zda `IMarshal` implementace je platný.</span><span class="sxs-lookup"><span data-stu-id="a1a8a-109">Make sure you have a proxy stub registered and that the `IMarshal` implementation is valid.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a1a8a-110">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="a1a8a-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="a1a8a-111">Tato MDA nemá žádný vliv na modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a1a8a-111">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a1a8a-112">Výstup</span><span class="sxs-lookup"><span data-stu-id="a1a8a-112">Output</span></span>  
 <span data-ttu-id="a1a8a-113">Zpráva s popisem problému.</span><span class="sxs-lookup"><span data-stu-id="a1a8a-113">A message describing the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a1a8a-114">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="a1a8a-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a1a8a-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1a8a-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="a1a8a-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="a1a8a-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="a1a8a-117">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="a1a8a-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
