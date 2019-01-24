---
title: Znaky typu (Visual Basic)
ms.date: 01/31/2018
helpviewer_keywords:
- '&H prefix for hexadecimal values'
- hexadecimal literals [Visual Basic]
- F literal type character [Visual Basic]
- '& identifier type character'
- type characters [Visual Basic]
- octal literals [Visual Basic]
- literals [Visual Basic], hexadecimal
- '&O prefix for octal values'
- literals [Visual Basic], default types
- defaults, literal types
- C literal type character [Visual Basic]
- type characters [Visual Basic], literal
- $ identifier type character
- L literal type character [Visual Basic]
- UI literal type characters [Visual Basic]
- default literal types [Visual Basic]
- D literal type character [Visual Basic]
- literals [Visual Basic], octal
- S literal type character [Visual Basic]
- '! identifier type character'
- US literal type characters [Visual Basic]
- '% identifier type character'
- data types [Visual Basic], type characters
- characters [Visual Basic], identifier type
- type characters [Visual Basic], identifier
- '# identifier type character'
- identifier type characters [Visual Basic]
- literal type characters [Visual Basic]
- I literal type character [Visual Basic]
- R literal type character [Visual Basic]
- '@ identifier type character'
- UL literal type characters [Visual Basic]
- literal types [Visual Basic], default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
ms.openlocfilehash: a469a08ebadd77d5abbfa95b270784c9ef534691
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734867"
---
# <a name="type-characters-visual-basic"></a><span data-ttu-id="52220-102">Zadejte znaky (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52220-102">Type characters (Visual Basic)</span></span>

<span data-ttu-id="52220-103">Kromě zadání datový typ v příkazu deklarace, můžete vynutit datový typ některé programovací prvky s *znak*.</span><span class="sxs-lookup"><span data-stu-id="52220-103">In addition to specifying a data type in a declaration statement, you can force the data type of some programming elements with a *type character*.</span></span> <span data-ttu-id="52220-104">Znak typu musí následovat bezprostředně za elementem žádné znaky použité jakéhokoli druhu.</span><span class="sxs-lookup"><span data-stu-id="52220-104">The type character must immediately follow the element, with no intervening characters of any kind.</span></span>

<span data-ttu-id="52220-105">Znak typu není součástí názvu elementu.</span><span class="sxs-lookup"><span data-stu-id="52220-105">The type character is not part of the name of the element.</span></span> <span data-ttu-id="52220-106">Element definice se znakem typu může být odkazováno bez znak typu.</span><span class="sxs-lookup"><span data-stu-id="52220-106">An element defined with a type character can be referenced without the type character.</span></span>

## <a name="identifier-type-characters"></a><span data-ttu-id="52220-107">Identifikátor – znaky typu</span><span class="sxs-lookup"><span data-stu-id="52220-107">Identifier type characters</span></span>

<span data-ttu-id="52220-108">Visual Basic poskytuje sadu *identifikátor – znaky typu* , můžete použít v deklaraci zadat datový typ proměnné nebo konstanta.</span><span class="sxs-lookup"><span data-stu-id="52220-108">Visual Basic supplies a set of *identifier type characters* that you can use in a declaration to specify the data type of a variable or constant.</span></span> <span data-ttu-id="52220-109">V následující tabulce jsou uvedeny k dispozici identifikátor – znaky typu s příklady využití.</span><span class="sxs-lookup"><span data-stu-id="52220-109">The following table shows the available identifier type characters with examples of usage.</span></span>
  
|<span data-ttu-id="52220-110">Znak typu identifikátoru</span><span class="sxs-lookup"><span data-stu-id="52220-110">Identifier type character</span></span>|<span data-ttu-id="52220-111">Datový typ</span><span class="sxs-lookup"><span data-stu-id="52220-111">Data type</span></span>|<span data-ttu-id="52220-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="52220-112">Example</span></span>|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 <span data-ttu-id="52220-113">Neexistuje žádný identifikátor – znaky typu pro `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, nebo `UShort` datové typy, nebo pro všechny složené datové typy, například pole nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="52220-113">No identifier type characters exist for the `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="52220-114">V některých případech se můžete připojit `$` znak pro funkci jazyka Visual Basic, například `Left$` místo `Left`, k získání vrácené hodnoty typu `String`.</span><span class="sxs-lookup"><span data-stu-id="52220-114">In some cases, you can append the `$` character to a Visual Basic function, for example `Left$` instead of `Left`, to obtain a returned value of type `String`.</span></span>

