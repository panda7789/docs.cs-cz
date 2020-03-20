---
title: Služby a transakce
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: 4c59b83448f5a2c448843c12dae99c442441441f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143275"
---
# <a name="services-and-transactions"></a>Služby a transakce
Aplikace WCF (Windows Communication Foundation) můžete zahájit transakci z klienta a koordinovat transakci v rámci operace služby. Klienti mohou zahájit transakci a vyvolat několik operací služby a zajistit, aby operace služby byly potvrzeny nebo vráceny zpět jako jedna jednotka.  
  
 Chování transakce v servisní smlouvě můžete povolit <xref:System.ServiceModel.ServiceBehaviorAttribute> zadáním <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> a nastavením vlastností a vlastností pro operace služeb, které vyžadují transakce klienta. Parametr <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> určuje, zda je transakce, ve které se metoda provádí, automaticky dokončena, pokud nejsou vyvolány žádné neošetřené výjimky. Další informace o těchto atributech naleznete v tématu [ServiceModel Transaction Attributes](./feature-details/servicemodel-transaction-attributes.md).  
  
 Práce, která se provádí v operacích služby a spravuje správce prostředků, jako je například protokolování aktualizací databáze, je součástí transakce klienta.  
  
 Následující ukázka ukazuje použití <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute> atributy a k řízení chování transakcí na straně služby.  
  
```csharp
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService: ICalculatorLog  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                           TransactionAutoComplete = true)]  
    public double Add(double n1, double n2)  
    {  
        recordToLog($"Added {n1} to {n2}");
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                               TransactionAutoComplete = true)]  
    public double Subtract(double n1, double n2)  
    {  
        recordToLog($"Subtracted {n1} from {n2}");
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                       TransactionAutoComplete = true)]  
    public double Multiply(double n1, double n2)  
    {  
        recordToLog($"Multiplied {n1} by {n2}");
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                       TransactionAutoComplete = true)]  
    public double Divide(double n1, double n2)  
    {  
        recordToLog($"Divided {n1} by {n2}", n1, n2);
        return n1 / n2;  
    }  
  
}  
```  
  
 Transakce a tok transakcí můžete povolit konfigurací vazby klienta a služby pro použití protokolu WS-AtomicTransaction a nastavením `true` [ \<](../configure-apps/file-schema/wcf/transactionflow.md) prvku transactionFlow>na , jak je znázorněno v následující ukázkové konfiguraci.  
  
```xml  
<client>  
    <endpoint address="net.tcp://localhost/ServiceModelSamples/service"
          binding="netTcpBinding"
          bindingConfiguration="netTcpBindingWSAT"
          contract="Microsoft.ServiceModel.Samples.ICalculatorLog" />  
</client>  
  
<bindings>  
    <netTcpBinding>  
        <binding name="netTcpBindingWSAT"  
                transactionFlow="true"  
                transactionProtocol="WSAtomicTransactionOctober2004" />  
     </netTcpBinding>  
</bindings>  
```  
  
 Klienti mohou zahájit transakci <xref:System.Transactions.TransactionScope> vytvořením a vyvoláním operací služby v rámci transakce.  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a>Viz také

- [Podpora transakcí v System.ServiceModel](./feature-details/transactional-support-in-system-servicemodel.md)
- [Modely transakcí](./feature-details/transaction-models.md)
- [Tok transakcí WS](./samples/ws-transaction-flow.md)
