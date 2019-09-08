---
title: Odložené vs. okamžité načítání
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1d7247f-a3b7-460b-b342-5c1a2365aa1a
ms.openlocfilehash: 2045cab19e7400f94888297571a172de1578094d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794138"
---
# <a name="deferred-versus-immediate-loading"></a>Odložené vs. okamžité načítání
Při dotazování na objekt skutečně načtete pouze požadovaný objekt. *Související* objekty nejsou automaticky načteny ve stejnou dobu. (Další informace najdete v tématu [dotazování napříč relacemi](querying-across-relationships.md).) Nemůžete vidět skutečnost, že související objekty ještě nejsou načtené, protože se k nim pokusíte získat přístup.  
  
 Můžete například chtít zadat dotaz na konkrétní sadu objednávek a pak jenom občas odeslat e-mailové oznámení konkrétním zákazníkům. Proto nutně nemusíte potřebovat načíst všechna zákaznická data se všemi objednávkami. Odložené načítání můžete použít k odložení načítání dalších informací, dokud je nebudete muset naprosto. Vezměte v úvahu v následujícím příkladu:  
  
 [!code-csharp[DLinqQueryConcepts#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#1)]
 [!code-vb[DLinqQueryConcepts#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#1)]  
  
 Opak může mít také hodnotu true. Je možné, že máte aplikaci, která má zobrazit data zákazníků a objednávek ve stejnou dobu. Víte, že potřebujete obě sady dat. Víte, že vaše aplikace potřebuje informace o objednávkách pro každého zákazníka hned po dosažení výsledků. Nechcete odesílat jednotlivé dotazy na objednávky pro každého zákazníka. To, co opravdu chcete, je načíst data objednávky společně se zákazníky.  
  
 [!code-csharp[DLinqQueryConcepts#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#2)]
 [!code-vb[DLinqQueryConcepts#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#2)]  
  
 Můžete se také připojit k zákazníkům a objednávkám v dotazu tím, že provedete různé produkty a načtete všechny relativní bity dat jako jednu velkou projekci. Ale tyto výsledky nejsou entitami. (Další informace najdete v tématu [Model LINQ to SQL objektů](the-linq-to-sql-object-model.md)). Entity jsou objekty, které mají identitu a kterou můžete upravovat, zatímco tyto výsledky budou projekce, které nelze změnit a zachovat. Ještě horší je, že byste nahlásili spoustu redundantních dat, protože každý zákazník opakuje každou objednávku ve výstupu s plochými spojeními.  
  
 To, co skutečně potřebujete, je způsob, jak načíst sadu souvisejících objektů ve stejnou dobu. Sada je vymezená část grafu, takže nikdy nebudete mít více nebo méně, než bylo nutné pro zamýšlené použití. Pro účely tohoto účelu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje <xref:System.Data.Linq.DataLoadOptions> pro okamžité načtení oblasti objektového modelu. Mezi tyto metody patří:  
  
- <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> Metodu, která okamžitě načte data související s hlavním cílem.  
  
- <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> Metoda pro filtrování objektů načtených pro konkrétní vztah.  
  
## <a name="see-also"></a>Viz také:

- [Koncepty dotazů](query-concepts.md)
