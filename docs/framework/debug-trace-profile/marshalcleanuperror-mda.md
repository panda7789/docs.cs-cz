---
title: marshalCleanupError – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- cleanup operations
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- marshaling cleanup error
- MarshalCleanupError MDA
- memory, cleanup errors
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2399f72b6efcdf69d8ff4bb3bce541073063c750
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61753930"
---
# <a name="marshalcleanuperror-mda"></a><span data-ttu-id="ce4af-102">marshalCleanupError – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="ce4af-102">marshalCleanupError MDA</span></span>
<span data-ttu-id="ce4af-103">`marshalCleanupError` Pomocníka spravovaného ladění (MDA) se aktivuje, když modul CLR (CLR) dojde k chybě při pokusu o Vyčištění dočasné struktury a paměť používanou pro zařazování typů dat mezi hranice nativního a spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="ce4af-103">The `marshalCleanupError` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters an error while attempting to clean up temporary structures and memory used for marshaling data types between native and managed code boundaries.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="ce4af-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="ce4af-104">Symptoms</span></span>  
 <span data-ttu-id="ce4af-105">Nevracení paměti dochází při provádění přechody nativního a spravovaného kódu, modulu runtime stavu, například jazyková verze vlákna se neobnoví, nebo dojde k chybám v <xref:System.Runtime.InteropServices.SafeHandle> vyčištění.</span><span class="sxs-lookup"><span data-stu-id="ce4af-105">A memory leak occurs when making native and managed code transitions, runtime state such as thread culture is not restored, or errors occur in <xref:System.Runtime.InteropServices.SafeHandle> cleanup.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="ce4af-106">Příčina</span><span class="sxs-lookup"><span data-stu-id="ce4af-106">Cause</span></span>  
 <span data-ttu-id="ce4af-107">Při čištění dočasné struktury došlo k neočekávané chybě.</span><span class="sxs-lookup"><span data-stu-id="ce4af-107">An unexpected error occurred while cleaning up temporary structures.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="ce4af-108">Řešení</span><span class="sxs-lookup"><span data-stu-id="ce4af-108">Resolution</span></span>  
 <span data-ttu-id="ce4af-109">Zkontrolujte všechny <xref:System.Runtime.InteropServices.SafeHandle> destruktor, finalizační metody a vlastní zařazovací modul implementace chyby.</span><span class="sxs-lookup"><span data-stu-id="ce4af-109">Review all <xref:System.Runtime.InteropServices.SafeHandle> destructor, finalizer, and custom marshaler implementations for errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ce4af-110">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="ce4af-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="ce4af-111">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="ce4af-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ce4af-112">Výstup</span><span class="sxs-lookup"><span data-stu-id="ce4af-112">Output</span></span>  
 <span data-ttu-id="ce4af-113">Zpráva reporting operace, které selhaly během čištění.</span><span class="sxs-lookup"><span data-stu-id="ce4af-113">A message reporting the operation that failed during cleanup.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="ce4af-114">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="ce4af-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce4af-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce4af-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="ce4af-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="ce4af-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="ce4af-117">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="ce4af-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
