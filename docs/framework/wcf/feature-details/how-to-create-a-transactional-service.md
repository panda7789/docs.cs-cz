---
title: "Postupy: Vytvoření transakční služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bd2e4ed-a557-43f9-ba98-4c70cb75c154
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 647b551e9b78d89cee3ddaf8f47ba8174a23fc5a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-transactional-service"></a>Postupy: Vytvoření transakční služby
Tento příklad znázorňuje různé aspekty vytvoření transakční služby a použití transakci iniciované klientem ke koordinaci operací služby.  
  
### <a name="creating-a-transactional-service"></a>Vytvoření transakční služby  
  
1.  Vytvoření kontraktu služby a opatřit poznámkami operací s požadované nastavení z <xref:System.ServiceModel.TransactionFlowOption> výčtu k určení požadavků na příchozí transakce. Všimněte si, že můžete taky umístit <xref:System.ServiceModel.TransactionFlowAttribute> na třídě služby se implementuje. To umožňuje jediná implementace typu rozhraní pro použití těchto nastavení transakcí místo každých implementace.  
  
    ```  
    [ServiceContract]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // Use this to require an incoming transaction  
        [TransactionFlow(TransactionFlowOption.Mandatory)]  
        double Add(double n1, double n2);  
        [OperationContract]  
        // Use this to permit an incoming transaction  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        double Subtract(double n1, double n2);  
    }  
    ```  
  
2.  Vytvoření třídy implementaci a použít <xref:System.ServiceModel.ServiceBehaviorAttribute> volitelně zadat <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>. Upozorňujeme ale, který v mnoha případech výchozí <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> 60 sekund a výchozí <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> z `Unspecified` jsou vhodné. Pro každou operaci, můžete použít <xref:System.ServiceModel.OperationBehaviorAttribute> atribut k určení, zda pracovní provede v rámci metody provedeno v rámci oboru oboru transakce podle hodnoty <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> atribut. V takovém případě transakce používá pro `Add` metoda je stejný jako povinné příchozí transakce, která je plynoucích z klienta a transakce pro `Subtract` metoda je buď stejné, jako příchozí transakce když jeden byl plynoucích z klienta, nebo novou transakci implicitně a místně vytvořené.  
  
    ```  
    [ServiceBehavior(  
        TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,  
        TransactionTimeout = "00:00:45")]  
    public class CalculatorService : ICalculator  
    {  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog(String.Format("Adding {0} to {1}", n1, n2));  
            return n1 + n2;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog(String.Format("Subtracting {0} from {1}", n2, n1));  
            return n1 - n2;  
        }  
  
        private static void RecordToLog(string recordText)  
        {  
            // Database operations omitted for brevity  
            // This is where the transaction provides specific benefit  
            // - changes to the database will be committed only when  
            // the transaction completes.  
        }  
    }  
    ```  
  
3.  V konfiguračním souboru, určující, zda by měl plynoucích kontext transakce a protokoly, který se má použít k tomu, nakonfigurujte vazby. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Konfigurace transakcí ServiceModel](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md). Konkrétně je typ vazby zadaný v elementu koncový bod `binding` atribut. [ \<Endpoint >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) obsahuje element `bindingConfiguration` atribut, který odkazuje na vazbu konfigurace s názvem `transactionalOleTransactionsTcpBinding`, jak ukazuje následující ukázka konfigurace.  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     Tok transakcí je povolena na úrovni konfigurace pomocí `transactionFlow` atribut a protokol transakcí je zadán pomocí `transactionProtocol` atributu, jak je znázorněno v následující konfiguraci.  
  
    ```xml  
    <bindings>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="supporting-multiple-transaction-protocols"></a>Podpora více protokoly transakcí  
  
1.  Pro optimální výkon, musí používat protokol OleTransactions pro scénáře zahrnující klienta a služby napsané pomocí [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Protokol WS-AtomicTransaction (WS-AT) je však užitečné v případech, pokud je potřeba vzájemná funkční spolupráce s zásobníky protokol třetích stran. Můžete nakonfigurovat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby tak, aby přijímal oba protokoly poskytováním více koncových bodů s příslušnou specifické pro protokol vazby, jak je znázorněno v následující ukázka konfigurace.  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="http://localhost:8000/CalcService"  
        binding="wsHttpBinding"  
        bindingConfiguration="transactionalWsatHttpBinding"  
        contract="ICalculator"  
        name="WSAtomicTransaction_endpoint" />  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     Protokol transakce je zadán pomocí `transactionProtocol` atribut. Tento atribut je však chybí z poskytované systémem `wsHttpBinding`, protože tuto vazbu lze použít pouze protokol WS-AT.  
  
    ```xml  
    <bindings>  
      <wsHttpBinding>  
        <binding name="transactionalWsatHttpBinding"  
          transactionFlow="true" />  
      </wsHttpBinding>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="controlling-the-completion-of-a-transaction"></a>Řízení dokončení transakce.  
  
