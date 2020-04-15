---
title: 'C# Vyhrazené atributy: Statická analýza s možnou hodnotou Null'
ms.date: 04/14/2020
description: Tyto atributy jsou interpretovány kompilátorem poskytnout lepší statickou analýzu pro nullable a nenulelné typy odkazů.
ms.openlocfilehash: 0315d78db7517541efe578d8675c0f2fe45f5aea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389861"
---
# <a name="reserved-attributes-contribute-to-the-compilers-null-state-static-analysis"></a><span data-ttu-id="5dac4-103">Vyhrazené atributy přispívají ke statické analýze nulového stavu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="5dac4-103">Reserved attributes contribute to the compiler's null state static analysis</span></span>

<span data-ttu-id="5dac4-104">V kontextu s možnou hodnotou null kompilátor provádí statickou analýzu kódu k určení stavu null všech proměnných typu odkazu:</span><span class="sxs-lookup"><span data-stu-id="5dac4-104">In a nullable context, the compiler performs static analysis of code to determine the null state of all reference type variables:</span></span>

- <span data-ttu-id="5dac4-105">*not null*: Statická analýza zjistila, že proměnná je přiřazena k nenulové hodnotě.</span><span class="sxs-lookup"><span data-stu-id="5dac4-105">*not null*: Static analysis determined that the variable is assigned to a non-null value.</span></span>
- <span data-ttu-id="5dac4-106">*možná null*: Statická analýza nemůže určit, že proměnné je přiřazena hodnota bez hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-106">*maybe null*: Static analysis cannot determine that a variable is assigned a non-null value.</span></span>

<span data-ttu-id="5dac4-107">Můžete použít několik atributů, které poskytují informace kompilátoru o sémantiku vašich api.</span><span class="sxs-lookup"><span data-stu-id="5dac4-107">You can apply a number of attributes that provide information to the compiler about the semantics of your APIs.</span></span> <span data-ttu-id="5dac4-108">Tyto informace pomáhají kompilátoru provádět statickou analýzu a určit, kdy proměnná není null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-108">That information helps the compiler perform static analysis and determine when a variable is not null.</span></span> <span data-ttu-id="5dac4-109">Tento článek obsahuje stručný popis každého z těchto atributů a jak je používat.</span><span class="sxs-lookup"><span data-stu-id="5dac4-109">This article provides a brief description of each of those attributes and how to use them.</span></span> <span data-ttu-id="5dac4-110">Všechny příklady předpokládají C# 8.0 nebo novější a kód je v kontextu s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-110">All the examples assume C# 8.0 or newer, and the code is in a nullable context.</span></span>

<span data-ttu-id="5dac4-111">Začněme se známým příkladem.</span><span class="sxs-lookup"><span data-stu-id="5dac4-111">Let's start with a familiar example.</span></span> <span data-ttu-id="5dac4-112">Představte si, že vaše knihovna má následující rozhraní API pro načtení řetězce prostředků:</span><span class="sxs-lookup"><span data-stu-id="5dac4-112">Imagine your library has the following API to retrieve a resource string:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="5dac4-113">Předchozí příklad následuje známý `Try*` vzor v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="5dac4-113">The preceding example follows the familiar `Try*` pattern in .NET.</span></span> <span data-ttu-id="5dac4-114">Existují dva referenční argumenty pro `key` toto `message` rozhraní API: a parametr.</span><span class="sxs-lookup"><span data-stu-id="5dac4-114">There are two reference arguments for this API: the `key` and the `message` parameter.</span></span> <span data-ttu-id="5dac4-115">Toto rozhraní API má následující pravidla týkající se nullness těchto argumentů:</span><span class="sxs-lookup"><span data-stu-id="5dac4-115">This API has the following rules relating to the nullness of these arguments:</span></span>

- <span data-ttu-id="5dac4-116">Volající by neměli `null` projít jako `key`argument pro .</span><span class="sxs-lookup"><span data-stu-id="5dac4-116">Callers shouldn't pass `null` as the argument for `key`.</span></span>
- <span data-ttu-id="5dac4-117">Volající mohou předat proměnnou, `null` jejíž `message`hodnota je jako argument pro .</span><span class="sxs-lookup"><span data-stu-id="5dac4-117">Callers can pass a variable whose value is `null` as the argument for `message`.</span></span>
- <span data-ttu-id="5dac4-118">Pokud `TryGetMessage` metoda `true`vrátí , `message` hodnota není null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-118">If the `TryGetMessage` method returns `true`, the value of `message` isn't null.</span></span> <span data-ttu-id="5dac4-119">Pokud je `false,` vrácená hodnota `message` hodnota (a její stav null) je null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-119">If the return value is `false,` the value of `message` (and its null state) is null.</span></span>

<span data-ttu-id="5dac4-120">Pravidlo pro `key` může být vyjádřeno typem proměnné: `key` by měl být typ odkazu s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-120">The rule for `key` can be expressed by the variable type: `key` should be a non-nullable reference type.</span></span> <span data-ttu-id="5dac4-121">Parametr `message` je složitější.</span><span class="sxs-lookup"><span data-stu-id="5dac4-121">The `message` parameter is more complex.</span></span> <span data-ttu-id="5dac4-122">Umožňuje `null` jako argument, ale zaručuje, že na `out` úspěch, že argument není null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-122">It allows `null` as the argument, but guarantees that, on success, that `out` argument isn't null.</span></span> <span data-ttu-id="5dac4-123">Pro tyto scénáře potřebujete bohatší slovní zásobu k popisu očekávání.</span><span class="sxs-lookup"><span data-stu-id="5dac4-123">For these scenarios, you need a richer vocabulary to describe the expectations.</span></span>

