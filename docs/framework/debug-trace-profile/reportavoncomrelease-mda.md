---
title: reportAvOnComRelease – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c70c70f251fca9312019d4c63304e8354bf87fd1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729155"
---
# <a name="reportavoncomrelease-mda"></a><span data-ttu-id="2e3ac-102">reportAvOnComRelease – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="2e3ac-102">reportAvOnComRelease MDA</span></span>
<span data-ttu-id="2e3ac-103">`reportAvOnComRelease` Pomocníka spravovaného ladění (MDA) se aktivuje, pokud jsou výjimky vyvolány z důvodu chyby při provádění COM interop a používá počítání uživatelských referencí <xref:System.Runtime.InteropServices.Marshal.Release%2A> nebo <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> metoda v kombinaci s nezpracovaná volání COM.</span><span class="sxs-lookup"><span data-stu-id="2e3ac-103">The `reportAvOnComRelease` managed debugging assistant (MDA) is activated when exceptions are thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="2e3ac-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="2e3ac-104">Symptoms</span></span>  
 <span data-ttu-id="2e3ac-105">Narušení přístupu a poškození paměti.</span><span class="sxs-lookup"><span data-stu-id="2e3ac-105">Access violations and memory corruption.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="2e3ac-106">Příčina</span><span class="sxs-lookup"><span data-stu-id="2e3ac-106">Cause</span></span>  
 <span data-ttu-id="2e3ac-107">V některých případech je vyvolána výjimka z důvodu chyby při provádění COM interop a používá počítání uživatelských referencí <xref:System.Runtime.InteropServices.Marshal.Release%2A> nebo <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> metoda v kombinaci s nezpracovaná volání COM.</span><span class="sxs-lookup"><span data-stu-id="2e3ac-107">Occasionally, an exception is thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span> <span data-ttu-id="2e3ac-108">Za normálních okolností se tato výjimka je zahozena, protože pokud to neuděláte by způsobila porušení přístupu v prostředí CLR, Probíhá ukončování.</span><span class="sxs-lookup"><span data-stu-id="2e3ac-108">Normally, this exception is discarded because not doing so would cause an access violation in the CLR, bringing it down.</span></span> <span data-ttu-id="2e3ac-109">Pokud tohoto Pomocníka s nastavením je povoleno, možné takové výjimky zjištěna a předávat místo jednoduše zahozeny.</span><span class="sxs-lookup"><span data-stu-id="2e3ac-109">When this assistant is enabled, such exceptions can be detected and reported instead of being simply discarded.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="2e3ac-110">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="2e3ac-110">Resolution</span></span>  
 <span data-ttu-id="2e3ac-111">Zkontrolujte vaši informaci, počítací kódu a vyhledejte chyby, stejně jako zkoumání nativní klienty objektu pro chyby při počítání referencí.</span><span class="sxs-lookup"><span data-stu-id="2e3ac-111">Examine your reference counting code and search for errors as well as examining the native clients of your object for reference counting errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="2e3ac-112">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="2e3ac-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="2e3ac-113">K dispozici jsou dva režimy.</span><span class="sxs-lookup"><span data-stu-id="2e3ac-113">Two modes are available.</span></span> <span data-ttu-id="2e3ac-114">Pokud `allowAv` atribut je `true`, pomocníka zabraňuje modulu runtime zahazuje se narušení přístupu.</span><span class="sxs-lookup"><span data-stu-id="2e3ac-114">If the `allowAv` attribute is `true`, the assistant prevents the runtime from discarding the access violation.</span></span> <span data-ttu-id="2e3ac-115">Pokud `allowAv` je `false`, což je výchozí, modul runtime odstraní narušení přístupu, ale upozornění se oznamuje službě uživatele k označení, že výjimka byla vyvolána a zahodí.</span><span class="sxs-lookup"><span data-stu-id="2e3ac-115">If `allowAv` is `false`, which is the default, the runtime discards the access violation, but a warning message is reported to the user to indicate that an exception was thrown and discarded.</span></span>  
  
## <a name="output"></a><span data-ttu-id="2e3ac-116">Výstup</span><span class="sxs-lookup"><span data-stu-id="2e3ac-116">Output</span></span>  
 <span data-ttu-id="2e3ac-117">Pokud je to možné výstup obsahuje původní ukazatel rozhraní modelu COM vtable.</span><span class="sxs-lookup"><span data-stu-id="2e3ac-117">If possible, the output contains the COM interface pointer's original vtable.</span></span> <span data-ttu-id="2e3ac-118">V opačném případě se zobrazí informační zpráva.</span><span class="sxs-lookup"><span data-stu-id="2e3ac-118">Otherwise, an informational message is displayed.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="2e3ac-119">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="2e3ac-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e3ac-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e3ac-120">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="2e3ac-121">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="2e3ac-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="2e3ac-122">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="2e3ac-122">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
