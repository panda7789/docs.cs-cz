---
title: Inherits – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: 6e6e9cc9210232059210862f2bda691c57b372d6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353230"
---
# <a name="inherits-statement"></a><span data-ttu-id="e3aee-102">Inherits – příkaz</span><span class="sxs-lookup"><span data-stu-id="e3aee-102">Inherits Statement</span></span>
<span data-ttu-id="e3aee-103">Způsobí, že aktuální třída nebo rozhraní zdědí atributy, proměnné, vlastnosti, procedury a události z jiné třídy nebo sady rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e3aee-103">Causes the current class or interface to inherit the attributes, variables, properties, procedures, and events from another class or set of interfaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3aee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3aee-104">Syntax</span></span>  
  
```vb  
Inherits basetypenames  
```  
  
## <a name="parts"></a><span data-ttu-id="e3aee-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="e3aee-105">Parts</span></span>  
  
|<span data-ttu-id="e3aee-106">Termín</span><span class="sxs-lookup"><span data-stu-id="e3aee-106">Term</span></span>|<span data-ttu-id="e3aee-107">Definice</span><span class="sxs-lookup"><span data-stu-id="e3aee-107">Definition</span></span>|  
|---|---|  
|`basetypenames`|<span data-ttu-id="e3aee-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e3aee-108">Required.</span></span> <span data-ttu-id="e3aee-109">Název třídy, ze které je tato třída odvozena.</span><span class="sxs-lookup"><span data-stu-id="e3aee-109">The name of the class from which this class derives.</span></span><br /><br /> <span data-ttu-id="e3aee-110">-nebo-</span><span class="sxs-lookup"><span data-stu-id="e3aee-110">-or-</span></span><br /><br /> <span data-ttu-id="e3aee-111">Názvy rozhraní, ze kterých je toto rozhraní odvozeno.</span><span class="sxs-lookup"><span data-stu-id="e3aee-111">The names of the interfaces from which this interface derives.</span></span> <span data-ttu-id="e3aee-112">K oddělení více názvů použijte čárky.</span><span class="sxs-lookup"><span data-stu-id="e3aee-112">Use commas to separate multiple names.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3aee-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e3aee-113">Remarks</span></span>  
 <span data-ttu-id="e3aee-114">V případě použití musí být příkaz `Inherits` prvním neprázdným řádkem bez komentářů v definici třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e3aee-114">If used, the `Inherits` statement must be the first non-blank, non-comment line in a class or interface definition.</span></span> <span data-ttu-id="e3aee-115">Měla by následovat bezprostředně po příkazu `Class` nebo `Interface`.</span><span class="sxs-lookup"><span data-stu-id="e3aee-115">It should immediately follow the `Class` or `Interface` statement.</span></span>  
  
 <span data-ttu-id="e3aee-116">`Inherits` lze použít pouze ve třídě nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e3aee-116">You can use `Inherits` only in a class or interface.</span></span> <span data-ttu-id="e3aee-117">To znamená, že kontext deklarace pro dědičnost nemůže být zdrojový soubor, obor názvů, struktura, modul, procedura nebo blok.</span><span class="sxs-lookup"><span data-stu-id="e3aee-117">This means the declaration context for an inheritance cannot be a source file, namespace, structure, module, procedure, or block.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="e3aee-118">Pravidla</span><span class="sxs-lookup"><span data-stu-id="e3aee-118">Rules</span></span>  
  
- <span data-ttu-id="e3aee-119">**Dědičnost tříd.**</span><span class="sxs-lookup"><span data-stu-id="e3aee-119">**Class Inheritance.**</span></span> <span data-ttu-id="e3aee-120">Pokud třída používá příkaz `Inherits`, můžete zadat pouze jednu základní třídu.</span><span class="sxs-lookup"><span data-stu-id="e3aee-120">If a class uses the `Inherits` statement, you can specify only one base class.</span></span>  
  
     <span data-ttu-id="e3aee-121">Třída nemůže dědit z třídy, ve které je vnořená.</span><span class="sxs-lookup"><span data-stu-id="e3aee-121">A class cannot inherit from a class nested within it.</span></span>  
  
