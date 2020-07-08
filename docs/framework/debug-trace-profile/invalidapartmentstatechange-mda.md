---
title: invalidApartmentStateChange – pomocník spravovaného ladění (MDA)
description: Přečtěte si o nástroji invalidApartmentStateChange – Managed Debugging Assistant (MDA) v rozhraní .NET, který se aktivuje v případě problémů se stavem objektu COM Apartment.
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
ms.openlocfilehash: c6f7b6a5e450d4167946d22b2ada268ea2b0135f
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051824"
---
# <a name="invalidapartmentstatechange-mda"></a><span data-ttu-id="6f427-103">invalidApartmentStateChange – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="6f427-103">invalidApartmentStateChange MDA</span></span>
<span data-ttu-id="6f427-104">`invalidApartmentStateChange`Pomocník spravovaného ladění (MDS) se aktivuje jedním z těchto dvou problémů:</span><span class="sxs-lookup"><span data-stu-id="6f427-104">The `invalidApartmentStateChange` managed debugging assistant (MDS) is activated by either of two problems:</span></span>  
  
- <span data-ttu-id="6f427-105">Došlo k pokusu o změnu stavu objektu COM apartment vlákna, které již bylo inicializováno modelem COM, do jiného stavu objektu apartment.</span><span class="sxs-lookup"><span data-stu-id="6f427-105">An attempt is made to change the COM apartment state of a thread that has already been initialized by COM to a different apartment state.</span></span>  
  
- <span data-ttu-id="6f427-106">Stav objektu COM Apartment v vlákně se neočekávaně mění.</span><span class="sxs-lookup"><span data-stu-id="6f427-106">The COM apartment state of a thread changes unexpectedly.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="6f427-107">Příznaky</span><span class="sxs-lookup"><span data-stu-id="6f427-107">Symptoms</span></span>  
  
- <span data-ttu-id="6f427-108">Stav objektu COM v vlákně vlákna není to, co bylo vyžádáno.</span><span class="sxs-lookup"><span data-stu-id="6f427-108">A thread's COM apartment state is not what was requested.</span></span> <span data-ttu-id="6f427-109">To může způsobit, že se proxy budou používat pro komponenty modelu COM, které mají model podprocesů odlišný od aktuálního typu.</span><span class="sxs-lookup"><span data-stu-id="6f427-109">This may cause proxies to be used for COM components that have a threading model different from the current one.</span></span> <span data-ttu-id="6f427-110">To může způsobit <xref:System.InvalidCastException> , že bude vyvolána výjimka při volání objektu COM prostřednictvím rozhraní, která nejsou nastavena pro zařazování mezi platformami.</span><span class="sxs-lookup"><span data-stu-id="6f427-110">This in turn may cause an <xref:System.InvalidCastException> to be thrown when calling the COM object through interfaces that are not set up for cross-apartment marshaling.</span></span>  
  
- <span data-ttu-id="6f427-111">Stav objektu COM apartment vlákna je jiný, než se očekávalo.</span><span class="sxs-lookup"><span data-stu-id="6f427-111">The COM apartment state of the thread is different than expected.</span></span> <span data-ttu-id="6f427-112">To může způsobit odpověď <xref:System.Runtime.InteropServices.COMException> s hodnotou HRESULT RPC_E_WRONG_THREAD a také <xref:System.InvalidCastException> při volání na [obálku](../../standard/native-interop/runtime-callable-wrapper.md) , která je volána za běhu (RCW).</span><span class="sxs-lookup"><span data-stu-id="6f427-112">This can cause a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD as well as a <xref:System.InvalidCastException> when making calls on a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="6f427-113">To může také způsobit, že některé komponenty modelu COM s jedním vláknem mají přístup více vlákny ve stejnou dobu, což může vést k poškození nebo ztrátě dat.</span><span class="sxs-lookup"><span data-stu-id="6f427-113">This can also cause some single-threaded COM components to be accessed by multiple threads at the same time, which can lead to corruption or data loss.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="6f427-114">Příčina</span><span class="sxs-lookup"><span data-stu-id="6f427-114">Cause</span></span>  
  
