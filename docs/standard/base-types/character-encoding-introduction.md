---
title: Úvod k kódování znaků v rozhraní .NET
description: Informace o kódování a dekódování znaků v rozhraní .NET.
ms.date: 03/09/2020
no-loc:
- Rune
- char
- string
dev_langs:
- csharp
helpviewer_keywords:
- encoding, understanding
ms.openlocfilehash: 34b1577f8bcea80c1f41b6f9605bf47d132fdb4f
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134407"
---
# <a name="character-encoding-in-net"></a><span data-ttu-id="f2947-103">Kódování znaků v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="f2947-103">Character encoding in .NET</span></span>

<span data-ttu-id="f2947-104">Tento článek obsahuje úvod do systémů kódování znaků, které používá rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="f2947-104">This article provides an introduction to character encoding systems that are used by .NET.</span></span> <span data-ttu-id="f2947-105">Článek <xref:System.String>vysvětluje, jak <xref:System.Char>, <xref:System.Text.Rune>, <xref:System.Globalization.StringInfo> a typy pracovat s Unicode, UTF-16 a UTF-8.</span><span class="sxs-lookup"><span data-stu-id="f2947-105">The article explains how the <xref:System.String>, <xref:System.Char>, <xref:System.Text.Rune>, and <xref:System.Globalization.StringInfo> types work with Unicode, UTF-16, and UTF-8.</span></span>

