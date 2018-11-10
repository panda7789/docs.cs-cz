---
title: 'Postupy: Ochrana argumentu procedury proti změnám hodnoty (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
ms.openlocfilehash: 393127353a020c1db5df3011b2a97b1c53097f27
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225331"
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a>Postupy: Ochrana argumentu procedury proti změnám hodnoty (Visual Basic)
Pokud se deklaruje jako parametr procedury [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic poskytuje kód procedury přímý odkaz na programovací prvek základní argumentu ve volajícím kódu. To umožňuje změnit hodnotu argumentu ve volajícím kódu základní postup. V některých případech volající kód může být vhodné pro ochranu před tuto změnu.  
  
 Argument lze vždy chránit před změnu deklarováním odpovídajícího parametru [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) v postupu. Pokud chcete být schopni změnit daný argument v některých případech ale jiné ne, je možné deklarovat `ByRef` a umožní volajícím kódu určit předávání mechanismus při každém volání. Dělá to tak, že nadřazený odpovídající argument v závorkách předat hodnotou nebo není nadřazený v závorkách předávání pomocí odkazu. Další informace najdete v tématu [postupy: vynucení argumentu mají být předány podle hodnoty](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dva postupy, které trvat proměnnou pole a provozují na jeho prvků. `increase` Procedura přidá pouze jednu na každý prvek. `replace` Postup přiřadí nové pole parametru `a()` a pak přidá jednu na každý prvek. Opětovné přiřazení neovlivní základní proměnné pole ve volajícím kódu.  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]  
  
 První `MsgBox` volání zobrazí "po increase(n): 11, 21, 31, 41". Protože pole `n` je typem odkazu `increase` lze měnit její členy, i když je mechanismus předávání `ByVal`.  
  
 Druhá `MsgBox` volání zobrazí "po replace(n): 11, 21, 31, 41". Protože `n` je předán `ByVal`, `replace` nelze upravit proměnnou `n` ve volajícím kódu tak, že k němu přiřadíte nové pole. Když `replace` vytvoří novou instanci pole `k` a přiřadí ji na místní proměnnou `a`, ztratí odkaz na `n` předaných v volající kód. Při změně členů `a`, pouze místní pole `k` má vliv. Proto `replace` nezvyšuje hodnoty pole `n` ve volajícím kódu.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Ve výchozím nastavení v jazyce Visual Basic je předání argumentů podle hodnoty. Ale při programování je dobrým zvykem zahrnout buď [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) – klíčové slovo s každou deklarovaný parametr. Díky tomu váš kód lépe čitelný.  
  
## <a name="see-also"></a>Viz také  
 [Procedury](./index.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)  
 [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)  
 [Rozdíly mezi upravitelnými a neupravitelnými argumenty](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [Rozdíly mezi předáním argumentu podle hodnoty a podle reference](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [Postupy: Změna hodnoty argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Postupy: Vynucení předání argumentu podle hodnoty](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md)  
 [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
