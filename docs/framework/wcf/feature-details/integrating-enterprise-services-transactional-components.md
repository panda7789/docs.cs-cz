---
title: Integrace transakčních komponent služeb Enterprise Services
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: c73be31bef67f1de818f7b04181a3540bbd7caa8
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991538"
---
# <a name="integrating-enterprise-services-transactional-components"></a><span data-ttu-id="9f963-102">Integrace transakčních komponent služeb Enterprise Services</span><span class="sxs-lookup"><span data-stu-id="9f963-102">Integrating Enterprise Services Transactional Components</span></span>
<span data-ttu-id="9f963-103">Windows Communication Foundation (WCF) poskytuje automatický mechanismus pro integraci s podnikovými službami (viz [integrace s aplikacemi modelu COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)).</span><span class="sxs-lookup"><span data-stu-id="9f963-103">Windows Communication Foundation (WCF) provides an automatic mechanism for integrating with Enterprise Services (see [Integrating with COM+ Applications](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)).</span></span> <span data-ttu-id="9f963-104">Je ale možné, že budete chtít pružně vyvíjet služby, které interně využívají transakční komponenty hostované v rámci podnikových služeb.</span><span class="sxs-lookup"><span data-stu-id="9f963-104">However, you may want the flexibility to develop services that internally use transactional components hosted within Enterprise Services.</span></span> <span data-ttu-id="9f963-105">Vzhledem k tomu, že funkce transakcí WCF je <xref:System.Transactions> postavená na infrastruktuře, proces pro integraci podnikových služeb se službou WCF je stejný jako při <xref:System.Transactions> určování interoperability mezi službami a podnikovými službami, jak je uvedeno v části. [Interoperabilita se službami Enterprise Services a transakcemi com+](https://go.microsoft.com/fwlink/?LinkId=94949).</span><span class="sxs-lookup"><span data-stu-id="9f963-105">Because the WCF Transactions feature is built on the <xref:System.Transactions> infrastructure, the process for integrating Enterprise Services with WCF is identical to that for specifying interoperability between <xref:System.Transactions> and Enterprise Services, as outlined in [Interoperability with Enterprise Services and COM+ Transactions](https://go.microsoft.com/fwlink/?LinkId=94949).</span></span>  
  
 <span data-ttu-id="9f963-106">Aby byla zajištěna požadovaná úroveň vzájemné funkční spolupráce mezi příchozí transakcí toku a transakcemi kontextu modelu COM+, musí implementace služby vytvořit <xref:System.Transactions.TransactionScope> instanci a použít příslušnou hodnotu <xref:System.Transactions.EnterpriseServicesInteropOption> z výčtu.</span><span class="sxs-lookup"><span data-stu-id="9f963-106">To provide the desired level of interoperability between the incoming flowed transaction and the COM+ context transaction, the service implementation must create a <xref:System.Transactions.TransactionScope> instance and use the appropriate value from the <xref:System.Transactions.EnterpriseServicesInteropOption> enumeration.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a><span data-ttu-id="9f963-107">Integrace služeb Enterprise Services s operací služby</span><span class="sxs-lookup"><span data-stu-id="9f963-107">Integrating Enterprise Services with a Service Operation</span></span>  
 <span data-ttu-id="9f963-108">Následující kód demonstruje operaci s povoleným tokem transakce, která vytvoří <xref:System.Transactions.TransactionScope> <xref:System.Transactions.EnterpriseServicesInteropOption.Full> s možností.</span><span class="sxs-lookup"><span data-stu-id="9f963-108">The following code demonstrates an operation, with Allowed transaction flow, that creates a <xref:System.Transactions.TransactionScope> with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> option.</span></span> <span data-ttu-id="9f963-109">V tomto scénáři platí následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="9f963-109">The following conditions apply in this scenario:</span></span>  
  
- <span data-ttu-id="9f963-110">Pokud klient natéká transakci, operace, včetně volání do komponenty Enterprise Services, se spustí v rámci této transakce.</span><span class="sxs-lookup"><span data-stu-id="9f963-110">If the client flows a transaction, the operation, including the call to the Enterprise Services component, is executed within the scope of that transaction.</span></span> <span data-ttu-id="9f963-111">Pomocí <xref:System.Transactions.EnterpriseServicesInteropOption.Full> nástroje je zajištěno, že transakce je <xref:System.EnterpriseServices> synchronizována s kontextem, což znamená, <xref:System.Transactions> že <xref:System.EnterpriseServices> ambientní transakce pro a je stejná.</span><span class="sxs-lookup"><span data-stu-id="9f963-111">Using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the transaction is synchronized with the <xref:System.EnterpriseServices> context, which means that the ambient transaction for <xref:System.Transactions> and the <xref:System.EnterpriseServices> is the same.</span></span>  
  
- <span data-ttu-id="9f963-112">Pokud klient neflowe transakci, nastavení <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> `true` vytvoří nový obor transakce pro operaci.</span><span class="sxs-lookup"><span data-stu-id="9f963-112">If the client does not flow a transaction, setting <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> to `true` creates a new transaction scope for the operation.</span></span> <span data-ttu-id="9f963-113">Podobně použití <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zajistí, že transakce operace je shodná s transakcí použitou <xref:System.EnterpriseServices> v kontextu součásti.</span><span class="sxs-lookup"><span data-stu-id="9f963-113">Similarly, using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the operation’s transaction is the same as the transaction used inside the <xref:System.EnterpriseServices> component's context.</span></span>  
  
 <span data-ttu-id="9f963-114">K dalším voláním metody dojde také v rámci oboru transakce stejné operace.</span><span class="sxs-lookup"><span data-stu-id="9f963-114">Any additional method calls also occur within the scope of the same operation’s transaction.</span></span>  
  
```csharp
[ServiceContract()]  
public interface ICustomerServiceContract  
{  
   [OperationContract]  
   [TransactionFlow(TransactionFlowOption.Allowed)]  
   void UpdateCustomerNameOperation(int customerID, string newCustomerName);  
}  
  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CustomerService : ICustomerServiceContract  
{  
   [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
   public void UpdateCustomerNameOperation(int customerID, string newCustomerName)  
   {  
   // Create a transaction scope with full ES interop  
      using (TransactionScope ts = new TransactionScope(  
                     TransactionScopeOption.Required,  
                     new TransactionOptions(),  
                     EnterpriseServicesInteropOption.Full))  
      {  
         // Create an Enterprise Services component  
         // Call UpdateCustomer method on an Enterprise Services   
         // component   
  
         // Call UpdateOtherCustomerData method on an Enterprise   
         // Services component   
         ts.Complete();  
      }  
  
      // Do UpdateAdditionalData on an non-Enterprise Services  
      // component  
   }  
}  
```  
  
 <span data-ttu-id="9f963-115">Pokud mezi aktuální transakcí operace není vyžadována žádná synchronizace a volání součástí transakčních služeb Enterprise Services, použijte <xref:System.Transactions.EnterpriseServicesInteropOption.None> při vytváření <xref:System.Transactions.TransactionScope> instance instance možnost.</span><span class="sxs-lookup"><span data-stu-id="9f963-115">If no synchronization is required between an operation’s current transaction and calls to transactional Enterprise Services components, then use the <xref:System.Transactions.EnterpriseServicesInteropOption.None> option when instantiating the <xref:System.Transactions.TransactionScope> instance.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-client"></a><span data-ttu-id="9f963-116">Integrace podnikových služeb s klientem</span><span class="sxs-lookup"><span data-stu-id="9f963-116">Integrating Enterprise Services with a Client</span></span>  
 <span data-ttu-id="9f963-117">Následující kód demonstruje klientský kód pomocí <xref:System.Transactions.TransactionScope> instance <xref:System.Transactions.EnterpriseServicesInteropOption.Full> s nastavením.</span><span class="sxs-lookup"><span data-stu-id="9f963-117">The following code demonstrates client code using a <xref:System.Transactions.TransactionScope> instance with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> setting.</span></span> <span data-ttu-id="9f963-118">V tomto scénáři volání služeb, které podporují tok transakce, dochází v rámci oboru stejné transakce jako volání součástí služeb Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="9f963-118">In this scenario, calls to service operations that support transaction flow occur within the scope of the same transaction as the calls to Enterprise Services components.</span></span>  
  
```csharp
static void Main()  
{  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
  
    // Create a transaction scope with full ES interop  
    using (TransactionScope ts = new TransactionScope(  
          TransactionScopeOption.Required,  
          new TransactionOptions(),  
          EnterpriseServicesInteropOption.Full))  
    {  
        // Call Add calculator service operation  
  
        // Create an Enterprise Services component  
  
        // Call UpdateCustomer method on an Enterprise Services   
        // component   
  
        ts.Complete();  
    }  
  
    // Closing the client gracefully closes the connection and   
    // cleans up resources  
    client.Close();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f963-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f963-119">See also</span></span>

- [<span data-ttu-id="9f963-120">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="9f963-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="9f963-121">Integrace s aplikacemi modelu COM</span><span class="sxs-lookup"><span data-stu-id="9f963-121">Integrating with COM Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
