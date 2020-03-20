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
# <a name="integrating-enterprise-services-transactional-components"></a>Integrace transakčních komponent služeb Enterprise Services

Windows Communication Foundation (WCF) poskytuje automatický mechanismus pro integraci s Enterprise Services (viz [Integrace s com+ aplikace).](integrating-with-com-plus-applications.md) Můžete však chtít flexibilitu při vývoji služeb, které interně používají transakční součásti hostované v rámci služeb Enterprise Services. Vzhledem k tomu, že funkce <xref:System.Transactions> WCF Transactions je postavena na infrastruktuře, proces integrace <xref:System.Transactions> podnikových služeb s WCF je shodný s procesem pro určení interoperability mezi a enterprise services, jak je uvedeno v [interoperabilitě s podnikovými službami a transakcemi modelu COM+](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85)).  
  
 Chcete-li poskytnout požadovanou úroveň interoperability mezi příchozí tok transakce a com + <xref:System.Transactions.TransactionScope> kontext transakce, implementace <xref:System.Transactions.EnterpriseServicesInteropOption> služby musí vytvořit instanci a použít příslušnou hodnotu z výčtu.  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>Integrace podnikových služeb s operací služby  
 Následující kód ukazuje operaci s povoleným tokem <xref:System.Transactions.TransactionScope> transakce, která vytvoří s <xref:System.Transactions.EnterpriseServicesInteropOption.Full> možností. V tomto scénáři platí následující podmínky:  
  
- Pokud klient toky transakce, operace, včetně volání součásti Enterprise Services, je proveden v rámci této transakce. Použití <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zajišťuje, že transakce je <xref:System.EnterpriseServices> synchronizována s kontextem, <xref:System.Transactions> což <xref:System.EnterpriseServices> znamená, že okolí transakce pro a je stejný.  
  
- Pokud klient netokuje transakci, nastavení <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> vytvoří `true` nový rozsah transakce pro operaci. Podobně pomocí <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zajišťuje, že transakce operace je stejná jako transakce <xref:System.EnterpriseServices> použitá v kontextu komponenty.  
  
 Jakékoli další volání metody také dojít v rámci rozsahu transakce stejné operace.  
  
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
  
 Pokud není vyžadována žádná synchronizace mezi aktuální transakcí operace a voláním transakčních součástí služby Enterprise Services, použijte <xref:System.Transactions.EnterpriseServicesInteropOption.None> tuto možnost při vytváření instancí. <xref:System.Transactions.TransactionScope>  
  
## <a name="integrating-enterprise-services-with-a-client"></a>Integrace podnikových služeb s klientem  
 Následující kód ukazuje kód klienta <xref:System.Transactions.TransactionScope> pomocí <xref:System.Transactions.EnterpriseServicesInteropOption.Full> instance s nastavením. V tomto scénáři volání operací služby, které podporují tok transakcí dojít v rámci rozsahu stejné transakce jako volání součásti Enterprise Services.  
  
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
  
## <a name="see-also"></a>Viz také

- [Integrace s aplikacemi modelu COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [Integrace s aplikacemi modelu COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
