---
title: Co je nového v C# 6 - C# Průvodce
description: Naučte se nové funkce v C# verze 6
ms.date: 12/12/2018
ms.openlocfilehash: da40b4c9d4af0094fdd907c542e971ba55086e0f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399390"
---
# <a name="whats-new-in-c-6"></a><span data-ttu-id="dc4f1-103">Co je nového v C# 6</span><span class="sxs-lookup"><span data-stu-id="dc4f1-103">What's New in C# 6</span></span>

<span data-ttu-id="dc4f1-104">Verze 6.0 c# obsahuje mnoho funkcí, které zlepšují produktivitu pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-104">The 6.0 release of C# contained many features that improve productivity for developers.</span></span> <span data-ttu-id="dc4f1-105">Celkový efekt těchto funkcí je, že píšete stručnější kód, který je také čitelnější.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-105">The overall effect of these features is that you write more concise code that is also more readable.</span></span> <span data-ttu-id="dc4f1-106">Syntaxe obsahuje méně obřad u mnoha běžných postupů.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-106">The syntax contains less ceremony for many common practices.</span></span> <span data-ttu-id="dc4f1-107">Je snazší vidět záměr návrhu s menším obřadem.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-107">It's easier to see the design intent with less ceremony.</span></span> <span data-ttu-id="dc4f1-108">Naučte se tyto funkce dobře a budete produktivnější a napíšete čitelnější kód.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-108">Learn these features well, and you'll be more productive and write more readable code.</span></span> <span data-ttu-id="dc4f1-109">Můžete se soustředit více na své funkce než na konstrukce jazyka.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-109">You can concentrate more on your features than on the constructs of the language.</span></span>

