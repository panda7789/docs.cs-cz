---
title: Uživatelský datový typ
ms.date: 07/20/2015
f1_keywords:
- UserDefined
- UDT
- vb.UDT
- User-Defined
- vb.UserDefined
- vb.User-Defined
helpviewer_keywords:
- user-defined data types [Visual Basic], Visual Basic
- user-defined types
- structures [Visual Basic], as user-defined data types
- user-defined types [Visual Basic], Visual Basic
- user-defined types [Visual Basic], structure declaration
- user-defined types [Visual Basic], structures in Visual Basic
- user-defined data types [Visual Basic], structure declaration
- data types [Visual Basic], assigning
- Structure statement [Visual Basic]
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], structures in Visual Basic
- user-defined data types
- types [Visual Basic], user-defined
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
ms.openlocfilehash: 99eeb4b619f6bb23d00f8e449de953d41843f714
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343870"
---
# <a name="user-defined-data-type"></a><span data-ttu-id="db917-102">Uživatelský datový typ</span><span class="sxs-lookup"><span data-stu-id="db917-102">User-Defined Data Type</span></span>

<span data-ttu-id="db917-103">Holds data in a format you define.</span><span class="sxs-lookup"><span data-stu-id="db917-103">Holds data in a format you define.</span></span> <span data-ttu-id="db917-104">The `Structure` statement defines the format.</span><span class="sxs-lookup"><span data-stu-id="db917-104">The `Structure` statement defines the format.</span></span>

<span data-ttu-id="db917-105">Previous versions of Visual Basic support the user-defined type (UDT).</span><span class="sxs-lookup"><span data-stu-id="db917-105">Previous versions of Visual Basic support the user-defined type (UDT).</span></span> <span data-ttu-id="db917-106">The current version expands the UDT to a *structure*.</span><span class="sxs-lookup"><span data-stu-id="db917-106">The current version expands the UDT to a *structure*.</span></span> <span data-ttu-id="db917-107">A structure is a concatenation of one or more *members* of various data types.</span><span class="sxs-lookup"><span data-stu-id="db917-107">A structure is a concatenation of one or more *members* of various data types.</span></span> <span data-ttu-id="db917-108">Visual Basic treats a structure as a single unit, although you can also access its members individually.</span><span class="sxs-lookup"><span data-stu-id="db917-108">Visual Basic treats a structure as a single unit, although you can also access its members individually.</span></span>

## <a name="remarks"></a><span data-ttu-id="db917-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db917-109">Remarks</span></span>

<span data-ttu-id="db917-110">Define and use a structure data type when you need to combine various data types into a single unit, or when none of the elementary data types serve your needs.</span><span class="sxs-lookup"><span data-stu-id="db917-110">Define and use a structure data type when you need to combine various data types into a single unit, or when none of the elementary data types serve your needs.</span></span>

<span data-ttu-id="db917-111">The default value of a structure data type consists of the combination of the default values of each of its members.</span><span class="sxs-lookup"><span data-stu-id="db917-111">The default value of a structure data type consists of the combination of the default values of each of its members.</span></span>

## <a name="declaration-format"></a><span data-ttu-id="db917-112">Declaration Format</span><span class="sxs-lookup"><span data-stu-id="db917-112">Declaration Format</span></span>

<span data-ttu-id="db917-113">A structure declaration starts with the [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) and ends with the `End Structure` statement.</span><span class="sxs-lookup"><span data-stu-id="db917-113">A structure declaration starts with the [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) and ends with the `End Structure` statement.</span></span> <span data-ttu-id="db917-114">The `Structure` statement supplies the name of the structure, which is also the identifier of the data type the structure is defining.</span><span class="sxs-lookup"><span data-stu-id="db917-114">The `Structure` statement supplies the name of the structure, which is also the identifier of the data type the structure is defining.</span></span> <span data-ttu-id="db917-115">Other parts of the code can use this identifier to declare variables, parameters, and function return values to be of this structure's data type.</span><span class="sxs-lookup"><span data-stu-id="db917-115">Other parts of the code can use this identifier to declare variables, parameters, and function return values to be of this structure's data type.</span></span>

<span data-ttu-id="db917-116">The declarations between the `Structure` and `End Structure` statements define the members of the structure.</span><span class="sxs-lookup"><span data-stu-id="db917-116">The declarations between the `Structure` and `End Structure` statements define the members of the structure.</span></span>

## <a name="member-access-levels"></a><span data-ttu-id="db917-117">Member Access Levels</span><span class="sxs-lookup"><span data-stu-id="db917-117">Member Access Levels</span></span>

