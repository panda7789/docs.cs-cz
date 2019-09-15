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
# <a name="integrating-enterprise-services-transactional-components"></a>Integrace transakčních komponent služeb Enterprise Services
Windows Communication Foundation (WCF) poskytuje automatický mechanismus pro integraci s podnikovými službami (viz [integrace s aplikacemi modelu COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)). Je ale možné, že budete chtít pružně vyvíjet služby, které interně využívají transakční komponenty hostované v rámci podnikových služeb. Vzhledem k tomu, že funkce transakcí WCF je <xref:System.Transactions> postavená na infrastruktuře, proces pro integraci podnikových služeb se službou WCF je stejný jako při <xref:System.Transactions> určování interoperability mezi službami a podnikovými službami, jak je uvedeno v části. [Interoperabilita se službami Enterprise Services a transakcemi com+](https://go.microsoft.com/fwlink/?LinkId=94949).  
  
 Aby byla zajištěna požadovaná úroveň vzájemné funkční spolupráce mezi příchozí transakcí toku a transakcemi kontextu modelu COM+, musí implementace služby vytvořit <xref:System.Transactions.TransactionScope> instanci a použít příslušnou hodnotu <xref:System.Transactions.EnterpriseServicesInteropOption> z výčtu.  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>Integrace služeb Enterprise Services s operací služby  
 Následující kód demonstruje operaci s povoleným tokem transakce, která vytvoří <xref:System.Transactions.TransactionScope> <xref:System.Transactions.EnterpriseServicesInteropOption.Full> s možností. V tomto scénáři platí následující podmínky:  
  
- Pokud klient natéká transakci, operace, včetně volání do komponenty Enterprise Services, se spustí v rámci této transakce. Pomocí <xref:System.Transactions.EnterpriseServicesInteropOption.Full> nástroje je zajištěno, že transakce je <xref:System.EnterpriseServices> synchronizována s kontextem, což znamená, <xref:System.Transactions> že <xref:System.EnterpriseServices> ambientní transakce pro a je stejná.  
  
- Pokud klient neflowe transakci, nastavení <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> `true` vytvoří nový obor transakce pro operaci. Podobně použití <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zajistí, že transakce operace je shodná s transakcí použitou <xref:System.EnterpriseServices> v kontextu součásti.  
  
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
  
 Pokud mezi aktuální transakcí operace není vyžadována žádná synchronizace a volání součástí transakčních služeb Enterprise Services, použijte <xref:System.Transactions.EnterpriseServicesInteropOption.None> při vytváření <xref:System.Transactions.TransactionScope> instance instance možnost.  
  
## <a name="integrating-enterprise-services-with-a-client"></a>Integrace podnikových služeb s klientem  
 Následující kód demonstruje klientský kód pomocí <xref:System.Transactions.TransactionScope> instance <xref:System.Transactions.EnterpriseServicesInteropOption.Full> s nastavením. V tomto scénáři volání služeb, které podporují tok transakce, dochází v rámci oboru stejné transakce jako volání součástí služeb Enterprise Services.  
  
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
