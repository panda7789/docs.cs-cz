---
title: Tok transakcí webové služby
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: 781934e9ab27f761e71841c2edc509f9b8022aa7
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094745"
---
# <a name="ws-transaction-flow"></a><span data-ttu-id="4fe6c-102">Tok transakcí webové služby</span><span class="sxs-lookup"><span data-stu-id="4fe6c-102">WS Transaction Flow</span></span>
<span data-ttu-id="4fe6c-103">Tato ukázka demonstruje použití transakce s koordinovaným klientem a možností klienta a serveru pro tok transakce pomocí protokolu WS-Atomic nebo protokolu OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-103">This sample demonstrates the use of a client-coordinated transaction and the client and server options for transaction flow using either the WS-Atomic Transaction or OleTransactions protocol.</span></span> <span data-ttu-id="4fe6c-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) , která implementuje službu kalkulačky, ale operace jsou popsány k předvedení použití `TransactionFlowAttribute` s výčtem **TransactionFlowOption** k určení toho, jakým způsobem je tok transakcí povolen.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service but the operations are attributed to demonstrate the use of the `TransactionFlowAttribute` with the **TransactionFlowOption** enumeration to determine to what degree transaction flow is enabled.</span></span> <span data-ttu-id="4fe6c-105">V rámci rozsahu transakce toku se do databáze zapíše protokol požadovaných operací, dokud se nedokončila koordinovaný transakce klienta – Pokud se transakce klienta nedokončila, transakce webové služby zajistí, že příslušné aktualizace databáze nejsou potvrzeny.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-105">Within the scope of the flowed transaction, a log of the requested operations is written to a database and persists until the client coordinated transaction has completed - if the client transaction does not complete, the Web service transaction ensures that the appropriate updates to the database are not committed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4fe6c-106">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4fe6c-107">Po zahájení připojení ke službě a transakci klient přistupuje k několika operacím služby.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-107">After initiating a connection to the service and a transaction, the client accesses several service operations.</span></span> <span data-ttu-id="4fe6c-108">Smlouva pro službu je definována následovně a všemi operacemi, které demonstrují jiné nastavení `TransactionFlowOption`.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-108">The contract for the service is defined as follows with each of the operations demonstrating a different setting for the `TransactionFlowOption`.</span></span>  

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

 <span data-ttu-id="4fe6c-109">Tím se definují operace v pořadí, ve kterém se mají zpracovat:</span><span class="sxs-lookup"><span data-stu-id="4fe6c-109">This defines the operations in the order they are to be processed:</span></span>  
  
- <span data-ttu-id="4fe6c-110">Požadavek operace `Add` musí zahrnovat transakci typu Flow.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-110">An `Add` operation request must include a flowed transaction.</span></span>  
  
- <span data-ttu-id="4fe6c-111">Požadavek na operaci `Subtract` může zahrnovat transakci typu Flow.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-111">A `Subtract` operation request may include a flowed transaction.</span></span>  
  
- <span data-ttu-id="4fe6c-112">Požadavek operace `Multiply` nesmí zahrnovat transakci toku prostřednictvím explicitního nastavení.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-112">A `Multiply` operation request must not include a flowed transaction through the explicit NotAllowed setting.</span></span>  
  
