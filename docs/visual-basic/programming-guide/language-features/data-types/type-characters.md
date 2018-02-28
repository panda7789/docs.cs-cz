---
title: Znaky typu (Visual Basic)
ms.custom: 
ms.date: 01/31/2018
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
author: rpetrusha
ms.author: ronpet
ms.manager: wpickett
ms.openlocfilehash: 20a9a30689fb62a6956987b06470e76eeb42ebab
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2018
---
# <a name="type-characters-visual-basic"></a><span data-ttu-id="8976a-102">Zadejte znaky (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8976a-102">Type characters (Visual Basic)</span></span>

<span data-ttu-id="8976a-103">Kromě určení datový typ v příkazu deklaraci, můžete vynutit datový typ některé elementům programování s *znak typu*.</span><span class="sxs-lookup"><span data-stu-id="8976a-103">In addition to specifying a data type in a declaration statement, you can force the data type of some programming elements with a *type character*.</span></span> <span data-ttu-id="8976a-104">Znak, který typ musí následovat okamžitě element s žádné použité znaky jakéhokoli druhu.</span><span class="sxs-lookup"><span data-stu-id="8976a-104">The type character must immediately follow the element, with no intervening characters of any kind.</span></span>

<span data-ttu-id="8976a-105">Typ znak, který není součástí názvu elementu.</span><span class="sxs-lookup"><span data-stu-id="8976a-105">The type character is not part of the name of the element.</span></span> <span data-ttu-id="8976a-106">Element definovaný s – znak typu může být odkaz bez typu znaků.</span><span class="sxs-lookup"><span data-stu-id="8976a-106">An element defined with a type character can be referenced without the type character.</span></span>

## <a name="identifier-type-characters"></a><span data-ttu-id="8976a-107">Identifikátor – znaky typu</span><span class="sxs-lookup"><span data-stu-id="8976a-107">Identifier type characters</span></span>

<span data-ttu-id="8976a-108">Visual Basic poskytuje sadu *identifikátor – znaky typu* používané v deklaraci zadat datový typ proměnné nebo konstanta.</span><span class="sxs-lookup"><span data-stu-id="8976a-108">Visual Basic supplies a set of *identifier type characters* that you can use in a declaration to specify the data type of a variable or constant.</span></span> <span data-ttu-id="8976a-109">V následující tabulce jsou uvedeny k dispozici identifikátor – znaky typu s příklady využití.</span><span class="sxs-lookup"><span data-stu-id="8976a-109">The following table shows the available identifier type characters with examples of usage.</span></span>
  
|<span data-ttu-id="8976a-110">– Znak typu identifikátoru</span><span class="sxs-lookup"><span data-stu-id="8976a-110">Identifier type character</span></span>|<span data-ttu-id="8976a-111">Datový typ</span><span class="sxs-lookup"><span data-stu-id="8976a-111">Data type</span></span>|<span data-ttu-id="8976a-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="8976a-112">Example</span></span>|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 <span data-ttu-id="8976a-113">Pro neexistují žádné identifikátor – znaky typu `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, nebo `UShort` datové typy, nebo pro všechny složené datové typy, jako je například pole nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="8976a-113">No identifier type characters exist for the `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="8976a-114">V některých případech se můžete připojit `$` znak pro funkci jazyka Visual Basic, například `Left$` místo `Left`, získat vrácená hodnota typu `String`.</span><span class="sxs-lookup"><span data-stu-id="8976a-114">In some cases, you can append the `$` character to a Visual Basic function, for example `Left$` instead of `Left`, to obtain a returned value of type `String`.</span></span>

<span data-ttu-id="8976a-115">Ve všech případech musí následovat znak typu identifikátoru okamžitě název identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="8976a-115">In all cases, the identifier type character must immediately follow the identifier name.</span></span>

## <a name="literal-type-characters"></a><span data-ttu-id="8976a-116">Literálové znaky typu</span><span class="sxs-lookup"><span data-stu-id="8976a-116">Literal type characters</span></span>

<span data-ttu-id="8976a-117">A *literálu* je textovou reprezentaci konkrétní hodnotu datového typu.</span><span class="sxs-lookup"><span data-stu-id="8976a-117">A *literal* is a textual representation of a particular value of a data type.</span></span>  

### <a name="default-literal-types"></a><span data-ttu-id="8976a-118">Výchozí typy literálu</span><span class="sxs-lookup"><span data-stu-id="8976a-118">Default literal types</span></span>

<span data-ttu-id="8976a-119">Formu literál, jak se objevuje v kódu normálně určuje jeho datového typu.</span><span class="sxs-lookup"><span data-stu-id="8976a-119">The form of a literal as it appears in your code ordinarily determines its data type.</span></span> <span data-ttu-id="8976a-120">V následující tabulce jsou tyto typy výchozí.</span><span class="sxs-lookup"><span data-stu-id="8976a-120">The following table shows these default types.</span></span>  
  
