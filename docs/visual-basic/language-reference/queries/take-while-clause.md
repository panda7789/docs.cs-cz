---
title: "Take While – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5c8add6c55bb9353bac3489e68f497cb32785aad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="take-while-clause-visual-basic"></a>Take While – klauzule (Visual Basic)
Obsahuje prvky v kolekci, pokud je zadaná podmínka `true` a obchází zbývající elementy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Take While expression  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`expression`|Požadováno. Výraz, který představuje podmínku, kterou chcete testovat prvky pro. Výraz musí vrátit `Boolean` hodnotu nebo funkční ekvivalent, například `Integer` má být vyhodnocen jako `Boolean`.|  
  
## <a name="remarks"></a>Poznámky  
 `Take While` Klauzule obsahuje prvky od začátku výsledku dotazu až do zadaných `expression` vrátí `false`. Po `expression` vrátí `false`, dotaz se nepoužívat všechny zbývající elementy. `expression` Pro zbývající výsledky se ignoruje.  
  
 `Take While` Klauzule se liší od `Where` klauzule v tom, že `Where` klauzule lze zahrnout všechny elementy z dotazu, které splňují určitá podmínka. `Take While` Klauzule obsahuje prvky pouze dokud poprvé, která není splněna podmínka. `Take While` Klauzule je nejvhodnější pro práci se výsledek seřazené dotazu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá `Take While` klauzule a načtěte výsledky, dokud nebude nalezen první zákazníků bez jakékoli objednávky.  
  
 [!code-vb[VbSimpleQuerySamples#2](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-while-clause_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Úvod do LINQ v jazyku Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Dotazy](../../../visual-basic/language-reference/queries/queries.md)  
 [Select – klauzule](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From – klauzule](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Take – klauzule](../../../visual-basic/language-reference/queries/take-clause.md)  
 [Skip While – klauzule](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Kde – klauzule](../../../visual-basic/language-reference/queries/where-clause.md)
