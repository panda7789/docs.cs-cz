---
title: Co je nového v jazyce C# 6 – Průvodce v C#
description: Informace o nových funkcích v C# verze 6
keywords: Rozhraní .NET, .NET core
author: BillWagner
ms.date: 09/22/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 4d879f69-f889-4d3f-a781-75194e143400
ms.openlocfilehash: ea54e9a05120134eea8e1bc9d82302a7513b43e7
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2018
---
# <a name="whats-new-in-c-6"></a><span data-ttu-id="326e9-104">Co je nového v jazyce C# 6</span><span class="sxs-lookup"><span data-stu-id="326e9-104">What's New in C# 6</span></span>

<span data-ttu-id="326e9-105">6.0 verze jazyka C# obsahuje řadu funkcí, které zvýšení produktivity pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="326e9-105">The 6.0 release of C# contained many features that improve productivity for developers.</span></span> <span data-ttu-id="326e9-106">Funkce v této verzi patří:</span><span class="sxs-lookup"><span data-stu-id="326e9-106">Features in this release include:</span></span>

* <span data-ttu-id="326e9-107">[Auto vlastnosti jen pro čtení](#read-only-auto-properties):</span><span class="sxs-lookup"><span data-stu-id="326e9-107">[Read-only Auto-properties](#read-only-auto-properties):</span></span>
    - <span data-ttu-id="326e9-108">Můžete vytvořit jen pro čtení automaticky – vlastnosti, které lze nastavit pouze v konstruktory.</span><span class="sxs-lookup"><span data-stu-id="326e9-108">You can create read-only auto-properties that can be set only in constructors.</span></span>
* <span data-ttu-id="326e9-109">[Inicializátory automaticky vlastnost](#auto-property-initializers):</span><span class="sxs-lookup"><span data-stu-id="326e9-109">[Auto-Property Initializers](#auto-property-initializers):</span></span>
    - <span data-ttu-id="326e9-110">Můžete napsat inicializace výrazy pro nastavení počáteční hodnota auto vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="326e9-110">You can write initialization expressions to set the initial value of an auto-property.</span></span>
* <span data-ttu-id="326e9-111">[Výraz vozidlo funkce členy](#expression-bodied-function-members):</span><span class="sxs-lookup"><span data-stu-id="326e9-111">[Expression-bodied function members](#expression-bodied-function-members):</span></span>
    - <span data-ttu-id="326e9-112">Můžete vytvořit metody jednořádkové použití výrazů lambda.</span><span class="sxs-lookup"><span data-stu-id="326e9-112">You can author one-line methods using lambda expressions.</span></span>
* <span data-ttu-id="326e9-113">[pomocí statické](#using-static):</span><span class="sxs-lookup"><span data-stu-id="326e9-113">[using static](#using-static):</span></span>
    - <span data-ttu-id="326e9-114">Všechny metody jedné třídy můžete importovat do aktuální obor názvů.</span><span class="sxs-lookup"><span data-stu-id="326e9-114">You can import all the methods of a single class into the current namespace.</span></span>
* <span data-ttu-id="326e9-115">[Null – podmíněné operátory](#null-conditional-operators):</span><span class="sxs-lookup"><span data-stu-id="326e9-115">[Null - conditional operators](#null-conditional-operators):</span></span>
    - <span data-ttu-id="326e9-116">Můžete výstižně a bezpečně přistupovat členům v objektu při kontrole stále null s podmíněný operátor s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="326e9-116">You can concisely and safely access members of an object while still checking for null with the null conditional operator.</span></span>
* <span data-ttu-id="326e9-117">[Řetězec interpolace](#string-interpolation):</span><span class="sxs-lookup"><span data-stu-id="326e9-117">[String Interpolation](#string-interpolation):</span></span>
    - <span data-ttu-id="326e9-118">Můžete napsat řetězec formátování výrazy pomocí vložené výrazy místo poziční argumenty.</span><span class="sxs-lookup"><span data-stu-id="326e9-118">You can write string formatting expressions using inline expressions instead of positional arguments.</span></span>
* <span data-ttu-id="326e9-119">[Filtry výjimek](#exception-filters):</span><span class="sxs-lookup"><span data-stu-id="326e9-119">[Exception filters](#exception-filters):</span></span>
    - <span data-ttu-id="326e9-120">Můžete zachytit výrazy na základě vlastností výjimku nebo jiný stav programu.</span><span class="sxs-lookup"><span data-stu-id="326e9-120">You can catch expressions based on properties of the exception or other program state.</span></span> 
* <span data-ttu-id="326e9-121">[nameof výrazy](#nameof-expressions):</span><span class="sxs-lookup"><span data-stu-id="326e9-121">[nameof Expressions](#nameof-expressions):</span></span>
    - <span data-ttu-id="326e9-122">Můžete je nechat kompilátoru generovat řetězcové vyjádření symbolů.</span><span class="sxs-lookup"><span data-stu-id="326e9-122">You can let the compiler generate string representations of symbols.</span></span>
* <span data-ttu-id="326e9-123">[await v catch a nakonec blokuje](#await-in-catch-and-finally-blocks):</span><span class="sxs-lookup"><span data-stu-id="326e9-123">[await in catch and finally blocks](#await-in-catch-and-finally-blocks):</span></span>
    - <span data-ttu-id="326e9-124">Můžete použít `await` výrazy v umístění, které dříve je zakázána.</span><span class="sxs-lookup"><span data-stu-id="326e9-124">You can use `await` expressions in locations that previously disallowed them.</span></span>
* <span data-ttu-id="326e9-125">[index inicializátory](#index-initializers):</span><span class="sxs-lookup"><span data-stu-id="326e9-125">[index initializers](#index-initializers):</span></span>
    - <span data-ttu-id="326e9-126">Můžete vytvářet inicializace výrazy pro asociativní kontejnery, jakož i kontejnery pořadí.</span><span class="sxs-lookup"><span data-stu-id="326e9-126">You can author initialization expressions for associative containers as well as sequence containers.</span></span>
* <span data-ttu-id="326e9-127">[Rozšiřující metody pro Inicializátory kolekcí](#extension-add-methods-in-collection-initializers):</span><span class="sxs-lookup"><span data-stu-id="326e9-127">[Extension methods for collection initializers](#extension-add-methods-in-collection-initializers):</span></span>
    - <span data-ttu-id="326e9-128">Inicializátory kolekcí může se spoléhat na dostupné rozšiřující metody, kromě metod člen.</span><span class="sxs-lookup"><span data-stu-id="326e9-128">Collection initializers can rely on accessible extension methods, in addition to member methods.</span></span>
* <span data-ttu-id="326e9-129">[Vylepšené rozlišení přetížení](#improved-overload-resolution):</span><span class="sxs-lookup"><span data-stu-id="326e9-129">[Improved overload resolution](#improved-overload-resolution):</span></span>
    - <span data-ttu-id="326e9-130">Některé konstruktory, které dříve generovány volání metod nejednoznačný nyní správně přeložit.</span><span class="sxs-lookup"><span data-stu-id="326e9-130">Some constructs that previously generated ambiguous method calls now resolve correctly.</span></span>

<span data-ttu-id="326e9-131">Celkový efekt těchto funkcí je psaní přesnější kód, který je také lépe čitelný.</span><span class="sxs-lookup"><span data-stu-id="326e9-131">The overall effect of these features is that you write more concise code that is also more readable.</span></span> <span data-ttu-id="326e9-132">Syntaxe obsahuje menší procedury pro mnoho běžné postupy.</span><span class="sxs-lookup"><span data-stu-id="326e9-132">The syntax contains less ceremony for many common practices.</span></span> <span data-ttu-id="326e9-133">Je snazší zjistit záměr návrh s menší procedury.</span><span class="sxs-lookup"><span data-stu-id="326e9-133">It's easier to see the design intent with less ceremony.</span></span> <span data-ttu-id="326e9-134">Tyto funkce a další a budete zvýšit produktivitu, napsat srozumitelnější kód a více soustředit na základní funkce, než na konstrukce jazyka.</span><span class="sxs-lookup"><span data-stu-id="326e9-134">Learn these features well, and you'll be more productive, write more readable code, and concentrate more on your core features than on the constructs of the language.</span></span>

<span data-ttu-id="326e9-135">Zbývající část tohoto tématu poskytuje podrobné informace o jednotlivých funkcí.</span><span class="sxs-lookup"><span data-stu-id="326e9-135">The remainder of this topic provides details on each of these features.</span></span>

## <a name="auto-property-enhancements"></a><span data-ttu-id="326e9-136">Vylepšení automatického – vlastnost</span><span class="sxs-lookup"><span data-stu-id="326e9-136">Auto-Property enhancements</span></span> 

<span data-ttu-id="326e9-137">Syntaxe automaticky implementované vlastnosti (obvykle označuje jako 'auto vlastnosti') provedené velmi snadné vytváření vlastnosti, které měl jednoduché get a nastavení přístupových objektů:</span><span class="sxs-lookup"><span data-stu-id="326e9-137">The syntax for automatically implemented properties (usually referred to as 'auto-properties') made it very easy to create properties that had simple get and set accessors:</span></span>

[!code-csharp[ClassicAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicAutoProperty)]

<span data-ttu-id="326e9-138">Tento jednoduchý syntaktický však omezenou druhy vzorů, které může podporovat použití automatického vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="326e9-138">However, this simple syntax limited the kinds of designs you could support using auto-properties.</span></span> <span data-ttu-id="326e9-139">C# 6 vylepšuje možnosti automatického vlastnosti tak, aby je mohli používat další způsoby.</span><span class="sxs-lookup"><span data-stu-id="326e9-139">C# 6 improves the auto-properties capabilities so that you can use them in more scenarios.</span></span> <span data-ttu-id="326e9-140">Nebudete muset přejít na podrobnější syntaxe deklarace a manipulace s nimi pole Základní ručně tak často.</span><span class="sxs-lookup"><span data-stu-id="326e9-140">You won't need to fall back on the more verbose syntax of declaring and manipulating the backing field by hand so often.</span></span>

<span data-ttu-id="326e9-141">Nové syntaxe adresy scénáře vlastnosti jen pro čtení a inicializace proměnné úložiště za auto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="326e9-141">The new syntax addresses scenarios for read-only properties, and for initializing the variable storage behind an auto-property.</span></span>

### <a name="read-only-auto-properties"></a><span data-ttu-id="326e9-142">Auto vlastnosti jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="326e9-142">Read-only auto-properties</span></span>

<span data-ttu-id="326e9-143">*Auto vlastnosti jen pro čtení* poskytnout přesnější syntaxe k vytvoření nedá změnit typy.</span><span class="sxs-lookup"><span data-stu-id="326e9-143">*Read-only auto-properties* provide a more concise syntax to create immutable types.</span></span> <span data-ttu-id="326e9-144">Na nejbližší, které může dojít k neměnné typy v dřívějších verzích systému C# byla deklarovat privátní setter:</span><span class="sxs-lookup"><span data-stu-id="326e9-144">The closest you could get to immutable types in earlier versions of C# was to declare private setters:</span></span>

[!code-csharp[ClassicReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicReadOnlyAutoProperty)]
 
<span data-ttu-id="326e9-145">Pomocí této syntaxe, kompilátor není zajistěte, aby byl typ skutečně neměnné.</span><span class="sxs-lookup"><span data-stu-id="326e9-145">Using this syntax, the compiler doesn't ensure that the type really is immutable.</span></span> <span data-ttu-id="326e9-146">Pouze vynucuje, který `FirstName` a `LastName` vlastnosti nejsou změnit tak, že žádný kód mimo třídu.</span><span class="sxs-lookup"><span data-stu-id="326e9-146">It only enforces that the `FirstName` and `LastName` properties are not modified from any code outside the class.</span></span>

<span data-ttu-id="326e9-147">Hodnota true, jen pro čtení chování povolit automatické – vlastnosti jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="326e9-147">Read-only auto-properties enable true read-only behavior.</span></span> <span data-ttu-id="326e9-148">Je s pouze přistupující deklarovat vlastnost automaticky:</span><span class="sxs-lookup"><span data-stu-id="326e9-148">You declare the auto-property with only a get accessor:</span></span>

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

<span data-ttu-id="326e9-149">`FirstName` a `LastName` vlastnosti lze nastavit pouze v těle konstruktor:</span><span class="sxs-lookup"><span data-stu-id="326e9-149">The `FirstName` and `LastName` properties can be set only in the body of a constructor:</span></span>

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

<span data-ttu-id="326e9-150">Při operaci set `LastName` v jiné metody generuje `CS0200` došlo k chybě kompilace:</span><span class="sxs-lookup"><span data-stu-id="326e9-150">Trying to set `LastName` in another method generates a `CS0200` compilation error:</span></span>

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

<span data-ttu-id="326e9-151">Tato funkce umožňuje true jazyková podpora pro vytváření neměnné typy a pomocí syntaxe zkracují a pohodlný vlastnost automaticky.</span><span class="sxs-lookup"><span data-stu-id="326e9-151">This feature enables true language support for creating immutable types and using the more concise and convenient auto-property syntax.</span></span>

### <a name="auto-property-initializers"></a><span data-ttu-id="326e9-152">Inicializátory automaticky – vlastnost</span><span class="sxs-lookup"><span data-stu-id="326e9-152">Auto-Property Initializers</span></span>

<span data-ttu-id="326e9-153">*Inicializátory automaticky vlastnost* umožňují deklarovat počáteční hodnota auto-vlastnosti jako součást deklarace vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="326e9-153">*Auto-Property Initializers* let you declare the initial value for an auto-property as part of the property declaration.</span></span>  <span data-ttu-id="326e9-154">V dřívějších verzích tyto vlastnosti třeba, aby měl setter a museli byste se inicializovat úložiště dat používá pole zálohování pomocí tohoto nastavení.</span><span class="sxs-lookup"><span data-stu-id="326e9-154">In earlier versions, these properties would need to have setters and you would need to use that setter to initialize the data storage used by the backing field.</span></span> <span data-ttu-id="326e9-155">Vezměte v úvahu tato třída pro studenty, který obsahuje název a seznam tříd Studentova:</span><span class="sxs-lookup"><span data-stu-id="326e9-155">Consider this class for a student that contains the name and a list of the student's grades:</span></span>

[!code-csharp[Construction](../../../samples/snippets/csharp/new-in-6/oldcode.cs#Construction)]
 
<span data-ttu-id="326e9-156">S růstem této třídy může zahrnovat další konstruktory.</span><span class="sxs-lookup"><span data-stu-id="326e9-156">As this class grows, you may include other constructors.</span></span> <span data-ttu-id="326e9-157">Každý konstruktor musí inicializovat toto pole, nebo budete zavádět chyby.</span><span class="sxs-lookup"><span data-stu-id="326e9-157">Each constructor needs to initialize this field, or you'll introduce errors.</span></span>

<span data-ttu-id="326e9-158">C# 6 umožňuje přiřadit počáteční hodnotu pro úložiště používá vlastnost automaticky v deklaraci automaticky vlastnost:</span><span class="sxs-lookup"><span data-stu-id="326e9-158">C# 6 enables you to assign an initial value for the storage used by an auto-property in the auto-property declaration:</span></span>

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

<span data-ttu-id="326e9-159">`Grades` Člen je inicializován, kde je deklarován.</span><span class="sxs-lookup"><span data-stu-id="326e9-159">The `Grades` member is initialized where it is declared.</span></span> <span data-ttu-id="326e9-160">Který usnadňuje provést inicializaci právě jednou.</span><span class="sxs-lookup"><span data-stu-id="326e9-160">That makes it easier to perform the initialization exactly once.</span></span> <span data-ttu-id="326e9-161">Inicializace je součástí deklarace vlastnosti, což usnadňuje označení rovnosti přidělení úložiště s veřejné rozhraní pro `Student` objekty.</span><span class="sxs-lookup"><span data-stu-id="326e9-161">The initialization is part of the property declaration, making it easier to equate the storage allocation with public interface for `Student` objects.</span></span>

<span data-ttu-id="326e9-162">Inicializátory vlastnost lze použít s vlastností čtení/zápisu a také vlastnosti jen pro čtení, jak je uvedené v tomto poli.</span><span class="sxs-lookup"><span data-stu-id="326e9-162">Property Initializers can be used with read/write properties as well as read-only properties, as shown here.</span></span>

[!code-csharp[ReadWriteInitialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadWriteInitialization)]

## <a name="expression-bodied-function-members"></a><span data-ttu-id="326e9-163">Výraz vozidlo funkce členy</span><span class="sxs-lookup"><span data-stu-id="326e9-163">Expression-bodied function members</span></span>

<span data-ttu-id="326e9-164">Tělo mnoho členů, které jsme zapsat obsahovat pouze jeden příkaz, který může být reprezentován jako výraz.</span><span class="sxs-lookup"><span data-stu-id="326e9-164">The body of a lot of members that we write consist of only one statement that can be represented as an expression.</span></span> <span data-ttu-id="326e9-165">Zápisem člena výraz vozidlo místo toho můžete snížit této syntaxe.</span><span class="sxs-lookup"><span data-stu-id="326e9-165">You can reduce that syntax by writing an expression-bodied member instead.</span></span> <span data-ttu-id="326e9-166">Funguje pro metody a vlastnosti jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="326e9-166">It works for methods and read-only properties.</span></span> <span data-ttu-id="326e9-167">Například přepsání `ToString()` je často skvělé kandidátem:</span><span class="sxs-lookup"><span data-stu-id="326e9-167">For example, an override of `ToString()` is often a great candidate:</span></span>

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

<span data-ttu-id="326e9-168">V také vlastnosti jen pro čtení můžete použít také výraz vozidlo členy:</span><span class="sxs-lookup"><span data-stu-id="326e9-168">You can also use expression-bodied members in read-only properties as well:</span></span>

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

## <a name="using-static"></a><span data-ttu-id="326e9-169">pomocí statické</span><span class="sxs-lookup"><span data-stu-id="326e9-169">using static</span></span>

<span data-ttu-id="326e9-170">*Pomocí statické* vylepšení umožňuje importovat statické metody třídy jednu třídu.</span><span class="sxs-lookup"><span data-stu-id="326e9-170">The *using static* enhancement enables you to import the static methods of a single class.</span></span> <span data-ttu-id="326e9-171">Dříve `using` příkaz naimportovány všechny typy v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="326e9-171">Previously, the `using` statement imported all types in a namespace.</span></span> 

<span data-ttu-id="326e9-172">Statické metody třídy se často používáme v našem kódu.</span><span class="sxs-lookup"><span data-stu-id="326e9-172">Often we use a class' static methods throughout our code.</span></span> <span data-ttu-id="326e9-173">Opakovaně zadáním názvu třídy mohou skrývat význam kódu.</span><span class="sxs-lookup"><span data-stu-id="326e9-173">Repeatedly typing the class name can obscure the meaning of your code.</span></span> <span data-ttu-id="326e9-174">Běžným příkladem jsou při psaní třídy, které provádějí mnoho číselné výpočty.</span><span class="sxs-lookup"><span data-stu-id="326e9-174">A common example is when you write classes that perform many numeric calculations.</span></span>
<span data-ttu-id="326e9-175">Váš kód podestlána <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> a další volání různé metody v <xref:System.Math> třídy.</span><span class="sxs-lookup"><span data-stu-id="326e9-175">Your code will be littered with <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> and other calls to different methods in the <xref:System.Math> class.</span></span> <span data-ttu-id="326e9-176">Nové `using static` syntaxe provádět tyto třídy mnohem čisticí ke čtení.</span><span class="sxs-lookup"><span data-stu-id="326e9-176">The new `using static` syntax can make these classes much cleaner to read.</span></span> <span data-ttu-id="326e9-177">Zadejte třídu, kterou používáte:</span><span class="sxs-lookup"><span data-stu-id="326e9-177">You specify the class you're using:</span></span>

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<span data-ttu-id="326e9-178">A teď můžete použít libovolnou statickou metodu v <xref:System.Math> třída bez kvalifikace <xref:System.Math> třídy.</span><span class="sxs-lookup"><span data-stu-id="326e9-178">And now, you can use any static method in the <xref:System.Math> class without qualifying the <xref:System.Math> class.</span></span> <span data-ttu-id="326e9-179"><xref:System.Math> Třída je případ skvělé použití pro tuto funkci, protože neobsahuje žádné instance metody.</span><span class="sxs-lookup"><span data-stu-id="326e9-179">The <xref:System.Math> class is a great use case for this feature because it does not contain any instance methods.</span></span> <span data-ttu-id="326e9-180">Můžete také použít `using static` k importu třída statické metody pro třídu, která má statické a instance metody.</span><span class="sxs-lookup"><span data-stu-id="326e9-180">You can also use `using static` to import a class' static methods for a class that has both static and instance methods.</span></span> <span data-ttu-id="326e9-181">Jedním z příkladů je nejvhodnější je <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="326e9-181">One of the most useful examples is <xref:System.String>:</span></span>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> <span data-ttu-id="326e9-182">Je nutné použít plně kvalifikovaný název, `System.String` v statického pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="326e9-182">You must use the fully qualified class name, `System.String` in a static using statement.</span></span> <span data-ttu-id="326e9-183">Nelze použít `string` – klíčové slovo místo.</span><span class="sxs-lookup"><span data-stu-id="326e9-183">You cannot use the `string` keyword instead.</span></span> 

<span data-ttu-id="326e9-184">Nyní můžete volat statické metody definované v <xref:System.String> třída bez kvalifikace tyto metody jako členy této třídy:</span><span class="sxs-lookup"><span data-stu-id="326e9-184">You can now call static methods defined in the <xref:System.String> class without qualifying those methods as members of that class:</span></span>

[!code-csharp[UsingStaticString](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticString)]

<span data-ttu-id="326e9-185">`static using` Funkce a rozšíření metody pracovat zajímavými způsoby a jazyk návrhu zahrnuté některá pravidla, které konkrétně řeší tyto interakce.</span><span class="sxs-lookup"><span data-stu-id="326e9-185">The `static using` feature and extension methods interact in interesting ways, and the language design included some rules that specifically address those interactions.</span></span> <span data-ttu-id="326e9-186">Cílem je, chcete-li minimalizovat žádné pravděpodobnost nejnovější změny v existující základy kódu, včetně vašeho.</span><span class="sxs-lookup"><span data-stu-id="326e9-186">The goal is to minimize any chances of breaking changes in existing codebases, including yours.</span></span>

<span data-ttu-id="326e9-187">Rozšiřující metody jsou pouze v oboru při volání pomocí syntaxe volání metody rozšíření, ne v případě, že se říká statickou metodu.</span><span class="sxs-lookup"><span data-stu-id="326e9-187">Extension methods are only in scope when called using the extension method invocation syntax, not when called as a static method.</span></span>
<span data-ttu-id="326e9-188">To se často zobrazí v dotazech LINQ.</span><span class="sxs-lookup"><span data-stu-id="326e9-188">You'll often see this in LINQ queries.</span></span> <span data-ttu-id="326e9-189">Můžete importovat vzoru LINQ importováním <xref:System.Linq.Enumerable>.</span><span class="sxs-lookup"><span data-stu-id="326e9-189">You can import the LINQ pattern by importing <xref:System.Linq.Enumerable>.</span></span>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

<span data-ttu-id="326e9-190">To importuje všechny metody v <xref:System.Linq.Enumerable> třídy.</span><span class="sxs-lookup"><span data-stu-id="326e9-190">This imports all the methods in the <xref:System.Linq.Enumerable> class.</span></span>
<span data-ttu-id="326e9-191">Rozšiřující metody jsou však pouze v oboru při volání jako rozšiřující metody.</span><span class="sxs-lookup"><span data-stu-id="326e9-191">However, the extension methods are only in scope when called as extension methods.</span></span> <span data-ttu-id="326e9-192">Nejsou v oboru Pokud jsou volány pomocí syntaxe statickou metodu:</span><span class="sxs-lookup"><span data-stu-id="326e9-192">They are not in scope if they are called using the static method syntax:</span></span>

[!code-csharp[UsingStaticLinqMethod](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticLinkMethod)]

<span data-ttu-id="326e9-193">Toto rozhodnutí totiž rozšiřující metody jsou obvykle nazývá pomocí výrazů volání metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="326e9-193">This decision is because extension methods are typically called using extension method invocation expressions.</span></span> <span data-ttu-id="326e9-194">Ve výjimečných případu, kdy jsou volány pomocí statickou metodu volejte syntaxe je vyřešit nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="326e9-194">In the rare case where they are called using the static method call syntax it is to resolve ambiguity.</span></span>
<span data-ttu-id="326e9-195">Vyžadování název třídy jako součást volání zdá se, že vhodné.</span><span class="sxs-lookup"><span data-stu-id="326e9-195">Requiring the class name as part of the invocation seems wise.</span></span>

<span data-ttu-id="326e9-196">Je poslední funkce z `static using`.</span><span class="sxs-lookup"><span data-stu-id="326e9-196">There's one last feature of `static using`.</span></span> <span data-ttu-id="326e9-197">`static using` – Direktiva také importuje všechny vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="326e9-197">The `static using` directive also imports any nested types.</span></span> <span data-ttu-id="326e9-198">Můžete odkazovat všechny vnořené typy bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="326e9-198">That enables you to reference any nested types without qualification.</span></span>

## <a name="null-conditional-operators"></a><span data-ttu-id="326e9-199">Podmíněné operátory s Null</span><span class="sxs-lookup"><span data-stu-id="326e9-199">Null-conditional operators</span></span>

<span data-ttu-id="326e9-200">Hodnoty Null zkomplikovat kódu.</span><span class="sxs-lookup"><span data-stu-id="326e9-200">Null values complicate code.</span></span> <span data-ttu-id="326e9-201">Je potřeba zkontrolovat každých přístup proměnných zajistit nejsou vyhodnocení `null`.</span><span class="sxs-lookup"><span data-stu-id="326e9-201">You need to check every access of variables to ensure you are not dereferencing `null`.</span></span> <span data-ttu-id="326e9-202">*Null podmíněný operátor* díky ty kontroly mnohem snazší a plynulá práce.</span><span class="sxs-lookup"><span data-stu-id="326e9-202">The *null conditional operator* makes those checks much easier and fluid.</span></span>

<span data-ttu-id="326e9-203">Jednoduše nahradit přístup ke členu `.` s `?.`:</span><span class="sxs-lookup"><span data-stu-id="326e9-203">Simply replace the member access `.` with `?.`:</span></span>

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

<span data-ttu-id="326e9-204">V předchozím příkladu, proměnná `first` je přiřazen `null` Pokud je objekt osoba `null`.</span><span class="sxs-lookup"><span data-stu-id="326e9-204">In the preceding example, the variable `first` is assigned `null` if the person object is `null`.</span></span> <span data-ttu-id="326e9-205">Jinak, získá přiřadí hodnota `FirstName` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="326e9-205">Otherwise, it gets assigned the value of the `FirstName` property.</span></span> <span data-ttu-id="326e9-206">Co je nejdůležitější `?.` znamená, že tento řádek kódu negeneruje `NullReferenceException` při `person` proměnná `null`.</span><span class="sxs-lookup"><span data-stu-id="326e9-206">Most importantly, the `?.` means that this line of code does not generate a `NullReferenceException` when the `person` variable is `null`.</span></span> <span data-ttu-id="326e9-207">Místo toho zkratům a vytváří `null`.</span><span class="sxs-lookup"><span data-stu-id="326e9-207">Instead, it short-circuits and produces `null`.</span></span>

<span data-ttu-id="326e9-208">Také Upozorňujeme, že tento výraz vrátí `string`, bez ohledu na to hodnota `person`.</span><span class="sxs-lookup"><span data-stu-id="326e9-208">Also, note that this expression returns a `string`, regardless of the value of `person`.</span></span>
<span data-ttu-id="326e9-209">V případě krátké circuiting `null` hodnota vrácená je zadán tak, aby odpovídaly úplné výraz.</span><span class="sxs-lookup"><span data-stu-id="326e9-209">In the case of short circuiting, the `null` value returned is typed to match the full expression.</span></span>

<span data-ttu-id="326e9-210">Často můžete použít tento konstrukce s *null slučování* operátor přiřadit výchozí hodnoty, když jedna z vlastností `null`:</span><span class="sxs-lookup"><span data-stu-id="326e9-210">You can often use this construct with the *null coalescing* operator to assign default values when one of the properties are `null`:</span></span>

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

<span data-ttu-id="326e9-211">Operand pravé straně `?.` operátor není omezen na vlastnosti nebo pole.</span><span class="sxs-lookup"><span data-stu-id="326e9-211">The right hand side operand of the `?.` operator is not limited to properties or fields.</span></span>
<span data-ttu-id="326e9-212">Můžete ji použít i podmíněně volat metody.</span><span class="sxs-lookup"><span data-stu-id="326e9-212">You can also use it to conditionally invoke methods.</span></span> <span data-ttu-id="326e9-213">Se nejčastěji používá členských funkcí s hodnotou null podmíněný operátor bezpečně volat delegáti (nebo obslužné rutiny událostí), může být `null`.</span><span class="sxs-lookup"><span data-stu-id="326e9-213">The most common use of member functions with the null conditional operator is to safely invoke delegates (or event handlers) that may be `null`.</span></span>  <span data-ttu-id="326e9-214">Můžete to udělat pomocí volání metody delegáta `Invoke` metoda pomocí `?.` operátor pro přístup k členovi.</span><span class="sxs-lookup"><span data-stu-id="326e9-214">You'll do this by calling the delegate's `Invoke` method using the `?.` operator to access the member.</span></span> <span data-ttu-id="326e9-215">Můžete zobrazit příklad v</span><span class="sxs-lookup"><span data-stu-id="326e9-215">You can see an example in the</span></span>  
<span data-ttu-id="326e9-216">[Delegovat vzory](../delegates-patterns.md#handling-null-delegates) tématu.</span><span class="sxs-lookup"><span data-stu-id="326e9-216">[delegate patterns](../delegates-patterns.md#handling-null-delegates) topic.</span></span>

<span data-ttu-id="326e9-217">Pravidla `?.` operátor Ujistěte se, že je na levé straně operátoru vyhodnotit pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="326e9-217">The rules of the `?.` operator ensure that the left-hand side of the operator is evaluated only once.</span></span> <span data-ttu-id="326e9-218">To je důležité a umožňuje mnoho idioms, včetně příklad pomocí obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="326e9-218">This is important and enables many idioms, including the example using event handlers.</span></span> <span data-ttu-id="326e9-219">Začněme využití obslužná rutina události.</span><span class="sxs-lookup"><span data-stu-id="326e9-219">Let's start with the event handler usage.</span></span> <span data-ttu-id="326e9-220">V předchozích verzích jazyka C# byli vyzváni k zápisu kódu takto:</span><span class="sxs-lookup"><span data-stu-id="326e9-220">In previous versions of C#, you were encouraged to write code like this:</span></span>

```csharp
var handler = this.SomethingHappened;
if (handler != null)
    handler(this, eventArgs);
```

<span data-ttu-id="326e9-221">To se upřednostňované přes jednodušší syntaxe:</span><span class="sxs-lookup"><span data-stu-id="326e9-221">This was preferred over a simpler syntax:</span></span>

```csharp
// Not recommended
if (this.SomethingHappened != null)
    this.SomethingHappened(this, eventArgs);
```

> [!IMPORTANT]
> <span data-ttu-id="326e9-222">V předchozím příkladu představuje časování.</span><span class="sxs-lookup"><span data-stu-id="326e9-222">The preceding example introduces a race condition.</span></span> <span data-ttu-id="326e9-223">`SomethingHappened` Událost může mít Odběratelé, kteří v případě zaškrtnutí proti `null`, a tyto odběratele byl odebrán předtím, než se vyvolá událost.</span><span class="sxs-lookup"><span data-stu-id="326e9-223">The `SomethingHappened` event may have subscribers when checked against `null`, and those subscribers may have been removed before the event is raised.</span></span> <span data-ttu-id="326e9-224">By to způsobilo <xref:System.NullReferenceException> vyvolání.</span><span class="sxs-lookup"><span data-stu-id="326e9-224">That would cause a <xref:System.NullReferenceException> to be thrown.</span></span>

<span data-ttu-id="326e9-225">V této verzi druhý `SomethingHappened` obslužné rutiny události může obsahovat hodnotu null při testování, ale pokud jiný kód odebere obslužnou rutinu, ho může mít hodnotu null při volání obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="326e9-225">In this second version, the `SomethingHappened` event handler might be non-null when tested, but if other code removes a handler, it could still be null when the event handler was called.</span></span>

<span data-ttu-id="326e9-226">Generuje kód pro kompilátor `?.` operátor, který zajišťuje na levé straně (`this.SomethingHappened`) z `?.` výraz vyhodnocen jednou a výsledek je uložený v mezipaměti:</span><span class="sxs-lookup"><span data-stu-id="326e9-226">The compiler generates code for the `?.` operator that ensures the left side (`this.SomethingHappened`) of the `?.` expression is evaluated once, and the result is cached:</span></span>

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

<span data-ttu-id="326e9-227">Zajištění, že je na levé straně vyhodnotit pouze jednou můžete také použít libovolný výraz, včetně volání metod, na levé straně `?.` i v případě, že musí vedlejší účinky, jsou vyhodnocovány jednou, takže vedlejší účinky nastane jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="326e9-227">Ensuring that the left side is evaluated only once also enables you to use any expression, including method calls, on the left side of the `?.` Even if these have side-effects, they are evaluated once, so the side effects occur only once.</span></span> <span data-ttu-id="326e9-228">Můžete zobrazit příklad v našem obsahu na [události](../events-overview.md#language-support-for-events).</span><span class="sxs-lookup"><span data-stu-id="326e9-228">You can see an example in our content on [events](../events-overview.md#language-support-for-events).</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="326e9-229">Řetězec interpolace</span><span class="sxs-lookup"><span data-stu-id="326e9-229">String Interpolation</span></span>

<span data-ttu-id="326e9-230">C# 6 obsahuje nové syntaxe pro sestavování řetězců z formátovacího řetězce a výrazy, které se vyhodnocují k vytvoření dalších řetězcové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="326e9-230">C# 6 contains new syntax for composing strings from a format string and expressions that are evaluated to produce other string values.</span></span>

<span data-ttu-id="326e9-231">Tradičně, je potřeba k použití poziční parametry v metodě jako `string.Format`:</span><span class="sxs-lookup"><span data-stu-id="326e9-231">Traditionally, you needed to use positional parameters in a method like `string.Format`:</span></span>

[!code-csharp[stringFormat](../../../samples/snippets/csharp/new-in-6/oldcode.cs#stringFormat)]

<span data-ttu-id="326e9-232">S C# 6 nové [řetězec interpolace](../language-reference/tokens/interpolated.md) funkce umožňuje vložení výrazů do řetězce formátu.</span><span class="sxs-lookup"><span data-stu-id="326e9-232">With C# 6, the new [string interpolation](../language-reference/tokens/interpolated.md) feature enables you to embed the expressions in the format string.</span></span> <span data-ttu-id="326e9-233">Jednoduše adresa řetězec s `$`:</span><span class="sxs-lookup"><span data-stu-id="326e9-233">Simply preface the string with `$`:</span></span>

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="326e9-234">Tento počáteční příklad používá vlastnost výrazy pro nahrazovanou výrazy.</span><span class="sxs-lookup"><span data-stu-id="326e9-234">This initial example uses property expressions for the substituted expressions.</span></span> <span data-ttu-id="326e9-235">Můžete rozbalit na tuto syntaxi použít jakýkoli výraz.</span><span class="sxs-lookup"><span data-stu-id="326e9-235">You can expand on this syntax to use any expression.</span></span> <span data-ttu-id="326e9-236">Například může výpočetní Studentova průměr studijních jako součást interpolace:</span><span class="sxs-lookup"><span data-stu-id="326e9-236">For example, you could compute a student's grade point average as part of the interpolation:</span></span>

[!code-csharp[stringInterpolationExpression](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationExpression)]

<span data-ttu-id="326e9-237">Spuštěný v předchozím příkladu, by zjistíte, že výstup `Grades.Average()` může mít většího počtu desetinných míst, než byste chtěli.</span><span class="sxs-lookup"><span data-stu-id="326e9-237">Running the preceding example, you would find that the output for `Grades.Average()` might have more decimal places than you would like.</span></span> <span data-ttu-id="326e9-238">Syntaxe interpolace řetězec podporuje všechny na formát řetězce k dispozici pomocí dříve formátování metody.</span><span class="sxs-lookup"><span data-stu-id="326e9-238">The string interpolation syntax supports all the format strings available using earlier formatting methods.</span></span> <span data-ttu-id="326e9-239">Můžete přidat řetězce formátu uvnitř složené závorky.</span><span class="sxs-lookup"><span data-stu-id="326e9-239">You add the format strings inside the braces.</span></span> <span data-ttu-id="326e9-240">Přidat `:` následující výraz, který se formátu:</span><span class="sxs-lookup"><span data-stu-id="326e9-240">Add a `:` following the expression to format:</span></span>

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

<span data-ttu-id="326e9-241">Naformátuje hodnotu pro předchozí řádek kódu `Grades.Average()` jako číslo s plovoucí desetinnou čárkou se dvěma desetinnými místy.</span><span class="sxs-lookup"><span data-stu-id="326e9-241">The preceding line of code formats the value for `Grades.Average()` as a floating-point number with two decimal places.</span></span>

<span data-ttu-id="326e9-242">`:` Vždy interpretována jako oddělovač mezi výraz, který je formátován a řetězec formátu.</span><span class="sxs-lookup"><span data-stu-id="326e9-242">The `:` is always interpreted as the separator between the expression being formatted and the format string.</span></span> <span data-ttu-id="326e9-243">To může nastat problémy při výraz používá `:` jiným způsobem, jako je například podmíněný operátor:</span><span class="sxs-lookup"><span data-stu-id="326e9-243">This can introduce problems when your expression uses a `:` in another way, such as a conditional operator:</span></span>

```csharp
public string GetGradePointPercentages() =>
    $"Name: {LastName}, {FirstName}. G.P.A: {Grades.Any() ? Grades.Average() : double.NaN:F2}";
```

<span data-ttu-id="326e9-244">V předchozím příkladu `:` je analyzovat jako začátek řetězec formátu, nejsou součástí podmíněný operátor.</span><span class="sxs-lookup"><span data-stu-id="326e9-244">In the preceding example, the `:` is parsed as the beginning of the format string, not part of the conditional operator.</span></span> <span data-ttu-id="326e9-245">Ve všech případech, kdy k tomu dojde je nutné uvést výrazu v závorkách vynutit kompilátoru interpretovat výraz jako, který chcete:</span><span class="sxs-lookup"><span data-stu-id="326e9-245">In all cases where this happens, you can surround the expression with parentheses to force the compiler to interpret the expression as you intend:</span></span>

[!code-csharp[stringInterpolationConditional](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationConditional)]

<span data-ttu-id="326e9-246">Nejsou k dispozici žádné omezení na výrazy, které můžete umístit mezi složenými závorkami.</span><span class="sxs-lookup"><span data-stu-id="326e9-246">There aren't any limitations on the expressions you can place between the braces.</span></span> <span data-ttu-id="326e9-247">Můžete provést komplexní dotaz LINQ uvnitř řetězec interpolované k provádění výpočtů a zobrazit výsledek:</span><span class="sxs-lookup"><span data-stu-id="326e9-247">You can execute a complex LINQ query inside an interpolated string to perform computations and display the result:</span></span>

[!code-csharp[stringInterpolationLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationLinq)]

<span data-ttu-id="326e9-248">Zobrazí se od této ukázky můžete dokonce vkládat řetězcového výrazu interpolace uvnitř jiného výrazu interpolace řetězec.</span><span class="sxs-lookup"><span data-stu-id="326e9-248">You can see from this sample that you can even nest a string interpolation expression inside another string interpolation expression.</span></span> <span data-ttu-id="326e9-249">V tomto příkladu je velmi pravděpodobné, by měly být složitější než jste v produkčním kódu.</span><span class="sxs-lookup"><span data-stu-id="326e9-249">This example is very likely more complex than you would want in production code.</span></span>
<span data-ttu-id="326e9-250">Místo toho je ilustrativní šířky funkci.</span><span class="sxs-lookup"><span data-stu-id="326e9-250">Rather, it is illustrative of the breadth of the feature.</span></span> <span data-ttu-id="326e9-251">Jakýkoli výraz jazyka C# mohou být umístěny ve složených závorkách interpolované řetězce.</span><span class="sxs-lookup"><span data-stu-id="326e9-251">Any C# expression can be placed between the curly braces of an interpolated string.</span></span>

### <a name="string-interpolation-and-specific-cultures"></a><span data-ttu-id="326e9-252">Řetězec interpolace a konkrétní jazykové verze</span><span class="sxs-lookup"><span data-stu-id="326e9-252">String interpolation and specific cultures</span></span>

<span data-ttu-id="326e9-253">Všechny příklady uvedené v předchozí části formátu řetězce pomocí aktuální jazykovou verzi a jazyka v počítači kde kód spustí.</span><span class="sxs-lookup"><span data-stu-id="326e9-253">All the examples shown in the preceding section format the strings using the current culture and language on the machine where the code executes.</span></span> <span data-ttu-id="326e9-254">Potřebujete často řetězec vytvořeného pomocí konkrétní jazykové verze formátu.</span><span class="sxs-lookup"><span data-stu-id="326e9-254">Often you may need to format the string produced using a specific culture.</span></span>
<span data-ttu-id="326e9-255">Pokud chcete provést, použijte ke skutečnosti, že objekt vyprodukované interpolace řetězec může být implicitně převedena na <xref:System.FormattableString>.</span><span class="sxs-lookup"><span data-stu-id="326e9-255">To do that use the fact that the object produced by a string interpolation can be implicitly converted to <xref:System.FormattableString>.</span></span>

<span data-ttu-id="326e9-256"><xref:System.FormattableString> Instance obsahuje řetězec formátu a výsledky vyhodnocení výrazů před jejich převádění na řetězce.</span><span class="sxs-lookup"><span data-stu-id="326e9-256">The <xref:System.FormattableString> instance contains the format string, and the results of evaluating the expressions before converting them to strings.</span></span> <span data-ttu-id="326e9-257">Můžete použít veřejné metody třídy <xref:System.FormattableString> zadat jazykovou verzi, při formátování řetězce.</span><span class="sxs-lookup"><span data-stu-id="326e9-257">You can use public methods of <xref:System.FormattableString> to specify the culture when formatting a string.</span></span> <span data-ttu-id="326e9-258">Například následující příklad vytvoří řetězec s využitím německé jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="326e9-258">For example, the following example produces a string using German culture.</span></span> <span data-ttu-id="326e9-259">(Používá znak ',' oddělovač desetinných míst a '.' tisíce znak oddělovače.)</span><span class="sxs-lookup"><span data-stu-id="326e9-259">(It uses the ',' character for the decimal separator, and the '.' character as the thousands separator.)</span></span>

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

<span data-ttu-id="326e9-260">Další informace najdete v tématu [řetězec interpolace](../language-reference/tokens/interpolated.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="326e9-260">For more information, see the [String interpolation](../language-reference/tokens/interpolated.md) topic.</span></span>

## <a name="exception-filters"></a><span data-ttu-id="326e9-261">Filtry výjimek</span><span class="sxs-lookup"><span data-stu-id="326e9-261">Exception Filters</span></span>

<span data-ttu-id="326e9-262">Další novou funkcí v C# 6 je *filtry výjimek*.</span><span class="sxs-lookup"><span data-stu-id="326e9-262">Another new feature in C# 6 is *exception filters*.</span></span> <span data-ttu-id="326e9-263">Filtry výjimek jsou klauzule, které určují, kdy se má použít klauzuli dané catch.</span><span class="sxs-lookup"><span data-stu-id="326e9-263">Exception Filters are clauses that determine when a given catch clause should be applied.</span></span>
<span data-ttu-id="326e9-264">Pokud se používá pro filtr výjimek vyhodnocen jako `true`, klauzuli catch provádí běžného zpracování výjimku.</span><span class="sxs-lookup"><span data-stu-id="326e9-264">If the expression used for an exception filter evaluates to `true`, the catch clause performs its normal processing on an exception.</span></span> <span data-ttu-id="326e9-265">Pokud je výsledkem výrazu `false`, pak se `catch` klauzule bylo přeskočeno.</span><span class="sxs-lookup"><span data-stu-id="326e9-265">If the expression evaluates to `false`, then the `catch` clause is skipped.</span></span>

<span data-ttu-id="326e9-266">Je jedno použití zjistit informace o výjimce k určení, zda `catch` klauzule může zpracovat výjimku:</span><span class="sxs-lookup"><span data-stu-id="326e9-266">One use is to examine information about an exception to determine if a `catch` clause can process the exception:</span></span>

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

<span data-ttu-id="326e9-267">Kód vygenerovaný filtry výjimek poskytuje lepší informace o výjimku, která je vyvolána a nebyl zpracován.</span><span class="sxs-lookup"><span data-stu-id="326e9-267">The code generated by exception filters provides better information about an exception that is thrown and not processed.</span></span> <span data-ttu-id="326e9-268">Před filtry výjimek byly přidány do jazyka, museli byste vytvořit kód takto:</span><span class="sxs-lookup"><span data-stu-id="326e9-268">Before exception filters were added to the language, you would need to create code like the following:</span></span>

[!code-csharp[ExceptionFilterOld](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilterOld)]

<span data-ttu-id="326e9-269">Bod, kde je vyvolána výjimka změny mezi tyto dva příklady.</span><span class="sxs-lookup"><span data-stu-id="326e9-269">The point where the exception is thrown changes between these two examples.</span></span>
<span data-ttu-id="326e9-270">V předchozí kód, kde `throw` klauzule, všechny analýzu trasování zásobníku nebo zkoumání výpisy stavu systému se zobrazí, zda byla výjimka vydána z `throw` příkaz v klauzuli vaší catch.</span><span class="sxs-lookup"><span data-stu-id="326e9-270">In the previous code, where a `throw` clause is used, any stack trace analysis or examination of crash dumps will show that the exception was thrown from the `throw` statement in your catch clause.</span></span> <span data-ttu-id="326e9-271">Objekt skutečné výjimky bude obsahovat původní zásobníku volání, ale všechny ostatní informace o všech proměnných v zásobníku volání mezi tento bod throw a umístění původního bodu throw bylo ztraceno.</span><span class="sxs-lookup"><span data-stu-id="326e9-271">The actual exception object will contain the original call stack, but all other information about any variables in the call stack between this throw point and the location of the original throw point has been lost.</span></span> 

<span data-ttu-id="326e9-272">Rozdíl oproti, zpracování kód pomocí filtru výjimek: výjimka výraz filtru se vyhodnocuje `false`.</span><span class="sxs-lookup"><span data-stu-id="326e9-272">Contrast that with how the code using an exception filter is processed: the exception filter expression evaluates to `false`.</span></span> <span data-ttu-id="326e9-273">Proto nikdy zadá provádění `catch` klauzule.</span><span class="sxs-lookup"><span data-stu-id="326e9-273">Therefore, execution never enters the `catch` clause.</span></span> <span data-ttu-id="326e9-274">Protože `catch` klauzule nepracuje, bez uvolnění zásobníku probíhá.</span><span class="sxs-lookup"><span data-stu-id="326e9-274">Because the `catch` clause does not execute, no stack unwinding takes place.</span></span> <span data-ttu-id="326e9-275">Pro všechny ladění aktivity, které by proběhnout později je zachovaná, throw znamená původní umístění.</span><span class="sxs-lookup"><span data-stu-id="326e9-275">That means the original throw location is preserved for any debugging activities that would take place later.</span></span>

<span data-ttu-id="326e9-276">Kdykoli budete potřebovat k vyhodnocení, pole nebo vlastnosti výjimky, aniž byste museli spoléhat výhradně na typ výjimky, použijte filtr výjimek pro zachování Další informace o ladění.</span><span class="sxs-lookup"><span data-stu-id="326e9-276">Whenever you need to evaluate fields or properties of an exception, instead of relying solely on the exception type, use an exception filter to preserve more debugging information.</span></span>

<span data-ttu-id="326e9-277">Další doporučené vzor s filtry výjimek je používat pro rutiny protokolování.</span><span class="sxs-lookup"><span data-stu-id="326e9-277">Another recommended pattern with exception filters is to use them for logging routines.</span></span> <span data-ttu-id="326e9-278">Toto použití také využívá způsobem, ve kterém je zachová bodem throw výjimky, i když se vyhodnocuje filtru výjimek `false`.</span><span class="sxs-lookup"><span data-stu-id="326e9-278">This usage also leverages the manner in which the exception throw point is preserved when an exception filter evaluates to `false`.</span></span>

<span data-ttu-id="326e9-279">Metoda protokolování by metodou, jehož argumentem je výjimka, která bezpodmínečně vrací `false`:</span><span class="sxs-lookup"><span data-stu-id="326e9-279">A logging method would be a method whose argument is the exception that unconditionally returns `false`:</span></span>

[!code-csharp[ExceptionFilterLogging](../../../samples/snippets/csharp/new-in-6/ExceptionFilterHelpers.cs#ExceptionFilterLogging)]

<span data-ttu-id="326e9-280">Vždy, když chcete k přihlášení k výjimce, můžete přidat klauzuli catch a použít tuto metodu jako filtr výjimek:</span><span class="sxs-lookup"><span data-stu-id="326e9-280">Whenever you want to log an exception, you can add a catch clause, and use this method as the exception filter:</span></span>

[!code-csharp[LogException](../../../samples/snippets/csharp/new-in-6/program.cs#LogException)]

<span data-ttu-id="326e9-281">Výjimky jsou nikdy zachycena, protože `LogException` metoda vždy vrátí hodnotu `false`.</span><span class="sxs-lookup"><span data-stu-id="326e9-281">The exceptions are never caught, because the `LogException` method always returns `false`.</span></span> <span data-ttu-id="326e9-282">Tento filtr výjimek vždy false znamená, že můžete umístit této obslužné rutiny protokolování před všechny ostatní obslužné rutiny výjimek:</span><span class="sxs-lookup"><span data-stu-id="326e9-282">That always false exception filter means that you can place this logging handler before any other exception handlers:</span></span>

[!code-csharp[LogExceptionRecovery](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionRecovery)]

<span data-ttu-id="326e9-283">V předchozím příkladu zvýrazňuje důležité omezující vlastnosti výjimky filtrů.</span><span class="sxs-lookup"><span data-stu-id="326e9-283">The preceding example highlights a very important facet of exception filters.</span></span>
<span data-ttu-id="326e9-284">Filtry výjimek povolit scénáře, kde může před více některou zobrazí další obecné klauzule catch výjimky.</span><span class="sxs-lookup"><span data-stu-id="326e9-284">The exception filters enable scenarios where a more general exception catch clause may appear before a more specific one.</span></span> <span data-ttu-id="326e9-285">Je také možné, že se zobrazí v více klauzulí catch stejného typu Výjimka:</span><span class="sxs-lookup"><span data-stu-id="326e9-285">It's also possible to have the same exception type appear in multiple catch clauses:</span></span>

[!code-csharp[HandleNotChanged](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#HandleNotChanged)]

<span data-ttu-id="326e9-286">Další doporučené vzor pomáhá zabránit klauzule catch – zpracování výjimek, pokud je připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="326e9-286">Another recommended pattern helps prevent catch clauses from processing exceptions when a debugger is attached.</span></span> <span data-ttu-id="326e9-287">Tento postup umožňuje spuštění aplikace s ladicím programem a zastavit provádění, když je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="326e9-287">This technique enables you to run an application with the debugger, and stop execution when an exception is thrown.</span></span>

<span data-ttu-id="326e9-288">V kódu přidejte filtr výjimek tak, aby všechny kód pro obnovení se provádí jenom v případě, že není připojen ladicí program:</span><span class="sxs-lookup"><span data-stu-id="326e9-288">In your code, add an exception filter so that any recovery code executes only when a debugger is not attached:</span></span>

[!code-csharp[LogExceptionDebugger](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionDebugger)]

<span data-ttu-id="326e9-289">Po přidání tohoto v kódu, můžete nastavit ladicí program na přerušení na všechny neošetřené výjimky.</span><span class="sxs-lookup"><span data-stu-id="326e9-289">After adding this in code, you set your debugger to break on all unhandled exceptions.</span></span> <span data-ttu-id="326e9-290">Ladicí program konce kdykoli a spusťte program v ladicím programu `PerformFailingOperation()` vyvolá `RecoverableException`.</span><span class="sxs-lookup"><span data-stu-id="326e9-290">Run the program under the debugger, and the debugger breaks whenever `PerformFailingOperation()` throws a `RecoverableException`.</span></span>
<span data-ttu-id="326e9-291">Ladicí program dělí program, protože klauzule catch nebudou provedeny z důvodu výjimky filtr vrací hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="326e9-291">The debugger breaks your program, because the catch clause won't be executed due to the false-returning exception filter.</span></span>

## <a name="nameof-expressions"></a><span data-ttu-id="326e9-292">`nameof` Výrazy</span><span class="sxs-lookup"><span data-stu-id="326e9-292">`nameof` Expressions</span></span>

<span data-ttu-id="326e9-293">`nameof` Výraz vyhodnocen jako název symbolu.</span><span class="sxs-lookup"><span data-stu-id="326e9-293">The `nameof` expression evaluates to the name of a symbol.</span></span> <span data-ttu-id="326e9-294">Je skvělým způsobem, jak získat nástroje práce kdykoli budete potřebovat název proměnné, vlastnost nebo pole členů.</span><span class="sxs-lookup"><span data-stu-id="326e9-294">It's a great way to get tools working whenever you need the name of a variable, a property, or a member field.</span></span>

<span data-ttu-id="326e9-295">Mezi nejběžnější používá pro `nameof` je poskytnout název symbol, který způsobil výjimku:</span><span class="sxs-lookup"><span data-stu-id="326e9-295">One of the most common uses for `nameof` is to provide the name of a symbol that caused an exception:</span></span>

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

<span data-ttu-id="326e9-296">Použití jiné je XAML na základě aplikací, které implementují `INotifyPropertyChanged` rozhraní:</span><span class="sxs-lookup"><span data-stu-id="326e9-296">Another use is with XAML based applications that implement the `INotifyPropertyChanged` interface:</span></span>

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

<span data-ttu-id="326e9-297">Výhodou použití `nameof` operátor přes konstantní řetězec je, že nástroje můžete porozumět symbolu.</span><span class="sxs-lookup"><span data-stu-id="326e9-297">The advantage of using the `nameof` operator over a constant string is that tools can understand the symbol.</span></span> <span data-ttu-id="326e9-298">Používáte-li přejmenovat symbol refaktoringu nástroje, můžete ho přejmenuje ho `nameof` výraz.</span><span class="sxs-lookup"><span data-stu-id="326e9-298">If you use refactoring tools to rename the symbol, it will rename it in the `nameof` expression.</span></span> <span data-ttu-id="326e9-299">Konstantní řetězce nemají této výhody.</span><span class="sxs-lookup"><span data-stu-id="326e9-299">Constant strings don't have that advantage.</span></span> <span data-ttu-id="326e9-300">Vyzkoušejte si to ve svém oblíbeném editoru: Přejmenovat proměnnou a všechna `nameof` výrazy se aktualizuje také.</span><span class="sxs-lookup"><span data-stu-id="326e9-300">Try it yourself in your favorite editor: rename a variable, and any `nameof` expressions will update as well.</span></span>

<span data-ttu-id="326e9-301">`nameof` Výraz vytvoří nekvalifikované název její argument (`LastName` v předchozích příkladech) i v případě, že používáte plně kvalifikovaný název pro argument:</span><span class="sxs-lookup"><span data-stu-id="326e9-301">The `nameof` expression produces the unqualified name of its argument (`LastName` in the previous examples) even if you use the fully qualified name for the argument:</span></span>

[!code-csharp[QualifiedNameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#QualifiedNameofNotify)]

<span data-ttu-id="326e9-302">To `nameof` výraz vytváří `FirstName`, nikoli `UXComponents.ViewModel.FirstName`.</span><span class="sxs-lookup"><span data-stu-id="326e9-302">This `nameof` expression produces `FirstName`, not `UXComponents.ViewModel.FirstName`.</span></span>

## <a name="await-in-catch-and-finally-blocks"></a><span data-ttu-id="326e9-303">Await v Catch a nakonec blokuje.</span><span class="sxs-lookup"><span data-stu-id="326e9-303">Await in Catch and Finally blocks</span></span>

<span data-ttu-id="326e9-304">C# 5 měl několik omezení kolem kam může být `await` výrazy.</span><span class="sxs-lookup"><span data-stu-id="326e9-304">C# 5 had several limitations around where you could place `await` expressions.</span></span>
<span data-ttu-id="326e9-305">Jeden z nich byla odebrána v C# 6.</span><span class="sxs-lookup"><span data-stu-id="326e9-305">One of those has been removed in C# 6.</span></span> <span data-ttu-id="326e9-306">Teď můžete použít `await` v `catch` nebo `finally` výrazy.</span><span class="sxs-lookup"><span data-stu-id="326e9-306">You can now use `await` in `catch` or `finally` expressions.</span></span> 

<span data-ttu-id="326e9-307">Přidání await výrazy v catch a nakonec bloky zdánlivě zkomplikovat ty zpracování.</span><span class="sxs-lookup"><span data-stu-id="326e9-307">The addition of await expressions in catch and finally blocks may appear to complicate how those are processed.</span></span> <span data-ttu-id="326e9-308">Přidejme příklad diskutovat o tom, jak se zobrazuje.</span><span class="sxs-lookup"><span data-stu-id="326e9-308">Let's add an example to discuss how this appears.</span></span> <span data-ttu-id="326e9-309">V žádné asynchronní metody, můžete použít výraz await v a nakonec klauzule.</span><span class="sxs-lookup"><span data-stu-id="326e9-309">In any async method, you can use an await expression in a finally clause.</span></span>

<span data-ttu-id="326e9-310">S C# 6 může také await ve výrazech catch.</span><span class="sxs-lookup"><span data-stu-id="326e9-310">With C# 6, you can also await in catch expressions.</span></span> <span data-ttu-id="326e9-311">Tato možnost se nejčastěji používá s scénáře protokolování:</span><span class="sxs-lookup"><span data-stu-id="326e9-311">This is most often used with logging scenarios:</span></span>

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

<span data-ttu-id="326e9-312">Podrobnosti implementace pro přidání `await` podporu uvnitř `catch` a `finally` klauzule zajistí, že její chování je konzistentní s chování synchronní kódu.</span><span class="sxs-lookup"><span data-stu-id="326e9-312">The implementation details for adding `await` support inside `catch` and `finally` clauses ensures that the behavior is consistent with the behavior for synchronous code.</span></span> <span data-ttu-id="326e9-313">Při provedení kódu `catch` nebo `finally` vyvolá klauzule, provádění hledá vhodný `catch` klauzuli v další blok okolního.</span><span class="sxs-lookup"><span data-stu-id="326e9-313">When code executed in a `catch` or `finally` clause throws, execution looks for a suitable `catch` clause in the next surrounding block.</span></span> <span data-ttu-id="326e9-314">Došlo k výjimce aktuální, dojde ke ztrátě této výjimky.</span><span class="sxs-lookup"><span data-stu-id="326e9-314">If there was a current exception, that exception is lost.</span></span> <span data-ttu-id="326e9-315">Stejné se stane s očekávaná výrazy v `catch` a `finally` klauzule: vhodný `catch` je hledán, a aktuální výjimky, pokud existuje, bude ztracena.</span><span class="sxs-lookup"><span data-stu-id="326e9-315">The same happens with awaited expressions in `catch` and `finally` clauses: a suitable `catch` is searched for, and the current exception, if any, is lost.</span></span>  

> [!NOTE]
> <span data-ttu-id="326e9-316">Toto chování je z důvodu se doporučuje pro zápis `catch` a `finally` klauzule pečlivě, aby nedošlo k zavedení nových výjimek.</span><span class="sxs-lookup"><span data-stu-id="326e9-316">This behavior is the reason it's recommended to write `catch` and `finally` clauses carefully, to avoid introducing new exceptions.</span></span>

## <a name="index-initializers"></a><span data-ttu-id="326e9-317">Inicializátory indexu</span><span class="sxs-lookup"><span data-stu-id="326e9-317">Index Initializers</span></span>

<span data-ttu-id="326e9-318">*Inicializátory index* je jednou ze dvou funkcí, které byly víc konzistentní Inicializátory kolekcí.</span><span class="sxs-lookup"><span data-stu-id="326e9-318">*Index Initializers* is one of two features that make collection initializers more consistent.</span></span> <span data-ttu-id="326e9-319">V dřívějších verzích jazyka C#, můžete použít *Inicializátory kolekcí* pouze s kolekcemi styl pořadí:</span><span class="sxs-lookup"><span data-stu-id="326e9-319">In earlier releases of C#, you could use *collection initializers* only with sequence style collections:</span></span>

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#ListInitializer)]

<span data-ttu-id="326e9-320">Teď můžete také použít je s <xref:System.Collections.Generic.Dictionary%602> kolekce a podobné typy:</span><span class="sxs-lookup"><span data-stu-id="326e9-320">Now, you can also use them with <xref:System.Collections.Generic.Dictionary%602> collections and similar types:</span></span>

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

<span data-ttu-id="326e9-321">Tato funkce znamená, že asociativní kontejnery můžete inicializovat pomocí syntaxe podobná co bylo nastavené pro kontejnery pořadí pro několik verzí.</span><span class="sxs-lookup"><span data-stu-id="326e9-321">This feature means that associative containers can be initialized using syntax similar to what's been in place for sequence containers for several versions.</span></span>

### <a name="extension-add-methods-in-collection-initializers"></a><span data-ttu-id="326e9-322">Rozšíření `Add` metody v Inicializátory kolekcí</span><span class="sxs-lookup"><span data-stu-id="326e9-322">Extension `Add` methods in collection initializers</span></span>

<span data-ttu-id="326e9-323">Další funkce, která usnadňuje inicializace kolekce je schopnost používat *metoda rozšíření* pro `Add` metoda.</span><span class="sxs-lookup"><span data-stu-id="326e9-323">Another feature that makes collection initialization easier is the ability to use an *extension method* for the `Add` method.</span></span> <span data-ttu-id="326e9-324">Tato funkce byla přidána parita s jazykem Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="326e9-324">This feature was added for parity with Visual Basic.</span></span> 

<span data-ttu-id="326e9-325">Tato funkce je velmi užitečné, když máte třídy vlastní kolekce, která má metoda s jiným názvem sémanticky přidávat nové položky.</span><span class="sxs-lookup"><span data-stu-id="326e9-325">The feature is most useful when you have a custom collection class that has a method with a different name to semantically add new items.</span></span>

<span data-ttu-id="326e9-326">Zvažte například kolekce studenty takto:</span><span class="sxs-lookup"><span data-stu-id="326e9-326">For example, consider a collection of students like this:</span></span>

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]

<span data-ttu-id="326e9-327">`Enroll` Metoda přidá student.</span><span class="sxs-lookup"><span data-stu-id="326e9-327">The `Enroll` method adds a student.</span></span> <span data-ttu-id="326e9-328">Ale není pomocí `Add` vzor.</span><span class="sxs-lookup"><span data-stu-id="326e9-328">But it doesn't follow the `Add` pattern.</span></span>
<span data-ttu-id="326e9-329">V předchozích verzích jazyka C#, nelze používat Inicializátory kolekcí s `Enrollment` objektu:</span><span class="sxs-lookup"><span data-stu-id="326e9-329">In previous versions of C#, you could not use collection initializers with an `Enrollment` object:</span></span>

[!code-csharp[InitializeEnrollment](../../../samples/snippets/csharp/new-in-6/classList.cs#InitializeEnrollment)]

<span data-ttu-id="326e9-330">Teď můžete, ale jenom v případě, že vytvoříte metody rozšíření, která mapuje `Add` k `Enroll`:</span><span class="sxs-lookup"><span data-stu-id="326e9-330">Now you can, but only if you create an extension method that maps `Add` to `Enroll`:</span></span>

[!code-csharp[ExtensionAdd](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAdd)]

<span data-ttu-id="326e9-331">Co dělají pomocí této funkce je k mapování libovolné metody přidá položky do kolekce na metodu s názvem `Add` vytvořením metody rozšíření:</span><span class="sxs-lookup"><span data-stu-id="326e9-331">What you are doing with this feature is to map whatever method adds items to a collection to a method named `Add` by creating an extension method:</span></span> 

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]
[!code-csharp[ExtensionAddSample](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAddSample)]

## <a name="improved-overload-resolution"></a><span data-ttu-id="326e9-332">Vylepšené přetížení řešení</span><span class="sxs-lookup"><span data-stu-id="326e9-332">Improved overload resolution</span></span>

<span data-ttu-id="326e9-333">Tato funkce poslední je jednou z pravděpodobně nebude zjistíte.</span><span class="sxs-lookup"><span data-stu-id="326e9-333">This last feature is one you probably won't notice.</span></span> <span data-ttu-id="326e9-334">Nebyly konstrukce kde předchozí verzi kompilátor jazyka C# může našli některé volání metody zahrnující nejednoznačné výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="326e9-334">There were constructs where the previous version of the C# compiler may have found some method calls involving lambda expressions ambiguous.</span></span> <span data-ttu-id="326e9-335">Vezměte v úvahu tuto metodu:</span><span class="sxs-lookup"><span data-stu-id="326e9-335">Consider this method:</span></span>

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

<span data-ttu-id="326e9-336">Voláním této metody pomocí syntaxe skupiny metoda skončí v dřívějších verzích jazyka C# s chybou:</span><span class="sxs-lookup"><span data-stu-id="326e9-336">In earlier versions of C#, calling that method using the method group syntax would fail:</span></span>

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]
 
<span data-ttu-id="326e9-337">Starší kompilátoru nelze správně mezi rozlišit `Task.Run(Action)` a `Task.Run(Func<Task>())`.</span><span class="sxs-lookup"><span data-stu-id="326e9-337">The earlier compiler could not distinguish correctly between `Task.Run(Action)` and `Task.Run(Func<Task>())`.</span></span> <span data-ttu-id="326e9-338">V předchozích verzích je třeba použít jako argument výraz lambda:</span><span class="sxs-lookup"><span data-stu-id="326e9-338">In previous versions, you'd need to use a lambda expression as an argument:</span></span>

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

<span data-ttu-id="326e9-339">Kompilátor jazyka C# 6 správně zjistí, `Task.Run(Func<Task>())` je lepší volbou.</span><span class="sxs-lookup"><span data-stu-id="326e9-339">The C# 6 compiler correctly determines that `Task.Run(Func<Task>())` is a better choice.</span></span>
