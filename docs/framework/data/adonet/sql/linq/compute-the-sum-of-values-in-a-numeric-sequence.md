---
title: Určení součtu hodnot v číselné posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
ms.openlocfilehash: 3a404068c2d89610aa9b01b392bca40f82e17707
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247917"
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a>Určení součtu hodnot v číselné posloupnosti
<xref:System.Linq.Enumerable.Sum%2A> Použijte operátor k výpočtu součtu číselných hodnot v sekvenci.  
  
 Všimněte si následujících vlastností `Sum` operátoru v: [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
- Agregační operátor `Sum` standardního operátoru dotazu vyhodnocuje nulu pro prázdnou sekvenci nebo sekvenci, která obsahuje pouze hodnoty null. V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]systému jsou sémantika jazyka SQL ponechána beze změny. Z tohoto důvodu je `Sum` vyhodnocena na hodnotu null namísto na nulu pro prázdnou sekvenci nebo pro sekvenci, která obsahuje pouze hodnoty null.  
  
- Omezení SQL pro mezilehlé výsledky se vztahují na agregace v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Součet 32 celočíselných celočíselných hodnot není počítán pomocí 64 bitových výsledků a přetečení může nastat pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Sum`překlad. Tato možnost existuje i v případě, že standardní implementace operátoru dotazu nezpůsobí přetečení odpovídající posloupnosti v paměti.  
  
## <a name="example"></a>Příklad  
 Následující příklad najde celkové přepravení všech objednávek v `Order` tabulce.  
  
 Pokud spustíte tento dotaz proti ukázkové databázi Northwind, výstup je: `64942.6900`.  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a>Příklad  
 Následující příklad najde celkový počet jednotek v pořadí pro všechny produkty.  
  
 Pokud spustíte tento dotaz proti ukázkové databázi Northwind, výstup je: `780`.  
  
 Všimněte si, že je `short` nutné přetypovat typy ( `UnitsOnOrder`například), `Sum` protože nemá žádné přetížení pro krátké typy.  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a>Viz také:

- [Agregační dotazy](aggregate-queries.md)
- [Stažení ukázkových databází](downloading-sample-databases.md)
