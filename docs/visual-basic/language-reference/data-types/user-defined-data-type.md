---
title: "Uživatelský datový typ"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e1876d61a2ce89b04c6e5061b868f0be365639f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="user-defined-data-type"></a><span data-ttu-id="d036d-102">Uživatelský datový typ</span><span class="sxs-lookup"><span data-stu-id="d036d-102">User-Defined Data Type</span></span>
<span data-ttu-id="d036d-103">Obsahuje data ve formátu, který definujete.</span><span class="sxs-lookup"><span data-stu-id="d036d-103">Holds data in a format you define.</span></span> <span data-ttu-id="d036d-104">`Structure` Příkaz definuje formát.</span><span class="sxs-lookup"><span data-stu-id="d036d-104">The `Structure` statement defines the format.</span></span>  
  
 <span data-ttu-id="d036d-105">Předchozí verze jazyka Visual Basic podporují uživatelem definovaný typ (UDT).</span><span class="sxs-lookup"><span data-stu-id="d036d-105">Previous versions of Visual Basic support the user-defined type (UDT).</span></span> <span data-ttu-id="d036d-106">Aktuální verze rozšíří UDT k *struktura*.</span><span class="sxs-lookup"><span data-stu-id="d036d-106">The current version expands the UDT to a *structure*.</span></span> <span data-ttu-id="d036d-107">Struktura je zřetězení jednoho nebo více *členy* různých datových typů.</span><span class="sxs-lookup"><span data-stu-id="d036d-107">A structure is a concatenation of one or more *members* of various data types.</span></span> <span data-ttu-id="d036d-108">Visual Basic struktura považuje za jedné jednotky, i když je dostupný také její členy jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="d036d-108">Visual Basic treats a structure as a single unit, although you can also access its members individually.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d036d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d036d-109">Remarks</span></span>  
 <span data-ttu-id="d036d-110">Definice a používání Struktura datový typ, když je nutné sloučit různé typy dat do jedné jednotky, nebo když žádný z základní datové typy slouží vašim potřebám.</span><span class="sxs-lookup"><span data-stu-id="d036d-110">Define and use a structure data type when you need to combine various data types into a single unit, or when none of the elementary data types serve your needs.</span></span>  
  
 <span data-ttu-id="d036d-111">Výchozí hodnota datového typu Struktura se skládá z kombinace výchozí hodnoty jednotlivých její členy.</span><span class="sxs-lookup"><span data-stu-id="d036d-111">The default value of a structure data type consists of the combination of the default values of each of its members.</span></span>  
  
## <a name="declaration-format"></a><span data-ttu-id="d036d-112">Formát deklarace</span><span class="sxs-lookup"><span data-stu-id="d036d-112">Declaration Format</span></span>  
 <span data-ttu-id="d036d-113">Deklarace struktury začíná [Structure – příkaz](../../../visual-basic/language-reference/statements/structure-statement.md) a končí `End``Structure` příkaz.</span><span class="sxs-lookup"><span data-stu-id="d036d-113">A structure declaration starts with the [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) and ends with the `End``Structure` statement.</span></span> <span data-ttu-id="d036d-114">`Structure` Příkaz poskytuje název struktury, což je také identifikátor datového typu, který definuje strukturu.</span><span class="sxs-lookup"><span data-stu-id="d036d-114">The `Structure` statement supplies the name of the structure, which is also the identifier of the data type the structure is defining.</span></span> <span data-ttu-id="d036d-115">Ostatní části kódu můžete použít tento identifikátor proměnné a parametry, funkce vrátí hodnoty, které mají být data typu tuto strukturu deklarovat.</span><span class="sxs-lookup"><span data-stu-id="d036d-115">Other parts of the code can use this identifier to declare variables, parameters, and function return values to be of this structure's data type.</span></span>  
  
 <span data-ttu-id="d036d-116">Deklarace mezi `Structure` a `End``Structure` příkazy definovat členů struktury.</span><span class="sxs-lookup"><span data-stu-id="d036d-116">The declarations between the `Structure` and `End``Structure` statements define the members of the structure.</span></span>  
  
## <a name="member-access-levels"></a><span data-ttu-id="d036d-117">Úrovně přístupu členů</span><span class="sxs-lookup"><span data-stu-id="d036d-117">Member Access Levels</span></span>  
 <span data-ttu-id="d036d-118">Je potřeba deklarovat každý člen pomocí [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md) nebo příkazu, který určuje úroveň přístupu, jako například [veřejné](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), nebo [privátní](../../../visual-basic/language-reference/modifiers/private.md).</span><span class="sxs-lookup"><span data-stu-id="d036d-118">You must declare every member using a [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) or a statement that specifies access level, such as [Public](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../visual-basic/language-reference/modifiers/private.md).</span></span> <span data-ttu-id="d036d-119">Pokud používáte `Dim` prohlášení, výchozí hodnoty úrovně přístupu na hodnotu veřejná.</span><span class="sxs-lookup"><span data-stu-id="d036d-119">If you use a `Dim` statement, the access level defaults to public.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="d036d-120">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="d036d-120">Programming Tips</span></span>  
  