<span data-ttu-id="dc4f1-110">Zbývající část tohoto článku obsahuje přehled každé z těchto funkcí s odkazem na prozkoumání jednotlivých funkcí.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-110">The rest of this article provides an overview of each of these features, with a link to explore each feature.</span></span> <span data-ttu-id="dc4f1-111">Můžete také prozkoumat funkce v [interaktivní průzkum na C# 6](../tutorials/exploration/csharp-6.yml) v části kurzy.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-111">You can also explore the features in an [interactive exploration on C# 6](../tutorials/exploration/csharp-6.yml) in the tutorials section.</span></span>

## <a name="read-only-auto-properties"></a><span data-ttu-id="dc4f1-112">Automatické vlastnosti jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="dc4f1-112">Read-only auto-properties</span></span>

<span data-ttu-id="dc4f1-113">*Automatické vlastnosti jen pro čtení* poskytují stručnější syntaxi pro vytváření neměnných typů.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-113">*Read-only auto-properties* provide a more concise syntax to create immutable types.</span></span> <span data-ttu-id="dc4f1-114">Deklarace auto-vlastnost pouze získat přistupujícího objektu:</span><span class="sxs-lookup"><span data-stu-id="dc4f1-114">You declare the auto-property with only a get accessor:</span></span>

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

<span data-ttu-id="dc4f1-115">`FirstName` Vlastnosti `LastName` a lze nastavit pouze v těle konstruktoru stejné třídy:</span><span class="sxs-lookup"><span data-stu-id="dc4f1-115">The `FirstName` and `LastName` properties can be set only in the body of the constructor of the same class:</span></span>

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

<span data-ttu-id="dc4f1-116">Při pokusu o nastavení `LastName` `CS0200` v jiné metodě se vygeneruje chyba kompilace:</span><span class="sxs-lookup"><span data-stu-id="dc4f1-116">Trying to set `LastName` in another method generates a `CS0200` compilation error:</span></span>

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

<span data-ttu-id="dc4f1-117">Tato funkce umožňuje skutečnou jazykovou podporu pro vytváření neměnných typů a používá stručnější a pohodlnější syntaxi automatické vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-117">This feature enables true language support for creating immutable types and uses the more concise and convenient auto-property syntax.</span></span>

<span data-ttu-id="dc4f1-118">Pokud přidání této syntaxe neodebere přístupnou metodu, jedná se o [binární kompatibilní změnu](version-update-considerations.md#binary-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="dc4f1-118">If adding this syntax doesn't remove an accessible method, it's a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="auto-property-initializers"></a><span data-ttu-id="dc4f1-119">Inicializátory automatických vlastností</span><span class="sxs-lookup"><span data-stu-id="dc4f1-119">Auto-property initializers</span></span>

<span data-ttu-id="dc4f1-120">*Inicializátory automatických vlastností* umožňují deklarovat počáteční hodnotu pro automatickou vlastnost jako součást deklarace vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-120">*Auto-property initializers* let you declare the initial value for an auto-property as part of the property declaration.</span></span>

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

<span data-ttu-id="dc4f1-121">Člen `Grades` je inicializován tam, kde je deklarován.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-121">The `Grades` member is initialized where it's declared.</span></span> <span data-ttu-id="dc4f1-122">To usnadňuje provedení inicializace přesně jednou.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-122">That makes it easier to perform the initialization exactly once.</span></span> <span data-ttu-id="dc4f1-123">Inicializace je součástí deklarace vlastnosti, což usnadňuje srovnávač přidělení úložiště s veřejným rozhraním pro `Student` objekty.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-123">The initialization is part of the property declaration, making it easier to equate the storage allocation with the public interface for `Student` objects.</span></span>

## <a name="expression-bodied-function-members"></a><span data-ttu-id="dc4f1-124">Členy funkce s výrazným tělem</span><span class="sxs-lookup"><span data-stu-id="dc4f1-124">Expression-bodied function members</span></span>

<span data-ttu-id="dc4f1-125">Mnoho členů, které píšete, jsou jednotlivé příkazy, které mohou být jednotlivé výrazy.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-125">Many members that you write are single statements that could be single expressions.</span></span> <span data-ttu-id="dc4f1-126">Místo toho napište člen s výrazem.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-126">Write an expression-bodied member instead.</span></span> <span data-ttu-id="dc4f1-127">Funguje pro metody a vlastnosti jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-127">It works for methods and read-only properties.</span></span> <span data-ttu-id="dc4f1-128">Například přepsání `ToString()` je často velkým kandidátem:</span><span class="sxs-lookup"><span data-stu-id="dc4f1-128">For example, an override of `ToString()` is often a great candidate:</span></span>

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

<span data-ttu-id="dc4f1-129">Tuto syntaxi můžete také použít pro vlastnosti jen pro čtení:</span><span class="sxs-lookup"><span data-stu-id="dc4f1-129">You can also use this syntax for read-only properties:</span></span>

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="dc4f1-130">Změna existujícího člena na člen s tělesnou dolinou výrazu je [binární kompatibilní změna](version-update-considerations.md#binary-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="dc4f1-130">Changing an existing member to an expression bodied member is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="using-static"></a><span data-ttu-id="dc4f1-131">použití statické</span><span class="sxs-lookup"><span data-stu-id="dc4f1-131">using static</span></span>

<span data-ttu-id="dc4f1-132">*Použití statické* vylepšení umožňuje importovat statické metody jedné třídy.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-132">The *using static* enhancement enables you to import the static methods of a single class.</span></span> <span data-ttu-id="dc4f1-133">Zadejte třídu, kterou používáte:</span><span class="sxs-lookup"><span data-stu-id="dc4f1-133">You specify the class you're using:</span></span>

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<span data-ttu-id="dc4f1-134">Neobsahuje <xref:System.Math> žádné metody instance.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-134">The <xref:System.Math> does not contain any instance methods.</span></span> <span data-ttu-id="dc4f1-135">Můžete také `using static` použít k importu statické metody třídy pro třídu, která má statické metody i metody instance.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-135">You can also use `using static` to import a class' static methods for a class that has both static and instance methods.</span></span> <span data-ttu-id="dc4f1-136">Jedním z nejužitečnějších <xref:System.String>příkladů je :</span><span class="sxs-lookup"><span data-stu-id="dc4f1-136">One of the most useful examples is <xref:System.String>:</span></span>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> <span data-ttu-id="dc4f1-137">Je nutné použít plně kvalifikovaný `System.String` název třídy, ve statické using příkazu.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-137">You must use the fully qualified class name, `System.String`  in a static using statement.</span></span>  <span data-ttu-id="dc4f1-138">Místo toho `string` nelze použít klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-138">You cannot use the `string` keyword instead.</span></span>

<span data-ttu-id="dc4f1-139">Při importu `static using` z příkazu jsou metody rozšíření pouze v oboru, pokud jsou volány pomocí syntaxe vyvolání metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-139">When imported from a `static using` statement, extension methods are only in scope when called using the extension method invocation syntax.</span></span> <span data-ttu-id="dc4f1-140">Nejsou v oboru při volání jako statická metoda.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-140">They aren't in scope when called as a static method.</span></span> <span data-ttu-id="dc4f1-141">Často se zobrazí v dotazech LINQ.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-141">You'll often see this in LINQ queries.</span></span> <span data-ttu-id="dc4f1-142">Vzorek LINQ můžete importovat <xref:System.Linq.Enumerable>importováním <xref:System.Linq.Queryable>nebo .</span><span class="sxs-lookup"><span data-stu-id="dc4f1-142">You can import the LINQ pattern by importing <xref:System.Linq.Enumerable>, or <xref:System.Linq.Queryable>.</span></span>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

<span data-ttu-id="dc4f1-143">Obvykle volání metody rozšíření pomocí výrazy vyvolání metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-143">You typically call extension methods using extension method invocation expressions.</span></span> <span data-ttu-id="dc4f1-144">Přidání názvu třídy ve výjimečných případech, kdy je voláte pomocí syntaxe volání statické metody, řeší nejednoznačnost.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-144">Adding the class name in the rare case where you call them using static method call syntax resolves ambiguity.</span></span>

<span data-ttu-id="dc4f1-145">Směrnice `static using` také importuje všechny vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-145">The `static using` directive also imports any nested types.</span></span> <span data-ttu-id="dc4f1-146">Můžete odkazovat na všechny vnořené typy bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-146">You can reference any nested types without qualification.</span></span>

## <a name="null-conditional-operators"></a><span data-ttu-id="dc4f1-147">Operátory s nulovým podmíněným podmínkou</span><span class="sxs-lookup"><span data-stu-id="dc4f1-147">Null-conditional operators</span></span>

<span data-ttu-id="dc4f1-148">Operátor *podmíněné null* umožňuje null kontroly mnohem jednodušší a plynulé.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-148">The *null conditional operator* makes null checks much easier and fluid.</span></span> <span data-ttu-id="dc4f1-149">Nahraďte `.` přístup `?.`člena :</span><span class="sxs-lookup"><span data-stu-id="dc4f1-149">Replace the member access `.` with `?.`:</span></span>

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

<span data-ttu-id="dc4f1-150">V předchozím příkladu je `first` proměnná `null` přiřazena, `null`pokud je objekt osoby .</span><span class="sxs-lookup"><span data-stu-id="dc4f1-150">In the preceding example, the variable `first` is assigned `null` if the person object is `null`.</span></span> <span data-ttu-id="dc4f1-151">V opačném případě je přiřazena hodnota vlastnosti. `FirstName`</span><span class="sxs-lookup"><span data-stu-id="dc4f1-151">Otherwise, it is assigned the value of the `FirstName` property.</span></span> <span data-ttu-id="dc4f1-152">A co je `?.` nejdůležitější, znamená, že tento `NullReferenceException` řádek `person` kódu `null`negeneruje, pokud je proměnná .</span><span class="sxs-lookup"><span data-stu-id="dc4f1-152">Most importantly, the `?.` means that this line of code doesn't generate a `NullReferenceException` if the `person` variable is `null`.</span></span> <span data-ttu-id="dc4f1-153">Místo toho zkratuje a `null`vrací .</span><span class="sxs-lookup"><span data-stu-id="dc4f1-153">Instead, it short-circuits and returns `null`.</span></span> <span data-ttu-id="dc4f1-154">Můžete také použít operátor podmíněné null pro přístup k poli nebo indexeru.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-154">You can also use a null conditional operator for array or indexer access.</span></span> <span data-ttu-id="dc4f1-155">Nahradit `[]` `?[]` ve výrazu indexu.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-155">Replace `[]` with `?[]` in the index expression.</span></span>

<span data-ttu-id="dc4f1-156">Následující výraz vrátí `string`hodnotu a , `person`bez ohledu na hodnotu .</span><span class="sxs-lookup"><span data-stu-id="dc4f1-156">The following expression returns a `string`, regardless of the value of `person`.</span></span> <span data-ttu-id="dc4f1-157">Často používáte tento konstrukt s *nulovou slučovací* operátor přiřadit `null`výchozí hodnoty, pokud je jedna z vlastností .</span><span class="sxs-lookup"><span data-stu-id="dc4f1-157">You often use this construct with the *null coalescing* operator to assign default values when one of the properties is `null`.</span></span> <span data-ttu-id="dc4f1-158">Když se výraz zkratuje, `null` vrácená hodnota je zadántak, aby odpovídala úplnému výrazu.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-158">When the expression short-circuits, the `null` value returned is typed to match the full expression.</span></span>

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

<span data-ttu-id="dc4f1-159">Můžete také `?.` použít k podmíněnému vyvolání metod.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-159">You can also use `?.` to conditionally invoke methods.</span></span> <span data-ttu-id="dc4f1-160">Nejběžnější použití členských funkcí s operátorem podmíněné null je bezpečně vyvolat delegáty `null`(nebo obslužné rutiny událostí), které mohou být .</span><span class="sxs-lookup"><span data-stu-id="dc4f1-160">The most common use of member functions  with the null conditional operator is to safely invoke delegates (or event handlers) that may be `null`.</span></span>  <span data-ttu-id="dc4f1-161">Budete volat metodu delegáta `Invoke` pomocí `?.` operátoru pro přístup k členu.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-161">You'll call the delegate's `Invoke` method using the `?.` operator to access the member.</span></span> <span data-ttu-id="dc4f1-162">Příklad můžete vidět v článku [vzory delegáta.](../delegates-patterns.md#handling-null-delegates)</span><span class="sxs-lookup"><span data-stu-id="dc4f1-162">You can see an example in the [delegate patterns](../delegates-patterns.md#handling-null-delegates) article.</span></span>

<span data-ttu-id="dc4f1-163">Pravidla `?.` provozovatele zajišťují, že levá strana obsluhy je vyhodnocena pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-163">The rules of the `?.` operator ensure that the left-hand side of the operator is evaluated only once.</span></span> <span data-ttu-id="dc4f1-164">Umožňuje mnoho idiomy, včetně následujícího příkladu pomocí obslužné rutiny událostí:</span><span class="sxs-lookup"><span data-stu-id="dc4f1-164">It enables many idioms, including the following example using event handlers:</span></span>

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

<span data-ttu-id="dc4f1-165">Zajištění, že levá strana je vyhodnocena pouze jednou, umožňuje použít libovolný výraz, včetně volání metod, na levé straně`?.`</span><span class="sxs-lookup"><span data-stu-id="dc4f1-165">Ensuring that the left side is evaluated only once also enables you to use any expression, including method calls, on the left side of the `?.`</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="dc4f1-166">Interpolace řetězců</span><span class="sxs-lookup"><span data-stu-id="dc4f1-166">String interpolation</span></span>

<span data-ttu-id="dc4f1-167">S C# 6 nový řetězec [interpolace](../language-reference/tokens/interpolated.md) funkce umožňuje vložit výrazy v řetězci.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-167">With C# 6, the new [string interpolation](../language-reference/tokens/interpolated.md) feature enables you to embed expressions in a string.</span></span> <span data-ttu-id="dc4f1-168">Jednoduše předmluva `$`řetězec s a `{` `}` používat výrazy mezi a místo řadových čísel:</span><span class="sxs-lookup"><span data-stu-id="dc4f1-168">Simply preface the string with `$`and use expressions between `{` and `}` instead of ordinals:</span></span>

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="dc4f1-169">Tento příklad používá vlastnosti pro nahrazené výrazy.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-169">This example uses properties for the substituted expressions.</span></span> <span data-ttu-id="dc4f1-170">Můžete použít libovolný výraz.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-170">You can use any expression.</span></span> <span data-ttu-id="dc4f1-171">Můžete například vypočítat bodový průměr hodnocení studenta jako součást interpolace:</span><span class="sxs-lookup"><span data-stu-id="dc4f1-171">For example, you could compute a student's grade point average as part of the interpolation:</span></span>

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

<span data-ttu-id="dc4f1-172">Předchozí řádek kódu formátuje hodnotu `Grades.Average()` jako číslo s plovoucí desetinnou čárkou se dvěma desetinnými místy.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-172">The preceding line of code formats the value for `Grades.Average()` as a floating-point number with two decimal places.</span></span>

<span data-ttu-id="dc4f1-173">Často může být nutné formátovat řetězec vytvořený pomocí určité jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-173">Often, you may need to format the string produced using a specific culture.</span></span> <span data-ttu-id="dc4f1-174">Použijete skutečnost, že objekt vytvořený interpolací řetězce lze <xref:System.FormattableString?displayProperty=nameWithType>implicitně převést na .</span><span class="sxs-lookup"><span data-stu-id="dc4f1-174">You use the fact that the object produced by a string interpolation can be implicitly converted to <xref:System.FormattableString?displayProperty=nameWithType>.</span></span> <span data-ttu-id="dc4f1-175">Instance <xref:System.FormattableString> obsahuje složený formátovací řetězec a výsledky vyhodnocení výrazů před jejich převodem na řetězce.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-175">The <xref:System.FormattableString> instance contains the composite format string and the results of evaluating the expressions before converting them to strings.</span></span> <span data-ttu-id="dc4f1-176">Pomocí <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> metody určete jazykovou verzi při formátování řetězce.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-176">Use the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method to specify the culture when formatting a string.</span></span> <span data-ttu-id="dc4f1-177">Následující příklad vytvoří řetězec pomocí německé (de-DE) jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-177">The following example produces a string using the German (de-DE) culture.</span></span> <span data-ttu-id="dc4f1-178">(Ve výchozím nastavení používá německá jazyková verze znak ',' pro oddělovač desetinných míst a znak '.' jako oddělovač tisíců.)</span><span class="sxs-lookup"><span data-stu-id="dc4f1-178">(By default, the German culture uses the ',' character for the decimal separator, and the '.' character as the thousands separator.)</span></span>

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

<span data-ttu-id="dc4f1-179">Chcete-li začít s interpolací řetězců, naleznete v interaktivním kurzu [String interpolace v c#](../tutorials/exploration/interpolated-strings.yml) [, článek interpolace řetězce](../language-reference/tokens/interpolated.md) a [interpolace řetězce v kurzu Jazyka C#.](../tutorials/string-interpolation.md)</span><span class="sxs-lookup"><span data-stu-id="dc4f1-179">To get started with string interpolation, see the [String interpolation in C#](../tutorials/exploration/interpolated-strings.yml) interactive tutorial, the [String interpolation](../language-reference/tokens/interpolated.md) article, and the [String interpolation in C#](../tutorials/string-interpolation.md) tutorial.</span></span>

## <a name="exception-filters"></a><span data-ttu-id="dc4f1-180">Filtry výjimek</span><span class="sxs-lookup"><span data-stu-id="dc4f1-180">Exception filters</span></span>

<span data-ttu-id="dc4f1-181">*Filtry výjimek* jsou klauzule, které určují, kdy by měla být použita daná klauzule catch.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-181">*Exception Filters* are clauses that determine when a given catch clause should be applied.</span></span> <span data-ttu-id="dc4f1-182">Pokud výraz použitý pro filtr výjimek vyhodnotí `true`, klauzule catch provede normální zpracování na výjimku.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-182">If the expression used for an exception filter evaluates to `true`, the catch clause performs its normal processing on an exception.</span></span> <span data-ttu-id="dc4f1-183">Pokud výraz vyhodnotí `false`do `catch` , pak je klauzule přeskočena.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-183">If the expression evaluates to `false`, then the `catch` clause is skipped.</span></span> <span data-ttu-id="dc4f1-184">Jedním z použití je prozkoumat informace `catch` o výjimce k určení, zda klauzule může zpracovat výjimku:</span><span class="sxs-lookup"><span data-stu-id="dc4f1-184">One use is to examine information about an exception to determine if a `catch` clause can process the exception:</span></span>

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

## <a name="the-nameof-expression"></a><span data-ttu-id="dc4f1-185">Výraz `nameof`</span><span class="sxs-lookup"><span data-stu-id="dc4f1-185">The `nameof` expression</span></span>

<span data-ttu-id="dc4f1-186">Název [výrazu](../language-reference/operators/nameof.md) vyhodnotí název symbolu.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-186">The [nameof](../language-reference/operators/nameof.md) expression evaluates to the name of a symbol.</span></span> <span data-ttu-id="dc4f1-187">Je to skvělý způsob, jak získat nástroje pracovní kdykoli budete potřebovat název proměnné, vlastnost nebo členské pole.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-187">It's a great way to get tools working whenever you need the name of a variable, a property, or a member field.</span></span> <span data-ttu-id="dc4f1-188">Jedním z nejběžnějších `nameof` použití pro je poskytnout název symbolu, který způsobil výjimku:</span><span class="sxs-lookup"><span data-stu-id="dc4f1-188">One of the most common uses for `nameof` is to provide the name of a symbol that caused an exception:</span></span>

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

<span data-ttu-id="dc4f1-189">Další použití je s aplikacemi založenými `INotifyPropertyChanged` na XAML, které implementují rozhraní:</span><span class="sxs-lookup"><span data-stu-id="dc4f1-189">Another use is with XAML-based applications that implement the `INotifyPropertyChanged` interface:</span></span>

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

## <a name="await-in-catch-and-finally-blocks"></a><span data-ttu-id="dc4f1-190">Čekají v Catch a Finally bloky</span><span class="sxs-lookup"><span data-stu-id="dc4f1-190">Await in Catch and Finally blocks</span></span>

<span data-ttu-id="dc4f1-191">C# 5 měl několik omezení kolem `await` místa, kde můžete umístit výrazy.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-191">C# 5 had several limitations around where you could place `await` expressions.</span></span> <span data-ttu-id="dc4f1-192">S C# 6, nyní `await` `catch` můžete `finally` použít v nebo výrazy.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-192">With C# 6, you can now use `await` in `catch` or `finally` expressions.</span></span> <span data-ttu-id="dc4f1-193">To se nejčastěji používá se scénáři protokolování:</span><span class="sxs-lookup"><span data-stu-id="dc4f1-193">This is most often used with logging scenarios:</span></span>

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

<span data-ttu-id="dc4f1-194">Podrobnosti implementace `await` pro `catch` přidání `finally` podpory uvnitř a klauzule zajistit, že chování je konzistentní s chováním pro synchronní kód.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-194">The implementation details for adding `await` support inside `catch` and `finally` clauses ensure that the behavior is consistent with the behavior for synchronous code.</span></span> <span data-ttu-id="dc4f1-195">Při spuštění kódu `catch` v `finally` nebo klauzule vyvolá, `catch` spuštění hledá vhodnou klauzuli v dalším okolním bloku.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-195">When code executed in a `catch` or `finally` clause throws, execution looks for a suitable `catch` clause in the next surrounding block.</span></span> <span data-ttu-id="dc4f1-196">Pokud byla aktuální výjimka, tato výjimka je ztracena.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-196">If there was a current exception, that exception is lost.</span></span> <span data-ttu-id="dc4f1-197">Totéž se děje s `catch` očekávanými výrazy a `finally` klauzulemi: je vyhledána vhodná `catch` a aktuální výjimka, pokud existuje, je ztracena.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-197">The same happens with awaited expressions in `catch` and `finally` clauses: a suitable `catch` is searched for, and the current exception, if any, is lost.</span></span>  

> [!NOTE]
> <span data-ttu-id="dc4f1-198">Toto chování je důvod, proč `catch` `finally` se doporučuje psát a klauzule pečlivě, aby se zabránilo zavedení nové výjimky.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-198">This behavior is the reason it's recommended to write `catch` and `finally` clauses carefully, to avoid introducing new exceptions.</span></span>

## <a name="initialize-associative-collections-using-indexers"></a><span data-ttu-id="dc4f1-199">Inicializovat asociativní kolekce pomocí indexerů</span><span class="sxs-lookup"><span data-stu-id="dc4f1-199">Initialize associative collections using indexers</span></span>

<span data-ttu-id="dc4f1-200">*Index Initializers* je jedním ze dvou funkcí, které kolekce inicializátory více konzistentní s využití indexu.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-200">*Index Initializers* is one of two features that make collection initializers more consistent with index usage.</span></span> <span data-ttu-id="dc4f1-201">V dřívějších verzích jazyka C# můžete použít *inicializátory kolekce* s kolekcemi stylů sekvence, včetně <xref:System.Collections.Generic.Dictionary%602>, přidáním závorek kolem párů klíčů a hodnot:</span><span class="sxs-lookup"><span data-stu-id="dc4f1-201">In earlier releases of C#, you could use *collection initializers* with sequence style collections, including <xref:System.Collections.Generic.Dictionary%602>, by adding braces around key and value pairs:</span></span>

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#CollectionInitializer)]

<span data-ttu-id="dc4f1-202">Můžete je použít <xref:System.Collections.Generic.Dictionary%602> s kolekcemi a `Add` jinými typy, kde přístupná metoda přijímá více než jeden argument.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-202">You can use them with <xref:System.Collections.Generic.Dictionary%602> collections and other types where the accessible `Add` method accepts more than one argument.</span></span> <span data-ttu-id="dc4f1-203">Nová syntaxe podporuje přiřazení pomocí indexu do kolekce:</span><span class="sxs-lookup"><span data-stu-id="dc4f1-203">The new syntax supports assignment using an index into the collection:</span></span>

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

<span data-ttu-id="dc4f1-204">Tato funkce znamená, že asociativní kontejnery lze inicializovat pomocí syntaxe podobné tomu, co bylo na místě pro kontejnery sekvence pro několik verzí.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-204">This feature means that associative containers can be initialized using syntax similar to what's been in place for sequence containers for several versions.</span></span>

## <a name="extension-add-methods-in-collection-initializers"></a><span data-ttu-id="dc4f1-205">Metody `Add` rozšíření v inicializátorech kolekce</span><span class="sxs-lookup"><span data-stu-id="dc4f1-205">Extension `Add` methods in collection initializers</span></span>

<span data-ttu-id="dc4f1-206">Další funkce, která usnadňuje inicializaci kolekce je `Add` možnost použít *metodu rozšíření* pro metodu.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-206">Another feature that makes collection initialization easier is the ability to use an *extension method* for the `Add` method.</span></span> <span data-ttu-id="dc4f1-207">Tato funkce byla přidána pro paritu s visual basicem.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-207">This feature was added for parity with Visual Basic.</span></span> <span data-ttu-id="dc4f1-208">Funkce je nejužitečnější, pokud máte vlastní třídu kolekce, která má metodu s jiným názvem sémanticky přidat nové položky.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-208">The feature is most useful when you have a custom collection class that has a method with a different name to semantically add new items.</span></span>

## <a name="improved-overload-resolution"></a><span data-ttu-id="dc4f1-209">Vylepšené rozlišení přetížení</span><span class="sxs-lookup"><span data-stu-id="dc4f1-209">Improved overload resolution</span></span>

<span data-ttu-id="dc4f1-210">Tato poslední funkce je ta, kterou si pravděpodobně nevšimnete.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-210">This last feature is one you probably won't notice.</span></span> <span data-ttu-id="dc4f1-211">Tam byly konstrukce, kde předchozí verze kompilátoru Jazyka C# může mít nalezeny některé volání metod zahrnující lambda výrazy nejednoznačné.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-211">There were constructs where the previous version of the C# compiler may have found some method calls involving lambda expressions ambiguous.</span></span> <span data-ttu-id="dc4f1-212">Zvažte tuto metodu:</span><span class="sxs-lookup"><span data-stu-id="dc4f1-212">Consider this method:</span></span>

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

<span data-ttu-id="dc4f1-213">V dřívějších verzích jazyka C# by volání této metody pomocí syntaxe skupiny metody selhalo:</span><span class="sxs-lookup"><span data-stu-id="dc4f1-213">In earlier versions of C#, calling that method using the method group syntax would fail:</span></span>

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]

<span data-ttu-id="dc4f1-214">Dřívější kompilátor nemohl správně `Task.Run(Action)` rozlišit mezi a `Task.Run(Func<Task>())`.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-214">The earlier compiler couldn't distinguish correctly between `Task.Run(Action)` and `Task.Run(Func<Task>())`.</span></span> <span data-ttu-id="dc4f1-215">V předchozích verzích byste museli použít výraz lambda jako argument:</span><span class="sxs-lookup"><span data-stu-id="dc4f1-215">In previous versions, you'd need to use a lambda expression as an argument:</span></span>

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

<span data-ttu-id="dc4f1-216">Kompilátor Jazyka C# 6 `Task.Run(Func<Task>())` správně určuje, že je lepší volbou.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-216">The C# 6 compiler correctly determines that `Task.Run(Func<Task>())` is a better choice.</span></span>

### <a name="deterministic-compiler-output"></a><span data-ttu-id="dc4f1-217">Deterministický výstup kompilátoru</span><span class="sxs-lookup"><span data-stu-id="dc4f1-217">Deterministic compiler output</span></span>

<span data-ttu-id="dc4f1-218">Tato `-deterministic` možnost instruuje kompilátor k vytvoření identického výstupního sestavení bajtu za bajt pro následné kompilace stejných zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-218">The `-deterministic` option instructs the compiler to produce a byte-for-byte identical output assembly for successive compilations of the same source files.</span></span>

<span data-ttu-id="dc4f1-219">Ve výchozím nastavení každá kompilace vytváří jedinečný výstup na každé kompilaci.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-219">By default, every compilation produces unique output on each compilation.</span></span> <span data-ttu-id="dc4f1-220">Kompilátor přidá časové razítko a identifikátor GUID generovaný z náhodných čísel.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-220">The compiler adds a timestamp, and a GUID generated from random numbers.</span></span> <span data-ttu-id="dc4f1-221">Tuto možnost použijte, pokud chcete porovnat výstup bajt za bajt, abyste zajistili konzistenci mezi sestaveními.</span><span class="sxs-lookup"><span data-stu-id="dc4f1-221">You use this option if you want to compare the byte-for-byte output to ensure consistency across builds.</span></span>

<span data-ttu-id="dc4f1-222">Další informace naleznete v článku [možnosti determinismu -deterministický kompilátor.](../language-reference/compiler-options/deterministic-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="dc4f1-222">For more information, see the [-deterministic compiler option](../language-reference/compiler-options/deterministic-compiler-option.md) article.</span></span>
