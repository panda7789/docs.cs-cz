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
ms.openlocfilehash: 5a28820479ca15ad72475ae9a7754bbbf99ce5c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108586"
---
# <a name="dirtycastandcalloninterface-mda"></a><span data-ttu-id="7b08a-102">dirtyCastAndCallOnInterface – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="7b08a-102">dirtyCastAndCallOnInterface MDA</span></span>
<span data-ttu-id="7b08a-103">`dirtyCastAndCallOnInterface` Pomocníka spravovaného ladění (MDA) se aktivuje, když dojde k pokusu o volání časnou vazbou prostřednictvím tabulku vtable na třídy rozhraní, která byla označena s pozdní vazbou pouze.</span><span class="sxs-lookup"><span data-stu-id="7b08a-103">The `dirtyCastAndCallOnInterface` managed debugging assistant (MDA) is activated when an early-bound call through a vtable is attempted on a class interface that has been marked late-bound only.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="7b08a-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="7b08a-104">Symptoms</span></span>  
 <span data-ttu-id="7b08a-105">Aplikace vyvolá narušení přístupu, nebo obsahuje neočekávané chování při volání časnou vazbou prostřednictvím modelu COM do CLR.</span><span class="sxs-lookup"><span data-stu-id="7b08a-105">An application throws an access violation or has unexpected behavior when placing an early-bound call via COM into the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="7b08a-106">Příčina</span><span class="sxs-lookup"><span data-stu-id="7b08a-106">Cause</span></span>  
 <span data-ttu-id="7b08a-107">Kód se pokouší o volání časné vazby prostřednictvím vtable prostřednictvím třídy rozhraní, které je pouze s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="7b08a-107">Code is attempting an early-bound call through a vtable via a class interface that is late-bound only.</span></span> <span data-ttu-id="7b08a-108">Všimněte si, že výchozí třídou rozhraní považujete za se s pozdní vazbou pouze.</span><span class="sxs-lookup"><span data-stu-id="7b08a-108">Note that by default class interfaces are identified as being late-bound only.</span></span> <span data-ttu-id="7b08a-109">Je také možné identifikovat jako s pozdní vazbou pomocí <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributem <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> hodnotu (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span><span class="sxs-lookup"><span data-stu-id="7b08a-109">They can also be identified as late-bound with the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute with an <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> value (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="7b08a-110">Řešení</span><span class="sxs-lookup"><span data-stu-id="7b08a-110">Resolution</span></span>  
 <span data-ttu-id="7b08a-111">Doporučené řešení je definovat explicitní rozhraní pro použití modelem COM a mít volání klienty modelu COM prostřednictvím tohoto rozhraní místo přes rozhraní automaticky generovanou třídu.</span><span class="sxs-lookup"><span data-stu-id="7b08a-111">The recommended resolution is to define an explicit interface for use by COM and have the COM clients call through this interface instead of through the automatically generated class interface.</span></span> <span data-ttu-id="7b08a-112">Alternativně je možné transformovat volání z modelu COM do volání s pozdní vazbou prostřednictvím `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="7b08a-112">Alternatively, the call from COM can be transformed into a late-bound call via `IDispatch`.</span></span>  
  
 <span data-ttu-id="7b08a-113">Nakonec je možné identifikovat třídu jako <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) Chcete-li povolit volání časné umístit z modelu COM; však pomocí <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> se důrazně nedoporučuje kvůli omezení správy verzí je popsáno v <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7b08a-113">Finally, it is possible to identify the class as <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) to allow early bound calls to be placed from COM; however, using <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> is strongly discouraged because of the versioning limitations described in <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="7b08a-114">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="7b08a-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="7b08a-115">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="7b08a-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="7b08a-116">Sestavy pouze data o volání časné vazby na rozhraní s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="7b08a-116">It only reports data about early-bound calls on late-bound interfaces.</span></span>  
  
## <a name="output"></a><span data-ttu-id="7b08a-117">Výstup</span><span class="sxs-lookup"><span data-stu-id="7b08a-117">Output</span></span>  
 <span data-ttu-id="7b08a-118">Název metody nebo název pole, ke kterému přistupujete časné vazby.</span><span class="sxs-lookup"><span data-stu-id="7b08a-118">The name of the method or name of the field being accessed early-bound.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="7b08a-119">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="7b08a-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b08a-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b08a-120">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="7b08a-121">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="7b08a-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
