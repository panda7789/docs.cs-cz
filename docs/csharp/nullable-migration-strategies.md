---
title: Aktualizace základu kódu pro použití typů odkazů s možnou hodnotou null
description: Vyberte si nejlepší strategii pro upgrade základu kódu pro použití typů odkazů s možnou hodnotou null.
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: 5909eb9ffe1f5398fc2eb74848b82f8fe9516548
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975331"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a><span data-ttu-id="c5b55-103">Aktualizace knihoven pro použití typů odkazů s možnou hodnotou null a sdělování pravidel s možnou hodnotou null volajícím</span><span class="sxs-lookup"><span data-stu-id="c5b55-103">Update libraries to use nullable reference types and communicate nullable rules to callers</span></span>

<span data-ttu-id="c5b55-104">Přidání [odkazových typů s možnou hodnotou null](nullable-references.md) znamená, že můžete deklarovat `null` , zda je nebo není hodnota pro každou proměnnou povolena nebo očekávána.</span><span class="sxs-lookup"><span data-stu-id="c5b55-104">The addition of [nullable reference types](nullable-references.md) means you can declare whether or not a `null` value is allowed or expected for every variable.</span></span> <span data-ttu-id="c5b55-105">Kromě toho můžete použít několik `AllowNull`atributů:, `DisallowNull`, `MaybeNull`, `NotNull`, `NotNullWhen`, `MaybeNullWhen`a `NotNullIfNotNull` k úplnému popisu stavů null argumentů a vrácených hodnot.</span><span class="sxs-lookup"><span data-stu-id="c5b55-105">In addition, you can apply a number of attributes: `AllowNull`, `DisallowNull`, `MaybeNull`, `NotNull`, `NotNullWhen`, `MaybeNullWhen`, and `NotNullIfNotNull` to completely describe the null states of argument and return values.</span></span> <span data-ttu-id="c5b55-106">Poskytuje skvělé prostředí při psaní kódu.</span><span class="sxs-lookup"><span data-stu-id="c5b55-106">That provides a great experience as you write code.</span></span> <span data-ttu-id="c5b55-107">Zobrazí se upozornění, pokud může být proměnná bez hodnoty null nastavena na `null`.</span><span class="sxs-lookup"><span data-stu-id="c5b55-107">You get warnings if a non-nullable variable might be set to `null`.</span></span> <span data-ttu-id="c5b55-108">Zobrazí se upozornění, pokud u proměnné s možnou hodnotou null není zkontrolována hodnota null před tím, než ji zrušíte.</span><span class="sxs-lookup"><span data-stu-id="c5b55-108">You get warnings if a nullable variable isn't null-checked before you dereference it.</span></span> <span data-ttu-id="c5b55-109">Aktualizace knihoven může chvíli trvat, ale výnosy je.</span><span class="sxs-lookup"><span data-stu-id="c5b55-109">Updating your libraries can take time, but the payoffs are worth it.</span></span> <span data-ttu-id="c5b55-110">Další informace, které pro kompilátor poskytnete, *Pokud* je `null` hodnota povolená nebo zakázaná, budou se vám lépe zobrazovat uživatelé vašeho rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="c5b55-110">The more information you provide to the compiler about *when* a `null` value is allowed or prohibited, the better warnings users of your API will get.</span></span> <span data-ttu-id="c5b55-111">Pojďme začít se známým příkladem.</span><span class="sxs-lookup"><span data-stu-id="c5b55-111">Let's start with a familiar example.</span></span> <span data-ttu-id="c5b55-112">Představte si, že knihovna má následující rozhraní API k načtení řetězce prostředků:</span><span class="sxs-lookup"><span data-stu-id="c5b55-112">Imagine your library has the following API to retrieve a resource string:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="c5b55-113">Předchozí příklad se řídí známým `Try*` vzorem v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="c5b55-113">The preceding example follows the familiar `Try*` pattern in .NET.</span></span> <span data-ttu-id="c5b55-114">Pro toto rozhraní API existují dva argumenty odkazů: `key` a `message` parametr.</span><span class="sxs-lookup"><span data-stu-id="c5b55-114">There are two reference arguments for this API: the `key` and the `message` parameter.</span></span> <span data-ttu-id="c5b55-115">Toto rozhraní API má následující pravidla týkající se hodnoty null těchto argumentů:</span><span class="sxs-lookup"><span data-stu-id="c5b55-115">This API has the following rules relating to the nullness of these arguments:</span></span>

- <span data-ttu-id="c5b55-116">Volající by neměli předat `null` jako argument pro `key`.</span><span class="sxs-lookup"><span data-stu-id="c5b55-116">Callers shouldn't pass `null` as the argument for `key`.</span></span>
- <span data-ttu-id="c5b55-117">Volající mohou předat proměnnou, jejíž hodnota je `null` jako argument pro. `message`</span><span class="sxs-lookup"><span data-stu-id="c5b55-117">Callers can pass a variable whose value is `null` as the argument for `message`.</span></span>
- <span data-ttu-id="c5b55-118">Pokud `TryGetMessage` metoda vrátí `true`hodnotu, hodnota `message` není null.</span><span class="sxs-lookup"><span data-stu-id="c5b55-118">If the `TryGetMessage` method returns `true`, the value of `message` isn't null.</span></span> <span data-ttu-id="c5b55-119">Pokud je návratovou hodnotou `false,` hodnota `message` (a její stav null), má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="c5b55-119">If the return value is `false,` the value of `message` (and its null state) is null.</span></span>

