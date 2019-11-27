---
title: Synchronní a asynchronní operace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], synchronous operations
- service contracts [WCF], asynchronous operations
ms.assetid: db8a51cb-67e6-411b-9035-e5821ed350c9
ms.openlocfilehash: 39a7db3fb7dc3651f2cf6c850e7ebb5525e24963
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74281634"
---
# <a name="synchronous-and-asynchronous-operations"></a><span data-ttu-id="2d2f2-102">Synchronní a asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="2d2f2-102">Synchronous and Asynchronous Operations</span></span>
<span data-ttu-id="2d2f2-103">Toto téma popisuje implementaci a volání asynchronních operací služby.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-103">This topic discusses implementing and calling asynchronous service operations.</span></span>  
  
 <span data-ttu-id="2d2f2-104">Mnoho aplikací volá metody asynchronně, protože umožňuje aplikaci dál provádět užitečnou práci, i když je volání metody spuštěno.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-104">Many applications call methods asynchronously because it enables the application to continue doing useful work while the method call runs.</span></span> <span data-ttu-id="2d2f2-105">Služby Windows Communication Foundation (WCF) a klienti se můžou účastnit volání asynchronních operací na dvou různých úrovních aplikace, které poskytují aplikacím WCF ještě větší flexibilitu při maximalizaci propustnosti vyvážené vůči interaktivitě. .</span><span class="sxs-lookup"><span data-stu-id="2d2f2-105">Windows Communication Foundation (WCF) services and clients can participate in asynchronous operation calls at two distinct levels of the application, which provide WCF applications even more flexibility to maximize throughput balanced against interactivity.</span></span>  
  
## <a name="types-of-asynchronous-operations"></a><span data-ttu-id="2d2f2-106">Typy asynchronních operací</span><span class="sxs-lookup"><span data-stu-id="2d2f2-106">Types of Asynchronous Operations</span></span>  
 <span data-ttu-id="2d2f2-107">Všechny kontrakty služeb ve službě WCF bez ohledu na typy parametrů a návratové hodnoty, používají atributy WCF k určení konkrétního vzoru výměny zpráv mezi klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-107">All service contracts in WCF, no matter the parameters types and return values, use WCF attributes to specify a particular message exchange pattern between client and service.</span></span> <span data-ttu-id="2d2f2-108">Služba WCF automaticky směruje příchozí a odchozí zprávy na příslušnou operaci služby nebo běžící kód klienta.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-108">WCF automatically routes inbound and outbound messages to the appropriate service operation or running client code.</span></span>  
  
 <span data-ttu-id="2d2f2-109">Klient má pouze kontrakt služby, který určuje vzor výměny zpráv pro konkrétní operaci.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-109">The client possesses only the service contract, which specifies the message exchange pattern for a particular operation.</span></span> <span data-ttu-id="2d2f2-110">Klienti mohou nabídnout vývojářům libovolný model programování, který si zvolí, pokud je zaznamenán základní vzor výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-110">Clients can offer the developer any programming model they choose, so long as the underlying message exchange pattern is observed.</span></span> <span data-ttu-id="2d2f2-111">To je také možné, že mohou služby implementovat operace jakýmkoli způsobem, pokud je zaznamenán zadaný vzor zprávy.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-111">So, too, can services implement operations in any manner, so long as the specified message pattern is observed.</span></span>  
  
 <span data-ttu-id="2d2f2-112">Nezávislost kontraktu služby od implementace služby nebo klienta umožňuje následující formy asynchronního spuštění v aplikacích WCF:</span><span class="sxs-lookup"><span data-stu-id="2d2f2-112">The independence of the service contract from either the service or client implementation enables the following forms of asynchronous execution in WCF applications:</span></span>  
  
- <span data-ttu-id="2d2f2-113">Klienti mohou asynchronně vyvolat operace požadavku/odpovědi pomocí synchronní výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-113">Clients can invoke request/response operations asynchronously using a synchronous message exchange.</span></span>  
  
- <span data-ttu-id="2d2f2-114">Služby mohou implementovat operaci žádosti nebo odpovědi asynchronně pomocí synchronní výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-114">Services can implement a request/response operation asynchronously using a synchronous message exchange.</span></span>  
  
- <span data-ttu-id="2d2f2-115">Výměna zpráv může být jednosměrná, bez ohledu na implementaci klienta nebo služby.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-115">Message exchanges can be one-way, regardless of the implementation of the client or service.</span></span>  
  
