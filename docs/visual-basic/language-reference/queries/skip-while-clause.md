---
title: Skip While – klauzule
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 47703e445865435f5bf5312c3fe41833ac21aa3f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333142"
---
# <a name="skip-while-clause-visual-basic"></a>Skip While – klauzule (Visual Basic)
Vynechá prvky v kolekci, pokud je zadaná podmínka `true` a vrátí zbývající prvky.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`expression`|Požadováno. Výraz, který představuje podmínku pro testování prvků pro. Výraz musí vracet `Boolean` hodnotu nebo funkční ekvivalent, jako je například `Integer` pro vyhodnocení jako `Boolean`.|  
  
## <a name="remarks"></a>Poznámky  
 Klauzule `Skip While` obchází prvky od začátku výsledku dotazu, dokud zadaný `expression` nevrátí `false`. Po `expression` vrátí `false`, dotaz vrátí všechny zbývající prvky. `expression` se u zbývajících výsledků ignoruje.  
  
 Klauzule `Skip While` se liší od klauzule `Where` v tom, že klauzuli `Where` lze použít k vyloučení všech prvků z dotazu, který nesplňuje určitou podmínku. Klauzule `Skip While` vyloučí prvky pouze do doby, než první podmínka není splněna. Klauzule `Skip While` je nejužitečnější, když pracujete s výsledkem seřazeného dotazu.  
  
 Můžete obejít určitý počet výsledků od začátku výsledku dotazu pomocí klauzule `Skip`.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá klauzuli `Skip While` pro obejití výsledků, dokud se nenajde první zákazník z USA.  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Úvod do jazyka LINQ v Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Skip](../../../visual-basic/language-reference/queries/skip-clause.md)
- [Klauzule Take While](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
