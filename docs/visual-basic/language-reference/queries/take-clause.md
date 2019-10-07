---
title: Take – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 32a4c7fd7f1e2f6fe640f3f53f15579f014759d5
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004712"
---
# <a name="take-clause-visual-basic"></a>Take – klauzule (Visual Basic)
Vrátí zadaný počet souvislých prvků od začátku kolekce.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Take count  
```  
  
## <a name="parts"></a>Součásti  
 `count`  
 Požadováno. Hodnota nebo výraz, který se vyhodnotí na počet prvků sekvence, která se má vrátit.  
  
## <a name="remarks"></a>Poznámky  
 Klauzule `Take` způsobí, že dotaz zahrne do začátku seznamu výsledků určitý počet souvislých prvků. Počet prvků, které mají být zahrnuty, je určen parametrem `count`.  
  
 Klauzuli `Take` s klauzulí `Skip` můžete použít k vrácení rozsahu dat z libovolného segmentu dotazu. Provedete to tak, že předáte index prvního prvku rozsahu na klauzuli `Skip` a velikost rozsahu na klauzuli `Take`. V takovém případě musí být klauzule `Take` zadána za klauzulí `Skip`.  
  
 Použijete-li v dotazu klauzuli `Take`, může být také nutné zajistit, aby výsledky byly vráceny v pořadí, které umožní, aby klauzule `Take` zahrnovala zamýšlené výsledky. Další informace o řazení výsledků dotazu naleznete v tématu [ORDER by klauzule](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Pomocí klauzule `TakeWhile` můžete určit, že se v závislosti na zadané podmínce mají vracet jenom určité prvky.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá klauzuli `Take` spolu s klauzulí `Skip` pro vrácení dat z dotazu na stránkách. Funkce GetCustomers používá klauzuli `Skip` pro obejít zákazníky v seznamu až do zadané hodnoty počátečního indexu a pomocí klauzule `Take` vrátit stránku zákazníků počínaje touto hodnotou indexu.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Úvod do jazyka LINQ v Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Klauzule Take While](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Klauzule Skip](../../../visual-basic/language-reference/queries/skip-clause.md)