- <span data-ttu-id="4fe6c-113">Požadavek operace `Divide` nesmí zahrnovat tok transakce v důsledku vynechání atributu `TransactionFlow`.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-113">A `Divide` operation request must not include a flowed transaction through the omission of a `TransactionFlow` attribute.</span></span>  
  
 <span data-ttu-id="4fe6c-114">Aby bylo možné povolit tok transakce, musí být kromě příslušných atributů operace použita vazba s povolenou vlastností [\<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) .</span><span class="sxs-lookup"><span data-stu-id="4fe6c-114">To enable transaction flow, bindings with the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled must be used in addition to the appropriate operation attributes.</span></span> <span data-ttu-id="4fe6c-115">V této ukázce konfigurace služby zveřejňuje koncový bod TCP a koncový bod HTTP kromě koncového bodu výměny metadat.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-115">In this sample, the service's configuration exposes a TCP endpoint and an HTTP endpoint in addition to a Metadata Exchange endpoint.</span></span> <span data-ttu-id="4fe6c-116">Koncový bod TCP a koncový bod HTTP používají následující vazby, u kterých je povolena vlastnost [\<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) .</span><span class="sxs-lookup"><span data-stu-id="4fe6c-116">The TCP endpoint and the HTTP endpoint use the following bindings, both of which have the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled.</span></span>  
  
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
> <span data-ttu-id="4fe6c-117">Systém netTcpBinding poskytuje specifikace transactionProtocol, zatímco systém wsHttpBinding používá pouze bezpečnější WSAtomicTransactionOctober2004 protokol.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-117">The system-provided netTcpBinding allows specification of the transactionProtocol whereas the system-provided wsHttpBinding uses only the more interoperable WSAtomicTransactionOctober2004 protocol.</span></span> <span data-ttu-id="4fe6c-118">Protokol OleTransactions je k dispozici pouze pro klienty Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4fe6c-118">The OleTransactions protocol is only available for use by Windows Communication Foundation (WCF) clients.</span></span>  
  
 <span data-ttu-id="4fe6c-119">Pro třídu, která implementuje rozhraní `ICalculator`, jsou všechny metody nastaveny s vlastností <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> nastavenou na `true`.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-119">For the class that implements the `ICalculator` interface, all of the methods are attributed with <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property set to `true`.</span></span> <span data-ttu-id="4fe6c-120">Toto nastavení deklaruje, že všechny akce provedené v rámci metody nastávají v rámci rozsahu transakce.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-120">This setting declares that all actions taken within the method occur within the scope of a transaction.</span></span> <span data-ttu-id="4fe6c-121">V takovém případě akce prováděné zahrnují záznam do databáze protokolu.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-121">In this case, the actions taken include recording to the log database.</span></span> <span data-ttu-id="4fe6c-122">Pokud požadavek na operaci zahrnuje transakci typu flow, pak dojde k akcím v rámci oboru příchozí transakce nebo je automaticky vygenerován nový obor transakce.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-122">If the operation request includes a flowed transaction then the actions occur within the scope of the incoming transaction or a new transaction scope is automatically generated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4fe6c-123">Vlastnost <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> definuje chování jako lokální pro implementace metod služby a nedefinuje schopnost klienta nebo požadavek na tok transakce.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-123">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property defines behavior local to the service method implementations and does not define the client's ability to or requirement for flowing a transaction.</span></span>  

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

 <span data-ttu-id="4fe6c-124">V klientovi se nastavení `TransactionFlowOption` služby na operace odrazí v definici `ICalculator` rozhraní vygenerované klientem.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-124">On the client, the service's `TransactionFlowOption` settings on the operations are reflected in the client's generated definition of the `ICalculator` interface.</span></span> <span data-ttu-id="4fe6c-125">Také nastavení vlastnosti `transactionFlow` služby se projeví v konfiguraci aplikace klienta.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-125">Also, the service's `transactionFlow` property settings are reflected in the client's application configuration.</span></span> <span data-ttu-id="4fe6c-126">Klient může vybrat přenos a protokol výběrem příslušné `endpointConfigurationName`.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-126">The client can select the transport and protocol by selecting the appropriate `endpointConfigurationName`.</span></span>  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
> <span data-ttu-id="4fe6c-127">Zjištěné chování této ukázky je stejné bez ohledu na to, který protokol nebo přenos se volí.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-127">The observed behavior of this sample is the same no matter which protocol or transport is chosen.</span></span>  
  
 <span data-ttu-id="4fe6c-128">Po iniciaci připojení ke službě vytvoří klient nové `TransactionScope` kolem volání služby.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-128">Having initiated the connection to the service, the client creates a new `TransactionScope` around the calls to the service operations.</span></span>  

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

 <span data-ttu-id="4fe6c-129">Volání operací jsou následující:</span><span class="sxs-lookup"><span data-stu-id="4fe6c-129">The calls to the operations are as follows:</span></span>  
  
