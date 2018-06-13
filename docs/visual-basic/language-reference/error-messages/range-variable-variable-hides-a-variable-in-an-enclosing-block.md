---
title: Proměnná rozsahu &lt;proměnná&gt; skrývá proměnnou z vnějšího bloku, dříve definovaném rozsahu proměnná nebo proměnná implicitně deklarované ve výrazu dotazu
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: f02533cf7cb79c34e5bb5a6d445aaef7ab0e86da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593123"
---
# <a name="range-variable-ltvariablegt-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a>Proměnná rozsahu &lt;proměnná&gt; skrývá proměnnou z vnějšího bloku, dříve definovaném rozsahu proměnná nebo proměnná implicitně deklarované ve výrazu dotazu
Název proměnné rozsahu zadaný v `Select`, `From`, `Aggregate`, nebo `Let` klauzule duplikuje název proměnné rozsahu již dříve zadaný v dotazu nebo název proměnné, která je implicitně deklarován v dotazu jako název pole nebo název agregační funkci.  
  
 **ID chyby:** BC36633  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zajistěte, aby všechny proměnné rozsahu v oboru konkrétní dotazu jedinečné názvy. Dotaz můžete uveďte v závorkách, vnořené dotazy získali jedinečný obor.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do LINQ v jazyku Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Klauzule Let](../../../visual-basic/language-reference/queries/let-clause.md)  
 [Klauzule Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
