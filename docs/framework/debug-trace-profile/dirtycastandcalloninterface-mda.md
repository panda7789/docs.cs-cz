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
ms.openlocfilehash: 6ac43f6b92198fec03e722b6cf5e12b86df6f4b8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052866"
---
# <a name="dirtycastandcalloninterface-mda"></a><span data-ttu-id="dc993-102">dirtyCastAndCallOnInterface – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="dc993-102">dirtyCastAndCallOnInterface MDA</span></span>
<span data-ttu-id="dc993-103">Pomocník `dirtyCastAndCallOnInterface` spravovaného ladění (MDA) je aktivován při pokusu o volání s časnou vazbou prostřednictvím vtable na rozhraní třídy, které bylo označeno pouze s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="dc993-103">The `dirtyCastAndCallOnInterface` managed debugging assistant (MDA) is activated when an early-bound call through a vtable is attempted on a class interface that has been marked late-bound only.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="dc993-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="dc993-104">Symptoms</span></span>  
 <span data-ttu-id="dc993-105">Aplikace vyvolá narušení přístupu nebo má neočekávané chování při umísťování volání s časnou vazbou přes COM do CLR.</span><span class="sxs-lookup"><span data-stu-id="dc993-105">An application throws an access violation or has unexpected behavior when placing an early-bound call via COM into the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="dc993-106">příčina</span><span class="sxs-lookup"><span data-stu-id="dc993-106">Cause</span></span>  
 <span data-ttu-id="dc993-107">Kód provádí pokus o předčasné vázání prostřednictvím metody vtable prostřednictvím rozhraní třídy, které je pouze pro pozdní vazbu.</span><span class="sxs-lookup"><span data-stu-id="dc993-107">Code is attempting an early-bound call through a vtable via a class interface that is late-bound only.</span></span> <span data-ttu-id="dc993-108">Všimněte si, že ve výchozím nastavení jsou rozhraní třídy identifikována pouze s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="dc993-108">Note that by default class interfaces are identified as being late-bound only.</span></span> <span data-ttu-id="dc993-109">Mohou být také identifikovány jako pozdní vazby s <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributem <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> s hodnotou (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span><span class="sxs-lookup"><span data-stu-id="dc993-109">They can also be identified as late-bound with the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute with an <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> value (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="dc993-110">Řešení</span><span class="sxs-lookup"><span data-stu-id="dc993-110">Resolution</span></span>  
 <span data-ttu-id="dc993-111">Doporučené řešení je definování explicitního rozhraní pro použití modelem COM a zaznamenání klientů modelu COM prostřednictvím tohoto rozhraní místo pomocí automaticky generovaného rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="dc993-111">The recommended resolution is to define an explicit interface for use by COM and have the COM clients call through this interface instead of through the automatically generated class interface.</span></span> <span data-ttu-id="dc993-112">Alternativně lze volání z modelu COM transformovat do volání s pozdní vazbou prostřednictvím `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="dc993-112">Alternatively, the call from COM can be transformed into a late-bound call via `IDispatch`.</span></span>  
  
 <span data-ttu-id="dc993-113">Nakonec je možné identifikovat třídu <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> jako (`[ClassInterface(ClassInterfaceType.AutoDual)]`) a umožnit tak volání počátečních vazeb z modelu COM. použití <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> je však důrazně nedoporučeno z důvodu omezení verzí popsaných v <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>tématu.</span><span class="sxs-lookup"><span data-stu-id="dc993-113">Finally, it is possible to identify the class as <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) to allow early bound calls to be placed from COM; however, using <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> is strongly discouraged because of the versioning limitations described in <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="dc993-114">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="dc993-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="dc993-115">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="dc993-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="dc993-116">Oznamuje pouze data o voláních s časnou vazbou na rozhraních s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="dc993-116">It only reports data about early-bound calls on late-bound interfaces.</span></span>  
  
## <a name="output"></a><span data-ttu-id="dc993-117">Výstup</span><span class="sxs-lookup"><span data-stu-id="dc993-117">Output</span></span>  
 <span data-ttu-id="dc993-118">Název metody nebo názvu pole, ke kterému se přistupovalo s časnou vazbou</span><span class="sxs-lookup"><span data-stu-id="dc993-118">The name of the method or name of the field being accessed early-bound.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="dc993-119">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="dc993-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dc993-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dc993-120">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="dc993-121">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="dc993-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
