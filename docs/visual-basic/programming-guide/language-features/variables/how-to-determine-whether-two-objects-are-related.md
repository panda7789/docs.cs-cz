---
title: 'Postupy: Určení, zda dva objekty souvisejí (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: f59e00d80d28fc4bf24874d25b5c12643649c834
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769067"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>Postupy: Určení, zda dva objekty souvisejí (Visual Basic)
Můžete porovnat dva objekty, určit vztah, pokud existuje mezi třídami, ze které se vytvářejí. <xref:System.Type.IsInstanceOfType%2A> Metodu <xref:System.Type?displayProperty=nameWithType> třídy vrátí `True` Pokud zadaná třída dědí ze třídy aktuální, nebo pokud aktuální typ je rozhraní nepodporuje zadanou třídu.  
  
### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>Chcete-li zjistit, pokud jeden objekt dědí z třídy nebo rozhraní jiného objektu.  
  
1. U objektu si myslíte, že může být základního typu, vyvolají <xref:System.Object.GetType%2A> metody.  
  
2. Na <xref:System.Type?displayProperty=nameWithType> vrácený <xref:System.Object.GetType%2A>, vyvolat <xref:System.Type.IsInstanceOfType%2A> metody.  
  
3. V seznamu argumentů pro <xref:System.Type.IsInstanceOfType%2A>, zadejte objekt si myslíte, že může být odvozeného typu.  
  
     <xref:System.Type.IsInstanceOfType%2A> Vrátí `True` pokud její argument typ dědí z <xref:System.Type?displayProperty=nameWithType> typ objektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad určuje, zda jeden objekt představuje třídu odvozenou z třídy jiného objektu.  
  
```  
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
  
 Poznámka: Neočekávaná umístění dvou objektů proměnné ve volání <xref:System.Type.IsInstanceOfType%2A>. Předpokládaný základní typ se používá ke generování <xref:System.Type?displayProperty=nameWithType> třídy a předpokládaný odvozený typ je předán jako argument <xref:System.Type.IsInstanceOfType%2A> metody.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Hodnoty objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Postupy: Určení, zda dva objekty jsou identické](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
