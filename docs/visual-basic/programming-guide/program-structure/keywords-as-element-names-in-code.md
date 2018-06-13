---
title: Klíčová slova jako názvy elementu v kódu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: 53c3172e8518115d001c23be2430fbc87ae1b60f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652575"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a>Klíčová slova jako názvy elementu v kódu (Visual Basic)
Žádné program element – například proměnné, třída nebo člen – může mít stejný název jako s omezeným přístupem – klíčové slovo. Například můžete vytvořit proměnné s názvem `Loop`. Však k odkazování na vaší verzi, který má stejný název jako s omezeným přístupem `Loop` – klíčové slovo – musí předcházet řetězcem úplné kvalifikace nebo hranaté závorky (`[ ]`), jak ukazuje následující příklad.  
  
 [!code-vb[VbVbcnConventions#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/keywords-as-element-names-in-code_1.vb)]  
  
 Pokud neprovedete tyto, pak jazyka Visual Basic předpokládá použití vnitřní `Loop` – klíčové slovo a vytvoří chybu, jako v následujícím příkladu:  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 Hranaté závorky můžete použít k odkazování na formuláře a ovládací prvky a pokud deklarace proměnné nebo definování procedura se stejným názvem jako s omezeným přístupem – klíčové slovo. Může být snadno nezapomněli kvalifikovat názvy nebo zahrnují hranaté závorky a proto zavést kódu chyby a znesnadňuje ke čtení. Z tohoto důvodu doporučujeme používat s omezeným přístupem klíčová slova jako názvy elementů programu. Ale pokud budoucí verze aplikace Visual Basic definuje new – klíčové slovo, které jsou v konfliktu s existující formuláře nebo název ovládacího prvku, pak můžete tento postup při aktualizaci kódu pro práci s novou verzí.  
  
> [!NOTE]
>  Váš program také mohou zahrnovat názvy elementů od ostatních odkazované sestavení. Pokud tyto názvy v konfliktu s omezeným klíčová slova, pak umístění hranaté závorky je obcházet způsobí, že je interpretovat jako definované prvky jazyka Visual Basic.  
  
## <a name="see-also"></a>Viz také  
 [Zásady vytváření názvů jazyka Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [Struktura programu a zásady týkající se kódu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
