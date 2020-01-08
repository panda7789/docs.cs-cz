---
title: NameOf – operátor
description: Naučte se používat operátor NameOf v Visual Basic
ms.date: 10/27/2019
helpviewer_keywords:
- NameOf operator [Visual Basic]
ms.openlocfilehash: e7dd55bfd98b34449b9f1a35375198598f57b46f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347020"
---
# <a name="nameof-operator---visual-basic"></a><span data-ttu-id="1527b-103">NameOf – operátor Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1527b-103">NameOf operator - Visual Basic</span></span>

<span data-ttu-id="1527b-104">Operátor `NameOf` Získá název proměnné, typu nebo členu jako řetězcové konstanty:</span><span class="sxs-lookup"><span data-stu-id="1527b-104">The `NameOf` operator obtains the name of a variable, type, or member as the string constant:</span></span>

```vb
Console.WriteLine(NameOf(System.Collections.Generic))  ' output: Generic
Console.WriteLine(NameOf(List(Of Integer)))  ' output: List
Console.WriteLine(NameOf(List(Of Integer).Count))  ' output: Count
Console.WriteLine(NameOf(List(Of Integer).Add))  ' output: Add

Dim numbers As New List(Of Integer) From { 1, 2, 3 }
Console.WriteLine(NameOf(numbers))  ' output: numbers
Console.WriteLine(NameOf(numbers.Count))  ' output: Count
Console.WriteLine(NameOf(numbers.Add))  ' output: Add
```

<span data-ttu-id="1527b-105">Jak ukazuje předchozí příklad, v případě typu a oboru názvů není vytvořen název obvykle [plně kvalifikovaný](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="1527b-105">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="1527b-106">Operátor `NameOf` je vyhodnocen v době kompilace a nemá žádný vliv na dobu běhu.</span><span class="sxs-lookup"><span data-stu-id="1527b-106">The `NameOf` operator is evaluated at compile time, and has no effect at run time.</span></span>

<span data-ttu-id="1527b-107">Operátor `NameOf` lze použít k zajištění udržovatelnosti kódu pro kontrolu argumentu:</span><span class="sxs-lookup"><span data-stu-id="1527b-107">You can use the `NameOf` operator to make the argument-checking code more maintainable:</span></span>

```vb
Private _name As String

Public Property Name As String
    Get
        Return _name
    End Get
    Set
        If value Is Nothing Then
            Throw New ArgumentNullException(NameOf(value), $"{NameOf(name)} cannot be null.")
        End If
    End Set
End Property
```

<span data-ttu-id="1527b-108">Operátor `NameOf` je k dispozici v Visual Basic 14 a novějších.</span><span class="sxs-lookup"><span data-stu-id="1527b-108">The `NameOf` operator is available in Visual Basic 14 and later.</span></span>

## <a name="see-also"></a><span data-ttu-id="1527b-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1527b-109">See also</span></span>

- [<span data-ttu-id="1527b-110">Referenční příručka jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1527b-110">Visual Basic Language Reference</span></span>](../index.md)
- [<span data-ttu-id="1527b-111">Operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1527b-111">Operators (Visual Basic)</span></span>](index.md)
