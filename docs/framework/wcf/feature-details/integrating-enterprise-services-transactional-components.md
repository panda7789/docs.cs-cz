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
ms.workload: dotnet
ms.openlocfilehash: b6ce82d100341fec4415cf9fdb7159706b2accc4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="integrating-enterprise-services-transactional-components"></a>Integrace transakčních komponent služeb Enterprise Services
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]poskytuje mechanismus automatického pro integraci do podnikové služby (viz [integrace s aplikacemi modelu COM +](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)). Ale můžete chtít flexibilitu při vývoji služeb, které používají interně hostovaným v rámci služby podnikového transakčních komponent. Protože [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transakce funkce je založená na <xref:System.Transactions> infrastruktury, proces pro integraci služby Enterprise s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je stejná jako pro zadání vzájemná funkční spolupráce mezi <xref:System.Transactions> a Enterprise Služby, jak je uvedeno v [vzájemná funkční spolupráce s Enterprise služeb a transakcí modelu COM +](http://go.microsoft.com/fwlink/?LinkId=94949).  
  
 Zájmu poskytnutí požadované úrovně vzájemné funkční spolupráce mezi příchozí sdružení transakcí a kontextu transakce modelu COM +, musíte vytvořit implementace služby <xref:System.Transactions.TransactionScope> instance a použít na odpovídající hodnotu z <xref:System.Transactions.EnterpriseServicesInteropOption> výčtu.  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>Integrace služby Enterprise s operaci služby  
 Následující kód ukazuje operace s toku transakcí povolené, která vytvoří <xref:System.Transactions.TransactionScope> s <xref:System.Transactions.EnterpriseServicesInteropOption.Full> možnost. V tomto scénáři platí následující podmínky:  
  
-   Pokud klient toků transakce, provedení operace, včetně volání komponentu podnikové služby v rámci oboru této transakce. Pomocí <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zajistí, že transakce je synchronizován s <xref:System.EnterpriseServices> kontextu, což znamená, že vedlejším transakci pro <xref:System.Transactions> a <xref:System.EnterpriseServices> je stejný.  
  
-   Pokud klient není toku transakcí, nastavení <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> k `true` vytvoří nový obor transakce pro operaci. Podobně <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zajišťuje, že operace transakce je stejný jako použit v rámci transakce <xref:System.EnterpriseServices> součásti kontextu.  
  
 Žádné další metodu volání dojít také v rámci oboru stejné operace transakce.  
  
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
  
 Pokud žádná synchronizace je vyžadován mezi operaci aktuální transakci a volání transakčních komponent služeb Enterprise, použijte <xref:System.Transactions.EnterpriseServicesInteropOption.None> možnost při vytváření instance <xref:System.Transactions.TransactionScope> instance.  
  
## <a name="integrating-enterprise-services-with-a-client"></a>Integrace služby Enterprise s klientem  
 Následující kód ukazuje, jak pomocí kódu klienta <xref:System.Transactions.TransactionScope> instanci s <xref:System.Transactions.EnterpriseServicesInteropOption.Full> nastavení. V tomto scénáři dojde k volání operací služby, které podporují toku transakcí v rámci oboru stejné transakci jako volání součásti služby Enterprise.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Integrace s aplikacemi modelu COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [Integrace s aplikacemi modelu COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
