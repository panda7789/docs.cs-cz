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
ms.openlocfilehash: 75a585efcdf316f407f3617fef8e1e279dcd922d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143210"
---
# <a name="synchronous-and-asynchronous-operations"></a><span data-ttu-id="5b0bd-102">Synchronní a asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="5b0bd-102">Synchronous and Asynchronous Operations</span></span>
<span data-ttu-id="5b0bd-103">Toto téma popisuje implementaci a volání operací asynchronní služby.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-103">This topic discusses implementing and calling asynchronous service operations.</span></span>  
  
 <span data-ttu-id="5b0bd-104">Mnoho aplikací volat metody asynchronně, protože umožňuje aplikaci pokračovat v provádění užitečné práce při spuštění volání metody.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-104">Many applications call methods asynchronously because it enables the application to continue doing useful work while the method call runs.</span></span> <span data-ttu-id="5b0bd-105">Služby a klienti WCF (Windows Communication Foundation) se mohou účastnit volání asynchronních operací na dvou různých úrovních aplikace, které poskytují aplikacím WCF ještě větší flexibilitu pro maximalizaci propustnosti vyváženou interaktivitou .</span><span class="sxs-lookup"><span data-stu-id="5b0bd-105">Windows Communication Foundation (WCF) services and clients can participate in asynchronous operation calls at two distinct levels of the application, which provide WCF applications even more flexibility to maximize throughput balanced against interactivity.</span></span>  
  
## <a name="types-of-asynchronous-operations"></a><span data-ttu-id="5b0bd-106">Typy asynchronních operací</span><span class="sxs-lookup"><span data-stu-id="5b0bd-106">Types of Asynchronous Operations</span></span>  
 <span data-ttu-id="5b0bd-107">Všechny smlouvy o poskytování služeb v WCF, bez ohledu na typy parametrů a vrácené hodnoty, použijte atributy WCF k určení konkrétního vzoru výměny zpráv mezi klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-107">All service contracts in WCF, no matter the parameters types and return values, use WCF attributes to specify a particular message exchange pattern between client and service.</span></span> <span data-ttu-id="5b0bd-108">WCF automaticky směruje příchozí a odchozí zprávy do příslušné operace služby nebo spuštěný kód klienta.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-108">WCF automatically routes inbound and outbound messages to the appropriate service operation or running client code.</span></span>  
  
 <span data-ttu-id="5b0bd-109">Klient vlastní pouze servisní smlouvu, která určuje vzor výměny zpráv pro určitou operaci.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-109">The client possesses only the service contract, which specifies the message exchange pattern for a particular operation.</span></span> <span data-ttu-id="5b0bd-110">Klienti mohou nabídnout vývojáři libovolný programovací model, který zvolí, tak dlouho, dokud je dodržen základní vzor výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-110">Clients can offer the developer any programming model they choose, so long as the underlying message exchange pattern is observed.</span></span> <span data-ttu-id="5b0bd-111">Stejně tak služby mohou provádět operace jakýmkoli způsobem, pokud je dodržen zadaný vzor zprávy.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-111">So, too, can services implement operations in any manner, so long as the specified message pattern is observed.</span></span>  
  
 <span data-ttu-id="5b0bd-112">Nezávislost smlouvy o poskytování služeb na implementaci služby nebo klienta umožňuje následující formy asynchronního provádění v aplikacích WCF:</span><span class="sxs-lookup"><span data-stu-id="5b0bd-112">The independence of the service contract from either the service or client implementation enables the following forms of asynchronous execution in WCF applications:</span></span>  
  
- <span data-ttu-id="5b0bd-113">Klienti mohou vyvolat operace požadavku a odpovědi asynchronně pomocí synchronní výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-113">Clients can invoke request/response operations asynchronously using a synchronous message exchange.</span></span>  
  
- <span data-ttu-id="5b0bd-114">Služby mohou implementovat operaci požadavku a odpovědi asynchronně pomocí synchronní výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-114">Services can implement a request/response operation asynchronously using a synchronous message exchange.</span></span>  
  
- <span data-ttu-id="5b0bd-115">Výměny zpráv může být jednosměrné, bez ohledu na implementaci klienta nebo služby.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-115">Message exchanges can be one-way, regardless of the implementation of the client or service.</span></span>  
  
