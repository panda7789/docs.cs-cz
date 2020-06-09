---
title: Chování transakce služby
ms.date: 03/30/2017
helpviewer_keywords:
- Service Transaction Behavior Sample [Windows Communication Foundation]
ms.assetid: 1a9842a3-e84d-427c-b6ac-6999cbbc2612
ms.openlocfilehash: 0be5bf0dbe6416febb898fb5150c5a516c8b0969
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591524"
---
# <a name="service-transaction-behavior"></a><span data-ttu-id="08626-102">Chování transakce služby</span><span class="sxs-lookup"><span data-stu-id="08626-102">Service Transaction Behavior</span></span>

<span data-ttu-id="08626-103">Tato ukázka demonstruje použití transakce s koordinovaným klientem a nastavení atributu ServiceBehaviorAttribute a OperationBehaviorAttribute pro řízení chování transakce služby.</span><span class="sxs-lookup"><span data-stu-id="08626-103">This sample demonstrates the use of a client-coordinated transaction and the settings of ServiceBehaviorAttribute and OperationBehaviorAttribute to control service transaction behavior.</span></span> <span data-ttu-id="08626-104">Tato ukázka je založena na [Začínáme](getting-started-sample.md) , která implementuje službu kalkulačky, ale je rozšířena tak, aby udržovala protokol serveru provedených operací v tabulce databáze a stavový Mezisoučet pro operace kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="08626-104">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service, but is extended to maintain a server log of the performed operations in a database table and a stateful running total for the calculator operations.</span></span> <span data-ttu-id="08626-105">Trvalé zápisy do tabulky protokolu serveru jsou závislé na výsledku klientské transakce, Pokud klientská transakce není dokončena, transakce webové služby zajistí, že aktualizace databáze nebudou potvrzeny.</span><span class="sxs-lookup"><span data-stu-id="08626-105">Persisted writes to the server log table are dependent upon the outcome of a client coordinated transaction - if the client transaction does not complete, the Web service transaction ensures that the updates to the database are not committed.</span></span>

> [!NOTE]
> <span data-ttu-id="08626-106">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="08626-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="08626-107">Smlouva pro službu definuje, že všechny operace vyžadují, aby transakce byly předávány s požadavky:</span><span class="sxs-lookup"><span data-stu-id="08626-107">The contract for the service defines that all of the operations require a transaction to be flowed with requests:</span></span>

```csharp
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

<span data-ttu-id="08626-108">Chcete-li povolit tok příchozích transakcí, je služba konfigurována se systémem poskytnutým systémem wsHttpBinding s atributem transactionFlow nastaveným na hodnotu `true` .</span><span class="sxs-lookup"><span data-stu-id="08626-108">To enable the incoming transaction flow, the service is configured with the system-provided wsHttpBinding with the transactionFlow attribute set to `true`.</span></span> <span data-ttu-id="08626-109">Tato vazba používá interoperabilní protokol WSAtomicTransactionOctober2004:</span><span class="sxs-lookup"><span data-stu-id="08626-109">This binding uses the interoperable WSAtomicTransactionOctober2004 protocol:</span></span>

```xml
<bindings>
  <wsHttpBinding>
    <binding name="transactionalBinding" transactionFlow="true" />
  </wsHttpBinding>
</bindings>
```

<span data-ttu-id="08626-110">Po zahájení připojení ke službě i k transakci klient přistupuje k několika operacím služby v rámci této transakce a pak dokončí transakci a ukončí připojení:</span><span class="sxs-lookup"><span data-stu-id="08626-110">After initiating both a connection to the service and a transaction, the client accesses several service operations within the scope of that transaction and then completes the transaction and closes the connection:</span></span>

```csharp
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

<span data-ttu-id="08626-111">Ve službě existují tři atributy, které mají vliv na chování transakce služby a mají tak následující možnosti:</span><span class="sxs-lookup"><span data-stu-id="08626-111">On the service, there are three attributes that affect the service transaction behavior, and they do so in the following ways:</span></span>

