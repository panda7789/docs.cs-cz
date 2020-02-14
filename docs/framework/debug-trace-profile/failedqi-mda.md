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
ms.openlocfilehash: 4c36ec514645a38ef1228e76bdf6dbd06e886bae
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217509"
---
# <a name="failedqi-mda"></a><span data-ttu-id="ab658-102">failedQI – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="ab658-102">failedQI MDA</span></span>
<span data-ttu-id="ab658-103">Pokud běhové prostředí za běhu `QueryInterface` na ukazatel rozhraní modelu COM za běhu RCW (), a volání `QueryInterface` se nezdařilo, aktivuje se Pomocník pro správu spravovaného ladění (MDA). `failedQI`</span><span class="sxs-lookup"><span data-stu-id="ab658-103">The `failedQI` managed debugging assistant (MDA) is activated when the runtime calls `QueryInterface` on a COM interface pointer on behalf of a runtime callable wrapper (RCW), and the `QueryInterface` call fails.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="ab658-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="ab658-104">Symptoms</span></span>  
 <span data-ttu-id="ab658-105">Přetypování na RCW se nepovedlo nebo se neočekávaně vyvolá volání modelu COM z RCW.</span><span class="sxs-lookup"><span data-stu-id="ab658-105">A cast on an RCW fails, or a call to COM from an RCW fails unexpectedly.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="ab658-106">Příčina</span><span class="sxs-lookup"><span data-stu-id="ab658-106">Cause</span></span>  
  
- <span data-ttu-id="ab658-107">Volání bylo provedeno z chybného kontextu.</span><span class="sxs-lookup"><span data-stu-id="ab658-107">The call is made from the wrong context.</span></span>  
  
- <span data-ttu-id="ab658-108">Registrovaný proxy server selhává `QueryInterface` volání, protože došlo k pokusu o volání v nesprávném kontextu.</span><span class="sxs-lookup"><span data-stu-id="ab658-108">The registered proxy is failing the `QueryInterface` call because the call was attempted in the wrong context.</span></span>  
  
- <span data-ttu-id="ab658-109">Proxy ve vlastnictví OLE vrátil chybu HRESULT.</span><span class="sxs-lookup"><span data-stu-id="ab658-109">An OLE-owned proxy returned a failure HRESULT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="ab658-110">Řešení</span><span class="sxs-lookup"><span data-stu-id="ab658-110">Resolution</span></span>  
 <span data-ttu-id="ab658-111">Prohlédněte si dokumentaci MSDN o pravidlech modelu COM.</span><span class="sxs-lookup"><span data-stu-id="ab658-111">See the MSDN documentation on COM rules.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ab658-112">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="ab658-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="ab658-113">Selže-li `QueryInterface` volání, je kontext přepnut a je znovu proveden pokus o `QueryInterface` volání, aby bylo možné zjistit, zda došlo k chybě v nesprávném kontextu.</span><span class="sxs-lookup"><span data-stu-id="ab658-113">If a `QueryInterface` call fails, the context is switched and the `QueryInterface` call is attempted again to see if an incorrect context was at fault.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ab658-114">Výstup</span><span class="sxs-lookup"><span data-stu-id="ab658-114">Output</span></span>  
 <span data-ttu-id="ab658-115">Spravovaný název rozhraní, identifikátor GUID rozhraní a hodnota HRESULT selhání.</span><span class="sxs-lookup"><span data-stu-id="ab658-115">The managed name of the interface, the GUID of the interface, and the HRESULT of the failure.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="ab658-116">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="ab658-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab658-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab658-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="ab658-118">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="ab658-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="ab658-119">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="ab658-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
