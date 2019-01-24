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
ms.openlocfilehash: 4ff7286eb104f36ceb5e1d9b30f4a265fb068d3e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564666"
---
# <a name="marshalcleanuperror-mda"></a><span data-ttu-id="68cf8-102">marshalCleanupError – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="68cf8-102">marshalCleanupError MDA</span></span>
<span data-ttu-id="68cf8-103">`marshalCleanupError` Pomocníka spravovaného ladění (MDA) se aktivuje, když modul CLR (CLR) dojde k chybě při pokusu o Vyčištění dočasné struktury a paměť používanou pro zařazování typů dat mezi hranice nativního a spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="68cf8-103">The `marshalCleanupError` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters an error while attempting to clean up temporary structures and memory used for marshaling data types between native and managed code boundaries.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="68cf8-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="68cf8-104">Symptoms</span></span>  
 <span data-ttu-id="68cf8-105">Nevracení paměti dochází při provádění přechody nativního a spravovaného kódu, modulu runtime stavu, například jazyková verze vlákna se neobnoví, nebo dojde k chybám v <xref:System.Runtime.InteropServices.SafeHandle> vyčištění.</span><span class="sxs-lookup"><span data-stu-id="68cf8-105">A memory leak occurs when making native and managed code transitions, runtime state such as thread culture is not restored, or errors occur in <xref:System.Runtime.InteropServices.SafeHandle> cleanup.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="68cf8-106">Příčina</span><span class="sxs-lookup"><span data-stu-id="68cf8-106">Cause</span></span>  
 <span data-ttu-id="68cf8-107">Při čištění dočasné struktury došlo k neočekávané chybě.</span><span class="sxs-lookup"><span data-stu-id="68cf8-107">An unexpected error occurred while cleaning up temporary structures.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="68cf8-108">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="68cf8-108">Resolution</span></span>  
 <span data-ttu-id="68cf8-109">Zkontrolujte všechny <xref:System.Runtime.InteropServices.SafeHandle> destruktor, finalizační metody a vlastní zařazovací modul implementace chyby.</span><span class="sxs-lookup"><span data-stu-id="68cf8-109">Review all <xref:System.Runtime.InteropServices.SafeHandle> destructor, finalizer, and custom marshaler implementations for errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="68cf8-110">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="68cf8-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="68cf8-111">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="68cf8-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="68cf8-112">Výstup</span><span class="sxs-lookup"><span data-stu-id="68cf8-112">Output</span></span>  
 <span data-ttu-id="68cf8-113">Zpráva reporting operace, které selhaly během čištění.</span><span class="sxs-lookup"><span data-stu-id="68cf8-113">A message reporting the operation that failed during cleanup.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="68cf8-114">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="68cf8-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="68cf8-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68cf8-115">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="68cf8-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="68cf8-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="68cf8-117">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="68cf8-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
