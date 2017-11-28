---
title: "Take – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ee289a24c15226126a526af116ed53b4a9055b35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Select – klauzule](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From – klauzule](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Order By – klauzule](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Take While – klauzule](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [Skip – klauzule](../../../visual-basic/language-reference/queries/skip-clause.md)
