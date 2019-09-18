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
ms.openlocfilehash: 3a49bdce78c1445cd25de8755ded0f27a4902937
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052816"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a><span data-ttu-id="338f2-102">exceptionSwallowedOnCallFromCom – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="338f2-102">exceptionSwallowedOnCallFromCom MDA</span></span>
<span data-ttu-id="338f2-103">Pokud je vyvolána výjimka z kódu modulu CLR (Common Language Runtime), který je volán z modelu COM prostřednictvím metody, která nemá nespravovaný návratový typ HRESULT, je aktivována pomocník spravovanéholadění(MDA).`exceptionSwallowedOnCallFromCOM`</span><span class="sxs-lookup"><span data-stu-id="338f2-103">The `exceptionSwallowedOnCallFromCOM` managed debugging assistant (MDA) is activated when an exception is thrown from common language runtime (CLR) code called from COM via a method that does not have an unmanaged HRESULT return type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="338f2-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="338f2-104">Symptoms</span></span>  
 <span data-ttu-id="338f2-105">Volání spravované komponenty z modelu COM vrátí hodnotu FALSE nebo 0.</span><span class="sxs-lookup"><span data-stu-id="338f2-105">A call to a managed component from COM returns with a value of FALSE or 0.</span></span> <span data-ttu-id="338f2-106">Případně, pokud má metoda návratový typ void, nesmí být žádné náznaky, že při provádění metody došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="338f2-106">Alternatively, if the method has a void return type, there may be no indication that an exception was thrown during the execution of the method.</span></span> <span data-ttu-id="338f2-107">V tomto případě bude výjimka tiše zachycena a provádění se vrátí volajícímu modelu COM.</span><span class="sxs-lookup"><span data-stu-id="338f2-107">In this case, the exception will be silently caught and execution will return to the COM caller.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="338f2-108">příčina</span><span class="sxs-lookup"><span data-stu-id="338f2-108">Cause</span></span>  
 <span data-ttu-id="338f2-109">Došlo k výjimce, ale neexistuje žádný platný způsob, jak ji ohlásit.</span><span class="sxs-lookup"><span data-stu-id="338f2-109">An exception was thrown, but there is no valid way to report it.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="338f2-110">Řešení</span><span class="sxs-lookup"><span data-stu-id="338f2-110">Resolution</span></span>  
 <span data-ttu-id="338f2-111">Pouze informativní, nemusí nutně vyindikativní chybu.</span><span class="sxs-lookup"><span data-stu-id="338f2-111">Informational only, not necessarily indicative of a bug.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="338f2-112">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="338f2-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="338f2-113">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="338f2-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="338f2-114">Pouze hlásí data o tichém zachycení výjimek.</span><span class="sxs-lookup"><span data-stu-id="338f2-114">It only reports data about silently caught exceptions.</span></span>  
  
## <a name="output"></a><span data-ttu-id="338f2-115">Výstup</span><span class="sxs-lookup"><span data-stu-id="338f2-115">Output</span></span>  
 <span data-ttu-id="338f2-116">Informační zpráva obsahující název metody, název typu a zprávu o výjimce.</span><span class="sxs-lookup"><span data-stu-id="338f2-116">Informational message containing the method name, type name, and exception message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="338f2-117">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="338f2-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="338f2-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="338f2-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="338f2-119">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="338f2-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="338f2-120">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="338f2-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
