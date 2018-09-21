---
title: Tok transakcí webové služby
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: 35af3090c0f898578a5f8dfb81d02d22a0074ad2
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46471327"
---
# <a name="ws-transaction-flow"></a><span data-ttu-id="e19cd-102">Tok transakcí webové služby</span><span class="sxs-lookup"><span data-stu-id="e19cd-102">WS Transaction Flow</span></span>
<span data-ttu-id="e19cd-103">Tato ukázka demonstruje použití transakce koordinovaný klienta a klient a server možnosti pro transakci tok pomocí protokolu WS-Atomic Transactions nebo OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="e19cd-103">This sample demonstrates the use of a client-coordinated transaction and the client and server options for transaction flow using either the WS-Atomic Transaction or OleTransactions protocol.</span></span> <span data-ttu-id="e19cd-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) , který implementuje službu kalkulačky, ale operace mají atributy pro demonstraci použití `TransactionFlowAttribute` s **TransactionFlowOption** výčet, chcete-li zjistit, jaké úroveň transakce je povolen tok.</span><span class="sxs-lookup"><span data-stu-id="e19cd-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service but the operations are attributed to demonstrate the use of the `TransactionFlowAttribute` with the **TransactionFlowOption** enumeration to determine to what degree transaction flow is enabled.</span></span> <span data-ttu-id="e19cd-105">V rámci oboru sdružení probíhajících transakcí, protokol požadované operace jsou zapsána do databáze a zůstává v platnosti do klienta koordinované transakce byla dokončena – Pokud klientská transakce nedokončí, transakce webové služby zajišťuje, že příslušné aktualizace do databáze nejsou potvrzeny.</span><span class="sxs-lookup"><span data-stu-id="e19cd-105">Within the scope of the flowed transaction, a log of the requested operations is written to a database and persists until the client coordinated transaction has completed - if the client transaction does not complete, the Web service transaction ensures that the appropriate updates to the database are not committed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e19cd-106">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="e19cd-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e19cd-107">Po zahájení připojení do služby a transakce ke kterým přistupuje klient několik operací služby.</span><span class="sxs-lookup"><span data-stu-id="e19cd-107">After initiating a connection to the service and a transaction, the client accesses several service operations.</span></span> <span data-ttu-id="e19cd-108">Kontrakt služby je definovaná následujícím způsobem s každou operací demonstrace různých nastavení `TransactionFlowOption`.</span><span class="sxs-lookup"><span data-stu-id="e19cd-108">The contract for the service is defined as follows with each of the operations demonstrating a different setting for the `TransactionFlowOption`.</span></span>  

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

 <span data-ttu-id="e19cd-109">Definuje operace v pořadí, ve kterém jsou ke zpracování:</span><span class="sxs-lookup"><span data-stu-id="e19cd-109">This defines the operations in the order they are to be processed:</span></span>  
  
-   <span data-ttu-id="e19cd-110">`Add` Žádost o operaci musí obsahovat sdružení probíhajících transakcí.</span><span class="sxs-lookup"><span data-stu-id="e19cd-110">An `Add` operation request must include a flowed transaction.</span></span>  
  
-   <span data-ttu-id="e19cd-111">A `Subtract` žádost o operaci může zahrnovat sdružení probíhajících transakcí.</span><span class="sxs-lookup"><span data-stu-id="e19cd-111">A `Subtract` operation request may include a flowed transaction.</span></span>  
  
-   <span data-ttu-id="e19cd-112">A `Multiply` žádost o operaci, nesmí obsahovat toku transakce pomocí explicitní nastavení hodnotu NotAllowed.</span><span class="sxs-lookup"><span data-stu-id="e19cd-112">A `Multiply` operation request must not include a flowed transaction through the explicit NotAllowed setting.</span></span>  
  
