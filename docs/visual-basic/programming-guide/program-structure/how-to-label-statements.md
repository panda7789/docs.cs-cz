---
title: 'Postupy: Vytváření popisků příkazů (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: df368bdba73ca35dd70bdd2f4e88cc10af894b5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-label-statements-visual-basic"></a>Postupy: Vytváření popisků příkazů (Visual Basic)
Blok příkazu jsou tvořeny řádků kódu oddělené dvojtečkou. Řádky kódu před sebou identifikační řetězec nebo celé číslo, které jsou označeny jako *s názvem bez přípony*. Příkaz popisky slouží k označení řádku kódu pro jeho rozpoznání pro použití s příkazy, jako `On Error Goto`.  
  
 Popisky může být buď platné identifikátory jazyka Visual Basic – jako jsou ty, které identifikují elementům programování – nebo literály celé číslo. Štítek musí být uvedena na začátku řádku zdrojového kódu a musí být následovaným dvojtečkou, bez ohledu na to, jestli je následovaný příkazem na stejném řádku.  
  
 Kompilátor rozpoznává popisky tak, že zkontrolujete, jestli začátek řádku odpovídá žádný identifikátor již definována. Pokud ne, kompilátor předpokládá, že je štítek.  
  
 Popisky vlastní deklarace místa a nebudou v konfliktu s další identifikátory. Rozsah popisku je těla metody. Popisek deklarace má přednost před v jakékoliv jiné situaci s nejednoznačný.  
  
> [!NOTE]
>  Popisky lze použít pouze v spustitelné příkazy uvnitř metody.  
  
### <a name="to-label-a-line-of-code"></a>Pro označení řádku kódu  
  
-   Umístěte identifikátorem následovaným dvojtečkou, na začátku řádku zdrojového kódu.  
  
     Například následující řádky kódu jsou označeny `Jump` a `120`, v uvedeném pořadí:  
  
     [!code-vb[VbVbalrStatements#708](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/how-to-label-statements_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Struktura programu a zásady týkající se kódu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
