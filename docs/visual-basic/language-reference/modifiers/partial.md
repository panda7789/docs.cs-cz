---
title: Partial (Visual Basic)
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
ms.openlocfilehash: 0f74935d58d47e65b5eb614abc86a3fc9c8e6c42
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838362"
---
# <a name="partial-visual-basic"></a><span data-ttu-id="44819-102">Partial (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44819-102">Partial (Visual Basic)</span></span>
<span data-ttu-id="44819-103">Označuje, že deklarace typu je částečnou definici typu.</span><span class="sxs-lookup"><span data-stu-id="44819-103">Indicates that a type declaration is a partial definition of the type.</span></span>  
  
 <span data-ttu-id="44819-104">Definice typu mezi několik deklarací můžete rozdělit pomocí `Partial` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="44819-104">You can divide the definition of a type among several declarations by using the `Partial` keyword.</span></span> <span data-ttu-id="44819-105">Můžete použít tolik částečné deklarace chcete v tolika jiných zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="44819-105">You can use as many partial declarations as you want, in as many different source files as you want.</span></span> <span data-ttu-id="44819-106">Všechny deklarace však musí být ve stejném sestavení a stejný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="44819-106">However, all the declarations must be in the same assembly and the same namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44819-107">Visual Basic podporuje *částečné metody*, které jsou zpravidla implementovaní v částečné třídy.</span><span class="sxs-lookup"><span data-stu-id="44819-107">Visual Basic supports *partial methods*, which are typically implemented in partial classes.</span></span> <span data-ttu-id="44819-108">Další informace najdete v tématu [částečné metody](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) a [příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="44819-108">For more information, see [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44819-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44819-109">Syntax</span></span>  
  
