---
title: Co je nového v C# 6. C# příručce
description: Naučte se nové funkce C# ve verzi 6.
ms.date: 12/12/2018
ms.openlocfilehash: da40b4c9d4af0094fdd907c542e971ba55086e0f
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971386"
---
# <a name="whats-new-in-c-6"></a><span data-ttu-id="13e25-103">Co je nového v C# 6</span><span class="sxs-lookup"><span data-stu-id="13e25-103">What's New in C# 6</span></span>

<span data-ttu-id="13e25-104">Verze 6,0 C# obsahuje mnoho funkcí, které zlepšují produktivitu pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="13e25-104">The 6.0 release of C# contained many features that improve productivity for developers.</span></span> <span data-ttu-id="13e25-105">Celkový vliv těchto funkcí je, že píšete výstižnější kód, který je také čitelnější.</span><span class="sxs-lookup"><span data-stu-id="13e25-105">The overall effect of these features is that you write more concise code that is also more readable.</span></span> <span data-ttu-id="13e25-106">Syntaxe obsahuje méně procedury pro mnoho běžných postupů.</span><span class="sxs-lookup"><span data-stu-id="13e25-106">The syntax contains less ceremony for many common practices.</span></span> <span data-ttu-id="13e25-107">Je snazší, abyste viděli záměr návrhu s méně procedury.</span><span class="sxs-lookup"><span data-stu-id="13e25-107">It's easier to see the design intent with less ceremony.</span></span> <span data-ttu-id="13e25-108">Seznamte se s těmito funkcemi dobře a budete produktivnější a zapište čitelnější kód.</span><span class="sxs-lookup"><span data-stu-id="13e25-108">Learn these features well, and you'll be more productive and write more readable code.</span></span> <span data-ttu-id="13e25-109">Můžete se soustředit na další funkce než v konstrukcích daného jazyka.</span><span class="sxs-lookup"><span data-stu-id="13e25-109">You can concentrate more on your features than on the constructs of the language.</span></span>

