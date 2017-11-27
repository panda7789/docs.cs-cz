---
title: "Souhrn stromů výrazů"
description: "Recaps použití stromů výrazů k vytvoření dynamických programy, které interpretovat kód jako data a vytvářet nové funkce založené na tento kód."
keywords: "Rozhraní .NET, .NET core"
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 8088ce0c138cdb05a6e4a4fb6467e43efd252ba7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="expression-trees-summary"></a><span data-ttu-id="b3408-104">Souhrn stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="b3408-104">Expression Trees Summary</span></span>

[<span data-ttu-id="b3408-105">Předchozí – Překladu výrazy</span><span class="sxs-lookup"><span data-stu-id="b3408-105">Previous -- Translating Expressions</span></span>](expression-trees-translating.md)

<span data-ttu-id="b3408-106">Z této série jste viděli, jak můžete použít *stromů výrazů* vytvořit dynamické programy, které interpretovat kód jako data a vytvářet nové funkce založené na tento kód.</span><span class="sxs-lookup"><span data-stu-id="b3408-106">In this series, you've seen how you can use *expression trees* to create dynamic programs that interpret code as data and build new functionality based on that code.</span></span>

<span data-ttu-id="b3408-107">Stromy výrazů pochopit záměr algoritmus můžete zkontrolovat.</span><span class="sxs-lookup"><span data-stu-id="b3408-107">You can examine expression trees to understand the intent of an algorithm.</span></span> <span data-ttu-id="b3408-108">Nelze pouze prozkoumat tento kód.</span><span class="sxs-lookup"><span data-stu-id="b3408-108">You can not only examine that code.</span></span> <span data-ttu-id="b3408-109">Můžete vytvořit nové stromů výrazů, které představují upravené verze původní kód.</span><span class="sxs-lookup"><span data-stu-id="b3408-109">You can build new expression trees that represent modified versions of the original code.</span></span>

<span data-ttu-id="b3408-110">Můžete taky použití stromů výrazů k podívejte se na algoritmus a převede tento algoritmus na jiný jazyk nebo prostředí.</span><span class="sxs-lookup"><span data-stu-id="b3408-110">You can also use expression trees to look at an algorithm, and translate that algorithm into another language or environment.</span></span> 

## <a name="limitations"></a><span data-ttu-id="b3408-111">Omezení</span><span class="sxs-lookup"><span data-stu-id="b3408-111">Limitations</span></span>

<span data-ttu-id="b3408-112">Existují některé novější C# jazyka prvky, které nejsou převede i na stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="b3408-112">There are some newer C# language elements that don't translate well into expression trees.</span></span> <span data-ttu-id="b3408-113">Stromy výrazů nesmí obsahovat `await` výrazy, nebo `async` výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="b3408-113">Expression trees cannot contain `await` expressions, or `async` lambda expressions.</span></span> <span data-ttu-id="b3408-114">Mnoho funkcí přidaných do verze jazyka C# 6 tak, jak je napsaný v stromů výrazů nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="b3408-114">Many of the features added in the C# 6 release don't appear exactly as written in expression trees.</span></span> <span data-ttu-id="b3408-115">Místo toho novější funkce zveřejní ve stromech výrazy v syntaxi ekvivalentní, dřívější.</span><span class="sxs-lookup"><span data-stu-id="b3408-115">Instead, newer features will be exposed in expressions trees in the equivalent, earlier syntax.</span></span> <span data-ttu-id="b3408-116">Toto nemusí být tolik omezeními může si myslíte.</span><span class="sxs-lookup"><span data-stu-id="b3408-116">This may not be as much of a limitation as you might think.</span></span> <span data-ttu-id="b3408-117">Ve skutečnosti znamená, že váš kód, který interpretuje stromů výrazů bude stále pravděpodobně fungovat stejně při byly zavedeny nové jazykové funkce.</span><span class="sxs-lookup"><span data-stu-id="b3408-117">In fact, it means that your code that interprets expression trees will likely still work the same when new language features are introduced.</span></span>

<span data-ttu-id="b3408-118">I když tato omezení stromů výrazů umožňují vytvářet dynamické algoritmy, které závisí na interpretace a úpravy kódu, který je reprezentován jako datové struktury.</span><span class="sxs-lookup"><span data-stu-id="b3408-118">Even with these limitations, expression trees do enable you to create dynamic algorithms that rely on interpreting and modifying code that is represetned as a data structure.</span></span> <span data-ttu-id="b3408-119">Je výkonný nástroj a je jedna z funkcí ekosystému .NET, která umožňuje bohaté knihovny, například rozhraní Entity Framework dosáhnout toho, co dělají.</span><span class="sxs-lookup"><span data-stu-id="b3408-119">It's a powerful tool, and it's one of the features of the .NET ecosystem that enables rich libraries such as Entity Framework to accomplish what they do.</span></span>

