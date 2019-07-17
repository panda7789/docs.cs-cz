---
title: Co je nového v jazyce C# 6 – Průvodce v C#
description: Informace o nových funkcích v jazyce C# verze 6
ms.date: 12/12/2018
ms.openlocfilehash: 49247109bd1acbf697f5700b5cfe9a2b85393b2c
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68235724"
---
# <a name="whats-new-in-c-6"></a><span data-ttu-id="95648-103">Co je nového v jazyce C# 6</span><span class="sxs-lookup"><span data-stu-id="95648-103">What's New in C# 6</span></span>

<span data-ttu-id="95648-104">C# 6.0 vydání obsahovala řadu funkcí, které zvyšují produktivitu pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="95648-104">The 6.0 release of C# contained many features that improve productivity for developers.</span></span> <span data-ttu-id="95648-105">Celkový efekt z těchto funkcí je, že napíšete stručnější kód, který je také lépe čitelný.</span><span class="sxs-lookup"><span data-stu-id="95648-105">The overall effect of these features is that you write more concise code that is also more readable.</span></span> <span data-ttu-id="95648-106">Syntaxe obsahuje méně procedury pro mnoho běžných postupech.</span><span class="sxs-lookup"><span data-stu-id="95648-106">The syntax contains less ceremony for many common practices.</span></span> <span data-ttu-id="95648-107">Je snazší zjistit záměr návrhu s méně procedury.</span><span class="sxs-lookup"><span data-stu-id="95648-107">It's easier to see the design intent with less ceremony.</span></span> <span data-ttu-id="95648-108">Přečtěte si tyto funkce dobře, a budete produktivnější a napsat kód lépe čitelný.</span><span class="sxs-lookup"><span data-stu-id="95648-108">Learn these features well, and you'll be more productive and write more readable code.</span></span> <span data-ttu-id="95648-109">Více můžete soustředit na funkce než na konstrukce jazyka.</span><span class="sxs-lookup"><span data-stu-id="95648-109">You can concentrate more on your features than on the constructs of the language.</span></span>

