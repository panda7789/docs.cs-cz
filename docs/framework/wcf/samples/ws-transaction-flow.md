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
# <a name="ws-transaction-flow"></a>Tok transakcí webové služby
Tato ukázka ukazuje použití transakce koordinované klientem a možnosti klienta a serveru pro tok transakcí pomocí protokolu WS-Atomic Transaction nebo OleTransactions. Tento příklad je založen na [Začínáme,](../../../../docs/framework/wcf/samples/getting-started-sample.md) který implementuje službu kalkulačky, `TransactionFlowAttribute` ale operace jsou přiřazeny k předvedení použití s **TransactionFlowOption** výčtu k určení, do jaké míry je povolen tok transakcí. V rámci tokované transakce je do databáze zapsán protokol požadovaných operací a přetrvává, dokud nebude dokončena koordinovaná transakce klienta – pokud transakce klienta není dokončena, transakce webové služby zajistí, že transakce webové služby zajistí, že transakce webové služby příslušné aktualizace databáze nejsou potvrzeny.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Po spuštění připojení ke službě a transakce klient přistupuje k několika operacím služby. Smlouva o poskytování služeb je definována takto u každého z `TransactionFlowOption`operací, které prokazují jiné nastavení pro .  

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

 To definuje operace v pořadí, v jakém mají být zpracovány:  
  
- Požadavek `Add` operace musí obsahovat tok transakce.  
  
- Požadavek `Subtract` na operaci může zahrnovat tokovou transakci.  
  
- Požadavek `Multiply` operace nesmí obsahovat tokovou transakci prostřednictvím explicitního nastavení NotAllowed.  
  
- Požadavek `Divide` operace nesmí obsahovat tokovou transakci `TransactionFlow` prostřednictvím vynechání atributu.  
  
 Chcete-li povolit tok [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) transakcí, musí být použity vazby s povolenou vlastností transactionFlow>kromě příslušných atributů operace. V této ukázce konfigurace služby zpřístupňuje koncový bod TCP a koncový bod HTTP kromě koncového bodu serveru Metadata Exchange. Koncový bod TCP a koncový bod HTTP používají následující vazby, které mají [ \<povolenou vlastnost transactionFlow>.](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)  
  
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
> Systémem poskytované netTcpBinding umožňuje specifikaci transactionProtocol vzhledem k tomu, že systémem poskytované wsHttpBinding používá pouze interoperabilnější WSAtomicTransactionOctober2004 protokol. Protokol OleTransactions je k dispozici pouze pro klienty WCF (Windows Communication Foundation).  
  
 Pro třídu, která `ICalculator` implementuje rozhraní, jsou <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> všechny metody `true`přiřazeny s vlastností nastavenou na . Toto nastavení deklaruje, že všechny akce provedené v rámci metody dojít v rámci transakce. V tomto případě provedené akce zahrnují záznam do databáze protokolu. Pokud požadavek operace obsahuje tok transakce pak akce dojít v rámci rozsahu příchozí transakce nebo je automaticky generován nový rozsah transakce.  
  
> [!NOTE]
> Vlastnost <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> definuje chování místní implementace metody služby a nedefinuje schopnost klienta nebo požadavek na tekoucí transakce.  

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

 Na straně klienta `TransactionFlowOption` nastavení služby na operace se projeví v klientově `ICalculator` generované definice rozhraní. Nastavení `transactionFlow` vlastností služby se také projeví v konfiguraci aplikace klienta. Klient může vybrat přenos a protokol výběrem příslušného `endpointConfigurationName`.  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
> Pozorované chování tohoto vzorku je stejné bez ohledu na to, který protokol nebo přenos je vybrán.  
  
 Po iniciování připojení ke službě vytvoří `TransactionScope` klient nové kolem volání operací služby.  

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

 Volání operací jsou následující:  
  
- Požadavek `Add` toky požadovanou transakci do služby a akce služby dojít v rámci transakce klienta.  
  
- První `Subtract` požadavek také toky povolené transakce do služby a znovu akce služby dojít v rámci transakce klienta.  
  
- Druhý `Subtract` požadavek se provádí v rámci `TransactionScopeOption.Suppress` nového oboru transakce deklarované s možností. To potlačí počáteční vnější transakce klienta a požadavek netokuje transakce do služby. Tento přístup umožňuje klientovi explicitně odhlásit a chránit před tekoucí transakce do služby, pokud to není požadováno. Akce služby dojít v rámci nové a nepřipojené transakce.  
  
- `Multiply` Požadavek netokuje transakci do služby, protože klientova `ICalculator` vygenerovaná definice rozhraní obsahuje <xref:System.ServiceModel.TransactionFlowAttribute> sadu na <xref:System.ServiceModel.TransactionFlowOption> `NotAllowed`.  
  
- Požadavek `Divide` netokuje transakci do služby, protože znovu klienta generované definice `ICalculator` rozhraní neobsahuje `TransactionFlowAttribute`. Akce služby znovu dojít v rámci jiné nové a nepřipojené transakce.  
  
 Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi. Stisknutím klávesy ENTER v okně klienta vypněte klienta.  
  
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
  
 Protokolování požadavků na provoz služby se zobrazí v okně konzoly služby. Stisknutím klávesy ENTER v okně klienta vypněte klienta.  
  