-   <span data-ttu-id="d036d-121">**Využití paměti.**</span><span class="sxs-lookup"><span data-stu-id="d036d-121">**Memory Consumption.**</span></span> <span data-ttu-id="d036d-122">Stejně jako u všech složené datové typy, nelze počítat bezpečně celkové paměti spotřeby strukturou společně přidáním přidělení nominální úložiště svých členů.</span><span class="sxs-lookup"><span data-stu-id="d036d-122">As with all composite data types, you cannot safely calculate the total memory consumption of a structure by adding together the nominal storage allocations of its members.</span></span> <span data-ttu-id="d036d-123">Kromě toho nelze předpokládat bezpečně, že pořadí úložiště v paměti je stejný jako vaši objednávku deklarace.</span><span class="sxs-lookup"><span data-stu-id="d036d-123">Furthermore, you cannot safely assume that the order of storage in memory is the same as your order of declaration.</span></span> <span data-ttu-id="d036d-124">Pokud potřebujete k řízení rozložení úložiště struktury, můžete použít <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut `Structure` příkaz.</span><span class="sxs-lookup"><span data-stu-id="d036d-124">If you need to control the storage layout of a structure, you can apply the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute to the `Structure` statement.</span></span>  
  
-   <span data-ttu-id="d036d-125">**Spolupráce aspekty.**</span><span class="sxs-lookup"><span data-stu-id="d036d-125">**Interop Considerations.**</span></span> <span data-ttu-id="d036d-126">Pokud se propojení s součásti, které nejsou určeny pro rozhraní .NET Framework, například objekty automatizace nebo COM, mějte na paměti, že nejsou kompatibilní s jazykem Visual Basic uživatelem definované typy v jiných prostředích struktury typy.</span><span class="sxs-lookup"><span data-stu-id="d036d-126">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that user-defined types in other environments are not compatible with Visual Basic structure types.</span></span>  
  
-   <span data-ttu-id="d036d-127">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="d036d-127">**Widening.**</span></span> <span data-ttu-id="d036d-128">Neexistuje žádný automatický převod na nebo z jakéhokoli struktura datového typu.</span><span class="sxs-lookup"><span data-stu-id="d036d-128">There is no automatic conversion to or from any structure data type.</span></span> <span data-ttu-id="d036d-129">Operátory převodu můžete definovat na váš struktura pomocí [Operator – příkaz](../../../visual-basic/language-reference/statements/operator-statement.md), a můžou deklarovat každý operátor převodu být `Widening` nebo `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="d036d-129">You can define conversion operators on your structure using the [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md), and you can declare each conversion operator to be `Widening` or `Narrowing`.</span></span>  
  
-   <span data-ttu-id="d036d-130">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="d036d-130">**Type Characters.**</span></span> <span data-ttu-id="d036d-131">Struktura datové typy mít žádné – znak typu literálu ani – znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="d036d-131">Structure data types have no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="d036d-132">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="d036d-132">**Framework Type.**</span></span> <span data-ttu-id="d036d-133">Neexistuje žádný odpovídající typ v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d036d-133">There is no corresponding type in the .NET Framework.</span></span> <span data-ttu-id="d036d-134">Všechny struktury dědění ze třídy rozhraní .NET Framework <xref:System.ValueType?displayProperty=nameWithType>, ale bez individuálních struktura odpovídá <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d036d-134">All structures inherit from the .NET Framework class <xref:System.ValueType?displayProperty=nameWithType>, but no individual structure corresponds to <xref:System.ValueType?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d036d-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="d036d-135">Example</span></span>  
 <span data-ttu-id="d036d-136">Následující zlepší ukazuje obrys deklaraci do struktury.</span><span class="sxs-lookup"><span data-stu-id="d036d-136">The following paradigm shows the outline of the declaration of a structure.</span></span>  
  
```  
[Public | Protected | Friend | Protected Friend | Private] Structure structname  
    {Dim | Public | Friend | Private} member1 As datatype1  
    ' ...  
    {Dim | Public | Friend | Private} memberN As datatypeN  
End Structure  
```  
  
## <a name="see-also"></a><span data-ttu-id="d036d-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="d036d-137">See Also</span></span>  
 <xref:System.ValueType>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 [<span data-ttu-id="d036d-138">Datové typy</span><span class="sxs-lookup"><span data-stu-id="d036d-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="d036d-139">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="d036d-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="d036d-140">Souhrn konverze</span><span class="sxs-lookup"><span data-stu-id="d036d-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="d036d-141">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="d036d-141">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="d036d-142">Rozšíření</span><span class="sxs-lookup"><span data-stu-id="d036d-142">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="d036d-143">Zužující</span><span class="sxs-lookup"><span data-stu-id="d036d-143">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="d036d-144">Struktury</span><span class="sxs-lookup"><span data-stu-id="d036d-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="d036d-145">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="d036d-145">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
