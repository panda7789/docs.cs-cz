---
title: Skip While – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 9d95dc4a9f61a9ec3a50f9d594b31d673c2d3764
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="skip-while-clause-visual-basic"></a>Skip While – klauzule (Visual Basic)
Obchází elementů v kolekci, pokud je zadaná podmínka `true` a vrátí zbývající elementy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`expression`|Požadováno. Výraz, který představuje podmínku, kterou chcete testovat prvky pro. Výraz musí vrátit `Boolean` hodnotu nebo funkční ekvivalent, například `Integer` má být vyhodnocen jako `Boolean`.|  
  
## <a name="remarks"></a>Poznámky  
 `Skip While` Klauzule obchází elementy od začátku až do zadaných výsledků dotazu `expression` vrátí `false`. Po `expression` vrátí `false`, dotaz vrátí všechny zbývající elementy. `expression` Pro zbývající výsledky se ignoruje.  
  
 `Skip While` Klauzule se liší od `Where` klauzule v tom, že `Where` klauzuli lze použít k vyloučení všechny elementy z dotazu, které nesplňují určité podmínky. `Skip While` Klauzule vyloučí elementy pouze dokud poprvé, která není splněna podmínka. `Skip While` Klauzule je nejvhodnější pro práci se výsledek seřazené dotazu.  
  
 Můžete obejít konkrétní počet výsledků od začátku výsledků dotazu pomocí `Skip` klauzule.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá `Skip While` klauzule obejít výsledky, dokud nebude nalezen první zákazník z USA.  
  
 [!code-vb[VbSimpleQuerySamples#3](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-while-clause_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Úvod do LINQ v jazyku Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Dotazy](../../../visual-basic/language-reference/queries/queries.md)  
 [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Klauzule Skip](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Klauzule Take While](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
