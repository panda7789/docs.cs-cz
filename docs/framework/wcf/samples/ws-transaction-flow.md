---
title: Tok transakcí webové služby
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: 35af3090c0f898578a5f8dfb81d02d22a0074ad2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483879"
---
# <a name="ws-transaction-flow"></a>Tok transakcí webové služby
Tato ukázka demonstruje použití transakce koordinovaný klienta a klient a server možnosti pro transakci tok pomocí protokolu WS-Atomic Transactions nebo OleTransactions. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) , který implementuje službu kalkulačky, ale operace mají atributy pro demonstraci použití `TransactionFlowAttribute` s **TransactionFlowOption** výčet, chcete-li zjistit, jaké úroveň transakce je povolen tok. V rámci oboru sdružení probíhajících transakcí, protokol požadované operace jsou zapsána do databáze a zůstává v platnosti do klienta koordinované transakce byla dokončena – Pokud klientská transakce nedokončí, transakce webové služby zajišťuje, že příslušné aktualizace do databáze nejsou potvrzeny.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Po zahájení připojení do služby a transakce ke kterým přistupuje klient několik operací služby. Kontrakt služby je definovaná následujícím způsobem s každou operací demonstrace různých nastavení `TransactionFlowOption`.  

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

 Definuje operace v pořadí, ve kterém jsou ke zpracování:  
  
-   `Add` Žádost o operaci musí obsahovat sdružení probíhajících transakcí.  
  
-   A `Subtract` žádost o operaci může zahrnovat sdružení probíhajících transakcí.  
  
-   A `Multiply` žádost o operaci, nesmí obsahovat toku transakce pomocí explicitní nastavení hodnotu NotAllowed.  
  
-   A `Divide` žádost o operaci, nesmí obsahovat sdružení probíhajících transakcí prostřednictvím vynechání `TransactionFlow` atribut.  
  
 Povolení toku transakcí, vazby s [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) vlastnost povoleno je nutné použít kromě atributů příslušné operace. Konfigurace služby v této ukázce zpřístupňuje koncový bod TCP a koncový bod HTTP kromě koncový bod výměny metadat. Koncový bod TCP a koncový bod protokolu HTTP použijte následující vazby, které mají [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) vlastnost povolena.  
  
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
>  NetTcpBinding poskytované systémem zatímco wsHttpBinding poskytované systémem používá více interoperabilní protokol WSAtomicTransactionOctober2004 umožňuje volbu specifikace třídu transactionProtocol. Použít OleTransactions, který protokol je dostupná jenom pro klienty Windows Communication Foundation (WCF).  
  
 Pro třídu, která implementuje `ICalculator` rozhraní, všechny metody jsou připisuje <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> nastavenou na `true`. Toto nastavení deklaruje, že všechny akce prováděné v metodě dojít v rámci oboru transakce. Akce prováděné v tomto případě patří nahrávání protokolu databáze. Pokud žádost o operaci zahrnují sdružení probíhajících transakcí dojde k akcím v rámci oboru příchozí transakce nebo nový obor transakce není automaticky vygenerován.  
  
> [!NOTE]
>  <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> Vlastnost definuje chování místní implementace metod služby a nedefinuje schopnost klienta nebo požadavek toku transakce.  

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

 Na klienta, služba `TransactionFlowOption` nastavení na operace se projeví v definici generovaného klienta `ICalculator` rozhraní. Kromě toho služby `transactionFlow` nastavení vlastnosti se projeví v konfiguraci klienta aplikace. Klienta můžete vybrat přenosu a protokol tak, že vyberete příslušný `endpointConfigurationName`.  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
>  Vypozorovaná chování této ukázky je stejný bez ohledu na to, který je vybrán protokol nebo přenos.  
  
 Zahájení připojení ke službě vytvoří klient nový `TransactionScope` po volání operace služby.  

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

 Volání operace jsou následující:  
  
-   `Add` Požadavek toky požadovanou transakci ke službě a k akcím služby v rámci oboru transakce na straně klienta.  
  
-   První `Subtract` požadavku se přenášejí také povolené transakce ve službě a znovu k akcím služby v rámci oboru transakce na straně klienta.  
  
-   Druhá `Subtract` žádosti se provede v rámci nového oboru transakce deklarována s `TransactionScopeOption.Suppress` možnost. Toto potlačí počáteční vnější transakci klienta a požadavek nepostupuje transakci ke službě. Tento přístup umožňuje klientovi explicitně odhlásit a ochranu proti toku transakce služby, při které se nevyžaduje. V rámci oboru transakce nové a nepřipojené provedou služby akce.  
  
-   `Multiply` Žádost o nepostupuje transakce ve službě, protože klient vygenerovaný definice `ICalculator` zahrnuje rozhraní <xref:System.ServiceModel.TransactionFlowAttribute> nastavena na <xref:System.ServiceModel.TransactionFlowOption> `NotAllowed`.  
  
