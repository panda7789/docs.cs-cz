---
title: Začínáme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: bd82b7e83149aaa53cf1b240cb79f8747bccba47
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793911"
---
# <a name="getting-started"></a>Začínáme
Pomocí nástroje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]můžete [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] využívat technologii pro přístup k databázím SQL stejně, jako byste měli přístup ke kolekci v paměti.  
  
 `nw` Například objekt v následujícím kódu je vytvořen pro `Customers` `Northwind` reprezentaci databáze, na `Customers` cílovou tabulku, řádky jsou filtrovány z `London`a je vybrán řetězec pro `CompanyName` . pro načtení.  
  
 Po spuštění smyčky se načte kolekce `CompanyName` hodnot.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a>Další kroky  
 Další příklady, včetně vkládání a aktualizace, najdete v tématu [co můžete s LINQ to SQL](what-you-can-do-with-linq-to-sql.md).  
  
 Dále vyzkoušejte některé návody a kurzy, které vám pomají praktické zkušenosti s používáním [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Přečtěte si [návody v tématu učení](learning-by-walkthroughs.md).  
  
 Nakonec se naučíte, jak začít pracovat na vlastním [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu načtením [typických kroků pro použití LINQ to SQL](typical-steps-for-using-linq-to-sql.md).  
  
## <a name="see-also"></a>Viz také:

- [LINQ to SQL](index.md)
- [Úvod do LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [Úvod do LINQ (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [Objektový model LINQ to SQL](the-linq-to-sql-object-model.md)