<span data-ttu-id="52220-115">Ve všech případech se znak typu identifikátoru musí následovat bezprostředně za název identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="52220-115">In all cases, the identifier type character must immediately follow the identifier name.</span></span>

## <a name="literal-type-characters"></a><span data-ttu-id="52220-116">Literálové znaky typu</span><span class="sxs-lookup"><span data-stu-id="52220-116">Literal type characters</span></span>

<span data-ttu-id="52220-117">A *literálu* je textovou reprezentaci určité hodnoty datového typu.</span><span class="sxs-lookup"><span data-stu-id="52220-117">A *literal* is a textual representation of a particular value of a data type.</span></span>  

### <a name="default-literal-types"></a><span data-ttu-id="52220-118">Výchozí typy literálu</span><span class="sxs-lookup"><span data-stu-id="52220-118">Default literal types</span></span>

<span data-ttu-id="52220-119">Formulář literál jak se zobrazí v kódu obvykle určuje jeho datového typu.</span><span class="sxs-lookup"><span data-stu-id="52220-119">The form of a literal as it appears in your code ordinarily determines its data type.</span></span> <span data-ttu-id="52220-120">V následující tabulce jsou uvedeny tyto výchozí typy.</span><span class="sxs-lookup"><span data-stu-id="52220-120">The following table shows these default types.</span></span>  
  
|<span data-ttu-id="52220-121">Textové formě literál</span><span class="sxs-lookup"><span data-stu-id="52220-121">Textual form of literal</span></span>|<span data-ttu-id="52220-122">Výchozí typ.</span><span class="sxs-lookup"><span data-stu-id="52220-122">Default data type</span></span>|<span data-ttu-id="52220-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="52220-123">Example</span></span>|  
|-----------------------------|-----------------------|-------------|  
|<span data-ttu-id="52220-124">Číselné, ne desetinné části</span><span class="sxs-lookup"><span data-stu-id="52220-124">Numeric, no fractional part</span></span>|`Integer`|`2147483647`|  
|<span data-ttu-id="52220-125">Číselné, ne zlomkové části, příliš velký pro `Integer`</span><span class="sxs-lookup"><span data-stu-id="52220-125">Numeric, no fractional part, too large for `Integer`</span></span>|`Long`|`2147483648`|  
|<span data-ttu-id="52220-126">Číselné, desetinné části</span><span class="sxs-lookup"><span data-stu-id="52220-126">Numeric, fractional part</span></span>|`Double`|`1.2`|  
|<span data-ttu-id="52220-127">Uzavřený do dvojitých uvozovek</span><span class="sxs-lookup"><span data-stu-id="52220-127">Enclosed in double quotation marks</span></span>|`String`|`"A"`|  
|<span data-ttu-id="52220-128">Uzavřený do znaky složených závorek</span><span class="sxs-lookup"><span data-stu-id="52220-128">Enclosed within number signs</span></span>|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a><span data-ttu-id="52220-129">Vynucené typy literálu</span><span class="sxs-lookup"><span data-stu-id="52220-129">Forced literal types</span></span>

<span data-ttu-id="52220-130">Visual Basic poskytuje sadu *– literálové znaky typu*, označuje, který můžete použít k vynucení literál předpokládat, že datový typ jiný než ten její formulář.</span><span class="sxs-lookup"><span data-stu-id="52220-130">Visual Basic supplies a set of *literal type characters*, which you can use to force a literal to assume a data type other than the one its form indicates.</span></span> <span data-ttu-id="52220-131">To provedete přidáním znak na konci literál.</span><span class="sxs-lookup"><span data-stu-id="52220-131">You do this by appending the character to the end of the literal.</span></span> <span data-ttu-id="52220-132">V následující tabulce jsou uvedeny k dispozici – literálové znaky typu s příklady využití.</span><span class="sxs-lookup"><span data-stu-id="52220-132">The following table shows the available literal type characters with examples of usage.</span></span>
  