### <a name="suggested-asynchronous-scenarios"></a><span data-ttu-id="5b0bd-116">Navrhované asynchronní scénáře</span><span class="sxs-lookup"><span data-stu-id="5b0bd-116">Suggested Asynchronous Scenarios</span></span>  
 <span data-ttu-id="5b0bd-117">Použijte asynchronní přístup v implementaci operace služby, pokud implementace služby operace provede blokování volání, jako je například provádění vstupně-va., jako je například provádění vstupně-va.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-117">Use an asynchronous approach in a service operation implementation if the operation service implementation makes a blocking call, such as doing I/O work.</span></span> <span data-ttu-id="5b0bd-118">Pokud jste v implementaci asynchronní operace, zkuste volat asynchronní operace a metody rozšířit cestu asynchronní volání co nejvíce.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-118">When you are in an asynchronous operation implementation, try to call asynchronous operations and methods to extend the asynchronous call path as far as possible.</span></span> <span data-ttu-id="5b0bd-119">Například volání `BeginOperationTwo()` a `BeginOperationOne()`zevnitř .</span><span class="sxs-lookup"><span data-stu-id="5b0bd-119">For example, call a `BeginOperationTwo()` from within `BeginOperationOne()`.</span></span>  
  
- <span data-ttu-id="5b0bd-120">Použijte asynchronní přístup v klientské nebo volající aplikaci v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="5b0bd-120">Use an asynchronous approach in a client or calling application in the following cases:</span></span>  
  
- <span data-ttu-id="5b0bd-121">Pokud se odvoláváte na operace z aplikace střední vrstvy.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-121">If you are invoking operations from a middle-tier application.</span></span> <span data-ttu-id="5b0bd-122">(Další informace o těchto scénářích naleznete v tématu [klientské aplikace střední vrstvy](./feature-details/middle-tier-client-applications.md).)</span><span class="sxs-lookup"><span data-stu-id="5b0bd-122">(For more information about such scenarios, see [Middle-Tier Client Applications](./feature-details/middle-tier-client-applications.md).)</span></span>  
  
- <span data-ttu-id="5b0bd-123">Pokud vyvoláte operace v rámci ASP.NET stránky, použijte asynchronní stránky.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-123">If you are invoking operations within an ASP.NET page, use asynchronous pages.</span></span>  
  
- <span data-ttu-id="5b0bd-124">Pokud vyvoláváte operace z libovolné aplikace, která je s jedním zřetězením, jako jsou například Windows Forms nebo Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="5b0bd-124">If you are invoking operations from any application that is single threaded, such as Windows Forms or Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="5b0bd-125">Při použití modelu asynchronnívolání založené na událostech je událost výsledku vyvolána ve vlákně uživatelského rozhraní a přidává odezvu do aplikace, aniž byste museli zpracovávat více vláken sami.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-125">When using the event-based asynchronous calling model, the result event is raised on the UI thread, adding responsiveness to the application without requiring you to handle multiple threads yourself.</span></span>  
  
- <span data-ttu-id="5b0bd-126">Obecně platí, že pokud máte na výběr mezi synchronní a asynchronní volání, zvolte asynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-126">In general, if you have a choice between a synchronous and asynchronous call, choose the asynchronous call.</span></span>  
  
### <a name="implementing-an-asynchronous-service-operation"></a><span data-ttu-id="5b0bd-127">Implementace operace asynchronní služby</span><span class="sxs-lookup"><span data-stu-id="5b0bd-127">Implementing an Asynchronous Service Operation</span></span>  
 <span data-ttu-id="5b0bd-128">Asynchronní operace lze implementovat pomocí jedné ze tří následujících metod:</span><span class="sxs-lookup"><span data-stu-id="5b0bd-128">Asynchronous operations can be implemented by using one of the three following methods:</span></span>  
  
1. <span data-ttu-id="5b0bd-129">Asynchronní vzor založený na úlohách</span><span class="sxs-lookup"><span data-stu-id="5b0bd-129">The task-based asynchronous pattern</span></span>  
  
2. <span data-ttu-id="5b0bd-130">Asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="5b0bd-130">The event-based asynchronous pattern</span></span>  
  
