---
title: "Přetížení operátoru (F#)"
description: "Naučte se přetížení aritmetické operátory ve třídě nebo typ záznamu a na globální úrovni v jazyce F #."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 019277ed-f649-4fa5-ad43-097865f449d9
ms.openlocfilehash: 76ddab5339e11d71bb326b60d727017eb838ccf4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="operator-overloading"></a><span data-ttu-id="73513-104">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="73513-104">Operator Overloading</span></span>

<span data-ttu-id="73513-105">Toto téma popisuje, jak přetěžovat aritmetické operátory ve třídě nebo v typu záznamu a na globální úrovni.</span><span class="sxs-lookup"><span data-stu-id="73513-105">This topic describes how to overload arithmetic operators in a class or record type, and at the global level.</span></span>


## <a name="syntax"></a><span data-ttu-id="73513-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73513-106">Syntax</span></span>

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a><span data-ttu-id="73513-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73513-107">Remarks</span></span>
<span data-ttu-id="73513-108">V předchozích syntaxi *symbol operátoru* je jedním z `+`, `-`, `*`, `/`, `=`a tak dále.</span><span class="sxs-lookup"><span data-stu-id="73513-108">In the previous syntax, the *operator-symbol* is one of `+`, `-`, `*`, `/`, `=`, and so on.</span></span> <span data-ttu-id="73513-109">*Seznam parametrů* určuje operandy v pořadí, jsou zobrazeny v obvyklé syntaxi pro tento operátor.</span><span class="sxs-lookup"><span data-stu-id="73513-109">The *parameter-list* specifies the operands in the order they appear in the usual syntax for that operator.</span></span> <span data-ttu-id="73513-110">*Metoda textu* vytvoří výslednou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="73513-110">The *method-body* constructs the resulting value.</span></span>

<span data-ttu-id="73513-111">Přetížení operátoru musí být statické.</span><span class="sxs-lookup"><span data-stu-id="73513-111">Operator overloads for operators must be static.</span></span> <span data-ttu-id="73513-112">Operátor přetížení unárních operátorů, například `+` a `-`, musíte použít tildou (`~`) v *symbol operátoru* k označení, že je operátor unární operátor a binární operátor, jak je znázorněno Následující prohlášení.</span><span class="sxs-lookup"><span data-stu-id="73513-112">Operator overloads for unary operators, such as `+` and `-`, must use a tilde (`~`) in the *operator-symbol* to indicate that the operator is a unary operator and not a binary operator, as shown in the following declaration.</span></span>

```fsharp
static member (~-) (v : Vector)
```

<span data-ttu-id="73513-113">Následující kód ukazuje třídu Vector, která má pouze dva operátory, jeden pro unární mínus a jeden pro násobení pomocí skaláru.</span><span class="sxs-lookup"><span data-stu-id="73513-113">The following code illustrates a vector class that has just two operators, one for unary minus and one for multiplication by a scalar.</span></span> <span data-ttu-id="73513-114">V tomto příkladu jsou pro skalární násobení potřeba dvě přetížení, protože operátor musí fungovat bez ohledu na pořadí vektoru a skaláru.</span><span class="sxs-lookup"><span data-stu-id="73513-114">In the example, two overloads for scalar multiplication are needed because the operator must work regardless of the order in which the vector and scalar appear.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a><span data-ttu-id="73513-115">Vytvoření nových operátorů</span><span class="sxs-lookup"><span data-stu-id="73513-115">Creating New Operators</span></span>
<span data-ttu-id="73513-116">Přetížit lze všechny standardní operátory, avšak můžete také vytvořit nové operátory mimo sekvence určitých znaků.</span><span class="sxs-lookup"><span data-stu-id="73513-116">You can overload all the standard operators, but you can also create new operators out of sequences of certain characters.</span></span> <span data-ttu-id="73513-117">Operátor znaky jsou povoleny `!`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, a `~`.</span><span class="sxs-lookup"><span data-stu-id="73513-117">Allowed operator characters are `!`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, and `~`.</span></span> <span data-ttu-id="73513-118">Znak `~` má zvláštní význam, který vytváří z operátoru unární operátor a není součástí sekvence znaků operátoru.</span><span class="sxs-lookup"><span data-stu-id="73513-118">The `~` character has the special meaning of making an operator unary, and is not part of the operator character sequence.</span></span> <span data-ttu-id="73513-119">Ne všechny operátory můžete provedeny unární.</span><span class="sxs-lookup"><span data-stu-id="73513-119">Not all operators can be made unary.</span></span>

