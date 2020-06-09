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
# <a name="service-transaction-behavior"></a>Chování transakce služby

Tato ukázka demonstruje použití transakce s koordinovaným klientem a nastavení atributu ServiceBehaviorAttribute a OperationBehaviorAttribute pro řízení chování transakce služby. Tato ukázka je založena na [Začínáme](getting-started-sample.md) , která implementuje službu kalkulačky, ale je rozšířena tak, aby udržovala protokol serveru provedených operací v tabulce databáze a stavový Mezisoučet pro operace kalkulačky. Trvalé zápisy do tabulky protokolu serveru jsou závislé na výsledku klientské transakce, Pokud klientská transakce není dokončena, transakce webové služby zajistí, že aktualizace databáze nebudou potvrzeny.

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

Smlouva pro službu definuje, že všechny operace vyžadují, aby transakce byly předávány s požadavky:

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

Chcete-li povolit tok příchozích transakcí, je služba konfigurována se systémem poskytnutým systémem wsHttpBinding s atributem transactionFlow nastaveným na hodnotu `true` . Tato vazba používá interoperabilní protokol WSAtomicTransactionOctober2004:

```xml
<bindings>
  <wsHttpBinding>
    <binding name="transactionalBinding" transactionFlow="true" />
  </wsHttpBinding>
</bindings>
```

Po zahájení připojení ke službě i k transakci klient přistupuje k několika operacím služby v rámci této transakce a pak dokončí transakci a ukončí připojení:

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

Ve službě existují tři atributy, které mají vliv na chování transakce služby a mají tak následující možnosti:

- V `ServiceBehaviorAttribute` :

  - `TransactionTimeout`Vlastnost určuje časové období, během kterého musí být transakce dokončena. V této ukázce je nastavená na 30 sekund.

  - `TransactionIsolationLevel`Vlastnost určuje úroveň izolace, kterou služba podporuje. To je nutné, aby se shodovala s úrovní izolace klienta.

  - `ReleaseServiceInstanceOnTransactionComplete`Vlastnost určuje, zda je instance služby recyklována při dokončení transakce. Když ji nastavíte na `false` , služba udržuje v rámci požadavků na operaci stejnou instanci služby. To je nutné pro udržení průběžného součtu. Pokud je nastavena na `true` , nová instance se vygeneruje po každé dokončené akci.

  - `TransactionAutoCompleteOnSessionClose`Vlastnost určuje, zda jsou nevyřízené transakce dokončeny při zavření relace. Nastavením na je `false` nutné jednotlivé operace buď nastavit <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete?displayProperty=nameWithType> vlastnost na `true` nebo explicitně vyžadovat volání <xref:System.ServiceModel.OperationContext.SetTransactionComplete?displayProperty=nameWithType> metody k dokončení transakcí. Tato ukázka ukazuje oba přístupy.

- V `ServiceContractAttribute` :

  - `SessionMode`Vlastnost určuje, zda služba koreluje příslušné požadavky do logické relace. Vzhledem k tomu, že tato služba zahrnuje operace, na kterých je vlastnost TransactionAutoComplete OperationBehaviorAttribute nastavena na `false` (vynásobení a dělení), `SessionMode.Required` musí být zadána. Například operace násobení nedokončila svoji transakci a místo toho spoléhá na pozdější volání metody k dokončení pomocí `SetTransactionComplete` metody; služba musí být schopna určit, že se tyto operace vyskytují v rámci stejné relace.

- V `OperationBehaviorAttribute` :

  - `TransactionScopeRequired`Vlastnost určuje, zda mají být akce operace provedeny v rámci oboru transakce. To je nastaveno na hodnotu `true` pro všechny operace v této ukázce a, protože klient natéká svou transakci na všechny operace, k akcím dochází v rámci této transakce klienta.

  - `TransactionAutoComplete`Vlastnost určuje, zda transakce, ve které je metoda spuštěna, je automaticky dokončena, pokud nedojde k žádným neošetřeným výjimkám. Jak je uvedeno výše, je nastavena na `true` pro operace sčítání a odečítání, ale `false` pro operace vynásobení a dělení. Operace sčítání a odečítání dokončují své akce automaticky, dělení dokončí své akce prostřednictvím explicitního volání `SetTransactionComplete` metody a násobení nedokončuje své akce, ale místo toho se spoléhá na a vyžaduje pozdější volání, například k rozdělení, aby se akce dokončily.

Implementací služby s atributy je následující:

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

Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.

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

Protokolování požadavků na operace služby se zobrazí v okně konzoly služby. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.

