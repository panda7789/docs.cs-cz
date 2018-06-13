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
ms.openlocfilehash: 43a8aa4e9e04ee035cb52e9f829de13e5c022217
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604338"
---
# <a name="inherits-statement"></a><span data-ttu-id="6e1c8-102">Inherits – příkaz</span><span class="sxs-lookup"><span data-stu-id="6e1c8-102">Inherits Statement</span></span>
<span data-ttu-id="6e1c8-103">Způsobí, že aktuální třídy nebo rozhraní dědění atributy, proměnné, vlastnosti, postupy a události z jiné třídy nebo sadu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-103">Causes the current class or interface to inherit the attributes, variables, properties, procedures, and events from another class or set of interfaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e1c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e1c8-104">Syntax</span></span>  
  
```  
Inherits basetypenames  
```  
  
## <a name="parts"></a><span data-ttu-id="6e1c8-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="6e1c8-105">Parts</span></span>  
  
|<span data-ttu-id="6e1c8-106">Termín</span><span class="sxs-lookup"><span data-stu-id="6e1c8-106">Term</span></span>|<span data-ttu-id="6e1c8-107">Definice</span><span class="sxs-lookup"><span data-stu-id="6e1c8-107">Definition</span></span>|  
|---|---|  
|`basetypenames`|<span data-ttu-id="6e1c8-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-108">Required.</span></span> <span data-ttu-id="6e1c8-109">Název třídy, ze které je tato třída odvozena.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-109">The name of the class from which this class derives.</span></span><br /><br /> <span data-ttu-id="6e1c8-110">-nebo-</span><span class="sxs-lookup"><span data-stu-id="6e1c8-110">-or-</span></span><br /><br /> <span data-ttu-id="6e1c8-111">Názvy rozhraní, ze kterých je odvozena toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-111">The names of the interfaces from which this interface derives.</span></span> <span data-ttu-id="6e1c8-112">K oddělení více názvů používejte čárky.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-112">Use commas to separate multiple names.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e1c8-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6e1c8-113">Remarks</span></span>  
 <span data-ttu-id="6e1c8-114">Pokud se používá, `Inherits` příkaz musí být první neprázdné, bez komentář řádek v definici třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-114">If used, the `Inherits` statement must be the first non-blank, non-comment line in a class or interface definition.</span></span> <span data-ttu-id="6e1c8-115">Okamžitě postupujte `Class` nebo `Interface` příkaz.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-115">It should immediately follow the `Class` or `Interface` statement.</span></span>  
  
 <span data-ttu-id="6e1c8-116">Můžete použít `Inherits` pouze ve třídě nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-116">You can use `Inherits` only in a class or interface.</span></span> <span data-ttu-id="6e1c8-117">To znamená, že deklarace kontext dědičnosti nesmí být zdrojový soubor, obor názvů, struktura, modul, postup nebo bloku.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-117">This means the declaration context for an inheritance cannot be a source file, namespace, structure, module, procedure, or block.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="6e1c8-118">Pravidla</span><span class="sxs-lookup"><span data-stu-id="6e1c8-118">Rules</span></span>  
  
-   <span data-ttu-id="6e1c8-119">**Dědičnost tříd.**</span><span class="sxs-lookup"><span data-stu-id="6e1c8-119">**Class Inheritance.**</span></span> <span data-ttu-id="6e1c8-120">Pokud používá třídu `Inherits` prohlášení, můžete zadat pouze jeden základní třídu.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-120">If a class uses the `Inherits` statement, you can specify only one base class.</span></span>  
  
     <span data-ttu-id="6e1c8-121">Třída nemůže Zdědit z ní vnořené třídy.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-121">A class cannot inherit from a class nested within it.</span></span>  
  