<span data-ttu-id="5dac4-124">Několik atributů byly přidány vyjádřit další informace o stavu null proměnných.</span><span class="sxs-lookup"><span data-stu-id="5dac4-124">Several attributes have been added to express additional information about the null state of variables.</span></span> <span data-ttu-id="5dac4-125">Veškerý kód, který jste napsali před c# 8 představil null reference typy byl *null nevšímavý*.</span><span class="sxs-lookup"><span data-stu-id="5dac4-125">All code you wrote before C# 8 introduced nullable reference types was *null oblivious*.</span></span> <span data-ttu-id="5dac4-126">To znamená, že všechny proměnné typu odkazu může být null, ale null kontroly nejsou vyžadovány.</span><span class="sxs-lookup"><span data-stu-id="5dac4-126">That means any reference type variable may be null, but null checks aren't required.</span></span> <span data-ttu-id="5dac4-127">Jakmile váš kód je *null,,,* tato pravidla změnit.</span><span class="sxs-lookup"><span data-stu-id="5dac4-127">Once your code is *nullable aware*, those rules change.</span></span> <span data-ttu-id="5dac4-128">Referenční typy by `null` nikdy měla být hodnota a nullable `null` typy odkazů musí být zkontrolovány proti před tím, než je odkazováno.</span><span class="sxs-lookup"><span data-stu-id="5dac4-128">Reference types should never be the `null` value, and nullable reference types must be checked against `null` before being dereferenced.</span></span>

<span data-ttu-id="5dac4-129">Pravidla pro vaše rozhraní API jsou pravděpodobně složitější, `TryGetValue` jak jste viděli u scénáře rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="5dac4-129">The rules for your APIs are likely more complicated, as you saw with the `TryGetValue` API scenario.</span></span> <span data-ttu-id="5dac4-130">Mnoho vašich api mají složitější pravidla pro proměnné může `null`nebo nemůže být .</span><span class="sxs-lookup"><span data-stu-id="5dac4-130">Many of your APIs have more complex rules for when variables can or can't be `null`.</span></span> <span data-ttu-id="5dac4-131">V těchto případech použijete k vyjádření těchto pravidel jeden z následujících atributů:</span><span class="sxs-lookup"><span data-stu-id="5dac4-131">In these cases, you'll use one of the following attributes to express those rules:</span></span>

- <span data-ttu-id="5dac4-132">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Vstupní argument, který nelze upustit, může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-132">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="5dac4-133">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Vstupní argument s možnou hodnotou null by nikdy neměl mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-133">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>
- <span data-ttu-id="5dac4-134">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Vrácená hodnota, jejíž nenulovatelná hodnota může být null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-134">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="5dac4-135">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Vrácená hodnota s možnou hodnotou null nikdy nebude null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-135">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>
- <span data-ttu-id="5dac4-136">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Vstupní argument, který nelze utnou, `bool` může mít hodnotu null, pokud metoda vrátí zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5dac4-136">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="5dac4-137">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Vstupní argument s možnou hodnotou null `bool` nebude null, pokud metoda vrátí zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5dac4-137">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="5dac4-138">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Vrácená hodnota není null, pokud argument pro zadaný parametr není null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-138">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the argument for the specified parameter isn't null.</span></span>
- <span data-ttu-id="5dac4-139">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): Metoda nikdy vrátí.</span><span class="sxs-lookup"><span data-stu-id="5dac4-139">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): A method never returns.</span></span> <span data-ttu-id="5dac4-140">Jinými slovy vždy vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="5dac4-140">In other words, it always throws an exception.</span></span>
- <span data-ttu-id="5dac4-141">[DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): Tato metoda nikdy `bool` vrátí, pokud přidružený parametr má zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5dac4-141">[DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): This method never returns if the associated `bool` parameter has the specified value.</span></span>

<span data-ttu-id="5dac4-142">Předchozí popisy jsou stručný odkaz na to, co každý atribut dělá.</span><span class="sxs-lookup"><span data-stu-id="5dac4-142">The preceding descriptions are a quick reference to what each attribute does.</span></span> <span data-ttu-id="5dac4-143">Každá následující část popisuje chování a význam důkladněji.</span><span class="sxs-lookup"><span data-stu-id="5dac4-143">Each following section describes the behavior and meaning more thoroughly.</span></span>

<span data-ttu-id="5dac4-144">Přidání těchto atributů poskytuje kompilátoru další informace o pravidlech pro rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="5dac4-144">Adding these attributes gives the compiler more information about the rules for your API.</span></span> <span data-ttu-id="5dac4-145">Při volání kódu je kompilován v kontextu s povoleným hodnotou null, kompilátor bude varovat volající, když porušují tato pravidla.</span><span class="sxs-lookup"><span data-stu-id="5dac4-145">When calling code is compiled in a nullable enabled context, the compiler will warn callers when they violate those rules.</span></span> <span data-ttu-id="5dac4-146">Tyto atributy neumožňují další kontroly implementace.</span><span class="sxs-lookup"><span data-stu-id="5dac4-146">These attributes don't enable additional checks on your implementation.</span></span>

## <a name="specify-preconditions-allownull-and-disallownull"></a><span data-ttu-id="5dac4-147">Určete předběžné `AllowNull` podmínky: a`DisallowNull`</span><span class="sxs-lookup"><span data-stu-id="5dac4-147">Specify preconditions: `AllowNull` and `DisallowNull`</span></span>

<span data-ttu-id="5dac4-148">Zvažte vlastnost pro čtení `null` a zápis, která se nikdy nevrátí, protože má přiměřenou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5dac4-148">Consider a read/write property that never returns `null` because it has a reasonable default value.</span></span> <span data-ttu-id="5dac4-149">Volající předat `null` nastavit přistupujícího pole při jeho nastavení na tuto výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5dac4-149">Callers pass `null` to the set accessor when setting it to that default value.</span></span> <span data-ttu-id="5dac4-150">Zvažte například systém zasílání zpráv, který požádá o název obrazovky v chatovací místnosti.</span><span class="sxs-lookup"><span data-stu-id="5dac4-150">For example, consider a messaging system that asks for a screen name in a chat room.</span></span> <span data-ttu-id="5dac4-151">Pokud není k dispozici žádný, systém generuje náhodný název:</span><span class="sxs-lookup"><span data-stu-id="5dac4-151">If none is provided, the system generates a random name:</span></span>

