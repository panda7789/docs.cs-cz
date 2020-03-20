---
title: Tok transakcí webové služby
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: 8b037a2faa6ed5f7c77ea9347b92af7dc1ec2c27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183171"
---
# <a name="ws-transaction-flow"></a><span data-ttu-id="2d5b4-102">Tok transakcí webové služby</span><span class="sxs-lookup"><span data-stu-id="2d5b4-102">WS Transaction Flow</span></span>
<span data-ttu-id="2d5b4-103">Tato ukázka ukazuje použití transakce koordinované klientem a možnosti klienta a serveru pro tok transakcí pomocí protokolu WS-Atomic Transaction nebo OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-103">This sample demonstrates the use of a client-coordinated transaction and the client and server options for transaction flow using either the WS-Atomic Transaction or OleTransactions protocol.</span></span> <span data-ttu-id="2d5b4-104">Tento příklad je založen na [Začínáme,](../../../../docs/framework/wcf/samples/getting-started-sample.md) který implementuje službu kalkulačky, `TransactionFlowAttribute` ale operace jsou přiřazeny k předvedení použití s **TransactionFlowOption** výčtu k určení, do jaké míry je povolen tok transakcí.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service but the operations are attributed to demonstrate the use of the `TransactionFlowAttribute` with the **TransactionFlowOption** enumeration to determine to what degree transaction flow is enabled.</span></span> <span data-ttu-id="2d5b4-105">V rámci tokované transakce je do databáze zapsán protokol požadovaných operací a přetrvává, dokud nebude dokončena koordinovaná transakce klienta – pokud transakce klienta není dokončena, transakce webové služby zajistí, že transakce webové služby zajistí, že transakce webové služby příslušné aktualizace databáze nejsou potvrzeny.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-105">Within the scope of the flowed transaction, a log of the requested operations is written to a database and persists until the client coordinated transaction has completed - if the client transaction does not complete, the Web service transaction ensures that the appropriate updates to the database are not committed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d5b4-106">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2d5b4-107">Po spuštění připojení ke službě a transakce klient přistupuje k několika operacím služby.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-107">After initiating a connection to the service and a transaction, the client accesses several service operations.</span></span> <span data-ttu-id="2d5b4-108">Smlouva o poskytování služeb je definována takto u každého z `TransactionFlowOption`operací, které prokazují jiné nastavení pro .</span><span class="sxs-lookup"><span data-stu-id="2d5b4-108">The contract for the service is defined as follows with each of the operations demonstrating a different setting for the `TransactionFlowOption`.</span></span>  

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

 <span data-ttu-id="2d5b4-109">To definuje operace v pořadí, v jakém mají být zpracovány:</span><span class="sxs-lookup"><span data-stu-id="2d5b4-109">This defines the operations in the order they are to be processed:</span></span>  
  
- <span data-ttu-id="2d5b4-110">Požadavek `Add` operace musí obsahovat tok transakce.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-110">An `Add` operation request must include a flowed transaction.</span></span>  
  
- <span data-ttu-id="2d5b4-111">Požadavek `Subtract` na operaci může zahrnovat tokovou transakci.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-111">A `Subtract` operation request may include a flowed transaction.</span></span>  
  
- <span data-ttu-id="2d5b4-112">Požadavek `Multiply` operace nesmí obsahovat tokovou transakci prostřednictvím explicitního nastavení NotAllowed.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-112">A `Multiply` operation request must not include a flowed transaction through the explicit NotAllowed setting.</span></span>  
  
