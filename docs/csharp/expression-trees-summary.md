---
title: Souhrn stromů výrazů
description: Mění způsob použití stromů výrazů k vytváření dynamických programů, které interpretují kód jako data a vytvářejí nové funkce založené na tomto kódu.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 43715c94b70f1cd7f758cde91ae7c8d1b2f70f9f
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036746"
---
# <a name="expression-trees-summary"></a><span data-ttu-id="9b00b-103">Souhrn stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="9b00b-103">Expression Trees Summary</span></span>

[<span data-ttu-id="9b00b-104">Předchozí--posunutí výrazů</span><span class="sxs-lookup"><span data-stu-id="9b00b-104">Previous -- Translating Expressions</span></span>](expression-trees-translating.md)

<span data-ttu-id="9b00b-105">V této řadě jste viděli, jak můžete pomocí *stromů výrazů* vytvářet dynamické programy, které interpretují kód jako data a vytvářejí nové funkce založené na tomto kódu.</span><span class="sxs-lookup"><span data-stu-id="9b00b-105">In this series, you've seen how you can use *expression trees* to create dynamic programs that interpret code as data and build new functionality based on that code.</span></span>

<span data-ttu-id="9b00b-106">Můžete prozkoumávat stromy výrazů a pochopit záměr algoritmu.</span><span class="sxs-lookup"><span data-stu-id="9b00b-106">You can examine expression trees to understand the intent of an algorithm.</span></span> <span data-ttu-id="9b00b-107">Tento kód nelze kontrolovat.</span><span class="sxs-lookup"><span data-stu-id="9b00b-107">You can not only examine that code.</span></span> <span data-ttu-id="9b00b-108">Můžete vytvořit nové stromy výrazů, které reprezentují upravené verze původního kódu.</span><span class="sxs-lookup"><span data-stu-id="9b00b-108">You can build new expression trees that represent modified versions of the original code.</span></span>

<span data-ttu-id="9b00b-109">Můžete také použít stromy výrazů k zobrazení algoritmu a překladu tohoto algoritmu do jiného jazyka nebo prostředí.</span><span class="sxs-lookup"><span data-stu-id="9b00b-109">You can also use expression trees to look at an algorithm, and translate that algorithm into another language or environment.</span></span> 

## <a name="limitations"></a><span data-ttu-id="9b00b-110">Omezení</span><span class="sxs-lookup"><span data-stu-id="9b00b-110">Limitations</span></span>

<span data-ttu-id="9b00b-111">Existují některé novější C# jazykové prvky, které nemusejí být dobře přeloženy do stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="9b00b-111">There are some newer C# language elements that don't translate well into expression trees.</span></span> <span data-ttu-id="9b00b-112">Stromy výrazů nemůžou obsahovat výrazy `await` ani `async` výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="9b00b-112">Expression trees cannot contain `await` expressions, or `async` lambda expressions.</span></span> <span data-ttu-id="9b00b-113">Mnohé z funkcí přidaných v C# 6. verzi se ve stromech výrazů přesně neprojeví jako zapsané.</span><span class="sxs-lookup"><span data-stu-id="9b00b-113">Many of the features added in the C# 6 release don't appear exactly as written in expression trees.</span></span> <span data-ttu-id="9b00b-114">Místo toho budou ve stromech výrazů k dispozici novější funkce v ekvivalentu předchozí syntaxe.</span><span class="sxs-lookup"><span data-stu-id="9b00b-114">Instead, newer features will be exposed in expressions trees in the equivalent, earlier syntax.</span></span> <span data-ttu-id="9b00b-115">To nemusí být tolik omezení, jak si možná myslíte.</span><span class="sxs-lookup"><span data-stu-id="9b00b-115">This may not be as much of a limitation as you might think.</span></span> <span data-ttu-id="9b00b-116">Ve skutečnosti to znamená, že váš kód, který interpretuje stromy výrazů, bude nejspíš stále fungovat stejně, když jsou zavedeny nové funkce jazyka.</span><span class="sxs-lookup"><span data-stu-id="9b00b-116">In fact, it means that your code that interprets expression trees will likely still work the same when new language features are introduced.</span></span>

<span data-ttu-id="9b00b-117">I s těmito omezeními mají stromy výrazů možnost vytvářet dynamické algoritmy, které spoléhají na interpretaci a úpravu kódu, který je reprezentován jako datová struktura.</span><span class="sxs-lookup"><span data-stu-id="9b00b-117">Even with these limitations, expression trees do enable you to create dynamic algorithms that rely on interpreting and modifying code that is represented as a data structure.</span></span> <span data-ttu-id="9b00b-118">Jedná se o výkonný nástroj a jedná se o jednu z funkcí ekosystému .NET, která umožňuje využít bohatých knihoven, jako je například Entity Framework k tomu, co dělají.</span><span class="sxs-lookup"><span data-stu-id="9b00b-118">It's a powerful tool, and it's one of the features of the .NET ecosystem that enables rich libraries such as Entity Framework to accomplish what they do.</span></span>