- <span data-ttu-id="08626-112">V `ServiceBehaviorAttribute` :</span><span class="sxs-lookup"><span data-stu-id="08626-112">On the `ServiceBehaviorAttribute`:</span></span>

  - <span data-ttu-id="08626-113">`TransactionTimeout`Vlastnost určuje časové období, během kterého musí být transakce dokončena.</span><span class="sxs-lookup"><span data-stu-id="08626-113">The `TransactionTimeout` property specifies the time period within which a transaction must complete.</span></span> <span data-ttu-id="08626-114">V této ukázce je nastavená na 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="08626-114">In this sample it is set to 30 seconds.</span></span>

  - <span data-ttu-id="08626-115">`TransactionIsolationLevel`Vlastnost určuje úroveň izolace, kterou služba podporuje.</span><span class="sxs-lookup"><span data-stu-id="08626-115">The `TransactionIsolationLevel` property specifies the isolation level that the service supports.</span></span> <span data-ttu-id="08626-116">To je nutné, aby se shodovala s úrovní izolace klienta.</span><span class="sxs-lookup"><span data-stu-id="08626-116">This is required to match the client's isolation level.</span></span>

  - <span data-ttu-id="08626-117">`ReleaseServiceInstanceOnTransactionComplete`Vlastnost určuje, zda je instance služby recyklována při dokončení transakce.</span><span class="sxs-lookup"><span data-stu-id="08626-117">The `ReleaseServiceInstanceOnTransactionComplete` property specifies whether the service instance is recycled when a transaction completes.</span></span> <span data-ttu-id="08626-118">Když ji nastavíte na `false` , služba udržuje v rámci požadavků na operaci stejnou instanci služby.</span><span class="sxs-lookup"><span data-stu-id="08626-118">By setting it to `false`, the service maintains the same service instance across the operation requests.</span></span> <span data-ttu-id="08626-119">To je nutné pro udržení průběžného součtu.</span><span class="sxs-lookup"><span data-stu-id="08626-119">This is required to maintain the running total.</span></span> <span data-ttu-id="08626-120">Pokud je nastavena na `true` , nová instance se vygeneruje po každé dokončené akci.</span><span class="sxs-lookup"><span data-stu-id="08626-120">If set to `true`, a new instance is generated after each completed action.</span></span>

  - <span data-ttu-id="08626-121">`TransactionAutoCompleteOnSessionClose`Vlastnost určuje, zda jsou nevyřízené transakce dokončeny při zavření relace.</span><span class="sxs-lookup"><span data-stu-id="08626-121">The `TransactionAutoCompleteOnSessionClose` property specifies whether outstanding transactions are completed when the session closes.</span></span> <span data-ttu-id="08626-122">Nastavením na je `false` nutné jednotlivé operace buď nastavit <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete?displayProperty=nameWithType> vlastnost na `true` nebo explicitně vyžadovat volání <xref:System.ServiceModel.OperationContext.SetTransactionComplete?displayProperty=nameWithType> metody k dokončení transakcí.</span><span class="sxs-lookup"><span data-stu-id="08626-122">By setting it to `false`, the individual operations are required to either set the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete?displayProperty=nameWithType> property to `true` or to explicitly require a call to the <xref:System.ServiceModel.OperationContext.SetTransactionComplete?displayProperty=nameWithType> method to complete transactions.</span></span> <span data-ttu-id="08626-123">Tato ukázka ukazuje oba přístupy.</span><span class="sxs-lookup"><span data-stu-id="08626-123">This sample demonstrates both approaches.</span></span>

- <span data-ttu-id="08626-124">V `ServiceContractAttribute` :</span><span class="sxs-lookup"><span data-stu-id="08626-124">On the `ServiceContractAttribute`:</span></span>

  - <span data-ttu-id="08626-125">`SessionMode`Vlastnost určuje, zda služba koreluje příslušné požadavky do logické relace.</span><span class="sxs-lookup"><span data-stu-id="08626-125">The `SessionMode` property specifies whether the service correlates the appropriate requests into a logical session.</span></span> <span data-ttu-id="08626-126">Vzhledem k tomu, že tato služba zahrnuje operace, na kterých je vlastnost TransactionAutoComplete OperationBehaviorAttribute nastavena na `false` (vynásobení a dělení), `SessionMode.Required` musí být zadána.</span><span class="sxs-lookup"><span data-stu-id="08626-126">Because this service includes operations where the OperationBehaviorAttribute TransactionAutoComplete property is set to `false` (Multiply and Divide), `SessionMode.Required` must be specified.</span></span> <span data-ttu-id="08626-127">Například operace násobení nedokončila svoji transakci a místo toho spoléhá na pozdější volání metody k dokončení pomocí `SetTransactionComplete` metody; služba musí být schopna určit, že se tyto operace vyskytují v rámci stejné relace.</span><span class="sxs-lookup"><span data-stu-id="08626-127">For example, the Multiply operation does not complete its transaction and instead relies upon a later call to Divide to complete using the `SetTransactionComplete` method; the service must be able to determine that these operations are occurring within the same session.</span></span>

