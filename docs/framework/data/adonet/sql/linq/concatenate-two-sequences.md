---
title: Řetězení dvě pořadí
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
ms.openlocfilehash: c0a6dde667c4f858d8177dc80a726619f463f3a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354050"
---
# <a name="concatenate-two-sequences"></a>Řetězení dvě pořadí
Použití <xref:System.Linq.Queryable.Concat%2A> operátor ke zřetězení dvě pořadí.  
  
 <xref:System.Linq.Queryable.Concat%2A> Operátor je definována pro seřazené multisets kde objednávky příjemce a argument jsou stejné.  
  
 Řazení v systému SQL je v posledním kroku, před vytváří výsledky. Z tohoto důvodu <xref:System.Linq.Queryable.Concat%2A> operátor je implementována pomocí `UNION ALL` a nezachovává pořadí argumentů. Ujistěte se, že řazení je správný ve výsledcích, zajistěte, aby explicitně řazení výsledků.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Linq.Queryable.Concat%2A> vrátit pořadí všech `Customer` a `Employee` číslo telefonu a faxu.  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Linq.Queryable.Concat%2A> vrátit pořadí všech `Customer` a `Employee` název a telefonní číslo mapování.  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a>Viz také  
 [Příklady dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [Převod standardních operátorů dotazů](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
