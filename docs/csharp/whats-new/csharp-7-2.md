---
title: Co je nového v jazyce C# 7.2
description: Přehled nových funkcí v jazyce C# 7.2.
ms.date: 08/16/2017
ms.openlocfilehash: b8b2be68aac3cba92e0dbd74dfe4ee3cbbef0e88
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706088"
---
# <a name="whats-new-in-c-72"></a><span data-ttu-id="eb907-103">Co je nového v jazyce C# 7.2</span><span class="sxs-lookup"><span data-stu-id="eb907-103">What's new in C# 7.2</span></span>

<span data-ttu-id="eb907-104">C# 7.2 je jiný bod. Tato verze přidává řadu užitečných funkcí.</span><span class="sxs-lookup"><span data-stu-id="eb907-104">C# 7.2 is another point release that adds a number of useful features.</span></span>
<span data-ttu-id="eb907-105">Jeden motiv pro tuto verzi je efektivnější práci s typy hodnot se vyhnout zbytečným kopie nebo přidělení.</span><span class="sxs-lookup"><span data-stu-id="eb907-105">One theme for this release is working more efficiently with value types by avoiding unnecessary copies or allocations.</span></span>

<span data-ttu-id="eb907-106">Zbývající součásti jsou malé, nice mají funkce.</span><span class="sxs-lookup"><span data-stu-id="eb907-106">The remaining features are small, nice-to-have features.</span></span>

<span data-ttu-id="eb907-107">Používá C# 7.2 [výběr verze jazyka](../language-reference/configure-language-version.md) konfigurační prvek a vyberte verzi jazyka kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="eb907-107">C# 7.2 uses the [language version selection](../language-reference/configure-language-version.md) configuration element to select the compiler language version.</span></span>

<span data-ttu-id="eb907-108">Nové funkce jazyků v této verzi jsou:</span><span class="sxs-lookup"><span data-stu-id="eb907-108">The new language features in this release are:</span></span>

