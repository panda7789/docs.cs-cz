---
title: Operand 'IsNot' typu 'typename' lze porovnat pouze s hodnotou 'Nothing', protože 'typename' je typ s povolenou hodnotou Null.
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: fb61b04021bd844fade94413b4f3b28b82f6411b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402795"
---
# <a name="isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a>Operand 'IsNot' typu 'typename' lze porovnat pouze s hodnotou 'Nothing', protože 'typename' je typ s povolenou hodnotou Null.

Proměnná deklarovaná jako typ hodnoty s možnou hodnotou null byla porovnána s výrazem jiným než `Nothing` použití `IsNot` operátoru.

**ID chyby:** BC32128

## <a name="to-correct-this-error"></a>Oprava této chyby

Chcete-li porovnat typ s možnou hodnotou null na jiný výraz než pomocí `Nothing` `IsNot` operátoru, zavolejte `GetType` metodu u typu s možnou hodnotou null a porovnejte výsledek s výrazem, jak je znázorněno v následujícím příkladu.

```vb
Dim number? As Integer = 5

If number IsNot Nothing Then
  If number.GetType() IsNot Type.GetType("System.Int32") Then

  End If
End If
```

## <a name="see-also"></a>Viz také

- [Typy hodnot s možnou hodnotou null](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [IsNot – operátor](../operators/isnot-operator.md)
