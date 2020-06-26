---
title: failedQI – pomocník spravovaného ladění (MDA)
description: Přečtěte si téma Failedqi – Managed Debugging Assistant (MDA) v rozhraní .NET, které může být aktivováno, když se přetypování nebo volání modelu COM z obálky s voláním metody runtime (RCW) nezdařilo.
ms.date: 03/30/2017
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
ms.openlocfilehash: 2d7f14c67d47e58bcb88eab4621df63d7c598a7a
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415937"
---
# <a name="failedqi-mda"></a><span data-ttu-id="5c172-103">failedQI – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="5c172-103">failedQI MDA</span></span>
<span data-ttu-id="5c172-104">`failedQI`Pomocník spravovaného ladění (MDA) je aktivován při volání za běhu `QueryInterface` v ukazateli rozhraní modelu COM za běhu s voláním obálky (RCW) za běhu a `QueryInterface` volání se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="5c172-104">The `failedQI` managed debugging assistant (MDA) is activated when the runtime calls `QueryInterface` on a COM interface pointer on behalf of a runtime callable wrapper (RCW), and the `QueryInterface` call fails.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5c172-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="5c172-105">Symptoms</span></span>  
 <span data-ttu-id="5c172-106">Přetypování na RCW se nepovedlo nebo se neočekávaně vyvolá volání modelu COM z RCW.</span><span class="sxs-lookup"><span data-stu-id="5c172-106">A cast on an RCW fails, or a call to COM from an RCW fails unexpectedly.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5c172-107">Příčina</span><span class="sxs-lookup"><span data-stu-id="5c172-107">Cause</span></span>  
  
- <span data-ttu-id="5c172-108">Volání bylo provedeno z chybného kontextu.</span><span class="sxs-lookup"><span data-stu-id="5c172-108">The call is made from the wrong context.</span></span>  
  
- <span data-ttu-id="5c172-109">Registrovaný proxy server selhává při volání, `QueryInterface` protože došlo k pokusu o volání v nesprávném kontextu.</span><span class="sxs-lookup"><span data-stu-id="5c172-109">The registered proxy is failing the `QueryInterface` call because the call was attempted in the wrong context.</span></span>  
  
- <span data-ttu-id="5c172-110">Proxy ve vlastnictví OLE vrátil chybu HRESULT.</span><span class="sxs-lookup"><span data-stu-id="5c172-110">An OLE-owned proxy returned a failure HRESULT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="5c172-111">Řešení</span><span class="sxs-lookup"><span data-stu-id="5c172-111">Resolution</span></span>  
 <span data-ttu-id="5c172-112">Prohlédněte si dokumentaci MSDN o pravidlech modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5c172-112">See the MSDN documentation on COM rules.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5c172-113">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="5c172-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="5c172-114">Pokud `QueryInterface` volání selže, kontext je přepnut a `QueryInterface` volání se znovu pokusí zjistit, zda došlo k chybě v nesprávném kontextu.</span><span class="sxs-lookup"><span data-stu-id="5c172-114">If a `QueryInterface` call fails, the context is switched and the `QueryInterface` call is attempted again to see if an incorrect context was at fault.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5c172-115">Výstup</span><span class="sxs-lookup"><span data-stu-id="5c172-115">Output</span></span>  
 <span data-ttu-id="5c172-116">Spravovaný název rozhraní, identifikátor GUID rozhraní a hodnota HRESULT selhání.</span><span class="sxs-lookup"><span data-stu-id="5c172-116">The managed name of the interface, the GUID of the interface, and the HRESULT of the failure.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="5c172-117">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="5c172-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c172-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c172-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="5c172-119">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="5c172-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="5c172-120">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="5c172-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
