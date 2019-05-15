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
ms.openlocfilehash: c2e6a955a151e0e11bcf189085dc24e7815fb747
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582741"
---
# <a name="synchronous-and-asynchronous-operations"></a><span data-ttu-id="1e44e-102">Synchronní a asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="1e44e-102">Synchronous and Asynchronous Operations</span></span>
<span data-ttu-id="1e44e-103">Toto téma popisuje implementace a volání operace asynchronní služby.</span><span class="sxs-lookup"><span data-stu-id="1e44e-103">This topic discusses implementing and calling asynchronous service operations.</span></span>  
  
 <span data-ttu-id="1e44e-104">Mnoho aplikací volat metody asynchronně, protože umožní aplikaci pokračovat v provádění užitečné práce při volání metody, které běží.</span><span class="sxs-lookup"><span data-stu-id="1e44e-104">Many applications call methods asynchronously because it enables the application to continue doing useful work while the method call runs.</span></span> <span data-ttu-id="1e44e-105">Služby Windows Communication Foundation (WCF) a klienti mohou účastnit volání asynchronní operaci na dvě různé úrovně aplikace, které poskytují ještě větší flexibilita díky maximalizuje propustnost porovnán s interaktivitu aplikací služby WCF .</span><span class="sxs-lookup"><span data-stu-id="1e44e-105">Windows Communication Foundation (WCF) services and clients can participate in asynchronous operation calls at two distinct levels of the application, which provide WCF applications even more flexibility to maximize throughput balanced against interactivity.</span></span>  
  
## <a name="types-of-asynchronous-operations"></a><span data-ttu-id="1e44e-106">Typy asynchronních operací</span><span class="sxs-lookup"><span data-stu-id="1e44e-106">Types of Asynchronous Operations</span></span>  
 <span data-ttu-id="1e44e-107">Všechny služby smluv ve službě WCF, bez ohledu na to typů parametrů a návratové hodnoty, použijte k určení vzoru výměny konkrétní zpráv mezi klientem a službou WCF atributy.</span><span class="sxs-lookup"><span data-stu-id="1e44e-107">All service contracts in WCF, no matter the parameters types and return values, use WCF attributes to specify a particular message exchange pattern between client and service.</span></span> <span data-ttu-id="1e44e-108">WCF automaticky směruje příchozí a odchozí zprávy do příslušné službě operaci nebo se spuštěním kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="1e44e-108">WCF automatically routes inbound and outbound messages to the appropriate service operation or running client code.</span></span>  
  
 <span data-ttu-id="1e44e-109">Klient má pouze kontraktu služby, který určuje vzorce výměny zpráv pro určitou operaci.</span><span class="sxs-lookup"><span data-stu-id="1e44e-109">The client possesses only the service contract, which specifies the message exchange pattern for a particular operation.</span></span> <span data-ttu-id="1e44e-110">Klienti nabízí vývojářům libovolný programovací model, která si vyberou, tak dlouho, dokud se vyskytuje základní vzorce výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="1e44e-110">Clients can offer the developer any programming model they choose, so long as the underlying message exchange pattern is observed.</span></span> <span data-ttu-id="1e44e-111">Tedy příliš, můžete služby implementovat operace jakýmkoli způsobem tak dlouho, dokud se vyskytuje vzor určenou zprávu.</span><span class="sxs-lookup"><span data-stu-id="1e44e-111">So, too, can services implement operations in any manner, so long as the specified message pattern is observed.</span></span>  
  
 <span data-ttu-id="1e44e-112">Nezávislost kontrakt služby od implementace služby nebo klienta umožňuje následující formy asynchronní provádění ve službě WCF aplikací:</span><span class="sxs-lookup"><span data-stu-id="1e44e-112">The independence of the service contract from either the service or client implementation enables the following forms of asynchronous execution in WCF applications:</span></span>  
  