<span data-ttu-id="c5b55-120">Pravidlo pro `key` může být zcela vyjádřeno typem proměnné: `key` typ odkazu, který neumožňuje hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="c5b55-120">The rule for `key` can be completely expressed by the variable type: `key` should be a non-nullable reference type.</span></span> <span data-ttu-id="c5b55-121">`message` Parametr je složitější.</span><span class="sxs-lookup"><span data-stu-id="c5b55-121">The `message` parameter is more complex.</span></span> <span data-ttu-id="c5b55-122">To umožňuje `null` jako argument, ale zaručuje, že po úspěšném dokončení tento `out` argument nemá hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="c5b55-122">It allows `null` as the argument, but guarantees that, on success, that `out` argument isn't null.</span></span> <span data-ttu-id="c5b55-123">V těchto scénářích potřebujete podrobnější slovník, který popisuje očekávání.</span><span class="sxs-lookup"><span data-stu-id="c5b55-123">For these scenarios, you need a richer vocabulary to describe the expectations.</span></span>

<span data-ttu-id="c5b55-124">Aktualizace knihovny pro odkazy s možnou hodnotou null vyžaduje více `?` než automatické automatických zadávání u některých proměnných a názvů typů.</span><span class="sxs-lookup"><span data-stu-id="c5b55-124">Updating your library for nullable references requires more than sprinkling `?` on some of the variables and type names.</span></span> <span data-ttu-id="c5b55-125">Předchozí příklad ukazuje, že je nutné projít vaše rozhraní API a vzít v úvahu vaše očekávání pro každý vstupní argument.</span><span class="sxs-lookup"><span data-stu-id="c5b55-125">The preceding example shows that you need to examine your APIs and consider your expectations for each input argument.</span></span> <span data-ttu-id="c5b55-126">Vezměte v úvahu záruky pro vrácenou hodnotu a jakékoli `out` argumenty `ref` nebo argumentů, které vrátí metoda.</span><span class="sxs-lookup"><span data-stu-id="c5b55-126">Consider the guarantees for the return value, and any `out` or `ref` arguments upon the method's return.</span></span> <span data-ttu-id="c5b55-127">Potom tyto pravidla sdělí kompilátoru a kompilátor poskytne upozornění, pokud se volajícím tyto pravidla neřídí.</span><span class="sxs-lookup"><span data-stu-id="c5b55-127">Then communicate those rules to the compiler, and the compiler will provide warnings when callers don't abide by those rules.</span></span>

<span data-ttu-id="c5b55-128">Tato práce trvá určitou dobu.</span><span class="sxs-lookup"><span data-stu-id="c5b55-128">This work takes time.</span></span> <span data-ttu-id="c5b55-129">Pojďme začít s strategiemi, které vaší knihovně nebo aplikaci zohledňují hodnoty null, zatímco se vyrovnávají další požadavky a dodávky.</span><span class="sxs-lookup"><span data-stu-id="c5b55-129">Let's start with strategies to make your library or application nullable-aware, while balancing other requirements and deliverables.</span></span> <span data-ttu-id="c5b55-130">Uvidíte, jak vyrovnávat průběžný vývoj a povolit typy odkazů s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="c5b55-130">You'll see how to balance ongoing development enabling nullable reference types.</span></span> <span data-ttu-id="c5b55-131">Seznámíte se s problémy s definicemi obecného typu.</span><span class="sxs-lookup"><span data-stu-id="c5b55-131">You'll learn challenges for generic type definitions.</span></span> <span data-ttu-id="c5b55-132">Dozvíte se, jak použít atributy k popisu před a po jednotlivých podmínkách rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="c5b55-132">You'll learn to apply attributes to describe pre- and post-conditions on individual APIs.</span></span>

## <a name="choose-a-strategy-for-nullable-reference-types"></a><span data-ttu-id="c5b55-133">Zvolit strategii pro typy odkazů s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="c5b55-133">Choose a strategy for nullable reference types</span></span>

<span data-ttu-id="c5b55-134">První volbou je, že ve výchozím nastavení by se měly zapnout nebo vypnout typy odkazů s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="c5b55-134">The first choice is whether nullable reference types should be on or off by default.</span></span> <span data-ttu-id="c5b55-135">Máte dvě strategie:</span><span class="sxs-lookup"><span data-stu-id="c5b55-135">You have two strategies:</span></span>

