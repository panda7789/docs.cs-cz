---
title: exceptionSwallowedOnCallFromCom – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
ms.openlocfilehash: 4ccb03c9a8a473c10f15b00e64810b04f21504c9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217515"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a><span data-ttu-id="5ff92-102">exceptionSwallowedOnCallFromCom – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="5ff92-102">exceptionSwallowedOnCallFromCom MDA</span></span>
<span data-ttu-id="5ff92-103">Pokud je vyvolána výjimka z kódu modulu CLR (Common Language Runtime), který je volán z modelu COM prostřednictvím metody, která nemá nespravovaný návratový typ HRESULT, je aktivována aplikace `exceptionSwallowedOnCallFromCOM` Managed Debugging Assistant (MDA).</span><span class="sxs-lookup"><span data-stu-id="5ff92-103">The `exceptionSwallowedOnCallFromCOM` managed debugging assistant (MDA) is activated when an exception is thrown from common language runtime (CLR) code called from COM via a method that does not have an unmanaged HRESULT return type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5ff92-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="5ff92-104">Symptoms</span></span>  
 <span data-ttu-id="5ff92-105">Volání spravované komponenty z modelu COM vrátí hodnotu FALSE nebo 0.</span><span class="sxs-lookup"><span data-stu-id="5ff92-105">A call to a managed component from COM returns with a value of FALSE or 0.</span></span> <span data-ttu-id="5ff92-106">Případně, pokud má metoda návratový typ void, nesmí být žádné náznaky, že při provádění metody došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="5ff92-106">Alternatively, if the method has a void return type, there may be no indication that an exception was thrown during the execution of the method.</span></span> <span data-ttu-id="5ff92-107">V tomto případě bude výjimka tiše zachycena a provádění se vrátí volajícímu modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5ff92-107">In this case, the exception will be silently caught and execution will return to the COM caller.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5ff92-108">Příčina</span><span class="sxs-lookup"><span data-stu-id="5ff92-108">Cause</span></span>  
 <span data-ttu-id="5ff92-109">Došlo k výjimce, ale neexistuje žádný platný způsob, jak ji ohlásit.</span><span class="sxs-lookup"><span data-stu-id="5ff92-109">An exception was thrown, but there is no valid way to report it.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="5ff92-110">Řešení</span><span class="sxs-lookup"><span data-stu-id="5ff92-110">Resolution</span></span>  
 <span data-ttu-id="5ff92-111">Pouze informativní, nemusí nutně vyindikativní chybu.</span><span class="sxs-lookup"><span data-stu-id="5ff92-111">Informational only, not necessarily indicative of a bug.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5ff92-112">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="5ff92-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="5ff92-113">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="5ff92-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="5ff92-114">Pouze hlásí data o tichém zachycení výjimek.</span><span class="sxs-lookup"><span data-stu-id="5ff92-114">It only reports data about silently caught exceptions.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5ff92-115">Výstup</span><span class="sxs-lookup"><span data-stu-id="5ff92-115">Output</span></span>  
 <span data-ttu-id="5ff92-116">Informační zpráva obsahující název metody, název typu a zprávu o výjimce.</span><span class="sxs-lookup"><span data-stu-id="5ff92-116">Informational message containing the method name, type name, and exception message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="5ff92-117">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="5ff92-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ff92-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ff92-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="5ff92-119">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="5ff92-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="5ff92-120">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="5ff92-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
