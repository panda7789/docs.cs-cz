---
title: "Co je nového v C# 7.2"
description: "Přehled nových funkcí v C# 7.2."
keywords: "C# jazyka návrhu, 7.2, Visual Studio 2017"
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: db22c9251fa5e9f5a9cb66af6ec8b193b88e0eb3
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2018
---
# <a name="whats-new-in-c-72"></a><span data-ttu-id="0e902-104">Co je nového v C# 7.2</span><span class="sxs-lookup"><span data-stu-id="0e902-104">What's new in C# 7.2</span></span>

<span data-ttu-id="0e902-105">C# 7.2 je jiné verze bodu, který přidává několik užitečných funkcí.</span><span class="sxs-lookup"><span data-stu-id="0e902-105">C# 7.2 is another point release that adds a number of useful features.</span></span>
<span data-ttu-id="0e902-106">Jeden motivu pro tuto verzi je efektivnější práci s typy hodnot vyhnout nepotřebné kopie nebo přidělení.</span><span class="sxs-lookup"><span data-stu-id="0e902-106">One theme for this release is working more efficiently with value types by avoiding unnecessary copies or allocations.</span></span> 

<span data-ttu-id="0e902-107">Zbývající součásti jsou malé, dobrý obsahovat funkce.</span><span class="sxs-lookup"><span data-stu-id="0e902-107">The remaining features are small, nice-to-have features.</span></span>

<span data-ttu-id="0e902-108">C# 7.2 používá [výběr verze jazyka](csharp-7-1.md#language-version-selection) prvku konfigurace vyberte verzi jazyka kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="0e902-108">C# 7.2 uses the [language version selection](csharp-7-1.md#language-version-selection) configuration element to select the compiler language version.</span></span>

<span data-ttu-id="0e902-109">Mezi nové jazykové funkce v této verzi jsou:</span><span class="sxs-lookup"><span data-stu-id="0e902-109">The new language features in this release are:</span></span>