3. <span data-ttu-id="5b0bd-131">Asynchronní vzor IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="5b0bd-131">The IAsyncResult asynchronous pattern</span></span>  
  
#### <a name="task-based-asynchronous-pattern"></a><span data-ttu-id="5b0bd-132">Asynchronní vzor založený na úlohách</span><span class="sxs-lookup"><span data-stu-id="5b0bd-132">Task-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="5b0bd-133">Asynchronní vzor založený na úlohách je upřednostňovaným způsobem implementace asynchronních operací, protože je nejjednodušší a nejpřímější.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-133">The task-based asynchronous pattern is the preferred way to implement asynchronous operations because it is the easiest and most straight forward.</span></span> <span data-ttu-id="5b0bd-134">Chcete-li použít tuto metodu jednoduše implementovat\<operaci služby a zadejte návratový typ úkolu T>, kde T je typ vrácený logickou operací.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-134">To use this method simply implement your service operation and specify a return type of Task\<T>, where T is the type returned by the logical operation.</span></span> <span data-ttu-id="5b0bd-135">Například:</span><span class="sxs-lookup"><span data-stu-id="5b0bd-135">For example:</span></span>  
  
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
  
 <span data-ttu-id="5b0bd-136">Operace SampleMethodTaskAsync vrátí\<řetězec úlohy> protože logická operace vrátí řetězec.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-136">The SampleMethodTaskAsync operation returns Task\<string> because the logical operation returns a string.</span></span> <span data-ttu-id="5b0bd-137">Další informace o asynchronním vzoru založeném na úlohách naleznete [v tématu Asynchronní vzor založený na úlohách](https://go.microsoft.com/fwlink/?LinkId=232504).</span><span class="sxs-lookup"><span data-stu-id="5b0bd-137">For more information about the task-based asynchronous pattern, see [The Task-Based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=232504).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="5b0bd-138">Při použití asynchronní vzor založený na úlohách T:System.AggregateException může být vyvolána, pokud dojde k výjimce při čekání na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-138">When using the task-based asynchronous pattern, a T:System.AggregateException may be thrown if an exception occurs while waiting on the completion of the operation.</span></span> <span data-ttu-id="5b0bd-139">Tato výjimka může nastat u klienta nebo služeb.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-139">This exception may occur on the client or services</span></span>  
  
