---
title: Procedury funkcí
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: b0ba96a875fd8785e45eee565beefe4b961ffc9d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388748"
---
# <a name="function-procedures-visual-basic"></a>Procedury funkcí (Visual Basic)

`Function`Procedura je řada příkazů Visual Basic uzavřených `Function` `End Function` příkazy a. `Function`Procedura provede úlohu a vrátí řízení volajícímu kódu. Při návratu ovládacího prvku vrátí také hodnotu volajícímu kódu.

Pokaždé, když je procedura volána, její příkazy se spustí, počínaje prvním spustitelným příkazem po `Function` příkazu a končí prvním `End Function` `Exit Function` příkazem, nebo `Return` .

Můžete definovat `Function` proceduru v modulu, třídě nebo struktuře. `Public`Ve výchozím nastavení to znamená, že ho můžete volat odkudkoli v aplikaci, která má přístup k modulu, třídě nebo struktuře, ve které jste ho definovali.

`Function`Procedura může přebírat argumenty, jako jsou konstanty, proměnné nebo výrazy, které jsou předány volajícím kódem.

## <a name="declaration-syntax"></a>Syntaxe deklarace

Syntaxe pro deklaraci `Function` procedury je následující:

```vb
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType
    [Statements]
End Function
```

*Modifikátory* mohou určovat úroveň přístupu a informace týkající se přetížení, přepsání, sdílení a stínování. Další informace naleznete v tématu [příkaz Function](../../../language-reference/statements/function-statement.md).

Každý parametr deklarujete stejným způsobem jako [procedury pro sub](./sub-procedures.md).

### <a name="data-type"></a>Datový typ

Každý `Function` postup má datový typ stejně jako každá proměnná. Tento typ dat je určen `As` klauzulí v `Function` příkazu a určuje datový typ hodnoty, kterou funkce vrátí na volající kód. Tento příklad ilustruje následující ukázkové deklarace.

```vb
Function Yesterday() As Date
End Function

Function FindSqrt(radicand As Single) As Single
End Function
```

Další informace naleznete v části "části" v [příkazu Function](../../../language-reference/statements/function-statement.md).

### <a name="returning-values"></a>Vracení hodnot

Hodnota, kterou `Function` procedura odesílá zpět do volajícího kódu, se nazývá vrácená hodnota. Procedura vrátí tuto hodnotu jedním ze dvou způsobů:

- Používá `Return` příkaz k určení návratové hodnoty a vrátí řízení ihned volajícímu programu. Toto dokládá následující příklad.

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement immediately transfers control back
      ' to the calling code and returns the value of Expression.
      Return Expression
  End Function
  ```

- Přiřadí hodnotu vlastnímu názvu funkce v jednom nebo více příkazech procedury. Řízení se nevrátí do volajícího programu, dokud `Exit Function` `End Function` není proveden příkaz nebo. Toto dokládá následující příklad.

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement does not transfer control back to the calling code.
      FunctionName = Expression
      ' When control returns to the calling code, Expression is the return value.
  End Function
  ```

Výhodou přiřazení návratové hodnoty k názvu funkce je, že se ovládací prvek z procedury nevrátí, dokud nenalezne `Exit Function` příkaz or `End Function` . To vám umožní přiřadit předběžnou hodnotu a v případě potřeby ho upravit později.

Další informace o vrácení hodnot naleznete v tématu [příkaz Function](../../../language-reference/statements/function-statement.md). Informace o vracení polí naleznete v tématu [Arrays](../arrays/index.md).

## <a name="calling-syntax"></a>Syntaxe volání

Proceduru vyvoláte tak, že zadáte `Function` její název a argumenty buď na pravé straně příkazu přiřazení, nebo ve výrazu. Je nutné zadat hodnoty pro všechny argumenty, které nejsou volitelné, a je třeba uzavřít seznam argumentů v závorkách. Pokud nejsou zadány žádné argumenty, můžete volitelně vynechat závorky.

Syntaxe pro volání `Function` procedury je následující.

*l* `=` -hodnota *funkce Function* `[(` *ArgumentList*    `)]`

`If ((`*funkce Function* `[(` *ArgumentList* `)] / 3) <=` *výraz*  `) Then`

Při volání `Function` procedury není nutné použít její návratovou hodnotu. Pokud to neuděláte, jsou provedeny všechny akce funkce, ale návratová hodnota je ignorována. <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>se často volá tímto způsobem.

### <a name="illustration-of-declaration-and-call"></a>Ilustrace deklarace a volání

Následující `Function` postup vypočítá nejdelší stranu (neboli přepony) pravého trojúhelníku s ohledem na hodnoty ostatních dvou stran.

[!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

Následující příklad ukazuje typické volání metody `hypotenuse` .

[!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]

## <a name="see-also"></a>Viz také

- [Procedury](./index.md)
- [Procedury Sub](./sub-procedures.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Procedury operátoru](./operator-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Function – příkaz](../../../language-reference/statements/function-statement.md)
- [Postupy: Vytvoření procedury, která vrací hodnotu](./how-to-create-a-procedure-that-returns-a-value.md)
- [Postupy: Vrácení hodnoty z procedury](./how-to-return-a-value-from-a-procedure.md)
- [Postupy. Volání procedury, která vrací hodnotu](./how-to-call-a-procedure-that-returns-a-value.md)
