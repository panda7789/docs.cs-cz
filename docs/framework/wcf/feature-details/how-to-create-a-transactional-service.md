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
# <a name="how-to-create-a-transactional-service"></a><span data-ttu-id="a883c-102">Postupy: Vytvoření transakční služby</span><span class="sxs-lookup"><span data-stu-id="a883c-102">How to: Create a Transactional Service</span></span>
<span data-ttu-id="a883c-103">Tato ukázka předvádí různé aspekty vytvoření transakční služby a použití transakce iniciované klientem pro koordinaci operací služby.</span><span class="sxs-lookup"><span data-stu-id="a883c-103">This sample demonstrates various aspects of creating a transactional service and the use of a client-initiated transaction to coordinate service operations.</span></span>  
  
### <a name="creating-a-transactional-service"></a><span data-ttu-id="a883c-104">Vytvoření transakční služby</span><span class="sxs-lookup"><span data-stu-id="a883c-104">Creating a transactional service</span></span>  
  
1. <span data-ttu-id="a883c-105">Vytvořte kontrakt služby a přidávejte do něj operace s požadovaným nastavením z <xref:System.ServiceModel.TransactionFlowOption> výčtu, abyste určili požadavky na příchozí transakce.</span><span class="sxs-lookup"><span data-stu-id="a883c-105">Create a service contract and annotate the operations with the desired setting from the <xref:System.ServiceModel.TransactionFlowOption> enumeration to specify the incoming transaction requirements.</span></span> <span data-ttu-id="a883c-106">Všimněte si, že můžete také umístit <xref:System.ServiceModel.TransactionFlowAttribute> na implementovanou třídu služby.</span><span class="sxs-lookup"><span data-stu-id="a883c-106">Note that you can also place the <xref:System.ServiceModel.TransactionFlowAttribute> on the service class being implemented.</span></span> <span data-ttu-id="a883c-107">To umožňuje, aby jedna implementace rozhraní používala tato nastavení transakce namísto každé implementace.</span><span class="sxs-lookup"><span data-stu-id="a883c-107">This allows for a single implementation of an interface to use these transaction settings, instead of every implementation.</span></span>  
  
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
  
2. <span data-ttu-id="a883c-108">Vytvořte implementační třídu a použijte <xref:System.ServiceModel.ServiceBehaviorAttribute> k volitelnému <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> zadání a a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span><span class="sxs-lookup"><span data-stu-id="a883c-108">Create an implementation class, and use the <xref:System.ServiceModel.ServiceBehaviorAttribute> to optionally specify a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span></span> <span data-ttu-id="a883c-109">Měli byste si uvědomit, že v mnoha případech je <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> výchozí hodnota 60 sekund a `Unspecified` výchozí <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> hodnota.</span><span class="sxs-lookup"><span data-stu-id="a883c-109">You should note that in many cases, the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> of 60 seconds and the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> of `Unspecified` are appropriate.</span></span> <span data-ttu-id="a883c-110">Pro každou operaci můžete použít <xref:System.ServiceModel.OperationBehaviorAttribute> atribut k určení, zda má být práce v rámci metody provedena v rámci rozsahu transakce podle hodnoty <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> atributu.</span><span class="sxs-lookup"><span data-stu-id="a883c-110">For each operation, you can use the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute to specify whether work performed within the method should occur within the scope of a transaction scope according to the value of the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> attribute.</span></span> <span data-ttu-id="a883c-111">V tomto případě je transakce použitá pro `Add` metodu stejná jako povinná příchozí transakce, která je předávána z klienta, a transakce použitá `Subtract` pro metodu je buď stejná jako příchozí transakce, pokud došlo k nějakému toku. z klienta nebo nové implicitně a místně vytvořené transakce.</span><span class="sxs-lookup"><span data-stu-id="a883c-111">In this case, the transaction used for the `Add` method is the same as the mandatory incoming transaction that is flowed from the client, and the transaction used for the `Subtract` method is either the same as the incoming transaction if one was flowed from the client, or a new implicitly and locally created transaction.</span></span>  
  
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
  