#### <a name="event-based-asynchronous-pattern"></a><span data-ttu-id="5b0bd-140">Asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="5b0bd-140">Event-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="5b0bd-141">Služba, která podporuje asynchronní vzorek založený na událostech, bude mít jednu nebo více operací s názvem MethodNameAsync.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-141">A service that supports the Event-based Asynchronous Pattern will have one or more operations named MethodNameAsync.</span></span> <span data-ttu-id="5b0bd-142">Tyto metody mohou zrcadlit synchronní verze, které provádějí stejnou operaci v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-142">These methods may mirror synchronous versions, which perform the same operation on the current thread.</span></span> <span data-ttu-id="5b0bd-143">Třída může mít také MetodNameCompleted událost a může mít MethodNameAsyncCancel (nebo jednoduše CancelAsync) metoda.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-143">The class may also have a MethodNameCompleted event and it may have a MethodNameAsyncCancel (or simply CancelAsync) method.</span></span> <span data-ttu-id="5b0bd-144">Klient, který chce volat operaci, definuje obslužnou rutinu události, která má být volána po dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-144">A client wishing to call the operation will define an event handler to be called when the operation completes,</span></span>  
  
 <span data-ttu-id="5b0bd-145">Následující fragment kódu ukazuje, jak deklarovat asynchronní operace pomocí asynchronního vzoru založeného na událostech.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-145">The following code snippet illustrates how to declare asynchronous operations using the event-based asynchronous pattern.</span></span>  
  
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
  
 <span data-ttu-id="5b0bd-146">Další informace o asynchronním vzoru založeném na událostech naleznete [v tématu Asynchronní vzor založený na událostech](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5b0bd-146">For more information about the Event-based Asynchronous Pattern, see [The Event-Based Asynchronous Pattern](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>  
  
#### <a name="iasyncresult-asynchronous-pattern"></a><span data-ttu-id="5b0bd-147">IAsyncResult asynchronní vzor</span><span class="sxs-lookup"><span data-stu-id="5b0bd-147">IAsyncResult Asynchronous Pattern</span></span>  
 <span data-ttu-id="5b0bd-148">Operaci služby lze implementovat asynchronním způsobem pomocí vzoru asynchronního programování `<Begin>` rozhraní .NET Framework a označením metody <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> vlastností nastavenou na `true`.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-148">A service operation can be implemented in an asynchronous fashion using the .NET Framework asynchronous programming pattern and marking the `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true`.</span></span> <span data-ttu-id="5b0bd-149">V tomto případě je asynchronní operace vystavena v metadatech ve stejném tvaru jako synchronní operace: Je vystavena jako jedna operace se zprávou požadavku a korelační zprávou odpovědi.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-149">In this case, the asynchronous operation is exposed in metadata in the same form as a synchronous operation: It is exposed as a single operation with a request message and a correlated response message.</span></span> <span data-ttu-id="5b0bd-150">Klientské programovací modely pak mají na výběr.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-150">Client programming models then have a choice.</span></span> <span data-ttu-id="5b0bd-151">Mohou představovat tento vzor jako synchronní operace nebo jako asynchronní, tak dlouho, dokud je služba vyvolána výměna zpráv požadavek odpověď probíhá.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-151">They can represent this pattern as a synchronous operation or as an asynchronous one, so long as when the service is invoked a request-response message exchange takes place.</span></span>  
  
 <span data-ttu-id="5b0bd-152">Obecně platí, že s asynchronní povahu systémů, neměli byste mít závislost na vláknech.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-152">In general, with the asynchronous nature of the systems, you should not take a dependency on the threads.</span></span>  <span data-ttu-id="5b0bd-153">Nejspolehlivějším způsobem předávání dat do různých fází zpracování expedice operace je použití rozšíření.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-153">The most reliable way of passing data to various stages of operation dispatch processing is to use extensions.</span></span>  
  
 <span data-ttu-id="5b0bd-154">Příklad najdete v [tématu How to: Implementace operace asynchronní služby](how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="5b0bd-154">For an example, see [How to: Implement an Asynchronous Service Operation](how-to-implement-an-asynchronous-service-operation.md).</span></span>  
  
 <span data-ttu-id="5b0bd-155">Chcete-li definovat `X` operaci smlouvy, která je provedena asynchronně bez ohledu na to, jak je volána v klientské aplikaci:</span><span class="sxs-lookup"><span data-stu-id="5b0bd-155">To define a contract operation `X` that is executed asynchronously regardless of how it is called in the client application:</span></span>  
  
- <span data-ttu-id="5b0bd-156">Definujte dvě metody `BeginOperation` `EndOperation`pomocí vzoru a .</span><span class="sxs-lookup"><span data-stu-id="5b0bd-156">Define two methods using the pattern `BeginOperation` and `EndOperation`.</span></span>  
  
- <span data-ttu-id="5b0bd-157">Metoda `BeginOperation` obsahuje `in` `ref` a parametry pro operaci <xref:System.IAsyncResult> a vrátí typ.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-157">The `BeginOperation` method includes `in` and `ref` parameters for the operation and returns an <xref:System.IAsyncResult> type.</span></span>  
  
- <span data-ttu-id="5b0bd-158">Metoda `EndOperation` obsahuje <xref:System.IAsyncResult> parametr, jakož `out` i `ref` parametry a vrátí návratový typ operací.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-158">The `EndOperation` method includes an <xref:System.IAsyncResult> parameter as well as the `out` and `ref` parameters and returns the operations return type.</span></span>  
  
 <span data-ttu-id="5b0bd-159">Podívejte se například na následující metodu.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-159">For example, see the following method.</span></span>  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 <span data-ttu-id="5b0bd-160">Chcete-li vytvořit asynchronní operaci, dvě metody by byly:</span><span class="sxs-lookup"><span data-stu-id="5b0bd-160">To create an asynchronous operation, the two methods would be:</span></span>  
  
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
> <span data-ttu-id="5b0bd-161">Atribut <xref:System.ServiceModel.OperationContractAttribute> je použit pouze `BeginDoWork` pro metodu.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-161">The <xref:System.ServiceModel.OperationContractAttribute> attribute is applied only to the `BeginDoWork` method.</span></span> <span data-ttu-id="5b0bd-162">Výsledná smlouva má jednu operaci `DoWork`WSDL s názvem .</span><span class="sxs-lookup"><span data-stu-id="5b0bd-162">The resulting contract has one WSDL operation named `DoWork`.</span></span>  
  
### <a name="client-side-asynchronous-invocations"></a><span data-ttu-id="5b0bd-163">Asynchronní vyvolání na straně klienta</span><span class="sxs-lookup"><span data-stu-id="5b0bd-163">Client-Side Asynchronous Invocations</span></span>  
 <span data-ttu-id="5b0bd-164">Klientská aplikace WCF může používat libovolný ze tří asynchronních volajících modelů popsaných dříve</span><span class="sxs-lookup"><span data-stu-id="5b0bd-164">A WCF client application can use any of three asynchronous calling models described previously</span></span>  
  
 <span data-ttu-id="5b0bd-165">Při použití modelu založeného na úlohách jednoduše zavolejte operaci pomocí klíčového slova await, jak je znázorněno v následujícím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-165">When using the task-based model, simply call the operation using the await keyword as shown in the following code snippet.</span></span>  
  
```csharp  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 <span data-ttu-id="5b0bd-166">Použití asynchronního vzoru založeného na událostech vyžaduje pouze přidání obslužné rutiny události pro příjem oznámení o odpovědi a výsledná událost je vyvolána ve vlákně uživatelského rozhraní automaticky.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-166">Using the event-based asynchronous pattern only requires adding an event handler to receive a notification of the response -- and the resulting event is raised on the user interface thread automatically.</span></span> <span data-ttu-id="5b0bd-167">Chcete-li použít tento přístup, zadejte možnosti příkazu **/async** a **/tcv:Version35** pomocí [nástroje ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-167">To use this approach, specify both the **/async** and **/tcv:Version35** command options with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 <span data-ttu-id="5b0bd-168">Když toto provedete, Svcutil.exe generuje WCF třídy klienta s infrastrukturou událostí, která umožňuje volající aplikace implementovat a přiřadit obslužnou rutinu události pro příjem odpovědi a přijmout příslušnou akci.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-168">When this is done, Svcutil.exe generates a WCF client class with the event infrastructure that enables the calling application to implement and assign an event handler to receive the response and take the appropriate action.</span></span> <span data-ttu-id="5b0bd-169">Úplný příklad najdete v [tématu Postup: Volání operací služby asynchronně](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="5b0bd-169">For a complete example, see [How to: Call Service Operations Asynchronously](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span>  
  
 <span data-ttu-id="5b0bd-170">Asynchronní model založený na událostech je však k dispozici pouze v rozhraní .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-170">The event-based asynchronous model, however, is only available in .NET Framework 3.5.</span></span> <span data-ttu-id="5b0bd-171">Kromě toho není podporována ani v rozhraní .NET Framework 3.5 při <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>vytvoření kanálu klienta WCF pomocí .</span><span class="sxs-lookup"><span data-stu-id="5b0bd-171">In addition, it is not supported even in .NET Framework 3.5 when a WCF client channel is created by using a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5b0bd-172">S wcf objekty kanálu <xref:System.IAsyncResult?displayProperty=nameWithType> klienta, musíte použít objekty vyvolat operace asynchronně.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-172">With WCF client channel objects, you must use <xref:System.IAsyncResult?displayProperty=nameWithType> objects to invoke your operations asynchronously.</span></span> <span data-ttu-id="5b0bd-173">Chcete-li použít tento přístup, zadejte **/async** příkaz možnost s [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-173">To use this approach, specify the **/async** command option with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async
```  
  
 <span data-ttu-id="5b0bd-174">Tím se vygeneruje servisní smlouva, ve `<Begin>` které je <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> každá `true` operace modelována jako metoda s vlastností nastavenou na a odpovídající `<End>` metodou.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-174">This generates a service contract in which each operation is modeled as a `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true` and a corresponding `<End>` method.</span></span> <span data-ttu-id="5b0bd-175">Úplný příklad pomocí <xref:System.ServiceModel.ChannelFactory%601>aplikace naleznete v tématu [How to: Call Operations Asynchronně Using a Channel Factory](./feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="5b0bd-175">For a complete example using a <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](./feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
 <span data-ttu-id="5b0bd-176">V obou případech aplikace můžete vyvolat operaci asynchronně i v případě, že služba je implementována synchronně, stejným způsobem, že aplikace můžete použít stejný vzor vyvolat asynchronně místní synchronní metody.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-176">In either case, applications can invoke an operation asynchronously even if the service is implemented synchronously, in the same way that an application can use the same pattern to invoke asynchronously a local synchronous method.</span></span> <span data-ttu-id="5b0bd-177">Jak je operace implementována, není pro klienta významná. když přijde zpráva odpovědi, jeho obsah je odeslán asynchronní `End` <> metody klienta a klient načte informace.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-177">How the operation is implemented is not significant to the client; when the response message arrives, its content is dispatched to the client's asynchronous <`End`> method and the client retrieves the information.</span></span>  
  
### <a name="one-way-message-exchange-patterns"></a><span data-ttu-id="5b0bd-178">Vzorové vzory výměny jednosměrných zpráv</span><span class="sxs-lookup"><span data-stu-id="5b0bd-178">One-Way Message Exchange Patterns</span></span>  
 <span data-ttu-id="5b0bd-179">Můžete také vytvořit vzor asynchronní výměny zpráv, ve kterém jednosměrné operace (operace, pro které <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> nemá `true` žádnou korelační odpověď) mohou být odeslány v obou směrech klientem nebo službou nezávisle na druhé straně.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-179">You can also create an asynchronous message exchange pattern in which one-way operations (operations for which the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> is `true` have no correlated response) can be sent in either direction by the client or service independently of the other side.</span></span> <span data-ttu-id="5b0bd-180">(Používá duplexní vzor výměny zpráv s jednosměrné zprávy.) V tomto případě smlouva o poskytování služeb určuje jednosměrnou výměnu zpráv, kterou může kterákoli strana implementovat jako asynchronní volání nebo implementace, nebo podle potřeby ne.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-180">(This uses the duplex message exchange pattern with one-way messages.) In this case, the service contract specifies a one-way message exchange that either side can implement as asynchronous calls or implementations, or not, as appropriate.</span></span> <span data-ttu-id="5b0bd-181">Obecně platí, že pokud je smlouva výměnou jednosměrných zpráv, implementace mohou být do značné míry asynchronní, protože po odeslání zprávy aplikace nečeká na odpověď a může pokračovat v jiné práci.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-181">Generally, when the contract is an exchange of one-way messages, the implementations can largely be asynchronous because once a message is sent the application does not wait for a reply and can continue doing other work.</span></span>  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a><span data-ttu-id="5b0bd-182">Asynchronní klienti a smlouvy se zprávami založené na událostech</span><span class="sxs-lookup"><span data-stu-id="5b0bd-182">Event-based Asynchronous Clients and Message Contracts</span></span>  
 <span data-ttu-id="5b0bd-183">Pokyny pro návrh pro asynchronní model založený na událostech uvádějí, že pokud je `Result` vrácena více než jedna <xref:System.EventArgs> hodnota, je vrácena jedna hodnota jako vlastnost a ostatní jsou vráceny jako vlastnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-183">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="5b0bd-184">Jedním z výsledků je, že pokud klient importuje metadata pomocí možností asynchronního příkazu založené <xref:System.EventArgs> na událostech `Result` a operace vrátí více <xref:System.EventArgs> než jednu hodnotu, výchozí objekt vrátí jednu hodnotu jako vlastnost a zbytek jsou vlastnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-184">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="5b0bd-185">Pokud chcete přijmout objekt zprávy `Result` jako vlastnost a mít vrácené hodnoty jako vlastnosti na tento objekt, použijte parametr příkazu **/messageContract.**</span><span class="sxs-lookup"><span data-stu-id="5b0bd-185">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the **/messageContract** command option.</span></span> <span data-ttu-id="5b0bd-186">Tím se vygeneruje podpis, který `Result` vrátí <xref:System.EventArgs> zprávu odpovědi jako vlastnost na objektu.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-186">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="5b0bd-187">Všechny vnitřní vrácené hodnoty jsou pak vlastnosti objektu zprávy odpovědi.</span><span class="sxs-lookup"><span data-stu-id="5b0bd-187">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b0bd-188">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b0bd-188">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>
- <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
