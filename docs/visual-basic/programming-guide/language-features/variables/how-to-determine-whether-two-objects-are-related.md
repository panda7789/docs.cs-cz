---
title: 'Postupy: Určení, zda dva objekty souvisejí (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: 2041f89ffd954e479046eb85c6dd82de1f8793ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649822"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>Postupy: Určení, zda dva objekty souvisejí (Visual Basic)
K určení relace, pokud existuje, mezi třídami, ze kterých jsou vytvořeny dva objekty, můžete porovnat. <xref:System.Type.IsInstanceOfType%2A> Metodu <xref:System.Type?displayProperty=nameWithType> vrací `True` Pokud pro zadanou třídu dědí z aktuální třídy, nebo pokud je aktuální typ rozhraní nepodporuje zadanou třídu.  
  
### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>Chcete-li zjistit, pokud se jeden objekt dědí z třídy nebo rozhraní jiného objektu.  
  
1.  Na objekt domníváte, že může být základní typ, vyvolání <xref:System.Object.GetType%2A> metoda.  
  
2.  Na <xref:System.Type?displayProperty=nameWithType> objekt vrácený <xref:System.Object.GetType%2A>, vyvolání <xref:System.Type.IsInstanceOfType%2A> metoda.  
  
3.  V seznamu argumentů pro <xref:System.Type.IsInstanceOfType%2A>, zadejte objekt domníváte, že může být odvozený typ.  
  
     <xref:System.Type.IsInstanceOfType%2A> Vrátí `True` pokud její argument typ dědí od <xref:System.Type?displayProperty=nameWithType> typ objektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad určuje, zda představuje jeden objekt třídy odvozené od třídy jiný objekt.  
  
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
  
 Všimněte si neočekávané umístění dvou objektů proměnných ve volání <xref:System.Type.IsInstanceOfType%2A>. Předpokládané základní typ se používá ke generování <xref:System.Type?displayProperty=nameWithType> třídy a předpokládané odvozený typ je předat jako argument k <xref:System.Type.IsInstanceOfType%2A> metoda.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Object.GetType%2A>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Type.IsInstanceOfType%2A>  
 [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Hodnoty objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Postupy: Určení, zda dva objekty jsou identické](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
