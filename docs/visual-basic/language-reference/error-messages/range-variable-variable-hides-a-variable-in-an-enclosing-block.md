---
title: Proměnná rozsahu <variable> skrývá proměnnou v nadřazeném bloku, dříve definovanou proměnnou rozsahu nebo implicitně deklarovanou proměnnou ve výrazu dotazu.
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: 290ca81dea500558ed73956c91bdf7bfec312014
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400393"
---
# <a name="range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a>Proměnná rozsahu \<variable> skrývá proměnnou v nadřazeném bloku, dříve definovanou proměnnou rozsahu nebo implicitně deklarovanou proměnnou ve výrazu dotazu.
Název proměnné rozsahu zadaný v `Select` `From` klauzuli,, `Aggregate` nebo `Let` je duplicitní s názvem proměnné rozsahu, která je již v dotazu zadána dříve, nebo názvem proměnné, která je implicitně deklarována dotazem, jako je název pole nebo název agregační funkce.  
  
 **ID chyby:** BC36633  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Ujistěte se, že všechny proměnné rozsahu v konkrétním oboru dotazu mají jedinečné názvy. Dotaz můžete uzavřít do závorek, abyste zajistili, že vnořené dotazy mají jedinečný obor.  
  
## <a name="see-also"></a>Viz také

- [Představení technologie LINQ v jazyce Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Klauzule FROM](../queries/from-clause.md)
- [Let – klauzule](../queries/let-clause.md)
- [Aggregate – klauzule](../queries/aggregate-clause.md)
- [Klauzule SELECT](../queries/select-clause.md)
