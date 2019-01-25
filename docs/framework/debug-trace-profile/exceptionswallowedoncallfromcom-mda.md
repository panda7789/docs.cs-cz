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
ms.openlocfilehash: aebcd2d2f2387f478c36e84dad82d90d4d70d68e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554670"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a><span data-ttu-id="d7b98-102">exceptionSwallowedOnCallFromCom – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="d7b98-102">exceptionSwallowedOnCallFromCom MDA</span></span>
<span data-ttu-id="d7b98-103">`exceptionSwallowedOnCallFromCOM` Pomocníka spravovaného ladění (MDA) se aktivuje, když je vyvolána výjimka z common language runtime (CLR) kódu volat z modelu COM pomocí metody, která nemá nespravovaný návratový typ HRESULT.</span><span class="sxs-lookup"><span data-stu-id="d7b98-103">The `exceptionSwallowedOnCallFromCOM` managed debugging assistant (MDA) is activated when an exception is thrown from common language runtime (CLR) code called from COM via a method that does not have an unmanaged HRESULT return type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d7b98-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="d7b98-104">Symptoms</span></span>  
 <span data-ttu-id="d7b98-105">Volání spravované součásti z modelu COM, vrátí hodnotu FALSE nebo 0.</span><span class="sxs-lookup"><span data-stu-id="d7b98-105">A call to a managed component from COM returns with a value of FALSE or 0.</span></span> <span data-ttu-id="d7b98-106">Případně pokud metoda nemá návratový typ void, můžou existovat žádné označení, která během provádění metody došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="d7b98-106">Alternatively, if the method has a void return type, there may be no indication that an exception was thrown during the execution of the method.</span></span> <span data-ttu-id="d7b98-107">V tomto případě výjimku tiše zachytí se a vrátí provádění volajícímu modulu COM.</span><span class="sxs-lookup"><span data-stu-id="d7b98-107">In this case, the exception will be silently caught and execution will return to the COM caller.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d7b98-108">Příčina</span><span class="sxs-lookup"><span data-stu-id="d7b98-108">Cause</span></span>  
 <span data-ttu-id="d7b98-109">Došlo k výjimce, ale neexistuje žádný platný způsob, jak ji ohlásit.</span><span class="sxs-lookup"><span data-stu-id="d7b98-109">An exception was thrown, but there is no valid way to report it.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="d7b98-110">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="d7b98-110">Resolution</span></span>  
 <span data-ttu-id="d7b98-111">Informativní pouze, není nutně indikátorem chyby.</span><span class="sxs-lookup"><span data-stu-id="d7b98-111">Informational only, not necessarily indicative of a bug.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d7b98-112">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="d7b98-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="d7b98-113">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="d7b98-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="d7b98-114">Sestavy pouze data o tiše zachycené výjimky.</span><span class="sxs-lookup"><span data-stu-id="d7b98-114">It only reports data about silently caught exceptions.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d7b98-115">Výstup</span><span class="sxs-lookup"><span data-stu-id="d7b98-115">Output</span></span>  
 <span data-ttu-id="d7b98-116">Informační zpráva obsahující název metody, název typu a zpráva o výjimce.</span><span class="sxs-lookup"><span data-stu-id="d7b98-116">Informational message containing the method name, type name, and exception message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="d7b98-117">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="d7b98-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7b98-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d7b98-118">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="d7b98-119">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="d7b98-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="d7b98-120">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="d7b98-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
