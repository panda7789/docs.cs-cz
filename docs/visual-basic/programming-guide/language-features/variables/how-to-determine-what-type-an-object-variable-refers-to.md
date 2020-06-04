---
title: 'Postupy: Určení, na jaký typ proměnná objektu odkazuje'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: d3224000f5958a8619e38c4d2f6dc5dbb275ad45
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410487"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>Postupy: Určení, na jaký typ proměnná objektu odkazuje (Visual Basic)

Proměnná objektu obsahuje ukazatel na data, která jsou uložená jinde. Typ těchto dat se může během běhu změnit. V každém okamžiku můžete použít <xref:System.Type.GetTypeCode%2A> metodu k určení aktuálního typu za běhu nebo [operátora typeof](../../../language-reference/operators/typeof-operator.md) k zjištění, zda je aktuální typ běhu kompatibilní se zadaným typem.

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>Určení přesného typu, na který aktuálně odkazuje proměnná objektu

1. Na objektovou proměnnou volejte <xref:System.Object.GetType%2A> metodu pro načtení <xref:System.Type?displayProperty=nameWithType> objektu.

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. U <xref:System.Type?displayProperty=nameWithType> třídy zavolejte sdílenou metodu <xref:System.Type.GetTypeCode%2A> pro načtení <xref:System.TypeCode> hodnoty výčtu pro typ objektu.

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    Můžete otestovat <xref:System.TypeCode> hodnotu výčtu na základě toho, co členové výčtu mají zájem, například `Double` .

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>Určení, zda je typ objektové proměnné kompatibilní se zadaným typem

- Použijte `TypeOf` operátor v kombinaci s [operátorem is](../../../language-reference/operators/is-operator.md) k otestování objektu pomocí `TypeOf` výrazu.... `Is`

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    `TypeOf`Výraz... `Is` vrátí, `True` Pokud je typ modulu runtime objektu kompatibilní se zadaným typem.

    Kritérium kompatibility závisí na tom, zda je zadaný typ třída, struktura nebo rozhraní. Obecně jsou typy kompatibilní, pokud je objekt stejného typu jako, dědí z nebo implementuje zadaný typ. Další informace naleznete v tématu [operátor typeof](../../../language-reference/operators/typeof-operator.md).

## <a name="compile-the-code"></a>Kompilovat kód

Všimněte si, že zadaný typ nemůže být proměnná nebo výraz. Musí se jednat o název definovaného typu, jako je například třída, struktura nebo rozhraní. To zahrnuje vnitřní typy, jako jsou `Integer` a `String` .

## <a name="see-also"></a>Viz také

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [Proměnné objektu](object-variables.md)
- [Hodnoty proměnné objektu](object-variable-values.md)
- [Datový typ objektu](../../../language-reference/data-types/object-data-type.md)