-   <span data-ttu-id="e19cd-113">A `Divide` žádost o operaci, nesmí obsahovat sdružení probíhajících transakcí prostřednictvím vynechání `TransactionFlow` atribut.</span><span class="sxs-lookup"><span data-stu-id="e19cd-113">A `Divide` operation request must not include a flowed transaction through the omission of a `TransactionFlow` attribute.</span></span>  
  
 <span data-ttu-id="e19cd-114">Povolení toku transakcí, vazby s [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) vlastnost povoleno je nutné použít kromě atributů příslušné operace.</span><span class="sxs-lookup"><span data-stu-id="e19cd-114">To enable transaction flow, bindings with the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled must be used in addition to the appropriate operation attributes.</span></span> <span data-ttu-id="e19cd-115">Konfigurace služby v této ukázce zpřístupňuje koncový bod TCP a koncový bod HTTP kromě koncový bod výměny metadat.</span><span class="sxs-lookup"><span data-stu-id="e19cd-115">In this sample, the service's configuration exposes a TCP endpoint and an HTTP endpoint in addition to a Metadata Exchange endpoint.</span></span> <span data-ttu-id="e19cd-116">Koncový bod TCP a koncový bod protokolu HTTP použijte následující vazby, které mají [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) vlastnost povolena.</span><span class="sxs-lookup"><span data-stu-id="e19cd-116">The TCP endpoint and the HTTP endpoint use the following bindings, both of which have the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled.</span></span>  
  
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
>  <span data-ttu-id="e19cd-117">NetTcpBinding poskytované systémem zatímco wsHttpBinding poskytované systémem používá více interoperabilní protokol WSAtomicTransactionOctober2004 umožňuje volbu specifikace třídu transactionProtocol.</span><span class="sxs-lookup"><span data-stu-id="e19cd-117">The system-provided netTcpBinding allows specification of the transactionProtocol whereas the system-provided wsHttpBinding uses only the more interoperable WSAtomicTransactionOctober2004 protocol.</span></span> <span data-ttu-id="e19cd-118">Použít OleTransactions, který protokol je dostupná jenom pro klienty Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e19cd-118">The OleTransactions protocol is only available for use by Windows Communication Foundation (WCF) clients.</span></span>  
  
 <span data-ttu-id="e19cd-119">Pro třídu, která implementuje `ICalculator` rozhraní, všechny metody jsou připisuje <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> nastavenou na `true`.</span><span class="sxs-lookup"><span data-stu-id="e19cd-119">For the class that implements the `ICalculator` interface, all of the methods are attributed with <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property set to `true`.</span></span> <span data-ttu-id="e19cd-120">Toto nastavení deklaruje, že všechny akce prováděné v metodě dojít v rámci oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="e19cd-120">This setting declares that all actions taken within the method occur within the scope of a transaction.</span></span> <span data-ttu-id="e19cd-121">Akce prováděné v tomto případě patří nahrávání protokolu databáze.</span><span class="sxs-lookup"><span data-stu-id="e19cd-121">In this case, the actions taken include recording to the log database.</span></span> <span data-ttu-id="e19cd-122">Pokud žádost o operaci zahrnují sdružení probíhajících transakcí dojde k akcím v rámci oboru příchozí transakce nebo nový obor transakce není automaticky vygenerován.</span><span class="sxs-lookup"><span data-stu-id="e19cd-122">If the operation request includes a flowed transaction then the actions occur within the scope of the incoming transaction or a new transaction scope is automatically generated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e19cd-123"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> Vlastnost definuje chování místní implementace metod služby a nedefinuje schopnost klienta nebo požadavek toku transakce.</span><span class="sxs-lookup"><span data-stu-id="e19cd-123">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property defines behavior local to the service method implementations and does not define the client's ability to or requirement for flowing a transaction.</span></span>  

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

 <span data-ttu-id="e19cd-124">Na klienta, služba `TransactionFlowOption` nastavení na operace se projeví v definici generovaného klienta `ICalculator` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e19cd-124">On the client, the service's `TransactionFlowOption` settings on the operations are reflected in the client's generated definition of the `ICalculator` interface.</span></span> <span data-ttu-id="e19cd-125">Kromě toho služby `transactionFlow` nastavení vlastnosti se projeví v konfiguraci klienta aplikace.</span><span class="sxs-lookup"><span data-stu-id="e19cd-125">Also, the service's `transactionFlow` property settings are reflected in the client's application configuration.</span></span> <span data-ttu-id="e19cd-126">Klienta můžete vybrat přenosu a protokol tak, že vyberete příslušný `endpointConfigurationName`.</span><span class="sxs-lookup"><span data-stu-id="e19cd-126">The client can select the transport and protocol by selecting the appropriate `endpointConfigurationName`.</span></span>  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
