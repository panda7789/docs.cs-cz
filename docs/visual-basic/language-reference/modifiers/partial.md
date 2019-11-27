---
title: Částečně
ms.date: 07/20/2015
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
ms.openlocfilehash: df85571b757fd54496677bad1195fab9690b79cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351361"
---
# <a name="partial-visual-basic"></a><span data-ttu-id="31e55-102">Partial (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31e55-102">Partial (Visual Basic)</span></span>
<span data-ttu-id="31e55-103">Označuje, že deklarace typu je částečná definice typu.</span><span class="sxs-lookup"><span data-stu-id="31e55-103">Indicates that a type declaration is a partial definition of the type.</span></span>  
  
 <span data-ttu-id="31e55-104">Definici typu můžete rozdělit mezi několik deklarací pomocí klíčového slova `Partial`.</span><span class="sxs-lookup"><span data-stu-id="31e55-104">You can divide the definition of a type among several declarations by using the `Partial` keyword.</span></span> <span data-ttu-id="31e55-105">Můžete použít libovolný počet částečných deklarací v libovolných různých zdrojových souborech, kolik chcete.</span><span class="sxs-lookup"><span data-stu-id="31e55-105">You can use as many partial declarations as you want, in as many different source files as you want.</span></span> <span data-ttu-id="31e55-106">Nicméně všechny deklarace musí být ve stejném sestavení a stejném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="31e55-106">However, all the declarations must be in the same assembly and the same namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31e55-107">Visual Basic podporuje *částečné metody*, které jsou obvykle implementovány v dílčích třídách.</span><span class="sxs-lookup"><span data-stu-id="31e55-107">Visual Basic supports *partial methods*, which are typically implemented in partial classes.</span></span> <span data-ttu-id="31e55-108">Další informace naleznete v tématu [částečné metody](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) a [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="31e55-108">For more information, see [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31e55-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31e55-109">Syntax</span></span>  
  