- <span data-ttu-id="4fe6c-130">Požadavek `Add` natéká do služby požadovanou transakci a akce služby se objeví v rámci rozsahu transakce klienta.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-130">The `Add` request flows the required transaction to the service and the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="4fe6c-131">První `Subtract` požadavek také Flowe povolenou transakci ke službě a akce služby se projeví v rozsahu transakce klienta.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-131">The first `Subtract` request also flows the allowed transaction to the service and again the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="4fe6c-132">Druhá `Subtract` požadavek se provádí v rámci nového oboru transakce deklarovaného s možností `TransactionScopeOption.Suppress`.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-132">The second `Subtract` request is performed within a new transaction scope declared with the `TransactionScopeOption.Suppress` option.</span></span> <span data-ttu-id="4fe6c-133">Tím se potlačí počáteční vnější transakce klienta a požadavek neflowe transakci ke službě.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-133">This suppresses the client's initial outer transaction and the request does not flow a transaction to the service.</span></span> <span data-ttu-id="4fe6c-134">Tento přístup umožňuje klientovi explicitně se odhlásit a chránit před přetečením transakce do služby, když to není nutné.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-134">This approach allows a client to explicitly opt-out of and protect against flowing a transaction to a service when that is not required.</span></span> <span data-ttu-id="4fe6c-135">Akce služby se vyskytují v rámci rozsahu nové a nepřipojené transakce.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-135">The service's actions occur within the scope of a new and unconnected transaction.</span></span>  
  
- <span data-ttu-id="4fe6c-136">Požadavek `Multiply` neflowe transakci ke službě, protože vygenerovaná definice `ICalculator` rozhraní klienta obsahuje <xref:System.ServiceModel.TransactionFlowAttribute> nastaveno na <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-136">The `Multiply` request does not flow a transaction to the service because the client's generated definition of the `ICalculator` interface includes a <xref:System.ServiceModel.TransactionFlowAttribute> set to <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span></span>  
  
- <span data-ttu-id="4fe6c-137">Požadavek `Divide` neflowe transakci ke službě, protože znovu vygenerovaná definice `ICalculator` rozhraní nezahrnuje `TransactionFlowAttribute`.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-137">The `Divide` request does not flow a transaction to the service because again the client's generated definition of the `ICalculator` interface does not include a `TransactionFlowAttribute`.</span></span> <span data-ttu-id="4fe6c-138">Akce služby se znovu vyskytují v rozsahu jiné nové a nepřipojené transakce.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-138">The service's actions again occur within the scope of another new and unconnected transaction.</span></span>  
  
 <span data-ttu-id="4fe6c-139">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-139">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="4fe6c-140">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-140">Press ENTER in the client window to shut down the client.</span></span>  
  
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
  
 <span data-ttu-id="4fe6c-141">Protokolování požadavků na operace služby se zobrazí v okně konzoly služby.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-141">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="4fe6c-142">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-142">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 <span data-ttu-id="4fe6c-143">Po úspěšném provedení se rozsah transakce klienta dokončí a všechny akce prováděné v rámci tohoto oboru jsou potvrzeny.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-143">After a successful execution, the client's transaction scope completes and all actions taken within that scope are committed.</span></span> <span data-ttu-id="4fe6c-144">Konkrétně zaznamenané 5 záznamy jsou v databázi služby trvalé.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-144">Specifically, the noted 5 records are persisted in the service's database.</span></span> <span data-ttu-id="4fe6c-145">První 2 z nich došlo v rámci oboru transakce klienta.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-145">The first 2 of these have occurred within the scope of the client's transaction.</span></span>  
  
 <span data-ttu-id="4fe6c-146">Pokud došlo k výjimce kdekoli v rámci `TransactionScope` klienta, transakce nemůže být dokončena.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-146">If an exception occurred anywhere within the client's `TransactionScope` then the transaction cannot complete.</span></span> <span data-ttu-id="4fe6c-147">To způsobí, že záznamy zaznamenané do tohoto oboru nebudou potvrzeny do databáze.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-147">This causes the records logged within that scope to not be committed to the database.</span></span> <span data-ttu-id="4fe6c-148">Tento efekt lze pozorovat opakovaným spuštěním ukázkového běhu po zakomentování volání za účelem dokončení vnějšího `TransactionScope`.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-148">This effect can be observed by repeating the sample run after commenting out the call to complete the outer `TransactionScope`.</span></span> <span data-ttu-id="4fe6c-149">V takovém případě jsou protokolovány pouze poslední 3 akce (od druhé `Subtract`, `Multiply` a `Divide` požadavky), protože transakce klienta neproudí do těch.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-149">On such a run, only the last 3 actions (from the second `Subtract`, the `Multiply` and the `Divide` requests) are logged because the client transaction did not flow to those.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4fe6c-150">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="4fe6c-150">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4fe6c-151">Pokud chcete vytvořit C# nebo Visual Basic verzi rozhraní .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)</span><span class="sxs-lookup"><span data-stu-id="4fe6c-151">To build the C# or Visual Basic .NET version of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)</span></span>  
  
