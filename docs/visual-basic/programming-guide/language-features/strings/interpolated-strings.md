---
title: "Interpolované řetězce (Visual Basic)"
ms.date: 10/31/2017
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f865d5a7167847bf869d70a39570413dac271a2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="interpolated-strings-visual-basic-reference"></a><span data-ttu-id="424f0-102">Interpolované řetězce (referenční dokumentace jazyka Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="424f0-102">Interpolated Strings (Visual Basic Reference)</span></span>

<span data-ttu-id="424f0-103">Umožňuje vytvářet řetězce.</span><span class="sxs-lookup"><span data-stu-id="424f0-103">Used to construct strings.</span></span>  <span data-ttu-id="424f0-104">Interpolované řetězec vypadá jako řetězec šablony, která obsahuje *interpolované výrazy*.</span><span class="sxs-lookup"><span data-stu-id="424f0-104">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="424f0-105">Interpolované řetězce vrátí řetězec, který nahradí jejich řetězcové vyjádření interpolované výrazy, které obsahuje.</span><span class="sxs-lookup"><span data-stu-id="424f0-105">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span> <span data-ttu-id="424f0-106">Tato funkce je dostupná v jazyce Visual Basic 14 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="424f0-106">This feature is available in Visual Basic 14 and later versions.</span></span>

<span data-ttu-id="424f0-107">Argumenty interpolované řetězce jsou srozumitelnější než [složený formátovací řetězec](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span><span class="sxs-lookup"><span data-stu-id="424f0-107">The arguments of an interpolated string are easier to understand than a [composite format string](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="424f0-108">Například interpolované řetězce</span><span class="sxs-lookup"><span data-stu-id="424f0-108">For example, the interpolated string</span></span>  
  
```vb  
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```  
<span data-ttu-id="424f0-109">obsahuje dva interpolované výrazy {name}' a '{hodin: hh}'.</span><span class="sxs-lookup"><span data-stu-id="424f0-109">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span></span> <span data-ttu-id="424f0-110">Je ekvivalentní složený formátovací řetězec:</span><span class="sxs-lookup"><span data-stu-id="424f0-110">The equivalent composite format string is:</span></span>

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

<span data-ttu-id="424f0-111">Struktura interpolované řetězce je:</span><span class="sxs-lookup"><span data-stu-id="424f0-111">The structure of an interpolated string is:</span></span>  
  
```vb  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

<span data-ttu-id="424f0-112">kde:</span><span class="sxs-lookup"><span data-stu-id="424f0-112">where:</span></span> 

- <span data-ttu-id="424f0-113">*Šířka pole* se znaménkem, která určuje počet znaků v poli.</span><span class="sxs-lookup"><span data-stu-id="424f0-113">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="424f0-114">Pokud je kladné, je pole vpravo zarovnaný; záporná, zarovnaný doleva.</span><span class="sxs-lookup"><span data-stu-id="424f0-114">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span> 

- <span data-ttu-id="424f0-115">*řetězec formátu* je vhodný pro typ objektu, který je formátován řetězec formátu.</span><span class="sxs-lookup"><span data-stu-id="424f0-115">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="424f0-116">Například <xref:System.DateTime> hodnotu, může to být [řetězec formátu standardní hodnoty data a času](~/docs/standard/base-types/standard-date-and-time-format-strings.md) jako je například "D" nebo "d".</span><span class="sxs-lookup"><span data-stu-id="424f0-116">For example, for a <xref:System.DateTime> value, it could be a [standard date and time format string](~/docs/standard/base-types/standard-date-and-time-format-strings.md) such as "D" or "d".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="424f0-117">Nemůže mít žádné mezery mezi `$` a `"` , začíná řetězec.</span><span class="sxs-lookup"><span data-stu-id="424f0-117">You cannot have any whitespace between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="424f0-118">Chyba kompilátoru při restartování.</span><span class="sxs-lookup"><span data-stu-id="424f0-118">Doing so causes a compiler error.</span></span>

 <span data-ttu-id="424f0-119">Interpolované řetězce můžete použít kdekoli můžete řetězcový literál.</span><span class="sxs-lookup"><span data-stu-id="424f0-119">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="424f0-120">Interpolované řetězce je vyhodnocován pokaždé, když spustí kód s interpolované řetězce.</span><span class="sxs-lookup"><span data-stu-id="424f0-120">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="424f0-121">To umožňuje oddělit definice a vyhodnocení interpolované řetězce.</span><span class="sxs-lookup"><span data-stu-id="424f0-121">This allows you to separate the definition and evaluation of an interpolated string.</span></span>  
  
 <span data-ttu-id="424f0-122">Zahrnout složené závorky ("{" nebo "}") v interpolované řetězce, pomocí dvou složené závorky, "{{" nebo "}}".</span><span class="sxs-lookup"><span data-stu-id="424f0-122">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="424f0-123">Implicitní převody části Další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="424f0-123">See the Implicit Conversions section for more details.</span></span>  

<span data-ttu-id="424f0-124">Pokud interpolované řetězec obsahuje jiné znaky s zvláštní význam interpolované řetězce, jako je například uvozovky ("), dvojtečkou (:) ani čárky (,), že by měly být ukončeny Pokud se vyskytují v literálu text, nebo by měl být součástí výrazu oddělená závorky, pokud jsou součástí interpolované výrazu prvků jazyka.</span><span class="sxs-lookup"><span data-stu-id="424f0-124">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="424f0-125">Následující příklad řídicí sekvence znaky uvozovek pro zahrnutí ve výsledném řetězci a používá kulaté závorky a tím vymezit výraz `(age == 1 ? "" : "s")` tak, aby dvojtečkou není interpretována jako od řetězec formátu.</span><span class="sxs-lookup"><span data-stu-id="424f0-125">The following example escapes quotation marks to include them in the result string, and it uses parentheses to delimit the expression `(age == 1 ? "" : "s")` so that the colon is not interpreted as beginning a format string.</span></span>

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]  

## <a name="implicit-conversions"></a><span data-ttu-id="424f0-126">Implicitní převody</span><span class="sxs-lookup"><span data-stu-id="424f0-126">Implicit Conversions</span></span>  

<span data-ttu-id="424f0-127">Existují tři typu implicitní převody z interpolované řetězce:</span><span class="sxs-lookup"><span data-stu-id="424f0-127">There are three implicit type conversions from an interpolated string:</span></span>  

1. <span data-ttu-id="424f0-128">Interpolované řetězce pro převod <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="424f0-128">Conversion of an interpolated string to a <xref:System.String>.</span></span> <span data-ttu-id="424f0-129">Následující příklad vrátí řetězec, jehož interpolované řetězce výrazy nahradil jejich řetězcové vyjádření.</span><span class="sxs-lookup"><span data-stu-id="424f0-129">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="424f0-130">Příklad:</span><span class="sxs-lookup"><span data-stu-id="424f0-130">For example:</span></span>

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]  

   <span data-ttu-id="424f0-131">Toto je poslední výsledek interpretace řetězec.</span><span class="sxs-lookup"><span data-stu-id="424f0-131">This is the final result of a string interpretation.</span></span> <span data-ttu-id="424f0-132">Všechny výskyty dvojité složené závorky ("{{" a "}}") se převedou na jednom složených závorek.</span><span class="sxs-lookup"><span data-stu-id="424f0-132">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span> 

2. <span data-ttu-id="424f0-133">Interpolované řetězce pro převod <xref:System.IFormattable> proměnné, která umožňuje vytvořit více výsledek řetězce s obsahem specifické pro jazykovou verzi z jedné <xref:System.IFormattable> instance.</span><span class="sxs-lookup"><span data-stu-id="424f0-133">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="424f0-134">To je užitečné pro jako jsou správné číselné a číselné formáty pro jednotlivé jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="424f0-134">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="424f0-135">Všechny výskyty dvojité složené závorky ("{{" a "}}") zůstanou jako dvojité složené závorky, dokud se naformátovat řetězec voláním explicitně nebo implicitně <xref:System.Object.ToString> metoda.</span><span class="sxs-lookup"><span data-stu-id="424f0-135">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the <xref:System.Object.ToString> method.</span></span>  <span data-ttu-id="424f0-136">Všechny obsažené interpolace výrazy se převedou na {0}, {1} a tak dále.</span><span class="sxs-lookup"><span data-stu-id="424f0-136">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   <span data-ttu-id="424f0-137">Následující příklad používá reflexe k zobrazení členů, jakož i pole a vlastnosti hodnoty <xref:System.IFormattable> proměnné, která je vytvořena z interpolované řetězce.</span><span class="sxs-lookup"><span data-stu-id="424f0-137">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="424f0-138">Také předá <xref:System.IFormattable> proměnnou <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="424f0-138">It also passes the <xref:System.IFormattable> variable to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method.</span></span>

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]  

   <span data-ttu-id="424f0-139">Všimněte si, že může být prověřovány interpolované řetězce pouze pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="424f0-139">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="424f0-140">Pokud je předán řetězec formátování metoda, jako například <xref:System.Console.WriteLine(System.String)>, jeho položky formátu jsou vyřešeny a vrátí výsledný řetězec.</span><span class="sxs-lookup"><span data-stu-id="424f0-140">If it is passed to a string formatting method, such as <xref:System.Console.WriteLine(System.String)>, its format items are resolved and the result string returned.</span></span> 

3. <span data-ttu-id="424f0-141">Interpolované řetězce pro převod <xref:System.FormattableString> proměnné, která představuje složený formátovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="424f0-141">Conversion of an interpolated string to a <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="424f0-142">Probíhá kontrola složený formátovací řetězec a jak se vykreslí v důsledku řetězec, například vám můžou pomoct chránit před útoky, vkládání, pokud vytváříte dotazu.</span><span class="sxs-lookup"><span data-stu-id="424f0-142">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span> <span data-ttu-id="424f0-143">A <xref:System.FormattableString> také zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="424f0-143">A <xref:System.FormattableString> also includes:</span></span>

      - <span data-ttu-id="424f0-144">A <xref:System.FormattableString.ToString> přetížení, které vytváří výsledný řetězec pro <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="424f0-144">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      
      - <span data-ttu-id="424f0-145">A <xref:System.FormattableString.Invariant%2A> metoda, která vytvoří řetězec pro <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="424f0-145">A <xref:System.FormattableString.Invariant%2A> method that produces a string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      
      - <span data-ttu-id="424f0-146">A <xref:System.FormattableString.ToString(System.IFormatProvider)> metoda, která vytváří výsledný řetězec pro zadanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="424f0-146">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span> 
  
    <span data-ttu-id="424f0-147">Všechny výskyty dvojité složené závorky ("{{" a "}}") zůstanou jako dvojité složené závorky, dokud formátovat.</span><span class="sxs-lookup"><span data-stu-id="424f0-147">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format.</span></span>  <span data-ttu-id="424f0-148">Všechny obsažené interpolace výrazy se převedou na {0}, {1} a tak dále.</span><span class="sxs-lookup"><span data-stu-id="424f0-148">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]  

## <a name="see-also"></a><span data-ttu-id="424f0-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="424f0-149">See Also</span></span>  
<span data-ttu-id="424f0-150">f<xref:System.IFormattable?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="424f0-150">f <xref:System.IFormattable?displayProperty=nameWithType></span></span>   
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [<span data-ttu-id="424f0-151">Referenční dokumentace jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="424f0-151">Visual Basic Language Reference</span></span>](index.md)  
 