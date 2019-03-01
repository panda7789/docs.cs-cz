---
title: Skip – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: 8441e619cdbd18545be72fd701c2cc9b1cf495d9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971234"
---
# <a name="skip-clause-visual-basic"></a>Skip – klauzule (Visual Basic)
Vynechá zadaný počet prvků v kolekci a vrátí zbývající prvky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Skip count  
```  
  
## <a name="parts"></a>Součásti  
 `count`  
 Povinný parametr. Hodnota nebo výraz, který se vyhodnotí jako počet elementů pořadí přeskočit.  
  
## <a name="remarks"></a>Poznámky  
 `Skip` Klauzule způsobí, že dotaz obejít prvky na začátek seznamu výsledků a vrátí zbývající prvky. Počet prvků, které mají přeskočit je identifikován `count` parametru.  
  
 Můžete použít `Skip` klauzule `Take` klauzule, která vrátí celou řadu dat z libovolnou část dotazu. K tomuto účelu předat index prvního prvku rozsahu, který chcete `Skip` klauzule a velikost rozsahu `Take` klauzuli.  
  
 Při použití `Skip` klauzule v dotazu, budete také muset zajistit, že výsledky jsou vráceny v pořadí, které vám umožní `Skip` klauzule obejít požadovaných výsledků. Další informace o řazení výsledků dotazu, naleznete v tématu [klauzuli ORDER by](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Můžete použít `SkipWhile` klauzule k určení, že pouze některé prvky jsou ignorovány, v závislosti na zadaných podmínek.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá `Skip` klauzule spolu s `Take` klauzule vrátit data z dotazu na stránkách. `GetCustomers` Funkce používá `Skip` klauzule obejít zákazníky v seznamu, dokud se zadaný počáteční index, hodnotu a použití `Take` klauzuli pro vrácení stránky s zákazníků od hodnotě indexu.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Viz také:
- [Úvod do LINQ v JAZYKU Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Klauzule Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Klauzule Take](../../../visual-basic/language-reference/queries/take-clause.md)
