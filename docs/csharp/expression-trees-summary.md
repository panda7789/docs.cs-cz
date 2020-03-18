---
title: Souhrn stromů výrazů
description: Rekapituluje, jak můžete pomocí stromů výrazů vytvářet dynamické programy, které interpretují kód jako data, a vytvářet nové funkce založené na tomto kódu.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 513244a987e295c81cfb5d00d9a0cfd6912074e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145888"
---
# <a name="expression-trees-summary"></a><span data-ttu-id="d16bc-103">Souhrn stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="d16bc-103">Expression Trees Summary</span></span>

[<span data-ttu-id="d16bc-104">Předchozí -- Překlad výrazů</span><span class="sxs-lookup"><span data-stu-id="d16bc-104">Previous -- Translating Expressions</span></span>](expression-trees-translating.md)

<span data-ttu-id="d16bc-105">V této řadě jste viděli, jak můžete pomocí *stromů výrazů* vytvářet dynamické programy, které interpretují kód jako data, a vytvářet nové funkce založené na tomto kódu.</span><span class="sxs-lookup"><span data-stu-id="d16bc-105">In this series, you've seen how you can use *expression trees* to create dynamic programs that interpret code as data and build new functionality based on that code.</span></span>

<span data-ttu-id="d16bc-106">Můžete prozkoumat stromy výrazů pochopit záměr algoritmu.</span><span class="sxs-lookup"><span data-stu-id="d16bc-106">You can examine expression trees to understand the intent of an algorithm.</span></span> <span data-ttu-id="d16bc-107">Můžete nejen zkoumat tento kód.</span><span class="sxs-lookup"><span data-stu-id="d16bc-107">You can not only examine that code.</span></span> <span data-ttu-id="d16bc-108">Můžete vytvořit nové stromy výrazů, které představují upravené verze původního kódu.</span><span class="sxs-lookup"><span data-stu-id="d16bc-108">You can build new expression trees that represent modified versions of the original code.</span></span>

<span data-ttu-id="d16bc-109">Stromy výrazů můžete také použít k pohledu na algoritmus a přeložit tento algoritmus do jiného jazyka nebo prostředí.</span><span class="sxs-lookup"><span data-stu-id="d16bc-109">You can also use expression trees to look at an algorithm, and translate that algorithm into another language or environment.</span></span>

## <a name="limitations"></a><span data-ttu-id="d16bc-110">Omezení</span><span class="sxs-lookup"><span data-stu-id="d16bc-110">Limitations</span></span>

<span data-ttu-id="d16bc-111">Existují některé novější prvky jazyka Jazyka Jazyka Jazyka C#, které se nepřekládají dobře do stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="d16bc-111">There are some newer C# language elements that don't translate well into expression trees.</span></span> <span data-ttu-id="d16bc-112">Stromy výrazů `await` nemohou obsahovat výrazy nebo `async` výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="d16bc-112">Expression trees cannot contain `await` expressions, or `async` lambda expressions.</span></span> <span data-ttu-id="d16bc-113">Mnoho funkcí přidaných ve verzi C# 6 se nezobrazuje přesně tak, jak je napsáno ve stromech výrazů.</span><span class="sxs-lookup"><span data-stu-id="d16bc-113">Many of the features added in the C# 6 release don't appear exactly as written in expression trees.</span></span> <span data-ttu-id="d16bc-114">Místo toho budou novější funkce vystaveny ve stromech výrazů v ekvivalentní starší syntaxi.</span><span class="sxs-lookup"><span data-stu-id="d16bc-114">Instead, newer features will be exposed in expressions trees in the equivalent, earlier syntax.</span></span> <span data-ttu-id="d16bc-115">To nemusí být tak velké omezení, jak si možná myslíte.</span><span class="sxs-lookup"><span data-stu-id="d16bc-115">This may not be as much of a limitation as you might think.</span></span> <span data-ttu-id="d16bc-116">Ve skutečnosti to znamená, že váš kód, který interpretuje stromy výrazů bude pravděpodobně i nadále fungovat stejně, když jsou zavedeny nové funkce jazyka.</span><span class="sxs-lookup"><span data-stu-id="d16bc-116">In fact, it means that your code that interprets expression trees will likely still work the same when new language features are introduced.</span></span>

<span data-ttu-id="d16bc-117">I s těmito omezeními stromy výrazů umožňují vytvářet dynamické algoritmy, které spoléhají na interpretaci a úpravu kódu, který je reprezentován jako datová struktura.</span><span class="sxs-lookup"><span data-stu-id="d16bc-117">Even with these limitations, expression trees do enable you to create dynamic algorithms that rely on interpreting and modifying code that is represented as a data structure.</span></span> <span data-ttu-id="d16bc-118">Je to mocný nástroj a je to jedna z funkcí ekosystému .NET, který umožňuje bohaté knihovny, jako je entity Framework k dosažení toho, co dělají.</span><span class="sxs-lookup"><span data-stu-id="d16bc-118">It's a powerful tool, and it's one of the features of the .NET ecosystem that enables rich libraries such as Entity Framework to accomplish what they do.</span></span>
