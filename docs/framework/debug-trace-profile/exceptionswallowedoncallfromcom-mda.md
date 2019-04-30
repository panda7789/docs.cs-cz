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
ms.openlocfilehash: 4f076cbc556c7d9feff8a226f050743cd7728622
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61874442"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a><span data-ttu-id="269a5-102">exceptionSwallowedOnCallFromCom – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="269a5-102">exceptionSwallowedOnCallFromCom MDA</span></span>
<span data-ttu-id="269a5-103">`exceptionSwallowedOnCallFromCOM` Pomocníka spravovaného ladění (MDA) se aktivuje, když je vyvolána výjimka z common language runtime (CLR) kódu volat z modelu COM pomocí metody, která nemá nespravovaný návratový typ HRESULT.</span><span class="sxs-lookup"><span data-stu-id="269a5-103">The `exceptionSwallowedOnCallFromCOM` managed debugging assistant (MDA) is activated when an exception is thrown from common language runtime (CLR) code called from COM via a method that does not have an unmanaged HRESULT return type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="269a5-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="269a5-104">Symptoms</span></span>  
 <span data-ttu-id="269a5-105">Volání spravované součásti z modelu COM, vrátí hodnotu FALSE nebo 0.</span><span class="sxs-lookup"><span data-stu-id="269a5-105">A call to a managed component from COM returns with a value of FALSE or 0.</span></span> <span data-ttu-id="269a5-106">Případně pokud metoda nemá návratový typ void, můžou existovat žádné označení, která během provádění metody došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="269a5-106">Alternatively, if the method has a void return type, there may be no indication that an exception was thrown during the execution of the method.</span></span> <span data-ttu-id="269a5-107">V tomto případě výjimku tiše zachytí se a vrátí provádění volajícímu modulu COM.</span><span class="sxs-lookup"><span data-stu-id="269a5-107">In this case, the exception will be silently caught and execution will return to the COM caller.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="269a5-108">Příčina</span><span class="sxs-lookup"><span data-stu-id="269a5-108">Cause</span></span>  
 <span data-ttu-id="269a5-109">Došlo k výjimce, ale neexistuje žádný platný způsob, jak ji ohlásit.</span><span class="sxs-lookup"><span data-stu-id="269a5-109">An exception was thrown, but there is no valid way to report it.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="269a5-110">Řešení</span><span class="sxs-lookup"><span data-stu-id="269a5-110">Resolution</span></span>  
 <span data-ttu-id="269a5-111">Informativní pouze, není nutně indikátorem chyby.</span><span class="sxs-lookup"><span data-stu-id="269a5-111">Informational only, not necessarily indicative of a bug.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="269a5-112">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="269a5-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="269a5-113">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="269a5-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="269a5-114">Sestavy pouze data o tiše zachycené výjimky.</span><span class="sxs-lookup"><span data-stu-id="269a5-114">It only reports data about silently caught exceptions.</span></span>  
  
## <a name="output"></a><span data-ttu-id="269a5-115">Výstup</span><span class="sxs-lookup"><span data-stu-id="269a5-115">Output</span></span>  
 <span data-ttu-id="269a5-116">Informační zpráva obsahující název metody, název typu a zpráva o výjimce.</span><span class="sxs-lookup"><span data-stu-id="269a5-116">Informational message containing the method name, type name, and exception message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="269a5-117">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="269a5-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="269a5-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="269a5-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="269a5-119">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="269a5-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="269a5-120">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="269a5-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
