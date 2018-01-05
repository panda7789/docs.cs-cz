---
title: "Výpočetní součet hodnot v číselného pořadí"
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
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6b28c6f9626919ee52be2a42eb2f68aecc9acbf6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a>Výpočetní součet hodnot v číselného pořadí
Použití <xref:System.Linq.Enumerable.Sum%2A> operátor vypočítat součet číselných hodnot v pořadí.  
  
 Všimněte si těchto vlastností `Sum` operátor v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:  
  
-   Agregační operátor standardní – operátor dotazu `Sum` vyhodnotí na nulu pro prázdnou sekvencí nebo sekvenci, která obsahuje jenom hodnoty Null. V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], sémantika SQL jsou ponechána beze změny. Z tohoto důvodu `Sum` vyhodnocen jako null místo na nulu pro prázdnou sekvencí nebo sekvenci, která obsahuje jenom hodnoty Null.  
  
-   Platí omezení SQL na mezilehlých výsledků agregace v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Součet počty 32bitové celé číslo není počítaný pomocí 64-bit výsledky a pro může dojít k přetečení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překlad `Sum`. Tato možnost existuje i v případě implementace standardní – operátor dotazu nezpůsobí přetečení pro odpovídající sekvence v paměti.  
  
## <a name="example"></a>Příklad  
 Vyhledá celkový nákladní všech objednávek v následujícím příkladu `Order` tabulky.  
  
 Pokud spustíte tento dotaz proti ukázková databáze Northwind, je výstup: `64942.6900`.  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a>Příklad  
 Následující příklad vyhledá celkový počet jednotek v pořadí pro všechny produkty.  
  
 Pokud spustíte tento dotaz proti ukázková databáze Northwind, je výstup: `780`.  
  
 Všimněte si, že musíte vysílat `short` typy (například `UnitsOnOrder`) protože `Sum` nemá žádné přetížení pro krátké typy.  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a>Viz také  
 [Agregační dotazy](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [Stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