1.  Ve výchozím nastavení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] operace automaticky dokončit transakce, pokud jsou vyvolány žádné neošetřené výjimky. Toto chování můžete upravit pomocí <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> vlastnost a <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> metoda. Když operace je potřeba v rámci stejné transakci jako jiná operace (například operace MD a Dal), můžete zakázat chování automatického dokončování nastavením <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> vlastnost `false` jak je znázorněno v následujícím `Debit` příklad operaci. Transakce `Debit` není používá operaci dokončit, dokud nebudou metodu s <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> vlastnost nastavena na hodnotu `true` je volána, jak je znázorněno v operaci `Credit1`, nebo když <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> metoda je volána explicitně označit transakce jako dokončené, jak je znázorněno v operaci `Credit2`. Upozorňujeme, že pro účely obrázku jsou zobrazeny dvě platební operace a že jeden úvěrového operace by typičtější.  
  
    ```  
    [ServiceBehavior]  
    public class CalculatorService : IAccount  
    {  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = false)]  
        public void Debit(double n)  
        {  
            // Perform debit operation  
  
            return;  
        }  
  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = true)]  
        public void Credit1(double n)  
        {  
            // Perform credit operation  
  
            return;  
        }  
  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = false)]  
        public void Credit2(double n)  
        {  
            // Perform alternate credit operation  
  
            OperationContext.Current.SetTransactionComplete();  
            return;  
        }  
    }  
    ```  
  
2.  Pro účely korelace transakce, nastavení <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> vlastnost `false` vyžaduje použití relacemi vazby. Tento požadavek zadaný `SessionMode` vlastnost <xref:System.ServiceModel.ServiceContractAttribute>.  
  
    ```  
    [ServiceContract(SessionMode = SessionMode.Required)]  
    public interface IAccount  
    {  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Debit(double n);  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Credit1(double n);  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Credit2(double n);  
    }  
    ```  
  
### <a name="controlling-the-lifetime-of-a-transactional-service-instance"></a>Řízení životního cyklu instance služby zasílání transakčních  
  
1.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]používá <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> vlastnosti k určení, zda je základní instance služby vydané po dokončení transakce. Vzhledem k tomu, že se `true`, pokud není uvedeno jinak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vykazuje aktivaci "v běhu" efektivní a předvídatelné chování. Volání do služby na následné transakce jsou zajištěná nové instance služby se žádné zbytky stav předchozí transakce. Přestože se často užitečné, v některých případech může chcete zachovat stav v rámci instance služby nad rámec dokončení transakce. Příklady tohoto by po nákladné načíst nebo rekonstruovat požadované stavu nebo obslužných rutin k prostředkům. To provedete nastavením <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> vlastnost `false`. Toto nastavení, instanci a všechny přidružené stavu bude k dispozici pro následující volání. Při použití tohoto nástroje věnujte pozornost pozor, kdy a jak stavu a transakce budou vymazána a dokončit. Následující příklad ukazuje, jak to udělat Údržba instance s `runningTotal` proměnné.  
  
    ```  
    [ServiceBehavior(TransactionIsolationLevel = [ServiceBehavior(  
        ReleaseServiceInstanceOnTransactionComplete = false)]  
    public class CalculatorService : ICalculator  
    {  
        double runningTotal = 0;  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n)  
        {  
            // Perform transactional operation  
            RecordToLog(String.Format("Adding {0} to {1}", n, runningTotal));  
            runningTotal = runningTotal + n;  
            return runningTotal;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n)  
        {  
            // Perform transactional operation  
            RecordToLog(String.Format("Subtracting {0} from {1}", n, runningTotal));  
            runningTotal = runningTotal - n;  
            return runningTotal;  
        }  
  
        private static void RecordToLog(string recordText)  
        {  
            // Database operations omitted for brevity  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  Vzhledem k tomu, že instance životnost je chování, které je interní ke službě a řízené prostřednictvím <xref:System.ServiceModel.ServiceBehaviorAttribute> vlastnost žádné změny konfigurace služby ani kontrakt služby je potřeba nastavit chování instance. Kromě toho sítě bude obsahovat žádné reprezentace tohoto objektu.
