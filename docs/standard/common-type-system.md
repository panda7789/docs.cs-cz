---
title: "Obecný systém typů & Common Language Specification"
description: "Zjistěte, jak běžné typ systému (CTS) a specifikace CLS (Common Language) umožňují pro .NET pro podporu více jazyků."
keywords: "Rozhraní .NET, .NET core"
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3b1f5725-ac94-4f17-8e5f-244442438a4d
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d7626b0a6a902465416187b2c09d624dfe9a9773
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="common-type-system--common-language-specification"></a><span data-ttu-id="37d61-104">Obecný systém typů & Common Language Specification</span><span class="sxs-lookup"><span data-stu-id="37d61-104">Common Type System & Common Language Specification</span></span>

<span data-ttu-id="37d61-105">Znovu dva termíny, které jsou volně používat na světě .NET ve skutečnosti jsou velmi důležité, abyste pochopili, jak implementace rozhraní .NET umožňuje vývoj vícejazyčné a pochopit, jak funguje.</span><span class="sxs-lookup"><span data-stu-id="37d61-105">Again, two terms that are freely used in the .NET world, they actually are crucial to understand how a .NET implementation enables multi-language development and to understand how it works.</span></span>

## <a name="common-type-system"></a><span data-ttu-id="37d61-106">Obecný systém typů</span><span class="sxs-lookup"><span data-stu-id="37d61-106">Common Type System</span></span>

<span data-ttu-id="37d61-107">Chcete-li začít od začátku, mějte na paměti, že je implementace rozhraní .NET _bez ohledu na jazyk_.</span><span class="sxs-lookup"><span data-stu-id="37d61-107">To start from the beginning, remember that a .NET implementation is _language agnostic_.</span></span> <span data-ttu-id="37d61-108">Právě to však neznamená, že může být z programátorem zapsat v libovolném jazyce, který může být sestaven svůj kód do IL.</span><span class="sxs-lookup"><span data-stu-id="37d61-108">This doesn’t just mean that a programmer can write her code in any language that can be compiled to IL.</span></span> <span data-ttu-id="37d61-109">Taky to znamená, že uživatel musí být moci pracovat s kód napsaný v jiných jazycích, které jsou možné na implementaci rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="37d61-109">It also means that she needs to be able to interact with code written in other languages that are able to be used on a .NET implementation.</span></span>

<span data-ttu-id="37d61-110">Pokud to chcete provést transparentně, musí být běžný způsob popisují všechny podporované typy.</span><span class="sxs-lookup"><span data-stu-id="37d61-110">In order to do this transparently, there has to be a common way to describe all supported types.</span></span> <span data-ttu-id="37d61-111">Toto je co běžné typ systému (CTS) má na starosti dělat.</span><span class="sxs-lookup"><span data-stu-id="37d61-111">This is what the Common Type System (CTS) is in charge of doing.</span></span> <span data-ttu-id="37d61-112">Došlo k několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="37d61-112">It was made to do several things:</span></span>

*   <span data-ttu-id="37d61-113">Vytvořte rozhraní pro provádění mezi jazyky.</span><span class="sxs-lookup"><span data-stu-id="37d61-113">Establish a framework for cross-language execution.</span></span>
*   <span data-ttu-id="37d61-114">Zadejte model objektově orientované na podporu implementace různé jazyky na implementaci rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="37d61-114">Provide an object-oriented model to support implementing various languages on a .NET implementation.</span></span>
*   <span data-ttu-id="37d61-115">Definujte sadu pravidel, která řídí všechny jazyky při rozhodování o práci s typy.</span><span class="sxs-lookup"><span data-stu-id="37d61-115">Define a set of rules that all languages must follow when it comes to working with types.</span></span>
*   <span data-ttu-id="37d61-116">Zadejte knihovnu, která obsahuje základní primitivní typy, které se používají při vývoji aplikace (jako je třeba `Boolean`, `Byte`, `Char` atd.)</span><span class="sxs-lookup"><span data-stu-id="37d61-116">Provide a library that contains the basic primitive types that are used in application development (such as, `Boolean`, `Byte`, `Char` etc.)</span></span>

