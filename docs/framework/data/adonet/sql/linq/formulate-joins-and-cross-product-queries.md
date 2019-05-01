---
title: Formulování spojení a dotazů napříč produkty
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
ms.openlocfilehash: b0037f56947a86627ee9ea84369527aec859a0f8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032601"
---
# <a name="formulate-joins-and-cross-product-queries"></a>Formulování spojení a dotazů napříč produkty
Následující příklady znázorňují způsob kombinace výsledků z více tabulek.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá cizího klíče navigace ve `From` klauzule v jazyce Visual Basic (`from` klauzuli v C#) Chcete-li vybrat všechny objednávky pro zákazníky, kteří v Londýně.  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá cizího klíče navigace v `Where` klauzule v jazyce Visual Basic (`where` klauzuli v C#) Chcete-li filtrovat mimo akcie `Products` jehož `Supplier` je ve Spojených státech.  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá cizího klíče navigace v `From` klauzule v jazyce Visual Basic (`from` klauzuli v C#) Chcete-li filtrovat zaměstnanci v Praze a seznam jejich území.  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá cizího klíče navigace ve `Select` klauzule v jazyce Visual Basic (`select` klauzuli v C#) Chcete-li filtrovat páry zaměstnanců, kde sestavy jeden ze zaměstnanců na druhý a kde jsou obě zaměstnanci ze stejné `City`.  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a>Příklad  
 Následující příklad jazyka Visual Basic vyhledá všechny zákazníci a objednávky, zajišťuje, že zákazníci budou odpovídat objednávky a zaručuje, že pro každý zákazník v tomto seznamu jméno kontaktní osoby je k dispozici.  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a>Příklad  
 Následující příklad připojí explicitně dvě tabulky a projekty výsledky z obou tabulek.  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a>Příklad  
 Následující příklad explicitně sloučí tři tabulky a projekty výsledky z každé z nich.  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak dosáhnout `LEFT OUTER JOIN` pomocí `DefaultIfEmpty()`. `DefaultIfEmpty()` Metoda vrátí hodnotu null, pokud neexistuje žádný `Order` pro `Employee`.  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a>Příklad  
 Následující vzorové projekty `let` výraz vyplývající z spojení.  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `join` s složený klíč.  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `join` kde na jedné straně může mít hodnotu Null a druhá ne.  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a>Viz také:

- [Příklady dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