```console  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 Po úspěšném spuštění dokončení oboru transakce klienta a všechny akce provedené v rámci tohoto oboru jsou potvrzeny. Konkrétně je v databázi služby zachováno 5 záznamů. První 2 z nich došlo v rámci transakce klienta.  
  
 Pokud došlo k výjimce `TransactionScope` kdekoli v rámci klienta pak transakce nelze dokončit. To způsobí, že záznamy zaznamenané v rámci tohoto oboru není potvrzena do databáze. Tento efekt lze pozorovat opakováním spuštění vzorku po zakomentování volání k dokončení vnější `TransactionScope`. Při takovém spuštění jsou zaznamenány pouze poslední `Subtract`3 `Multiply` akce `Divide` (z druhé , a požadavky) protože transakce klienta netokla k těmto.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Chcete-li vytvořit verzi řešení jazyka C# nebo Visual Basic .NET, postupujte podle pokynů v [části Vytváření ukázek windows communication foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)  
  
2. Ujistěte se, že jste nainstalovali SQL Server Express Edition nebo SQL Server a že připojovací řetězec byl správně nastaven v konfiguračním souboru aplikace služby. Chcete-li spustit ukázku bez `usingSql` použití databáze, nastavte hodnotu v konfiguračním souboru aplikace služby na`false`  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    > Pro konfiguraci mezi počítači povolte koordinátora distribuovaných transakcí pomocí níže uvedených pokynů a pomocí nástroje WsatConfig.exe z sady Windows SDK povolte podporu sítě WCF Transactions. Informace o nastavení souboru WsatConfig.exe naleznete [v tématu Configuring WS-Atomic Transaction Support](../feature-details/configuring-ws-atomic-transaction-support.md).  
  
 Bez ohledu na to, zda spustíte ukázku ve stejném počítači nebo v různých počítačích, je nutné nakonfigurovat koordinátor microsoft distribuovaných transakcí (MSDTC) tak, aby umožňoval tok síťových transakcí a pomocí nástroje WsatConfig.exe povoloval podporu sítě transakcí WCF.  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a>Konfigurace koordinátoru distribuovaných transakcí společnosti Microsoft (MSDTC) pro podporu spuštění ukázkové  
  
1. V servisním počítači se systémem Windows Server 2003 nebo Windows XP nakonfigurujte koordinátor MSDTC tak, aby umožňoval příchozí síťové transakce podle následujících pokynů.  
  
    1. V nabídce **Start** přejděte na **Ovládací panely**, nástroje **pro správu**a poté **na služby Component Services**.  
  
    2. Rozbalte **službu Component Services**. Otevřete složku **Počítače.**  
  
    3. Klepněte pravým tlačítkem myši na **položku Tento počítač** a vyberte příkaz **Vlastnosti**.  
  
    4. Na kartě **MSDTC** klepněte na **položku Konfigurace zabezpečení**.  
  
    5. Zkontrolujte **přístup k síti DTC** a **povolit příchozí**připojení .  
  
    6. Klepněte na tlačítko **OK**a potom klepnutím na **tlačítko Ano** restartujte službu MSDTC.  
  
    7. Kliknutím na **OK** zavřete dialogové okno.  
  
2. V servisním počítači se systémem Windows Server 2008 nebo Windows Vista nakonfigurujte koordinátor MSDTC tak, aby umožňoval příchozí síťové transakce podle následujících pokynů.  
  
    1. V nabídce **Start** přejděte na **Ovládací panely**, nástroje **pro správu**a poté **na služby Component Services**.  
  
    2. Rozbalte **službu Component Services**. Otevřete složku **Počítače.** Vyberte **koordinátor distribuovaných transakcí**.  
  
    3. Klepněte pravým tlačítkem myši na **položku Koordinátor koordinátoru DTC** a vyberte příkaz **Vlastnosti**.  
  
    4. Na kartě **Zabezpečení** zaškrtněte **políčko Síťový přístup k dtc** a **povolit vstup**.  
  
    5. Klepněte na tlačítko **OK**a potom klepnutím na **tlačítko Ano** restartujte službu MSDTC.  
  
    6. Kliknutím na **OK** zavřete dialogové okno.  
  
3. V klientském počítači nakonfigurujte msdtc tak, aby umožňoval odchozí síťové transakce:  
  
    1. V nabídce **Start** `Control Panel`přejděte na **položku Nástroje pro správu**a potom **na služby Component Services**.  
  
    2. Klepněte pravým tlačítkem myši na **položku Tento počítač** a vyberte příkaz **Vlastnosti**.  
  
    3. Na kartě **MSDTC** klepněte na **položku Konfigurace zabezpečení**.  
  
    4. Zkontrolujte **přístup k síti DTC** a **povolit odchozí**přístup .  
  
    5. Klepněte na tlačítko **OK**a potom klepnutím na **tlačítko Ano** restartujte službu MSDTC.  
  
    6. Kliknutím na **OK** zavřete dialogové okno.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