```vb  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a><span data-ttu-id="31e55-110">Součásti</span><span class="sxs-lookup"><span data-stu-id="31e55-110">Parts</span></span>  
  
|<span data-ttu-id="31e55-111">Termín</span><span class="sxs-lookup"><span data-stu-id="31e55-111">Term</span></span>|<span data-ttu-id="31e55-112">Definice</span><span class="sxs-lookup"><span data-stu-id="31e55-112">Definition</span></span>|  
|---|---|  
|`attrlist`|<span data-ttu-id="31e55-113">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="31e55-113">Optional.</span></span> <span data-ttu-id="31e55-114">Seznam atributů, které se vztahují na tento typ.</span><span class="sxs-lookup"><span data-stu-id="31e55-114">List of attributes that apply to this type.</span></span> <span data-ttu-id="31e55-115">[Seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md) je nutné uzavřít do lomených závorek (`< >`).</span><span class="sxs-lookup"><span data-stu-id="31e55-115">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets (`< >`).</span></span>|  
|`accessmodifier`|<span data-ttu-id="31e55-116">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="31e55-116">Optional.</span></span> <span data-ttu-id="31e55-117">Určuje, jaký kód má k tomuto typu přístup.</span><span class="sxs-lookup"><span data-stu-id="31e55-117">Specifies what code can access this type.</span></span> <span data-ttu-id="31e55-118">Podívejte [se na úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="31e55-118">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`Shadows`|<span data-ttu-id="31e55-119">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="31e55-119">Optional.</span></span> <span data-ttu-id="31e55-120">Viz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="31e55-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>|  
|`MustInherit`|<span data-ttu-id="31e55-121">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="31e55-121">Optional.</span></span> <span data-ttu-id="31e55-122">Viz [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="31e55-122">See [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>|  
|`NotInheritable`|<span data-ttu-id="31e55-123">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="31e55-123">Optional.</span></span> <span data-ttu-id="31e55-124">Viz [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span><span class="sxs-lookup"><span data-stu-id="31e55-124">See [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span></span>|  
|`name`|<span data-ttu-id="31e55-125">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="31e55-125">Required.</span></span> <span data-ttu-id="31e55-126">Název tohoto typu</span><span class="sxs-lookup"><span data-stu-id="31e55-126">Name of this type.</span></span> <span data-ttu-id="31e55-127">Musí odpovídat názvu definovanému ve všech ostatních částečných deklaracích stejného typu.</span><span class="sxs-lookup"><span data-stu-id="31e55-127">Must match the name defined in all other partial declarations of the same type.</span></span>|  
|`Of`|<span data-ttu-id="31e55-128">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="31e55-128">Optional.</span></span> <span data-ttu-id="31e55-129">Určuje, že se jedná o obecný typ.</span><span class="sxs-lookup"><span data-stu-id="31e55-129">Specifies that this is a generic type.</span></span> <span data-ttu-id="31e55-130">Viz [Obecné typy v Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="31e55-130">See [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>|  
|`typelist`|<span data-ttu-id="31e55-131">Vyžaduje [se, pokud používáte.](../../../visual-basic/language-reference/statements/of-clause.md)</span><span class="sxs-lookup"><span data-stu-id="31e55-131">Required if you use [Of](../../../visual-basic/language-reference/statements/of-clause.md).</span></span> <span data-ttu-id="31e55-132">Viz [seznam typů](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="31e55-132">See [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>|  
|`Inherits`|<span data-ttu-id="31e55-133">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="31e55-133">Optional.</span></span> <span data-ttu-id="31e55-134">Viz [příkaz Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="31e55-134">See [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md).</span></span>|  
|`classname`|<span data-ttu-id="31e55-135">Vyžaduje se, pokud používáte `Inherits`.</span><span class="sxs-lookup"><span data-stu-id="31e55-135">Required if you use `Inherits`.</span></span> <span data-ttu-id="31e55-136">Název třídy nebo rozhraní, ze kterého je tato třída odvozena.</span><span class="sxs-lookup"><span data-stu-id="31e55-136">The name of the class or interface from which this class derives.</span></span>|  
|`Implements`|<span data-ttu-id="31e55-137">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="31e55-137">Optional.</span></span> <span data-ttu-id="31e55-138">Viz [příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="31e55-138">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>|  
|`interfacenames`|<span data-ttu-id="31e55-139">Vyžaduje se, pokud používáte `Implements`.</span><span class="sxs-lookup"><span data-stu-id="31e55-139">Required if you use `Implements`.</span></span> <span data-ttu-id="31e55-140">Názvy rozhraní, které tento typ implementuje.</span><span class="sxs-lookup"><span data-stu-id="31e55-140">The names of the interfaces this type implements.</span></span>|  
|`variabledeclarations`|<span data-ttu-id="31e55-141">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="31e55-141">Optional.</span></span> <span data-ttu-id="31e55-142">Příkazy, které deklarují další proměnné a události pro daný typ.</span><span class="sxs-lookup"><span data-stu-id="31e55-142">Statements which declare additional variables and events for the type.</span></span>|  
|`proceduredeclarations`|<span data-ttu-id="31e55-143">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="31e55-143">Optional.</span></span> <span data-ttu-id="31e55-144">Příkazy, které deklarují a definují další postupy pro typ.</span><span class="sxs-lookup"><span data-stu-id="31e55-144">Statements which declare and define additional procedures for the type.</span></span>|  
|<span data-ttu-id="31e55-145">`End Class` nebo `End Structure`</span><span class="sxs-lookup"><span data-stu-id="31e55-145">`End Class` or `End Structure`</span></span>|<span data-ttu-id="31e55-146">Ukončí tuto částečnou `Class` nebo definici `Structure`.</span><span class="sxs-lookup"><span data-stu-id="31e55-146">Ends this partial `Class` or `Structure` definition.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31e55-147">Poznámky</span><span class="sxs-lookup"><span data-stu-id="31e55-147">Remarks</span></span>  
 <span data-ttu-id="31e55-148">Visual Basic používá definice částečné třídy pro oddělení vygenerovaného kódu od uživatelem vytvořeného kódu v samostatných zdrojových souborech.</span><span class="sxs-lookup"><span data-stu-id="31e55-148">Visual Basic uses partial-class definitions to separate generated code from user-authored code in separate source files.</span></span> <span data-ttu-id="31e55-149">Například **Návrhář formuláře Windows** definuje částečné třídy pro ovládací prvky, jako je například <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="31e55-149">For example, the **Windows Form Designer** defines partial classes for controls such as <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="31e55-150">V těchto ovládacích prvcích byste neměli upravovat generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="31e55-150">You should not modify the generated code in these controls.</span></span>  
  
 <span data-ttu-id="31e55-151">Všechna pravidla pro třídu, strukturu, rozhraní a vytváření modulů, jako jsou například pro použití modifikátoru a dědičnosti, se použijí při vytváření částečného typu.</span><span class="sxs-lookup"><span data-stu-id="31e55-151">All the rules for class, structure, interface, and module creation, such as those for modifier usage and inheritance, apply when creating a partial type.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="31e55-152">Doporučené postupy</span><span class="sxs-lookup"><span data-stu-id="31e55-152">Best Practices</span></span>  
  
- <span data-ttu-id="31e55-153">Za běžných okolností byste neměli rozdělit vývoj jednoho typu ve dvou nebo více deklaracích.</span><span class="sxs-lookup"><span data-stu-id="31e55-153">Under normal circumstances, you should not split the development of a single type across two or more declarations.</span></span> <span data-ttu-id="31e55-154">Proto ve většině případů nepotřebujete klíčové slovo `Partial`.</span><span class="sxs-lookup"><span data-stu-id="31e55-154">Therefore, in most cases you do not need the `Partial` keyword.</span></span>  
  
- <span data-ttu-id="31e55-155">Pro účely čitelnosti by měla každá částečná deklarace typu zahrnovat klíčové slovo `Partial`.</span><span class="sxs-lookup"><span data-stu-id="31e55-155">For readability, every partial declaration of a type should include the `Partial` keyword.</span></span> <span data-ttu-id="31e55-156">Kompilátor umožňuje nejvýše jednu částečnou deklaraci, aby klíčové slovo bylo vynecháno. Pokud je vynecháte dva nebo více, kompilátor signalizuje chybu.</span><span class="sxs-lookup"><span data-stu-id="31e55-156">The compiler allows at most one partial declaration to omit the keyword; if two or more omit it the compiler signals an error.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="31e55-157">Chování</span><span class="sxs-lookup"><span data-stu-id="31e55-157">Behavior</span></span>  
  
- <span data-ttu-id="31e55-158">**Sjednocení deklarací.**</span><span class="sxs-lookup"><span data-stu-id="31e55-158">**Union of Declarations.**</span></span> <span data-ttu-id="31e55-159">Kompilátor považuje typ za sjednocení všech jeho částečných deklarací.</span><span class="sxs-lookup"><span data-stu-id="31e55-159">The compiler treats the type as the union of all its partial declarations.</span></span> <span data-ttu-id="31e55-160">Všechny modifikátory od každé částečné definice platí pro celý typ a každý člen z každé částečné definice je k dispozici pro celý typ.</span><span class="sxs-lookup"><span data-stu-id="31e55-160">Every modifier from every partial definition applies to the entire type, and every member from every partial definition is available to the entire type.</span></span>  
  
- <span data-ttu-id="31e55-161">**Pro částečné typy v modulech není povolena propagace typu.**</span><span class="sxs-lookup"><span data-stu-id="31e55-161">**Type Promotion Not Allowed For Partial Types in Modules.**</span></span> <span data-ttu-id="31e55-162">Pokud je v modulu Částečná definice, typ propagace tohoto typu je automaticky připraven.</span><span class="sxs-lookup"><span data-stu-id="31e55-162">If a partial definition is inside a module, type promotion of that type is automatically defeated.</span></span> <span data-ttu-id="31e55-163">V takovém případě může sada částečných definic způsobit neočekávané výsledky a dokonce i chyby kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="31e55-163">In such a case, a set of partial definitions can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="31e55-164">Další informace najdete v tématu o [typu propagace](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="31e55-164">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
     <span data-ttu-id="31e55-165">Kompilátor sloučí částečné definice pouze v případě, že jsou jejich plně kvalifikované cesty identické.</span><span class="sxs-lookup"><span data-stu-id="31e55-165">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
 <span data-ttu-id="31e55-166">Klíčové slovo `Partial` lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="31e55-166">The `Partial` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="31e55-167">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="31e55-167">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="31e55-168">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="31e55-168">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a><span data-ttu-id="31e55-169">Příklad</span><span class="sxs-lookup"><span data-stu-id="31e55-169">Example</span></span>  
 <span data-ttu-id="31e55-170">V následujícím příkladu je rozdělena definice třídy `sampleClass` do dvou deklarací, z nichž každá definuje jiný způsob `Sub`.</span><span class="sxs-lookup"><span data-stu-id="31e55-170">The following example splits the definition of class `sampleClass` into two declarations, each of which defines a different `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 <span data-ttu-id="31e55-171">Dvě částečné definice v předchozím příkladu můžou být ve stejném zdrojovém souboru nebo ve dvou různých zdrojových souborech.</span><span class="sxs-lookup"><span data-stu-id="31e55-171">The two partial definitions in the preceding example could be in the same source file or in two different source files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31e55-172">Viz také:</span><span class="sxs-lookup"><span data-stu-id="31e55-172">See also</span></span>

- [<span data-ttu-id="31e55-173">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="31e55-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="31e55-174">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="31e55-174">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="31e55-175">Propagace typu</span><span class="sxs-lookup"><span data-stu-id="31e55-175">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
- [<span data-ttu-id="31e55-176">Shadows</span><span class="sxs-lookup"><span data-stu-id="31e55-176">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="31e55-177">Obecné typy v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="31e55-177">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="31e55-178">Částečné metody</span><span class="sxs-lookup"><span data-stu-id="31e55-178">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
