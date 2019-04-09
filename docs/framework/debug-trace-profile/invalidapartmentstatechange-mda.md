---
title: invalidApartmentStateChange – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c201ab51c1af8a86fc1c2c4f80738007152b3bd9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122847"
---
# <a name="invalidapartmentstatechange-mda"></a><span data-ttu-id="28476-102">invalidApartmentStateChange – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="28476-102">invalidApartmentStateChange MDA</span></span>
<span data-ttu-id="28476-103">`invalidApartmentStateChange` Pomocníka spravovaného ladění (MDS) je aktivován některý z dva problémy:</span><span class="sxs-lookup"><span data-stu-id="28476-103">The `invalidApartmentStateChange` managed debugging assistant (MDS) is activated by either of two problems:</span></span>  
  
-   <span data-ttu-id="28476-104">Chcete-li změnit stavu apartment modelu COM, který již byl inicializován pomocí modelu COM do stavu různých apartment vlákna je proveden pokus o.</span><span class="sxs-lookup"><span data-stu-id="28476-104">An attempt is made to change the COM apartment state of a thread that has already been initialized by COM to a different apartment state.</span></span>  
  
-   <span data-ttu-id="28476-105">Neočekávaně se změní stav objektu apartment modelu COM vlákna.</span><span class="sxs-lookup"><span data-stu-id="28476-105">The COM apartment state of a thread changes unexpectedly.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="28476-106">Příznaky</span><span class="sxs-lookup"><span data-stu-id="28476-106">Symptoms</span></span>  
  
-   <span data-ttu-id="28476-107">Stav objektu apartment modelu COM vlákna je co nebyl požadován.</span><span class="sxs-lookup"><span data-stu-id="28476-107">A thread's COM apartment state is not what was requested.</span></span> <span data-ttu-id="28476-108">To může způsobit proxy má být použit pro komponenty modelu COM, které mají jiný než aktuální model vlákna.</span><span class="sxs-lookup"><span data-stu-id="28476-108">This may cause proxies to be used for COM components that have a threading model different from the current one.</span></span> <span data-ttu-id="28476-109">Pak může dojít <xref:System.InvalidCastException> vyvolání při volání objektu COM prostřednictvím rozhraní, které nejsou nastaveny pro zařazování mezi objektu apartment.</span><span class="sxs-lookup"><span data-stu-id="28476-109">This in turn may cause an <xref:System.InvalidCastException> to be thrown when calling the COM object through interfaces that are not set up for cross-apartment marshaling.</span></span>  
  
-   <span data-ttu-id="28476-110">Stav objektu apartment modelu COM vlákna je jiný, než se očekávalo.</span><span class="sxs-lookup"><span data-stu-id="28476-110">The COM apartment state of the thread is different than expected.</span></span> <span data-ttu-id="28476-111">To může způsobit <xref:System.Runtime.InteropServices.COMException> s HRESULT RPC_E_WRONG_THREAD a také <xref:System.InvalidCastException> při provádění volání na [obálka volatelná za běhu](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW).</span><span class="sxs-lookup"><span data-stu-id="28476-111">This can cause a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD as well as a <xref:System.InvalidCastException> when making calls on a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="28476-112">To může způsobit také některé komponenty modelu COM s jedním vláknem přístup více vláken ve stejnou dobu, což může vést k poškození nebo ztrátě dat k.</span><span class="sxs-lookup"><span data-stu-id="28476-112">This can also cause some single-threaded COM components to be accessed by multiple threads at the same time, which can lead to corruption or data loss.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="28476-113">Příčina</span><span class="sxs-lookup"><span data-stu-id="28476-113">Cause</span></span>  
  
