---
title: Formulování spojení a dotazů napříč produkty
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
ms.openlocfilehash: 002a644ff5d48b25351228dcd74330707491d6c8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782091"
---
# <a name="formulate-joins-and-cross-product-queries"></a>Formulování spojení a dotazů napříč produkty
Následující příklady znázorňují, jak kombinovat výsledky z více tabulek.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se používá navigace pomocí cizího `From` klíče v klauzuli v`from` Visual Basic ( C#klauzule in) pro výběr všech objednávek pro zákazníky v Londýně.  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se používá navigace pomocí cizího `Where` klíče v klauzuli v`where` Visual Basic ( C#klauzule in) k filtrování pro nepoužitou `Products` populaci `Supplier` , jejíž je v USA.  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se používá navigace pomocí cizího `From` klíče v klauzuli v`from` Visual Basic ( C#klauzule in) k filtrování zaměstnanců v Seattlu a k vypsání jejich oblastí.  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se používá navigace pomocí cizího `Select` klíče v klauzuli v`select` Visual Basic ( C#klauzule in) k filtrování párů zaměstnanců, kteří jeden zaměstnanec nahlásí do druhé a kde jsou oba zaměstnanci ze stejné `City`.  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a>Příklad  
 Následující Visual Basic příklad vyhledá všechny zákazníky a objednávky, zajistěte, aby objednávky odpovídaly zákazníkům, a zaručuje, že pro každého zákazníka v tomto seznamu se zadá jméno kontaktu.  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a>Příklad  
 Následující příklad explicitně spojí dvě tabulky a projekty z obou tabulek.  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a>Příklad  
 Následující příklad explicitně spojí tři tabulky a projekty z každého z nich.  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak dosáhnout `LEFT OUTER JOIN` pomocí. `DefaultIfEmpty()` Metoda vrátí hodnotu null, pokud `Order` není pro `Employee`. `DefaultIfEmpty()`  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a>Příklad  
 Následující příklad vyjedná výraz `let` , který je výsledkem spojení.  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje a `join` obsahuje složený klíč.  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit, kde `join` jedna strana může mít hodnotu null a druhá není.  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a>Viz také:

- [Příklady dotazů](query-examples.md)
