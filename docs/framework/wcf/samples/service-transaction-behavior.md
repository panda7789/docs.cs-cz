---
title: "Chování transakce služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Service Transaction Behavior Sample [Windows Communication Foundation]
ms.assetid: 1a9842a3-e84d-427c-b6ac-6999cbbc2612
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a4c7c9c78b821f7457f193d24bae031d49b301ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="service-transaction-behavior"></a><span data-ttu-id="3f537-102">Chování transakce služby</span><span class="sxs-lookup"><span data-stu-id="3f537-102">Service Transaction Behavior</span></span>
<span data-ttu-id="3f537-103">Tento příklad znázorňuje použití transakce koordinované klienta a nastavení ServiceBehaviorAttribute a OperationBehaviorAttribute pro řízení chování transakce služby.</span><span class="sxs-lookup"><span data-stu-id="3f537-103">This sample demonstrates the use of a client-coordinated transaction and the settings of ServiceBehaviorAttribute and OperationBehaviorAttribute to control service transaction behavior.</span></span> <span data-ttu-id="3f537-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) které implementuje službu kalkulačky, ale je rozšířeno udržování protokolu serveru provádět operace v tabulce databáze a stateful, Mezisoučet pro operace kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="3f537-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service, but is extended to maintain a server log of the performed operations in a database table and a stateful running total for the calculator operations.</span></span> <span data-ttu-id="3f537-105">Trvalý provede zápis do tabulky protokolu serveru jsou závislé na výsledek transakce klienta koordinované -, pokud klientská transakce nedokončí, transakce webové služby zajistí, že nejsou potvrdit aktualizace do databáze.</span><span class="sxs-lookup"><span data-stu-id="3f537-105">Persisted writes to the server log table are dependent upon the outcome of a client coordinated transaction - if the client transaction does not complete, the Web service transaction ensures that the updates to the database are not committed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f537-106">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="3f537-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3f537-107">Kontrakt služby definuje, že všechny operace, vyžadují transakci zalomen s požadavky:</span><span class="sxs-lookup"><span data-stu-id="3f537-107">The contract for the service defines that all of the operations require a transaction to be flowed with requests:</span></span>  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples",  
                    SessionMode = SessionMode.Required)]  
