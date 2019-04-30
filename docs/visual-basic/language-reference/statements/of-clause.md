---
title: Of – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Of
- vb.Of
- vb.of
helpviewer_keywords:
- Of keyword [Visual Basic]
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
ms.openlocfilehash: 880570c714292b0c11eef4e2cd4c4b410bb075f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784147"
---
# <a name="of-clause-visual-basic"></a><span data-ttu-id="e5402-102">Of – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5402-102">Of Clause (Visual Basic)</span></span>
<span data-ttu-id="e5402-103">Zavádí `Of` klauzuli, která identifikuje *parametr typu* na *obecný* třídy, struktury, rozhraní, delegáta nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="e5402-103">Introduces an `Of` clause, which identifies a *type parameter* on a *generic* class, structure, interface, delegate, or procedure.</span></span> <span data-ttu-id="e5402-104">Informace v obecných typech najdete v tématu [obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="e5402-104">For information on generic types, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>  
  
## <a name="using-the-of-keyword"></a><span data-ttu-id="e5402-105">Použití klíčového slova</span><span class="sxs-lookup"><span data-stu-id="e5402-105">Using the Of Keyword</span></span>  
 <span data-ttu-id="e5402-106">Následující příklad kódu používá `Of` – klíčové slovo k definování obrysu třídu, která přijímá dva parametry typu.</span><span class="sxs-lookup"><span data-stu-id="e5402-106">The following code example uses the `Of` keyword to define the outline of a class that takes two type parameters.</span></span> <span data-ttu-id="e5402-107">To *omezí* `keyType` parametr odkázal <xref:System.IComparable> rozhraní, což znamená, že časově náročný kód musíte zadat argument typu, který implementuje <xref:System.IComparable>.</span><span class="sxs-lookup"><span data-stu-id="e5402-107">It *constrains* the `keyType` parameter by the <xref:System.IComparable> interface, which means the consuming code must supply a type argument that implements <xref:System.IComparable>.</span></span> <span data-ttu-id="e5402-108">To je nezbytné tak, aby `add` postup můžete volat <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="e5402-108">This is necessary so that the `add` procedure can call the <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e5402-109">Další informace o omezení, najdete v části [seznam typů](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="e5402-109">For more information on constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
```  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 <span data-ttu-id="e5402-110">Jestliže dokončíte předchozí definice třídy, musíte postavit celou řadu `dictionary` třídy z něj.</span><span class="sxs-lookup"><span data-stu-id="e5402-110">If you complete the preceding class definition, you can construct a variety of `dictionary` classes from it.</span></span> <span data-ttu-id="e5402-111">Typy, které zadáte, `entryType` a `keyType` určit, jaký typ položky obsahuje třídy a jaký typ klíče, který přidruží s každou položku.</span><span class="sxs-lookup"><span data-stu-id="e5402-111">The types you supply to `entryType` and `keyType` determine what type of entry the class holds and what type of key it associates with each entry.</span></span> <span data-ttu-id="e5402-112">Z důvodu omezení, je nutné zadat do `keyType` typ, který implementuje <xref:System.IComparable>.</span><span class="sxs-lookup"><span data-stu-id="e5402-112">Because of the constraint, you must supply to `keyType` a type that implements <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="e5402-113">Následující příklad kódu vytvoří objekt, který obsahuje `String` položky a přidruží `Integer` klíče s každé z nich.</span><span class="sxs-lookup"><span data-stu-id="e5402-113">The following code example creates an object that holds `String` entries and associates an `Integer` key with each one.</span></span> <span data-ttu-id="e5402-114">`Integer` implementuje <xref:System.IComparable> a proto nebude vyhovovat omezení na `keyType`.</span><span class="sxs-lookup"><span data-stu-id="e5402-114">`Integer` implements <xref:System.IComparable> and therefore satisfies the constraint on `keyType`.</span></span>  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 <span data-ttu-id="e5402-115">`Of` – Klíčové slovo lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="e5402-115">The `Of` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="e5402-116">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="e5402-116">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="e5402-117">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="e5402-117">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="e5402-118">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="e5402-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="e5402-119">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="e5402-119">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="e5402-120">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="e5402-120">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="e5402-121">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="e5402-121">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="e5402-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5402-122">See also</span></span>

- <xref:System.IComparable>
- [<span data-ttu-id="e5402-123">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="e5402-123">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="e5402-124">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e5402-124">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="e5402-125">V</span><span class="sxs-lookup"><span data-stu-id="e5402-125">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [<span data-ttu-id="e5402-126">navýšení kapacity</span><span class="sxs-lookup"><span data-stu-id="e5402-126">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
