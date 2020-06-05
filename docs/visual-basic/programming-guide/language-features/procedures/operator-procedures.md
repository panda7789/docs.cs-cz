---
title: Procedury operátoru
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
ms.openlocfilehash: a1dd183570c8aa50efff85bdaebef90bd3b0120f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364315"
---
# <a name="operator-procedures-visual-basic"></a>Procedury operátoru (Visual Basic)

Procedura operátora je série Visual Basic příkazů, které definují chování standardního operátoru (například `*` , `<>` nebo `And` ) na třídě nebo struktuře, kterou jste definovali. Tato metoda se označuje také jako *přetížení operátoru*.

## <a name="when-to-define-operator-procedures"></a>Kdy definovat procedury operátorů

Pokud jste definovali třídu nebo strukturu, můžete deklarovat proměnné, které mají být typu této třídy nebo struktury. V některých případech je třeba, aby se tato proměnná účastnila operace v rámci výrazu. Chcete-li to provést, musí být operandem operátoru.

Visual Basic definuje operátory pouze na svých základních datových typech. Můžete definovat chování operátoru v případě, že jeden nebo oba operandy jsou typu vaší třídy nebo struktury.

Další informace naleznete v tématu [operátor příkazu](../../../language-reference/statements/operator-statement.md).

## <a name="types-of-operator-procedure"></a>Typy procedury operátoru

Procedura operátora může být jedním z následujících typů:

- Definice unárního operátoru, kde argument je typu vaší třídy nebo struktury.

- Definice binárního operátoru, kde je alespoň jeden z argumentů typu vaší třídy nebo struktury.

- Definice operátora převodu, kde argument je typu vaší třídy nebo struktury.

- Definice operátora převodu, který vrací typ vaší třídy nebo struktury.

 Operátory převodu jsou vždycky unární a vždycky se používají `CType` jako operátor, který definujete.

## <a name="declaration-syntax"></a>Syntaxe deklarace

Syntaxe pro deklarování procedury operátoru je následující:

```vb
Public Shared [Widening | Narrowing] Operator operatorsymbol ( operand1 [,  operand2 ]) As datatype

' Statements of the operator procedure.

End Operator
```

`Widening`Klíčové slovo nebo použijte `Narrowing` pouze v operátoru konverze typu. Symbol operátoru je vždy [CType funkce](../../../language-reference/functions/ctype-function.md) pro operátor převodu typu.

Deklarujete dva operandy pro definování binárního operátoru a deklarujete jeden operand pro definování unárního operátoru, včetně operátoru převodu typu. Všechny operandy musí být deklarovány `ByVal` .

Každým operandem deklarujete stejný způsob, jakým deklarujete parametry pro [procedury Sub](./sub-procedures.md).

### <a name="data-type"></a>Typ dat

Vzhledem k tomu, že definujete operátora pro třídu nebo strukturu, kterou jste definovali, alespoň jeden z operandů musí být datového typu této třídy nebo struktury. Pro operátor konverze typu musí být operand nebo návratový typ buď datového typu třídy nebo struktury.

Další podrobnosti naleznete v tématu [operátor příkazu](../../../language-reference/statements/operator-statement.md).

## <a name="calling-syntax"></a>Syntaxe volání

Proceduru operátoru můžete implicitně vyvolat pomocí symbolu operátoru ve výrazu. Operandy zadáte stejným způsobem jako předdefinované operátory.

Syntaxe pro implicitní volání procedury operátoru je následující:

`Dim testStruct As`  *StructureName*

`Dim testNewStruct As`  *Struktura* `= testStruct` *operatorsymbol*      `10`

### <a name="illustration-of-declaration-and-call"></a>Ilustrace deklarace a volání

Následující struktura ukládá znaménko celé číslo se znaménkem 128 jako části s horním a dolním pořadím. Definuje `+` operátor pro přidání dvou `veryLong` hodnot a vygenerování výsledné `veryLong` hodnoty.

[!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]

Následující příklad ukazuje typické volání `+` operátoru definovaného na `veryLong` .

[!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]

## <a name="see-also"></a>Viz také

- [Procedury](./index.md)
- [Procedury Sub](./sub-procedures.md)
- [Procedury funkcí](./function-procedures.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Operator – příkaz](../../../language-reference/statements/operator-statement.md)
- [Postupy: Definice operátoru](./how-to-define-an-operator.md)
- [Postupy: Definice operátoru převodu](./how-to-define-a-conversion-operator.md)
- [Postupy: Volání procedury operátoru](./how-to-call-an-operator-procedure.md)
- [Postupy: Použití třídy, která definuje operátory](./how-to-use-a-class-that-defines-operators.md)
