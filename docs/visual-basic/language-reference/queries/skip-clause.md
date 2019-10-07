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
ms.openlocfilehash: e52de186e1475bfabd02821a0cd2384d8350eed3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004764"
---
# <a name="skip-clause-visual-basic"></a>Skip – klauzule (Visual Basic)
Obchází zadaný počet prvků v kolekci a vrátí zbývající prvky.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a>Součásti  
 `count`  
 Požadováno. Hodnota nebo výraz, který se vyhodnotí na počet prvků sekvence, která se má přeskočit.  
  
## <a name="remarks"></a>Poznámky  
 Klauzule `Skip` způsobí, že dotaz obchází prvky na začátku seznamu výsledků a vrátí zbývající prvky. Počet elementů, které mají být přeskočeny, je identifikován parametrem `count`.  
  
 Klauzuli `Skip` s klauzulí `Take` můžete použít k vrácení rozsahu dat z libovolného segmentu dotazu. Provedete to tak, že předáte index prvního prvku rozsahu na klauzuli `Skip` a velikost rozsahu na klauzuli `Take`.  
  
 Použijete-li v dotazu klauzuli `Skip`, může být také nutné zajistit, aby výsledky byly vráceny v pořadí, které umožní, aby klauzule `Skip` využívala zamýšlené výsledky. Další informace o řazení výsledků dotazu naleznete v tématu [ORDER by klauzule](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Pomocí klauzule `SkipWhile` můžete určit, že se v závislosti na zadané podmínce ignorují jenom určité prvky.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá klauzuli `Skip` spolu s klauzulí `Take` pro vrácení dat z dotazu na stránkách. Funkce `GetCustomers` používá klauzuli `Skip` pro obejít zákazníky v seznamu do zadané hodnoty počátečního indexu a pomocí klauzule `Take` vrátí stránku zákazníků počínaje touto hodnotou indexu.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Úvod do jazyka LINQ v Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Klauzule Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Klauzule Take](../../../visual-basic/language-reference/queries/take-clause.md)
