---
title: Integrace transakčních komponent služeb Enterprise Services
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 5914f76639adc3ff569a3bfb8d6eb1db14313e76
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76211941"
---
# <a name="integrating-enterprise-services-transactional-components"></a>Integrace transakčních komponent služeb Enterprise Services

Windows Communication Foundation (WCF) poskytuje automatický mechanismus pro integraci s podnikovými službami (viz [integrace s aplikacemi modelu COM+](integrating-with-com-plus-applications.md)). Je ale možné, že budete chtít pružně vyvíjet služby, které interně využívají transakční komponenty hostované v rámci podnikových služeb. Vzhledem k tomu, že funkce transakcí WCF je postavená na infrastruktuře <xref:System.Transactions>, proces integrace podnikových služeb se službou WCF je stejný jako při určování interoperability mezi <xref:System.Transactions> a podnikovými službami, jak je uvedeno v [interoperabilitě se službami Enterprise Services a transakcemi com+](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85)).  
  
 Aby byla zajištěna požadovaná úroveň interoperability mezi příchozími transakcemi a transakcemi kontextu modelu COM+, musí implementace služby vytvořit instanci <xref:System.Transactions.TransactionScope> a použít odpovídající hodnotu z výčtu <xref:System.Transactions.EnterpriseServicesInteropOption>.  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>Integrace služeb Enterprise Services s operací služby  
 Následující kód demonstruje operaci s povoleným tokem transakce, která vytvoří <xref:System.Transactions.TransactionScope> s možností <xref:System.Transactions.EnterpriseServicesInteropOption.Full>. V tomto scénáři platí následující podmínky:  
  
- Pokud klient natéká transakci, operace, včetně volání do komponenty Enterprise Services, se spustí v rámci této transakce. Pomocí <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zajistí, že transakce bude synchronizována s <xref:System.EnterpriseServices>m kontextem, což znamená, že ambientní transakce pro <xref:System.Transactions> a <xref:System.EnterpriseServices> je stejná.  
  
- Pokud klient neflowe transakci, nastavení <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> pro `true` vytvoří nový obor transakce pro operaci. Podobně použití <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zajišťuje, že transakce operace je stejná jako transakce použitá v kontextu <xref:System.EnterpriseServices> součásti.  
  
 K dalším voláním metody dojde také v rámci oboru transakce stejné operace.  
  
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
  
 Pokud se mezi aktuální transakcí operace nepožaduje žádná synchronizace a volání součástí transakčních služeb Enterprise Services, použijte při vytváření instance <xref:System.Transactions.TransactionScope> možnost <xref:System.Transactions.EnterpriseServicesInteropOption.None>.  
  
## <a name="integrating-enterprise-services-with-a-client"></a>Integrace podnikových služeb s klientem  
 Následující kód demonstruje klientský kód pomocí <xref:System.Transactions.TransactionScope> instance s nastavením <xref:System.Transactions.EnterpriseServicesInteropOption.Full>. V tomto scénáři volání služeb, které podporují tok transakce, dochází v rámci oboru stejné transakce jako volání součástí služeb Enterprise Services.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Integrace s aplikacemi modelu COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [Integrace s aplikacemi modelu COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