- <span data-ttu-id="c5b55-136">Povolte typy odkazů s možnou hodnotou null pro celý projekt a zakažte ho v kódu, který není připravený.</span><span class="sxs-lookup"><span data-stu-id="c5b55-136">Enable nullable reference types for the entire project, and disable it in code that's not ready.</span></span>
- <span data-ttu-id="c5b55-137">Povolit pouze typy odkazů s možnou hodnotou null pro kód, který je opatřen poznámkou pro typy s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="c5b55-137">Only enable nullable reference types for code that's been annotated for nullable reference types.</span></span>

<span data-ttu-id="c5b55-138">První strategie funguje nejlépe při přidávání dalších funkcí do knihovny při jejich aktualizaci na typy odkazů s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="c5b55-138">The first strategy works best when you're adding other features to the library as you update it for nullable reference types.</span></span> <span data-ttu-id="c5b55-139">Veškerý nový vývoj má na paměti s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="c5b55-139">All new development is nullable aware.</span></span> <span data-ttu-id="c5b55-140">Při aktualizaci existujícího kódu povolíte v těchto třídách typy odkazů s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="c5b55-140">As you update existing code, you enable nullable reference types in those classes.</span></span>

<span data-ttu-id="c5b55-141">Po této první strategii provedete následující:</span><span class="sxs-lookup"><span data-stu-id="c5b55-141">Following this first strategy, you do the following:</span></span>

1. <span data-ttu-id="c5b55-142">Povolte typy odkazů s možnou hodnotou null pro celý projekt `<Nullable>enable</Nullable>` přidáním elementu do souborů *csproj* .</span><span class="sxs-lookup"><span data-stu-id="c5b55-142">Enable nullable reference types for the entire project by adding the `<Nullable>enable</Nullable>` element to your *csproj* files.</span></span>
1. <span data-ttu-id="c5b55-143">Přidejte `#nullable disable` direktivu pragma do každého zdrojového souboru v projektu.</span><span class="sxs-lookup"><span data-stu-id="c5b55-143">Add the `#nullable disable` pragma to every source file in your project.</span></span>
1. <span data-ttu-id="c5b55-144">Při práci na jednotlivých souborech odeberte direktivu pragma a vyřešte všechna upozornění.</span><span class="sxs-lookup"><span data-stu-id="c5b55-144">As you work on each file, remove the pragma and address any warnings.</span></span>

<span data-ttu-id="c5b55-145">Tato první strategie obsahuje více než více práce pro přidání direktivy pragma do každého souboru.</span><span class="sxs-lookup"><span data-stu-id="c5b55-145">This first strategy has more up-front work to add the pragma to every file.</span></span> <span data-ttu-id="c5b55-146">Výhodou je, že každý nový soubor kódu přidaný do projektu bude mít povolenou hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="c5b55-146">The advantage is that every new code file added to the project will be nullable enabled.</span></span> <span data-ttu-id="c5b55-147">Jakékoli nové práce budou mít na paměti nabývat hodnoty null; je nutné aktualizovat pouze existující kód.</span><span class="sxs-lookup"><span data-stu-id="c5b55-147">Any new work will be nullable aware; only existing code must be updated.</span></span>

<span data-ttu-id="c5b55-148">Druhá strategie funguje lépe, pokud je knihovna obecně stabilní a hlavní fokus vývoje je přijmout typy odkazů s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="c5b55-148">The second strategy works better if the library is generally stable, and the main focus of the development is to adopt nullable reference types.</span></span> <span data-ttu-id="c5b55-149">Při přidávání poznámek k rozhraním API můžete zapnout typy odkazů s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="c5b55-149">You turn on nullable reference types as you annotate APIs.</span></span> <span data-ttu-id="c5b55-150">Až budete hotovi, povolte v celém projektu typy odkazů s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="c5b55-150">When you've finished, you enable nullable reference types for the entire project.</span></span>

<span data-ttu-id="c5b55-151">Po této druhé strategii provedete následující:</span><span class="sxs-lookup"><span data-stu-id="c5b55-151">Following this second strategy you do the following:</span></span>

1. <span data-ttu-id="c5b55-152">Přidejte `#nullable enable` direktivu pragma do souboru, pro který chcete nastavit nepovolenou hodnotu s podporou.</span><span class="sxs-lookup"><span data-stu-id="c5b55-152">Add the `#nullable enable` pragma to the file you want to make nullable aware.</span></span>
1. <span data-ttu-id="c5b55-153">Vyřešte všechna upozornění.</span><span class="sxs-lookup"><span data-stu-id="c5b55-153">Address any warnings.</span></span>
1. <span data-ttu-id="c5b55-154">Pokračujte v těchto prvních dvou krocích, dokud nebudete mít k celou knihovnu s podporou null.</span><span class="sxs-lookup"><span data-stu-id="c5b55-154">Continue these first two steps until you've made the entire library nullable aware.</span></span>
1. <span data-ttu-id="c5b55-155">Povolit typy s možnou hodnotou null pro celý projekt `<Nullable>enable</Nullable>` přidáním elementu do souborů *csproj* .</span><span class="sxs-lookup"><span data-stu-id="c5b55-155">Enable nullable types for the entire project by adding the `<Nullable>enable</Nullable>` element to your *csproj* files.</span></span>
1. <span data-ttu-id="c5b55-156">Odeberte `#nullable enable` direktivy pragma, protože už nejsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="c5b55-156">Remove the `#nullable enable` pragmas, as they're no longer needed.</span></span>

