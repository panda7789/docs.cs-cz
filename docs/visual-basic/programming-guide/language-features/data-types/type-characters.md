---
title: Znaky typu
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
ms.openlocfilehash: 628461c8136946dd902c0a52048eee7c516c52cd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352927"
---
# <a name="type-characters-visual-basic"></a><span data-ttu-id="c6dc2-102">Znaky typu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6dc2-102">Type characters (Visual Basic)</span></span>

<span data-ttu-id="c6dc2-103">Kromě určení datového typu v příkazu deklarace můžete vynutit datový typ některých programovacích prvků se *znakem typu*.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-103">In addition to specifying a data type in a declaration statement, you can force the data type of some programming elements with a *type character*.</span></span> <span data-ttu-id="c6dc2-104">Znak typu musí hned následovat za elementem bez jakýchkoli znaků.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-104">The type character must immediately follow the element, with no intervening characters of any kind.</span></span>

<span data-ttu-id="c6dc2-105">Znak typu není součástí názvu elementu.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-105">The type character is not part of the name of the element.</span></span> <span data-ttu-id="c6dc2-106">Element definovaný s znakem typu může být odkazován bez znaku typu.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-106">An element defined with a type character can be referenced without the type character.</span></span>

## <a name="identifier-type-characters"></a><span data-ttu-id="c6dc2-107">Znaky typu identifikátoru</span><span class="sxs-lookup"><span data-stu-id="c6dc2-107">Identifier type characters</span></span>

<span data-ttu-id="c6dc2-108">Visual Basic poskytuje sadu *znaků typu identifikátoru* , které lze použít v deklaraci k určení datového typu proměnné nebo konstanty.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-108">Visual Basic supplies a set of *identifier type characters* that you can use in a declaration to specify the data type of a variable or constant.</span></span> <span data-ttu-id="c6dc2-109">Následující tabulka uvádí dostupné znaky typu identifikátoru s příklady použití.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-109">The following table shows the available identifier type characters with examples of usage.</span></span>
  
|<span data-ttu-id="c6dc2-110">Znak typu identifikátoru</span><span class="sxs-lookup"><span data-stu-id="c6dc2-110">Identifier type character</span></span>|<span data-ttu-id="c6dc2-111">Typ dat</span><span class="sxs-lookup"><span data-stu-id="c6dc2-111">Data type</span></span>|<span data-ttu-id="c6dc2-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6dc2-112">Example</span></span>|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 <span data-ttu-id="c6dc2-113">Neexistují žádné znaky typu identifikátoru pro `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`nebo `UShort` datových typů nebo pro všechny složené datové typy, jako jsou pole nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-113">No identifier type characters exist for the `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="c6dc2-114">V některých případech můžete `$` znak připojit k funkci Visual Basic, například `Left$` místo `Left`, a získat tak vrácenou hodnotu typu `String`.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-114">In some cases, you can append the `$` character to a Visual Basic function, for example `Left$` instead of `Left`, to obtain a returned value of type `String`.</span></span>

<span data-ttu-id="c6dc2-115">Ve všech případech znak typu identifikátoru musí hned následovat za názvem identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-115">In all cases, the identifier type character must immediately follow the identifier name.</span></span>

## <a name="literal-type-characters"></a><span data-ttu-id="c6dc2-116">Literálové znaky typu</span><span class="sxs-lookup"><span data-stu-id="c6dc2-116">Literal type characters</span></span>

<span data-ttu-id="c6dc2-117">*Literál* je textová reprezentace konkrétní hodnoty datového typu.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-117">A *literal* is a textual representation of a particular value of a data type.</span></span>  

### <a name="default-literal-types"></a><span data-ttu-id="c6dc2-118">Výchozí typy literálů</span><span class="sxs-lookup"><span data-stu-id="c6dc2-118">Default literal types</span></span>

<span data-ttu-id="c6dc2-119">Tvar literálu, který se zobrazí ve vašem kódu, obvykle určuje jeho datový typ.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-119">The form of a literal as it appears in your code ordinarily determines its data type.</span></span> <span data-ttu-id="c6dc2-120">Následující tabulka ukazuje tyto výchozí typy.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-120">The following table shows these default types.</span></span>  
  
