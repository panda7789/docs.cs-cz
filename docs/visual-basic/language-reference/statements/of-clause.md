---
title: Of – klauzule
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
ms.openlocfilehash: d88c43efe858d6b81b7d8d2470b234ff5d40632a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353842"
---
# <a name="of-clause-visual-basic"></a><span data-ttu-id="41ded-102">Of – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41ded-102">Of Clause (Visual Basic)</span></span>
<span data-ttu-id="41ded-103">Zavádí klauzuli `Of`, která identifikuje *parametr typu* pro *obecnou* třídu, strukturu, rozhraní, delegáta nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="41ded-103">Introduces an `Of` clause, which identifies a *type parameter* on a *generic* class, structure, interface, delegate, or procedure.</span></span> <span data-ttu-id="41ded-104">Informace o obecných typech naleznete v tématu [Obecné typy v Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="41ded-104">For information on generic types, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>  
  
## <a name="using-the-of-keyword"></a><span data-ttu-id="41ded-105">Použití klíčového slova of</span><span class="sxs-lookup"><span data-stu-id="41ded-105">Using the Of Keyword</span></span>  
 <span data-ttu-id="41ded-106">Následující příklad kódu používá klíčové slovo `Of` k definování obrysu třídy, která přijímá dva parametry typu.</span><span class="sxs-lookup"><span data-stu-id="41ded-106">The following code example uses the `Of` keyword to define the outline of a class that takes two type parameters.</span></span> <span data-ttu-id="41ded-107">*Omezuje* parametr `keyType` rozhraním <xref:System.IComparable>, což znamená, že nenáročného kódu musí zadat argument typu, který implementuje <xref:System.IComparable>.</span><span class="sxs-lookup"><span data-stu-id="41ded-107">It *constrains* the `keyType` parameter by the <xref:System.IComparable> interface, which means the consuming code must supply a type argument that implements <xref:System.IComparable>.</span></span> <span data-ttu-id="41ded-108">To je nezbytné, aby `add` procedura mohla volat metodu <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="41ded-108">This is necessary so that the `add` procedure can call the <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="41ded-109">Další informace o omezeních najdete v tématu [seznam typů](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="41ded-109">For more information on constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
```vb  
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
  
 <span data-ttu-id="41ded-110">Pokud dokončíte definici předchozí třídy, můžete z ní vytvořit různé třídy `dictionary`.</span><span class="sxs-lookup"><span data-stu-id="41ded-110">If you complete the preceding class definition, you can construct a variety of `dictionary` classes from it.</span></span> <span data-ttu-id="41ded-111">Typy, které zadáte pro `entryType` a `keyType` určení, jaký typ položky má třída obsahovat a jaký typ klíče přidruží ke každé položce.</span><span class="sxs-lookup"><span data-stu-id="41ded-111">The types you supply to `entryType` and `keyType` determine what type of entry the class holds and what type of key it associates with each entry.</span></span> <span data-ttu-id="41ded-112">Z důvodu omezení musíte zadat, aby `keyType` typ, který implementuje <xref:System.IComparable>.</span><span class="sxs-lookup"><span data-stu-id="41ded-112">Because of the constraint, you must supply to `keyType` a type that implements <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="41ded-113">Následující příklad kódu vytvoří objekt, který obsahuje položky `String` a přidruží k každé z nich `Integer` klíč.</span><span class="sxs-lookup"><span data-stu-id="41ded-113">The following code example creates an object that holds `String` entries and associates an `Integer` key with each one.</span></span> <span data-ttu-id="41ded-114">`Integer` implementuje <xref:System.IComparable> a proto splňuje omezení na `keyType`.</span><span class="sxs-lookup"><span data-stu-id="41ded-114">`Integer` implements <xref:System.IComparable> and therefore satisfies the constraint on `keyType`.</span></span>  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 <span data-ttu-id="41ded-115">Klíčové slovo `Of` lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="41ded-115">The `Of` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="41ded-116">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="41ded-116">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="41ded-117">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="41ded-117">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="41ded-118">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="41ded-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="41ded-119">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="41ded-119">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="41ded-120">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="41ded-120">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="41ded-121">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="41ded-121">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="41ded-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="41ded-122">See also</span></span>

- <xref:System.IComparable>
- [<span data-ttu-id="41ded-123">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="41ded-123">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="41ded-124">Obecné typy v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="41ded-124">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="41ded-125">Pro</span><span class="sxs-lookup"><span data-stu-id="41ded-125">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [<span data-ttu-id="41ded-126">Mimo</span><span class="sxs-lookup"><span data-stu-id="41ded-126">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
