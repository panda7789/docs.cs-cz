---
title: "Postupy: Určení, zda dva objekty souvisejí (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7824742459fca355c0043ad8ed20a26330402c05
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a><span data-ttu-id="76219-102">Postupy: Určení, zda dva objekty souvisejí (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76219-102">How to: Determine Whether Two Objects Are Related (Visual Basic)</span></span>
<span data-ttu-id="76219-103">K určení relace, pokud existuje, mezi třídami, ze kterých jsou vytvořeny dva objekty, můžete porovnat.</span><span class="sxs-lookup"><span data-stu-id="76219-103">You can compare two objects to determine the relationship, if any, between the classes from which they are created.</span></span> <span data-ttu-id="76219-104"><xref:System.Type.IsInstanceOfType%2A> Metodu <xref:System.Type?displayProperty=nameWithType> vrací `True` Pokud pro zadanou třídu dědí z aktuální třídy, nebo pokud je aktuální typ rozhraní nepodporuje zadanou třídu.</span><span class="sxs-lookup"><span data-stu-id="76219-104">The <xref:System.Type.IsInstanceOfType%2A> method of the <xref:System.Type?displayProperty=nameWithType> class returns `True` if the specified class inherits from the current class, or if the current type is an interface supported by the specified class.</span></span>  
  
### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a><span data-ttu-id="76219-105">Chcete-li zjistit, pokud se jeden objekt dědí z třídy nebo rozhraní jiného objektu.</span><span class="sxs-lookup"><span data-stu-id="76219-105">To determine if one object inherits from another object's class or interface</span></span>  
  
1.  <span data-ttu-id="76219-106">Na objekt domníváte, že může být základní typ, vyvolání <xref:System.Object.GetType%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="76219-106">On the object you think might be of the base type, invoke the <xref:System.Object.GetType%2A> method.</span></span>  
  
2.  <span data-ttu-id="76219-107">Na <xref:System.Type?displayProperty=nameWithType> objekt vrácený <xref:System.Object.GetType%2A>, vyvolání <xref:System.Type.IsInstanceOfType%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="76219-107">On the <xref:System.Type?displayProperty=nameWithType> object returned by <xref:System.Object.GetType%2A>, invoke the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>  
  
3.  <span data-ttu-id="76219-108">V seznamu argumentů pro <xref:System.Type.IsInstanceOfType%2A>, zadejte objekt domníváte, že může být odvozený typ.</span><span class="sxs-lookup"><span data-stu-id="76219-108">In the argument list for <xref:System.Type.IsInstanceOfType%2A>, specify the object you think might be of the derived type.</span></span>  
  
     <span data-ttu-id="76219-109"><xref:System.Type.IsInstanceOfType%2A>Vrátí `True` pokud její argument typ dědí od <xref:System.Type?displayProperty=nameWithType> typ objektu.</span><span class="sxs-lookup"><span data-stu-id="76219-109"><xref:System.Type.IsInstanceOfType%2A> returns `True` if its argument type inherits from the <xref:System.Type?displayProperty=nameWithType> object type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76219-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="76219-110">Example</span></span>  
 <span data-ttu-id="76219-111">Následující příklad určuje, zda představuje jeden objekt třídy odvozené od třídy jiný objekt.</span><span class="sxs-lookup"><span data-stu-id="76219-111">The following example determines whether one object represents a class derived from another object's class.</span></span>  
  
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
  
 <span data-ttu-id="76219-112">Všimněte si neočekávané umístění dvou objektů proměnných ve volání <xref:System.Type.IsInstanceOfType%2A>.</span><span class="sxs-lookup"><span data-stu-id="76219-112">Note the unexpected placement of the two object variables in the call to <xref:System.Type.IsInstanceOfType%2A>.</span></span> <span data-ttu-id="76219-113">Předpokládané základní typ se používá ke generování <xref:System.Type?displayProperty=nameWithType> třídy a předpokládané odvozený typ je předat jako argument k <xref:System.Type.IsInstanceOfType%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="76219-113">The supposed base type is used to generate the <xref:System.Type?displayProperty=nameWithType> class, and the supposed derived type is passed as an argument to the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76219-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="76219-114">See Also</span></span>  
 <xref:System.Object.GetType%2A>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Type.IsInstanceOfType%2A>  
 [<span data-ttu-id="76219-115">Object – datový typ</span><span class="sxs-lookup"><span data-stu-id="76219-115">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="76219-116">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="76219-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="76219-117">Hodnoty proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="76219-117">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [<span data-ttu-id="76219-118">Postupy: určení, zda dva objekty jsou identické</span><span class="sxs-lookup"><span data-stu-id="76219-118">How to: Determine Whether Two Objects Are Identical</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
