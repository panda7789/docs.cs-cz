---
title: 'Postupy: Určete, na jaký typ proměnná objektu odkazuje (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 935623dd4b6edca188f932aca0e560130199e8f6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626566"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>Postupy: Určete, na jaký typ proměnná objektu odkazuje (Visual Basic)

Proměnná objektu obsahuje ukazatel na data, která jsou uložená jinde. Typ těchto dat se může během běhu změnit. V každém okamžiku můžete použít <xref:System.Type.GetTypeCode%2A> metodu k určení aktuálního typu za běhu nebo operátora [typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md) k zjištění, zda je aktuální typ běhu kompatibilní se zadaným typem.

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>Určení přesného typu, na který aktuálně odkazuje proměnná objektu

1. Na objektovou proměnnou volejte <xref:System.Object.GetType%2A> metodu pro <xref:System.Type?displayProperty=nameWithType> načtení objektu.

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. U třídy zavolejte sdílenou metodu <xref:System.Type.GetTypeCode%2A> pro načtení <xref:System.TypeCode> hodnoty výčtu pro typ objektu. <xref:System.Type?displayProperty=nameWithType>

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    Můžete otestovat hodnotu výčtu <xref:System.TypeCode> na základě toho, co členové výčtu mají zájem, `Double`například.

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>Určení, zda je typ objektové proměnné kompatibilní se zadaným typem

- Použijte operátor v kombinaci s operátorem [is](../../../../visual-basic/language-reference/operators/is-operator.md) k otestování objektu s `TypeOf`... `TypeOf` `Is` výraz.

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    `TypeOf`... `Is` výraz vrátí`True` , pokud je typ modulu runtime objektu kompatibilní se zadaným typem.

    Kritérium kompatibility závisí na tom, zda je zadaný typ třída, struktura nebo rozhraní. Obecně jsou typy kompatibilní, pokud je objekt stejného typu jako, dědí z nebo implementuje zadaný typ. Další informace naleznete v tématu [operátor typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md).

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Všimněte si, že zadaný typ nemůže být proměnná nebo výraz. Musí se jednat o název definovaného typu, jako je například třída, struktura nebo rozhraní. To zahrnuje vnitřní typy, jako `Integer` jsou `String`a.

## <a name="see-also"></a>Viz také:

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Hodnoty objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
