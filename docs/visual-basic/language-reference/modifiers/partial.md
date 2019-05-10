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
ms.openlocfilehash: da5679c3e69a938e9735922bcf4f912428024610
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642791"
---
# <a name="partial-visual-basic"></a><span data-ttu-id="fe4f8-102">Partial (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe4f8-102">Partial (Visual Basic)</span></span>
<span data-ttu-id="fe4f8-103">Označuje, že deklarace typu je částečnou definici typu.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-103">Indicates that a type declaration is a partial definition of the type.</span></span>  
  
 <span data-ttu-id="fe4f8-104">Definice typu mezi několik deklarací můžete rozdělit pomocí `Partial` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-104">You can divide the definition of a type among several declarations by using the `Partial` keyword.</span></span> <span data-ttu-id="fe4f8-105">Můžete použít tolik částečné deklarace chcete v tolika jiných zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-105">You can use as many partial declarations as you want, in as many different source files as you want.</span></span> <span data-ttu-id="fe4f8-106">Všechny deklarace však musí být ve stejném sestavení a stejný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-106">However, all the declarations must be in the same assembly and the same namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe4f8-107">Visual Basic podporuje *částečné metody*, které jsou zpravidla implementovaní v částečné třídy.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-107">Visual Basic supports *partial methods*, which are typically implemented in partial classes.</span></span> <span data-ttu-id="fe4f8-108">Další informace najdete v tématu [částečné metody](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) a [příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fe4f8-108">For more information, see [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe4f8-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe4f8-109">Syntax</span></span>  
  
```  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a><span data-ttu-id="fe4f8-110">Součásti</span><span class="sxs-lookup"><span data-stu-id="fe4f8-110">Parts</span></span>  
  
|<span data-ttu-id="fe4f8-111">Termín</span><span class="sxs-lookup"><span data-stu-id="fe4f8-111">Term</span></span>|<span data-ttu-id="fe4f8-112">Definice</span><span class="sxs-lookup"><span data-stu-id="fe4f8-112">Definition</span></span>|  
|---|---|  
|`attrlist`|<span data-ttu-id="fe4f8-113">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-113">Optional.</span></span> <span data-ttu-id="fe4f8-114">Seznam atributů, které se vztahují k tomuto typu.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-114">List of attributes that apply to this type.</span></span> <span data-ttu-id="fe4f8-115">Je nutné uzavřít [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md) v lomených závorkách (`< >`).</span><span class="sxs-lookup"><span data-stu-id="fe4f8-115">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets (`< >`).</span></span>|  
|`accessmodifier`|<span data-ttu-id="fe4f8-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-116">Optional.</span></span> <span data-ttu-id="fe4f8-117">Určuje, jaký kód může přistupovat k tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-117">Specifies what code can access this type.</span></span> <span data-ttu-id="fe4f8-118">Zobrazit [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="fe4f8-118">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`Shadows`|<span data-ttu-id="fe4f8-119">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-119">Optional.</span></span> <span data-ttu-id="fe4f8-120">Zobrazit [stíny](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="fe4f8-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>|  
|`MustInherit`|<span data-ttu-id="fe4f8-121">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-121">Optional.</span></span> <span data-ttu-id="fe4f8-122">Zobrazit [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="fe4f8-122">See [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>|  
|`NotInheritable`|<span data-ttu-id="fe4f8-123">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-123">Optional.</span></span> <span data-ttu-id="fe4f8-124">Zobrazit [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span><span class="sxs-lookup"><span data-stu-id="fe4f8-124">See [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span></span>|  
|`name`|<span data-ttu-id="fe4f8-125">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-125">Required.</span></span> <span data-ttu-id="fe4f8-126">Název tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-126">Name of this type.</span></span> <span data-ttu-id="fe4f8-127">Musí odpovídat názvu definovaný v jiné částečné deklarace stejného typu.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-127">Must match the name defined in all other partial declarations of the same type.</span></span>|  
|`Of`|<span data-ttu-id="fe4f8-128">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-128">Optional.</span></span> <span data-ttu-id="fe4f8-129">Určuje, že se jedná o obecného typu.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-129">Specifies that this is a generic type.</span></span> <span data-ttu-id="fe4f8-130">Zobrazit [obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="fe4f8-130">See [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>|  
|`typelist`|<span data-ttu-id="fe4f8-131">Povinné, pokud používáte [z](../../../visual-basic/language-reference/statements/of-clause.md).</span><span class="sxs-lookup"><span data-stu-id="fe4f8-131">Required if you use [Of](../../../visual-basic/language-reference/statements/of-clause.md).</span></span> <span data-ttu-id="fe4f8-132">Zobrazit [seznamu](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="fe4f8-132">See [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>|  
|`Inherits`|<span data-ttu-id="fe4f8-133">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-133">Optional.</span></span> <span data-ttu-id="fe4f8-134">Zobrazit [Inherits – příkaz](../../../visual-basic/language-reference/statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fe4f8-134">See [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md).</span></span>|  
|`classname`|<span data-ttu-id="fe4f8-135">Povinné, pokud používáte `Inherits`.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-135">Required if you use `Inherits`.</span></span> <span data-ttu-id="fe4f8-136">Název třídy nebo rozhraní, ze kterého tato třída je odvozena.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-136">The name of the class or interface from which this class derives.</span></span>|  
|`Implements`|<span data-ttu-id="fe4f8-137">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-137">Optional.</span></span> <span data-ttu-id="fe4f8-138">Zobrazit [implementuje příkaz](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fe4f8-138">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>|  
|`interfacenames`|<span data-ttu-id="fe4f8-139">Povinné, pokud používáte `Implements`.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-139">Required if you use `Implements`.</span></span> <span data-ttu-id="fe4f8-140">Názvy, které tento typ implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-140">The names of the interfaces this type implements.</span></span>|  
|`variabledeclarations`|<span data-ttu-id="fe4f8-141">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-141">Optional.</span></span> <span data-ttu-id="fe4f8-142">Příkazy, které deklarace události pro typ a další proměnné.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-142">Statements which declare additional variables and events for the type.</span></span>|  
|`proceduredeclarations`|<span data-ttu-id="fe4f8-143">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-143">Optional.</span></span> <span data-ttu-id="fe4f8-144">Příkazy, které deklarace a definovat další postupy pro typ.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-144">Statements which declare and define additional procedures for the type.</span></span>|  
|<span data-ttu-id="fe4f8-145">`End Class` Nebo `End Structure`</span><span class="sxs-lookup"><span data-stu-id="fe4f8-145">`End Class` or `End Structure`</span></span>|<span data-ttu-id="fe4f8-146">Končí tento částečné `Class` nebo `Structure` definice.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-146">Ends this partial `Class` or `Structure` definition.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe4f8-147">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fe4f8-147">Remarks</span></span>  
 <span data-ttu-id="fe4f8-148">Visual Basic používá definicí částečné třídy pro oddělení generovaný kód z kódu uživatelem definovaných v samostatných zdrojové soubory.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-148">Visual Basic uses partial-class definitions to separate generated code from user-authored code in separate source files.</span></span> <span data-ttu-id="fe4f8-149">Například **Návrhář formulářů Windows** definuje částečné třídy pro ovládací prvky, jako <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-149">For example, the **Windows Form Designer** defines partial classes for controls such as <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="fe4f8-150">Generovaný kód v těchto ovládacích prvků byste neměli měnit.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-150">You should not modify the generated code in these controls.</span></span>  
  
 <span data-ttu-id="fe4f8-151">Všechna pravidla pro třídu, strukturu, rozhraní a vytváření modulu, třeba kroky týkající se použití modifikátoru a dědičnost, použít při vytváření částečného typu.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-151">All the rules for class, structure, interface, and module creation, such as those for modifier usage and inheritance, apply when creating a partial type.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="fe4f8-152">Doporučené postupy</span><span class="sxs-lookup"><span data-stu-id="fe4f8-152">Best Practices</span></span>  
  
- <span data-ttu-id="fe4f8-153">Za normálních podmínek by neměl vývoj jeden typ rozdělit mezi dva nebo více deklarací.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-153">Under normal circumstances, you should not split the development of a single type across two or more declarations.</span></span> <span data-ttu-id="fe4f8-154">Proto se ve většině případů není nutné `Partial` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-154">Therefore, in most cases you do not need the `Partial` keyword.</span></span>  
  
- <span data-ttu-id="fe4f8-155">Pro lepší čitelnost, by měl obsahovat všechny částečné deklaraci typu `Partial` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-155">For readability, every partial declaration of a type should include the `Partial` keyword.</span></span> <span data-ttu-id="fe4f8-156">Kompilátor povoluje nejvýše jedna částečná deklarace chcete vynechat, nechte – klíčové slovo; Pokud ji vynechte nejméně dva signály kompilátor chybu.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-156">The compiler allows at most one partial declaration to omit the keyword; if two or more omit it the compiler signals an error.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="fe4f8-157">Chování</span><span class="sxs-lookup"><span data-stu-id="fe4f8-157">Behavior</span></span>  
  
- <span data-ttu-id="fe4f8-158">**Deklarace sjednocení.**</span><span class="sxs-lookup"><span data-stu-id="fe4f8-158">**Union of Declarations.**</span></span> <span data-ttu-id="fe4f8-159">Kompilátor zpracovává typ jako její částečné deklarace sjednocení.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-159">The compiler treats the type as the union of all its partial declarations.</span></span> <span data-ttu-id="fe4f8-160">Každý modifikátor z každé Částečná definice platí pro celý typ a je k dispozici pro celý typ každého člena z každé částečnou definici.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-160">Every modifier from every partial definition applies to the entire type, and every member from every partial definition is available to the entire type.</span></span>  
  
- <span data-ttu-id="fe4f8-161">**Propagace typu není povolený pro částečné typy v modulech.**</span><span class="sxs-lookup"><span data-stu-id="fe4f8-161">**Type Promotion Not Allowed For Partial Types in Modules.**</span></span> <span data-ttu-id="fe4f8-162">Pokud je částečnou definici uvnitř modulu, typu povýšení tohoto typu není automaticky zrušena.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-162">If a partial definition is inside a module, type promotion of that type is automatically defeated.</span></span> <span data-ttu-id="fe4f8-163">V takovém případě sada částečné definice může způsobit neočekávané výsledky a dokonce i chyby kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-163">In such a case, a set of partial definitions can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="fe4f8-164">Další informace najdete v tématu [propagace typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="fe4f8-164">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
     <span data-ttu-id="fe4f8-165">Kompilátor sloučí částečné definice pouze v případě jejich úplné cesty jsou identické.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-165">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
 <span data-ttu-id="fe4f8-166">`Partial` – Klíčové slovo lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="fe4f8-166">The `Partial` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="fe4f8-167">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="fe4f8-167">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="fe4f8-168">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="fe4f8-168">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a><span data-ttu-id="fe4f8-169">Příklad</span><span class="sxs-lookup"><span data-stu-id="fe4f8-169">Example</span></span>  
 <span data-ttu-id="fe4f8-170">Následující příklad rozdělí definice třídy `sampleClass` do dvě deklarace, z nichž každý definuje jiný `Sub` postup.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-170">The following example splits the definition of class `sampleClass` into two declarations, each of which defines a different `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 <span data-ttu-id="fe4f8-171">Dvě Částečná definice v předchozím příkladu může být ve stejném zdrojovém souboru nebo ve dvou různých zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="fe4f8-171">The two partial definitions in the preceding example could be in the same source file or in two different source files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe4f8-172">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe4f8-172">See also</span></span>

- [<span data-ttu-id="fe4f8-173">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="fe4f8-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="fe4f8-174">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="fe4f8-174">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="fe4f8-175">Propagace typu</span><span class="sxs-lookup"><span data-stu-id="fe4f8-175">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
- [<span data-ttu-id="fe4f8-176">Shadows</span><span class="sxs-lookup"><span data-stu-id="fe4f8-176">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="fe4f8-177">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fe4f8-177">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="fe4f8-178">Částečné metody</span><span class="sxs-lookup"><span data-stu-id="fe4f8-178">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
