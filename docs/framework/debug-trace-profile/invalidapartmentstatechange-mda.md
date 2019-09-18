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
ms.openlocfilehash: ed4933ae59223c0674d2e36428894cbc3a07933f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052667"
---
# <a name="invalidapartmentstatechange-mda"></a><span data-ttu-id="10308-102">invalidApartmentStateChange – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="10308-102">invalidApartmentStateChange MDA</span></span>
<span data-ttu-id="10308-103">Pomocník `invalidApartmentStateChange` spravovaného ladění (MDS) se aktivuje jedním z těchto dvou problémů:</span><span class="sxs-lookup"><span data-stu-id="10308-103">The `invalidApartmentStateChange` managed debugging assistant (MDS) is activated by either of two problems:</span></span>  
  
- <span data-ttu-id="10308-104">Došlo k pokusu o změnu stavu objektu COM apartment vlákna, které již bylo inicializováno modelem COM, do jiného stavu objektu apartment.</span><span class="sxs-lookup"><span data-stu-id="10308-104">An attempt is made to change the COM apartment state of a thread that has already been initialized by COM to a different apartment state.</span></span>  
  
- <span data-ttu-id="10308-105">Stav objektu COM Apartment v vlákně se neočekávaně mění.</span><span class="sxs-lookup"><span data-stu-id="10308-105">The COM apartment state of a thread changes unexpectedly.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="10308-106">Příznaky</span><span class="sxs-lookup"><span data-stu-id="10308-106">Symptoms</span></span>  
  
- <span data-ttu-id="10308-107">Stav objektu COM v vlákně vlákna není to, co bylo vyžádáno.</span><span class="sxs-lookup"><span data-stu-id="10308-107">A thread's COM apartment state is not what was requested.</span></span> <span data-ttu-id="10308-108">To může způsobit, že se proxy budou používat pro komponenty modelu COM, které mají model podprocesů odlišný od aktuálního typu.</span><span class="sxs-lookup"><span data-stu-id="10308-108">This may cause proxies to be used for COM components that have a threading model different from the current one.</span></span> <span data-ttu-id="10308-109">To může způsobit <xref:System.InvalidCastException> , že bude vyvolána výjimka při volání objektu COM prostřednictvím rozhraní, která nejsou nastavena pro zařazování mezi platformami.</span><span class="sxs-lookup"><span data-stu-id="10308-109">This in turn may cause an <xref:System.InvalidCastException> to be thrown when calling the COM object through interfaces that are not set up for cross-apartment marshaling.</span></span>  
  
- <span data-ttu-id="10308-110">Stav objektu COM apartment vlákna je jiný, než se očekávalo.</span><span class="sxs-lookup"><span data-stu-id="10308-110">The COM apartment state of the thread is different than expected.</span></span> <span data-ttu-id="10308-111">To může způsobit neočekávanou hodnotu <xref:System.Runtime.InteropServices.COMException> RPC_E_WRONG_THREAD a také <xref:System.InvalidCastException> při volání na [obálku](../../standard/native-interop/runtime-callable-wrapper.md) , která je volána za běhu (RCW).</span><span class="sxs-lookup"><span data-stu-id="10308-111">This can cause a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD as well as a <xref:System.InvalidCastException> when making calls on a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="10308-112">To může také způsobit, že některé komponenty modelu COM s jedním vláknem mají přístup více vlákny ve stejnou dobu, což může vést k poškození nebo ztrátě dat.</span><span class="sxs-lookup"><span data-stu-id="10308-112">This can also cause some single-threaded COM components to be accessed by multiple threads at the same time, which can lead to corruption or data loss.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="10308-113">příčina</span><span class="sxs-lookup"><span data-stu-id="10308-113">Cause</span></span>  
  
