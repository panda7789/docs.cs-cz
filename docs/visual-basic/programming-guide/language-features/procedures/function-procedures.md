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
ms.openlocfilehash: 887c930cb757b012542c97d64a57a62882a2eed3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655532"
---
# <a name="function-procedures-visual-basic"></a>Procedury funkcí (Visual Basic)
A `Function` postup je řada příkazů jazyka Visual Basic uzavřené do `Function` a `End Function` příkazy. `Function` Postup provede úlohu a potom se vrátí ovládací prvek volání kódu. Až se obnoví ovládací prvek, také vrátí hodnotu, voláním kódu.  
  
 Při každém volání procedury, jeho příkazy spustit, počínaje prvním příkazem spustitelný soubor po `Function` prohlášení a ukončuje se první `End Function`, `Exit Function`, nebo `Return` byl zjištěn příkaz.  
  
 Můžete definovat `Function` postupu v modulu, třídu nebo strukturu. Je `Public` ve výchozím nastavení, což znamená, můžete ji volat z libovolného místa ve vaší aplikaci, která má přístup k modulu, třídu nebo strukturu, ve kterém jste ji definovali.  
  
 A `Function` postup může trvat argumenty, jako jsou konstanty, proměnné nebo výrazy, které jsou k němu předaná volající kód.  
  
## <a name="declaration-syntax"></a>Syntaxe deklarace  
 Syntaxe deklarace `Function` postup je následující:  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 *Modifikátory* můžete zadat úroveň přístupu a informací o přetížení, přepsání, sdílení a stínový provoz. Další informace najdete v tématu [funkce příkaz](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Deklarovat každý parametr stejným způsobem jako u [Sub – procedury](./sub-procedures.md).  
  
### <a name="data-type"></a>Datový typ  
 Každý `Function` postup má datový typ, stejně jako všechny proměnné nemá. Tento typ dat je zadána `As` klauzuli v `Function` příkaz a určuje datový typ hodnoty, vrátí funkce volání kódu. Následující ukázka deklarace znázornění.  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 Další informace najdete v tématu "Částí" v [funkce příkaz](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="returning-values"></a>Návrat hodnot  
 Hodnota `Function` postup odesílá zpět do volání kódu se nazývá hodnoty. Postup vrací hodnotu této v jednom ze dvou způsobů:  
  
-   Použije `Return` příkaz k určení návratovou hodnotu a vrátí řídit okamžitě k volací program. Toto dokládá následující příklad.  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
-   Přiřadí hodnotu svůj vlastní název funkce v jednom či více příkazech procedury. Řízení nevrátí volací program až `Exit Function` nebo `End Function` spustit příkaz. Toto dokládá následující příklad.  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 Výhodou přiřazení návratovou hodnotu pro název funkce je, dokud zjistí nevrací ovládací prvek v postupu `Exit Function` nebo `End Function` příkaz. To umožňuje přiřadit hodnotu předběžná a později upravit v případě potřeby.  
  
 Další informace o vrácení hodnot najdete v tématu [funkce příkaz](../../../../visual-basic/language-reference/statements/function-statement.md). Informace o vrácení pole najdete v tématu [pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="calling-syntax"></a>Syntaxe volání  
 Vyvolání `Function` postupu včetně jeho název a argumenty buď na pravé straně příkazu přiřazení nebo ve výrazu. Je nutné zadat hodnoty pro všechny argumenty, které nejsou volitelné a seznam argumentů je nutné uzavřít do závorek. Pokud jsou zadány žádné argumenty, můžete volitelně vynechat závorkách.  
  
 Syntaxe volání `Function` postup je následující:  
  
 *lvalue*`=`*%{FunctionName/* `[(` *argumentlist* `)]`  
  
 `If ((` *%{FunctionName/* `[(` *argumentlist* `)] / 3) <=` *výraz* `) Then`  
  
 Při volání `Function` postupu, není nutné použít hodnoty. Pokud ho použít nechcete, všechny akce, které funkce jsou prováděny, ale vrácená hodnota je ignorována. <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> se často nazývá tímto způsobem.  
  
### <a name="illustration-of-declaration-and-call"></a>Obrázek deklarace a volání  
 Následující `Function` postup vypočítá nejdelší straně nebo přepony trojúhelníku vpravo, pro zbývající dvě strany zadané hodnoty.  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/function-procedures_1.vb)]  
  
 Následující příklad ukazuje typické volání `hypotenuse`.  
  
 [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/function-procedures_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Procedury](./index.md)  
 [Procedury Sub](./sub-procedures.md)  
 [Procedury vlastnosti](./property-procedures.md)  
 [Procedury operátoru](./operator-procedures.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Příkaz Function](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Postupy: Vytvoření procedury, která vrací hodnotu](./how-to-create-a-procedure-that-returns-a-value.md)  
 [Postupy: Vrácení hodnoty z procedury](./how-to-return-a-value-from-a-procedure.md)  
 [Postupy. Volání procedury, která vrací hodnotu](./how-to-call-a-procedure-that-returns-a-value.md)
