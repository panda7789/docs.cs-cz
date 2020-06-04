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
ms.openlocfilehash: 4b6133efdbd9c46ab85201ad454671e5538b6a81
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359577"
---
# <a name="take-while-clause-visual-basic"></a>Take While – klauzule (Visual Basic)
Obsahuje prvky v kolekci, pokud je zadaná podmínka `true` a obchází zbývající prvky.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a>Součásti  
  
|Pojem|Definice|  
|---|---|  
|`expression`|Povinná hodnota. Výraz, který představuje podmínku pro testování prvků pro. Výraz musí vracet `Boolean` hodnotu nebo funkční ekvivalent, jako je například, aby se `Integer` vyhodnotil jako `Boolean` .|  
  
## <a name="remarks"></a>Poznámky  
 `Take While`Klauzule obsahuje prvky z začátek výsledku dotazu, dokud se nevrátí dodaný `expression` výsledek `false` . Po `expression` vrácení `false` bude dotaz obejít všechny zbývající prvky. U `expression` zbývajících výsledků se ignoruje.  
  
 `Take While`Klauzule se liší od `Where` klauzule v tom, že `Where` klauzuli lze použít k zahrnutí všech prvků z dotazu, který splňuje určitou podmínku. `Take While`Klauzule obsahuje prvky pouze do doby, než první podmínka není splněna. `Take While`Klauzule je nejužitečnější, když pracujete s výsledkem seřazeného dotazu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá `Take While` klauzuli pro načtení výsledků, dokud se nenajde první zákazník bez jakýchkoli objednávek.  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a>Viz také

- [Představení technologie LINQ v jazyce Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](index.md)
- [Klauzule SELECT](select-clause.md)
- [Klauzule FROM](from-clause.md)
- [Take – klauzule](take-clause.md)
- [Skip While – klauzule](skip-while-clause.md)
- [Klauzule WHERE](where-clause.md)
