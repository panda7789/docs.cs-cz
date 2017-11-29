---
title: "Proměnná rozsahu &lt;proměnná&gt; skrývá proměnnou z vnějšího bloku, dříve definovaném rozsahu proměnná nebo proměnná implicitně deklarované ve výrazu dotazu"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords: BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ccbac48694a13daa09f2511cf39d5dbd51cdaaf7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="range-variable-ltvariablegt-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a>Proměnná rozsahu &lt;proměnná&gt; skrývá proměnnou z vnějšího bloku, dříve definovaném rozsahu proměnná nebo proměnná implicitně deklarované ve výrazu dotazu
Název proměnné rozsahu zadaný v `Select`, `From`, `Aggregate`, nebo `Let` klauzule duplikuje název proměnné rozsahu již dříve zadaný v dotazu nebo název proměnné, která je implicitně deklarován v dotazu jako název pole nebo název agregační funkci.  
  
 **ID chyby:** BC36633  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zajistěte, aby všechny proměnné rozsahu v oboru konkrétní dotazu jedinečné názvy. Dotaz můžete uveďte v závorkách, vnořené dotazy získali jedinečný obor.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do LINQ v jazyku Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [From – klauzule](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Let – klauzule](../../../visual-basic/language-reference/queries/let-clause.md)  
 [AGGREGATE – klauzule](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Select – klauzule](../../../visual-basic/language-reference/queries/select-clause.md)
