---
title: "reportAvOnComRelease – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), reference counting errors
- exceptions, reference counting errors
- ReportAvOnComRelease MDA
- COM release access violations
- user reference counting errors
- managed debugging assistants (MDAs), reference counting errors
- report access violation on Com release
- reference counting errors
ms.assetid: a2b86b63-08b2-4943-b344-3c2cf46ccd31
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b198c6a026cded788c0030f1319b37e874d0eb5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="reportavoncomrelease-mda"></a><span data-ttu-id="4d1cb-102">reportAvOnComRelease – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="4d1cb-102">reportAvOnComRelease MDA</span></span>
<span data-ttu-id="4d1cb-103">`reportAvOnComRelease` Pomocník spravovaného ladění (MDA) se aktivuje, pokud jsou výjimky vyvolány z důvodu chyby při provádění COM spolupráce a pomocí počítání uživatelských referencí <xref:System.Runtime.InteropServices.Marshal.Release%2A> nebo <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> metoda v kombinaci s nezpracovaná volání COM.</span><span class="sxs-lookup"><span data-stu-id="4d1cb-103">The `reportAvOnComRelease` managed debugging assistant (MDA) is activated when exceptions are thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="4d1cb-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="4d1cb-104">Symptoms</span></span>  
 <span data-ttu-id="4d1cb-105">Narušení přístupu a poškození paměti.</span><span class="sxs-lookup"><span data-stu-id="4d1cb-105">Access violations and memory corruption.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="4d1cb-106">příčina</span><span class="sxs-lookup"><span data-stu-id="4d1cb-106">Cause</span></span>  
 <span data-ttu-id="4d1cb-107">V některých případech je vyvolána výjimka z důvodu chyby při provádění COM spolupráce a pomocí počítání uživatelských referencí <xref:System.Runtime.InteropServices.Marshal.Release%2A> nebo <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> metoda v kombinaci s nezpracovaná volání COM.</span><span class="sxs-lookup"><span data-stu-id="4d1cb-107">Occasionally, an exception is thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span> <span data-ttu-id="4d1cb-108">Za normálních okolností se tato výjimka je zahozena, protože není tak by způsobit narušení přístupu v prostředí CLR, bude mimo provoz.</span><span class="sxs-lookup"><span data-stu-id="4d1cb-108">Normally, this exception is discarded because not doing so would cause an access violation in the CLR, bringing it down.</span></span> <span data-ttu-id="4d1cb-109">Pokud tohoto pomocníka je povoleno, můžete tyto výjimky zjistil a hlášené místo jednoduše budou odstraněny.</span><span class="sxs-lookup"><span data-stu-id="4d1cb-109">When this assistant is enabled, such exceptions can be detected and reported instead of being simply discarded.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="4d1cb-110">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="4d1cb-110">Resolution</span></span>  
 <span data-ttu-id="4d1cb-111">Zkontrolujte vaši informaci, kód a vyhledejte chyby při počítání a také zkoumání nativních klientů objektu pro chyby při počítání referencí.</span><span class="sxs-lookup"><span data-stu-id="4d1cb-111">Examine your reference counting code and search for errors as well as examining the native clients of your object for reference counting errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="4d1cb-112">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="4d1cb-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="4d1cb-113">K dispozici jsou dva režimy.</span><span class="sxs-lookup"><span data-stu-id="4d1cb-113">Two modes are available.</span></span> <span data-ttu-id="4d1cb-114">Pokud `allowAv` atribut je `true`, pomocníka brání modulu runtime zahození porušení přístupu.</span><span class="sxs-lookup"><span data-stu-id="4d1cb-114">If the `allowAv` attribute is `true`, the assistant prevents the runtime from discarding the access violation.</span></span> <span data-ttu-id="4d1cb-115">Pokud `allowAv` je `false`, který je výchozí, modul runtime zahodí narušení přístupu, ale upozornění údajně uživateli znamenat, že byla vyvolána a zahodí výjimku.</span><span class="sxs-lookup"><span data-stu-id="4d1cb-115">If `allowAv` is `false`, which is the default, the runtime discards the access violation, but a warning message is reported to the user to indicate that an exception was thrown and discarded.</span></span>  
  
## <a name="output"></a><span data-ttu-id="4d1cb-116">Výstup</span><span class="sxs-lookup"><span data-stu-id="4d1cb-116">Output</span></span>  
 <span data-ttu-id="4d1cb-117">Pokud je to možné výstup obsahuje původní vtable ukazatel rozhraní COM.</span><span class="sxs-lookup"><span data-stu-id="4d1cb-117">If possible, the output contains the COM interface pointer's original vtable.</span></span> <span data-ttu-id="4d1cb-118">Jinak se zobrazí informační zpráva.</span><span class="sxs-lookup"><span data-stu-id="4d1cb-118">Otherwise, an informational message is displayed.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="4d1cb-119">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="4d1cb-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d1cb-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d1cb-120">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="4d1cb-121">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="4d1cb-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="4d1cb-122">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="4d1cb-122">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
