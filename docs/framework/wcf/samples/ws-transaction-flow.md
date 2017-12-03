---
title: "Tok transakcí webové služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
caps.latest.revision: "43"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d14f516ed32ecbada0b612cf06179e47acf18ddc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ws-transaction-flow"></a>Tok transakcí webové služby
Tento příklad znázorňuje použití transakce koordinované klienta a klient a server možnosti pro transakci toku pomocí protokolu WS-Atomic Transactions nebo OleTransactions. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje ale operace, které jsou označené k předvedení použití `TransactionFlowAttribute` s **TransactionFlowOption** výčet k určení, do jaké míry transakce toku povolený. V rámci oboru sdružení transakcí protokolu požadovaná operace je zapsán do databáze a dál, dokud klient koordinované transakce byla dokončena – i když klientská transakce nedokončí, transakce webové služby zajišťuje, že příslušné aktualizace do databáze nejsou potvrzeny.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Po inicializaci připojení k služby a transakce, klient přistupuje k několik operací služby. Kontrakt služby je definován následujícím způsobem v každé z operací jiné nastavení pro demonstraci `TransactionFlowOption`.  
  
```  
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
  
 Definuje operace v pořadí, ve kterém se mají být zpracovány:  
  
-   `Add` Žádost o operaci musí zahrnovat sdružení transakcí.  
  
-   A `Subtract` žádost o operaci může zahrnovat sdružení transakcí.  
  
-   A `Multiply` žádost o operaci nesmí obsahovat sdružení transakcí prostřednictvím explicitní NotAllowed nastavení.  
  
-   A `Divide` žádost o operaci nesmí obsahovat sdružení transakcí prostřednictvím vynechání `TransactionFlow` atribut.  
  
 Povolení toku transakcí, vazby s [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) vlastnost povoleno je nutné použít kromě atributy příslušnou operaci. Konfigurace služby v této ukázce zpřístupní koncový bod TCP a koncový bod HTTP kromě koncový bod metadat systému Exchange. Koncový bod TCP a koncový bod protokolu HTTP použijte následující vazby, které mají [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) vlastnost povoleno.  
  
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
>  Poskytované systémem netTcpBinding umožňuje specifikaci transactionProtocol, zatímco wsHttpBinding poskytované systémem používá jenom více interoperabilní WSAtomicTransactionOctober2004 protokol. Protokol OleTransactions je k dispozici pro použití pouze [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klientů.  
  
 Pro třídu, která implementuje `ICalculator` rozhraní, všechny metody jsou opatřená <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> vlastnost nastavena na hodnotu `true`. Toto nastavení deklaruje, že všechny akce prováděné v rámci metody dojít v rámci oboru transakce. Akce prováděné v tomto případě zahrnují záznam do protokolu databáze. Pokud žádost o operaci zahrnuje sdružení transakcí akce, které se vyskytují v rozsahu příchozí transakce nebo nového oboru transakce se automaticky vygeneroval.  
  
> [!NOTE]
>  <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> Vlastnost definuje chování, které jsou místní pro implementace metoda služby a nedefinuje schopnost klienta nebo požadavek toku transakce.  
  
```  
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
  
 Na klienta, službu `TransactionFlowOption` nastavení na operace se projeví v definici generovaného klienta `ICalculator` rozhraní. Navíc služby `transactionFlow` se projeví nastavení vlastnosti v konfiguraci klienta aplikace. Klienta můžete vybrat přenosu a protokol výběrem příslušné `endpointConfigurationName`.  
  
```  
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```  
  
> [!NOTE]
>  Zjištěnou chování Tato ukázka je stejný bez ohledu na to, který je vybrán protokol nebo přenos.  
  
 Bylo zahájeno připojení ke službě, klient vytvoří novou `TransactionScope` kolem volání operací služby.  
  
```  
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
  
-   `Add` Požadavek toků požadované transakce ke službě a k akcím služby v rámci oboru transakce klienta.  
  
-   První `Subtract` požadavek také toků povolené transakce ke službě a znovu k akcím služby v rámci oboru transakce klienta.  
  
-   Druhý `Subtract` požadavku je provést v rámci nového oboru transakce deklarovat s `TransactionScopeOption.Suppress` možnost. To potlačí počáteční vnější transakci klienta a požadavek nepostupuje transakce ke službě. Tento přístup umožňuje klientovi výslovně výslovný nesouhlas s a chránit proti toku transakce služby, při které se nevyžaduje. Služby akce se provedou v rámci oboru transakce nové a které nejsou připojeny.  
  
-   `Multiply` Požadavku není toku transakce ke službě, protože klient je vygenerován definice `ICalculator` rozhraní obsahuje <xref:System.ServiceModel.TransactionFlowAttribute> nastavena na <xref:System.ServiceModel.TransactionFlowOption> `NotAllowed`.  
  
-   `Divide` Požadavku není toku transakce ke službě, protože klient je znovu vygenerován definice `ICalculator` rozhraní nezahrnuje `TransactionFlowAttribute`. V rámci oboru jiné nové a které nejsou připojeny transakci znovu provedou služby akce.  
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
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
  
 Protokolování žádosti o operaci služby se zobrazí v okně konzoly služby. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
```  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 Po úspěšném spuštění dokončí oboru transakce klienta a potvrzeny všechny akce prováděné v rámci tohoto oboru. Konkrétně uvedené 5 záznamy zůstávají v databázi služby. První 2 z nich došlo v rámci oboru transakce klienta.  
  
 Pokud došlo k výjimce kdekoli v rámci klienta `TransactionScope` pak transakci nelze dokončit. To způsobí, že záznamy zapsané do protokolu v rámci tohoto oboru na nebyla zapsána do databáze. Tento efekt může být dodržen opakováním ukázku spustit po komentářů se volání dokončení vnější `TransactionScope`. Na takové spustit pouze poslední 3 akce (od druhého `Subtract`, `Multiply` a `Divide` požadavky) se protokolují, protože klientská transakce toku není na ty.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Sestavení C# nebo Visual Basic .NET verzi řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)  
  