-   `Divide` Požadavek nepostupuje transakce ve službě, protože znovu klienta vygenerovaný definice `ICalculator` rozhraní nezahrnuje `TransactionFlowAttribute`. V rámci oboru jinou transakcí nové a nepřipojené dojde znovu k akcím služby.  
  
 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
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
  
 Protokolování žádosti o operaci služby se zobrazí v okně konzoly služby. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
```  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 Po úspěšném spuštění klienta oboru transakce dokončena a usilujeme o to všechny akce v daném oboru. Konkrétně uvedené 5 záznamů se uchovávají v databázi služby. První 2 z nich došlo v rámci oboru transakce na straně klienta.  
  
 Pokud došlo k výjimce kdekoli v rámci klienta `TransactionScope` pak transakce nelze dokončit. To způsobí, že záznamy, které jsou zaznamenány v daném oboru na nebudou zapíšou do databáze. Tomu můžete dodržovat opakující se ukázku spustit po okomentováním odpovídajícího volání k dokončení vnější `TransactionScope`. Na těchto spustit pouze poslední 3 akce (druhého `Subtract`, `Multiply` a `Divide` požadavků) jsou protokolována, protože klientská transakce není tok na ty.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Chcete-li sestavení C# nebo Visual Basic .NET verze řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)  
  
2.  Ujistěte se, že jste nainstalovali SQL Server Express Edition nebo SQL Server a že připojovací řetězec správně nastavena v konfiguračním souboru aplikace služby. Ke spuštění ukázky bez použití databáze, nastavte `usingSql` hodnoty v konfiguračním souboru aplikace služby k `false`  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Pro konfigurace mezi počítači povolte koordinátor distribuovaných transakcí pomocí následujícího postupu a použít nástroj WsatConfig.exe ze sady Windows SDK k povolení podpory síťové transakce WCF. Zobrazit [konfigurace WS-Atomic podpora transakcí](https://go.microsoft.com/fwlink/?LinkId=190370) informace o nastavení WsatConfig.exe.  
  
 Zda ukázku spustíte ve stejném počítači nebo na různých počítačích, musíte nakonfigurovat Microsoft distribuované transakce koordinátor (MSDTC) k povolení toku transakcí sítě a nástrojem WsatConfig.exe povolit podporu sítě transakce WCF.  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a>Konfigurace Microsoft distribuované transakce koordinátor (MSDTC) k podpoře spouštění vzorku  
  
1.  V rámci služby počítače se systémem Windows Server 2003 nebo Windows XP nakonfigurujte MSDTC povolit příchozí síťové transakce podle těchto pokynů.  
  
    1.  Z **Start** nabídky, přejděte na **ovládací panely**, pak **nástroje pro správu**a potom **služby Component Services**.  
  
    2.  Rozbalte **služby Component Services**. Otevřít **počítače** složky.  
  
    3.  Klikněte pravým tlačítkem na **tento počítač** a vyberte **vlastnosti**.  
  
    4.  Na **MSDTC** klikněte na tlačítko **konfigurace zabezpečení**.  
  
    5.  Zkontrolujte **DTC přístup k síti** a **povolit příchozí**.  
  
    6.  Klikněte na tlačítko **OK**, pak klikněte na tlačítko **Ano** restartování služby MSDTC.  
  
    7.  Klikněte na tlačítko **OK** zavřete dialogové okno.  
  
2.  V rámci služby počítače se systémem Windows Server 2008 nebo Windows Vista nakonfigurujte MSDTC povolit příchozí síťové transakce podle těchto pokynů.  
  
    1.  Z **Start** nabídky, přejděte na **ovládací panely**, pak **nástroje pro správu**a potom **služby Component Services**.  
  
    2.  Rozbalte **služby Component Services**. Otevřít **počítače** složky. Vyberte **koordinátor distribuovaných transakcí**.  
  
    3.  Klikněte pravým tlačítkem na **Koordinátor DTC** a vyberte **vlastnosti**.  
  
    4.  Na **zabezpečení** kartě **síťový přístup DTC** a **povolit příchozí**.  
  
    5.  Klikněte na tlačítko **OK**, pak klikněte na tlačítko **Ano** restartování služby MSDTC.  
  
    6.  Klikněte na tlačítko **OK** zavřete dialogové okno.  
  
3.  V klientském počítači nakonfigurujte MSDTC povolit odchozí síťové transakce:  
  
    1.  Z **Start** nabídky, přejděte na `Control Panel`, pak **nástroje pro správu**a potom **služby Component Services**.  
  
    2.  Klikněte pravým tlačítkem na **tento počítač** a vyberte **vlastnosti**.  
  
    3.  Na **MSDTC** klikněte na tlačítko **konfigurace zabezpečení**.  
  
    4.  Zkontrolujte **DTC přístup k síti** a **povolit odchozí**.  
  
    5.  Klikněte na tlačítko **OK**, pak klikněte na tlačítko **Ano** restartování služby MSDTC.  
  
    6.  Klikněte na tlačítko **OK** zavřete dialogové okno.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
