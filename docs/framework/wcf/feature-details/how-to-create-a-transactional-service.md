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
# <a name="how-to-create-a-transactional-service"></a><span data-ttu-id="e05cb-102">Postupy: Vytvoření transakční služby</span><span class="sxs-lookup"><span data-stu-id="e05cb-102">How to: Create a Transactional Service</span></span>
<span data-ttu-id="e05cb-103">Tento příklad ukazuje různé aspekty vytvoření transakční služby a použití klientem iniciované transakci ke koordinaci operací služby.</span><span class="sxs-lookup"><span data-stu-id="e05cb-103">This sample demonstrates various aspects of creating a transactional service and the use of a client-initiated transaction to coordinate service operations.</span></span>  
  
### <a name="creating-a-transactional-service"></a><span data-ttu-id="e05cb-104">Vytvoření transakční služby</span><span class="sxs-lookup"><span data-stu-id="e05cb-104">Creating a transactional service</span></span>  
  
1. <span data-ttu-id="e05cb-105">Vytvoření kontraktu service a opatřovat je poznámkami operací pomocí požadovaného nastavení z <xref:System.ServiceModel.TransactionFlowOption> výčet k určení požadavků na příchozí transakce.</span><span class="sxs-lookup"><span data-stu-id="e05cb-105">Create a service contract and annotate the operations with the desired setting from the <xref:System.ServiceModel.TransactionFlowOption> enumeration to specify the incoming transaction requirements.</span></span> <span data-ttu-id="e05cb-106">Všimněte si, že můžete také umístit <xref:System.ServiceModel.TransactionFlowAttribute> na třídu služby se implementuje.</span><span class="sxs-lookup"><span data-stu-id="e05cb-106">Note that you can also place the <xref:System.ServiceModel.TransactionFlowAttribute> on the service class being implemented.</span></span> <span data-ttu-id="e05cb-107">To umožňuje jedna implementace rozhraní nahrazujícím každou implementaci těchto nastavení transakcí.</span><span class="sxs-lookup"><span data-stu-id="e05cb-107">This allows for a single implementation of an interface to use these transaction settings, instead of every implementation.</span></span>  
  
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
  
2. <span data-ttu-id="e05cb-108">Vytvoření třídy implementaci a použití <xref:System.ServiceModel.ServiceBehaviorAttribute> volitelně zadat <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span><span class="sxs-lookup"><span data-stu-id="e05cb-108">Create an implementation class, and use the <xref:System.ServiceModel.ServiceBehaviorAttribute> to optionally specify a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span></span> <span data-ttu-id="e05cb-109">Nezapomeňte přitom, která v mnoha případech se výchozí <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> 60 sekund a výchozí <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> z `Unspecified` jsou vhodné.</span><span class="sxs-lookup"><span data-stu-id="e05cb-109">You should note that in many cases, the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> of 60 seconds and the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> of `Unspecified` are appropriate.</span></span> <span data-ttu-id="e05cb-110">Pro každou operaci, můžete použít <xref:System.ServiceModel.OperationBehaviorAttribute> atribut udává, jestli pracovní provést v rámci metody se budou objevovat v rámci oboru transakce oboru podle hodnoty <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> atribut.</span><span class="sxs-lookup"><span data-stu-id="e05cb-110">For each operation, you can use the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute to specify whether work performed within the method should occur within the scope of a transaction scope according to the value of the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> attribute.</span></span> <span data-ttu-id="e05cb-111">V tomto případě používá transakce pro `Add` metodou je stejný jako povinné příchozí transakce, která je počet plynoucích z klienta a transakce pro `Subtract` metoda je buď stejná jako příchozí transakce, pokud jeden byla převedena z klienta, nebo implicitně a místně vytvořenou novou transakci.</span><span class="sxs-lookup"><span data-stu-id="e05cb-111">In this case, the transaction used for the `Add` method is the same as the mandatory incoming transaction that is flowed from the client, and the transaction used for the `Subtract` method is either the same as the incoming transaction if one was flowed from the client, or a new implicitly and locally created transaction.</span></span>  
  
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
  
