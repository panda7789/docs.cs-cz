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
# <a name="workflow-transactions"></a>Transakce pracovního postupu

[!INCLUDE[wf1](../../../includes/wf1-md.md)]poskytuje podporu pro <xref:System.Transactions> účast v <xref:System.Activities.Statements.TransactionScope> transakcích pomocí aktivity k rozsahu transakční jednotky práce. Zatímco <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> musí být explicitně dokončena aktivita <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> implicitně volá dokončení transakce po úspěšném dokončení. Všechny aktivity, které <xref:System.Activities.Statements.TransactionScope.Body%2A> jsou <xref:System.Activities.Statements.TransactionScope> obsaženy v aktivitě účastnit transakce. Wf může tok transakcí do pracovního <xref:System.ServiceModel.Activities.TransactedReceiveScope> postupu pomocí aktivity. Stejně <xref:System.Activities.Statements.TransactionScope> jako aktivita, všechny <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> aktivity obsažené v účasti v transakci. Služba WF zajišťuje, <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> že aktivity <xref:System.ServiceModel.Activities.TransactedReceiveScope>závislé na práci s oběma a <xref:System.Activities.Statements.TransactionScope> . Pokud aktivity poskytované systémem neřeší všechny požadavky, vlastní aktivity lze sestavit pomocí <xref:System.Activities.RuntimeTransactionHandle> povolit pokročilé toku a řízení transakcí scénáře.  
  
V následujícím příkladu je vytvořen pracovní postup <xref:System.Activities.Statements.Sequence> skládající se z <xref:System.Activities.Statements.TransactionScope> aktivity, která obsahuje podřízené aktivity včetně aktivity. Aktivity <xref:System.Activities.Statements.TransactionScope.Body%2A> provést <xref:System.Activities.Statements.TransactionScope> v rámci transakce inicializovány aktivitou. <xref:System.Activities.Statements.TransactionScope>  
  
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
  
Další informace naleznete v <xref:System.ServiceModel.Activities.TransactedReceiveScope>tématu použití , naleznete [v tématu plynulé transakce do a z pracovního postupu služby](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Activities.Statements.TransactionScope>
- <xref:System.Transactions.TransactionScope>
- <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
