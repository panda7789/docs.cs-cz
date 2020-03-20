---
title: Integrace transakčních komponent služeb Enterprise Services
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 292573f911459d8a8419e09d81fd1e54dbc6c70b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184742"
---
# <a name="integrating-enterprise-services-transactional-components"></a><span data-ttu-id="f2563-102">Integrace transakčních komponent služeb Enterprise Services</span><span class="sxs-lookup"><span data-stu-id="f2563-102">Integrating Enterprise Services Transactional Components</span></span>

<span data-ttu-id="f2563-103">Windows Communication Foundation (WCF) poskytuje automatický mechanismus pro integraci s Enterprise Services (viz [Integrace s com+ aplikace).](integrating-with-com-plus-applications.md)</span><span class="sxs-lookup"><span data-stu-id="f2563-103">Windows Communication Foundation (WCF) provides an automatic mechanism for integrating with Enterprise Services (see [Integrating with COM+ Applications](integrating-with-com-plus-applications.md)).</span></span> <span data-ttu-id="f2563-104">Můžete však chtít flexibilitu při vývoji služeb, které interně používají transakční součásti hostované v rámci služeb Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="f2563-104">However, you may want the flexibility to develop services that internally use transactional components hosted within Enterprise Services.</span></span> <span data-ttu-id="f2563-105">Vzhledem k tomu, že funkce <xref:System.Transactions> WCF Transactions je postavena na infrastruktuře, proces integrace <xref:System.Transactions> podnikových služeb s WCF je shodný s procesem pro určení interoperability mezi a enterprise services, jak je uvedeno v [interoperabilitě s podnikovými službami a transakcemi modelu COM+](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="f2563-105">Because the WCF Transactions feature is built on the <xref:System.Transactions> infrastructure, the process for integrating Enterprise Services with WCF is identical to that for specifying interoperability between <xref:System.Transactions> and Enterprise Services, as outlined in [Interoperability with Enterprise Services and COM+ Transactions](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85)).</span></span>  
  
 <span data-ttu-id="f2563-106">Chcete-li poskytnout požadovanou úroveň interoperability mezi příchozí tok transakce a com + <xref:System.Transactions.TransactionScope> kontext transakce, implementace <xref:System.Transactions.EnterpriseServicesInteropOption> služby musí vytvořit instanci a použít příslušnou hodnotu z výčtu.</span><span class="sxs-lookup"><span data-stu-id="f2563-106">To provide the desired level of interoperability between the incoming flowed transaction and the COM+ context transaction, the service implementation must create a <xref:System.Transactions.TransactionScope> instance and use the appropriate value from the <xref:System.Transactions.EnterpriseServicesInteropOption> enumeration.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a><span data-ttu-id="f2563-107">Integrace podnikových služeb s operací služby</span><span class="sxs-lookup"><span data-stu-id="f2563-107">Integrating Enterprise Services with a Service Operation</span></span>  
 <span data-ttu-id="f2563-108">Následující kód ukazuje operaci s povoleným tokem <xref:System.Transactions.TransactionScope> transakce, která vytvoří s <xref:System.Transactions.EnterpriseServicesInteropOption.Full> možností.</span><span class="sxs-lookup"><span data-stu-id="f2563-108">The following code demonstrates an operation, with Allowed transaction flow, that creates a <xref:System.Transactions.TransactionScope> with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> option.</span></span> <span data-ttu-id="f2563-109">V tomto scénáři platí následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="f2563-109">The following conditions apply in this scenario:</span></span>  
  
- <span data-ttu-id="f2563-110">Pokud klient toky transakce, operace, včetně volání součásti Enterprise Services, je proveden v rámci této transakce.</span><span class="sxs-lookup"><span data-stu-id="f2563-110">If the client flows a transaction, the operation, including the call to the Enterprise Services component, is executed within the scope of that transaction.</span></span> <span data-ttu-id="f2563-111">Použití <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zajišťuje, že transakce je <xref:System.EnterpriseServices> synchronizována s kontextem, <xref:System.Transactions> což <xref:System.EnterpriseServices> znamená, že okolí transakce pro a je stejný.</span><span class="sxs-lookup"><span data-stu-id="f2563-111">Using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the transaction is synchronized with the <xref:System.EnterpriseServices> context, which means that the ambient transaction for <xref:System.Transactions> and the <xref:System.EnterpriseServices> is the same.</span></span>  
  
- <span data-ttu-id="f2563-112">Pokud klient netokuje transakci, nastavení <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> vytvoří `true` nový rozsah transakce pro operaci.</span><span class="sxs-lookup"><span data-stu-id="f2563-112">If the client does not flow a transaction, setting <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> to `true` creates a new transaction scope for the operation.</span></span> <span data-ttu-id="f2563-113">Podobně pomocí <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zajišťuje, že transakce operace je stejná jako transakce <xref:System.EnterpriseServices> použitá v kontextu komponenty.</span><span class="sxs-lookup"><span data-stu-id="f2563-113">Similarly, using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the operation’s transaction is the same as the transaction used inside the <xref:System.EnterpriseServices> component's context.</span></span>  
  
 <span data-ttu-id="f2563-114">Jakékoli další volání metody také dojít v rámci rozsahu transakce stejné operace.</span><span class="sxs-lookup"><span data-stu-id="f2563-114">Any additional method calls also occur within the scope of the same operation’s transaction.</span></span>  
  
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
  
 <span data-ttu-id="f2563-115">Pokud není vyžadována žádná synchronizace mezi aktuální transakcí operace a voláním transakčních součástí služby Enterprise Services, použijte <xref:System.Transactions.EnterpriseServicesInteropOption.None> tuto možnost při vytváření instancí. <xref:System.Transactions.TransactionScope></span><span class="sxs-lookup"><span data-stu-id="f2563-115">If no synchronization is required between an operation’s current transaction and calls to transactional Enterprise Services components, then use the <xref:System.Transactions.EnterpriseServicesInteropOption.None> option when instantiating the <xref:System.Transactions.TransactionScope> instance.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-client"></a><span data-ttu-id="f2563-116">Integrace podnikových služeb s klientem</span><span class="sxs-lookup"><span data-stu-id="f2563-116">Integrating Enterprise Services with a Client</span></span>  
 <span data-ttu-id="f2563-117">Následující kód ukazuje kód klienta <xref:System.Transactions.TransactionScope> pomocí <xref:System.Transactions.EnterpriseServicesInteropOption.Full> instance s nastavením.</span><span class="sxs-lookup"><span data-stu-id="f2563-117">The following code demonstrates client code using a <xref:System.Transactions.TransactionScope> instance with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> setting.</span></span> <span data-ttu-id="f2563-118">V tomto scénáři volání operací služby, které podporují tok transakcí dojít v rámci rozsahu stejné transakce jako volání součásti Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="f2563-118">In this scenario, calls to service operations that support transaction flow occur within the scope of the same transaction as the calls to Enterprise Services components.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f2563-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2563-119">See also</span></span>

- [<span data-ttu-id="f2563-120">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="f2563-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="f2563-121">Integrace s aplikacemi modelu COM</span><span class="sxs-lookup"><span data-stu-id="f2563-121">Integrating with COM Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