- <span data-ttu-id="1e44e-113">Klienty můžete vyvolat operace požadavku/odpovědi asynchronně pomocí synchronní zprávy exchange.</span><span class="sxs-lookup"><span data-stu-id="1e44e-113">Clients can invoke request/response operations asynchronously using a synchronous message exchange.</span></span>  
  
- <span data-ttu-id="1e44e-114">Služby můžete implementovat operaci požadavku nebo odpovědi asynchronně pomocí synchronní zprávy exchange.</span><span class="sxs-lookup"><span data-stu-id="1e44e-114">Services can implement a request/response operation asynchronously using a synchronous message exchange.</span></span>  
  
- <span data-ttu-id="1e44e-115">Výměny zpráv může být jednosměrné, bez ohledu na implementaci klienta nebo služby.</span><span class="sxs-lookup"><span data-stu-id="1e44e-115">Message exchanges can be one-way, regardless of the implementation of the client or service.</span></span>  
  
### <a name="suggested-asynchronous-scenarios"></a><span data-ttu-id="1e44e-116">Navrhované asynchronní scénáře</span><span class="sxs-lookup"><span data-stu-id="1e44e-116">Suggested Asynchronous Scenarios</span></span>  
 <span data-ttu-id="1e44e-117">Pokud implementace služby operace provede blokovacího hovoru, jako je vytváření pracovních I/O, použijte asynchronní přístup při provádění operace služby.</span><span class="sxs-lookup"><span data-stu-id="1e44e-117">Use an asynchronous approach in a service operation implementation if the operation service implementation makes a blocking call, such as doing I/O work.</span></span> <span data-ttu-id="1e44e-118">Když jste v implementaci asynchronní operace, zkuste pro volání asynchronní operace a metody rozšíření cesty asynchronní volání, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="1e44e-118">When you are in an asynchronous operation implementation, try to call asynchronous operations and methods to extend the asynchronous call path as far as possible.</span></span> <span data-ttu-id="1e44e-119">Například volání `BeginOperationTwo()` zevnitř `BeginOperationOne()`.</span><span class="sxs-lookup"><span data-stu-id="1e44e-119">For example, call a `BeginOperationTwo()` from within `BeginOperationOne()`.</span></span>  
  
- <span data-ttu-id="1e44e-120">Použijte asynchronní přístup v klientovi nebo volající aplikace v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="1e44e-120">Use an asynchronous approach in a client or calling application in the following cases:</span></span>  
  
- <span data-ttu-id="1e44e-121">Pokud jsou volání operace z aplikace střední vrstvy.</span><span class="sxs-lookup"><span data-stu-id="1e44e-121">If you are invoking operations from a middle-tier application.</span></span> <span data-ttu-id="1e44e-122">(Další informace o těchto scénářích najdete v tématu [klientské aplikace střední vrstvy](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).)</span><span class="sxs-lookup"><span data-stu-id="1e44e-122">(For more information about such scenarios, see [Middle-Tier Client Applications](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).)</span></span>  
  
- <span data-ttu-id="1e44e-123">Pokud vyvoláváte operace v rámci stránky ASP.NET, použijte asynchronní stránky.</span><span class="sxs-lookup"><span data-stu-id="1e44e-123">If you are invoking operations within an ASP.NET page, use asynchronous pages.</span></span>  
  
- <span data-ttu-id="1e44e-124">Pokud jsou volání operace z jakékoliv aplikace, která je jedinou vláken, jako jsou formuláře Windows nebo Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="1e44e-124">If you are invoking operations from any application that is single threaded, such as Windows Forms or Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="1e44e-125">Při použití založený na událostech asynchronní volání modelu, výsledek událost je aktivována na vlákně uživatelského rozhraní, přidání rychlost odezvy do aplikace, aniž by bylo potřeba zpracovávat více vláken, sami.</span><span class="sxs-lookup"><span data-stu-id="1e44e-125">When using the event-based asynchronous calling model, the result event is raised on the UI thread, adding responsiveness to the application without requiring you to handle multiple threads yourself.</span></span>  
  