### <a name="suggested-asynchronous-scenarios"></a><span data-ttu-id="2d2f2-116">Navrhované asynchronní scénáře</span><span class="sxs-lookup"><span data-stu-id="2d2f2-116">Suggested Asynchronous Scenarios</span></span>  
 <span data-ttu-id="2d2f2-117">Použijte asynchronní přístup v implementaci operace služby, pokud implementace služby operace znemožňuje blokující volání, jako je například zpracování vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-117">Use an asynchronous approach in a service operation implementation if the operation service implementation makes a blocking call, such as doing I/O work.</span></span> <span data-ttu-id="2d2f2-118">Pokud jste v implementaci asynchronní operace, zkuste volat asynchronní operace a metody, aby co nejvíce rozšířily cestu asynchronního volání.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-118">When you are in an asynchronous operation implementation, try to call asynchronous operations and methods to extend the asynchronous call path as far as possible.</span></span> <span data-ttu-id="2d2f2-119">Například volejte `BeginOperationTwo()` v rámci `BeginOperationOne()`.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-119">For example, call a `BeginOperationTwo()` from within `BeginOperationOne()`.</span></span>  
  
- <span data-ttu-id="2d2f2-120">Použijte asynchronní přístup v klientovi nebo volání aplikace v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="2d2f2-120">Use an asynchronous approach in a client or calling application in the following cases:</span></span>  
  
- <span data-ttu-id="2d2f2-121">Pokud vyvoláte operace z aplikace střední vrstvy.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-121">If you are invoking operations from a middle-tier application.</span></span> <span data-ttu-id="2d2f2-122">(Další informace o takových scénářích najdete v tématu [klientské aplikace střední vrstvy](./feature-details/middle-tier-client-applications.md).)</span><span class="sxs-lookup"><span data-stu-id="2d2f2-122">(For more information about such scenarios, see [Middle-Tier Client Applications](./feature-details/middle-tier-client-applications.md).)</span></span>  
  
- <span data-ttu-id="2d2f2-123">Při vyvolávání operací na stránce ASP.NET použijte asynchronní stránky.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-123">If you are invoking operations within an ASP.NET page, use asynchronous pages.</span></span>  
  
- <span data-ttu-id="2d2f2-124">Pokud vyvoláte operace z jakékoli aplikace s jedním vláknem, například model Windows Forms nebo Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="2d2f2-124">If you are invoking operations from any application that is single threaded, such as Windows Forms or Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="2d2f2-125">Při použití asynchronního volání modelu založeného na událostech se událost výsledek vyvolá ve vlákně uživatelského rozhraní, čímž se do aplikace přidá odezva bez nutnosti zpracovávat více vláken sami.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-125">When using the event-based asynchronous calling model, the result event is raised on the UI thread, adding responsiveness to the application without requiring you to handle multiple threads yourself.</span></span>  
  
- <span data-ttu-id="2d2f2-126">Obecně, pokud máte možnost volby mezi synchronním a asynchronním voláním, zvolte asynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-126">In general, if you have a choice between a synchronous and asynchronous call, choose the asynchronous call.</span></span>  
  
### <a name="implementing-an-asynchronous-service-operation"></a><span data-ttu-id="2d2f2-127">Implementace asynchronní operace služby</span><span class="sxs-lookup"><span data-stu-id="2d2f2-127">Implementing an Asynchronous Service Operation</span></span>  
 <span data-ttu-id="2d2f2-128">Asynchronní operace mohou být implementovány pomocí jedné ze tří následujících metod:</span><span class="sxs-lookup"><span data-stu-id="2d2f2-128">Asynchronous operations can be implemented by using one of the three following methods:</span></span>  
  
1. <span data-ttu-id="2d2f2-129">Asynchronní vzor založený na úlohách</span><span class="sxs-lookup"><span data-stu-id="2d2f2-129">The task-based asynchronous pattern</span></span>  
  
2. <span data-ttu-id="2d2f2-130">Asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="2d2f2-130">The event-based asynchronous pattern</span></span>  
  
3. <span data-ttu-id="2d2f2-131">Asynchronní vzor IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="2d2f2-131">The IAsyncResult asynchronous pattern</span></span>  
  
