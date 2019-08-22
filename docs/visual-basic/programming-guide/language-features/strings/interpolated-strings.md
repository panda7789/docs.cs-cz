---
title: Interpolované řetězce (Visual Basic)
ms.date: 10/31/2017
ms.openlocfilehash: b9dd055154c86da370a984a465ed412f1fd9908c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666941"
---
# <a name="interpolated-strings-visual-basic-reference"></a><span data-ttu-id="de0ae-102">Interpolované řetězce (Visual Basic Reference)</span><span class="sxs-lookup"><span data-stu-id="de0ae-102">Interpolated Strings (Visual Basic Reference)</span></span>

<span data-ttu-id="de0ae-103">Slouží k vytváření řetězců.</span><span class="sxs-lookup"><span data-stu-id="de0ae-103">Used to construct strings.</span></span>  <span data-ttu-id="de0ae-104">Interpolovaná řetězcová událost vypadá jako řetězec šablony, který obsahuje *interpolované výrazy*.</span><span class="sxs-lookup"><span data-stu-id="de0ae-104">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="de0ae-105">Interpolovaná řetězcová funkce vrátí řetězec, který nahradí interpolované výrazy, které obsahuje, spolu s jejich řetězcovými reprezentacemi.</span><span class="sxs-lookup"><span data-stu-id="de0ae-105">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span> <span data-ttu-id="de0ae-106">Tato funkce je k dispozici v Visual Basic 14 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="de0ae-106">This feature is available in Visual Basic 14 and later versions.</span></span>

