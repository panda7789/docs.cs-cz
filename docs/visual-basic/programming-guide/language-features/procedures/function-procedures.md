---
title: Procedury funkcí (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: 8b67a6953e7788827ef1ec268f54bddf2f1392c3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662254"
---
# <a name="function-procedures-visual-basic"></a>Procedury funkcí (Visual Basic)
A `Function` postup je řadu příkazů jazyka Visual Basic ohraničená `Function` a `End Function` příkazy. `Function` Postupu provede úlohu a potom vrátí řízení volajícímu kódu. Když vrátí řízení, také vrátí hodnotu volajícímu kódu.  
  
 Pokaždé, když volání procedury, jeho příkazy, počínaje první spustitelný příkaz po `Function` příkazu a končí prvním `End Function`, `Exit Function`, nebo `Return` byl zjištěn příkaz.  
  
 Můžete definovat `Function` postupu v modulu, třídy nebo struktury. Je `Public` ve výchozím nastavení, což znamená, že ho můžete volat z libovolného místa v aplikaci, která má přístup k modulu, třídy nebo struktury, ve kterém jste ji definovali.  
  
 A `Function` postupu můžete převzít argumenty, jako jsou konstanty, proměnné a výrazy, které jsou předávány do ní volající kód.  
  
## <a name="declaration-syntax"></a>Syntaxe deklarace  
 Syntaxe pro deklarování `Function` postup je následující:  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 *Modifikátory* můžete určit úroveň přístupu a informace týkající se přetížení, přepsání, sdílení a stínování. Další informace najdete v tématu [Function – příkaz](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Deklarujete každý parametr stejným způsobem jako u [Sub – procedury](./sub-procedures.md).  
  
### <a name="data-type"></a>Datový typ  
 Každý `Function` postupu má datový typ, stejně jako každá proměnná nemá. Tento typ dat je určená `As` klauzule `Function` příkaz který určuje datový typ hodnoty, vrátí funkce hodnotu volajícímu kódu. Následující ukázka deklarace ukazuje to.  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 Další informace najdete v tématu "Části" [Function – příkaz](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="returning-values"></a>Vrací hodnoty  
 Hodnota `Function` postup odešle zpět volajícímu kódu nazývá jeho návratovou hodnotu. Postup vrátí tuto hodnotu v jednom ze dvou způsobů:  
  
-   Používá `Return` příkaz a zadejte návratovou hodnotu a vrátí řízení okamžitě na volající program. Toto dokládá následující příklad.  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
-   Přiřadí hodnotu svůj vlastní název funkce v jeden nebo více příkazů procedury. Ovládací prvek nevrací do volajícího programu do `Exit Function` nebo `End Function` je proveden příkaz. Toto dokládá následující příklad.  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 Výhodou přiřazení návratovou hodnotu pro název funkce je, dokud nenarazí nevrátí řízení z procedury `Exit Function` nebo `End Function` příkazu. To umožňuje přiřadit hodnotu předběžné a upravte ho později, v případě potřeby.  
  
 Další informace o vrácení hodnot najdete v tématu [Function – příkaz](../../../../visual-basic/language-reference/statements/function-statement.md). Informace o vrácení pole najdete v tématu [pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="calling-syntax"></a>Syntaxe volání  
 Vyvolání `Function` proceduru včetně jejího názvu a argumenty buď na pravé straně příkazu přiřazení nebo ve výrazu. Je nutné zadat hodnoty pro všechny argumenty, které nejsou nepovinné a je nutné uzavřít do závorek seznamu argumentů. Pokud nejsou dodány žádné argumenty, můžete volitelně vynechejte závorky.  
  
 Syntaxe pro volání `Function` postup je následující:  
  
 *l-hodnoty*`=`*functionname* `[(` *seznam_argumentů*  `)]`  
  
 `If ((` *FunctionName* `[(` *seznam_argumentů* `)] / 3) <=` *výraz*  `) Then`  
  
 Při volání `Function` procedury, není nutné používat jeho návratovou hodnotu. Pokud ho nevidíte, jsou provedeny všechny akce funkce, ale je návratová hodnota ignorována. <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> se často nazývá tímto způsobem.  
  
### <a name="illustration-of-declaration-and-call"></a>Obrázek deklarace a volání  
 Následující `Function` postup vypočítá nejdelší strana nebo přepony pravoúhlého trojúhelníku, pro obě strany zadané hodnoty.  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/function-procedures_1.vb)]  
  
 Následující příklad ukazuje typické volání `hypotenuse`.  
  
 [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/function-procedures_2.vb)]  
  
## <a name="see-also"></a>Viz také:
- [Procedury](./index.md)
- [Procedury Sub](./sub-procedures.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Procedury operátoru](./operator-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Příkaz Function](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Postupy: Vytvořit proceduru, která vrací hodnotu](./how-to-create-a-procedure-that-returns-a-value.md)
- [Postupy: Vrácení hodnoty z procedury](./how-to-return-a-value-from-a-procedure.md)
- [Postupy: Volání procedury, která vrací hodnotu](./how-to-call-a-procedure-that-returns-a-value.md)
