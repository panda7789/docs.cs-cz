---
title: 'Postupy: Určení, zda dva objekty souvisejí.'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: b3f5fc017166ba9cf28359db5de850c81b73bd69
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348633"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>Postupy: Určení, zda dva objekty souvisejí (Visual Basic)

You can compare two objects to determine the relationship, if any, between the classes from which they are created. The <xref:System.Type.IsInstanceOfType%2A> method of the <xref:System.Type?displayProperty=nameWithType> class returns `True` if the specified class inherits from the current class, or if the current type is an interface supported by the specified class.

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>To determine if one object inherits from another object's class or interface

1. On the object you think might be of the base type, invoke the <xref:System.Object.GetType%2A> method.

2. On the <xref:System.Type?displayProperty=nameWithType> object returned by <xref:System.Object.GetType%2A>, invoke the <xref:System.Type.IsInstanceOfType%2A> method.

3. In the argument list for <xref:System.Type.IsInstanceOfType%2A>, specify the object you think might be of the derived type.

    <xref:System.Type.IsInstanceOfType%2A> returns `True` if its argument type inherits from the <xref:System.Type?displayProperty=nameWithType> object type.

## <a name="example"></a>Příklad
 The following example determines whether one object represents a class derived from another object's class.

```vb
Public Class baseClass
End Class
Public Class derivedClass : Inherits baseClass
End Class
Public Class testTheseClasses
    Public Sub seeIfRelated()
        Dim baseObj As Object = New baseClass()
        Dim derivedObj As Object = New derivedClass()
        Dim related As Boolean
        related = baseObj.GetType().IsInstanceOfType(derivedObj)
        MsgBox(CStr(related))
    End Sub
End Class
```

Note the unexpected placement of the two object variables in the call to <xref:System.Type.IsInstanceOfType%2A>. The supposed base type is used to generate the <xref:System.Type?displayProperty=nameWithType> class, and the supposed derived type is passed as an argument to the <xref:System.Type.IsInstanceOfType%2A> method.

## <a name="see-also"></a>Viz také:

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Hodnoty objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Postupy: Určení, zda dva objekty jsou identické](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
