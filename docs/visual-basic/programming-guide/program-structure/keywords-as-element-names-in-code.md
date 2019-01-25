---
title: Klíčová slova jako názvy elementu v kódu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: 0d52df42b00abfa364762d97c162eb143e511f06
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649482"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a>Klíčová slova jako názvy elementu v kódu (Visual Basic)
Libovolný prvek programu, jako jsou proměnné, třídu nebo člen – může mít stejný název jako s omezeným přístupem – klíčové slovo. Můžete například vytvořit proměnnou s názvem `Loop`. Však k odkazování na vaší verzi, která má stejný název jako s omezeným přístupem `Loop` – klíčové slovo – musí předcházet řetězec úplné kvalifikace nebo uzavřete ho do hranatých závorek (`[ ]`), jak ukazuje následující příklad.  
  
 [!code-vb[VbVbcnConventions#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/keywords-as-element-names-in-code_1.vb)]  
  
 Pokud, proveďte jednu z nich pak jazyka Visual Basic se předpokládá použití uvedených vnitřní `Loop` – klíčové slovo a dojde k chybě, jako v následujícím příkladu:  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 Hranaté závorky můžete použít k odkazování na formuláře a ovládací prvky a při deklarování proměnné nebo definice procedury se stejným názvem jako s omezeným přístupem – klíčové slovo. Může být snadné zapomenout kvalifikovat názvy nebo zahrnovat hranaté závorky a proto zanést chyby do kódu a znesnadňuje ke čtení. Z tohoto důvodu doporučujeme je velmi riskantní používat s omezeným přístupem klíčová slova jako názvy prvků programu. Ale pokud budoucí verzi systému Visual Basic definuje new – klíčové slovo této je v konfliktu s existujícím formuláři nebo název ovládacího prvku, pak můžete použít tento postup při aktualizaci kódu pro práci s novou verzí.  
  
> [!NOTE]
>  Váš program může obsahovat také názvy elementů poskytované jiných odkazovaných sestavení. Pokud tyto názvy jsou v konfliktu s klíčovými slovy s omezeným přístupem, pak umístění hranaté závorky kolem nich způsobí, že chcete interpretovat jako definované elementy jazyka Visual Basic.  
  
## <a name="see-also"></a>Viz také:
- [Zásady vytváření názvů jazyka Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [Struktura programu a zásady týkající se kódu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
