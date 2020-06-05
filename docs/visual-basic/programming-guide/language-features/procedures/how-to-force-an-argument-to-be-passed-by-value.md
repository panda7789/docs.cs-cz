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
ms.openlocfilehash: 48f7d7afebd76916cba11459532d89d71871c79b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387961"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>Postupy: Vynucení předání argumentu podle hodnoty (Visual Basic)
Deklarace procedury určuje mechanismus předávání. Pokud je parametr deklarovaný jako [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic očekává předání odpovídajícího argumentu odkazem. To umožňuje proceduře změnit hodnotu programovacího prvku podkladu argumentu v volajícím kódu. Pokud chcete chránit základní prvek proti takové změně, můžete přepsat `ByRef` mechanismus předávání v volání procedury uzavřením názvu argumentu do závorek. Tyto kulaté závorky jsou kromě závorek ohraničujících seznam argumentů ve volání.  
  
 Volající kód nemůže přepsat mechanismus [ByVal](../../../language-reference/modifiers/byval.md) .  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>Vynutit předání argumentu hodnotou  
  
- Pokud je příslušný parametr deklarován `ByVal` v proceduře, není nutné provádět žádné další kroky. Visual Basic již očekává předání argumentu hodnotou.  
  
- Pokud je odpovídající parametr deklarován `ByRef` v proceduře, uveďte argument do závorek v proceduře volání procedury.  
  
## <a name="example"></a>Příklad  
 Následující příklad přepisuje `ByRef` deklaraci parametru. V volání, které vynucuje `ByVal` , si všimněte dvou úrovní závorek.  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 Když `str` je uzavřen v závorkách v seznamu argumentů, `setNewString` procedura nemůže změnit jeho hodnotu v kódu volajícího a `MsgBox` zobrazení "nemůže být nahrazeno, pokud bylo předáno" ByVal ". Když není `str` uzavřen v závorkách navíc, procedura ho může změnit a `MsgBox` zobrazí "Toto je nová hodnota pro argument inString."  
  
## <a name="compile-the-code"></a>Kompilovat kód  
 Pokud předáte proměnnou odkazem, je nutné použít `ByRef` klíčové slovo k určení tohoto mechanismu.  
  
 Výchozí hodnotou v Visual Basic je předání argumentů podle hodnoty. Nicméně je dobrým programovacím postupem, jak zahrnout klíčové slovo [ByVal](../../../language-reference/modifiers/byval.md) nebo [ByRef](../../../language-reference/modifiers/byref.md) s každým deklarovaným parametrem. To usnadňuje čtení kódu.  
  
## <a name="robust-programming"></a>Robustní programování  
 Pokud procedura deklaruje parametr [ByRef](../../../language-reference/modifiers/byref.md), správné spuštění kódu může záviset na tom, zda je možné změnit podkladový prvek v kódu volajícího. Pokud volající kód přepíše tento volající mechanismus uzavřením argumentu do závorek nebo pokud předává argument, který není upraviteln, procedura nemůže změnit základní prvek. To může vést k neočekávaným výsledkům při volání kódu.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 V případě, že je možné změnit hodnotu podkladového typu argumentu v volajícím kódu, je vždy potenciálním rizikem. Ujistěte se, že jste očekávali, že tato hodnota se má změnit, a je připravená ji před použitím ověřit.  
  
## <a name="see-also"></a>Viz také

- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)
- [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)
- [Rozdíly mezi upravitelnými a neupravitelnými argumenty](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Rozdíly mezi předáním argumentu podle hodnoty a podle reference](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Postupy: Změna hodnoty argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)
- [Postupy: Ochrana argumentu procedury před změnami hodnoty](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md)
- [Typy hodnot a typy odkazu](../data-types/value-types-and-reference-types.md)