- <span data-ttu-id="10308-114">Vlákno bylo dříve inicializováno do jiného stavu apartment modelu COM.</span><span class="sxs-lookup"><span data-stu-id="10308-114">The thread was previously initialized to a different COM apartment state.</span></span> <span data-ttu-id="10308-115">Všimněte si, že stav objektu apartment vlákna lze nastavit buď explicitně, nebo implicitně.</span><span class="sxs-lookup"><span data-stu-id="10308-115">Note that the apartment state of a thread can be set either explicitly or implicitly.</span></span> <span data-ttu-id="10308-116">Mezi explicitní operace patří <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> vlastnost <xref:System.Threading.Thread.SetApartmentState%2A> a metody a <xref:System.Threading.Thread.TrySetApartmentState%2A> .</span><span class="sxs-lookup"><span data-stu-id="10308-116">The explicit operations include the <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> property and the <xref:System.Threading.Thread.SetApartmentState%2A> and <xref:System.Threading.Thread.TrySetApartmentState%2A> methods.</span></span> <span data-ttu-id="10308-117">Vlákno vytvořené pomocí <xref:System.Threading.Thread.Start%2A> metody je implicitně nastaveno na hodnotu, <xref:System.Threading.ApartmentState.MTA> Pokud <xref:System.Threading.Thread.SetApartmentState%2A> není voláno před spuštěním vlákna.</span><span class="sxs-lookup"><span data-stu-id="10308-117">A thread created using the <xref:System.Threading.Thread.Start%2A> method is implicitly set to <xref:System.Threading.ApartmentState.MTA> unless <xref:System.Threading.Thread.SetApartmentState%2A> is called before the thread is started.</span></span> <span data-ttu-id="10308-118">Hlavní vlákno aplikace je také implicitně inicializováno na hodnotu, <xref:System.Threading.ApartmentState.MTA> <xref:System.STAThreadAttribute> Pokud atribut není zadán v metodě Main.</span><span class="sxs-lookup"><span data-stu-id="10308-118">The main thread of the application is also implicitly initialized to <xref:System.Threading.ApartmentState.MTA> unless the <xref:System.STAThreadAttribute> attribute is specified on the main method.</span></span>  
  
- <span data-ttu-id="10308-119">`CoUninitialize` Metoda (`CoInitializeEx` nebo metoda) s jiným modelem souběžnosti je volána ve vlákně.</span><span class="sxs-lookup"><span data-stu-id="10308-119">The `CoUninitialize` method (or the `CoInitializeEx` method) with a different concurrency model is called on the thread.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="10308-120">Řešení</span><span class="sxs-lookup"><span data-stu-id="10308-120">Resolution</span></span>  
 <span data-ttu-id="10308-121">Nastavte stav objektu apartment vlákna předtím, než se spustí jeho spuštění, nebo použijte <xref:System.STAThreadAttribute> atribut <xref:System.MTAThreadAttribute> nebo atribut na metodu Main aplikace.</span><span class="sxs-lookup"><span data-stu-id="10308-121">Set the apartment state of the thread before it begins executing, or apply either the <xref:System.STAThreadAttribute> attribute or the <xref:System.MTAThreadAttribute> attribute to the main method of the application.</span></span>  
  
 <span data-ttu-id="10308-122">V případě druhé příčiny by v ideálním případě by měl být kód `CoUninitialize` , který volá metodu, upraven tak, aby zpozdil volání, dokud vlákno nekončí a neexistují žádné RCW a jejich podkladové komponenty COM jsou stále používány vláknem.</span><span class="sxs-lookup"><span data-stu-id="10308-122">For the second cause, ideally, the code that calls the `CoUninitialize` method should be modified to delay the call until the thread is about to terminate and there are no RCWs and their underlying COM components still in use by the thread.</span></span> <span data-ttu-id="10308-123">Nicméně pokud není možné upravit kód, který volá `CoUninitialize` metodu, pak by neměl být použit žádný RCW z vláken, která jsou tímto způsobem neinicializována.</span><span class="sxs-lookup"><span data-stu-id="10308-123">However, if it is not possible to modify the code that calls the `CoUninitialize` method, then no RCWs should be used from threads that are uninitialized in this way.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="10308-124">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="10308-124">Effect on the Runtime</span></span>  
 <span data-ttu-id="10308-125">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="10308-125">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="10308-126">Výstup</span><span class="sxs-lookup"><span data-stu-id="10308-126">Output</span></span>  
 <span data-ttu-id="10308-127">Stav objektu COM Apartment aktuálního vlákna a stav, který byl proveden pokus o použití kódu.</span><span class="sxs-lookup"><span data-stu-id="10308-127">The COM apartment state of the current thread, and the state that the code was attempting to apply.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="10308-128">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="10308-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="10308-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="10308-129">Example</span></span>  
 <span data-ttu-id="10308-130">Následující příklad kódu ukazuje situaci, která může aktivovat Tento MDA.</span><span class="sxs-lookup"><span data-stu-id="10308-130">The following code example demonstrates a situation that can activate this MDA.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="10308-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10308-131">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="10308-132">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="10308-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="10308-133">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="10308-133">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