<span data-ttu-id="c5b55-157">Tato druhá strategie má méně práce předem.</span><span class="sxs-lookup"><span data-stu-id="c5b55-157">This second strategy has less work up-front.</span></span> <span data-ttu-id="c5b55-158">Kompromisy je, že první úkol při vytváření nového souboru je přidání direktivy pragma a zpřístupnění hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="c5b55-158">The tradeoff is that the first task when you create a new file is to add the pragma and make it nullable aware.</span></span> <span data-ttu-id="c5b55-159">Pokud se některý z vývojářů v týmu zapomene, je nový kód v nedokončené práci, aby se zajistilo, že bude mít veškerý kód na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="c5b55-159">If any developers on your team forget, that new code is now in the backlog of work to make all code nullable aware.</span></span>

<span data-ttu-id="c5b55-160">Které z těchto strategií vybíráte, závisí na tom, kolik aktivního vývoje se v projektu provádí.</span><span class="sxs-lookup"><span data-stu-id="c5b55-160">Which of these strategies you pick depends on how much active development is taking place in your project.</span></span> <span data-ttu-id="c5b55-161">Tím se zlepší a stabilnější váš projekt, tím lepší je druhá strategie.</span><span class="sxs-lookup"><span data-stu-id="c5b55-161">The more mature and stable your project, the better the second strategy.</span></span> <span data-ttu-id="c5b55-162">Vyvíjejí se další funkce, což je lepší první strategie.</span><span class="sxs-lookup"><span data-stu-id="c5b55-162">The more features being developed, the better the first strategy.</span></span>

## <a name="should-nullable-warnings-introduce-breaking-changes"></a><span data-ttu-id="c5b55-163">Má upozornění na hodnotu null zavést průlomové změny?</span><span class="sxs-lookup"><span data-stu-id="c5b55-163">Should nullable warnings introduce breaking changes?</span></span>

<span data-ttu-id="c5b55-164">Než povolíte typy odkazů s možnou hodnotou null, jsou proměnné považovány za *Nullable oblivious*.</span><span class="sxs-lookup"><span data-stu-id="c5b55-164">Before you enable nullable reference types, variables are considered *nullable oblivious*.</span></span> <span data-ttu-id="c5b55-165">Jakmile povolíte typy odkazů s možnou hodnotou null, všechny tyto proměnné nebudou *mít hodnotu null*.</span><span class="sxs-lookup"><span data-stu-id="c5b55-165">Once you enable nullable reference types, all those variables are *non-nullable*.</span></span> <span data-ttu-id="c5b55-166">Kompilátor bude vydávat upozornění, pokud tyto proměnné nejsou inicializovány na hodnoty, které nejsou null.</span><span class="sxs-lookup"><span data-stu-id="c5b55-166">The compiler will issue warnings if those variables aren't initialized to non-null values.</span></span>

<span data-ttu-id="c5b55-167">Dalším pravděpodobným zdrojem upozornění je vrácení hodnot, pokud hodnota nebyla inicializována.</span><span class="sxs-lookup"><span data-stu-id="c5b55-167">Another likely source of warnings is return values when the value hasn't been initialized.</span></span>

<span data-ttu-id="c5b55-168">Prvním krokem při adresování upozornění kompilátoru je použití `?` poznámek na parametrech a návratových typech k označení, že argumenty nebo návratové hodnoty mohou být null.</span><span class="sxs-lookup"><span data-stu-id="c5b55-168">The first step in addressing the compiler warnings is to use `?` annotations on parameter and return types to indicate when arguments or return values may be null.</span></span> <span data-ttu-id="c5b55-169">Pokud referenční proměnné nesmí mít hodnotu null, je původní deklarace správná.</span><span class="sxs-lookup"><span data-stu-id="c5b55-169">When reference variables must not be null, the original declaration is correct.</span></span> <span data-ttu-id="c5b55-170">V takovém případě váš cíl nestačí jenom opravit upozornění.</span><span class="sxs-lookup"><span data-stu-id="c5b55-170">As you do this, your goal isn't just to fix warnings.</span></span> <span data-ttu-id="c5b55-171">Důležitější je, že kompilátor porozuměl vašemu záměru pro potenciální hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="c5b55-171">The more important goal is to make the compiler understand your intent for potential null values.</span></span> <span data-ttu-id="c5b55-172">Při kontrole upozornění se dostanete k vašemu dalšímu hlavnímu rozhodnutí o vaší knihovně.</span><span class="sxs-lookup"><span data-stu-id="c5b55-172">As you examine the warnings, you reach your next major decision for your library.</span></span> <span data-ttu-id="c5b55-173">Chcete zvážit úpravu signatur rozhraní API, abyste mohli snadněji sdělit záměr návrhu?</span><span class="sxs-lookup"><span data-stu-id="c5b55-173">Do you want to consider modifying API signatures to more clearly communicate your design intent?</span></span> <span data-ttu-id="c5b55-174">Lepší signatura rozhraní API pro `TryGetMessage` dříve zkoumané metody může být:</span><span class="sxs-lookup"><span data-stu-id="c5b55-174">A better API signature for the `TryGetMessage` method examined earlier could be:</span></span>