<span data-ttu-id="95648-110">Zbývající část tohoto článku poskytuje přehled o každé z těchto funkcí s odkazem k prozkoumání jednotlivých funkcí.</span><span class="sxs-lookup"><span data-stu-id="95648-110">The rest of this article provides an overview of each of these features, with a link to explore each feature.</span></span> <span data-ttu-id="95648-111">Můžete si taky prostudovat funkce [interaktivní zkoumání na C# 6](../tutorials/exploration/csharp-6.yml) v části kurzy.</span><span class="sxs-lookup"><span data-stu-id="95648-111">You can also explore the features in an [interactive exploration on C# 6](../tutorials/exploration/csharp-6.yml) in the tutorials section.</span></span>

## <a name="read-only-auto-properties"></a><span data-ttu-id="95648-112">Auto vlastnosti jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="95648-112">Read-only auto-properties</span></span>

<span data-ttu-id="95648-113">*Auto vlastnosti jen pro čtení* poskytují stručnější syntaxi, vytvořte neměnný typy.</span><span class="sxs-lookup"><span data-stu-id="95648-113">*Read-only auto-properties* provide a more concise syntax to create immutable types.</span></span> <span data-ttu-id="95648-114">Deklarovat vlastnost automaticky s pouze přístupový objekt get:</span><span class="sxs-lookup"><span data-stu-id="95648-114">You declare the auto-property with only a get accessor:</span></span>

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

<span data-ttu-id="95648-115">`FirstName` a `LastName` vlastnosti lze nastavit pouze v těle konstruktoru:</span><span class="sxs-lookup"><span data-stu-id="95648-115">The `FirstName` and `LastName` properties can be set only in the body of a constructor:</span></span>

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

<span data-ttu-id="95648-116">Pokoušíte se nastavit `LastName` v jiné metody generuje `CS0200` Chyba kompilace:</span><span class="sxs-lookup"><span data-stu-id="95648-116">Trying to set `LastName` in another method generates a `CS0200` compilation error:</span></span>

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

<span data-ttu-id="95648-117">Tato funkce umožňuje podporu opravdový jazyk pro vytváření typů neměnných a používá syntaxi automatickou vlastnost stručnějším a pohodlné.</span><span class="sxs-lookup"><span data-stu-id="95648-117">This feature enables true language support for creating immutable types and uses the more concise and convenient auto-property syntax.</span></span>

<span data-ttu-id="95648-118">Pokud přidáte tuto syntaxi neodebere dostupná metoda, je [binární kompatibilní změnu](version-update-considerations.md#binary-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="95648-118">If adding this syntax doesn't remove an accessible method, it's a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="auto-property-initializers"></a><span data-ttu-id="95648-119">Inicializátory automatickou vlastnost</span><span class="sxs-lookup"><span data-stu-id="95648-119">Auto-property initializers</span></span>

<span data-ttu-id="95648-120">*Inicializátory automatickou vlastnost* umožňuje deklarovat počáteční hodnotu pro automatickou vlastnost jako součást deklarace vlastností.</span><span class="sxs-lookup"><span data-stu-id="95648-120">*Auto-property initializers* let you declare the initial value for an auto-property as part of the property declaration.</span></span>

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

<span data-ttu-id="95648-121">`Grades` Člen je inicializovaný, ve kterém je deklarována.</span><span class="sxs-lookup"><span data-stu-id="95648-121">The `Grades` member is initialized where it's declared.</span></span> <span data-ttu-id="95648-122">Který usnadňuje provedení inicializace přesně jednou.</span><span class="sxs-lookup"><span data-stu-id="95648-122">That makes it easier to perform the initialization exactly once.</span></span> <span data-ttu-id="95648-123">Inicializace je součástí deklaraci vlastnosti, což usnadňuje odpovídá přidělení úložiště pro veřejné rozhraní `Student` objekty.</span><span class="sxs-lookup"><span data-stu-id="95648-123">The initialization is part of the property declaration, making it easier to equate the storage allocation with the public interface for `Student` objects.</span></span>

## <a name="expression-bodied-function-members"></a><span data-ttu-id="95648-124">Členové tvoření výrazy – funkce</span><span class="sxs-lookup"><span data-stu-id="95648-124">Expression-bodied function members</span></span>

<span data-ttu-id="95648-125">Mnoho členů, které napíšete jsou jednotlivé příkazy, které mohou být jednoho výrazy.</span><span class="sxs-lookup"><span data-stu-id="95648-125">Many members that you write are single statements that could be single expressions.</span></span> <span data-ttu-id="95648-126">Místo toho zapisovat na člena s výrazem v těle.</span><span class="sxs-lookup"><span data-stu-id="95648-126">Write an expression-bodied member instead.</span></span> <span data-ttu-id="95648-127">Funguje to pro metody a vlastnosti jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="95648-127">It works for methods and read-only properties.</span></span> <span data-ttu-id="95648-128">Například přepsání `ToString()` často je vynikající kandidát:</span><span class="sxs-lookup"><span data-stu-id="95648-128">For example, an override of `ToString()` is often a great candidate:</span></span>

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

<span data-ttu-id="95648-129">Pro vlastnosti jen pro čtení můžete také použít tuto syntaxi:</span><span class="sxs-lookup"><span data-stu-id="95648-129">You can also use this syntax for read-only properties:</span></span>

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="95648-130">Změna existujícího člena pro člena vozidlo výrazu je [binární kompatibilní změnu](version-update-considerations.md#binary-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="95648-130">Changing an existing member to an expression bodied member is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="using-static"></a><span data-ttu-id="95648-131">Pomocí statické</span><span class="sxs-lookup"><span data-stu-id="95648-131">using static</span></span>

<span data-ttu-id="95648-132">*Pomocí statické* vylepšení umožňuje importovat statické metody jednu třídu.</span><span class="sxs-lookup"><span data-stu-id="95648-132">The *using static* enhancement enables you to import the static methods of a single class.</span></span> <span data-ttu-id="95648-133">Můžete zadat třídu, kterou používáte:</span><span class="sxs-lookup"><span data-stu-id="95648-133">You specify the class you're using:</span></span>

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<span data-ttu-id="95648-134"><xref:System.Math> Neobsahuje žádné metody instance.</span><span class="sxs-lookup"><span data-stu-id="95648-134">The <xref:System.Math> does not contain any instance methods.</span></span> <span data-ttu-id="95648-135">Můžete také použít `using static` importovat třídy statické metody pro třídu, která má statické a metody instance.</span><span class="sxs-lookup"><span data-stu-id="95648-135">You can also use `using static` to import a class' static methods for a class that has both static and instance methods.</span></span> <span data-ttu-id="95648-136">Jedním z nejužitečnějších příkladů je <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="95648-136">One of the most useful examples is <xref:System.String>:</span></span>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> <span data-ttu-id="95648-137">Musíte použít plně kvalifikovaný název třídy, `System.String` v statický příkaz using.</span><span class="sxs-lookup"><span data-stu-id="95648-137">You must use the fully qualified class name, `System.String`  in a static using statement.</span></span>  <span data-ttu-id="95648-138">Nelze použít `string` – klíčové slovo místo.</span><span class="sxs-lookup"><span data-stu-id="95648-138">You cannot use the `string` keyword instead.</span></span>

<span data-ttu-id="95648-139">Při importu z `static using` , rozšiřující metody jsou pouze v oboru při volány pomocí syntaxe volání metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="95648-139">When imported from a `static using` statement, extension methods are only in scope when called using the extension method invocation syntax.</span></span> <span data-ttu-id="95648-140">Proto nejsou v oboru při volá jako statická metoda.</span><span class="sxs-lookup"><span data-stu-id="95648-140">They aren't in scope when called as a static method.</span></span> <span data-ttu-id="95648-141">To se často zobrazí v dotazech LINQ.</span><span class="sxs-lookup"><span data-stu-id="95648-141">You'll often see this in LINQ queries.</span></span> <span data-ttu-id="95648-142">Vzor LINQ můžete importovat pomocí importu <xref:System.Linq.Enumerable>, nebo <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="95648-142">You can import the LINQ pattern by importing <xref:System.Linq.Enumerable>, or <xref:System.Linq.Queryable>.</span></span>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

<span data-ttu-id="95648-143">Obvykle volání metody rozšíření používat výrazy typu invocation – metoda rozšíření.</span><span class="sxs-lookup"><span data-stu-id="95648-143">You typically call extension methods using extension method invocation expressions.</span></span> <span data-ttu-id="95648-144">Přidání názvu třídy ve výjimečných případech, kde je volat pomocí volání statické metody řeší nejednoznačnost syntaxe.</span><span class="sxs-lookup"><span data-stu-id="95648-144">Adding the class name in the rare case where you call them using static method call syntax resolves ambiguity.</span></span>

<span data-ttu-id="95648-145">`static using` Direktiva také importuje všechny vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="95648-145">The `static using` directive also imports any nested types.</span></span> <span data-ttu-id="95648-146">Můžete odkazovat na jakékoli vnořené typy bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="95648-146">You can reference any nested types without qualification.</span></span>

## <a name="null-conditional-operators"></a><span data-ttu-id="95648-147">Podmíněné operátory s Null</span><span class="sxs-lookup"><span data-stu-id="95648-147">Null-conditional operators</span></span>

<span data-ttu-id="95648-148">*Null podmiňovací operátor* mnohem jednodušší a plynulé provede kontroly hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="95648-148">The *null conditional operator* makes null checks much easier and fluid.</span></span> <span data-ttu-id="95648-149">Nahraďte přístup ke členu `.` s `?.`:</span><span class="sxs-lookup"><span data-stu-id="95648-149">Replace the member access `.` with `?.`:</span></span>

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

<span data-ttu-id="95648-150">V předchozím příkladu je proměnná `first` je přiřazena `null` Pokud objekt osoba `null`.</span><span class="sxs-lookup"><span data-stu-id="95648-150">In the preceding example, the variable `first` is assigned `null` if the person object is `null`.</span></span> <span data-ttu-id="95648-151">V opačném případě je přiřazena hodnota `FirstName` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="95648-151">Otherwise, it is assigned the value of the `FirstName` property.</span></span> <span data-ttu-id="95648-152">Co je nejdůležitější `?.` znamená, že negeneruje tento řádek kódu `NullReferenceException` Pokud `person` proměnná je `null`.</span><span class="sxs-lookup"><span data-stu-id="95648-152">Most importantly, the `?.` means that this line of code doesn't generate a `NullReferenceException` if the `person` variable is `null`.</span></span> <span data-ttu-id="95648-153">Místo toho zkratům a vrátí `null`.</span><span class="sxs-lookup"><span data-stu-id="95648-153">Instead, it short-circuits and returns `null`.</span></span> <span data-ttu-id="95648-154">Můžete také null podmíněný operátor pro přístup k poli nebo indexeru.</span><span class="sxs-lookup"><span data-stu-id="95648-154">You can also use a null conditional operator for array or indexer access.</span></span> <span data-ttu-id="95648-155">Nahraďte `[]` s `?[]` ve výrazu indexu.</span><span class="sxs-lookup"><span data-stu-id="95648-155">Replace `[]` with `?[]` in the index expression.</span></span>

<span data-ttu-id="95648-156">Vrátí následující výraz `string`bez ohledu hodnotu `person`.</span><span class="sxs-lookup"><span data-stu-id="95648-156">The following expression returns a `string`, regardless of the value of `person`.</span></span> <span data-ttu-id="95648-157">Tento konstruktor se často používají *nulové sloučení* operátor přiřazení výchozí hodnoty, pokud jedna z vlastností `null`.</span><span class="sxs-lookup"><span data-stu-id="95648-157">You often use this construct with the *null coalescing* operator to assign default values when one of the properties is `null`.</span></span> <span data-ttu-id="95648-158">Pokud výraz zkratům, `null` vrácená hodnota je typu tak, aby odpovídaly úplného výrazu.</span><span class="sxs-lookup"><span data-stu-id="95648-158">When the expression short-circuits, the `null` value returned is typed to match the full expression.</span></span>

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

<span data-ttu-id="95648-159">Můžete také použít `?.` podmíněně volat metody.</span><span class="sxs-lookup"><span data-stu-id="95648-159">You can also use `?.` to conditionally invoke methods.</span></span> <span data-ttu-id="95648-160">Nejběžnější použití nástroje členské funkce s hodnotou null podmíněný operátor je pro bezpečné vyvolání delegátů (nebo obslužné rutiny událostí), které mohou být `null`.</span><span class="sxs-lookup"><span data-stu-id="95648-160">The most common use of member functions  with the null conditional operator is to safely invoke delegates (or event handlers) that may be `null`.</span></span>  <span data-ttu-id="95648-161">Bude volání delegáta `Invoke` pomocí metody `?.` operátor pro přístup k členu.</span><span class="sxs-lookup"><span data-stu-id="95648-161">You'll call the delegate's `Invoke` method using the `?.` operator to access the member.</span></span> <span data-ttu-id="95648-162">Můžete zobrazit příklad v [delegovat vzory](../delegates-patterns.md#handling-null-delegates) článku.</span><span class="sxs-lookup"><span data-stu-id="95648-162">You can see an example in the [delegate patterns](../delegates-patterns.md#handling-null-delegates) article.</span></span>

<span data-ttu-id="95648-163">Pravidla `?.` operátor Ujistěte se, že levá strana operátoru je vyhodnocen pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="95648-163">The rules of the `?.` operator ensure that the left-hand side of the operator is evaluated only once.</span></span> <span data-ttu-id="95648-164">Umožňuje mnoho idiomy, včetně následující příklad pomocí obslužných rutin událostí:</span><span class="sxs-lookup"><span data-stu-id="95648-164">It enables many idioms, including the following example using event handlers:</span></span>

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

<span data-ttu-id="95648-165">Zajištění, že na levé straně je vyhodnocen pouze jednou můžete také použít libovolný výraz, včetně volání metod na levé straně `?.`</span><span class="sxs-lookup"><span data-stu-id="95648-165">Ensuring that the left side is evaluated only once also enables you to use any expression, including method calls, on the left side of the `?.`</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="95648-166">Interpolace řetězců</span><span class="sxs-lookup"><span data-stu-id="95648-166">String interpolation</span></span>

<span data-ttu-id="95648-167">S C# 6, nové [interpolace](../language-reference/tokens/interpolated.md) funkce umožňuje vložení výrazů do řetězce.</span><span class="sxs-lookup"><span data-stu-id="95648-167">With C# 6, the new [string interpolation](../language-reference/tokens/interpolated.md) feature enables you to embed expressions in a string.</span></span> <span data-ttu-id="95648-168">Jednoduše začínat řetězec s `$`a používat výrazy mezi `{` a `}` místo řadové číslovky:</span><span class="sxs-lookup"><span data-stu-id="95648-168">Simply preface the string with `$`and use expressions between `{` and `}` instead of ordinals:</span></span>

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="95648-169">Tento příklad používá vlastnosti pro nahrazeny výrazy.</span><span class="sxs-lookup"><span data-stu-id="95648-169">This example uses properties for the substituted expressions.</span></span> <span data-ttu-id="95648-170">Můžete použít libovolný výraz.</span><span class="sxs-lookup"><span data-stu-id="95648-170">You can use any expression.</span></span> <span data-ttu-id="95648-171">Například může vypočítat průměr student získal na podnikové úrovni jako součást interpolace:</span><span class="sxs-lookup"><span data-stu-id="95648-171">For example, you could compute a student's grade point average as part of the interpolation:</span></span>

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

<span data-ttu-id="95648-172">Naformátuje hodnotu pro předchozí řádek kódu `Grades.Average()` jako číslo s plovoucí desetinnou čárkou se dvěma desetinnými místy.</span><span class="sxs-lookup"><span data-stu-id="95648-172">The preceding line of code formats the value for `Grades.Average()` as a floating-point number with two decimal places.</span></span>

<span data-ttu-id="95648-173">Často je potřeba formátovací řetězec vytvořený pomocí konkrétní jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="95648-173">Often, you may need to format the string produced using a specific culture.</span></span> <span data-ttu-id="95648-174">Použít skutečnost, že objekt vytvořený testovaným interpolace řetězců lze implicitně převést na <xref:System.FormattableString?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="95648-174">You use the fact that the object produced by a string interpolation can be implicitly converted to <xref:System.FormattableString?displayProperty=nameWithType>.</span></span> <span data-ttu-id="95648-175"><xref:System.FormattableString> Instance obsahuje složeném formátovacím řetězci a výsledky vyhodnocování výrazů před převedením na řetězce.</span><span class="sxs-lookup"><span data-stu-id="95648-175">The <xref:System.FormattableString> instance contains the composite format string and the results of evaluating the expressions before converting them to strings.</span></span> <span data-ttu-id="95648-176">Použití <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> metoda zadat jazykovou verzi, při formátování řetězce.</span><span class="sxs-lookup"><span data-stu-id="95648-176">Use the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method to specify the culture when formatting a string.</span></span> <span data-ttu-id="95648-177">Následující příklad vytvoří řetězec za použití němčina (de-DE) jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="95648-177">The following example produces a string using the German (de-DE) culture.</span></span> <span data-ttu-id="95648-178">(Ve výchozím nastavení, Německá jazyková verze používá znak "," jako oddělovač desetinných míst a "." znak jako tisíců oddělovač.)</span><span class="sxs-lookup"><span data-stu-id="95648-178">(By default, the German culture uses the ',' character for the decimal separator, and the '.' character as the thousands separator.)</span></span>

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

<span data-ttu-id="95648-179">Začít s interpolace řetězců, přečtěte si článek [interpolace v C# ](../tutorials/exploration/interpolated-strings.yml) Interaktivní kurz, [interpolace řetězců](../language-reference/tokens/interpolated.md) článku a [interpolace v C# ](../tutorials/string-interpolation.md) kurzu.</span><span class="sxs-lookup"><span data-stu-id="95648-179">To get started with string interpolation, see the [String interpolation in C#](../tutorials/exploration/interpolated-strings.yml) interactive tutorial, the [String interpolation](../language-reference/tokens/interpolated.md) article, and the [String interpolation in C#](../tutorials/string-interpolation.md) tutorial.</span></span>

## <a name="exception-filters"></a><span data-ttu-id="95648-180">Filtry výjimek</span><span class="sxs-lookup"><span data-stu-id="95648-180">Exception filters</span></span>

<span data-ttu-id="95648-181">*Filtry výjimek* jsou klauzule, které určují, kdy by použít klauzuli catch. daný.</span><span class="sxs-lookup"><span data-stu-id="95648-181">*Exception Filters* are clauses that determine when a given catch clause should be applied.</span></span> <span data-ttu-id="95648-182">Pokud výraz použitý pro filtr výjimek vyhodnocuje na `true`, klauzule catch provádí běžného zpracování při výskytu výjimky.</span><span class="sxs-lookup"><span data-stu-id="95648-182">If the expression used for an exception filter evaluates to `true`, the catch clause performs its normal processing on an exception.</span></span> <span data-ttu-id="95648-183">Pokud je výraz vyhodnocen `false`, pak bude `catch` klauzule se přeskočí.</span><span class="sxs-lookup"><span data-stu-id="95648-183">If the expression evaluates to `false`, then the `catch` clause is skipped.</span></span> <span data-ttu-id="95648-184">Zjistit informace o výjimce k určení, zda je jedno použití `catch` klauzule může zpracovat výjimku:</span><span class="sxs-lookup"><span data-stu-id="95648-184">One use is to examine information about an exception to determine if a `catch` clause can process the exception:</span></span>

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

## <a name="the-nameof-expression"></a><span data-ttu-id="95648-185">`nameof` Výraz</span><span class="sxs-lookup"><span data-stu-id="95648-185">The `nameof` expression</span></span>

<span data-ttu-id="95648-186">[Nameof](../language-reference/operators/nameof.md) výraz vyhodnocen jako název symbolu.</span><span class="sxs-lookup"><span data-stu-id="95648-186">The [nameof](../language-reference/operators/nameof.md) expression evaluates to the name of a symbol.</span></span> <span data-ttu-id="95648-187">To je skvělý způsob, jak získat nástroje pracovat pokaždé, když budete potřebovat název proměnné, vlastnost nebo pole členů.</span><span class="sxs-lookup"><span data-stu-id="95648-187">It's a great way to get tools working whenever you need the name of a variable, a property, or a member field.</span></span> <span data-ttu-id="95648-188">Jeden z nejčastěji používaných používá pro `nameof` je k poskytnutí názvu symbolu, která způsobila výjimku:</span><span class="sxs-lookup"><span data-stu-id="95648-188">One of the most common uses for `nameof` is to provide the name of a symbol that caused an exception:</span></span>

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

<span data-ttu-id="95648-189">Další možností použití je aplikace založené na XAML, které implementují `INotifyPropertyChanged` rozhraní:</span><span class="sxs-lookup"><span data-stu-id="95648-189">Another use is with XAML-based applications that implement the `INotifyPropertyChanged` interface:</span></span>

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

## <a name="await-in-catch-and-finally-blocks"></a><span data-ttu-id="95648-190">Operátor await v Catch a blocích Finally</span><span class="sxs-lookup"><span data-stu-id="95648-190">Await in Catch and Finally blocks</span></span>

<span data-ttu-id="95648-191">C# 5 má několik omezení kde mohli byste umístit `await` výrazy.</span><span class="sxs-lookup"><span data-stu-id="95648-191">C# 5 had several limitations around where you could place `await` expressions.</span></span> <span data-ttu-id="95648-192">S C# 6, můžete nyní použít `await` v `catch` nebo `finally` výrazy.</span><span class="sxs-lookup"><span data-stu-id="95648-192">With C# 6, you can now use `await` in `catch` or `finally` expressions.</span></span> <span data-ttu-id="95648-193">To se nejčastěji používá v případě protokolování:</span><span class="sxs-lookup"><span data-stu-id="95648-193">This is most often used with logging scenarios:</span></span>

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

<span data-ttu-id="95648-194">Podrobnosti implementace pro přidání `await` podporovala uvnitř `catch` a `finally` klauzule Ujistěte se, že její chování je konzistentní s chování pro synchronní kód.</span><span class="sxs-lookup"><span data-stu-id="95648-194">The implementation details for adding `await` support inside `catch` and `finally` clauses ensure that the behavior is consistent with the behavior for synchronous code.</span></span> <span data-ttu-id="95648-195">Při spouštění kódu v `catch` nebo `finally` klauzule vyvolá výjimku, provádění hledá vhodný `catch` klauzule v další okolní bloku.</span><span class="sxs-lookup"><span data-stu-id="95648-195">When code executed in a `catch` or `finally` clause throws, execution looks for a suitable `catch` clause in the next surrounding block.</span></span> <span data-ttu-id="95648-196">Pokud se aktuální výjimku, tato výjimka bude ztracena.</span><span class="sxs-lookup"><span data-stu-id="95648-196">If there was a current exception, that exception is lost.</span></span> <span data-ttu-id="95648-197">Stejné se stane s očekávané výrazy v `catch` a `finally` klauzulí: vhodný `catch` prohledána, a na aktuální výjimku, pokud existuje, dojde ke ztrátě.</span><span class="sxs-lookup"><span data-stu-id="95648-197">The same happens with awaited expressions in `catch` and `finally` clauses: a suitable `catch` is searched for, and the current exception, if any, is lost.</span></span>  

> [!NOTE]
> <span data-ttu-id="95648-198">Toto chování je z důvodu se doporučuje pro zápis `catch` a `finally` klauzule pečlivě, aby nedošlo k zavedení nové výjimky.</span><span class="sxs-lookup"><span data-stu-id="95648-198">This behavior is the reason it's recommended to write `catch` and `finally` clauses carefully, to avoid introducing new exceptions.</span></span>

## <a name="initialize-associative-collections-using-indexers"></a><span data-ttu-id="95648-199">Inicializovat asociativní kolekce pomocí indexerů</span><span class="sxs-lookup"><span data-stu-id="95648-199">Initialize associative collections using indexers</span></span>

<span data-ttu-id="95648-200">*Inicializátory indexů* je jedním ze dvou funkcí, které usnadňují inicializátory kolekce konzistentnější s využitím indexu.</span><span class="sxs-lookup"><span data-stu-id="95648-200">*Index Initializers* is one of two features that make collection initializers more consistent with index usage.</span></span> <span data-ttu-id="95648-201">V dřívějších verzích C#, můžete použít *inicializátory kolekce* s kolekcemi styl sekvence, včetně <xref:System.Collections.Generic.Dictionary%602>, tím, že přidáte počet závorek kolem klíč a páry hodnot:</span><span class="sxs-lookup"><span data-stu-id="95648-201">In earlier releases of C#, you could use *collection initializers* with sequence style collections, including <xref:System.Collections.Generic.Dictionary%602>, by adding braces around key and value pairs:</span></span>

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#CollectionInitializer)]

<span data-ttu-id="95648-202">Můžete využít s <xref:System.Collections.Generic.Dictionary%602> kolekce a další typy, kde přístupný `Add` metoda přijímá více než jeden argument.</span><span class="sxs-lookup"><span data-stu-id="95648-202">You can use them with <xref:System.Collections.Generic.Dictionary%602> collections and other types where the accessible `Add` method accepts more than one argument.</span></span> <span data-ttu-id="95648-203">Nová syntaxe podporuje přiřazení do kolekce pomocí indexu:</span><span class="sxs-lookup"><span data-stu-id="95648-203">The new syntax supports assignment using an index into the collection:</span></span>

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

<span data-ttu-id="95648-204">Tato funkce znamená, že asociativní kontejnery mohou být inicializovány pomocí syntaxe podobné co bylo nastavené pro kontejnery sekvence pro několik verzí.</span><span class="sxs-lookup"><span data-stu-id="95648-204">This feature means that associative containers can be initialized using syntax similar to what's been in place for sequence containers for several versions.</span></span>

## <a name="extension-add-methods-in-collection-initializers"></a><span data-ttu-id="95648-205">Rozšíření `Add` metody v inicializátory kolekce</span><span class="sxs-lookup"><span data-stu-id="95648-205">Extension `Add` methods in collection initializers</span></span>

<span data-ttu-id="95648-206">Další funkce, která usnadňuje inicializace kolekce je schopnost používat *– metoda rozšíření* pro `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="95648-206">Another feature that makes collection initialization easier is the ability to use an *extension method* for the `Add` method.</span></span> <span data-ttu-id="95648-207">Tato funkce byla přidána parita s jazykem Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="95648-207">This feature was added for parity with Visual Basic.</span></span> <span data-ttu-id="95648-208">Tato funkce je nejužitečnější v případě, že máte vlastní třídu kolekce, která obsahuje metodu s jiným názvem sémanticky přidávat nové položky.</span><span class="sxs-lookup"><span data-stu-id="95648-208">The feature is most useful when you have a custom collection class that has a method with a different name to semantically add new items.</span></span>

## <a name="improved-overload-resolution"></a><span data-ttu-id="95648-209">Vylepšené přetížení</span><span class="sxs-lookup"><span data-stu-id="95648-209">Improved overload resolution</span></span>

<span data-ttu-id="95648-210">Tato funkce poslední je ten, který pravděpodobně nebude oznámení.</span><span class="sxs-lookup"><span data-stu-id="95648-210">This last feature is one you probably won't notice.</span></span> <span data-ttu-id="95648-211">Došlo k konstrukce předchozí verze kompilátoru jazyka C# může kde najdete některé volání metody zahrnující nejednoznačné výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="95648-211">There were constructs where the previous version of the C# compiler may have found some method calls involving lambda expressions ambiguous.</span></span> <span data-ttu-id="95648-212">Vezměte v úvahu tuto metodu:</span><span class="sxs-lookup"><span data-stu-id="95648-212">Consider this method:</span></span>

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

<span data-ttu-id="95648-213">Voláním této metody pomocí syntaxe metody skupiny selže v dřívějších verzích jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="95648-213">In earlier versions of C#, calling that method using the method group syntax would fail:</span></span>

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]

<span data-ttu-id="95648-214">Kompilátor starší nelze rozlišit správně mezi `Task.Run(Action)` a `Task.Run(Func<Task>())`.</span><span class="sxs-lookup"><span data-stu-id="95648-214">The earlier compiler couldn't distinguish correctly between `Task.Run(Action)` and `Task.Run(Func<Task>())`.</span></span> <span data-ttu-id="95648-215">V předchozích verzích je třeba použít výraz lambda jako argument:</span><span class="sxs-lookup"><span data-stu-id="95648-215">In previous versions, you'd need to use a lambda expression as an argument:</span></span>

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

<span data-ttu-id="95648-216">Určuje, který kompilátor jazyka C# 6 správně `Task.Run(Func<Task>())` je lepší volbou.</span><span class="sxs-lookup"><span data-stu-id="95648-216">The C# 6 compiler correctly determines that `Task.Run(Func<Task>())` is a better choice.</span></span>

### <a name="deterministic-compiler-output"></a><span data-ttu-id="95648-217">Výstup kompilátoru deterministické</span><span class="sxs-lookup"><span data-stu-id="95648-217">Deterministic compiler output</span></span>

<span data-ttu-id="95648-218">`-deterministic` Možnost instruuje kompilátor, aby vytvořit bajt po bajtu identické výstupního sestavení po sobě následujících souborů stejných zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="95648-218">The `-deterministic` option instructs the compiler to produce a byte-for-byte identical output assembly for successive compilations of the same source files.</span></span>

<span data-ttu-id="95648-219">Ve výchozím nastavení vytvoří každé kompilaci jedinečný výstup na každý kompilace.</span><span class="sxs-lookup"><span data-stu-id="95648-219">By default, every compilation produces unique output on each compilation.</span></span> <span data-ttu-id="95648-220">Kompilátor přidá časové razítko a identifikátor GUID vygenerovaný z náhodných čísel.</span><span class="sxs-lookup"><span data-stu-id="95648-220">The compiler adds a timestamp, and a GUID generated from random numbers.</span></span> <span data-ttu-id="95648-221">Tuto možnost použijte, pokud chcete k porovnání pro bajtech výstupu k zajištění konzistence se v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="95648-221">You use this option if you want to compare the byte-for-byte output to ensure consistency across builds.</span></span>

<span data-ttu-id="95648-222">Další informace najdete v tématu [– možnost kompilátoru deterministické](../language-reference/compiler-options/deterministic-compiler-option.md) článku.</span><span class="sxs-lookup"><span data-stu-id="95648-222">For more information, see the [-deterministic compiler option](../language-reference/compiler-options/deterministic-compiler-option.md) article.</span></span>
