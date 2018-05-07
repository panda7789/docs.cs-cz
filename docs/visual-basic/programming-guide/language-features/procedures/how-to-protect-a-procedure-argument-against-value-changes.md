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
ms.openlocfilehash: d2e131b770d8498a634d946a5900f9b373ca7e56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a>Postupy: Ochrana argumentu procedury proti změnám hodnoty (Visual Basic)
Pokud procedury deklaruje parametr jako [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic poskytuje kód postup přímý odkaz na programovací element základní argument ve volání kódu. To umožňuje postup změňte hodnotu základní argument ve volání kódu. V některých případech může volající kód chcete chránit proti takové změny.  
  
 Vždy můžete chránit argument z změnu deklarováním odpovídající parametr [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) v postupu. Pokud chcete změnit zadaný argument v některých případech ale jiné ne, je možné deklarovat `ByRef` a nechat kód volání určit mechanismus předávání při každém volání. Dělá to pomocí uzavření odpovídající argument v závorkách k předání hodnotou nebo není uveden v závorkách k předání odkazem. Další informace najdete v tématu [postupy: vynucení předání hodnotou argumentu](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dva postupy, které provádějí proměnné pole a pracovat na jeho elementy. `increase` Postup jednoduše přidá jeden na každý element. `replace` Postup přiřadí nové pole do parametru `a()` a potom přidá jeden na každý element. Opětovné přiřazení neovlivňuje základní proměnné pole v volající kód.  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]  
  
 První `MsgBox` volání zobrazí "po increase(n): 11, 21, 31, 41". Protože pole `n` je typu odkazu `replace` můžete změnit její členy, i když tento mechanismus předávání `ByVal`.  
  
 Druhý `MsgBox` volání zobrazí "po replace(n): 11, 21, 31, 41". Protože `n` je předán `ByVal`, `replace` nelze upravit proměnnou `n` v kód volání přiřazením nové pole. Když `replace` vytvoří novou instanci pole `k` a přiřadí ji k místní proměnné `a`, se ztratí odkaz na `n` předaná volající kódem. Po změně členů `a`, pouze místní pole `k` má vliv. Proto `replace` nezvyšuje hodnoty pole `n` v volání kódu.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Ve výchozím nastavení v jazyce Visual Basic se předání argumentů hodnotou. Ale je dobrým zvykem obsahovat buď programovacím [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) – klíčové slovo s každou deklarovaný parametr. To výrazně zjednodušuje kódu ke čtení.  
  
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