- <span data-ttu-id="6f427-115">Vlákno bylo dříve inicializováno do jiného stavu apartment modelu COM.</span><span class="sxs-lookup"><span data-stu-id="6f427-115">The thread was previously initialized to a different COM apartment state.</span></span> <span data-ttu-id="6f427-116">Všimněte si, že stav objektu apartment vlákna lze nastavit buď explicitně, nebo implicitně.</span><span class="sxs-lookup"><span data-stu-id="6f427-116">Note that the apartment state of a thread can be set either explicitly or implicitly.</span></span> <span data-ttu-id="6f427-117">Mezi explicitní operace patří <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> vlastnost a <xref:System.Threading.Thread.SetApartmentState%2A> <xref:System.Threading.Thread.TrySetApartmentState%2A> metody a.</span><span class="sxs-lookup"><span data-stu-id="6f427-117">The explicit operations include the <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> property and the <xref:System.Threading.Thread.SetApartmentState%2A> and <xref:System.Threading.Thread.TrySetApartmentState%2A> methods.</span></span> <span data-ttu-id="6f427-118">Vlákno vytvořené pomocí <xref:System.Threading.Thread.Start%2A> metody je implicitně nastaveno na hodnotu, <xref:System.Threading.ApartmentState.MTA> Pokud <xref:System.Threading.Thread.SetApartmentState%2A> není voláno před spuštěním vlákna.</span><span class="sxs-lookup"><span data-stu-id="6f427-118">A thread created using the <xref:System.Threading.Thread.Start%2A> method is implicitly set to <xref:System.Threading.ApartmentState.MTA> unless <xref:System.Threading.Thread.SetApartmentState%2A> is called before the thread is started.</span></span> <span data-ttu-id="6f427-119">Hlavní vlákno aplikace je také implicitně inicializováno na hodnotu, <xref:System.Threading.ApartmentState.MTA> Pokud <xref:System.STAThreadAttribute> atribut není zadán v metodě Main.</span><span class="sxs-lookup"><span data-stu-id="6f427-119">The main thread of the application is also implicitly initialized to <xref:System.Threading.ApartmentState.MTA> unless the <xref:System.STAThreadAttribute> attribute is specified on the main method.</span></span>  
  
- <span data-ttu-id="6f427-120">`CoUninitialize`Metoda (nebo `CoInitializeEx` Metoda) s jiným modelem souběžnosti je volána ve vlákně.</span><span class="sxs-lookup"><span data-stu-id="6f427-120">The `CoUninitialize` method (or the `CoInitializeEx` method) with a different concurrency model is called on the thread.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="6f427-121">Řešení</span><span class="sxs-lookup"><span data-stu-id="6f427-121">Resolution</span></span>  
 <span data-ttu-id="6f427-122">Nastavte stav objektu apartment vlákna předtím, než se spustí jeho spuštění, nebo použijte <xref:System.STAThreadAttribute> atribut nebo <xref:System.MTAThreadAttribute> atribut na metodu Main aplikace.</span><span class="sxs-lookup"><span data-stu-id="6f427-122">Set the apartment state of the thread before it begins executing, or apply either the <xref:System.STAThreadAttribute> attribute or the <xref:System.MTAThreadAttribute> attribute to the main method of the application.</span></span>  
  
 <span data-ttu-id="6f427-123">V případě druhé příčiny by v ideálním případě by měl být kód, který volá `CoUninitialize` metodu, upraven tak, aby zpozdil volání, dokud vlákno nekončí a neexistují žádné RCW a jejich podkladové komponenty COM jsou stále používány vláknem.</span><span class="sxs-lookup"><span data-stu-id="6f427-123">For the second cause, ideally, the code that calls the `CoUninitialize` method should be modified to delay the call until the thread is about to terminate and there are no RCWs and their underlying COM components still in use by the thread.</span></span> <span data-ttu-id="6f427-124">Nicméně pokud není možné upravit kód, který volá `CoUninitialize` metodu, pak by neměl být použit žádný RCW z vláken, která jsou tímto způsobem neinicializována.</span><span class="sxs-lookup"><span data-stu-id="6f427-124">However, if it is not possible to modify the code that calls the `CoUninitialize` method, then no RCWs should be used from threads that are uninitialized in this way.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="6f427-125">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="6f427-125">Effect on the Runtime</span></span>  
 <span data-ttu-id="6f427-126">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="6f427-126">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="6f427-127">Výstup</span><span class="sxs-lookup"><span data-stu-id="6f427-127">Output</span></span>  
 <span data-ttu-id="6f427-128">Stav objektu COM Apartment aktuálního vlákna a stav, který byl proveden pokus o použití kódu.</span><span class="sxs-lookup"><span data-stu-id="6f427-128">The COM apartment state of the current thread, and the state that the code was attempting to apply.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="6f427-129">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="6f427-129">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="6f427-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="6f427-130">Example</span></span>  
 <span data-ttu-id="6f427-131">Následující příklad kódu ukazuje situaci, která může aktivovat Tento MDA.</span><span class="sxs-lookup"><span data-stu-id="6f427-131">The following code example demonstrates a situation that can activate this MDA.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6f427-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f427-132">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="6f427-133">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="6f427-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="6f427-134">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="6f427-134">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
