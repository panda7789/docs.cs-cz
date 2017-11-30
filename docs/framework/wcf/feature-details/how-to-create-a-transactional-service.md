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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a7ef8d4778b21d33501e3f3d4478b722bf1e1cc3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-transactional-service"></a><span data-ttu-id="82d79-102">Postupy: Vytvoření transakční služby</span><span class="sxs-lookup"><span data-stu-id="82d79-102">How to: Create a Transactional Service</span></span>
<span data-ttu-id="82d79-103">Tento příklad znázorňuje různé aspekty vytvoření transakční služby a použití transakci iniciované klientem ke koordinaci operací služby.</span><span class="sxs-lookup"><span data-stu-id="82d79-103">This sample demonstrates various aspects of creating a transactional service and the use of a client-initiated transaction to coordinate service operations.</span></span>  
  
### <a name="creating-a-transactional-service"></a><span data-ttu-id="82d79-104">Vytvoření transakční služby</span><span class="sxs-lookup"><span data-stu-id="82d79-104">Creating a transactional service</span></span>  
  
1.  <span data-ttu-id="82d79-105">Vytvoření kontraktu služby a opatřit poznámkami operací s požadované nastavení z <xref:System.ServiceModel.TransactionFlowOption> výčtu k určení požadavků na příchozí transakce.</span><span class="sxs-lookup"><span data-stu-id="82d79-105">Create a service contract and annotate the operations with the desired setting from the <xref:System.ServiceModel.TransactionFlowOption> enumeration to specify the incoming transaction requirements.</span></span> <span data-ttu-id="82d79-106">Všimněte si, že můžete taky umístit <xref:System.ServiceModel.TransactionFlowAttribute> na třídě služby se implementuje.</span><span class="sxs-lookup"><span data-stu-id="82d79-106">Note that you can also place the <xref:System.ServiceModel.TransactionFlowAttribute> on the service class being implemented.</span></span> <span data-ttu-id="82d79-107">To umožňuje jediná implementace typu rozhraní pro použití těchto nastavení transakcí místo každých implementace.</span><span class="sxs-lookup"><span data-stu-id="82d79-107">This allows for a single implementation of an interface to use these transaction settings, instead of every implementation.</span></span>  
  
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
  
2.  <span data-ttu-id="82d79-108">Vytvoření třídy implementaci a použít <xref:System.ServiceModel.ServiceBehaviorAttribute> volitelně zadat <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span><span class="sxs-lookup"><span data-stu-id="82d79-108">Create an implementation class, and use the <xref:System.ServiceModel.ServiceBehaviorAttribute> to optionally specify a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span></span> <span data-ttu-id="82d79-109">Upozorňujeme ale, který v mnoha případech výchozí <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> 60 sekund a výchozí <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> z `Unspecified` jsou vhodné.</span><span class="sxs-lookup"><span data-stu-id="82d79-109">You should note that in many cases, the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> of 60 seconds and the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> of `Unspecified` are appropriate.</span></span> <span data-ttu-id="82d79-110">Pro každou operaci, můžete použít <xref:System.ServiceModel.OperationBehaviorAttribute> atribut k určení, zda pracovní provede v rámci metody provedeno v rámci oboru oboru transakce podle hodnoty <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> atribut.</span><span class="sxs-lookup"><span data-stu-id="82d79-110">For each operation, you can use the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute to specify whether work performed within the method should occur within the scope of a transaction scope according to the value of the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> attribute.</span></span> <span data-ttu-id="82d79-111">V takovém případě transakce používá pro `Add` metoda je stejný jako povinné příchozí transakce, která je plynoucích z klienta a transakce pro `Subtract` metoda je buď stejné, jako příchozí transakce když jeden byl plynoucích z klienta, nebo novou transakci implicitně a místně vytvořené.</span><span class="sxs-lookup"><span data-stu-id="82d79-111">In this case, the transaction used for the `Add` method is the same as the mandatory incoming transaction that is flowed from the client, and the transaction used for the `Subtract` method is either the same as the incoming transaction if one was flowed from the client, or a new implicitly and locally created transaction.</span></span>  
  
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
  
