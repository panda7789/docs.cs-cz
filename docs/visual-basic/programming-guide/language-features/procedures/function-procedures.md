---
title: Function – procedury
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: d7a0293e2ec520c2278f67156be56315d1def2b5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76780085"
---
# <a name="function-procedures-visual-basic"></a>Procedury funkcí (Visual Basic)

Procedura `Function` je série Visual Basic příkazů, které jsou uzavřeny příkazy `Function` a `End Function`. Procedura `Function` provede úlohu a vrátí řízení volajícímu kódu. Při návratu ovládacího prvku vrátí také hodnotu volajícímu kódu.

Pokaždé, když je procedura volána, její příkazy se spustí, počínaje prvním spustitelným příkazem po příkazu `Function` a končící prvním `End Function`, `Exit Function`nebo `Return`m příkazu.

Můžete definovat `Function` proceduru v modulu, třídě nebo struktuře. Ve výchozím nastavení je `Public`, což znamená, že ho můžete volat odkudkoli v aplikaci, která má přístup k modulu, třídě nebo struktuře, ve které jste ji definovali.

`Function` procedura může přebírat argumenty, jako jsou konstanty, proměnné nebo výrazy, které jsou předány volajícím kódem.

## <a name="declaration-syntax"></a>Syntaxe deklarace

Syntaxe pro deklaraci `Function` postup je následující:

```vb
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType
    [Statements]
End Function
```

*Modifikátory* mohou určovat úroveň přístupu a informace týkající se přetížení, přepsání, sdílení a stínování. Další informace naleznete v tématu [příkaz Function](../../../language-reference/statements/function-statement.md).

Každý parametr deklarujete stejným způsobem jako [procedury pro sub](./sub-procedures.md).

### <a name="data-type"></a>Datový typ

Každý `Function` procedura má datový typ stejně jako každá proměnná. Tento typ dat je určen klauzulí `As` v příkazu `Function` a určuje datový typ hodnoty, kterou funkce vrátí na volající kód. Tento příklad ilustruje následující ukázkové deklarace.

```vb
Function Yesterday() As Date
End Function

Function FindSqrt(radicand As Single) As Single
End Function
```

Další informace naleznete v části "části" v [příkazu Function](../../../language-reference/statements/function-statement.md).

### <a name="returning-values"></a>Vracení hodnot

Hodnota `Function` procedura odesílá zpět do volajícího kódu se nazývá návratová hodnota. Procedura vrátí tuto hodnotu jedním ze dvou způsobů:

- Používá příkaz `Return` k určení návratové hodnoty a vrátí řízení ihned volajícímu programu. Toto dokládá následující příklad.

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement immediately transfers control back
      ' to the calling code and returns the value of Expression.
      Return Expression
  End Function
  ```

- Přiřadí hodnotu vlastnímu názvu funkce v jednom nebo více příkazech procedury. Řízení se nevrátí do volajícího programu, dokud není proveden příkaz `Exit Function` nebo `End Function`. Toto dokládá následující příklad.

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement does not transfer control back to the calling code.
      FunctionName = Expression
      ' When control returns to the calling code, Expression is the return value.
  End Function
  ```

Výhodou přiřazení návratové hodnoty k názvu funkce je, že se ovládací prvek z procedury nevrátí, dokud nenalezne příkaz `Exit Function` nebo `End Function`. To vám umožní přiřadit předběžnou hodnotu a v případě potřeby ho upravit později.

Další informace o vrácení hodnot naleznete v tématu [příkaz Function](../../../language-reference/statements/function-statement.md). Informace o vracení polí naleznete v tématu [Arrays](../arrays/index.md).

## <a name="calling-syntax"></a>Syntaxe volání

Vyvoláte `Function` proceduru zahrnutím jejího názvu a argumentů buď na pravé straně příkazu přiřazení, nebo ve výrazu. Je nutné zadat hodnoty pro všechny argumenty, které nejsou volitelné, a je třeba uzavřít seznam argumentů v závorkách. Pokud nejsou zadány žádné argumenty, můžete volitelně vynechat závorky.

Syntaxe pro volání procedury `Function` je následující.

*l* -hodnota`=`*function* `[(` *ArgumentList* `)]`

`If ((` *function* `[(` *argumentlist* `)] / 3) <=`*výraz* `) Then`

Při volání `Function`ho postupu není nutné použít jeho návratovou hodnotu. Pokud to neuděláte, jsou provedeny všechny akce funkce, ale návratová hodnota je ignorována. Tento způsob je často volán <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>.

### <a name="illustration-of-declaration-and-call"></a>Ilustrace deklarace a volání

Následující `Function` postup vypočítá nejdelší stranu (neboli přepony) pravého trojúhelníku s ohledem na hodnoty ostatních dvou stran.

[!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

Následující příklad ukazuje typické volání `hypotenuse`.

[!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]

## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Procedury Sub](./sub-procedures.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Procedury operátoru](./operator-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Příkaz Function](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Postupy: Vytvoření procedury, která vrací hodnotu](./how-to-create-a-procedure-that-returns-a-value.md)
- [Postupy: Vrácení hodnoty z procedury](./how-to-return-a-value-from-a-procedure.md)
- [Postupy. Volání procedury, která vrací hodnotu](./how-to-call-a-procedure-that-returns-a-value.md)
