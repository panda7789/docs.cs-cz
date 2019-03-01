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
ms.openlocfilehash: 2705b61f4ebc839a9db98f037f303b4df78bbe5f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976210"
---
# <a name="take-clause-visual-basic"></a>Take – klauzule (Visual Basic)
Vrátí zadaný počet souvislých prvků od začátku kolekce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Take count  
```  
  
## <a name="parts"></a>Součásti  
 `count`  
 Povinný parametr. Hodnota nebo výraz, který se vyhodnotí jako počet elementů k vrácení sekvence.  
  
## <a name="remarks"></a>Poznámky  
 `Take` Klauzule způsobí, že dotaz pro přidání zadaný počet souvislých prvků od začátku seznamu výsledků. Je určený počet prvků, které chcete zahrnout `count` parametru.  
  
 Můžete použít `Take` klauzule `Skip` klauzule, která vrátí celou řadu dat z libovolnou část dotazu. K tomuto účelu předat index prvního prvku rozsahu, který chcete `Skip` klauzule a velikost rozsahu `Take` klauzuli. V takovém případě `Take` klauzule musí být zadán za `Skip` klauzuli.  
  
 Při použití `Take` klauzule v dotazu, budete také muset zajistit, že výsledky jsou vráceny v pořadí, které vám umožní `Take` klauzule, která zahrnují požadovaných výsledků. Další informace o řazení výsledků dotazu, naleznete v tématu [klauzuli ORDER by](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Můžete použít `TakeWhile` klauzule k určení, že se vrátí jenom některé prvky, v závislosti na zadaných podmínek.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá `Take` klauzule spolu s `Skip` klauzule vrátit data z dotazu na stránkách. GetCustomers funkce používá `Skip` klauzule obejít zákazníky v seznamu, dokud se zadaný počáteční index, hodnotu a použití `Take` klauzuli pro vrácení stránky s zákazníků od hodnotě indexu.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Viz také:
- [Úvod do LINQ v JAZYKU Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Klauzule Take While](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Klauzule Skip](../../../visual-basic/language-reference/queries/skip-clause.md)