<span data-ttu-id="73513-120">V závislosti na přesné posloupnosti znaků bude mít operátor určitou přednost a asociativitu.</span><span class="sxs-lookup"><span data-stu-id="73513-120">Depending on the exact character sequence you use, your operator will have a certain precedence and associativity.</span></span> <span data-ttu-id="73513-121">Asociativita může být buď zleva doprava, nebo zprava doleva a používá se při zobrazení sekvence operátorů stejné úrovně priority bez použití závorek.</span><span class="sxs-lookup"><span data-stu-id="73513-121">Associativity can be either left to right or right to left and is used whenever operators of the same level of precedence appear in sequence without parentheses.</span></span>

<span data-ttu-id="73513-122">Znak operátoru `.` neovlivňuje prioritu, takže pokud je například třeba definovat vlastní verzi násobení, která má stejnou prioritu a asociativitu operátorů jako obyčejné násobení, je možné vytvořit operátory, jako například `.*`.</span><span class="sxs-lookup"><span data-stu-id="73513-122">The operator character `.` does not affect precedence, so that, for example, if you want to define your own version of multiplication that has the same precedence and associativity as ordinary multiplication, you could create operators such as `.*`.</span></span>

<span data-ttu-id="73513-123">Pouze operátory `?` a `?<-` může začínat `?`.</span><span class="sxs-lookup"><span data-stu-id="73513-123">Only the operators `?` and `?<-` may start with `?`.</span></span>

<span data-ttu-id="73513-124">Tabulka zobrazující prioritu všechny operátory v jazyce F # lze nalézt v [operátor referenční dokumentace symbolů a](symbol-and-operator-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="73513-124">A table that shows the precedence of all operators in F# can be found in [Symbol and Operator Reference](symbol-and-operator-reference/index.md).</span></span>


## <a name="overloaded-operator-names"></a><span data-ttu-id="73513-125">Názvy přetíženého operátoru</span><span class="sxs-lookup"><span data-stu-id="73513-125">Overloaded Operator Names</span></span>
<span data-ttu-id="73513-126">Když kompilátor jazyka F# kompiluje výraz operátoru, generuje metodu, která má pro tento operátor název vygenerovaný kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="73513-126">When the F# compiler compiles an operator expression, it generates a method that has a compiler-generated name for that operator.</span></span> <span data-ttu-id="73513-127">Jde o název, který se pro metodu zobrazuje v jazyce MSIL (Microsoft Intermediate Language) a také v reflexi a v technologii IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="73513-127">This is the name that appears in the Microsoft intermediate language (MSIL) for the method, and also in reflection and IntelliSense.</span></span> <span data-ttu-id="73513-128">V kódu jazyka F# obvykle není nutné tyto názvy používat.</span><span class="sxs-lookup"><span data-stu-id="73513-128">You do not normally need to use these names in F# code.</span></span>

<span data-ttu-id="73513-129">Následující tabulka uvádí standardní operátory a jejich odpovídající vygenerované názvy.</span><span class="sxs-lookup"><span data-stu-id="73513-129">The following table shows the standard operators and their corresponding generated names.</span></span>



