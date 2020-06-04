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
ms.openlocfilehash: b357320a92ace1b7a261991737ed653d54d0eeab
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359642"
---
# <a name="skip-while-clause-visual-basic"></a>Skip While – klauzule (Visual Basic)
Vynechá prvky v kolekci, pokud je zadaná podmínka `true` a vrátí zbývající prvky.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a>Součásti  
  
|Pojem|Definice|  
|---|---|  
|`expression`|Povinná hodnota. Výraz, který představuje podmínku pro testování prvků pro. Výraz musí vracet `Boolean` hodnotu nebo funkční ekvivalent, jako je například, aby se `Integer` vyhodnotil jako `Boolean` .|  
  
## <a name="remarks"></a>Poznámky  
 `Skip While`Klauzule vynechává prvky od začátku výsledku dotazu, dokud se nevrátí zadané výsledky `expression` `false` . Po `expression` návratu `false` dotaz vrátí všechny zbývající prvky. U `expression` zbývajících výsledků se ignoruje.  
  
 `Skip While`Klauzule se liší od `Where` klauzule v tom, že `Where` klauzuli lze použít k vyloučení všech prvků z dotazu, který nesplňuje určitou podmínku. `Skip While`Klauzule vyloučí prvky pouze do prvního okamžiku, kdy podmínka není splněna. `Skip While`Klauzule je nejužitečnější, když pracujete s výsledkem seřazeného dotazu.  
  
 Můžete obejít určitý počet výsledků od začátku výsledku dotazu pomocí `Skip` klauzule.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá `Skip While` klauzuli pro obejití výsledků, dokud se nenajde první zákazník z USA.  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a>Viz také

- [Představení technologie LINQ v jazyce Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](index.md)
- [Klauzule SELECT](select-clause.md)
- [Klauzule FROM](from-clause.md)
- [Skip – klauzule](skip-clause.md)
- [Take While – klauzule](take-while-clause.md)
- [Klauzule WHERE](where-clause.md)