- <span data-ttu-id="2d5b4-113">Požadavek `Divide` operace nesmí obsahovat tokovou transakci `TransactionFlow` prostřednictvím vynechání atributu.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-113">A `Divide` operation request must not include a flowed transaction through the omission of a `TransactionFlow` attribute.</span></span>  
  
 <span data-ttu-id="2d5b4-114">Chcete-li povolit tok [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) transakcí, musí být použity vazby s povolenou vlastností transactionFlow>kromě příslušných atributů operace.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-114">To enable transaction flow, bindings with the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled must be used in addition to the appropriate operation attributes.</span></span> <span data-ttu-id="2d5b4-115">V této ukázce konfigurace služby zpřístupňuje koncový bod TCP a koncový bod HTTP kromě koncového bodu serveru Metadata Exchange.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-115">In this sample, the service's configuration exposes a TCP endpoint and an HTTP endpoint in addition to a Metadata Exchange endpoint.</span></span> <span data-ttu-id="2d5b4-116">Koncový bod TCP a koncový bod HTTP používají následující vazby, které mají [ \<povolenou vlastnost transactionFlow>.](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)</span><span class="sxs-lookup"><span data-stu-id="2d5b4-116">The TCP endpoint and the HTTP endpoint use the following bindings, both of which have the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled.</span></span>  
  
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
> <span data-ttu-id="2d5b4-117">Systémem poskytované netTcpBinding umožňuje specifikaci transactionProtocol vzhledem k tomu, že systémem poskytované wsHttpBinding používá pouze interoperabilnější WSAtomicTransactionOctober2004 protokol.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-117">The system-provided netTcpBinding allows specification of the transactionProtocol whereas the system-provided wsHttpBinding uses only the more interoperable WSAtomicTransactionOctober2004 protocol.</span></span> <span data-ttu-id="2d5b4-118">Protokol OleTransactions je k dispozici pouze pro klienty WCF (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="2d5b4-118">The OleTransactions protocol is only available for use by Windows Communication Foundation (WCF) clients.</span></span>  
  
 <span data-ttu-id="2d5b4-119">Pro třídu, která `ICalculator` implementuje rozhraní, jsou <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> všechny metody `true`přiřazeny s vlastností nastavenou na .</span><span class="sxs-lookup"><span data-stu-id="2d5b4-119">For the class that implements the `ICalculator` interface, all of the methods are attributed with <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property set to `true`.</span></span> <span data-ttu-id="2d5b4-120">Toto nastavení deklaruje, že všechny akce provedené v rámci metody dojít v rámci transakce.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-120">This setting declares that all actions taken within the method occur within the scope of a transaction.</span></span> <span data-ttu-id="2d5b4-121">V tomto případě provedené akce zahrnují záznam do databáze protokolu.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-121">In this case, the actions taken include recording to the log database.</span></span> <span data-ttu-id="2d5b4-122">Pokud požadavek operace obsahuje tok transakce pak akce dojít v rámci rozsahu příchozí transakce nebo je automaticky generován nový rozsah transakce.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-122">If the operation request includes a flowed transaction then the actions occur within the scope of the incoming transaction or a new transaction scope is automatically generated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d5b4-123">Vlastnost <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> definuje chování místní implementace metody služby a nedefinuje schopnost klienta nebo požadavek na tekoucí transakce.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-123">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property defines behavior local to the service method implementations and does not define the client's ability to or requirement for flowing a transaction.</span></span>  

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

 <span data-ttu-id="2d5b4-124">Na straně klienta `TransactionFlowOption` nastavení služby na operace se projeví v klientově `ICalculator` generované definice rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-124">On the client, the service's `TransactionFlowOption` settings on the operations are reflected in the client's generated definition of the `ICalculator` interface.</span></span> <span data-ttu-id="2d5b4-125">Nastavení `transactionFlow` vlastností služby se také projeví v konfiguraci aplikace klienta.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-125">Also, the service's `transactionFlow` property settings are reflected in the client's application configuration.</span></span> <span data-ttu-id="2d5b4-126">Klient může vybrat přenos a protokol výběrem příslušného `endpointConfigurationName`.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-126">The client can select the transport and protocol by selecting the appropriate `endpointConfigurationName`.</span></span>  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
> <span data-ttu-id="2d5b4-127">Pozorované chování tohoto vzorku je stejné bez ohledu na to, který protokol nebo přenos je vybrán.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-127">The observed behavior of this sample is the same no matter which protocol or transport is chosen.</span></span>  
  
 <span data-ttu-id="2d5b4-128">Po iniciování připojení ke službě vytvoří `TransactionScope` klient nové kolem volání operací služby.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-128">Having initiated the connection to the service, the client creates a new `TransactionScope` around the calls to the service operations.</span></span>  

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

 <span data-ttu-id="2d5b4-129">Volání operací jsou následující:</span><span class="sxs-lookup"><span data-stu-id="2d5b4-129">The calls to the operations are as follows:</span></span>  
  
