---
title: Interpolované řetězce (Visual Basic)
ms.date: 10/31/2017
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 313e74d5ce252884f1df2479ef1db8b4b24b5cce
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480007"
---
# <a name="interpolated-strings-visual-basic-reference"></a><span data-ttu-id="c6801-102">Interpolované řetězce (referenční dokumentace jazyka Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6801-102">Interpolated Strings (Visual Basic Reference)</span></span>

<span data-ttu-id="c6801-103">Použít k vytvoření řetězce.</span><span class="sxs-lookup"><span data-stu-id="c6801-103">Used to construct strings.</span></span>  <span data-ttu-id="c6801-104">Interpolovaný řetězec vypadá jako řetězec šablony, který obsahuje *interpolovaných výrazů*.</span><span class="sxs-lookup"><span data-stu-id="c6801-104">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="c6801-105">Interpolované řetězce vrátí řetězec, který nahradí interpolovaných výrazů, které obsahuje jejich řetězcové vyjádření.</span><span class="sxs-lookup"><span data-stu-id="c6801-105">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span> <span data-ttu-id="c6801-106">Tato funkce je dostupná v jazyce Visual Basic, 14 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="c6801-106">This feature is available in Visual Basic 14 and later versions.</span></span>

<span data-ttu-id="c6801-107">Jsou Jednoduší na porozumění než argumenty interpolovaném řetězci [složený řetězec formátu](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span><span class="sxs-lookup"><span data-stu-id="c6801-107">The arguments of an interpolated string are easier to understand than a [composite format string](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="c6801-108">Například interpolovaný řetězec</span><span class="sxs-lookup"><span data-stu-id="c6801-108">For example, the interpolated string</span></span>  
  
```vb  
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```  
<span data-ttu-id="c6801-109">obsahuje dva interpolovaných výrazů {name}"a"{hodin: hh}".</span><span class="sxs-lookup"><span data-stu-id="c6801-109">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span></span> <span data-ttu-id="c6801-110">Je ekvivalentní složeném formátovacím řetězci:</span><span class="sxs-lookup"><span data-stu-id="c6801-110">The equivalent composite format string is:</span></span>

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

<span data-ttu-id="c6801-111">Struktura interpolovaného řetězce je:</span><span class="sxs-lookup"><span data-stu-id="c6801-111">The structure of an interpolated string is:</span></span>  
  
```vb  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

<span data-ttu-id="c6801-112">kde:</span><span class="sxs-lookup"><span data-stu-id="c6801-112">where:</span></span> 

- <span data-ttu-id="c6801-113">*Šířka pole* je celé číslo se znaménkem, která určuje počet znaků v poli.</span><span class="sxs-lookup"><span data-stu-id="c6801-113">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="c6801-114">Pokud je pozitivní, pole zarovnané vpravo; Pokud je záporná, zarovnané vlevo.</span><span class="sxs-lookup"><span data-stu-id="c6801-114">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span> 

- <span data-ttu-id="c6801-115">*řetězec formátu* formátovací řetězec odpovídá typu formátovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="c6801-115">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="c6801-116">Třeba <xref:System.DateTime> hodnotu, může to být [řetězec formátu data a času](~/docs/standard/base-types/standard-date-and-time-format-strings.md) jako je například "D" nebo "d".</span><span class="sxs-lookup"><span data-stu-id="c6801-116">For example, for a <xref:System.DateTime> value, it could be a [standard date and time format string](~/docs/standard/base-types/standard-date-and-time-format-strings.md) such as "D" or "d".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6801-117">Nemůže obsahovat žádné prázdné znaky. mezi `$` a `"` na začátku řetězce.</span><span class="sxs-lookup"><span data-stu-id="c6801-117">You cannot have any white space between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="c6801-118">To způsobí chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="c6801-118">Doing so causes a compiler error.</span></span>

 <span data-ttu-id="c6801-119">Můžete použít interpolovaném řetězci kdekoli můžete použít textový literál.</span><span class="sxs-lookup"><span data-stu-id="c6801-119">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="c6801-120">Interpolované řetězce se vyhodnocuje pokaždé, když spustí kód interpolovaném řetězci.</span><span class="sxs-lookup"><span data-stu-id="c6801-120">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="c6801-121">To umožňuje oddělit definici a hodnocení interpolovaného řetězce.</span><span class="sxs-lookup"><span data-stu-id="c6801-121">This allows you to separate the definition and evaluation of an interpolated string.</span></span>  
  
 <span data-ttu-id="c6801-122">Zahrnout složenou závorku ("{" nebo "}") v interpolovaném řetězci, použijte dvě složené závorky, "{{" nebo "}}".</span><span class="sxs-lookup"><span data-stu-id="c6801-122">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="c6801-123">Další podrobnosti v části implicitní převody.</span><span class="sxs-lookup"><span data-stu-id="c6801-123">See the Implicit Conversions section for more details.</span></span>  

<span data-ttu-id="c6801-124">Pokud interpolovaný řetězec obsahuje jiné znaky zvláštní význam v interpolovaném řetězci, jako je například dvojité uvozovky ("), dvojtečka (:) nebo čárka (,), že by měly být ukončeny Pokud k nim dojde v textovém literálu nebo by měla být součástí výrazu odděleny závorky, pokud jsou prvky jazyka, které jsou součástí interpolovaným výrazem.</span><span class="sxs-lookup"><span data-stu-id="c6801-124">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="c6801-125">Následující příklad řídicí sekvence uvozovek pro zahrnutí ve výsledném řetězci a používá závorky pro vymezení výraz `(age == 1 ? "" : "s")` tak, aby dvojtečka není interpretován jako od řetězec formátu.</span><span class="sxs-lookup"><span data-stu-id="c6801-125">The following example escapes quotation marks to include them in the result string, and it uses parentheses to delimit the expression `(age == 1 ? "" : "s")` so that the colon is not interpreted as beginning a format string.</span></span>

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]  

## <a name="implicit-conversions"></a><span data-ttu-id="c6801-126">Implicitní převody</span><span class="sxs-lookup"><span data-stu-id="c6801-126">Implicit Conversions</span></span>  

<span data-ttu-id="c6801-127">Existují tři implicitních převodech typů v interpolovaném řetězci:</span><span class="sxs-lookup"><span data-stu-id="c6801-127">There are three implicit type conversions from an interpolated string:</span></span>  

1. <span data-ttu-id="c6801-128">Převod interpolované řetězce, který se <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c6801-128">Conversion of an interpolated string to a <xref:System.String>.</span></span> <span data-ttu-id="c6801-129">Následující příklad vrátí řetězec, jehož interpolovaném řetězci výrazy byly nahrazeny jejich řetězcové vyjádření.</span><span class="sxs-lookup"><span data-stu-id="c6801-129">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="c6801-130">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c6801-130">For example:</span></span>

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]  

   <span data-ttu-id="c6801-131">Toto je konečný výsledek interpretace řetězce.</span><span class="sxs-lookup"><span data-stu-id="c6801-131">This is the final result of a string interpretation.</span></span> <span data-ttu-id="c6801-132">Všechny výskyty dvojitých složených závorek ("{{" a "}}") jsou převedeny na jednu složenou závorku.</span><span class="sxs-lookup"><span data-stu-id="c6801-132">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span> 

2. <span data-ttu-id="c6801-133">Převod interpolovaného řetězce do <xref:System.IFormattable> proměnné, která umožňuje vytvořit více výsledek řetězce s obsahem specifické pro jazykovou verzi z jedné <xref:System.IFormattable> instance.</span><span class="sxs-lookup"><span data-stu-id="c6801-133">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="c6801-134">To je užitečné pro včetně prvků jako správný číselné a číselné formáty pro jednotlivé jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="c6801-134">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="c6801-135">Všechny výskyty dvojitých složených závorek ("{{" a "}}") zůstanou jako dvojitých složených závorek, dokud je naformátovat řetězec voláním explicitně nebo implicitně <xref:System.Object.ToString> metody.</span><span class="sxs-lookup"><span data-stu-id="c6801-135">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the <xref:System.Object.ToString> method.</span></span>  <span data-ttu-id="c6801-136">Všechny obsažené interpolace výrazy jsou převedeny na {0}, {1}, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="c6801-136">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   <span data-ttu-id="c6801-137">Následující příklad používá reflexi k zobrazení členů, jakož i hodnoty polí a vlastností <xref:System.IFormattable> proměnná, která je vytvořena z interpolovaného řetězce.</span><span class="sxs-lookup"><span data-stu-id="c6801-137">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="c6801-138">Také předá <xref:System.IFormattable> proměnnou <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="c6801-138">It also passes the <xref:System.IFormattable> variable to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method.</span></span>

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]  

   <span data-ttu-id="c6801-139">Mějte na paměti, můžete ho zkontrolovat interpolovaném řetězci pouze pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="c6801-139">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="c6801-140">Pokud je předán do řetězce formátování, jako například <xref:System.Console.WriteLine(System.String)>, jeho položkami formátu jsou vyřešeny a vrátí výsledný řetězec.</span><span class="sxs-lookup"><span data-stu-id="c6801-140">If it is passed to a string formatting method, such as <xref:System.Console.WriteLine(System.String)>, its format items are resolved and the result string returned.</span></span> 

