---
title: 'Postupy: Vytvoření transakční služby'
ms.date: 03/30/2017
ms.assetid: 1bd2e4ed-a557-43f9-ba98-4c70cb75c154
ms.openlocfilehash: be364e7638394a30c199b05dd15ef4c44e18e688
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964022"
---
# <a name="how-to-create-a-transactional-service"></a>Postupy: Vytvoření transakční služby
Tato ukázka předvádí různé aspekty vytvoření transakční služby a použití transakce iniciované klientem pro koordinaci operací služby.  
  
### <a name="creating-a-transactional-service"></a>Vytvoření transakční služby  
  
1. Vytvořte kontrakt služby a přidávejte do něj operace s požadovaným nastavením z <xref:System.ServiceModel.TransactionFlowOption> výčtu, abyste určili požadavky na příchozí transakce. Všimněte si, že můžete také umístit <xref:System.ServiceModel.TransactionFlowAttribute> na implementovanou třídu služby. To umožňuje, aby jedna implementace rozhraní používala tato nastavení transakce namísto každé implementace.  
  
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
  
2. Vytvořte implementační třídu a použijte <xref:System.ServiceModel.ServiceBehaviorAttribute> k volitelnému <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> zadání a a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>. Měli byste si uvědomit, že v mnoha případech je <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> výchozí hodnota 60 sekund a `Unspecified` výchozí <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> hodnota. Pro každou operaci můžete použít <xref:System.ServiceModel.OperationBehaviorAttribute> atribut k určení, zda má být práce v rámci metody provedena v rámci rozsahu transakce podle hodnoty <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> atributu. V tomto případě je transakce použitá pro `Add` metodu stejná jako povinná příchozí transakce, která je předávána z klienta, a transakce použitá `Subtract` pro metodu je buď stejná jako příchozí transakce, pokud došlo k nějakému toku. z klienta nebo nové implicitně a místně vytvořené transakce.  
  
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
  
3. Nakonfigurujte vazby v konfiguračním souboru a určete tak, že by měl být tok kontextu transakce a jaké protokoly se mají použít. Další informace najdete v tématu [Konfigurace transakce ServiceModel](servicemodel-transaction-configuration.md). Konkrétně je určen typ vazby v `binding` atributu elementu koncového bodu. `bindingConfiguration` `transactionalOleTransactionsTcpBinding`Element [Endpoint > obsahuje atribut, který odkazuje na konfiguraci vazby s názvem, jak je znázorněno v \<](../../configure-apps/file-schema/wcf/endpoint-element.md) následující ukázkové konfiguraci.  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     Tok transakce je povolen na úrovni konfigurace pomocí `transactionFlow` atributu a transakční protokol je určen `transactionProtocol` pomocí atributu, jak je znázorněno v následující konfiguraci.  
  
    ```xml  
    <bindings>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="supporting-multiple-transaction-protocols"></a>Podpora více transakčních protokolů  
  
1. Pro zajištění optimálního výkonu byste měli použít protokol OleTransactions pro scénáře týkající se klienta a služby napsaného pomocí Windows Communication Foundation (WCF). Protokol WS-AtomicTransaction (WS-AT) je ale užitečný pro scénáře, kdy je potřeba interoperabilita se zásobníky protokolů třetích stran. Služby WCF můžete nakonfigurovat tak, aby přijímaly oba protokoly tím, že poskytují více koncových bodů s odpovídajícími vazbami specifických pro protokol, jak je znázorněno v následující ukázkové konfiguraci.  
  
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
  
     Protokol transakce je určen pomocí `transactionProtocol` atributu. Tento atribut však není v systému k dispozici `wsHttpBinding`, protože tato vazba může používat pouze protokol WS-AT.  
  
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
  
1. Ve výchozím nastavení operace WCF automaticky dokončí transakce, pokud nejsou vyvolány žádné neošetřené výjimky. Toto chování lze upravit pomocí <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> vlastnosti <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> a metody. Pokud se vyžaduje operace v rámci stejné transakce jako jiná operace (například operace MD a kredit), můžete chování automatického dokončování zakázat nastavením <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> vlastnosti na `false` hodnotu, jak je znázorněno v následujícím příkladu.`Debit` příklad operace. Transakce, kterou `Debit` operace používá, není dokončena, dokud nebude volána metoda <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> s vlastností nastavenou na `true` hodnotu, jak je <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> znázorněno `Credit1`v operaci, nebo když je metoda volána k explicitnímu označení transakce jako dokončená, jak je znázorněno `Credit2`v operaci. Všimněte si, že tyto dvě operace kreditu jsou uvedené pro ilustraci a že jedna operace kreditu by byla častěji typická.  
  
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
  
2. Pro účely korelace transakce nastavuje <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> vlastnost tak, aby `false` vyžadovala použití vazby s relacemi. Tento požadavek je zadán s `SessionMode` vlastností <xref:System.ServiceModel.ServiceContractAttribute>na.  
  
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
  
### <a name="controlling-the-lifetime-of-a-transactional-service-instance"></a>Řízení životnosti instance transakční služby  
  
1. Služba WCF používá <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> vlastnost k určení, zda je daná instance služby uvolněna při dokončení transakce. Vzhledem k tomu, `true`že se jedná o výchozí nastavení, pokud není nakonfigurováno jinak, WCF vykazuje efektivní a předvídatelné chování aktivace za běhu. Volání služby v následné transakci jsou zaručena nová instance služby, která nemá žádné zbytky stavu předchozí transakce. I když je to často užitečné, někdy může být vhodné zachovat stav v rámci instance služby nad rámec dokončení transakce. Příklady by mohly být v případě, že je požadovaný stav nebo popisovač prostředků náročný na načtení nebo re. To můžete provést nastavením <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> vlastnosti na. `false` V takovém případě budou instance a všechny přidružené stavy k dispozici při následných voláních. Při použití tohoto postupu dejte pozor na to, kdy a jak se budou stavy a transakce vymazat a dokončit. Následující příklad ukazuje, jak to provést udržováním instance s `runningTotal` proměnnou.  
  
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
    > Vzhledem k tomu, že doba životnosti instance je chování interní pro službu a je řízeno <xref:System.ServiceModel.ServiceBehaviorAttribute> prostřednictvím vlastnosti, není nutné upravovat konfiguraci služby ani kontrakt služby, aby bylo možné nastavit chování instance. Kromě toho kabel nebude obsahovat žádné reprezentace.