```csharp
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName;
```

<span data-ttu-id="5dac4-152">Při kompilaci předchozíkód v nečitelný kontext, vše je v pořádku.</span><span class="sxs-lookup"><span data-stu-id="5dac4-152">When you compile the preceding code in a nullable oblivious context, everything is fine.</span></span> <span data-ttu-id="5dac4-153">Jakmile povolíte typy odkazů `ScreenName` s možnou hodnotou null, vlastnost se stane nenulelným odkazem.</span><span class="sxs-lookup"><span data-stu-id="5dac4-153">Once you enable nullable reference types, the `ScreenName` property becomes a non-nullable reference.</span></span> <span data-ttu-id="5dac4-154">To je správné `get` pro přistupující `null`ho: nikdy se vrátí .</span><span class="sxs-lookup"><span data-stu-id="5dac4-154">That's correct for the `get` accessor: it never returns `null`.</span></span> <span data-ttu-id="5dac4-155">Volající nemusí kontrolovat vrácenou vlastnost pro `null`.</span><span class="sxs-lookup"><span data-stu-id="5dac4-155">Callers don't need to check the returned property for `null`.</span></span> <span data-ttu-id="5dac4-156">Ale nyní nastavení `null` vlastnosti generuje upozornění.</span><span class="sxs-lookup"><span data-stu-id="5dac4-156">But now setting the property to `null` generates a warning.</span></span> <span data-ttu-id="5dac4-157">Chcete-li i nadále podporovat tento typ <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> kódu, přidejte atribut do vlastnosti, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="5dac4-157">In order to continue to support this type of code, you add the <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> attribute to the property, as shown in the following code:</span></span>

```csharp
[AllowNull]
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName = GenerateRandomScreenName();
```

<span data-ttu-id="5dac4-158">Možná budete muset `using` přidat <xref:System.Diagnostics.CodeAnalysis> direktivu pro použití tohoto a dalších atributů popsaných v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="5dac4-158">You may need to add a `using` directive for <xref:System.Diagnostics.CodeAnalysis> to use this and other attributes discussed in this article.</span></span> <span data-ttu-id="5dac4-159">Atribut je použit a vlastnost, `set` nikoli přistupující objekt.</span><span class="sxs-lookup"><span data-stu-id="5dac4-159">The attribute is applied to the property, not the `set` accessor.</span></span> <span data-ttu-id="5dac4-160">Atribut `AllowNull` určuje *předběžné podmínky*a vztahuje se pouze na vstupy.</span><span class="sxs-lookup"><span data-stu-id="5dac4-160">The `AllowNull` attribute specifies *pre-conditions*, and only applies to inputs.</span></span> <span data-ttu-id="5dac4-161">Přistupující `get` odkaz má vrácenou hodnotu, ale žádné vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="5dac4-161">The `get` accessor has a return value, but no input arguments.</span></span> <span data-ttu-id="5dac4-162">Proto `AllowNull` atribut platí pouze pro `set` přistupujícího pole.</span><span class="sxs-lookup"><span data-stu-id="5dac4-162">Therefore, the `AllowNull` attribute only applies to the `set` accessor.</span></span>

<span data-ttu-id="5dac4-163">Předchozí příklad ukazuje, co hledat při `AllowNull` přidávání atributu na argument:</span><span class="sxs-lookup"><span data-stu-id="5dac4-163">The preceding example demonstrates what to look for when adding the `AllowNull` attribute on an argument:</span></span>

1. <span data-ttu-id="5dac4-164">Obecná smlouva pro tuto proměnnou je, `null`že by neměla být , takže chcete typ odkazu s nemožnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-164">The general contract for that variable is that it shouldn't be `null`, so you want a non-nullable reference type.</span></span>
1. <span data-ttu-id="5dac4-165">Existují scénáře pro vstupní proměnné `null`, i když nejsou nejběžnější použití.</span><span class="sxs-lookup"><span data-stu-id="5dac4-165">There are scenarios for the input variable to be `null`, though they aren't the most common usage.</span></span>

<span data-ttu-id="5dac4-166">Nejčastěji budete potřebovat tento atribut pro `in` `out`vlastnosti `ref` , nebo , a argumenty.</span><span class="sxs-lookup"><span data-stu-id="5dac4-166">Most often you'll need this attribute for properties, or `in`, `out`, and `ref` arguments.</span></span> <span data-ttu-id="5dac4-167">Atribut `AllowNull` je nejlepší volbou, pokud je proměnná obvykle non-null, ale je třeba povolit `null` jako předběžnou podmínku.</span><span class="sxs-lookup"><span data-stu-id="5dac4-167">The `AllowNull` attribute is the best choice when a variable is typically non-null, but you need to allow `null` as a precondition.</span></span>

<span data-ttu-id="5dac4-168">Kontrast, který se `DisallowNull`scénáře pro použití : Tento atribut slouží k určení, že `null`vstupní proměnná typu odkazu s možnou hodnotou null by neměla být .</span><span class="sxs-lookup"><span data-stu-id="5dac4-168">Contrast that with scenarios for using `DisallowNull`: You use this attribute to specify that an input variable of a nullable reference type shouldn't be `null`.</span></span> <span data-ttu-id="5dac4-169">Zvažte vlastnost, kde `null` je výchozí hodnota, ale klienti ji mohou nastavit pouze na hodnotu, která není null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-169">Consider a property where `null` is the default value, but clients can only set it to a non-null value.</span></span> <span data-ttu-id="5dac4-170">Uvažujte následující kód:</span><span class="sxs-lookup"><span data-stu-id="5dac4-170">Consider the following code:</span></span>

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