- <span data-ttu-id="08626-128">V `OperationBehaviorAttribute` :</span><span class="sxs-lookup"><span data-stu-id="08626-128">On the `OperationBehaviorAttribute`:</span></span>

  - <span data-ttu-id="08626-129">`TransactionScopeRequired`Vlastnost určuje, zda mají být akce operace provedeny v rámci oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="08626-129">The `TransactionScopeRequired` property specifies whether the operation's actions should be executed within a transaction scope.</span></span> <span data-ttu-id="08626-130">To je nastaveno na hodnotu `true` pro všechny operace v této ukázce a, protože klient natéká svou transakci na všechny operace, k akcím dochází v rámci této transakce klienta.</span><span class="sxs-lookup"><span data-stu-id="08626-130">This is set to `true` for all operations in this sample and, because the client flows its transaction to all operations, the actions occur within the scope of that client transaction.</span></span>

  - <span data-ttu-id="08626-131">`TransactionAutoComplete`Vlastnost určuje, zda transakce, ve které je metoda spuštěna, je automaticky dokončena, pokud nedojde k žádným neošetřeným výjimkám.</span><span class="sxs-lookup"><span data-stu-id="08626-131">The `TransactionAutoComplete` property specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions occur.</span></span> <span data-ttu-id="08626-132">Jak je uvedeno výše, je nastavena na `true` pro operace sčítání a odečítání, ale `false` pro operace vynásobení a dělení.</span><span class="sxs-lookup"><span data-stu-id="08626-132">As previously described, this is set to `true` for the Add and Subtract operations but `false` for the Multiply and Divide operations.</span></span> <span data-ttu-id="08626-133">Operace sčítání a odečítání dokončují své akce automaticky, dělení dokončí své akce prostřednictvím explicitního volání `SetTransactionComplete` metody a násobení nedokončuje své akce, ale místo toho se spoléhá na a vyžaduje pozdější volání, například k rozdělení, aby se akce dokončily.</span><span class="sxs-lookup"><span data-stu-id="08626-133">The Add and Subtract operations complete their actions automatically, the Divide completes its actions through an explicit call to the `SetTransactionComplete` method, and the Multiply does not complete its actions but instead relies upon and requires a later call, such as to Divide, to complete the actions.</span></span>

<span data-ttu-id="08626-134">Implementací služby s atributy je následující:</span><span class="sxs-lookup"><span data-stu-id="08626-134">The attributed service implementation is as follows:</span></span>

```csharp
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

    // Logging method omitted for brevity
}
```

<span data-ttu-id="08626-135">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="08626-135">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="08626-136">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="08626-136">Press ENTER in the client window to shut down the client.</span></span>

```console
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

<span data-ttu-id="08626-137">Protokolování požadavků na operace služby se zobrazí v okně konzoly služby.</span><span class="sxs-lookup"><span data-stu-id="08626-137">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="08626-138">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="08626-138">Press ENTER in the client window to shut down the client.</span></span>

```console
Press <ENTER> to terminate service.
Creating new service instance...
  Writing row 1 to database: Adding 100 to 0
  Writing row 2 to database: Subtracting 45 from 100
  Writing row 3 to database: Multiplying 55 by 9
  Writing row 4 to database: Dividing 495 by 15
