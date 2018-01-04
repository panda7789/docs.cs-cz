---
title: "marshalCleanupError – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cleanup operations
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- marshaling cleanup error
- MarshalCleanupError MDA
- memory, cleanup errors
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 641d12131f1502ce1ef00c6cf3889c803bd9fce3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="marshalcleanuperror-mda"></a><span data-ttu-id="128aa-102">marshalCleanupError – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="128aa-102">marshalCleanupError MDA</span></span>
<span data-ttu-id="128aa-103">`marshalCleanupError` Pomocník spravovaného ladění (MDA) se aktivuje, když modul CLR (CLR) dojde k chybě při pokusu o Vyčištění dočasné struktury a paměť použitá pro zařazování typů dat mezi hranice nativního a spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="128aa-103">The `marshalCleanupError` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters an error while attempting to clean up temporary structures and memory used for marshaling data types between native and managed code boundaries.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="128aa-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="128aa-104">Symptoms</span></span>  
 <span data-ttu-id="128aa-105">Nevracení paměti dojde při provádění přechody nativního a spravovaného kódu, modul runtime stavu, jako je tato funkce nebude obnovena jazykovou verzi vlákna nebo dojít k chybám v <xref:System.Runtime.InteropServices.SafeHandle> čištění.</span><span class="sxs-lookup"><span data-stu-id="128aa-105">A memory leak occurs when making native and managed code transitions, runtime state such as thread culture is not restored, or errors occur in <xref:System.Runtime.InteropServices.SafeHandle> cleanup.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="128aa-106">příčina</span><span class="sxs-lookup"><span data-stu-id="128aa-106">Cause</span></span>  
 <span data-ttu-id="128aa-107">Došlo k neočekávané chybě při čištění dočasné struktury.</span><span class="sxs-lookup"><span data-stu-id="128aa-107">An unexpected error occurred while cleaning up temporary structures.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="128aa-108">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="128aa-108">Resolution</span></span>  
 <span data-ttu-id="128aa-109">Zkontrolujte všechny <xref:System.Runtime.InteropServices.SafeHandle> – destruktor, finalizační metodu a implementace vlastní chyby.</span><span class="sxs-lookup"><span data-stu-id="128aa-109">Review all <xref:System.Runtime.InteropServices.SafeHandle> destructor, finalizer, and custom marshaler implementations for errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="128aa-110">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="128aa-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="128aa-111">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="128aa-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="128aa-112">Výstup</span><span class="sxs-lookup"><span data-stu-id="128aa-112">Output</span></span>  
 <span data-ttu-id="128aa-113">Zpráva reporting operace, které selhaly během čištění.</span><span class="sxs-lookup"><span data-stu-id="128aa-113">A message reporting the operation that failed during cleanup.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="128aa-114">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="128aa-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="128aa-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="128aa-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="128aa-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="128aa-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="128aa-117">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="128aa-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
