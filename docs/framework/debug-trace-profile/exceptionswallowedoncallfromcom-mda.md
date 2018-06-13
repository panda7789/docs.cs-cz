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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b4c1cbf075ef96073061679b6d062075490f5e4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390605"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a><span data-ttu-id="0ca8d-102">exceptionSwallowedOnCallFromCom – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="0ca8d-102">exceptionSwallowedOnCallFromCom MDA</span></span>
<span data-ttu-id="0ca8d-103">`exceptionSwallowedOnCallFromCOM` Pomocník spravovaného ladění (MDA) se aktivuje, když z společný kód language runtime (CLR) volat z COM prostřednictvím metody, která nemá nespravované HRESULT návratový typ je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="0ca8d-103">The `exceptionSwallowedOnCallFromCOM` managed debugging assistant (MDA) is activated when an exception is thrown from common language runtime (CLR) code called from COM via a method that does not have an unmanaged HRESULT return type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="0ca8d-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="0ca8d-104">Symptoms</span></span>  
 <span data-ttu-id="0ca8d-105">Volání spravované součásti z modelu COM, vrátí se hodnota FALSE nebo 0.</span><span class="sxs-lookup"><span data-stu-id="0ca8d-105">A call to a managed component from COM returns with a value of FALSE or 0.</span></span> <span data-ttu-id="0ca8d-106">Případně pokud metoda má typ vrácené hodnoty void, mohou existovat žádné naznačeno, že došlo k výjimce během provádění metody.</span><span class="sxs-lookup"><span data-stu-id="0ca8d-106">Alternatively, if the method has a void return type, there may be no indication that an exception was thrown during the execution of the method.</span></span> <span data-ttu-id="0ca8d-107">V takovém případě bude bezobslužně zachycena výjimka a provádění vrátí COM volajícímu.</span><span class="sxs-lookup"><span data-stu-id="0ca8d-107">In this case, the exception will be silently caught and execution will return to the COM caller.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="0ca8d-108">příčina</span><span class="sxs-lookup"><span data-stu-id="0ca8d-108">Cause</span></span>  
 <span data-ttu-id="0ca8d-109">Došlo k výjimce, ale neexistuje žádný platný způsob zprávu vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="0ca8d-109">An exception was thrown, but there is no valid way to report it.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="0ca8d-110">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="0ca8d-110">Resolution</span></span>  
 <span data-ttu-id="0ca8d-111">Informativní pouze, nikoli nutně naznačuje výslednou chyby.</span><span class="sxs-lookup"><span data-stu-id="0ca8d-111">Informational only, not necessarily indicative of a bug.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="0ca8d-112">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="0ca8d-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="0ca8d-113">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="0ca8d-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="0ca8d-114">Pouze sestavy data o bezobslužně zachycení výjimky.</span><span class="sxs-lookup"><span data-stu-id="0ca8d-114">It only reports data about silently caught exceptions.</span></span>  
  
## <a name="output"></a><span data-ttu-id="0ca8d-115">Výstup</span><span class="sxs-lookup"><span data-stu-id="0ca8d-115">Output</span></span>  
 <span data-ttu-id="0ca8d-116">Informační zpráva, která obsahuje název metody, název typu a zpráva o výjimce.</span><span class="sxs-lookup"><span data-stu-id="0ca8d-116">Informational message containing the method name, type name, and exception message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="0ca8d-117">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="0ca8d-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ca8d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ca8d-118">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="0ca8d-119">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="0ca8d-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="0ca8d-120">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="0ca8d-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
