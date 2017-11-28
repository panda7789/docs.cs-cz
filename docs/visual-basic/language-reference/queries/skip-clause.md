---
title: "Skip – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 508f3c094df4c834305bcb4a78223c1cee82b1c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Select – klauzule](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From – klauzule](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Order By – klauzule](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Skip While – klauzule](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Take – klauzule](../../../visual-basic/language-reference/queries/take-clause.md)
