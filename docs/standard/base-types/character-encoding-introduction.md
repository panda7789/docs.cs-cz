---
title: Úvod do char kódování Acter v .NET
description: Přečtěte si o char kódování a dekódování Acter v .NET.
ms.date: 03/09/2020
no-loc:
- Rune
- char
- string
dev_langs:
- csharp
helpviewer_keywords:
- encoding, understanding
ms.openlocfilehash: d1f9878c7e7c07944a943c0b05e557ceaa5d1b2f
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812117"
---
# <a name="character-encoding-in-net"></a><span data-ttu-id="080f8-103">Kódování znaků v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="080f8-103">Character encoding in .NET</span></span>

<span data-ttu-id="080f8-104">Tento článek poskytuje Úvod k char systémům kódování Acter, které používá .NET.</span><span class="sxs-lookup"><span data-stu-id="080f8-104">This article provides an introduction to character encoding systems that are used by .NET.</span></span> <span data-ttu-id="080f8-105">Článek vysvětluje, jak <xref:System.String> typy, <xref:System.Char> , <xref:System.Text.Rune> a <xref:System.Globalization.StringInfo> fungují s kódováním Unicode, UTF-16 a UTF-8.</span><span class="sxs-lookup"><span data-stu-id="080f8-105">The article explains how the <xref:System.String>, <xref:System.Char>, <xref:System.Text.Rune>, and <xref:System.Globalization.StringInfo> types work with Unicode, UTF-16, and UTF-8.</span></span>

