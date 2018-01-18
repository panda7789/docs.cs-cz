---
title: "Postupy: odeslání změn do databáze"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c7cba174-9d40-491d-b32c-f2d73b7e9eab
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: bf1f9c7982cf9f328fe060266762658ab9693c2e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-submit-changes-to-the-database"></a>Postupy: odeslání změn do databáze
Bez ohledu na to, kolik změny k objektům jsou provedeny změny jenom pro repliky v paměti. Žádné změny provedené na skutečná data v databázi. Změny nejsou přenášeny do serveru, dokud explicitně volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na <xref:System.Data.Linq.DataContext>.  
  
 Pokud provedete toto volání <xref:System.Data.Linq.DataContext> pokusí přeložit změny do ekvivalentní příkazy SQL. Vlastní logiky můžete přepsat tyto akce, ale pořadí odeslání je řízená službu <xref:System.Data.Linq.DataContext> známé jako *změnit procesoru*. Posloupnost událostí je následující:  
  
1.  Při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prověřuje sadu objektů známé k určení, zda byly nové instance připojeny k nim. Pokud budou mít, jsou tyto nové instance přidat do sady sledovaných objektů.  
  
2.  Všechny objekty, které jsou čekající změny, jsou uspořádány do posloupnost objekty podle jejich vzájemné závislosti. Objekty jejichž změny závisí na jiné objekty jsou seřazeny po jejich závislosti.  
  
3.  Bezprostředně před změny skutečné přenášejí, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] spustí transakci zapouzdření řadu jednotlivé příkazy.  
  
4.  Změny objektů jsou přeložený postupně na příkazy SQL a odesílá na server.  
  
 V tomto okamžiku všech chyb zjištěných při databáze způsobit zastavení procesu odeslání a dojde k výjimce. Všechny změny do databáze jsou vráceny zpět, jako by se někdy došlo k chybě bez odesílání. <xref:System.Data.Linq.DataContext> Má stále úplný záznam všech změn. Proto můžete zkusit opravit problém a volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A> znovu, jako v příkladu kódu, který následuje dále.  
  
## <a name="example"></a>Příklad  
 Pokud transakce kolem odesílání je dokončeno, <xref:System.Data.Linq.DataContext> přijímá změny objektů, které informace o sledování změn je ignorována.  
  
 [!code-csharp[DLinqSubmittingChanges#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#1)]
 [!code-vb[DLinqSubmittingChanges#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Zjištění a vyřešení konfliktních odeslání](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)  
 [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [Stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [Vytvoření a odeslání změn dat](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
