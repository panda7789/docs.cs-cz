---
title: Transakce pracovního postupu
ms.date: 03/30/2017
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
ms.openlocfilehash: cb2a72bb24640d214170c52b8b3bf0a328d3f775
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714616"
---
# <a name="workflow-transactions"></a>Transakce pracovního postupu

[!INCLUDE[wf1](../../../includes/wf1-md.md)] poskytuje podporu pro účastní <xref:System.Transactions> transakce pomocí <xref:System.Activities.Statements.TransactionScope> aktivity k určení oboru transakce jednotku práce. Zatímco <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> musí být explicitně Dokončit <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> aktivity implicitně volání dokončení transakce po úspěšném dokončení. Všechny aktivity, které jsou součástí <xref:System.Activities.Statements.TransactionScope.Body%2A> z <xref:System.Activities.Statements.TransactionScope> aktivity účasti v transakci. WF můžete tok transakcí do pracovních postupů prostřednictvím <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity. Podobně jako <xref:System.Activities.Statements.TransactionScope> aktivity, všechny obsažené v <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> účastní v transakci. WF zajišťuje této aktivity závislé na <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> pracuje s oběma <xref:System.Activities.Statements.TransactionScope> a <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Pokud poskytované systémem aktivity se nezabývají všechny požadavky, můžete vlastní aktivity vytvořené pomocí <xref:System.Activities.RuntimeTransactionHandle> povolit pokročilé toku a scénáře řízení transakce.  
  
V následujícím příkladu je vytvořen skládající se z pracovního postupu <xref:System.Activities.Statements.Sequence> aktivitu, která obsahuje podřízené aktivity, včetně <xref:System.Activities.Statements.TransactionScope> aktivity. <xref:System.Activities.Statements.TransactionScope.Body%2A> Aktivity <xref:System.Activities.Statements.TransactionScope> provést v rámci transakce inicializovány <xref:System.Activities.Statements.TransactionScope> aktivity.  
  
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
  
Další informace najdete v tématu o použití <xref:System.ServiceModel.Activities.TransactedReceiveScope>, naleznete v tématu [tok transakcí do a ze služby pracovních postupů](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Activities.Statements.TransactionScope>
- <xref:System.Transactions.TransactionScope>
- <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
