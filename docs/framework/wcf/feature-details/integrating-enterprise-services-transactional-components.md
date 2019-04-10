---
title: Integrace transakčních komponent služeb Enterprise Services
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 33e09eab1d7ad24dc234cfff21e352611e0b2ef9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202026"
---
# <a name="integrating-enterprise-services-transactional-components"></a><span data-ttu-id="8e814-102">Integrace transakčních komponent služeb Enterprise Services</span><span class="sxs-lookup"><span data-stu-id="8e814-102">Integrating Enterprise Services Transactional Components</span></span>
<span data-ttu-id="8e814-103">Windows Communication Foundation (WCF) poskytuje mechanismus automatického pro integraci se službami Enterprise (viz [integrace s aplikacemi modelu COM +](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)).</span><span class="sxs-lookup"><span data-stu-id="8e814-103">Windows Communication Foundation (WCF) provides an automatic mechanism for integrating with Enterprise Services (see [Integrating with COM+ Applications](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)).</span></span> <span data-ttu-id="8e814-104">Však můžete chtít flexibilitu pro vývoj služeb, které používají interně transakčních komponent, které jsou hostované v rámci podnikové služby.</span><span class="sxs-lookup"><span data-stu-id="8e814-104">However, you may want the flexibility to develop services that internally use transactional components hosted within Enterprise Services.</span></span> <span data-ttu-id="8e814-105">Protože funkce transakce WCF je založená na <xref:System.Transactions> infrastruktury, proces pro integraci podnikových služeb s použitím technologie WCF je stejná jako pro určení vzájemná funkční spolupráce mezi <xref:System.Transactions> a podnikových služeb, jak je uvedeno v [Interoperabilita se službami Enterprise Services a transakcemi COM +](https://go.microsoft.com/fwlink/?LinkId=94949).</span><span class="sxs-lookup"><span data-stu-id="8e814-105">Because the WCF Transactions feature is built on the <xref:System.Transactions> infrastructure, the process for integrating Enterprise Services with WCF is identical to that for specifying interoperability between <xref:System.Transactions> and Enterprise Services, as outlined in [Interoperability with Enterprise Services and COM+ Transactions](https://go.microsoft.com/fwlink/?LinkId=94949).</span></span>  
  
 <span data-ttu-id="8e814-106">K poskytování požadované úrovni vzájemná funkční spolupráce mezi sdružení příchozí transakce a transakce kontext modelu COM +, musíte vytvořit implementace služby <xref:System.Transactions.TransactionScope> instance a použijte příslušné hodnoty od <xref:System.Transactions.EnterpriseServicesInteropOption> výčtu.</span><span class="sxs-lookup"><span data-stu-id="8e814-106">To provide the desired level of interoperability between the incoming flowed transaction and the COM+ context transaction, the service implementation must create a <xref:System.Transactions.TransactionScope> instance and use the appropriate value from the <xref:System.Transactions.EnterpriseServicesInteropOption> enumeration.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a><span data-ttu-id="8e814-107">Integrace služby Enterprise s operací služby</span><span class="sxs-lookup"><span data-stu-id="8e814-107">Integrating Enterprise Services with a Service Operation</span></span>  
 <span data-ttu-id="8e814-108">Následující kód ukazuje operaci s toku transakcí povolené, který vytvoří <xref:System.Transactions.TransactionScope> s <xref:System.Transactions.EnterpriseServicesInteropOption.Full> možnost.</span><span class="sxs-lookup"><span data-stu-id="8e814-108">The following code demonstrates an operation, with Allowed transaction flow, that creates a <xref:System.Transactions.TransactionScope> with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> option.</span></span> <span data-ttu-id="8e814-109">V tomto případě platí následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="8e814-109">The following conditions apply in this scenario:</span></span>  
  
-   <span data-ttu-id="8e814-110">Pokud klient tok transakce, provádí se operace, včetně volání na komponentu podnikové služby v rámci oboru dané transakce.</span><span class="sxs-lookup"><span data-stu-id="8e814-110">If the client flows a transaction, the operation, including the call to the Enterprise Services component, is executed within the scope of that transaction.</span></span> <span data-ttu-id="8e814-111">Pomocí <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zajistí, že transakce se synchronizují s <xref:System.EnterpriseServices> kontextu, což znamená, že okolí transakce pro <xref:System.Transactions> a <xref:System.EnterpriseServices> je stejný.</span><span class="sxs-lookup"><span data-stu-id="8e814-111">Using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the transaction is synchronized with the <xref:System.EnterpriseServices> context, which means that the ambient transaction for <xref:System.Transactions> and the <xref:System.EnterpriseServices> is the same.</span></span>  
  
-   <span data-ttu-id="8e814-112">Pokud klient není tok transakce, nastavení <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> k `true` vytvoří nový obor transakce pro operace.</span><span class="sxs-lookup"><span data-stu-id="8e814-112">If the client does not flow a transaction, setting <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> to `true` creates a new transaction scope for the operation.</span></span> <span data-ttu-id="8e814-113">Podobně použití <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zajistí, že operace transakce je stejná jako transakce použitá uvnitř <xref:System.EnterpriseServices> kontextu komponenty.</span><span class="sxs-lookup"><span data-stu-id="8e814-113">Similarly, using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the operation’s transaction is the same as the transaction used inside the <xref:System.EnterpriseServices> component's context.</span></span>  
  
 <span data-ttu-id="8e814-114">Všechna volání další metodu dojít také v rámci oboru transakce stejné operace.</span><span class="sxs-lookup"><span data-stu-id="8e814-114">Any additional method calls also occur within the scope of the same operation’s transaction.</span></span>  
  
```  
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
  
 <span data-ttu-id="8e814-115">Pokud není žádná synchronizace musí být mezi aktuální transakce a volání transakčních komponent služeb Enterprise operace, použijte <xref:System.Transactions.EnterpriseServicesInteropOption.None> možnosti při vytváření instance <xref:System.Transactions.TransactionScope> instance.</span><span class="sxs-lookup"><span data-stu-id="8e814-115">If no synchronization is required between an operation’s current transaction and calls to transactional Enterprise Services components, then use the <xref:System.Transactions.EnterpriseServicesInteropOption.None> option when instantiating the <xref:System.Transactions.TransactionScope> instance.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-client"></a><span data-ttu-id="8e814-116">Integrace s klientem služby Enterprise</span><span class="sxs-lookup"><span data-stu-id="8e814-116">Integrating Enterprise Services with a Client</span></span>  
 <span data-ttu-id="8e814-117">Následující kód ukazuje použití kódu klienta <xref:System.Transactions.TransactionScope> instanci s <xref:System.Transactions.EnterpriseServicesInteropOption.Full> nastavení.</span><span class="sxs-lookup"><span data-stu-id="8e814-117">The following code demonstrates client code using a <xref:System.Transactions.TransactionScope> instance with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> setting.</span></span> <span data-ttu-id="8e814-118">V tomto scénáři dojde k volání operací služby, které podporují tok transakcí v rámci oboru stejné transakci jako volání součásti služby Enterprise.</span><span class="sxs-lookup"><span data-stu-id="8e814-118">In this scenario, calls to service operations that support transaction flow occur within the scope of the same transaction as the calls to Enterprise Services components.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="8e814-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e814-119">See also</span></span>

- [<span data-ttu-id="8e814-120">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="8e814-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="8e814-121">Integrace s aplikacemi modelu COM</span><span class="sxs-lookup"><span data-stu-id="8e814-121">Integrating with COM Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