- <span data-ttu-id="e3aee-122">**Dědičnost rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="e3aee-122">**Interface Inheritance.**</span></span> <span data-ttu-id="e3aee-123">Pokud rozhraní používá příkaz `Inherits`, můžete zadat jedno nebo více základních rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e3aee-123">If an interface uses the `Inherits` statement, you can specify one or more base interfaces.</span></span> <span data-ttu-id="e3aee-124">Můžete Zdědit ze dvou rozhraní i v případě, že každý definuje člena se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="e3aee-124">You can inherit from two interfaces even if they each define a member with the same name.</span></span> <span data-ttu-id="e3aee-125">Pokud to uděláte, implementace kódu musí použít kvalifikaci názvu k určení, který člen implementuje.</span><span class="sxs-lookup"><span data-stu-id="e3aee-125">If you do so, the implementing code must use name qualification to specify which member it is implementing.</span></span>  
  
     <span data-ttu-id="e3aee-126">Rozhraní nemůže dědit z jiného rozhraní s více omezující úrovní přístupu.</span><span class="sxs-lookup"><span data-stu-id="e3aee-126">An interface cannot inherit from another interface with a more restrictive access level.</span></span> <span data-ttu-id="e3aee-127">Rozhraní `Public` například nemůže dědit z rozhraní `Friend`.</span><span class="sxs-lookup"><span data-stu-id="e3aee-127">For example, a `Public` interface cannot inherit from a `Friend` interface.</span></span>  
  
     <span data-ttu-id="e3aee-128">Rozhraní nemůže dědit z rozhraní, které je v něm vnořené.</span><span class="sxs-lookup"><span data-stu-id="e3aee-128">An interface cannot inherit from an interface nested within it.</span></span>  
  
 <span data-ttu-id="e3aee-129">Příkladem dědičnosti třídy v .NET Framework je <xref:System.ArgumentException> třída, která dědí z třídy <xref:System.SystemException>.</span><span class="sxs-lookup"><span data-stu-id="e3aee-129">An example of class inheritance in the .NET Framework is the <xref:System.ArgumentException> class, which inherits from the <xref:System.SystemException> class.</span></span> <span data-ttu-id="e3aee-130">To umožňuje <xref:System.ArgumentException> všechny předdefinované vlastnosti a procedury vyžadované systémovými výjimkami, jako je například vlastnost <xref:System.Exception.Message%2A> a metoda <xref:System.Exception.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="e3aee-130">This provides to <xref:System.ArgumentException> all the predefined properties and procedures required by system exceptions, such as the <xref:System.Exception.Message%2A> property and the <xref:System.Exception.ToString%2A> method.</span></span>  
  
 <span data-ttu-id="e3aee-131">Příkladem dědičnosti rozhraní v .NET Framework je rozhraní <xref:System.Collections.ICollection>, které dědí z rozhraní <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="e3aee-131">An example of interface inheritance in the .NET Framework is the <xref:System.Collections.ICollection> interface, which inherits from the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="e3aee-132">To způsobí, <xref:System.Collections.ICollection> dědění definice výčtu potřebného k procházení kolekce.</span><span class="sxs-lookup"><span data-stu-id="e3aee-132">This causes <xref:System.Collections.ICollection> to inherit the definition of the enumerator required to traverse a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3aee-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="e3aee-133">Example</span></span>  
 <span data-ttu-id="e3aee-134">Následující příklad používá příkaz `Inherits` k zobrazení, jak třída s názvem `thisClass` může dědit všechny členy základní třídy s názvem `anotherClass`.</span><span class="sxs-lookup"><span data-stu-id="e3aee-134">The following example uses the `Inherits` statement to show how a class named `thisClass` can inherit all the members of a base class named `anotherClass`.</span></span>  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="e3aee-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="e3aee-135">Example</span></span>  
 <span data-ttu-id="e3aee-136">Následující příklad ukazuje dědění více rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e3aee-136">The following example shows inheritance of multiple interfaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 <span data-ttu-id="e3aee-137">Rozhraní s názvem `thisInterface` nyní zahrnuje všechny definice v rozhraních <xref:System.IComparable>, <xref:System.IDisposable>a <xref:System.IFormattable> zděděné členy v uvedeném pořadí pro porovnání dvou objektů, uvolnění přidělených prostředků a vyjádření hodnoty objektu jako `String`.</span><span class="sxs-lookup"><span data-stu-id="e3aee-137">The interface named `thisInterface` now includes all the definitions in the <xref:System.IComparable>, <xref:System.IDisposable>, and <xref:System.IFormattable> interfaces The inherited members provide respectively for type-specific comparison of two objects, releasing allocated resources, and expressing the value of an object as a `String`.</span></span> <span data-ttu-id="e3aee-138">Třída, která implementuje `thisInterface` musí implementovat všechny členy každého základního rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e3aee-138">A class that implements `thisInterface` must implement every member of every base interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3aee-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3aee-139">See also</span></span>

- [<span data-ttu-id="e3aee-140">MustInherit</span><span class="sxs-lookup"><span data-stu-id="e3aee-140">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [<span data-ttu-id="e3aee-141">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="e3aee-141">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="e3aee-142">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="e3aee-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="e3aee-143">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="e3aee-143">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="e3aee-144">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="e3aee-144">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
