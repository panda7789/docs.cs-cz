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

Můžete porovnat dva objekty a určit vztah, pokud existuje, mezi třídami, ze kterých jsou vytvořeny. Metoda <xref:System.Type.IsInstanceOfType%2A> třídy <xref:System.Type?displayProperty=nameWithType> vrátí `True`, pokud zadaná třída dědí z aktuální třídy, nebo pokud aktuální typ je rozhraní podporované zadanou třídou.

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>Určení, zda jeden objekt dědí z jiného objektu nebo třídy nebo rozhraní

1. U objektu, který si myslíte, může být základní typ, vyvolat metodu <xref:System.Object.GetType%2A>.

2. U objektu <xref:System.Type?displayProperty=nameWithType> vráceného <xref:System.Object.GetType%2A>volejte metodu <xref:System.Type.IsInstanceOfType%2A>.

3. V seznamu argumentů pro <xref:System.Type.IsInstanceOfType%2A>určete objekt, který si myslíte, může být odvozený typ.

    <xref:System.Type.IsInstanceOfType%2A> vrátí `True`, pokud jeho typ argumentu dědí z typu objektu <xref:System.Type?displayProperty=nameWithType>.

## <a name="example"></a>Příklad
 Následující příklad určuje, zda jeden objekt představuje třídu odvozenou z jiného objektu třídy.

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

Všimněte si neočekávaného umístění dvou objektových proměnných při volání <xref:System.Type.IsInstanceOfType%2A>. Předpokládaný základní typ se používá ke generování <xref:System.Type?displayProperty=nameWithType> třídy a předpokládaný odvozený typ je předán jako argument metodě <xref:System.Type.IsInstanceOfType%2A>.

## <a name="see-also"></a>Viz také:

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Hodnoty objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Postupy: Určení, zda dva objekty jsou identické](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
