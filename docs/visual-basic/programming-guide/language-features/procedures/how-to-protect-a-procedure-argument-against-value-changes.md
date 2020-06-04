---
title: 'Postupy: Ochrana argumentu procedury proti změnám hodnoty'
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
ms.openlocfilehash: b0504d9f7a8862274d5d71dc6a9c1570551629a5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414360"
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a>Postupy: Ochrana argumentu procedury proti změnám hodnoty (Visual Basic)
Pokud procedura deklaruje parametr jako typ [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic poskytne kód procedury přímý odkaz na programovací element podkladové argumentu v volajícím kódu. To umožňuje proceduře změnit hodnotu podkladové hodnoty argumentu ve volajícím kódu. V některých případech by volající kód mohl chtít chránit proti takové změně.  
  
 Můžete vždy chránit argument ze změny tím, že deklarujete odpovídající parametr [ByVal](../../../language-reference/modifiers/byval.md) v proceduře. Pokud chcete mít možnost změnit daný argument v některých případech, ale ne jiné, můžete ho deklarovat `ByRef` a nechat volající kód určit mechanismus předávání v každém volání. To dělá tak, že uzavře odpovídající argument v závorkách, aby je předávala podle hodnoty, nebo nesmí být uzavřen v závorkách, aby bylo možné ho předat odkazem. Další informace naleznete v tématu [How to: Force a argument by měl být předán hodnotou](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dva postupy, které přebírají proměnnou pole a pracují s jejími prvky. `increase`Procedura jednoduše přidá jeden do každého prvku. `replace`Procedura přiřadí parametr novému poli `a()` a poté přidá jeden do každého prvku. Opětovné přiřazení však nemá vliv na podkladovou proměnnou pole v kódu volajícího.  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 První `MsgBox` volání zobrazí "po zvýšení (n): 11, 21, 31, 41". Vzhledem k tomu `n` , že pole je odkazový typ, `increase` může změnit jeho členy, i když je mechanismus předávání `ByVal` .  
  
 Druhé `MsgBox` volání zobrazí "po nahrazení (n): 11, 21, 31, 41". Vzhledem `n` k tomu, že je předána `ByVal` , `replace` nelze změnit proměnnou `n` v volajícím kódu přiřazením nového pole do něj. Když `replace` vytvoří novou instanci pole `k` a přiřadí ji k místní proměnné `a` , ztratí odkaz na `n` předaný volajícím kódem. Když změní členy `a` , bude ovlivněn pouze místní pole `k` . Proto `replace` nezvyšuje hodnoty pole `n` v volajícím kódu.  
  
## <a name="compile-the-code"></a>Kompilovat kód  
 Výchozí hodnotou v Visual Basic je předání argumentů podle hodnoty. Nicméně je dobrým programovacím postupem, jak zahrnout klíčové slovo [ByVal](../../../language-reference/modifiers/byval.md) nebo [ByRef](../../../language-reference/modifiers/byref.md) s každým deklarovaným parametrem. To usnadňuje čtení kódu.  
  
## <a name="see-also"></a>Viz také

- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)
- [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)
- [Rozdíly mezi upravitelnými a neupravitelnými argumenty](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Rozdíly mezi předáním argumentu podle hodnoty a podle reference](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Postupy: Změna hodnoty argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)
- [Postupy: Vynucení předání argumentu podle hodnoty](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md)
- [Typy hodnot a typy odkazu](../data-types/value-types-and-reference-types.md)
