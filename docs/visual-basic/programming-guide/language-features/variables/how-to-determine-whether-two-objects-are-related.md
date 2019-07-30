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
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a><span data-ttu-id="ca56e-102">Postupy: Určení, zda dva objekty souvisejí (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca56e-102">How to: Determine Whether Two Objects Are Related (Visual Basic)</span></span>

<span data-ttu-id="ca56e-103">Můžete porovnat dva objekty a určit vztah, pokud existuje, mezi třídami, ze kterých jsou vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="ca56e-103">You can compare two objects to determine the relationship, if any, between the classes from which they are created.</span></span> <span data-ttu-id="ca56e-104"><xref:System.Type.IsInstanceOfType%2A> Metoda třídy<xref:System.Type?displayProperty=nameWithType> vrací ,pokudzadanátřídadědízaktuálnítřídy,nebopokudje`True` aktuální typ rozhraní podporované zadanou třídou.</span><span class="sxs-lookup"><span data-stu-id="ca56e-104">The <xref:System.Type.IsInstanceOfType%2A> method of the <xref:System.Type?displayProperty=nameWithType> class returns `True` if the specified class inherits from the current class, or if the current type is an interface supported by the specified class.</span></span>

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a><span data-ttu-id="ca56e-105">Určení, zda jeden objekt dědí z jiného objektu nebo třídy nebo rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca56e-105">To determine if one object inherits from another object's class or interface</span></span>

1. <span data-ttu-id="ca56e-106">U objektu, který si myslíte, může být základní typ, vyvolat <xref:System.Object.GetType%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="ca56e-106">On the object you think might be of the base type, invoke the <xref:System.Object.GetType%2A> method.</span></span>

2. <span data-ttu-id="ca56e-107">U objektu vráceného metodou volejte <xref:System.Type.IsInstanceOfType%2A>metodu. <xref:System.Object.GetType%2A> <xref:System.Type?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ca56e-107">On the <xref:System.Type?displayProperty=nameWithType> object returned by <xref:System.Object.GetType%2A>, invoke the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>

3. <span data-ttu-id="ca56e-108">V seznamu argumentů pro <xref:System.Type.IsInstanceOfType%2A>zadejte objekt, který si myslíte, může být odvozený typ.</span><span class="sxs-lookup"><span data-stu-id="ca56e-108">In the argument list for <xref:System.Type.IsInstanceOfType%2A>, specify the object you think might be of the derived type.</span></span>

    <span data-ttu-id="ca56e-109"><xref:System.Type.IsInstanceOfType%2A>Vrátí `True` , zda typ argumentu dědí <xref:System.Type?displayProperty=nameWithType> z typu objektu.</span><span class="sxs-lookup"><span data-stu-id="ca56e-109"><xref:System.Type.IsInstanceOfType%2A> returns `True` if its argument type inherits from the <xref:System.Type?displayProperty=nameWithType> object type.</span></span>

## <a name="example"></a><span data-ttu-id="ca56e-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="ca56e-110">Example</span></span>
 <span data-ttu-id="ca56e-111">Následující příklad určuje, zda jeden objekt představuje třídu odvozenou z jiného objektu třídy.</span><span class="sxs-lookup"><span data-stu-id="ca56e-111">The following example determines whether one object represents a class derived from another object's class.</span></span>

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

<span data-ttu-id="ca56e-112">Všimněte si neočekávaného umístění dvou objektových proměnných v volání <xref:System.Type.IsInstanceOfType%2A>.</span><span class="sxs-lookup"><span data-stu-id="ca56e-112">Note the unexpected placement of the two object variables in the call to <xref:System.Type.IsInstanceOfType%2A>.</span></span> <span data-ttu-id="ca56e-113">Předpokládaný základní typ se používá ke generování <xref:System.Type?displayProperty=nameWithType> třídy a předpokládaný odvozený typ je předán jako argument <xref:System.Type.IsInstanceOfType%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ca56e-113">The supposed base type is used to generate the <xref:System.Type?displayProperty=nameWithType> class, and the supposed derived type is passed as an argument to the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca56e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca56e-114">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [<span data-ttu-id="ca56e-115">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="ca56e-115">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="ca56e-116">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="ca56e-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="ca56e-117">Hodnoty objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="ca56e-117">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="ca56e-118">Postupy: Určení, zda jsou dva objekty identické</span><span class="sxs-lookup"><span data-stu-id="ca56e-118">How to: Determine Whether Two Objects Are Identical</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