```console
Press <ENTER> to terminate service.
Creating new service instance...
  Writing row 1 to database: Adding 100 to 0
  Writing row 2 to database: Subtracting 45 from 100
  Writing row 3 to database: Multiplying 55 by 9
  Writing row 4 to database: Dividing 495 by 15
```

Všimněte si, že kromě udržování průběžného součtu výpočtů služba oznamuje vytváření instancí (jednu instanci pro tuto ukázku) a zaznamená požadavky na operace do databáze. Vzhledem k tomu, že všechny požadavky mají za následek transakci klienta, jakékoli neúspěšné dokončení této transakce způsobí všechny operace v databázi vracené zpět. To může být ukázáno několika způsoby:

- Odkomentujte volání klienta `tx.Complete` () a spusťte akci znovu. výsledkem bude, že klient ukončí obor transakce bez dokončení transakce.

- Odkomentujte volání operace dělení – tento výsledek zabrání dokončení akce iniciované operací vynásobení, takže transakce klienta nakonec nebude také dokončena.

- Vyvolat neošetřenou výjimku kdekoli v oboru transakce klienta – to podobně zabrání klientovi v dokončení transakce.

Výsledkem kterékoli z nich je, že žádná operace prováděná v rámci tohoto oboru není potvrzena a počet řádků trvalých do databáze se nezvyšuje.

> [!NOTE]
> V rámci procesu sestavení se databázový soubor zkopíruje do složky bin. Aby bylo možné sledovat řádky, které jsou uchovány v protokolu, nikoli soubor, který je součástí projektu sady Visual Studio, je nutné se podívat na tuto kopii databázového souboru.

### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že máte nainstalovanou SQL Server 2005 Express Edition nebo SQL Server 2005. V souboru App. config služby `connectionString` může být databáze nastavena nebo je možné zakázat interakce databáze nastavením `usingSql` hodnoty appSettings na `false` .

2. Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).

3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).

Pokud spustíte ukázku napříč počítači, je nutné nakonfigurovat službu Microsoft DTC (Distributed Transaction Coordinator) (MSDTC), aby povolovala tok síťových transakcí, a pomocí nástroje WsatConfig. exe povolit transakce služby Windows Communication Foundation (WCF) pro podporu sítě.

### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a>Konfigurace služby Microsoft DTC (Distributed Transaction Coordinator) (MSDTC) pro podporu spuštění ukázky napříč počítači

1. Na počítači služby nakonfigurujte MSDTC tak, aby povoloval příchozí síťové transakce.

    1. V nabídce **Start** přejděte na **Ovládací panely**, klikněte na **Nástroje pro správu**a pak na **služby komponent**.

    2. Pravým tlačítkem myši klikněte na položku **Tento počítač** a vyberte možnost **vlastnosti**.

    3. Na kartě **MSDTC** klikněte na **Konfigurace zabezpečení**.

    4. Ověřte **přístup k síťovému DTC** a **povolte příchozí**.

    5. Kliknutím na tlačítko **Ano** restartujte službu MS DTC a pak klikněte na tlačítko **OK**.

    6. Kliknutím na **OK** zavřete dialogové okno.

2. Na počítači služby a klientském počítači nakonfigurujte bránu Windows Firewall tak, aby zahrnovala Microsoft DTC (Distributed Transaction Coordinator) (MSDTC) do seznamu s výjimkou aplikací:

    1. Spusťte aplikaci brány Windows Firewall z ovládacích panelů.

    2. Na kartě **výjimky** klikněte na **Přidat program**.

    3. Přejděte do složky C:\WINDOWS\System32.

    4. Vyberte MSDTC. exe a klikněte na **otevřít**.

    5. Kliknutím na tlačítko **OK** zavřete dialogové okno **Přidat program** a dalším kliknutím na tlačítko **OK** zavřete aplet brány Windows Firewall.

3. Na klientském počítači nakonfigurujte koordinátor MSDTC tak, aby povoloval odchozí síťové transakce:

    1. V nabídce **Start** přejděte na **Ovládací panely**, klikněte na **Nástroje pro správu**a pak na **služby komponent**.

    2. Pravým tlačítkem myši klikněte na položku **Tento počítač** a vyberte možnost **vlastnosti**.

    3. Na kartě **MSDTC** klikněte na **Konfigurace zabezpečení**.

    4. Ověřte **přístup k síťovému DTC** a **Povolte odchozí**.

    5. Kliknutím na tlačítko **Ano** restartujte službu MS DTC a pak klikněte na tlačítko **OK**.

    6. Kliknutím na **OK** zavřete dialogové okno.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`
