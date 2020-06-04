---
title: Take – klauzule
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 25dd06905525a96bc1504f033eb4f19af6d454a2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359629"
---
# <a name="take-clause-visual-basic"></a>Take – klauzule (Visual Basic)
Vrátí zadaný počet souvislých prvků od začátku kolekce.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Take count  
```  
  
## <a name="parts"></a>Součásti  
 `count`  
 Povinná hodnota. Hodnota nebo výraz, který se vyhodnotí na počet prvků sekvence, která se má vrátit.  
  
## <a name="remarks"></a>Poznámky  
 `Take`Klauzule způsobí, že dotaz zahrne zadaný počet souvislých prvků od začátku seznamu výsledků. Počet prvků, které mají být zahrnuty, je určen `count` parametrem.  
  
 `Take`Klauzuli s klauzulí můžete použít `Skip` k vrácení rozsahu dat z libovolného segmentu dotazu. Provedete to tak, že předáte index prvního prvku rozsahu k `Skip` klauzuli a velikost rozsahu na `Take` klauzuli. V takovém případě `Take` musí být klauzule uvedena za `Skip` klauzulí.  
  
 Použijete-li `Take` klauzuli v dotazu, může být také nutné zajistit, aby výsledky byly vráceny v pořadí, které umožní `Take` klauzuli zahrnout zamýšlené výsledky. Další informace o řazení výsledků dotazu naleznete v tématu [ORDER by klauzule](order-by-clause.md).  
  
 Pomocí `TakeWhile` klauzule můžete určit, že se v závislosti na zadané podmínce mají vracet jenom určité prvky.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá `Take` klauzuli spolu s `Skip` klauzulí k vrácení dat z dotazu na stránkách. Funkce GetCustomers používá `Skip` klauzuli pro obejít zákazníky v seznamu až do zadané hodnoty počátečního indexu a pomocí `Take` klauzule vrátí stránku zákazníků počínaje touto hodnotou indexu.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [Představení technologie LINQ v jazyce Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](index.md)
- [Klauzule SELECT](select-clause.md)
- [Klauzule FROM](from-clause.md)
- [Order By – klauzule](order-by-clause.md)
- [Take While – klauzule](take-while-clause.md)
- [Skip – klauzule](skip-clause.md)
