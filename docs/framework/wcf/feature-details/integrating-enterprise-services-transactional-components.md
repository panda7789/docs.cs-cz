---
title: "Integrace transakčních komponent služeb Enterprise Services"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a236a34dd20661d62d59a3712a1800ff1f9a11ad
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="integrating-enterprise-services-transactional-components"></a><span data-ttu-id="b2a2a-102">Integrace transakčních komponent služeb Enterprise Services</span><span class="sxs-lookup"><span data-stu-id="b2a2a-102">Integrating Enterprise Services Transactional Components</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="b2a2a-103">poskytuje mechanismus automatického pro integraci do podnikové služby (viz [integrace s aplikacemi modelu COM +](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)).</span><span class="sxs-lookup"><span data-stu-id="b2a2a-103"> provides an automatic mechanism for integrating with Enterprise Services (see [Integrating with COM+ Applications](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)).</span></span> <span data-ttu-id="b2a2a-104">Ale můžete chtít flexibilitu při vývoji služeb, které používají interně hostovaným v rámci služby podnikového transakčních komponent.</span><span class="sxs-lookup"><span data-stu-id="b2a2a-104">However, you may want the flexibility to develop services that internally use transactional components hosted within Enterprise Services.</span></span> <span data-ttu-id="b2a2a-105">Protože [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transakce funkce je založená na <xref:System.Transactions> infrastruktury, proces pro integraci služby Enterprise s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je stejná jako pro zadání vzájemná funkční spolupráce mezi <xref:System.Transactions> a Enterprise Služby, jak je uvedeno v [vzájemná funkční spolupráce s Enterprise služeb a transakcí modelu COM +](http://go.microsoft.com/fwlink/?LinkId=94949).</span><span class="sxs-lookup"><span data-stu-id="b2a2a-105">Because the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Transactions feature is built on the <xref:System.Transactions> infrastructure, the process for integrating Enterprise Services with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is identical to that for specifying interoperability between <xref:System.Transactions> and Enterprise Services, as outlined in [Interoperability with Enterprise Services and COM+ Transactions](http://go.microsoft.com/fwlink/?LinkId=94949).</span></span>  
  
 <span data-ttu-id="b2a2a-106">Zájmu poskytnutí požadované úrovně vzájemné funkční spolupráce mezi příchozí sdružení transakcí a kontextu transakce modelu COM +, musíte vytvořit implementace služby <xref:System.Transactions.TransactionScope> instance a použít na odpovídající hodnotu z <xref:System.Transactions.EnterpriseServicesInteropOption> výčtu.</span><span class="sxs-lookup"><span data-stu-id="b2a2a-106">To provide the desired level of interoperability between the incoming flowed transaction and the COM+ context transaction, the service implementation must create a <xref:System.Transactions.TransactionScope> instance and use the appropriate value from the <xref:System.Transactions.EnterpriseServicesInteropOption> enumeration.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a><span data-ttu-id="b2a2a-107">Integrace služby Enterprise s operaci služby</span><span class="sxs-lookup"><span data-stu-id="b2a2a-107">Integrating Enterprise Services with a Service Operation</span></span>  
 <span data-ttu-id="b2a2a-108">Následující kód ukazuje operace s toku transakcí povolené, která vytvoří <xref:System.Transactions.TransactionScope> s <xref:System.Transactions.EnterpriseServicesInteropOption.Full> možnost.</span><span class="sxs-lookup"><span data-stu-id="b2a2a-108">The following code demonstrates an operation, with Allowed transaction flow, that creates a <xref:System.Transactions.TransactionScope> with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> option.</span></span> <span data-ttu-id="b2a2a-109">V tomto scénáři platí následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="b2a2a-109">The following conditions apply in this scenario:</span></span>  
  
-   <span data-ttu-id="b2a2a-110">Pokud klient toků transakce, provedení operace, včetně volání komponentu podnikové služby v rámci oboru této transakce.</span><span class="sxs-lookup"><span data-stu-id="b2a2a-110">If the client flows a transaction, the operation, including the call to the Enterprise Services component, is executed within the scope of that transaction.</span></span> <span data-ttu-id="b2a2a-111">Pomocí <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zajistí, že transakce je synchronizován s <xref:System.EnterpriseServices> kontextu, což znamená, že vedlejším transakci pro <xref:System.Transactions> a <xref:System.EnterpriseServices> je stejný.</span><span class="sxs-lookup"><span data-stu-id="b2a2a-111">Using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the transaction is synchronized with the <xref:System.EnterpriseServices> context, which means that the ambient transaction for <xref:System.Transactions> and the <xref:System.EnterpriseServices> is the same.</span></span>  
  
-   <span data-ttu-id="b2a2a-112">Pokud klient není toku transakcí, nastavení <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> k `true` vytvoří nový obor transakce pro operaci.</span><span class="sxs-lookup"><span data-stu-id="b2a2a-112">If the client does not flow a transaction, setting <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> to `true` creates a new transaction scope for the operation.</span></span> <span data-ttu-id="b2a2a-113">Podobně <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zajišťuje, že operace transakce je stejný jako použit v rámci transakce <xref:System.EnterpriseServices> součásti kontextu.</span><span class="sxs-lookup"><span data-stu-id="b2a2a-113">Similarly, using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the operation’s transaction is the same as the transaction used inside the <xref:System.EnterpriseServices> component's context.</span></span>  
  
 <span data-ttu-id="b2a2a-114">Žádné další metodu volání dojít také v rámci oboru stejné operace transakce.</span><span class="sxs-lookup"><span data-stu-id="b2a2a-114">Any additional method calls also occur within the scope of the same operation’s transaction.</span></span>  
  
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
  
 <span data-ttu-id="b2a2a-115">Pokud žádná synchronizace je vyžadován mezi operaci aktuální transakci a volání transakčních komponent služeb Enterprise, použijte <xref:System.Transactions.EnterpriseServicesInteropOption.None> možnost při vytváření instance <xref:System.Transactions.TransactionScope> instance.</span><span class="sxs-lookup"><span data-stu-id="b2a2a-115">If no synchronization is required between an operation’s current transaction and calls to transactional Enterprise Services components, then use the <xref:System.Transactions.EnterpriseServicesInteropOption.None> option when instantiating the <xref:System.Transactions.TransactionScope> instance.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-client"></a><span data-ttu-id="b2a2a-116">Integrace služby Enterprise s klientem</span><span class="sxs-lookup"><span data-stu-id="b2a2a-116">Integrating Enterprise Services with a Client</span></span>  
 <span data-ttu-id="b2a2a-117">Následující kód ukazuje, jak pomocí kódu klienta <xref:System.Transactions.TransactionScope> instanci s <xref:System.Transactions.EnterpriseServicesInteropOption.Full> nastavení.</span><span class="sxs-lookup"><span data-stu-id="b2a2a-117">The following code demonstrates client code using a <xref:System.Transactions.TransactionScope> instance with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> setting.</span></span> <span data-ttu-id="b2a2a-118">V tomto scénáři dojde k volání operací služby, které podporují toku transakcí v rámci oboru stejné transakci jako volání součásti služby Enterprise.</span><span class="sxs-lookup"><span data-stu-id="b2a2a-118">In this scenario, calls to service operations that support transaction flow occur within the scope of the same transaction as the calls to Enterprise Services components.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b2a2a-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2a2a-119">See Also</span></span>  
 [<span data-ttu-id="b2a2a-120">Integrace s aplikacemi modelu COM +</span><span class="sxs-lookup"><span data-stu-id="b2a2a-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="b2a2a-121">Integrace s aplikacemi modelu COM</span><span class="sxs-lookup"><span data-stu-id="b2a2a-121">Integrating with COM Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