|<span data-ttu-id="c6dc2-121">Textový tvar literálu</span><span class="sxs-lookup"><span data-stu-id="c6dc2-121">Textual form of literal</span></span>|<span data-ttu-id="c6dc2-122">Výchozí datový typ</span><span class="sxs-lookup"><span data-stu-id="c6dc2-122">Default data type</span></span>|<span data-ttu-id="c6dc2-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6dc2-123">Example</span></span>|  
|-----------------------------|-----------------------|-------------|  
|<span data-ttu-id="c6dc2-124">Číselná, bez zlomkové části</span><span class="sxs-lookup"><span data-stu-id="c6dc2-124">Numeric, no fractional part</span></span>|`Integer`|`2147483647`|  
|<span data-ttu-id="c6dc2-125">Číselná, bez zlomkové součásti, je pro `Integer` moc velká.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-125">Numeric, no fractional part, too large for `Integer`</span></span>|`Long`|`2147483648`|  
|<span data-ttu-id="c6dc2-126">Číselná, Zlomková část</span><span class="sxs-lookup"><span data-stu-id="c6dc2-126">Numeric, fractional part</span></span>|`Double`|`1.2`|  
|<span data-ttu-id="c6dc2-127">Uzavřeno do dvojitých uvozovek</span><span class="sxs-lookup"><span data-stu-id="c6dc2-127">Enclosed in double quotation marks</span></span>|`String`|`"A"`|  
|<span data-ttu-id="c6dc2-128">Uzavřeno v symbolech čísla</span><span class="sxs-lookup"><span data-stu-id="c6dc2-128">Enclosed within number signs</span></span>|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a><span data-ttu-id="c6dc2-129">Typy vynucených literálů</span><span class="sxs-lookup"><span data-stu-id="c6dc2-129">Forced literal types</span></span>

<span data-ttu-id="c6dc2-130">Visual Basic poskytuje sadu *literálních znaků*, které lze použít k vynucení literálu, který předpokládá, že typ dat je jiný než ten, který formulář označuje.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-130">Visual Basic supplies a set of *literal type characters*, which you can use to force a literal to assume a data type other than the one its form indicates.</span></span> <span data-ttu-id="c6dc2-131">Provedete to tak, že na konec literálu připojíte znak.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-131">You do this by appending the character to the end of the literal.</span></span> <span data-ttu-id="c6dc2-132">V následující tabulce jsou uvedeny dostupné znaky literálového typu s příklady použití.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-132">The following table shows the available literal type characters with examples of usage.</span></span>
  
|<span data-ttu-id="c6dc2-133">Literál – znak typu</span><span class="sxs-lookup"><span data-stu-id="c6dc2-133">Literal type character</span></span>|<span data-ttu-id="c6dc2-134">Typ dat</span><span class="sxs-lookup"><span data-stu-id="c6dc2-134">Data type</span></span>|<span data-ttu-id="c6dc2-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6dc2-135">Example</span></span>|  
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

<span data-ttu-id="c6dc2-136">Pro `Boolean`, `Byte`, `Date`, `Object`, `SByte`nebo pro datové typy, jako jsou například pole nebo struktury, neexistuje žádný typ literálních znaků.`String`</span><span class="sxs-lookup"><span data-stu-id="c6dc2-136">No literal type characters exist for the `Boolean`, `Byte`, `Date`, `Object`, `SByte`, or `String` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="c6dc2-137">Literály mohou také používat znaky typu identifikátoru (`%`, `&`, `@`, `!`, `#`, `$`), jako jsou proměnné, konstanty a výrazy.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-137">Literals can also use the identifier type characters (`%`, `&`, `@`, `!`, `#`, `$`), as can variables, constants, and expressions.</span></span> <span data-ttu-id="c6dc2-138">Literální znaky typu (`S`, `I`, `L`, `D`, `F`, `R`, `C`) však lze použít pouze s literály.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-138">However, the literal type characters (`S`, `I`, `L`, `D`, `F`, `R`, `C`) can be used only with literals.</span></span>

<span data-ttu-id="c6dc2-139">Ve všech případech znak literálního typu musí bezprostředně následovat po hodnotě literálu.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-139">In all cases, the literal type character must immediately follow the literal value.</span></span>

## <a name="hexadecimal-binary-and-octal-literals"></a><span data-ttu-id="c6dc2-140">Šestnáctkové, binární a osmičkové literály</span><span class="sxs-lookup"><span data-stu-id="c6dc2-140">Hexadecimal, binary, and octal literals</span></span>

<span data-ttu-id="c6dc2-141">Kompilátor obvykle interpretuje celočíselný literál, který je v desítkovém systému desítkových čísel (desítkový 10).</span><span class="sxs-lookup"><span data-stu-id="c6dc2-141">The compiler normally interprets an integer literal to be in the decimal (base 10) number system.</span></span> <span data-ttu-id="c6dc2-142">Můžete také definovat celočíselný literál jako hexadecimální (základní 16) číslo s předponou `&H` jako binární (základní 2) číslo s předponou `&B` a jako osmičkové (desítkové 8) číslo s předponou `&O`.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-142">You can also define an integer literal as a hexadecimal (base 16) number with the `&H` prefix, as a binary (base 2) number with the `&B` prefix, and as an octal (base 8) number with the `&O` prefix.</span></span> <span data-ttu-id="c6dc2-143">Číslice, které následují předponu, musí být vhodné pro číselný systém.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-143">The digits that follow the prefix must be appropriate for the number system.</span></span> <span data-ttu-id="c6dc2-144">To je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-144">The following table illustrates this.</span></span>  
  
