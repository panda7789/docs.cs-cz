---
title: NameOf – operátor Visual Basic
description: Naučte se používat operátor NameOf v Visual Basic
ms.date: 10/27/2019
helpviewer_keywords:
- NameOf operator [Visual Basic]
ms.openlocfilehash: 8416bb1a1715c1c37b62cac6a9e0b427a9c72547
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041315"
---
# <a name="nameof-operator---visual-basic"></a>NameOf – operátor Visual Basic

Operátor `NameOf` Získá název proměnné, typu nebo členu jako řetězcové konstanty:

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

Jak ukazuje předchozí příklad, v případě typu a oboru názvů není vytvořen název obvykle [plně kvalifikovaný](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

Operátor `NameOf` je vyhodnocen v době kompilace a nemá žádný vliv na dobu běhu.

Operátor `NameOf` lze použít k zajištění udržovatelnosti kódu pro kontrolu argumentu:

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

Operátor `NameOf` je k dispozici v Visual Basic 14 a novějších.

## <a name="see-also"></a>Viz také:

- [Referenční příručka jazyka Visual Basic](../index.md)
- [Operátory (Visual Basic)](index.md)