-   <span data-ttu-id="6e1c8-122">**Rozhraní dědičnosti.**</span><span class="sxs-lookup"><span data-stu-id="6e1c8-122">**Interface Inheritance.**</span></span> <span data-ttu-id="6e1c8-123">Pokud používá rozhraní `Inherits` prohlášení, můžete určit jeden nebo více základní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-123">If an interface uses the `Inherits` statement, you can specify one or more base interfaces.</span></span> <span data-ttu-id="6e1c8-124">Může dědit z dvě rozhraní, i v případě, že každý definují člen se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-124">You can inherit from two interfaces even if they each define a member with the same name.</span></span> <span data-ttu-id="6e1c8-125">Pokud tak učiníte, implementující kód musíte použít kvalifikace názvu k určení členů, které implementuje.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-125">If you do so, the implementing code must use name qualification to specify which member it is implementing.</span></span>  
  
     <span data-ttu-id="6e1c8-126">Rozhraní nemůže Zdědit z jiné rozhraní s více omezující úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-126">An interface cannot inherit from another interface with a more restrictive access level.</span></span> <span data-ttu-id="6e1c8-127">Například `Public` rozhraní nemůže Zdědit z `Friend` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-127">For example, a `Public` interface cannot inherit from a `Friend` interface.</span></span>  
  
     <span data-ttu-id="6e1c8-128">Rozhraní nemůže Zdědit z ní vnořené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-128">An interface cannot inherit from an interface nested within it.</span></span>  
  
 <span data-ttu-id="6e1c8-129">Je například dědění tříd v rozhraní .NET Framework <xref:System.ArgumentException> třídy, která dědí z <xref:System.SystemException> třídy.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-129">An example of class inheritance in the .NET Framework is the <xref:System.ArgumentException> class, which inherits from the <xref:System.SystemException> class.</span></span> <span data-ttu-id="6e1c8-130">To poskytuje <xref:System.ArgumentException> všechny předdefinované vlastnosti a postupy vyžadované výjimky systému, jako <xref:System.Exception.Message%2A> vlastnost a <xref:System.Exception.ToString%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-130">This provides to <xref:System.ArgumentException> all the predefined properties and procedures required by system exceptions, such as the <xref:System.Exception.Message%2A> property and the <xref:System.Exception.ToString%2A> method.</span></span>  
  
 <span data-ttu-id="6e1c8-131">Je například rozhraní dědičnosti v rozhraní .NET Framework <xref:System.Collections.ICollection> rozhraní, které dědí z <xref:System.Collections.IEnumerable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-131">An example of interface inheritance in the .NET Framework is the <xref:System.Collections.ICollection> interface, which inherits from the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="6e1c8-132">To způsobí, že <xref:System.Collections.ICollection> dědění definici enumerátor požadované procházení kolekce.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-132">This causes <xref:System.Collections.ICollection> to inherit the definition of the enumerator required to traverse a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e1c8-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="6e1c8-133">Example</span></span>  
 <span data-ttu-id="6e1c8-134">Následující příklad používá `Inherits` příkaz, který má zobrazit, jak třída s názvem `thisClass` může dědit vlastnosti všechny členy základní třídy s názvem `anotherClass`.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-134">The following example uses the `Inherits` statement to show how a class named `thisClass` can inherit all the members of a base class named `anotherClass`.</span></span>  
  
 [!code-vb[VbVbalrStatements#37](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="6e1c8-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="6e1c8-135">Example</span></span>  
 <span data-ttu-id="6e1c8-136">Následující příklad ukazuje dědičnosti více rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-136">The following example shows inheritance of multiple interfaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#38](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_2.vb)]  
  
 <span data-ttu-id="6e1c8-137">Rozhraní s názvem `thisInterface` nyní zahrnuje všechny definice v <xref:System.IComparable>, <xref:System.IDisposable>, a <xref:System.IFormattable> rozhraní zděděné členy zadejte v uvedeném pořadí pro konkrétní typ porovnání dva objekty, vydání přidělené prostředky a vyjadřující hodnotu objektu jako `String`.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-137">The interface named `thisInterface` now includes all the definitions in the <xref:System.IComparable>, <xref:System.IDisposable>, and <xref:System.IFormattable> interfaces The inherited members provide respectively for type-specific comparison of two objects, releasing allocated resources, and expressing the value of an object as a `String`.</span></span> <span data-ttu-id="6e1c8-138">Třídu, která implementuje `thisInterface` musí implementovat každého člena každé základní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-138">A class that implements `thisInterface` must implement every member of every base interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e1c8-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e1c8-139">See Also</span></span>  
 [<span data-ttu-id="6e1c8-140">MustInherit</span><span class="sxs-lookup"><span data-stu-id="6e1c8-140">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
 [<span data-ttu-id="6e1c8-141">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="6e1c8-141">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [<span data-ttu-id="6e1c8-142">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="6e1c8-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="6e1c8-143">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="6e1c8-143">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="6e1c8-144">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e1c8-144">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