<span data-ttu-id="5dac4-171">Předchozí kód je nejlepší způsob, jak vyjádřit `ReviewComment` svůj `null`návrh, který by `null`mohl být , ale nelze nastavit na .</span><span class="sxs-lookup"><span data-stu-id="5dac4-171">The preceding code is the best way to express your design that the `ReviewComment` could be `null`, but can't be set to `null`.</span></span> <span data-ttu-id="5dac4-172">Jakmile je tento kód nullable vědomi, můžete vyjádřit tento <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>koncept jasněji volajícím pomocí :</span><span class="sxs-lookup"><span data-stu-id="5dac4-172">Once this code is nullable aware, you can express this concept more clearly to callers using the <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>:</span></span>

```csharp
[DisallowNull]
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

<span data-ttu-id="5dac4-173">V kontextu s možnou hodnotou `ReviewComment` `get` null může `null`přistupující odkaz vrátit výchozí hodnotu aplikace .</span><span class="sxs-lookup"><span data-stu-id="5dac4-173">In a nullable context, the `ReviewComment` `get` accessor could return the default value of `null`.</span></span> <span data-ttu-id="5dac4-174">Kompilátor varuje, že musí být kontrolovány před přístupem.</span><span class="sxs-lookup"><span data-stu-id="5dac4-174">The compiler warns that it must be checked before access.</span></span> <span data-ttu-id="5dac4-175">Kromě toho varuje volající, že i když `null`by to mohlo být , `null`volající by nemělexplicitně nastavit na .</span><span class="sxs-lookup"><span data-stu-id="5dac4-175">Furthermore, it warns callers that, even though it could be `null`, callers shouldn't explicitly set it to `null`.</span></span> <span data-ttu-id="5dac4-176">Atribut `DisallowNull` také určuje *předběžnou podmínku*, nemá `get` vliv na přistupující ho.</span><span class="sxs-lookup"><span data-stu-id="5dac4-176">The `DisallowNull` attribute also specifies a *pre-condition*, it does not affect the `get` accessor.</span></span> <span data-ttu-id="5dac4-177">Atribut se `DisallowNull` používá, když sledujete tyto charakteristiky o:</span><span class="sxs-lookup"><span data-stu-id="5dac4-177">You use the `DisallowNull` attribute when you observe these characteristics about:</span></span>

1. <span data-ttu-id="5dac4-178">Proměnná může `null` být v základních scénářích, často při první instanci.</span><span class="sxs-lookup"><span data-stu-id="5dac4-178">The variable could be `null` in core scenarios, often when first instantiated.</span></span>
1. <span data-ttu-id="5dac4-179">Proměnná by neměla být `null`explicitně nastavena na .</span><span class="sxs-lookup"><span data-stu-id="5dac4-179">The variable shouldn't be explicitly set to `null`.</span></span>

<span data-ttu-id="5dac4-180">Tyto situace jsou běžné v kódu, který byl původně *null nevšímavý*.</span><span class="sxs-lookup"><span data-stu-id="5dac4-180">These situations are common in code that was originally *null oblivious*.</span></span> <span data-ttu-id="5dac4-181">Je možné, že vlastnosti objektu jsou nastaveny ve dvou odlišných inicializačních operacích.</span><span class="sxs-lookup"><span data-stu-id="5dac4-181">It may be that object properties are set in two distinct initialization operations.</span></span> <span data-ttu-id="5dac4-182">Je možné, že některé vlastnosti jsou nastaveny pouze po dokončení některé asynchronní práce.</span><span class="sxs-lookup"><span data-stu-id="5dac4-182">It may be that some properties are set only after some asynchronous work has completed.</span></span>

<span data-ttu-id="5dac4-183">`AllowNull` Atributy `DisallowNull` a umožňují určit, že předběžné podmínky na proměnné nemusí odpovídat poznámky s hodnotou null na tyto proměnné.</span><span class="sxs-lookup"><span data-stu-id="5dac4-183">The `AllowNull` and `DisallowNull` attributes enable you to specify that preconditions on variables may not match the nullable annotations on those variables.</span></span> <span data-ttu-id="5dac4-184">Tyto poskytují další podrobnosti o charakteristikách rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="5dac4-184">These provide more detail about the characteristics of your API.</span></span> <span data-ttu-id="5dac4-185">Tyto další informace pomáhají volajícím správně používat vaše rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="5dac4-185">This additional information helps callers use your API correctly.</span></span> <span data-ttu-id="5dac4-186">Nezapomeňte zadat předběžné podmínky pomocí následujících atributů:</span><span class="sxs-lookup"><span data-stu-id="5dac4-186">Remember you specify preconditions using the following attributes:</span></span>

- <span data-ttu-id="5dac4-187">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Vstupní argument, který nelze upustit, může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-187">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="5dac4-188">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Vstupní argument s možnou hodnotou null by nikdy neměl mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-188">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>

## <a name="specify-post-conditions-maybenull-and-notnull"></a><span data-ttu-id="5dac4-189">Uveďte post-podmínky: `MaybeNull` a`NotNull`</span><span class="sxs-lookup"><span data-stu-id="5dac4-189">Specify post-conditions: `MaybeNull` and `NotNull`</span></span>

<span data-ttu-id="5dac4-190">Předpokládejme, že máte metodu s následujícím podpisem:</span><span class="sxs-lookup"><span data-stu-id="5dac4-190">Suppose you have a method with the following signature:</span></span>

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

<span data-ttu-id="5dac4-191">Pravděpodobně jste napsali metodu, `null` jako je tato, abyste se vrátili, když se nenašel hledaný název.</span><span class="sxs-lookup"><span data-stu-id="5dac4-191">You've likely written a method like this to return `null` when the name sought wasn't found.</span></span> <span data-ttu-id="5dac4-192">Jasně `null` ukazuje, že záznam nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="5dac4-192">The `null` clearly indicates that the record wasn't found.</span></span> <span data-ttu-id="5dac4-193">V tomto příkladu byste pravděpodobně změnit `Customer` návratový typ z na `Customer?`.</span><span class="sxs-lookup"><span data-stu-id="5dac4-193">In this example, you'd likely change the return type from `Customer` to `Customer?`.</span></span> <span data-ttu-id="5dac4-194">Deklarování vrácené hodnoty jako typu odkazu s možnou hodnotou null jasně určuje záměr tohoto rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="5dac4-194">Declaring the return value as a nullable reference type specifies the intent of this API clearly.</span></span>

<span data-ttu-id="5dac4-195">Z důvodů uvedených v [obecných definicích a nullability](../../nullable-attributes.md#generic-definitions-and-nullability) tato technika nefunguje s obecnými metodami.</span><span class="sxs-lookup"><span data-stu-id="5dac4-195">For reasons covered under [Generic definitions and nullability](../../nullable-attributes.md#generic-definitions-and-nullability) that technique does not work with generic methods.</span></span> <span data-ttu-id="5dac4-196">Můžete mít obecnou metodu, která následuje podobný vzor:</span><span class="sxs-lookup"><span data-stu-id="5dac4-196">You may have a generic method that follows a similar pattern:</span></span>

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

<span data-ttu-id="5dac4-197">Nelze určit, že vrácená `T?`hodnota je .</span><span class="sxs-lookup"><span data-stu-id="5dac4-197">You can't specify that the return value is `T?`.</span></span> <span data-ttu-id="5dac4-198">Metoda vrátí, `null` když není nalezena požadovaná položka.</span><span class="sxs-lookup"><span data-stu-id="5dac4-198">The method returns `null` when the sought item isn't found.</span></span> <span data-ttu-id="5dac4-199">Vzhledem k tomu, `T?` že nelze deklarovat návratový typ, přidáte poznámku `MaybeNull` k metodě return:</span><span class="sxs-lookup"><span data-stu-id="5dac4-199">Since you can't declare a `T?` return type, you add the `MaybeNull` annotation to the method return:</span></span>

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

<span data-ttu-id="5dac4-200">Předchozí kód informuje volající, že smlouva znamená typ s nulou, ale vrácená hodnota *může* být ve skutečnosti null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-200">The preceding code informs callers that the contract implies a non-nullable type, but the return value *may* actually be null.</span></span>  <span data-ttu-id="5dac4-201">Použijte `MaybeNull` atribut, pokud by vaše rozhraní API mělo být typu s nulovým hodnotou, `null` obvykle parametr obecného typu, ale mohou existovat instance, kde by měl být vrácen.</span><span class="sxs-lookup"><span data-stu-id="5dac4-201">Use the `MaybeNull` attribute when your API should be a non-nullable type, typically a generic type parameter, but there may be instances where `null` would be returned.</span></span>

<span data-ttu-id="5dac4-202">Můžete také určit, že vrácená hodnota nebo `out` nebo `ref` argument není null, i když typ je typ odkazu s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-202">You can also specify that a return value or an `out` or `ref` argument isn't null even though the type is a nullable reference type.</span></span> <span data-ttu-id="5dac4-203">Zvažte metodu, která zajišťuje, že pole je dostatečně velké pro uložení několika prvků.</span><span class="sxs-lookup"><span data-stu-id="5dac4-203">Consider a method that ensures an array is large enough to hold a number of elements.</span></span> <span data-ttu-id="5dac4-204">Pokud vstupní argument nemá kapacitu, rutina by přidělit nové pole a zkopírovat všechny existující prvky do něj.</span><span class="sxs-lookup"><span data-stu-id="5dac4-204">If the input argument doesn't have capacity, the routine would allocate a new array and copy all the existing elements into it.</span></span> <span data-ttu-id="5dac4-205">Pokud je `null`vstupní argument , rutina by přidělit nové úložiště.</span><span class="sxs-lookup"><span data-stu-id="5dac4-205">If the input argument is `null`, the routine would allocate new storage.</span></span> <span data-ttu-id="5dac4-206">Pokud je dostatečná kapacita, rutina nedělá nic:</span><span class="sxs-lookup"><span data-stu-id="5dac4-206">If there's sufficient capacity, the routine does nothing:</span></span>

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

<span data-ttu-id="5dac4-207">Dalo by se volat tuto rutinu takto:</span><span class="sxs-lookup"><span data-stu-id="5dac4-207">You could call this routine as follows:</span></span>

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

<span data-ttu-id="5dac4-208">Po povolení typů odkazů null, chcete zajistit, že předchozí kód zkompiluje bez upozornění.</span><span class="sxs-lookup"><span data-stu-id="5dac4-208">After enabling null reference types, you want to ensure that the preceding code compiles without warnings.</span></span> <span data-ttu-id="5dac4-209">Když metoda vrátí, `storage` argument je zaručeno, že není null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-209">When the method returns, the `storage` argument is guaranteed to be not null.</span></span> <span data-ttu-id="5dac4-210">Je však přijatelné volat `EnsureCapacity` s nulovým odkazem.</span><span class="sxs-lookup"><span data-stu-id="5dac4-210">However, it's acceptable to call `EnsureCapacity` with a null reference.</span></span> <span data-ttu-id="5dac4-211">Můžete vytvořit `storage` typ odkazu s možnou `NotNull` hodnotou null a přidat do deklarace parametru podmínku post-condition:</span><span class="sxs-lookup"><span data-stu-id="5dac4-211">You can make `storage` a nullable reference type, and add the `NotNull` post-condition to the parameter declaration:</span></span>

```csharp
public void EnsureCapacity<T>([NotNull]ref T[]? storage, int size)
```

<span data-ttu-id="5dac4-212">Předchozí kód vyjadřuje existující smlouvy jasně: Volající můžete předat `null` proměnnou s hodnotou, ale vrácená hodnota je zaručeno, že nikdy být null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-212">The preceding code expresses the existing contract clearly: Callers can pass a variable with the `null` value, but the return value is guaranteed to never be null.</span></span> <span data-ttu-id="5dac4-213">Atribut `NotNull` je nejužitečnější pro `ref` a `out` argumenty, kde `null` mohou být předány jako argument, ale tento argument je zaručeno, že není null, když metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="5dac4-213">The `NotNull` attribute is most useful for `ref` and `out` arguments where `null` may be passed as an argument, but that argument is guaranteed to be not null when the method returns.</span></span>

<span data-ttu-id="5dac4-214">Můžete zadat bezpodmínečné postconditions pomocí následujících atributů:</span><span class="sxs-lookup"><span data-stu-id="5dac4-214">You specify unconditional postconditions using the following attributes:</span></span>

- <span data-ttu-id="5dac4-215">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Vrácená hodnota, jejíž nenulovatelná hodnota může být null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-215">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="5dac4-216">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Vrácená hodnota s možnou hodnotou null nikdy nebude null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-216">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a><span data-ttu-id="5dac4-217">Určete podmíněné `NotNullWhen`post-podmínky: , `MaybeNullWhen`a`NotNullIfNotNull`</span><span class="sxs-lookup"><span data-stu-id="5dac4-217">Specify conditional post-conditions: `NotNullWhen`, `MaybeNullWhen`, and `NotNullIfNotNull`</span></span>

<span data-ttu-id="5dac4-218">Pravděpodobně jste obeznámeni `string` s <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>metodou .</span><span class="sxs-lookup"><span data-stu-id="5dac4-218">You're likely familiar with the `string` method <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>.</span></span> <span data-ttu-id="5dac4-219">Tato metoda `true` vrátí, pokud je argument null nebo prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="5dac4-219">This method returns `true` when the argument is null or an empty string.</span></span> <span data-ttu-id="5dac4-220">Je to forma null-check: Volající nemusí null-zkontrolovat argument, pokud metoda `false`vrátí .</span><span class="sxs-lookup"><span data-stu-id="5dac4-220">It's a form of null-check: Callers don't need to null-check the argument if the method returns `false`.</span></span> <span data-ttu-id="5dac4-221">Chcete-li metodu, jako je tato nullable aware, byste nastavit argument `NotNullWhen` na typ odkazu s hodnotou null a přidat atribut:</span><span class="sxs-lookup"><span data-stu-id="5dac4-221">To make a method like this nullable aware, you'd set the argument to a nullable reference type, and add the `NotNullWhen` attribute:</span></span>

```csharp
bool IsNullOrEmpty([NotNullWhen(false)]string? value);
```

<span data-ttu-id="5dac4-222">To informuje kompilátor, že žádný kód, kde je `false` vrácená hodnota nemusí být null-kontrolovány.</span><span class="sxs-lookup"><span data-stu-id="5dac4-222">That informs the compiler that any code where the return value is `false` need not be null-checked.</span></span> <span data-ttu-id="5dac4-223">Přidání atributu informuje statické analýzy kompilátoru, který `IsNullOrEmpty` provádí potřebnou `false`kontrolu null: `null`když vrátí , vstupní argument není .</span><span class="sxs-lookup"><span data-stu-id="5dac4-223">The addition of the attribute informs the compiler's static analysis that `IsNullOrEmpty` performs the necessary null check: when it returns `false`, the input argument is not `null`.</span></span>

```csharp
string? userInput = GetUserInput();
if (!string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

<span data-ttu-id="5dac4-224">Metoda <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> bude uvedena v notaci, jak je uvedeno výše pro .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="5dac4-224">The <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> method will be annotated as shown above for .NET Core 3.0.</span></span> <span data-ttu-id="5dac4-225">Můžete mít podobné metody v základu kódu, které kontrolují stav objektů pro nulové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5dac4-225">You may have similar methods in your codebase that check the state of objects for null values.</span></span> <span data-ttu-id="5dac4-226">Kompilátor nerozpozná vlastní metody kontroly null a poznámky budete muset přidat sami.</span><span class="sxs-lookup"><span data-stu-id="5dac4-226">The compiler won't recognize custom null check methods, and you'll need to add the annotations yourself.</span></span> <span data-ttu-id="5dac4-227">Když přidáte atribut, statická analýza kompilátoru ví, kdy byla ověřená proměnná zkontrolována.</span><span class="sxs-lookup"><span data-stu-id="5dac4-227">When you add the attribute, the compiler's static analysis knows when the tested variable has been null checked.</span></span>

<span data-ttu-id="5dac4-228">Dalším použitím pro tyto `Try*` atributy je vzor.</span><span class="sxs-lookup"><span data-stu-id="5dac4-228">Another use for these attributes is the `Try*` pattern.</span></span> <span data-ttu-id="5dac4-229">Postconditions pro `ref` `out` a proměnné jsou sdělovány prostřednictvím vrácená hodnota.</span><span class="sxs-lookup"><span data-stu-id="5dac4-229">The postconditions for `ref` and `out` variables are communicated through the return value.</span></span> <span data-ttu-id="5dac4-230">Zvažte tuto metodu zobrazenou dříve:</span><span class="sxs-lookup"><span data-stu-id="5dac4-230">Consider this method shown earlier:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="5dac4-231">Předchozí metoda následuje za typickým idiomem .NET: `message` vrácená hodnota označuje, zda byla nastavena na nalezenou hodnotu nebo, pokud není nalezena žádná zpráva, na výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5dac4-231">The preceding method follows a typical .NET idiom: the return value indicates if `message` was set to the found value or, if no message is found, to the default value.</span></span> <span data-ttu-id="5dac4-232">Pokud metoda `true`vrátí , `message` hodnota není null; jinak metoda nastaví `message` na null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-232">If the method returns `true`, the value of `message` isn't null; otherwise, the method sets `message` to null.</span></span>

<span data-ttu-id="5dac4-233">Můžete komunikovat, že idiom pomocí atributu. `NotNullWhen`</span><span class="sxs-lookup"><span data-stu-id="5dac4-233">You can communicate that idiom using the `NotNullWhen` attribute.</span></span> <span data-ttu-id="5dac4-234">Při aktualizaci podpisu pro typy `message` odkazů `string?` s možnou hodnotou null vytvořte atribut a přidejte:</span><span class="sxs-lookup"><span data-stu-id="5dac4-234">When you update the signature for nullable reference types, make `message` a `string?` and add an attribute:</span></span>

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

<span data-ttu-id="5dac4-235">V předchozím příkladu `message` je známo, že hodnota `TryGetMessage` není `true`null při vrátí .</span><span class="sxs-lookup"><span data-stu-id="5dac4-235">In the preceding example, the value of `message` is known to be not null when `TryGetMessage` returns `true`.</span></span> <span data-ttu-id="5dac4-236">Měli byste anotovat podobné metody v základu kódu stejným způsobem: argumenty mohou být `null`a je `true`známo, že nejsou null, když metoda vrátí .</span><span class="sxs-lookup"><span data-stu-id="5dac4-236">You should annotate similar methods in your codebase in the same way: the arguments could be `null`, and are known to be not null when the method returns `true`.</span></span>

<span data-ttu-id="5dac4-237">Je tu ještě jeden poslední atribut, který můžete také potřebovat.</span><span class="sxs-lookup"><span data-stu-id="5dac4-237">There's one final attribute you may also need.</span></span> <span data-ttu-id="5dac4-238">Někdy stav null vrácené hodnoty závisí na stavu null jednoho nebo více vstupních argumentů.</span><span class="sxs-lookup"><span data-stu-id="5dac4-238">Sometimes the null state of a return value depends on the null state of one or more input arguments.</span></span> <span data-ttu-id="5dac4-239">Tyto metody vrátí hodnotu bez hodnoty null vždy, `null`když určité vstupní argumenty nejsou .</span><span class="sxs-lookup"><span data-stu-id="5dac4-239">These methods will return a non-null value whenever certain input arguments aren't `null`.</span></span> <span data-ttu-id="5dac4-240">Chcete-li správně opatří tyto metody, použijte `NotNullIfNotNull` atribut.</span><span class="sxs-lookup"><span data-stu-id="5dac4-240">To correctly annotate these methods, you use the `NotNullIfNotNull` attribute.</span></span> <span data-ttu-id="5dac4-241">Zvažte následující metodu:</span><span class="sxs-lookup"><span data-stu-id="5dac4-241">Consider the following method:</span></span>

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

<span data-ttu-id="5dac4-242">Pokud `url` argument není null, výstup není `null`.</span><span class="sxs-lookup"><span data-stu-id="5dac4-242">If the `url` argument isn't null, the output isn't `null`.</span></span> <span data-ttu-id="5dac4-243">Po povolení odkazů s možnou hodnotou null bude tento podpis fungovat správně za předpokladu, že rozhraní API nikdy nepřijme nulový vstup.</span><span class="sxs-lookup"><span data-stu-id="5dac4-243">Once nullable references are enabled, that signature works correctly, provided your API never accepts a null input.</span></span> <span data-ttu-id="5dac4-244">Však pokud vstup může být null, pak vrácená hodnota může být také null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-244">However, if the input could be null, then return value could also be null.</span></span> <span data-ttu-id="5dac4-245">Proto můžete změnit podpis na následující kód:</span><span class="sxs-lookup"><span data-stu-id="5dac4-245">Therefore, you could change the signature to the following code:</span></span>

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

<span data-ttu-id="5dac4-246">To také funguje, ale často nutí `null` volající implementovat další kontroly.</span><span class="sxs-lookup"><span data-stu-id="5dac4-246">That also works, but will often force callers to implement extra `null` checks.</span></span> <span data-ttu-id="5dac4-247">Smlouva je, že vrácená `null` hodnota by `url` být `null`pouze v případě, že vstupní argument je .</span><span class="sxs-lookup"><span data-stu-id="5dac4-247">The contract is that the return value would be `null` only when the input argument `url` is `null`.</span></span> <span data-ttu-id="5dac4-248">Chcete-li vyjádřit tuto smlouvu, měli byste anotovat tuto metodu, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="5dac4-248">To express that contract, you would annotate this method as shown in the following code:</span></span>

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

<span data-ttu-id="5dac4-249">Vrácená hodnota a argument byly anotovány `?` s označením, `null`že buď může být .</span><span class="sxs-lookup"><span data-stu-id="5dac4-249">The return value and the argument have both been annotated with the `?` indicating that either could be `null`.</span></span> <span data-ttu-id="5dac4-250">Atribut dále objasňuje, že vrácená hodnota `url` nebude null, `null`pokud argument není .</span><span class="sxs-lookup"><span data-stu-id="5dac4-250">The attribute further clarifies that the return value won't be null when the `url` argument isn't `null`.</span></span>

<span data-ttu-id="5dac4-251">Podmíněné postconditions zadáte pomocí těchto atributů:</span><span class="sxs-lookup"><span data-stu-id="5dac4-251">You specify conditional postconditions using these attributes:</span></span>

- <span data-ttu-id="5dac4-252">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Vstupní argument, který nelze utnou, `bool` může mít hodnotu null, pokud metoda vrátí zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5dac4-252">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="5dac4-253">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Vstupní argument s možnou hodnotou null `bool` nebude null, pokud metoda vrátí zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5dac4-253">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="5dac4-254">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Vrácená hodnota není null, pokud vstupní argument pro zadaný parametr není null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-254">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the input argument for the specified parameter isn't null.</span></span>

## <a name="verify-unreachable-code"></a><span data-ttu-id="5dac4-255">Ověření nedostupného kódu</span><span class="sxs-lookup"><span data-stu-id="5dac4-255">Verify unreachable code</span></span>

<span data-ttu-id="5dac4-256">Některé metody, obvykle pomocné shody nebo jiné metody nástroje, vždy ukončit vyvoláním výjimky.</span><span class="sxs-lookup"><span data-stu-id="5dac4-256">Some methods, typically exception helpers or other utility methods, always exit by throwing an exception.</span></span> <span data-ttu-id="5dac4-257">Nebo pomocník může vyvolat výjimku na základě hodnoty logického argumentu.</span><span class="sxs-lookup"><span data-stu-id="5dac4-257">Or, a helper may throw an exception based on the value of a Boolean argument.</span></span>

<span data-ttu-id="5dac4-258">V prvním případě můžete přidat `DoesNotReturn` atribut do deklarace metody.</span><span class="sxs-lookup"><span data-stu-id="5dac4-258">In the first case, you can add the `DoesNotReturn` attribute to the method declaration.</span></span> <span data-ttu-id="5dac4-259">Kompilátor vám pomůže třemi způsoby.</span><span class="sxs-lookup"><span data-stu-id="5dac4-259">The compiler helps you in three ways.</span></span> <span data-ttu-id="5dac4-260">Nejprve kompilátor vydá upozornění, pokud existuje cesta, kde může být metoda ukončena bez vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="5dac4-260">First, the compiler issues a warning if there is a path where the method can exit without throwing an exception.</span></span> <span data-ttu-id="5dac4-261">Za druhé, kompilátor označí jakýkoli kód po volání této `catch` metody jako *nedostupný*, dokud není zjištěna příslušná klauzule.</span><span class="sxs-lookup"><span data-stu-id="5dac4-261">Second, the compiler marks any code after a call to that method as *unreachable*, until an appropriate `catch` clause is encountered.</span></span> <span data-ttu-id="5dac4-262">Za třetí, nedostupný kód nebude mít vliv na žádné stavy null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-262">Third, the unreachable code won't affect any null states.</span></span> <span data-ttu-id="5dac4-263">Zvažte tuto metodu:</span><span class="sxs-lookup"><span data-stu-id="5dac4-263">Consider this method:</span></span>

```csharp
[DoesNotReturn]
private void FailFast()
{
   throw new InvalidOperationException();
}

public void SetState(object containedField)
{
   if (!isInitialized)
      FailFast();

   // unreachable code:
   this.field = containedField;
}
```

<span data-ttu-id="5dac4-264">V druhém případě přidáte `DoesNotReturnIf` atribut do logického parametru metody.</span><span class="sxs-lookup"><span data-stu-id="5dac4-264">In the second case, you add the `DoesNotReturnIf` attribute to a Boolean parameter of the method.</span></span> <span data-ttu-id="5dac4-265">Předchozí příklad můžete upravit následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5dac4-265">You can modify the previous example as follows:</span></span>

```csharp
private void FailFast([DoesNotReturnIf(false)]bool isValid)
{
   if (!isValid)
       throw new InvalidOperationException();
}

public void SetState(object containedField)
{
   FailFast(isInitialized);

   // unreachable code when "isInitialized" is false:
   this.field = containedField;
}
```

## <a name="summary"></a><span data-ttu-id="5dac4-266">Souhrn</span><span class="sxs-lookup"><span data-stu-id="5dac4-266">Summary</span></span>

<span data-ttu-id="5dac4-267">Přidání typů odkazů s možnou hodnotou null poskytuje počáteční slovní `null`zásobu k popisu očekávání api pro proměnné, které by mohly být .</span><span class="sxs-lookup"><span data-stu-id="5dac4-267">Adding nullable reference types provides an initial vocabulary to describe your APIs expectations for variables that could be `null`.</span></span> <span data-ttu-id="5dac4-268">Další atributy poskytují bohatší slovní zásobu k popisu stavu null proměnných jako předpoklady a postconditions.</span><span class="sxs-lookup"><span data-stu-id="5dac4-268">The additional attributes provide a richer vocabulary to describe the null state of variables as preconditions and postconditions.</span></span> <span data-ttu-id="5dac4-269">Tyto atributy jasněji popisují vaše očekávání a poskytují lepší prostředí pro vývojáře, kteří používají vaše rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="5dac4-269">These attributes more clearly describe your expectations and provide a better experience for the developers using your APIs.</span></span>

<span data-ttu-id="5dac4-270">Při aktualizaci knihoven pro kontext s možnou hodnotou null přidejte tyto atributy, které uživatele vašich api navedou ke správnému použití.</span><span class="sxs-lookup"><span data-stu-id="5dac4-270">As you update libraries for a nullable context, add these attributes to guide users of your APIs to the correct usage.</span></span> <span data-ttu-id="5dac4-271">Tyto atributy vám pomohou plně popsat stav null vstupních argumentů a vrácených hodnot:</span><span class="sxs-lookup"><span data-stu-id="5dac4-271">These attributes help you fully describe the null-state of input arguments and return values:</span></span>

- <span data-ttu-id="5dac4-272">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Vstupní argument, který nelze upustit, může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-272">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="5dac4-273">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Vstupní argument s možnou hodnotou null by nikdy neměl mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-273">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>
- <span data-ttu-id="5dac4-274">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Vrácená hodnota, jejíž nenulovatelná hodnota může být null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-274">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="5dac4-275">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Vrácená hodnota s možnou hodnotou null nikdy nebude null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-275">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>
- <span data-ttu-id="5dac4-276">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Vstupní argument, který nelze utnou, `bool` může mít hodnotu null, pokud metoda vrátí zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5dac4-276">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="5dac4-277">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Vstupní argument s možnou hodnotou null `bool` nebude null, pokud metoda vrátí zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5dac4-277">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="5dac4-278">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Vrácená hodnota není null, pokud vstupní argument pro zadaný parametr není null.</span><span class="sxs-lookup"><span data-stu-id="5dac4-278">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the input argument for the specified parameter isn't null.</span></span>
- <span data-ttu-id="5dac4-279">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): Metoda nikdy vrátí.</span><span class="sxs-lookup"><span data-stu-id="5dac4-279">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): A method never returns.</span></span> <span data-ttu-id="5dac4-280">Jinými slovy vždy vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="5dac4-280">In other words, it always throws an exception.</span></span>
- <span data-ttu-id="5dac4-281">[DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): Tato metoda nikdy `bool` vrátí, pokud přidružený parametr má zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5dac4-281">[DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): This method never returns if the associated `bool` parameter has the specified value.</span></span>