|<span data-ttu-id="8976a-121">Textové formě literál</span><span class="sxs-lookup"><span data-stu-id="8976a-121">Textual form of literal</span></span>|<span data-ttu-id="8976a-122">Výchozí datový typ</span><span class="sxs-lookup"><span data-stu-id="8976a-122">Default data type</span></span>|<span data-ttu-id="8976a-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="8976a-123">Example</span></span>|  
|-----------------------------|-----------------------|-------------|  
|<span data-ttu-id="8976a-124">Číselné, ne zlomkové části</span><span class="sxs-lookup"><span data-stu-id="8976a-124">Numeric, no fractional part</span></span>|`Integer`|`2147483647`|  
|<span data-ttu-id="8976a-125">Číselné, ne zlomkové části, příliš velký pro `Integer`</span><span class="sxs-lookup"><span data-stu-id="8976a-125">Numeric, no fractional part, too large for `Integer`</span></span>|`Long`|`2147483648`|  
|<span data-ttu-id="8976a-126">Číselné, zlomkové části</span><span class="sxs-lookup"><span data-stu-id="8976a-126">Numeric, fractional part</span></span>|`Double`|`1.2`|  
|<span data-ttu-id="8976a-127">Uzavřena v uvozovkách</span><span class="sxs-lookup"><span data-stu-id="8976a-127">Enclosed in double quotation marks</span></span>|`String`|`"A"`|  
|<span data-ttu-id="8976a-128">Uzavřené v rámci znaky</span><span class="sxs-lookup"><span data-stu-id="8976a-128">Enclosed within number signs</span></span>|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a><span data-ttu-id="8976a-129">Typy vynucené literálu</span><span class="sxs-lookup"><span data-stu-id="8976a-129">Forced literal types</span></span>

<span data-ttu-id="8976a-130">Visual Basic poskytuje sadu *literálové znaky typu*, určuje, který můžete použít k vynucení literál předpokládat, že datový typ jiný než ten jeho formuláře.</span><span class="sxs-lookup"><span data-stu-id="8976a-130">Visual Basic supplies a set of *literal type characters*, which you can use to force a literal to assume a data type other than the one its form indicates.</span></span> <span data-ttu-id="8976a-131">Provedete to přidáním znak na konec literál.</span><span class="sxs-lookup"><span data-stu-id="8976a-131">You do this by appending the character to the end of the literal.</span></span> <span data-ttu-id="8976a-132">V následující tabulce jsou uvedeny k dispozici literálové znaky typu s příklady využití.</span><span class="sxs-lookup"><span data-stu-id="8976a-132">The following table shows the available literal type characters with examples of usage.</span></span>
  
|<span data-ttu-id="8976a-133">– Znak typu literálu</span><span class="sxs-lookup"><span data-stu-id="8976a-133">Literal type character</span></span>|<span data-ttu-id="8976a-134">Datový typ</span><span class="sxs-lookup"><span data-stu-id="8976a-134">Data type</span></span>|<span data-ttu-id="8976a-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="8976a-135">Example</span></span>|  
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

<span data-ttu-id="8976a-136">Pro neexistují žádné znaky typu literálu `Boolean`, `Byte`, `Date`, `Object`, `SByte`, nebo `String` datové typy, nebo pro jakékoli složené datové typy, jako je například pole nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="8976a-136">No literal type characters exist for the `Boolean`, `Byte`, `Date`, `Object`, `SByte`, or `String` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="8976a-137">Literály můžete také použít identifikátor – znaky typu (`%`, `&`, `@`, `!`, `#`, `$`), jak můžete proměnné, konstanty a výrazy.</span><span class="sxs-lookup"><span data-stu-id="8976a-137">Literals can also use the identifier type characters (`%`, `&`, `@`, `!`, `#`, `$`), as can variables, constants, and expressions.</span></span> <span data-ttu-id="8976a-138">Nicméně skutečné zadejte znaky (`S`, `I`, `L`, `D`, `F`, `R`, `C`) lze použít pouze s literály.</span><span class="sxs-lookup"><span data-stu-id="8976a-138">However, the literal type characters (`S`, `I`, `L`, `D`, `F`, `R`, `C`) can be used only with literals.</span></span>

<span data-ttu-id="8976a-139">Ve všech případech musí následovat znak typu literálu okamžitě literálovou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="8976a-139">In all cases, the literal type character must immediately follow the literal value.</span></span>

## <a name="hexadecimal-binary-and-octal-literals"></a><span data-ttu-id="8976a-140">Hexadecimální, binární a osmičkové literály</span><span class="sxs-lookup"><span data-stu-id="8976a-140">Hexadecimal, binary, and octal literals</span></span>

