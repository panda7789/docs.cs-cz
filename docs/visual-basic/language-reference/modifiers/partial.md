---
title: Částečné
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
ms.openlocfilehash: 650ead2f0deb9813b26241a6a4676907de3f263d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362239"
---
# <a name="partial-visual-basic"></a><span data-ttu-id="1b22f-102">Partial (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b22f-102">Partial (Visual Basic)</span></span>
<span data-ttu-id="1b22f-103">Označuje, že deklarace typu je částečná definice typu.</span><span class="sxs-lookup"><span data-stu-id="1b22f-103">Indicates that a type declaration is a partial definition of the type.</span></span>  
  
 <span data-ttu-id="1b22f-104">Definici typu můžete rozdělit mezi několik deklarací pomocí `Partial` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="1b22f-104">You can divide the definition of a type among several declarations by using the `Partial` keyword.</span></span> <span data-ttu-id="1b22f-105">Můžete použít libovolný počet částečných deklarací v libovolných různých zdrojových souborech, kolik chcete.</span><span class="sxs-lookup"><span data-stu-id="1b22f-105">You can use as many partial declarations as you want, in as many different source files as you want.</span></span> <span data-ttu-id="1b22f-106">Nicméně všechny deklarace musí být ve stejném sestavení a stejném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1b22f-106">However, all the declarations must be in the same assembly and the same namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1b22f-107">Visual Basic podporuje *částečné metody*, které jsou obvykle implementovány v dílčích třídách.</span><span class="sxs-lookup"><span data-stu-id="1b22f-107">Visual Basic supports *partial methods*, which are typically implemented in partial classes.</span></span> <span data-ttu-id="1b22f-108">Další informace naleznete v tématu [částečné metody](../../programming-guide/language-features/procedures/partial-methods.md) a [Sub Statement](../statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b22f-108">For more information, see [Partial Methods](../../programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../statements/sub-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b22f-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b22f-109">Syntax</span></span>  
  
```vb  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a><span data-ttu-id="1b22f-110">Součásti</span><span class="sxs-lookup"><span data-stu-id="1b22f-110">Parts</span></span>  
  
|<span data-ttu-id="1b22f-111">Pojem</span><span class="sxs-lookup"><span data-stu-id="1b22f-111">Term</span></span>|<span data-ttu-id="1b22f-112">Definice</span><span class="sxs-lookup"><span data-stu-id="1b22f-112">Definition</span></span>|  
|---|---|  
|`attrlist`|<span data-ttu-id="1b22f-113">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="1b22f-113">Optional.</span></span> <span data-ttu-id="1b22f-114">Seznam atributů, které se vztahují na tento typ.</span><span class="sxs-lookup"><span data-stu-id="1b22f-114">List of attributes that apply to this type.</span></span> <span data-ttu-id="1b22f-115">[Seznam atributů](../statements/attribute-list.md) musíte uzavřít do lomených závorek ( `< >` ).</span><span class="sxs-lookup"><span data-stu-id="1b22f-115">You must enclose the [Attribute List](../statements/attribute-list.md) in angle brackets (`< >`).</span></span>|  
|`accessmodifier`|<span data-ttu-id="1b22f-116">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="1b22f-116">Optional.</span></span> <span data-ttu-id="1b22f-117">Určuje, jaký kód má k tomuto typu přístup.</span><span class="sxs-lookup"><span data-stu-id="1b22f-117">Specifies what code can access this type.</span></span> <span data-ttu-id="1b22f-118">Podívejte [se na úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="1b22f-118">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`Shadows`|<span data-ttu-id="1b22f-119">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="1b22f-119">Optional.</span></span> <span data-ttu-id="1b22f-120">Viz [Shadows](shadows.md).</span><span class="sxs-lookup"><span data-stu-id="1b22f-120">See [Shadows](shadows.md).</span></span>|  
|`MustInherit`|<span data-ttu-id="1b22f-121">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="1b22f-121">Optional.</span></span> <span data-ttu-id="1b22f-122">Viz [MustInherit](mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="1b22f-122">See [MustInherit](mustinherit.md).</span></span>|  
|`NotInheritable`|<span data-ttu-id="1b22f-123">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="1b22f-123">Optional.</span></span> <span data-ttu-id="1b22f-124">Viz [NotInheritable](notinheritable.md).</span><span class="sxs-lookup"><span data-stu-id="1b22f-124">See [NotInheritable](notinheritable.md).</span></span>|  
|`name`|<span data-ttu-id="1b22f-125">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="1b22f-125">Required.</span></span> <span data-ttu-id="1b22f-126">Název tohoto typu</span><span class="sxs-lookup"><span data-stu-id="1b22f-126">Name of this type.</span></span> <span data-ttu-id="1b22f-127">Musí odpovídat názvu definovanému ve všech ostatních částečných deklaracích stejného typu.</span><span class="sxs-lookup"><span data-stu-id="1b22f-127">Must match the name defined in all other partial declarations of the same type.</span></span>|  
|`Of`|<span data-ttu-id="1b22f-128">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="1b22f-128">Optional.</span></span> <span data-ttu-id="1b22f-129">Určuje, že se jedná o obecný typ.</span><span class="sxs-lookup"><span data-stu-id="1b22f-129">Specifies that this is a generic type.</span></span> <span data-ttu-id="1b22f-130">Viz [Obecné typy v Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="1b22f-130">See [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span></span>|  
|`typelist`|<span data-ttu-id="1b22f-131">Vyžaduje [se, pokud používáte.](../statements/of-clause.md)</span><span class="sxs-lookup"><span data-stu-id="1b22f-131">Required if you use [Of](../statements/of-clause.md).</span></span> <span data-ttu-id="1b22f-132">Viz [seznam typů](../statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="1b22f-132">See [Type List](../statements/type-list.md).</span></span>|  
|`Inherits`|<span data-ttu-id="1b22f-133">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="1b22f-133">Optional.</span></span> <span data-ttu-id="1b22f-134">Viz [příkaz Inherits](../statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b22f-134">See [Inherits Statement](../statements/inherits-statement.md).</span></span>|  
|`classname`|<span data-ttu-id="1b22f-135">Vyžaduje se, pokud používáte `Inherits` .</span><span class="sxs-lookup"><span data-stu-id="1b22f-135">Required if you use `Inherits`.</span></span> <span data-ttu-id="1b22f-136">Název třídy nebo rozhraní, ze kterého je tato třída odvozena.</span><span class="sxs-lookup"><span data-stu-id="1b22f-136">The name of the class or interface from which this class derives.</span></span>|  
|`Implements`|<span data-ttu-id="1b22f-137">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="1b22f-137">Optional.</span></span> <span data-ttu-id="1b22f-138">Viz [příkaz Implements](../statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b22f-138">See [Implements Statement](../statements/implements-statement.md).</span></span>|  
|`interfacenames`|<span data-ttu-id="1b22f-139">Vyžaduje se, pokud používáte `Implements` .</span><span class="sxs-lookup"><span data-stu-id="1b22f-139">Required if you use `Implements`.</span></span> <span data-ttu-id="1b22f-140">Názvy rozhraní, které tento typ implementuje.</span><span class="sxs-lookup"><span data-stu-id="1b22f-140">The names of the interfaces this type implements.</span></span>|  
|`variabledeclarations`|<span data-ttu-id="1b22f-141">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="1b22f-141">Optional.</span></span> <span data-ttu-id="1b22f-142">Příkazy, které deklarují další proměnné a události pro daný typ.</span><span class="sxs-lookup"><span data-stu-id="1b22f-142">Statements which declare additional variables and events for the type.</span></span>|  
|`proceduredeclarations`|<span data-ttu-id="1b22f-143">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="1b22f-143">Optional.</span></span> <span data-ttu-id="1b22f-144">Příkazy, které deklarují a definují další postupy pro typ.</span><span class="sxs-lookup"><span data-stu-id="1b22f-144">Statements which declare and define additional procedures for the type.</span></span>|  
|<span data-ttu-id="1b22f-145">`End Class` nebo `End Structure`</span><span class="sxs-lookup"><span data-stu-id="1b22f-145">`End Class` or `End Structure`</span></span>|<span data-ttu-id="1b22f-146">Ukončí tento částečný `Class` nebo `Structure` definice.</span><span class="sxs-lookup"><span data-stu-id="1b22f-146">Ends this partial `Class` or `Structure` definition.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b22f-147">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1b22f-147">Remarks</span></span>  
 <span data-ttu-id="1b22f-148">Visual Basic používá definice částečné třídy pro oddělení vygenerovaného kódu od uživatelem vytvořeného kódu v samostatných zdrojových souborech.</span><span class="sxs-lookup"><span data-stu-id="1b22f-148">Visual Basic uses partial-class definitions to separate generated code from user-authored code in separate source files.</span></span> <span data-ttu-id="1b22f-149">Například **Návrhář formuláře Windows** definuje částečné třídy pro ovládací prvky, jako například <xref:System.Windows.Forms.Form> .</span><span class="sxs-lookup"><span data-stu-id="1b22f-149">For example, the **Windows Form Designer** defines partial classes for controls such as <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="1b22f-150">V těchto ovládacích prvcích byste neměli upravovat generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="1b22f-150">You should not modify the generated code in these controls.</span></span>  
  
 <span data-ttu-id="1b22f-151">Všechna pravidla pro třídu, strukturu, rozhraní a vytváření modulů, jako jsou například pro použití modifikátoru a dědičnosti, se použijí při vytváření částečného typu.</span><span class="sxs-lookup"><span data-stu-id="1b22f-151">All the rules for class, structure, interface, and module creation, such as those for modifier usage and inheritance, apply when creating a partial type.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="1b22f-152">Osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="1b22f-152">Best Practices</span></span>  
  
- <span data-ttu-id="1b22f-153">Za běžných okolností byste neměli rozdělit vývoj jednoho typu ve dvou nebo více deklaracích.</span><span class="sxs-lookup"><span data-stu-id="1b22f-153">Under normal circumstances, you should not split the development of a single type across two or more declarations.</span></span> <span data-ttu-id="1b22f-154">Ve většině případů proto klíčové slovo nepotřebujete `Partial` .</span><span class="sxs-lookup"><span data-stu-id="1b22f-154">Therefore, in most cases you do not need the `Partial` keyword.</span></span>  
  
- <span data-ttu-id="1b22f-155">Z důvodu čitelnosti by měla každá částečná deklarace typu zahrnovat `Partial` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="1b22f-155">For readability, every partial declaration of a type should include the `Partial` keyword.</span></span> <span data-ttu-id="1b22f-156">Kompilátor umožňuje nejvýše jednu částečnou deklaraci, aby klíčové slovo bylo vynecháno. Pokud je vynecháte dva nebo více, kompilátor signalizuje chybu.</span><span class="sxs-lookup"><span data-stu-id="1b22f-156">The compiler allows at most one partial declaration to omit the keyword; if two or more omit it the compiler signals an error.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="1b22f-157">Chování</span><span class="sxs-lookup"><span data-stu-id="1b22f-157">Behavior</span></span>  
  
- <span data-ttu-id="1b22f-158">**Sjednocení deklarací.**</span><span class="sxs-lookup"><span data-stu-id="1b22f-158">**Union of Declarations.**</span></span> <span data-ttu-id="1b22f-159">Kompilátor považuje typ za sjednocení všech jeho částečných deklarací.</span><span class="sxs-lookup"><span data-stu-id="1b22f-159">The compiler treats the type as the union of all its partial declarations.</span></span> <span data-ttu-id="1b22f-160">Všechny modifikátory od každé částečné definice platí pro celý typ a každý člen z každé částečné definice je k dispozici pro celý typ.</span><span class="sxs-lookup"><span data-stu-id="1b22f-160">Every modifier from every partial definition applies to the entire type, and every member from every partial definition is available to the entire type.</span></span>  
  
- <span data-ttu-id="1b22f-161">**Pro částečné typy v modulech není povolena propagace typu.**</span><span class="sxs-lookup"><span data-stu-id="1b22f-161">**Type Promotion Not Allowed For Partial Types in Modules.**</span></span> <span data-ttu-id="1b22f-162">Pokud je v modulu Částečná definice, typ propagace tohoto typu je automaticky připraven.</span><span class="sxs-lookup"><span data-stu-id="1b22f-162">If a partial definition is inside a module, type promotion of that type is automatically defeated.</span></span> <span data-ttu-id="1b22f-163">V takovém případě může sada částečných definic způsobit neočekávané výsledky a dokonce i chyby kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="1b22f-163">In such a case, a set of partial definitions can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="1b22f-164">Další informace najdete v tématu o [typu propagace](../../programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="1b22f-164">For more information, see [Type Promotion](../../programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
     <span data-ttu-id="1b22f-165">Kompilátor sloučí částečné definice pouze v případě, že jsou jejich plně kvalifikované cesty identické.</span><span class="sxs-lookup"><span data-stu-id="1b22f-165">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
 <span data-ttu-id="1b22f-166">`Partial`Klíčové slovo lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="1b22f-166">The `Partial` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="1b22f-167">Class – příkaz</span><span class="sxs-lookup"><span data-stu-id="1b22f-167">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="1b22f-168">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="1b22f-168">Structure Statement</span></span>](../statements/structure-statement.md)  
  
## <a name="example"></a><span data-ttu-id="1b22f-169">Příklad</span><span class="sxs-lookup"><span data-stu-id="1b22f-169">Example</span></span>  
 <span data-ttu-id="1b22f-170">V následujícím příkladu je rozdělena definice třídy `sampleClass` do dvou deklarací, z nichž každá definuje jiný `Sub` postup.</span><span class="sxs-lookup"><span data-stu-id="1b22f-170">The following example splits the definition of class `sampleClass` into two declarations, each of which defines a different `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 <span data-ttu-id="1b22f-171">Dvě částečné definice v předchozím příkladu můžou být ve stejném zdrojovém souboru nebo ve dvou různých zdrojových souborech.</span><span class="sxs-lookup"><span data-stu-id="1b22f-171">The two partial definitions in the preceding example could be in the same source file or in two different source files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b22f-172">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b22f-172">See also</span></span>

- [<span data-ttu-id="1b22f-173">Class – příkaz</span><span class="sxs-lookup"><span data-stu-id="1b22f-173">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="1b22f-174">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="1b22f-174">Structure Statement</span></span>](../statements/structure-statement.md)
- [<span data-ttu-id="1b22f-175">Propagace typu</span><span class="sxs-lookup"><span data-stu-id="1b22f-175">Type Promotion</span></span>](../../programming-guide/language-features/declared-elements/type-promotion.md)
- [<span data-ttu-id="1b22f-176">Shadows</span><span class="sxs-lookup"><span data-stu-id="1b22f-176">Shadows</span></span>](shadows.md)
- [<span data-ttu-id="1b22f-177">Obecné typy v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1b22f-177">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="1b22f-178">Částečné metody</span><span class="sxs-lookup"><span data-stu-id="1b22f-178">Partial Methods</span></span>](../../programming-guide/language-features/procedures/partial-methods.md)