```

<span data-ttu-id="08626-139">Všimněte si, že kromě udržování průběžného součtu výpočtů služba oznamuje vytváření instancí (jednu instanci pro tuto ukázku) a zaznamená požadavky na operace do databáze.</span><span class="sxs-lookup"><span data-stu-id="08626-139">Note that in addition to keeping the running total of the calculations, the service reports the creation of instances (one instance for this sample) and logs the operation requests to a database.</span></span> <span data-ttu-id="08626-140">Vzhledem k tomu, že všechny požadavky mají za následek transakci klienta, jakékoli neúspěšné dokončení této transakce způsobí všechny operace v databázi vracené zpět.</span><span class="sxs-lookup"><span data-stu-id="08626-140">Because all of the requests flow the client's transaction, any failure to complete that transaction results in all of the database operations being rolled back.</span></span> <span data-ttu-id="08626-141">To může být ukázáno několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="08626-141">This can be demonstrated in a number of ways:</span></span>

- <span data-ttu-id="08626-142">Odkomentujte volání klienta `tx.Complete` () a spusťte akci znovu. výsledkem bude, že klient ukončí obor transakce bez dokončení transakce.</span><span class="sxs-lookup"><span data-stu-id="08626-142">Comment out the client's call to `tx.Complete`() and rerun - this results in the client exiting the transaction scope without completing its transaction.</span></span>

- <span data-ttu-id="08626-143">Odkomentujte volání operace dělení – tento výsledek zabrání dokončení akce iniciované operací vynásobení, takže transakce klienta nakonec nebude také dokončena.</span><span class="sxs-lookup"><span data-stu-id="08626-143">Comment out the call to the Divide service operation - this results prevent the action initiated by the Multiply operation from completing and thus the client's transaction ultimately also fails to complete.</span></span>

- <span data-ttu-id="08626-144">Vyvolat neošetřenou výjimku kdekoli v oboru transakce klienta – to podobně zabrání klientovi v dokončení transakce.</span><span class="sxs-lookup"><span data-stu-id="08626-144">Throw an unhandled exception anywhere in the client's transaction scope - this similarly prevents the client from completing its transaction.</span></span>

<span data-ttu-id="08626-145">Výsledkem kterékoli z nich je, že žádná operace prováděná v rámci tohoto oboru není potvrzena a počet řádků trvalých do databáze se nezvyšuje.</span><span class="sxs-lookup"><span data-stu-id="08626-145">The result of any of these is that none of the operations performed within that scope are committed and the count of rows persisted to the database do not increment.</span></span>

> [!NOTE]
> <span data-ttu-id="08626-146">V rámci procesu sestavení se databázový soubor zkopíruje do složky bin.</span><span class="sxs-lookup"><span data-stu-id="08626-146">As part of the build process the database file is copied to the bin folder.</span></span> <span data-ttu-id="08626-147">Aby bylo možné sledovat řádky, které jsou uchovány v protokolu, nikoli soubor, který je součástí projektu sady Visual Studio, je nutné se podívat na tuto kopii databázového souboru.</span><span class="sxs-lookup"><span data-stu-id="08626-147">You must look at that copy of the database file to observe the rows that are persisted to the log rather than the file that is included in the Visual Studio project.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="08626-148">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="08626-148">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="08626-149">Ujistěte se, že máte nainstalovanou SQL Server 2005 Express Edition nebo SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="08626-149">Ensure that you have installed SQL Server 2005 Express Edition or SQL Server 2005.</span></span> <span data-ttu-id="08626-150">V souboru App. config služby `connectionString` může být databáze nastavena nebo je možné zakázat interakce databáze nastavením `usingSql` hodnoty appSettings na `false` .</span><span class="sxs-lookup"><span data-stu-id="08626-150">In the service's App.config file, the database `connectionString` may be set or the database interactions may be disabled by setting the appSettings `usingSql` value to `false`.</span></span>

2. <span data-ttu-id="08626-151">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="08626-151">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="08626-152">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="08626-152">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

<span data-ttu-id="08626-153">Pokud spustíte ukázku napříč počítači, je nutné nakonfigurovat službu Microsoft DTC (Distributed Transaction Coordinator) (MSDTC), aby povolovala tok síťových transakcí, a pomocí nástroje WsatConfig. exe povolit transakce služby Windows Communication Foundation (WCF) pro podporu sítě.</span><span class="sxs-lookup"><span data-stu-id="08626-153">If you run the sample across machines, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable Windows Communication Foundation (WCF) transactions network support.</span></span>

### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a><span data-ttu-id="08626-154">Konfigurace služby Microsoft DTC (Distributed Transaction Coordinator) (MSDTC) pro podporu spuštění ukázky napříč počítači</span><span class="sxs-lookup"><span data-stu-id="08626-154">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample across machines</span></span>

1. <span data-ttu-id="08626-155">Na počítači služby nakonfigurujte MSDTC tak, aby povoloval příchozí síťové transakce.</span><span class="sxs-lookup"><span data-stu-id="08626-155">On the service machine, configure MSDTC to allow incoming network transactions.</span></span>

    1. <span data-ttu-id="08626-156">V nabídce **Start** přejděte na **Ovládací panely**, klikněte na **Nástroje pro správu**a pak na **služby komponent**.</span><span class="sxs-lookup"><span data-stu-id="08626-156">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>

    2. <span data-ttu-id="08626-157">Pravým tlačítkem myši klikněte na položku **Tento počítač** a vyberte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="08626-157">Right-click **My Computer** and select **Properties**.</span></span>

    3. <span data-ttu-id="08626-158">Na kartě **MSDTC** klikněte na **Konfigurace zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="08626-158">On the **MSDTC** tab, click **Security Configuration**.</span></span>

    4. <span data-ttu-id="08626-159">Ověřte **přístup k síťovému DTC** a **povolte příchozí**.</span><span class="sxs-lookup"><span data-stu-id="08626-159">Check **Network DTC Access** and **Allow Inbound**.</span></span>

    5. <span data-ttu-id="08626-160">Kliknutím na tlačítko **Ano** restartujte službu MS DTC a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="08626-160">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>

    6. <span data-ttu-id="08626-161">Kliknutím na **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="08626-161">Click **OK** to close the dialog box.</span></span>

2. <span data-ttu-id="08626-162">Na počítači služby a klientském počítači nakonfigurujte bránu Windows Firewall tak, aby zahrnovala Microsoft DTC (Distributed Transaction Coordinator) (MSDTC) do seznamu s výjimkou aplikací:</span><span class="sxs-lookup"><span data-stu-id="08626-162">On the service machine and the client machine, configure the Windows Firewall to include the Microsoft Distributed Transaction Coordinator (MSDTC) to the list of excepted applications:</span></span>

    1. <span data-ttu-id="08626-163">Spusťte aplikaci brány Windows Firewall z ovládacích panelů.</span><span class="sxs-lookup"><span data-stu-id="08626-163">Run the Windows Firewall application from Control Panel.</span></span>

    2. <span data-ttu-id="08626-164">Na kartě **výjimky** klikněte na **Přidat program**.</span><span class="sxs-lookup"><span data-stu-id="08626-164">From the **Exceptions** tab, click **Add Program**.</span></span>

    3. <span data-ttu-id="08626-165">Přejděte do složky C:\WINDOWS\System32.</span><span class="sxs-lookup"><span data-stu-id="08626-165">Browse to the folder C:\WINDOWS\System32.</span></span>

    4. <span data-ttu-id="08626-166">Vyberte MSDTC. exe a klikněte na **otevřít**.</span><span class="sxs-lookup"><span data-stu-id="08626-166">Select Msdtc.exe and click **Open**.</span></span>

    5. <span data-ttu-id="08626-167">Kliknutím na tlačítko **OK** zavřete dialogové okno **Přidat program** a dalším kliknutím na tlačítko **OK** zavřete aplet brány Windows Firewall.</span><span class="sxs-lookup"><span data-stu-id="08626-167">Click **OK** to close the **Add Program** dialog box, and click **OK** again to close the Windows Firewall applet.</span></span>

3. <span data-ttu-id="08626-168">Na klientském počítači nakonfigurujte koordinátor MSDTC tak, aby povoloval odchozí síťové transakce:</span><span class="sxs-lookup"><span data-stu-id="08626-168">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>

    1. <span data-ttu-id="08626-169">V nabídce **Start** přejděte na **Ovládací panely**, klikněte na **Nástroje pro správu**a pak na **služby komponent**.</span><span class="sxs-lookup"><span data-stu-id="08626-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>

    2. <span data-ttu-id="08626-170">Pravým tlačítkem myši klikněte na položku **Tento počítač** a vyberte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="08626-170">Right-click **My Computer** and select **Properties**.</span></span>

    3. <span data-ttu-id="08626-171">Na kartě **MSDTC** klikněte na **Konfigurace zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="08626-171">On the **MSDTC** tab, click **Security Configuration**.</span></span>

    4. <span data-ttu-id="08626-172">Ověřte **přístup k síťovému DTC** a **Povolte odchozí**.</span><span class="sxs-lookup"><span data-stu-id="08626-172">Check **Network DTC Access** and **Allow Outbound**.</span></span>

    5. <span data-ttu-id="08626-173">Kliknutím na tlačítko **Ano** restartujte službu MS DTC a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="08626-173">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>

    6. <span data-ttu-id="08626-174">Kliknutím na **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="08626-174">Click **OK** to close the dialog box.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="08626-175">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="08626-175">The samples may already be installed on your machine.</span></span> <span data-ttu-id="08626-176">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="08626-176">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="08626-177">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="08626-177">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="08626-178">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="08626-178">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`