|<span data-ttu-id="52220-133">Znak typu literálu</span><span class="sxs-lookup"><span data-stu-id="52220-133">Literal type character</span></span>|<span data-ttu-id="52220-134">Datový typ</span><span class="sxs-lookup"><span data-stu-id="52220-134">Data type</span></span>|<span data-ttu-id="52220-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="52220-135">Example</span></span>|  
|----------------------------|---------------|-------------|  
|`S`|`Short`|`I = 347S`|
|`I`|`Integer`|`J = 347I`|
|`L`|`Long`|`K = 347L`|
|`D`|`Decimal`|`X = 347D`|
|`F`|`Single`|`Y = 347F`|
|`R`|`Double`|`Z = 347R`|
|`US`|`UShort`|`L = 347US`|
|`UI`|`UInteger`|`M = 347UI`|
|`UL`|`ULong`|`N = 347UL`|
|`C`|`Char`|`Q = "."C`|

<span data-ttu-id="52220-136">Pro neexistují žádné znaky typu literálu `Boolean`, `Byte`, `Date`, `Object`, `SByte`, nebo `String` datové typy, nebo pro všechny složené datové typy, jako je například pole nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="52220-136">No literal type characters exist for the `Boolean`, `Byte`, `Date`, `Object`, `SByte`, or `String` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="52220-137">Literály můžou používat také identifikátor – znaky typu (`%`, `&`, `@`, `!`, `#`, `$`), jak můžete proměnné, konstanty a výrazy.</span><span class="sxs-lookup"><span data-stu-id="52220-137">Literals can also use the identifier type characters (`%`, `&`, `@`, `!`, `#`, `$`), as can variables, constants, and expressions.</span></span> <span data-ttu-id="52220-138">Ale literál znaky (`S`, `I`, `L`, `D`, `F`, `R`, `C`) lze použít pouze s literály.</span><span class="sxs-lookup"><span data-stu-id="52220-138">However, the literal type characters (`S`, `I`, `L`, `D`, `F`, `R`, `C`) can be used only with literals.</span></span>

<span data-ttu-id="52220-139">Ve všech případech se znak typu literálu musí bezprostředně následuje po hodnotě literálu.</span><span class="sxs-lookup"><span data-stu-id="52220-139">In all cases, the literal type character must immediately follow the literal value.</span></span>

## <a name="hexadecimal-binary-and-octal-literals"></a><span data-ttu-id="52220-140">Šestnáctkové binární a osmičkové literály</span><span class="sxs-lookup"><span data-stu-id="52220-140">Hexadecimal, binary, and octal literals</span></span>

<span data-ttu-id="52220-141">Kompilátor interpretuje obvykle celočíselného literálu v systému desetinné číslo (se základem 10) čísla.</span><span class="sxs-lookup"><span data-stu-id="52220-141">The compiler normally interprets an integer literal to be in the decimal (base 10) number system.</span></span> <span data-ttu-id="52220-142">Můžete také definovat celočíselného literálu jako šestnáctkové číslo (základní 16) číslo s `&H` předpony jako binární soubor (základní 2) číslo s `&B` předponu a jako osmičkové (základní 8) čísla s `&O` předponu.</span><span class="sxs-lookup"><span data-stu-id="52220-142">You can also define an integer literal as a hexadecimal (base 16) number with the `&H` prefix, as a binary (base 2) number with the `&B` prefix, and as an octal (base 8) number with the `&O` prefix.</span></span> <span data-ttu-id="52220-143">Číslic, které následují předpona, která musí odpovídat číslo systému.</span><span class="sxs-lookup"><span data-stu-id="52220-143">The digits that follow the prefix must be appropriate for the number system.</span></span> <span data-ttu-id="52220-144">Následující tabulka ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="52220-144">The following table illustrates this.</span></span>  
  
