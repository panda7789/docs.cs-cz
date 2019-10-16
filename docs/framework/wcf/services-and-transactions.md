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
# <a name="services-and-transactions"></a><span data-ttu-id="090d3-102">Služby a transakce</span><span class="sxs-lookup"><span data-stu-id="090d3-102">Services and Transactions</span></span>
<span data-ttu-id="090d3-103">Aplikace Windows Communication Foundation (WCF) mohou iniciovat transakci v rámci klienta a koordinovat transakci v rámci operace služby.</span><span class="sxs-lookup"><span data-stu-id="090d3-103">Windows Communication Foundation (WCF) applications can initiate a transaction from within a client and coordinate the transaction within the service operation.</span></span> <span data-ttu-id="090d3-104">Klienti mohou iniciovat transakci a vyvolat několik operací služby a zajistit, že operace služby jsou buď potvrzené, nebo vracené zpět jako jedna jednotka.</span><span class="sxs-lookup"><span data-stu-id="090d3-104">Clients can initiate a transaction and invoke several service operations and ensure that the service operations are either committed or rolled back as a single unit.</span></span>  
  
 <span data-ttu-id="090d3-105">Můžete povolit chování transakce v kontraktu služby zadáním <xref:System.ServiceModel.ServiceBehaviorAttribute> a nastavením vlastností <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> a <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> pro operace služby, které vyžadují transakce klienta.</span><span class="sxs-lookup"><span data-stu-id="090d3-105">You can enable the transaction behavior in the service contract by specifying a <xref:System.ServiceModel.ServiceBehaviorAttribute> and setting its <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> properties for service operations that require client transactions.</span></span> <span data-ttu-id="090d3-106">Parametr <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> určuje, zda transakce, ve které je metoda spuštěna, je automaticky dokončena, pokud nejsou vyvolány žádné neošetřené výjimky.</span><span class="sxs-lookup"><span data-stu-id="090d3-106">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> parameter specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="090d3-107">Další informace o těchto atributech naleznete v tématu [atributy transakce ServiceModel](./feature-details/servicemodel-transaction-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="090d3-107">For more information about these attributes, see [ServiceModel Transaction Attributes](./feature-details/servicemodel-transaction-attributes.md).</span></span>  
  
 <span data-ttu-id="090d3-108">Práce, která je prováděna v operacích služby a spravovaná správcem prostředků, jako je například protokolování aktualizací databáze, je součástí transakce klienta.</span><span class="sxs-lookup"><span data-stu-id="090d3-108">The work that is performed in the service operations and managed by a resource manager, such as logging database updates, is part of the client’s transaction.</span></span>  
  
 <span data-ttu-id="090d3-109">Následující příklad ukazuje použití atributů <xref:System.ServiceModel.ServiceBehaviorAttribute> a <xref:System.ServiceModel.OperationBehaviorAttribute> pro řízení chování transakce na straně služby.</span><span class="sxs-lookup"><span data-stu-id="090d3-109">The following sample demonstrates usage of the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes to control service-side transaction behavior.</span></span>  
  
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
  
 <span data-ttu-id="090d3-110">Můžete povolit transakce a tok transakce konfigurací vazeb klienta a služby k použití protokolu WS-AtomicTransaction a nastavením prvku [\<transactionFlow >](../configure-apps/file-schema/wcf/transactionflow.md) na hodnotu `true`, jak je znázorněno v následujícím příkladu. rozšířeného.</span><span class="sxs-lookup"><span data-stu-id="090d3-110">You can enable transactions and transaction flow by configuring the client and service bindings to use the WS-AtomicTransaction protocol, and setting the [\<transactionFlow>](../configure-apps/file-schema/wcf/transactionflow.md) element to `true`, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="090d3-111">Klienti mohou zahájit transakci vytvořením <xref:System.Transactions.TransactionScope> a vyvoláním operací služby v rámci rozsahu transakce.</span><span class="sxs-lookup"><span data-stu-id="090d3-111">Clients can begin a transaction by creating a <xref:System.Transactions.TransactionScope> and invoking service operations within the scope of the transaction.</span></span>  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="090d3-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="090d3-112">See also</span></span>

- [<span data-ttu-id="090d3-113">Podpora transakcí v System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="090d3-113">Transactional Support in System.ServiceModel</span></span>](./feature-details/transactional-support-in-system-servicemodel.md)
- [<span data-ttu-id="090d3-114">Modely transakcí</span><span class="sxs-lookup"><span data-stu-id="090d3-114">Transaction Models</span></span>](./feature-details/transaction-models.md)
- [<span data-ttu-id="090d3-115">Tok transakcí WS</span><span class="sxs-lookup"><span data-stu-id="090d3-115">WS Transaction Flow</span></span>](./samples/ws-transaction-flow.md)
