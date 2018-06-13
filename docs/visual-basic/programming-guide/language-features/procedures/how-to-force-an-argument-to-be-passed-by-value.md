---
title: 'Postupy: Vynucení předání argumentu podle hodnoty (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], in parentheses
- procedure arguments [Visual Basic], in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
ms.openlocfilehash: adc58c34150030eb0fc82050576bfecc453e21ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651074"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>Postupy: Vynucení předání argumentu podle hodnoty (Visual Basic)
Deklarace procedury určuje předávání. Pokud je deklarovaný parametr [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic očekává, že předávají odpovídající argument odkazem. To umožňuje postup změnit hodnotu programovací element základní argument ve volání kódu. Pokud chcete chránit základní element proti takové změn, můžete přepsat `ByRef` mechanismus předávání v postupu volání uzavřením argument názvu v závorkách. Tyto závorek je kromě závorkách ohraničení seznamu argumentů volání.  
  
 Volání kódu nejde přepsat [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mechanismus.  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>Chcete-li vynutit argumentu předání hodnotou  
  
-   Pokud je deklarovaný s odpovídajícím parametrem `ByVal` v postupu, není nutné žádné další kroky. Visual Basic již očekává k předání argumentu podle hodnoty.  
  
-   Pokud je deklarovaný s odpovídajícím parametrem `ByRef` v postupu, uzavřete jej v závorkách ve volání procedury.  
  
## <a name="example"></a>Příklad  
 Následující příklad přepíše `ByRef` deklarace parametru. Ve volání, které vynutí `ByVal`, Všimněte si, která je dvě úrovně závorek.  
  
 [!code-vb[VbVbcnProcedures#39](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#40](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]  
  
 Když `str` uzavřený v závorkách navíc v seznamu argument `setNewString` procedury nelze změnit její hodnota v kód volání a `MsgBox` zobrazí "Nelze nahradit, pokud předány ByVal". Když `str` není uzavřený v závorkách navíc, postup, můžete ho změnit a `MsgBox` zobrazí "Toto je nová hodnota pro inString argument."  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Pokud předáte proměnné odkazem, je nutné použít `ByRef` – klíčové slovo zadat Tento mechanismus.  
  
 Ve výchozím nastavení v jazyce Visual Basic se předání argumentů hodnotou. Ale je dobrým zvykem obsahovat buď programovacím [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) – klíčové slovo s každou deklarovaný parametr. To výrazně zjednodušuje kódu ke čtení.  
  
## <a name="robust-programming"></a>Robustní programování  
 Pokud procedury deklaruje parametr [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), správné spuštění kódu může záviset na možnost změnit základní elementu v kódu volání. Pokud volání kód přepíše tento mechanismus volání uzavřením argument do závorek, nebo pokud předává neupravitelnými argument, nelze změnit postup základní elementu. To může vést k neočekávaným výsledkům v volání kódu.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Postup ke změně hodnoty základní argument volající kód, který umožňuje existuje vždy představuje potenciální riziko. Ujistěte se, že byste měli tuto hodnotu změnit, a zkontrolujte správnost před jeho použitím připravit.  
  
## <a name="see-also"></a>Viz také  
 [Procedury](./index.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)  
 [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)  
 [Rozdíly mezi upravitelnými a neupravitelnými argumenty](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [Rozdíly mezi předáním argumentu podle hodnoty a podle reference](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [Postupy: Změna hodnoty argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Postupy: Ochrana argumentu procedury před změnami hodnoty](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md)  
 [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