|<span data-ttu-id="73513-130">Operátor</span><span class="sxs-lookup"><span data-stu-id="73513-130">Operator</span></span>|<span data-ttu-id="73513-131">Vygenerovaný název</span><span class="sxs-lookup"><span data-stu-id="73513-131">Generated name</span></span>|
|--------|--------------|
|`[]`|`op_Nil`|
|`::`|`op_Cons`|
|`+`|`op_Addition`|
|`-`|`op_Subtraction`|
|`*`|`op_Multiply`|
|`/`|`op_Division`|
|`@`|`op_Append`|
|`^`|`op_Concatenate`|
|`%`|`op_Modulus`|
|`&&&`|`op_BitwiseAnd`|
|<code>&#124;&#124;&#124;</code>|`op_BitwiseOr`|
|`^^^`|`op_ExclusiveOr`|
|`<<<`|`op_LeftShift`|
|`~~~`|`op_LogicalNot`|
|`>>>`|`op_RightShift`|
|`~+`|`op_UnaryPlus`|
|`~-`|`op_UnaryNegation`|
|`=`|`op_Equality`|
|`<=`|`op_LessThanOrEqual`|
|`>=`|`op_GreaterThanOrEqual`|
|`<`|`op_LessThan`|
|`>`|`op_GreaterThan`|
|`?`|`op_Dynamic`|
|`?<-`|`op_DynamicAssignment`|
|<code>&#124;></code>|`op_PipeRight`|
|<code><&#124;</code>|`op_PipeLeft`|
|`!`|`op_Dereference`|
|`>>`|`op_ComposeRight`|
|`<<`|`op_ComposeLeft`|
|`<@ @>`|`op_Quotation`|
|`<@@ @@>`|`op_QuotationUntyped`|
|`+=`|`op_AdditionAssignment`|
|`-=`|`op_SubtractionAssignment`|
|`*=`|`op_MultiplyAssignment`|
|`/=`|`op_DivisionAssignment`|
|`..`|`op_Range`|
|`.. ..`|`op_RangeStep`|
<span data-ttu-id="73513-132">Další kombinace znaků operátoru, které zde nejsou uvedeny, lze použít jako operátory a mohou mít názvy, jež jsou vytvořeny zřetězením názvů jednotlivých znaků z následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="73513-132">Other combinations of operator characters that are not listed here can be used as operators and have names that are made up by concatenating names for the individual characters from the following table.</span></span> <span data-ttu-id="73513-133">Například +!</span><span class="sxs-lookup"><span data-stu-id="73513-133">For example, +!</span></span> <span data-ttu-id="73513-134">stane `op_PlusBang`.</span><span class="sxs-lookup"><span data-stu-id="73513-134">becomes `op_PlusBang`.</span></span>



|<span data-ttu-id="73513-135">Znak operátoru</span><span class="sxs-lookup"><span data-stu-id="73513-135">Operator character</span></span>|<span data-ttu-id="73513-136">Název</span><span class="sxs-lookup"><span data-stu-id="73513-136">Name</span></span>|
|------------------|----|
|`>`|`Greater`|
|`<`|`Less`|
|`+`|`Plus`|
|`-`|`Minus`|
|`*`|`Multiply`|
|`/`|`Divide`|
|`=`|`Equals`|
|`~`|`Twiddle`|
|`%`|`Percent`|
|`.`|`Dot`|
|`&`|`Amp`|
|<code>&#124;</code>|`Bar`|
|`@`|`At`|
|`^`|`Hat`|
|`!`|`Bang`|
|`?`|`Qmark`|
|`(`|`LParen`|
|`,`|`Comma`|
|`)`|`RParen`|
|`[`|`LBrack`|
|`]`|`RBrack`|

## <a name="prefix-and-infix-operators"></a><span data-ttu-id="73513-137">Operátory Prefix a Infix</span><span class="sxs-lookup"><span data-stu-id="73513-137">Prefix and Infix Operators</span></span>
<span data-ttu-id="73513-138">*Předpony* operátory jsou očekávané před operand nebo operandy, podobně jako funkce.</span><span class="sxs-lookup"><span data-stu-id="73513-138">*Prefix* operators are expected to be placed in front of an operand or operands, much like a function.</span></span> <span data-ttu-id="73513-139">*Infix* operátory jsou očekávané mezi dva operandy.</span><span class="sxs-lookup"><span data-stu-id="73513-139">*Infix* operators are expected to be placed between the two operands.</span></span>

<span data-ttu-id="73513-140">Pouze některé operátory lze používat jako operátory Prefix.</span><span class="sxs-lookup"><span data-stu-id="73513-140">Only certain operators can be used as prefix operators.</span></span> <span data-ttu-id="73513-141">Některé operátory jsou vždy operátory Prefix, ostatní mohou být Prefix nebo Infix a zbývající jsou vždy operátory Infix.</span><span class="sxs-lookup"><span data-stu-id="73513-141">Some operators are always prefix operators, others can be infix or prefix, and the rest are always infix operators.</span></span> <span data-ttu-id="73513-142">Operátory, které začínají znakem `!`, s výjimkou `!=` a operátoru `~` nebo opakované sekvence`~`, jsou vždy operátory Prefix.</span><span class="sxs-lookup"><span data-stu-id="73513-142">Operators that begin with `!`, except `!=`, and the operator `~`, or repeated sequences of`~`, are always prefix operators.</span></span> <span data-ttu-id="73513-143">Operátory `+`, `-`, `+.`, `-.`, `&`, `&&`, `%` a `%%` mohou být operátory Prefix nebo Infix.</span><span class="sxs-lookup"><span data-stu-id="73513-143">The operators `+`, `-`, `+.`, `-.`, `&`, `&&`, `%`, and `%%` can be prefix operators or infix operators.</span></span> <span data-ttu-id="73513-144">Rozlišovat mezi Prefix a Infix verzí operátoru lze přidáním znaku `~` na začátek operátoru Prefix, a to při jeho definici.</span><span class="sxs-lookup"><span data-stu-id="73513-144">You distinguish the prefix version of these operators from the infix version by adding a `~` at the beginning of a prefix operator when it is defined.</span></span> <span data-ttu-id="73513-145">Znak `~` se nebude používat při použití operátoru, ale pouze při jeho definici.</span><span class="sxs-lookup"><span data-stu-id="73513-145">The `~` is not used when you use the operator, only when it is defined.</span></span>