<span data-ttu-id="37d61-117">Definuje dva hlavní typy typy, které by mělo podporovat CTS: typy odkazu a hodnotu.</span><span class="sxs-lookup"><span data-stu-id="37d61-117">CTS defines two main kinds of types that should be supported: reference and value types.</span></span> <span data-ttu-id="37d61-118">Jejich názvy přejděte na jejich definice.</span><span class="sxs-lookup"><span data-stu-id="37d61-118">Their names point to their definitions.</span></span>

<span data-ttu-id="37d61-119">Odkazové typy objektů jsou reprezentované pomocí odkaz na skutečnou hodnotu objektu; odkaz na tady je podobná ukazatel v jazyce C/C++.</span><span class="sxs-lookup"><span data-stu-id="37d61-119">Reference types’ objects are represented by a reference to the object’s actual value; a reference here is similar to a pointer in C/C++.</span></span> <span data-ttu-id="37d61-120">Jednoduše odkazuje umístění paměti, kde jsou hodnoty objektu.</span><span class="sxs-lookup"><span data-stu-id="37d61-120">It simply refers to a memory location where the objects’ values are.</span></span> <span data-ttu-id="37d61-121">Tato akce nemá velký dopad na tom, jak se používají tyto typy.</span><span class="sxs-lookup"><span data-stu-id="37d61-121">This has a profound impact on how these types are used.</span></span> <span data-ttu-id="37d61-122">Pokud přiřadit typu odkazu na proměnnou a pak předejte tuto proměnnou na metodu, například všechny změny do objektu se projeví na hlavním objektem; není žádný kopírování.</span><span class="sxs-lookup"><span data-stu-id="37d61-122">If you assign a reference type to a variable and then pass that variable into a method, for instance, any changes to the object will be reflected on the main object; there is no copying.</span></span>

<span data-ttu-id="37d61-123">Typy hodnot jsou opak, kde jsou objekty reprezentované pomocí jejich hodnot.</span><span class="sxs-lookup"><span data-stu-id="37d61-123">Value types are the opposite, where the objects are represented by their values.</span></span> <span data-ttu-id="37d61-124">Chcete-li přiřadit typ hodnoty proměnné, jsou v podstatě kopírování hodnotu objektu.</span><span class="sxs-lookup"><span data-stu-id="37d61-124">If you assign a value type to a variable, you are essentially copying a value of the object.</span></span>

<span data-ttu-id="37d61-125">CTS definuje několik kategorií typů, které mají své specifické sémantiku a využití:</span><span class="sxs-lookup"><span data-stu-id="37d61-125">CTS defines several categories of types, each with their specific semantics and usage:</span></span>

*   <span data-ttu-id="37d61-126">Třídy</span><span class="sxs-lookup"><span data-stu-id="37d61-126">Classes</span></span>
*   <span data-ttu-id="37d61-127">Struktury</span><span class="sxs-lookup"><span data-stu-id="37d61-127">Structures</span></span>
*   <span data-ttu-id="37d61-128">Výčty</span><span class="sxs-lookup"><span data-stu-id="37d61-128">Enums</span></span>
*   <span data-ttu-id="37d61-129">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="37d61-129">Interfaces</span></span>
*   <span data-ttu-id="37d61-130">Delegáty</span><span class="sxs-lookup"><span data-stu-id="37d61-130">Delegates</span></span>