<span data-ttu-id="db917-118">You must declare every member using a [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) or a statement that specifies access level, such as [Public](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../visual-basic/language-reference/modifiers/private.md).</span><span class="sxs-lookup"><span data-stu-id="db917-118">You must declare every member using a [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) or a statement that specifies access level, such as [Public](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../visual-basic/language-reference/modifiers/private.md).</span></span> <span data-ttu-id="db917-119">If you use a `Dim` statement, the access level defaults to public.</span><span class="sxs-lookup"><span data-stu-id="db917-119">If you use a `Dim` statement, the access level defaults to public.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="db917-120">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="db917-120">Programming Tips</span></span>

- <span data-ttu-id="db917-121">**Memory Consumption.**</span><span class="sxs-lookup"><span data-stu-id="db917-121">**Memory Consumption.**</span></span> <span data-ttu-id="db917-122">As with all composite data types, you cannot safely calculate the total memory consumption of a structure by adding together the nominal storage allocations of its members.</span><span class="sxs-lookup"><span data-stu-id="db917-122">As with all composite data types, you cannot safely calculate the total memory consumption of a structure by adding together the nominal storage allocations of its members.</span></span> <span data-ttu-id="db917-123">Furthermore, you cannot safely assume that the order of storage in memory is the same as your order of declaration.</span><span class="sxs-lookup"><span data-stu-id="db917-123">Furthermore, you cannot safely assume that the order of storage in memory is the same as your order of declaration.</span></span> <span data-ttu-id="db917-124">If you need to control the storage layout of a structure, you can apply the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute to the `Structure` statement.</span><span class="sxs-lookup"><span data-stu-id="db917-124">If you need to control the storage layout of a structure, you can apply the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute to the `Structure` statement.</span></span>

- <span data-ttu-id="db917-125">**Interop Considerations.**</span><span class="sxs-lookup"><span data-stu-id="db917-125">**Interop Considerations.**</span></span> <span data-ttu-id="db917-126">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that user-defined types in other environments are not compatible with Visual Basic structure types.</span><span class="sxs-lookup"><span data-stu-id="db917-126">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that user-defined types in other environments are not compatible with Visual Basic structure types.</span></span>

- <span data-ttu-id="db917-127">**Widening.**</span><span class="sxs-lookup"><span data-stu-id="db917-127">**Widening.**</span></span> <span data-ttu-id="db917-128">There is no automatic conversion to or from any structure data type.</span><span class="sxs-lookup"><span data-stu-id="db917-128">There is no automatic conversion to or from any structure data type.</span></span> <span data-ttu-id="db917-129">You can define conversion operators on your structure using the [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md), and you can declare each conversion operator to be `Widening` or `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="db917-129">You can define conversion operators on your structure using the [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md), and you can declare each conversion operator to be `Widening` or `Narrowing`.</span></span>

- <span data-ttu-id="db917-130">**Type Characters.**</span><span class="sxs-lookup"><span data-stu-id="db917-130">**Type Characters.**</span></span> <span data-ttu-id="db917-131">Structure data types have no literal type character or identifier type character.</span><span class="sxs-lookup"><span data-stu-id="db917-131">Structure data types have no literal type character or identifier type character.</span></span>

- <span data-ttu-id="db917-132">**Framework Type.**</span><span class="sxs-lookup"><span data-stu-id="db917-132">**Framework Type.**</span></span> <span data-ttu-id="db917-133">There is no corresponding type in the .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="db917-133">There is no corresponding type in the .NET Framework.</span></span> <span data-ttu-id="db917-134">All structures inherit from the .NET Framework class <xref:System.ValueType?displayProperty=nameWithType>, but no individual structure corresponds to <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="db917-134">All structures inherit from the .NET Framework class <xref:System.ValueType?displayProperty=nameWithType>, but no individual structure corresponds to <xref:System.ValueType?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="db917-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="db917-135">Example</span></span>

<span data-ttu-id="db917-136">The following paradigm shows the outline of the declaration of a structure.</span><span class="sxs-lookup"><span data-stu-id="db917-136">The following paradigm shows the outline of the declaration of a structure.</span></span>

```vb
[Public | Protected | Friend | Protected Friend | Private] Structure structname
    {Dim | Public | Friend | Private} member1 As datatype1
    ' ...
    {Dim | Public | Friend | Private} memberN As datatypeN
End Structure
```

## <a name="see-also"></a><span data-ttu-id="db917-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db917-137">See also</span></span>

- <xref:System.ValueType>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [<span data-ttu-id="db917-138">Datové typy</span><span class="sxs-lookup"><span data-stu-id="db917-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="db917-139">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="db917-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="db917-140">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="db917-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="db917-141">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="db917-141">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="db917-142">Widening</span><span class="sxs-lookup"><span data-stu-id="db917-142">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="db917-143">Narrowing</span><span class="sxs-lookup"><span data-stu-id="db917-143">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="db917-144">Struktury</span><span class="sxs-lookup"><span data-stu-id="db917-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="db917-145">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="db917-145">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
