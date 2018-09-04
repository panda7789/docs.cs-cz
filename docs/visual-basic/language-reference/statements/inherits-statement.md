---
title: Inherits – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: 4a98ada39a04730b46f40fe139e72d1855d9b067
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43533245"
---
# <a name="inherits-statement"></a><span data-ttu-id="4f225-102">Inherits – příkaz</span><span class="sxs-lookup"><span data-stu-id="4f225-102">Inherits Statement</span></span>
<span data-ttu-id="4f225-103">Způsobí, že aktuální třída nebo rozhraní zdědí atributy, proměnné, vlastnosti, procedury a události z jiné třídy nebo sady rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4f225-103">Causes the current class or interface to inherit the attributes, variables, properties, procedures, and events from another class or set of interfaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f225-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f225-104">Syntax</span></span>  
  
```  
Inherits basetypenames  
```  
  
## <a name="parts"></a><span data-ttu-id="4f225-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="4f225-105">Parts</span></span>  
  
|<span data-ttu-id="4f225-106">Termín</span><span class="sxs-lookup"><span data-stu-id="4f225-106">Term</span></span>|<span data-ttu-id="4f225-107">Definice</span><span class="sxs-lookup"><span data-stu-id="4f225-107">Definition</span></span>|  
|---|---|  
|`basetypenames`|<span data-ttu-id="4f225-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="4f225-108">Required.</span></span> <span data-ttu-id="4f225-109">Název třídy, ze kterého tato třída odvozená.</span><span class="sxs-lookup"><span data-stu-id="4f225-109">The name of the class from which this class derives.</span></span><br /><br /> <span data-ttu-id="4f225-110">-nebo-</span><span class="sxs-lookup"><span data-stu-id="4f225-110">-or-</span></span><br /><br /> <span data-ttu-id="4f225-111">Názvy rozhraní, ze kterých tato rozhraní je odvozena.</span><span class="sxs-lookup"><span data-stu-id="4f225-111">The names of the interfaces from which this interface derives.</span></span> <span data-ttu-id="4f225-112">Použijte čárky k oddělení více názvů.</span><span class="sxs-lookup"><span data-stu-id="4f225-112">Use commas to separate multiple names.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f225-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4f225-113">Remarks</span></span>  
 <span data-ttu-id="4f225-114">Pokud použijete, `Inherits` příkaz musí být na prvním řádku neprázdné, mimo komentář v definici třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4f225-114">If used, the `Inherits` statement must be the first non-blank, non-comment line in a class or interface definition.</span></span> <span data-ttu-id="4f225-115">Měla by odpovídat okamžitě `Class` nebo `Interface` příkazu.</span><span class="sxs-lookup"><span data-stu-id="4f225-115">It should immediately follow the `Class` or `Interface` statement.</span></span>  
  
 <span data-ttu-id="4f225-116">Můžete použít `Inherits` pouze ve třídě nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4f225-116">You can use `Inherits` only in a class or interface.</span></span> <span data-ttu-id="4f225-117">To znamená, že se že kontext deklarace pro dědičnosti nesmí být zdrojový soubor, obor názvů, struktura, modulu, procedura nebo blok.</span><span class="sxs-lookup"><span data-stu-id="4f225-117">This means the declaration context for an inheritance cannot be a source file, namespace, structure, module, procedure, or block.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="4f225-118">pravidla</span><span class="sxs-lookup"><span data-stu-id="4f225-118">Rules</span></span>  
  
-   <span data-ttu-id="4f225-119">**Dědičnost tříd.**</span><span class="sxs-lookup"><span data-stu-id="4f225-119">**Class Inheritance.**</span></span> <span data-ttu-id="4f225-120">Pokud používá třídu `Inherits` příkazu, můžete zadat pouze jednu základní třídu.</span><span class="sxs-lookup"><span data-stu-id="4f225-120">If a class uses the `Inherits` statement, you can specify only one base class.</span></span>  
  
     <span data-ttu-id="4f225-121">Třída nemůže dědit ze třídy do něho vnořený.</span><span class="sxs-lookup"><span data-stu-id="4f225-121">A class cannot inherit from a class nested within it.</span></span>  
  
