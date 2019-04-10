---
title: 'Postupy: Vytvoření transakční služby'
ms.date: 03/30/2017
ms.assetid: 1bd2e4ed-a557-43f9-ba98-4c70cb75c154
ms.openlocfilehash: 7f7f060db5a4ffd66524e220e3e3291debd8a3fc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329489"
---
# <a name="how-to-create-a-transactional-service"></a>Postupy: Vytvoření transakční služby
Tento příklad ukazuje různé aspekty vytvoření transakční služby a použití klientem iniciované transakci ke koordinaci operací služby.  
  
### <a name="creating-a-transactional-service"></a>Vytvoření transakční služby  
  
1. Vytvoření kontraktu service a opatřovat je poznámkami operací pomocí požadovaného nastavení z <xref:System.ServiceModel.TransactionFlowOption> výčet k určení požadavků na příchozí transakce. Všimněte si, že můžete také umístit <xref:System.ServiceModel.TransactionFlowAttribute> na třídu služby se implementuje. To umožňuje jedna implementace rozhraní nahrazujícím každou implementaci těchto nastavení transakcí.  
  
    ```csharp
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
  
2. Vytvoření třídy implementaci a použití <xref:System.ServiceModel.ServiceBehaviorAttribute> volitelně zadat <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>. Nezapomeňte přitom, která v mnoha případech se výchozí <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> 60 sekund a výchozí <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> z `Unspecified` jsou vhodné. Pro každou operaci, můžete použít <xref:System.ServiceModel.OperationBehaviorAttribute> atribut udává, jestli pracovní provést v rámci metody se budou objevovat v rámci oboru transakce oboru podle hodnoty <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> atribut. V tomto případě používá transakce pro `Add` metodou je stejný jako povinné příchozí transakce, která je počet plynoucích z klienta a transakce pro `Subtract` metoda je buď stejná jako příchozí transakce, pokud jeden byla převedena z klienta, nebo implicitně a místně vytvořenou novou transakci.  
  
    ```csharp
    [ServiceBehavior(  
        TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,  
        TransactionTimeout = "00:00:45")]  
    public class CalculatorService : ICalculator  
    {  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog($"Adding {n1} to {n2}");
            return n1 + n2;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog($"Subtracting {n2} from {n1}");
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
  
3. Nakonfigurujte vazby v konfiguračním souboru, určení, že by měl být předávány kontext transakce a protokolů, který se má použít k tomu. Další informace najdete v tématu [konfigurace transakcí ServiceModel](servicemodel-transaction-configuration.md). Konkrétně je typ vazby zadaný v elementu koncového bodu `binding` atribut. [ \<Koncový bod >](../../configure-apps/file-schema/wcf/endpoint-element.md) obsahuje element `bindingConfiguration` atribut, který odkazuje na vazbu konfigurace s názvem `transactionalOleTransactionsTcpBinding`, jak je znázorněno v následující ukázkové konfiguraci.  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     Je povolen tok transakcí na úrovni konfigurace s použitím `transactionFlow` atribut a transakční protokol je specifikován pomocí `transactionProtocol` atributu, jak je znázorněno v následující konfiguraci.  
  
    ```xml  
    <bindings>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="supporting-multiple-transaction-protocols"></a>Podpora více protokolů transakcí  
  
1. Pro zajištění optimálního výkonu abyste používali protokolu OleTransactions pro scénáře zahrnující klienta a služby, které jsou napsané s využitím Windows Communication Foundation (WCF). Protokol WS-AtomicTransaction (WS-AT) je však užitečné pro scénáře při vzájemná funkční spolupráce s sad protokolů třetích stran je povinný. Můžete nakonfigurovat WCF services tak, aby přijímal oba protokoly tím, že poskytuje několik koncových bodů s odpovídající konkrétní vazby, jak je znázorněno v následující ukázková konfigurace.  
  
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
  
     Transakční protokol je specifikován pomocí `transactionProtocol` atribut. Nicméně, tento atribut chybí z poskytnuté systémem `wsHttpBinding`, protože tato vazba lze použít pouze WS-AT protokolu.  
  
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
  
### <a name="controlling-the-completion-of-a-transaction"></a>Řízení dokončení transakce  
  
1. Ve výchozím nastavení WCF operace automatického dokončení transakce, pokud nejsou vyvolány žádné neošetřené výjimky. Toto chování lze upravit pomocí <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> vlastnost a <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> metoda. Při operaci musí dojít v rámci stejné transakce jako jiná operace (například operace MD a Dal), můžete zakázat automatické dokončování chování tak, že nastavíte <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> vlastnost `false` jak je znázorněno v následujícím `Debit` příklad operace. Transakce `Debit` používá operace nedokončí až do metody s <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> vlastnost nastavena na `true` je volána, jak je znázorněno v operaci `Credit1`, nebo když <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> explicitně označit je volána metoda transakce jako dokončené, jak je znázorněno v operaci `Credit2`. Všimněte si, že dvě kredit operace jsou platné pro ilustraci a že jediného kredit ve výši operace by obvyklejší.  
  
    ```csharp
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
  
2. Pro účely transakce korelace, nastavení <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> vlastnost `false` vyžaduje použití vazby s relacemi. Tento požadavek není zadán s `SessionMode` vlastnost <xref:System.ServiceModel.ServiceContractAttribute>.  
  
    ```csharp
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
  
### <a name="controlling-the-lifetime-of-a-transactional-service-instance"></a>Řízení životního cyklu instance transakční služby  
  
1. Používá WCF <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> vlastnosti a určit, jestli se po dokončení transakce uvolní podkladové instance služby. Protože je výchozí hodnota `true`, pokud se nenakonfiguruje, chování aktivace WCF dodatků efektivní a předvídatelné "just-in-time". Volání služby v následných transakcí je zajištěna nové instance služby s žádné zbývající součásti stav předchozí transakce. Když je často užitečné, někdy můžete udržovat stav v rámci instance služby nad rámec dokončení transakce. Příklady by po drahé načíst nebo znovuvytvoření požadovaného stavu nebo popisovače k prostředkům. Můžete to provést tak, že nastavíte <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> vlastnost `false`. Při tomto nastavení instance a všechny přidružené stavu budou dostupné v následných voláních. Při použití této funkce, věnujte pozornost pozor, kdy a jak stavu a transakce budou vymazána a dokončit. Následující příklad ukazuje, jak to provést pomocí instance s `runningTotal` proměnné.  
  
    ```csharp
    [ServiceBehavior(TransactionIsolationLevel = [ServiceBehavior(  
        ReleaseServiceInstanceOnTransactionComplete = false)]  
    public class CalculatorService : ICalculator  
    {  
        double runningTotal = 0;  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n)  
        {  
            // Perform transactional operation  
            RecordToLog($"Adding {n} to {runningTotal}");
            runningTotal = runningTotal + n;  
            return runningTotal;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n)  
        {  
            // Perform transactional operation  
            RecordToLog($"Subtracting {n} from {runningTotal}");
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
    >  Protože životnost instance je chování, které je interní ke službě a řízené prostřednictvím <xref:System.ServiceModel.ServiceBehaviorAttribute> vlastnost, je vyžadovat, abyste nastavili chování instance bez změny konfigurace služby nebo kontrakt služby. Kromě toho přenosu bude obsahovat žádné reprezentace.