<span data-ttu-id="8976a-141">Kompilátor normálně interpretuje celé literálu jako v systému desetinné číslo (se základem 10) čísla.</span><span class="sxs-lookup"><span data-stu-id="8976a-141">The compiler normally interprets an integer literal to be in the decimal (base 10) number system.</span></span> <span data-ttu-id="8976a-142">Můžete také definovat celé literálu jako číslo šestnáctkové (základ 16) s `&H` předponou, jako číslo binárního souboru (se základem 2) s `&B` Předpona a jako osmičkové (základ 8) číslo s `&O` předponu.</span><span class="sxs-lookup"><span data-stu-id="8976a-142">You can also define an integer literal as a hexadecimal (base 16) number with the `&H` prefix, as a binary (base 2) number with the `&B` prefix, and as an octal (base 8) number with the `&O` prefix.</span></span> <span data-ttu-id="8976a-143">Musí být vhodný pro systém, počet číslic, které následují předponu.</span><span class="sxs-lookup"><span data-stu-id="8976a-143">The digits that follow the prefix must be appropriate for the number system.</span></span> <span data-ttu-id="8976a-144">Následující tabulka znázorňuje to.</span><span class="sxs-lookup"><span data-stu-id="8976a-144">The following table illustrates this.</span></span>  
  
|<span data-ttu-id="8976a-145">Číslo základní</span><span class="sxs-lookup"><span data-stu-id="8976a-145">Number base</span></span>|<span data-ttu-id="8976a-146">Předpona</span><span class="sxs-lookup"><span data-stu-id="8976a-146">Prefix</span></span>|<span data-ttu-id="8976a-147">Platný dvouciferné hodnoty</span><span class="sxs-lookup"><span data-stu-id="8976a-147">Valid digit values</span></span>|<span data-ttu-id="8976a-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="8976a-148">Example</span></span>|
|-----------------|------------|------------------------|-------------|
|<span data-ttu-id="8976a-149">Šestnáctkové (základ 16)</span><span class="sxs-lookup"><span data-stu-id="8976a-149">Hexadecimal (base 16)</span></span>|`&H`|<span data-ttu-id="8976a-150">0 – 9 a A-F</span><span class="sxs-lookup"><span data-stu-id="8976a-150">0-9 and A-F</span></span>|`&HFFFF`|
|<span data-ttu-id="8976a-151">Binární (se základem 2)</span><span class="sxs-lookup"><span data-stu-id="8976a-151">Binary (base 2)</span></span>|`&B`|<span data-ttu-id="8976a-152">0-1</span><span class="sxs-lookup"><span data-stu-id="8976a-152">0-1</span></span>|`&B01111100`|
|<span data-ttu-id="8976a-153">Octal (základní 8)</span><span class="sxs-lookup"><span data-stu-id="8976a-153">Octal (base 8)</span></span>|`&O`|<span data-ttu-id="8976a-154">0-7</span><span class="sxs-lookup"><span data-stu-id="8976a-154">0-7</span></span>|`&O77`|

<span data-ttu-id="8976a-155">Počínaje 2017 Visual Basic, můžete použít znak podtržítka (`_`) jako oddělovač skupin pro zlepšení čitelnosti celočíselný literál.</span><span class="sxs-lookup"><span data-stu-id="8976a-155">Starting in Visual Basic 2017, you can use the underscore character (`_`) as a group separator to enhance the readability of an integral literal.</span></span> <span data-ttu-id="8976a-156">Následující příklad používá `_` znak, který má skupinu binární literálu do skupin 8bitové:</span><span class="sxs-lookup"><span data-stu-id="8976a-156">The following example uses the `_` character to group a binary literal into 8-bit groups:</span></span>

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

<span data-ttu-id="8976a-157">Můžete postupovat podle předponou literál s – znak typu literálu.</span><span class="sxs-lookup"><span data-stu-id="8976a-157">You can follow a prefixed literal with a literal type character.</span></span> <span data-ttu-id="8976a-158">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="8976a-158">The following example shows this.</span></span>

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

<span data-ttu-id="8976a-159">V předchozím příkladu `counter` má hodnotu decimal-32 768, a `flags` desetinnou hodnotu +32768.</span><span class="sxs-lookup"><span data-stu-id="8976a-159">In the previous example, `counter` has the decimal value of -32768, and `flags` has the decimal value of +32768.</span></span>

<span data-ttu-id="8976a-160">Od verze Visual Basic 15,5, můžete také použít znak podtržítka (`_`) jako oddělovač úvodní mezi předponu a hexadecimální, binary nebo osmičková číslice.</span><span class="sxs-lookup"><span data-stu-id="8976a-160">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="8976a-161">Příklad:</span><span class="sxs-lookup"><span data-stu-id="8976a-161">For example:</span></span>

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a><span data-ttu-id="8976a-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="8976a-162">See Also</span></span>

 [<span data-ttu-id="8976a-163">Datové typy</span><span class="sxs-lookup"><span data-stu-id="8976a-163">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="8976a-164">Základní datové typy</span><span class="sxs-lookup"><span data-stu-id="8976a-164">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="8976a-165">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="8976a-165">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="8976a-166">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8976a-166">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="8976a-167">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="8976a-167">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="8976a-168">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="8976a-168">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="8976a-169">Datové typy</span><span class="sxs-lookup"><span data-stu-id="8976a-169">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
