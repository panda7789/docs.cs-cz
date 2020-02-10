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
# <a name="ws-transaction-flow"></a>Tok transakcí webové služby
Tato ukázka demonstruje použití transakce s koordinovaným klientem a možností klienta a serveru pro tok transakce pomocí protokolu WS-Atomic nebo protokolu OleTransactions. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) , která implementuje službu kalkulačky, ale operace jsou popsány k předvedení použití `TransactionFlowAttribute` s výčtem **TransactionFlowOption** k určení toho, jakým způsobem je tok transakcí povolen. V rámci rozsahu transakce toku se do databáze zapíše protokol požadovaných operací, dokud se nedokončila koordinovaný transakce klienta – Pokud se transakce klienta nedokončila, transakce webové služby zajistí, že příslušné aktualizace databáze nejsou potvrzeny.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Po zahájení připojení ke službě a transakci klient přistupuje k několika operacím služby. Smlouva pro službu je definována následovně a všemi operacemi, které demonstrují jiné nastavení `TransactionFlowOption`.  

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

 Tím se definují operace v pořadí, ve kterém se mají zpracovat:  
  
- Požadavek operace `Add` musí zahrnovat transakci typu Flow.  
  
- Požadavek na operaci `Subtract` může zahrnovat transakci typu Flow.  
  
- Požadavek operace `Multiply` nesmí zahrnovat transakci toku prostřednictvím explicitního nastavení.  
  
- Požadavek operace `Divide` nesmí zahrnovat tok transakce v důsledku vynechání atributu `TransactionFlow`.  
  
 Aby bylo možné povolit tok transakce, musí být kromě příslušných atributů operace použita vazba s povolenou vlastností [\<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) . V této ukázce konfigurace služby zveřejňuje koncový bod TCP a koncový bod HTTP kromě koncového bodu výměny metadat. Koncový bod TCP a koncový bod HTTP používají následující vazby, u kterých je povolena vlastnost [\<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) .  
  
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
> Systém netTcpBinding poskytuje specifikace transactionProtocol, zatímco systém wsHttpBinding používá pouze bezpečnější WSAtomicTransactionOctober2004 protokol. Protokol OleTransactions je k dispozici pouze pro klienty Windows Communication Foundation (WCF).  
  
 Pro třídu, která implementuje rozhraní `ICalculator`, jsou všechny metody nastaveny s vlastností <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> nastavenou na `true`. Toto nastavení deklaruje, že všechny akce provedené v rámci metody nastávají v rámci rozsahu transakce. V takovém případě akce prováděné zahrnují záznam do databáze protokolu. Pokud požadavek na operaci zahrnuje transakci typu flow, pak dojde k akcím v rámci oboru příchozí transakce nebo je automaticky vygenerován nový obor transakce.  
  
> [!NOTE]
> Vlastnost <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> definuje chování jako lokální pro implementace metod služby a nedefinuje schopnost klienta nebo požadavek na tok transakce.  

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

 V klientovi se nastavení `TransactionFlowOption` služby na operace odrazí v definici `ICalculator` rozhraní vygenerované klientem. Také nastavení vlastnosti `transactionFlow` služby se projeví v konfiguraci aplikace klienta. Klient může vybrat přenos a protokol výběrem příslušné `endpointConfigurationName`.  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
> Zjištěné chování této ukázky je stejné bez ohledu na to, který protokol nebo přenos se volí.  
  
 Po iniciaci připojení ke službě vytvoří klient nové `TransactionScope` kolem volání služby.  

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
  
- Požadavek `Add` natéká do služby požadovanou transakci a akce služby se objeví v rámci rozsahu transakce klienta.  
  
- První `Subtract` požadavek také Flowe povolenou transakci ke službě a akce služby se projeví v rozsahu transakce klienta.  
  
- Druhá `Subtract` požadavek se provádí v rámci nového oboru transakce deklarovaného s možností `TransactionScopeOption.Suppress`. Tím se potlačí počáteční vnější transakce klienta a požadavek neflowe transakci ke službě. Tento přístup umožňuje klientovi explicitně se odhlásit a chránit před přetečením transakce do služby, když to není nutné. Akce služby se vyskytují v rámci rozsahu nové a nepřipojené transakce.  
  
- Požadavek `Multiply` neflowe transakci ke službě, protože vygenerovaná definice `ICalculator` rozhraní klienta obsahuje <xref:System.ServiceModel.TransactionFlowAttribute> nastaveno na <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.  
  
- Požadavek `Divide` neflowe transakci ke službě, protože znovu vygenerovaná definice `ICalculator` rozhraní nezahrnuje `TransactionFlowAttribute`. Akce služby se znovu vyskytují v rozsahu jiné nové a nepřipojené transakce.  
  
 Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.  
  
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
  
 Protokolování požadavků na operace služby se zobrazí v okně konzoly služby. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.  
  
