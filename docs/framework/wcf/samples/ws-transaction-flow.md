---
title: Tok transakcí webové služby
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: bf78b679be84efa416d088d5addaaa25a593abf4
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="ws-transaction-flow"></a><span data-ttu-id="19652-102">Tok transakcí webové služby</span><span class="sxs-lookup"><span data-stu-id="19652-102">WS Transaction Flow</span></span>
<span data-ttu-id="19652-103">Tento příklad znázorňuje použití transakce koordinované klienta a klient a server možnosti pro transakci toku pomocí protokolu WS-Atomic Transactions nebo OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="19652-103">This sample demonstrates the use of a client-coordinated transaction and the client and server options for transaction flow using either the WS-Atomic Transaction or OleTransactions protocol.</span></span> <span data-ttu-id="19652-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje ale operace, které jsou označené k předvedení použití `TransactionFlowAttribute` s **TransactionFlowOption** výčet k určení, do jaké míry transakce toku povolený.</span><span class="sxs-lookup"><span data-stu-id="19652-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service but the operations are attributed to demonstrate the use of the `TransactionFlowAttribute` with the **TransactionFlowOption** enumeration to determine to what degree transaction flow is enabled.</span></span> <span data-ttu-id="19652-105">V rámci oboru sdružení transakcí protokolu požadovaná operace je zapsán do databáze a dál, dokud klient koordinované transakce byla dokončena – i když klientská transakce nedokončí, transakce webové služby zajišťuje, že příslušné aktualizace do databáze nejsou potvrzeny.</span><span class="sxs-lookup"><span data-stu-id="19652-105">Within the scope of the flowed transaction, a log of the requested operations is written to a database and persists until the client coordinated transaction has completed - if the client transaction does not complete, the Web service transaction ensures that the appropriate updates to the database are not committed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19652-106">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="19652-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="19652-107">Po inicializaci připojení k služby a transakce, klient přistupuje k několik operací služby.</span><span class="sxs-lookup"><span data-stu-id="19652-107">After initiating a connection to the service and a transaction, the client accesses several service operations.</span></span> <span data-ttu-id="19652-108">Kontrakt služby je definován následujícím způsobem v každé z operací jiné nastavení pro demonstraci `TransactionFlowOption`.</span><span class="sxs-lookup"><span data-stu-id="19652-108">The contract for the service is defined as follows with each of the operations demonstrating a different setting for the `TransactionFlowOption`.</span></span>  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Add(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Allowed)]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.NotAllowed)]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);   
}  
```

 <span data-ttu-id="19652-109">Definuje operace v pořadí, ve kterém se mají být zpracovány:</span><span class="sxs-lookup"><span data-stu-id="19652-109">This defines the operations in the order they are to be processed:</span></span>  
  
-   <span data-ttu-id="19652-110">`Add` Žádost o operaci musí zahrnovat sdružení transakcí.</span><span class="sxs-lookup"><span data-stu-id="19652-110">An `Add` operation request must include a flowed transaction.</span></span>  
  
-   <span data-ttu-id="19652-111">A `Subtract` žádost o operaci může zahrnovat sdružení transakcí.</span><span class="sxs-lookup"><span data-stu-id="19652-111">A `Subtract` operation request may include a flowed transaction.</span></span>  
  
-   <span data-ttu-id="19652-112">A `Multiply` žádost o operaci nesmí obsahovat sdružení transakcí prostřednictvím explicitní NotAllowed nastavení.</span><span class="sxs-lookup"><span data-stu-id="19652-112">A `Multiply` operation request must not include a flowed transaction through the explicit NotAllowed setting.</span></span>  
  
-   <span data-ttu-id="19652-113">A `Divide` žádost o operaci nesmí obsahovat sdružení transakcí prostřednictvím vynechání `TransactionFlow` atribut.</span><span class="sxs-lookup"><span data-stu-id="19652-113">A `Divide` operation request must not include a flowed transaction through the omission of a `TransactionFlow` attribute.</span></span>  
  
 <span data-ttu-id="19652-114">Povolení toku transakcí, vazby s [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) vlastnost povoleno je nutné použít kromě atributy příslušnou operaci.</span><span class="sxs-lookup"><span data-stu-id="19652-114">To enable transaction flow, bindings with the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled must be used in addition to the appropriate operation attributes.</span></span> <span data-ttu-id="19652-115">Konfigurace služby v této ukázce zpřístupní koncový bod TCP a koncový bod HTTP kromě koncový bod metadat systému Exchange.</span><span class="sxs-lookup"><span data-stu-id="19652-115">In this sample, the service's configuration exposes a TCP endpoint and an HTTP endpoint in addition to a Metadata Exchange endpoint.</span></span> <span data-ttu-id="19652-116">Koncový bod TCP a koncový bod protokolu HTTP použijte následující vazby, které mají [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) vlastnost povoleno.</span><span class="sxs-lookup"><span data-stu-id="19652-116">The TCP endpoint and the HTTP endpoint use the following bindings, both of which have the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled.</span></span>  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding name="transactionalOleTransactionsTcpBinding"  
             transactionFlow="true"  
             transactionProtocol="OleTransactions"/>  
  </netTcpBinding>  
  <wsHttpBinding>  
    <binding name="transactionalWsatHttpBinding"  
             transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="19652-117">Poskytované systémem netTcpBinding umožňuje specifikaci transactionProtocol, zatímco wsHttpBinding poskytované systémem používá jenom více interoperabilní WSAtomicTransactionOctober2004 protokol.</span><span class="sxs-lookup"><span data-stu-id="19652-117">The system-provided netTcpBinding allows specification of the transactionProtocol whereas the system-provided wsHttpBinding uses only the more interoperable WSAtomicTransactionOctober2004 protocol.</span></span> <span data-ttu-id="19652-118">OleTransactions, protokol je k dispozici pro pouze pomocí klienti Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="19652-118">The OleTransactions protocol is only available for use by Windows Communication Foundation (WCF) clients.</span></span>  
  
 <span data-ttu-id="19652-119">Pro třídu, která implementuje `ICalculator` rozhraní, všechny metody jsou opatřená <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> vlastnost nastavena na hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="19652-119">For the class that implements the `ICalculator` interface, all of the methods are attributed with <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property set to `true`.</span></span> <span data-ttu-id="19652-120">Toto nastavení deklaruje, že všechny akce prováděné v rámci metody dojít v rámci oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="19652-120">This setting declares that all actions taken within the method occur within the scope of a transaction.</span></span> <span data-ttu-id="19652-121">Akce prováděné v tomto případě zahrnují záznam do protokolu databáze.</span><span class="sxs-lookup"><span data-stu-id="19652-121">In this case, the actions taken include recording to the log database.</span></span> <span data-ttu-id="19652-122">Pokud žádost o operaci zahrnuje sdružení transakcí akce, které se vyskytují v rozsahu příchozí transakce nebo nového oboru transakce se automaticky vygeneroval.</span><span class="sxs-lookup"><span data-stu-id="19652-122">If the operation request includes a flowed transaction then the actions occur within the scope of the incoming transaction or a new transaction scope is automatically generated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19652-123"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> Vlastnost definuje chování, které jsou místní pro implementace metoda služby a nedefinuje schopnost klienta nebo požadavek toku transakce.</span><span class="sxs-lookup"><span data-stu-id="19652-123">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property defines behavior local to the service method implementations and does not define the client's ability to or requirement for flowing a transaction.</span></span>  

```csharp
// Service class that implements the service contract.  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Add(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n1, n2));  
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Subtract(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n2, n1));  
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Multiply(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", n1, n2));  
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Divide(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", n1, n2));  
        return n1 / n2;  
    }  
  
    // Logging method omitted for brevity  
}  
```

 <span data-ttu-id="19652-124">Na klienta, službu `TransactionFlowOption` nastavení na operace se projeví v definici generovaného klienta `ICalculator` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="19652-124">On the client, the service's `TransactionFlowOption` settings on the operations are reflected in the client's generated definition of the `ICalculator` interface.</span></span> <span data-ttu-id="19652-125">Navíc služby `transactionFlow` se projeví nastavení vlastnosti v konfiguraci klienta aplikace.</span><span class="sxs-lookup"><span data-stu-id="19652-125">Also, the service's `transactionFlow` property settings are reflected in the client's application configuration.</span></span> <span data-ttu-id="19652-126">Klienta můžete vybrat přenosu a protokol výběrem příslušné `endpointConfigurationName`.</span><span class="sxs-lookup"><span data-stu-id="19652-126">The client can select the transport and protocol by selecting the appropriate `endpointConfigurationName`.</span></span>  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
>  <span data-ttu-id="19652-127">Zjištěnou chování Tato ukázka je stejný bez ohledu na to, který je vybrán protokol nebo přenos.</span><span class="sxs-lookup"><span data-stu-id="19652-127">The observed behavior of this sample is the same no matter which protocol or transport is chosen.</span></span>  
  
 <span data-ttu-id="19652-128">Bylo zahájeno připojení ke službě, klient vytvoří novou `TransactionScope` kolem volání operací služby.</span><span class="sxs-lookup"><span data-stu-id="19652-128">Having initiated the connection to the service, the client creates a new `TransactionScope` around the calls to the service operations.</span></span>  

```csharp
// Start a transaction scope  
using (TransactionScope tx =  
            new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    Console.WriteLine("Starting transaction");  
  
    // Call the Add service operation  
    //  - generatedClient will flow the required active transaction  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("  Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation  
    //  - generatedClient will flow the allowed active transaction  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Start a transaction scope that suppresses the current transaction  
    using (TransactionScope txSuppress =  
                new TransactionScope(TransactionScopeOption.Suppress))  
    {  
        // Call the Subtract service operation  
        //  - the active transaction is suppressed from the generatedClient  
        //    and no transaction will flow  
        value1 = 21.05D;  
        value2 = 42.16D;  
        result = client.Subtract(value1, value2);  
        Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
        // Complete the suppressed scope  
        txSuppress.Complete();  
    }  
  
    // Call the Multiply service operation  
    // - generatedClient will not flow the active transaction  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("  Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    // - generatedClient will not flow the active transaction  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("  Divide({0},{1}) = {2}", value1, value2, result);  
  
    // Complete the transaction scope  
    Console.WriteLine("  Completing transaction");  
    tx.Complete();  
}  
  