- <span data-ttu-id="2d5b4-130">Požadavek `Add` toky požadovanou transakci do služby a akce služby dojít v rámci transakce klienta.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-130">The `Add` request flows the required transaction to the service and the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="2d5b4-131">První `Subtract` požadavek také toky povolené transakce do služby a znovu akce služby dojít v rámci transakce klienta.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-131">The first `Subtract` request also flows the allowed transaction to the service and again the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="2d5b4-132">Druhý `Subtract` požadavek se provádí v rámci `TransactionScopeOption.Suppress` nového oboru transakce deklarované s možností.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-132">The second `Subtract` request is performed within a new transaction scope declared with the `TransactionScopeOption.Suppress` option.</span></span> <span data-ttu-id="2d5b4-133">To potlačí počáteční vnější transakce klienta a požadavek netokuje transakce do služby.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-133">This suppresses the client's initial outer transaction and the request does not flow a transaction to the service.</span></span> <span data-ttu-id="2d5b4-134">Tento přístup umožňuje klientovi explicitně odhlásit a chránit před tekoucí transakce do služby, pokud to není požadováno.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-134">This approach allows a client to explicitly opt-out of and protect against flowing a transaction to a service when that is not required.</span></span> <span data-ttu-id="2d5b4-135">Akce služby dojít v rámci nové a nepřipojené transakce.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-135">The service's actions occur within the scope of a new and unconnected transaction.</span></span>  
  
- <span data-ttu-id="2d5b4-136">`Multiply` Požadavek netokuje transakci do služby, protože klientova `ICalculator` vygenerovaná definice rozhraní obsahuje <xref:System.ServiceModel.TransactionFlowAttribute> sadu na <xref:System.ServiceModel.TransactionFlowOption> `NotAllowed`.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-136">The `Multiply` request does not flow a transaction to the service because the client's generated definition of the `ICalculator` interface includes a <xref:System.ServiceModel.TransactionFlowAttribute> set to <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span></span>  
  
- <span data-ttu-id="2d5b4-137">Požadavek `Divide` netokuje transakci do služby, protože znovu klienta generované definice `ICalculator` rozhraní neobsahuje `TransactionFlowAttribute`.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-137">The `Divide` request does not flow a transaction to the service because again the client's generated definition of the `ICalculator` interface does not include a `TransactionFlowAttribute`.</span></span> <span data-ttu-id="2d5b4-138">Akce služby znovu dojít v rámci jiné nové a nepřipojené transakce.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-138">The service's actions again occur within the scope of another new and unconnected transaction.</span></span>  
  
 <span data-ttu-id="2d5b4-139">Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-139">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2d5b4-140">Stisknutím klávesy ENTER v okně klienta vypněte klienta.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-140">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
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
  
 <span data-ttu-id="2d5b4-141">Protokolování požadavků na provoz služby se zobrazí v okně konzoly služby.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-141">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="2d5b4-142">Stisknutím klávesy ENTER v okně klienta vypněte klienta.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-142">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 <span data-ttu-id="2d5b4-143">Po úspěšném spuštění dokončení oboru transakce klienta a všechny akce provedené v rámci tohoto oboru jsou potvrzeny.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-143">After a successful execution, the client's transaction scope completes and all actions taken within that scope are committed.</span></span> <span data-ttu-id="2d5b4-144">Konkrétně je v databázi služby zachováno 5 záznamů.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-144">Specifically, the noted 5 records are persisted in the service's database.</span></span> <span data-ttu-id="2d5b4-145">První 2 z nich došlo v rámci transakce klienta.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-145">The first 2 of these have occurred within the scope of the client's transaction.</span></span>  
  
 <span data-ttu-id="2d5b4-146">Pokud došlo k výjimce `TransactionScope` kdekoli v rámci klienta pak transakce nelze dokončit.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-146">If an exception occurred anywhere within the client's `TransactionScope` then the transaction cannot complete.</span></span> <span data-ttu-id="2d5b4-147">To způsobí, že záznamy zaznamenané v rámci tohoto oboru není potvrzena do databáze.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-147">This causes the records logged within that scope to not be committed to the database.</span></span> <span data-ttu-id="2d5b4-148">Tento efekt lze pozorovat opakováním spuštění vzorku po zakomentování volání k dokončení vnější `TransactionScope`.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-148">This effect can be observed by repeating the sample run after commenting out the call to complete the outer `TransactionScope`.</span></span> <span data-ttu-id="2d5b4-149">Při takovém spuštění jsou zaznamenány pouze poslední `Subtract`3 `Multiply` akce `Divide` (z druhé , a požadavky) protože transakce klienta netokla k těmto.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-149">On such a run, only the last 3 actions (from the second `Subtract`, the `Multiply` and the `Divide` requests) are logged because the client transaction did not flow to those.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2d5b4-150">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="2d5b4-150">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2d5b4-151">Chcete-li vytvořit verzi řešení jazyka C# nebo Visual Basic .NET, postupujte podle pokynů v [části Vytváření ukázek windows communication foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)</span><span class="sxs-lookup"><span data-stu-id="2d5b4-151">To build the C# or Visual Basic .NET version of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)</span></span>  
  