```csharp
string? TryGetMessage(string key);
```

<span data-ttu-id="c5b55-175">Vrácená hodnota označuje úspěch nebo neúspěch a přenese hodnotu, pokud byla hodnota nalezena.</span><span class="sxs-lookup"><span data-stu-id="c5b55-175">The return value indicates success or failure, and carries the value if the value was found.</span></span> <span data-ttu-id="c5b55-176">V mnoha případech může změna signatur rozhraní API zlepšit způsob, jakým komunikuje hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="c5b55-176">In many cases, changing API signatures can improve how they communicate null values.</span></span>

<span data-ttu-id="c5b55-177">Pro veřejné knihovny nebo knihovny s velkými základy uživatelů ale můžete raději nezavádět změny signatur rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="c5b55-177">However, for public libraries, or libraries with large user bases, you may prefer not introducing any API signature changes.</span></span> <span data-ttu-id="c5b55-178">Pro tyto případy a další běžné vzory můžete použít atributy pro přesnější definování v případě, že argument nebo návratová hodnota může být `null`.</span><span class="sxs-lookup"><span data-stu-id="c5b55-178">For those cases, and other common patterns, you can apply attributes to more clearly define when an argument or return value may be `null`.</span></span> <span data-ttu-id="c5b55-179">Bez ohledu na to, zda zvažte změnu povrchu rozhraní API, pravděpodobně zjistíte, že tyto anotace typu nejsou dostačující pro `null` popis hodnot argumentů nebo vrácených hodnot.</span><span class="sxs-lookup"><span data-stu-id="c5b55-179">Whether or not you consider changing the surface of your API, you'll likely find that type annotations alone aren't sufficient for describing `null` values for arguments or return values.</span></span> <span data-ttu-id="c5b55-180">V těchto případech můžete použít atributy pro přehlednější Popis rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="c5b55-180">In those instances, you can apply attributes to more clearly describe an API.</span></span>

## <a name="attributes-extend-type-annotations"></a><span data-ttu-id="c5b55-181">Atributy rozšiřuje anotace typu</span><span class="sxs-lookup"><span data-stu-id="c5b55-181">Attributes extend type annotations</span></span>

<span data-ttu-id="c5b55-182">Bylo přidáno několik atributů pro vyjádření dalších informací o stavu hodnoty null proměnných.</span><span class="sxs-lookup"><span data-stu-id="c5b55-182">Several attributes have been added to express additional information about the null state of variables.</span></span> <span data-ttu-id="c5b55-183">Veškerý kód, který jste napsali předtím, než C# 8 zavádí odkazy s možnou hodnotou null, byl *null oblivious*</span><span class="sxs-lookup"><span data-stu-id="c5b55-183">All code you wrote before C# 8 introduced nullable reference types was *null oblivious*.</span></span> <span data-ttu-id="c5b55-184">To znamená, že jakákoli proměnná typu odkazu může mít hodnotu null, ale kontroly hodnoty null nejsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="c5b55-184">That means any reference type variable may be null, but null checks aren't required.</span></span> <span data-ttu-id="c5b55-185">Jakmile kód bude *mít na paměti hodnotu s možnou hodnotou null*, změní se tato pravidla.</span><span class="sxs-lookup"><span data-stu-id="c5b55-185">Once your code is *nullable aware*, those rules change.</span></span> <span data-ttu-id="c5b55-186">Odkazové typy by nikdy neměly `null` být hodnotou a pro typy odkazů s možnou hodnotou `null` null musí být před zpětným odkazem zkontrolovány.</span><span class="sxs-lookup"><span data-stu-id="c5b55-186">Reference types should never be the `null` value, and nullable reference types must be checked against `null` before being dereferenced.</span></span>

