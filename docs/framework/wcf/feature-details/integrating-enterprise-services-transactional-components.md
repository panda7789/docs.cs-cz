---
title: Integrace transakčních komponent služeb Enterprise Services
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 1c4fabfadb113c79b216fa10ff80b551ba0f9716
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596848"
---
# <a name="integrating-enterprise-services-transactional-components"></a><span data-ttu-id="e3143-102">Integrace transakčních komponent služeb Enterprise Services</span><span class="sxs-lookup"><span data-stu-id="e3143-102">Integrating Enterprise Services Transactional Components</span></span>

<span data-ttu-id="e3143-103">Windows Communication Foundation (WCF) poskytuje automatický mechanismus pro integraci s podnikovými službami (viz [integrace s aplikacemi modelu COM+](integrating-with-com-plus-applications.md)).</span><span class="sxs-lookup"><span data-stu-id="e3143-103">Windows Communication Foundation (WCF) provides an automatic mechanism for integrating with Enterprise Services (see [Integrating with COM+ Applications](integrating-with-com-plus-applications.md)).</span></span> <span data-ttu-id="e3143-104">Je ale možné, že budete chtít pružně vyvíjet služby, které interně využívají transakční komponenty hostované v rámci podnikových služeb.</span><span class="sxs-lookup"><span data-stu-id="e3143-104">However, you may want the flexibility to develop services that internally use transactional components hosted within Enterprise Services.</span></span> <span data-ttu-id="e3143-105">Vzhledem k tomu, že je funkce transakcí WCF postavená na <xref:System.Transactions> infrastruktuře, proces pro integraci podnikových služeb se službou WCF je stejný jako při určování interoperability mezi <xref:System.Transactions> službami a podnikovými službami, jak je uvedeno v [interoperabilitě se službami Enterprise Services a transakcemi com+](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="e3143-105">Because the WCF Transactions feature is built on the <xref:System.Transactions> infrastructure, the process for integrating Enterprise Services with WCF is identical to that for specifying interoperability between <xref:System.Transactions> and Enterprise Services, as outlined in [Interoperability with Enterprise Services and COM+ Transactions](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85)).</span></span>  
  
 <span data-ttu-id="e3143-106">Aby byla zajištěna požadovaná úroveň vzájemné funkční spolupráce mezi příchozí transakcí toku a transakcemi kontextu modelu COM+, musí implementace služby vytvořit <xref:System.Transactions.TransactionScope> instanci a použít příslušnou hodnotu z <xref:System.Transactions.EnterpriseServicesInteropOption> výčtu.</span><span class="sxs-lookup"><span data-stu-id="e3143-106">To provide the desired level of interoperability between the incoming flowed transaction and the COM+ context transaction, the service implementation must create a <xref:System.Transactions.TransactionScope> instance and use the appropriate value from the <xref:System.Transactions.EnterpriseServicesInteropOption> enumeration.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a><span data-ttu-id="e3143-107">Integrace služeb Enterprise Services s operací služby</span><span class="sxs-lookup"><span data-stu-id="e3143-107">Integrating Enterprise Services with a Service Operation</span></span>  
 <span data-ttu-id="e3143-108">Následující kód demonstruje operaci s povoleným tokem transakce, která vytvoří <xref:System.Transactions.TransactionScope> s <xref:System.Transactions.EnterpriseServicesInteropOption.Full> možností.</span><span class="sxs-lookup"><span data-stu-id="e3143-108">The following code demonstrates an operation, with Allowed transaction flow, that creates a <xref:System.Transactions.TransactionScope> with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> option.</span></span> <span data-ttu-id="e3143-109">V tomto scénáři platí následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="e3143-109">The following conditions apply in this scenario:</span></span>  
  
- <span data-ttu-id="e3143-110">Pokud klient natéká transakci, operace, včetně volání do komponenty Enterprise Services, se spustí v rámci této transakce.</span><span class="sxs-lookup"><span data-stu-id="e3143-110">If the client flows a transaction, the operation, including the call to the Enterprise Services component, is executed within the scope of that transaction.</span></span> <span data-ttu-id="e3143-111">Pomocí nástroje je <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zajištěno, že transakce je synchronizována s <xref:System.EnterpriseServices> kontextem, což znamená, že ambientní transakce pro <xref:System.Transactions> a <xref:System.EnterpriseServices> je stejná.</span><span class="sxs-lookup"><span data-stu-id="e3143-111">Using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the transaction is synchronized with the <xref:System.EnterpriseServices> context, which means that the ambient transaction for <xref:System.Transactions> and the <xref:System.EnterpriseServices> is the same.</span></span>  
  
- <span data-ttu-id="e3143-112">Pokud klient neflowe transakci, nastavení <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> `true` vytvoří nový obor transakce pro operaci.</span><span class="sxs-lookup"><span data-stu-id="e3143-112">If the client does not flow a transaction, setting <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> to `true` creates a new transaction scope for the operation.</span></span> <span data-ttu-id="e3143-113">Podobně použití <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zajistí, že transakce operace je shodná s transakcí použitou v <xref:System.EnterpriseServices> kontextu součásti.</span><span class="sxs-lookup"><span data-stu-id="e3143-113">Similarly, using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the operation’s transaction is the same as the transaction used inside the <xref:System.EnterpriseServices> component's context.</span></span>  
  
 <span data-ttu-id="e3143-114">K dalším voláním metody dojde také v rámci oboru transakce stejné operace.</span><span class="sxs-lookup"><span data-stu-id="e3143-114">Any additional method calls also occur within the scope of the same operation’s transaction.</span></span>  
  
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
  
 <span data-ttu-id="e3143-115">Pokud mezi aktuální transakcí operace není vyžadována žádná synchronizace a volání součástí transakčních služeb Enterprise Services, použijte <xref:System.Transactions.EnterpriseServicesInteropOption.None> při vytváření instance <xref:System.Transactions.TransactionScope> instance možnost.</span><span class="sxs-lookup"><span data-stu-id="e3143-115">If no synchronization is required between an operation’s current transaction and calls to transactional Enterprise Services components, then use the <xref:System.Transactions.EnterpriseServicesInteropOption.None> option when instantiating the <xref:System.Transactions.TransactionScope> instance.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-client"></a><span data-ttu-id="e3143-116">Integrace podnikových služeb s klientem</span><span class="sxs-lookup"><span data-stu-id="e3143-116">Integrating Enterprise Services with a Client</span></span>  
 <span data-ttu-id="e3143-117">Následující kód demonstruje klientský kód pomocí <xref:System.Transactions.TransactionScope> instance s <xref:System.Transactions.EnterpriseServicesInteropOption.Full> nastavením.</span><span class="sxs-lookup"><span data-stu-id="e3143-117">The following code demonstrates client code using a <xref:System.Transactions.TransactionScope> instance with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> setting.</span></span> <span data-ttu-id="e3143-118">V tomto scénáři volání služeb, které podporují tok transakce, dochází v rámci oboru stejné transakce jako volání součástí služeb Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="e3143-118">In this scenario, calls to service operations that support transaction flow occur within the scope of the same transaction as the calls to Enterprise Services components.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e3143-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="e3143-119">See also</span></span>

- [<span data-ttu-id="e3143-120">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="e3143-120">Integrating with COM+ Applications</span></span>](integrating-with-com-plus-applications.md)
- [<span data-ttu-id="e3143-121">Integrace s aplikacemi modelu COM</span><span class="sxs-lookup"><span data-stu-id="e3143-121">Integrating with COM Applications</span></span>](integrating-with-com-applications.md)