2. <span data-ttu-id="4fe6c-152">Ujistěte se, že máte nainstalovanou edici SQL Server Express nebo SQL Server a že připojovací řetězec byl v konfiguračním souboru aplikace služby správně nastaven.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-152">Ensure that you have installed SQL Server Express Edition or SQL Server, and that the connection string has been correctly set in the service’s application configuration file.</span></span> <span data-ttu-id="4fe6c-153">Chcete-li spustit ukázku bez použití databáze, nastavte `usingSql` hodnoty v konfiguračním souboru aplikace služby na `false`</span><span class="sxs-lookup"><span data-stu-id="4fe6c-153">To run the sample without using a database, set the `usingSql` value in the service’s application configuration file to `false`</span></span>  
  
3. <span data-ttu-id="4fe6c-154">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4fe6c-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4fe6c-155">V případě konfigurace mezi počítači povolte DTC (Distributed Transaction Coordinator) podle níže uvedených pokynů a pomocí nástroje WsatConfig. exe z Windows SDK povolte podporu transakcí WCF v síti.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-155">For cross-machine configuration, enable the Distributed Transaction Coordinator using the instructions below, and use the WsatConfig.exe tool from the Windows SDK to enable WCF Transactions network support.</span></span> <span data-ttu-id="4fe6c-156">Informace o nastavení WsatConfig. exe najdete v tématu [Konfigurace podpory transakcí WS-Atomic](../feature-details/configuring-ws-atomic-transaction-support.md).</span><span class="sxs-lookup"><span data-stu-id="4fe6c-156">For information on setting up WsatConfig.exe, see [Configuring WS-Atomic Transaction Support](../feature-details/configuring-ws-atomic-transaction-support.md).</span></span>  
  
 <span data-ttu-id="4fe6c-157">Bez ohledu na to, jestli spouštíte ukázku na stejném počítači nebo na různých počítačích, musíte nakonfigurovat Microsoft DTC (Distributed Transaction Coordinator) (MSDTC), aby se povolil tok síťových transakcí, a pomocí nástroje WsatConfig. exe povolit podporu sítě WCF Transactions.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-157">Whether you run the sample on the same computer or on different computers, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable WCF transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a><span data-ttu-id="4fe6c-158">Konfigurace služby Microsoft DTC (Distributed Transaction Coordinator) (MSDTC) pro podporu spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="4fe6c-158">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample</span></span>  
  
