---
title: Partial (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Partial
- partial
helpviewer_keywords:
- structures [Visual Basic], partial
- classes [Visual Basic]
- partial, types [Visual Basic]
- partial, structures
- partial, classes [Visual Basic]
- classes [Visual Basic], partial
- Partial keyword [Visual Basic]
- type promotion
ms.assetid: 7adaef80-f435-46e1-970a-269fff63b448
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5129ef7737b1b07317d47f8d18e9aceb668bf05a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="partial-visual-basic"></a><span data-ttu-id="f0f60-102">Partial (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0f60-102">Partial (Visual Basic)</span></span>
<span data-ttu-id="f0f60-103">Označuje, že je typ deklarace částečnou definici typu.</span><span class="sxs-lookup"><span data-stu-id="f0f60-103">Indicates that a type declaration is a partial definition of the type.</span></span>  
  
 <span data-ttu-id="f0f60-104">Definici typu mezi několik deklarace můžete rozdělit pomocí `Partial` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="f0f60-104">You can divide the definition of a type among several declarations by using the `Partial` keyword.</span></span> <span data-ttu-id="f0f60-105">Můžete vytvořit tolik částečné deklarace tak, jak chcete v tolik jiných zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="f0f60-105">You can use as many partial declarations as you want, in as many different source files as you want.</span></span> <span data-ttu-id="f0f60-106">Všechny deklarace však musí být ve stejném sestavení a o stejný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="f0f60-106">However, all the declarations must be in the same assembly and the same namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0f60-107">Visual Basic podporuje *částečné metody*, které jsou obvykle implementované v částečné třídy.</span><span class="sxs-lookup"><span data-stu-id="f0f60-107">Visual Basic supports *partial methods*, which are typically implemented in partial classes.</span></span> <span data-ttu-id="f0f60-108">Další informace najdete v tématu [částečné metody](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) a [Sub – příkaz](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f0f60-108">For more information, see [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0f60-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0f60-109">Syntax</span></span>  
  
```  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a><span data-ttu-id="f0f60-110">Součásti</span><span class="sxs-lookup"><span data-stu-id="f0f60-110">Parts</span></span>  
  
|<span data-ttu-id="f0f60-111">Termín</span><span class="sxs-lookup"><span data-stu-id="f0f60-111">Term</span></span>|<span data-ttu-id="f0f60-112">Definice</span><span class="sxs-lookup"><span data-stu-id="f0f60-112">Definition</span></span>|  
|---|---|  
|`attrlist`|<span data-ttu-id="f0f60-113">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f0f60-113">Optional.</span></span> <span data-ttu-id="f0f60-114">Seznam atributů, které se vztahují k tomuto typu.</span><span class="sxs-lookup"><span data-stu-id="f0f60-114">List of attributes that apply to this type.</span></span> <span data-ttu-id="f0f60-115">Je nutné uzavřít [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md) v lomených závorkách (`< >`).</span><span class="sxs-lookup"><span data-stu-id="f0f60-115">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets (`< >`).</span></span>|  
|`accessmodifier`|<span data-ttu-id="f0f60-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f0f60-116">Optional.</span></span> <span data-ttu-id="f0f60-117">Určuje, jaký kód můžete přístup tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="f0f60-117">Specifies what code can access this type.</span></span> <span data-ttu-id="f0f60-118">V tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="f0f60-118">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`Shadows`|<span data-ttu-id="f0f60-119">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f0f60-119">Optional.</span></span> <span data-ttu-id="f0f60-120">V tématu [stínů](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="f0f60-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>|  
|`MustInherit`|<span data-ttu-id="f0f60-121">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f0f60-121">Optional.</span></span> <span data-ttu-id="f0f60-122">V tématu [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="f0f60-122">See [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>|  
|`NotInheritable`|<span data-ttu-id="f0f60-123">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f0f60-123">Optional.</span></span> <span data-ttu-id="f0f60-124">V tématu [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span><span class="sxs-lookup"><span data-stu-id="f0f60-124">See [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span></span>|  
|`name`|<span data-ttu-id="f0f60-125">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="f0f60-125">Required.</span></span> <span data-ttu-id="f0f60-126">Název tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="f0f60-126">Name of this type.</span></span> <span data-ttu-id="f0f60-127">Musí odpovídat názvu definována v jiné částečné deklarace stejného typu.</span><span class="sxs-lookup"><span data-stu-id="f0f60-127">Must match the name defined in all other partial declarations of the same type.</span></span>|  
|`Of`|<span data-ttu-id="f0f60-128">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f0f60-128">Optional.</span></span> <span data-ttu-id="f0f60-129">Určuje, že se jedná o obecného typu.</span><span class="sxs-lookup"><span data-stu-id="f0f60-129">Specifies that this is a generic type.</span></span> <span data-ttu-id="f0f60-130">V tématu [obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="f0f60-130">See [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>|  
|`typelist`|<span data-ttu-id="f0f60-131">Vyžaduje, pokud použijete [z](../../../visual-basic/language-reference/statements/of-clause.md).</span><span class="sxs-lookup"><span data-stu-id="f0f60-131">Required if you use [Of](../../../visual-basic/language-reference/statements/of-clause.md).</span></span> <span data-ttu-id="f0f60-132">V tématu [zadejte seznam](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="f0f60-132">See [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>|  
|`Inherits`|<span data-ttu-id="f0f60-133">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f0f60-133">Optional.</span></span> <span data-ttu-id="f0f60-134">V tématu [Inherits – příkaz](../../../visual-basic/language-reference/statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f0f60-134">See [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md).</span></span>|  
|`classname`|<span data-ttu-id="f0f60-135">Vyžaduje, pokud použijete `Inherits`.</span><span class="sxs-lookup"><span data-stu-id="f0f60-135">Required if you use `Inherits`.</span></span> <span data-ttu-id="f0f60-136">Název třídy nebo rozhraní, ze které je tato třída odvozena.</span><span class="sxs-lookup"><span data-stu-id="f0f60-136">The name of the class or interface from which this class derives.</span></span>|  
|`Implements`|<span data-ttu-id="f0f60-137">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f0f60-137">Optional.</span></span> <span data-ttu-id="f0f60-138">V tématu [implementuje příkaz](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f0f60-138">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>|  
|`interfacenames`|<span data-ttu-id="f0f60-139">Vyžaduje, pokud použijete `Implements`.</span><span class="sxs-lookup"><span data-stu-id="f0f60-139">Required if you use `Implements`.</span></span> <span data-ttu-id="f0f60-140">Názvy rozhraní, které implementuje tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="f0f60-140">The names of the interfaces this type implements.</span></span>|  
|`variabledeclarations`|<span data-ttu-id="f0f60-141">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f0f60-141">Optional.</span></span> <span data-ttu-id="f0f60-142">Příkazy, které deklarace další proměnné a událostí pro typ.</span><span class="sxs-lookup"><span data-stu-id="f0f60-142">Statements which declare additional variables and events for the type.</span></span>|  
|`proceduredeclarations`|<span data-ttu-id="f0f60-143">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f0f60-143">Optional.</span></span> <span data-ttu-id="f0f60-144">Příkazy, které deklarace a definice dalších kroků pro typ.</span><span class="sxs-lookup"><span data-stu-id="f0f60-144">Statements which declare and define additional procedures for the type.</span></span>|  
|<span data-ttu-id="f0f60-145">`End Class`nebo`End Structure`</span><span class="sxs-lookup"><span data-stu-id="f0f60-145">`End Class` or `End Structure`</span></span>|<span data-ttu-id="f0f60-146">Ukončí toto částečné `Class` nebo `Structure` definice.</span><span class="sxs-lookup"><span data-stu-id="f0f60-146">Ends this partial `Class` or `Structure` definition.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0f60-147">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f0f60-147">Remarks</span></span>  
 <span data-ttu-id="f0f60-148">Visual Basic používá definice částečné třídy pro oddělení generovaného kódu z kódu uživatelem definovaných v samostatných zdrojové soubory.</span><span class="sxs-lookup"><span data-stu-id="f0f60-148">Visual Basic uses partial-class definitions to separate generated code from user-authored code in separate source files.</span></span> <span data-ttu-id="f0f60-149">Například **Windows Form Designer** definuje částečné třídy pro ovládací prvky, jako <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="f0f60-149">For example, the **Windows Form Designer** defines partial classes for controls such as <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="f0f60-150">Neměli upravovat generovaného kódu v těchto ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="f0f60-150">You should not modify the generated code in these controls.</span></span>  
  
 <span data-ttu-id="f0f60-151">Všechna pravidla pro třídy, struktury, rozhraní a vytváření modulu, třeba kroky týkající se použití modifikátor a dědičnost, použít při vytváření typu částečné.</span><span class="sxs-lookup"><span data-stu-id="f0f60-151">All the rules for class, structure, interface, and module creation, such as those for modifier usage and inheritance, apply when creating a partial type.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="f0f60-152">Doporučené postupy</span><span class="sxs-lookup"><span data-stu-id="f0f60-152">Best Practices</span></span>  
  
-   <span data-ttu-id="f0f60-153">Za normálních podmínek by neměl rozdělit vývoj jednoho typu do dvou nebo více deklarace.</span><span class="sxs-lookup"><span data-stu-id="f0f60-153">Under normal circumstances, you should not split the development of a single type across two or more declarations.</span></span> <span data-ttu-id="f0f60-154">Proto ve většině případů není třeba `Partial` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="f0f60-154">Therefore, in most cases you do not need the `Partial` keyword.</span></span>  
  
-   <span data-ttu-id="f0f60-155">Čitelnější, by měly obsahovat všechny částečné deklaraci typu `Partial` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="f0f60-155">For readability, every partial declaration of a type should include the `Partial` keyword.</span></span> <span data-ttu-id="f0f60-156">Kompilátor umožňuje maximálně jeden částečné deklarace vynechat – klíčové slovo; Pokud dva nebo více vynechejte kompilátor nevydá signál k chybě.</span><span class="sxs-lookup"><span data-stu-id="f0f60-156">The compiler allows at most one partial declaration to omit the keyword; if two or more omit it the compiler signals an error.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="f0f60-157">Chování</span><span class="sxs-lookup"><span data-stu-id="f0f60-157">Behavior</span></span>  
  
-   <span data-ttu-id="f0f60-158">**Sjednocení deklarace.**</span><span class="sxs-lookup"><span data-stu-id="f0f60-158">**Union of Declarations.**</span></span> <span data-ttu-id="f0f60-159">Kompilátor považuje za sjednocení všech částečné deklarace typu.</span><span class="sxs-lookup"><span data-stu-id="f0f60-159">The compiler treats the type as the union of all its partial declarations.</span></span> <span data-ttu-id="f0f60-160">Každý modifikátor z každé částečné definice platí pro celý typ a každý člen z každé částečné definice je k dispozici pro celý typ.</span><span class="sxs-lookup"><span data-stu-id="f0f60-160">Every modifier from every partial definition applies to the entire type, and every member from every partial definition is available to the entire type.</span></span>  
  
-   <span data-ttu-id="f0f60-161">**Propagace typu není povoleno pro částečné typů v modulech.**</span><span class="sxs-lookup"><span data-stu-id="f0f60-161">**Type Promotion Not Allowed For Partial Types in Modules.**</span></span> <span data-ttu-id="f0f60-162">Pokud definici částečné uvnitř modulu, typu povýšení tohoto typu je automaticky nepotlačí.</span><span class="sxs-lookup"><span data-stu-id="f0f60-162">If a partial definition is inside a module, type promotion of that type is automatically defeated.</span></span> <span data-ttu-id="f0f60-163">V takovém případě sadu částečné definice může způsobit neočekávané výsledky a i chyby kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="f0f60-163">In such a case, a set of partial definitions can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="f0f60-164">Další informace najdete v tématu [propagace typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="f0f60-164">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
     <span data-ttu-id="f0f60-165">Kompilátor sloučí částečné definice jenom v případě, že jsou identické jejich plně kvalifikované cesty.</span><span class="sxs-lookup"><span data-stu-id="f0f60-165">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
 <span data-ttu-id="f0f60-166">`Partial` – Klíčové slovo lze použít v těchto kontexty:</span><span class="sxs-lookup"><span data-stu-id="f0f60-166">The `Partial` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="f0f60-167">Class – příkaz</span><span class="sxs-lookup"><span data-stu-id="f0f60-167">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="f0f60-168">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="f0f60-168">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a><span data-ttu-id="f0f60-169">Příklad</span><span class="sxs-lookup"><span data-stu-id="f0f60-169">Example</span></span>  
 <span data-ttu-id="f0f60-170">Následující příklad rozdělí definice třídy `sampleClass` do dvou deklarace, z nichž každý definuje jiné `Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="f0f60-170">The following example splits the definition of class `sampleClass` into two declarations, each of which defines a different `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrKeywords#3](../../../visual-basic/language-reference/codesnippet/VisualBasic/partial_1.vb)]  
  
 <span data-ttu-id="f0f60-171">Dva částečné definice v předchozím příkladu může být ve stejném souboru zdroje nebo ve dvou různých zdrojové soubory.</span><span class="sxs-lookup"><span data-stu-id="f0f60-171">The two partial definitions in the preceding example could be in the same source file or in two different source files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0f60-172">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0f60-172">See Also</span></span>  
 [<span data-ttu-id="f0f60-173">Class – příkaz</span><span class="sxs-lookup"><span data-stu-id="f0f60-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="f0f60-174">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="f0f60-174">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="f0f60-175">Propagace typu</span><span class="sxs-lookup"><span data-stu-id="f0f60-175">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)  
 [<span data-ttu-id="f0f60-176">Stínů</span><span class="sxs-lookup"><span data-stu-id="f0f60-176">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="f0f60-177">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f0f60-177">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="f0f60-178">Částečné metody</span><span class="sxs-lookup"><span data-stu-id="f0f60-178">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