<span data-ttu-id="c5b55-187">Pravidla pro vaše rozhraní API jsou pravděpodobně složitější, jak jste viděli ve scénáři `TryGetValue` rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="c5b55-187">The rules for your APIs are likely more complicated, as you saw with the `TryGetValue` API scenario.</span></span> <span data-ttu-id="c5b55-188">Mnohé z vašich rozhraní API mají složitější pravidla, kdy proměnné můžou nebo nemůžou `null`být.</span><span class="sxs-lookup"><span data-stu-id="c5b55-188">Many of your APIs have more complex rules for when variables can or can't be `null`.</span></span> <span data-ttu-id="c5b55-189">V těchto případech použijete atributy k vyjádření těchto pravidel.</span><span class="sxs-lookup"><span data-stu-id="c5b55-189">In these cases, you'll use attributes to express those rules.</span></span> <span data-ttu-id="c5b55-190">Atributy, které popisují sémantiku vašeho rozhraní API, najdete v článku o [atributech, které mají vliv na analýzu s možnou hodnotou null](./language-reference/attributes/nullable-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="c5b55-190">The attributes that describe the semantics of your API are found in the article on [Attributes that impact nullable analysis](./language-reference/attributes/nullable-analysis.md).</span></span>

## <a name="generic-definitions-and-nullability"></a><span data-ttu-id="c5b55-191">Obecné definice a možnost použití hodnoty null</span><span class="sxs-lookup"><span data-stu-id="c5b55-191">Generic definitions and nullability</span></span>

<span data-ttu-id="c5b55-192">Správně komunikující stav null obecných typů a obecné metody vyžadují zvláštní péči.</span><span class="sxs-lookup"><span data-stu-id="c5b55-192">Correctly communicating the null state of generic types and generic methods requires special care.</span></span> <span data-ttu-id="c5b55-193">To je fakt, že typ hodnoty s možnou hodnotou null a typ odkazu s možnou hodnotou null jsou zásadním rozdílem.</span><span class="sxs-lookup"><span data-stu-id="c5b55-193">This stems from the fact that a nullable value type and a nullable reference type are fundamentally different.</span></span> <span data-ttu-id="c5b55-194">`int?` Je synonymum pro `Nullable<int>`, zatímco `string?` je `string` atributem přidaným kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="c5b55-194">An `int?` is a synonym for `Nullable<int>`, whereas `string?` is `string` with an attribute added by the compiler.</span></span> <span data-ttu-id="c5b55-195">Výsledkem je, že kompilátor nemůže generovat správný `T?` kód bez vědomí, zda `T` je `class` nebo. `struct`</span><span class="sxs-lookup"><span data-stu-id="c5b55-195">The result is that the compiler can't generate correct code for `T?` without knowing if `T` is a `class` or a `struct`.</span></span>

<span data-ttu-id="c5b55-196">To neznamená, že nemůžete použít typ s povolenou hodnotou null (buď typ hodnoty, nebo odkazový typ) jako argument typu pro uzavřený obecný typ.</span><span class="sxs-lookup"><span data-stu-id="c5b55-196">This doesn't mean you can't use a nullable type (either value type or reference type) as the type argument for a closed generic type.</span></span> <span data-ttu-id="c5b55-197">`List<string?>` A `List<int?>` jsou platné instance `List<T>`.</span><span class="sxs-lookup"><span data-stu-id="c5b55-197">Both `List<string?>` and `List<int?>` are valid instantiations of `List<T>`.</span></span>

<span data-ttu-id="c5b55-198">To znamená, že nemůžete použít `T?` v deklaraci obecné třídy nebo metody bez omezení.</span><span class="sxs-lookup"><span data-stu-id="c5b55-198">What it does mean is that you can't use `T?` in a generic class or method declaration without constraints.</span></span> <span data-ttu-id="c5b55-199">Například se nemění, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> aby vracel. `T?`</span><span class="sxs-lookup"><span data-stu-id="c5b55-199">For example, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> won't be changed to return `T?`.</span></span> <span data-ttu-id="c5b55-200">Toto omezení můžete překonat přidáním omezení `struct` nebo. `class`</span><span class="sxs-lookup"><span data-stu-id="c5b55-200">You can overcome this limitation by adding either the `struct` or `class` constraint.</span></span> <span data-ttu-id="c5b55-201">U některého z těchto omezení kompilátor ví, jak generovat kód pro i `T` `T?`.</span><span class="sxs-lookup"><span data-stu-id="c5b55-201">With either of those constraints, the compiler knows how to generate code for both `T` and `T?`.</span></span>

<span data-ttu-id="c5b55-202">Můžete chtít omezit typy používané pro argument obecného typu, aby byly typy bez hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="c5b55-202">You may want to restrict the types used for a generic type argument to be non-nullable types.</span></span> <span data-ttu-id="c5b55-203">To lze provést přidáním `notnull` omezení na tento argument typu.</span><span class="sxs-lookup"><span data-stu-id="c5b55-203">You can do that by adding the `notnull` constraint on that type argument.</span></span> <span data-ttu-id="c5b55-204">Při použití tohoto omezení nesmí argument type být typ s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="c5b55-204">When that constraint is applied, the type argument must not be a nullable type.</span></span>

## <a name="late-initialized-properties-data-transfer-objects-and-nullability"></a><span data-ttu-id="c5b55-205">Opožděné inicializace vlastností, Přenos dat objektů a možnosti použití hodnoty null</span><span class="sxs-lookup"><span data-stu-id="c5b55-205">Late-initialized properties, Data Transfer Objects and nullability</span></span>

<span data-ttu-id="c5b55-206">Vzhledem k tomu, že hodnota null vlastností, které jsou zpožděně inicializovány, což znamená, že je nastavena po konstrukci, může vyžadovat zvláštní pozornost, aby vaše třída nadále správně nevyjádřila původní záměr návrhu.</span><span class="sxs-lookup"><span data-stu-id="c5b55-206">Indicating the nullability of properties that are late-initialized, meaning set after construction, may require special consideration to ensure that your class continues to correctly express the original design intent.</span></span>

<span data-ttu-id="c5b55-207">Typy, které obsahují zpožděné vlastnosti, jako je například Přenos dat objektů (DTO), jsou často vytvořeny pomocí externí knihovny, jako je například ORM databáze (objektová relační Mapovač), deserializátor nebo některá jiná komponenta, která automaticky vyplní vlastnosti z jiného zdroje.</span><span class="sxs-lookup"><span data-stu-id="c5b55-207">Types that contain late-initialized properties, such as Data Transfer Objects (DTOs), are often instantiated by an external library, like a database ORM (Object Relational Mapper), a deserializer, or some other component that automatically populates properties from another source.</span></span>

<span data-ttu-id="c5b55-208">Před povolením typů odkazů s možnou hodnotou null, které představují studenta, zvažte následující třídu DTO:</span><span class="sxs-lookup"><span data-stu-id="c5b55-208">Consider the following DTO class, prior to enabling nullable reference types, that represents a student:</span></span>

```csharp
class Student
{
    [Required]
    public string FirstName { get; set; }

    [Required]
    public string LastName { get; set; }

    public string VehicleRegistration { get; set; }
}
```

<span data-ttu-id="c5b55-209">Záměr návrhu (uvedený v tomto `Required` případě atributem) naznačuje, že v tomto systému jsou vlastnosti `FirstName` a `LastName` **povinné**, a proto není null.</span><span class="sxs-lookup"><span data-stu-id="c5b55-209">The design intent (indicated in this case by the `Required` attribute) suggests that in this system, the `FirstName` and `LastName` properties are **mandatory**, and therefore not null.</span></span>

<span data-ttu-id="c5b55-210">`VehicleRegistration` Vlastnost není **povinná**, takže může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="c5b55-210">The `VehicleRegistration` property is **not mandatory**, so may be null.</span></span>

<span data-ttu-id="c5b55-211">Pokud povolíte typy odkazů s možnou hodnotou null, chcete určit, které vlastnosti mohou být s možnou hodnotou null, v souladu s původním záměrem:</span><span class="sxs-lookup"><span data-stu-id="c5b55-211">When you enable nullable reference types, you want to indicate on our DTO which of the properties may be nullable, consistent with your original intent:</span></span>

```csharp
class Student
{
    [Required]
    public string FirstName { get; set; }

    [Required]
    public string LastName { get; set; }

    public string? VehicleRegistration { get; set; }
}
```

<span data-ttu-id="c5b55-212">Pro tento DTO je ``VehicleRegistration``jedinou vlastností, která může být null.</span><span class="sxs-lookup"><span data-stu-id="c5b55-212">For this DTO, the only property that may be null is ``VehicleRegistration``.</span></span>

<span data-ttu-id="c5b55-213">Kompilátor však vyvolává `CS8618` upozornění pro `FirstName` a `LastName`, což značí, že vlastnosti, které neumožňují hodnotu null, nejsou inicializovány.</span><span class="sxs-lookup"><span data-stu-id="c5b55-213">However, the compiler raises `CS8618` warnings for both `FirstName` and `LastName`, indicating the non-nullable properties are uninitialized.</span></span>

<span data-ttu-id="c5b55-214">Existují tři možnosti, které jsou k dispozici pro vyřešení upozornění kompilátoru způsobem, který zachovává původní záměr.</span><span class="sxs-lookup"><span data-stu-id="c5b55-214">There are three options available to you that resolve the compiler warnings in a way that maintains the original intent.</span></span> <span data-ttu-id="c5b55-215">Kterákoli z těchto možností je platná. měli byste zvolit ten, který nejlépe vyhovuje vašemu stylu kódování a požadavkům na návrh.</span><span class="sxs-lookup"><span data-stu-id="c5b55-215">Any of these options are valid; you should choose the one that best suits your coding style and design requirements.</span></span>

### <a name="initialize-in-the-constructor"></a><span data-ttu-id="c5b55-216">Inicializovat v konstruktoru</span><span class="sxs-lookup"><span data-stu-id="c5b55-216">Initialize in the constructor</span></span>

<span data-ttu-id="c5b55-217">Ideální způsob, jak vyřešit neinicializovaná upozornění, je inicializovat vlastnosti v konstruktoru:</span><span class="sxs-lookup"><span data-stu-id="c5b55-217">The ideal way to resolve the uninitialized warnings is to initialize the properties in the constructor:</span></span>

```csharp
class Student
{
    public Student(string firstName, string lastName)
    {
        FirstName = firstName;
        LastName = lastName;
    }

    [Required]
    public string FirstName { get; set; }

    [Required]
    public string LastName { get; set; }

    public string? VehicleRegistration { get; set; }
}
```

<span data-ttu-id="c5b55-218">Tento přístup funguje pouze v případě, že knihovna, kterou použijete k vytvoření instance třídy, podporuje předávání parametrů v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c5b55-218">This approach only works if the library that you use to instantiate the class supports passing parameters in the constructor.</span></span>

<span data-ttu-id="c5b55-219">Kromě toho knihovna může podporovat předávání *některých* vlastností v konstruktoru, ale ne všechny.</span><span class="sxs-lookup"><span data-stu-id="c5b55-219">In addition, a library may support passing *some* properties in the constructor, but not all.</span></span>
<span data-ttu-id="c5b55-220">Například EF Core podporuje [vazbu konstruktoru](/ef/core/modeling/constructors) pro normální vlastnosti sloupce, ale ne navigační vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c5b55-220">For example, EF Core supports [constructor binding](/ef/core/modeling/constructors) for normal column properties, but not navigation properties.</span></span>

<span data-ttu-id="c5b55-221">Podívejte se na dokumentaci knihovny, která vytváří instanci vaší třídy, abyste pochopili rozsah, ve kterém podporuje vazby konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c5b55-221">Check the documentation on the library that instantiates your class, to understand the extent to which it supports constructor binding.</span></span>

### <a name="property-with-nullable-backing-field"></a><span data-ttu-id="c5b55-222">Vlastnost s polem, které je k hodnotou null</span><span class="sxs-lookup"><span data-stu-id="c5b55-222">Property with nullable backing field</span></span>

<span data-ttu-id="c5b55-223">Pokud vazba konstruktoru nebude pro vás fungovat, jedním ze způsobů, jak se tomuto problému vypořádat, je mít vlastnost nepovolující hodnotu null s polem, které je k dispozici s možnou hodnotou null:</span><span class="sxs-lookup"><span data-stu-id="c5b55-223">If constructor binding won't work for you, one way to deal with this problem is to have a non-nullable property with a nullable backing field:</span></span>

```csharp
private string? _firstName;

[Required]
public string FirstName
{
    set => _firstName = value;
    get => _firstName
           ?? throw new InvalidOperationException("Uninitialized " + nameof(FirstName))
}
```

<span data-ttu-id="c5b55-224">V tomto scénáři, pokud je `FirstName` vlastnost k dispozici před inicializací, kód vyvolá výjimku `InvalidOperationException`, protože kontrakt rozhraní API byl nesprávně použit.</span><span class="sxs-lookup"><span data-stu-id="c5b55-224">In this scenario, if the `FirstName` property is accessed before it has been initialized, then the code throws an `InvalidOperationException`, because the API contract has been used incorrectly.</span></span>

<span data-ttu-id="c5b55-225">Při použití zálohovaných polí byste měli zvážit, že některé knihovny můžou mít zvláštní předpoklady.</span><span class="sxs-lookup"><span data-stu-id="c5b55-225">You should consider that some libraries may have special considerations when using backing fields.</span></span> <span data-ttu-id="c5b55-226">EF Core například může být nutné nakonfigurovat pro správné použití polí pro [zálohování](/ef/core/modeling/backing-field) .</span><span class="sxs-lookup"><span data-stu-id="c5b55-226">For example, EF Core may need to be configured to use [backing fields](/ef/core/modeling/backing-field) correctly.</span></span>

### <a name="initialize-the-property-to-null"></a><span data-ttu-id="c5b55-227">Inicializovat vlastnost na hodnotu null</span><span class="sxs-lookup"><span data-stu-id="c5b55-227">Initialize the property to null</span></span>

<span data-ttu-id="c5b55-228">Jako terser alternativa k použití pole, které je null, nebo v případě, že knihovna, která vytváří instanci vaší třídy, není kompatibilní s tímto přístupem, můžete jednoduše inicializovat `null` vlastnost přímo s použitím operátoru null-striktní (`!`):</span><span class="sxs-lookup"><span data-stu-id="c5b55-228">As a terser alternative to using a nullable backing field, or if the library that instantiates your class is not compatible with that approach, you can simply initialize the property to `null` directly, with the help of the null-forgiving operator (`!`):</span></span>

```csharp
[Required]
public string FirstName { get; set; } = null!;

[Required]
public string LastName { get; set; } = null!;

public string? VehicleRegistration { get; set; }
```

<span data-ttu-id="c5b55-229">Nebudete nikdy sledovat skutečnou hodnotu null za běhu s výjimkou důsledků programátorské chyby, a to tak, že přístup k vlastnosti před jejich správnou inicializací.</span><span class="sxs-lookup"><span data-stu-id="c5b55-229">You will never observe an actual null value at runtime except as a result of a programming bug, by accessing the property before it has been properly initialized.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5b55-230">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5b55-230">See also</span></span>

- [<span data-ttu-id="c5b55-231">Migrace existujícího základu kódu na odkazy s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="c5b55-231">Migrate an existing codebase to nullable references</span></span>](tutorials/upgrade-to-nullable-references.md)
- [<span data-ttu-id="c5b55-232">Práce s typy odkazů s možnou hodnotou null v EF Core</span><span class="sxs-lookup"><span data-stu-id="c5b55-232">Working with Nullable Reference Types in EF Core</span></span>](/ef/core/miscellaneous/nullable-reference-types)
