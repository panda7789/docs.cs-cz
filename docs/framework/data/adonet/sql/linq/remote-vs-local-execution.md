---
title: Vzdálené vs. Místní spuštění
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
ms.openlocfilehash: 9488cb4c15c2e0646d91bdba36e7d4e2be2efbbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="remote-vs-local-execution"></a>Vzdálené vs. Místní spuštění
Můžete se rozhodnout spustit své dotazy buď vzdáleně (to znamená, databázový stroj provede dotaz na databázi nástroje) nebo místně ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provede dotaz proti místní mezipaměti).  
  
## <a name="remote-execution"></a>Vzdálené spuštění  
 Vezměte v úvahu následující dotaz:  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 Pokud má vaše databáze tisíce řádky objednávky, nechcete je načtou všechny zpracovat malou. V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.EntitySet%601> třída implementuje <xref:System.Linq.IQueryable> rozhraní. Tento přístup zajišťuje, že takové dotazy můžete provést vzdáleně. Dvě hlavní výhody tok ze tento postup:  
  
-   Není-li načíst nepotřebná data.  
  
-   Dotaz spuštěný pro databázový stroj je často efektivní kvůli indexy databáze.  
  
## <a name="local-execution"></a>Místní spuštění  
 V ostatních případech můžete chtít mít kompletní sadu entit v relaci v místní mezipaměti. Pro tento účel <xref:System.Data.Linq.EntitySet%601> poskytuje <xref:System.Data.Linq.EntitySet%601.Load%2A> metoda explicitně načíst všechny členy <xref:System.Data.Linq.EntitySet%601>.  
  
 Pokud <xref:System.Data.Linq.EntitySet%601> je již načtena, následné dotazy jsou spouštěny místně. Tento přístup umožňuje, aby dvěma způsoby:  
  
-   Pokud kompletní sadu se musí použít místně nebo několikrát, se můžete vyhnout vzdálených dotazů a přidružené latenci.  
  
-   Entita může serializovat jako úplnou entitu.  
  
 Následující fragment kódu ukazuje, jak místní provádění získat:  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a>Srovnání  
 Tyto dvě možnosti poskytují výkonný kombinaci možností: vzdálené spuštění rozsáhlých kolekcí a místní spuštění pro malé kolekce nebo kde je potřeba úplnou kolekci. Implementace vzdálené spuštění prostřednictvím <xref:System.Linq.IQueryable>a místní provádění proti v paměti <xref:System.Collections.Generic.IEnumerable%601> kolekce. Chcete-li vynutit místní provádění (tedy <xref:System.Collections.Generic.IEnumerable%601>), najdete v části [převést typ na obecný IEnumerable](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md).  
  
### <a name="queries-against-unordered-sets"></a>Dotazy na neuspořádaný sady  
 Všimněte si důležitý rozdíl mezi místní kolekce, která implementuje <xref:System.Collections.Generic.List%601> a kolekce, která poskytuje vzdálené dotazy prováděné vůči *neuspořádané sady* v relační databázi. <xref:System.Collections.Generic.List%601> metody, jako jsou ty, které používají hodnoty indexu vyžadují sémantiku seznamu, který nelze obvykle získat prostřednictvím vzdálený dotaz proti neuspořádaný sady. Z tohoto důvodu se tyto metody implicitně zatížení <xref:System.Data.Linq.EntitySet%601> umožňuje místní spuštění.  
  
## <a name="see-also"></a>Viz také  
 [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