```  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a><span data-ttu-id="44819-110">Součásti</span><span class="sxs-lookup"><span data-stu-id="44819-110">Parts</span></span>  
  
|<span data-ttu-id="44819-111">Termín</span><span class="sxs-lookup"><span data-stu-id="44819-111">Term</span></span>|<span data-ttu-id="44819-112">Definice</span><span class="sxs-lookup"><span data-stu-id="44819-112">Definition</span></span>|  
|---|---|  
|`attrlist`|<span data-ttu-id="44819-113">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="44819-113">Optional.</span></span> <span data-ttu-id="44819-114">Seznam atributů, které se vztahují k tomuto typu.</span><span class="sxs-lookup"><span data-stu-id="44819-114">List of attributes that apply to this type.</span></span> <span data-ttu-id="44819-115">Je nutné uzavřít [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md) v lomených závorkách (`< >`).</span><span class="sxs-lookup"><span data-stu-id="44819-115">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets (`< >`).</span></span>|  
|`accessmodifier`|<span data-ttu-id="44819-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="44819-116">Optional.</span></span> <span data-ttu-id="44819-117">Určuje, jaký kód může přistupovat k tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="44819-117">Specifies what code can access this type.</span></span> <span data-ttu-id="44819-118">Zobrazit [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="44819-118">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`Shadows`|<span data-ttu-id="44819-119">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="44819-119">Optional.</span></span> <span data-ttu-id="44819-120">Zobrazit [stíny](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="44819-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>|  
|`MustInherit`|<span data-ttu-id="44819-121">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="44819-121">Optional.</span></span> <span data-ttu-id="44819-122">Zobrazit [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="44819-122">See [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>|  
|`NotInheritable`|<span data-ttu-id="44819-123">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="44819-123">Optional.</span></span> <span data-ttu-id="44819-124">Zobrazit [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span><span class="sxs-lookup"><span data-stu-id="44819-124">See [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span></span>|  
|`name`|<span data-ttu-id="44819-125">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="44819-125">Required.</span></span> <span data-ttu-id="44819-126">Název tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="44819-126">Name of this type.</span></span> <span data-ttu-id="44819-127">Musí odpovídat názvu definovaný v jiné částečné deklarace stejného typu.</span><span class="sxs-lookup"><span data-stu-id="44819-127">Must match the name defined in all other partial declarations of the same type.</span></span>|  
|`Of`|<span data-ttu-id="44819-128">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="44819-128">Optional.</span></span> <span data-ttu-id="44819-129">Určuje, že se jedná o obecného typu.</span><span class="sxs-lookup"><span data-stu-id="44819-129">Specifies that this is a generic type.</span></span> <span data-ttu-id="44819-130">Zobrazit [obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="44819-130">See [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>|  
|`typelist`|<span data-ttu-id="44819-131">Povinné, pokud používáte [z](../../../visual-basic/language-reference/statements/of-clause.md).</span><span class="sxs-lookup"><span data-stu-id="44819-131">Required if you use [Of](../../../visual-basic/language-reference/statements/of-clause.md).</span></span> <span data-ttu-id="44819-132">Zobrazit [seznamu](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="44819-132">See [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>|  
|`Inherits`|<span data-ttu-id="44819-133">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="44819-133">Optional.</span></span> <span data-ttu-id="44819-134">Zobrazit [Inherits – příkaz](../../../visual-basic/language-reference/statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="44819-134">See [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md).</span></span>|  
|`classname`|<span data-ttu-id="44819-135">Povinné, pokud používáte `Inherits`.</span><span class="sxs-lookup"><span data-stu-id="44819-135">Required if you use `Inherits`.</span></span> <span data-ttu-id="44819-136">Název třídy nebo rozhraní, ze kterého tato třída je odvozena.</span><span class="sxs-lookup"><span data-stu-id="44819-136">The name of the class or interface from which this class derives.</span></span>|  
|`Implements`|<span data-ttu-id="44819-137">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="44819-137">Optional.</span></span> <span data-ttu-id="44819-138">Zobrazit [implementuje příkaz](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="44819-138">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>|  
|`interfacenames`|<span data-ttu-id="44819-139">Povinné, pokud používáte `Implements`.</span><span class="sxs-lookup"><span data-stu-id="44819-139">Required if you use `Implements`.</span></span> <span data-ttu-id="44819-140">Názvy, které tento typ implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="44819-140">The names of the interfaces this type implements.</span></span>|  
|`variabledeclarations`|<span data-ttu-id="44819-141">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="44819-141">Optional.</span></span> <span data-ttu-id="44819-142">Příkazy, které deklarace události pro typ a další proměnné.</span><span class="sxs-lookup"><span data-stu-id="44819-142">Statements which declare additional variables and events for the type.</span></span>|  
|`proceduredeclarations`|<span data-ttu-id="44819-143">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="44819-143">Optional.</span></span> <span data-ttu-id="44819-144">Příkazy, které deklarace a definovat další postupy pro typ.</span><span class="sxs-lookup"><span data-stu-id="44819-144">Statements which declare and define additional procedures for the type.</span></span>|  
|<span data-ttu-id="44819-145">`End Class` Nebo `End Structure`</span><span class="sxs-lookup"><span data-stu-id="44819-145">`End Class` or `End Structure`</span></span>|<span data-ttu-id="44819-146">Končí tento částečné `Class` nebo `Structure` definice.</span><span class="sxs-lookup"><span data-stu-id="44819-146">Ends this partial `Class` or `Structure` definition.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44819-147">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44819-147">Remarks</span></span>  
 <span data-ttu-id="44819-148">Visual Basic používá definicí částečné třídy pro oddělení generovaný kód z kódu uživatelem definovaných v samostatných zdrojové soubory.</span><span class="sxs-lookup"><span data-stu-id="44819-148">Visual Basic uses partial-class definitions to separate generated code from user-authored code in separate source files.</span></span> <span data-ttu-id="44819-149">Například **Návrhář formulářů Windows** definuje částečné třídy pro ovládací prvky, jako <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="44819-149">For example, the **Windows Form Designer** defines partial classes for controls such as <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="44819-150">Generovaný kód v těchto ovládacích prvků byste neměli měnit.</span><span class="sxs-lookup"><span data-stu-id="44819-150">You should not modify the generated code in these controls.</span></span>  
  
 <span data-ttu-id="44819-151">Všechna pravidla pro třídu, strukturu, rozhraní a vytváření modulu, třeba kroky týkající se použití modifikátoru a dědičnost, použít při vytváření částečného typu.</span><span class="sxs-lookup"><span data-stu-id="44819-151">All the rules for class, structure, interface, and module creation, such as those for modifier usage and inheritance, apply when creating a partial type.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="44819-152">Doporučené postupy</span><span class="sxs-lookup"><span data-stu-id="44819-152">Best Practices</span></span>  
  
-   <span data-ttu-id="44819-153">Za normálních podmínek by neměl vývoj jeden typ rozdělit mezi dva nebo více deklarací.</span><span class="sxs-lookup"><span data-stu-id="44819-153">Under normal circumstances, you should not split the development of a single type across two or more declarations.</span></span> <span data-ttu-id="44819-154">Proto se ve většině případů není nutné `Partial` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="44819-154">Therefore, in most cases you do not need the `Partial` keyword.</span></span>  
  
-   <span data-ttu-id="44819-155">Pro lepší čitelnost, by měl obsahovat všechny částečné deklaraci typu `Partial` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="44819-155">For readability, every partial declaration of a type should include the `Partial` keyword.</span></span> <span data-ttu-id="44819-156">Kompilátor povoluje nejvýše jedna částečná deklarace chcete vynechat, nechte – klíčové slovo; Pokud ji vynechte nejméně dva signály kompilátor chybu.</span><span class="sxs-lookup"><span data-stu-id="44819-156">The compiler allows at most one partial declaration to omit the keyword; if two or more omit it the compiler signals an error.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="44819-157">Chování</span><span class="sxs-lookup"><span data-stu-id="44819-157">Behavior</span></span>  
  
-   <span data-ttu-id="44819-158">**Deklarace sjednocení.**</span><span class="sxs-lookup"><span data-stu-id="44819-158">**Union of Declarations.**</span></span> <span data-ttu-id="44819-159">Kompilátor zpracovává typ jako její částečné deklarace sjednocení.</span><span class="sxs-lookup"><span data-stu-id="44819-159">The compiler treats the type as the union of all its partial declarations.</span></span> <span data-ttu-id="44819-160">Každý modifikátor z každé Částečná definice platí pro celý typ a je k dispozici pro celý typ každého člena z každé částečnou definici.</span><span class="sxs-lookup"><span data-stu-id="44819-160">Every modifier from every partial definition applies to the entire type, and every member from every partial definition is available to the entire type.</span></span>  
  
-   <span data-ttu-id="44819-161">**Propagace typu není povolený pro částečné typy v modulech.**</span><span class="sxs-lookup"><span data-stu-id="44819-161">**Type Promotion Not Allowed For Partial Types in Modules.**</span></span> <span data-ttu-id="44819-162">Pokud je částečnou definici uvnitř modulu, typu povýšení tohoto typu není automaticky zrušena.</span><span class="sxs-lookup"><span data-stu-id="44819-162">If a partial definition is inside a module, type promotion of that type is automatically defeated.</span></span> <span data-ttu-id="44819-163">V takovém případě sada částečné definice může způsobit neočekávané výsledky a dokonce i chyby kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="44819-163">In such a case, a set of partial definitions can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="44819-164">Další informace najdete v tématu [propagace typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="44819-164">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
     <span data-ttu-id="44819-165">Kompilátor sloučí částečné definice pouze v případě jejich úplné cesty jsou identické.</span><span class="sxs-lookup"><span data-stu-id="44819-165">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
 <span data-ttu-id="44819-166">`Partial` – Klíčové slovo lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="44819-166">The `Partial` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="44819-167">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="44819-167">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="44819-168">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="44819-168">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a><span data-ttu-id="44819-169">Příklad</span><span class="sxs-lookup"><span data-stu-id="44819-169">Example</span></span>  
 <span data-ttu-id="44819-170">Následující příklad rozdělí definice třídy `sampleClass` do dvě deklarace, z nichž každý definuje jiný `Sub` postup.</span><span class="sxs-lookup"><span data-stu-id="44819-170">The following example splits the definition of class `sampleClass` into two declarations, each of which defines a different `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 <span data-ttu-id="44819-171">Dvě Částečná definice v předchozím příkladu může být ve stejném zdrojovém souboru nebo ve dvou různých zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="44819-171">The two partial definitions in the preceding example could be in the same source file or in two different source files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44819-172">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44819-172">See also</span></span>

- [<span data-ttu-id="44819-173">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="44819-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="44819-174">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="44819-174">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="44819-175">Propagace typu</span><span class="sxs-lookup"><span data-stu-id="44819-175">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
- [<span data-ttu-id="44819-176">Shadows</span><span class="sxs-lookup"><span data-stu-id="44819-176">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="44819-177">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="44819-177">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="44819-178">Částečné metody</span><span class="sxs-lookup"><span data-stu-id="44819-178">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
