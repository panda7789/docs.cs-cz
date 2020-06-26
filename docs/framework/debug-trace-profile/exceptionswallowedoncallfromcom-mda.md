---
title: exceptionSwallowedOnCallFromCom – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění Exceptionswallowedoncallfromcom – v .NET. K tomuto problému MDA dojde, pokud byla vyvolána výjimka, ale neexistuje žádný dobrý způsob, jak ji ohlásit.
ms.date: 03/30/2017
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
ms.openlocfilehash: 434f06cf953147d5c245e625db997bed6dbef700
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415950"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a><span data-ttu-id="14278-104">exceptionSwallowedOnCallFromCom – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="14278-104">exceptionSwallowedOnCallFromCom MDA</span></span>
<span data-ttu-id="14278-105">`exceptionSwallowedOnCallFromCOM`Pokud je vyvolána výjimka z kódu modulu CLR (Common Language Runtime), který je volán z modelu COM prostřednictvím metody, která nemá nespravovaný návratový typ HRESULT, je aktivována pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="14278-105">The `exceptionSwallowedOnCallFromCOM` managed debugging assistant (MDA) is activated when an exception is thrown from common language runtime (CLR) code called from COM via a method that does not have an unmanaged HRESULT return type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="14278-106">Příznaky</span><span class="sxs-lookup"><span data-stu-id="14278-106">Symptoms</span></span>  
 <span data-ttu-id="14278-107">Volání spravované komponenty z modelu COM vrátí hodnotu FALSE nebo 0.</span><span class="sxs-lookup"><span data-stu-id="14278-107">A call to a managed component from COM returns with a value of FALSE or 0.</span></span> <span data-ttu-id="14278-108">Případně, pokud má metoda návratový typ void, nesmí být žádné náznaky, že při provádění metody došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="14278-108">Alternatively, if the method has a void return type, there may be no indication that an exception was thrown during the execution of the method.</span></span> <span data-ttu-id="14278-109">V tomto případě bude výjimka tiše zachycena a provádění se vrátí volajícímu modelu COM.</span><span class="sxs-lookup"><span data-stu-id="14278-109">In this case, the exception will be silently caught and execution will return to the COM caller.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="14278-110">Příčina</span><span class="sxs-lookup"><span data-stu-id="14278-110">Cause</span></span>  
 <span data-ttu-id="14278-111">Došlo k výjimce, ale neexistuje žádný platný způsob, jak ji ohlásit.</span><span class="sxs-lookup"><span data-stu-id="14278-111">An exception was thrown, but there is no valid way to report it.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="14278-112">Řešení</span><span class="sxs-lookup"><span data-stu-id="14278-112">Resolution</span></span>  
 <span data-ttu-id="14278-113">Pouze informativní, nemusí nutně vyindikativní chybu.</span><span class="sxs-lookup"><span data-stu-id="14278-113">Informational only, not necessarily indicative of a bug.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="14278-114">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="14278-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="14278-115">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="14278-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="14278-116">Pouze hlásí data o tichém zachycení výjimek.</span><span class="sxs-lookup"><span data-stu-id="14278-116">It only reports data about silently caught exceptions.</span></span>  
  
## <a name="output"></a><span data-ttu-id="14278-117">Výstup</span><span class="sxs-lookup"><span data-stu-id="14278-117">Output</span></span>  
 <span data-ttu-id="14278-118">Informační zpráva obsahující název metody, název typu a zprávu o výjimce.</span><span class="sxs-lookup"><span data-stu-id="14278-118">Informational message containing the method name, type name, and exception message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="14278-119">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="14278-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="14278-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="14278-120">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="14278-121">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="14278-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="14278-122">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="14278-122">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
