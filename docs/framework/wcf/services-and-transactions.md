---
title: Služby a transakce
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: 5078e12ed5c68556a1d1d04d01c90440b57c1407
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736400"
---
# <a name="services-and-transactions"></a>Služby a transakce
Aplikace Windows Communication Foundation (WCF) můžete zahájit transakce z v rámci klienta a koordinovat transakce v rámci operace služby. Klienti můžou zahájení transakce a volání několika operací služby a ujistěte se, že operace služby jsou buď potvrzené nebo vrátit zpět jako jednu jednotku.  
  
 Chování transakce v kontraktu služby můžete povolit tak, že zadáte <xref:System.ServiceModel.ServiceBehaviorAttribute> a nastavení jeho <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> a <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> vlastnosti pro operace služby, které vyžadují transakce klienta. <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> Parametr určuje, zda je transakce, ve kterém metoda je provedena automaticky dokončit, pokud nejsou vyvolány žádné neošetřené výjimky. Další informace o těchto atributů najdete v tématu [atributy transakce ServiceModel](../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).  
  
 Práce, které se provádí v operacích služeb a spravuje správce prostředků, jako je například protokolování aktualizace databáze je součástí klienta transakce.  
  
 Následující příklad ukazuje použití <xref:System.ServiceModel.ServiceBehaviorAttribute> a <xref:System.ServiceModel.OperationBehaviorAttribute> atributy pro řízení chování transakce na straně služby.  
  
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
  
 Můžete povolit transakce a transakce tok pomocí klientského a vazby pro použití protokolu WS-AtomicTransaction a nastavení služby [ \<transactionFlow >](../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) element `true`, jak je znázorněno v následující ukázková konfigurace.  
  
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
  
 Klienti mohou spustit transakci tak, že vytvoříte <xref:System.Transactions.TransactionScope> a volání operací služby v rámci oboru transakce.  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a>Viz také:
- [Podpora transakcí v System.ServiceModel](../../../docs/framework/wcf/feature-details/transactional-support-in-system-servicemodel.md)
- [Modely transakcí](../../../docs/framework/wcf/feature-details/transaction-models.md)
- [Tok transakcí WS](../../../docs/framework/wcf/samples/ws-transaction-flow.md)