-   <span data-ttu-id="4f225-122">**Rozhraní dědičnosti.**</span><span class="sxs-lookup"><span data-stu-id="4f225-122">**Interface Inheritance.**</span></span> <span data-ttu-id="4f225-123">Pokud používáte rozhraní `Inherits` příkazu, můžete určit jeden nebo více základních rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4f225-123">If an interface uses the `Inherits` statement, you can specify one or more base interfaces.</span></span> <span data-ttu-id="4f225-124">Může dědit z dvě rozhraní, i když každá definovat člen se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="4f225-124">You can inherit from two interfaces even if they each define a member with the same name.</span></span> <span data-ttu-id="4f225-125">Pokud tak učiníte, implementující kód používaly kvalifikace názvu určete člen implementuje.</span><span class="sxs-lookup"><span data-stu-id="4f225-125">If you do so, the implementing code must use name qualification to specify which member it is implementing.</span></span>  
  
     <span data-ttu-id="4f225-126">Rozhraní nemůže dědit z jiného rozhraní s více omezující úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="4f225-126">An interface cannot inherit from another interface with a more restrictive access level.</span></span> <span data-ttu-id="4f225-127">Například `Public` rozhraní nemůže dědit od třídy `Friend` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4f225-127">For example, a `Public` interface cannot inherit from a `Friend` interface.</span></span>  
  
     <span data-ttu-id="4f225-128">Rozhraní nemůže dědit z rozhraní do něho vnořený.</span><span class="sxs-lookup"><span data-stu-id="4f225-128">An interface cannot inherit from an interface nested within it.</span></span>  
  
 <span data-ttu-id="4f225-129">Je například dědičnost třídy v rozhraní .NET Framework <xref:System.ArgumentException> třída, která dědí z <xref:System.SystemException> třídy.</span><span class="sxs-lookup"><span data-stu-id="4f225-129">An example of class inheritance in the .NET Framework is the <xref:System.ArgumentException> class, which inherits from the <xref:System.SystemException> class.</span></span> <span data-ttu-id="4f225-130">To poskytuje <xref:System.ArgumentException> předdefinované vlastnosti a postupy vyžadované výjimek systému, například <xref:System.Exception.Message%2A> vlastnost a <xref:System.Exception.ToString%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="4f225-130">This provides to <xref:System.ArgumentException> all the predefined properties and procedures required by system exceptions, such as the <xref:System.Exception.Message%2A> property and the <xref:System.Exception.ToString%2A> method.</span></span>  
  
 <span data-ttu-id="4f225-131">Je například dědičnost rozhraní v rozhraní .NET Framework <xref:System.Collections.ICollection> rozhraní, která dědí z <xref:System.Collections.IEnumerable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4f225-131">An example of interface inheritance in the .NET Framework is the <xref:System.Collections.ICollection> interface, which inherits from the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="4f225-132">To způsobí, že <xref:System.Collections.ICollection> dědění definice výčtu je vyžadováno k procházení kolekce.</span><span class="sxs-lookup"><span data-stu-id="4f225-132">This causes <xref:System.Collections.ICollection> to inherit the definition of the enumerator required to traverse a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f225-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="4f225-133">Example</span></span>  
 <span data-ttu-id="4f225-134">V následujícím příkladu `Inherits` příkaz Zobrazit jak třída s názvem `thisClass` může dědit všechny členy základní třídy s názvem `anotherClass`.</span><span class="sxs-lookup"><span data-stu-id="4f225-134">The following example uses the `Inherits` statement to show how a class named `thisClass` can inherit all the members of a base class named `anotherClass`.</span></span>  
  
 [!code-vb[VbVbalrStatements#37](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="4f225-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="4f225-135">Example</span></span>  
 <span data-ttu-id="4f225-136">Následující příklad ukazuje dědičnosti více rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4f225-136">The following example shows inheritance of multiple interfaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#38](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_2.vb)]  
  
 <span data-ttu-id="4f225-137">Rozhraní s názvem `thisInterface` teď obsahuje všechny definice v <xref:System.IComparable>, <xref:System.IDisposable>, a <xref:System.IFormattable> rozhraní zděděných členů poskytují v uvedeném pořadí pro konkrétní typ porovnání dvou objektů uvolnění při přidělování prostředků a vyjádření hodnoty objektu jako `String`.</span><span class="sxs-lookup"><span data-stu-id="4f225-137">The interface named `thisInterface` now includes all the definitions in the <xref:System.IComparable>, <xref:System.IDisposable>, and <xref:System.IFormattable> interfaces The inherited members provide respectively for type-specific comparison of two objects, releasing allocated resources, and expressing the value of an object as a `String`.</span></span> <span data-ttu-id="4f225-138">Třídu, která implementuje `thisInterface` musíte implementovat každého člena každé základní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4f225-138">A class that implements `thisInterface` must implement every member of every base interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f225-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="4f225-139">See Also</span></span>  
 [<span data-ttu-id="4f225-140">MustInherit</span><span class="sxs-lookup"><span data-stu-id="4f225-140">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
 [<span data-ttu-id="4f225-141">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="4f225-141">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [<span data-ttu-id="4f225-142">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="4f225-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="4f225-143">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="4f225-143">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="4f225-144">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="4f225-144">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