* [<span data-ttu-id="0e902-110">Referenční sémantika s typy hodnot</span><span class="sxs-lookup"><span data-stu-id="0e902-110">Reference semantics with value types</span></span>](#reference-semantics-with-value-types)
  - <span data-ttu-id="0e902-111">Kombinace syntaxe vylepšení, které umožňují práci s typy hodnot pomocí sémantiky odkaz.</span><span class="sxs-lookup"><span data-stu-id="0e902-111">A combination of syntax improvements that enable working with value types using reference semantics.</span></span>
* [<span data-ttu-id="0e902-112">Bez koncové pojmenované argumenty</span><span class="sxs-lookup"><span data-stu-id="0e902-112">Non-trailing named arguments</span></span>](#non-trailing-named-arguments)
  - <span data-ttu-id="0e902-113">Pojmenované argumenty může následovat poziční argumenty.</span><span class="sxs-lookup"><span data-stu-id="0e902-113">Named arguments can be followed by positional arguments.</span></span>
* [<span data-ttu-id="0e902-114">Úvodní podtržítka v číselné literály</span><span class="sxs-lookup"><span data-stu-id="0e902-114">Leading underscores in numeric literals</span></span>](#leading-underscores-in-numeric-literals)
  - <span data-ttu-id="0e902-115">Číselné literály teď může mít úvodní podtržítka před žádné tištěné číslice.</span><span class="sxs-lookup"><span data-stu-id="0e902-115">Numeric literals can now have leading underscores before any printed digits.</span></span>
* [<span data-ttu-id="0e902-116">`private protected` Modifikátor přístupu</span><span class="sxs-lookup"><span data-stu-id="0e902-116">`private protected` access modifier</span></span>](#private-protected-access-modifier)
  - <span data-ttu-id="0e902-117">`private protected` – Modifikátor přístupu umožňuje přístup k odvozené třídy ve stejném sestavení.</span><span class="sxs-lookup"><span data-stu-id="0e902-117">The `private protected` access modifier enables access for derived classes in the same assembly.</span></span>

## <a name="reference-semantics-with-value-types"></a><span data-ttu-id="0e902-118">Odkaz na sémantiku s typy hodnot</span><span class="sxs-lookup"><span data-stu-id="0e902-118">Reference semantics with value types</span></span>

<span data-ttu-id="0e902-119">Jazykové funkce byla zavedená v 7.2 umožňují pracovat s typy hodnot při používání sémantiky odkaz.</span><span class="sxs-lookup"><span data-stu-id="0e902-119">Language features introduced in 7.2 let you work with value types while using reference semantics.</span></span> <span data-ttu-id="0e902-120">Jsou navrženy pro zvýšení výkonu pomocí minimalizace kopírování typy hodnot, aniž by docházelo k přidělení paměti související s používáním odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="0e902-120">They are designed to increase performance by minimizing copying value types without incurring the memory allocations associated with using reference types.</span></span> <span data-ttu-id="0e902-121">Funkce patří:</span><span class="sxs-lookup"><span data-stu-id="0e902-121">The features include:</span></span>

 - <span data-ttu-id="0e902-122">`in` – Modifikátor parametrů, chcete-li určit, že je argument předaná odkaz ale nedojde ke změně volané metodou.</span><span class="sxs-lookup"><span data-stu-id="0e902-122">The `in` modifier on parameters, to specify that an argument is passed by reference but not modified by the called method.</span></span>
 - <span data-ttu-id="0e902-123">`ref readonly` Modifikátor na metoda vrátí označíte, že metoda vrátí jeho hodnotu odkazem, ale neumožňuje zápisy na tento objekt.</span><span class="sxs-lookup"><span data-stu-id="0e902-123">The `ref readonly` modifier on method returns, to indicate that a method returns its value by reference but doesn't allow writes to that object.</span></span>
 - <span data-ttu-id="0e902-124">`readonly struct` Prohlášení znamená, že struktury se nedá změnit a mají být předány jako `in` parametru její metody člen.</span><span class="sxs-lookup"><span data-stu-id="0e902-124">The `readonly struct` declaration, to indicate that a struct is immutable and should be passed as an `in` parameter to its member methods.</span></span>
 - <span data-ttu-id="0e902-125">`ref struct` Prohlášení znamená, že typu Struktura přistupují k spravované paměti přímo a musí vždy zásobníku přidělit.</span><span class="sxs-lookup"><span data-stu-id="0e902-125">The `ref struct` declaration, to indicate that a struct type accesses managed memory directly and must always be stack allocated.</span></span>

<span data-ttu-id="0e902-126">Můžete si přečíst informace o všech těchto změn v [typů hodnot pomocí sémantiky odkaz](../reference-semantics-with-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="0e902-126">You can read more about all these changes in [Using value types with reference semantics](../reference-semantics-with-value-types.md).</span></span>

## <a name="non-trailing-named-arguments"></a><span data-ttu-id="0e902-127">Bez koncové pojmenované argumenty</span><span class="sxs-lookup"><span data-stu-id="0e902-127">Non-trailing named arguments</span></span>

<span data-ttu-id="0e902-128">Volání metody teď může použít pojmenované argumenty, které předcházet argumentů umístění těchto pojmenovaných argumenty po na správném místě.</span><span class="sxs-lookup"><span data-stu-id="0e902-128">Method calls may now use named arguments that precede positional arguments when those named arguments are in the correct positions.</span></span> <span data-ttu-id="0e902-129">Další informace najdete v části [pojmenované a nepovinné argumenty](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="0e902-129">For more information see [Named and optional arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span></span>

## <a name="leading-underscores-in-numeric-literals"></a><span data-ttu-id="0e902-130">Úvodní podtržítka v číselné literály</span><span class="sxs-lookup"><span data-stu-id="0e902-130">Leading underscores in numeric literals</span></span>

<span data-ttu-id="0e902-131">Implementace podpory pro číslice oddělovače v C# 7.0 neumožnila `_` jako první znak literálovou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="0e902-131">The implementation of support for digit separators in C# 7.0 didn't allow the `_` to be the first character of the literal value.</span></span> <span data-ttu-id="0e902-132">Hex a binární číselné literály může teď začínají `_`.</span><span class="sxs-lookup"><span data-stu-id="0e902-132">Hex and binary numeric literals may now begin with an `_`.</span></span> 

<span data-ttu-id="0e902-133">Příklad:</span><span class="sxs-lookup"><span data-stu-id="0e902-133">For example:</span></span>

```csharp
int binaryValue = 0b_0101_0101;
```

## <a name="private-protected-access-modifier"></a><span data-ttu-id="0e902-134">_privátní chráněné_ – modifikátor přístupu</span><span class="sxs-lookup"><span data-stu-id="0e902-134">_private protected_ access modifier</span></span>

<span data-ttu-id="0e902-135">Nakonec novou modifikátor přístupu složené: `private protected` znamená, že může být členem přistupovat pomocí obsahující třídu nebo odvozené třídy, které jsou deklarovány ve stejném sestavení.</span><span class="sxs-lookup"><span data-stu-id="0e902-135">Finally, a new compound access modifier: `private protected` indicates that a member may be accessed by containing class or derived classes that are declared in the same assembly.</span></span> <span data-ttu-id="0e902-136">Při `protected internal` umožňuje přístup odvozené třídy nebo třídy, které jsou ve stejném sestavení `private protected` omezuje přístup na odvozené typy deklarován ve stejném sestavení.</span><span class="sxs-lookup"><span data-stu-id="0e902-136">While `protected internal` allows access by derived classes or classes that are in the same assembly, `private protected` limits access to derived types declared in the same assembly.</span></span>

<span data-ttu-id="0e902-137">Další informace najdete v části [přístup modifikátory](../language-reference/keywords/access-modifiers.md) v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0e902-137">For more information see [access modifiers](../language-reference/keywords/access-modifiers.md) in the language reference.</span></span>
