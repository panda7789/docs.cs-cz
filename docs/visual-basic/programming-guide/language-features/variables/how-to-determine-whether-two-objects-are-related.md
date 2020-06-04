---
title: 'Postupy: Určení, zda dva objekty souvisejí.'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: 30e88a21e737aa57513745899577381ed34151a2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410461"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>Postupy: Určení, zda dva objekty souvisejí (Visual Basic)

Můžete porovnat dva objekty a určit vztah, pokud existuje, mezi třídami, ze kterých jsou vytvořeny. <xref:System.Type.IsInstanceOfType%2A>Metoda <xref:System.Type?displayProperty=nameWithType> třídy vrací `True` , pokud zadaná třída dědí z aktuální třídy, nebo pokud je aktuální typ rozhraní podporované zadanou třídou.

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>Určení, zda jeden objekt dědí z jiného objektu nebo třídy nebo rozhraní

1. U objektu, který si myslíte, může být základní typ, vyvolat <xref:System.Object.GetType%2A> metodu.

2. U <xref:System.Type?displayProperty=nameWithType> objektu vráceného metodou <xref:System.Object.GetType%2A> volejte <xref:System.Type.IsInstanceOfType%2A> metodu.

3. V seznamu argumentů pro <xref:System.Type.IsInstanceOfType%2A> Zadejte objekt, který si myslíte, může být odvozený typ.

    <xref:System.Type.IsInstanceOfType%2A>Vrátí `True` , zda typ argumentu dědí z <xref:System.Type?displayProperty=nameWithType> typu objektu.

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

Všimněte si neočekávaného umístění dvou objektových proměnných v volání <xref:System.Type.IsInstanceOfType%2A> . Předpokládaný základní typ se používá ke generování <xref:System.Type?displayProperty=nameWithType> třídy a předpokládaný odvozený typ je předán jako argument <xref:System.Type.IsInstanceOfType%2A> metody.

## <a name="see-also"></a>Viz také

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [Datový typ objektu](../../../language-reference/data-types/object-data-type.md)
- [Proměnné objektu](object-variables.md)
- [Hodnoty proměnné objektu](object-variable-values.md)
- [Postupy: Určení, zda dva objekty jsou identické](how-to-determine-whether-two-objects-are-identical.md)