>  <span data-ttu-id="e19cd-127">Vypozorovaná chování této ukázky je stejný bez ohledu na to, který je vybrán protokol nebo přenos.</span><span class="sxs-lookup"><span data-stu-id="e19cd-127">The observed behavior of this sample is the same no matter which protocol or transport is chosen.</span></span>  
  
 <span data-ttu-id="e19cd-128">Zahájení připojení ke službě vytvoří klient nový `TransactionScope` po volání operace služby.</span><span class="sxs-lookup"><span data-stu-id="e19cd-128">Having initiated the connection to the service, the client creates a new `TransactionScope` around the calls to the service operations.</span></span>  

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

 <span data-ttu-id="e19cd-129">Volání operace jsou následující:</span><span class="sxs-lookup"><span data-stu-id="e19cd-129">The calls to the operations are as follows:</span></span>  
  
-   <span data-ttu-id="e19cd-130">`Add` Požadavek toky požadovanou transakci ke službě a k akcím služby v rámci oboru transakce na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="e19cd-130">The `Add` request flows the required transaction to the service and the service's actions occur within the scope of the client's transaction.</span></span>  
  
-   <span data-ttu-id="e19cd-131">První `Subtract` požadavku se přenášejí také povolené transakce ve službě a znovu k akcím služby v rámci oboru transakce na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="e19cd-131">The first `Subtract` request also flows the allowed transaction to the service and again the service's actions occur within the scope of the client's transaction.</span></span>  
  
-   <span data-ttu-id="e19cd-132">Druhá `Subtract` žádosti se provede v rámci nového oboru transakce deklarována s `TransactionScopeOption.Suppress` možnost.</span><span class="sxs-lookup"><span data-stu-id="e19cd-132">The second `Subtract` request is performed within a new transaction scope declared with the `TransactionScopeOption.Suppress` option.</span></span> <span data-ttu-id="e19cd-133">Toto potlačí počáteční vnější transakci klienta a požadavek nepostupuje transakci ke službě.</span><span class="sxs-lookup"><span data-stu-id="e19cd-133">This suppresses the client's initial outer transaction and the request does not flow a transaction to the service.</span></span> <span data-ttu-id="e19cd-134">Tento přístup umožňuje klientovi explicitně odhlásit a ochranu proti toku transakce služby, při které se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="e19cd-134">This approach allows a client to explicitly opt-out of and protect against flowing a transaction to a service when that is not required.</span></span> <span data-ttu-id="e19cd-135">V rámci oboru transakce nové a nepřipojené provedou služby akce.</span><span class="sxs-lookup"><span data-stu-id="e19cd-135">The service's actions occur within the scope of a new and unconnected transaction.</span></span>  
  
-   <span data-ttu-id="e19cd-136">`Multiply` Žádost o nepostupuje transakce ve službě, protože klient vygenerovaný definice `ICalculator` zahrnuje rozhraní <xref:System.ServiceModel.TransactionFlowAttribute> nastavena na <xref:System.ServiceModel.TransactionFlowOption> `NotAllowed`.</span><span class="sxs-lookup"><span data-stu-id="e19cd-136">The `Multiply` request does not flow a transaction to the service because the client's generated definition of the `ICalculator` interface includes a <xref:System.ServiceModel.TransactionFlowAttribute> set to <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span></span>  
  