```console  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 Po úspěšném provedení se rozsah transakce klienta dokončí a všechny akce prováděné v rámci tohoto oboru jsou potvrzeny. Konkrétně zaznamenané 5 záznamy jsou v databázi služby trvalé. První 2 z nich došlo v rámci oboru transakce klienta.  
  
 Pokud došlo k výjimce kdekoli v rámci `TransactionScope` klienta, transakce nemůže být dokončena. To způsobí, že záznamy zaznamenané do tohoto oboru nebudou potvrzeny do databáze. Tento efekt lze pozorovat opakovaným spuštěním ukázkového běhu po zakomentování volání za účelem dokončení vnějšího `TransactionScope`. V takovém případě jsou protokolovány pouze poslední 3 akce (od druhé `Subtract`, `Multiply` a `Divide` požadavky), protože transakce klienta neproudí do těch.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Pokud chcete vytvořit C# nebo Visual Basic verzi rozhraní .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)  
  
2. Ujistěte se, že máte nainstalovanou edici SQL Server Express nebo SQL Server a že připojovací řetězec byl v konfiguračním souboru aplikace služby správně nastaven. Chcete-li spustit ukázku bez použití databáze, nastavte `usingSql` hodnoty v konfiguračním souboru aplikace služby na `false`  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    > V případě konfigurace mezi počítači povolte DTC (Distributed Transaction Coordinator) podle níže uvedených pokynů a pomocí nástroje WsatConfig. exe z Windows SDK povolte podporu transakcí WCF v síti. Informace o nastavení WsatConfig. exe najdete v tématu [Konfigurace podpory transakcí WS-Atomic](../feature-details/configuring-ws-atomic-transaction-support.md).  
  
 Bez ohledu na to, jestli spouštíte ukázku na stejném počítači nebo na různých počítačích, musíte nakonfigurovat Microsoft DTC (Distributed Transaction Coordinator) (MSDTC), aby se povolil tok síťových transakcí, a pomocí nástroje WsatConfig. exe povolit podporu sítě WCF Transactions.  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a>Konfigurace služby Microsoft DTC (Distributed Transaction Coordinator) (MSDTC) pro podporu spuštění ukázky  
  
1. V počítači služby se systémem Windows Server 2003 nebo Windows XP nakonfigurujte službu MSDTC tak, aby povolovala příchozí síťové transakce pomocí následujících pokynů.  
  
    1. V nabídce **Start** přejděte na **Ovládací panely**, klikněte na **Nástroje pro správu**a pak na **služby komponent**.  
  
    2. Rozbalte položku **Služba komponent**. Otevřete složku **počítače** .  
  
    3. Pravým tlačítkem myši klikněte na položku **Tento počítač** a vyberte možnost **vlastnosti**.  
  
    4. Na kartě **MSDTC** klikněte na **Konfigurace zabezpečení**.  
  
    5. Ověřte **přístup k síťovému DTC** a **povolte příchozí**.  
  
    6. Klikněte na tlačítko **OK**a potom kliknutím na tlačítko **Ano** restartujte službu MSDTC.  
  
    7. Kliknutím na **OK** zavřete dialogové okno.  
  
2. V počítači služby se systémem Windows Server 2008 nebo Windows Vista nakonfigurujte službu MSDTC tak, aby povolovala příchozí síťové transakce pomocí následujících pokynů.  
  
    1. V nabídce **Start** přejděte na **Ovládací panely**, klikněte na **Nástroje pro správu**a pak na **služby komponent**.  
  
    2. Rozbalte položku **Služba komponent**. Otevřete složku **počítače** . Vyberte **DTC (Distributed Transaction Coordinator)** .  
  
    3. Klikněte pravým tlačítkem na **koordinátor DTC** a vyberte **vlastnosti**.  
  
    4. Na kartě **zabezpečení** ověřte **přístup k síti DTC** a **povolte příchozí**.  
  
    5. Klikněte na tlačítko **OK**a potom kliknutím na tlačítko **Ano** restartujte službu MSDTC.  
  
    6. Kliknutím na **OK** zavřete dialogové okno.  
  
3. Na klientském počítači nakonfigurujte koordinátor MSDTC tak, aby povoloval odchozí síťové transakce:  
  
    1. V nabídce **Start** přejděte na `Control Panel`, pak na **Nástroje pro správu**a pak na **služby komponent**.  
  
    2. Pravým tlačítkem myši klikněte na položku **Tento počítač** a vyberte možnost **vlastnosti**.  
  
    3. Na kartě **MSDTC** klikněte na **Konfigurace zabezpečení**.  
  
    4. Ověřte **přístup k síťovému DTC** a **Povolte odchozí**.  
  
    5. Klikněte na tlačítko **OK**a potom kliknutím na tlačítko **Ano** restartujte službu MSDTC.  
  
    6. Kliknutím na **OK** zavřete dialogové okno.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
