---
title: 'Postupy: Příkazy Label (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: 6b442b5a0ad731cfc490a7387c78ac9279dddaf0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961323"
---
# <a name="how-to-label-statements-visual-basic"></a>Postupy: Příkazy Label (Visual Basic)
Bloky příkazů jsou tvořeny řádky kódu, které jsou odděleny dvojtečkami. Řádky kódu předchází identifikující řetězec nebo celé číslo jsou označeny jako *popisky*. Popisky příkazů slouží k označení řádku kódu k identifikaci pro použití s příkazy, jako je například `On Error Goto`.  
  
 Popisky mohou být platné Visual Basic identifikátory, například ty, které identifikují programovací prvky – nebo celočíselné literály. Popisek se musí objevit na začátku řádku zdrojového kódu a musí následovat dvojtečka bez ohledu na to, jestli je následován příkazem na stejném řádku.  
  
 Kompilátor identifikuje popisky tím, že zkontroluje, zda začátek řádku odpovídá jakémukoli již definovanému identifikátoru. Pokud tomu tak není, kompilátor předpokládá, že se jedná o popisek.  
  
 Popisky mají vlastní prostor deklarací a neovlivňují jiné identifikátory. Obor popisku je tělo metody. Deklarace popisku má přednost v jakékoli dvojznačné situaci.  
  
> [!NOTE]
> Popisky lze použít pouze pro spustitelné příkazy uvnitř metod.  
  
### <a name="to-label-a-line-of-code"></a>Popisek řádku kódu  
  
- Umístěte identifikátor následovaný dvojtečkou na začátku řádku zdrojového kódu.  
  
     Například následující řádky kódu jsou označeny pomocí `Jump` a `120`, v uvedeném pořadí:  
  
     [!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]  
  
## <a name="see-also"></a>Viz také:

- [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
- [Deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Struktura programu a zásady týkající se kódu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
