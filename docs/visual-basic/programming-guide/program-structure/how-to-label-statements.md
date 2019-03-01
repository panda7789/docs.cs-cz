---
title: 'Postupy: Popisek příkazy (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: 2f6f0362fcec170e677d153ad9f936a5c2e55ad7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981202"
---
# <a name="how-to-label-statements-visual-basic"></a>Postupy: Popisek příkazy (Visual Basic)
Blok příkazu jsou tvořené řádků kódu, které jsou odděleny dvojtečkami. Řádky kódu předchází identifikační řetězec nebo celé číslo se označují jako *označené*. Popisky příkazů se používá k označení řádku kódu k jeho identifikaci při použití s příkazy, jako `On Error Goto`.  
  
 Popisky mohou být buď platné identifikátory jazyka Visual Basic, jako jsou ty, které identifikují programovací prvky, nebo literály celých čísel. Popisek musí být na začátku řádku zdrojového kódu a musí být následován dvojtečkou, bez ohledu na to, zda je následovaný příkazem na stejném řádku.  
  
 Kompilátor identifikuje popisky tak, že zkontrolujete, jestli odpovídá začátku řádku žádný identifikátor již definována. Pokud tomu tak není, kompilátor předpokládá, že je popisek.  
  
 Popisky své vlastní prohlášení místa a nejsou v konfliktu s další identifikátory. Obor popisku je tělo metody. Deklarace popisek má přednost před v každé situaci, nejednoznačný.  
  
> [!NOTE]
>  Popisky lze použít pouze na spustitelné příkazy uvnitř metody.  
  
### <a name="to-label-a-line-of-code"></a>K označení řádku kódu  
  
-   Místo identifikátoru, za nímž následuje dvojtečka, na začátek řádku zdrojového kódu.  
  
     Například následující řádky kódu jsou označeny `Jump` a `120`v uvedeném pořadí:  
  
     [!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]  
  
## <a name="see-also"></a>Viz také:
- [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
- [Deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Struktura programu a zásady týkající se kódu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
