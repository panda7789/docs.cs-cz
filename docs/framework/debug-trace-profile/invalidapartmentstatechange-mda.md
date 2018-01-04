---
title: "invalidApartmentStateChange – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid apartment state
- managed debugging assistants (MDAs), invalid apartment state
- InvalidApartmentStateChange MDA
- invalid apartment state changes
- threading [.NET Framework], apartment states
- apartment states
- threading [.NET Framework], managed debugging assistants
- COM apartment states
ms.assetid: e56fb9df-5286-4be7-b313-540c4d876cd7
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 654e950aab0e8ae2929a62e035ffc1252c5717d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="invalidapartmentstatechange-mda"></a><span data-ttu-id="c9ff3-102">invalidApartmentStateChange – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="c9ff3-102">invalidApartmentStateChange MDA</span></span>
<span data-ttu-id="c9ff3-103">`invalidApartmentStateChange` Pomocník spravovaného ladění (MDS) je aktivován buď dva problémy:</span><span class="sxs-lookup"><span data-stu-id="c9ff3-103">The `invalidApartmentStateChange` managed debugging assistant (MDS) is activated by either of two problems:</span></span>  
  
-   <span data-ttu-id="c9ff3-104">Chcete-li změnit stav objektu apartment COM podproces, který již byl inicializován nástrojem COM do stavu různých apartment je proveden pokus o.</span><span class="sxs-lookup"><span data-stu-id="c9ff3-104">An attempt is made to change the COM apartment state of a thread that has already been initialized by COM to a different apartment state.</span></span>  
  
-   <span data-ttu-id="c9ff3-105">Neočekávaně se změní stav objektu apartment COM vlákna.</span><span class="sxs-lookup"><span data-stu-id="c9ff3-105">The COM apartment state of a thread changes unexpectedly.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c9ff3-106">Příznaky</span><span class="sxs-lookup"><span data-stu-id="c9ff3-106">Symptoms</span></span>  
  
-   <span data-ttu-id="c9ff3-107">Stav objektu apartment COM vlákno je co nebyl požadován.</span><span class="sxs-lookup"><span data-stu-id="c9ff3-107">A thread's COM apartment state is not what was requested.</span></span> <span data-ttu-id="c9ff3-108">To může způsobit proxy, který se má použít pro komponenty modelu COM, které mají model vláken liší od aktuální verze.</span><span class="sxs-lookup"><span data-stu-id="c9ff3-108">This may cause proxies to be used for COM components that have a threading model different from the current one.</span></span> <span data-ttu-id="c9ff3-109">Pak může dojít <xref:System.InvalidCastException> vyvolání při volání objektu COM prostřednictvím rozhraní, které nejsou nastaveny pro zařazování mezi apartment.</span><span class="sxs-lookup"><span data-stu-id="c9ff3-109">This in turn may cause an <xref:System.InvalidCastException> to be thrown when calling the COM object through interfaces that are not set up for cross-apartment marshaling.</span></span>  
  
-   <span data-ttu-id="c9ff3-110">Stav objektu apartment COM vlákno je jiné, než se očekávalo.</span><span class="sxs-lookup"><span data-stu-id="c9ff3-110">The COM apartment state of the thread is different than expected.</span></span> <span data-ttu-id="c9ff3-111">To může způsobit <xref:System.Runtime.InteropServices.COMException> s hodnotou HRESULT RPC_E_WRONG_THREAD a také <xref:System.InvalidCastException> při provádění volání na [obálka volatelná za běhu](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW).</span><span class="sxs-lookup"><span data-stu-id="c9ff3-111">This can cause a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD as well as a <xref:System.InvalidCastException> when making calls on a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="c9ff3-112">To může způsobit také některé jednovláknové součásti COM přístup více vláken ve stejnou dobu, což může vést k poškození nebo ztrátě dat.</span><span class="sxs-lookup"><span data-stu-id="c9ff3-112">This can also cause some single-threaded COM components to be accessed by multiple threads at the same time, which can lead to corruption or data loss.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c9ff3-113">příčina</span><span class="sxs-lookup"><span data-stu-id="c9ff3-113">Cause</span></span>  
  
