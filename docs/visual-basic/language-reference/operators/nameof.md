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
