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
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a><span data-ttu-id="ebeae-102">Postupy: Určení, zda dva objekty souvisejí (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebeae-102">How to: Determine Whether Two Objects Are Related (Visual Basic)</span></span>

<span data-ttu-id="ebeae-103">Můžete porovnat dva objekty a určit vztah, pokud existuje, mezi třídami, ze kterých jsou vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="ebeae-103">You can compare two objects to determine the relationship, if any, between the classes from which they are created.</span></span> <span data-ttu-id="ebeae-104"><xref:System.Type.IsInstanceOfType%2A>Metoda <xref:System.Type?displayProperty=nameWithType> třídy vrací `True` , pokud zadaná třída dědí z aktuální třídy, nebo pokud je aktuální typ rozhraní podporované zadanou třídou.</span><span class="sxs-lookup"><span data-stu-id="ebeae-104">The <xref:System.Type.IsInstanceOfType%2A> method of the <xref:System.Type?displayProperty=nameWithType> class returns `True` if the specified class inherits from the current class, or if the current type is an interface supported by the specified class.</span></span>

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a><span data-ttu-id="ebeae-105">Určení, zda jeden objekt dědí z jiného objektu nebo třídy nebo rozhraní</span><span class="sxs-lookup"><span data-stu-id="ebeae-105">To determine if one object inherits from another object's class or interface</span></span>

1. <span data-ttu-id="ebeae-106">U objektu, který si myslíte, může být základní typ, vyvolat <xref:System.Object.GetType%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="ebeae-106">On the object you think might be of the base type, invoke the <xref:System.Object.GetType%2A> method.</span></span>

2. <span data-ttu-id="ebeae-107">U <xref:System.Type?displayProperty=nameWithType> objektu vráceného metodou <xref:System.Object.GetType%2A> volejte <xref:System.Type.IsInstanceOfType%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="ebeae-107">On the <xref:System.Type?displayProperty=nameWithType> object returned by <xref:System.Object.GetType%2A>, invoke the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>

3. <span data-ttu-id="ebeae-108">V seznamu argumentů pro <xref:System.Type.IsInstanceOfType%2A> Zadejte objekt, který si myslíte, může být odvozený typ.</span><span class="sxs-lookup"><span data-stu-id="ebeae-108">In the argument list for <xref:System.Type.IsInstanceOfType%2A>, specify the object you think might be of the derived type.</span></span>

    <span data-ttu-id="ebeae-109"><xref:System.Type.IsInstanceOfType%2A>Vrátí `True` , zda typ argumentu dědí z <xref:System.Type?displayProperty=nameWithType> typu objektu.</span><span class="sxs-lookup"><span data-stu-id="ebeae-109"><xref:System.Type.IsInstanceOfType%2A> returns `True` if its argument type inherits from the <xref:System.Type?displayProperty=nameWithType> object type.</span></span>

## <a name="example"></a><span data-ttu-id="ebeae-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="ebeae-110">Example</span></span>
 <span data-ttu-id="ebeae-111">Následující příklad určuje, zda jeden objekt představuje třídu odvozenou z jiného objektu třídy.</span><span class="sxs-lookup"><span data-stu-id="ebeae-111">The following example determines whether one object represents a class derived from another object's class.</span></span>

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

<span data-ttu-id="ebeae-112">Všimněte si neočekávaného umístění dvou objektových proměnných v volání <xref:System.Type.IsInstanceOfType%2A> .</span><span class="sxs-lookup"><span data-stu-id="ebeae-112">Note the unexpected placement of the two object variables in the call to <xref:System.Type.IsInstanceOfType%2A>.</span></span> <span data-ttu-id="ebeae-113">Předpokládaný základní typ se používá ke generování <xref:System.Type?displayProperty=nameWithType> třídy a předpokládaný odvozený typ je předán jako argument <xref:System.Type.IsInstanceOfType%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ebeae-113">The supposed base type is used to generate the <xref:System.Type?displayProperty=nameWithType> class, and the supposed derived type is passed as an argument to the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="ebeae-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="ebeae-114">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [<span data-ttu-id="ebeae-115">Datový typ objektu</span><span class="sxs-lookup"><span data-stu-id="ebeae-115">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="ebeae-116">Proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="ebeae-116">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="ebeae-117">Hodnoty proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="ebeae-117">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="ebeae-118">Postupy: Určení, zda dva objekty jsou identické</span><span class="sxs-lookup"><span data-stu-id="ebeae-118">How to: Determine Whether Two Objects Are Identical</span></span>](how-to-determine-whether-two-objects-are-identical.md)
