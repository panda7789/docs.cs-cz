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
# <a name="isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a><span data-ttu-id="1d6a8-102">Operand 'IsNot' typu 'typename' lze porovnat pouze s hodnotou 'Nothing', protože 'typename' je typ s povolenou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="1d6a8-102">'IsNot' operand of type 'typename' can only be compared to 'Nothing', because 'typename' is a nullable type</span></span>

<span data-ttu-id="1d6a8-103">Proměnná deklarovaná jako typ hodnoty s možnou hodnotou null byla porovnána s výrazem jiným než `Nothing` použití `IsNot` operátoru.</span><span class="sxs-lookup"><span data-stu-id="1d6a8-103">A variable declared as a nullable value type has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>

<span data-ttu-id="1d6a8-104">**ID chyby:** BC32128</span><span class="sxs-lookup"><span data-stu-id="1d6a8-104">**Error ID:** BC32128</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="1d6a8-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="1d6a8-105">To correct this error</span></span>

<span data-ttu-id="1d6a8-106">Chcete-li porovnat typ s možnou hodnotou null na jiný výraz než pomocí `Nothing` `IsNot` operátoru, zavolejte `GetType` metodu u typu s možnou hodnotou null a porovnejte výsledek s výrazem, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1d6a8-106">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>

```vb
Dim number? As Integer = 5

If number IsNot Nothing Then
  If number.GetType() IsNot Type.GetType("System.Int32") Then

  End If
End If
```

## <a name="see-also"></a><span data-ttu-id="1d6a8-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d6a8-107">See also</span></span>

- [<span data-ttu-id="1d6a8-108">Typy hodnot s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="1d6a8-108">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="1d6a8-109">IsNot – operátor</span><span class="sxs-lookup"><span data-stu-id="1d6a8-109">IsNot Operator</span></span>](../operators/isnot-operator.md)
