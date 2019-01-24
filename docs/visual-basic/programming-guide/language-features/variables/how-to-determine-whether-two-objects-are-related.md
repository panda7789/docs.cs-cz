---
title: 'Postupy: Určení, zda dva objekty souvisejí (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: 62c0280e3773d2e3ff15bc164d9e0e6cacb7bd4d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544585"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a><span data-ttu-id="ef3e1-102">Postupy: Určení, zda dva objekty souvisejí (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef3e1-102">How to: Determine Whether Two Objects Are Related (Visual Basic)</span></span>
<span data-ttu-id="ef3e1-103">Můžete porovnat dva objekty, určit vztah, pokud existuje mezi třídami, ze které se vytvářejí.</span><span class="sxs-lookup"><span data-stu-id="ef3e1-103">You can compare two objects to determine the relationship, if any, between the classes from which they are created.</span></span> <span data-ttu-id="ef3e1-104"><xref:System.Type.IsInstanceOfType%2A> Metodu <xref:System.Type?displayProperty=nameWithType> třídy vrátí `True` Pokud zadaná třída dědí ze třídy aktuální, nebo pokud aktuální typ je rozhraní nepodporuje zadanou třídu.</span><span class="sxs-lookup"><span data-stu-id="ef3e1-104">The <xref:System.Type.IsInstanceOfType%2A> method of the <xref:System.Type?displayProperty=nameWithType> class returns `True` if the specified class inherits from the current class, or if the current type is an interface supported by the specified class.</span></span>  
  
### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a><span data-ttu-id="ef3e1-105">Chcete-li zjistit, pokud jeden objekt dědí z třídy nebo rozhraní jiného objektu.</span><span class="sxs-lookup"><span data-stu-id="ef3e1-105">To determine if one object inherits from another object's class or interface</span></span>  
  
1.  <span data-ttu-id="ef3e1-106">U objektu si myslíte, že může být základního typu, vyvolají <xref:System.Object.GetType%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ef3e1-106">On the object you think might be of the base type, invoke the <xref:System.Object.GetType%2A> method.</span></span>  
  
2.  <span data-ttu-id="ef3e1-107">Na <xref:System.Type?displayProperty=nameWithType> vrácený <xref:System.Object.GetType%2A>, vyvolat <xref:System.Type.IsInstanceOfType%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ef3e1-107">On the <xref:System.Type?displayProperty=nameWithType> object returned by <xref:System.Object.GetType%2A>, invoke the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>  
  
3.  <span data-ttu-id="ef3e1-108">V seznamu argumentů pro <xref:System.Type.IsInstanceOfType%2A>, zadejte objekt si myslíte, že může být odvozeného typu.</span><span class="sxs-lookup"><span data-stu-id="ef3e1-108">In the argument list for <xref:System.Type.IsInstanceOfType%2A>, specify the object you think might be of the derived type.</span></span>  
  
     <span data-ttu-id="ef3e1-109"><xref:System.Type.IsInstanceOfType%2A> Vrátí `True` pokud její argument typ dědí z <xref:System.Type?displayProperty=nameWithType> typ objektu.</span><span class="sxs-lookup"><span data-stu-id="ef3e1-109"><xref:System.Type.IsInstanceOfType%2A> returns `True` if its argument type inherits from the <xref:System.Type?displayProperty=nameWithType> object type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef3e1-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef3e1-110">Example</span></span>  
 <span data-ttu-id="ef3e1-111">Následující příklad určuje, zda jeden objekt představuje třídu odvozenou z třídy jiného objektu.</span><span class="sxs-lookup"><span data-stu-id="ef3e1-111">The following example determines whether one object represents a class derived from another object's class.</span></span>  
  
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
  
 <span data-ttu-id="ef3e1-112">Poznámka: Neočekávaná umístění dvou objektů proměnné ve volání <xref:System.Type.IsInstanceOfType%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef3e1-112">Note the unexpected placement of the two object variables in the call to <xref:System.Type.IsInstanceOfType%2A>.</span></span> <span data-ttu-id="ef3e1-113">Předpokládaný základní typ se používá ke generování <xref:System.Type?displayProperty=nameWithType> třídy a předpokládaný odvozený typ je předán jako argument <xref:System.Type.IsInstanceOfType%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ef3e1-113">The supposed base type is used to generate the <xref:System.Type?displayProperty=nameWithType> class, and the supposed derived type is passed as an argument to the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef3e1-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef3e1-114">See also</span></span>
- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [<span data-ttu-id="ef3e1-115">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="ef3e1-115">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="ef3e1-116">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="ef3e1-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="ef3e1-117">Hodnoty objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="ef3e1-117">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="ef3e1-118">Postupy: Určení, zda dva objekty jsou identické</span><span class="sxs-lookup"><span data-stu-id="ef3e1-118">How to: Determine Whether Two Objects Are Identical</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
