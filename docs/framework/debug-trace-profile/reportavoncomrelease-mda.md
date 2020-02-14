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
ms.openlocfilehash: fca6b209e6432678a264f10762adb3871e3596ce
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217226"
---
# <a name="reportavoncomrelease-mda"></a><span data-ttu-id="7fdfc-102">reportAvOnComRelease – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="7fdfc-102">reportAvOnComRelease MDA</span></span>
<span data-ttu-id="7fdfc-103">Pokud jsou výjimky vyvolány z důvodu chyby počítání odkazů uživatele při provádění zprostředkovatele komunikace s objekty COM a použitím metody <xref:System.Runtime.InteropServices.Marshal.Release%2A> nebo <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> kombinované s nezpracovanými voláními modelu COM, je aktivována aplikace `reportAvOnComRelease` Managed Debugging Assistant (MDA).</span><span class="sxs-lookup"><span data-stu-id="7fdfc-103">The `reportAvOnComRelease` managed debugging assistant (MDA) is activated when exceptions are thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="7fdfc-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="7fdfc-104">Symptoms</span></span>  
 <span data-ttu-id="7fdfc-105">Narušení přístupu a poškození paměti.</span><span class="sxs-lookup"><span data-stu-id="7fdfc-105">Access violations and memory corruption.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="7fdfc-106">Příčina</span><span class="sxs-lookup"><span data-stu-id="7fdfc-106">Cause</span></span>  
 <span data-ttu-id="7fdfc-107">V některých případech je výjimka vyvolána z důvodu chyby počítání odkazů uživatele při provádění zprostředkovatele komunikace s objekty COM a použití metody <xref:System.Runtime.InteropServices.Marshal.Release%2A> nebo <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> kombinované s nezpracovanými voláními COM.</span><span class="sxs-lookup"><span data-stu-id="7fdfc-107">Occasionally, an exception is thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span> <span data-ttu-id="7fdfc-108">V normálním případě je tato výjimka zahozena, protože to nedělá, by způsobilo narušení přístupu v modulu CLR, takže by to mělo za následek.</span><span class="sxs-lookup"><span data-stu-id="7fdfc-108">Normally, this exception is discarded because not doing so would cause an access violation in the CLR, bringing it down.</span></span> <span data-ttu-id="7fdfc-109">Když je tento asistent povolený, můžou se tyto výjimky detekovat a nahlásit místo pouhého zahození.</span><span class="sxs-lookup"><span data-stu-id="7fdfc-109">When this assistant is enabled, such exceptions can be detected and reported instead of being simply discarded.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="7fdfc-110">Řešení</span><span class="sxs-lookup"><span data-stu-id="7fdfc-110">Resolution</span></span>  
 <span data-ttu-id="7fdfc-111">Prozkoumejte kód pro počítání odkazů a vyhledejte chyby a také prozkoumání nativních klientů vašeho objektu pro chyby počítání odkazů.</span><span class="sxs-lookup"><span data-stu-id="7fdfc-111">Examine your reference counting code and search for errors as well as examining the native clients of your object for reference counting errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="7fdfc-112">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="7fdfc-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="7fdfc-113">K dispozici jsou dva režimy.</span><span class="sxs-lookup"><span data-stu-id="7fdfc-113">Two modes are available.</span></span> <span data-ttu-id="7fdfc-114">Pokud je atribut `allowAv` `true`, asistent zabraňuje modulu runtime v zahození porušení přístupu.</span><span class="sxs-lookup"><span data-stu-id="7fdfc-114">If the `allowAv` attribute is `true`, the assistant prevents the runtime from discarding the access violation.</span></span> <span data-ttu-id="7fdfc-115">Je-li `allowAv` `false`, což je výchozí hodnota, modul runtime zruší porušení přístupu, ale uživateli je hlášena zpráva s upozorněním, že byla vyvolána výjimka a zahozena.</span><span class="sxs-lookup"><span data-stu-id="7fdfc-115">If `allowAv` is `false`, which is the default, the runtime discards the access violation, but a warning message is reported to the user to indicate that an exception was thrown and discarded.</span></span>  
  
## <a name="output"></a><span data-ttu-id="7fdfc-116">Výstup</span><span class="sxs-lookup"><span data-stu-id="7fdfc-116">Output</span></span>  
 <span data-ttu-id="7fdfc-117">Pokud je to možné, výstup obsahuje původní tabulku vtable ukazatele rozhraní modelu COM.</span><span class="sxs-lookup"><span data-stu-id="7fdfc-117">If possible, the output contains the COM interface pointer's original vtable.</span></span> <span data-ttu-id="7fdfc-118">V opačném případě se zobrazí informační zpráva.</span><span class="sxs-lookup"><span data-stu-id="7fdfc-118">Otherwise, an informational message is displayed.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="7fdfc-119">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="7fdfc-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7fdfc-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="7fdfc-120">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="7fdfc-121">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="7fdfc-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="7fdfc-122">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="7fdfc-122">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
