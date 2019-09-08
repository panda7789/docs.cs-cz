---
title: 'Postupy: Odeslání změn do databáze'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c7cba174-9d40-491d-b32c-f2d73b7e9eab
ms.openlocfilehash: c279d4ed32aed4788ee5866a24572663a1e2f580
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793103"
---
# <a name="how-to-submit-changes-to-the-database"></a>Postupy: Odeslání změn do databáze
Bez ohledu na to, kolik změn provedete v objektech, jsou změny provedeny pouze v replikách v paměti. Neudělali jste žádné změny v skutečných datech v databázi. Vaše změny se neodesílají na server, dokud explicitně nebudete <xref:System.Data.Linq.DataContext.SubmitChanges%2A> volat <xref:System.Data.Linq.DataContext>.  
  
 Po provedení tohoto volání se <xref:System.Data.Linq.DataContext> pokusí přeložit změny do ekvivalentních příkazů SQL. Pomocí vlastní logiky můžete tyto akce přepsat, ale pořadí odeslání je Orchestrované pomocí služby <xref:System.Data.Linq.DataContext> známé jako *procesor změn*. Sekvence událostí je následující:  
  
1. Když <xref:System.Data.Linq.DataContext.SubmitChanges%2A>zavoláte [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , prověřuje sadu známých objektů a určí, zda jsou k nim připojeny nové instance. Pokud mají, tyto nové instance se přidají do sady sledovaných objektů.  
  
2. Všechny objekty, které mají probíhající změny, jsou uspořádány do sekvence objektů na základě závislostí mezi nimi. Objekty, jejichž změny závisí na jiných objektech, se sekvencují po jejich závislosti.  
  
3. Ihned před odesláním jakýchkoli aktuálních změn [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] spustí transakce k zapouzdření řady jednotlivých příkazů.  
  
4. Změny objektů jsou přeloženy jedním z nich na příkazy SQL a odeslány na server.  
  
 V tomto okamžiku všechny chyby zjištěné databází způsobují zastavení procesu odeslání a je vyvolána výjimka. Všechny změny v databázi se vrátí zpět, jako by nebyly k dispozici žádné odeslání. <xref:System.Data.Linq.DataContext> Pořád má úplný záznam o všech změnách. Proto se můžete pokusit problém vyřešit a zavolat <xref:System.Data.Linq.DataContext.SubmitChanges%2A> znovu, jako v následujícím příkladu kódu.  
  
## <a name="example"></a>Příklad  
 Pokud je transakce kolem odeslání úspěšně dokončena, <xref:System.Data.Linq.DataContext> akceptuje změny objektů ignorováním informací o sledování změn.  
  
 [!code-csharp[DLinqSubmittingChanges#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#1)]
 [!code-vb[DLinqSubmittingChanges#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Zjištění a vyřešení konfliktních odeslání](how-to-detect-and-resolve-conflicting-submissions.md)
- [Postupy: Správa konfliktů změn](how-to-manage-change-conflicts.md)
- [Stažení ukázkových databází](downloading-sample-databases.md)
- [Vytvoření a odeslání změn dat](making-and-submitting-data-changes.md)