-   <span data-ttu-id="c9ff3-114">Vlákno byl dříve na jiný stav objektu apartment COM inicializován.</span><span class="sxs-lookup"><span data-stu-id="c9ff3-114">The thread was previously initialized to a different COM apartment state.</span></span> <span data-ttu-id="c9ff3-115">Všimněte si, že stav objektu apartment vlákna lze nastavit explicitně nebo implicitně.</span><span class="sxs-lookup"><span data-stu-id="c9ff3-115">Note that the apartment state of a thread can be set either explicitly or implicitly.</span></span> <span data-ttu-id="c9ff3-116">Explicitní operace zahrnují <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> vlastnost a <xref:System.Threading.Thread.SetApartmentState%2A> a <xref:System.Threading.Thread.TrySetApartmentState%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c9ff3-116">The explicit operations include the <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> property and the <xref:System.Threading.Thread.SetApartmentState%2A> and <xref:System.Threading.Thread.TrySetApartmentState%2A> methods.</span></span> <span data-ttu-id="c9ff3-117">Vlákno vytvořené pomocí <xref:System.Threading.Thread.Start%2A> je implicitně nastavena metoda <xref:System.Threading.ApartmentState.MTA> Pokud <xref:System.Threading.Thread.SetApartmentState%2A> je volat před zahájením vlákno.</span><span class="sxs-lookup"><span data-stu-id="c9ff3-117">A thread created using the <xref:System.Threading.Thread.Start%2A> method is implicitly set to <xref:System.Threading.ApartmentState.MTA> unless <xref:System.Threading.Thread.SetApartmentState%2A> is called before the thread is started.</span></span> <span data-ttu-id="c9ff3-118">Hlavní vlákno aplikace je také implicitně inicializována tak, aby <xref:System.Threading.ApartmentState.MTA> Pokud <xref:System.STAThreadAttribute> atribut je zadaný na hlavní metodu.</span><span class="sxs-lookup"><span data-stu-id="c9ff3-118">The main thread of the application is also implicitly initialized to <xref:System.Threading.ApartmentState.MTA> unless the <xref:System.STAThreadAttribute> attribute is specified on the main method.</span></span>  
  
-   <span data-ttu-id="c9ff3-119">`CoUninitialize` – Metoda (nebo `CoInitializeEx` metoda) s jinou souběžnosti se nazývá model na vlákno.</span><span class="sxs-lookup"><span data-stu-id="c9ff3-119">The `CoUninitialize` method (or the `CoInitializeEx` method) with a different concurrency model is called on the thread.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c9ff3-120">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="c9ff3-120">Resolution</span></span>  
 <span data-ttu-id="c9ff3-121">Nastavit stav objektu apartment vlákna, než začne provádění nebo použít buď <xref:System.STAThreadAttribute> atribut nebo <xref:System.MTAThreadAttribute> atribut hlavní metodu aplikace.</span><span class="sxs-lookup"><span data-stu-id="c9ff3-121">Set the apartment state of the thread before it begins executing, or apply either the <xref:System.STAThreadAttribute> attribute or the <xref:System.MTAThreadAttribute> attribute to the main method of the application.</span></span>  
  
 <span data-ttu-id="c9ff3-122">Pro druhý příčina v ideálním případě kód, který volá `CoUninitialize` by měl být upraven metoda k volání počkat, až budou vlákno se chystá ukončit a neexistují žádné RCWs a jejich základní komponenty modelu COM stále používá vlákno.</span><span class="sxs-lookup"><span data-stu-id="c9ff3-122">For the second cause, ideally, the code that calls the `CoUninitialize` method should be modified to delay the call until the thread is about to terminate and there are no RCWs and their underlying COM components still in use by the thread.</span></span> <span data-ttu-id="c9ff3-123">Ale pokud není možné změnit kód, který volá `CoUninitialize` metoda pak žádné RCWs slouží z vláken, které jsou tímto způsobem Neinicializovaný.</span><span class="sxs-lookup"><span data-stu-id="c9ff3-123">However, if it is not possible to modify the code that calls the `CoUninitialize` method, then no RCWs should be used from threads that are uninitialized in this way.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c9ff3-124">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="c9ff3-124">Effect on the Runtime</span></span>  
 <span data-ttu-id="c9ff3-125">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="c9ff3-125">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c9ff3-126">Výstup</span><span class="sxs-lookup"><span data-stu-id="c9ff3-126">Output</span></span>  
 <span data-ttu-id="c9ff3-127">Stav objektu apartment COM aktuální vlákno a stav, který kód při pokusu o použití.</span><span class="sxs-lookup"><span data-stu-id="c9ff3-127">The COM apartment state of the current thread, and the state that the code was attempting to apply.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c9ff3-128">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c9ff3-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="c9ff3-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="c9ff3-129">Example</span></span>  
 <span data-ttu-id="c9ff3-130">Následující příklad kódu ukazuje situace, které můžou aktivovat tuto (mda).</span><span class="sxs-lookup"><span data-stu-id="c9ff3-130">The following code example demonstrates a situation that can activate this MDA.</span></span>  
  
```  
using System.Threading;  
namespace ApartmentStateMDA  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Thread.CurrentThread.SetApartmentState(ApartmentState.STA);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9ff3-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="c9ff3-131">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="c9ff3-132">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="c9ff3-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="c9ff3-133">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="c9ff3-133">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
