---
title: Co je nového v jazyce C# 6 – Průvodce v C#
description: Informace o nových funkcích v jazyce C# verze 6
ms.date: 09/22/2016
ms.assetid: 4d879f69-f889-4d3f-a781-75194e143400
ms.openlocfilehash: f6f953eacc935d38cc7d45173109c96c52a5e2f3
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47208182"
---
# <a name="whats-new-in-c-6"></a><span data-ttu-id="c8460-103">Co je nového v jazyce C# 6</span><span class="sxs-lookup"><span data-stu-id="c8460-103">What's New in C# 6</span></span>

<span data-ttu-id="c8460-104">C# 6.0 vydání obsahovala řadu funkcí, které zvyšují produktivitu pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="c8460-104">The 6.0 release of C# contained many features that improve productivity for developers.</span></span> <span data-ttu-id="c8460-105">Funkce v této verzi patří:</span><span class="sxs-lookup"><span data-stu-id="c8460-105">Features in this release include:</span></span>

* <span data-ttu-id="c8460-106">[Auto vlastnosti jen pro čtení](#read-only-auto-properties):</span><span class="sxs-lookup"><span data-stu-id="c8460-106">[Read-only Auto-properties](#read-only-auto-properties):</span></span>
    - <span data-ttu-id="c8460-107">Můžete vytvořit jen pro čtení automatické vlastnosti, které lze nastavit pouze v konstruktorech.</span><span class="sxs-lookup"><span data-stu-id="c8460-107">You can create read-only auto-properties that can be set only in constructors.</span></span>
* <span data-ttu-id="c8460-108">[Inicializátory automatickou vlastnost](#auto-property-initializers):</span><span class="sxs-lookup"><span data-stu-id="c8460-108">[Auto-Property Initializers](#auto-property-initializers):</span></span>
    - <span data-ttu-id="c8460-109">Můžete psát výrazy inicializace nastavit počáteční hodnotu Automatická vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c8460-109">You can write initialization expressions to set the initial value of an auto-property.</span></span>
* <span data-ttu-id="c8460-110">[Členové s výrazem v těle funkce](#expression-bodied-function-members):</span><span class="sxs-lookup"><span data-stu-id="c8460-110">[Expression-bodied function members](#expression-bodied-function-members):</span></span>
    - <span data-ttu-id="c8460-111">Můžete vytvářet metody jednořádkové použití výrazů lambda.</span><span class="sxs-lookup"><span data-stu-id="c8460-111">You can author one-line methods using lambda expressions.</span></span>
* <span data-ttu-id="c8460-112">[pomocí statické](#using-static):</span><span class="sxs-lookup"><span data-stu-id="c8460-112">[using static](#using-static):</span></span>
    - <span data-ttu-id="c8460-113">Všechny metody jednu třídu můžete importovat do aktuálního oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c8460-113">You can import all the methods of a single class into the current namespace.</span></span>
* <span data-ttu-id="c8460-114">[Null – podmíněných operátorů](#null-conditional-operators):</span><span class="sxs-lookup"><span data-stu-id="c8460-114">[Null - conditional operators](#null-conditional-operators):</span></span>
    - <span data-ttu-id="c8460-115">Stručně a výstižně a bezpečně dostanete členy objektu při pořád ještě se hledají null s hodnotou null podmiňovací operátor.</span><span class="sxs-lookup"><span data-stu-id="c8460-115">You can concisely and safely access members of an object while still checking for null with the null conditional operator.</span></span>
* <span data-ttu-id="c8460-116">[Interpolace řetězců](#string-interpolation):</span><span class="sxs-lookup"><span data-stu-id="c8460-116">[String Interpolation](#string-interpolation):</span></span>
    - <span data-ttu-id="c8460-117">Můžete napsat řetězce formátování výrazů vložené výrazy místo poziční argumenty.</span><span class="sxs-lookup"><span data-stu-id="c8460-117">You can write string formatting expressions using inline expressions instead of positional arguments.</span></span>
* <span data-ttu-id="c8460-118">[Filtry výjimek](#exception-filters):</span><span class="sxs-lookup"><span data-stu-id="c8460-118">[Exception filters](#exception-filters):</span></span>
    - <span data-ttu-id="c8460-119">Je možné zachytit výrazům založeným na vlastnosti výjimky nebo jiných stav programu.</span><span class="sxs-lookup"><span data-stu-id="c8460-119">You can catch expressions based on properties of the exception or other program state.</span></span> 
* <span data-ttu-id="c8460-120">[Výrazy nameof](#nameof-expressions):</span><span class="sxs-lookup"><span data-stu-id="c8460-120">[nameof Expressions](#nameof-expressions):</span></span>
    - <span data-ttu-id="c8460-121">Můžete nechat kompilátor generovat řetězcové reprezentace symboly.</span><span class="sxs-lookup"><span data-stu-id="c8460-121">You can let the compiler generate string representations of symbols.</span></span>
* <span data-ttu-id="c8460-122">[operátor await v catch a finally blokuje](#await-in-catch-and-finally-blocks):</span><span class="sxs-lookup"><span data-stu-id="c8460-122">[await in catch and finally blocks](#await-in-catch-and-finally-blocks):</span></span>
    - <span data-ttu-id="c8460-123">Můžete použít `await` výrazy v umístění, která dříve je zakázané.</span><span class="sxs-lookup"><span data-stu-id="c8460-123">You can use `await` expressions in locations that previously disallowed them.</span></span>
* <span data-ttu-id="c8460-124">[Inicializátory indexů](#index-initializers):</span><span class="sxs-lookup"><span data-stu-id="c8460-124">[index initializers](#index-initializers):</span></span>
    - <span data-ttu-id="c8460-125">Výrazy inicializace pro asociativní kontejnery, stejně jako kontejnery sekvence, můžete vytvářet.</span><span class="sxs-lookup"><span data-stu-id="c8460-125">You can author initialization expressions for associative containers as well as sequence containers.</span></span>
* <span data-ttu-id="c8460-126">[Rozšiřující metody pro inicializátory kolekce](#extension-add-methods-in-collection-initializers):</span><span class="sxs-lookup"><span data-stu-id="c8460-126">[Extension methods for collection initializers](#extension-add-methods-in-collection-initializers):</span></span>
    - <span data-ttu-id="c8460-127">Inicializátory kolekce můžete spolehnout na dostupné rozšiřující metody, kromě metod člena.</span><span class="sxs-lookup"><span data-stu-id="c8460-127">Collection initializers can rely on accessible extension methods, in addition to member methods.</span></span>
* <span data-ttu-id="c8460-128">[Vylepšené řešení přetížení](#improved-overload-resolution):</span><span class="sxs-lookup"><span data-stu-id="c8460-128">[Improved overload resolution](#improved-overload-resolution):</span></span>
    - <span data-ttu-id="c8460-129">Některé konstrukce, které dříve vygenerovaný volání metody nejednoznačný nyní správně přeložit.</span><span class="sxs-lookup"><span data-stu-id="c8460-129">Some constructs that previously generated ambiguous method calls now resolve correctly.</span></span>
* <span data-ttu-id="c8460-130">[`deterministic` – možnost kompilátoru](#deterministic-compiler-output):</span><span class="sxs-lookup"><span data-stu-id="c8460-130">[`deterministic` compiler option](#deterministic-compiler-output):</span></span>
    - <span data-ttu-id="c8460-131">Možnost kompilátoru deterministické zajišťuje, následné kompilace se stejným zdrojem generovat stejný binární výstup.</span><span class="sxs-lookup"><span data-stu-id="c8460-131">The deterministic compiler option ensures that subsequent compilations of the same source generate the same binary output.</span></span>

<span data-ttu-id="c8460-132">Celkový efekt z těchto funkcí je, že napíšete stručnější kód, který je také lépe čitelný.</span><span class="sxs-lookup"><span data-stu-id="c8460-132">The overall effect of these features is that you write more concise code that is also more readable.</span></span> <span data-ttu-id="c8460-133">Syntaxe obsahuje méně procedury pro mnoho běžných postupech.</span><span class="sxs-lookup"><span data-stu-id="c8460-133">The syntax contains less ceremony for many common practices.</span></span> <span data-ttu-id="c8460-134">Je snazší zjistit záměr návrhu s méně procedury.</span><span class="sxs-lookup"><span data-stu-id="c8460-134">It's easier to see the design intent with less ceremony.</span></span> <span data-ttu-id="c8460-135">Přečtěte si tyto funkce dobře a budete produktivnější, psát kód lépe čitelný a více se soustředit na základní funkce, než na konstrukce jazyka.</span><span class="sxs-lookup"><span data-stu-id="c8460-135">Learn these features well, and you'll be more productive, write more readable code, and concentrate more on your core features than on the constructs of the language.</span></span>

<span data-ttu-id="c8460-136">Zbývající část tohoto tématu poskytuje podrobné informace o každé z těchto funkcí.</span><span class="sxs-lookup"><span data-stu-id="c8460-136">The remainder of this topic provides details on each of these features.</span></span>

## <a name="auto-property-enhancements"></a><span data-ttu-id="c8460-137">Vylepšení automatickou vlastnost</span><span class="sxs-lookup"><span data-stu-id="c8460-137">Auto-Property enhancements</span></span>

<span data-ttu-id="c8460-138">Syntaxe pro automaticky implementované vlastnosti (obvykle označované jako automatické vlastnosti) provedené velmii snadné vytváření vlastnosti, které bylo jednoduché get a set přístupové objekty:</span><span class="sxs-lookup"><span data-stu-id="c8460-138">The syntax for automatically implemented properties (usually referred to as 'auto-properties') made it very easy to create properties that had simple get and set accessors:</span></span>

[!code-csharp[ClassicAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicAutoProperty)]

<span data-ttu-id="c8460-139">Tato jednoduchá syntaxe však omezenou druhy vzorů, které může podporovat použití automatických vlastností.</span><span class="sxs-lookup"><span data-stu-id="c8460-139">However, this simple syntax limited the kinds of designs you could support using auto-properties.</span></span> <span data-ttu-id="c8460-140">C# 6 vylepšuje možnosti automatické vlastnosti tak, aby je mohli používat ve více scénářích.</span><span class="sxs-lookup"><span data-stu-id="c8460-140">C# 6 improves the auto-properties capabilities so that you can use them in more scenarios.</span></span> <span data-ttu-id="c8460-141">Nebudete se muset vrátit zpět na podrobnější syntaxi deklarace a manipulace s pomocným polem ručně tak často.</span><span class="sxs-lookup"><span data-stu-id="c8460-141">You won't need to fall back on the more verbose syntax of declaring and manipulating the backing field by hand so often.</span></span>

<span data-ttu-id="c8460-142">Nová syntaxe adresy scénáře pro vlastnosti jen pro čtení a pro inicializaci proměnné úložiště za automatickou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c8460-142">The new syntax addresses scenarios for read-only properties, and for initializing the variable storage behind an auto-property.</span></span>

### <a name="read-only-auto-properties"></a><span data-ttu-id="c8460-143">Auto vlastnosti jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="c8460-143">Read-only auto-properties</span></span>

<span data-ttu-id="c8460-144">*Auto vlastnosti jen pro čtení* poskytují stručnější syntaxi, vytvořte neměnný typy.</span><span class="sxs-lookup"><span data-stu-id="c8460-144">*Read-only auto-properties* provide a more concise syntax to create immutable types.</span></span> <span data-ttu-id="c8460-145">Nejbližší, které můžete narazit na neměnné typy ve starších verzích jazyka C# došlo k deklaraci privátní metody setter:</span><span class="sxs-lookup"><span data-stu-id="c8460-145">The closest you could get to immutable types in earlier versions of C# was to declare private setters:</span></span>

[!code-csharp[ClassicReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicReadOnlyAutoProperty)]
 
<span data-ttu-id="c8460-146">Pomocí této syntaxe, kompilátor nebude zajistěte, aby byl typ skutečně neměnné.</span><span class="sxs-lookup"><span data-stu-id="c8460-146">Using this syntax, the compiler doesn't ensure that the type really is immutable.</span></span> <span data-ttu-id="c8460-147">Pouze rozdělení promítá `FirstName` a `LastName` vlastnosti nezmění v žádném kódu mimo třídu.</span><span class="sxs-lookup"><span data-stu-id="c8460-147">It only enforces that the `FirstName` and `LastName` properties are not modified from any code outside the class.</span></span>

<span data-ttu-id="c8460-148">True jen pro čtení chování povolit automatické – vlastnosti jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="c8460-148">Read-only auto-properties enable true read-only behavior.</span></span> <span data-ttu-id="c8460-149">Deklarovat vlastnost automaticky s pouze přístupový objekt get:</span><span class="sxs-lookup"><span data-stu-id="c8460-149">You declare the auto-property with only a get accessor:</span></span>

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

<span data-ttu-id="c8460-150">`FirstName` a `LastName` vlastnosti lze nastavit pouze v těle konstruktoru:</span><span class="sxs-lookup"><span data-stu-id="c8460-150">The `FirstName` and `LastName` properties can be set only in the body of a constructor:</span></span>

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

<span data-ttu-id="c8460-151">Pokoušíte se nastavit `LastName` v jiné metody generuje `CS0200` Chyba kompilace:</span><span class="sxs-lookup"><span data-stu-id="c8460-151">Trying to set `LastName` in another method generates a `CS0200` compilation error:</span></span>

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

<span data-ttu-id="c8460-152">Tato funkce umožňuje true jazykovou podporu pro vytváření typů neměnných a pomocí syntaxe automatickou vlastnost stručnějším a pohodlné.</span><span class="sxs-lookup"><span data-stu-id="c8460-152">This feature enables true language support for creating immutable types and using the more concise and convenient auto-property syntax.</span></span>

<span data-ttu-id="c8460-153">Pokud přidáte tuto syntaxi není neodebere dostupná metoda, je [binární kompatibilní změnu](version-update-considerations.md#binary-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="c8460-153">If adding this syntax does not not remove an accessible method, it is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

### <a name="auto-property-initializers"></a><span data-ttu-id="c8460-154">Inicializátory automatickou vlastnost</span><span class="sxs-lookup"><span data-stu-id="c8460-154">Auto-Property Initializers</span></span>

<span data-ttu-id="c8460-155">*Inicializátory automatickou vlastnost* umožňuje deklarovat počáteční hodnotu pro automatickou vlastnost jako součást deklarace vlastností.</span><span class="sxs-lookup"><span data-stu-id="c8460-155">*Auto-Property Initializers* let you declare the initial value for an auto-property as part of the property declaration.</span></span>  <span data-ttu-id="c8460-156">V dřívějších verzích byste potřebovali mít nastavení těchto vlastností a je třeba použít tuto metodu setter se inicializovat datové úložiště používané pomocným polem.</span><span class="sxs-lookup"><span data-stu-id="c8460-156">In earlier versions, these properties would need to have setters and you would need to use that setter to initialize the data storage used by the backing field.</span></span> <span data-ttu-id="c8460-157">Vezměte v úvahu tuto třídu pro student, který obsahuje název a seznam tříd studenta:</span><span class="sxs-lookup"><span data-stu-id="c8460-157">Consider this class for a student that contains the name and a list of the student's grades:</span></span>

[!code-csharp[Construction](../../../samples/snippets/csharp/new-in-6/oldcode.cs#Construction)]
 
<span data-ttu-id="c8460-158">S růstem této třídy může obsahovat další konstruktory.</span><span class="sxs-lookup"><span data-stu-id="c8460-158">As this class grows, you may include other constructors.</span></span> <span data-ttu-id="c8460-159">Každý konstruktor musí inicializovat toto pole, nebo budete způsobit chyby.</span><span class="sxs-lookup"><span data-stu-id="c8460-159">Each constructor needs to initialize this field, or you'll introduce errors.</span></span>

<span data-ttu-id="c8460-160">C# 6 umožňuje přiřadit počáteční hodnotu pro úložiště využitá službou Automatické vlastnosti v deklaraci automatickou vlastnost:</span><span class="sxs-lookup"><span data-stu-id="c8460-160">C# 6 enables you to assign an initial value for the storage used by an auto-property in the auto-property declaration:</span></span>

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

<span data-ttu-id="c8460-161">`Grades` Člen je inicializovaný, ve kterém je deklarována.</span><span class="sxs-lookup"><span data-stu-id="c8460-161">The `Grades` member is initialized where it is declared.</span></span> <span data-ttu-id="c8460-162">Který usnadňuje provedení inicializace přesně jednou.</span><span class="sxs-lookup"><span data-stu-id="c8460-162">That makes it easier to perform the initialization exactly once.</span></span> <span data-ttu-id="c8460-163">Inicializace je součástí deklaraci vlastnosti, což usnadňuje odpovídá přidělení úložiště pomocí veřejného rozhraní pro `Student` objekty.</span><span class="sxs-lookup"><span data-stu-id="c8460-163">The initialization is part of the property declaration, making it easier to equate the storage allocation with public interface for `Student` objects.</span></span>

<span data-ttu-id="c8460-164">Vlastnosti lze použít s vlastností čtení/zápisu, jakož i vlastnosti jen pro čtení, jak je znázorněno zde.</span><span class="sxs-lookup"><span data-stu-id="c8460-164">Property Initializers can be used with read/write properties as well as read-only properties, as shown here.</span></span>

[!code-csharp[ReadWriteInitialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadWriteInitialization)]

## <a name="expression-bodied-function-members"></a><span data-ttu-id="c8460-165">Členové tvoření výrazy – funkce</span><span class="sxs-lookup"><span data-stu-id="c8460-165">Expression-bodied function members</span></span>

<span data-ttu-id="c8460-166">Tělo mnoho členů, které jsme napsali obsahovat pouze jeden příkaz, který může být reprezentována jako výraz.</span><span class="sxs-lookup"><span data-stu-id="c8460-166">The body of a lot of members that we write consist of only one statement that can be represented as an expression.</span></span> <span data-ttu-id="c8460-167">Syntaxe můžete snížit napsáním na člena s výrazem v těle.</span><span class="sxs-lookup"><span data-stu-id="c8460-167">You can reduce that syntax by writing an expression-bodied member instead.</span></span> <span data-ttu-id="c8460-168">Funguje to pro metody a vlastnosti jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="c8460-168">It works for methods and read-only properties.</span></span> <span data-ttu-id="c8460-169">Například přepsání `ToString()` často je vynikající kandidát:</span><span class="sxs-lookup"><span data-stu-id="c8460-169">For example, an override of `ToString()` is often a great candidate:</span></span>

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

<span data-ttu-id="c8460-170">Můžete také použít s výrazem v těle členy v také vlastnosti jen pro čtení:</span><span class="sxs-lookup"><span data-stu-id="c8460-170">You can also use expression-bodied members in read-only properties as well:</span></span>

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="c8460-171">Změna existujícího člena pro člena vozidlo výrazu je [binární kompatibilní změnu](version-update-considerations.md#binary-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="c8460-171">Changing an existing member to an expression bodied member is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>


## <a name="using-static"></a><span data-ttu-id="c8460-172">Pomocí statické</span><span class="sxs-lookup"><span data-stu-id="c8460-172">using static</span></span>

<span data-ttu-id="c8460-173">*Pomocí statické* vylepšení umožňuje importovat statické metody jednu třídu.</span><span class="sxs-lookup"><span data-stu-id="c8460-173">The *using static* enhancement enables you to import the static methods of a single class.</span></span> <span data-ttu-id="c8460-174">Dříve `using` příkaz naimportovány všechny typy v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c8460-174">Previously, the `using` statement imported all types in a namespace.</span></span> 

<span data-ttu-id="c8460-175">Často používáme statické metody třídy v rámci našeho kódu.</span><span class="sxs-lookup"><span data-stu-id="c8460-175">Often we use a class' static methods throughout our code.</span></span> <span data-ttu-id="c8460-176">Opakovaně zadávat název třídy může ztížit odhalení zjevného význam kódu.</span><span class="sxs-lookup"><span data-stu-id="c8460-176">Repeatedly typing the class name can obscure the meaning of your code.</span></span> <span data-ttu-id="c8460-177">Běžným příkladem jsou při psaní třídy, které provádějí mnoho číselné výpočty.</span><span class="sxs-lookup"><span data-stu-id="c8460-177">A common example is when you write classes that perform many numeric calculations.</span></span>
<span data-ttu-id="c8460-178">Váš kód podestlána <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> a jiných volání do různých metod v <xref:System.Math> třídy.</span><span class="sxs-lookup"><span data-stu-id="c8460-178">Your code will be littered with <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> and other calls to different methods in the <xref:System.Math> class.</span></span> <span data-ttu-id="c8460-179">Nové `using static` syntaxe můžete provádět tyto třídy mnohem čisticího modulu pro čtení.</span><span class="sxs-lookup"><span data-stu-id="c8460-179">The new `using static` syntax can make these classes much cleaner to read.</span></span> <span data-ttu-id="c8460-180">Můžete zadat třídu, kterou používáte:</span><span class="sxs-lookup"><span data-stu-id="c8460-180">You specify the class you're using:</span></span>

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<span data-ttu-id="c8460-181">A teď můžete použít jakékoli statické metodě v <xref:System.Math> třídy bez kvalifikace <xref:System.Math> třídy.</span><span class="sxs-lookup"><span data-stu-id="c8460-181">And now, you can use any static method in the <xref:System.Math> class without qualifying the <xref:System.Math> class.</span></span> <span data-ttu-id="c8460-182"><xref:System.Math> Třída je případ vynikající možnosti využití pro tuto funkci, protože neobsahuje žádné metody instance.</span><span class="sxs-lookup"><span data-stu-id="c8460-182">The <xref:System.Math> class is a great use case for this feature because it does not contain any instance methods.</span></span> <span data-ttu-id="c8460-183">Můžete také použít `using static` importovat třídy statické metody pro třídu, která má statické a metody instance.</span><span class="sxs-lookup"><span data-stu-id="c8460-183">You can also use `using static` to import a class' static methods for a class that has both static and instance methods.</span></span> <span data-ttu-id="c8460-184">Jedním z nejužitečnějších příkladů je <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="c8460-184">One of the most useful examples is <xref:System.String>:</span></span>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> <span data-ttu-id="c8460-185">Musíte použít plně kvalifikovaný název třídy, `System.String` v statický příkaz using.</span><span class="sxs-lookup"><span data-stu-id="c8460-185">You must use the fully qualified class name, `System.String` in a static using statement.</span></span> <span data-ttu-id="c8460-186">Nelze použít `string` – klíčové slovo místo.</span><span class="sxs-lookup"><span data-stu-id="c8460-186">You cannot use the `string` keyword instead.</span></span> 

<span data-ttu-id="c8460-187">Nyní můžete volat statické metody definované v <xref:System.String> třídy bez kvalifikace tyto metody jako členy této třídy:</span><span class="sxs-lookup"><span data-stu-id="c8460-187">You can now call static methods defined in the <xref:System.String> class without qualifying those methods as members of that class:</span></span>

[!code-csharp[UsingStaticString](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticString)]

<span data-ttu-id="c8460-188">`static using` Metody funkce a rozšíření interagovali zajímavé a návrhu jazyka zahrnuté některá pravidla, které konkrétně řeší tyto interakce.</span><span class="sxs-lookup"><span data-stu-id="c8460-188">The `static using` feature and extension methods interact in interesting ways, and the language design included some rules that specifically address those interactions.</span></span> <span data-ttu-id="c8460-189">Cílem je minimalizovat jakékoli riziko rozbíjející změny v existujícím základů kódu, včetně těch vašich.</span><span class="sxs-lookup"><span data-stu-id="c8460-189">The goal is to minimize any chances of breaking changes in existing codebases, including yours.</span></span>

<span data-ttu-id="c8460-190">Rozšiřující metody jsou pouze v oboru při volány pomocí syntaxe volání metody rozšíření, ne v případě, že volá jako statická metoda.</span><span class="sxs-lookup"><span data-stu-id="c8460-190">Extension methods are only in scope when called using the extension method invocation syntax, not when called as a static method.</span></span>
<span data-ttu-id="c8460-191">To se často zobrazí v dotazech LINQ.</span><span class="sxs-lookup"><span data-stu-id="c8460-191">You'll often see this in LINQ queries.</span></span> <span data-ttu-id="c8460-192">Vzor LINQ můžete importovat importováním <xref:System.Linq.Enumerable>.</span><span class="sxs-lookup"><span data-stu-id="c8460-192">You can import the LINQ pattern by importing <xref:System.Linq.Enumerable>.</span></span>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

<span data-ttu-id="c8460-193">Tento postup importuje všechny metody v <xref:System.Linq.Enumerable> třídy.</span><span class="sxs-lookup"><span data-stu-id="c8460-193">This imports all the methods in the <xref:System.Linq.Enumerable> class.</span></span>
<span data-ttu-id="c8460-194">Rozšiřující metody jsou však jenom v oboru při volání jako metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="c8460-194">However, the extension methods are only in scope when called as extension methods.</span></span> <span data-ttu-id="c8460-195">Nejsou v oboru Pokud jsou volány pomocí syntaxe statickou metodu:</span><span class="sxs-lookup"><span data-stu-id="c8460-195">They are not in scope if they are called using the static method syntax:</span></span>

[!code-csharp[UsingStaticLinqMethod](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticLinkMethod)]

<span data-ttu-id="c8460-196">Toto rozhodnutí je vzhledem k tomu, že metody rozšíření jsou obvykle volány pomocí výrazy typu invocation – metoda rozšíření.</span><span class="sxs-lookup"><span data-stu-id="c8460-196">This decision is because extension methods are typically called using extension method invocation expressions.</span></span> <span data-ttu-id="c8460-197">Ve výjimečných případech, ve kterém jsou volány pomocí statické metody volání se vyřešit nejednoznačnost syntaxe.</span><span class="sxs-lookup"><span data-stu-id="c8460-197">In the rare case where they are called using the static method call syntax it is to resolve ambiguity.</span></span>
<span data-ttu-id="c8460-198">Vyžadování názvu třídy jako součást volání zdá se, že z pohledu.</span><span class="sxs-lookup"><span data-stu-id="c8460-198">Requiring the class name as part of the invocation seems wise.</span></span>

<span data-ttu-id="c8460-199">Existuje jeden poslední funkci `static using`.</span><span class="sxs-lookup"><span data-stu-id="c8460-199">There's one last feature of `static using`.</span></span> <span data-ttu-id="c8460-200">`static using` Direktiva také importuje všechny vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="c8460-200">The `static using` directive also imports any nested types.</span></span> <span data-ttu-id="c8460-201">Která umožňuje odkazovat na jakékoli vnořené typy bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="c8460-201">That enables you to reference any nested types without qualification.</span></span>

## <a name="null-conditional-operators"></a><span data-ttu-id="c8460-202">Podmíněné operátory s Null</span><span class="sxs-lookup"><span data-stu-id="c8460-202">Null-conditional operators</span></span>

<span data-ttu-id="c8460-203">Hodnoty Null zkomplikovat kódu.</span><span class="sxs-lookup"><span data-stu-id="c8460-203">Null values complicate code.</span></span> <span data-ttu-id="c8460-204">Je potřeba zkontrolovat každý přístup proměnné k zajištění nejsou přesměrování `null`.</span><span class="sxs-lookup"><span data-stu-id="c8460-204">You need to check every access of variables to ensure you are not dereferencing `null`.</span></span> <span data-ttu-id="c8460-205">*Null podmiňovací operátor* díky kontrol mnohem jednodušší a plynulé.</span><span class="sxs-lookup"><span data-stu-id="c8460-205">The *null conditional operator* makes those checks much easier and fluid.</span></span>

<span data-ttu-id="c8460-206">Jednoduše nahradit přístup ke členu `.` s `?.`:</span><span class="sxs-lookup"><span data-stu-id="c8460-206">Simply replace the member access `.` with `?.`:</span></span>

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

<span data-ttu-id="c8460-207">V předchozím příkladu je proměnná `first` je přiřazena `null` Pokud objekt osoba `null`.</span><span class="sxs-lookup"><span data-stu-id="c8460-207">In the preceding example, the variable `first` is assigned `null` if the person object is `null`.</span></span> <span data-ttu-id="c8460-208">V opačném případě získá přiřadí hodnota `FirstName` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c8460-208">Otherwise, it gets assigned the value of the `FirstName` property.</span></span> <span data-ttu-id="c8460-209">Co je nejdůležitější `?.` znamená, že negeneruje tento řádek kódu `NullReferenceException` při `person` proměnná je `null`.</span><span class="sxs-lookup"><span data-stu-id="c8460-209">Most importantly, the `?.` means that this line of code does not generate a `NullReferenceException` when the `person` variable is `null`.</span></span> <span data-ttu-id="c8460-210">Místo toho zkratům a vytváří `null`.</span><span class="sxs-lookup"><span data-stu-id="c8460-210">Instead, it short-circuits and produces `null`.</span></span>

<span data-ttu-id="c8460-211">Všimněte si také, že tento výraz vrátí `string`bez ohledu hodnotu `person`.</span><span class="sxs-lookup"><span data-stu-id="c8460-211">Also, note that this expression returns a `string`, regardless of the value of `person`.</span></span>
<span data-ttu-id="c8460-212">V případě krátký circuiting `null` vrácená hodnota je typu tak, aby odpovídaly úplného výrazu.</span><span class="sxs-lookup"><span data-stu-id="c8460-212">In the case of short circuiting, the `null` value returned is typed to match the full expression.</span></span>

<span data-ttu-id="c8460-213">Můžete často použít tento konstruktor s *nulové sloučení* operátor přiřadit výchozí hodnoty, pokud jedna z vlastností jsou `null`:</span><span class="sxs-lookup"><span data-stu-id="c8460-213">You can often use this construct with the *null coalescing* operator to assign default values when one of the properties are `null`:</span></span>

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

<span data-ttu-id="c8460-214">Pravý operand na straně aplikace `?.` operátor není omezena pouze na vlastnosti nebo pole.</span><span class="sxs-lookup"><span data-stu-id="c8460-214">The right hand side operand of the `?.` operator is not limited to properties or fields.</span></span>
<span data-ttu-id="c8460-215">Také vám pomůže ho podmíněně vyvolávat metody.</span><span class="sxs-lookup"><span data-stu-id="c8460-215">You can also use it to conditionally invoke methods.</span></span> <span data-ttu-id="c8460-216">Nejběžnější použití nástroje členské funkce s hodnotou null podmíněný operátor je pro bezpečné vyvolání delegátů (nebo obslužné rutiny událostí), které mohou být `null`.</span><span class="sxs-lookup"><span data-stu-id="c8460-216">The most common use of member functions with the null conditional operator is to safely invoke delegates (or event handlers) that may be `null`.</span></span>  <span data-ttu-id="c8460-217">Uděláte to pomocí volání delegáta `Invoke` pomocí metody `?.` operátor pro přístup k členu.</span><span class="sxs-lookup"><span data-stu-id="c8460-217">You'll do this by calling the delegate's `Invoke` method using the `?.` operator to access the member.</span></span> <span data-ttu-id="c8460-218">Příklad v můžete vidět</span><span class="sxs-lookup"><span data-stu-id="c8460-218">You can see an example in the</span></span>  
<span data-ttu-id="c8460-219">[delegování vzorce](../delegates-patterns.md#handling-null-delegates) tématu.</span><span class="sxs-lookup"><span data-stu-id="c8460-219">[delegate patterns](../delegates-patterns.md#handling-null-delegates) topic.</span></span>

<span data-ttu-id="c8460-220">Pravidla `?.` operátor Ujistěte se, že levá strana operátoru je vyhodnocen pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="c8460-220">The rules of the `?.` operator ensure that the left-hand side of the operator is evaluated only once.</span></span> <span data-ttu-id="c8460-221">To je důležité a umožňuje mnoho idiomy, včetně příkladu pomocí obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="c8460-221">This is important and enables many idioms, including the example using event handlers.</span></span> <span data-ttu-id="c8460-222">Začněme s využitím obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="c8460-222">Let's start with the event handler usage.</span></span> <span data-ttu-id="c8460-223">V předchozích verzích jazyka C# byla ukončena. doporučujeme psát kód následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="c8460-223">In previous versions of C#, you were encouraged to write code like this:</span></span>

```csharp
var handler = this.SomethingHappened;
if (handler != null)
    handler(this, eventArgs);
```

<span data-ttu-id="c8460-224">To byla upřednostňované nad jednodušší syntaxí:</span><span class="sxs-lookup"><span data-stu-id="c8460-224">This was preferred over a simpler syntax:</span></span>

```csharp
// Not recommended
if (this.SomethingHappened != null)
    this.SomethingHappened(this, eventArgs);
```

> [!IMPORTANT]
> <span data-ttu-id="c8460-225">V předchozím příkladu představuje časování.</span><span class="sxs-lookup"><span data-stu-id="c8460-225">The preceding example introduces a race condition.</span></span> <span data-ttu-id="c8460-226">`SomethingHappened` Událost může mít předplatitele, pokud je zaškrtnuto proti `null`, a tyto předplatitele byl odebrán předtím, než se vyvolá událost.</span><span class="sxs-lookup"><span data-stu-id="c8460-226">The `SomethingHappened` event may have subscribers when checked against `null`, and those subscribers may have been removed before the event is raised.</span></span> <span data-ttu-id="c8460-227">Která by způsobila <xref:System.NullReferenceException> vyvolání.</span><span class="sxs-lookup"><span data-stu-id="c8460-227">That would cause a <xref:System.NullReferenceException> to be thrown.</span></span>

<span data-ttu-id="c8460-228">V této verzi druhý `SomethingHappened` obslužná rutina události může být jiná než null při testování, ale pokud jiný kód odebere obslužnou rutinu, je stále možné null při byla volána obslužná rutina události.</span><span class="sxs-lookup"><span data-stu-id="c8460-228">In this second version, the `SomethingHappened` event handler might be non-null when tested, but if other code removes a handler, it could still be null when the event handler was called.</span></span>

<span data-ttu-id="c8460-229">Kompilátor generuje kód `?.` operátor, který zajistí na levé straně (`this.SomethingHappened`) z `?.` výraz se vyhodnotí jednou a výsledek je uložen do mezipaměti:</span><span class="sxs-lookup"><span data-stu-id="c8460-229">The compiler generates code for the `?.` operator that ensures the left side (`this.SomethingHappened`) of the `?.` expression is evaluated once, and the result is cached:</span></span>

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

<span data-ttu-id="c8460-230">Zajištění, že na levé straně je vyhodnocen pouze jednou můžete také použít libovolný výraz, včetně volání metod na levé straně `?.` i v případě, že mají vedlejší účinky, jsou vyhodnocovány jednou, takže k vedlejším účinkům dochází pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="c8460-230">Ensuring that the left side is evaluated only once also enables you to use any expression, including method calls, on the left side of the `?.` Even if these have side-effects, they are evaluated once, so the side effects occur only once.</span></span> <span data-ttu-id="c8460-231">Můžete zobrazit příklad, v našem obsahu na [události](../events-overview.md#language-support-for-events).</span><span class="sxs-lookup"><span data-stu-id="c8460-231">You can see an example in our content on [events](../events-overview.md#language-support-for-events).</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="c8460-232">Interpolace řetězců</span><span class="sxs-lookup"><span data-stu-id="c8460-232">String Interpolation</span></span>

<span data-ttu-id="c8460-233">C# 6 obsahuje novou syntaxi pro vytvoření řetězce z formátovacího řetězce a výrazy, které jsou vyhodnocovány vytvoří další hodnoty řetězce.</span><span class="sxs-lookup"><span data-stu-id="c8460-233">C# 6 contains new syntax for composing strings from a format string and expressions that are evaluated to produce other string values.</span></span>

<span data-ttu-id="c8460-234">Tradičně, museli jste pro použít poziční parametry v metodě, jako je `string.Format`:</span><span class="sxs-lookup"><span data-stu-id="c8460-234">Traditionally, you needed to use positional parameters in a method like `string.Format`:</span></span>

[!code-csharp[stringFormat](../../../samples/snippets/csharp/new-in-6/oldcode.cs#stringFormat)]

<span data-ttu-id="c8460-235">Pomocí jazyka C# 6 nové [interpolace](../language-reference/tokens/interpolated.md) funkce vám umožní vložit výrazy ve formátovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="c8460-235">With C# 6, the new [string interpolation](../language-reference/tokens/interpolated.md) feature enables you to embed the expressions in the format string.</span></span> <span data-ttu-id="c8460-236">Jednoduše začínat řetězec s `$`:</span><span class="sxs-lookup"><span data-stu-id="c8460-236">Simply preface the string with `$`:</span></span>

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="c8460-237">Tento první příklad používá vlastnost výrazy pro nahrazeny výrazy.</span><span class="sxs-lookup"><span data-stu-id="c8460-237">This initial example uses property expressions for the substituted expressions.</span></span> <span data-ttu-id="c8460-238">Můžete rozšířit na tahle syntaxe použít libovolný výraz.</span><span class="sxs-lookup"><span data-stu-id="c8460-238">You can expand on this syntax to use any expression.</span></span> <span data-ttu-id="c8460-239">Například může vypočítat průměr student získal na podnikové úrovni jako součást interpolace:</span><span class="sxs-lookup"><span data-stu-id="c8460-239">For example, you could compute a student's grade point average as part of the interpolation:</span></span>

[!code-csharp[stringInterpolationExpression](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationExpression)]

<span data-ttu-id="c8460-240">Spuštěný v předchozím příkladu, jehož ekvivalent byste našli, který ve výstupu `Grades.Average()` může mít více desetinných míst, než byste chtěli.</span><span class="sxs-lookup"><span data-stu-id="c8460-240">Running the preceding example, you would find that the output for `Grades.Average()` might have more decimal places than you would like.</span></span> <span data-ttu-id="c8460-241">Syntaxe interpolace řetězce podporuje všechny na formát řetězce k dispozici pomocí dříve formátování metod.</span><span class="sxs-lookup"><span data-stu-id="c8460-241">The string interpolation syntax supports all the format strings available using earlier formatting methods.</span></span> <span data-ttu-id="c8460-242">Přidání formátovacích řetězců uvnitř složených závorek.</span><span class="sxs-lookup"><span data-stu-id="c8460-242">You add the format strings inside the braces.</span></span> <span data-ttu-id="c8460-243">Přidat `:` následující výraz, který má formát:</span><span class="sxs-lookup"><span data-stu-id="c8460-243">Add a `:` following the expression to format:</span></span>

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

<span data-ttu-id="c8460-244">Naformátuje hodnotu pro předchozí řádek kódu `Grades.Average()` jako číslo s plovoucí desetinnou čárkou se dvěma desetinnými místy.</span><span class="sxs-lookup"><span data-stu-id="c8460-244">The preceding line of code formats the value for `Grades.Average()` as a floating-point number with two decimal places.</span></span>

<span data-ttu-id="c8460-245">`:` Je vždy interpretováno jako oddělovač mezi výrazem formátovaného a formátovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="c8460-245">The `:` is always interpreted as the separator between the expression being formatted and the format string.</span></span> <span data-ttu-id="c8460-246">To může způsobit problémy při výraz používá `:` jiným způsobem, jako je například podmíněný operátor:</span><span class="sxs-lookup"><span data-stu-id="c8460-246">This can introduce problems when your expression uses a `:` in another way, such as a conditional operator:</span></span>

```csharp
public string GetGradePointPercentages() =>
    $"Name: {LastName}, {FirstName}. G.P.A: {Grades.Any() ? Grades.Average() : double.NaN:F2}";
```

<span data-ttu-id="c8460-247">V předchozím příkladu `:` je analyzován jako začátek formátovací řetězec, podmiňovací operátor není součástí.</span><span class="sxs-lookup"><span data-stu-id="c8460-247">In the preceding example, the `:` is parsed as the beginning of the format string, not part of the conditional operator.</span></span> <span data-ttu-id="c8460-248">Ve všech případech, kdy k tomu dojde je možné ohraničit výrazu v závorkách k vynucení Kompilátor interpretuje výraz jako určené pro instalaci:</span><span class="sxs-lookup"><span data-stu-id="c8460-248">In all cases where this happens, you can surround the expression with parentheses to force the compiler to interpret the expression as you intend:</span></span>

[!code-csharp[stringInterpolationConditional](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationConditional)]

<span data-ttu-id="c8460-249">Nejsou k dispozici žádné omezení na výrazy, které můžete umístit mezi závorkami.</span><span class="sxs-lookup"><span data-stu-id="c8460-249">There aren't any limitations on the expressions you can place between the braces.</span></span> <span data-ttu-id="c8460-250">Můžete spustit složitého dotazu LINQ v interpolovaném řetězci provádět výpočty a zobrazí výsledek:</span><span class="sxs-lookup"><span data-stu-id="c8460-250">You can execute a complex LINQ query inside an interpolated string to perform computations and display the result:</span></span>

[!code-csharp[stringInterpolationLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationLinq)]

<span data-ttu-id="c8460-251">Zobrazí se od této ukázky můžete dokonce vnořit řetězcového výrazu interpolace uvnitř jiného výrazu interpolace řetězce.</span><span class="sxs-lookup"><span data-stu-id="c8460-251">You can see from this sample that you can even nest a string interpolation expression inside another string interpolation expression.</span></span> <span data-ttu-id="c8460-252">V tomto příkladu je velmi pravděpodobné, byste měli složitější než na kolik máte v produkčním kódu.</span><span class="sxs-lookup"><span data-stu-id="c8460-252">This example is very likely more complex than you would want in production code.</span></span>
<span data-ttu-id="c8460-253">Místo toho je příkladem škálu funkci.</span><span class="sxs-lookup"><span data-stu-id="c8460-253">Rather, it is illustrative of the breadth of the feature.</span></span> <span data-ttu-id="c8460-254">Libovolný výraz C# je možné použít ve složených závorkách interpolovaného řetězce.</span><span class="sxs-lookup"><span data-stu-id="c8460-254">Any C# expression can be placed between the curly braces of an interpolated string.</span></span>

### <a name="string-interpolation-and-specific-cultures"></a><span data-ttu-id="c8460-255">Interpolace řetězců a specifické jazykové verze</span><span class="sxs-lookup"><span data-stu-id="c8460-255">String interpolation and specific cultures</span></span>

<span data-ttu-id="c8460-256">Všechny příkladů uvedených v předchozí části formátovací řetězce, pomocí aktuální jazykové verze a jazyk na počítači kde spustí kód.</span><span class="sxs-lookup"><span data-stu-id="c8460-256">All the examples shown in the preceding section format the strings using the current culture and language on the machine where the code executes.</span></span> <span data-ttu-id="c8460-257">Často je potřeba formátovací řetězec vytvořený pomocí konkrétní jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="c8460-257">Often you may need to format the string produced using a specific culture.</span></span>
<span data-ttu-id="c8460-258">Provedete to, které používají skutečnost, že objekt vytvořený testovaným interpolace řetězců lze implicitně převést na <xref:System.FormattableString>.</span><span class="sxs-lookup"><span data-stu-id="c8460-258">To do that use the fact that the object produced by a string interpolation can be implicitly converted to <xref:System.FormattableString>.</span></span>

<span data-ttu-id="c8460-259"><xref:System.FormattableString> Instance obsahuje řetězec formátu a výsledky vyhodnocování výrazů před převedením na řetězce.</span><span class="sxs-lookup"><span data-stu-id="c8460-259">The <xref:System.FormattableString> instance contains the format string, and the results of evaluating the expressions before converting them to strings.</span></span> <span data-ttu-id="c8460-260">Můžete použít veřejné metody <xref:System.FormattableString> zadat jazykovou verzi, při formátování řetězce.</span><span class="sxs-lookup"><span data-stu-id="c8460-260">You can use public methods of <xref:System.FormattableString> to specify the culture when formatting a string.</span></span> <span data-ttu-id="c8460-261">Například následující příklad vytvoří řetězec za použití Německá jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="c8460-261">For example, the following example produces a string using German culture.</span></span> <span data-ttu-id="c8460-262">(Jako oddělovač desetinných míst používá znak "," a "." znak jako tisíců oddělovač.)</span><span class="sxs-lookup"><span data-stu-id="c8460-262">(It uses the ',' character for the decimal separator, and the '.' character as the thousands separator.)</span></span>

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

<span data-ttu-id="c8460-263">Další informace najdete v tématu [interpolace](../language-reference/tokens/interpolated.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="c8460-263">For more information, see the [String interpolation](../language-reference/tokens/interpolated.md) topic.</span></span>

## <a name="exception-filters"></a><span data-ttu-id="c8460-264">Filtry výjimek</span><span class="sxs-lookup"><span data-stu-id="c8460-264">Exception Filters</span></span>

<span data-ttu-id="c8460-265">Další novou funkcí v jazyce C# 6 je *filtry výjimek*.</span><span class="sxs-lookup"><span data-stu-id="c8460-265">Another new feature in C# 6 is *exception filters*.</span></span> <span data-ttu-id="c8460-266">Filtry výjimek jsou klauzule, které určují, kdy by použít klauzuli catch. daný.</span><span class="sxs-lookup"><span data-stu-id="c8460-266">Exception Filters are clauses that determine when a given catch clause should be applied.</span></span>
<span data-ttu-id="c8460-267">Pokud výraz použitý pro filtr výjimek vyhodnocuje na `true`, klauzule catch provádí běžného zpracování při výskytu výjimky.</span><span class="sxs-lookup"><span data-stu-id="c8460-267">If the expression used for an exception filter evaluates to `true`, the catch clause performs its normal processing on an exception.</span></span> <span data-ttu-id="c8460-268">Pokud je výraz vyhodnocen `false`, pak bude `catch` klauzule se přeskočí.</span><span class="sxs-lookup"><span data-stu-id="c8460-268">If the expression evaluates to `false`, then the `catch` clause is skipped.</span></span>

<span data-ttu-id="c8460-269">Zjistit informace o výjimce k určení, zda je jedno použití `catch` klauzule může zpracovat výjimku:</span><span class="sxs-lookup"><span data-stu-id="c8460-269">One use is to examine information about an exception to determine if a `catch` clause can process the exception:</span></span>

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

<span data-ttu-id="c8460-270">Kód vygenerovaný filtry výjimek poskytuje lepší informace o výjimce, která je vyvolána a nebyl zpracován.</span><span class="sxs-lookup"><span data-stu-id="c8460-270">The code generated by exception filters provides better information about an exception that is thrown and not processed.</span></span> <span data-ttu-id="c8460-271">Před filtry výjimek byly přidány do jazyka, je třeba vytvořit kód podobný tomuto:</span><span class="sxs-lookup"><span data-stu-id="c8460-271">Before exception filters were added to the language, you would need to create code like the following:</span></span>

[!code-csharp[ExceptionFilterOld](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilterOld)]

<span data-ttu-id="c8460-272">Místo, kde je vyvolána výjimka změny mezi tyto dva příklady.</span><span class="sxs-lookup"><span data-stu-id="c8460-272">The point where the exception is thrown changes between these two examples.</span></span>
<span data-ttu-id="c8460-273">V předchozím kódu, kde `throw` klauzule, všechny analýzu trasování zásobníku nebo zkoumání výpisy při selhání se zobrazí, že byla vyvolána výjimka z `throw` klauzulí catch příkazu.</span><span class="sxs-lookup"><span data-stu-id="c8460-273">In the previous code, where a `throw` clause is used, any stack trace analysis or examination of crash dumps will show that the exception was thrown from the `throw` statement in your catch clause.</span></span> <span data-ttu-id="c8460-274">Objekt výjimky skutečné obsahovala původní zásobník volání, ale všechny ostatní informace o proměnných v zásobníku volání od tohoto okamžiku throw umístění původního bodu throw bylo ztraceno.</span><span class="sxs-lookup"><span data-stu-id="c8460-274">The actual exception object will contain the original call stack, but all other information about any variables in the call stack between this throw point and the location of the original throw point has been lost.</span></span> 

<span data-ttu-id="c8460-275">Rozdíl oproti, jak se zpracovávají kódu pomocí filtru výjimky: výraz filtru výjimky je vyhodnocen jako `false`.</span><span class="sxs-lookup"><span data-stu-id="c8460-275">Contrast that with how the code using an exception filter is processed: the exception filter expression evaluates to `false`.</span></span> <span data-ttu-id="c8460-276">Proto nikdy zadá provádění `catch` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="c8460-276">Therefore, execution never enters the `catch` clause.</span></span> <span data-ttu-id="c8460-277">Vzhledem k tomu, `catch` klauzule nespustí, žádné odvíjení zásobníku probíhá.</span><span class="sxs-lookup"><span data-stu-id="c8460-277">Because the `catch` clause does not execute, no stack unwinding takes place.</span></span> <span data-ttu-id="c8460-278">Pro ladění činnosti, které by proběhnout později se zachovají, throw znamená, že původní umístění.</span><span class="sxs-lookup"><span data-stu-id="c8460-278">That means the original throw location is preserved for any debugging activities that would take place later.</span></span>

<span data-ttu-id="c8460-279">Kdykoli budete potřebovat k vyhodnocení, pole nebo vlastnosti výjimky, namísto spoléhání se výhradně na typ výjimky, použijte filtr výjimek pro zachování Další informace o ladění.</span><span class="sxs-lookup"><span data-stu-id="c8460-279">Whenever you need to evaluate fields or properties of an exception, instead of relying solely on the exception type, use an exception filter to preserve more debugging information.</span></span>

<span data-ttu-id="c8460-280">Další doporučené vzor s filtry výjimek je k jejich použití pro rutiny protokolování.</span><span class="sxs-lookup"><span data-stu-id="c8460-280">Another recommended pattern with exception filters is to use them for logging routines.</span></span> <span data-ttu-id="c8460-281">Toto použití také využívá způsobem, ve kterém je zachová bodu vyvolání výjimky, i když filtr výjimek vyhodnocuje na `false`.</span><span class="sxs-lookup"><span data-stu-id="c8460-281">This usage also leverages the manner in which the exception throw point is preserved when an exception filter evaluates to `false`.</span></span>

<span data-ttu-id="c8460-282">Metoda protokolování bude metodou, jehož argumentem je výjimka, která bezpodmínečně vrací hodnotu `false`:</span><span class="sxs-lookup"><span data-stu-id="c8460-282">A logging method would be a method whose argument is the exception that unconditionally returns `false`:</span></span>

[!code-csharp[ExceptionFilterLogging](../../../samples/snippets/csharp/new-in-6/ExceptionFilterHelpers.cs#ExceptionFilterLogging)]

<span data-ttu-id="c8460-283">Pokaždé, když se chcete přihlásit k výjimce, můžete přidat klauzuli catch a tuto metodu použít jako filtr výjimek:</span><span class="sxs-lookup"><span data-stu-id="c8460-283">Whenever you want to log an exception, you can add a catch clause, and use this method as the exception filter:</span></span>

[!code-csharp[LogException](../../../samples/snippets/csharp/new-in-6/program.cs#LogException)]

<span data-ttu-id="c8460-284">Výjimky jsou nikdy zachycena, protože `LogException` metoda vždy vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="c8460-284">The exceptions are never caught, because the `LogException` method always returns `false`.</span></span> <span data-ttu-id="c8460-285">Tento filtr výjimek vždy false znamená, že tato obslužná rutina protokolování před všechny ostatní obslužné rutiny výjimek můžete umístit:</span><span class="sxs-lookup"><span data-stu-id="c8460-285">That always false exception filter means that you can place this logging handler before any other exception handlers:</span></span>

[!code-csharp[LogExceptionRecovery](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionRecovery)]

<span data-ttu-id="c8460-286">V předchozím příkladu jsou zvýrazněné velmi důležitý aspekt filtry výjimek.</span><span class="sxs-lookup"><span data-stu-id="c8460-286">The preceding example highlights a very important facet of exception filters.</span></span>
<span data-ttu-id="c8460-287">Filtry výjimek umožňují scénáře, ve kterém může obecnější klauzuli catch. výjimky vyskytovat před konkrétnější jeden.</span><span class="sxs-lookup"><span data-stu-id="c8460-287">The exception filters enable scenarios where a more general exception catch clause may appear before a more specific one.</span></span> <span data-ttu-id="c8460-288">Je také možné mít stejný typ výjimky, se zobrazí ve více klauzulí catch:</span><span class="sxs-lookup"><span data-stu-id="c8460-288">It's also possible to have the same exception type appear in multiple catch clauses:</span></span>

[!code-csharp[HandleNotChanged](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#HandleNotChanged)]

<span data-ttu-id="c8460-289">Další doporučené vzor zabraňuje klauzule catch zpracování výjimek, když je připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="c8460-289">Another recommended pattern helps prevent catch clauses from processing exceptions when a debugger is attached.</span></span> <span data-ttu-id="c8460-290">Tato technika umožňuje spouštět aplikace s ladicím programem a zastavit provádění, když dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="c8460-290">This technique enables you to run an application with the debugger, and stop execution when an exception is thrown.</span></span>

<span data-ttu-id="c8460-291">Ve vašem kódu přidejte filtr výjimek, aby kód pro obnovení provádí pouze v případě, že není připojený ladicí program:</span><span class="sxs-lookup"><span data-stu-id="c8460-291">In your code, add an exception filter so that any recovery code executes only when a debugger is not attached:</span></span>

[!code-csharp[LogExceptionDebugger](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionDebugger)]

<span data-ttu-id="c8460-292">Po přidání tohoto v kódu, nastavujete ladicí program na přerušení na všechny neošetřené výjimky.</span><span class="sxs-lookup"><span data-stu-id="c8460-292">After adding this in code, you set your debugger to break on all unhandled exceptions.</span></span> <span data-ttu-id="c8460-293">Spuštění programu v ladicím programu a ladicí program přeruší vždy, když `PerformFailingOperation()` vyvolá `RecoverableException`.</span><span class="sxs-lookup"><span data-stu-id="c8460-293">Run the program under the debugger, and the debugger breaks whenever `PerformFailingOperation()` throws a `RecoverableException`.</span></span>
<span data-ttu-id="c8460-294">Ladicí program přeruší programu, protože klauzule catch nebude provedeno z důvodu výjimky filtr vrátí hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="c8460-294">The debugger breaks your program, because the catch clause won't be executed due to the false-returning exception filter.</span></span>

## <a name="nameof-expressions"></a><span data-ttu-id="c8460-295">`nameof` Výrazy</span><span class="sxs-lookup"><span data-stu-id="c8460-295">`nameof` Expressions</span></span>

<span data-ttu-id="c8460-296">`nameof` Výraz vyhodnocen jako název symbolu.</span><span class="sxs-lookup"><span data-stu-id="c8460-296">The `nameof` expression evaluates to the name of a symbol.</span></span> <span data-ttu-id="c8460-297">To je skvělý způsob, jak získat nástroje pracovat pokaždé, když budete potřebovat název proměnné, vlastnost nebo pole členů.</span><span class="sxs-lookup"><span data-stu-id="c8460-297">It's a great way to get tools working whenever you need the name of a variable, a property, or a member field.</span></span>

<span data-ttu-id="c8460-298">Jeden z nejčastěji používaných používá pro `nameof` je k poskytnutí názvu symbolu, která způsobila výjimku:</span><span class="sxs-lookup"><span data-stu-id="c8460-298">One of the most common uses for `nameof` is to provide the name of a symbol that caused an exception:</span></span>

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

<span data-ttu-id="c8460-299">Další možností použití je s XAML na základě aplikace, které implementují `INotifyPropertyChanged` rozhraní:</span><span class="sxs-lookup"><span data-stu-id="c8460-299">Another use is with XAML based applications that implement the `INotifyPropertyChanged` interface:</span></span>

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

<span data-ttu-id="c8460-300">Výhodou použití `nameof` operátor přes konstantní řetězce je, že nástroje by rozuměla symbolu.</span><span class="sxs-lookup"><span data-stu-id="c8460-300">The advantage of using the `nameof` operator over a constant string is that tools can understand the symbol.</span></span> <span data-ttu-id="c8460-301">Pokud používáte nástroje pro refaktoring Přejmenování symbolu, ji budou přejmenujte ji v `nameof` výrazu.</span><span class="sxs-lookup"><span data-stu-id="c8460-301">If you use refactoring tools to rename the symbol, it will rename it in the `nameof` expression.</span></span> <span data-ttu-id="c8460-302">Konstantní řetězce nemají tuto výhodu.</span><span class="sxs-lookup"><span data-stu-id="c8460-302">Constant strings don't have that advantage.</span></span> <span data-ttu-id="c8460-303">Vyzkoušejte si to sami ve svém oblíbeném editoru: přejmenování proměnnou a všechny `nameof` výrazy budou aktualizovat také.</span><span class="sxs-lookup"><span data-stu-id="c8460-303">Try it yourself in your favorite editor: rename a variable, and any `nameof` expressions will update as well.</span></span>

<span data-ttu-id="c8460-304">`nameof` Výraz vytvoří neúplný název svého argumentu (`LastName` v předchozích příkladech) i v případě, že používáte plně kvalifikovaný název argumentu:</span><span class="sxs-lookup"><span data-stu-id="c8460-304">The `nameof` expression produces the unqualified name of its argument (`LastName` in the previous examples) even if you use the fully qualified name for the argument:</span></span>

[!code-csharp[QualifiedNameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#QualifiedNameofNotify)]

<span data-ttu-id="c8460-305">To `nameof` výraz vytvoří `FirstName`, nikoli `UXComponents.ViewModel.FirstName`.</span><span class="sxs-lookup"><span data-stu-id="c8460-305">This `nameof` expression produces `FirstName`, not `UXComponents.ViewModel.FirstName`.</span></span>

## <a name="await-in-catch-and-finally-blocks"></a><span data-ttu-id="c8460-306">Operátor await v Catch a blocích Finally</span><span class="sxs-lookup"><span data-stu-id="c8460-306">Await in Catch and Finally blocks</span></span>

<span data-ttu-id="c8460-307">C# 5 má několik omezení kde mohli byste umístit `await` výrazy.</span><span class="sxs-lookup"><span data-stu-id="c8460-307">C# 5 had several limitations around where you could place `await` expressions.</span></span>
<span data-ttu-id="c8460-308">Jedna z těchto byla odebrána v jazyce C# 6.</span><span class="sxs-lookup"><span data-stu-id="c8460-308">One of those has been removed in C# 6.</span></span> <span data-ttu-id="c8460-309">Teď můžete použít `await` v `catch` nebo `finally` výrazy.</span><span class="sxs-lookup"><span data-stu-id="c8460-309">You can now use `await` in `catch` or `finally` expressions.</span></span> 

<span data-ttu-id="c8460-310">Přidání await výrazy v catch a finally může zdát zkomplikovat ty zpracování bloky.</span><span class="sxs-lookup"><span data-stu-id="c8460-310">The addition of await expressions in catch and finally blocks may appear to complicate how those are processed.</span></span> <span data-ttu-id="c8460-311">Přidejme popisují, jak se zobrazuje příklad.</span><span class="sxs-lookup"><span data-stu-id="c8460-311">Let's add an example to discuss how this appears.</span></span> <span data-ttu-id="c8460-312">V asynchronní metody, výrazu await v můžete klauzule finally.</span><span class="sxs-lookup"><span data-stu-id="c8460-312">In any async method, you can use an await expression in a finally clause.</span></span>

<span data-ttu-id="c8460-313">Pomocí jazyka C# 6 může také čekat ve výrazech catch.</span><span class="sxs-lookup"><span data-stu-id="c8460-313">With C# 6, you can also await in catch expressions.</span></span> <span data-ttu-id="c8460-314">To se nejčastěji používá v případě protokolování:</span><span class="sxs-lookup"><span data-stu-id="c8460-314">This is most often used with logging scenarios:</span></span>

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

<span data-ttu-id="c8460-315">Podrobnosti implementace pro přidání `await` podporovala uvnitř `catch` a `finally` klauzule zajistí, že její chování je konzistentní s chování pro synchronní kód.</span><span class="sxs-lookup"><span data-stu-id="c8460-315">The implementation details for adding `await` support inside `catch` and `finally` clauses ensures that the behavior is consistent with the behavior for synchronous code.</span></span> <span data-ttu-id="c8460-316">Při spouštění kódu v `catch` nebo `finally` klauzule vyvolá výjimku, provádění hledá vhodný `catch` klauzule v další okolní bloku.</span><span class="sxs-lookup"><span data-stu-id="c8460-316">When code executed in a `catch` or `finally` clause throws, execution looks for a suitable `catch` clause in the next surrounding block.</span></span> <span data-ttu-id="c8460-317">Pokud se aktuální výjimku, tato výjimka bude ztracena.</span><span class="sxs-lookup"><span data-stu-id="c8460-317">If there was a current exception, that exception is lost.</span></span> <span data-ttu-id="c8460-318">Stejné se stane s očekávané výrazy v `catch` a `finally` klauzulí: vhodný `catch` prohledána, a na aktuální výjimku, pokud existuje, dojde ke ztrátě.</span><span class="sxs-lookup"><span data-stu-id="c8460-318">The same happens with awaited expressions in `catch` and `finally` clauses: a suitable `catch` is searched for, and the current exception, if any, is lost.</span></span>  

> [!NOTE]
> <span data-ttu-id="c8460-319">Toto chování je z důvodu se doporučuje pro zápis `catch` a `finally` klauzule pečlivě, aby nedošlo k zavedení nové výjimky.</span><span class="sxs-lookup"><span data-stu-id="c8460-319">This behavior is the reason it's recommended to write `catch` and `finally` clauses carefully, to avoid introducing new exceptions.</span></span>

## <a name="index-initializers"></a><span data-ttu-id="c8460-320">Inicializátory indexů</span><span class="sxs-lookup"><span data-stu-id="c8460-320">Index Initializers</span></span>

<span data-ttu-id="c8460-321">*Inicializátory indexů* je jedním ze dvou funkcí, které usnadňují inicializátory kolekce konzistentnější s využitím indexu.</span><span class="sxs-lookup"><span data-stu-id="c8460-321">*Index Initializers* is one of two features that make collection initializers more consistent with index usage.</span></span> <span data-ttu-id="c8460-322">V dřívějších verzích jazyka C#, můžete použít *inicializátory kolekce* pouze s kolekcemi styl sekvence, včetně <xref:System.Collections.Generic.Dictionary%602> přidáním závorek kolem páry klíč-hodnota:</span><span class="sxs-lookup"><span data-stu-id="c8460-322">In earlier releases of C#, you could use *collection initializers* only with sequence style collections, including <xref:System.Collections.Generic.Dictionary%602> by adding braces around key and value pairs:</span></span>

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#ListInitializer)]

<span data-ttu-id="c8460-323">Teď je můžete využít s <xref:System.Collections.Generic.Dictionary%602> kolekce a podobné typy.</span><span class="sxs-lookup"><span data-stu-id="c8460-323">Now, you can use them with <xref:System.Collections.Generic.Dictionary%602> collections and similar types.</span></span> <span data-ttu-id="c8460-324">Nová syntaxe podporuje přiřazení do kolekce pomocí indexu:</span><span class="sxs-lookup"><span data-stu-id="c8460-324">The new syntax supports assignment using an index into the collection:</span></span>

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

<span data-ttu-id="c8460-325">Tato funkce znamená, že asociativní kontejnery mohou být inicializovány pomocí syntaxe podobné co bylo nastavené pro kontejnery sekvence pro několik verzí.</span><span class="sxs-lookup"><span data-stu-id="c8460-325">This feature means that associative containers can be initialized using syntax similar to what's been in place for sequence containers for several versions.</span></span>

## <a name="extension-add-methods-in-collection-initializers"></a><span data-ttu-id="c8460-326">Rozšíření `Add` metody v inicializátory kolekce</span><span class="sxs-lookup"><span data-stu-id="c8460-326">Extension `Add` methods in collection initializers</span></span>

<span data-ttu-id="c8460-327">Další funkce, která usnadňuje inicializace kolekce je schopnost používat *– metoda rozšíření* pro `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="c8460-327">Another feature that makes collection initialization easier is the ability to use an *extension method* for the `Add` method.</span></span> <span data-ttu-id="c8460-328">Tato funkce byla přidána parita s jazykem Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c8460-328">This feature was added for parity with Visual Basic.</span></span> 

<span data-ttu-id="c8460-329">Tato funkce je nejužitečnější v případě, že máte vlastní třídu kolekce, která obsahuje metodu s jiným názvem sémanticky přidávat nové položky.</span><span class="sxs-lookup"><span data-stu-id="c8460-329">The feature is most useful when you have a custom collection class that has a method with a different name to semantically add new items.</span></span>

<span data-ttu-id="c8460-330">Představte si třeba kolekce studentů takto:</span><span class="sxs-lookup"><span data-stu-id="c8460-330">For example, consider a collection of students like this:</span></span>

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]

<span data-ttu-id="c8460-331">`Enroll` Metoda přidá student.</span><span class="sxs-lookup"><span data-stu-id="c8460-331">The `Enroll` method adds a student.</span></span> <span data-ttu-id="c8460-332">Ale jeho není postupujte `Add` vzor.</span><span class="sxs-lookup"><span data-stu-id="c8460-332">But it doesn't follow the `Add` pattern.</span></span>
<span data-ttu-id="c8460-333">V předchozích verzích jazyka C#, nelze používat inicializátory kolekce s `Enrollment` objektu:</span><span class="sxs-lookup"><span data-stu-id="c8460-333">In previous versions of C#, you could not use collection initializers with an `Enrollment` object:</span></span>

[!code-csharp[InitializeEnrollment](../../../samples/snippets/csharp/new-in-6/classList.cs#InitializeEnrollment)]

<span data-ttu-id="c8460-334">Nyní můžete, ale pouze v případě, že vytvoření metody rozšíření, která mapuje `Add` k `Enroll`:</span><span class="sxs-lookup"><span data-stu-id="c8460-334">Now you can, but only if you create an extension method that maps `Add` to `Enroll`:</span></span>

[!code-csharp[ExtensionAdd](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAdd)]

<span data-ttu-id="c8460-335">Co právě děláte pomocí této funkce je k mapování libovolné metody přidá položky do kolekce na metodu s názvem `Add` tak, že vytvoříte metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="c8460-335">What you are doing with this feature is to map whatever method adds items to a collection to a method named `Add` by creating an extension method.</span></span>

## <a name="improved-overload-resolution"></a><span data-ttu-id="c8460-336">Vylepšené přetížení</span><span class="sxs-lookup"><span data-stu-id="c8460-336">Improved overload resolution</span></span>

<span data-ttu-id="c8460-337">Tato funkce poslední je ten, který pravděpodobně nebude oznámení.</span><span class="sxs-lookup"><span data-stu-id="c8460-337">This last feature is one you probably won't notice.</span></span> <span data-ttu-id="c8460-338">Došlo k konstrukce předchozí verze kompilátoru jazyka C# může kde najdete některé volání metody zahrnující nejednoznačné výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="c8460-338">There were constructs where the previous version of the C# compiler may have found some method calls involving lambda expressions ambiguous.</span></span> <span data-ttu-id="c8460-339">Vezměte v úvahu tuto metodu:</span><span class="sxs-lookup"><span data-stu-id="c8460-339">Consider this method:</span></span>

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

<span data-ttu-id="c8460-340">Voláním této metody pomocí syntaxe metody skupiny selže v dřívějších verzích jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="c8460-340">In earlier versions of C#, calling that method using the method group syntax would fail:</span></span>

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]
 
<span data-ttu-id="c8460-341">Kompilátor starší nelze rozlišit správně mezi `Task.Run(Action)` a `Task.Run(Func<Task>())`.</span><span class="sxs-lookup"><span data-stu-id="c8460-341">The earlier compiler could not distinguish correctly between `Task.Run(Action)` and `Task.Run(Func<Task>())`.</span></span> <span data-ttu-id="c8460-342">V předchozích verzích je třeba použít výraz lambda jako argument:</span><span class="sxs-lookup"><span data-stu-id="c8460-342">In previous versions, you'd need to use a lambda expression as an argument:</span></span>

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

<span data-ttu-id="c8460-343">Určuje, který kompilátor jazyka C# 6 správně `Task.Run(Func<Task>())` je lepší volbou.</span><span class="sxs-lookup"><span data-stu-id="c8460-343">The C# 6 compiler correctly determines that `Task.Run(Func<Task>())` is a better choice.</span></span>

### <a name="deterministic-compiler-output"></a><span data-ttu-id="c8460-344">Výstup kompilátoru deterministické</span><span class="sxs-lookup"><span data-stu-id="c8460-344">Deterministic compiler output</span></span>

<span data-ttu-id="c8460-345">`-deterministic` Možnost instruuje kompilátor, aby vytvořit bajt po bajtu identické výstupního sestavení po sobě následujících souborů stejných zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="c8460-345">The `-deterministic` option instructs the compiler to produce a byte-for-byte identical output assembly for successive compilations of the same source files.</span></span>

<span data-ttu-id="c8460-346">Ve výchozím nastavení vytvoří každé kompilaci jedinečný výstup na každý kompilace.</span><span class="sxs-lookup"><span data-stu-id="c8460-346">By default, every compilation produces unique output on each compilation.</span></span> <span data-ttu-id="c8460-347">Kompilátor přidá časové razítko a identifikátor GUID vygenerovaný z náhodných čísel.</span><span class="sxs-lookup"><span data-stu-id="c8460-347">The compiler adds a timestamp, and a GUID generated from random numbers.</span></span> <span data-ttu-id="c8460-348">Tuto možnost použijte, pokud chcete k porovnání pro bajtech výstupu k zajištění konzistence se v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="c8460-348">You use this option if you want to compare the byte-for-byte output to ensure consistency across builds.</span></span>

<span data-ttu-id="c8460-349">Další informace najdete v tématu [– možnost kompilátoru deterministické](../language-reference/compiler-options/deterministic-compiler-option.md) článku.</span><span class="sxs-lookup"><span data-stu-id="c8460-349">For more information, see the [-deterministic compiler option](../language-reference/compiler-options/deterministic-compiler-option.md) article.</span></span>
