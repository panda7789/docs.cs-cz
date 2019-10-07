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
ms.openlocfilehash: fe6ee470698504bc0434930cc9aa6de712e04254
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004671"
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
|`expression`|Požadováno. Výraz, který představuje podmínku pro testování prvků pro. Výraz musí vracet hodnotu `Boolean` nebo funkční ekvivalent, jako je například `Integer` pro vyhodnocení jako `Boolean`.|  
  
## <a name="remarks"></a>Poznámky  
 Klauzule `Take While` obsahuje prvky od začátku výsledku dotazu, dokud zadaná `expression` nevrátí `false`. Po `expression` vrátí `false`, dotaz vynechá všechny zbývající prvky. @No__t-0 se u zbývajících výsledků ignoruje.  
  
 Klauzule `Take While` se liší od klauzule `Where` v tom, že klauzuli `Where` lze použít k zahrnutí všech prvků z dotazu, který splňuje určitou podmínku. Klauzule `Take While` obsahuje prvky pouze do doby, než první podmínka není splněna. Klauzule `Take While` je nejužitečnější, když pracujete s výsledkem seřazeného dotazu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá klauzuli `Take While` pro načtení výsledků, dokud se nenajde první zákazník bez jakýchkoli objednávek.  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Úvod do jazyka LINQ v Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Take](../../../visual-basic/language-reference/queries/take-clause.md)
- [Klauzule Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
