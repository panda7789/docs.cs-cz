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
ms.openlocfilehash: 8497f46453d586fb94e1f7c82c81c6b923dd6f60
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404418"
---
# <a name="of-clause-visual-basic"></a><span data-ttu-id="269cd-102">Of – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="269cd-102">Of Clause (Visual Basic)</span></span>
<span data-ttu-id="269cd-103">Zavádí `Of` klauzuli, která identifikuje *parametr typu* pro *obecnou* třídu, strukturu, rozhraní, delegáta nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="269cd-103">Introduces an `Of` clause, which identifies a *type parameter* on a *generic* class, structure, interface, delegate, or procedure.</span></span> <span data-ttu-id="269cd-104">Informace o obecných typech naleznete v tématu [Obecné typy v Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="269cd-104">For information on generic types, see [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span></span>  
  
## <a name="using-the-of-keyword"></a><span data-ttu-id="269cd-105">Použití klíčového slova of</span><span class="sxs-lookup"><span data-stu-id="269cd-105">Using the Of Keyword</span></span>  
 <span data-ttu-id="269cd-106">Následující příklad kódu používá `Of` klíčové slovo k definování obrysu třídy, která přijímá dva parametry typu.</span><span class="sxs-lookup"><span data-stu-id="269cd-106">The following code example uses the `Of` keyword to define the outline of a class that takes two type parameters.</span></span> <span data-ttu-id="269cd-107">*Omezuje* `keyType` parametr <xref:System.IComparable> rozhraním, což znamená, že nenáročného kódu musí zadat argument typu, který implementuje <xref:System.IComparable> .</span><span class="sxs-lookup"><span data-stu-id="269cd-107">It *constrains* the `keyType` parameter by the <xref:System.IComparable> interface, which means the consuming code must supply a type argument that implements <xref:System.IComparable>.</span></span> <span data-ttu-id="269cd-108">To je nezbytné, aby `add` procedura mohla zavolat <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="269cd-108">This is necessary so that the `add` procedure can call the <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="269cd-109">Další informace o omezeních najdete v tématu [seznam typů](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="269cd-109">For more information on constraints, see [Type List](type-list.md).</span></span>  
  
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
  
 <span data-ttu-id="269cd-110">Pokud dokončíte definici předchozí třídy, můžete `dictionary` z ní vytvořit různé třídy.</span><span class="sxs-lookup"><span data-stu-id="269cd-110">If you complete the preceding class definition, you can construct a variety of `dictionary` classes from it.</span></span> <span data-ttu-id="269cd-111">Typy, které zadáte, `entryType` a `keyType` Určete, jaký typ položky má třída obsahovat a jaký typ klíče přidruží ke každé položce.</span><span class="sxs-lookup"><span data-stu-id="269cd-111">The types you supply to `entryType` and `keyType` determine what type of entry the class holds and what type of key it associates with each entry.</span></span> <span data-ttu-id="269cd-112">Z důvodu omezení je nutné zadat do `keyType` typu, který implementuje <xref:System.IComparable> .</span><span class="sxs-lookup"><span data-stu-id="269cd-112">Because of the constraint, you must supply to `keyType` a type that implements <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="269cd-113">Následující příklad kódu vytvoří objekt, který obsahuje `String` položky a přidruží `Integer` ke každému z nich klíč.</span><span class="sxs-lookup"><span data-stu-id="269cd-113">The following code example creates an object that holds `String` entries and associates an `Integer` key with each one.</span></span> <span data-ttu-id="269cd-114">`Integer`implementuje <xref:System.IComparable> a proto splňuje omezení na `keyType` .</span><span class="sxs-lookup"><span data-stu-id="269cd-114">`Integer` implements <xref:System.IComparable> and therefore satisfies the constraint on `keyType`.</span></span>  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 <span data-ttu-id="269cd-115">`Of`Klíčové slovo lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="269cd-115">The `Of` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="269cd-116">Class – příkaz</span><span class="sxs-lookup"><span data-stu-id="269cd-116">Class Statement</span></span>](class-statement.md)  
  
 [<span data-ttu-id="269cd-117">Delegate – příkaz</span><span class="sxs-lookup"><span data-stu-id="269cd-117">Delegate Statement</span></span>](delegate-statement.md)  
  
 [<span data-ttu-id="269cd-118">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="269cd-118">Function Statement</span></span>](function-statement.md)  
  
 [<span data-ttu-id="269cd-119">Interface – příkaz</span><span class="sxs-lookup"><span data-stu-id="269cd-119">Interface Statement</span></span>](interface-statement.md)  
  
 [<span data-ttu-id="269cd-120">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="269cd-120">Structure Statement</span></span>](structure-statement.md)  
  
 [<span data-ttu-id="269cd-121">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="269cd-121">Sub Statement</span></span>](sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="269cd-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="269cd-122">See also</span></span>

- <xref:System.IComparable>
- [<span data-ttu-id="269cd-123">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="269cd-123">Type List</span></span>](type-list.md)
- [<span data-ttu-id="269cd-124">Obecné typy v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="269cd-124">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="269cd-125">V</span><span class="sxs-lookup"><span data-stu-id="269cd-125">In</span></span>](../modifiers/in-generic-modifier.md)
- [<span data-ttu-id="269cd-126">Mimo</span><span class="sxs-lookup"><span data-stu-id="269cd-126">Out</span></span>](../modifiers/out-generic-modifier.md)
