---
title: Vzdálené vs. Místní spuštění
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
ms.openlocfilehash: 9d72350c472ff68d8ee623d82096bdab0c88abb3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547115"
---
# <a name="remote-vs-local-execution"></a>Vzdálené vs. Místní spuštění
Můžete se rozhodnout spustit dotazy buď vzdáleně (to znamená, že databázový stroj provede dotaz na databázi) nebo místně ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provede dotaz proti místní mezipaměti).  
  
## <a name="remote-execution"></a>Vzdálené spuštění  
 Vezměte v úvahu následující dotaz:  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 Pokud má vaše databáze tisíce řádků objednávek, nechcete je načíst všechny malou zpracovat. V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.EntitySet%601> implementuje třída <xref:System.Linq.IQueryable> rozhraní. Tento přístup zajišťuje, že tyto dotazy mohou být provedeny vzdáleně. Tato technika tok dvě hlavní výhody:  
  
-   Není načten nepotřebná data.  
  
-   Dotaz proveden databázový stroj je často efektivnější z důvodu indexy databáze.  
  
## <a name="local-execution"></a>Místní spuštění  
 V ostatních případech můžete chtít mít v místní mezipaměti úplnou sadu souvisejících entit. Pro tento účel <xref:System.Data.Linq.EntitySet%601> poskytuje <xref:System.Data.Linq.EntitySet%601.Load%2A> metodu pro explicitní načtení všech členů <xref:System.Data.Linq.EntitySet%601>.  
  
 Pokud <xref:System.Data.Linq.EntitySet%601> je již načten, následující dotazy se spouštějí místně. Tento přístup pomáhá dvěma způsoby:  
  
-   Pokud se všechny musí využívat místně nebo více než jednou, se můžete vyhnout vzdálené dotazy a související latenci.  
  
-   Entity lze serializovat jako úplnou entitu.  
  
 Následující fragment kódu ukazuje, jak místní spuštění lze získat:  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a>Srovnání  
 Tyto dvě schopnosti poskytovat výkonnou kombinaci možností: vzdálené spouštění rozsáhlých kolekcí a místní spuštění pro malé kolekce nebo kde je potřeba úplnou kolekci. Implementace vzdálené spuštění prostřednictvím <xref:System.Linq.IQueryable>a místní spuštění proti v paměti <xref:System.Collections.Generic.IEnumerable%601> kolekce. Chcete-li vynutit místní spuštění (to znamená, <xref:System.Collections.Generic.IEnumerable%601>), najdete v článku [převod typu na obecnou položku IEnumerable](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md).  
  
### <a name="queries-against-unordered-sets"></a>Dotazy na Neseřazený sady  
 Všimněte si důležitý rozdíl mezi místní kolekci, která implementuje <xref:System.Collections.Generic.List%601> a kolekce, která poskytuje vzdálený dotazů vůči *neuspořádaná sady* v relační databázi. <xref:System.Collections.Generic.List%601> metody, jako jsou ty, které používají hodnoty indexu vyžadovat seznamu sémantiku, která obvykle je nelze získat prostřednictvím vzdálený dotaz proti neuspořádanou sadu. Z tohoto důvodu se tyto metody implicitně načíst <xref:System.Data.Linq.EntitySet%601> umožňující místní spouštění.  
  
## <a name="see-also"></a>Viz také:
- [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
