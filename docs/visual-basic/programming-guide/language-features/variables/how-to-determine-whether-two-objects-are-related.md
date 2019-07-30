---
title: 'Postupy: Určení, zda dva objekty souvisejí (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: 2b17be4ef5a7dabfc4779ab6f5675cc2baec9c3c
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626564"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>Postupy: Určení, zda dva objekty souvisejí (Visual Basic)

Můžete porovnat dva objekty a určit vztah, pokud existuje, mezi třídami, ze kterých jsou vytvořeny. <xref:System.Type.IsInstanceOfType%2A> Metoda třídy<xref:System.Type?displayProperty=nameWithType> vrací ,pokudzadanátřídadědízaktuálnítřídy,nebopokudje`True` aktuální typ rozhraní podporované zadanou třídou.

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>Určení, zda jeden objekt dědí z jiného objektu nebo třídy nebo rozhraní

1. U objektu, který si myslíte, může být základní typ, vyvolat <xref:System.Object.GetType%2A> metodu.

2. U objektu vráceného metodou volejte <xref:System.Type.IsInstanceOfType%2A>metodu. <xref:System.Object.GetType%2A> <xref:System.Type?displayProperty=nameWithType>

3. V seznamu argumentů pro <xref:System.Type.IsInstanceOfType%2A>zadejte objekt, který si myslíte, může být odvozený typ.

    <xref:System.Type.IsInstanceOfType%2A>Vrátí `True` , zda typ argumentu dědí <xref:System.Type?displayProperty=nameWithType> z typu objektu.

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

Všimněte si neočekávaného umístění dvou objektových proměnných v volání <xref:System.Type.IsInstanceOfType%2A>. Předpokládaný základní typ se používá ke generování <xref:System.Type?displayProperty=nameWithType> třídy a předpokládaný odvozený typ je předán jako argument <xref:System.Type.IsInstanceOfType%2A> metody.

## <a name="see-also"></a>Viz také:

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Hodnoty objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Postupy: Určení, zda jsou dva objekty identické](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
