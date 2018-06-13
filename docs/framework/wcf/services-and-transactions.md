---
title: Služby a transakce
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: 85792584660bd742ad3d313bf04ef1ce88bddcc2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33504316"
---
# <a name="services-and-transactions"></a>Služby a transakce
Aplikace Windows Communication Foundation (WCF) můžete zahájit transakci ze v rámci klienta a koordinovat transakce v rámci operace služby. Klienty můžete zahájit transakci a vyvolání několik operací služby a ujistěte se, že operace služby jsou buď potvrzena nebo vrácena zpět jako na jednu jednotku.  
  
 Chování transakce v kontrakt služby můžete povolit zadáním <xref:System.ServiceModel.ServiceBehaviorAttribute> a nastavení jeho <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> a <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> vlastnosti pro operace služby, které vyžadují transakce klienta. <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> Parametr určuje, zda je transakce, ve kterém metoda spustí automaticky dokončit, pokud jsou vyvolány žádné neošetřené výjimky. Další informace o těchto atributů najdete v tématu [atributy transakce ServiceModel](../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).  
  
 Práce, které se provádí v operací služby a spravuje správce prostředků, jako je například protokolování aktualizace databáze je součástí klienta transakce.  
  
 Následující příklad ukazuje použití <xref:System.ServiceModel.ServiceBehaviorAttribute> a <xref:System.ServiceModel.OperationBehaviorAttribute> atributy pro řízení chování transakce na straně služby.  
  
```  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService: ICalculatorLog  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                           TransactionAutoComplete = true)]  
    public double Add(double n1, double n2)  
    {  
        recordToLog(String.Format("Added {0} to {1}", n1, n2));  
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                               TransactionAutoComplete = true)]  
    public double Subtract(double n1, double n2)  
    {  
        recordToLog(String.Format("Subtracted {0} from {1}", n1, n2));  
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                       TransactionAutoComplete = true)]  
    public double Multiply(double n1, double n2)  
    {  
        recordToLog(String.Format("Multiplied {0} by {1}", n1, n2));  
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                       TransactionAutoComplete = true)]  
    public double Divide(double n1, double n2)  
    {  
        recordToLog(String.Format("Divided {0} by {1}", n1, n2));  
        return n1 / n2;  
    }  
  
}  
```  
  
 Můžete povolit transakce a transakce toku konfigurací klienta a služby vazby pro použití protokolu WS-AtomicTransaction a nastavení [ \<transactionFlow >](../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) element `true`, jak je znázorněno v následující ukázka konfigurace.  
  
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
  
 Klienty můžete spustit transakci tak, že vytvoříte <xref:System.Transactions.TransactionScope> a volání operací služby v rámci oboru transakce.  
  
```  
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Podpora transakcí v System.ServiceModel](../../../docs/framework/wcf/feature-details/transactional-support-in-system-servicemodel.md)  
 [Modely transakcí](../../../docs/framework/wcf/feature-details/transaction-models.md)  
 [Tok transakcí WS](../../../docs/framework/wcf/samples/ws-transaction-flow.md)
