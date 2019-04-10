---
title: 'Postupy: Odeslání změn do databáze'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c7cba174-9d40-491d-b32c-f2d73b7e9eab
ms.openlocfilehash: 222ce575d9e977cc8b68862385b4a1b147c6394a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326382"
---
# <a name="how-to-submit-changes-to-the-database"></a>Postupy: Odeslání změn do databáze
Bez ohledu na to, kolik změny, které provedete do objektů dojde ke změně pouze do replik v paměti. Žádné změny provedené na skutečná data v databázi. Změny nejsou přenášeny do serveru, dokud explicitně volat <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na <xref:System.Data.Linq.DataContext>.  
  
 Když provedete toto volání <xref:System.Data.Linq.DataContext> pokusí přeložit změny na ekvivalentní příkazy jazyka SQL. Přepsat tyto akce můžete použít vlastní logiku, ale pořadí odeslání je orchestrovaných službou z <xref:System.Data.Linq.DataContext> označované jako *změnit procesoru*. Posloupnost událostí je následující:  
  
1. Při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prověřuje sadu známým objektům k určení, zda byly nové instance připojeny k nim. Pokud ano, tyto nové instance se přidají do sady sledovaných objektů.  
  
2. Všechny objekty, které mají čekající změny jsou uspořádány do sekvence objektů na základě závislostí mezi nimi. Objekty, jejichž změny závisí na jiné objekty jsou seřazeny po jejich závislosti.  
  
3. Bezprostředně před vlastní změny jsou přenášeny, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] spustí transakci zapouzdřit posloupnost jednotlivých příkazů.  
  
4. Změny objektů se přeložený jeden po druhém SQL příkazy a odeslat na server.  
  
 V tuto chvíli způsobit, že proces odeslání přestane všech chyb zjištěných v databázi a je vyvolána výjimka. Všechny změny do databáze se vrátí zpět, jako by se nikdy došlo k žádné příspěvky. <xref:System.Data.Linq.DataContext> Má stále plnou záznam všech změn. Proto můžete zkusit opravit problém a volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A> znovu, stejně jako v následujícím příkladu kódu.  
  
## <a name="example"></a>Příklad  
 Když transakce po odeslání se dokončí úspěšně, <xref:System.Data.Linq.DataContext> přijímá změny objektů ignorováním informace sledování změn.  
  
 [!code-csharp[DLinqSubmittingChanges#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#1)]
 [!code-vb[DLinqSubmittingChanges#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Zjištění a vyřešení konfliktních odeslání](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)
- [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [Vytvoření a odeslání změn dat](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