#### <a name="task-based-asynchronous-pattern"></a><span data-ttu-id="2d2f2-132">Asynchronní vzor založený na úlohách</span><span class="sxs-lookup"><span data-stu-id="2d2f2-132">Task-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="2d2f2-133">Asynchronní vzor založený na úlohách je preferovaný způsob implementace asynchronních operací, protože se jedná o nejjednodušší a nejvíce rovnou dopředně.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-133">The task-based asynchronous pattern is the preferred way to implement asynchronous operations because it is the easiest and most straight forward.</span></span> <span data-ttu-id="2d2f2-134">Chcete-li použít tuto metodu, jednoduše implementujte operaci služby a zadejte návratový typ úkolu\<T >, kde T je typ vrácený logickou operací.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-134">To use this method simply implement your service operation and specify a return type of Task\<T>, where T is the type returned by the logical operation.</span></span> <span data-ttu-id="2d2f2-135">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2d2f2-135">For example:</span></span>  
  
```csharp  
public class SampleService:ISampleService   
{   
   // ...  
   public async Task<string> SampleMethodTaskAsync(string msg)   
   {   
      return Task<string>.Factory.StartNew(() =>   
      {   
         return msg;   
      });   
   }  
   // ...  
}  
```  
  
 <span data-ttu-id="2d2f2-136">Operace SampleMethodTaskAsync vrací > řetězec\<úkolu, protože logická operace vrací řetězec.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-136">The SampleMethodTaskAsync operation returns Task\<string> because the logical operation returns a string.</span></span> <span data-ttu-id="2d2f2-137">Další informace o asynchronním vzoru založeném na úlohách naleznete v tématu [asynchronní vzor založený na úlohách](https://go.microsoft.com/fwlink/?LinkId=232504).</span><span class="sxs-lookup"><span data-stu-id="2d2f2-137">For more information about the task-based asynchronous pattern, see [The Task-Based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=232504).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="2d2f2-138">Při použití asynchronního vzoru založeného na úlohách může být událost T:System.AggregateException vyvolána, pokud dojde k výjimce při čekání na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-138">When using the task-based asynchronous pattern, a T:System.AggregateException may be thrown if an exception occurs while waiting on the completion of the operation.</span></span> <span data-ttu-id="2d2f2-139">Tato výjimka může nastat u klienta nebo služeb.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-139">This exception may occur on the client or services</span></span>  
  
#### <a name="event-based-asynchronous-pattern"></a><span data-ttu-id="2d2f2-140">Asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="2d2f2-140">Event-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="2d2f2-141">Služba, která podporuje asynchronní vzor založený na událostech, bude mít jednu nebo více operací s názvem MethodNameAsync.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-141">A service that supports the Event-based Asynchronous Pattern will have one or more operations named MethodNameAsync.</span></span> <span data-ttu-id="2d2f2-142">Tyto metody mohou zrcadlit synchronní verze, které provádějí stejnou operaci v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-142">These methods may mirror synchronous versions, which perform the same operation on the current thread.</span></span> <span data-ttu-id="2d2f2-143">Třída může mít také událost MethodNameCompleted a může mít metodu MethodNameAsyncCancel (nebo jednoduše CancelAsync).</span><span class="sxs-lookup"><span data-stu-id="2d2f2-143">The class may also have a MethodNameCompleted event and it may have a MethodNameAsyncCancel (or simply CancelAsync) method.</span></span> <span data-ttu-id="2d2f2-144">Klient, který chce zavolat operaci, definuje obslužnou rutinu události, která se má volat po dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-144">A client wishing to call the operation will define an event handler to be called when the operation completes,</span></span>  
  
 <span data-ttu-id="2d2f2-145">Následující fragment kódu ukazuje, jak deklarovat asynchronní operace pomocí asynchronního vzoru založeného na událostech.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-145">The following code snippet illustrates how to declare asynchronous operations using the event-based asynchronous pattern.</span></span>  
  