<span data-ttu-id="13e25-110">Zbývající část tohoto článku obsahuje přehled každé z těchto funkcí s odkazem na prozkoumání jednotlivých funkcí.</span><span class="sxs-lookup"><span data-stu-id="13e25-110">The rest of this article provides an overview of each of these features, with a link to explore each feature.</span></span> <span data-ttu-id="13e25-111">V části kurzy můžete také prozkoumat funkce [interaktivního průzkumu na C# 6](../tutorials/exploration/csharp-6.yml) .</span><span class="sxs-lookup"><span data-stu-id="13e25-111">You can also explore the features in an [interactive exploration on C# 6](../tutorials/exploration/csharp-6.yml) in the tutorials section.</span></span>

## <a name="read-only-auto-properties"></a><span data-ttu-id="13e25-112">Automatické vlastnosti jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="13e25-112">Read-only auto-properties</span></span>

<span data-ttu-id="13e25-113">*Automatické vlastnosti jen pro čtení* poskytují stručnější syntaxi pro vytváření neměnných typů.</span><span class="sxs-lookup"><span data-stu-id="13e25-113">*Read-only auto-properties* provide a more concise syntax to create immutable types.</span></span> <span data-ttu-id="13e25-114">Automatickou vlastnost deklarujete pouze pomocí přístupového objektu Get:</span><span class="sxs-lookup"><span data-stu-id="13e25-114">You declare the auto-property with only a get accessor:</span></span>

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

<span data-ttu-id="13e25-115">Vlastnosti `FirstName` a`LastName` lze nastavit pouze v těle konstruktoru stejné třídy:</span><span class="sxs-lookup"><span data-stu-id="13e25-115">The `FirstName` and `LastName` properties can be set only in the body of the constructor of the same class:</span></span>

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

<span data-ttu-id="13e25-116">Pokus o nastavení `LastName` v jiné metodě `CS0200` generuje chybu kompilace:</span><span class="sxs-lookup"><span data-stu-id="13e25-116">Trying to set `LastName` in another method generates a `CS0200` compilation error:</span></span>

```csharp
public class Student
{
    public string LastName { get;  }

    public void ChangeName(string newLastName)
    {
        // Generates CS0200: Property or indexer cannot be assigned to -- it is read only
        LastName = newLastName;
    }
}
```

<span data-ttu-id="13e25-117">Tato funkce umožňuje skutečnou podporu jazyka pro vytváření neměnných typů a používá stručnější a pohodlný syntax automatických vlastností.</span><span class="sxs-lookup"><span data-stu-id="13e25-117">This feature enables true language support for creating immutable types and uses the more concise and convenient auto-property syntax.</span></span>

<span data-ttu-id="13e25-118">Pokud přidání této syntaxe neodebere přístupnou metodu, jedná se o [binární kompatibilní změnu](version-update-considerations.md#binary-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="13e25-118">If adding this syntax doesn't remove an accessible method, it's a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="auto-property-initializers"></a><span data-ttu-id="13e25-119">Inicializátory automatickou vlastnost</span><span class="sxs-lookup"><span data-stu-id="13e25-119">Auto-property initializers</span></span>

<span data-ttu-id="13e25-120">*Inicializátory automatických vlastností* umožňují deklarovat počáteční hodnotu pro automatickou vlastnost v rámci deklarace vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="13e25-120">*Auto-property initializers* let you declare the initial value for an auto-property as part of the property declaration.</span></span>

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

<span data-ttu-id="13e25-121">`Grades` Člen je inicializován, kde je deklarován.</span><span class="sxs-lookup"><span data-stu-id="13e25-121">The `Grades` member is initialized where it's declared.</span></span> <span data-ttu-id="13e25-122">To usnadňuje provedení inicializace přesně jednou.</span><span class="sxs-lookup"><span data-stu-id="13e25-122">That makes it easier to perform the initialization exactly once.</span></span> <span data-ttu-id="13e25-123">Inicializace je součástí deklarace vlastnosti, což usnadňuje přidělení úložiště k veřejnému rozhraní pro `Student` objekty.</span><span class="sxs-lookup"><span data-stu-id="13e25-123">The initialization is part of the property declaration, making it easier to equate the storage allocation with the public interface for `Student` objects.</span></span>

## <a name="expression-bodied-function-members"></a><span data-ttu-id="13e25-124">Členové funkce Expression-těle</span><span class="sxs-lookup"><span data-stu-id="13e25-124">Expression-bodied function members</span></span>

<span data-ttu-id="13e25-125">Mnoho členů, které napíšete, je jediné příkazy, které by mohly být jednotlivé výrazy.</span><span class="sxs-lookup"><span data-stu-id="13e25-125">Many members that you write are single statements that could be single expressions.</span></span> <span data-ttu-id="13e25-126">Místo toho zapište člen Expression-těle.</span><span class="sxs-lookup"><span data-stu-id="13e25-126">Write an expression-bodied member instead.</span></span> <span data-ttu-id="13e25-127">Funguje pro metody a vlastnosti jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="13e25-127">It works for methods and read-only properties.</span></span> <span data-ttu-id="13e25-128">Například přepsání `ToString()` je často skvělým kandidátem:</span><span class="sxs-lookup"><span data-stu-id="13e25-128">For example, an override of `ToString()` is often a great candidate:</span></span>

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

<span data-ttu-id="13e25-129">Tuto syntaxi můžete použít také pro vlastnosti jen pro čtení:</span><span class="sxs-lookup"><span data-stu-id="13e25-129">You can also use this syntax for read-only properties:</span></span>

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="13e25-130">Změna existujícího člena na člen Expression těle je [binární kompatibilní změna](version-update-considerations.md#binary-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="13e25-130">Changing an existing member to an expression bodied member is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="using-static"></a><span data-ttu-id="13e25-131">Použití static</span><span class="sxs-lookup"><span data-stu-id="13e25-131">using static</span></span>

<span data-ttu-id="13e25-132">*Použití statického* rozšíření umožňuje importovat statické metody jedné třídy.</span><span class="sxs-lookup"><span data-stu-id="13e25-132">The *using static* enhancement enables you to import the static methods of a single class.</span></span> <span data-ttu-id="13e25-133">Určíte třídu, kterou používáte:</span><span class="sxs-lookup"><span data-stu-id="13e25-133">You specify the class you're using:</span></span>

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<span data-ttu-id="13e25-134"><xref:System.Math> Neobsahuje žádné metody instance.</span><span class="sxs-lookup"><span data-stu-id="13e25-134">The <xref:System.Math> does not contain any instance methods.</span></span> <span data-ttu-id="13e25-135">Můžete také použít `using static` k importu statických metod třídy, které mají jak statické, tak metody instance.</span><span class="sxs-lookup"><span data-stu-id="13e25-135">You can also use `using static` to import a class' static methods for a class that has both static and instance methods.</span></span> <span data-ttu-id="13e25-136">Jedním z nejužitečnějších příkladů je <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="13e25-136">One of the most useful examples is <xref:System.String>:</span></span>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> <span data-ttu-id="13e25-137">`System.String` V příkazu static using je nutné použít plně kvalifikovaný název třídy.</span><span class="sxs-lookup"><span data-stu-id="13e25-137">You must use the fully qualified class name, `System.String`  in a static using statement.</span></span>  <span data-ttu-id="13e25-138">Místo toho se `string` klíčové slovo nedá použít.</span><span class="sxs-lookup"><span data-stu-id="13e25-138">You cannot use the `string` keyword instead.</span></span>

<span data-ttu-id="13e25-139">Při importu z `static using` příkazu jsou metody rozšíření v oboru pouze při volání pomocí syntaxe volání metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="13e25-139">When imported from a `static using` statement, extension methods are only in scope when called using the extension method invocation syntax.</span></span> <span data-ttu-id="13e25-140">Nejsou v oboru, který je volán jako statická metoda.</span><span class="sxs-lookup"><span data-stu-id="13e25-140">They aren't in scope when called as a static method.</span></span> <span data-ttu-id="13e25-141">Často se to zobrazí v dotazech LINQ.</span><span class="sxs-lookup"><span data-stu-id="13e25-141">You'll often see this in LINQ queries.</span></span> <span data-ttu-id="13e25-142">Můžete importovat vzor LINQ importem <xref:System.Linq.Enumerable>, nebo. <xref:System.Linq.Queryable></span><span class="sxs-lookup"><span data-stu-id="13e25-142">You can import the LINQ pattern by importing <xref:System.Linq.Enumerable>, or <xref:System.Linq.Queryable>.</span></span>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

<span data-ttu-id="13e25-143">Metody rozšíření se obvykle volají pomocí výrazů volání rozšiřujících metod.</span><span class="sxs-lookup"><span data-stu-id="13e25-143">You typically call extension methods using extension method invocation expressions.</span></span> <span data-ttu-id="13e25-144">Přidání názvu třídy ve výjimečném případě, kdy je zavoláte pomocí syntaxe volání statické metody, řeší nejednoznačnost.</span><span class="sxs-lookup"><span data-stu-id="13e25-144">Adding the class name in the rare case where you call them using static method call syntax resolves ambiguity.</span></span>

<span data-ttu-id="13e25-145">`static using` Direktiva také importuje všechny vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="13e25-145">The `static using` directive also imports any nested types.</span></span> <span data-ttu-id="13e25-146">Na všechny vnořené typy můžete odkazovat bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="13e25-146">You can reference any nested types without qualification.</span></span>

## <a name="null-conditional-operators"></a><span data-ttu-id="13e25-147">Podmíněné operátory s hodnotou null</span><span class="sxs-lookup"><span data-stu-id="13e25-147">Null-conditional operators</span></span>

<span data-ttu-id="13e25-148">*Podmíněný operátor s hodnotou null* zpřístupňuje v hodnotě null kontroly mnohem jednodušší a kapalin.</span><span class="sxs-lookup"><span data-stu-id="13e25-148">The *null conditional operator* makes null checks much easier and fluid.</span></span> <span data-ttu-id="13e25-149">Nahraďte přístup `.` členů pomocí `?.`:</span><span class="sxs-lookup"><span data-stu-id="13e25-149">Replace the member access `.` with `?.`:</span></span>

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

<span data-ttu-id="13e25-150">V předchozím příkladu je proměnná `first` přiřazena `null` , pokud je `null`objekt Person.</span><span class="sxs-lookup"><span data-stu-id="13e25-150">In the preceding example, the variable `first` is assigned `null` if the person object is `null`.</span></span> <span data-ttu-id="13e25-151">V opačném případě se mu přiřadí hodnota `FirstName` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="13e25-151">Otherwise, it is assigned the value of the `FirstName` property.</span></span> <span data-ttu-id="13e25-152">Co je nejdůležitější `?.` , znamená to, že tento řádek kódu `NullReferenceException` negeneruje, pokud `person` je `null`proměnná.</span><span class="sxs-lookup"><span data-stu-id="13e25-152">Most importantly, the `?.` means that this line of code doesn't generate a `NullReferenceException` if the `person` variable is `null`.</span></span> <span data-ttu-id="13e25-153">Místo toho se jedná o krátkodobé okruhy `null`a vrátí.</span><span class="sxs-lookup"><span data-stu-id="13e25-153">Instead, it short-circuits and returns `null`.</span></span> <span data-ttu-id="13e25-154">Pro přístup k poli nebo indexeru můžete použít také podmíněný operátor s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="13e25-154">You can also use a null conditional operator for array or indexer access.</span></span> <span data-ttu-id="13e25-155">Nahraďte `[]` výrazem vindexu.`?[]`</span><span class="sxs-lookup"><span data-stu-id="13e25-155">Replace `[]` with `?[]` in the index expression.</span></span>

<span data-ttu-id="13e25-156">Následující výraz vrátí `string`, bez ohledu na `person`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="13e25-156">The following expression returns a `string`, regardless of the value of `person`.</span></span> <span data-ttu-id="13e25-157">Tento konstruktor se často používá s operátorem sloučení s *hodnotou null* k přiřazení výchozích hodnot, pokud je `null`jedna z vlastností.</span><span class="sxs-lookup"><span data-stu-id="13e25-157">You often use this construct with the *null coalescing* operator to assign default values when one of the properties is `null`.</span></span> <span data-ttu-id="13e25-158">Při krátkých okruhech výrazu je vrácená `null` hodnota zadána, aby odpovídala celému výrazu.</span><span class="sxs-lookup"><span data-stu-id="13e25-158">When the expression short-circuits, the `null` value returned is typed to match the full expression.</span></span>

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

<span data-ttu-id="13e25-159">Můžete také použít `?.` k podmíněnému vyvolání metod.</span><span class="sxs-lookup"><span data-stu-id="13e25-159">You can also use `?.` to conditionally invoke methods.</span></span> <span data-ttu-id="13e25-160">Nejběžnějším použitím členských funkcí s podmíněným operátorem s hodnotou null je bezpečné vyvolání delegátů (nebo obslužných rutin událostí `null`), které mohou být.</span><span class="sxs-lookup"><span data-stu-id="13e25-160">The most common use of member functions  with the null conditional operator is to safely invoke delegates (or event handlers) that may be `null`.</span></span>  <span data-ttu-id="13e25-161">`Invoke` Metodu delegáta zavoláte `?.` pomocí operátoru pro přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="13e25-161">You'll call the delegate's `Invoke` method using the `?.` operator to access the member.</span></span> <span data-ttu-id="13e25-162">Příklad najdete v článku [vzory delegátů](../delegates-patterns.md#handling-null-delegates) .</span><span class="sxs-lookup"><span data-stu-id="13e25-162">You can see an example in the [delegate patterns](../delegates-patterns.md#handling-null-delegates) article.</span></span>

<span data-ttu-id="13e25-163">Pravidla `?.` operátora zajišťují, že levá strana operátoru je vyhodnocena pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="13e25-163">The rules of the `?.` operator ensure that the left-hand side of the operator is evaluated only once.</span></span> <span data-ttu-id="13e25-164">Umožňuje mnoho idiomy, včetně následujícího příkladu, pomocí obslužných rutin událostí:</span><span class="sxs-lookup"><span data-stu-id="13e25-164">It enables many idioms, including the following example using event handlers:</span></span>

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

<span data-ttu-id="13e25-165">Zajistěte, aby byla levá strana vyhodnocována pouze jednou, a umožňuje použít libovolný výraz, včetně volání metody, na levé straně`?.`</span><span class="sxs-lookup"><span data-stu-id="13e25-165">Ensuring that the left side is evaluated only once also enables you to use any expression, including method calls, on the left side of the `?.`</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="13e25-166">Interpolace řetězců</span><span class="sxs-lookup"><span data-stu-id="13e25-166">String interpolation</span></span>

<span data-ttu-id="13e25-167">S C# 6, nová funkce [interpolace řetězce](../language-reference/tokens/interpolated.md) umožňuje vkládat výrazy do řetězce.</span><span class="sxs-lookup"><span data-stu-id="13e25-167">With C# 6, the new [string interpolation](../language-reference/tokens/interpolated.md) feature enables you to embed expressions in a string.</span></span> <span data-ttu-id="13e25-168">Jednoduše se dotvářte do `$`řetězce a používejte výrazy `{` mezi `}` a místo pořadových čísel:</span><span class="sxs-lookup"><span data-stu-id="13e25-168">Simply preface the string with `$`and use expressions between `{` and `}` instead of ordinals:</span></span>

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="13e25-169">Tento příklad používá vlastnosti pro substituované výrazy.</span><span class="sxs-lookup"><span data-stu-id="13e25-169">This example uses properties for the substituted expressions.</span></span> <span data-ttu-id="13e25-170">Můžete použít libovolný výraz.</span><span class="sxs-lookup"><span data-stu-id="13e25-170">You can use any expression.</span></span> <span data-ttu-id="13e25-171">Jako součást interpolace můžete například vypočítat průměrnou hodnotu typu "Student 's".</span><span class="sxs-lookup"><span data-stu-id="13e25-171">For example, you could compute a student's grade point average as part of the interpolation:</span></span>

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

<span data-ttu-id="13e25-172">Předchozí řádek kódu formátuje hodnotu `Grades.Average()` jako číslo s plovoucí desetinnou čárkou se dvěma desetinnými místy.</span><span class="sxs-lookup"><span data-stu-id="13e25-172">The preceding line of code formats the value for `Grades.Average()` as a floating-point number with two decimal places.</span></span>

<span data-ttu-id="13e25-173">Často může být nutné zformátovat řetězec vytvořený pomocí konkrétní jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="13e25-173">Often, you may need to format the string produced using a specific culture.</span></span> <span data-ttu-id="13e25-174">Můžete použít fakt, že objekt vytvořený pomocí interpolace řetězce lze implicitně převést na <xref:System.FormattableString?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="13e25-174">You use the fact that the object produced by a string interpolation can be implicitly converted to <xref:System.FormattableString?displayProperty=nameWithType>.</span></span> <span data-ttu-id="13e25-175"><xref:System.FormattableString> Instance obsahuje složený řetězec formátu a výsledky vyhodnocení výrazů před jejich převodem na řetězce.</span><span class="sxs-lookup"><span data-stu-id="13e25-175">The <xref:System.FormattableString> instance contains the composite format string and the results of evaluating the expressions before converting them to strings.</span></span> <span data-ttu-id="13e25-176"><xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> Použijte metodu k určení jazykové verze při formátování řetězce.</span><span class="sxs-lookup"><span data-stu-id="13e25-176">Use the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method to specify the culture when formatting a string.</span></span> <span data-ttu-id="13e25-177">Následující příklad vytvoří řetězec pomocí jazykové verze německé (de-DE-DE).</span><span class="sxs-lookup"><span data-stu-id="13e25-177">The following example produces a string using the German (de-DE) culture.</span></span> <span data-ttu-id="13e25-178">(Ve výchozím nastavení německá jazyková verze používá znak "," pro oddělovač desetinných míst a znak "." jako oddělovač tisíců.)</span><span class="sxs-lookup"><span data-stu-id="13e25-178">(By default, the German culture uses the ',' character for the decimal separator, and the '.' character as the thousands separator.)</span></span>

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

<span data-ttu-id="13e25-179">Chcete-li začít s interpolací řetězců, přečtěte si článek o [interpolaci řetězce C# v](../tutorials/exploration/interpolated-strings.yml) interaktivním kurzu, o [interpolaci řetězce](../language-reference/tokens/interpolated.md) a o [interpolaci řetězce v C# ](../tutorials/string-interpolation.md) kurzu.</span><span class="sxs-lookup"><span data-stu-id="13e25-179">To get started with string interpolation, see the [String interpolation in C#](../tutorials/exploration/interpolated-strings.yml) interactive tutorial, the [String interpolation](../language-reference/tokens/interpolated.md) article, and the [String interpolation in C#](../tutorials/string-interpolation.md) tutorial.</span></span>

## <a name="exception-filters"></a><span data-ttu-id="13e25-180">Filtry výjimek</span><span class="sxs-lookup"><span data-stu-id="13e25-180">Exception filters</span></span>

<span data-ttu-id="13e25-181">*Filtry výjimek* jsou klauzule, které určují, kdy se má daná klauzule catch použít.</span><span class="sxs-lookup"><span data-stu-id="13e25-181">*Exception Filters* are clauses that determine when a given catch clause should be applied.</span></span> <span data-ttu-id="13e25-182">Pokud je výraz použitý pro filtr výjimek vyhodnocen `true`jako, klauzule catch provede své normální zpracování na výjimku.</span><span class="sxs-lookup"><span data-stu-id="13e25-182">If the expression used for an exception filter evaluates to `true`, the catch clause performs its normal processing on an exception.</span></span> <span data-ttu-id="13e25-183">Pokud se výraz vyhodnotí `false`jako, `catch` pak se klauzule přeskočí.</span><span class="sxs-lookup"><span data-stu-id="13e25-183">If the expression evaluates to `false`, then the `catch` clause is skipped.</span></span> <span data-ttu-id="13e25-184">Jedním z nich je prozkoumávat informace o výjimce k určení, `catch` zda klauzule může zpracovat výjimku:</span><span class="sxs-lookup"><span data-stu-id="13e25-184">One use is to examine information about an exception to determine if a `catch` clause can process the exception:</span></span>

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

## <a name="the-nameof-expression"></a><span data-ttu-id="13e25-185">`nameof` Výraz</span><span class="sxs-lookup"><span data-stu-id="13e25-185">The `nameof` expression</span></span>

<span data-ttu-id="13e25-186">Výraz [nameof](../language-reference/operators/nameof.md) se vyhodnocuje jako název symbolu.</span><span class="sxs-lookup"><span data-stu-id="13e25-186">The [nameof](../language-reference/operators/nameof.md) expression evaluates to the name of a symbol.</span></span> <span data-ttu-id="13e25-187">Je to skvělý způsob, jak získat nástroje, kdykoli potřebujete název proměnné, vlastnosti nebo pole členů.</span><span class="sxs-lookup"><span data-stu-id="13e25-187">It's a great way to get tools working whenever you need the name of a variable, a property, or a member field.</span></span> <span data-ttu-id="13e25-188">Jedním z nejběžnějších použití pro `nameof` je poskytnout název symbolu, který způsobil výjimku:</span><span class="sxs-lookup"><span data-stu-id="13e25-188">One of the most common uses for `nameof` is to provide the name of a symbol that caused an exception:</span></span>

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

<span data-ttu-id="13e25-189">Jiné použití je v aplikacích založených na jazyce XAML, `INotifyPropertyChanged` které implementují rozhraní:</span><span class="sxs-lookup"><span data-stu-id="13e25-189">Another use is with XAML-based applications that implement the `INotifyPropertyChanged` interface:</span></span>

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

## <a name="await-in-catch-and-finally-blocks"></a><span data-ttu-id="13e25-190">Očekává se v blocích catch a finally.</span><span class="sxs-lookup"><span data-stu-id="13e25-190">Await in Catch and Finally blocks</span></span>

<span data-ttu-id="13e25-191">C#5 bylo několik omezení, kde byste mohli umístit `await` výrazy.</span><span class="sxs-lookup"><span data-stu-id="13e25-191">C# 5 had several limitations around where you could place `await` expressions.</span></span> <span data-ttu-id="13e25-192">S C# 6 můžete teď použít `await` ve `catch` výrazech nebo `finally` .</span><span class="sxs-lookup"><span data-stu-id="13e25-192">With C# 6, you can now use `await` in `catch` or `finally` expressions.</span></span> <span data-ttu-id="13e25-193">Nejčastěji se používá při protokolování scénářů:</span><span class="sxs-lookup"><span data-stu-id="13e25-193">This is most often used with logging scenarios:</span></span>

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

<span data-ttu-id="13e25-194">Podrobnosti implementace pro přidání `await` podpory uvnitř `catch` klauzulí a `finally` zajišťují, že chování je konzistentní s chováním pro synchronní kód.</span><span class="sxs-lookup"><span data-stu-id="13e25-194">The implementation details for adding `await` support inside `catch` and `finally` clauses ensure that the behavior is consistent with the behavior for synchronous code.</span></span> <span data-ttu-id="13e25-195">Když kód spuštěný v `catch` klauzuli `finally` or vyvolá, vyhledá vhodnou `catch` klauzuli v dalším okolním bloku.</span><span class="sxs-lookup"><span data-stu-id="13e25-195">When code executed in a `catch` or `finally` clause throws, execution looks for a suitable `catch` clause in the next surrounding block.</span></span> <span data-ttu-id="13e25-196">Pokud byla zjištěna aktuální výjimka, dojde ke ztrátě této výjimky.</span><span class="sxs-lookup"><span data-stu-id="13e25-196">If there was a current exception, that exception is lost.</span></span> <span data-ttu-id="13e25-197">Totéž se stane s očekávanými výrazy v `catch` klauzulích a `finally` : je `catch` prohledána vhodná a aktuální výjimka, pokud nějaká existuje.</span><span class="sxs-lookup"><span data-stu-id="13e25-197">The same happens with awaited expressions in `catch` and `finally` clauses: a suitable `catch` is searched for, and the current exception, if any, is lost.</span></span>  

> [!NOTE]
> <span data-ttu-id="13e25-198">Toto chování je důvodem pro pečlivou psaní `catch` a `finally` klauzulí, aby nedocházelo k zavlečení nových výjimek.</span><span class="sxs-lookup"><span data-stu-id="13e25-198">This behavior is the reason it's recommended to write `catch` and `finally` clauses carefully, to avoid introducing new exceptions.</span></span>

## <a name="initialize-associative-collections-using-indexers"></a><span data-ttu-id="13e25-199">Inicializace asociativních kolekcí pomocí indexerů</span><span class="sxs-lookup"><span data-stu-id="13e25-199">Initialize associative collections using indexers</span></span>

<span data-ttu-id="13e25-200">*Inicializátory indexu* jsou jednou ze dvou funkcí, které vytvářejí inicializátory kolekce více konzistentní s využitím indexu.</span><span class="sxs-lookup"><span data-stu-id="13e25-200">*Index Initializers* is one of two features that make collection initializers more consistent with index usage.</span></span> <span data-ttu-id="13e25-201">V dřívějších verzích C#nástroje můžete použít inicializátory *kolekce* s kolekcemi stylu sekvence, včetně <xref:System.Collections.Generic.Dictionary%602>, přidáním složených závorek kolem párů klíč-hodnota:</span><span class="sxs-lookup"><span data-stu-id="13e25-201">In earlier releases of C#, you could use *collection initializers* with sequence style collections, including <xref:System.Collections.Generic.Dictionary%602>, by adding braces around key and value pairs:</span></span>

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#CollectionInitializer)]

<span data-ttu-id="13e25-202">Můžete je použít s <xref:System.Collections.Generic.Dictionary%602> kolekcemi a jinými typy, kde přístupná `Add` Metoda akceptuje více než jeden argument.</span><span class="sxs-lookup"><span data-stu-id="13e25-202">You can use them with <xref:System.Collections.Generic.Dictionary%602> collections and other types where the accessible `Add` method accepts more than one argument.</span></span> <span data-ttu-id="13e25-203">Nová syntaxe podporuje přiřazení pomocí indexu do kolekce:</span><span class="sxs-lookup"><span data-stu-id="13e25-203">The new syntax supports assignment using an index into the collection:</span></span>

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

<span data-ttu-id="13e25-204">Tato funkce znamená, že asociativní kontejnery lze inicializovat pomocí syntaxe podobně jako u kontejnerů sekvence pro několik verzí.</span><span class="sxs-lookup"><span data-stu-id="13e25-204">This feature means that associative containers can be initialized using syntax similar to what's been in place for sequence containers for several versions.</span></span>

## <a name="extension-add-methods-in-collection-initializers"></a><span data-ttu-id="13e25-205">Metody `Add` rozšíření v inicializátorech kolekcí</span><span class="sxs-lookup"><span data-stu-id="13e25-205">Extension `Add` methods in collection initializers</span></span>

<span data-ttu-id="13e25-206">Další funkcí, která usnadňuje inicializaci kolekce, je možnost použít *metodu rozšíření* pro `Add` metodu.</span><span class="sxs-lookup"><span data-stu-id="13e25-206">Another feature that makes collection initialization easier is the ability to use an *extension method* for the `Add` method.</span></span> <span data-ttu-id="13e25-207">Tato funkce byla přidána pro paritu s Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="13e25-207">This feature was added for parity with Visual Basic.</span></span> <span data-ttu-id="13e25-208">Tato funkce je nejužitečnější, když máte vlastní třídu kolekce, která má metodu s jiným názvem pro sémantické přidání nových položek.</span><span class="sxs-lookup"><span data-stu-id="13e25-208">The feature is most useful when you have a custom collection class that has a method with a different name to semantically add new items.</span></span>

## <a name="improved-overload-resolution"></a><span data-ttu-id="13e25-209">Vylepšené rozlišení přetížení</span><span class="sxs-lookup"><span data-stu-id="13e25-209">Improved overload resolution</span></span>

<span data-ttu-id="13e25-210">Tato poslední funkce je ta, kterou si pravděpodobně nevšimnete.</span><span class="sxs-lookup"><span data-stu-id="13e25-210">This last feature is one you probably won't notice.</span></span> <span data-ttu-id="13e25-211">Byly zjištěny konstrukce, kde předchozí verze C# kompilátoru mohla najít některá volání metod zahrnující výrazy lambda nejednoznačná.</span><span class="sxs-lookup"><span data-stu-id="13e25-211">There were constructs where the previous version of the C# compiler may have found some method calls involving lambda expressions ambiguous.</span></span> <span data-ttu-id="13e25-212">Zvažte tuto metodu:</span><span class="sxs-lookup"><span data-stu-id="13e25-212">Consider this method:</span></span>

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

<span data-ttu-id="13e25-213">V dřívějších verzích systému C#volání této metody pomocí syntaxe skupiny metod selže:</span><span class="sxs-lookup"><span data-stu-id="13e25-213">In earlier versions of C#, calling that method using the method group syntax would fail:</span></span>

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]

<span data-ttu-id="13e25-214">Předchozí kompilátor nemůže správně rozlišovat mezi `Task.Run(Action)` a. `Task.Run(Func<Task>())`</span><span class="sxs-lookup"><span data-stu-id="13e25-214">The earlier compiler couldn't distinguish correctly between `Task.Run(Action)` and `Task.Run(Func<Task>())`.</span></span> <span data-ttu-id="13e25-215">V předchozích verzích byste měli použít výraz lambda jako argument:</span><span class="sxs-lookup"><span data-stu-id="13e25-215">In previous versions, you'd need to use a lambda expression as an argument:</span></span>

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

<span data-ttu-id="13e25-216">C# 6 kompilátor správně určí, že `Task.Run(Func<Task>())` je lepší volbou.</span><span class="sxs-lookup"><span data-stu-id="13e25-216">The C# 6 compiler correctly determines that `Task.Run(Func<Task>())` is a better choice.</span></span>

### <a name="deterministic-compiler-output"></a><span data-ttu-id="13e25-217">Deterministický výstup kompilátoru</span><span class="sxs-lookup"><span data-stu-id="13e25-217">Deterministic compiler output</span></span>

<span data-ttu-id="13e25-218">`-deterministic` Možnost instruuje kompilátor, aby vytvořil stejné výstupní sestavení typu Byte-Byte pro následná kompilace stejných zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="13e25-218">The `-deterministic` option instructs the compiler to produce a byte-for-byte identical output assembly for successive compilations of the same source files.</span></span>

<span data-ttu-id="13e25-219">Ve výchozím nastavení každá kompilace vytvoří jedinečný výstup v každé kompilaci.</span><span class="sxs-lookup"><span data-stu-id="13e25-219">By default, every compilation produces unique output on each compilation.</span></span> <span data-ttu-id="13e25-220">Kompilátor přidá časové razítko a identifikátor GUID vygenerovaný z náhodných čísel.</span><span class="sxs-lookup"><span data-stu-id="13e25-220">The compiler adds a timestamp, and a GUID generated from random numbers.</span></span> <span data-ttu-id="13e25-221">Tuto možnost použijete, pokud chcete porovnat výstup bajtů za bajt, aby se zajistila konzistence napříč sestaveními.</span><span class="sxs-lookup"><span data-stu-id="13e25-221">You use this option if you want to compare the byte-for-byte output to ensure consistency across builds.</span></span>

<span data-ttu-id="13e25-222">Další informace naleznete v článku o [Možnosti deterministického kompilátoru](../language-reference/compiler-options/deterministic-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="13e25-222">For more information, see the [-deterministic compiler option](../language-reference/compiler-options/deterministic-compiler-option.md) article.</span></span>
