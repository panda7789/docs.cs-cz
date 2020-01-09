---
title: Začínáme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: 3bff4e9f268e9eac84c244cb58eed8b4384e717d
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634687"
---
# <a name="getting-started"></a>Začínáme
Pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]můžete technologii LINQ použít pro přístup k databázím SQL stejně, jako byste měli přístup ke kolekci v paměti.  
  
 Například objekt `nw` v následujícím kódu je vytvořen tak, aby představoval databázi `Northwind`, cílová tabulka `Customers`, řádky jsou filtrovány pro `Customers` z `London`a řetězec pro `CompanyName` je vybrán pro načtení.  
  
 Po spuštění smyčky se načtou kolekce hodnot `CompanyName`.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a>Další kroky  
 Další příklady, včetně vkládání a aktualizace, najdete v tématu [co můžete s LINQ to SQL](what-you-can-do-with-linq-to-sql.md).  
  
 Dále vyzkoušejte některé návody a kurzy, které vám pomají praktickou zkušenost s používáním [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Přečtěte si [návody v tématu učení](learning-by-walkthroughs.md).  
  
 Nakonec se naučíte, jak začít používat vlastní [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projekt, a to čtením [typických kroků pro použití LINQ to SQL](typical-steps-for-using-linq-to-sql.md).  
  
## <a name="see-also"></a>Viz také:

- [LINQ to SQL](index.md)
- [Úvod do LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [Úvod do LINQ (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [Objektový model LINQ to SQL](the-linq-to-sql-object-model.md)
