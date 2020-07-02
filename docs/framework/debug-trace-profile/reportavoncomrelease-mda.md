---
title: reportAvOnComRelease – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění Reportavoncomrelease – (MDA), který může být aktivovaný z důvodu narušení přístupu a poškození paměti v rozhraní .NET.
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
ms.openlocfilehash: f9ba343060cb4d16de5909a5b619353546aca8ca
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803607"
---
# <a name="reportavoncomrelease-mda"></a><span data-ttu-id="85e2c-103">reportAvOnComRelease – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="85e2c-103">reportAvOnComRelease MDA</span></span>
<span data-ttu-id="85e2c-104">`reportAvOnComRelease`Pomocník spravovaného ladění (MDA) je aktivován, pokud jsou výjimky vyvolány z důvodu chyby počítání odkazů uživatele při provádění zprostředkovatele komunikace s objekty COM a pomocí <xref:System.Runtime.InteropServices.Marshal.Release%2A> <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> metody nebo kombinované s nezpracovanými voláními modelu COM.</span><span class="sxs-lookup"><span data-stu-id="85e2c-104">The `reportAvOnComRelease` managed debugging assistant (MDA) is activated when exceptions are thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="85e2c-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="85e2c-105">Symptoms</span></span>  
 <span data-ttu-id="85e2c-106">Narušení přístupu a poškození paměti.</span><span class="sxs-lookup"><span data-stu-id="85e2c-106">Access violations and memory corruption.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="85e2c-107">Příčina</span><span class="sxs-lookup"><span data-stu-id="85e2c-107">Cause</span></span>  
 <span data-ttu-id="85e2c-108">V některých případech je výjimka vyvolána z důvodu chyby počítání odkazů uživatele při provádění zprostředkovatele komunikace s objekty COM a použití <xref:System.Runtime.InteropServices.Marshal.Release%2A> <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> metody nebo kombinované s nezpracovanými voláními com.</span><span class="sxs-lookup"><span data-stu-id="85e2c-108">Occasionally, an exception is thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span> <span data-ttu-id="85e2c-109">V normálním případě je tato výjimka zahozena, protože to nedělá, by způsobilo narušení přístupu v modulu CLR, takže by to mělo za následek.</span><span class="sxs-lookup"><span data-stu-id="85e2c-109">Normally, this exception is discarded because not doing so would cause an access violation in the CLR, bringing it down.</span></span> <span data-ttu-id="85e2c-110">Když je tento asistent povolený, můžou se tyto výjimky detekovat a nahlásit místo pouhého zahození.</span><span class="sxs-lookup"><span data-stu-id="85e2c-110">When this assistant is enabled, such exceptions can be detected and reported instead of being simply discarded.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="85e2c-111">Řešení</span><span class="sxs-lookup"><span data-stu-id="85e2c-111">Resolution</span></span>  
 <span data-ttu-id="85e2c-112">Prozkoumejte kód pro počítání odkazů a vyhledejte chyby a také prozkoumání nativních klientů vašeho objektu pro chyby počítání odkazů.</span><span class="sxs-lookup"><span data-stu-id="85e2c-112">Examine your reference counting code and search for errors as well as examining the native clients of your object for reference counting errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="85e2c-113">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="85e2c-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="85e2c-114">K dispozici jsou dva režimy.</span><span class="sxs-lookup"><span data-stu-id="85e2c-114">Two modes are available.</span></span> <span data-ttu-id="85e2c-115">Pokud `allowAv` je atribut `true` , asistent zabraňuje modulu runtime v zahození porušení přístupu.</span><span class="sxs-lookup"><span data-stu-id="85e2c-115">If the `allowAv` attribute is `true`, the assistant prevents the runtime from discarding the access violation.</span></span> <span data-ttu-id="85e2c-116">Pokud `allowAv` je `false` , což je výchozí hodnota, modul runtime zruší porušení přístupu, ale uživateli je hlášena zpráva s upozorněním, že byla vyvolána výjimka a byla zahozena.</span><span class="sxs-lookup"><span data-stu-id="85e2c-116">If `allowAv` is `false`, which is the default, the runtime discards the access violation, but a warning message is reported to the user to indicate that an exception was thrown and discarded.</span></span>  
  
## <a name="output"></a><span data-ttu-id="85e2c-117">Výstup</span><span class="sxs-lookup"><span data-stu-id="85e2c-117">Output</span></span>  
 <span data-ttu-id="85e2c-118">Pokud je to možné, výstup obsahuje původní tabulku vtable ukazatele rozhraní modelu COM.</span><span class="sxs-lookup"><span data-stu-id="85e2c-118">If possible, the output contains the COM interface pointer's original vtable.</span></span> <span data-ttu-id="85e2c-119">V opačném případě se zobrazí informační zpráva.</span><span class="sxs-lookup"><span data-stu-id="85e2c-119">Otherwise, an informational message is displayed.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="85e2c-120">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="85e2c-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="85e2c-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85e2c-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="85e2c-122">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="85e2c-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="85e2c-123">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="85e2c-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
