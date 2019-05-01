---
title: Integrace transakčních komponent služeb Enterprise Services
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 33e09eab1d7ad24dc234cfff21e352611e0b2ef9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047032"
---
# <a name="integrating-enterprise-services-transactional-components"></a>Integrace transakčních komponent služeb Enterprise Services
Windows Communication Foundation (WCF) poskytuje mechanismus automatického pro integraci se službami Enterprise (viz [integrace s aplikacemi modelu COM +](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)). Však můžete chtít flexibilitu pro vývoj služeb, které používají interně transakčních komponent, které jsou hostované v rámci podnikové služby. Protože funkce transakce WCF je založená na <xref:System.Transactions> infrastruktury, proces pro integraci podnikových služeb s použitím technologie WCF je stejná jako pro určení vzájemná funkční spolupráce mezi <xref:System.Transactions> a podnikových služeb, jak je uvedeno v [Interoperabilita se službami Enterprise Services a transakcemi COM +](https://go.microsoft.com/fwlink/?LinkId=94949).  
  
 K poskytování požadované úrovni vzájemná funkční spolupráce mezi sdružení příchozí transakce a transakce kontext modelu COM +, musíte vytvořit implementace služby <xref:System.Transactions.TransactionScope> instance a použijte příslušné hodnoty od <xref:System.Transactions.EnterpriseServicesInteropOption> výčtu.  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>Integrace služby Enterprise s operací služby  
 Následující kód ukazuje operaci s toku transakcí povolené, který vytvoří <xref:System.Transactions.TransactionScope> s <xref:System.Transactions.EnterpriseServicesInteropOption.Full> možnost. V tomto případě platí následující podmínky:  
  
- Pokud klient tok transakce, provádí se operace, včetně volání na komponentu podnikové služby v rámci oboru dané transakce. Pomocí <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zajistí, že transakce se synchronizují s <xref:System.EnterpriseServices> kontextu, což znamená, že okolí transakce pro <xref:System.Transactions> a <xref:System.EnterpriseServices> je stejný.  
  
- Pokud klient není tok transakce, nastavení <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> k `true` vytvoří nový obor transakce pro operace. Podobně použití <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zajistí, že operace transakce je stejná jako transakce použitá uvnitř <xref:System.EnterpriseServices> kontextu komponenty.  
  
 Všechna volání další metodu dojít také v rámci oboru transakce stejné operace.  
  
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
  
 Pokud není žádná synchronizace musí být mezi aktuální transakce a volání transakčních komponent služeb Enterprise operace, použijte <xref:System.Transactions.EnterpriseServicesInteropOption.None> možnosti při vytváření instance <xref:System.Transactions.TransactionScope> instance.  
  
## <a name="integrating-enterprise-services-with-a-client"></a>Integrace s klientem služby Enterprise  
 Následující kód ukazuje použití kódu klienta <xref:System.Transactions.TransactionScope> instanci s <xref:System.Transactions.EnterpriseServicesInteropOption.Full> nastavení. V tomto scénáři dojde k volání operací služby, které podporují tok transakcí v rámci oboru stejné transakci jako volání součásti služby Enterprise.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Integrace s aplikacemi modelu COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [Integrace s aplikacemi modelu COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
