---
title: 'Postupy: Vynucení předání argumentu podle hodnoty'
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
ms.openlocfilehash: 8261d126f988bdcf05b4a2af3106b38717e46bc8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344520"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>Postupy: Vynucení předání argumentu podle hodnoty (Visual Basic)
Deklarace procedury určuje mechanismus předávání. Pokud je parametr deklarovaný jako [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic očekává předání odpovídajícího argumentu odkazem. To umožňuje proceduře změnit hodnotu programovacího prvku podkladu argumentu v volajícím kódu. Pokud chcete chránit základní prvek proti takové změně, můžete přepsat `ByRef` mechanismu předání procedury v volání procedury uzavřením názvu argumentu do závorek. Tyto kulaté závorky jsou kromě závorek ohraničujících seznam argumentů ve volání.  
  
 Volající kód nemůže přepsat mechanismus [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) .  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>Vynutit předání argumentu hodnotou  
  
- Pokud je odpovídající parametr deklarován `ByVal` v proceduře, není nutné provádět žádné další kroky. Visual Basic již očekává předání argumentu hodnotou.  
  
- Pokud je odpovídající parametr deklarován `ByRef` v proceduře, uveďte argument do závorek ve volání procedury.  
  
## <a name="example"></a>Příklad  
 Následující příklad přepisuje deklaraci parametru `ByRef`. V volání, které vynucuje `ByVal`, si poznamenejte dvě úrovně závorek.  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 Pokud je `str` uzavřen v závorkách v seznamu argumentů, procedura `setNewString` nemůže změnit její hodnotu v kódu volajícího a `MsgBox` zobrazí "nelze je nahradit, pokud je to předáno". Když `str` není uzavřen v závorkách navíc, procedura ho může změnit a `MsgBox` zobrazí "Toto je nová hodnota pro argument inString."  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Pokud předáte proměnnou odkazem, je nutné použít klíčové slovo `ByRef` k určení tohoto mechanismu.  
  
 Výchozí hodnotou v Visual Basic je předání argumentů podle hodnoty. Nicméně je dobrým programovacím postupem, jak zahrnout klíčové slovo [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) s každým deklarovaným parametrem. To usnadňuje čtení kódu.  
  
## <a name="robust-programming"></a>Robustní programování  
 Pokud procedura deklaruje parametr [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), správné spuštění kódu může záviset na tom, zda je možné změnit podkladový prvek v kódu volajícího. Pokud volající kód přepíše tento volající mechanismus uzavřením argumentu do závorek nebo pokud předává argument, který není upraviteln, procedura nemůže změnit základní prvek. To může vést k neočekávaným výsledkům při volání kódu.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 V případě, že je možné změnit hodnotu podkladového typu argumentu v volajícím kódu, je vždy potenciálním rizikem. Ujistěte se, že jste očekávali, že tato hodnota se má změnit, a je připravená ji před použitím ověřit.  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)
- [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)
- [Rozdíly mezi upravitelnými a neupravitelnými argumenty](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Rozdíly mezi předáním argumentu podle hodnoty a podle reference](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Postupy: Změna hodnoty argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)
- [Postupy: Ochrana argumentu procedury před změnami hodnoty](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