|<span data-ttu-id="c6dc2-145">Základ čísla</span><span class="sxs-lookup"><span data-stu-id="c6dc2-145">Number base</span></span>|<span data-ttu-id="c6dc2-146">směr</span><span class="sxs-lookup"><span data-stu-id="c6dc2-146">Prefix</span></span>|<span data-ttu-id="c6dc2-147">Platné číselné hodnoty</span><span class="sxs-lookup"><span data-stu-id="c6dc2-147">Valid digit values</span></span>|<span data-ttu-id="c6dc2-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6dc2-148">Example</span></span>|
|-----------------|------------|------------------------|-------------|
|<span data-ttu-id="c6dc2-149">Šestnáctkový (základní 16)</span><span class="sxs-lookup"><span data-stu-id="c6dc2-149">Hexadecimal (base 16)</span></span>|`&H`|<span data-ttu-id="c6dc2-150">0-9 a a-F</span><span class="sxs-lookup"><span data-stu-id="c6dc2-150">0-9 and A-F</span></span>|`&HFFFF`|
|<span data-ttu-id="c6dc2-151">Binární (základní 2)</span><span class="sxs-lookup"><span data-stu-id="c6dc2-151">Binary (base 2)</span></span>|`&B`|<span data-ttu-id="c6dc2-152">0-1</span><span class="sxs-lookup"><span data-stu-id="c6dc2-152">0-1</span></span>|`&B01111100`|
|<span data-ttu-id="c6dc2-153">Osmičková (základní 8)</span><span class="sxs-lookup"><span data-stu-id="c6dc2-153">Octal (base 8)</span></span>|`&O`|<span data-ttu-id="c6dc2-154">0-7</span><span class="sxs-lookup"><span data-stu-id="c6dc2-154">0-7</span></span>|`&O77`|

<span data-ttu-id="c6dc2-155">Počínaje Visual Basic 2017 lze použít znak podtržítka (`_`) jako oddělovač skupin pro zlepšení čitelnosti integrálního literálu.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-155">Starting in Visual Basic 2017, you can use the underscore character (`_`) as a group separator to enhance the readability of an integral literal.</span></span> <span data-ttu-id="c6dc2-156">V následujícím příkladu se používá znak `_` k seskupení binárního literálu do 8 bitových skupin:</span><span class="sxs-lookup"><span data-stu-id="c6dc2-156">The following example uses the `_` character to group a binary literal into 8-bit groups:</span></span>

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

<span data-ttu-id="c6dc2-157">Můžete postupovat podle předem fixního literálu s literálovým znakem typu.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-157">You can follow a prefixed literal with a literal type character.</span></span> <span data-ttu-id="c6dc2-158">Následující příklad ukazuje toto.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-158">The following example shows this.</span></span>

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

<span data-ttu-id="c6dc2-159">V předchozím příkladu má `counter` desítkovou hodnotu-32768 a `flags` má desítkovou hodnotu + 32768.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-159">In the previous example, `counter` has the decimal value of -32768, and `flags` has the decimal value of +32768.</span></span>

<span data-ttu-id="c6dc2-160">Počínaje Visual Basic 15,5 můžete také použít znak podtržítka (`_`) jako úvodní oddělovač mezi předponou a šestnáctkovou, binární nebo osmičkovou číslicí.</span><span class="sxs-lookup"><span data-stu-id="c6dc2-160">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="c6dc2-161">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c6dc2-161">For example:</span></span>

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a><span data-ttu-id="c6dc2-162">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6dc2-162">See also</span></span>

- [<span data-ttu-id="c6dc2-163">Datové typy</span><span class="sxs-lookup"><span data-stu-id="c6dc2-163">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="c6dc2-164">Základní datové typy</span><span class="sxs-lookup"><span data-stu-id="c6dc2-164">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="c6dc2-165">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="c6dc2-165">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="c6dc2-166">Převody typu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c6dc2-166">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="c6dc2-167">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="c6dc2-167">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="c6dc2-168">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="c6dc2-168">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="c6dc2-169">Datové typy</span><span class="sxs-lookup"><span data-stu-id="c6dc2-169">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
