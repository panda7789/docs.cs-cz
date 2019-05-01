---
title: Proměnná rozsahu <variable> skrývá proměnnou v nadřazeném bloku, dříve definovanou proměnnou rozsahu nebo implicitně deklarovanou proměnnou ve výrazu dotazu.
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: e31f728de228bea743f6c7b5cbfef3cd73367262
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971625"
---
# <a name="range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a>Proměnná rozsahu \<proměnná > skrývá proměnnou v nadřízeném bloku, dříve definovanou proměnnou rozsahu nebo implicitně deklarovanou proměnnou ve výrazu dotazu
Název proměnné rozsahu podle `Select`, `From`, `Aggregate`, nebo `Let` klauzule duplikuje název proměnné rozsahu již dříve zadaný v dotazu, nebo název proměnné, která je implicitně deklarován podle dotazu třeba na název pole nebo název agregační funkci.  
  
 **ID chyby:** BC36633  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Ujistěte se, že všechny proměnné rozsahu v oboru speciální dotaz mít jedinečné názvy. Dotaz můžete uvést v závorkách k zajištění, že vnořené dotazy obsahovat jedinečný obor.  
  
## <a name="see-also"></a>Viz také:

- [Úvod do LINQ v JAZYKU Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Let](../../../visual-basic/language-reference/queries/let-clause.md)
- [Klauzule Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