- <span data-ttu-id="1e44e-126">Obecně platí Pokud máte možnost volby mezi synchronní a asynchronní volání, zvolte asynchronního volání.</span><span class="sxs-lookup"><span data-stu-id="1e44e-126">In general, if you have a choice between a synchronous and asynchronous call, choose the asynchronous call.</span></span>  
  
### <a name="implementing-an-asynchronous-service-operation"></a><span data-ttu-id="1e44e-127">Implementace operace asynchronní služby</span><span class="sxs-lookup"><span data-stu-id="1e44e-127">Implementing an Asynchronous Service Operation</span></span>  
 <span data-ttu-id="1e44e-128">Asynchronní operace lze provést pomocí jedné z těchto tří metod:</span><span class="sxs-lookup"><span data-stu-id="1e44e-128">Asynchronous operations can be implemented by using one of the three following methods:</span></span>  
  
1. <span data-ttu-id="1e44e-129">Asynchronní vzor založený na úlohách</span><span class="sxs-lookup"><span data-stu-id="1e44e-129">The task-based asynchronous pattern</span></span>  
  
2. <span data-ttu-id="1e44e-130">Asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="1e44e-130">The event-based asynchronous pattern</span></span>  
  
3. <span data-ttu-id="1e44e-131">Asynchronní vzor IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="1e44e-131">The IAsyncResult asynchronous pattern</span></span>  
  