-   <span data-ttu-id="e19cd-137">`Divide` Požadavek nepostupuje transakce ve službě, protože znovu klienta vygenerovaný definice `ICalculator` rozhraní nezahrnuje `TransactionFlowAttribute`.</span><span class="sxs-lookup"><span data-stu-id="e19cd-137">The `Divide` request does not flow a transaction to the service because again the client's generated definition of the `ICalculator` interface does not include a `TransactionFlowAttribute`.</span></span> <span data-ttu-id="e19cd-138">V rámci oboru jinou transakcí nové a nepřipojené dojde znovu k akcím služby.</span><span class="sxs-lookup"><span data-stu-id="e19cd-138">The service's actions again occur within the scope of another new and unconnected transaction.</span></span>  
  
 <span data-ttu-id="e19cd-139">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="e19cd-139">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e19cd-140">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="e19cd-140">Press ENTER in the client window to shut down the client.</span></span>  
  
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
  
 <span data-ttu-id="e19cd-141">Protokolování žádosti o operaci služby se zobrazí v okně konzoly služby.</span><span class="sxs-lookup"><span data-stu-id="e19cd-141">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="e19cd-142">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="e19cd-142">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 <span data-ttu-id="e19cd-143">Po úspěšném spuštění klienta oboru transakce dokončena a usilujeme o to všechny akce v daném oboru.</span><span class="sxs-lookup"><span data-stu-id="e19cd-143">After a successful execution, the client's transaction scope completes and all actions taken within that scope are committed.</span></span> <span data-ttu-id="e19cd-144">Konkrétně uvedené 5 záznamů se uchovávají v databázi služby.</span><span class="sxs-lookup"><span data-stu-id="e19cd-144">Specifically, the noted 5 records are persisted in the service's database.</span></span> <span data-ttu-id="e19cd-145">První 2 z nich došlo v rámci oboru transakce na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="e19cd-145">The first 2 of these have occurred within the scope of the client's transaction.</span></span>  
  
 <span data-ttu-id="e19cd-146">Pokud došlo k výjimce kdekoli v rámci klienta `TransactionScope` pak transakce nelze dokončit.</span><span class="sxs-lookup"><span data-stu-id="e19cd-146">If an exception occurred anywhere within the client's `TransactionScope` then the transaction cannot complete.</span></span> <span data-ttu-id="e19cd-147">To způsobí, že záznamy, které jsou zaznamenány v daném oboru na nebudou zapíšou do databáze.</span><span class="sxs-lookup"><span data-stu-id="e19cd-147">This causes the records logged within that scope to not be committed to the database.</span></span> <span data-ttu-id="e19cd-148">Tomu můžete dodržovat opakující se ukázku spustit po okomentováním odpovídajícího volání k dokončení vnější `TransactionScope`.</span><span class="sxs-lookup"><span data-stu-id="e19cd-148">This effect can be observed by repeating the sample run after commenting out the call to complete the outer `TransactionScope`.</span></span> <span data-ttu-id="e19cd-149">Na těchto spustit pouze poslední 3 akce (druhého `Subtract`, `Multiply` a `Divide` požadavků) jsou protokolována, protože klientská transakce není tok na ty.</span><span class="sxs-lookup"><span data-stu-id="e19cd-149">On such a run, only the last 3 actions (from the second `Subtract`, the `Multiply` and the `Divide` requests) are logged because the client transaction did not flow to those.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e19cd-150">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="e19cd-150">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e19cd-151">Chcete-li sestavení C# nebo Visual Basic .NET verze řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)</span><span class="sxs-lookup"><span data-stu-id="e19cd-151">To build the C# or Visual Basic .NET version of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)</span></span>  
  
