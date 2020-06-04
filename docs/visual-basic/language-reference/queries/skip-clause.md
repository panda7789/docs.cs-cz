---
title: Skip – klauzule
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: 427d14453260a54bd3f2ab9a8ac75dedacd291f4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359655"
---
# <a name="skip-clause-visual-basic"></a>Skip – klauzule (Visual Basic)
Obchází zadaný počet prvků v kolekci a vrátí zbývající prvky.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a>Součásti  
 `count`  
 Povinná hodnota. Hodnota nebo výraz, který se vyhodnotí na počet prvků sekvence, která se má přeskočit.  
  
## <a name="remarks"></a>Poznámky  
 `Skip`Klauzule způsobí, že dotaz obchází prvky na začátku seznamu výsledků a vrátí zbývající prvky. Počet elementů, které mají být přeskočeny, je identifikován `count` parametrem.  
  
 `Skip`Klauzuli s klauzulí můžete použít `Take` k vrácení rozsahu dat z libovolného segmentu dotazu. Provedete to tak, že předáte index prvního prvku rozsahu k `Skip` klauzuli a velikost rozsahu na `Take` klauzuli.  
  
 Při použití `Skip` klauzule v dotazu může být také nutné zajistit, aby výsledky byly vráceny v pořadí, které umožní `Skip` klauzuli pro obejít zamýšlené výsledky. Další informace o řazení výsledků dotazu naleznete v tématu [ORDER by klauzule](order-by-clause.md).  
  
 Pomocí `SkipWhile` klauzule můžete určit, že se v závislosti na zadané podmínce mají ignorovat jenom určité prvky.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá `Skip` klauzuli spolu s `Take` klauzulí k vrácení dat z dotazu na stránkách. `GetCustomers`Funkce používá `Skip` klauzuli pro obejít zákazníky v seznamu až do zadané hodnoty počátečního indexu a pomocí `Take` klauzule vrátí stránku zákazníků počínaje touto hodnotou indexu.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [Představení technologie LINQ v jazyce Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](index.md)
- [Klauzule SELECT](select-clause.md)
- [Klauzule FROM](from-clause.md)
- [Order By – klauzule](order-by-clause.md)
- [Skip While – klauzule](skip-while-clause.md)
- [Take – klauzule](take-clause.md)
