---
title: Určení součtu hodnot v číselné posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
ms.openlocfilehash: 2f66b996a0e688205d61f5fca476c0335616ee38
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59143569"
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a>Určení součtu hodnot v číselné posloupnosti
Použití <xref:System.Linq.Enumerable.Sum%2A> operátor pro výpočet součtu číselných hodnot v sekvenci.  
  
 Mějte na paměti následující charakteristiky `Sum` operátor v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:  
  
-   Standardní operátor dotazu agregační operátor `Sum` vyhodnocen jako nula k prázdné sekvenci nebo sekvenci, která obsahuje pouze hodnoty Null. V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], sémantika SQL jsou ponechány beze změny. Z tohoto důvodu `Sum` vyhodnotí na hodnotu null namísto na nulu pro prázdnou sekvencí nebo pro sekvenci, která obsahuje pouze hodnoty Null.  
  
-   Platí omezení SQL na mezilehlých výsledků agregace v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Součet počty 32bitové celé číslo není počítaný pomocí 64-bit výsledky a přetečení se může stát [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překlad `Sum`. Tato možnost existuje i v případě, že implementace standardní operátor dotazu nezpůsobí přetečení pro odpovídající sekvence v paměti.  
  
## <a name="example"></a>Příklad  
 Následující příklad vyhledá Dopravné celkem všech objednávek v `Order` tabulky.  
  
 Pokud spouštíte skript v ukázkové databázi Northwind tento dotaz, je výstup: `64942.6900`.  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a>Příklad  
 Následující příklad vyhledá celkový počet jednotek v pořadí pro všechny produkty.  
  
 Pokud spouštíte skript v ukázkové databázi Northwind tento dotaz, je výstup: `780`.  
  
 Všimněte si, že musíte přetypovat `short` typů (například `UnitsOnOrder`) protože `Sum` nemá žádné přetížení pro krátké typy.  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a>Viz také:

- [Agregační dotazy](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
- [Stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
