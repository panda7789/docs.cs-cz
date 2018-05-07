---
title: Skip – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: 1810bf4a6573c6fa36f1d8149bf341d45cfd6f52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="skip-clause-visual-basic"></a>Skip – klauzule (Visual Basic)
Obchází zadaný počet elementů v kolekci a pak vrátí zbývající elementy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Skip count  
```  
  
## <a name="parts"></a>Součásti  
 `count`  
 Požadováno. Hodnota nebo výraz, který se vyhodnotí jako počet elementů pořadí tak, aby přeskočil.  
  
## <a name="remarks"></a>Poznámky  
 `Skip` Klauzule způsobí, že dotaz vynechat elementy na začátku seznamu výsledků a vrátíte se zbývající elementy. Počet elementů tak, aby přeskočil je identifikována `count` parametr.  
  
 Můžete použít `Skip` klauzuli with `Take` klauzule vrátit celou řadu dat ze žádného segmentu dotazu. K tomuto účelu předat index první prvek rozsahu `Skip` klauzule a velikost rozsahu `Take` klauzule.  
  
 Při použití `Skip` klauzuli v dotazu, může také musíte zajistit, že jsou vráceny v pořadí, které vám umožní `Skip` klauzule obejít požadovaných výsledků. Další informace o řazení výsledků dotazu, najdete v části [klauzuli ORDER by](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Můžete použít `SkipWhile` klauzule k určení, že pouze některé prvky jsou ignorovány, v závislosti na podmínce zadaný.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá `Skip` klauzule společně s `Take` klauzule vrátit data z dotazu na stránkách. `GetCustomers` Využívá `Skip` klauzule obejít zákazníků v seznamu, dokud zadaný počáteční index hodnota a používá `Take` klauzule vrátit na stránce zákazníků od tuto hodnotu indexu.  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-clause_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Úvod do LINQ v jazyku Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Dotazy](../../../visual-basic/language-reference/queries/queries.md)  
 [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Klauzule Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Klauzule Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Klauzule Take](../../../visual-basic/language-reference/queries/take-clause.md)