2.  <span data-ttu-id="e19cd-152">Ujistěte se, že jste nainstalovali SQL Server Express Edition nebo SQL Server a že připojovací řetězec správně nastavena v konfiguračním souboru aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="e19cd-152">Ensure that you have installed SQL Server Express Edition or SQL Server, and that the connection string has been correctly set in the service’s application configuration file.</span></span> <span data-ttu-id="e19cd-153">Ke spuštění ukázky bez použití databáze, nastavte `usingSql` hodnoty v konfiguračním souboru aplikace služby k `false`</span><span class="sxs-lookup"><span data-stu-id="e19cd-153">To run the sample without using a database, set the `usingSql` value in the service’s application configuration file to `false`</span></span>  
  
3.  <span data-ttu-id="e19cd-154">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e19cd-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e19cd-155">Pro konfigurace mezi počítači povolte koordinátor distribuovaných transakcí pomocí následujícího postupu a použít nástroj WsatConfig.exe ze sady Windows SDK k povolení podpory síťové transakce WCF.</span><span class="sxs-lookup"><span data-stu-id="e19cd-155">For cross-machine configuration, enable the Distributed Transaction Coordinator using the instructions below, and use the WsatConfig.exe tool from the Windows SDK to enable WCF Transactions network support.</span></span> <span data-ttu-id="e19cd-156">Zobrazit [konfigurace WS-Atomic podpora transakcí](https://go.microsoft.com/fwlink/?LinkId=190370) informace o nastavení WsatConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="e19cd-156">See [Configuring WS-Atomic Transaction Support](https://go.microsoft.com/fwlink/?LinkId=190370) for information on setting up WsatConfig.exe.</span></span>  
  
 <span data-ttu-id="e19cd-157">Zda ukázku spustíte ve stejném počítači nebo na různých počítačích, musíte nakonfigurovat Microsoft distribuované transakce koordinátor (MSDTC) k povolení toku transakcí sítě a nástrojem WsatConfig.exe povolit podporu sítě transakce WCF.</span><span class="sxs-lookup"><span data-stu-id="e19cd-157">Whether you run the sample on the same computer or on different computers, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable WCF transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a><span data-ttu-id="e19cd-158">Konfigurace Microsoft distribuované transakce koordinátor (MSDTC) k podpoře spouštění vzorku</span><span class="sxs-lookup"><span data-stu-id="e19cd-158">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample</span></span>  
  
1.  <span data-ttu-id="e19cd-159">V rámci služby počítače se systémem Windows Server 2003 nebo Windows XP nakonfigurujte MSDTC povolit příchozí síťové transakce podle těchto pokynů.</span><span class="sxs-lookup"><span data-stu-id="e19cd-159">On a service machine running Windows Server 2003 or Windows XP, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1.  <span data-ttu-id="e19cd-160">Z **Start** nabídky, přejděte na **ovládací panely**, pak **nástroje pro správu**a potom **služby Component Services**.</span><span class="sxs-lookup"><span data-stu-id="e19cd-160">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="e19cd-161">Rozbalte **služby Component Services**.</span><span class="sxs-lookup"><span data-stu-id="e19cd-161">Expand **Component Services**.</span></span> <span data-ttu-id="e19cd-162">Otevřít **počítače** složky.</span><span class="sxs-lookup"><span data-stu-id="e19cd-162">Open the **Computers** folder.</span></span>  
  
    3.  <span data-ttu-id="e19cd-163">Klikněte pravým tlačítkem na **tento počítač** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="e19cd-163">Right-click **My Computer** and select **Properties**.</span></span>  
  
    4.  <span data-ttu-id="e19cd-164">Na **MSDTC** klikněte na tlačítko **konfigurace zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="e19cd-164">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    5.  <span data-ttu-id="e19cd-165">Zkontrolujte **DTC přístup k síti** a **povolit příchozí**.</span><span class="sxs-lookup"><span data-stu-id="e19cd-165">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    6.  <span data-ttu-id="e19cd-166">Klikněte na tlačítko **OK**, pak klikněte na tlačítko **Ano** restartování služby MSDTC.</span><span class="sxs-lookup"><span data-stu-id="e19cd-166">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    7.  <span data-ttu-id="e19cd-167">Klikněte na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e19cd-167">Click **OK** to close the dialog box.</span></span>  
  
