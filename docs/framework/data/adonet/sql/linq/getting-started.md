---
title: začínáme
description: Pomocí tohoto ukázkového LINQ to SQL kódu můžete začít používat technologii LINQ pro přístup k databázím SQL stejně, jako byste měli přístup ke kolekci v paměti.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: a46c42e917bdab0d32ee594bbcd604ee9e3d26bc
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286414"
---
# <a name="getting-started"></a>začínáme
Pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] můžete technologii LINQ použít pro přístup k databázím SQL stejně, jako byste měli přístup ke kolekci v paměti.  
  
 Například `nw` objekt v následujícím kódu je vytvořen pro reprezentaci `Northwind` databáze, na `Customers` cílovou tabulku, řádky jsou filtrovány `Customers` z `London` a `CompanyName` je vybrán řetězec pro načtení.  
  
 Po spuštění smyčky se `CompanyName` načte kolekce hodnot.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a>Další kroky  
 Další příklady, včetně vkládání a aktualizace, najdete v tématu [co můžete s LINQ to SQL](what-you-can-do-with-linq-to-sql.md).  
  
 Dále vyzkoušejte některé návody a kurzy, které vám pomají praktické zkušenosti s používáním [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Přečtěte si [návody v tématu učení](learning-by-walkthroughs.md).  
  
 Nakonec se naučíte, jak začít pracovat na vlastním [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu načtením [typických kroků pro použití LINQ to SQL](typical-steps-for-using-linq-to-sql.md).  
  
## <a name="see-also"></a>Viz také

- [Technologie LINQ to SQL](index.md)
- [Úvod do jazyka LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [Úvod do LINQ (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [Objektový model LINQ to SQL](the-linq-to-sql-object-model.md)
