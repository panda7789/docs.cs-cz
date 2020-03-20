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
# <a name="services-and-transactions"></a><span data-ttu-id="d5ac9-102">Služby a transakce</span><span class="sxs-lookup"><span data-stu-id="d5ac9-102">Services and Transactions</span></span>
<span data-ttu-id="d5ac9-103">Aplikace WCF (Windows Communication Foundation) můžete zahájit transakci z klienta a koordinovat transakci v rámci operace služby.</span><span class="sxs-lookup"><span data-stu-id="d5ac9-103">Windows Communication Foundation (WCF) applications can initiate a transaction from within a client and coordinate the transaction within the service operation.</span></span> <span data-ttu-id="d5ac9-104">Klienti mohou zahájit transakci a vyvolat několik operací služby a zajistit, aby operace služby byly potvrzeny nebo vráceny zpět jako jedna jednotka.</span><span class="sxs-lookup"><span data-stu-id="d5ac9-104">Clients can initiate a transaction and invoke several service operations and ensure that the service operations are either committed or rolled back as a single unit.</span></span>  
  
 <span data-ttu-id="d5ac9-105">Chování transakce v servisní smlouvě můžete povolit <xref:System.ServiceModel.ServiceBehaviorAttribute> zadáním <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> a nastavením vlastností a vlastností pro operace služeb, které vyžadují transakce klienta.</span><span class="sxs-lookup"><span data-stu-id="d5ac9-105">You can enable the transaction behavior in the service contract by specifying a <xref:System.ServiceModel.ServiceBehaviorAttribute> and setting its <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> properties for service operations that require client transactions.</span></span> <span data-ttu-id="d5ac9-106">Parametr <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> určuje, zda je transakce, ve které se metoda provádí, automaticky dokončena, pokud nejsou vyvolány žádné neošetřené výjimky.</span><span class="sxs-lookup"><span data-stu-id="d5ac9-106">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> parameter specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="d5ac9-107">Další informace o těchto atributech naleznete v tématu [ServiceModel Transaction Attributes](./feature-details/servicemodel-transaction-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="d5ac9-107">For more information about these attributes, see [ServiceModel Transaction Attributes](./feature-details/servicemodel-transaction-attributes.md).</span></span>  
  
 <span data-ttu-id="d5ac9-108">Práce, která se provádí v operacích služby a spravuje správce prostředků, jako je například protokolování aktualizací databáze, je součástí transakce klienta.</span><span class="sxs-lookup"><span data-stu-id="d5ac9-108">The work that is performed in the service operations and managed by a resource manager, such as logging database updates, is part of the client’s transaction.</span></span>  
  
 <span data-ttu-id="d5ac9-109">Následující ukázka ukazuje použití <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute> atributy a k řízení chování transakcí na straně služby.</span><span class="sxs-lookup"><span data-stu-id="d5ac9-109">The following sample demonstrates usage of the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes to control service-side transaction behavior.</span></span>  
  
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
  
 <span data-ttu-id="d5ac9-110">Transakce a tok transakcí můžete povolit konfigurací vazby klienta a služby pro použití protokolu WS-AtomicTransaction a nastavením `true` [ \<](../configure-apps/file-schema/wcf/transactionflow.md) prvku transactionFlow>na , jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="d5ac9-110">You can enable transactions and transaction flow by configuring the client and service bindings to use the WS-AtomicTransaction protocol, and setting the [\<transactionFlow>](../configure-apps/file-schema/wcf/transactionflow.md) element to `true`, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="d5ac9-111">Klienti mohou zahájit transakci <xref:System.Transactions.TransactionScope> vytvořením a vyvoláním operací služby v rámci transakce.</span><span class="sxs-lookup"><span data-stu-id="d5ac9-111">Clients can begin a transaction by creating a <xref:System.Transactions.TransactionScope> and invoking service operations within the scope of the transaction.</span></span>  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d5ac9-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5ac9-112">See also</span></span>

- [<span data-ttu-id="d5ac9-113">Podpora transakcí v System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d5ac9-113">Transactional Support in System.ServiceModel</span></span>](./feature-details/transactional-support-in-system-servicemodel.md)
- [<span data-ttu-id="d5ac9-114">Modely transakcí</span><span class="sxs-lookup"><span data-stu-id="d5ac9-114">Transaction Models</span></span>](./feature-details/transaction-models.md)
- [<span data-ttu-id="d5ac9-115">Tok transakcí WS</span><span class="sxs-lookup"><span data-stu-id="d5ac9-115">WS Transaction Flow</span></span>](./samples/ws-transaction-flow.md)
