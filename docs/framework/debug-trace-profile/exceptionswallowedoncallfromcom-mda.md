---
title: "exceptionSwallowedOnCallFromCom – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c20c4e0b6c1c711b2044bc3ba32d00447220cb8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="exceptionswallowedoncallfromcom-mda"></a><span data-ttu-id="b78ce-102">exceptionSwallowedOnCallFromCom – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="b78ce-102">exceptionSwallowedOnCallFromCom MDA</span></span>
<span data-ttu-id="b78ce-103">`exceptionSwallowedOnCallFromCOM` Pomocník spravovaného ladění (MDA) se aktivuje, když z společný kód language runtime (CLR) volat z COM prostřednictvím metody, která nemá nespravované HRESULT návratový typ je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="b78ce-103">The `exceptionSwallowedOnCallFromCOM` managed debugging assistant (MDA) is activated when an exception is thrown from common language runtime (CLR) code called from COM via a method that does not have an unmanaged HRESULT return type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="b78ce-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="b78ce-104">Symptoms</span></span>  
 <span data-ttu-id="b78ce-105">Volání spravované součásti z modelu COM, vrátí se hodnota FALSE nebo 0.</span><span class="sxs-lookup"><span data-stu-id="b78ce-105">A call to a managed component from COM returns with a value of FALSE or 0.</span></span> <span data-ttu-id="b78ce-106">Případně pokud metoda má typ vrácené hodnoty void, mohou existovat žádné naznačeno, že došlo k výjimce během provádění metody.</span><span class="sxs-lookup"><span data-stu-id="b78ce-106">Alternatively, if the method has a void return type, there may be no indication that an exception was thrown during the execution of the method.</span></span> <span data-ttu-id="b78ce-107">V takovém případě bude bezobslužně zachycena výjimka a provádění vrátí COM volajícímu.</span><span class="sxs-lookup"><span data-stu-id="b78ce-107">In this case, the exception will be silently caught and execution will return to the COM caller.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="b78ce-108">příčina</span><span class="sxs-lookup"><span data-stu-id="b78ce-108">Cause</span></span>  
 <span data-ttu-id="b78ce-109">Došlo k výjimce, ale neexistuje žádný platný způsob zprávu vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="b78ce-109">An exception was thrown, but there is no valid way to report it.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="b78ce-110">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="b78ce-110">Resolution</span></span>  
 <span data-ttu-id="b78ce-111">Informativní pouze, nikoli nutně naznačuje výslednou chyby.</span><span class="sxs-lookup"><span data-stu-id="b78ce-111">Informational only, not necessarily indicative of a bug.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="b78ce-112">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="b78ce-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="b78ce-113">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="b78ce-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="b78ce-114">Pouze sestavy data o bezobslužně zachycení výjimky.</span><span class="sxs-lookup"><span data-stu-id="b78ce-114">It only reports data about silently caught exceptions.</span></span>  
  
## <a name="output"></a><span data-ttu-id="b78ce-115">Výstup</span><span class="sxs-lookup"><span data-stu-id="b78ce-115">Output</span></span>  
 <span data-ttu-id="b78ce-116">Informační zpráva, která obsahuje název metody, název typu a zpráva o výjimce.</span><span class="sxs-lookup"><span data-stu-id="b78ce-116">Informational message containing the method name, type name, and exception message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b78ce-117">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="b78ce-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b78ce-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="b78ce-118">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="b78ce-119">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="b78ce-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="b78ce-120">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="b78ce-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