3. <span data-ttu-id="a883c-112">Nakonfigurujte vazby v konfiguračním souboru a určete tak, že by měl být tok kontextu transakce a jaké protokoly se mají použít.</span><span class="sxs-lookup"><span data-stu-id="a883c-112">Configure the bindings in the configuration file, specifying that the transaction context should be flowed, and the protocols to be used to do so.</span></span> <span data-ttu-id="a883c-113">Další informace najdete v tématu [Konfigurace transakce ServiceModel](servicemodel-transaction-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="a883c-113">For more information, see [ServiceModel Transaction Configuration](servicemodel-transaction-configuration.md).</span></span> <span data-ttu-id="a883c-114">Konkrétně je určen typ vazby v `binding` atributu elementu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="a883c-114">Specifically, the binding type is specified in the endpoint element’s `binding` attribute.</span></span> <span data-ttu-id="a883c-115">`bindingConfiguration` `transactionalOleTransactionsTcpBinding`Element [Endpoint > obsahuje atribut, který odkazuje na konfiguraci vazby s názvem, jak je znázorněno v \<](../../configure-apps/file-schema/wcf/endpoint-element.md) následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="a883c-115">The [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element contains a `bindingConfiguration` attribute that references a binding configuration named `transactionalOleTransactionsTcpBinding`, as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     <span data-ttu-id="a883c-116">Tok transakce je povolen na úrovni konfigurace pomocí `transactionFlow` atributu a transakční protokol je určen `transactionProtocol` pomocí atributu, jak je znázorněno v následující konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="a883c-116">Transaction flow is enabled at the configuration level by using the `transactionFlow` attribute, and the transaction protocol is specified using the `transactionProtocol` attribute, as shown in the following configuration.</span></span>  
  
    ```xml  
    <bindings>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="supporting-multiple-transaction-protocols"></a><span data-ttu-id="a883c-117">Podpora více transakčních protokolů</span><span class="sxs-lookup"><span data-stu-id="a883c-117">Supporting multiple transaction protocols</span></span>  
  
1. <span data-ttu-id="a883c-118">Pro zajištění optimálního výkonu byste měli použít protokol OleTransactions pro scénáře týkající se klienta a služby napsaného pomocí Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a883c-118">For optimal performance, you should use the OleTransactions protocol for scenarios involving a client and service written using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="a883c-119">Protokol WS-AtomicTransaction (WS-AT) je ale užitečný pro scénáře, kdy je potřeba interoperabilita se zásobníky protokolů třetích stran.</span><span class="sxs-lookup"><span data-stu-id="a883c-119">However, the WS-AtomicTransaction (WS-AT) protocol is useful for scenarios when interoperability with third-party protocol stacks is required.</span></span> <span data-ttu-id="a883c-120">Služby WCF můžete nakonfigurovat tak, aby přijímaly oba protokoly tím, že poskytují více koncových bodů s odpovídajícími vazbami specifických pro protokol, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="a883c-120">You can configure WCF services to accept both protocols by providing multiple endpoints with appropriate protocol-specific bindings, as shown in the following sample configuration.</span></span>  
  
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
  
     <span data-ttu-id="a883c-121">Protokol transakce je určen pomocí `transactionProtocol` atributu.</span><span class="sxs-lookup"><span data-stu-id="a883c-121">The transaction protocol is specified using the `transactionProtocol` attribute.</span></span> <span data-ttu-id="a883c-122">Tento atribut však není v systému k dispozici `wsHttpBinding`, protože tato vazba může používat pouze protokol WS-AT.</span><span class="sxs-lookup"><span data-stu-id="a883c-122">However, this attribute is absent from the system-provided `wsHttpBinding`, because this binding can only use the WS-AT protocol.</span></span>  
  
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
  
### <a name="controlling-the-completion-of-a-transaction"></a><span data-ttu-id="a883c-123">Řízení dokončení transakce</span><span class="sxs-lookup"><span data-stu-id="a883c-123">Controlling the completion of a transaction</span></span>  
  
1. <span data-ttu-id="a883c-124">Ve výchozím nastavení operace WCF automaticky dokončí transakce, pokud nejsou vyvolány žádné neošetřené výjimky.</span><span class="sxs-lookup"><span data-stu-id="a883c-124">By default, WCF operations automatically complete transactions if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="a883c-125">Toto chování lze upravit pomocí <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> vlastnosti <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> a metody.</span><span class="sxs-lookup"><span data-stu-id="a883c-125">You can modify this behavior by using the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property and the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method.</span></span> <span data-ttu-id="a883c-126">Pokud se vyžaduje operace v rámci stejné transakce jako jiná operace (například operace MD a kredit), můžete chování automatického dokončování zakázat nastavením <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> vlastnosti na `false` hodnotu, jak je znázorněno v následujícím příkladu.`Debit` příklad operace.</span><span class="sxs-lookup"><span data-stu-id="a883c-126">When an operation is required to occur within the same transaction as another operation (for example, a debit and credit operation), you can disable the autocomplete behavior by setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` as shown in the following `Debit` operation example.</span></span> <span data-ttu-id="a883c-127">Transakce, kterou `Debit` operace používá, není dokončena, dokud nebude volána metoda <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> s vlastností nastavenou na `true` hodnotu, jak je <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> znázorněno `Credit1`v operaci, nebo když je metoda volána k explicitnímu označení transakce jako dokončená, jak je znázorněno `Credit2`v operaci.</span><span class="sxs-lookup"><span data-stu-id="a883c-127">The transaction the `Debit` operation uses is not completed until a method with the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property set to `true` is called, as shown in the operation `Credit1`, or when the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method is called to explicitly mark the transaction as complete, as shown in the operation `Credit2`.</span></span> <span data-ttu-id="a883c-128">Všimněte si, že tyto dvě operace kreditu jsou uvedené pro ilustraci a že jedna operace kreditu by byla častěji typická.</span><span class="sxs-lookup"><span data-stu-id="a883c-128">Note that the two credit operations are shown for illustration purposes, and that a single credit operation would be more typical.</span></span>  
  
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
  
2. <span data-ttu-id="a883c-129">Pro účely korelace transakce nastavuje <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> vlastnost tak, aby `false` vyžadovala použití vazby s relacemi.</span><span class="sxs-lookup"><span data-stu-id="a883c-129">For the purposes of transaction correlation, setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` requires the use of a sessionful binding.</span></span> <span data-ttu-id="a883c-130">Tento požadavek je zadán s `SessionMode` vlastností <xref:System.ServiceModel.ServiceContractAttribute>na.</span><span class="sxs-lookup"><span data-stu-id="a883c-130">This requirement is specified with the `SessionMode` property on the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span>  
  
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
  
### <a name="controlling-the-lifetime-of-a-transactional-service-instance"></a><span data-ttu-id="a883c-131">Řízení životnosti instance transakční služby</span><span class="sxs-lookup"><span data-stu-id="a883c-131">Controlling the lifetime of a transactional service instance</span></span>  
  
1. <span data-ttu-id="a883c-132">Služba WCF používá <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> vlastnost k určení, zda je daná instance služby uvolněna při dokončení transakce.</span><span class="sxs-lookup"><span data-stu-id="a883c-132">WCF uses the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to specify whether the underlying service instance is released when a transaction completes.</span></span> <span data-ttu-id="a883c-133">Vzhledem k tomu, `true`že se jedná o výchozí nastavení, pokud není nakonfigurováno jinak, WCF vykazuje efektivní a předvídatelné chování aktivace za běhu.</span><span class="sxs-lookup"><span data-stu-id="a883c-133">Since this defaults to `true`, unless configured otherwise, WCF exhibits an efficient and predictable "just-in-time" activation behavior.</span></span> <span data-ttu-id="a883c-134">Volání služby v následné transakci jsou zaručena nová instance služby, která nemá žádné zbytky stavu předchozí transakce.</span><span class="sxs-lookup"><span data-stu-id="a883c-134">Calls to a service on a subsequent transaction are assured a new service instance with no remnants of the previous transaction's state.</span></span> <span data-ttu-id="a883c-135">I když je to často užitečné, někdy může být vhodné zachovat stav v rámci instance služby nad rámec dokončení transakce.</span><span class="sxs-lookup"><span data-stu-id="a883c-135">While this is often useful, sometimes you may want to maintain state within the service instance beyond the transaction completion.</span></span> <span data-ttu-id="a883c-136">Příklady by mohly být v případě, že je požadovaný stav nebo popisovač prostředků náročný na načtení nebo re.</span><span class="sxs-lookup"><span data-stu-id="a883c-136">Examples of this would be when required state or handles to resources are expensive to retrieve or reconstitute.</span></span> <span data-ttu-id="a883c-137">To můžete provést nastavením <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> vlastnosti na. `false`</span><span class="sxs-lookup"><span data-stu-id="a883c-137">You can do this by setting the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to `false`.</span></span> <span data-ttu-id="a883c-138">V takovém případě budou instance a všechny přidružené stavy k dispozici při následných voláních.</span><span class="sxs-lookup"><span data-stu-id="a883c-138">With that setting, the instance and any associated state will be available on subsequent calls.</span></span> <span data-ttu-id="a883c-139">Při použití tohoto postupu dejte pozor na to, kdy a jak se budou stavy a transakce vymazat a dokončit.</span><span class="sxs-lookup"><span data-stu-id="a883c-139">When using this, give careful consideration to when and how state and transactions will be cleared and completed.</span></span> <span data-ttu-id="a883c-140">Následující příklad ukazuje, jak to provést udržováním instance s `runningTotal` proměnnou.</span><span class="sxs-lookup"><span data-stu-id="a883c-140">The following sample demonstrates how to do this by maintaining the instance with the `runningTotal` variable.</span></span>  
  
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
    > <span data-ttu-id="a883c-141">Vzhledem k tomu, že doba životnosti instance je chování interní pro službu a je řízeno <xref:System.ServiceModel.ServiceBehaviorAttribute> prostřednictvím vlastnosti, není nutné upravovat konfiguraci služby ani kontrakt služby, aby bylo možné nastavit chování instance.</span><span class="sxs-lookup"><span data-stu-id="a883c-141">Since the instance lifetime is a behavior that is internal to the service, and controlled through the <xref:System.ServiceModel.ServiceBehaviorAttribute> property, no modification to the service configuration or service contract is required to set the instance behavior.</span></span> <span data-ttu-id="a883c-142">Kromě toho kabel nebude obsahovat žádné reprezentace.</span><span class="sxs-lookup"><span data-stu-id="a883c-142">In addition, the wire will contain no representation of this.</span></span>