## <a name="example"></a><span data-ttu-id="73513-146">Příklad</span><span class="sxs-lookup"><span data-stu-id="73513-146">Example</span></span>

<span data-ttu-id="73513-147">Následující kód ukazuje použití přetěžování pro implementaci typu zlomku.</span><span class="sxs-lookup"><span data-stu-id="73513-147">The following code illustrates the use of operator overloading to implement a fraction type.</span></span> <span data-ttu-id="73513-148">Zlomek je reprezentován čitatelem a jmenovatelem.</span><span class="sxs-lookup"><span data-stu-id="73513-148">A fraction is represented by a numerator and a denominator.</span></span> <span data-ttu-id="73513-149">Funkce `hcf` se používá k určení nejvyššího společného faktoru, který slouží k redukci zlomků.</span><span class="sxs-lookup"><span data-stu-id="73513-149">The function `hcf` is used to determine the highest common factor, which is used to reduce fractions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

<span data-ttu-id="73513-150">**Výstup:**</span><span class="sxs-lookup"><span data-stu-id="73513-150">**Output:**</span></span>

```
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a><span data-ttu-id="73513-151">Operátory na globální úrovni</span><span class="sxs-lookup"><span data-stu-id="73513-151">Operators at the Global Level</span></span>
<span data-ttu-id="73513-152">Je také možné definovat operátory na globální úrovni.</span><span class="sxs-lookup"><span data-stu-id="73513-152">You can also define operators at the global level.</span></span> <span data-ttu-id="73513-153">Následující kód definuje operátor `+?`.</span><span class="sxs-lookup"><span data-stu-id="73513-153">The following code defines an operator `+?`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

<span data-ttu-id="73513-154">Výstupem kódu uvedeného výše je `12`.</span><span class="sxs-lookup"><span data-stu-id="73513-154">The output of the above code is `12`.</span></span>

<span data-ttu-id="73513-155">Vzhledem k tomu, že pravidla oboru jazyka F# nařizují, že nově definované operátory mají přednost před vestavěnými operátory, je možné tímto způsobem předefinovat běžné aritmetické operátory.</span><span class="sxs-lookup"><span data-stu-id="73513-155">You can redefine the regular arithmetic operators in this manner because the scoping rules for F# dictate that newly defined operators take precedence over the built-in operators.</span></span>

<span data-ttu-id="73513-156">U globálních operátorů, které mnohdy představují malé funkce, jež jsou nejlépe začlenitelné do volaného kódu, se často používá klíčové slovo `inline`.</span><span class="sxs-lookup"><span data-stu-id="73513-156">The keyword `inline` is often used with global operators, which are often small functions that are best integrated into the calling code.</span></span> <span data-ttu-id="73513-157">Vložení funkcí operátoru umožňuje operátorům pracovat se staticky řešenými typy parametrů za účelem vytvoření staticky řešeného generického kódu.</span><span class="sxs-lookup"><span data-stu-id="73513-157">Making operator functions inline also enables them to work with statically resolved type parameters to produce statically resolved generic code.</span></span> <span data-ttu-id="73513-158">Další informace najdete v tématu [vložené funkce](functions/inline-functions.md) a [statisticky vyřešené parametry typu](generics/statically-resolved-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="73513-158">For more information, see [Inline Functions](functions/inline-functions.md) and [Statically Resolved Type Parameters](generics/statically-resolved-type-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="73513-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="73513-159">See Also</span></span>
[<span data-ttu-id="73513-160">Členy</span><span class="sxs-lookup"><span data-stu-id="73513-160">Members</span></span>](members/index.md)