-   <span data-ttu-id="28476-114">K jiným stavem objektu apartment modelu COM byl dřív inicializovaný vlákna.</span><span class="sxs-lookup"><span data-stu-id="28476-114">The thread was previously initialized to a different COM apartment state.</span></span> <span data-ttu-id="28476-115">Všimněte si, že stav oddílu vlákna lze nastavit explicitně nebo implicitně.</span><span class="sxs-lookup"><span data-stu-id="28476-115">Note that the apartment state of a thread can be set either explicitly or implicitly.</span></span> <span data-ttu-id="28476-116">Explicitní operace zahrnují <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> vlastnost a <xref:System.Threading.Thread.SetApartmentState%2A> a <xref:System.Threading.Thread.TrySetApartmentState%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="28476-116">The explicit operations include the <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> property and the <xref:System.Threading.Thread.SetApartmentState%2A> and <xref:System.Threading.Thread.TrySetApartmentState%2A> methods.</span></span> <span data-ttu-id="28476-117">Vlákna vytvořeného <xref:System.Threading.Thread.Start%2A> metoda je implicitně nastavena na <xref:System.Threading.ApartmentState.MTA> Pokud <xref:System.Threading.Thread.SetApartmentState%2A> je volána před spuštěním podprocesu.</span><span class="sxs-lookup"><span data-stu-id="28476-117">A thread created using the <xref:System.Threading.Thread.Start%2A> method is implicitly set to <xref:System.Threading.ApartmentState.MTA> unless <xref:System.Threading.Thread.SetApartmentState%2A> is called before the thread is started.</span></span> <span data-ttu-id="28476-118">Hlavního vlákna aplikace je také implicitně inicializován na <xref:System.Threading.ApartmentState.MTA> není-li <xref:System.STAThreadAttribute> je zadán atribut v hlavní metodě.</span><span class="sxs-lookup"><span data-stu-id="28476-118">The main thread of the application is also implicitly initialized to <xref:System.Threading.ApartmentState.MTA> unless the <xref:System.STAThreadAttribute> attribute is specified on the main method.</span></span>  
  
-   <span data-ttu-id="28476-119">`CoUninitialize` – Metoda (nebo `CoInitializeEx` metoda) s jinou souběžnosti se nazývá modelu ve vlákně.</span><span class="sxs-lookup"><span data-stu-id="28476-119">The `CoUninitialize` method (or the `CoInitializeEx` method) with a different concurrency model is called on the thread.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="28476-120">Řešení</span><span class="sxs-lookup"><span data-stu-id="28476-120">Resolution</span></span>  
 <span data-ttu-id="28476-121">Před zahájením provádění se nastavit stav objektu apartment vlákna, nebo použít buď <xref:System.STAThreadAttribute> atribut nebo <xref:System.MTAThreadAttribute> atribut do metody main aplikace.</span><span class="sxs-lookup"><span data-stu-id="28476-121">Set the apartment state of the thread before it begins executing, or apply either the <xref:System.STAThreadAttribute> attribute or the <xref:System.MTAThreadAttribute> attribute to the main method of the application.</span></span>  
  
 <span data-ttu-id="28476-122">Pro druhý příčinu v ideálním případě by kód, který volá `CoUninitialize` metoda by měla upravit tak, aby zpoždění volání, dokud vlákno se chystá ukončit a neexistují žádné RCW a jejich základní komponenty modelu COM stále používá v vlákna.</span><span class="sxs-lookup"><span data-stu-id="28476-122">For the second cause, ideally, the code that calls the `CoUninitialize` method should be modified to delay the call until the thread is about to terminate and there are no RCWs and their underlying COM components still in use by the thread.</span></span> <span data-ttu-id="28476-123">Ale pokud to není možné upravovat kód, který volá `CoUninitialize` metoda pak žádné RCW by měla sloužit z vláken, které jsou neinicializované tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="28476-123">However, if it is not possible to modify the code that calls the `CoUninitialize` method, then no RCWs should be used from threads that are uninitialized in this way.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="28476-124">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="28476-124">Effect on the Runtime</span></span>  
 <span data-ttu-id="28476-125">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="28476-125">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="28476-126">Výstup</span><span class="sxs-lookup"><span data-stu-id="28476-126">Output</span></span>  
 <span data-ttu-id="28476-127">Stavu apartment modelu COM aktuálního vlákna a stav, který byl pokus o přidání kódu.</span><span class="sxs-lookup"><span data-stu-id="28476-127">The COM apartment state of the current thread, and the state that the code was attempting to apply.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="28476-128">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="28476-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="28476-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="28476-129">Example</span></span>  
 <span data-ttu-id="28476-130">Následující příklad kódu ukazuje situaci, která může aktivovat toto MDA.</span><span class="sxs-lookup"><span data-stu-id="28476-130">The following code example demonstrates a situation that can activate this MDA.</span></span>  
  
```csharp
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
  
## <a name="see-also"></a><span data-ttu-id="28476-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="28476-131">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="28476-132">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="28476-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="28476-133">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="28476-133">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