3. <span data-ttu-id="c6801-141">Převod interpolované řetězce, který se <xref:System.FormattableString> proměnné, která představuje složený řetězec formátu.</span><span class="sxs-lookup"><span data-stu-id="c6801-141">Conversion of an interpolated string to a <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="c6801-142">Kontrola složeném formátovacím řetězci a jak se vykresluje v důsledku řetězec, například vám můžou pomoct chránit před útoky prostřednictvím injektáže, pokud vytváříte dotazu.</span><span class="sxs-lookup"><span data-stu-id="c6801-142">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span> <span data-ttu-id="c6801-143">A <xref:System.FormattableString> také zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="c6801-143">A <xref:System.FormattableString> also includes:</span></span>

      - <span data-ttu-id="c6801-144">A <xref:System.FormattableString.ToString> přetížení, které vytváří výsledný řetězec pro <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="c6801-144">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      
      - <span data-ttu-id="c6801-145">A <xref:System.FormattableString.Invariant%2A> metodu, která vytvoří řetězec <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="c6801-145">A <xref:System.FormattableString.Invariant%2A> method that produces a string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      
      - <span data-ttu-id="c6801-146">A <xref:System.FormattableString.ToString(System.IFormatProvider)> metodu, která vytváří výsledný řetězec pro zadanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="c6801-146">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span> 
  
    <span data-ttu-id="c6801-147">Všechny výskyty dvojitých složených závorek ("{{" a "}}") zůstanou jako dvojitých složených závorek, dokud je naformátovat.</span><span class="sxs-lookup"><span data-stu-id="c6801-147">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format.</span></span>  <span data-ttu-id="c6801-148">Všechny obsažené interpolace výrazy jsou převedeny na {0}, {1}, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="c6801-148">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]  

## <a name="see-also"></a><span data-ttu-id="c6801-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6801-149">See Also</span></span>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [<span data-ttu-id="c6801-150">Referenční příručka jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c6801-150">Visual Basic Language Reference</span></span>](index.md)  
 