<span data-ttu-id="080f8-106">Pojem \* char Acter\* se zde používá v obecném smyslu, *co čtenář detekuje jako jeden prvek zobrazení*.</span><span class="sxs-lookup"><span data-stu-id="080f8-106">The term *character* is used here in the general sense of *what a reader perceives as a single display element*.</span></span> <span data-ttu-id="080f8-107">Běžnými příklady jsou písmena "a", symbol "@" a Emoji " 🐂 ".</span><span class="sxs-lookup"><span data-stu-id="080f8-107">Common examples are the letter "a", the symbol "@", and the emoji "🐂".</span></span> <span data-ttu-id="080f8-108">V některých případech se zdá char , že jeden Acter se ve skutečnosti skládá z několika nezávislých prvků zobrazení, protože se vysvětluje oddíl [grapheme clusterů](#grapheme-clusters) .</span><span class="sxs-lookup"><span data-stu-id="080f8-108">Sometimes what looks like one character is actually composed of multiple independent display elements, as the section on [grapheme clusters](#grapheme-clusters) explains.</span></span>

## <a name="the-no-locstring-and-no-locchar-types"></a><span data-ttu-id="080f8-109">stringTypy a char</span><span class="sxs-lookup"><span data-stu-id="080f8-109">The string and char types</span></span>

<span data-ttu-id="080f8-110">Instance [string](xref:System.String) třídy představuje nějaký text.</span><span class="sxs-lookup"><span data-stu-id="080f8-110">An instance of the [string](xref:System.String) class represents some text.</span></span> <span data-ttu-id="080f8-111">`string`Je logicky sekvencí 16bitových hodnot, z nichž každá je instancí [char](xref:System.Char) struktury.</span><span class="sxs-lookup"><span data-stu-id="080f8-111">A `string` is logically a sequence of 16-bit values, each of which is an instance of the [char](xref:System.Char) struct.</span></span> <span data-ttu-id="080f8-112">Rozhraní [ string . Vlastnost length](xref:System.String.Length) vrátí počet `char` instancí `string` instance.</span><span class="sxs-lookup"><span data-stu-id="080f8-112">The [string.Length](xref:System.String.Length) property returns the number of `char` instances in the `string` instance.</span></span>

<span data-ttu-id="080f8-113">Následující ukázková funkce vytiskne hodnoty v šestnáctkovém zápisu všech `char` instancí v `string` :</span><span class="sxs-lookup"><span data-stu-id="080f8-113">The following sample function prints out the values in hexadecimal notation of all the `char` instances in a `string`:</span></span>

<span data-ttu-id="080f8-114">::: Code Language = "CSharp" Source = "fragmenty/ char Acter-Encoding-Úvod/CSharp/PrintStringChars. cs" ID = "SnippetPrintChars":::</span><span class="sxs-lookup"><span data-stu-id="080f8-114">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::</span></span>

<span data-ttu-id="080f8-115">Předat string "Hello" této funkci a získáte následující výstup:</span><span class="sxs-lookup"><span data-stu-id="080f8-115">Pass the string "Hello" to this function, and you get the following output:</span></span>

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

<span data-ttu-id="080f8-116">Jednotlivé char actery jsou reprezentovány jedinou `char` hodnotou.</span><span class="sxs-lookup"><span data-stu-id="080f8-116">Each character is represented by a single `char` value.</span></span> <span data-ttu-id="080f8-117">Tento model má pro většinu jazyků světa hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="080f8-117">That pattern holds true for most of the world's languages.</span></span> <span data-ttu-id="080f8-118">Zde je například výstup pro dva čínské char actersy, jako je *nǐ hǎo* a střední hodnota *Hello*:</span><span class="sxs-lookup"><span data-stu-id="080f8-118">For example, here's the output for two Chinese characters that sound like *nǐ hǎo* and mean *Hello*:</span></span>

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

<span data-ttu-id="080f8-119">U některých jazyků a pro některé symboly a Emoji ale převezme dvě instance, `char` aby představovaly jeden char Acter.</span><span class="sxs-lookup"><span data-stu-id="080f8-119">However, for some languages and for some symbols and emoji, it takes two `char` instances to represent a single character.</span></span> <span data-ttu-id="080f8-120">Porovnejte například char acters a `char` instance ve slově, které znamenají *Osage* v Osage jazyce:</span><span class="sxs-lookup"><span data-stu-id="080f8-120">For example, compare the characters and `char` instances in the word that means *Osage* in the Osage language:</span></span>

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

<span data-ttu-id="080f8-121">V předchozím příkladu každý char Acter s výjimkou místa je reprezentován dvěma `char` instancemi.</span><span class="sxs-lookup"><span data-stu-id="080f8-121">In the preceding example, each character except the space is represented by two `char` instances.</span></span>

<span data-ttu-id="080f8-122">Jedna Emoji Unicode je také zastoupena dvěma `char` s, jak je vidět v následujícím příkladu, který ukazuje Ox Emoji:</span><span class="sxs-lookup"><span data-stu-id="080f8-122">A single Unicode emoji is also represented by two `char`s, as seen in the following example showing an ox emoji:</span></span>

```output
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

<span data-ttu-id="080f8-123">Tyto příklady ukazují, že hodnota `string.Length` , která označuje počet `char` instancí, nemusí nutně označovat počet zobrazených char acters.</span><span class="sxs-lookup"><span data-stu-id="080f8-123">These examples show that the value of `string.Length`, which indicates the number of `char` instances, doesn't necessarily indicate the number of displayed characters.</span></span> <span data-ttu-id="080f8-124">Jedna `char` instance sama o sobě nutně reprezentuje char Acter.</span><span class="sxs-lookup"><span data-stu-id="080f8-124">A single `char` instance by itself doesn't necessarily represent a character.</span></span>

<span data-ttu-id="080f8-125">`char`Páry, které jsou mapovány na jeden char Acter, se nazývají *náhradní páry*.</span><span class="sxs-lookup"><span data-stu-id="080f8-125">The `char` pairs that map to a single character are called *surrogate pairs*.</span></span> <span data-ttu-id="080f8-126">Pro pochopení, jak fungují, je nutné pochopit kódování Unicode a UTF-16.</span><span class="sxs-lookup"><span data-stu-id="080f8-126">To understand how they work, you need to understand Unicode and UTF-16 encoding.</span></span>

## <a name="unicode-code-points"></a><span data-ttu-id="080f8-127">Body kódu Unicode</span><span class="sxs-lookup"><span data-stu-id="080f8-127">Unicode code points</span></span>

<span data-ttu-id="080f8-128">Unicode je mezinárodní standard kódování pro použití na různých platformách a v různých jazycích a skriptech.</span><span class="sxs-lookup"><span data-stu-id="080f8-128">Unicode is an international encoding standard for use on various platforms and with various languages and scripts.</span></span>

<span data-ttu-id="080f8-129">Standard Unicode definuje více než 1 100 000 [kódových bodů](https://www.unicode.org/glossary/#code_point).</span><span class="sxs-lookup"><span data-stu-id="080f8-129">The Unicode Standard defines over 1.1 million [code points](https://www.unicode.org/glossary/#code_point).</span></span> <span data-ttu-id="080f8-130">Bod kódu je celočíselná hodnota, která může být v rozsahu od 0 do `U+10FFFF` (desítková 1 114 111).</span><span class="sxs-lookup"><span data-stu-id="080f8-130">A code point is an integer value that can range from 0 to `U+10FFFF` (decimal 1,114,111).</span></span> <span data-ttu-id="080f8-131">Některé body kódu jsou přiřazeny k písmenům, symbolům nebo emoji.</span><span class="sxs-lookup"><span data-stu-id="080f8-131">Some code points are assigned to letters, symbols, or emoji.</span></span> <span data-ttu-id="080f8-132">Jiné jsou přiřazeny k akcím, které řídí způsob char zobrazení textu nebo acters, jako je například přechod na nový řádek.</span><span class="sxs-lookup"><span data-stu-id="080f8-132">Others are assigned to actions that control how text or characters are displayed, such as advance to a new line.</span></span> <span data-ttu-id="080f8-133">Mnoho bodů kódu ještě není přiřazeno.</span><span class="sxs-lookup"><span data-stu-id="080f8-133">Many code points are not yet assigned.</span></span>

<span data-ttu-id="080f8-134">Tady jsou některé příklady přiřazení bodů kódu s odkazy na sadu Unicode char TS, ve kterých se zobrazují:</span><span class="sxs-lookup"><span data-stu-id="080f8-134">Here are some examples of code point assignments, with links to Unicode charts in which they appear:</span></span>

|<span data-ttu-id="080f8-135">Decimal</span><span class="sxs-lookup"><span data-stu-id="080f8-135">Decimal</span></span>|<span data-ttu-id="080f8-136">Soustavy</span><span class="sxs-lookup"><span data-stu-id="080f8-136">Hex</span></span>       |<span data-ttu-id="080f8-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="080f8-137">Example</span></span>|<span data-ttu-id="080f8-138">Popis</span><span class="sxs-lookup"><span data-stu-id="080f8-138">Description</span></span>|
|------:|----------|-------|-----------|
|<span data-ttu-id="080f8-139">10</span><span class="sxs-lookup"><span data-stu-id="080f8-139">10</span></span>     | `U+000A` |<span data-ttu-id="080f8-140">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="080f8-140">N/A</span></span>| <span data-ttu-id="080f8-141">[ČÁROVÝ KANÁL](https://www.unicode.org/charts/PDF/U0000.pdf)</span><span class="sxs-lookup"><span data-stu-id="080f8-141">[LINE FEED](https://www.unicode.org/charts/PDF/U0000.pdf)</span></span> |
|<span data-ttu-id="080f8-142">65</span><span class="sxs-lookup"><span data-stu-id="080f8-142">65</span></span>     | `U+0061` | <span data-ttu-id="080f8-143">pro</span><span class="sxs-lookup"><span data-stu-id="080f8-143">a</span></span> | <span data-ttu-id="080f8-144">[MALÉ PÍSMENO LATINKY A](https://www.unicode.org/charts/PDF/U0000.pdf)</span><span class="sxs-lookup"><span data-stu-id="080f8-144">[LATIN SMALL LETTER A](https://www.unicode.org/charts/PDF/U0000.pdf)</span></span> |
|<span data-ttu-id="080f8-145">562</span><span class="sxs-lookup"><span data-stu-id="080f8-145">562</span></span>    | `U+0232` | <span data-ttu-id="080f8-146">Ȳ</span><span class="sxs-lookup"><span data-stu-id="080f8-146">Ȳ</span></span> | <span data-ttu-id="080f8-147">[VELKÉ PÍSMENO LATINKY Y S POMLČKOU](https://www.unicode.org/charts/PDF/U0180.pdf)</span><span class="sxs-lookup"><span data-stu-id="080f8-147">[LATIN CAPITAL LETTER Y WITH MACRON](https://www.unicode.org/charts/PDF/U0180.pdf)</span></span> |
|<span data-ttu-id="080f8-148">68 675</span><span class="sxs-lookup"><span data-stu-id="080f8-148">68,675</span></span> | `U+10C43`| <span data-ttu-id="080f8-149">𐱃</span><span class="sxs-lookup"><span data-stu-id="080f8-149">𐱃</span></span> | <span data-ttu-id="080f8-150">[STARÉ ORKHONOVÉ DOPISY V](https://www.unicode.org/charts/PDF/U10C00.pdf)</span><span class="sxs-lookup"><span data-stu-id="080f8-150">[OLD TURKIC LETTER ORKHON AT](https://www.unicode.org/charts/PDF/U10C00.pdf)</span></span> |
|<span data-ttu-id="080f8-151">127 801</span><span class="sxs-lookup"><span data-stu-id="080f8-151">127,801</span></span>| `U+1F339`| <span data-ttu-id="080f8-152">🌹</span><span class="sxs-lookup"><span data-stu-id="080f8-152">🌹</span></span> | <span data-ttu-id="080f8-153">[RŮŽE – Emoji](https://www.unicode.org/charts/PDF/U1F300.pdf)</span><span class="sxs-lookup"><span data-stu-id="080f8-153">[ROSE emoji](https://www.unicode.org/charts/PDF/U1F300.pdf)</span></span> |

<span data-ttu-id="080f8-154">Body kódu jsou obvykle označovány pomocí syntaxe `U+xxxx` , kde `xxxx` je celočíselně zakódovaná celočíselná hodnota.</span><span class="sxs-lookup"><span data-stu-id="080f8-154">Code points are customarily referred to by using the syntax `U+xxxx`, where `xxxx` is the hex-encoded integer value.</span></span>

<span data-ttu-id="080f8-155">V celém rozsahu kódových bodů existují dva podrozsahy:</span><span class="sxs-lookup"><span data-stu-id="080f8-155">Within the full range of code points there are two subranges:</span></span>

* <span data-ttu-id="080f8-156">**Základní vícejazyčné roviny (BMP)** v rozsahu `U+0000..U+FFFF` .</span><span class="sxs-lookup"><span data-stu-id="080f8-156">The **Basic Multilingual Plane (BMP)** in the range `U+0000..U+FFFF`.</span></span> <span data-ttu-id="080f8-157">Tento 16bitový rozsah poskytuje 65 536 kódových bodů, které jsou dostatečně k pokrytí většiny systémů pro psaní světa.</span><span class="sxs-lookup"><span data-stu-id="080f8-157">This 16-bit range provides 65,536 code points, enough to cover the majority of the world's writing systems.</span></span>
* <span data-ttu-id="080f8-158">**Doplňkové body kódu** v rozsahu `U+10000..U+10FFFF` .</span><span class="sxs-lookup"><span data-stu-id="080f8-158">**Supplementary code points** in the range `U+10000..U+10FFFF`.</span></span> <span data-ttu-id="080f8-159">Tento 21. rozsah poskytuje více než milion dalších kódových bodů, které lze použít pro méně známé jazyky a jiné účely, jako je například emoji.</span><span class="sxs-lookup"><span data-stu-id="080f8-159">This 21-bit range provides more than a million additional code points that can be used for less well-known languages and other purposes such as emojis.</span></span>

<span data-ttu-id="080f8-160">Následující diagram znázorňuje vztah mezi BMP a doplňkovými body kódu.</span><span class="sxs-lookup"><span data-stu-id="080f8-160">The following diagram illustrates the relationship between the BMP and the supplementary code points.</span></span>

:::image type="content" source="media/:::No-Loc (Char)::: Acter-Encoding-Introduction/BMP-and-Supplementary. SVG "ALT-text =" BMP a doplňkový kódový bod ":::

## <a name="utf-16-code-units"></a><span data-ttu-id="080f8-162">Jednotky kódu UTF-16</span><span class="sxs-lookup"><span data-stu-id="080f8-162">UTF-16 code units</span></span>

<span data-ttu-id="080f8-163">16bitový formát transformace Unicode ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) je char systém kódování Acter, který používá 16bitové *jednotky kódu* pro reprezentaci bodů kódu Unicode.</span><span class="sxs-lookup"><span data-stu-id="080f8-163">16-bit Unicode Transformation Format ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) is a character encoding system that uses 16-bit *code units* to represent Unicode code points.</span></span> <span data-ttu-id="080f8-164">Rozhraní .NET používá UTF-16 ke kódování textu v `string` .</span><span class="sxs-lookup"><span data-stu-id="080f8-164">.NET uses UTF-16 to encode the text in a `string`.</span></span> <span data-ttu-id="080f8-165">`char`Instance představuje 16bitové jednotky kódu.</span><span class="sxs-lookup"><span data-stu-id="080f8-165">A `char` instance represents a 16-bit code unit.</span></span>

<span data-ttu-id="080f8-166">Jedna 16bitová jednotka kódu může představovat libovolný bod kódu v 16bitovém rozsahu základní vícejazyčné roviny.</span><span class="sxs-lookup"><span data-stu-id="080f8-166">A single 16-bit code unit can represent any code point in the 16-bit range of the Basic Multilingual Plane.</span></span> <span data-ttu-id="080f8-167">Ale pro bod kódu v doplňkovém rozsahu `char` jsou potřeba dvě instance.</span><span class="sxs-lookup"><span data-stu-id="080f8-167">But for a code point in the supplementary range, two `char` instances are needed.</span></span>

## <a name="surrogate-pairs"></a><span data-ttu-id="080f8-168">Náhradní páry</span><span class="sxs-lookup"><span data-stu-id="080f8-168">Surrogate pairs</span></span>

<span data-ttu-id="080f8-169">Překlad 2 16 hodnot na jednu hodnotu na 21 bitů usnadňuje speciální rozsah nazvaný *body náhrady*, od `U+D800` do `U+DFFF` (desítková 55 296 až 57 343) včetně.</span><span class="sxs-lookup"><span data-stu-id="080f8-169">The translation of two 16-bit values to a single 21-bit value is facilitated by a special range called the *surrogate code points*, from `U+D800` to `U+DFFF` (decimal 55,296 to 57,343), inclusive.</span></span>

<span data-ttu-id="080f8-170">Následující diagram znázorňuje vztah mezi BMP a náhradními body kódu.</span><span class="sxs-lookup"><span data-stu-id="080f8-170">The following diagram illustrates the relationship between the BMP and the surrogate code points.</span></span>

:::image type="content" source="media/:::No-Loc (Char)::: Acter-Encoding-Introduction/BMP-and-Surrogate. SVG "ALT-text =" BMP a náhradní body kódu ":::

<span data-ttu-id="080f8-172">Pokud je za klíčovým bodem *vysoké náhrady* `U+D800..U+DBFF` okamžitě následován bod *nízkého náhrady* ( `U+DC00..U+DFFF` ), je pár interpretován jako doplňkový bod kódu pomocí následujícího vzorce:</span><span class="sxs-lookup"><span data-stu-id="080f8-172">When a *high surrogate* code point (`U+D800..U+DBFF`) is immediately followed by a *low surrogate* code point (`U+DC00..U+DFFF`), the pair is interpreted as a supplementary code point by using the following formula:</span></span>

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

<span data-ttu-id="080f8-173">Toto je stejný vzorec pomocí desítkového zápisu:</span><span class="sxs-lookup"><span data-stu-id="080f8-173">Here's the same formula using decimal notation:</span></span>

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

<span data-ttu-id="080f8-174">*Vysoký* náhradní bod kódu nemá vyšší číselnou hodnotu než bod *nedostatku* náhradního kódu.</span><span class="sxs-lookup"><span data-stu-id="080f8-174">A *high* surrogate code point doesn't have a higher number value than a *low* surrogate code point.</span></span> <span data-ttu-id="080f8-175">Vysoký náhradní bod kódu se nazývá "vysoká", protože se používá k výpočtu vyššího řádu 11 bitů plného rozsahu 21-bitového bodu kódu.</span><span class="sxs-lookup"><span data-stu-id="080f8-175">The high surrogate code point is called "high" because it's used to calculate the higher-order 11 bits of the full 21-bit code point range.</span></span> <span data-ttu-id="080f8-176">Nízká náhrada za bod kódu se používá k výpočtu 10 bitů s nižším pořadím.</span><span class="sxs-lookup"><span data-stu-id="080f8-176">The low surrogate code point is used to calculate the lower-order 10 bits.</span></span>

<span data-ttu-id="080f8-177">Například skutečný bod kódu, který odpovídá náhradnímu páru `0xD83C` a `0xDF39`  je vypočítán následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="080f8-177">For example, the actual code point that corresponds to the surrogate pair `0xD83C` and `0xDF39`  is computed as follows:</span></span>

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

<span data-ttu-id="080f8-178">Toto je stejný výpočet pomocí desítkového zápisu:</span><span class="sxs-lookup"><span data-stu-id="080f8-178">Here's the same calculation using decimal notation:</span></span>

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

<span data-ttu-id="080f8-179">Předchozí příklad ukazuje, že `"\ud83c\udf39"` je kódování UTF-16 výše `U+1F339 ROSE ('🌹')` zmíněného bodu kódu.</span><span class="sxs-lookup"><span data-stu-id="080f8-179">The preceding example demonstrates that `"\ud83c\udf39"` is the UTF-16 encoding of the `U+1F339 ROSE ('🌹')` code point mentioned earlier.</span></span>

## <a name="unicode-scalar-values"></a><span data-ttu-id="080f8-180">Skalární hodnoty Unicode</span><span class="sxs-lookup"><span data-stu-id="080f8-180">Unicode scalar values</span></span>

<span data-ttu-id="080f8-181">Pojem [skalární hodnota Unicode](https://www.unicode.org/glossary/#unicode_scalar_value) odkazuje na všechny body kódu, než jsou body náhradního kódu.</span><span class="sxs-lookup"><span data-stu-id="080f8-181">The term [Unicode scalar value](https://www.unicode.org/glossary/#unicode_scalar_value) refers to all code points other than the surrogate code points.</span></span> <span data-ttu-id="080f8-182">Jinými slovy, skalární hodnota je jakýkoliv bod kódu, který je přiřazen char Acter nebo může být char v budoucnu přiřazena Acter.</span><span class="sxs-lookup"><span data-stu-id="080f8-182">In other words, a scalar value is any code point that is assigned a character or can be assigned a character in the future.</span></span> <span data-ttu-id="080f8-183">"Znak" tady odkazuje na cokoli, co může být přiřazeno k bodu kódu, který obsahuje takové věci jako akce, které řídí způsob char zobrazení textu nebo acters.</span><span class="sxs-lookup"><span data-stu-id="080f8-183">"Character" here refers to anything that can be assigned to a code point, which includes such things as actions that control how text or characters are displayed.</span></span>

<span data-ttu-id="080f8-184">Následující diagram znázorňuje body kódu skalární hodnoty.</span><span class="sxs-lookup"><span data-stu-id="080f8-184">The following diagram illustrates the scalar value code points.</span></span>

:::image type="content" source="media/:::No-Loc (Char)::: Acter-Encoding-Introduction/Scalar-Values. SVG "ALT-text =" skalární hodnoty ":::

### <a name="the-no-locrune-type-as-a-scalar-value"></a><span data-ttu-id="080f8-186">RuneTyp jako skalární hodnota</span><span class="sxs-lookup"><span data-stu-id="080f8-186">The Rune type as a scalar value</span></span>

<span data-ttu-id="080f8-187">Počínaje rozhraním .NET Core 3,0 <xref:System.Text.Rune?displayProperty=fullName> Typ představuje skalární hodnotu Unicode.</span><span class="sxs-lookup"><span data-stu-id="080f8-187">Beginning with .NET Core 3.0, the <xref:System.Text.Rune?displayProperty=fullName> type represents a Unicode scalar value.</span></span> <span data-ttu-id="080f8-188">**`Rune` není k dispozici v rozhraní .NET Core 2. x nebo .NET Framework 4. x.**</span><span class="sxs-lookup"><span data-stu-id="080f8-188">**`Rune` is not available in .NET Core 2.x or .NET Framework 4.x.**</span></span>

<span data-ttu-id="080f8-189">`Rune`Konstruktory ověřují, zda je výsledná instance platnou skalární hodnotou kódování Unicode, jinak vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="080f8-189">The `Rune` constructors validate that the resulting instance is a valid Unicode scalar value, otherwise they throw an exception.</span></span> <span data-ttu-id="080f8-190">Následující příklad ukazuje kód, který úspěšně vytvoří instanci `Rune` instance, protože vstup představuje platné skalární hodnoty:</span><span class="sxs-lookup"><span data-stu-id="080f8-190">The following example shows code that successfully instantiates `Rune` instances because the input represents valid scalar values:</span></span>

<span data-ttu-id="080f8-191">::: Code Language = "CSharp" Source = "fragmenty/ char Acter-Encoding-Úvod/CSharp/instance Rune s.cs" ID = "SnippetValid":::</span><span class="sxs-lookup"><span data-stu-id="080f8-191">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::</span></span>

<span data-ttu-id="080f8-192">Následující příklad vyvolá výjimku, protože bod kódu je v rozsahu nahrazení a není součástí náhradního páru:</span><span class="sxs-lookup"><span data-stu-id="080f8-192">The following example throws an exception because the code point is in the surrogate range and isn't part of a surrogate pair:</span></span>

<span data-ttu-id="080f8-193">::: Code Language = "CSharp" Source = "fragmenty/ char Acter-Encoding-Úvod/CSharp/instance Rune s.cs" ID = "SnippetInvalidSurrogate":::</span><span class="sxs-lookup"><span data-stu-id="080f8-193">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::</span></span>

<span data-ttu-id="080f8-194">Následující příklad vyvolá výjimku, protože bod kódu je mimo doplňkový rozsah:</span><span class="sxs-lookup"><span data-stu-id="080f8-194">The following example throws an exception because the code point is beyond the supplementary range:</span></span>

<span data-ttu-id="080f8-195">::: Code Language = "CSharp" Source = "fragmenty/ char Acter-Encoding-Úvod/CSharp/instance Rune s.cs" ID = "SnippetInvalidHigh":::</span><span class="sxs-lookup"><span data-stu-id="080f8-195">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::</span></span>

### <a name="no-locrune-usage-example-changing-letter-case"></a><span data-ttu-id="080f8-196">Rune Příklad použití: Změna malých písmen</span><span class="sxs-lookup"><span data-stu-id="080f8-196">Rune usage example: changing letter case</span></span>

<span data-ttu-id="080f8-197">Rozhraní API, které přijímá `char` a předpokládá, že pracuje s bodem kódu, který je skalární hodnota, nefunguje správně, pokud `char` je z náhradního páru.</span><span class="sxs-lookup"><span data-stu-id="080f8-197">An API that takes a `char` and assumes it is working with a code point that is a scalar value doesn't work correctly if the `char` is from a surrogate pair.</span></span> <span data-ttu-id="080f8-198">Zvažte například následující metodu, která volá <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> každou char v string :</span><span class="sxs-lookup"><span data-stu-id="080f8-198">For example, consider the following method that calls <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> on each char in a string:</span></span>

<span data-ttu-id="080f8-199">::: Code Language = "CSharp" Source = "fragmenty/ char Acter-Encoding-Úvod/CSharp/ConvertToUpper. cs" ID = "SnippetBadExample":::</span><span class="sxs-lookup"><span data-stu-id="080f8-199">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::</span></span>

<span data-ttu-id="080f8-200">Pokud `input` string obsahuje písmeno Deseret s malým písmenem `er` ( `𐑉` ), tento kód ho nepřevede na velká písmena ( `𐐡` ).</span><span class="sxs-lookup"><span data-stu-id="080f8-200">If the `input` string contains the lowercase Deseret letter `er` (`𐑉`), this code won't convert it to uppercase (`𐐡`).</span></span> <span data-ttu-id="080f8-201">Kód volá `char.ToUpperInvariant` samostatně na každý náhradní bod kódu `U+D801` a `U+DC49` .</span><span class="sxs-lookup"><span data-stu-id="080f8-201">The code calls `char.ToUpperInvariant` separately on each surrogate code point, `U+D801` and `U+DC49`.</span></span> <span data-ttu-id="080f8-202">Nemá ale `U+D801` dostatek informací, aby ho identifikoval jako malé písmeno, takže `char.ToUpperInvariant` ho ponechá samostatně.</span><span class="sxs-lookup"><span data-stu-id="080f8-202">But `U+D801` doesn't have enough information by itself to identify it as a lowercase letter, so `char.ToUpperInvariant` leaves it alone.</span></span> <span data-ttu-id="080f8-203">A zpracovává `U+DC49` se stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="080f8-203">And it handles `U+DC49` the same way.</span></span> <span data-ttu-id="080f8-204">Výsledkem je, že malé písmeno ' 𐑉 ' v ' `input` string nebude převedeno na velká písmena ' 𐑉 '.</span><span class="sxs-lookup"><span data-stu-id="080f8-204">The result is that lowercase '𐑉' in the `input` string doesn't get converted to uppercase '𐐡'.</span></span>

<span data-ttu-id="080f8-205">Tady jsou dvě možnosti pro správné převádění string na velká písmena:</span><span class="sxs-lookup"><span data-stu-id="080f8-205">Here are two options for correctly converting a string to uppercase:</span></span>

* <span data-ttu-id="080f8-206">Zavolejte <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> na vstup string místo iterace `char` -by- `char` .</span><span class="sxs-lookup"><span data-stu-id="080f8-206">Call <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> on the input string rather than iterating `char`-by-`char`.</span></span> <span data-ttu-id="080f8-207">`string.ToUpperInvariant`Metoda má přístup k oběma částem každého náhradního páru, takže může správně zpracovat všechny body kódu Unicode.</span><span class="sxs-lookup"><span data-stu-id="080f8-207">The `string.ToUpperInvariant` method has access to both parts of each surrogate pair, so it can handle all Unicode code points correctly.</span></span>
* <span data-ttu-id="080f8-208">Iterujte pomocí skalárních hodnot Unicode jako `Rune` instancí namísto `char` instancí, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="080f8-208">Iterate through the Unicode scalar values as `Rune` instances instead of `char` instances, as shown in the following example.</span></span> <span data-ttu-id="080f8-209">Vzhledem k `Rune` tomu, že instance je platná skalární hodnota Unicode, může být předána rozhraním API, která očekávají, že budou pracovat na skalární hodnotě.</span><span class="sxs-lookup"><span data-stu-id="080f8-209">Since a `Rune` instance is a valid Unicode scalar value, it can be passed to APIs that expect to operate on a scalar value.</span></span> <span data-ttu-id="080f8-210">Například volání, <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> jak je znázorněno v následujícím příkladu, poskytuje správné výsledky:</span><span class="sxs-lookup"><span data-stu-id="080f8-210">For example, calling <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> as shown in the following example gives correct results:</span></span>

  <span data-ttu-id="080f8-211">::: Code Language = "CSharp" Source = "fragmenty/ char Acter-Encoding-Úvod/CSharp/ConvertToUpper. cs" ID = "SnippetGoodExample":::</span><span class="sxs-lookup"><span data-stu-id="080f8-211">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::</span></span>

### <a name="other-no-locrune-apis"></a><span data-ttu-id="080f8-212">Další Rune rozhraní API</span><span class="sxs-lookup"><span data-stu-id="080f8-212">Other Rune APIs</span></span>

<span data-ttu-id="080f8-213">`Rune`Typ zveřejňuje analogové typy mnoha `char` rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="080f8-213">The `Rune` type exposes analogs of many of the `char` APIs.</span></span> <span data-ttu-id="080f8-214">Například následující metody zrcadlí statická rozhraní API pro daný `char` Typ:</span><span class="sxs-lookup"><span data-stu-id="080f8-214">For example, the following methods mirror static APIs on the `char` type:</span></span>

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

<span data-ttu-id="080f8-215">Chcete-li získat nezpracovanou skalární hodnotu z `Rune` instance, použijte <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="080f8-215">To get the raw scalar value from a `Rune` instance, use the <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="080f8-216">Chcete-li převést `Rune` instanci zpět na sekvenci `char` s, použijte <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> metodu nebo <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="080f8-216">To convert a `Rune` instance back to a sequence of `char`s, use <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> or the <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="080f8-217">Vzhledem k tomu, že jakákoli skalární hodnota Unicode je reprezentována jedním `char` nebo náhradním párem, `Rune` může být libovolná instance reprezentovaná ve většině dvou `char` instancí.</span><span class="sxs-lookup"><span data-stu-id="080f8-217">Since any Unicode scalar value is representable by a single `char` or by a surrogate pair, any `Rune` instance can be represented by at most 2 `char` instances.</span></span> <span data-ttu-id="080f8-218">Použijte <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> k zobrazení, kolik `char` instancí je potřeba k reprezentaci `Rune` instance.</span><span class="sxs-lookup"><span data-stu-id="080f8-218">Use <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> to see how many `char` instances are required to represent a `Rune` instance.</span></span>

<span data-ttu-id="080f8-219">Další informace o typu .NET najdete v referenčních informacích k `Rune` [ `Rune` rozhraní API](xref:System.Text.Rune).</span><span class="sxs-lookup"><span data-stu-id="080f8-219">For more information about the .NET `Rune` type, see the [`Rune` API reference](xref:System.Text.Rune).</span></span>

## <a name="grapheme-clusters"></a><span data-ttu-id="080f8-220">Clustery Grapheme</span><span class="sxs-lookup"><span data-stu-id="080f8-220">Grapheme clusters</span></span>

<span data-ttu-id="080f8-221">Co vypadá jako jeden char Acter, může být výsledkem kombinace více bodů kódu, takže výstižnější pojem, který se často používá místo " char Acter" je [cluster grapheme](https://www.unicode.org/glossary/#grapheme_cluster).</span><span class="sxs-lookup"><span data-stu-id="080f8-221">What looks like one character might result from a combination of multiple code points, so a more descriptive term that is often used in place of "character" is [grapheme cluster](https://www.unicode.org/glossary/#grapheme_cluster).</span></span> <span data-ttu-id="080f8-222">Ekvivalentní termín v .NET je [textový prvek](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span><span class="sxs-lookup"><span data-stu-id="080f8-222">The equivalent term in .NET is [text element](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span></span>

<span data-ttu-id="080f8-223">Vezměte v úvahu `string` instance "a", "á", "á" a " `👩🏽‍🚒` ".</span><span class="sxs-lookup"><span data-stu-id="080f8-223">Consider the `string` instances "a", "á", "á", and "`👩🏽‍🚒`".</span></span> <span data-ttu-id="080f8-224">Pokud je operační systém zpracuje podle standardu Unicode, každá z těchto `string` instancí se zobrazí jako jeden textový prvek nebo grapheme cluster.</span><span class="sxs-lookup"><span data-stu-id="080f8-224">If your operating system handles them as specified by the Unicode standard, each of these `string` instances appears as a single text element or grapheme cluster.</span></span> <span data-ttu-id="080f8-225">Ale poslední dva jsou reprezentovány více než jedním skalárním bodem kódu.</span><span class="sxs-lookup"><span data-stu-id="080f8-225">But the last two are represented by more than one scalar value code point.</span></span>

* <span data-ttu-id="080f8-226">string"A" je reprezentován jednou skalární hodnotou a obsahuje jednu `char` instanci.</span><span class="sxs-lookup"><span data-stu-id="080f8-226">The string "a" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+0061 LATIN SMALL LETTER A`

* <span data-ttu-id="080f8-227">string"Á" je reprezentován jednou skalární hodnotou a obsahuje jednu `char` instanci.</span><span class="sxs-lookup"><span data-stu-id="080f8-227">The string "á" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+00E1 LATIN SMALL LETTER A WITH ACUTE`

* <span data-ttu-id="080f8-228">string"Á" vypadá stejně jako "á", ale je reprezentován dvěma skalárními hodnotami a obsahuje dvě `char` instance.</span><span class="sxs-lookup"><span data-stu-id="080f8-228">The string "á" looks the same as "á" but is represented by two scalar values and contains two `char` instances.</span></span>

  * `U+0061 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* <span data-ttu-id="080f8-229">Nakonec string "" představují `👩🏽‍🚒` čtyři skalární hodnoty a obsahují sedm `char` instancí.</span><span class="sxs-lookup"><span data-stu-id="080f8-229">Finally, the string "`👩🏽‍🚒`" is represented by four scalar values and contains seven `char` instances.</span></span>

  * <span data-ttu-id="080f8-230">`U+1F469 WOMAN` (doplňkový rozsah, vyžaduje náhradní pár)</span><span class="sxs-lookup"><span data-stu-id="080f8-230">`U+1F469 WOMAN` (supplementary range, requires a surrogate pair)</span></span>
  * <span data-ttu-id="080f8-231">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (doplňkový rozsah, vyžaduje náhradní pár)</span><span class="sxs-lookup"><span data-stu-id="080f8-231">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (supplementary range, requires a surrogate pair)</span></span>
  * `U+200D ZERO WIDTH JOINER`
  * <span data-ttu-id="080f8-232">`U+1F692 FIRE ENGINE` (doplňkový rozsah, vyžaduje náhradní pár)</span><span class="sxs-lookup"><span data-stu-id="080f8-232">`U+1F692 FIRE ENGINE` (supplementary range, requires a surrogate pair)</span></span>

<span data-ttu-id="080f8-233">V některých předchozích příkladech, například v kombinaci s modifikátorem akcent nebo v modifikátoru intonace skinu, se bod kódu na obrazovce nezobrazí jako samostatný prvek.</span><span class="sxs-lookup"><span data-stu-id="080f8-233">In some of the preceding examples - such as the combining accent modifier or the skin tone modifier - the code point does not display as a standalone element on the screen.</span></span> <span data-ttu-id="080f8-234">Místo toho slouží k úpravě vzhledu textového prvku, který byl dodán před ním.</span><span class="sxs-lookup"><span data-stu-id="080f8-234">Rather, it serves to modify the appearance of a text element that came before it.</span></span> <span data-ttu-id="080f8-235">Tyto příklady ukazují, že může trvat více skalárních hodnot, aby se zajistilo, co považujeme za jeden char cluster "Acter" nebo "grapheme".</span><span class="sxs-lookup"><span data-stu-id="080f8-235">These examples show that it might take multiple scalar values to make up what we think of as a single "character," or "grapheme cluster."</span></span>

<span data-ttu-id="080f8-236">Chcete-li vytvořit výčet clusterů grapheme v nástroji `string` , použijte <xref:System.Globalization.StringInfo> třídu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="080f8-236">To enumerate the grapheme clusters of a `string`, use the <xref:System.Globalization.StringInfo> class as shown in the following example.</span></span> <span data-ttu-id="080f8-237">Pokud jste obeznámeni s SWIFT, typ .NET `StringInfo` je koncepčně podobný [ `character` typu SWIFT](https://developer.apple.com/documentation/swift/character).</span><span class="sxs-lookup"><span data-stu-id="080f8-237">If you're familiar with Swift, the .NET `StringInfo` type is conceptually similar to [Swift's `character` type](https://developer.apple.com/documentation/swift/character).</span></span>

### <a name="example-count-no-locchar-no-locrune-and-text-element-instances"></a><span data-ttu-id="080f8-238">Příklad: počet char Rune instancí elementu text</span><span class="sxs-lookup"><span data-stu-id="080f8-238">Example: count char, Rune, and text element instances</span></span>

<span data-ttu-id="080f8-239">V rozhraní .NET API se cluster grapheme nazývá *textový prvek*.</span><span class="sxs-lookup"><span data-stu-id="080f8-239">In .NET APIs, a grapheme cluster is called a *text element*.</span></span> <span data-ttu-id="080f8-240">Následující metoda ukazuje rozdíly mezi `char` `Rune` instancemi prvků textu, a v `string` :</span><span class="sxs-lookup"><span data-stu-id="080f8-240">The following method demonstrates the differences between `char`, `Rune`, and text element instances in a `string`:</span></span>

<span data-ttu-id="080f8-241">::: Code Language = "CSharp" Source = "fragmenty/ char Acter-Encoding-Úvod/CSharp/CountTextElements. cs" ID = "SnippetCountMethod":::</span><span class="sxs-lookup"><span data-stu-id="080f8-241">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::</span></span>

<span data-ttu-id="080f8-242">::: Code Language = "CSharp" Source = "fragmenty/ char Acter-Encoding-Úvod/CSharp/CountTextElements. cs" ID = "SnippetCallCountMethod":::</span><span class="sxs-lookup"><span data-stu-id="080f8-242">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::</span></span>

<span data-ttu-id="080f8-243">Pokud tento kód spustíte v .NET Framework nebo .NET Core 3,1 nebo starším, zobrazí se počet prvků textu pro Emoji `4` .</span><span class="sxs-lookup"><span data-stu-id="080f8-243">If you run this code in .NET Framework or .NET Core 3.1 or earlier, the text element count for the emoji shows `4`.</span></span> <span data-ttu-id="080f8-244">To je způsobeno chybou ve `StringInfo` třídě, která je opravena v rozhraní .NET 5.</span><span class="sxs-lookup"><span data-stu-id="080f8-244">That is due to a bug in the `StringInfo` class that is fixed in .NET 5.</span></span>

### <a name="example-splitting-no-locstring-instances"></a><span data-ttu-id="080f8-245">Příklad: rozdělení string instancí</span><span class="sxs-lookup"><span data-stu-id="080f8-245">Example: splitting string instances</span></span>

<span data-ttu-id="080f8-246">Při rozdělování `string` instancí se nerozdělují náhradní páry a grapheme clustery.</span><span class="sxs-lookup"><span data-stu-id="080f8-246">When splitting `string` instances, avoid splitting surrogate pairs and grapheme clusters.</span></span> <span data-ttu-id="080f8-247">Vezměte v úvahu následující příklad nesprávného kódu, který je v úmyslu vkládat zalomení řádků každých 10 char acters v string :</span><span class="sxs-lookup"><span data-stu-id="080f8-247">Consider the following example of incorrect code, which intends to insert line breaks every 10 characters in a string:</span></span>

<span data-ttu-id="080f8-248">::: Code Language = "CSharp" Source = "fragmenty/ char Acter-Encoding-Úvod/CSharp/InsertNewlines. cs" ID = "SnippetBadExample":::</span><span class="sxs-lookup"><span data-stu-id="080f8-248">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::</span></span>

<span data-ttu-id="080f8-249">Vzhledem k tomu, že tento kód vytváří výčet instancí, je náhradní pár, který je považován za překrytí `char` 10 `char` hranic, rozdělen a mezi nimi bude vložen nový řádek.</span><span class="sxs-lookup"><span data-stu-id="080f8-249">Because this code enumerates `char` instances, a surrogate pair that happens to straddle a 10-`char` boundary will be split and a newline injected between them.</span></span> <span data-ttu-id="080f8-250">Toto vložení zavádí poškození dat, protože náhradní body kódu jsou smysluplné jenom jako páry.</span><span class="sxs-lookup"><span data-stu-id="080f8-250">This insertion introduces data corruption, because surrogate code points are meaningful only as pairs.</span></span>

<span data-ttu-id="080f8-251">Možnost poškození dat není při vytváření výčtu `Rune` instancí (skalárních hodnot) namísto `char` instancí odstraněna.</span><span class="sxs-lookup"><span data-stu-id="080f8-251">The potential for data corruption isn't eliminated if you enumerate `Rune` instances (scalar values) instead of `char` instances.</span></span> <span data-ttu-id="080f8-252">Sada `Rune` instancí může vytvořit cluster grapheme, který přechází na 10 `char` hranici.</span><span class="sxs-lookup"><span data-stu-id="080f8-252">A set of `Rune` instances might make up a grapheme cluster that straddles a 10-`char` boundary.</span></span> <span data-ttu-id="080f8-253">Pokud je sada clusterů grapheme rozdělená, nedá se správně interpretovat.</span><span class="sxs-lookup"><span data-stu-id="080f8-253">If the grapheme cluster set is split up, it can't be interpreted correctly.</span></span>

<span data-ttu-id="080f8-254">Lepším řešením je přerušit string počítání grapheme clusterů nebo textových prvků, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="080f8-254">A better approach is to break the string by counting grapheme clusters, or text elements, as in the following example:</span></span>

<span data-ttu-id="080f8-255">::: Code Language = "CSharp" Source = "fragmenty/ char Acter-Encoding-Úvod/CSharp/InsertNewlines. cs" ID = "SnippetGoodExample":::</span><span class="sxs-lookup"><span data-stu-id="080f8-255">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::</span></span>

<span data-ttu-id="080f8-256">Jak bylo uvedeno dříve, ale v implementacích rozhraní .NET jiné než .NET 5, `StringInfo` může třída považovat některé clustery grapheme nesprávně.</span><span class="sxs-lookup"><span data-stu-id="080f8-256">As noted earlier, however, in implementations of .NET other than .NET 5, the `StringInfo` class might handle some grapheme clusters incorrectly.</span></span>

## <a name="utf-8-and-utf-32"></a><span data-ttu-id="080f8-257">UTF-8 a UTF-32</span><span class="sxs-lookup"><span data-stu-id="080f8-257">UTF-8 and UTF-32</span></span>

<span data-ttu-id="080f8-258">Předchozí části se zaměřují na UTF-16, protože to je to, co rozhraní .NET používá ke kódování `string` instancí.</span><span class="sxs-lookup"><span data-stu-id="080f8-258">The preceding sections focused on UTF-16 because that's what .NET uses to encode `string` instances.</span></span> <span data-ttu-id="080f8-259">Pro Unicode- [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) a [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32)jsou k dispozici jiné systémy kódování.</span><span class="sxs-lookup"><span data-stu-id="080f8-259">There are other encoding systems for Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) and [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span></span> <span data-ttu-id="080f8-260">Tato kódování používají 8bitové jednotky kódu a 32 jednotek kódu v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="080f8-260">These encodings use 8-bit code units and 32-bit code units, respectively.</span></span>

<span data-ttu-id="080f8-261">Podobně jako UTF-16 vyžaduje UTF-8 několik jednotek kódu, které reprezentují některé skalární hodnoty Unicode.</span><span class="sxs-lookup"><span data-stu-id="080f8-261">Like UTF-16, UTF-8 requires multiple code units to represent some Unicode scalar values.</span></span> <span data-ttu-id="080f8-262">UTF-32 může představovat libovolnou skalární hodnotu v jedné 32-bitové kódové jednotce.</span><span class="sxs-lookup"><span data-stu-id="080f8-262">UTF-32 can represent any scalar value in a single 32-bit code unit.</span></span>

<span data-ttu-id="080f8-263">Tady je několik příkladů, které ukazují, jak je stejný bod kódu Unicode reprezentován v každém z těchto tří systémů kódování Unicode:</span><span class="sxs-lookup"><span data-stu-id="080f8-263">Here are some examples showing how the same Unicode code point is represented in each of these three Unicode encoding systems:</span></span>

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

<span data-ttu-id="080f8-264">Jak bylo uvedeno dříve, jedna jednotka kódu UTF-16 z [náhradního páru](#surrogate-pairs) nemá smysl sám o sobě.</span><span class="sxs-lookup"><span data-stu-id="080f8-264">As noted earlier, a single UTF-16 code unit from a [surrogate pair](#surrogate-pairs) is meaningless by itself.</span></span> <span data-ttu-id="080f8-265">Stejně tak jedna jednotka kódu UTF-8 nemá význam, pokud je v sekvenci dvou, tří nebo čtyř používaných k výpočtu skalární hodnoty.</span><span class="sxs-lookup"><span data-stu-id="080f8-265">In the same way, a single UTF-8 code unit is meaningless by itself if it's in a sequence of two, three, or four used to calculate a scalar value.</span></span>

### <a name="endianness"></a><span data-ttu-id="080f8-266">Endianitou</span><span class="sxs-lookup"><span data-stu-id="080f8-266">Endianness</span></span>

<span data-ttu-id="080f8-267">V rozhraní .NET jednotky kódu UTF-16 string jsou uloženy v souvislé paměti jako sekvence 16bitových celých čísel ( `char` instancí).</span><span class="sxs-lookup"><span data-stu-id="080f8-267">In .NET, the UTF-16 code units of a string are stored in contiguous memory as a sequence of 16-bit integers (`char` instances).</span></span> <span data-ttu-id="080f8-268">Bity jednotlivých jednotek kódu jsou rozloženy podle kódování [endian](https://en.wikipedia.org/wiki/Endianness) aktuální architektury.</span><span class="sxs-lookup"><span data-stu-id="080f8-268">The bits of individual code units are laid out according to the [endianness](https://en.wikipedia.org/wiki/Endianness) of the current architecture.</span></span>

<span data-ttu-id="080f8-269">V architektuře s malým počtem bitů by se string skládají z kódových bodů UTF-16 `[ D801 DCCC ]` v paměti jako bajty `[ 0x01, 0xD8, 0xCC, 0xDC ]` .</span><span class="sxs-lookup"><span data-stu-id="080f8-269">On a little-endian architecture, the string consisting of the UTF-16 code points `[ D801 DCCC ]` would be laid out in memory as the bytes `[ 0x01, 0xD8, 0xCC, 0xDC ]`.</span></span> <span data-ttu-id="080f8-270">V architektuře big-endian by se stejná velikost nahlásila string v paměti jako bajty `[ 0xD8, 0x01, 0xDC, 0xCC ]` .</span><span class="sxs-lookup"><span data-stu-id="080f8-270">On a big-endian architecture that same string would be laid out in memory as the bytes `[ 0xD8, 0x01, 0xDC, 0xCC ]`.</span></span>

<span data-ttu-id="080f8-271">Počítačové systémy, které vzájemně komunikují, musí souhlasit s tím, jak se data přenáší na síťový přenos.</span><span class="sxs-lookup"><span data-stu-id="080f8-271">Computer systems that communicate with each other must agree on the representation of data crossing the wire.</span></span> <span data-ttu-id="080f8-272">Většina síťových protokolů jako standard pro přenos textu používá UTF-8, aby nedocházelo k problémům, které by mohly nastat při komunikaci počítače big-endian s počítačem se systémem Little endian.</span><span class="sxs-lookup"><span data-stu-id="080f8-272">Most network protocols use UTF-8 as a standard when transmitting text, partly to avoid issues that might result from a big-endian machine communicating with a little-endian machine.</span></span> <span data-ttu-id="080f8-273">stringBody kódu znakové sady UTF-8 `[ F0 90 93 8C ]` budou vždy reprezentovány jako bajty `[ 0xF0, 0x90, 0x93, 0x8C ]` bez ohledu na formát endian.</span><span class="sxs-lookup"><span data-stu-id="080f8-273">The string consisting of the UTF-8 code points `[ F0 90 93 8C ]` will always be represented as the bytes `[ 0xF0, 0x90, 0x93, 0x8C ]` regardless of endianness.</span></span>

<span data-ttu-id="080f8-274">Chcete-li použít kódování UTF-8 pro přenos textu, aplikace .NET často používají kód podobný následujícímu příkladu:</span><span class="sxs-lookup"><span data-stu-id="080f8-274">To use UTF-8 for transmitting text, .NET applications often use code like the following example:</span></span>

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

<span data-ttu-id="080f8-275">V předchozím příkladu metoda [Encoding. UTF8. GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) dekóduje znak UTF-16 `string` zpět do série skalárních hodnot Unicode, poté tyto skalární hodnoty znovu ZAkóduje do znakové sady UTF-8 a umístí výslednou sekvenci do `byte` pole.</span><span class="sxs-lookup"><span data-stu-id="080f8-275">In the preceding example, the method [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) decodes the UTF-16 `string` back into a series of Unicode scalar values, then it re-encodes those scalar values into UTF-8 and places the resulting sequence into a `byte` array.</span></span> <span data-ttu-id="080f8-276">Metoda [Encoding. UTF8. GetString](xref:System.Text.UTF8Encoding.GetString%2A) provádí opačnou transformaci a PŘEVÁDÍ pole UTF-8 `byte` na UTF-16 `string` .</span><span class="sxs-lookup"><span data-stu-id="080f8-276">The method [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) performs the opposite transformation, converting a UTF-8 `byte` array to a UTF-16 `string`.</span></span>

> [!WARNING]
> <span data-ttu-id="080f8-277">Vzhledem k tomu, že UTF-8 je maloobchodech na internetu, může se stát, že se načtou nezpracované bajty z kabelu a data se budou považovat za, jako kdyby byla UTF-8.</span><span class="sxs-lookup"><span data-stu-id="080f8-277">Since UTF-8 is commonplace on the internet, it may be tempting to read raw bytes from the wire and to treat the data as if it were UTF-8.</span></span> <span data-ttu-id="080f8-278">Měli byste ale ověřit, že je ve skutečnosti ve správném formátu.</span><span class="sxs-lookup"><span data-stu-id="080f8-278">However, you should validate that it is indeed well-formed.</span></span> <span data-ttu-id="080f8-279">Uživatel se zlými úmysly může do vaší služby odeslat nesprávně formátovanou znakovou sadu UTF-8.</span><span class="sxs-lookup"><span data-stu-id="080f8-279">A malicious client might submit ill-formed UTF-8 to your service.</span></span> <span data-ttu-id="080f8-280">Pokud s těmito daty pracujete, jako kdyby byla ve správném formátu, mohlo by dojít k chybám nebo bezpečnostním otvorům ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="080f8-280">If you operate on that data as if it were well-formed, it could cause errors or security holes in your application.</span></span> <span data-ttu-id="080f8-281">Chcete-li ověřit data UTF-8, můžete použít metodu `Encoding.UTF8.GetString` , například, která provede ověření při převodu příchozích dat na `string` .</span><span class="sxs-lookup"><span data-stu-id="080f8-281">To validate UTF-8 data, you can use a method like `Encoding.UTF8.GetString`, which will perform validation while converting the incoming data to a `string`.</span></span>

### <a name="well-formed-encoding"></a><span data-ttu-id="080f8-282">Kódování ve správném formátu</span><span class="sxs-lookup"><span data-stu-id="080f8-282">Well-formed encoding</span></span>

<span data-ttu-id="080f8-283">Dobře formátované kódování Unicode je string jednotky kódu, které lze dekódovat jednoznačně a bez chyby v sekvenci skalárních hodnot Unicode.</span><span class="sxs-lookup"><span data-stu-id="080f8-283">A well-formed Unicode encoding is a string of code units that can be decoded unambiguously and without error into a sequence of Unicode scalar values.</span></span> <span data-ttu-id="080f8-284">Data ve správném formátu se dají překódovat volně a zpátky mezi UTF-8, UTF-16 a UTF-32.</span><span class="sxs-lookup"><span data-stu-id="080f8-284">Well-formed data can be transcoded freely back and forth between UTF-8, UTF-16, and UTF-32.</span></span>

<span data-ttu-id="080f8-285">Otázka, zda je sekvence kódování ve správném formátu nebo nesouvisí se Endian architektury počítače.</span><span class="sxs-lookup"><span data-stu-id="080f8-285">The question of whether an encoding sequence is well-formed or not is unrelated to the endianness of a machine's architecture.</span></span> <span data-ttu-id="080f8-286">Nesprávně vytvořená sekvence UTF-8 je nesprávně vytvořená stejným způsobem na počítačích se systémem big endian a little endian.</span><span class="sxs-lookup"><span data-stu-id="080f8-286">An ill-formed UTF-8 sequence is ill-formed in the same way on both big-endian and little-endian machines.</span></span>

<span data-ttu-id="080f8-287">Tady je několik příkladů nesprávně vytvořených kódování:</span><span class="sxs-lookup"><span data-stu-id="080f8-287">Here are some examples of ill-formed encodings:</span></span>

* <span data-ttu-id="080f8-288">V kódování UTF-8 je sekvence `[ 6C C2 61 ]` nesprávně vytvořená, protože `C2` nemůže následovat `61` .</span><span class="sxs-lookup"><span data-stu-id="080f8-288">In UTF-8, the sequence `[ 6C C2 61 ]` is ill-formed because `C2` cannot be followed by `61`.</span></span>

* <span data-ttu-id="080f8-289">V kódování UTF-16 je sekvence `[ DC00 DD00 ]` (nebo v jazyce C#, a string `"\udc00\udd00"` ) nesprávně vytvořená, protože Nízká náhrada `DC00` nemůže následovat za jinou nízkou náhradou `DD00` .</span><span class="sxs-lookup"><span data-stu-id="080f8-289">In UTF-16, the sequence `[ DC00 DD00 ]` (or, in C#, the string `"\udc00\udd00"`) is ill-formed because the low surrogate `DC00` cannot be followed by another low surrogate `DD00`.</span></span>

* <span data-ttu-id="080f8-290">V kódování UTF-32 je sekvence `[ 0011ABCD ]` nesprávně vytvořená, protože `0011ABCD` je mimo rozsah skalárních hodnot Unicode.</span><span class="sxs-lookup"><span data-stu-id="080f8-290">In UTF-32, the sequence `[ 0011ABCD ]` is ill-formed because `0011ABCD` is outside the range of Unicode scalar values.</span></span>

<span data-ttu-id="080f8-291">V rozhraní .NET `string` instance téměř vždy obsahují dobře vytvořená data UTF-16, ale nejsou zaručena.</span><span class="sxs-lookup"><span data-stu-id="080f8-291">In .NET, `string` instances almost always contain well-formed UTF-16 data, but that isn't guaranteed.</span></span> <span data-ttu-id="080f8-292">Následující příklady znázorňují platný kód C#, který v instancích vytváří nesprávně se formátovanou data UTF-16 `string` .</span><span class="sxs-lookup"><span data-stu-id="080f8-292">The following examples show valid C# code that creates ill-formed UTF-16 data in `string` instances.</span></span>

* <span data-ttu-id="080f8-293">Nesprávně vytvořený literál:</span><span class="sxs-lookup"><span data-stu-id="080f8-293">An ill-formed literal:</span></span>

  ```csharp
  const string s = "\ud800";
  ```

* <span data-ttu-id="080f8-294">Sub string , která rozdělí náhradní pár:</span><span class="sxs-lookup"><span data-stu-id="080f8-294">A substring that splits up a surrogate pair:</span></span>

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

<span data-ttu-id="080f8-295">Rozhraní API [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) , jako nikdy nevracejí nesprávně formátované `string` instance.</span><span class="sxs-lookup"><span data-stu-id="080f8-295">APIs like [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) never return ill-formed `string` instances.</span></span> <span data-ttu-id="080f8-296">`Encoding.GetString` a `Encoding.GetBytes` metody zjišťují ve vstupní sekvenci nesprávně formátované sekvence a char při generování výstupu provede substituci Acter.</span><span class="sxs-lookup"><span data-stu-id="080f8-296">`Encoding.GetString` and `Encoding.GetBytes` methods detect ill-formed sequences in the input and perform character substitution when generating the output.</span></span> <span data-ttu-id="080f8-297">Například pokud se [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) ve vstupu zobrazí bajt jiného typu než ASCII (mimo rozsah U + 0000.. U + 007F), vloží do vrácené instance znak? `string` .</span><span class="sxs-lookup"><span data-stu-id="080f8-297">For example, if [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) sees a non-ASCII byte in the input (outside the range U+0000..U+007F), it inserts a '?' into the returned `string` instance.</span></span> <span data-ttu-id="080f8-298">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) nahradí nesprávně vytvořené sekvence UTF-8 `U+FFFD REPLACEMENT CHARACTER ('�')` ve vrácené `string` instanci.</span><span class="sxs-lookup"><span data-stu-id="080f8-298">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) replaces ill-formed UTF-8 sequences with `U+FFFD REPLACEMENT CHARACTER ('�')` in the returned `string` instance.</span></span> <span data-ttu-id="080f8-299">Další informace najdete v části [Standard Unicode](https://www.unicode.org/versions/latest/), oddíly 5,22 a 3,9.</span><span class="sxs-lookup"><span data-stu-id="080f8-299">For more information, see [the Unicode Standard](https://www.unicode.org/versions/latest/), Sections 5.22 and 3.9.</span></span>

<span data-ttu-id="080f8-300">Vestavěné `Encoding` třídy lze také nakonfigurovat tak, aby vyvolaly výjimku místo toho, aby prováděly char Acter nahrazení, pokud jsou zobrazeny sekvence s chybnou strukturou.</span><span class="sxs-lookup"><span data-stu-id="080f8-300">The built-in `Encoding` classes can also be configured to throw an exception rather than perform character substitution when ill-formed sequences are seen.</span></span> <span data-ttu-id="080f8-301">Tento přístup se často používá v aplikacích citlivých na zabezpečení, kde char Acter nahrazení nemusí být přijatelné.</span><span class="sxs-lookup"><span data-stu-id="080f8-301">This approach is often used in security-sensitive applications where character substitution might not be acceptable.</span></span>

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

<span data-ttu-id="080f8-302">Informace o použití vestavěných `Encoding` tříd naleznete v tématu [How to use char Acter Encoding Classes in .NET](character-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="080f8-302">For information about how to use the built-in `Encoding` classes, see [How to use character encoding classes in .NET](character-encoding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="080f8-303">Viz také</span><span class="sxs-lookup"><span data-stu-id="080f8-303">See also</span></span>

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [<span data-ttu-id="080f8-304">Globalizace a lokalizace</span><span class="sxs-lookup"><span data-stu-id="080f8-304">Globalization and Localization</span></span>](../globalization-localization/index.md)