```csharp  
public class AsyncExample  
{  
    // Synchronous methods.  
    public int Method1(string param);  
    public void Method2(double param);  
  
    // Asynchronous methods.  
    public void Method1Async(string param);  
    public void Method1Async(string param, object userState);  
    public event Method1CompletedEventHandler Method1Completed;  
  
    public void Method2Async(double param);  
    public void Method2Async(double param, object userState);  
    public event Method2CompletedEventHandler Method2Completed;  
  
    public void CancelAsync(object userState);  
  
    public bool IsBusy { get; }  
  
    // Class implementation not shown.  
}  
```  
  
 <span data-ttu-id="2d2f2-146">Další informace o asynchronním vzoru založeném na událostech naleznete v tématu [asynchronní vzor založený na událostech](https://go.microsoft.com/fwlink/?LinkId=232515).</span><span class="sxs-lookup"><span data-stu-id="2d2f2-146">For more information about the Event-based Asynchronous Pattern, see [The Event-Based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=232515).</span></span>  
  
#### <a name="iasyncresult-asynchronous-pattern"></a><span data-ttu-id="2d2f2-147">Asynchronní vzor IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="2d2f2-147">IAsyncResult Asynchronous Pattern</span></span>  
 <span data-ttu-id="2d2f2-148">Operace služby může být implementována asynchronním způsobem pomocí .NET Framework asynchronního programovacího vzoru a označením `<Begin>` metody s vlastností <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> nastavenou na `true`.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-148">A service operation can be implemented in an asynchronous fashion using the .NET Framework asynchronous programming pattern and marking the `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true`.</span></span> <span data-ttu-id="2d2f2-149">V tomto případě je asynchronní operace vystavena v metadatech ve stejném tvaru jako synchronní operace: je vystavena jako jediná operace se zprávou požadavku a zprávou s korelační odpovědí.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-149">In this case, the asynchronous operation is exposed in metadata in the same form as a synchronous operation: It is exposed as a single operation with a request message and a correlated response message.</span></span> <span data-ttu-id="2d2f2-150">Modely programování klientů pak mají možnost zvolit.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-150">Client programming models then have a choice.</span></span> <span data-ttu-id="2d2f2-151">Mohou představovat tento model jako synchronní operaci nebo jako asynchronní, tak dlouho, jak je vyvolána služba Výměna zpráv odezvy požadavku.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-151">They can represent this pattern as a synchronous operation or as an asynchronous one, so long as when the service is invoked a request-response message exchange takes place.</span></span>  
  
 <span data-ttu-id="2d2f2-152">Obecně platí, že s asynchronní povahou systémů byste neměli mít závislost na vláknech.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-152">In general, with the asynchronous nature of the systems, you should not take a dependency on the threads.</span></span>  <span data-ttu-id="2d2f2-153">Nejspolehlivějším způsobem, jak předat data do různých fází zpracování odesílání operací, je použít rozšíření.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-153">The most reliable way of passing data to various stages of operation dispatch processing is to use extensions.</span></span>  
  
 <span data-ttu-id="2d2f2-154">Příklad naleznete v tématu [How to: implementace asynchronní operace služby](how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="2d2f2-154">For an example, see [How to: Implement an Asynchronous Service Operation](how-to-implement-an-asynchronous-service-operation.md).</span></span>  
  
 <span data-ttu-id="2d2f2-155">Definování operace kontraktu `X`, která se provádí asynchronně bez ohledu na to, jak se volá v klientské aplikaci:</span><span class="sxs-lookup"><span data-stu-id="2d2f2-155">To define a contract operation `X` that is executed asynchronously regardless of how it is called in the client application:</span></span>  
  
- <span data-ttu-id="2d2f2-156">Pomocí `BeginOperation` vzorů a `EndOperation`definujte dvě metody.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-156">Define two methods using the pattern `BeginOperation` and `EndOperation`.</span></span>  
  
- <span data-ttu-id="2d2f2-157">Metoda `BeginOperation` zahrnuje parametry `in` a `ref` pro operaci a vrací typ <xref:System.IAsyncResult>.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-157">The `BeginOperation` method includes `in` and `ref` parameters for the operation and returns an <xref:System.IAsyncResult> type.</span></span>  
  
- <span data-ttu-id="2d2f2-158">Metoda `EndOperation` obsahuje parametr <xref:System.IAsyncResult> a parametry `out` a `ref` a vrací návratový typ operací.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-158">The `EndOperation` method includes an <xref:System.IAsyncResult> parameter as well as the `out` and `ref` parameters and returns the operations return type.</span></span>  
  
 <span data-ttu-id="2d2f2-159">Podívejte se například na následující metodu.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-159">For example, see the following method.</span></span>  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 <span data-ttu-id="2d2f2-160">Chcete-li vytvořit asynchronní operaci, budou tyto dvě metody:</span><span class="sxs-lookup"><span data-stu-id="2d2f2-160">To create an asynchronous operation, the two methods would be:</span></span>  
  
```csharp  
[OperationContract(AsyncPattern=true)]
IAsyncResult BeginDoWork(string data,
                         ref string inout,
                         AsyncCallback callback,
                         object state);
int EndDoWork(ref string inout, out string outonly, IAsyncResult result);  
```  
  
```vb  
<OperationContract(AsyncPattern := True)>
Function BeginDoWork(ByVal data As String, _
                     ByRef inout As String, _
                     ByVal callback As AsyncCallback, _
                     ByVal state As Object) As IAsyncResult
Function EndDoWork(ByRef inout As String, ByRef outonly As String, ByVal result As IAsyncResult) As Integer  
```  
  
> [!NOTE]
> <span data-ttu-id="2d2f2-161">Atribut <xref:System.ServiceModel.OperationContractAttribute> je použit pouze pro metodu `BeginDoWork`.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-161">The <xref:System.ServiceModel.OperationContractAttribute> attribute is applied only to the `BeginDoWork` method.</span></span> <span data-ttu-id="2d2f2-162">Výsledný kontrakt má jednu operaci WSDL s názvem `DoWork`.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-162">The resulting contract has one WSDL operation named `DoWork`.</span></span>  
  
### <a name="client-side-asynchronous-invocations"></a><span data-ttu-id="2d2f2-163">Asynchronní volání na straně klienta</span><span class="sxs-lookup"><span data-stu-id="2d2f2-163">Client-Side Asynchronous Invocations</span></span>  
 <span data-ttu-id="2d2f2-164">Klientská aplikace WCF může použít kterýkoli ze tří modelů asynchronního volání popsaných výše.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-164">A WCF client application can use any of three asynchronous calling models described previously</span></span>  
  
 <span data-ttu-id="2d2f2-165">Při použití modelu založeného na úlohách jednoduše zavolejte operaci pomocí klíčového slova await, jak je znázorněno v následujícím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-165">When using the task-based model, simply call the operation using the await keyword as shown in the following code snippet.</span></span>  
  
```csharp  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 <span data-ttu-id="2d2f2-166">Použití asynchronního vzoru založeného na událostech vyžaduje pouze přidání obslužné rutiny události pro příjem oznámení o odpovědi – a výsledná událost je vyvolána automaticky ve vlákně uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-166">Using the event-based asynchronous pattern only requires adding an event handler to receive a notification of the response -- and the resulting event is raised on the user interface thread automatically.</span></span> <span data-ttu-id="2d2f2-167">Chcete-li použít tento přístup, zadejte obě možnosti příkazu **/Async** a **/tcv: Version35** pomocí nástroje pro dodávání [metadat ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-167">To use this approach, specify both the **/async** and **/tcv:Version35** command options with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 <span data-ttu-id="2d2f2-168">Po dokončení Svcutil. exe vygeneruje třídu klienta WCF s infrastrukturou událostí, která umožňuje volající aplikaci implementovat a přiřadit obslužnou rutinu události pro příjem odpovědi a provedení příslušné akce.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-168">When this is done, Svcutil.exe generates a WCF client class with the event infrastructure that enables the calling application to implement and assign an event handler to receive the response and take the appropriate action.</span></span> <span data-ttu-id="2d2f2-169">Úplný příklad naleznete v tématu [Postupy: asynchronní volání operací služby](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="2d2f2-169">For a complete example, see [How to: Call Service Operations Asynchronously](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span>  
  
 <span data-ttu-id="2d2f2-170">Asynchronní model založený na událostech je však k dispozici pouze v .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-170">The event-based asynchronous model, however, is only available in .NET Framework 3.5.</span></span> <span data-ttu-id="2d2f2-171">Kromě toho není podporován ani v .NET Framework 3,5, když je kanál klienta WCF vytvořen pomocí <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-171">In addition, it is not supported even in .NET Framework 3.5 when a WCF client channel is created by using a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2d2f2-172">S objekty kanálu klienta WCF je nutné použít <xref:System.IAsyncResult?displayProperty=nameWithType> objekty k asynchronnímu vyvolání vašich operací.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-172">With WCF client channel objects, you must use <xref:System.IAsyncResult?displayProperty=nameWithType> objects to invoke your operations asynchronously.</span></span> <span data-ttu-id="2d2f2-173">Chcete-li použít tento přístup, zadejte možnost příkazu **/Async** pomocí nástroje pro dodávání [metadat (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-173">To use this approach, specify the **/async** command option with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async   
```  
  
 <span data-ttu-id="2d2f2-174">Tím se vygeneruje kontrakt služby, ve kterém každá operace je modelována jako metoda `<Begin>` s vlastností <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> nastavenou na `true` a odpovídající `<End>` metoda.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-174">This generates a service contract in which each operation is modeled as a `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true` and a corresponding `<End>` method.</span></span> <span data-ttu-id="2d2f2-175">Úplný příklad použití <xref:System.ServiceModel.ChannelFactory%601>naleznete v tématu [How to: Asynchronous volání operací pomocí objektu pro vytváření kanálů](./feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="2d2f2-175">For a complete example using a <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](./feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
 <span data-ttu-id="2d2f2-176">V obou případech mohou aplikace vyvolat operaci asynchronně i v případě, že je služba implementována synchronně a stejným způsobem, jako aplikace může použít stejný vzor k asynchronnímu vyvolání místní synchronní metody.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-176">In either case, applications can invoke an operation asynchronously even if the service is implemented synchronously, in the same way that an application can use the same pattern to invoke asynchronously a local synchronous method.</span></span> <span data-ttu-id="2d2f2-177">Způsob implementace operace není pro klienta významné; po přijetí zprávy odpovědi se její obsah odešle do asynchronního <`End`> metody a klient tyto informace načte.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-177">How the operation is implemented is not significant to the client; when the response message arrives, its content is dispatched to the client's asynchronous <`End`> method and the client retrieves the information.</span></span>  
  
### <a name="one-way-message-exchange-patterns"></a><span data-ttu-id="2d2f2-178">Modely jednosměrového výměny zpráv</span><span class="sxs-lookup"><span data-stu-id="2d2f2-178">One-Way Message Exchange Patterns</span></span>  
 <span data-ttu-id="2d2f2-179">Můžete také vytvořit vzorec asynchronní výměny zpráv, ve kterém jednosměrné operace (operace, pro které <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> `true` nemají žádnou korelační odpověď), mohou být odesílány buď klientem nebo službou nezávisle na druhé straně.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-179">You can also create an asynchronous message exchange pattern in which one-way operations (operations for which the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> is `true` have no correlated response) can be sent in either direction by the client or service independently of the other side.</span></span> <span data-ttu-id="2d2f2-180">(Používá se jednosměrné zprávy pro výměnu zpráv.) V tomto případě kontrakt služby určuje jednosměrnou výměnu zpráv, kterou může kterákoli strana implementovat jako asynchronní volání nebo implementace nebo nemusí (případně ne).</span><span class="sxs-lookup"><span data-stu-id="2d2f2-180">(This uses the duplex message exchange pattern with one-way messages.) In this case, the service contract specifies a one-way message exchange that either side can implement as asynchronous calls or implementations, or not, as appropriate.</span></span> <span data-ttu-id="2d2f2-181">Obecně platí, že pokud je kontraktem výměna jednosměrných zpráv, implementace mohou být převážně asynchronní, protože jakmile se pošle zpráva, aplikace nečeká na odpověď a může pokračovat v práci.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-181">Generally, when the contract is an exchange of one-way messages, the implementations can largely be asynchronous because once a message is sent the application does not wait for a reply and can continue doing other work.</span></span>  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a><span data-ttu-id="2d2f2-182">Asynchronní klienti založené na událostech a kontrakty zpráv</span><span class="sxs-lookup"><span data-stu-id="2d2f2-182">Event-based Asynchronous Clients and Message Contracts</span></span>  
 <span data-ttu-id="2d2f2-183">Pokyny pro návrh stavu asynchronního modelu založeného na událostech, pokud je vrácena více než jedna hodnota, je vrácena jedna hodnota jako vlastnost `Result` a ostatní jsou vráceny jako vlastnosti objektu <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-183">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="2d2f2-184">Jedním z těchto výsledků je, že pokud klient Importuje metadata pomocí parametrů asynchronního příkazu založeného na událostech a operace vrátí více než jednu hodnotu, výchozí objekt <xref:System.EventArgs> vrátí jednu hodnotu jako vlastnost `Result` a zbytek je vlastnosti objektu <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-184">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="2d2f2-185">Pokud chcete objekt zprávy přijmout jako vlastnost `Result` a vracet hodnoty jako vlastnosti tohoto objektu, použijte možnost příkazového řádku **/MessageContract** .</span><span class="sxs-lookup"><span data-stu-id="2d2f2-185">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the **/messageContract** command option.</span></span> <span data-ttu-id="2d2f2-186">Tím se vygeneruje podpis, který vrátí zprávu odpovědi jako vlastnost `Result` objektu <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-186">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="2d2f2-187">Všechny interní návratové hodnoty jsou potom vlastnostmi objektu zprávy odpovědi.</span><span class="sxs-lookup"><span data-stu-id="2d2f2-187">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d2f2-188">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d2f2-188">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>
- <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
