---
title: "failedQI – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 87fe67e1e64d69912095e1d9587d277805a3eb80
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="failedqi-mda"></a><span data-ttu-id="21d58-102">failedQI – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="21d58-102">failedQI MDA</span></span>
<span data-ttu-id="21d58-103">`failedQI` Pomocník spravovaného ladění (MDA) se aktivuje při volání modulu runtime `QueryInterface` na ukazatel rozhraní COM jménem obálka volatelná aplikacemi runtime (RCW) a `QueryInterface` volání selže.</span><span class="sxs-lookup"><span data-stu-id="21d58-103">The `failedQI` managed debugging assistant (MDA) is activated when the runtime calls `QueryInterface` on a COM interface pointer on behalf of a runtime callable wrapper (RCW), and the `QueryInterface` call fails.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="21d58-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="21d58-104">Symptoms</span></span>  
 <span data-ttu-id="21d58-105">Přetypování na RCW selže nebo volání COM z RCW neočekávaně selže.</span><span class="sxs-lookup"><span data-stu-id="21d58-105">A cast on an RCW fails, or a call to COM from an RCW fails unexpectedly.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="21d58-106">příčina</span><span class="sxs-lookup"><span data-stu-id="21d58-106">Cause</span></span>  
  
-   <span data-ttu-id="21d58-107">Přišla z nesprávného kontextu.</span><span class="sxs-lookup"><span data-stu-id="21d58-107">The call is made from the wrong context.</span></span>  
  
-   <span data-ttu-id="21d58-108">Registrovaný proxy selhává `QueryInterface` volat, protože došlo k pokusu o volání v chybě kontextu.</span><span class="sxs-lookup"><span data-stu-id="21d58-108">The registered proxy is failing the `QueryInterface` call because the call was attempted in the wrong context.</span></span>  
  
-   <span data-ttu-id="21d58-109">Proxy služby vlastněných OLE vrátila chybu HRESULT.</span><span class="sxs-lookup"><span data-stu-id="21d58-109">An OLE-owned proxy returned a failure HRESULT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="21d58-110">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="21d58-110">Resolution</span></span>  
 <span data-ttu-id="21d58-111">V MSDN dokumentaci na COM pravidla.</span><span class="sxs-lookup"><span data-stu-id="21d58-111">See the MSDN documentation on COM rules.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="21d58-112">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="21d58-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="21d58-113">Pokud `QueryInterface` volání selže, kontext se přepnul a `QueryInterface` volání je opakovat pokus o chcete zobrazit, pokud byl nesprávný kontextu při selhání.</span><span class="sxs-lookup"><span data-stu-id="21d58-113">If a `QueryInterface` call fails, the context is switched and the `QueryInterface` call is attempted again to see if an incorrect context was at fault.</span></span>  
  
## <a name="output"></a><span data-ttu-id="21d58-114">Výstup</span><span class="sxs-lookup"><span data-stu-id="21d58-114">Output</span></span>  
 <span data-ttu-id="21d58-115">Název spravovaného rozhraní, identifikátor GUID rozhraní a HRESULT selhání.</span><span class="sxs-lookup"><span data-stu-id="21d58-115">The managed name of the interface, the GUID of the interface, and the HRESULT of the failure.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="21d58-116">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="21d58-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="21d58-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="21d58-117">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="21d58-118">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="21d58-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="21d58-119">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="21d58-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
