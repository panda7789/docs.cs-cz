---
title: Take While – klauzule
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 23b7c84a9f896161a66059fcb1f30753d3b863d5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347102"
---
# <a name="take-while-clause-visual-basic"></a>Take While – klauzule (Visual Basic)
Obsahuje prvky v kolekci, pokud je zadaná podmínka `true` a obchází zbývající prvky.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`expression`|Požadováno. Výraz, který představuje podmínku pro testování prvků pro. Výraz musí vracet `Boolean` hodnotu nebo funkční ekvivalent, jako je například `Integer` pro vyhodnocení jako `Boolean`.|  
  
## <a name="remarks"></a>Poznámky  
 Klauzule `Take While` obsahuje prvky z začátek výsledku dotazu, dokud zadaný `expression` nevrátí `false`. Po `expression` vrátí `false`, dotaz vynechá všechny zbývající prvky. `expression` se u zbývajících výsledků ignoruje.  
  
 Klauzule `Take While` se liší od klauzule `Where` v tom, že klauzuli `Where` lze použít k zahrnutí všech prvků z dotazu, který splňuje určitou podmínku. Klauzule `Take While` obsahuje prvky pouze do doby, než první podmínka není splněna. Klauzule `Take While` je nejužitečnější, když pracujete s výsledkem seřazeného dotazu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá klauzuli `Take While` k načtení výsledků, dokud se nenajde první zákazník bez jakýchkoli objednávek.  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Úvod do jazyka LINQ v Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Take](../../../visual-basic/language-reference/queries/take-clause.md)
- [Klauzule Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
