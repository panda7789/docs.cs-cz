---
title: Vzdálené vs. místní spuštění
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
ms.openlocfilehash: a21d5bbffdb1a78d3062929a1ca384a750af59a7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781166"
---
# <a name="remote-vs-local-execution"></a>Vzdálené vs. místní spuštění
Můžete se rozhodnout spustit dotazy buď vzdáleně (to znamená, že databázový stroj provede dotaz na databázi) nebo lokálně ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] spustí dotaz na místní mezipaměti).  
  
## <a name="remote-execution"></a>Vzdálené spuštění  
 Vezměte v úvahu následující dotaz:  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 Pokud má vaše databáze tisíce řádků objednávek, nechcete je načíst pro zpracování malé podmnožiny. V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ,<xref:System.Data.Linq.EntitySet%601> třída implementuje<xref:System.Linq.IQueryable> rozhraní. Tento přístup zajišťuje, že tyto dotazy mohou být spouštěny vzdáleně. Dva hlavní výhody plynoucí z této techniky:  
  
- Nepovedlo se načíst nepotřebná data.  
  
- Dotaz spuštěný databázovým strojem je často efektivnější z důvodu indexů databáze.  
  
## <a name="local-execution"></a>místní spuštění  
 V jiných situacích možná budete chtít mít kompletní sadu souvisejících entit v místní mezipaměti. Pro tento účel <xref:System.Data.Linq.EntitySet%601> <xref:System.Data.Linq.EntitySet%601.Load%2A> poskytuje metodu pro explicitní načtení <xref:System.Data.Linq.EntitySet%601>všech členů.  
  
 <xref:System.Data.Linq.EntitySet%601> Pokud je již načten, následné dotazy jsou spouštěny místně. Tento přístup pomáhá dvěma způsoby:  
  
- Pokud se úplná sada musí používat místně nebo víckrát, můžete se vyhnout vzdáleným dotazům a přidruženým latencím.  
  
- Entita může být serializována jako kompletní entita.  
  
 Následující fragment kódu ukazuje, jak lze získat místní spuštění:  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a>Srovnání  
 Tyto dvě funkce poskytují výkonnou kombinaci možností: vzdálené spuštění velkých kolekcí a místní spouštění pro malé kolekce, nebo kde je potřeba kompletní kolekce. Implementujete vzdálené spouštění prostřednictvím <xref:System.Linq.IQueryable>a místní spuštění proti kolekci v paměti. <xref:System.Collections.Generic.IEnumerable%601> Chcete-li vynutit místní spuštění ( <xref:System.Collections.Generic.IEnumerable%601>tj.), přečtěte si téma [převod typu na obecné rozhraní IEnumerable](convert-a-type-to-a-generic-ienumerable.md).  
  
### <a name="queries-against-unordered-sets"></a>Dotazy na neuspořádané sady  
 Všimněte si důležitého rozdílu mezi místní kolekcí, <xref:System.Collections.Generic.List%601> která implementuje, a kolekcí, která poskytuje vzdálené dotazy spouštěné proti *neuspořádaným sadám* v relační databázi. <xref:System.Collections.Generic.List%601>metody, jako jsou například ty, které používají hodnoty indexu, vyžadují sémantiku seznamu, což obvykle nelze získat pomocí vzdáleného dotazu proti neuspořádané sadě. Z tohoto důvodu tyto metody implicitně načtou <xref:System.Data.Linq.EntitySet%601> a umožňují místní spuštění.  
  
## <a name="see-also"></a>Viz také:

- [Koncepty dotazů](query-concepts.md)
