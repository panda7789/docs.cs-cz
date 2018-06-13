---
title: dirtyCastAndCallOnInterface – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), early bound calls AutoDispatch
- dispatch-only mode
- dirtyCastAndCallOnInterface
- early-bound managed classes
- early bound calls on AutoDispatch
- MDAs (managed debugging assistants), early bound calls AutoDispatch
- EarlyBoundCallOnAutorDispatchClassInteface MDA
ms.assetid: aa388ed3-7e3d-48ea-a0b5-c47ae19cec38
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b5c54b8c2600dca1c7b24ac663a6ed506ca8ef24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390507"
---
# <a name="dirtycastandcalloninterface-mda"></a><span data-ttu-id="67c93-102">dirtyCastAndCallOnInterface – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="67c93-102">dirtyCastAndCallOnInterface MDA</span></span>
<span data-ttu-id="67c93-103">`dirtyCastAndCallOnInterface` Pomocník spravovaného ladění (MDA) se aktivuje, když dojde k pokusu o třídy rozhraní, které bylo označeno jako pozdní vazbou pouze volání časné vazby prostřednictvím vtable.</span><span class="sxs-lookup"><span data-stu-id="67c93-103">The `dirtyCastAndCallOnInterface` managed debugging assistant (MDA) is activated when an early-bound call through a vtable is attempted on a class interface that has been marked late-bound only.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="67c93-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="67c93-104">Symptoms</span></span>  
 <span data-ttu-id="67c93-105">Aplikace vyvolá porušení pravidel přístupu nebo má neočekávanému chování při umísťování volání časné vazby prostřednictvím COM do modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="67c93-105">An application throws an access violation or has unexpected behavior when placing an early-bound call via COM into the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="67c93-106">příčina</span><span class="sxs-lookup"><span data-stu-id="67c93-106">Cause</span></span>  
 <span data-ttu-id="67c93-107">Kód se pokouší volání časné vazby prostřednictvím vtable prostřednictvím třídy rozhraní, které je pouze pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="67c93-107">Code is attempting an early-bound call through a vtable via a class interface that is late-bound only.</span></span> <span data-ttu-id="67c93-108">Všimněte si, že třídou výchozí rozhraní považujete za probíhá pozdní vazbou jenom.</span><span class="sxs-lookup"><span data-stu-id="67c93-108">Note that by default class interfaces are identified as being late-bound only.</span></span> <span data-ttu-id="67c93-109">Můžete také možné identifikovat jako pozdní vazbu s <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atribut s <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> hodnotu (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span><span class="sxs-lookup"><span data-stu-id="67c93-109">They can also be identified as late-bound with the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute with an <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> value (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="67c93-110">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="67c93-110">Resolution</span></span>  
 <span data-ttu-id="67c93-111">Doporučené řešení je definovat explicitní rozhraní pro použití v modelu COM a máte klienty volání COM prostřednictvím tohoto rozhraní místo přes rozhraní automaticky vygenerované třídy.</span><span class="sxs-lookup"><span data-stu-id="67c93-111">The recommended resolution is to define an explicit interface for use by COM and have the COM clients call through this interface instead of through the automatically generated class interface.</span></span> <span data-ttu-id="67c93-112">Alternativně lze je transformovat volání z modelu COM do volání pozdní vazbou prostřednictvím `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="67c93-112">Alternatively, the call from COM can be transformed into a late-bound call via `IDispatch`.</span></span>  
  
 <span data-ttu-id="67c93-113">Nakonec je možné k identifikaci třídy jako <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) Chcete-li povolit volání časné umístit z modelu COM; však pomocí <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> se důrazně nedoporučuje kvůli Správa verzí omezení popsaná v <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span><span class="sxs-lookup"><span data-stu-id="67c93-113">Finally, it is possible to identify the class as <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) to allow early bound calls to be placed from COM; however, using <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> is strongly discouraged because of the versioning limitations described in <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="67c93-114">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="67c93-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="67c93-115">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="67c93-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="67c93-116">Pouze sestavy data o volání časné vazby na rozhraní pozdní vazbu.</span><span class="sxs-lookup"><span data-stu-id="67c93-116">It only reports data about early-bound calls on late-bound interfaces.</span></span>  
  
## <a name="output"></a><span data-ttu-id="67c93-117">Výstup</span><span class="sxs-lookup"><span data-stu-id="67c93-117">Output</span></span>  
 <span data-ttu-id="67c93-118">Název metody nebo název pole přistupuje časné vazby.</span><span class="sxs-lookup"><span data-stu-id="67c93-118">The name of the method or name of the field being accessed early-bound.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="67c93-119">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="67c93-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="67c93-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="67c93-120">See Also</span></span>  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>  
 [<span data-ttu-id="67c93-121">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="67c93-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