#### <a name="task-based-asynchronous-pattern"></a><span data-ttu-id="1e44e-132">Asynchronní vzor založený na úlohách</span><span class="sxs-lookup"><span data-stu-id="1e44e-132">Task-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="1e44e-133">Asynchronní vzor založený na úlohách je preferovaný způsob, jak implementovat asynchronní operace, protože je nejjednodušší a většina přímočaré.</span><span class="sxs-lookup"><span data-stu-id="1e44e-133">The task-based asynchronous pattern is the preferred way to implement asynchronous operations because it is the easiest and most straight forward.</span></span> <span data-ttu-id="1e44e-134">Chcete-li tuto metodu použijte, jednoduše implementovat vaše operace služby a určit návratový typ úlohy\<T >, kde T je typ vrácený logické operace.</span><span class="sxs-lookup"><span data-stu-id="1e44e-134">To use this method simply implement your service operation and specify a return type of Task\<T>, where T is the type returned by the logical operation.</span></span> <span data-ttu-id="1e44e-135">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1e44e-135">For example:</span></span>  
  
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
  
 <span data-ttu-id="1e44e-136">Operace SampleMethodTaskAsync vrátí úkol\<řetězec > protože logické operace vrátí hodnotu typu string.</span><span class="sxs-lookup"><span data-stu-id="1e44e-136">The SampleMethodTaskAsync operation returns Task\<string> because the logical operation returns a string.</span></span> <span data-ttu-id="1e44e-137">Další informace o asynchronní vzor založený na úlohách najdete v tématu [asynchronní vzor The Task-Based](https://go.microsoft.com/fwlink/?LinkId=232504).</span><span class="sxs-lookup"><span data-stu-id="1e44e-137">For more information about the task-based asynchronous pattern, see [The Task-Based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=232504).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="1e44e-138">Při použití asynchronního vzoru založeného na úlohách, T:System.AggregateException může být vyvolána, pokud dojde k výjimce při čekání na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="1e44e-138">When using the task-based asynchronous pattern, a T:System.AggregateException may be thrown if an exception occurs while waiting on the completion of the operation.</span></span> <span data-ttu-id="1e44e-139">Tato výjimka může dojít u klienta nebo služby</span><span class="sxs-lookup"><span data-stu-id="1e44e-139">This exception may occur on the client or services</span></span>  
  
#### <a name="event-based-asynchronous-pattern"></a><span data-ttu-id="1e44e-140">Asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="1e44e-140">Event-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="1e44e-141">Služba, která podporuje asynchronní vzor založený na událostech bude mít jednu nebo více operací s názvem MethodNameAsync.</span><span class="sxs-lookup"><span data-stu-id="1e44e-141">A service that supports the Event-based Asynchronous Pattern will have one or more operations named MethodNameAsync.</span></span> <span data-ttu-id="1e44e-142">Tyto metody mohou zrcadlí synchronní verze, které provádět stejnou operaci i u aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="1e44e-142">These methods may mirror synchronous versions, which perform the same operation on the current thread.</span></span> <span data-ttu-id="1e44e-143">Třídy mohou mít i MethodNameCompleted událostí a může mít MethodNameAsyncCancel (nebo jednoduše CancelAsync) metody.</span><span class="sxs-lookup"><span data-stu-id="1e44e-143">The class may also have a MethodNameCompleted event and it may have a MethodNameAsyncCancel (or simply CancelAsync) method.</span></span> <span data-ttu-id="1e44e-144">Klient chtějí volat operaci budou definovat obslužnou rutinu události, která se má volat po dokončení operace</span><span class="sxs-lookup"><span data-stu-id="1e44e-144">A client wishing to call the operation will define an event handler to be called when the operation completes,</span></span>  
  
 <span data-ttu-id="1e44e-145">Následující fragment kódu ukazuje, jak deklarovat asynchronních operací s použitím asynchronního vzoru založeného na událostech.</span><span class="sxs-lookup"><span data-stu-id="1e44e-145">The following code snippet illustrates how to declare asynchronous operations using the event-based asynchronous pattern.</span></span>  
  
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
  
 <span data-ttu-id="1e44e-146">Další informace o asynchronní vzor založený na událostech najdete v tématu [asynchronní vzor The Event-Based](https://go.microsoft.com/fwlink/?LinkId=232515).</span><span class="sxs-lookup"><span data-stu-id="1e44e-146">For more information about the Event-based Asynchronous Pattern, see [The Event-Based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=232515).</span></span>  
  
#### <a name="iasyncresult-asynchronous-pattern"></a><span data-ttu-id="1e44e-147">Asynchronní vzor IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="1e44e-147">IAsyncResult Asynchronous Pattern</span></span>  
 <span data-ttu-id="1e44e-148">Operace služby je možné implementovat asynchronním způsobem pomocí rozhraní .NET Framework asynchronní programovací model a označení `<Begin>` metodou <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> vlastnost nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="1e44e-148">A service operation can be implemented in an asynchronous fashion using the .NET Framework asynchronous programming pattern and marking the `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true`.</span></span> <span data-ttu-id="1e44e-149">Asynchronní operace v tomto případě je přístupný v metadatech ve stejné podobě jako synchronní operace: Je vystavena jako jednu operaci s zprávu požadavku a korelační odpověď.</span><span class="sxs-lookup"><span data-stu-id="1e44e-149">In this case, the asynchronous operation is exposed in metadata in the same form as a synchronous operation: It is exposed as a single operation with a request message and a correlated response message.</span></span> <span data-ttu-id="1e44e-150">Programovací modely Klient pak mít možnost volby.</span><span class="sxs-lookup"><span data-stu-id="1e44e-150">Client programming models then have a choice.</span></span> <span data-ttu-id="1e44e-151">Tento model může představovat jako synchronní operace nebo některý asynchronní tak dlouho, dokud při vyvolání služby probíhá výměna zpráv žádost odpověď.</span><span class="sxs-lookup"><span data-stu-id="1e44e-151">They can represent this pattern as a synchronous operation or as an asynchronous one, so long as when the service is invoked a request-response message exchange takes place.</span></span>  
  
 <span data-ttu-id="1e44e-152">Obecně platí s asynchronní povaze v systémech, neměla by mít závislost na vlákna.</span><span class="sxs-lookup"><span data-stu-id="1e44e-152">In general, with the asynchronous nature of the systems, you should not take a dependency on the threads.</span></span>  <span data-ttu-id="1e44e-153">Nejspolehlivější způsob předání dat, jak různé fáze zpracování operace odeslání je použít rozšíření.</span><span class="sxs-lookup"><span data-stu-id="1e44e-153">The most reliable way of passing data to various stages of operation dispatch processing is to use extensions.</span></span>  
  
 <span data-ttu-id="1e44e-154">Příklad najdete v tématu [jak: Implementace operace asynchronní služby](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="1e44e-154">For an example, see [How to: Implement an Asynchronous Service Operation](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span>  
  
 <span data-ttu-id="1e44e-155">K definování operace kontraktu `X` , který se provedl asynchronně bez ohledu na to, jak je volána v klientské aplikaci:</span><span class="sxs-lookup"><span data-stu-id="1e44e-155">To define a contract operation `X` that is executed asynchronously regardless of how it is called in the client application:</span></span>  
  
- <span data-ttu-id="1e44e-156">Definovat dvě metody, pomocí vzoru `BeginOperation` a `EndOperation`.</span><span class="sxs-lookup"><span data-stu-id="1e44e-156">Define two methods using the pattern `BeginOperation` and `EndOperation`.</span></span>  
  
- <span data-ttu-id="1e44e-157">`BeginOperation` Metoda obsahuje `in` a `ref` parametry operace a vrátí <xref:System.IAsyncResult> typu.</span><span class="sxs-lookup"><span data-stu-id="1e44e-157">The `BeginOperation` method includes `in` and `ref` parameters for the operation and returns an <xref:System.IAsyncResult> type.</span></span>  
  
- <span data-ttu-id="1e44e-158">`EndOperation` Obsahuje metodu <xref:System.IAsyncResult> parametr i na `out` a `ref` parametry a vrací operace návratový typ.</span><span class="sxs-lookup"><span data-stu-id="1e44e-158">The `EndOperation` method includes an <xref:System.IAsyncResult> parameter as well as the `out` and `ref` parameters and returns the operations return type.</span></span>  
  
 <span data-ttu-id="1e44e-159">Podívejte se například následující metodu.</span><span class="sxs-lookup"><span data-stu-id="1e44e-159">For example, see the following method.</span></span>  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 <span data-ttu-id="1e44e-160">K vytvoření asynchronní operace, by tyto dvě metody:</span><span class="sxs-lookup"><span data-stu-id="1e44e-160">To create an asynchronous operation, the two methods would be:</span></span>  
  
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
>  <span data-ttu-id="1e44e-161"><xref:System.ServiceModel.OperationContractAttribute> Atributu se použije pouze `BeginDoWork` metody.</span><span class="sxs-lookup"><span data-stu-id="1e44e-161">The <xref:System.ServiceModel.OperationContractAttribute> attribute is applied only to the `BeginDoWork` method.</span></span> <span data-ttu-id="1e44e-162">Výsledný smlouva obsahuje WSDL operací s názvem `DoWork`.</span><span class="sxs-lookup"><span data-stu-id="1e44e-162">The resulting contract has one WSDL operation named `DoWork`.</span></span>  
  
### <a name="client-side-asynchronous-invocations"></a><span data-ttu-id="1e44e-163">Asynchronní volání na straně klienta</span><span class="sxs-lookup"><span data-stu-id="1e44e-163">Client-Side Asynchronous Invocations</span></span>  
 <span data-ttu-id="1e44e-164">WCF klientské aplikace můžou používat kterýkoli z tři asynchronní volání modely je popsáno výše</span><span class="sxs-lookup"><span data-stu-id="1e44e-164">A WCF client application can use any of three asynchronous calling models described previously</span></span>  
  
 <span data-ttu-id="1e44e-165">Při použití modelu založeného na úlohách, jednoduše zavolejte operaci using – klíčové slovo await, jak je znázorněno v následujícím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="1e44e-165">When using the task-based model, simply call the operation using the await keyword as shown in the following code snippet.</span></span>  
  
```  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 <span data-ttu-id="1e44e-166">Použití asynchronního vzoru založeného na událostech pouze vyžaduje přidání, která je vyvolána obslužná rutina události upozornění na odpověď – a výsledné události na vlákně uživatelského rozhraní automaticky.</span><span class="sxs-lookup"><span data-stu-id="1e44e-166">Using the event-based asynchronous pattern only requires adding an event handler to receive a notification of the response -- and the resulting event is raised on the user interface thread automatically.</span></span> <span data-ttu-id="1e44e-167">Chcete-li tuto metodu použijte, zadejte oba **/async** a **/tcv:Version35** možnosti pomocí příkazu [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), jako v následující Příklad.</span><span class="sxs-lookup"><span data-stu-id="1e44e-167">To use this approach, specify both the **/async** and **/tcv:Version35** command options with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 <span data-ttu-id="1e44e-168">Když to uděláte, Svcutil.exe vygeneruje třídy klienta WCF s vaší stávající infrastrukturou událost, která umožňuje volající aplikace k implementaci a přiřadit obslužnou rutinu události pro příjem odpovědi a proveďte příslušnou akci.</span><span class="sxs-lookup"><span data-stu-id="1e44e-168">When this is done, Svcutil.exe generates a WCF client class with the event infrastructure that enables the calling application to implement and assign an event handler to receive the response and take the appropriate action.</span></span> <span data-ttu-id="1e44e-169">Kompletní příklad naleznete v tématu [jak: Asynchronní volání operací služby](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="1e44e-169">For a complete example, see [How to: Call Service Operations Asynchronously](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span>  
  
 <span data-ttu-id="1e44e-170">Asynchronní model založený na událostech, ale je k dispozici pouze v [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1e44e-170">The event-based asynchronous model, however, is only available in [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)].</span></span> <span data-ttu-id="1e44e-171">Kromě toho se nepodporuje i při [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] při vytvoření kanálu klienta WCF pomocí <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1e44e-171">In addition, it is not supported even in [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] when a WCF client channel is created by using a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1e44e-172">S objekty kanálu klienta WCF, je nutné použít <xref:System.IAsyncResult?displayProperty=nameWithType> objekty k vyvolání operace asynchronně.</span><span class="sxs-lookup"><span data-stu-id="1e44e-172">With WCF client channel objects, you must use <xref:System.IAsyncResult?displayProperty=nameWithType> objects to invoke your operations asynchronously.</span></span> <span data-ttu-id="1e44e-173">Chcete-li použít tuto metodu, zadejte **/async** možnost pomocí příkazu [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1e44e-173">To use this approach, specify the **/async** command option with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async   
```  
  
 <span data-ttu-id="1e44e-174">Tím se vygeneruje kontraktu služby ve které je každá operace modelovaná jako `<Begin>` metodu s <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> vlastnost nastavena na `true` a odpovídající `<End>` metoda.</span><span class="sxs-lookup"><span data-stu-id="1e44e-174">This generates a service contract in which each operation is modeled as a `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true` and a corresponding `<End>` method.</span></span> <span data-ttu-id="1e44e-175">Úplný příklad použití <xref:System.ServiceModel.ChannelFactory%601>, naleznete v tématu [jak: Asynchronní volání operací pomocí objektu pro vytváření kanálů](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="1e44e-175">For a complete example using a <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
 <span data-ttu-id="1e44e-176">V obou případech se aplikace může vyvolat operaci asynchronně i v případě, že služba se implementuje synchronně, stejným způsobem, který aplikace může používat stejný vzor pro vyvolání asynchronně místní synchronní metody.</span><span class="sxs-lookup"><span data-stu-id="1e44e-176">In either case, applications can invoke an operation asynchronously even if the service is implemented synchronously, in the same way that an application can use the same pattern to invoke asynchronously a local synchronous method.</span></span> <span data-ttu-id="1e44e-177">Jak implementovat operace není důležité pro klienta. Při doručení zprávy s odpovědí, jeho obsah je odeslán na straně klienta asynchronní <`End`> metoda a klient načte informace.</span><span class="sxs-lookup"><span data-stu-id="1e44e-177">How the operation is implemented is not significant to the client; when the response message arrives, its content is dispatched to the client's asynchronous <`End`> method and the client retrieves the information.</span></span>  
  
### <a name="one-way-message-exchange-patterns"></a><span data-ttu-id="1e44e-178">Jednosměrná zpráva Exchange vzory</span><span class="sxs-lookup"><span data-stu-id="1e44e-178">One-Way Message Exchange Patterns</span></span>  
 <span data-ttu-id="1e44e-179">Vzor asynchronních zpráv exchange můžete také vytvořit v jednosměrné operace, které (operace, pro kterou <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> je `true` mít žádné korelační reakce) může odeslat v obou směrech klienta nebo služby nezávisle na druhém na straně.</span><span class="sxs-lookup"><span data-stu-id="1e44e-179">You can also create an asynchronous message exchange pattern in which one-way operations (operations for which the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> is `true` have no correlated response) can be sent in either direction by the client or service independently of the other side.</span></span> <span data-ttu-id="1e44e-180">(Tato služba využívá vzoru výměny zpráv duplexní s jednosměrné zprávy.) V tomto případě určuje kontrakt služby jednosměrná zpráva systému exchange, který může implementovat buď na straně jako byla zahájena asynchronní volání nebo implementací, nebo Ne, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="1e44e-180">(This uses the duplex message exchange pattern with one-way messages.) In this case, the service contract specifies a one-way message exchange that either side can implement as asynchronous calls or implementations, or not, as appropriate.</span></span> <span data-ttu-id="1e44e-181">Obecně platí výměny jednosměrné zprávy po kontrakt implementace do značné míry lze asynchronní vzhledem k tomu, jakmile je odeslána zpráva aplikace nečeká na odpověď a můžete pokračovat v provádění jiné práce.</span><span class="sxs-lookup"><span data-stu-id="1e44e-181">Generally, when the contract is an exchange of one-way messages, the implementations can largely be asynchronous because once a message is sent the application does not wait for a reply and can continue doing other work.</span></span>  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a><span data-ttu-id="1e44e-182">Asynchronní klienty založené na události a kontrakty zpráv</span><span class="sxs-lookup"><span data-stu-id="1e44e-182">Event-based Asynchronous Clients and Message Contracts</span></span>  
 <span data-ttu-id="1e44e-183">Pokyny návrhu pro asynchronní model založený na událostech stát, že pokud se vrátí více než jednu hodnotu, se vrátí jednu hodnotu jako `Result` vlastnosti a ostatní jsou vrácena jako vlastnosti na <xref:System.EventArgs> objektu.</span><span class="sxs-lookup"><span data-stu-id="1e44e-183">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="1e44e-184">Jeden výsledek tohoto je, že pokud klient naimportuje metadata pomocí možnosti založené na událostech asynchronního příkazu a operace vrátí více než jednu hodnotu, výchozí <xref:System.EventArgs> objekt vrátí jednu hodnotu jako `Result` vlastnost a zbývající jsou vlastnosti <xref:System.EventArgs> objektu.</span><span class="sxs-lookup"><span data-stu-id="1e44e-184">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="1e44e-185">Pokud chcete přijímat zprávy objektu jako `Result` vlastnost a vrácené hodnoty jako vlastnosti objektu, použijte **/messageContract** možnost příkazu.</span><span class="sxs-lookup"><span data-stu-id="1e44e-185">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the **/messageContract** command option.</span></span> <span data-ttu-id="1e44e-186">Tím se vygeneruje podpis, který vrací zprávy s odpovědí jako `Result` vlastnost <xref:System.EventArgs> objektu.</span><span class="sxs-lookup"><span data-stu-id="1e44e-186">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="1e44e-187">Všechny interní vrácené hodnoty jsou pak vlastnosti objektu zprávu odpovědi.</span><span class="sxs-lookup"><span data-stu-id="1e44e-187">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e44e-188">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e44e-188">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>
- <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
