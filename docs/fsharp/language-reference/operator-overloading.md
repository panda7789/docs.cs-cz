---
title: Přetížení operátoru (F#)
description: 'Zjistěte, jak přetěžovat aritmetické operátory ve třídě nebo typ záznamu a na globální úrovni v jazyce F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 6232ebf215289e6a22b9d77fbd5fa67b82460486
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "44087296"
---
# <a name="operator-overloading"></a><span data-ttu-id="493ff-103">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="493ff-103">Operator Overloading</span></span>

<span data-ttu-id="493ff-104">Toto téma popisuje, jak přetěžovat aritmetické operátory ve třídě nebo v typu záznamu a na globální úrovni.</span><span class="sxs-lookup"><span data-stu-id="493ff-104">This topic describes how to overload arithmetic operators in a class or record type, and at the global level.</span></span>

## <a name="syntax"></a><span data-ttu-id="493ff-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="493ff-105">Syntax</span></span>

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a><span data-ttu-id="493ff-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="493ff-106">Remarks</span></span>

<span data-ttu-id="493ff-107">V předchozí syntaxi *symbol operátoru* je jedním z `+`, `-`, `*`, `/`, `=`, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="493ff-107">In the previous syntax, the *operator-symbol* is one of `+`, `-`, `*`, `/`, `=`, and so on.</span></span> <span data-ttu-id="493ff-108">*Seznam parametrů* určuje operandy v pořadí, jsou uvedeny v běžné syntaxi pro daný operátor.</span><span class="sxs-lookup"><span data-stu-id="493ff-108">The *parameter-list* specifies the operands in the order they appear in the usual syntax for that operator.</span></span> <span data-ttu-id="493ff-109">*Tělo metody* vytvoří výslednou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="493ff-109">The *method-body* constructs the resulting value.</span></span>

<span data-ttu-id="493ff-110">Přetížení operátoru musí být statické.</span><span class="sxs-lookup"><span data-stu-id="493ff-110">Operator overloads for operators must be static.</span></span> <span data-ttu-id="493ff-111">Přetížení operátoru unárních operátorů, například `+` a `-`, musí pomocí tildy (`~`) v *symbol operátoru* označuje, že operátor unární operátor a binárních operátorů, jak je znázorněno následující deklarace.</span><span class="sxs-lookup"><span data-stu-id="493ff-111">Operator overloads for unary operators, such as `+` and `-`, must use a tilde (`~`) in the *operator-symbol* to indicate that the operator is a unary operator and not a binary operator, as shown in the following declaration.</span></span>

```fsharp
static member (~-) (v : Vector)
```

<span data-ttu-id="493ff-112">Následující kód ukazuje třídu Vector, která má pouze dva operátory, jeden pro unární mínus a jeden pro násobení pomocí skaláru.</span><span class="sxs-lookup"><span data-stu-id="493ff-112">The following code illustrates a vector class that has just two operators, one for unary minus and one for multiplication by a scalar.</span></span> <span data-ttu-id="493ff-113">V tomto příkladu jsou pro skalární násobení potřeba dvě přetížení, protože operátor musí fungovat bez ohledu na pořadí vektoru a skaláru.</span><span class="sxs-lookup"><span data-stu-id="493ff-113">In the example, two overloads for scalar multiplication are needed because the operator must work regardless of the order in which the vector and scalar appear.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a><span data-ttu-id="493ff-114">Vytvoření nových operátorů</span><span class="sxs-lookup"><span data-stu-id="493ff-114">Creating New Operators</span></span>

<span data-ttu-id="493ff-115">Přetížit lze všechny standardní operátory, avšak můžete také vytvořit nové operátory mimo sekvence určitých znaků.</span><span class="sxs-lookup"><span data-stu-id="493ff-115">You can overload all the standard operators, but you can also create new operators out of sequences of certain characters.</span></span> <span data-ttu-id="493ff-116">Povolené znaky operátoru jsou `!`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, a `~`.</span><span class="sxs-lookup"><span data-stu-id="493ff-116">Allowed operator characters are `!`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, and `~`.</span></span> <span data-ttu-id="493ff-117">Znak `~` má zvláštní význam, který vytváří z operátoru unární operátor a není součástí sekvence znaků operátoru.</span><span class="sxs-lookup"><span data-stu-id="493ff-117">The `~` character has the special meaning of making an operator unary, and is not part of the operator character sequence.</span></span> <span data-ttu-id="493ff-118">Ne všechny operátory mohou být unární.</span><span class="sxs-lookup"><span data-stu-id="493ff-118">Not all operators can be made unary.</span></span>

<span data-ttu-id="493ff-119">V závislosti na přesné posloupnosti znaků bude mít operátor určitou přednost a asociativitu.</span><span class="sxs-lookup"><span data-stu-id="493ff-119">Depending on the exact character sequence you use, your operator will have a certain precedence and associativity.</span></span> <span data-ttu-id="493ff-120">Asociativita může být buď zleva doprava, nebo zprava doleva a používá se při zobrazení sekvence operátorů stejné úrovně priority bez použití závorek.</span><span class="sxs-lookup"><span data-stu-id="493ff-120">Associativity can be either left to right or right to left and is used whenever operators of the same level of precedence appear in sequence without parentheses.</span></span>

<span data-ttu-id="493ff-121">Znak operátoru `.` neovlivňuje prioritu, takže pokud je například třeba definovat vlastní verzi násobení, která má stejnou prioritu a asociativitu operátorů jako obyčejné násobení, je možné vytvořit operátory, jako například `.*`.</span><span class="sxs-lookup"><span data-stu-id="493ff-121">The operator character `.` does not affect precedence, so that, for example, if you want to define your own version of multiplication that has the same precedence and associativity as ordinary multiplication, you could create operators such as `.*`.</span></span>

<span data-ttu-id="493ff-122">Pouze operátory `?` a `?<-` může začínat `?`.</span><span class="sxs-lookup"><span data-stu-id="493ff-122">Only the operators `?` and `?<-` may start with `?`.</span></span>

<span data-ttu-id="493ff-123">Tabulku, která ukazuje priority všech operátorů v jazyce F # lze nalézt v [operátor referenční dokumentace symbolů a](symbol-and-operator-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="493ff-123">A table that shows the precedence of all operators in F# can be found in [Symbol and Operator Reference](symbol-and-operator-reference/index.md).</span></span>

## <a name="overloaded-operator-names"></a><span data-ttu-id="493ff-124">Názvy přetíženého operátoru</span><span class="sxs-lookup"><span data-stu-id="493ff-124">Overloaded Operator Names</span></span>

<span data-ttu-id="493ff-125">Když kompilátor jazyka F# kompiluje výraz operátoru, generuje metodu, která má pro tento operátor název vygenerovaný kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="493ff-125">When the F# compiler compiles an operator expression, it generates a method that has a compiler-generated name for that operator.</span></span> <span data-ttu-id="493ff-126">Jde o název, který se pro metodu zobrazuje v jazyce MSIL (Microsoft Intermediate Language) a také v reflexi a v technologii IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="493ff-126">This is the name that appears in the Microsoft intermediate language (MSIL) for the method, and also in reflection and IntelliSense.</span></span> <span data-ttu-id="493ff-127">V kódu jazyka F# obvykle není nutné tyto názvy používat.</span><span class="sxs-lookup"><span data-stu-id="493ff-127">You do not normally need to use these names in F# code.</span></span>

<span data-ttu-id="493ff-128">Následující tabulka uvádí standardní operátory a jejich odpovídající vygenerované názvy.</span><span class="sxs-lookup"><span data-stu-id="493ff-128">The following table shows the standard operators and their corresponding generated names.</span></span>

|<span data-ttu-id="493ff-129">Operátor</span><span class="sxs-lookup"><span data-stu-id="493ff-129">Operator</span></span>|<span data-ttu-id="493ff-130">Vygenerovaný název</span><span class="sxs-lookup"><span data-stu-id="493ff-130">Generated name</span></span>|
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

<span data-ttu-id="493ff-131">Další kombinace znaků operátoru, které zde nejsou uvedeny, lze použít jako operátory a mohou mít názvy, jež jsou vytvořeny zřetězením názvů jednotlivých znaků z následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="493ff-131">Other combinations of operator characters that are not listed here can be used as operators and have names that are made up by concatenating names for the individual characters from the following table.</span></span> <span data-ttu-id="493ff-132">Například +!</span><span class="sxs-lookup"><span data-stu-id="493ff-132">For example, +!</span></span> <span data-ttu-id="493ff-133">změní `op_PlusBang`.</span><span class="sxs-lookup"><span data-stu-id="493ff-133">becomes `op_PlusBang`.</span></span>

|<span data-ttu-id="493ff-134">Znak operátoru</span><span class="sxs-lookup"><span data-stu-id="493ff-134">Operator character</span></span>|<span data-ttu-id="493ff-135">Název</span><span class="sxs-lookup"><span data-stu-id="493ff-135">Name</span></span>|
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

## <a name="prefix-and-infix-operators"></a><span data-ttu-id="493ff-136">Operátory Prefix a Infix</span><span class="sxs-lookup"><span data-stu-id="493ff-136">Prefix and Infix Operators</span></span>

<span data-ttu-id="493ff-137">*Předpona* se očekává, že operátory budou umístěny před operand nebo operandy podobně jako funkce.</span><span class="sxs-lookup"><span data-stu-id="493ff-137">*Prefix* operators are expected to be placed in front of an operand or operands, much like a function.</span></span> <span data-ttu-id="493ff-138">*Infix* se očekává, že operátory budou umístěny mezi dva operandy.</span><span class="sxs-lookup"><span data-stu-id="493ff-138">*Infix* operators are expected to be placed between the two operands.</span></span>

<span data-ttu-id="493ff-139">Pouze některé operátory lze používat jako operátory Prefix.</span><span class="sxs-lookup"><span data-stu-id="493ff-139">Only certain operators can be used as prefix operators.</span></span> <span data-ttu-id="493ff-140">Některé operátory jsou vždy operátory Prefix, ostatní mohou být Prefix nebo Infix a zbývající jsou vždy operátory Infix.</span><span class="sxs-lookup"><span data-stu-id="493ff-140">Some operators are always prefix operators, others can be infix or prefix, and the rest are always infix operators.</span></span> <span data-ttu-id="493ff-141">Operátory, které začínají znakem `!`, s výjimkou `!=` a operátoru `~` nebo opakované sekvence`~`, jsou vždy operátory Prefix.</span><span class="sxs-lookup"><span data-stu-id="493ff-141">Operators that begin with `!`, except `!=`, and the operator `~`, or repeated sequences of`~`, are always prefix operators.</span></span> <span data-ttu-id="493ff-142">Operátory `+`, `-`, `+.`, `-.`, `&`, `&&`, `%` a `%%` mohou být operátory Prefix nebo Infix.</span><span class="sxs-lookup"><span data-stu-id="493ff-142">The operators `+`, `-`, `+.`, `-.`, `&`, `&&`, `%`, and `%%` can be prefix operators or infix operators.</span></span> <span data-ttu-id="493ff-143">Rozlišovat mezi Prefix a Infix verzí operátoru lze přidáním znaku `~` na začátek operátoru Prefix, a to při jeho definici.</span><span class="sxs-lookup"><span data-stu-id="493ff-143">You distinguish the prefix version of these operators from the infix version by adding a `~` at the beginning of a prefix operator when it is defined.</span></span> <span data-ttu-id="493ff-144">Znak `~` se nebude používat při použití operátoru, ale pouze při jeho definici.</span><span class="sxs-lookup"><span data-stu-id="493ff-144">The `~` is not used when you use the operator, only when it is defined.</span></span>

## <a name="example"></a><span data-ttu-id="493ff-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="493ff-145">Example</span></span>

<span data-ttu-id="493ff-146">Následující kód ukazuje použití přetěžování pro implementaci typu zlomku.</span><span class="sxs-lookup"><span data-stu-id="493ff-146">The following code illustrates the use of operator overloading to implement a fraction type.</span></span> <span data-ttu-id="493ff-147">Zlomek je reprezentován čitatelem a jmenovatelem.</span><span class="sxs-lookup"><span data-stu-id="493ff-147">A fraction is represented by a numerator and a denominator.</span></span> <span data-ttu-id="493ff-148">Funkce `hcf` se používá k určení nejvyššího společného faktoru, který slouží k redukci zlomků.</span><span class="sxs-lookup"><span data-stu-id="493ff-148">The function `hcf` is used to determine the highest common factor, which is used to reduce fractions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

<span data-ttu-id="493ff-149">**Výstup:**</span><span class="sxs-lookup"><span data-stu-id="493ff-149">**Output:**</span></span>

```
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a><span data-ttu-id="493ff-150">Operátory na globální úrovni</span><span class="sxs-lookup"><span data-stu-id="493ff-150">Operators at the Global Level</span></span>

<span data-ttu-id="493ff-151">Je také možné definovat operátory na globální úrovni.</span><span class="sxs-lookup"><span data-stu-id="493ff-151">You can also define operators at the global level.</span></span> <span data-ttu-id="493ff-152">Následující kód definuje operátor `+?`.</span><span class="sxs-lookup"><span data-stu-id="493ff-152">The following code defines an operator `+?`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

<span data-ttu-id="493ff-153">Výstupem kódu uvedeného výše je `12`.</span><span class="sxs-lookup"><span data-stu-id="493ff-153">The output of the above code is `12`.</span></span>

<span data-ttu-id="493ff-154">Vzhledem k tomu, že pravidla oboru jazyka F# nařizují, že nově definované operátory mají přednost před vestavěnými operátory, je možné tímto způsobem předefinovat běžné aritmetické operátory.</span><span class="sxs-lookup"><span data-stu-id="493ff-154">You can redefine the regular arithmetic operators in this manner because the scoping rules for F# dictate that newly defined operators take precedence over the built-in operators.</span></span>

<span data-ttu-id="493ff-155">U globálních operátorů, které mnohdy představují malé funkce, jež jsou nejlépe začlenitelné do volaného kódu, se často používá klíčové slovo `inline`.</span><span class="sxs-lookup"><span data-stu-id="493ff-155">The keyword `inline` is often used with global operators, which are often small functions that are best integrated into the calling code.</span></span> <span data-ttu-id="493ff-156">Vložení funkcí operátoru umožňuje operátorům pracovat se staticky řešenými typy parametrů za účelem vytvoření staticky řešeného generického kódu.</span><span class="sxs-lookup"><span data-stu-id="493ff-156">Making operator functions inline also enables them to work with statically resolved type parameters to produce statically resolved generic code.</span></span> <span data-ttu-id="493ff-157">Další informace najdete v tématu [vložené funkce](functions/inline-functions.md) a [statisticky vyřešených parametrů typu](generics/statically-resolved-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="493ff-157">For more information, see [Inline Functions](functions/inline-functions.md) and [Statically Resolved Type Parameters](generics/statically-resolved-type-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="493ff-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="493ff-158">See also</span></span>

- [<span data-ttu-id="493ff-159">Členové</span><span class="sxs-lookup"><span data-stu-id="493ff-159">Members</span></span>](members/index.md)
