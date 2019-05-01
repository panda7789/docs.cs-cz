---
title: Služby a transakce
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: 9dfe34406bfda2c16bd2f0cd53796b2fcef07b57
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967918"
---
# <a name="services-and-transactions"></a><span data-ttu-id="d3130-102">Služby a transakce</span><span class="sxs-lookup"><span data-stu-id="d3130-102">Services and Transactions</span></span>
<span data-ttu-id="d3130-103">Aplikace Windows Communication Foundation (WCF) můžete zahájit transakce z v rámci klienta a koordinovat transakce v rámci operace služby.</span><span class="sxs-lookup"><span data-stu-id="d3130-103">Windows Communication Foundation (WCF) applications can initiate a transaction from within a client and coordinate the transaction within the service operation.</span></span> <span data-ttu-id="d3130-104">Klienti můžou zahájení transakce a volání několika operací služby a ujistěte se, že operace služby jsou buď potvrzené nebo vrátit zpět jako jednu jednotku.</span><span class="sxs-lookup"><span data-stu-id="d3130-104">Clients can initiate a transaction and invoke several service operations and ensure that the service operations are either committed or rolled back as a single unit.</span></span>  
  
 <span data-ttu-id="d3130-105">Chování transakce v kontraktu služby můžete povolit tak, že zadáte <xref:System.ServiceModel.ServiceBehaviorAttribute> a nastavení jeho <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> a <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> vlastnosti pro operace služby, které vyžadují transakce klienta.</span><span class="sxs-lookup"><span data-stu-id="d3130-105">You can enable the transaction behavior in the service contract by specifying a <xref:System.ServiceModel.ServiceBehaviorAttribute> and setting its <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> properties for service operations that require client transactions.</span></span> <span data-ttu-id="d3130-106"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> Parametr určuje, zda je transakce, ve kterém metoda je provedena automaticky dokončit, pokud nejsou vyvolány žádné neošetřené výjimky.</span><span class="sxs-lookup"><span data-stu-id="d3130-106">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> parameter specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="d3130-107">Další informace o těchto atributů najdete v tématu [atributy transakce ServiceModel](../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="d3130-107">For more information about these attributes, see [ServiceModel Transaction Attributes](../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).</span></span>  
  
 <span data-ttu-id="d3130-108">Práce, které se provádí v operacích služeb a spravuje správce prostředků, jako je například protokolování aktualizace databáze je součástí klienta transakce.</span><span class="sxs-lookup"><span data-stu-id="d3130-108">The work that is performed in the service operations and managed by a resource manager, such as logging database updates, is part of the client’s transaction.</span></span>  
  
 <span data-ttu-id="d3130-109">Následující příklad ukazuje použití <xref:System.ServiceModel.ServiceBehaviorAttribute> a <xref:System.ServiceModel.OperationBehaviorAttribute> atributy pro řízení chování transakce na straně služby.</span><span class="sxs-lookup"><span data-stu-id="d3130-109">The following sample demonstrates usage of the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes to control service-side transaction behavior.</span></span>  
  
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
  
 <span data-ttu-id="d3130-110">Můžete povolit transakce a transakce tok pomocí klientského a vazby pro použití protokolu WS-AtomicTransaction a nastavení služby [ \<transactionFlow >](../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) element `true`, jak je znázorněno v následující ukázková konfigurace.</span><span class="sxs-lookup"><span data-stu-id="d3130-110">You can enable transactions and transaction flow by configuring the client and service bindings to use the WS-AtomicTransaction protocol, and setting the [\<transactionFlow>](../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) element to `true`, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="d3130-111">Klienti mohou spustit transakci tak, že vytvoříte <xref:System.Transactions.TransactionScope> a volání operací služby v rámci oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="d3130-111">Clients can begin a transaction by creating a <xref:System.Transactions.TransactionScope> and invoking service operations within the scope of the transaction.</span></span>  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3130-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3130-112">See also</span></span>

- [<span data-ttu-id="d3130-113">Podpora transakcí v System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d3130-113">Transactional Support in System.ServiceModel</span></span>](../../../docs/framework/wcf/feature-details/transactional-support-in-system-servicemodel.md)
- [<span data-ttu-id="d3130-114">Modely transakcí</span><span class="sxs-lookup"><span data-stu-id="d3130-114">Transaction Models</span></span>](../../../docs/framework/wcf/feature-details/transaction-models.md)
- [<span data-ttu-id="d3130-115">Tok transakcí WS</span><span class="sxs-lookup"><span data-stu-id="d3130-115">WS Transaction Flow</span></span>](../../../docs/framework/wcf/samples/ws-transaction-flow.md)
