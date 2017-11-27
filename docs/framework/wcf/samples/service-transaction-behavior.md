---
title: "Chování transakce služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Service Transaction Behavior Sample [Windows Communication Foundation]
ms.assetid: 1a9842a3-e84d-427c-b6ac-6999cbbc2612
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6d881e7727c002cc9cc5322881a67dcb9a780efa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="service-transaction-behavior"></a>Chování transakce služby
Tento příklad znázorňuje použití transakce koordinované klienta a nastavení ServiceBehaviorAttribute a OperationBehaviorAttribute pro řízení chování transakce služby. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) které implementuje službu kalkulačky, ale je rozšířeno udržování protokolu serveru provádět operace v tabulce databáze a stateful, Mezisoučet pro operace kalkulačky. Trvalý provede zápis do tabulky protokolu serveru jsou závislé na výsledek transakce klienta koordinované -, pokud klientská transakce nedokončí, transakce webové služby zajistí, že nejsou potvrdit aktualizace do databáze.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Kontrakt služby definuje, že všechny operace, vyžadují transakci zalomen s požadavky:  
  
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
  
 Pokud chcete povolit příchozí tok transakcí, služba nakonfigurovaná pomocí wsHttpBinding poskytované systémem atributem transactionFlow nastavena na `true`. Tato vazba používá protokol umožňuje vzájemnou spolupráci WSAtomicTransactionOctober2004:  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="transactionalBinding" transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
 Po inicializaci obě připojení služby a transakce, klient přistupuje k několik operací služby v rámci oboru této transakce dokončení transakce a uzavře připojení:  
  
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
  
 Na službu existují tři atributy, které ovlivňují chování transakce služby a k tomu mohou následujícími způsoby:  
  
-   Na `ServiceBehaviorAttribute`:  
  
    -   `TransactionTimeout` Vlastnost určuje časové období, ve kterém musíte dokončit transakci. V této ukázce je nastavena na 30 sekund.  
  
    -   `TransactionIsolationLevel` Vlastnost určuje úroveň izolace, která podporuje službu. To je nutné tak, aby odpovídaly úroveň izolace klienta.  
  
    -   `ReleaseServiceInstanceOnTransactionComplete` Vlastnost určuje, zda je instance služby recykluje po dokončení transakce. Nastavením na `false`, služba udržuje na stejnou instanci služby napříč požadavky operaci. To je potřeba k údržbě celkový počet spuštění. Pokud nastavena na `true`, novou instanci se generuje po každé dokončit akci.  
  
    -   `TransactionAutoCompleteOnSessionClose` Vlastnost určuje, zda jsou zbývající transakce dokončit po ukončení relace. Nastavením na `false`, je potřeba buď sadu jednotlivé operace `OperationBehaviorAttribute``TransactionAutoComplete` vlastnost, která má `true` nebo explicitně vyžaduje volání `SetTransactionComplete` Metoda dokončení transakcí. Tento příklad znázorňuje obou přístupů.  
  
-   Na `ServiceContractAttribute`:  
  
    -   `SessionMode` Vlastnost určuje, zda služba korelaci příslušných žádostí do logické relace. Protože tato služba zahrnuje operace, kde je vlastnost OperationBehaviorAttribute TransactionAutoComplete vlastnost nastavena na `false` (násobení a dělení), `SessionMode.Required` musí být zadán. Například násobkem operace nedokončí transakci a místo toho závisí na novější volání dělení dokončit pomocí `SetTransactionComplete` metoda; služby musí být schopní určit, že tyto operace dochází v rámci stejné relace.  
  
-   Na `OperationBehaviorAttribute`:  
  
    -   `TransactionScopeRequired` Vlastnost určuje, zda se má provést akce operace v oboru transakce. To je nastaven na `true` pro všechny operace v této ukázkové a, protože klient toků transakci ke všem operacím, dojde k akcím v rámci oboru této transakce klienta.  
  
    -   `TransactionAutoComplete` Vlastnost určuje, zda transakce, ve kterém metoda spustí automaticky dokončit, pokud dojde k žádné neošetřených výjimek. Jak se popisuje výš, je nastavena `true` pro operace přidat a Subtract ale `false` Multiply a operace dělení. Přidat a odečíst operace dokončit jejich akce automaticky, Rozděl dokončí svou činnost prostřednictvím explicitní volání `SetTransactionComplete` metoda a Multiply nedokončí jeho akce, ale místo toho závisí na a vyžaduje novější volání, jako třeba Dělení na dokončení akce.  
  
 Implementace s atributy služby je následující:  
  
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
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
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
  
 Protokolování žádosti o operaci služby se zobrazí v okně konzoly služby. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