Console.WriteLine("Transaction committed");  
```

 <span data-ttu-id="19652-129">Volání operace jsou následující:</span><span class="sxs-lookup"><span data-stu-id="19652-129">The calls to the operations are as follows:</span></span>  
  
-   <span data-ttu-id="19652-130">`Add` Požadavek toků požadované transakce ke službě a k akcím služby v rámci oboru transakce klienta.</span><span class="sxs-lookup"><span data-stu-id="19652-130">The `Add` request flows the required transaction to the service and the service's actions occur within the scope of the client's transaction.</span></span>  
  
-   <span data-ttu-id="19652-131">První `Subtract` požadavek také toků povolené transakce ke službě a znovu k akcím služby v rámci oboru transakce klienta.</span><span class="sxs-lookup"><span data-stu-id="19652-131">The first `Subtract` request also flows the allowed transaction to the service and again the service's actions occur within the scope of the client's transaction.</span></span>  
  
-   <span data-ttu-id="19652-132">Druhý `Subtract` požadavku je provést v rámci nového oboru transakce deklarovat s `TransactionScopeOption.Suppress` možnost.</span><span class="sxs-lookup"><span data-stu-id="19652-132">The second `Subtract` request is performed within a new transaction scope declared with the `TransactionScopeOption.Suppress` option.</span></span> <span data-ttu-id="19652-133">To potlačí počáteční vnější transakci klienta a požadavek nepostupuje transakce ke službě.</span><span class="sxs-lookup"><span data-stu-id="19652-133">This suppresses the client's initial outer transaction and the request does not flow a transaction to the service.</span></span> <span data-ttu-id="19652-134">Tento přístup umožňuje klientovi výslovně výslovný nesouhlas s a chránit proti toku transakce služby, při které se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="19652-134">This approach allows a client to explicitly opt-out of and protect against flowing a transaction to a service when that is not required.</span></span> <span data-ttu-id="19652-135">Služby akce se provedou v rámci oboru transakce nové a které nejsou připojeny.</span><span class="sxs-lookup"><span data-stu-id="19652-135">The service's actions occur within the scope of a new and unconnected transaction.</span></span>  
  
-   <span data-ttu-id="19652-136">`Multiply` Požadavku není toku transakce ke službě, protože klient je vygenerován definice `ICalculator` rozhraní obsahuje <xref:System.ServiceModel.TransactionFlowAttribute> nastavena na <xref:System.ServiceModel.TransactionFlowOption> `NotAllowed`.</span><span class="sxs-lookup"><span data-stu-id="19652-136">The `Multiply` request does not flow a transaction to the service because the client's generated definition of the `ICalculator` interface includes a <xref:System.ServiceModel.TransactionFlowAttribute> set to <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span></span>  
  
-   <span data-ttu-id="19652-137">`Divide` Požadavku není toku transakce ke službě, protože klient je znovu vygenerován definice `ICalculator` rozhraní nezahrnuje `TransactionFlowAttribute`.</span><span class="sxs-lookup"><span data-stu-id="19652-137">The `Divide` request does not flow a transaction to the service because again the client's generated definition of the `ICalculator` interface does not include a `TransactionFlowAttribute`.</span></span> <span data-ttu-id="19652-138">V rámci oboru jiné nové a které nejsou připojeny transakci znovu provedou služby akce.</span><span class="sxs-lookup"><span data-stu-id="19652-138">The service's actions again occur within the scope of another new and unconnected transaction.</span></span>  
  
 <span data-ttu-id="19652-139">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="19652-139">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="19652-140">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="19652-140">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Starting transaction  
  Add(100,15.99) = 115.99  
  Subtract(145,76.54) = 68.46  
  Subtract(21.05,42.16) = -21.11  
  Multiply(9,81.25) = 731.25  
  Divide(22,7) = 3.14285714285714  
  Completing transaction  
Transaction committed  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="19652-141">Protokolování žádosti o operaci služby se zobrazí v okně konzoly služby.</span><span class="sxs-lookup"><span data-stu-id="19652-141">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="19652-142">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="19652-142">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 <span data-ttu-id="19652-143">Po úspěšném spuštění dokončí oboru transakce klienta a potvrzeny všechny akce prováděné v rámci tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="19652-143">After a successful execution, the client's transaction scope completes and all actions taken within that scope are committed.</span></span> <span data-ttu-id="19652-144">Konkrétně uvedené 5 záznamy zůstávají v databázi služby.</span><span class="sxs-lookup"><span data-stu-id="19652-144">Specifically, the noted 5 records are persisted in the service's database.</span></span> <span data-ttu-id="19652-145">První 2 z nich došlo v rámci oboru transakce klienta.</span><span class="sxs-lookup"><span data-stu-id="19652-145">The first 2 of these have occurred within the scope of the client's transaction.</span></span>  
  
 <span data-ttu-id="19652-146">Pokud došlo k výjimce kdekoli v rámci klienta `TransactionScope` pak transakci nelze dokončit.</span><span class="sxs-lookup"><span data-stu-id="19652-146">If an exception occurred anywhere within the client's `TransactionScope` then the transaction cannot complete.</span></span> <span data-ttu-id="19652-147">To způsobí, že záznamy zapsané do protokolu v rámci tohoto oboru na nebyla zapsána do databáze.</span><span class="sxs-lookup"><span data-stu-id="19652-147">This causes the records logged within that scope to not be committed to the database.</span></span> <span data-ttu-id="19652-148">Tento efekt může být dodržen opakováním ukázku spustit po komentářů se volání dokončení vnější `TransactionScope`.</span><span class="sxs-lookup"><span data-stu-id="19652-148">This effect can be observed by repeating the sample run after commenting out the call to complete the outer `TransactionScope`.</span></span> <span data-ttu-id="19652-149">Na takové spustit pouze poslední 3 akce (od druhého `Subtract`, `Multiply` a `Divide` požadavky) se protokolují, protože klientská transakce toku není na ty.</span><span class="sxs-lookup"><span data-stu-id="19652-149">On such a run, only the last 3 actions (from the second `Subtract`, the `Multiply` and the `Divide` requests) are logged because the client transaction did not flow to those.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="19652-150">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="19652-150">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="19652-151">Sestavení C# nebo Visual Basic .NET verzi řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)</span><span class="sxs-lookup"><span data-stu-id="19652-151">To build the C# or Visual Basic .NET version of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)</span></span>  
  
2.  <span data-ttu-id="19652-152">Ujistěte se, že jste nainstalovali SQL Server Express Edition nebo SQL Server a že připojovací řetězec nebyla správně nastavena v konfiguračním souboru aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="19652-152">Ensure that you have installed SQL Server Express Edition or SQL Server, and that the connection string has been correctly set in the service’s application configuration file.</span></span> <span data-ttu-id="19652-153">Chcete-li spustit ukázku bez použití databáze, nastavte `usingSql` hodnota v konfiguračním souboru aplikace služby k `false`</span><span class="sxs-lookup"><span data-stu-id="19652-153">To run the sample without using a database, set the `usingSql` value in the service’s application configuration file to `false`</span></span>  
  
3.  <span data-ttu-id="19652-154">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="19652-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="19652-155">Pro konfiguraci mezi počítače povolte Distributed Transaction Coordinator pomocí níže uvedených pokynů a použít nástroj WsatConfig.exe ze sady Windows SDK k povolení podpory sítě transakce WCF.</span><span class="sxs-lookup"><span data-stu-id="19652-155">For cross-machine configuration, enable the Distributed Transaction Coordinator using the instructions below, and use the WsatConfig.exe tool from the Windows SDK to enable WCF Transactions network support.</span></span> <span data-ttu-id="19652-156">V tématu [konfigurace podpory WS-Atomic Transactions](http://go.microsoft.com/fwlink/?LinkId=190370) informace o nastavení WsatConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="19652-156">See [Configuring WS-Atomic Transaction Support](http://go.microsoft.com/fwlink/?LinkId=190370) for information on setting up WsatConfig.exe.</span></span>  
  
 <span data-ttu-id="19652-157">Jestli spuštěním ukázky ve stejném počítači nebo na různých počítačích, musíte nakonfigurovat Microsoft distribuované transakce koordinátora služba MSDTC () k povolení toku transakcí sítě a použít nástroj WsatConfig.exe k povolení podpory sítě transakce WCF.</span><span class="sxs-lookup"><span data-stu-id="19652-157">Whether you run the sample on the same computer or on different computers, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable WCF transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a><span data-ttu-id="19652-158">Konfigurace Microsoft distribuované transakce koordinátora služba MSDTC () k podpoře spouštění vzorku</span><span class="sxs-lookup"><span data-stu-id="19652-158">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample</span></span>  
  
1.  <span data-ttu-id="19652-159">Na počítači služby se systémem Windows Server 2003 nebo Windows XP nakonfigurujte služby MSDTC povolit příchozí transakce sítě podle těchto pokynů.</span><span class="sxs-lookup"><span data-stu-id="19652-159">On a service machine running Windows Server 2003 or Windows XP, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1.  <span data-ttu-id="19652-160">Z **spustit** nabídky, přejděte na **ovládací panely**, pak **nástroje pro správu**a potom **služby komponent**.</span><span class="sxs-lookup"><span data-stu-id="19652-160">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="19652-161">Rozbalte položku **služby komponent**.</span><span class="sxs-lookup"><span data-stu-id="19652-161">Expand **Component Services**.</span></span> <span data-ttu-id="19652-162">Otevřete **počítače** složky.</span><span class="sxs-lookup"><span data-stu-id="19652-162">Open the **Computers** folder.</span></span>  
  
    3.  <span data-ttu-id="19652-163">Klikněte pravým tlačítkem na **Můj počítač** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="19652-163">Right-click **My Computer** and select **Properties**.</span></span>  
  
    4.  <span data-ttu-id="19652-164">Na **služby MSDTC** , klikněte na **konfigurace zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="19652-164">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    5.  <span data-ttu-id="19652-165">Zkontrolujte **síťový přístup DTC** a **povolit příchozí**.</span><span class="sxs-lookup"><span data-stu-id="19652-165">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    6.  <span data-ttu-id="19652-166">Klikněte na tlačítko **OK**, pak klikněte na tlačítko **Ano** restartovat služba koordinátoru MS DTC.</span><span class="sxs-lookup"><span data-stu-id="19652-166">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    7.  <span data-ttu-id="19652-167">Klikněte na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="19652-167">Click **OK** to close the dialog box.</span></span>  
  
2.  <span data-ttu-id="19652-168">Na počítači služby se systémem Windows Server 2008 nebo Windows Vista nakonfigurujte služby MSDTC povolit příchozí transakce sítě podle těchto pokynů.</span><span class="sxs-lookup"><span data-stu-id="19652-168">On a service machine running Windows Server 2008 or Windows Vista, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1.  <span data-ttu-id="19652-169">Z **spustit** nabídky, přejděte na **ovládací panely**, pak **nástroje pro správu**a potom **služby komponent**.</span><span class="sxs-lookup"><span data-stu-id="19652-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="19652-170">Rozbalte položku **služby komponent**.</span><span class="sxs-lookup"><span data-stu-id="19652-170">Expand **Component Services**.</span></span> <span data-ttu-id="19652-171">Otevřete **počítače** složky.</span><span class="sxs-lookup"><span data-stu-id="19652-171">Open the **Computers** folder.</span></span> <span data-ttu-id="19652-172">Vyberte **Distributed Transaction Coordinator**.</span><span class="sxs-lookup"><span data-stu-id="19652-172">Select **Distributed Transaction Coordinator**.</span></span>  
  
    3.  <span data-ttu-id="19652-173">Klikněte pravým tlačítkem na **koordinátoru DTC** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="19652-173">Right-click **DTC Coordinator** and select **Properties**.</span></span>  
  
    4.  <span data-ttu-id="19652-174">Na **zabezpečení** zkontrolujte **síťový přístup DTC** a **povolit příchozí**.</span><span class="sxs-lookup"><span data-stu-id="19652-174">On the **Security** tab, check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5.  <span data-ttu-id="19652-175">Klikněte na tlačítko **OK**, pak klikněte na tlačítko **Ano** restartovat služba koordinátoru MS DTC.</span><span class="sxs-lookup"><span data-stu-id="19652-175">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6.  <span data-ttu-id="19652-176">Klikněte na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="19652-176">Click **OK** to close the dialog box.</span></span>  
  
3.  <span data-ttu-id="19652-177">V klientském počítači nakonfigurujte služby MSDTC povolit odchozí transakce sítě:</span><span class="sxs-lookup"><span data-stu-id="19652-177">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1.  <span data-ttu-id="19652-178">Z **spustit** nabídky, přejděte na `Control Panel`, pak **nástroje pro správu**a potom **služby komponent**.</span><span class="sxs-lookup"><span data-stu-id="19652-178">From the **Start** menu, navigate to `Control Panel`, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="19652-179">Klikněte pravým tlačítkem na **Můj počítač** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="19652-179">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="19652-180">Na **služby MSDTC** , klikněte na **konfigurace zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="19652-180">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4.  <span data-ttu-id="19652-181">Zkontrolujte **síťový přístup DTC** a **povolit odchozí**.</span><span class="sxs-lookup"><span data-stu-id="19652-181">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5.  <span data-ttu-id="19652-182">Klikněte na tlačítko **OK**, pak klikněte na tlačítko **Ano** restartovat služba koordinátoru MS DTC.</span><span class="sxs-lookup"><span data-stu-id="19652-182">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6.  <span data-ttu-id="19652-183">Klikněte na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="19652-183">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="19652-184">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="19652-184">The samples may already be installed on your machine.</span></span> <span data-ttu-id="19652-185">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="19652-185">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="19652-186">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="19652-186">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="19652-187">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="19652-187">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