<span data-ttu-id="de0ae-107">Argumenty interpolované řetězcové řetězce jsou snazší pochopit než [složený formátovací řetězec](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span><span class="sxs-lookup"><span data-stu-id="de0ae-107">The arguments of an interpolated string are easier to understand than a [composite format string](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="de0ae-108">Například interpolovaná řetězcová</span><span class="sxs-lookup"><span data-stu-id="de0ae-108">For example, the interpolated string</span></span>

```vb
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```

<span data-ttu-id="de0ae-109">obsahuje dva interpolované výrazy {Name} a {hours: hh}.</span><span class="sxs-lookup"><span data-stu-id="de0ae-109">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span></span> <span data-ttu-id="de0ae-110">Ekvivalentní řetězec složeného formátu je:</span><span class="sxs-lookup"><span data-stu-id="de0ae-110">The equivalent composite format string is:</span></span>

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours);
```

<span data-ttu-id="de0ae-111">Struktura interpolované řetězcové řetězce je:</span><span class="sxs-lookup"><span data-stu-id="de0ae-111">The structure of an interpolated string is:</span></span>

```vb
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."
```

<span data-ttu-id="de0ae-112">kde:</span><span class="sxs-lookup"><span data-stu-id="de0ae-112">where:</span></span>

- <span data-ttu-id="de0ae-113">*Šířka pole* je celé číslo se znaménkem, které označuje počet znaků v poli.</span><span class="sxs-lookup"><span data-stu-id="de0ae-113">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="de0ae-114">Pokud je kladné, pole je zarovnáno vpravo; If negativně zarovnaný doleva.</span><span class="sxs-lookup"><span data-stu-id="de0ae-114">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span>

- <span data-ttu-id="de0ae-115">*řetězec formátu* je řetězec formátu vhodný pro typ objektu, který se má formátovat.</span><span class="sxs-lookup"><span data-stu-id="de0ae-115">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="de0ae-116">Například pro <xref:System.DateTime> hodnotu může být [standardní formátovací řetězec data a času](../../../../standard/base-types/standard-date-and-time-format-strings.md) , například "d" nebo "d".</span><span class="sxs-lookup"><span data-stu-id="de0ae-116">For example, for a <xref:System.DateTime> value, it could be a [standard date and time format string](../../../../standard/base-types/standard-date-and-time-format-strings.md) such as "D" or "d".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="de0ae-117">Mezi `$` znakem `"` a, který začíná řetězcem, nemůže být mezera.</span><span class="sxs-lookup"><span data-stu-id="de0ae-117">You cannot have any white space between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="de0ae-118">V důsledku toho dojde k chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="de0ae-118">Doing so causes a compiler error.</span></span>

<span data-ttu-id="de0ae-119">Můžete použít interpolované řetězce kdekoli, kde můžete použít řetězcový literál.</span><span class="sxs-lookup"><span data-stu-id="de0ae-119">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="de0ae-120">Interpolovaná řetězcová doba je vyhodnocena pokaždé, když se spustí kód s interpolovaná řetězcovou dobou.</span><span class="sxs-lookup"><span data-stu-id="de0ae-120">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="de0ae-121">To umožňuje oddělit definici a vyhodnocení interpolované řetězcové lhůty.</span><span class="sxs-lookup"><span data-stu-id="de0ae-121">This allows you to separate the definition and evaluation of an interpolated string.</span></span>

<span data-ttu-id="de0ae-122">Chcete-li zahrnout složenou závorku ("{" nebo "}") do interpolované řetězcové řetězce, použijte dvě složené závorky, "{{" nebo "}}".</span><span class="sxs-lookup"><span data-stu-id="de0ae-122">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="de0ae-123">Další podrobnosti najdete v části implicitní převody.</span><span class="sxs-lookup"><span data-stu-id="de0ae-123">See the Implicit Conversions section for more details.</span></span>

<span data-ttu-id="de0ae-124">Pokud interpolovaná řetězec obsahuje jiné znaky se zvláštními významy v interpolované řetězci, například uvozovky ("), dvojtečka (:) nebo čárka (,), měla by být uvozena řídicím znakem, pokud k nim dojde v textovém literálu, nebo by měly být zahrnuty ve výrazu odděleném závorky, pokud jsou prvky jazyka zahrnuté do interpolované výrazu.</span><span class="sxs-lookup"><span data-stu-id="de0ae-124">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="de0ae-125">Následující příklad označuje uvozovky, které mají být zahrnuty ve výsledném řetězci, a používá závorky k vymezení výrazu `(age == 1 ? "" : "s")` tak, aby dvojtečka nebyla interpretována jako začátek řetězce formátu.</span><span class="sxs-lookup"><span data-stu-id="de0ae-125">The following example escapes quotation marks to include them in the result string, and it uses parentheses to delimit the expression `(age == 1 ? "" : "s")` so that the colon is not interpreted as beginning a format string.</span></span>

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]

## <a name="implicit-conversions"></a><span data-ttu-id="de0ae-126">Implicitní převody</span><span class="sxs-lookup"><span data-stu-id="de0ae-126">Implicit Conversions</span></span>

<span data-ttu-id="de0ae-127">Existují tři implicitní převody typu z interpolované řetězce:</span><span class="sxs-lookup"><span data-stu-id="de0ae-127">There are three implicit type conversions from an interpolated string:</span></span>

1. <span data-ttu-id="de0ae-128">Konverze interpolované řetězcové na <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="de0ae-128">Conversion of an interpolated string to a <xref:System.String>.</span></span> <span data-ttu-id="de0ae-129">Následující příklad vrátí řetězec, jehož interpolované řetězcové výrazy byly nahrazeny svými reprezentacemi řetězců.</span><span class="sxs-lookup"><span data-stu-id="de0ae-129">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="de0ae-130">Příklad:</span><span class="sxs-lookup"><span data-stu-id="de0ae-130">For example:</span></span>

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]

   <span data-ttu-id="de0ae-131">Toto je konečný výsledek interpretace řetězce.</span><span class="sxs-lookup"><span data-stu-id="de0ae-131">This is the final result of a string interpretation.</span></span> <span data-ttu-id="de0ae-132">Všechny výskyty dvojitých složených závorek ("{{" a "}}") jsou převedeny na jednu složenou závorku.</span><span class="sxs-lookup"><span data-stu-id="de0ae-132">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span>