1. <span data-ttu-id="4fe6c-159">V počítači služby se systémem Windows Server 2003 nebo Windows XP nakonfigurujte službu MSDTC tak, aby povolovala příchozí síťové transakce pomocí následujících pokynů.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-159">On a service machine running Windows Server 2003 or Windows XP, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="4fe6c-160">V nabídce **Start** přejděte na **Ovládací panely**, klikněte na **Nástroje pro správu**a pak na **služby komponent**.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-160">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="4fe6c-161">Rozbalte položku **Služba komponent**.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-161">Expand **Component Services**.</span></span> <span data-ttu-id="4fe6c-162">Otevřete složku **počítače** .</span><span class="sxs-lookup"><span data-stu-id="4fe6c-162">Open the **Computers** folder.</span></span>  
  
    3. <span data-ttu-id="4fe6c-163">Pravým tlačítkem myši klikněte na položku **Tento počítač** a vyberte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-163">Right-click **My Computer** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="4fe6c-164">Na kartě **MSDTC** klikněte na **Konfigurace zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-164">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    5. <span data-ttu-id="4fe6c-165">Ověřte **přístup k síťovému DTC** a **povolte příchozí**.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-165">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    6. <span data-ttu-id="4fe6c-166">Klikněte na tlačítko **OK**a potom kliknutím na tlačítko **Ano** restartujte službu MSDTC.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-166">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    7. <span data-ttu-id="4fe6c-167">Kliknutím na **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-167">Click **OK** to close the dialog box.</span></span>  
  
2. <span data-ttu-id="4fe6c-168">V počítači služby se systémem Windows Server 2008 nebo Windows Vista nakonfigurujte službu MSDTC tak, aby povolovala příchozí síťové transakce pomocí následujících pokynů.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-168">On a service machine running Windows Server 2008 or Windows Vista, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="4fe6c-169">V nabídce **Start** přejděte na **Ovládací panely**, klikněte na **Nástroje pro správu**a pak na **služby komponent**.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="4fe6c-170">Rozbalte položku **Služba komponent**.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-170">Expand **Component Services**.</span></span> <span data-ttu-id="4fe6c-171">Otevřete složku **počítače** .</span><span class="sxs-lookup"><span data-stu-id="4fe6c-171">Open the **Computers** folder.</span></span> <span data-ttu-id="4fe6c-172">Vyberte **DTC (Distributed Transaction Coordinator)** .</span><span class="sxs-lookup"><span data-stu-id="4fe6c-172">Select **Distributed Transaction Coordinator**.</span></span>  
  
    3. <span data-ttu-id="4fe6c-173">Klikněte pravým tlačítkem na **koordinátor DTC** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-173">Right-click **DTC Coordinator** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="4fe6c-174">Na kartě **zabezpečení** ověřte **přístup k síti DTC** a **povolte příchozí**.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-174">On the **Security** tab, check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5. <span data-ttu-id="4fe6c-175">Klikněte na tlačítko **OK**a potom kliknutím na tlačítko **Ano** restartujte službu MSDTC.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-175">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="4fe6c-176">Kliknutím na **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-176">Click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="4fe6c-177">Na klientském počítači nakonfigurujte koordinátor MSDTC tak, aby povoloval odchozí síťové transakce:</span><span class="sxs-lookup"><span data-stu-id="4fe6c-177">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1. <span data-ttu-id="4fe6c-178">V nabídce **Start** přejděte na `Control Panel`, pak na **Nástroje pro správu**a pak na **služby komponent**.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-178">From the **Start** menu, navigate to `Control Panel`, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="4fe6c-179">Pravým tlačítkem myši klikněte na položku **Tento počítač** a vyberte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-179">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3. <span data-ttu-id="4fe6c-180">Na kartě **MSDTC** klikněte na **Konfigurace zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-180">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4. <span data-ttu-id="4fe6c-181">Ověřte **přístup k síťovému DTC** a **Povolte odchozí**.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-181">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5. <span data-ttu-id="4fe6c-182">Klikněte na tlačítko **OK**a potom kliknutím na tlačítko **Ano** restartujte službu MSDTC.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-182">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="4fe6c-183">Kliknutím na **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-183">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4fe6c-184">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-184">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4fe6c-185">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-185">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="4fe6c-186">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-186">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4fe6c-187">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4fe6c-187">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
