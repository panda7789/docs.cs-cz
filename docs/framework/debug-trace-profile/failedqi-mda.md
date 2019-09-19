---
title: failedQI – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fec1bfb402f3b394ceb36590c3a880f82c5cb101
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052785"
---
# <a name="failedqi-mda"></a><span data-ttu-id="a070f-102">failedQI – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="a070f-102">failedQI MDA</span></span>
<span data-ttu-id="a070f-103">Pomocník spravovaného ladění (MDA) je aktivován při volání `QueryInterface` za běhu v ukazateli rozhraní modelu COM za běhu s voláním obálky (RCW) za běhu a `QueryInterface` volání se nezdařilo. `failedQI`</span><span class="sxs-lookup"><span data-stu-id="a070f-103">The `failedQI` managed debugging assistant (MDA) is activated when the runtime calls `QueryInterface` on a COM interface pointer on behalf of a runtime callable wrapper (RCW), and the `QueryInterface` call fails.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a070f-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="a070f-104">Symptoms</span></span>  
 <span data-ttu-id="a070f-105">Přetypování na RCW se nepovedlo nebo se neočekávaně vyvolá volání modelu COM z RCW.</span><span class="sxs-lookup"><span data-stu-id="a070f-105">A cast on an RCW fails, or a call to COM from an RCW fails unexpectedly.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a070f-106">příčina</span><span class="sxs-lookup"><span data-stu-id="a070f-106">Cause</span></span>  
  
- <span data-ttu-id="a070f-107">Volání bylo provedeno z chybného kontextu.</span><span class="sxs-lookup"><span data-stu-id="a070f-107">The call is made from the wrong context.</span></span>  
  
- <span data-ttu-id="a070f-108">Registrovaný proxy server selhává `QueryInterface` při volání, protože došlo k pokusu o volání v nesprávném kontextu.</span><span class="sxs-lookup"><span data-stu-id="a070f-108">The registered proxy is failing the `QueryInterface` call because the call was attempted in the wrong context.</span></span>  
  
- <span data-ttu-id="a070f-109">Proxy ve vlastnictví OLE vrátil chybu HRESULT.</span><span class="sxs-lookup"><span data-stu-id="a070f-109">An OLE-owned proxy returned a failure HRESULT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a070f-110">Řešení</span><span class="sxs-lookup"><span data-stu-id="a070f-110">Resolution</span></span>  
 <span data-ttu-id="a070f-111">Prohlédněte si dokumentaci MSDN o pravidlech modelu COM.</span><span class="sxs-lookup"><span data-stu-id="a070f-111">See the MSDN documentation on COM rules.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a070f-112">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="a070f-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="a070f-113">Pokud volání selže, kontext je přepnut `QueryInterface` a volání se znovu pokusí zjistit, zda došlo k chybě v nesprávném kontextu. `QueryInterface`</span><span class="sxs-lookup"><span data-stu-id="a070f-113">If a `QueryInterface` call fails, the context is switched and the `QueryInterface` call is attempted again to see if an incorrect context was at fault.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a070f-114">Výstup</span><span class="sxs-lookup"><span data-stu-id="a070f-114">Output</span></span>  
 <span data-ttu-id="a070f-115">Spravovaný název rozhraní, identifikátor GUID rozhraní a hodnota HRESULT selhání.</span><span class="sxs-lookup"><span data-stu-id="a070f-115">The managed name of the interface, the GUID of the interface, and the HRESULT of the failure.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a070f-116">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="a070f-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a070f-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a070f-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="a070f-118">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="a070f-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="a070f-119">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="a070f-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
