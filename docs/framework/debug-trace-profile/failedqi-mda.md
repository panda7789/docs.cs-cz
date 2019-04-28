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
ms.openlocfilehash: 0ac478644561d2aab13d10811987d8d02c8d7608
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754723"
---
# <a name="failedqi-mda"></a><span data-ttu-id="a9712-102">failedQI – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="a9712-102">failedQI MDA</span></span>
<span data-ttu-id="a9712-103">`failedQI` Pomocníka spravovaného ladění (MDA) se aktivuje, když modul runtime volá `QueryInterface` na ukazatele rozhraní modelu COM jménem obálka volatelná aplikacemi běhu (RCW) a `QueryInterface` volání selže.</span><span class="sxs-lookup"><span data-stu-id="a9712-103">The `failedQI` managed debugging assistant (MDA) is activated when the runtime calls `QueryInterface` on a COM interface pointer on behalf of a runtime callable wrapper (RCW), and the `QueryInterface` call fails.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a9712-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="a9712-104">Symptoms</span></span>  
 <span data-ttu-id="a9712-105">Přetypování na obálky RCW selže nebo volání COM z obálky RCW dojde k neočekávanému selhání.</span><span class="sxs-lookup"><span data-stu-id="a9712-105">A cast on an RCW fails, or a call to COM from an RCW fails unexpectedly.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a9712-106">Příčina</span><span class="sxs-lookup"><span data-stu-id="a9712-106">Cause</span></span>  
  
- <span data-ttu-id="a9712-107">Při volání z nesprávného kontextu.</span><span class="sxs-lookup"><span data-stu-id="a9712-107">The call is made from the wrong context.</span></span>  
  
- <span data-ttu-id="a9712-108">Registrovaný server proxy se nedaří `QueryInterface` volat, protože došlo k pokusu o volání v chybném kontextu.</span><span class="sxs-lookup"><span data-stu-id="a9712-108">The registered proxy is failing the `QueryInterface` call because the call was attempted in the wrong context.</span></span>  
  
- <span data-ttu-id="a9712-109">Proxy služby vlastnictví OLE vrátí selhání hodnoty HRESULT.</span><span class="sxs-lookup"><span data-stu-id="a9712-109">An OLE-owned proxy returned a failure HRESULT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a9712-110">Řešení</span><span class="sxs-lookup"><span data-stu-id="a9712-110">Resolution</span></span>  
 <span data-ttu-id="a9712-111">Pravidla modelu COM naleznete v dokumentaci MSDN.</span><span class="sxs-lookup"><span data-stu-id="a9712-111">See the MSDN documentation on COM rules.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a9712-112">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="a9712-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="a9712-113">Pokud `QueryInterface` volání selže, kontext se přepnul a `QueryInterface` volání se opakovat pokus o zobrazíte, pokud byl nesprávný kontextu 2!s!(0x%3!s!).</span><span class="sxs-lookup"><span data-stu-id="a9712-113">If a `QueryInterface` call fails, the context is switched and the `QueryInterface` call is attempted again to see if an incorrect context was at fault.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a9712-114">Výstup</span><span class="sxs-lookup"><span data-stu-id="a9712-114">Output</span></span>  
 <span data-ttu-id="a9712-115">Název spravovaného rozhraní, GUID rozhraní a hodnota HRESULT chyby.</span><span class="sxs-lookup"><span data-stu-id="a9712-115">The managed name of the interface, the GUID of the interface, and the HRESULT of the failure.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a9712-116">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="a9712-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a9712-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9712-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="a9712-118">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="a9712-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="a9712-119">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="a9712-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
