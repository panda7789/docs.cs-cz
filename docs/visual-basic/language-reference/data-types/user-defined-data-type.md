---
title: Uživatelský datový typ (Visual Basic)
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
ms.openlocfilehash: 33a9dd3144f6f51eb6a63ff93750019878cb4a03
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507470"
---
# <a name="user-defined-data-type"></a><span data-ttu-id="343ae-102">Uživatelský datový typ</span><span class="sxs-lookup"><span data-stu-id="343ae-102">User-Defined Data Type</span></span>
<span data-ttu-id="343ae-103">Obsahuje data ve formátu, který definujete.</span><span class="sxs-lookup"><span data-stu-id="343ae-103">Holds data in a format you define.</span></span> <span data-ttu-id="343ae-104">`Structure` Prohlášení definuje formát.</span><span class="sxs-lookup"><span data-stu-id="343ae-104">The `Structure` statement defines the format.</span></span>  
  
 <span data-ttu-id="343ae-105">Předchozí verze jazyka Visual Basic podporují uživatelem definovaný typ (UDT).</span><span class="sxs-lookup"><span data-stu-id="343ae-105">Previous versions of Visual Basic support the user-defined type (UDT).</span></span> <span data-ttu-id="343ae-106">Rozbalí UDT na aktuální verzi *struktura*.</span><span class="sxs-lookup"><span data-stu-id="343ae-106">The current version expands the UDT to a *structure*.</span></span> <span data-ttu-id="343ae-107">Struktura je složen z jednoho nebo více *členy* různých datových typů.</span><span class="sxs-lookup"><span data-stu-id="343ae-107">A structure is a concatenation of one or more *members* of various data types.</span></span> <span data-ttu-id="343ae-108">Jazyka Visual Basic struktury považuje za jednu jednotku, i když se dá dostat taky jejích členů jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="343ae-108">Visual Basic treats a structure as a single unit, although you can also access its members individually.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="343ae-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="343ae-109">Remarks</span></span>  
 <span data-ttu-id="343ae-110">Definujte a použijte datový typ struktura, když je nutné sloučit různé datové typy do jedné jednotky, nebo když žádný základní datové typy sloužit vašim potřebám.</span><span class="sxs-lookup"><span data-stu-id="343ae-110">Define and use a structure data type when you need to combine various data types into a single unit, or when none of the elementary data types serve your needs.</span></span>  
  
 <span data-ttu-id="343ae-111">Výchozí hodnota datového typu Struktura se skládá z kombinace výchozí hodnoty všech jejích členů.</span><span class="sxs-lookup"><span data-stu-id="343ae-111">The default value of a structure data type consists of the combination of the default values of each of its members.</span></span>  
  
## <a name="declaration-format"></a><span data-ttu-id="343ae-112">Formát deklarace</span><span class="sxs-lookup"><span data-stu-id="343ae-112">Declaration Format</span></span>  
 <span data-ttu-id="343ae-113">Deklarace struktury začíná [Structure – příkaz](../../../visual-basic/language-reference/statements/structure-statement.md) a končí `End Structure` příkaz.</span><span class="sxs-lookup"><span data-stu-id="343ae-113">A structure declaration starts with the [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) and ends with the `End Structure` statement.</span></span> <span data-ttu-id="343ae-114">`Structure` Příkaz poskytuje název struktury, což je také identifikátor datového typu, který definuje strukturu.</span><span class="sxs-lookup"><span data-stu-id="343ae-114">The `Structure` statement supplies the name of the structure, which is also the identifier of the data type the structure is defining.</span></span> <span data-ttu-id="343ae-115">Ostatní části kódu můžete použít tento identifikátor pro deklaraci proměnné, parametry a funkce vrátí hodnoty, které mají být tato struktura datového typu.</span><span class="sxs-lookup"><span data-stu-id="343ae-115">Other parts of the code can use this identifier to declare variables, parameters, and function return values to be of this structure's data type.</span></span>  
  
 <span data-ttu-id="343ae-116">Deklarace mezi `Structure` a `End Structure` příkazů definovat členy struktury.</span><span class="sxs-lookup"><span data-stu-id="343ae-116">The declarations between the `Structure` and `End Structure` statements define the members of the structure.</span></span>  
  
## <a name="member-access-levels"></a><span data-ttu-id="343ae-117">Úrovně přístupu členů</span><span class="sxs-lookup"><span data-stu-id="343ae-117">Member Access Levels</span></span>  
 <span data-ttu-id="343ae-118">Je třeba deklarovat každého člena pomocí [příkazu Dim](../../../visual-basic/language-reference/statements/dim-statement.md) nebo příkaz, který určuje úroveň přístupu, jako například [veřejné](../../../visual-basic/language-reference/modifiers/public.md), [typu Friend](../../../visual-basic/language-reference/modifiers/friend.md), nebo [privátní](../../../visual-basic/language-reference/modifiers/private.md).</span><span class="sxs-lookup"><span data-stu-id="343ae-118">You must declare every member using a [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) or a statement that specifies access level, such as [Public](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../visual-basic/language-reference/modifiers/private.md).</span></span> <span data-ttu-id="343ae-119">Pokud používáte `Dim` prohlášení, výchozí úrovně přístupu na veřejnou.</span><span class="sxs-lookup"><span data-stu-id="343ae-119">If you use a `Dim` statement, the access level defaults to public.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="343ae-120">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="343ae-120">Programming Tips</span></span>  
  