2.  <span data-ttu-id="e19cd-168">V rámci služby počítače se systémem Windows Server 2008 nebo Windows Vista nakonfigurujte MSDTC povolit příchozí síťové transakce podle těchto pokynů.</span><span class="sxs-lookup"><span data-stu-id="e19cd-168">On a service machine running Windows Server 2008 or Windows Vista, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1.  <span data-ttu-id="e19cd-169">Z **Start** nabídky, přejděte na **ovládací panely**, pak **nástroje pro správu**a potom **služby Component Services**.</span><span class="sxs-lookup"><span data-stu-id="e19cd-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="e19cd-170">Rozbalte **služby Component Services**.</span><span class="sxs-lookup"><span data-stu-id="e19cd-170">Expand **Component Services**.</span></span> <span data-ttu-id="e19cd-171">Otevřít **počítače** složky.</span><span class="sxs-lookup"><span data-stu-id="e19cd-171">Open the **Computers** folder.</span></span> <span data-ttu-id="e19cd-172">Vyberte **koordinátor distribuovaných transakcí**.</span><span class="sxs-lookup"><span data-stu-id="e19cd-172">Select **Distributed Transaction Coordinator**.</span></span>  
  
    3.  <span data-ttu-id="e19cd-173">Klikněte pravým tlačítkem na **Koordinátor DTC** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="e19cd-173">Right-click **DTC Coordinator** and select **Properties**.</span></span>  
  
    4.  <span data-ttu-id="e19cd-174">Na **zabezpečení** kartě **síťový přístup DTC** a **povolit příchozí**.</span><span class="sxs-lookup"><span data-stu-id="e19cd-174">On the **Security** tab, check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5.  <span data-ttu-id="e19cd-175">Klikněte na tlačítko **OK**, pak klikněte na tlačítko **Ano** restartování služby MSDTC.</span><span class="sxs-lookup"><span data-stu-id="e19cd-175">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6.  <span data-ttu-id="e19cd-176">Klikněte na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e19cd-176">Click **OK** to close the dialog box.</span></span>  
  
3.  <span data-ttu-id="e19cd-177">V klientském počítači nakonfigurujte MSDTC povolit odchozí síťové transakce:</span><span class="sxs-lookup"><span data-stu-id="e19cd-177">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1.  <span data-ttu-id="e19cd-178">Z **Start** nabídky, přejděte na `Control Panel`, pak **nástroje pro správu**a potom **služby Component Services**.</span><span class="sxs-lookup"><span data-stu-id="e19cd-178">From the **Start** menu, navigate to `Control Panel`, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="e19cd-179">Klikněte pravým tlačítkem na **tento počítač** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="e19cd-179">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="e19cd-180">Na **MSDTC** klikněte na tlačítko **konfigurace zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="e19cd-180">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4.  <span data-ttu-id="e19cd-181">Zkontrolujte **DTC přístup k síti** a **povolit odchozí**.</span><span class="sxs-lookup"><span data-stu-id="e19cd-181">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5.  <span data-ttu-id="e19cd-182">Klikněte na tlačítko **OK**, pak klikněte na tlačítko **Ano** restartování služby MSDTC.</span><span class="sxs-lookup"><span data-stu-id="e19cd-182">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6.  <span data-ttu-id="e19cd-183">Klikněte na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e19cd-183">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e19cd-184">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="e19cd-184">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e19cd-185">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="e19cd-185">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e19cd-186">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="e19cd-186">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e19cd-187">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e19cd-187">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