3.  <span data-ttu-id="82d79-112">V konfiguračním souboru, určující, zda by měl plynoucích kontext transakce a protokoly, který se má použít k tomu, nakonfigurujte vazby.</span><span class="sxs-lookup"><span data-stu-id="82d79-112">Configure the bindings in the configuration file, specifying that the transaction context should be flowed, and the protocols to be used to do so.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="82d79-113">[Konfigurace transakcí ServiceModel](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="82d79-113"> [ServiceModel Transaction Configuration](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md).</span></span> <span data-ttu-id="82d79-114">Konkrétně je typ vazby zadaný v elementu koncový bod `binding` atribut.</span><span class="sxs-lookup"><span data-stu-id="82d79-114">Specifically, the binding type is specified in the endpoint element’s `binding` attribute.</span></span> <span data-ttu-id="82d79-115">[ \<Endpoint >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) obsahuje element `bindingConfiguration` atribut, který odkazuje na vazbu konfigurace s názvem `transactionalOleTransactionsTcpBinding`, jak ukazuje následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="82d79-115">The [\<endpoint>](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element contains a `bindingConfiguration` attribute that references a binding configuration named `transactionalOleTransactionsTcpBinding`, as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     <span data-ttu-id="82d79-116">Tok transakcí je povolena na úrovni konfigurace pomocí `transactionFlow` atribut a protokol transakcí je zadán pomocí `transactionProtocol` atributu, jak je znázorněno v následující konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="82d79-116">Transaction flow is enabled at the configuration level by using the `transactionFlow` attribute, and the transaction protocol is specified using the `transactionProtocol` attribute, as shown in the following configuration.</span></span>  
  
    ```xml  
    <bindings>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="supporting-multiple-transaction-protocols"></a><span data-ttu-id="82d79-117">Podpora více protokoly transakcí</span><span class="sxs-lookup"><span data-stu-id="82d79-117">Supporting multiple transaction protocols</span></span>  
  
1.  <span data-ttu-id="82d79-118">Pro optimální výkon, musí používat protokol OleTransactions pro scénáře zahrnující klienta a služby napsané pomocí [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="82d79-118">For optimal performance, you should use the OleTransactions protocol for scenarios involving a client and service written using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="82d79-119">Protokol WS-AtomicTransaction (WS-AT) je však užitečné v případech, pokud je potřeba vzájemná funkční spolupráce s zásobníky protokol třetích stran.</span><span class="sxs-lookup"><span data-stu-id="82d79-119">However, the WS-AtomicTransaction (WS-AT) protocol is useful for scenarios when interoperability with third-party protocol stacks is required.</span></span> <span data-ttu-id="82d79-120">Můžete nakonfigurovat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby tak, aby přijímal oba protokoly poskytováním více koncových bodů s příslušnou specifické pro protokol vazby, jak je znázorněno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="82d79-120">You can configure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services to accept both protocols by providing multiple endpoints with appropriate protocol-specific bindings, as shown in the following sample configuration.</span></span>  
  
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
  
     <span data-ttu-id="82d79-121">Protokol transakce je zadán pomocí `transactionProtocol` atribut.</span><span class="sxs-lookup"><span data-stu-id="82d79-121">The transaction protocol is specified using the `transactionProtocol` attribute.</span></span> <span data-ttu-id="82d79-122">Tento atribut je však chybí z poskytované systémem `wsHttpBinding`, protože tuto vazbu lze použít pouze protokol WS-AT.</span><span class="sxs-lookup"><span data-stu-id="82d79-122">However, this attribute is absent from the system-provided `wsHttpBinding`, because this binding can only use the WS-AT protocol.</span></span>  
  
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
  
### <a name="controlling-the-completion-of-a-transaction"></a><span data-ttu-id="82d79-123">Řízení dokončení transakce.</span><span class="sxs-lookup"><span data-stu-id="82d79-123">Controlling the completion of a transaction</span></span>  
  
1.  <span data-ttu-id="82d79-124">Ve výchozím nastavení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] operace automaticky dokončit transakce, pokud jsou vyvolány žádné neošetřené výjimky.</span><span class="sxs-lookup"><span data-stu-id="82d79-124">By default, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] operations automatically complete transactions if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="82d79-125">Toto chování můžete upravit pomocí <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> vlastnost a <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="82d79-125">You can modify this behavior by using the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property and the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method.</span></span> <span data-ttu-id="82d79-126">Když operace je potřeba v rámci stejné transakci jako jiná operace (například operace MD a Dal), můžete zakázat chování automatického dokončování nastavením <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> vlastnost `false` jak je znázorněno v následujícím `Debit` příklad operaci.</span><span class="sxs-lookup"><span data-stu-id="82d79-126">When an operation is required to occur within the same transaction as another operation (for example, a debit and credit operation), you can disable the autocomplete behavior by setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` as shown in the following `Debit` operation example.</span></span> <span data-ttu-id="82d79-127">Transakce `Debit` není používá operaci dokončit, dokud nebudou metodu s <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> vlastnost nastavena na hodnotu `true` je volána, jak je znázorněno v operaci `Credit1`, nebo když <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> metoda je volána explicitně označit transakce jako dokončené, jak je znázorněno v operaci `Credit2`.</span><span class="sxs-lookup"><span data-stu-id="82d79-127">The transaction the `Debit` operation uses is not completed until a method with the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property set to `true` is called, as shown in the operation `Credit1`, or when the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method is called to explicitly mark the transaction as complete, as shown in the operation `Credit2`.</span></span> <span data-ttu-id="82d79-128">Upozorňujeme, že pro účely obrázku jsou zobrazeny dvě platební operace a že jeden úvěrového operace by typičtější.</span><span class="sxs-lookup"><span data-stu-id="82d79-128">Note that the two credit operations are shown for illustration purposes, and that a single credit operation would be more typical.</span></span>  
  
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
  
2.  <span data-ttu-id="82d79-129">Pro účely korelace transakce, nastavení <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> vlastnost `false` vyžaduje použití relacemi vazby.</span><span class="sxs-lookup"><span data-stu-id="82d79-129">For the purposes of transaction correlation, setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` requires the use of a sessionful binding.</span></span> <span data-ttu-id="82d79-130">Tento požadavek zadaný `SessionMode` vlastnost <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="82d79-130">This requirement is specified with the `SessionMode` property on the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span>  
  
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
  
### <a name="controlling-the-lifetime-of-a-transactional-service-instance"></a><span data-ttu-id="82d79-131">Řízení životního cyklu instance služby zasílání transakčních</span><span class="sxs-lookup"><span data-stu-id="82d79-131">Controlling the lifetime of a transactional service instance</span></span>  
  
1.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="82d79-132">používá <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> vlastnosti k určení, zda je základní instance služby vydané po dokončení transakce.</span><span class="sxs-lookup"><span data-stu-id="82d79-132"> uses the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to specify whether the underlying service instance is released when a transaction completes.</span></span> <span data-ttu-id="82d79-133">Vzhledem k tomu, že se `true`, pokud není uvedeno jinak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vykazuje aktivaci "v běhu" efektivní a předvídatelné chování.</span><span class="sxs-lookup"><span data-stu-id="82d79-133">Since this defaults to `true`, unless configured otherwise, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] exhibits an efficient and predictable "just-in-time" activation behavior.</span></span> <span data-ttu-id="82d79-134">Volání do služby na následné transakce jsou zajištěná nové instance služby se žádné zbytky stav předchozí transakce.</span><span class="sxs-lookup"><span data-stu-id="82d79-134">Calls to a service on a subsequent transaction are assured a new service instance with no remnants of the previous transaction's state.</span></span> <span data-ttu-id="82d79-135">Přestože se často užitečné, v některých případech může chcete zachovat stav v rámci instance služby nad rámec dokončení transakce.</span><span class="sxs-lookup"><span data-stu-id="82d79-135">While this is often useful, sometimes you may want to maintain state within the service instance beyond the transaction completion.</span></span> <span data-ttu-id="82d79-136">Příklady tohoto by po nákladné načíst nebo rekonstruovat požadované stavu nebo obslužných rutin k prostředkům.</span><span class="sxs-lookup"><span data-stu-id="82d79-136">Examples of this would be when required state or handles to resources are expensive to retrieve or reconstitute.</span></span> <span data-ttu-id="82d79-137">To provedete nastavením <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="82d79-137">You can do this by setting the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to `false`.</span></span> <span data-ttu-id="82d79-138">Toto nastavení, instanci a všechny přidružené stavu bude k dispozici pro následující volání.</span><span class="sxs-lookup"><span data-stu-id="82d79-138">With that setting, the instance and any associated state will be available on subsequent calls.</span></span> <span data-ttu-id="82d79-139">Při použití tohoto nástroje věnujte pozornost pozor, kdy a jak stavu a transakce budou vymazána a dokončit.</span><span class="sxs-lookup"><span data-stu-id="82d79-139">When using this, give careful consideration to when and how state and transactions will be cleared and completed.</span></span> <span data-ttu-id="82d79-140">Následující příklad ukazuje, jak to udělat Údržba instance s `runningTotal` proměnné.</span><span class="sxs-lookup"><span data-stu-id="82d79-140">The following sample demonstrates how to do this by maintaining the instance with the `runningTotal` variable.</span></span>  
  
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
    >  <span data-ttu-id="82d79-141">Vzhledem k tomu, že instance životnost je chování, které je interní ke službě a řízené prostřednictvím <xref:System.ServiceModel.ServiceBehaviorAttribute> vlastnost žádné změny konfigurace služby ani kontrakt služby je potřeba nastavit chování instance.</span><span class="sxs-lookup"><span data-stu-id="82d79-141">Since the instance lifetime is a behavior that is internal to the service, and controlled through the <xref:System.ServiceModel.ServiceBehaviorAttribute> property, no modification to the service configuration or service contract is required to set the instance behavior.</span></span> <span data-ttu-id="82d79-142">Kromě toho sítě bude obsahovat žádné reprezentace tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="82d79-142">In addition, the wire will contain no representation of this.</span></span>
