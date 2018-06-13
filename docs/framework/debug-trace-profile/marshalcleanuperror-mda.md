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
ms.openlocfilehash: 6784848a5103dc9206267fc25fe7457257624cb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392028"
---
# <a name="marshalcleanuperror-mda"></a><span data-ttu-id="1bc87-102">marshalCleanupError – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="1bc87-102">marshalCleanupError MDA</span></span>
<span data-ttu-id="1bc87-103">`marshalCleanupError` Pomocník spravovaného ladění (MDA) se aktivuje, když modul CLR (CLR) dojde k chybě při pokusu o Vyčištění dočasné struktury a paměť použitá pro zařazování typů dat mezi hranice nativního a spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="1bc87-103">The `marshalCleanupError` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters an error while attempting to clean up temporary structures and memory used for marshaling data types between native and managed code boundaries.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1bc87-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="1bc87-104">Symptoms</span></span>  
 <span data-ttu-id="1bc87-105">Nevracení paměti dojde při provádění přechody nativního a spravovaného kódu, modul runtime stavu, jako je tato funkce nebude obnovena jazykovou verzi vlákna nebo dojít k chybám v <xref:System.Runtime.InteropServices.SafeHandle> čištění.</span><span class="sxs-lookup"><span data-stu-id="1bc87-105">A memory leak occurs when making native and managed code transitions, runtime state such as thread culture is not restored, or errors occur in <xref:System.Runtime.InteropServices.SafeHandle> cleanup.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1bc87-106">příčina</span><span class="sxs-lookup"><span data-stu-id="1bc87-106">Cause</span></span>  
 <span data-ttu-id="1bc87-107">Došlo k neočekávané chybě při čištění dočasné struktury.</span><span class="sxs-lookup"><span data-stu-id="1bc87-107">An unexpected error occurred while cleaning up temporary structures.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1bc87-108">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="1bc87-108">Resolution</span></span>  
 <span data-ttu-id="1bc87-109">Zkontrolujte všechny <xref:System.Runtime.InteropServices.SafeHandle> – destruktor, finalizační metodu a implementace vlastní chyby.</span><span class="sxs-lookup"><span data-stu-id="1bc87-109">Review all <xref:System.Runtime.InteropServices.SafeHandle> destructor, finalizer, and custom marshaler implementations for errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1bc87-110">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="1bc87-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="1bc87-111">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="1bc87-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1bc87-112">Výstup</span><span class="sxs-lookup"><span data-stu-id="1bc87-112">Output</span></span>  
 <span data-ttu-id="1bc87-113">Zpráva reporting operace, které selhaly během čištění.</span><span class="sxs-lookup"><span data-stu-id="1bc87-113">A message reporting the operation that failed during cleanup.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="1bc87-114">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="1bc87-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1bc87-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="1bc87-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="1bc87-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="1bc87-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="1bc87-117">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="1bc87-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