2. <span data-ttu-id="2d5b4-152">Ujistěte se, že jste nainstalovali SQL Server Express Edition nebo SQL Server a že připojovací řetězec byl správně nastaven v konfiguračním souboru aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-152">Ensure that you have installed SQL Server Express Edition or SQL Server, and that the connection string has been correctly set in the service’s application configuration file.</span></span> <span data-ttu-id="2d5b4-153">Chcete-li spustit ukázku bez `usingSql` použití databáze, nastavte hodnotu v konfiguračním souboru aplikace služby na`false`</span><span class="sxs-lookup"><span data-stu-id="2d5b4-153">To run the sample without using a database, set the `usingSql` value in the service’s application configuration file to `false`</span></span>  
  
3. <span data-ttu-id="2d5b4-154">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2d5b4-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2d5b4-155">Pro konfiguraci mezi počítači povolte koordinátora distribuovaných transakcí pomocí níže uvedených pokynů a pomocí nástroje WsatConfig.exe z sady Windows SDK povolte podporu sítě WCF Transactions.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-155">For cross-machine configuration, enable the Distributed Transaction Coordinator using the instructions below, and use the WsatConfig.exe tool from the Windows SDK to enable WCF Transactions network support.</span></span> <span data-ttu-id="2d5b4-156">Informace o nastavení souboru WsatConfig.exe naleznete [v tématu Configuring WS-Atomic Transaction Support](../feature-details/configuring-ws-atomic-transaction-support.md).</span><span class="sxs-lookup"><span data-stu-id="2d5b4-156">For information on setting up WsatConfig.exe, see [Configuring WS-Atomic Transaction Support](../feature-details/configuring-ws-atomic-transaction-support.md).</span></span>  
  
 <span data-ttu-id="2d5b4-157">Bez ohledu na to, zda spustíte ukázku ve stejném počítači nebo v různých počítačích, je nutné nakonfigurovat koordinátor microsoft distribuovaných transakcí (MSDTC) tak, aby umožňoval tok síťových transakcí a pomocí nástroje WsatConfig.exe povoloval podporu sítě transakcí WCF.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-157">Whether you run the sample on the same computer or on different computers, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable WCF transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a><span data-ttu-id="2d5b4-158">Konfigurace koordinátoru distribuovaných transakcí společnosti Microsoft (MSDTC) pro podporu spuštění ukázkové</span><span class="sxs-lookup"><span data-stu-id="2d5b4-158">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample</span></span>  
  