<span data-ttu-id="37d61-131">CTS definuje také všechny ostatní vlastnosti z typů, jako je například modifikátory přístupu, co jsou členy platný typ, jak dědičnosti a přetížení funguje a tak dále.</span><span class="sxs-lookup"><span data-stu-id="37d61-131">CTS also defines all other properties of the types, such as access modifiers, what are valid type members, how inheritance and overloading works and so on.</span></span> <span data-ttu-id="37d61-132">Bohužel přejdete přímým do jakéhokoli z nich je nad rámec úvodní článek jako je tato, ale můžete obrátit [více prostředků](#more-resources) na konci odkazy na další podrobné obsah, který obsahuje tato témata.</span><span class="sxs-lookup"><span data-stu-id="37d61-132">Unfortunately, going deep into any of those is beyond the scope of an introductory article such as this, but you can consult [More resources](#more-resources) section at the end for links to more in-depth content that covers these topics.</span></span>

## <a name="common-language-specification"></a><span data-ttu-id="37d61-133">CLS (Common Language Specification)</span><span class="sxs-lookup"><span data-stu-id="37d61-133">Common Language Specification</span></span>

<span data-ttu-id="37d61-134">Pokud chcete povolit scénáře plnou interoperabilitu, musí všechny objekty, které jsou vytvořené v kódu spoléhat na některé funkcím v jazycích, které spotřebovávají je (jsou jejich _volající_).</span><span class="sxs-lookup"><span data-stu-id="37d61-134">To enable full interoperability scenarios, all objects that are created in code must rely on some commonality in the languages that are consuming them (are their _callers_).</span></span> <span data-ttu-id="37d61-135">Vzhledem k tomu, že existuje mnoho různých jazyků, rozhraní .NET byla zadána těchto commonalities v takzvaný **Common Language Specification** (CLS).</span><span class="sxs-lookup"><span data-stu-id="37d61-135">Since there are numerous different languages, .NET has specified those commonalities in something called the **Common Language Specification** (CLS).</span></span> <span data-ttu-id="37d61-136">Specifikace CLS definuje sadu funkcí, které jsou vyžadovány mnoho běžných aplikací.</span><span class="sxs-lookup"><span data-stu-id="37d61-136">CLS defines a set of features that are needed by many common applications.</span></span> <span data-ttu-id="37d61-137">Nabízí taky řazení recept na jakýkoli jazyk, který se implementuje nad .NET na vše potřebné pro podporu.</span><span class="sxs-lookup"><span data-stu-id="37d61-137">It also provides a sort of recipe for any language that is implemented on top of .NET on what it needs to support.</span></span>

<span data-ttu-id="37d61-138">Specifikací CLS je podmnožinou CTS.</span><span class="sxs-lookup"><span data-stu-id="37d61-138">CLS is a subset of the CTS.</span></span> <span data-ttu-id="37d61-139">To znamená, že všechna pravidla v CTS platí také pro specifikaci CLS pouze v případě jsou více striktní pravidla se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="37d61-139">This means that all of the rules in the CTS also apply to the CLS, unless the CLS rules are more strict.</span></span> <span data-ttu-id="37d61-140">Pokud součást je sestaven pomocí pouze pravidla ve specifikaci CLS, tedy zpřístupňuje pouze funkce specifikací CLS v jeho rozhraní API, je označováno jako **kompatibilní se specifikací CLS**.</span><span class="sxs-lookup"><span data-stu-id="37d61-140">If a component is built using only the rules in the CLS, that is, it exposes only the CLS features in its API, it is said to be **CLS-compliant**.</span></span> <span data-ttu-id="37d61-141">Například `<framework-librares>` jsou kompatibilní se specifikací CLS právě proto potřebují k práci ve všech jazycích, které jsou podporovány v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="37d61-141">For instance, the `<framework-librares>` are CLS-compliant precisely because they need to work across all of the languages that are supported on .NET.</span></span>

<span data-ttu-id="37d61-142">Lze najít dokumenty v [více prostředků](#more-resources) části níže získat přehled o všech funkcí ve specifikaci CLS.</span><span class="sxs-lookup"><span data-stu-id="37d61-142">You can consult the documents in the [More Resources](#more-resources) section below to get an overview of all the features in the CLS.</span></span>

## <a name="more-resources"></a><span data-ttu-id="37d61-143">Další prostředky</span><span class="sxs-lookup"><span data-stu-id="37d61-143">More resources</span></span>

*   [<span data-ttu-id="37d61-144">Obecný systém typů</span><span class="sxs-lookup"><span data-stu-id="37d61-144">Common Type System</span></span>](./base-types/common-type-system.md)
*   [<span data-ttu-id="37d61-145">Common Language Specification</span><span class="sxs-lookup"><span data-stu-id="37d61-145">Common Language Specification</span></span>](language-independence-and-language-independent-components.md)