* [<span data-ttu-id="eb907-109">Techniky pro psaní bezpečného kódu efektivní</span><span class="sxs-lookup"><span data-stu-id="eb907-109">Techniques for writing safe efficient code</span></span>](#safe-efficient-code-enhancements)
  - <span data-ttu-id="eb907-110">Kombinace syntaxe vylepšení, které umožňují práci s typy hodnot pomocí odkazové sémantiky.</span><span class="sxs-lookup"><span data-stu-id="eb907-110">A combination of syntax improvements that enable working with value types using reference semantics.</span></span>
* [<span data-ttu-id="eb907-111">Nekoncové pojmenované argumenty</span><span class="sxs-lookup"><span data-stu-id="eb907-111">Non-trailing named arguments</span></span>](#non-trailing-named-arguments)
  - <span data-ttu-id="eb907-112">Pojmenované argumenty může být následován poziční argumenty.</span><span class="sxs-lookup"><span data-stu-id="eb907-112">Named arguments can be followed by positional arguments.</span></span>
* [<span data-ttu-id="eb907-113">Úvodní podtržítka v numerických literálech</span><span class="sxs-lookup"><span data-stu-id="eb907-113">Leading underscores in numeric literals</span></span>](#leading-underscores-in-numeric-literals)
  - <span data-ttu-id="eb907-114">Číselné literály teď můžou mít úvodní podtržítka před všechny tištěné číslice.</span><span class="sxs-lookup"><span data-stu-id="eb907-114">Numeric literals can now have leading underscores before any printed digits.</span></span>
* [<span data-ttu-id="eb907-115">`private protected` Modifikátor přístupu</span><span class="sxs-lookup"><span data-stu-id="eb907-115">`private protected` access modifier</span></span>](#private-protected-access-modifier)
  - <span data-ttu-id="eb907-116">`private protected` Modifikátor přístupu umožňuje přístup pro odvozené třídy ve stejném sestavení.</span><span class="sxs-lookup"><span data-stu-id="eb907-116">The `private protected` access modifier enables access for derived classes in the same assembly.</span></span>
* [<span data-ttu-id="eb907-117">Podmíněné `ref` výrazy</span><span class="sxs-lookup"><span data-stu-id="eb907-117">Conditional `ref` expressions</span></span>](#conditional-ref-expressions)
  - <span data-ttu-id="eb907-118">Výsledek podmíněného výrazu (`?:`) teď může být odkaz.</span><span class="sxs-lookup"><span data-stu-id="eb907-118">The result of a conditional expression (`?:`) can now be a reference.</span></span>

## <a name="safe-efficient-code-enhancements"></a><span data-ttu-id="eb907-119">Vylepšení bezpečné efektivní kódu</span><span class="sxs-lookup"><span data-stu-id="eb907-119">Safe efficient code enhancements</span></span>

<span data-ttu-id="eb907-120">Jazykových funkcí 7.2 zavedený umožňují pracovat s typy hodnot a zároveň pomocí odkazové sémantiky.</span><span class="sxs-lookup"><span data-stu-id="eb907-120">Language features introduced in 7.2 let you work with value types while using reference semantics.</span></span> <span data-ttu-id="eb907-121">Jsou určené ke zvýšení výkonu minimalizací kopírování hodnotové typy bez dalších nákladů na přidělení paměti spojených s použitím typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="eb907-121">They are designed to increase performance by minimizing copying value types without incurring the memory allocations associated with using reference types.</span></span> <span data-ttu-id="eb907-122">Mezi funkce patří:</span><span class="sxs-lookup"><span data-stu-id="eb907-122">The features include:</span></span>

- <span data-ttu-id="eb907-123">`in` Modifikátor parametrů k určení, zda je argument předaný odkazem, ale nedojde ke změně ve volané metody.</span><span class="sxs-lookup"><span data-stu-id="eb907-123">The `in` modifier on parameters, to specify that an argument is passed by reference but not modified by the called method.</span></span> <span data-ttu-id="eb907-124">Přidání `in` modifikátor na argument [zdroj kompatibilní změnu](version-update-considerations.md#source-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="eb907-124">Adding the `in` modifier to an argument is a [source compatible change](version-update-considerations.md#source-compatible-changes).</span></span>
- <span data-ttu-id="eb907-125">`ref readonly` Modifikátor metoda vrátí hodnotu označující, že metoda vrátí jeho hodnota podle odkazu, ale neumožňuje zápisy do tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="eb907-125">The `ref readonly` modifier on method returns, to indicate that a method returns its value by reference but doesn't allow writes to that object.</span></span> <span data-ttu-id="eb907-126">Přidání `ref readonly` modifikátor [zdroj kompatibilní změnu](version-update-considerations.md#source-compatible-changes), pokud je vrácená přiřadit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="eb907-126">Adding the `ref readonly` modifier is a [source compatible change](version-update-considerations.md#source-compatible-changes), if the return is assigned to a value.</span></span> <span data-ttu-id="eb907-127">Přidávání `readonly` Modifikátor pro stávající `ref` návratový příkaz je [nekompatibilní změna](version-update-considerations.md#incompatible-changes).</span><span class="sxs-lookup"><span data-stu-id="eb907-127">Adding the `readonly` modifier to an existing `ref` return statement is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="eb907-128">Vyžaduje volající aktualizovat deklarace `ref` místní proměnné k zahrnutí `readonly` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="eb907-128">It requires callers to update the declaration of `ref` local variables to include the `readonly` modifier.</span></span>
- <span data-ttu-id="eb907-129">`readonly struct` Deklarace můžete určit, že struktura je neměnná a mají být předány jako `in` parametr metody jeho členů.</span><span class="sxs-lookup"><span data-stu-id="eb907-129">The `readonly struct` declaration, to indicate that a struct is immutable and should be passed as an `in` parameter to its member methods.</span></span> <span data-ttu-id="eb907-130">Přidání `readonly` modifikátor na existující deklaraci struktury [binární kompatibilní změnu](version-update-considerations.md#binary-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="eb907-130">Adding the `readonly` modifier to an existing struct declaration is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>
- <span data-ttu-id="eb907-131">`ref struct` Deklarace můžete určit, že typu Struktura přistupuje k nim spravované paměti přímo a musí vždy zásobníku přidělovat.</span><span class="sxs-lookup"><span data-stu-id="eb907-131">The `ref struct` declaration, to indicate that a struct type accesses managed memory directly and must always be stack allocated.</span></span> <span data-ttu-id="eb907-132">Přidávání `ref` Modifikátor pro stávající `struct` deklarace je [nekompatibilní změna](version-update-considerations.md#incompatible-changes).</span><span class="sxs-lookup"><span data-stu-id="eb907-132">Adding the `ref` modifier to an existing `struct` declaration is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="eb907-133">A `ref struct` nemůže být členem třídy nebo použít v jiných umístěních, kde mohou být přiděleny do haldy.</span><span class="sxs-lookup"><span data-stu-id="eb907-133">A `ref struct` cannot be a member of a class or used in other locations where it may be allocated on the heap.</span></span>

<span data-ttu-id="eb907-134">Můžete si přečíst další informace o všech těchto změn v [psát bezpečný kód efektivní](../write-safe-efficient-code.md).</span><span class="sxs-lookup"><span data-stu-id="eb907-134">You can read more about all these changes in [Write safe efficient code](../write-safe-efficient-code.md).</span></span>

## <a name="non-trailing-named-arguments"></a><span data-ttu-id="eb907-135">Nekoncové pojmenované argumenty</span><span class="sxs-lookup"><span data-stu-id="eb907-135">Non-trailing named arguments</span></span>

<span data-ttu-id="eb907-136">Volání metody teď může použít pojmenované argumenty, které předcházet poziční argumenty, pokud tyto pojmenované argumenty jsou do správné polohy.</span><span class="sxs-lookup"><span data-stu-id="eb907-136">Method calls may now use named arguments that precede positional arguments when those named arguments are in the correct positions.</span></span> <span data-ttu-id="eb907-137">Další informace najdete v části [pojmenované a nepovinné argumenty](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="eb907-137">For more information see [Named and optional arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span></span>

## <a name="leading-underscores-in-numeric-literals"></a><span data-ttu-id="eb907-138">Úvodní podtržítka v numerických literálech</span><span class="sxs-lookup"><span data-stu-id="eb907-138">Leading underscores in numeric literals</span></span>

<span data-ttu-id="eb907-139">Implementace podpory pro oddělovače číslic v jazyce C# 7.0 neměli povolit `_` bude první znak hodnota literálu.</span><span class="sxs-lookup"><span data-stu-id="eb907-139">The implementation of support for digit separators in C# 7.0 didn't allow the `_` to be the first character of the literal value.</span></span> <span data-ttu-id="eb907-140">Hex a binární číselné literály teď začít s `_`.</span><span class="sxs-lookup"><span data-stu-id="eb907-140">Hex and binary numeric literals may now begin with an `_`.</span></span>

<span data-ttu-id="eb907-141">Příklad:</span><span class="sxs-lookup"><span data-stu-id="eb907-141">For example:</span></span>

```csharp
int binaryValue = 0b_0101_0101;
```

## <a name="private-protected-access-modifier"></a><span data-ttu-id="eb907-142">_privátní, chráněné_ modifikátor přístupu</span><span class="sxs-lookup"><span data-stu-id="eb907-142">_private protected_ access modifier</span></span>

<span data-ttu-id="eb907-143">New – modifikátor přístupu složené: `private protected` označuje, že můžou být dostupné členy obsahující třídu nebo odvozené třídy, které jsou deklarovány ve stejném sestavení.</span><span class="sxs-lookup"><span data-stu-id="eb907-143">A new compound access modifier: `private protected` indicates that a member may be accessed by containing class or derived classes that are declared in the same assembly.</span></span> <span data-ttu-id="eb907-144">Zatímco `protected internal` umožňuje přístup odvozené třídy nebo třídy, které jsou ve stejném sestavení, `private protected` omezuje přístup k odvozené typy deklarované ve stejném sestavení.</span><span class="sxs-lookup"><span data-stu-id="eb907-144">While `protected internal` allows access by derived classes or classes that are in the same assembly, `private protected` limits access to derived types declared in the same assembly.</span></span>

<span data-ttu-id="eb907-145">Další informace najdete v části [modifikátorů přístupu](../language-reference/keywords/access-modifiers.md) v referenční dokumentaci jazyka.</span><span class="sxs-lookup"><span data-stu-id="eb907-145">For more information see [access modifiers](../language-reference/keywords/access-modifiers.md) in the language reference.</span></span>

## <a name="conditional-ref-expressions"></a><span data-ttu-id="eb907-146">Podmíněné `ref` výrazy</span><span class="sxs-lookup"><span data-stu-id="eb907-146">Conditional `ref` expressions</span></span>

<span data-ttu-id="eb907-147">Nakonec podmíněného výrazu může vytvořit výsledek ref místo hodnoty výsledku.</span><span class="sxs-lookup"><span data-stu-id="eb907-147">Finally, the conditional expression may produce a ref result instead of a value result.</span></span> <span data-ttu-id="eb907-148">Například měli byste napsat následující příkaz pro načtení odkazu na první prvek v jednom ze dvou polí:</span><span class="sxs-lookup"><span data-stu-id="eb907-148">For example, you would write the following to retrieve a reference to the first element in one of two arrays:</span></span>

```csharp
ref var r = ref (arr != null ? ref arr[0] : ref otherArr[0]);
```

<span data-ttu-id="eb907-149">Proměnná `r` je odkaz na první hodnota v jednom `arr` nebo `otherArr`.</span><span class="sxs-lookup"><span data-stu-id="eb907-149">The variable `r` is a reference to the first value in either `arr` or `otherArr`.</span></span>

<span data-ttu-id="eb907-150">Další informace najdete v tématu [podmiňovací operátor (?:) ](../language-reference/operators/conditional-operator.md) v referenční dokumentaci jazyka.</span><span class="sxs-lookup"><span data-stu-id="eb907-150">For more information, see [conditional operator (?:)](../language-reference/operators/conditional-operator.md) in the language reference.</span></span>
