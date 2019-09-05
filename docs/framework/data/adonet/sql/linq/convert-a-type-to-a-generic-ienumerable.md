---
title: Převod typu na obecnou položku IEnumerable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: c92f65c22fe4b4128a171c757bb9e9c0ccbc3fee
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247732"
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a>Převod typu na obecnou položku IEnumerable
Použijte <xref:System.Linq.Enumerable.AsEnumerable%2A> k vrácení argumentu zadaného jako obecné `IEnumerable`.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu ( [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pomocí výchozího obecného `Query`) se pokusí převést dotaz na SQL a spustit ho na serveru. Ale klauzule odkazuje na uživatelem definovanou metodu na straně klienta (`isValidProduct`), kterou nelze převést na SQL. `where`  
  
 Řešením je určit obecnou <xref:System.Collections.Generic.IEnumerable%601> `where` implementaci na straně klienta pro nahrazení obecného <xref:System.Linq.IQueryable%601>. Provedete to vyvoláním <xref:System.Linq.Enumerable.AsEnumerable%2A> operátoru.  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a>Viz také:

- [Příklady dotazů](query-examples.md)
