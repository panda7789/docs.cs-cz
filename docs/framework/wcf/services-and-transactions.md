---
title: Služby a transakce
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: 9110198fa64e43c20e1e6ba0dcf158dddeac93a6
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321140"
---
# <a name="services-and-transactions"></a>Služby a transakce
Aplikace Windows Communication Foundation (WCF) mohou iniciovat transakci v rámci klienta a koordinovat transakci v rámci operace služby. Klienti mohou iniciovat transakci a vyvolat několik operací služby a zajistit, že operace služby jsou buď potvrzené, nebo vracené zpět jako jedna jednotka.  
  
 Můžete povolit chování transakce v kontraktu služby zadáním <xref:System.ServiceModel.ServiceBehaviorAttribute> a nastavením vlastností <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> a <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> pro operace služby, které vyžadují transakce klienta. Parametr <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> určuje, zda transakce, ve které je metoda spuštěna, je automaticky dokončena, pokud nejsou vyvolány žádné neošetřené výjimky. Další informace o těchto atributech naleznete v tématu [atributy transakce ServiceModel](./feature-details/servicemodel-transaction-attributes.md).  
  
 Práce, která je prováděna v operacích služby a spravovaná správcem prostředků, jako je například protokolování aktualizací databáze, je součástí transakce klienta.  
  
 Následující příklad ukazuje použití atributů <xref:System.ServiceModel.ServiceBehaviorAttribute> a <xref:System.ServiceModel.OperationBehaviorAttribute> pro řízení chování transakce na straně služby.  
  
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
  
 Můžete povolit transakce a tok transakce konfigurací vazeb klienta a služby k použití protokolu WS-AtomicTransaction a nastavením prvku [\<transactionFlow >](../configure-apps/file-schema/wcf/transactionflow.md) na hodnotu `true`, jak je znázorněno v následujícím příkladu. rozšířeného.  
  
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
  
 Klienti mohou zahájit transakci vytvořením <xref:System.Transactions.TransactionScope> a vyvoláním operací služby v rámci rozsahu transakce.  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a>Viz také:

- [Podpora transakcí v System.ServiceModel](./feature-details/transactional-support-in-system-servicemodel.md)
- [Modely transakcí](./feature-details/transaction-models.md)
- [Tok transakcí WS](./samples/ws-transaction-flow.md)