3. <span data-ttu-id="e05cb-112">Nakonfigurujte vazby v konfiguračním souboru, určení, že by měl být předávány kontext transakce a protokolů, který se má použít k tomu.</span><span class="sxs-lookup"><span data-stu-id="e05cb-112">Configure the bindings in the configuration file, specifying that the transaction context should be flowed, and the protocols to be used to do so.</span></span> <span data-ttu-id="e05cb-113">Další informace najdete v tématu [konfigurace transakcí ServiceModel](servicemodel-transaction-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="e05cb-113">For more information, see [ServiceModel Transaction Configuration](servicemodel-transaction-configuration.md).</span></span> <span data-ttu-id="e05cb-114">Konkrétně je typ vazby zadaný v elementu koncového bodu `binding` atribut.</span><span class="sxs-lookup"><span data-stu-id="e05cb-114">Specifically, the binding type is specified in the endpoint element’s `binding` attribute.</span></span> <span data-ttu-id="e05cb-115">[ \<Koncový bod >](../../configure-apps/file-schema/wcf/endpoint-element.md) obsahuje element `bindingConfiguration` atribut, který odkazuje na vazbu konfigurace s názvem `transactionalOleTransactionsTcpBinding`, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="e05cb-115">The [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element contains a `bindingConfiguration` attribute that references a binding configuration named `transactionalOleTransactionsTcpBinding`, as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     <span data-ttu-id="e05cb-116">Je povolen tok transakcí na úrovni konfigurace s použitím `transactionFlow` atribut a transakční protokol je specifikován pomocí `transactionProtocol` atributu, jak je znázorněno v následující konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="e05cb-116">Transaction flow is enabled at the configuration level by using the `transactionFlow` attribute, and the transaction protocol is specified using the `transactionProtocol` attribute, as shown in the following configuration.</span></span>  
  
    ```xml  
    <bindings>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="supporting-multiple-transaction-protocols"></a><span data-ttu-id="e05cb-117">Podpora více protokolů transakcí</span><span class="sxs-lookup"><span data-stu-id="e05cb-117">Supporting multiple transaction protocols</span></span>  
  
1. <span data-ttu-id="e05cb-118">Pro zajištění optimálního výkonu abyste používali protokolu OleTransactions pro scénáře zahrnující klienta a služby, které jsou napsané s využitím Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e05cb-118">For optimal performance, you should use the OleTransactions protocol for scenarios involving a client and service written using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="e05cb-119">Protokol WS-AtomicTransaction (WS-AT) je však užitečné pro scénáře při vzájemná funkční spolupráce s sad protokolů třetích stran je povinný.</span><span class="sxs-lookup"><span data-stu-id="e05cb-119">However, the WS-AtomicTransaction (WS-AT) protocol is useful for scenarios when interoperability with third-party protocol stacks is required.</span></span> <span data-ttu-id="e05cb-120">Můžete nakonfigurovat WCF services tak, aby přijímal oba protokoly tím, že poskytuje několik koncových bodů s odpovídající konkrétní vazby, jak je znázorněno v následující ukázková konfigurace.</span><span class="sxs-lookup"><span data-stu-id="e05cb-120">You can configure WCF services to accept both protocols by providing multiple endpoints with appropriate protocol-specific bindings, as shown in the following sample configuration.</span></span>  
  
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
  
     <span data-ttu-id="e05cb-121">Transakční protokol je specifikován pomocí `transactionProtocol` atribut.</span><span class="sxs-lookup"><span data-stu-id="e05cb-121">The transaction protocol is specified using the `transactionProtocol` attribute.</span></span> <span data-ttu-id="e05cb-122">Nicméně, tento atribut chybí z poskytnuté systémem `wsHttpBinding`, protože tato vazba lze použít pouze WS-AT protokolu.</span><span class="sxs-lookup"><span data-stu-id="e05cb-122">However, this attribute is absent from the system-provided `wsHttpBinding`, because this binding can only use the WS-AT protocol.</span></span>  
  
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
  
### <a name="controlling-the-completion-of-a-transaction"></a><span data-ttu-id="e05cb-123">Řízení dokončení transakce</span><span class="sxs-lookup"><span data-stu-id="e05cb-123">Controlling the completion of a transaction</span></span>  
  
1. <span data-ttu-id="e05cb-124">Ve výchozím nastavení WCF operace automatického dokončení transakce, pokud nejsou vyvolány žádné neošetřené výjimky.</span><span class="sxs-lookup"><span data-stu-id="e05cb-124">By default, WCF operations automatically complete transactions if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="e05cb-125">Toto chování lze upravit pomocí <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> vlastnost a <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="e05cb-125">You can modify this behavior by using the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property and the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method.</span></span> <span data-ttu-id="e05cb-126">Při operaci musí dojít v rámci stejné transakce jako jiná operace (například operace MD a Dal), můžete zakázat automatické dokončování chování tak, že nastavíte <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> vlastnost `false` jak je znázorněno v následujícím `Debit` příklad operace.</span><span class="sxs-lookup"><span data-stu-id="e05cb-126">When an operation is required to occur within the same transaction as another operation (for example, a debit and credit operation), you can disable the autocomplete behavior by setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` as shown in the following `Debit` operation example.</span></span> <span data-ttu-id="e05cb-127">Transakce `Debit` používá operace nedokončí až do metody s <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> vlastnost nastavena na `true` je volána, jak je znázorněno v operaci `Credit1`, nebo když <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> explicitně označit je volána metoda transakce jako dokončené, jak je znázorněno v operaci `Credit2`.</span><span class="sxs-lookup"><span data-stu-id="e05cb-127">The transaction the `Debit` operation uses is not completed until a method with the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property set to `true` is called, as shown in the operation `Credit1`, or when the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method is called to explicitly mark the transaction as complete, as shown in the operation `Credit2`.</span></span> <span data-ttu-id="e05cb-128">Všimněte si, že dvě kredit operace jsou platné pro ilustraci a že jediného kredit ve výši operace by obvyklejší.</span><span class="sxs-lookup"><span data-stu-id="e05cb-128">Note that the two credit operations are shown for illustration purposes, and that a single credit operation would be more typical.</span></span>  
  
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
  
2. <span data-ttu-id="e05cb-129">Pro účely transakce korelace, nastavení <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> vlastnost `false` vyžaduje použití vazby s relacemi.</span><span class="sxs-lookup"><span data-stu-id="e05cb-129">For the purposes of transaction correlation, setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` requires the use of a sessionful binding.</span></span> <span data-ttu-id="e05cb-130">Tento požadavek není zadán s `SessionMode` vlastnost <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e05cb-130">This requirement is specified with the `SessionMode` property on the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span>  
  
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
  
### <a name="controlling-the-lifetime-of-a-transactional-service-instance"></a><span data-ttu-id="e05cb-131">Řízení životního cyklu instance transakční služby</span><span class="sxs-lookup"><span data-stu-id="e05cb-131">Controlling the lifetime of a transactional service instance</span></span>  
  
1. <span data-ttu-id="e05cb-132">Používá WCF <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> vlastnosti a určit, jestli se po dokončení transakce uvolní podkladové instance služby.</span><span class="sxs-lookup"><span data-stu-id="e05cb-132">WCF uses the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to specify whether the underlying service instance is released when a transaction completes.</span></span> <span data-ttu-id="e05cb-133">Protože je výchozí hodnota `true`, pokud se nenakonfiguruje, chování aktivace WCF dodatků efektivní a předvídatelné "just-in-time".</span><span class="sxs-lookup"><span data-stu-id="e05cb-133">Since this defaults to `true`, unless configured otherwise, WCF exhibits an efficient and predictable "just-in-time" activation behavior.</span></span> <span data-ttu-id="e05cb-134">Volání služby v následných transakcí je zajištěna nové instance služby s žádné zbývající součásti stav předchozí transakce.</span><span class="sxs-lookup"><span data-stu-id="e05cb-134">Calls to a service on a subsequent transaction are assured a new service instance with no remnants of the previous transaction's state.</span></span> <span data-ttu-id="e05cb-135">Když je často užitečné, někdy můžete udržovat stav v rámci instance služby nad rámec dokončení transakce.</span><span class="sxs-lookup"><span data-stu-id="e05cb-135">While this is often useful, sometimes you may want to maintain state within the service instance beyond the transaction completion.</span></span> <span data-ttu-id="e05cb-136">Příklady by po drahé načíst nebo znovuvytvoření požadovaného stavu nebo popisovače k prostředkům.</span><span class="sxs-lookup"><span data-stu-id="e05cb-136">Examples of this would be when required state or handles to resources are expensive to retrieve or reconstitute.</span></span> <span data-ttu-id="e05cb-137">Můžete to provést tak, že nastavíte <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="e05cb-137">You can do this by setting the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to `false`.</span></span> <span data-ttu-id="e05cb-138">Při tomto nastavení instance a všechny přidružené stavu budou dostupné v následných voláních.</span><span class="sxs-lookup"><span data-stu-id="e05cb-138">With that setting, the instance and any associated state will be available on subsequent calls.</span></span> <span data-ttu-id="e05cb-139">Při použití této funkce, věnujte pozornost pozor, kdy a jak stavu a transakce budou vymazána a dokončit.</span><span class="sxs-lookup"><span data-stu-id="e05cb-139">When using this, give careful consideration to when and how state and transactions will be cleared and completed.</span></span> <span data-ttu-id="e05cb-140">Následující příklad ukazuje, jak to provést pomocí instance s `runningTotal` proměnné.</span><span class="sxs-lookup"><span data-stu-id="e05cb-140">The following sample demonstrates how to do this by maintaining the instance with the `runningTotal` variable.</span></span>  
  
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
    >  <span data-ttu-id="e05cb-141">Protože životnost instance je chování, které je interní ke službě a řízené prostřednictvím <xref:System.ServiceModel.ServiceBehaviorAttribute> vlastnost, je vyžadovat, abyste nastavili chování instance bez změny konfigurace služby nebo kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="e05cb-141">Since the instance lifetime is a behavior that is internal to the service, and controlled through the <xref:System.ServiceModel.ServiceBehaviorAttribute> property, no modification to the service configuration or service contract is required to set the instance behavior.</span></span> <span data-ttu-id="e05cb-142">Kromě toho přenosu bude obsahovat žádné reprezentace.</span><span class="sxs-lookup"><span data-stu-id="e05cb-142">In addition, the wire will contain no representation of this.</span></span>
