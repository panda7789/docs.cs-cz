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
ms.openlocfilehash: 7f37a6fa1c9ba7fdf7978ac6853e4c2985bf72e7
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004709"
---
# <a name="skip-while-clause-visual-basic"></a>Skip While – klauzule (Visual Basic)
Vynechá prvky v kolekci, pokud je zadaná podmínka `true` a potom vrátí zbývající prvky.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`expression`|Požadováno. Výraz, který představuje podmínku pro testování prvků pro. Výraz musí vracet hodnotu `Boolean` nebo funkční ekvivalent, jako je například `Integer` pro vyhodnocení jako `Boolean`.|  
  
## <a name="remarks"></a>Poznámky  
 Klauzule `Skip While` obchází prvky od začátku výsledku dotazu, dokud zadaná `expression` nevrátí hodnotu `false`. Po `expression` vrátí `false`, dotaz vrátí všechny zbývající prvky. @No__t-0 se u zbývajících výsledků ignoruje.  
  
 Klauzule `Skip While` se liší od klauzule `Where` v tom, že klauzuli `Where` lze použít k vyloučení všech prvků z dotazu, který nesplňuje určitou podmínku. Klauzule `Skip While` vyloučí prvky pouze do prvního okamžiku, kdy podmínka není splněna. Klauzule `Skip While` je nejužitečnější, když pracujete s výsledkem seřazeného dotazu.  
  
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
