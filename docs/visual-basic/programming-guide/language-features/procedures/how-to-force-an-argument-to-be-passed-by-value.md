---
title: 'Postupy: Vynucení argumentu být předána podle hodnoty (Visual Basic)'
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
ms.openlocfilehash: 540271c414ac295c419533a4622657d60d123796
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665398"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>Postupy: Vynucení argumentu být předána podle hodnoty (Visual Basic)
Deklarace procedury určuje předávání. Pokud parametr je deklarován [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic se očekává, že odpovídající argument předávání odkazem. To umožňuje postup, chcete-li změnit hodnotu programovací element základní argumentu ve volajícím kódu. Pokud chcete chránit základní prvek proti takové změny, můžete přepsat `ByRef` předávání mechanismus v postupu pro volání uzavření název argumentu do závorek. Tyto závorky jsou kromě závorky uzavírající seznamu argumentů ve volání.  
  
 Volající kód nelze přepsat [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mechanismus.  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>K vynucení argumentu být předána podle hodnoty  
  
- Pokud je deklarován odpovídajícího parametru `ByVal` v postupu, nepotřebujete žádné další kroky. Visual Basic již očekává, že k předání argumentu podle hodnoty.  
  
- Pokud je deklarován odpovídajícího parametru `ByRef` v postupu, uzavřete jej do závorek ve volání procedury.  
  
## <a name="example"></a>Příklad  
 Následující příklad přepisuje `ByRef` deklarace parametru. Při volání funkce, která vynutí `ByVal`, Všimněte si dvě úrovně závorky.  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 Když `str` není uzavřen v závorkách navíc v rámci seznamu argumentů `setNewString` procedury nelze změnit jeho hodnotu ve volajícím kódu a `MsgBox` zobrazí "Nelze nahradit, pokud předaná ByVal". Když `str` není uzavřen v závorkách navíc, můžete změnit podle postupu, a `MsgBox` zobrazí "Toto je nová hodnota pro inString argument."  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Při předání proměnné podle odkazu, je nutné použít `ByRef` – klíčové slovo k určení tento mechanismus.  
  
 Ve výchozím nastavení v jazyce Visual Basic je předání argumentů podle hodnoty. Ale při programování je dobrým zvykem zahrnout buď [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) – klíčové slovo s každou deklarovaný parametr. Díky tomu váš kód lépe čitelný.  
  
## <a name="robust-programming"></a>Robustní programování  
 Pokud postup deklaruje parametr [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), správné spuštění kódu může záviset na schopnost změnit základní prvek ve volajícím kódu. Pokud volající kód přepíše tento mechanismus volání uzavřením argument v závorkách nebo v případě úspěšného neupravitelnými argumentu, nelze změnit postup základního elementu. To může vést k neočekávaným výsledkům ve volajícím kódu.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Je vždycky představuje potenciální riziko postup, chcete-li změnit hodnotu argumentu ve volajícím kódu základní, kterému je povoleno. Ujistěte se, že očekáváte, že tuto hodnotu změnit a připravit tak zkontrolovat, že platnost před jeho použitím.  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)
- [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)
- [Rozdíly mezi upravitelnými a neupravitelnými argumenty](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Rozdíly mezi předáním argumentu podle hodnoty a podle reference](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Postupy: Změna hodnoty argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)
- [Postupy: Ochrana argumentu procedury proti změnám hodnoty](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