```  
Press <ENTER> to terminate service.  
Creating new service instance...  
  Writing row 1 to database: Adding 100 to 0  
  Writing row 2 to database: Subtracting 45 from 100  
  Writing row 3 to database: Multiplying 55 by 9  
  Writing row 4 to database: Dividing 495 by 15  
```  
  
 Všimněte si, že kromě zachování spuštění celkový výpočtů, služby hlášení vytvoření instance (jedna instance pro tuto ukázku) a protokoly operaci žádosti do databáze. Vzhledem k tomu, že všechny žádosti toku transakcí klienta, jakákoli chyba k provedení této transakce výsledkem všechny operace databáze, je vrácena zpět. To prokázat u mnoha různými způsoby:  
  
-   Komentář volání klienta `tx.Complete`() a poté spusťte znovu - výsledkem klienta ukončení oboru transakce bez dokončení transakci.  
  
-   Komentář out volání operace služby dělení – tento výsledky brání provedení akce zahájili dokončení operace násobení a proto transakce klienta konečném důsledku také nepodaří dokončit.  
  
-   Throw k neošetřené výjimce kdekoli v oboru transakce klienta – podobně zabrání klientovi dokončení transakci.  
  
 Výsledek některý z těchto je, že žádná operací provést v rámci tohoto oboru není potvrzena a počtu řádků uchovány v databázi není zvýšit.  
  
> [!NOTE]
>  Jako součást procesu sestavení databázový soubor zkopírován do složky bin. Musí se podíváte na tuto kopii souboru databáze sledovat na řádky, které jsou nastavené jako trvalé do protokolu, nikoli soubor, který je zahrnutý v projektu sady Visual Studio.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste nainstalovali SQL Server 2005 Express Edition nebo SQL Server 2005. V souboru App.config služby, databázi `connectionString` může být sada nebo databázi interakce mohou být zakázány nastavením appSettings `usingSql` hodnotu `false`.  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Pokud spustíte ukázku mezi počítači, musíte nakonfigurovat Microsoft distribuované transakce koordinátora služba MSDTC () k povolení toku transakcí sítě a pomocí nástroje WsatConfig.exe povolit [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] transakce sítě podpory.  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a>Konfigurace Microsoft distribuované transakce koordinátora služba MSDTC () k podpoře spouštění vzorku mezi počítači  
  
1.  Na počítači služby konfigurace služby MS DTC povolit příchozí transakce sítě.  
  
    1.  Z **spustit** nabídky, přejděte na **ovládací panely**, pak **nástroje pro správu**a potom **služby komponent**.  
  
    2.  Klikněte pravým tlačítkem na **Můj počítač** a vyberte **vlastnosti**.  
  
    3.  Na **služby MSDTC** , klikněte na **konfigurace zabezpečení**.  
  
    4.  Zkontrolujte **síťový přístup DTC** a **povolit příchozí**.  
  
    5.  Klikněte na tlačítko **Ano** restartujte službu MS DTC a potom klikněte na **OK**.  
  
    6.  Klikněte na tlačítko **OK** zavřete dialogové okno.  
  
2.  V počítači služby a klientský počítač konfigurace brány Windows Firewall Microsoft distribuované transakce koordinátora služba MSDTC () do seznamu vyloučení aplikace zahrnout:  
  
    1.  Spusťte aplikaci brána Windows Firewall v Ovládacích panelech.  
  
    2.  Z **výjimky** , klikněte na **přidat Program**.  
  
    3.  Přejděte do složky C:\WINDOWS\System32.  
  
    4.  Vyberte Msdtc.exe a klikněte na **otevřete**.  
  
    5.  Klikněte na tlačítko **OK** zavřete **přidat Program** dialogové okno a klikněte na tlačítko **OK** zavřete apletu brány Windows Firewall.  
  
3.  V klientském počítači nakonfigurujte služby MSDTC povolit odchozí transakce sítě:  
  
    1.  Z **spustit** nabídky, přejděte na **ovládací panely**, pak **nástroje pro správu**a potom **služby komponent**.  
  
    2.  Klikněte pravým tlačítkem na **Můj počítač** a vyberte **vlastnosti**.  
  
    3.  Na **služby MSDTC** , klikněte na **konfigurace zabezpečení**.  
  
    4.  Zkontrolujte **síťový přístup DTC** a **povolit odchozí**.  
  
    5.  Klikněte na tlačítko **Ano** restartujte službu MS DTC a potom klikněte na **OK**.  
  
    6.  Klikněte na tlačítko **OK** zavřete dialogové okno.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`  
  
## <a name="see-also"></a>Viz také
