---
title: Take While – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 7e0a6bd77ca2594e9d74e669fcd9cddf91ee1cad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33600897"
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
 [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Klauzule Take](../../../visual-basic/language-reference/queries/take-clause.md)  
 [Klauzule Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
