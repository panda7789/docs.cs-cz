---
title: Chování transakce služby
ms.date: 03/30/2017
helpviewer_keywords:
- Service Transaction Behavior Sample [Windows Communication Foundation]
ms.assetid: 1a9842a3-e84d-427c-b6ac-6999cbbc2612
ms.openlocfilehash: bfdf0c9ddb8654bf7a6736bcccb0d9350e9a12a6
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50042490"
---
# <a name="service-transaction-behavior"></a>Chování transakce služby
Tato ukázka demonstruje použití transakce koordinovaný klienta a nastavení atributu ServiceBehaviorAttribute a OperationBehaviorAttribute řídit chování transakce služby. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) , který implementuje službu kalkulačky, ale je rozšířit na Udržovat protokol serveru provádět operace v databázové tabulce a stavový průběžný součet pro operace kalkulačky. Trvalé zápisy do tabulky protokolu serveru jsou závislé na výsledku transakce koordinovaný klient -, pokud klientská transakce nedokončí, transakce webové služby zajišťuje, že aktualizace databáze nejsou potvrzeny.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Kontrakt služby definuje, že všechny operace vyžadují transakci tok s požadavky:  
  
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
  
 Povolit tok příchozích transakcí, je služba nakonfigurována s poskytnutými systémem wsHttpBinding s transactionFlow atribut nastaven na `true`. Tato vazba používá interoperabilní WSAtomicTransactionOctober2004 protokolu:  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="transactionalBinding" transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
 Po zahájení obě připojení ke službě a transakce, klient několik operací služby v rámci oboru dané transakce přistupuje k dokončení transakce a uzavře připojení:  
  
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
  
 Ve službě existují tři atributy ovlivňující chování transakce služby a jejich učinit následujícími způsoby:  
  
-   Na `ServiceBehaviorAttribute`:  
  
    -   `TransactionTimeout` Vlastnost určuje časové období, ve kterém musí být transakce dokončena. V této ukázce je nastaven na 30 sekund.  
  
    -   `TransactionIsolationLevel` Vlastnost určuje úroveň izolace, která podporuje službu. To je vyžadovaný pro shodu úroveň izolace klienta.  
  
    -   `ReleaseServiceInstanceOnTransactionComplete` Vlastnost určuje, zda je instance služby recyklován po dokončení transakce. Nastavením na `false`, služba zajišťuje stejné instance služby napříč požadavky operace. To je potřeba k údržbě celkový počet spuštění. Pokud hodnotu `true`, novou instanci se vygeneruje po každé dokončit akci.  
  
    -   `TransactionAutoCompleteOnSessionClose` Vlastnost určuje, zda existují nevyřízené transakce dokončeny po zavření relace. Nastavením na `false`, jednotlivé operace se musí buď sadu `OperationBehaviorAttribute``TransactionAutoComplete` vlastnost `true` nebo chcete explicitně po volání `SetTransactionComplete` metody pro dokončení transakce. Tento příklad ukazuje oba přístupy.  
  
-   Na `ServiceContractAttribute`:  
  
    -   `SessionMode` Vlastnost určuje, zda služba koreluje příslušných žádostí do logické relace. Protože tato služba zahrnuje operace, kde je vlastnost Vlastnost OperationBehaviorAttribute TransactionAutoComplete nastaven na `false` (násobení a dělení), `SessionMode.Required` musí být zadán. Například vícenásobně operaci nelze dokončit transakci a místo toho spoléhá na pozdější volání dělení dokončete pomocí `SetTransactionComplete` metoda; služba musí být schopní určit, že tyto operace se vyskytnou v rámci stejné relace.  
  
-   Na `OperationBehaviorAttribute`:  
  
    -   `TransactionScopeRequired` Vlastnost určuje, jestli by měl provést operace akce v rámci oboru transakce. Je nastavené na `true` pro všechny operace v této ukázkové a, protože klient toky jeho transakce pro všechny operace, dojde k akcím v rámci oboru dané transakce klienta.  
  
    -   `TransactionAutoComplete` Vlastnost určuje, zda je transakce, ve kterém metoda je provedena automaticky dokončit, pokud nevyskytnou žádné nezpracované výjimky. Jak již bylo popsáno dříve, je nastavené na `true` pro přidání a rozdílové operace, ale `false` Multiply a operace dělení. Operace Add a rozdílové automatické dokončování jejich akce, dělení dokončí svou činnost prostřednictvím explicitní volání konstruktoru `SetTransactionComplete` metoda a Multiply nedokončí její akce, ale místo toho závisí na službě a vyžaduje, aby pozdější volání, například k Rozdělte na dokončení akce.  
  
 Implementace služby s atributy vypadá takto:  
  
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
  
    // Logging method ommitted for brevity  
}   
```  
  
 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
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
  
 Protokolování žádosti o operaci služby se zobrazí v okně konzoly služby. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
```console  
Press <ENTER> to terminate service.  
Creating new service instance...  
  Writing row 1 to database: Adding 100 to 0  
  Writing row 2 to database: Subtracting 45 from 100  
  Writing row 3 to database: Multiplying 55 by 9  
  Writing row 4 to database: Dividing 495 by 15  