|<span data-ttu-id="52220-145">Základna čísla</span><span class="sxs-lookup"><span data-stu-id="52220-145">Number base</span></span>|<span data-ttu-id="52220-146">Předpona</span><span class="sxs-lookup"><span data-stu-id="52220-146">Prefix</span></span>|<span data-ttu-id="52220-147">Hodnoty platné číslice</span><span class="sxs-lookup"><span data-stu-id="52220-147">Valid digit values</span></span>|<span data-ttu-id="52220-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="52220-148">Example</span></span>|
|-----------------|------------|------------------------|-------------|
|<span data-ttu-id="52220-149">Šestnáctková (základní 16)</span><span class="sxs-lookup"><span data-stu-id="52220-149">Hexadecimal (base 16)</span></span>|`&H`|<span data-ttu-id="52220-150">0 – 9 a A-F</span><span class="sxs-lookup"><span data-stu-id="52220-150">0-9 and A-F</span></span>|`&HFFFF`|
|<span data-ttu-id="52220-151">Binární soubor (základní 2)</span><span class="sxs-lookup"><span data-stu-id="52220-151">Binary (base 2)</span></span>|`&B`|<span data-ttu-id="52220-152">0-1</span><span class="sxs-lookup"><span data-stu-id="52220-152">0-1</span></span>|`&B01111100`|
|<span data-ttu-id="52220-153">Octal (základní 8)</span><span class="sxs-lookup"><span data-stu-id="52220-153">Octal (base 8)</span></span>|`&O`|<span data-ttu-id="52220-154">0-7</span><span class="sxs-lookup"><span data-stu-id="52220-154">0-7</span></span>|`&O77`|

<span data-ttu-id="52220-155">Spuštění v jazyce Visual Basic 2017, můžete použít znak podtržítka (`_`) jako oddělovač skupin za účelem zlepšení čitelnosti celočíselný literál.</span><span class="sxs-lookup"><span data-stu-id="52220-155">Starting in Visual Basic 2017, you can use the underscore character (`_`) as a group separator to enhance the readability of an integral literal.</span></span> <span data-ttu-id="52220-156">V následujícím příkladu `_` znak pro literál binární soubor pro seskupení 8bitové skupiny:</span><span class="sxs-lookup"><span data-stu-id="52220-156">The following example uses the `_` character to group a binary literal into 8-bit groups:</span></span>

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

<span data-ttu-id="52220-157">Můžete postupovat podle předponou literální znak typu literálu.</span><span class="sxs-lookup"><span data-stu-id="52220-157">You can follow a prefixed literal with a literal type character.</span></span> <span data-ttu-id="52220-158">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="52220-158">The following example shows this.</span></span>

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

<span data-ttu-id="52220-159">V předchozím příkladu `counter` má desetinnou hodnotou-32 768, a `flags` má desetinnou hodnotou +32768.</span><span class="sxs-lookup"><span data-stu-id="52220-159">In the previous example, `counter` has the decimal value of -32768, and `flags` has the decimal value of +32768.</span></span>

<span data-ttu-id="52220-160">Od verze 15.5 jazyka Visual Basic, můžete také použít znak podtržítka (`_`) jako počáteční oddělovač mezi prefix a šestnáctkové, binární nebo osmičkové číslice.</span><span class="sxs-lookup"><span data-stu-id="52220-160">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="52220-161">Příklad:</span><span class="sxs-lookup"><span data-stu-id="52220-161">For example:</span></span>

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a><span data-ttu-id="52220-162">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52220-162">See also</span></span>

- [<span data-ttu-id="52220-163">Datové typy</span><span class="sxs-lookup"><span data-stu-id="52220-163">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="52220-164">Základní datové typy</span><span class="sxs-lookup"><span data-stu-id="52220-164">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="52220-165">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="52220-165">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="52220-166">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="52220-166">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="52220-167">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="52220-167">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="52220-168">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="52220-168">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="52220-169">Datové typy</span><span class="sxs-lookup"><span data-stu-id="52220-169">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
