---
title: "notMarshalable – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 489f0e2ff4dc1eeaa9721ec6cf59faad0bee2ca8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="notmarshalable-mda"></a><span data-ttu-id="5e99f-102">notMarshalable – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="5e99f-102">notMarshalable MDA</span></span>
<span data-ttu-id="5e99f-103">`notMarshalable` Pomocník spravovaného ladění (MDA) se aktivuje, když se modul CLR (CLR) setká ukazatele rozhraní modelu COM bez platné registrované proxy nebo zástupnou proceduru nebo nesprávné `IMarshal` implementace při pokusu o rozhraní zařazování rozhraní mezi kontexty.</span><span class="sxs-lookup"><span data-stu-id="5e99f-103">The `notMarshalable` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters a COM interface pointer without a valid registered proxy/stub or an incorrect `IMarshal` interface implementation while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5e99f-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="5e99f-104">Symptoms</span></span>  
 <span data-ttu-id="5e99f-105">Nejsou servis volání nebo volání, ke kterým došlo v nesprávný kontext ukazatele rozhraní COM.</span><span class="sxs-lookup"><span data-stu-id="5e99f-105">Calls are not serviced, or calls occur in the wrong context for COM interface pointers.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5e99f-106">příčina</span><span class="sxs-lookup"><span data-stu-id="5e99f-106">Cause</span></span>  
 <span data-ttu-id="5e99f-107">Žádný platný registrované proxy/stub nebo nesprávné `IMarshal` při pokusu o zařazování rozhraní mezi kontexty.</span><span class="sxs-lookup"><span data-stu-id="5e99f-107">No valid registered proxy/stub or an incorrect `IMarshal` while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="5e99f-108">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="5e99f-108">Resolution</span></span>  
 <span data-ttu-id="5e99f-109">Zajistěte, aby byla proxy se zakázaným inzerováním zaregistrován a zda `IMarshal` implementace je platný.</span><span class="sxs-lookup"><span data-stu-id="5e99f-109">Make sure you have a proxy stub registered and that the `IMarshal` implementation is valid.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5e99f-110">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="5e99f-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="5e99f-111">Tato MDA nemá žádný vliv na modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="5e99f-111">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5e99f-112">Výstup</span><span class="sxs-lookup"><span data-stu-id="5e99f-112">Output</span></span>  
 <span data-ttu-id="5e99f-113">Zpráva s popisem problému.</span><span class="sxs-lookup"><span data-stu-id="5e99f-113">A message describing the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="5e99f-114">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="5e99f-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e99f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e99f-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="5e99f-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="5e99f-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="5e99f-117">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="5e99f-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
