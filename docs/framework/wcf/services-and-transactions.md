---
title: "Služby a transakce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7a206ff3d82378e825cd612a6564366ef1e07977
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="services-and-transactions"></a><span data-ttu-id="f1b77-102">Služby a transakce</span><span class="sxs-lookup"><span data-stu-id="f1b77-102">Services and Transactions</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="f1b77-103">aplikace můžete zahájit transakci ze v rámci klienta a koordinovat transakce v rámci operace služby.</span><span class="sxs-lookup"><span data-stu-id="f1b77-103"> applications can initiate a transaction from within a client and coordinate the transaction within the service operation.</span></span> <span data-ttu-id="f1b77-104">Klienty můžete zahájit transakci a vyvolání několik operací služby a ujistěte se, že operace služby jsou buď potvrzena nebo vrácena zpět jako na jednu jednotku.</span><span class="sxs-lookup"><span data-stu-id="f1b77-104">Clients can initiate a transaction and invoke several service operations and ensure that the service operations are either committed or rolled back as a single unit.</span></span>  
  
 <span data-ttu-id="f1b77-105">Chování transakce v kontrakt služby můžete povolit zadáním <xref:System.ServiceModel.ServiceBehaviorAttribute> a nastavení jeho <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> a <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> vlastnosti pro operace služby, které vyžadují transakce klienta.</span><span class="sxs-lookup"><span data-stu-id="f1b77-105">You can enable the transaction behavior in the service contract by specifying a <xref:System.ServiceModel.ServiceBehaviorAttribute> and setting its <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> properties for service operations that require client transactions.</span></span> <span data-ttu-id="f1b77-106"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> Parametr určuje, zda je transakce, ve kterém metoda spustí automaticky dokončit, pokud jsou vyvolány žádné neošetřené výjimky.</span><span class="sxs-lookup"><span data-stu-id="f1b77-106">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> parameter specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions are thrown.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="f1b77-107">Tyto atributy, najdete v části [atributy transakce ServiceModel](../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="f1b77-107"> these attributes, see [ServiceModel Transaction Attributes](../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).</span></span>  
  
 <span data-ttu-id="f1b77-108">Práce, které se provádí v operací služby a spravuje správce prostředků, jako je například protokolování aktualizace databáze je součástí klienta transakce.</span><span class="sxs-lookup"><span data-stu-id="f1b77-108">The work that is performed in the service operations and managed by a resource manager, such as logging database updates, is part of the client’s transaction.</span></span>  
  
 <span data-ttu-id="f1b77-109">Následující příklad ukazuje použití <xref:System.ServiceModel.ServiceBehaviorAttribute> a <xref:System.ServiceModel.OperationBehaviorAttribute> atributy pro řízení chování transakce na straně služby.</span><span class="sxs-lookup"><span data-stu-id="f1b77-109">The following sample demonstrates usage of the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes to control service-side transaction behavior.</span></span>  
  
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
  
 <span data-ttu-id="f1b77-110">Můžete povolit transakce a transakce toku konfigurací klienta a služby vazby pro použití protokolu WS-AtomicTransaction a nastavení [ \<transactionFlow >](../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) element `true`, jak je znázorněno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="f1b77-110">You can enable transactions and transaction flow by configuring the client and service bindings to use the WS-AtomicTransaction protocol, and setting the [\<transactionFlow>](../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) element to `true`, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="f1b77-111">Klienty můžete spustit transakci tak, že vytvoříte <xref:System.Transactions.TransactionScope> a volání operací služby v rámci oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="f1b77-111">Clients can begin a transaction by creating a <xref:System.Transactions.TransactionScope> and invoking service operations within the scope of the transaction.</span></span>  
  
```  
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f1b77-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1b77-112">See Also</span></span>  
 [<span data-ttu-id="f1b77-113">Podpora transakcí v názvovém prostoru System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f1b77-113">Transactional Support in System.ServiceModel</span></span>](../../../docs/framework/wcf/feature-details/transactional-support-in-system-servicemodel.md)  
 [<span data-ttu-id="f1b77-114">Modely transakcí</span><span class="sxs-lookup"><span data-stu-id="f1b77-114">Transaction Models</span></span>](../../../docs/framework/wcf/feature-details/transaction-models.md)  
 [<span data-ttu-id="f1b77-115">Tok transakcí</span><span class="sxs-lookup"><span data-stu-id="f1b77-115">WS Transaction Flow</span></span>](../../../docs/framework/wcf/samples/ws-transaction-flow.md)
