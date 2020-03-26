---
title: Operand 'IsNot' typu 'typename' lze porovnat pouze s hodnotou 'Nothing', protože 'typename' je typ s povolenou hodnotou Null.
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: 1660971e2a1a11d7a2d14f222cd149edf4aa4c7b
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249510"
---
# <a name="isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a><span data-ttu-id="62576-102">Operand 'IsNot' typu 'typename' lze porovnat pouze s hodnotou 'Nothing', protože 'typename' je typ s povolenou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="62576-102">'IsNot' operand of type 'typename' can only be compared to 'Nothing', because 'typename' is a nullable type</span></span>

<span data-ttu-id="62576-103">Proměnná deklarovaná jako typ hodnoty s možnou `Nothing` hodnotou s možnou hodnotou null byla porovnána s jiným výrazem než s použitím operátoru. `IsNot`</span><span class="sxs-lookup"><span data-stu-id="62576-103">A variable declared as a nullable value type has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>

<span data-ttu-id="62576-104">**ID chyby:** BC32128</span><span class="sxs-lookup"><span data-stu-id="62576-104">**Error ID:** BC32128</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="62576-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="62576-105">To correct this error</span></span>

<span data-ttu-id="62576-106">Chcete-li porovnat typ s možnou hodnotou null s jiným výrazem než `Nothing` pomocí operátoru, `IsNot` zavolejte metodu `GetType` na typ s možnou hodnotou null a porovnejte výsledek s výrazem, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="62576-106">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>

```vb
Dim number? As Integer = 5

If number IsNot Nothing Then
  If number.GetType() IsNot Type.GetType("System.Int32") Then

  End If
End If
```

## <a name="see-also"></a><span data-ttu-id="62576-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="62576-107">See also</span></span>

- [<span data-ttu-id="62576-108">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="62576-108">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="62576-109">Operátor IsNot</span><span class="sxs-lookup"><span data-stu-id="62576-109">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