-   <span data-ttu-id="343ae-121">**Využití paměti.**</span><span class="sxs-lookup"><span data-stu-id="343ae-121">**Memory Consumption.**</span></span> <span data-ttu-id="343ae-122">Stejně jako u všech složených datových typů nelze bezpečně vypočítat celkovou spotřebu paměti struktury sečtením nominálních přidělení úložiště jejích členů.</span><span class="sxs-lookup"><span data-stu-id="343ae-122">As with all composite data types, you cannot safely calculate the total memory consumption of a structure by adding together the nominal storage allocations of its members.</span></span> <span data-ttu-id="343ae-123">Kromě toho nelze bezpečně předpokládat, že pořadí úložiště v paměti je stejné jako vaše pořadí prohlášení.</span><span class="sxs-lookup"><span data-stu-id="343ae-123">Furthermore, you cannot safely assume that the order of storage in memory is the same as your order of declaration.</span></span> <span data-ttu-id="343ae-124">Pokud potřebujete řídit rozložení úložiště struktury, můžete použít <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut `Structure` příkazu.</span><span class="sxs-lookup"><span data-stu-id="343ae-124">If you need to control the storage layout of a structure, you can apply the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute to the `Structure` statement.</span></span>  
  
-   <span data-ttu-id="343ae-125">**Spolupráce aspekty.**</span><span class="sxs-lookup"><span data-stu-id="343ae-125">**Interop Considerations.**</span></span> <span data-ttu-id="343ae-126">Při vzájemném propojování součástí, které nejsou napsané pro rozhraní .NET Framework, například objekty automatizace nebo COM, mějte na paměti, že v jiných prostředích, uživatelem definované typy nejsou kompatibilní s jazykem Visual Basic struktury typů.</span><span class="sxs-lookup"><span data-stu-id="343ae-126">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that user-defined types in other environments are not compatible with Visual Basic structure types.</span></span>  
  
-   <span data-ttu-id="343ae-127">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="343ae-127">**Widening.**</span></span> <span data-ttu-id="343ae-128">Neexistuje žádný automatický převod do nebo z libovolného datového typu Struktura.</span><span class="sxs-lookup"><span data-stu-id="343ae-128">There is no automatic conversion to or from any structure data type.</span></span> <span data-ttu-id="343ae-129">Můžete definovat operátory převodu na váš pomocí struktury [Operator – příkaz](../../../visual-basic/language-reference/statements/operator-statement.md), a deklarujete každý operátor převodu na `Widening` nebo `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="343ae-129">You can define conversion operators on your structure using the [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md), and you can declare each conversion operator to be `Widening` or `Narrowing`.</span></span>  
  
-   <span data-ttu-id="343ae-130">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="343ae-130">**Type Characters.**</span></span> <span data-ttu-id="343ae-131">Struktura datové typy mít žádné – znak typu literálu nebo – znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="343ae-131">Structure data types have no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="343ae-132">**Typ architektury.**</span><span class="sxs-lookup"><span data-stu-id="343ae-132">**Framework Type.**</span></span> <span data-ttu-id="343ae-133">Neexistuje žádný odpovídající typ v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="343ae-133">There is no corresponding type in the .NET Framework.</span></span> <span data-ttu-id="343ae-134">Všechny struktury dědí z třídy rozhraní .NET Framework <xref:System.ValueType?displayProperty=nameWithType>, ale žádné jednotlivých struktura odpovídá <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="343ae-134">All structures inherit from the .NET Framework class <xref:System.ValueType?displayProperty=nameWithType>, but no individual structure corresponds to <xref:System.ValueType?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="343ae-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="343ae-135">Example</span></span>  
 <span data-ttu-id="343ae-136">Následující paradigma ukazuje obrys deklaraci struktury.</span><span class="sxs-lookup"><span data-stu-id="343ae-136">The following paradigm shows the outline of the declaration of a structure.</span></span>  
  
```  
[Public | Protected | Friend | Protected Friend | Private] Structure structname  
    {Dim | Public | Friend | Private} member1 As datatype1  
    ' ...  
    {Dim | Public | Friend | Private} memberN As datatypeN  
End Structure  
```  
  
## <a name="see-also"></a><span data-ttu-id="343ae-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="343ae-137">See also</span></span>
- <xref:System.ValueType>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [<span data-ttu-id="343ae-138">Datové typy</span><span class="sxs-lookup"><span data-stu-id="343ae-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="343ae-139">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="343ae-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="343ae-140">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="343ae-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="343ae-141">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="343ae-141">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="343ae-142">Widening</span><span class="sxs-lookup"><span data-stu-id="343ae-142">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="343ae-143">Narrowing</span><span class="sxs-lookup"><span data-stu-id="343ae-143">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="343ae-144">Struktury</span><span class="sxs-lookup"><span data-stu-id="343ae-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="343ae-145">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="343ae-145">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
