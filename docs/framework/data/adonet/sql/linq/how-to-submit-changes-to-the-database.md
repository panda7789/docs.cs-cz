---
title: 'Postupy: odeslání změn do databáze'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c7cba174-9d40-491d-b32c-f2d73b7e9eab
ms.openlocfilehash: fef41cd1bcb9d1c4b98f96975c56bfa19c675608
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362883"
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
