---
title: Transakce pracovního postupu
ms.date: 03/30/2017
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
ms.openlocfilehash: 223c18195c8ffd0b51eb5dff77aa81953f6e47a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182676"
---
# <a name="workflow-transactions"></a><span data-ttu-id="12db2-102">Transakce pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="12db2-102">Workflow Transactions</span></span>

[!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="12db2-103">poskytuje podporu pro <xref:System.Transactions> účast v <xref:System.Activities.Statements.TransactionScope> transakcích pomocí aktivity k rozsahu transakční jednotky práce.</span><span class="sxs-lookup"><span data-stu-id="12db2-103">provides support for participating in <xref:System.Transactions> transactions by using the <xref:System.Activities.Statements.TransactionScope> activity to scope a transacted unit of work.</span></span> <span data-ttu-id="12db2-104">Zatímco <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> musí být explicitně dokončena aktivita <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> implicitně volá dokončení transakce po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="12db2-104">While the <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> must be explicitly completed the <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> activity implicitly calls complete on the transaction upon successful completion.</span></span> <span data-ttu-id="12db2-105">Všechny aktivity, které <xref:System.Activities.Statements.TransactionScope.Body%2A> jsou <xref:System.Activities.Statements.TransactionScope> obsaženy v aktivitě účastnit transakce.</span><span class="sxs-lookup"><span data-stu-id="12db2-105">Any activities that are contained in the <xref:System.Activities.Statements.TransactionScope.Body%2A> of the <xref:System.Activities.Statements.TransactionScope> activity participate in the transaction.</span></span> <span data-ttu-id="12db2-106">Wf může tok transakcí do pracovního <xref:System.ServiceModel.Activities.TransactedReceiveScope> postupu pomocí aktivity.</span><span class="sxs-lookup"><span data-stu-id="12db2-106">WF can to flow transactions into a workflow through the use of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="12db2-107">Stejně <xref:System.Activities.Statements.TransactionScope> jako aktivita, všechny <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> aktivity obsažené v účasti v transakci.</span><span class="sxs-lookup"><span data-stu-id="12db2-107">Like the <xref:System.Activities.Statements.TransactionScope> activity, any activity contained in the <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> participates in the transaction.</span></span> <span data-ttu-id="12db2-108">Služba WF zajišťuje, <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> že aktivity <xref:System.ServiceModel.Activities.TransactedReceiveScope>závislé na práci s oběma a <xref:System.Activities.Statements.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="12db2-108">WF ensures that activities dependent on <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> works with both <xref:System.Activities.Statements.TransactionScope> and <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="12db2-109">Pokud aktivity poskytované systémem neřeší všechny požadavky, vlastní aktivity lze sestavit pomocí <xref:System.Activities.RuntimeTransactionHandle> povolit pokročilé toku a řízení transakcí scénáře.</span><span class="sxs-lookup"><span data-stu-id="12db2-109">If the system-provided activities do not address all requirements, custom activities can be built using the <xref:System.Activities.RuntimeTransactionHandle> to enable advanced flow and transaction control scenarios.</span></span>  
  
<span data-ttu-id="12db2-110">V následujícím příkladu je vytvořen pracovní postup <xref:System.Activities.Statements.Sequence> skládající se z <xref:System.Activities.Statements.TransactionScope> aktivity, která obsahuje podřízené aktivity včetně aktivity.</span><span class="sxs-lookup"><span data-stu-id="12db2-110">In the following example, a workflow is constructed consisting of a <xref:System.Activities.Statements.Sequence> activity that contains child activities including a <xref:System.Activities.Statements.TransactionScope> activity.</span></span> <span data-ttu-id="12db2-111">Aktivity <xref:System.Activities.Statements.TransactionScope.Body%2A> provést <xref:System.Activities.Statements.TransactionScope> v rámci transakce inicializovány aktivitou. <xref:System.Activities.Statements.TransactionScope></span><span class="sxs-lookup"><span data-stu-id="12db2-111">The <xref:System.Activities.Statements.TransactionScope.Body%2A> activities of the <xref:System.Activities.Statements.TransactionScope> execute under the transaction initialized by the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
```csharp  
static Activity ScenarioOne()  
{  
    return new Sequence  
    {  
        Activities =  
        {  
            new WriteLine { Text = "    Begin workflow" },  
  
            new TransactionScope  
            {  
                Body = new Sequence  
                {  
                    Activities =
                    {  
                        new WriteLine { Text = "    Begin TransactionScope" },  
  
                        new PrintTransactionId(),  
  
                        new TransactionScopeTest(),  
  
                        new WriteLine { Text = "    End TransactionScope" },  
                    },  
                },  
            },  
  
            new WriteLine { Text = "    End workflow" },  
        }  
    };  
}  
```  
  
<span data-ttu-id="12db2-112">Další informace naleznete v <xref:System.ServiceModel.Activities.TransactedReceiveScope>tématu použití , naleznete [v tématu plynulé transakce do a z pracovního postupu služby](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="12db2-112">For more information, see about using <xref:System.ServiceModel.Activities.TransactedReceiveScope>, see [Flowing Transactions into and out of Workflow Services](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12db2-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="12db2-113">See also</span></span>

- <xref:System.Activities.Statements.TransactionScope>
- <xref:System.Transactions.TransactionScope>
- <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