<span data-ttu-id="f2947-106">Termín *znak* se zde používá v obecném smyslu *toho, co čtenář vnímá jako jeden zobrazovací prvek*.</span><span class="sxs-lookup"><span data-stu-id="f2947-106">The term *character* is used here in the general sense of *what a reader perceives as a single display element*.</span></span> <span data-ttu-id="f2947-107">Běžnými příklady jsou písmeno "a", symbol "@" a emoji "🐂".</span><span class="sxs-lookup"><span data-stu-id="f2947-107">Common examples are the letter "a", the symbol "@", and the emoji "🐂".</span></span> <span data-ttu-id="f2947-108">Někdy to, co vypadá jako jeden znak, se ve skutečnosti skládá z více nezávislých prvků zobrazení, jak vysvětluje část [grafeme clusterů.](#grapheme-clusters)</span><span class="sxs-lookup"><span data-stu-id="f2947-108">Sometimes what looks like one character is actually composed of multiple independent display elements, as the section on [grapheme clusters](#grapheme-clusters) explains.</span></span>

## <a name="the-string-and-char-types"></a><span data-ttu-id="f2947-109">Typy řetězců a znaků</span><span class="sxs-lookup"><span data-stu-id="f2947-109">The string and char types</span></span>

<span data-ttu-id="f2947-110">Instance [třídy string](xref:System.String) představuje určitý text.</span><span class="sxs-lookup"><span data-stu-id="f2947-110">An instance of the [string](xref:System.String) class represents some text.</span></span> <span data-ttu-id="f2947-111">A `string` je logicky posloupnost 16bitových hodnot, z nichž každá je instancí třídy [char.](xref:System.Char)</span><span class="sxs-lookup"><span data-stu-id="f2947-111">A `string` is logically a sequence of 16-bit values, each of which is an instance of the [char](xref:System.Char) struct.</span></span> <span data-ttu-id="f2947-112">[Řetězec. Vlastnost Length](xref:System.String.Length) vrátí `char` počet instancí v instanci. `string`</span><span class="sxs-lookup"><span data-stu-id="f2947-112">The [string.Length](xref:System.String.Length) property returns the number of `char` instances in the `string` instance.</span></span>

<span data-ttu-id="f2947-113">Následující ukázková funkce vytiskne hodnoty v šestnáctkovém zápisu všech `char` `string`instancí v aplikaci :</span><span class="sxs-lookup"><span data-stu-id="f2947-113">The following sample function prints out the values in hexadecimal notation of all the `char` instances in a `string`:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::

<span data-ttu-id="f2947-114">Předat řetězec "Hello" na tuto funkci a získáte následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f2947-114">Pass the string "Hello" to this function, and you get the following output:</span></span>

```csharp
PrintChars("Hello");
```

```output
"Hello".Length = 5
s[0] = 'H' ('\u0048')
s[1] = 'e' ('\u0065')
s[2] = 'l' ('\u006c')
s[3] = 'l' ('\u006c')
s[4] = 'o' ('\u006f')
```

<span data-ttu-id="f2947-115">Každý znak je reprezentován jedinou `char` hodnotou.</span><span class="sxs-lookup"><span data-stu-id="f2947-115">Each character is represented by a single `char` value.</span></span> <span data-ttu-id="f2947-116">Tento vzorec platí pro většinu světových jazyků.</span><span class="sxs-lookup"><span data-stu-id="f2947-116">That pattern holds true for most of the world's languages.</span></span> <span data-ttu-id="f2947-117">Například, tady je výstup pro dva čínské znaky, které zní *Hello*jako *n?*</span><span class="sxs-lookup"><span data-stu-id="f2947-117">For example, here's the output for two Chinese characters that sound like *nǐ hǎo* and mean *Hello*:</span></span>

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

<span data-ttu-id="f2947-118">Pro některé jazyky a pro některé symboly `char` a emodži však trvá dvě instance představují jeden znak.</span><span class="sxs-lookup"><span data-stu-id="f2947-118">However, for some languages and for some symbols and emoji, it takes two `char` instances to represent a single character.</span></span> <span data-ttu-id="f2947-119">Porovnejte například `char` znaky a instance ve slově, které znamená *Osage* v jazyce Osage:</span><span class="sxs-lookup"><span data-stu-id="f2947-119">For example, compare the characters and `char` instances in the word that means *Osage* in the Osage language:</span></span>

```csharp
PrintChars("𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟");
```

```output
"𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟".Length = 17
s[0] = '�' ('\ud801')
s[1] = '�' ('\udccf')
s[2] = '�' ('\ud801')
s[3] = '�' ('\udcd8')
s[4] = '�' ('\ud801')
s[5] = '�' ('\udcfb')
s[6] = '�' ('\ud801')
s[7] = '�' ('\udcd8')
s[8] = '�' ('\ud801')
s[9] = '�' ('\udcfb')
s[10] = '�' ('\ud801')
s[11] = '�' ('\udcdf')
s[12] = ' ' ('\u0020')
s[13] = '�' ('\ud801')
s[14] = '�' ('\udcbb')
s[15] = '�' ('\ud801')
s[16] = '�' ('\udcdf')
```

<span data-ttu-id="f2947-120">V předchozím příkladu je každý znak kromě `char` mezery reprezentován dvěma instancemi.</span><span class="sxs-lookup"><span data-stu-id="f2947-120">In the preceding example, each character except the space is represented by two `char` instances.</span></span>

<span data-ttu-id="f2947-121">Jeden unicode emoji je také `char`reprezentován dvěma s, jak je vidět v následujícím příkladu ukazujícím vůl emoji:</span><span class="sxs-lookup"><span data-stu-id="f2947-121">A single Unicode emoji is also represented by two `char`s, as seen in the following example showing an ox emoji:</span></span>

```
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

<span data-ttu-id="f2947-122">Tyto příklady ukazují, `string.Length`že hodnota , `char` která označuje počet instancí, nemusí nutně označovat počet zobrazených znaků.</span><span class="sxs-lookup"><span data-stu-id="f2947-122">These examples show that the value of `string.Length`, which indicates the number of `char` instances, doesn't necessarily indicate the number of displayed characters.</span></span> <span data-ttu-id="f2947-123">Jedna `char` instance sama o sobě nemusí nutně představovat znak.</span><span class="sxs-lookup"><span data-stu-id="f2947-123">A single `char` instance by itself doesn't necessarily represent a character.</span></span>

<span data-ttu-id="f2947-124">Dvojice, `char` které mapují na jeden znak, se nazývají *náhradní páry*.</span><span class="sxs-lookup"><span data-stu-id="f2947-124">The `char` pairs that map to a single character are called *surrogate pairs*.</span></span> <span data-ttu-id="f2947-125">Chcete-li pochopit, jak fungují, musíte pochopit kódování Unicode a UTF-16.</span><span class="sxs-lookup"><span data-stu-id="f2947-125">To understand how they work, you need to understand Unicode and UTF-16 encoding.</span></span>

## <a name="unicode-code-points"></a><span data-ttu-id="f2947-126">Body kódu Unicode</span><span class="sxs-lookup"><span data-stu-id="f2947-126">Unicode code points</span></span>

<span data-ttu-id="f2947-127">Unicode je mezinárodní standard kódování pro použití na různých platformách a s různými jazyky a skripty.</span><span class="sxs-lookup"><span data-stu-id="f2947-127">Unicode is an international encoding standard for use on various platforms and with various languages and scripts.</span></span>

<span data-ttu-id="f2947-128">Standard Unicode definuje více než 1,1 milionu [bodů kódu](https://www.unicode.org/glossary/#code_point).</span><span class="sxs-lookup"><span data-stu-id="f2947-128">The Unicode Standard defines over 1.1 million [code points](https://www.unicode.org/glossary/#code_point).</span></span> <span data-ttu-id="f2947-129">Bod kódu je celá hodnota, která může `U+10FFFF` být v rozsahu od 0 do (desetinné číslo 1 114 111).</span><span class="sxs-lookup"><span data-stu-id="f2947-129">A code point is an integer value that can range from 0 to `U+10FFFF` (decimal 1,114,111).</span></span> <span data-ttu-id="f2947-130">Některé body kódu jsou přiřazeny písmenům, symbolům nebo emodži.</span><span class="sxs-lookup"><span data-stu-id="f2947-130">Some code points are assigned to letters, symbols, or emoji.</span></span> <span data-ttu-id="f2947-131">Jiné jsou přiřazeny k akcím, které řídí způsob zobrazení textu nebo znaků, například postup na nový řádek.</span><span class="sxs-lookup"><span data-stu-id="f2947-131">Others are assigned to actions that control how text or characters are displayed, such as advance to a new line.</span></span> <span data-ttu-id="f2947-132">Mnoho bodů kódu ještě není přiřazeno.</span><span class="sxs-lookup"><span data-stu-id="f2947-132">Many code points are not yet assigned.</span></span>

<span data-ttu-id="f2947-133">Zde jsou některé příklady přiřazení bodů kódu s odkazy na grafy Unicode, ve kterých se zobrazují:</span><span class="sxs-lookup"><span data-stu-id="f2947-133">Here are some examples of code point assignments, with links to Unicode charts in which they appear:</span></span>

|<span data-ttu-id="f2947-134">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="f2947-134">Decimal</span></span>|<span data-ttu-id="f2947-135">Hex</span><span class="sxs-lookup"><span data-stu-id="f2947-135">Hex</span></span>       |<span data-ttu-id="f2947-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2947-136">Example</span></span>|<span data-ttu-id="f2947-137">Popis</span><span class="sxs-lookup"><span data-stu-id="f2947-137">Description</span></span>|
|------:|----------|-------|-----------|
|<span data-ttu-id="f2947-138">10</span><span class="sxs-lookup"><span data-stu-id="f2947-138">10</span></span>     | `U+000A` |<span data-ttu-id="f2947-139">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="f2947-139">N/A</span></span>| [<span data-ttu-id="f2947-140">PŘÍKON LINKY</span><span class="sxs-lookup"><span data-stu-id="f2947-140">LINE FEED</span></span>](https://www.unicode.org/charts/PDF/U0000.pdf) |
|<span data-ttu-id="f2947-141">65</span><span class="sxs-lookup"><span data-stu-id="f2947-141">65</span></span>     | `U+0061` | <span data-ttu-id="f2947-142">a</span><span class="sxs-lookup"><span data-stu-id="f2947-142">a</span></span> | [<span data-ttu-id="f2947-143">MALÉ PÍSMENO LATINKy A</span><span class="sxs-lookup"><span data-stu-id="f2947-143">LATIN SMALL LETTER A</span></span>](https://www.unicode.org/charts/PDF/U0000.pdf) |
|<span data-ttu-id="f2947-144">562</span><span class="sxs-lookup"><span data-stu-id="f2947-144">562</span></span>    | `U+0232` | <span data-ttu-id="f2947-145">V roce 201</span><span class="sxs-lookup"><span data-stu-id="f2947-145">Ȳ</span></span> | [<span data-ttu-id="f2947-146">Velké písmeno latinky Y s makronem</span><span class="sxs-lookup"><span data-stu-id="f2947-146">LATIN CAPITAL LETTER Y WITH MACRON</span></span>](https://www.unicode.org/charts/PDF/U0180.pdf) |
|<span data-ttu-id="f2947-147">68,675</span><span class="sxs-lookup"><span data-stu-id="f2947-147">68,675</span></span> | `U+10C43`| <span data-ttu-id="f2947-148">𐱃</span><span class="sxs-lookup"><span data-stu-id="f2947-148">𐱃</span></span> | [<span data-ttu-id="f2947-149">OLD TURKIC LETTER ORKHON AT</span><span class="sxs-lookup"><span data-stu-id="f2947-149">OLD TURKIC LETTER ORKHON AT</span></span>](https://www.unicode.org/charts/PDF/U10C00.pdf) |
|<span data-ttu-id="f2947-150">127,801</span><span class="sxs-lookup"><span data-stu-id="f2947-150">127,801</span></span>| `U+1F339`| <span data-ttu-id="f2947-151">🌹</span><span class="sxs-lookup"><span data-stu-id="f2947-151">🌹</span></span> | [<span data-ttu-id="f2947-152">ROSE emodži</span><span class="sxs-lookup"><span data-stu-id="f2947-152">ROSE emoji</span></span>](https://www.unicode.org/charts/PDF/U1F300.pdf) |

<span data-ttu-id="f2947-153">Body kódu jsou obvykle označovány pomocí `U+xxxx`syntaxe , kde `xxxx` je hex kódovaná celočíselná hodnota.</span><span class="sxs-lookup"><span data-stu-id="f2947-153">Code points are customarily referred to by using the syntax `U+xxxx`, where `xxxx` is the hex-encoded integer value.</span></span>

<span data-ttu-id="f2947-154">V celém rozsahu bodů kódu existují dva podrozsahy:</span><span class="sxs-lookup"><span data-stu-id="f2947-154">Within the full range of code points there are two subranges:</span></span>

* <span data-ttu-id="f2947-155">**Základní vícejazyčná rovina (BMP)** v rozsahu `U+0000..U+FFFF`.</span><span class="sxs-lookup"><span data-stu-id="f2947-155">The **Basic Multilingual Plane (BMP)** in the range `U+0000..U+FFFF`.</span></span> <span data-ttu-id="f2947-156">Tato 16bitová řada poskytuje 65 536 bodů kódu, což je dost na pokrytí většiny světových systémů zápisu.</span><span class="sxs-lookup"><span data-stu-id="f2947-156">This 16-bit range provides 65,536 code points, enough to cover the majority of the world's writing systems.</span></span>
* <span data-ttu-id="f2947-157">**Doplňkové kódové body** `U+10000..U+10FFFF`v rozsahu .</span><span class="sxs-lookup"><span data-stu-id="f2947-157">**Supplementary code points** in the range `U+10000..U+10FFFF`.</span></span> <span data-ttu-id="f2947-158">Tato 21bitová oblast poskytuje více než milion dalších bodů kódu, které lze použít pro méně známé jazyky a další účely, jako jsou emodži.</span><span class="sxs-lookup"><span data-stu-id="f2947-158">This 21-bit range provides more than a million additional code points that can be used for less well-known languages and other purposes such as emojis.</span></span>

<span data-ttu-id="f2947-159">Následující diagram znázorňuje vztah mezi BMP a doplňkovými body kódu.</span><span class="sxs-lookup"><span data-stu-id="f2947-159">The following diagram illustrates the relationship between the BMP and the supplementary code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-supplementary.svg" alt-text="BMP a doplňkové kódové body":::

## <a name="utf-16-code-units"></a><span data-ttu-id="f2947-161">Kódové jednotky UTF-16</span><span class="sxs-lookup"><span data-stu-id="f2947-161">UTF-16 code units</span></span>

<span data-ttu-id="f2947-162">16bitový formát transformace Unicode ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) je systém kódování znaků, který používá 16bitové *kódové jednotky* k reprezentaci bodů kódu Unicode.</span><span class="sxs-lookup"><span data-stu-id="f2947-162">16-bit Unicode Transformation Format ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) is a character encoding system that uses 16-bit *code units* to represent Unicode code points.</span></span> <span data-ttu-id="f2947-163">Rozhraní .NET používá UTF-16 ke `string`kódování textu v rozhraní .</span><span class="sxs-lookup"><span data-stu-id="f2947-163">.NET uses UTF-16 to encode the text in a `string`.</span></span> <span data-ttu-id="f2947-164">Instance `char` představuje 16bitovou jednotku kódu.</span><span class="sxs-lookup"><span data-stu-id="f2947-164">A `char` instance represents a 16-bit code unit.</span></span>

<span data-ttu-id="f2947-165">Jedna 16bitová jednotka kódu může představovat libovolný bod kódu v 16bitovém rozsahu základní vícejazyčné roviny.</span><span class="sxs-lookup"><span data-stu-id="f2947-165">A single 16-bit code unit can represent any code point in the 16-bit range of the Basic Multilingual Plane.</span></span> <span data-ttu-id="f2947-166">Ale pro bod kódu v doplňkovéoblasti `char` jsou potřeba dvě instance.</span><span class="sxs-lookup"><span data-stu-id="f2947-166">But for a code point in the supplementary range, two `char` instances are needed.</span></span>

## <a name="surrogate-pairs"></a><span data-ttu-id="f2947-167">Náhradní páry</span><span class="sxs-lookup"><span data-stu-id="f2947-167">Surrogate pairs</span></span>

<span data-ttu-id="f2947-168">Překlad dvou 16bitových hodnot na jednu 21bitovou hodnotu je usnadněn `U+D800` zvláštním `U+DFFF` rozsahem nazývaným náhradní *body kódu*, z do (desetinné 55 296 až 57 343) včetně.</span><span class="sxs-lookup"><span data-stu-id="f2947-168">The translation of two 16-bit values to a single 21-bit value is facilitated by a special range called the *surrogate code points*, from `U+D800` to `U+DFFF` (decimal 55,296 to 57,343), inclusive.</span></span>

<span data-ttu-id="f2947-169">Následující diagram znázorňuje vztah mezi BMP a náhradní body kódu.</span><span class="sxs-lookup"><span data-stu-id="f2947-169">The following diagram illustrates the relationship between the BMP and the surrogate code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-surrogate.svg" alt-text="BMP a náhradní kódové body":::

<span data-ttu-id="f2947-171">Pokud je bod kódu`U+D800..U+DBFF` *vysokého náhradníka* ( )`U+DC00..U+DFFF`bezprostředně následován bodem kódu *nízkého náhradního* ( ), je dvojice interpretována jako doplňkový bod kódu pomocí následujícího vzorce:</span><span class="sxs-lookup"><span data-stu-id="f2947-171">When a *high surrogate* code point (`U+D800..U+DBFF`) is immediately followed by a *low surrogate* code point (`U+DC00..U+DFFF`), the pair is interpreted as a supplementary code point by using the following formula:</span></span>

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

<span data-ttu-id="f2947-172">Tady je stejný vzorec s desítkovou notací:</span><span class="sxs-lookup"><span data-stu-id="f2947-172">Here's the same formula using decimal notation:</span></span>

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

<span data-ttu-id="f2947-173">Bod kódu *s vysokým* náhradním kódem nemá vyšší číselnou hodnotu než bod kódu *s nízkým* náhradním kódem.</span><span class="sxs-lookup"><span data-stu-id="f2947-173">A *high* surrogate code point doesn't have a higher number value than a *low* surrogate code point.</span></span> <span data-ttu-id="f2947-174">Bod kódu s vysokým náhradním kódem se nazývá "vysoká", protože se používá k výpočtu 11 bitů vyššího řádu v rozsahu bodů celého 21bitového kódu.</span><span class="sxs-lookup"><span data-stu-id="f2947-174">The high surrogate code point is called "high" because it's used to calculate the higher-order 11 bits of the full 21-bit code point range.</span></span> <span data-ttu-id="f2947-175">Dolní náhradní bod kódu se používá k výpočtu nižší pořadí 10 bitů.</span><span class="sxs-lookup"><span data-stu-id="f2947-175">The low surrogate code point is used to calculate the lower-order 10 bits.</span></span>

<span data-ttu-id="f2947-176">Například skutečný bod kódu, který odpovídá `0xD83C` náhradní `0xDF39` dvojici a vypočítá se takto:</span><span class="sxs-lookup"><span data-stu-id="f2947-176">For example, the actual code point that corresponds to the surrogate pair `0xD83C` and `0xDF39`  is computed as follows:</span></span>

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

<span data-ttu-id="f2947-177">Zde je stejný výpočet s desítkovou notací:</span><span class="sxs-lookup"><span data-stu-id="f2947-177">Here's the same calculation using decimal notation:</span></span>

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

<span data-ttu-id="f2947-178">Předchozí příklad ukazuje, `"\ud83c\udf39"` že je UTF-16 kódování `U+1F339 ROSE ('🌹')` bodu kódu již bylo zmíněno dříve.</span><span class="sxs-lookup"><span data-stu-id="f2947-178">The preceding example demonstrates that `"\ud83c\udf39"` is the UTF-16 encoding of the `U+1F339 ROSE ('🌹')` code point mentioned earlier.</span></span>

## <a name="unicode-scalar-values"></a><span data-ttu-id="f2947-179">Skalární hodnoty Unicode</span><span class="sxs-lookup"><span data-stu-id="f2947-179">Unicode scalar values</span></span>

<span data-ttu-id="f2947-180">Termín [Unicode skalární hodnota](https://www.unicode.org/glossary/#unicode_scalar_value) odkazuje na všechny body kódu než náhradní body kódu.</span><span class="sxs-lookup"><span data-stu-id="f2947-180">The term [Unicode scalar value](https://www.unicode.org/glossary/#unicode_scalar_value) refers to all code points other than the surrogate code points.</span></span> <span data-ttu-id="f2947-181">Jinými slovy skalární hodnota je libovolný bod kódu, který je přiřazen znak nebo může být přiřazen znak v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="f2947-181">In other words, a scalar value is any code point that is assigned a character or can be assigned a character in the future.</span></span> <span data-ttu-id="f2947-182">"Znak" zde odkazuje na cokoli, co lze přiřadit k bodu kódu, který zahrnuje takové věci, jako jsou akce, které řídí, jak se zobrazuje text nebo znaky.</span><span class="sxs-lookup"><span data-stu-id="f2947-182">"Character" here refers to anything that can be assigned to a code point, which includes such things as actions that control how text or characters are displayed.</span></span>

<span data-ttu-id="f2947-183">Následující diagram znázorňuje body kódu skalární hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f2947-183">The following diagram illustrates the scalar value code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/scalar-values.svg" alt-text="Skalární hodnoty":::

### <a name="the-opno-locrune-type-as-a-scalar-value"></a><span data-ttu-id="f2947-185">Typ Rune jako skalární hodnota</span><span class="sxs-lookup"><span data-stu-id="f2947-185">The Rune type as a scalar value</span></span>

<span data-ttu-id="f2947-186">Počínaje rozhraním .NET Core <xref:System.Text.Rune?displayProperty=fullName> 3.0 představuje typ skalární hodnotu Unicode.</span><span class="sxs-lookup"><span data-stu-id="f2947-186">Beginning with .NET Core 3.0, the <xref:System.Text.Rune?displayProperty=fullName> type represents a Unicode scalar value.</span></span> <span data-ttu-id="f2947-187">**`Rune`není k dispozici v rozhraní .NET Core 2.x nebo .NET Framework 4.x.**</span><span class="sxs-lookup"><span data-stu-id="f2947-187">**`Rune` is not available in .NET Core 2.x or .NET Framework 4.x.**</span></span>

<span data-ttu-id="f2947-188">Konstruktory `Rune` ověřují, zda je výsledná instance platnou skalární hodnotou Unicode, jinak vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="f2947-188">The `Rune` constructors validate that the resulting instance is a valid Unicode scalar value, otherwise they throw an exception.</span></span> <span data-ttu-id="f2947-189">Následující příklad ukazuje kód, který úspěšně `Rune` instancije instance, protože vstup představuje platné skalární hodnoty:</span><span class="sxs-lookup"><span data-stu-id="f2947-189">The following example shows code that successfully instantiates `Rune` instances because the input represents valid scalar values:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::

<span data-ttu-id="f2947-190">Následující příklad vyvolá výjimku, protože bod kódu je v oblasti náhradní a není součástí náhradní dvojice:</span><span class="sxs-lookup"><span data-stu-id="f2947-190">The following example throws an exception because the code point is in the surrogate range and isn't part of a surrogate pair:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::

<span data-ttu-id="f2947-191">Následující příklad vyvolá výjimku, protože bod kódu je mimo doplňkový rozsah:</span><span class="sxs-lookup"><span data-stu-id="f2947-191">The following example throws an exception because the code point is beyond the supplementary range:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::

### <a name="opno-locrune-usage-example-changing-letter-case"></a>Rune<span data-ttu-id="f2947-192">příklad použití: změna písmene</span><span class="sxs-lookup"><span data-stu-id="f2947-192"> usage example: changing letter case</span></span>

<span data-ttu-id="f2947-193">Rozhraní API, `char` které přebírá a předpokládá, že pracuje s bodem kódu, který je `char` skalární hodnota nefunguje správně, pokud je z náhradní pár.</span><span class="sxs-lookup"><span data-stu-id="f2947-193">An API that takes a `char` and assumes it is working with a code point that is a scalar value doesn't work correctly if the `char` is from a surrogate pair.</span></span> <span data-ttu-id="f2947-194">Zvažte například následující metodu, char která stringvolá <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> každý v :</span><span class="sxs-lookup"><span data-stu-id="f2947-194">For example, consider the following method that calls <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> on each char in a string:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::

<span data-ttu-id="f2947-195">`input` string Pokud obsahuje malé písmeno Deseret `er` (`𐑉`), tento kód jej`𐐡`nepřevede na velká písmena ( ).</span><span class="sxs-lookup"><span data-stu-id="f2947-195">If the `input` string contains the lowercase Deseret letter `er` (`𐑉`), this code won't convert it to uppercase (`𐐡`).</span></span> <span data-ttu-id="f2947-196">Kód volá `char.ToUpperInvariant` samostatně na každém `U+D801` bodě `U+DC49`náhradního kódu a .</span><span class="sxs-lookup"><span data-stu-id="f2947-196">The code calls `char.ToUpperInvariant` separately on each surrogate code point, `U+D801` and `U+DC49`.</span></span> <span data-ttu-id="f2947-197">Ale `U+D801` nemá dostatek informací sám o sobě identifikovat jako malé `char.ToUpperInvariant` písmeno, tak to nechává na pokoji.</span><span class="sxs-lookup"><span data-stu-id="f2947-197">But `U+D801` doesn't have enough information by itself to identify it as a lowercase letter, so `char.ToUpperInvariant` leaves it alone.</span></span> <span data-ttu-id="f2947-198">A zvládá `U+DC49` to stejně.</span><span class="sxs-lookup"><span data-stu-id="f2947-198">And it handles `U+DC49` the same way.</span></span> <span data-ttu-id="f2947-199">Výsledkem je, že malá písmena "", v písmenu `input` string a) se nepřevedou na velká písmena .'.</span><span class="sxs-lookup"><span data-stu-id="f2947-199">The result is that lowercase '𐑉' in the `input` string doesn't get converted to uppercase '𐐡'.</span></span>

<span data-ttu-id="f2947-200">Zde jsou dvě možnosti string pro správný převod na velká písmena:</span><span class="sxs-lookup"><span data-stu-id="f2947-200">Here are two options for correctly converting a string to uppercase:</span></span>

* <span data-ttu-id="f2947-201">Volání <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> na string vstup spíše než `char`iterace -by-`char`.</span><span class="sxs-lookup"><span data-stu-id="f2947-201">Call <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> on the input string rather than iterating `char`-by-`char`.</span></span> <span data-ttu-id="f2947-202">Metoda `string.ToUpperInvariant` má přístup k oběma částem každé náhradní dvojice, takže může správně zpracovat všechny body kódu Unicode.</span><span class="sxs-lookup"><span data-stu-id="f2947-202">The `string.ToUpperInvariant` method has access to both parts of each surrogate pair, so it can handle all Unicode code points correctly.</span></span>
* <span data-ttu-id="f2947-203">Iterate prostřednictvím skalární hodnoty `Rune` Unicode `char` jako instance namísto instancí, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f2947-203">Iterate through the Unicode scalar values as `Rune` instances instead of `char` instances, as shown in the following example.</span></span> <span data-ttu-id="f2947-204">Vzhledem `Rune` k tomu, že instance je platnou skalární hodnotou Unicode, může být předána do prostředí API, která očekávají, že budou pracovat s skalární hodnotou.</span><span class="sxs-lookup"><span data-stu-id="f2947-204">Since a `Rune` instance is a valid Unicode scalar value, it can be passed to APIs that expect to operate on a scalar value.</span></span> <span data-ttu-id="f2947-205">Například volání, <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> jak je znázorněno v následujícím příkladu, poskytuje správné výsledky:</span><span class="sxs-lookup"><span data-stu-id="f2947-205">For example, calling <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> as shown in the following example gives correct results:</span></span>

  :::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::

### <a name="other-opno-locrune-apis"></a><span data-ttu-id="f2947-206">Další Rune api</span><span class="sxs-lookup"><span data-stu-id="f2947-206">Other Rune APIs</span></span>

<span data-ttu-id="f2947-207">Typ `Rune` zveřejňuje analogy mnoha `char` api.</span><span class="sxs-lookup"><span data-stu-id="f2947-207">The `Rune` type exposes analogs of many of the `char` APIs.</span></span> <span data-ttu-id="f2947-208">Například následující metody zrcadlí statická `char` api na typu:</span><span class="sxs-lookup"><span data-stu-id="f2947-208">For example, the following methods mirror static APIs on the `char` type:</span></span>

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

<span data-ttu-id="f2947-209">Chcete-li získat nezpracovaná skalární hodnota z `Rune` instance, použijte <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f2947-209">To get the raw scalar value from a `Rune` instance, use the <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="f2947-210">Chcete-li `Rune` převést instanci zpět <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> na <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> posloupnost `char`s, použijte nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="f2947-210">To convert a `Rune` instance back to a sequence of `char`s, use <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> or the <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="f2947-211">Vzhledem k tomu, že jakákoli skalární hodnota Unicode je rezivovatelná jedním `char` nebo náhradním párem, může být jakákoli `Rune` instance reprezentována maximálně 2 `char` instancemi.</span><span class="sxs-lookup"><span data-stu-id="f2947-211">Since any Unicode scalar value is representable by a single `char` or by a surrogate pair, any `Rune` instance can be represented by at most 2 `char` instances.</span></span> <span data-ttu-id="f2947-212">Slouží <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> k zobrazení, kolik `char` instancí `Rune` je nutné reprezentovat instanci.</span><span class="sxs-lookup"><span data-stu-id="f2947-212">Use <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> to see how many `char` instances are required to represent a `Rune` instance.</span></span>

<span data-ttu-id="f2947-213">Další informace o typu `Rune` .NET naleznete v [ `Rune` odkazu rozhraní API](xref:System.Text.Rune).</span><span class="sxs-lookup"><span data-stu-id="f2947-213">For more information about the .NET `Rune` type, see the [`Rune` API reference](xref:System.Text.Rune).</span></span>

## <a name="grapheme-clusters"></a><span data-ttu-id="f2947-214">Grafemové klastry</span><span class="sxs-lookup"><span data-stu-id="f2947-214">Grapheme clusters</span></span>

<span data-ttu-id="f2947-215">Co vypadá jako jeden znak může vyplývat z kombinace více bodů kódu, takže více popisný termín, který se často používá místo "znak" je [grafeme clusteru](https://www.unicode.org/glossary/#grapheme_cluster).</span><span class="sxs-lookup"><span data-stu-id="f2947-215">What looks like one character might result from a combination of multiple code points, so a more descriptive term that is often used in place of "character" is [grapheme cluster](https://www.unicode.org/glossary/#grapheme_cluster).</span></span> <span data-ttu-id="f2947-216">Ekvivalentní termín v rozhraní .NET je [textový prvek](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span><span class="sxs-lookup"><span data-stu-id="f2947-216">The equivalent term in .NET is [text element](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span></span>

<span data-ttu-id="f2947-217">Zvažte `string` instance "a", "á".</span><span class="sxs-lookup"><span data-stu-id="f2947-217">Consider the `string` instances "a", "á".</span></span> <span data-ttu-id="f2947-218">"á" a`👩🏽‍🚒`" ".</span><span class="sxs-lookup"><span data-stu-id="f2947-218">"á", and "`👩🏽‍🚒`".</span></span> <span data-ttu-id="f2947-219">Pokud je operační systém zpracovává podle specifikace standardu Unicode, každá z těchto `string` instancí se zobrazí jako jeden textový prvek nebo cluster grafeme.</span><span class="sxs-lookup"><span data-stu-id="f2947-219">If your operating system handles them as specified by the Unicode standard, each of these `string` instances appears as a single text element or grapheme cluster.</span></span> <span data-ttu-id="f2947-220">Ale poslední dva jsou reprezentovány více než jeden skalární bod kódu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f2947-220">But the last two are represented by more than one scalar value code point.</span></span>

* <span data-ttu-id="f2947-221">string "A" je reprezentováno jednou skalární `char` hodnotou a obsahuje jednu instanci.</span><span class="sxs-lookup"><span data-stu-id="f2947-221">The string "a" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+0061 LATIN SMALL LETTER A`

* <span data-ttu-id="f2947-222">"Á" string je reprezentováno jednou skalární `char` hodnotou a obsahuje jednu instanci.</span><span class="sxs-lookup"><span data-stu-id="f2947-222">The string "á" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+00E1 LATIN SMALL LETTER E WITH ACUTE`

* <span data-ttu-id="f2947-223">"Á" string vypadá stejně jako "á", ale je reprezentovándvěma skalárními hodnotami a obsahuje dvě `char` instance.</span><span class="sxs-lookup"><span data-stu-id="f2947-223">The string "á" looks the same as "á" but is represented by two scalar values and contains two `char` instances.</span></span>

  * `U+0065 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* <span data-ttu-id="f2947-224">Nakonec string "`👩🏽‍🚒`" je reprezentován čtyřmi skalárními hodnotami a obsahuje sedm `char` instancí.</span><span class="sxs-lookup"><span data-stu-id="f2947-224">Finally, the string "`👩🏽‍🚒`" is represented by four scalar values and contains seven `char` instances.</span></span>

  * <span data-ttu-id="f2947-225">`U+1F469 WOMAN`(doplňkový rozsah, vyžaduje náhradní pár)</span><span class="sxs-lookup"><span data-stu-id="f2947-225">`U+1F469 WOMAN` (supplementary range, requires a surrogate pair)</span></span>
  * <span data-ttu-id="f2947-226">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4`(doplňkový rozsah, vyžaduje náhradní pár)</span><span class="sxs-lookup"><span data-stu-id="f2947-226">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (supplementary range, requires a surrogate pair)</span></span>
  * `U+200D ZERO WIDTH JOINER`
  * <span data-ttu-id="f2947-227">`U+1F692 FIRE ENGINE`(doplňkový rozsah, vyžaduje náhradní pár)</span><span class="sxs-lookup"><span data-stu-id="f2947-227">`U+1F692 FIRE ENGINE` (supplementary range, requires a surrogate pair)</span></span>

<span data-ttu-id="f2947-228">V některých předchozích příkladech – například modifikátoru diakritiky nebo modifikátoru tónu pleti – se bod kódu nezobrazuje jako samostatný prvek na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="f2947-228">In some of the preceding examples - such as the combining accent modifier or the skin tone modifier - the code point does not display as a standalone element on the screen.</span></span> <span data-ttu-id="f2947-229">Spíše slouží k úpravě vzhledu textového prvku, který byl před ním.</span><span class="sxs-lookup"><span data-stu-id="f2947-229">Rather, it serves to modify the appearance of a text element that came before it.</span></span> <span data-ttu-id="f2947-230">Tyto příklady ukazují, že může trvat více skalární hodnoty, aby se to, co si myslíme, že jako jeden "znak" nebo "grafém clusteru."</span><span class="sxs-lookup"><span data-stu-id="f2947-230">These examples show that it might take multiple scalar values to make up what we think of as a single "character," or "grapheme cluster."</span></span>

<span data-ttu-id="f2947-231">Chcete-li vytvořit výčet clusterů grafeme `string` <xref:System.Globalization.StringInfo> , použijte třídu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f2947-231">To enumerate the grapheme clusters of a `string`, use the <xref:System.Globalization.StringInfo> class as shown in the following example.</span></span> <span data-ttu-id="f2947-232">Pokud jste obeznámeni s Swift, `StringInfo` typ .NET je koncepčně podobný [ `character` typu Swift](https://developer.apple.com/documentation/swift/character).</span><span class="sxs-lookup"><span data-stu-id="f2947-232">If you're familiar with Swift, the .NET `StringInfo` type is conceptually similar to [Swift's `character` type](https://developer.apple.com/documentation/swift/character).</span></span>

### <a name="example-count-opno-locchar-opno-locrune-and-text-element-instances"></a><span data-ttu-id="f2947-233">Příklad: charinstance Runeelementů count , a text element</span><span class="sxs-lookup"><span data-stu-id="f2947-233">Example: count char, Rune, and text element instances</span></span>

<span data-ttu-id="f2947-234">V rozhraní API rozhraní .NET se cluster grafeme nazývá *textový prvek*.</span><span class="sxs-lookup"><span data-stu-id="f2947-234">In .NET APIs, a grapheme cluster is called a *text element*.</span></span> <span data-ttu-id="f2947-235">Následující metoda ukazuje rozdíly mezi `char` `Rune`instancemi prvků , a `string`textového prvku v :</span><span class="sxs-lookup"><span data-stu-id="f2947-235">The following method demonstrates the differences between `char`, `Rune`, and text element instances in a `string`:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::

<span data-ttu-id="f2947-236">Pokud spustíte tento kód v rozhraní .NET Framework nebo .NET Core 3.1 nebo starší, zobrazí `4`se počet textových prvků pro emoji .</span><span class="sxs-lookup"><span data-stu-id="f2947-236">If you run this code in .NET Framework or .NET Core 3.1 or earlier, the text element count for the emoji shows `4`.</span></span> <span data-ttu-id="f2947-237">To je způsobeno chybou `StringInfo` ve třídě, která je opravena v rozhraní .NET 5.</span><span class="sxs-lookup"><span data-stu-id="f2947-237">That is due to a bug in the `StringInfo` class that is fixed in .NET 5.</span></span>

### <a name="example-splitting-opno-locstring-instances"></a><span data-ttu-id="f2947-238">Příklad: string rozdělení instancí</span><span class="sxs-lookup"><span data-stu-id="f2947-238">Example: splitting string instances</span></span>

<span data-ttu-id="f2947-239">Při `string` rozdělení instance, vyhnout se rozdělení náhradní páry a grafeme clustery.</span><span class="sxs-lookup"><span data-stu-id="f2947-239">When splitting `string` instances, avoid splitting surrogate pairs and grapheme clusters.</span></span> <span data-ttu-id="f2947-240">Vezměme si následující příklad nesprávného kódu, který má stringv úmyslu vložit zalomení řádků každých 10 znaků v :</span><span class="sxs-lookup"><span data-stu-id="f2947-240">Consider the following example of incorrect code, which intends to insert line breaks every 10 characters in a string:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::

<span data-ttu-id="f2947-241">Vzhledem k tomu, `char` že tento kód vytvoří výčet instancí,`char` náhradní pár, který se stane rozkročit hranice 10 bude rozdělena a nový řádek vložen mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="f2947-241">Because this code enumerates `char` instances, a surrogate pair that happens to straddle a 10-`char` boundary will be split and a newline injected between them.</span></span> <span data-ttu-id="f2947-242">Toto vložení zavádí poškození dat, protože náhradní body kódu jsou smysluplné pouze jako páry.</span><span class="sxs-lookup"><span data-stu-id="f2947-242">This insertion introduces data corruption, because surrogate code points are meaningful only as pairs.</span></span>

<span data-ttu-id="f2947-243">Potenciál pro poškození dat není eliminován, `Rune` pokud výčet instancí `char` (skalární hodnoty) namísto instancí.</span><span class="sxs-lookup"><span data-stu-id="f2947-243">The potential for data corruption isn't eliminated if you enumerate `Rune` instances (scalar values) instead of `char` instances.</span></span> <span data-ttu-id="f2947-244">Sada `Rune` instancí může vytvořit cluster grafeme, který se`char` rozkládá na hranici 10.</span><span class="sxs-lookup"><span data-stu-id="f2947-244">A set of `Rune` instances might make up a grapheme cluster that straddles a 10-`char` boundary.</span></span> <span data-ttu-id="f2947-245">Pokud je sada clusteru grafeme rozdělena, nelze ji správně interpretovat.</span><span class="sxs-lookup"><span data-stu-id="f2947-245">If the grapheme cluster set is split up, it can't be interpreted correctly.</span></span>

<span data-ttu-id="f2947-246">Lepším přístupem je string přerušit počítání grafeme clusterů nebo textových prvků, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f2947-246">A better approach is to break the string by counting grapheme clusters, or text elements, as in the following example:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::

<span data-ttu-id="f2947-247">Jak již bylo uvedeno dříve, však v implementacích `StringInfo` .NET než .NET 5, třída může zpracovat některé clustery grafeme nesprávně.</span><span class="sxs-lookup"><span data-stu-id="f2947-247">As noted earlier, however, in implementations of .NET other than .NET 5, the `StringInfo` class might handle some grapheme clusters incorrectly.</span></span>

## <a name="utf-8-and-utf-32"></a><span data-ttu-id="f2947-248">UTF-8 a UTF-32</span><span class="sxs-lookup"><span data-stu-id="f2947-248">UTF-8 and UTF-32</span></span>

<span data-ttu-id="f2947-249">Předchozí části zaměřené na UTF-16, protože to je to, `string` co rozhraní .NET používá ke kódování instancí.</span><span class="sxs-lookup"><span data-stu-id="f2947-249">The preceding sections focused on UTF-16 because that's what .NET uses to encode `string` instances.</span></span> <span data-ttu-id="f2947-250">Existují i jiné kódovací systémy pro Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) a [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span><span class="sxs-lookup"><span data-stu-id="f2947-250">There are other encoding systems for Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) and [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span></span> <span data-ttu-id="f2947-251">Tato kódování používají jednotky 8bitového kódu a jednotky 32bitového kódu.</span><span class="sxs-lookup"><span data-stu-id="f2947-251">These encodings use 8-bit code units and 32-bit code units, respectively.</span></span>

<span data-ttu-id="f2947-252">Stejně jako UTF-16, UTF-8 vyžaduje více jednotek kódu představují některé skalární hodnoty Unicode.</span><span class="sxs-lookup"><span data-stu-id="f2947-252">Like UTF-16, UTF-8 requires multiple code units to represent some Unicode scalar values.</span></span> <span data-ttu-id="f2947-253">UTF-32 může představovat libovolnou skalární hodnotu v jedné jednotce 32bitového kódu.</span><span class="sxs-lookup"><span data-stu-id="f2947-253">UTF-32 can represent any scalar value in a single 32-bit code unit.</span></span>

<span data-ttu-id="f2947-254">Zde jsou některé příklady, které ukazují, jak je v každém z těchto tří kódovacích systémů Unicode reprezentován stejný bod kódu Unicode:</span><span class="sxs-lookup"><span data-stu-id="f2947-254">Here are some examples showing how the same Unicode code point is represented in each of these three Unicode encoding systems:</span></span>

```
Scalar: U+0061 LATIN SMALL LETTER A ('a')
UTF-8 : [ 61 ]           (1x  8-bit code unit  = 8 bits total)
UTF-16: [ 0061 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000061 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+0429 CYRILLIC CAPITAL LETTER SHCHA ('Щ')
UTF-8 : [ D0 A9 ]        (2x  8-bit code units = 16 bits total)
UTF-16: [ 0429 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000429 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+A992 JAVANESE LETTER GA ('ꦒ')
UTF-8 : [ EA A6 92 ]     (3x  8-bit code units = 24 bits total)
UTF-16: [ A992 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 0000A992 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+104CC OSAGE CAPITAL LETTER TSHA ('𐓌')
UTF-8 : [ F0 90 93 8C ]  (4x  8-bit code units = 32 bits total)
UTF-16: [ D801 DCCC ]    (2x 16-bit code units = 32 bits total)
UTF-32: [ 000104CC ]     (1x 32-bit code unit  = 32 bits total)
```

<span data-ttu-id="f2947-255">Jak již bylo uvedeno dříve, jeden kód UTF-16 jednotky z [náhradní pár](#surrogate-pairs) je bezvýznamný sám o sobě.</span><span class="sxs-lookup"><span data-stu-id="f2947-255">As noted earlier, a single UTF-16 code unit from a [surrogate pair](#surrogate-pairs) is meaningless by itself.</span></span> <span data-ttu-id="f2947-256">Stejným způsobem jedna jednotka kódu UTF-8 je sama o sobě bezvýznamná, pokud je v posloupnosti dvou, tří nebo čtyř, která se používá k výpočtu skalární hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f2947-256">In the same way, a single UTF-8 code unit is meaningless by itself if it's in a sequence of two, three, or four used to calculate a scalar value.</span></span>

### <a name="endianness"></a><span data-ttu-id="f2947-257">Endianness</span><span class="sxs-lookup"><span data-stu-id="f2947-257">Endianness</span></span>

<span data-ttu-id="f2947-258">V rozhraní .NET string jsou kódové jednotky UTF-16 uloženy v souvislé paměti jako posloupnost`char` 16bitových celočísel (instancí).</span><span class="sxs-lookup"><span data-stu-id="f2947-258">In .NET, the UTF-16 code units of a string are stored in contiguous memory as a sequence of 16-bit integers (`char` instances).</span></span> <span data-ttu-id="f2947-259">Bity jednotlivých kódových jednotek jsou rozloženy podle [endianness](https://en.wikipedia.org/wiki/Endianness) aktuální architektury.</span><span class="sxs-lookup"><span data-stu-id="f2947-259">The bits of individual code units are laid out according to the [endianness](https://en.wikipedia.org/wiki/Endianness) of the current architecture.</span></span>

<span data-ttu-id="f2947-260">Na malé endian string architektury, skládající se z Bodů kódu `[ D801 DCCC ]` UTF-16 by být stanoveny v paměti jako bajty `[ 0x01, 0xD8, 0xCC, 0xDC ]`.</span><span class="sxs-lookup"><span data-stu-id="f2947-260">On a little-endian architecture, the string consisting of the UTF-16 code points `[ D801 DCCC ]` would be laid out in memory as the bytes `[ 0x01, 0xD8, 0xCC, 0xDC ]`.</span></span> <span data-ttu-id="f2947-261">Na big-endian architektury, string že stejné by být stanoveny `[ 0xD8, 0x01, 0xDC, 0xCC ]`v paměti jako bajty .</span><span class="sxs-lookup"><span data-stu-id="f2947-261">On a big-endian architecture that same string would be laid out in memory as the bytes `[ 0xD8, 0x01, 0xDC, 0xCC ]`.</span></span>

<span data-ttu-id="f2947-262">Počítačové systémy, které vzájemně komunikují, se musí dohodnout na reprezentaci dat překračujících drát.</span><span class="sxs-lookup"><span data-stu-id="f2947-262">Computer systems that communicate with each other must agree on the representation of data crossing the wire.</span></span> <span data-ttu-id="f2947-263">Většina síťových protokolů používá UTF-8 jako standard při přenosu textu, částečně proto, aby se zabránilo problémům, které by mohly vyplývat z počítače big-endian, který komunikuje s počítačem s malým endianem.</span><span class="sxs-lookup"><span data-stu-id="f2947-263">Most network protocols use UTF-8 as a standard when transmitting text, partly to avoid issues that might result from a big-endian machine communicating with a little-endian machine.</span></span> <span data-ttu-id="f2947-264">Skládání string z bodů `[ F0 90 93 8C ]` kódu UTF-8 bude vždy reprezentováno jako bajty `[ 0xF0, 0x90, 0x93, 0x8C ]` bez ohledu na endianness.</span><span class="sxs-lookup"><span data-stu-id="f2947-264">The string consisting of the UTF-8 code points `[ F0 90 93 8C ]` will always be represented as the bytes `[ 0xF0, 0x90, 0x93, 0x8C ]` regardless of endianness.</span></span>

<span data-ttu-id="f2947-265">Chcete-li použít UTF-8 pro přenos textu, aplikace .NET často používají kód jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f2947-265">To use UTF-8 for transmitting text, .NET applications often use code like the following example:</span></span>

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

<span data-ttu-id="f2947-266">V předchozím příkladu metoda [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) dekóduje UTF-16 `string` zpět do řady skalárních hodnot Unicode, pak znovu zakóduje tyto skalární hodnoty `byte` do UTF-8 a umístí výslednou sekvenci do pole.</span><span class="sxs-lookup"><span data-stu-id="f2947-266">In the preceding example, the method [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) decodes the UTF-16 `string` back into a series of Unicode scalar values, then it re-encodes those scalar values into UTF-8 and places the resulting sequence into a `byte` array.</span></span> <span data-ttu-id="f2947-267">Metoda [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) provádí opačnou transformaci, převod `byte` utf-8 pole `string`UTF-16 .</span><span class="sxs-lookup"><span data-stu-id="f2947-267">The method [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) performs the opposite transformation, converting a UTF-8 `byte` array to a UTF-16 `string`.</span></span>

> [!WARNING]
> <span data-ttu-id="f2947-268">Vzhledem k tomu, UTF-8 je samozřejmostí na internetu, to může být lákavé číst syrové byty z drátu a zacházet s daty, jako by to bylo UTF-8.</span><span class="sxs-lookup"><span data-stu-id="f2947-268">Since UTF-8 is commonplace on the internet, it may be tempting to read raw bytes from the wire and to treat the data as if it were UTF-8.</span></span> <span data-ttu-id="f2947-269">Měli byste však ověřit, že je skutečně dobře tvarovaný.</span><span class="sxs-lookup"><span data-stu-id="f2947-269">However, you should validate that it is indeed well-formed.</span></span> <span data-ttu-id="f2947-270">Škodlivý klient může odeslat špatně vytvořené UTF-8 do vaší služby.</span><span class="sxs-lookup"><span data-stu-id="f2947-270">A malicious client might submit ill-formed UTF-8 to your service.</span></span> <span data-ttu-id="f2947-271">Pokud pracujete s tato data, jako kdyby byly ve správném formátu, může způsobit chyby nebo bezpečnostní díry ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f2947-271">If you operate on that data as if it were well-formed, it could cause errors or security holes in your application.</span></span> <span data-ttu-id="f2947-272">Chcete-li ověřit data UTF-8, `Encoding.UTF8.GetString`můžete použít metodu, jako je , `string`která provede ověření při převodu příchozích dat na .</span><span class="sxs-lookup"><span data-stu-id="f2947-272">To validate UTF-8 data, you can use a method like `Encoding.UTF8.GetString`, which will perform validation while converting the incoming data to a `string`.</span></span>

### <a name="well-formed-encoding"></a><span data-ttu-id="f2947-273">Dobře formátované kódování</span><span class="sxs-lookup"><span data-stu-id="f2947-273">Well-formed encoding</span></span>

<span data-ttu-id="f2947-274">Dobře formátované kódování Unicode string je kódové jednotky, které lze jednoznačně a bez chybdekódovat do posloupnosti skalárních hodnot Unicode.</span><span class="sxs-lookup"><span data-stu-id="f2947-274">A well-formed Unicode encoding is a string of code units that can be decoded unambiguously and without error into a sequence of Unicode scalar values.</span></span> <span data-ttu-id="f2947-275">Dobře formátovaná data mohou být volně překódována mezi UTF-8, UTF-16 a UTF-32.</span><span class="sxs-lookup"><span data-stu-id="f2947-275">Well-formed data can be transcoded freely back and forth between UTF-8, UTF-16, and UTF-32.</span></span>

<span data-ttu-id="f2947-276">Otázka, zda je sekvence kódování ve správném formátu nebo ne, nesouvisí s endianness architektury počítače.</span><span class="sxs-lookup"><span data-stu-id="f2947-276">The question of whether an encoding sequence is well-formed or not is unrelated to the endianness of a machine's architecture.</span></span> <span data-ttu-id="f2947-277">Špatně tvarovaná sekvence UTF-8 je špatně vytvořená stejným způsobem na strojích big-endian i little-endian.</span><span class="sxs-lookup"><span data-stu-id="f2947-277">An ill-formed UTF-8 sequence is ill-formed in the same way on both big-endian and little-endian machines.</span></span>

<span data-ttu-id="f2947-278">Zde je několik příkladů špatně vytvořených kódování:</span><span class="sxs-lookup"><span data-stu-id="f2947-278">Here are some examples of ill-formed encodings:</span></span>

* <span data-ttu-id="f2947-279">V UTF-8 sekvence `[ 6C C2 61 ]` je špatně `C2` vytvořena, `61`protože nemůže být následován .</span><span class="sxs-lookup"><span data-stu-id="f2947-279">In UTF-8, the sequence `[ 6C C2 61 ]` is ill-formed because `C2` cannot be followed by `61`.</span></span>

* <span data-ttu-id="f2947-280">V UTF-16 sekvence `[ DC00 DD00 ]` (nebo string `"\udc00\udd00"`v C#, ) je špatně `DC00` vytvořena, protože nízké `DD00`náhradní nemůže následovat další nízké náhradní .</span><span class="sxs-lookup"><span data-stu-id="f2947-280">In UTF-16, the sequence `[ DC00 DD00 ]` (or, in C#, the string `"\udc00\udd00"`) is ill-formed because the low surrogate `DC00` cannot be followed by another low surrogate `DD00`.</span></span>

* <span data-ttu-id="f2947-281">V UTF-32 sekvence `[ 0011ABCD ]` je špatně `0011ABCD` vytvořena, protože je mimo rozsah skalární hodnoty Unicode.</span><span class="sxs-lookup"><span data-stu-id="f2947-281">In UTF-32, the sequence `[ 0011ABCD ]` is ill-formed because `0011ABCD` is outside the range of Unicode scalar values.</span></span>

<span data-ttu-id="f2947-282">V rozhraní `string` .NET instance téměř vždy obsahují dobře vytvořená data UTF-16, ale to není zaručeno.</span><span class="sxs-lookup"><span data-stu-id="f2947-282">In .NET, `string` instances almost always contain well-formed UTF-16 data, but that isn't guaranteed.</span></span> <span data-ttu-id="f2947-283">Následující příklady ukazují platný kód Jazyka C#, který v `string` instancích vytváří špatně vytvořená data UTF-16.</span><span class="sxs-lookup"><span data-stu-id="f2947-283">The following examples show valid C# code that creates ill-formed UTF-16 data in `string` instances.</span></span>

* <span data-ttu-id="f2947-284">Špatně tvarovaný doslov:</span><span class="sxs-lookup"><span data-stu-id="f2947-284">An ill-formed literal:</span></span>

  ```csharp
  const string s = "\ud800";
  ```

* <span data-ttu-id="f2947-285">Podřetězec, který rozdělí náhradní pár:</span><span class="sxs-lookup"><span data-stu-id="f2947-285">A substring that splits up a surrogate pair:</span></span>

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

<span data-ttu-id="f2947-286">Api jako [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) nikdy vrátit `string` špatně vytvořené instance.</span><span class="sxs-lookup"><span data-stu-id="f2947-286">APIs like [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) never return ill-formed `string` instances.</span></span> <span data-ttu-id="f2947-287">`Encoding.GetString`a `Encoding.GetBytes` metody detekují špatně vytvořené sekvence ve vstupu a provádějí substituci znaků při generování výstupu.</span><span class="sxs-lookup"><span data-stu-id="f2947-287">`Encoding.GetString` and `Encoding.GetBytes` methods detect ill-formed sequences in the input and perform character substitution when generating the output.</span></span> <span data-ttu-id="f2947-288">Například pokud [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) vidí non-ASCII bajt ve vstupu (mimo rozsah U + 0000..U + 007F), vloží `string` '?' do vrácené instance.</span><span class="sxs-lookup"><span data-stu-id="f2947-288">For example, if [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) sees a non-ASCII byte in the input (outside the range U+0000..U+007F), it inserts a '?' into the returned `string` instance.</span></span> <span data-ttu-id="f2947-289">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A)nahradí špatně vytvořené sekvence UTF-8 ve `string` vrácené `U+FFFD REPLACEMENT CHARACTER ('�')` instanci.</span><span class="sxs-lookup"><span data-stu-id="f2947-289">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) replaces ill-formed UTF-8 sequences with `U+FFFD REPLACEMENT CHARACTER ('�')` in the returned `string` instance.</span></span> <span data-ttu-id="f2947-290">Další informace naleznete [v části Unicode Standard](https://www.unicode.org/versions/latest/), oddíly 5.22 a 3.9.</span><span class="sxs-lookup"><span data-stu-id="f2947-290">For more information, see [the Unicode Standard](https://www.unicode.org/versions/latest/), Sections 5.22 and 3.9.</span></span>

<span data-ttu-id="f2947-291">Předdefinované `Encoding` třídy lze také nakonfigurovat tak, aby vyvolávají výjimku, spíše než provádět nahrazení znaků, když jsou vidět špatně vytvořené sekvence.</span><span class="sxs-lookup"><span data-stu-id="f2947-291">The built-in `Encoding` classes can also be configured to throw an exception rather than perform character substitution when ill-formed sequences are seen.</span></span> <span data-ttu-id="f2947-292">Tento přístup se často používá v aplikacích citlivých na zabezpečení, kde nahrazení znaků nemusí být přijatelné.</span><span class="sxs-lookup"><span data-stu-id="f2947-292">This approach is often used in security-sensitive applications where character substitution might not be acceptable.</span></span>

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

<span data-ttu-id="f2947-293">Informace o použití předdefinovaných `Encoding` tříd naleznete v tématu [Použití tříd kódování znaků v rozhraní .NET](character-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="f2947-293">For information about how to use the built-in `Encoding` classes, see [How to use character encoding classes in .NET](character-encoding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f2947-294">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2947-294">See also</span></span>

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [<span data-ttu-id="f2947-295">Globalizace a lokalizace</span><span class="sxs-lookup"><span data-stu-id="f2947-295">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)