2. <span data-ttu-id="de0ae-133">Převod interpolované řetězce na <xref:System.IFormattable> proměnnou, která umožňuje vytvořit více výsledných řetězců s obsahem specifickým pro jazykovou verzi z jedné <xref:System.IFormattable> instance.</span><span class="sxs-lookup"><span data-stu-id="de0ae-133">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="de0ae-134">To je užitečné pro zahrnutí takových věcí jako správných formátů číselného a data pro jednotlivé kultury.</span><span class="sxs-lookup"><span data-stu-id="de0ae-134">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="de0ae-135">Všechny výskyty dvojitých složených závorek ("{{" a "}}") zůstávají jako dvojité složené závorky, dokud řetězec neformátujete explicitně nebo implicitně voláním <xref:System.Object.ToString> metody.</span><span class="sxs-lookup"><span data-stu-id="de0ae-135">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the <xref:System.Object.ToString> method.</span></span>  <span data-ttu-id="de0ae-136">Všechny obsažené výrazy interpolace jsou převedeny na {0}, {1}a tak dále.</span><span class="sxs-lookup"><span data-stu-id="de0ae-136">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>

   <span data-ttu-id="de0ae-137">Následující příklad používá reflexi k zobrazení členů a hodnot pole a vlastností <xref:System.IFormattable> proměnné, která je vytvořena z interpolované řetězcové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="de0ae-137">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="de0ae-138">Také předá <xref:System.IFormattable> proměnnou <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodě.</span><span class="sxs-lookup"><span data-stu-id="de0ae-138">It also passes the <xref:System.IFormattable> variable to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method.</span></span>

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]

   <span data-ttu-id="de0ae-139">Všimněte si, že interpolovaná řetězcová operace může být zkontrolována pouze pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="de0ae-139">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="de0ae-140">Pokud je předána metodě formátování řetězce, například <xref:System.Console.WriteLine(System.String)>, jsou vyřešeny jeho položky formátu a výsledný řetězec je vrácen.</span><span class="sxs-lookup"><span data-stu-id="de0ae-140">If it is passed to a string formatting method, such as <xref:System.Console.WriteLine(System.String)>, its format items are resolved and the result string returned.</span></span>

3. <span data-ttu-id="de0ae-141">Konverze interpolované řetězce na <xref:System.FormattableString> proměnnou, která představuje řetězec složeného formátu.</span><span class="sxs-lookup"><span data-stu-id="de0ae-141">Conversion of an interpolated string to a <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="de0ae-142">Kontrola složeného formátovacího řetězce a jeho vykreslení jako výsledný řetězec může například přispět k ochraně proti útoku prostřednictvím injektáže, pokud jste sestavování dotazu.</span><span class="sxs-lookup"><span data-stu-id="de0ae-142">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span> <span data-ttu-id="de0ae-143">Zahrnuje <xref:System.FormattableString> také:</span><span class="sxs-lookup"><span data-stu-id="de0ae-143">A <xref:System.FormattableString> also includes:</span></span>

      - <span data-ttu-id="de0ae-144">Přetížení, které vytváří výsledný řetězec <xref:System.Globalization.CultureInfo.CurrentCulture>pro. <xref:System.FormattableString.ToString></span><span class="sxs-lookup"><span data-stu-id="de0ae-144">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>

      - <span data-ttu-id="de0ae-145">Metoda, která vytváří řetězec <xref:System.Globalization.CultureInfo.InvariantCulture>pro. <xref:System.FormattableString.Invariant%2A></span><span class="sxs-lookup"><span data-stu-id="de0ae-145">A <xref:System.FormattableString.Invariant%2A> method that produces a string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>

      - <span data-ttu-id="de0ae-146"><xref:System.FormattableString.ToString(System.IFormatProvider)> Metoda, která vytváří výsledný řetězec pro zadanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="de0ae-146">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="de0ae-147">Všechny výskyty dvojitých složených závorek ("{{" a "}}") zůstávají jako dvojité složené závorky, dokud je neformátujete.</span><span class="sxs-lookup"><span data-stu-id="de0ae-147">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format.</span></span>  <span data-ttu-id="de0ae-148">Všechny obsažené výrazy interpolace jsou převedeny na {0}, {1}a tak dále.</span><span class="sxs-lookup"><span data-stu-id="de0ae-148">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]

## <a name="see-also"></a><span data-ttu-id="de0ae-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de0ae-149">See also</span></span>

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- [<span data-ttu-id="de0ae-150">Referenční příručka jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="de0ae-150">Visual Basic Language Reference</span></span>](index.md)
