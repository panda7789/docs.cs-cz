---
title: "dirtyCastAndCallOnInterface – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), early bound calls AutoDispatch
- dispatch-only mode
- dirtyCastAndCallOnInterface
- early-bound managed classes
- early bound calls on AutoDispatch
- MDAs (managed debugging assistants), early bound calls AutoDispatch
- EarlyBoundCallOnAutorDispatchClassInteface MDA
ms.assetid: aa388ed3-7e3d-48ea-a0b5-c47ae19cec38
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: eebbf48f084a0c0125bf40e5e14b8c71c1b0a6ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="dirtycastandcalloninterface-mda"></a><span data-ttu-id="ffbc1-102">dirtyCastAndCallOnInterface – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="ffbc1-102">dirtyCastAndCallOnInterface MDA</span></span>
<span data-ttu-id="ffbc1-103">`dirtyCastAndCallOnInterface` Pomocník spravovaného ladění (MDA) se aktivuje, když dojde k pokusu o třídy rozhraní, které bylo označeno jako pozdní vazbou pouze volání časné vazby prostřednictvím vtable.</span><span class="sxs-lookup"><span data-stu-id="ffbc1-103">The `dirtyCastAndCallOnInterface` managed debugging assistant (MDA) is activated when an early-bound call through a vtable is attempted on a class interface that has been marked late-bound only.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="ffbc1-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="ffbc1-104">Symptoms</span></span>  
 <span data-ttu-id="ffbc1-105">Aplikace vyvolá porušení pravidel přístupu nebo má neočekávanému chování při umísťování volání časné vazby prostřednictvím COM do modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="ffbc1-105">An application throws an access violation or has unexpected behavior when placing an early-bound call via COM into the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="ffbc1-106">příčina</span><span class="sxs-lookup"><span data-stu-id="ffbc1-106">Cause</span></span>  
 <span data-ttu-id="ffbc1-107">Kód se pokouší volání časné vazby prostřednictvím vtable prostřednictvím třídy rozhraní, které je pouze pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="ffbc1-107">Code is attempting an early-bound call through a vtable via a class interface that is late-bound only.</span></span> <span data-ttu-id="ffbc1-108">Všimněte si, že třídou výchozí rozhraní považujete za probíhá pozdní vazbou jenom.</span><span class="sxs-lookup"><span data-stu-id="ffbc1-108">Note that by default class interfaces are identified as being late-bound only.</span></span> <span data-ttu-id="ffbc1-109">Můžete také možné identifikovat jako pozdní vazbu s <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atribut s <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> hodnotu (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span><span class="sxs-lookup"><span data-stu-id="ffbc1-109">They can also be identified as late-bound with the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute with an <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> value (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="ffbc1-110">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="ffbc1-110">Resolution</span></span>  
 <span data-ttu-id="ffbc1-111">Doporučené řešení je definovat explicitní rozhraní pro použití v modelu COM a máte klienty volání COM prostřednictvím tohoto rozhraní místo přes rozhraní automaticky vygenerované třídy.</span><span class="sxs-lookup"><span data-stu-id="ffbc1-111">The recommended resolution is to define an explicit interface for use by COM and have the COM clients call through this interface instead of through the automatically generated class interface.</span></span> <span data-ttu-id="ffbc1-112">Alternativně lze je transformovat volání z modelu COM do volání pozdní vazbou prostřednictvím `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="ffbc1-112">Alternatively, the call from COM can be transformed into a late-bound call via `IDispatch`.</span></span>  
  
 <span data-ttu-id="ffbc1-113">Nakonec je možné k identifikaci třídy jako <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) Chcete-li povolit volání časné umístit z modelu COM; však pomocí <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> se důrazně nedoporučuje kvůli Správa verzí omezení popsaná v <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ffbc1-113">Finally, it is possible to identify the class as <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) to allow early bound calls to be placed from COM; however, using <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> is strongly discouraged because of the versioning limitations described in <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ffbc1-114">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="ffbc1-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="ffbc1-115">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="ffbc1-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="ffbc1-116">Pouze sestavy data o volání časné vazby na rozhraní pozdní vazbu.</span><span class="sxs-lookup"><span data-stu-id="ffbc1-116">It only reports data about early-bound calls on late-bound interfaces.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ffbc1-117">Výstup</span><span class="sxs-lookup"><span data-stu-id="ffbc1-117">Output</span></span>  
 <span data-ttu-id="ffbc1-118">Název metody nebo název pole přistupuje časné vazby.</span><span class="sxs-lookup"><span data-stu-id="ffbc1-118">The name of the method or name of the field being accessed early-bound.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="ffbc1-119">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="ffbc1-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ffbc1-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="ffbc1-120">See Also</span></span>  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>  
 [<span data-ttu-id="ffbc1-121">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="ffbc1-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