1. <span data-ttu-id="2d5b4-159">V servisním počítači se systémem Windows Server 2003 nebo Windows XP nakonfigurujte koordinátor MSDTC tak, aby umožňoval příchozí síťové transakce podle následujících pokynů.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-159">On a service machine running Windows Server 2003 or Windows XP, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="2d5b4-160">V nabídce **Start** přejděte na **Ovládací panely**, nástroje **pro správu**a poté **na služby Component Services**.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-160">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="2d5b4-161">Rozbalte **službu Component Services**.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-161">Expand **Component Services**.</span></span> <span data-ttu-id="2d5b4-162">Otevřete složku **Počítače.**</span><span class="sxs-lookup"><span data-stu-id="2d5b4-162">Open the **Computers** folder.</span></span>  
  
    3. <span data-ttu-id="2d5b4-163">Klepněte pravým tlačítkem myši na **položku Tento počítač** a vyberte příkaz **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-163">Right-click **My Computer** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="2d5b4-164">Na kartě **MSDTC** klepněte na **položku Konfigurace zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-164">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    5. <span data-ttu-id="2d5b4-165">Zkontrolujte **přístup k síti DTC** a **povolit příchozí**připojení .</span><span class="sxs-lookup"><span data-stu-id="2d5b4-165">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    6. <span data-ttu-id="2d5b4-166">Klepněte na tlačítko **OK**a potom klepnutím na **tlačítko Ano** restartujte službu MSDTC.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-166">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    7. <span data-ttu-id="2d5b4-167">Kliknutím na **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-167">Click **OK** to close the dialog box.</span></span>  
  
2. <span data-ttu-id="2d5b4-168">V servisním počítači se systémem Windows Server 2008 nebo Windows Vista nakonfigurujte koordinátor MSDTC tak, aby umožňoval příchozí síťové transakce podle následujících pokynů.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-168">On a service machine running Windows Server 2008 or Windows Vista, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="2d5b4-169">V nabídce **Start** přejděte na **Ovládací panely**, nástroje **pro správu**a poté **na služby Component Services**.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="2d5b4-170">Rozbalte **službu Component Services**.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-170">Expand **Component Services**.</span></span> <span data-ttu-id="2d5b4-171">Otevřete složku **Počítače.**</span><span class="sxs-lookup"><span data-stu-id="2d5b4-171">Open the **Computers** folder.</span></span> <span data-ttu-id="2d5b4-172">Vyberte **koordinátor distribuovaných transakcí**.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-172">Select **Distributed Transaction Coordinator**.</span></span>  
  
    3. <span data-ttu-id="2d5b4-173">Klepněte pravým tlačítkem myši na **položku Koordinátor koordinátoru DTC** a vyberte příkaz **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-173">Right-click **DTC Coordinator** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="2d5b4-174">Na kartě **Zabezpečení** zaškrtněte **políčko Síťový přístup k dtc** a **povolit vstup**.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-174">On the **Security** tab, check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5. <span data-ttu-id="2d5b4-175">Klepněte na tlačítko **OK**a potom klepnutím na **tlačítko Ano** restartujte službu MSDTC.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-175">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="2d5b4-176">Kliknutím na **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-176">Click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="2d5b4-177">V klientském počítači nakonfigurujte msdtc tak, aby umožňoval odchozí síťové transakce:</span><span class="sxs-lookup"><span data-stu-id="2d5b4-177">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1. <span data-ttu-id="2d5b4-178">V nabídce **Start** `Control Panel`přejděte na **položku Nástroje pro správu**a potom **na služby Component Services**.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-178">From the **Start** menu, navigate to `Control Panel`, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="2d5b4-179">Klepněte pravým tlačítkem myši na **položku Tento počítač** a vyberte příkaz **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-179">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3. <span data-ttu-id="2d5b4-180">Na kartě **MSDTC** klepněte na **položku Konfigurace zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-180">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4. <span data-ttu-id="2d5b4-181">Zkontrolujte **přístup k síti DTC** a **povolit odchozí**přístup .</span><span class="sxs-lookup"><span data-stu-id="2d5b4-181">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5. <span data-ttu-id="2d5b4-182">Klepněte na tlačítko **OK**a potom klepnutím na **tlačítko Ano** restartujte službu MSDTC.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-182">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="2d5b4-183">Kliknutím na **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-183">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2d5b4-184">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-184">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2d5b4-185">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-185">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="2d5b4-186">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-186">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2d5b4-187">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="2d5b4-187">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