```  
  
 Všimněte si, že kromě zachování celkového spouštění výpočtů, služby hlášení vytváření instancí (jedna instance pro tuto ukázku) a protokoly operace žádosti do databáze. Vzhledem k tomu, že všechny žádosti tok transakce klienta, jakékoli neúspěchy k dokončení této transakce výsledkem všechny databázové operace zpět. To můžete předvedená v několika způsoby:  
  
-   Odkomentujte volání klienta `tx.Complete`() a znovu spusťte – výsledkem je klientské operace bude ukončena obor transakce bez dokončení jeho transakce.  
  
-   Komentář out volání operace služby dělení – Neumožnit tento výsledky akce iniciované dokončení operace násobení a proto klientská transakce takže v konečném důsledku také nepodaří dokončit.  
  
-   Vyvolání neošetřené výjimky kdekoli v oboru transakce klienta – Podobně tomu klienta od dokončení jeho transakce.  
  
 Některé z těchto výsledkem je, že žádná z operací provedených v daném oboru není potvrzena a počet řádků, které ukládají do databáze nezvyšuje.  
  
> [!NOTE]
>  Jako součást procesu sestavení databázový soubor je zkopírován do složky bin. Můžete třeba podívejte se na tuto kopii souboru databáze sledovat řádky, které se ukládají do protokolu, nikoli soubor, který je součástí projektu sady Visual Studio.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste nainstalovali SQL Server 2005 Express Edition nebo SQL Server 2005. V souboru App.config služby, databáze `connectionString` může být sada nebo databáze interakce může zakázat nastavením appSettings `usingSql` hodnota, která se `false`.  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Pokud ukázku spustíte napříč počítači, je nutné nakonfigurovat Microsoft distribuované transakce koordinátor (MSDTC) k povolení toku transakcí sítě a nástrojem WsatConfig.exe povolit síť transakce Windows Communication Foundation (WCF) podpora.  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a>Konfigurace Microsoft distribuované transakce koordinátor (MSDTC) k podpoře spouštění ukázku v počítačích  
  
1.  Na počítači služby konfigurace povolit příchozí síťové transakce koordinátor MSDTC.  
  
    1.  Z **Start** nabídky, přejděte na **ovládací panely**, pak **nástroje pro správu**a potom **služby Component Services**.  
  
    2.  Klikněte pravým tlačítkem na **tento počítač** a vyberte **vlastnosti**.  
  
    3.  Na **MSDTC** klikněte na tlačítko **konfigurace zabezpečení**.  
  
    4.  Zkontrolujte **DTC přístup k síti** a **povolit příchozí**.  
  
    5.  Klikněte na tlačítko **Ano** restartovat službu MS DTC a potom klikněte na **OK**.  
  
    6.  Klikněte na tlačítko **OK** zavřete dialogové okno.  
  
2.  V počítači služby a klientský počítač konfigurace brány Windows Firewall zahrnout Microsoft distribuované transakce koordinátor (MSDTC) do seznamu vyloučení aplikací:  
  
    1.  Spuštění aplikace Windows Firewall v Ovládacích panelech.  
  
    2.  Z **výjimky** klikněte na tlačítko **přidat Program**.  
  
    3.  Přejděte do složky C:\WINDOWS\System32.  
  
    4.  Msdtc.exe vyberte a klikněte na tlačítko **otevřít**.  
  
    5.  Klikněte na tlačítko **OK** zavřete **přidat Program** dialogové okno a klikněte na tlačítko **OK** zavřete aplet brány Windows Firewall.  
  
3.  V klientském počítači nakonfigurujte MSDTC povolit odchozí síťové transakce:  
  
    1.  Z **Start** nabídky, přejděte na **ovládací panely**, pak **nástroje pro správu**a potom **služby Component Services**.  
  
    2.  Klikněte pravým tlačítkem na **tento počítač** a vyberte **vlastnosti**.  
  
    3.  Na **MSDTC** klikněte na tlačítko **konfigurace zabezpečení**.  
  
    4.  Zkontrolujte **DTC přístup k síti** a **povolit odchozí**.  
  
    5.  Klikněte na tlačítko **Ano** restartovat službu MS DTC a potom klikněte na **OK**.  
  
    6.  Klikněte na tlačítko **OK** zavřete dialogové okno.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`  
  
## <a name="see-also"></a>Viz také
