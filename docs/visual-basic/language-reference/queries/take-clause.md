---
title: Take – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 0dddb411af1b4ee269e091c07553a94589d90b2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="take-clause-visual-basic"></a>Take – klauzule (Visual Basic)
Vrátí zadaný počet souvislý elementů od začátku kolekce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Take count  
```  
  
## <a name="parts"></a>Součásti  
 `count`  
 Požadováno. Hodnota nebo výraz, který se vyhodnotí jako počet elementů pořadí vrátit.  
  
## <a name="remarks"></a>Poznámky  
 `Take` Klauzule způsobí, že dotaz, který patří zadaný počet elementů souvislý od začátku seznamu výsledků. Počet elementů zahrnout je zadána `count` parametr.  
  
 Můžete použít `Take` klauzuli with `Skip` klauzule vrátit celou řadu dat ze žádného segmentu dotazu. K tomuto účelu předat index první prvek rozsahu `Skip` klauzule a velikost rozsahu `Take` klauzule. V takovém případě `Take` klauzule musí být zadán za `Skip` klauzule.  
  
 Při použití `Take` klauzuli v dotazu, může také musíte zajistit, že jsou vráceny v pořadí, které vám umožní `Take` klauzule zahrnout požadovaných výsledků. Další informace o řazení výsledků dotazu, najdete v části [klauzuli ORDER by](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Můžete použít `TakeWhile` klauzule k určení, že se vrátí jenom některé prvky, v závislosti na podmínce zadaný.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá `Take` klauzule společně s `Skip` klauzule vrátit data z dotazu na stránkách. GetCustomers funkce používá `Skip` klauzule obejít zákazníků v seznamu, dokud zadaný počáteční index hodnota a používá `Take` klauzule vrátit na stránce zákazníků od tuto hodnotu indexu.  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-clause_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Úvod do LINQ v jazyku Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Dotazy](../../../visual-basic/language-reference/queries/queries.md)  
 [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Klauzule Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Klauzule Take While](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [Klauzule Skip](../../../visual-basic/language-reference/queries/skip-clause.md)