2.  Ujistěte se, že jste nainstalovali SQL Server Express Edition nebo SQL Server a že připojovací řetězec nebyla správně nastavena v konfiguračním souboru aplikace služby. Chcete-li spustit ukázku bez použití databáze, nastavte `usingSql` hodnota v konfiguračním souboru aplikace služby k`false`  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Pro konfiguraci mezi počítače povolte Distributed Transaction Coordinator pomocí níže uvedených pokynů a použít nástroj WsatConfig.exe ze sady Windows SDK k povolení podpory sítě transakce WCF. V tématu [konfigurace podpory WS-Atomic Transactions](http://go.microsoft.com/fwlink/?LinkId=190370) informace o nastavení WsatConfig.exe.  
  
 Jestli spuštěním ukázky ve stejném počítači nebo na různých počítačích, musíte nakonfigurovat Microsoft distribuované transakce koordinátora služba MSDTC () k povolení toku transakcí sítě a pomocí nástroje WsatConfig.exe povolit [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transakce Podpora sítě.  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a>Konfigurace Microsoft distribuované transakce koordinátora služba MSDTC () k podpoře spouštění vzorku  
  
1.  Na počítači služby se systémem Windows Server 2003 nebo Windows XP nakonfigurujte služby MSDTC povolit příchozí transakce sítě podle těchto pokynů.  
  
    1.  Z **spustit** nabídky, přejděte na **ovládací panely**, pak **nástroje pro správu**a potom **služby komponent**.  
  
    2.  Rozbalte položku **služby komponent**. Otevřete **počítače** složky.  
  
    3.  Klikněte pravým tlačítkem na **Můj počítač** a vyberte **vlastnosti**.  
  
    4.  Na **služby MSDTC** , klikněte na **konfigurace zabezpečení**.  
  
    5.  Zkontrolujte **síťový přístup DTC** a **povolit příchozí**.  
  
    6.  Klikněte na tlačítko **OK**, pak klikněte na tlačítko **Ano** restartovat služba koordinátoru MS DTC.  
  
    7.  Klikněte na tlačítko **OK** zavřete dialogové okno.  
  
2.  Na počítači služby se systémem Windows Server 2008 nebo Windows Vista nakonfigurujte služby MSDTC povolit příchozí transakce sítě podle těchto pokynů.  
  
    1.  Z **spustit** nabídky, přejděte na **ovládací panely**, pak **nástroje pro správu**a potom **služby komponent**.  
  
    2.  Rozbalte položku **služby komponent**. Otevřete **počítače** složky. Vyberte **Distributed Transaction Coordinator**.  
  
    3.  Klikněte pravým tlačítkem na **koordinátoru DTC** a vyberte **vlastnosti**.  
  
    4.  Na **zabezpečení** zkontrolujte **síťový přístup DTC** a **povolit příchozí**.  
  
    5.  Klikněte na tlačítko **OK**, pak klikněte na tlačítko **Ano** restartovat služba koordinátoru MS DTC.  
  
    6.  Klikněte na tlačítko **OK** zavřete dialogové okno.  
  
3.  V klientském počítači nakonfigurujte služby MSDTC povolit odchozí transakce sítě:  
  
    1.  Z **spustit** nabídky, přejděte na `Control Panel`, pak **nástroje pro správu**a potom **služby komponent**.  
  
    2.  Klikněte pravým tlačítkem na **Můj počítač** a vyberte **vlastnosti**.  
  
    3.  Na **služby MSDTC** , klikněte na **konfigurace zabezpečení**.  
  
    4.  Zkontrolujte **síťový přístup DTC** a **povolit odchozí**.  
  
    5.  Klikněte na tlačítko **OK**, pak klikněte na tlačítko **Ano** restartovat služba koordinátoru MS DTC.  
  
    6.  Klikněte na tlačítko **OK** zavřete dialogové okno.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
