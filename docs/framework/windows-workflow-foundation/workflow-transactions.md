---
title: Pracovní postup transakce
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 66eecb9795c5a65b03559c28f2bfab0b3992bc8f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="workflow-transactions"></a>Pracovní postup transakce
[!INCLUDE[wf1](../../../includes/wf1-md.md)] poskytuje podporu pro účastní <xref:System.Transactions> transakce pomocí <xref:System.Activities.Statements.TransactionScope> aktivity k určení rozsahu zpracovaných jednotka práce. Při <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> musí být explicitně Dokončit <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> implicitně volání provést aktivitu v transakci po úspěšném dokončení. Všechny aktivity, které jsou součástí <xref:System.Activities.Statements.TransactionScope.Body%2A> z <xref:System.Activities.Statements.TransactionScope> aktivity, které jsou součástí transakce. WF můžete pro tok transakcí do pracovního postupu prostřednictvím <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity. Podobně jako <xref:System.Activities.Statements.TransactionScope> aktivity, všechny aktivity obsažené v <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> účastní transakce. WF zajistí, že aktivity závislé na <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> funguje s oběma <xref:System.Activities.Statements.TransactionScope> a <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Pokud aktivity poskytované systémem neřeší všechny požadavky, můžete vlastní aktivity vytvořené pomocí <xref:System.Activities.RuntimeTransactionHandle> umožnit pokročilé toku a scénáře řízení transakce.  
  
 V následujícím příkladu převzaty z [základní TransactionScope](../../../docs/framework/windows-workflow-foundation/samples/basic-transactionscope.md) ukázku, pracovní postup je vytvořený, který se skládá z <xref:System.Activities.Statements.Sequence> aktivity, která obsahuje podřízené aktivity, včetně <xref:System.Activities.Statements.TransactionScope> aktivity. <xref:System.Activities.Statements.TransactionScope.Body%2A> Činnosti <xref:System.Activities.Statements.TransactionScope> provést v transakci inicializuje pomocí <xref:System.Activities.Statements.TransactionScope> aktivity.  
  
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
  
 Další informace najdete v tématu základní [transakce](../../../docs/framework/windows-workflow-foundation/samples/transactions.md) ukázky a scénáře na základě [transakce](../../../docs/framework/windows-workflow-foundation/samples/transactions.md) ukázky. Další informace najdete v tématu o používání <xref:System.ServiceModel.Activities.TransactedReceiveScope>, najdete v části [toku transakcí do služeb pracovních postupů a mimo](../../../docs/framework/wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Activities.Statements.TransactionScope>  
 <xref:System.Transactions.TransactionScope>  
 <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