public interface ICalculator  
{  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Add(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Subtract(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Multiply(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Divide(double n);  
}  
```  
  
 <span data-ttu-id="3f537-108">Pokud chcete povolit příchozí tok transakcí, služba nakonfigurovaná pomocí wsHttpBinding poskytované systémem atributem transactionFlow nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="3f537-108">To enable the incoming transaction flow, the service is configured with the system-provided wsHttpBinding with the transactionFlow attribute set to `true`.</span></span> <span data-ttu-id="3f537-109">Tato vazba používá protokol umožňuje vzájemnou spolupráci WSAtomicTransactionOctober2004:</span><span class="sxs-lookup"><span data-stu-id="3f537-109">This binding uses the interoperable WSAtomicTransactionOctober2004 protocol:</span></span>  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="transactionalBinding" transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="3f537-110">Po inicializaci obě připojení služby a transakce, klient přistupuje k několik operací služby v rámci oboru této transakce dokončení transakce a uzavře připojení:</span><span class="sxs-lookup"><span data-stu-id="3f537-110">After initiating both a connection to the service and a transaction, the client accesses several service operations within the scope of that transaction and then completes the transaction and closes the connection:</span></span>  
  
```  
// Create a client  
CalculatorClient client = new CalculatorClient();  
  
// Create a transaction scope with the default isolation level of Serializable  
using (TransactionScope tx = new TransactionScope())  
{  
    Console.WriteLine("Starting transaction");  
  
    // Call the Add service operation.  
    double value = 100.00D;  
    Console.WriteLine("  Adding {0}, running total={1}",  
                                        value, client.Add(value));  
  
    // Call the Subtract service operation.  
    value = 45.00D;  
    Console.WriteLine("  Subtracting {0}, running total={1}",  
                                        value, client.Subtract(value));  
  
    // Call the Multiply service operation.  
    value = 9.00D;  
    Console.WriteLine("  Multiplying by {0}, running total={1}",  
                                        value, client.Multiply(value));  
  
    // Call the Divide service operation.  
    value = 15.00D;  
    Console.WriteLine("  Dividing by {0}, running total={1}",  
                                        value, client.Divide(value));  
  
    Console.WriteLine("  Completing transaction");  
    tx.Complete();  
}  
  
Console.WriteLine("Transaction committed");  
  
// Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
 <span data-ttu-id="3f537-111">Na službu existují tři atributy, které ovlivňují chování transakce služby a k tomu mohou následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="3f537-111">On the service, there are three attributes that affect the service transaction behavior, and they do so in the following ways:</span></span>  
  
-   <span data-ttu-id="3f537-112">Na `ServiceBehaviorAttribute`:</span><span class="sxs-lookup"><span data-stu-id="3f537-112">On the `ServiceBehaviorAttribute`:</span></span>  
  
    -   <span data-ttu-id="3f537-113">`TransactionTimeout` Vlastnost určuje časové období, ve kterém musíte dokončit transakci.</span><span class="sxs-lookup"><span data-stu-id="3f537-113">The `TransactionTimeout` property specifies the time period within which a transaction must complete.</span></span> <span data-ttu-id="3f537-114">V této ukázce je nastavena na 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="3f537-114">In this sample it is set to 30 seconds.</span></span>  
  
    -   <span data-ttu-id="3f537-115">`TransactionIsolationLevel` Vlastnost určuje úroveň izolace, která podporuje službu.</span><span class="sxs-lookup"><span data-stu-id="3f537-115">The `TransactionIsolationLevel` property specifies the isolation level that the service supports.</span></span> <span data-ttu-id="3f537-116">To je nutné tak, aby odpovídaly úroveň izolace klienta.</span><span class="sxs-lookup"><span data-stu-id="3f537-116">This is required to match the client's isolation level.</span></span>  
  
    -   <span data-ttu-id="3f537-117">`ReleaseServiceInstanceOnTransactionComplete` Vlastnost určuje, zda je instance služby recykluje po dokončení transakce.</span><span class="sxs-lookup"><span data-stu-id="3f537-117">The `ReleaseServiceInstanceOnTransactionComplete` property specifies whether the service instance is recycled when a transaction completes.</span></span> <span data-ttu-id="3f537-118">Nastavením na `false`, služba udržuje na stejnou instanci služby napříč požadavky operaci.</span><span class="sxs-lookup"><span data-stu-id="3f537-118">By setting it to `false`, the service maintains the same service instance across the operation requests.</span></span> <span data-ttu-id="3f537-119">To je potřeba k údržbě celkový počet spuštění.</span><span class="sxs-lookup"><span data-stu-id="3f537-119">This is required to maintain the running total.</span></span> <span data-ttu-id="3f537-120">Pokud nastavena na `true`, novou instanci se generuje po každé dokončit akci.</span><span class="sxs-lookup"><span data-stu-id="3f537-120">If set to `true`, a new instance is generated after each completed action.</span></span>  
  
    -   <span data-ttu-id="3f537-121">`TransactionAutoCompleteOnSessionClose` Vlastnost určuje, zda jsou zbývající transakce dokončit po ukončení relace.</span><span class="sxs-lookup"><span data-stu-id="3f537-121">The `TransactionAutoCompleteOnSessionClose` property specifies whether outstanding transactions are completed when the session closes.</span></span> <span data-ttu-id="3f537-122">Nastavením na `false`, je potřeba buď sadu jednotlivé operace `OperationBehaviorAttribute``TransactionAutoComplete` vlastnost, která má `true` nebo explicitně vyžaduje volání `SetTransactionComplete` Metoda dokončení transakcí.</span><span class="sxs-lookup"><span data-stu-id="3f537-122">By setting it to `false`, the individual operations are required to either set the `OperationBehaviorAttribute``TransactionAutoComplete` property to `true` or to explicitly require a call to the `SetTransactionComplete` method to complete transactions.</span></span> <span data-ttu-id="3f537-123">Tento příklad znázorňuje obou přístupů.</span><span class="sxs-lookup"><span data-stu-id="3f537-123">This sample demonstrates both approaches.</span></span>  
  
-   <span data-ttu-id="3f537-124">Na `ServiceContractAttribute`:</span><span class="sxs-lookup"><span data-stu-id="3f537-124">On the `ServiceContractAttribute`:</span></span>  
  
    -   <span data-ttu-id="3f537-125">`SessionMode` Vlastnost určuje, zda služba korelaci příslušných žádostí do logické relace.</span><span class="sxs-lookup"><span data-stu-id="3f537-125">The `SessionMode` property specifies whether the service correlates the appropriate requests into a logical session.</span></span> <span data-ttu-id="3f537-126">Protože tato služba zahrnuje operace, kde je vlastnost OperationBehaviorAttribute TransactionAutoComplete vlastnost nastavena na `false` (násobení a dělení), `SessionMode.Required` musí být zadán.</span><span class="sxs-lookup"><span data-stu-id="3f537-126">Because this service includes operations where the OperationBehaviorAttribute TransactionAutoComplete property is set to `false` (Multiply and Divide), `SessionMode.Required` must be specified.</span></span> <span data-ttu-id="3f537-127">Například násobkem operace nedokončí transakci a místo toho závisí na novější volání dělení dokončit pomocí `SetTransactionComplete` metoda; služby musí být schopní určit, že tyto operace dochází v rámci stejné relace.</span><span class="sxs-lookup"><span data-stu-id="3f537-127">For example, the Multiply operation does not complete its transaction and instead relies upon a later call to Divide to complete using the `SetTransactionComplete` method; the service must be able to determine that these operations are occurring within the same session.</span></span>  
  
-   <span data-ttu-id="3f537-128">Na `OperationBehaviorAttribute`:</span><span class="sxs-lookup"><span data-stu-id="3f537-128">On the `OperationBehaviorAttribute`:</span></span>  
  
    -   <span data-ttu-id="3f537-129">`TransactionScopeRequired` Vlastnost určuje, zda se má provést akce operace v oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="3f537-129">The `TransactionScopeRequired` property specifies whether the operation's actions should be executed within a transaction scope.</span></span> <span data-ttu-id="3f537-130">To je nastaven na `true` pro všechny operace v této ukázkové a, protože klient toků transakci ke všem operacím, dojde k akcím v rámci oboru této transakce klienta.</span><span class="sxs-lookup"><span data-stu-id="3f537-130">This is set to `true` for all operations in this sample and, because the client flows its transaction to all operations, the actions occur within the scope of that client transaction.</span></span>  
  
    -   <span data-ttu-id="3f537-131">`TransactionAutoComplete` Vlastnost určuje, zda transakce, ve kterém metoda spustí automaticky dokončit, pokud dojde k žádné neošetřených výjimek.</span><span class="sxs-lookup"><span data-stu-id="3f537-131">The `TransactionAutoComplete` property specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions occur.</span></span> <span data-ttu-id="3f537-132">Jak se popisuje výš, je nastavena `true` pro operace přidat a Subtract ale `false` Multiply a operace dělení.</span><span class="sxs-lookup"><span data-stu-id="3f537-132">As previously described, this is set to `true` for the Add and Subtract operations but `false` for the Multiply and Divide operations.</span></span> <span data-ttu-id="3f537-133">Přidat a odečíst operace dokončit jejich akce automaticky, Rozděl dokončí svou činnost prostřednictvím explicitní volání `SetTransactionComplete` metoda a Multiply nedokončí jeho akce, ale místo toho závisí na a vyžaduje novější volání, jako třeba Dělení na dokončení akce.</span><span class="sxs-lookup"><span data-stu-id="3f537-133">The Add and Subtract operations complete their actions automatically, the Divide completes its actions through an explicit call to the `SetTransactionComplete` method, and the Multiply does not complete its actions but instead relies upon and requires a later call, such as to Divide, to complete the actions.</span></span>  
  
 <span data-ttu-id="3f537-134">Implementace s atributy služby je následující:</span><span class="sxs-lookup"><span data-stu-id="3f537-134">The attributed service implementation is as follows:</span></span>  
  
```  
[ServiceBehavior(  
    TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,  
    TransactionTimeout = "00:00:30",  
    ReleaseServiceInstanceOnTransactionComplete = false,  
    TransactionAutoCompleteOnSessionClose = false)]  
public class CalculatorService : ICalculator  
{  
    double runningTotal;  
  
    public CalculatorService()  
    {  
        Console.WriteLine("Creating new service instance...");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public double Add(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n, runningTotal));  
        runningTotal = runningTotal + n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public double Subtract(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n, runningTotal));  
        runningTotal = runningTotal - n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]  
    public double Multiply(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", runningTotal, n));  
        runningTotal = runningTotal * n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]  
    public double Divide(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", runningTotal, n));  
        runningTotal = runningTotal / n;  
        OperationContext.Current.SetTransactionComplete();  
        return runningTotal;  
    }  
  
    // Logging method ommitted for brevity  
}   
```  
  
 <span data-ttu-id="3f537-135">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="3f537-135">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3f537-136">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="3f537-136">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Starting transaction  
Performing calculations...  
  Adding 100, running total=100  
  Subtracting 45, running total=55  
  Multiplying by 9, running total=495  
  Dividing by 15, running total=33  
  Completing transaction  
Transaction committed  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="3f537-137">Protokolování žádosti o operaci služby se zobrazí v okně konzoly služby.</span><span class="sxs-lookup"><span data-stu-id="3f537-137">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="3f537-138">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="3f537-138">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate service.  
Creating new service instance...  
  Writing row 1 to database: Adding 100 to 0  
  Writing row 2 to database: Subtracting 45 from 100  
  Writing row 3 to database: Multiplying 55 by 9  
  Writing row 4 to database: Dividing 495 by 15  
```  
  
 <span data-ttu-id="3f537-139">Všimněte si, že kromě zachování spuštění celkový výpočtů, služby hlášení vytvoření instance (jedna instance pro tuto ukázku) a protokoly operaci žádosti do databáze.</span><span class="sxs-lookup"><span data-stu-id="3f537-139">Note that in addition to keeping the running total of the calculations, the service reports the creation of instances (one instance for this sample) and logs the operation requests to a database.</span></span> <span data-ttu-id="3f537-140">Vzhledem k tomu, že všechny žádosti toku transakcí klienta, jakákoli chyba k provedení této transakce výsledkem všechny operace databáze, je vrácena zpět.</span><span class="sxs-lookup"><span data-stu-id="3f537-140">Because all of the requests flow the client's transaction, any failure to complete that transaction results in all of the database operations being rolled back.</span></span> <span data-ttu-id="3f537-141">To prokázat u mnoha různými způsoby:</span><span class="sxs-lookup"><span data-stu-id="3f537-141">This can be demonstrated in a number of ways:</span></span>  
  
-   <span data-ttu-id="3f537-142">Komentář volání klienta `tx.Complete`() a poté spusťte znovu - výsledkem klienta ukončení oboru transakce bez dokončení transakci.</span><span class="sxs-lookup"><span data-stu-id="3f537-142">Comment out the client's call to `tx.Complete`() and rerun - this results in the client exiting the transaction scope without completing its transaction.</span></span>  
  
-   <span data-ttu-id="3f537-143">Komentář out volání operace služby dělení – tento výsledky brání provedení akce zahájili dokončení operace násobení a proto transakce klienta konečném důsledku také nepodaří dokončit.</span><span class="sxs-lookup"><span data-stu-id="3f537-143">Comment out the call to the Divide service operation - this results prevent the action initiated by the Multiply operation from completing and thus the client's transaction ultimately also fails to complete.</span></span>  
  
-   <span data-ttu-id="3f537-144">Throw k neošetřené výjimce kdekoli v oboru transakce klienta – podobně zabrání klientovi dokončení transakci.</span><span class="sxs-lookup"><span data-stu-id="3f537-144">Throw an unhandled exception anywhere in the client's transaction scope - this similarly prevents the client from completing its transaction.</span></span>  
  
 <span data-ttu-id="3f537-145">Výsledek některý z těchto je, že žádná operací provést v rámci tohoto oboru není potvrzena a počtu řádků uchovány v databázi není zvýšit.</span><span class="sxs-lookup"><span data-stu-id="3f537-145">The result of any of these is that none of the operations performed within that scope are committed and the count of rows persisted to the database do not increment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f537-146">Jako součást procesu sestavení databázový soubor zkopírován do složky bin.</span><span class="sxs-lookup"><span data-stu-id="3f537-146">As part of the build process the database file is copied to the bin folder.</span></span> <span data-ttu-id="3f537-147">Musí se podíváte na tuto kopii souboru databáze sledovat na řádky, které jsou nastavené jako trvalé do protokolu, nikoli soubor, který je zahrnutý v projektu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3f537-147">You must look at that copy of the database file to observe the rows that are persisted to the log rather than the file that is included in the Visual Studio project.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3f537-148">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="3f537-148">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3f537-149">Ujistěte se, že jste nainstalovali SQL Server 2005 Express Edition nebo SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="3f537-149">Ensure that you have installed SQL Server 2005 Express Edition or SQL Server 2005.</span></span> <span data-ttu-id="3f537-150">V souboru App.config služby, databázi `connectionString` může být sada nebo databázi interakce mohou být zakázány nastavením appSettings `usingSql` hodnotu `false`.</span><span class="sxs-lookup"><span data-stu-id="3f537-150">In the service's App.config file, the database `connectionString` may be set or the database interactions may be disabled by setting the appSettings `usingSql` value to `false`.</span></span>  
  
2.  <span data-ttu-id="3f537-151">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3f537-151">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="3f537-152">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3f537-152">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="3f537-153">Pokud spustíte ukázku mezi počítači, musíte nakonfigurovat Microsoft distribuované transakce koordinátora služba MSDTC () k povolení toku transakcí sítě a pomocí nástroje WsatConfig.exe povolit [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] transakce sítě podpory.</span><span class="sxs-lookup"><span data-stu-id="3f537-153">If you run the sample across machines, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a><span data-ttu-id="3f537-154">Konfigurace Microsoft distribuované transakce koordinátora služba MSDTC () k podpoře spouštění vzorku mezi počítači</span><span class="sxs-lookup"><span data-stu-id="3f537-154">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample across machines</span></span>  
  
1.  <span data-ttu-id="3f537-155">Na počítači služby konfigurace služby MS DTC povolit příchozí transakce sítě.</span><span class="sxs-lookup"><span data-stu-id="3f537-155">On the service machine, configure MSDTC to allow incoming network transactions.</span></span>  
  
    1.  <span data-ttu-id="3f537-156">Z **spustit** nabídky, přejděte na **ovládací panely**, pak **nástroje pro správu**a potom **služby komponent**.</span><span class="sxs-lookup"><span data-stu-id="3f537-156">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="3f537-157">Klikněte pravým tlačítkem na **Můj počítač** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="3f537-157">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="3f537-158">Na **služby MSDTC** , klikněte na **konfigurace zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="3f537-158">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4.  <span data-ttu-id="3f537-159">Zkontrolujte **síťový přístup DTC** a **povolit příchozí**.</span><span class="sxs-lookup"><span data-stu-id="3f537-159">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5.  <span data-ttu-id="3f537-160">Klikněte na tlačítko **Ano** restartujte službu MS DTC a potom klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="3f537-160">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>  
  
    6.  <span data-ttu-id="3f537-161">Klikněte na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="3f537-161">Click **OK** to close the dialog box.</span></span>  
  
2.  <span data-ttu-id="3f537-162">V počítači služby a klientský počítač konfigurace brány Windows Firewall Microsoft distribuované transakce koordinátora služba MSDTC () do seznamu vyloučení aplikace zahrnout:</span><span class="sxs-lookup"><span data-stu-id="3f537-162">On the service machine and the client machine, configure the Windows Firewall to include the Microsoft Distributed Transaction Coordinator (MSDTC) to the list of excepted applications:</span></span>  
  
    1.  <span data-ttu-id="3f537-163">Spusťte aplikaci brána Windows Firewall v Ovládacích panelech.</span><span class="sxs-lookup"><span data-stu-id="3f537-163">Run the Windows Firewall application from Control Panel.</span></span>  
  
    2.  <span data-ttu-id="3f537-164">Z **výjimky** , klikněte na **přidat Program**.</span><span class="sxs-lookup"><span data-stu-id="3f537-164">From the **Exceptions** tab, click **Add Program**.</span></span>  
  
    3.  <span data-ttu-id="3f537-165">Přejděte do složky C:\WINDOWS\System32.</span><span class="sxs-lookup"><span data-stu-id="3f537-165">Browse to the folder C:\WINDOWS\System32.</span></span>  
  
    4.  <span data-ttu-id="3f537-166">Vyberte Msdtc.exe a klikněte na **otevřete**.</span><span class="sxs-lookup"><span data-stu-id="3f537-166">Select Msdtc.exe and click **Open**.</span></span>  
  
    5.  <span data-ttu-id="3f537-167">Klikněte na tlačítko **OK** zavřete **přidat Program** dialogové okno a klikněte na tlačítko **OK** zavřete apletu brány Windows Firewall.</span><span class="sxs-lookup"><span data-stu-id="3f537-167">Click **OK** to close the **Add Program** dialog box, and click **OK** again to close the Windows Firewall applet.</span></span>  
  
3.  <span data-ttu-id="3f537-168">V klientském počítači nakonfigurujte služby MSDTC povolit odchozí transakce sítě:</span><span class="sxs-lookup"><span data-stu-id="3f537-168">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1.  <span data-ttu-id="3f537-169">Z **spustit** nabídky, přejděte na **ovládací panely**, pak **nástroje pro správu**a potom **služby komponent**.</span><span class="sxs-lookup"><span data-stu-id="3f537-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="3f537-170">Klikněte pravým tlačítkem na **Můj počítač** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="3f537-170">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="3f537-171">Na **služby MSDTC** , klikněte na **konfigurace zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="3f537-171">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4.  <span data-ttu-id="3f537-172">Zkontrolujte **síťový přístup DTC** a **povolit odchozí**.</span><span class="sxs-lookup"><span data-stu-id="3f537-172">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5.  <span data-ttu-id="3f537-173">Klikněte na tlačítko **Ano** restartujte službu MS DTC a potom klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="3f537-173">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>  
  
    6.  <span data-ttu-id="3f537-174">Klikněte na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="3f537-174">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3f537-175">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="3f537-175">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3f537-176">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="3f537-176">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3f537-177">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="3f537-177">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3f537-178">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="3f537-178">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`  
  
## <a name="see-also"></a><span data-ttu-id="3f537-179">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f537-179">See Also</span></span>
