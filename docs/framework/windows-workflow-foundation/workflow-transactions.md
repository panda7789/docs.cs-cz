---
title: Pracovní postup transakce
ms.date: 03/30/2017
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
ms.openlocfilehash: 2bb5f6498b365f3b773eea9a5adce1ec1158a289
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517251"
---
# <a name="workflow-transactions"></a><span data-ttu-id="bcf2f-102">Pracovní postup transakce</span><span class="sxs-lookup"><span data-stu-id="bcf2f-102">Workflow Transactions</span></span>
[!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="bcf2f-103"> poskytuje podporu pro účastní <xref:System.Transactions> transakce pomocí <xref:System.Activities.Statements.TransactionScope> aktivity k určení rozsahu zpracovaných jednotka práce.</span><span class="sxs-lookup"><span data-stu-id="bcf2f-103"> provides support for participating in <xref:System.Transactions> transactions by using the <xref:System.Activities.Statements.TransactionScope> activity to scope a transacted unit of work.</span></span> <span data-ttu-id="bcf2f-104">Při <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> musí být explicitně Dokončit <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> implicitně volání provést aktivitu v transakci po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="bcf2f-104">While the <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> must be explicitly completed the <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> activity implicitly calls complete on the transaction upon successful completion.</span></span> <span data-ttu-id="bcf2f-105">Všechny aktivity, které jsou součástí <xref:System.Activities.Statements.TransactionScope.Body%2A> z <xref:System.Activities.Statements.TransactionScope> aktivity, které jsou součástí transakce.</span><span class="sxs-lookup"><span data-stu-id="bcf2f-105">Any activities that are contained in the <xref:System.Activities.Statements.TransactionScope.Body%2A> of the <xref:System.Activities.Statements.TransactionScope> activity participate in the transaction.</span></span> <span data-ttu-id="bcf2f-106">WF můžete pro tok transakcí do pracovního postupu prostřednictvím <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="bcf2f-106">WF can to flow transactions into a workflow through the use of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="bcf2f-107">Podobně jako <xref:System.Activities.Statements.TransactionScope> aktivity, všechny aktivity obsažené v <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> účastní transakce.</span><span class="sxs-lookup"><span data-stu-id="bcf2f-107">Like the <xref:System.Activities.Statements.TransactionScope> activity, any activity contained in the <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> participates in the transaction.</span></span> <span data-ttu-id="bcf2f-108">WF zajistí, že aktivity závislé na <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> funguje s oběma <xref:System.Activities.Statements.TransactionScope> a <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="bcf2f-108">WF ensures that activities dependent on <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> works with both <xref:System.Activities.Statements.TransactionScope> and <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="bcf2f-109">Pokud aktivity poskytované systémem neřeší všechny požadavky, můžete vlastní aktivity vytvořené pomocí <xref:System.Activities.RuntimeTransactionHandle> umožnit pokročilé toku a scénáře řízení transakce.</span><span class="sxs-lookup"><span data-stu-id="bcf2f-109">If the system-provided activities do not address all requirements, custom activities can be built using the <xref:System.Activities.RuntimeTransactionHandle> to enable advanced flow and transaction control scenarios.</span></span>  
  
 <span data-ttu-id="bcf2f-110">V následujícím příkladu převzaty z [základní TransactionScope](../../../docs/framework/windows-workflow-foundation/samples/basic-transactionscope.md) ukázku, pracovní postup je vytvořený, který se skládá z <xref:System.Activities.Statements.Sequence> aktivity, která obsahuje podřízené aktivity, včetně <xref:System.Activities.Statements.TransactionScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="bcf2f-110">In the following example, taken from the [Basic TransactionScope](../../../docs/framework/windows-workflow-foundation/samples/basic-transactionscope.md) sample, a workflow is constructed consisting of a <xref:System.Activities.Statements.Sequence> activity that contains child activities including a <xref:System.Activities.Statements.TransactionScope> activity.</span></span> <span data-ttu-id="bcf2f-111"><xref:System.Activities.Statements.TransactionScope.Body%2A> Činnosti <xref:System.Activities.Statements.TransactionScope> provést v transakci inicializuje pomocí <xref:System.Activities.Statements.TransactionScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="bcf2f-111">The <xref:System.Activities.Statements.TransactionScope.Body%2A> activities of the <xref:System.Activities.Statements.TransactionScope> execute under the transaction initialized by the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
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
  
 <span data-ttu-id="bcf2f-112">Další informace najdete v tématu základní [transakce](../../../docs/framework/windows-workflow-foundation/samples/transactions.md) ukázky a scénáře na základě [transakce](../../../docs/framework/windows-workflow-foundation/samples/transactions.md) ukázky.</span><span class="sxs-lookup"><span data-stu-id="bcf2f-112">For more information, see the basic [Transactions](../../../docs/framework/windows-workflow-foundation/samples/transactions.md) samples, and the scenario based [Transactions](../../../docs/framework/windows-workflow-foundation/samples/transactions.md) samples.</span></span> <span data-ttu-id="bcf2f-113">Další informace najdete v tématu o používání <xref:System.ServiceModel.Activities.TransactedReceiveScope>, najdete v části [toku transakcí do služeb pracovních postupů a mimo](../../../docs/framework/wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="bcf2f-113">For more information, see about using <xref:System.ServiceModel.Activities.TransactedReceiveScope>, see [Flowing Transactions into and out of Workflow Services](../../../docs/framework/wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcf2f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="bcf2f-114">See Also</span></span>  
 <xref:System.Activities.Statements.TransactionScope>  
 <xref:System.Transactions.TransactionScope>  
 <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
