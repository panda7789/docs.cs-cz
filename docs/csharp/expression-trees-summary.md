---
title: Souhrn stromů výrazů
description: Rekapitulace použití stromů výrazů k vytvoření dynamické programy, které interpretovat kód jako data a vytvářet nové funkce založené na tento kód.
ms.date: 06/20/2016
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 99b9463df096d3aada19ed7995b04ef4bd41c179
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148626"
---
# <a name="expression-trees-summary"></a><span data-ttu-id="b392d-103">Souhrn stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="b392d-103">Expression Trees Summary</span></span>

[<span data-ttu-id="b392d-104">Předchozí – Překlad výrazů</span><span class="sxs-lookup"><span data-stu-id="b392d-104">Previous -- Translating Expressions</span></span>](expression-trees-translating.md)

<span data-ttu-id="b392d-105">V této sérii, jste viděli, jak můžete *stromů výrazů* k vytvoření dynamické programy, které interpretovat kód jako data a vytvářet nové funkce založené na tento kód.</span><span class="sxs-lookup"><span data-stu-id="b392d-105">In this series, you've seen how you can use *expression trees* to create dynamic programs that interpret code as data and build new functionality based on that code.</span></span>

<span data-ttu-id="b392d-106">Můžete prozkoumat stromů výrazů k porozumění záměru algoritmus.</span><span class="sxs-lookup"><span data-stu-id="b392d-106">You can examine expression trees to understand the intent of an algorithm.</span></span> <span data-ttu-id="b392d-107">Nelze jenom zkontrolujte, že kód.</span><span class="sxs-lookup"><span data-stu-id="b392d-107">You can not only examine that code.</span></span> <span data-ttu-id="b392d-108">Můžete vytvářet nové stromů výrazů, které představují upravené verze původního kódu.</span><span class="sxs-lookup"><span data-stu-id="b392d-108">You can build new expression trees that represent modified versions of the original code.</span></span>

<span data-ttu-id="b392d-109">Můžete také použití stromů výrazů se podívat na algoritmus a převede tento algoritmus na jiný jazyk nebo prostředí.</span><span class="sxs-lookup"><span data-stu-id="b392d-109">You can also use expression trees to look at an algorithm, and translate that algorithm into another language or environment.</span></span> 

## <a name="limitations"></a><span data-ttu-id="b392d-110">Omezení</span><span class="sxs-lookup"><span data-stu-id="b392d-110">Limitations</span></span>

<span data-ttu-id="b392d-111">Existují některé novější C# prvky jazyka, které není převedou kontejneru stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="b392d-111">There are some newer C# language elements that don't translate well into expression trees.</span></span> <span data-ttu-id="b392d-112">Stromy výrazů nesmí obsahovat `await` výrazy, nebo `async` výrazů lambda.</span><span class="sxs-lookup"><span data-stu-id="b392d-112">Expression trees cannot contain `await` expressions, or `async` lambda expressions.</span></span> <span data-ttu-id="b392d-113">Mnoho z funkcí přidaných do C# verze 6, nejsou zobrazeny přesně napsané ve stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="b392d-113">Many of the features added in the C# 6 release don't appear exactly as written in expression trees.</span></span> <span data-ttu-id="b392d-114">Místo toho novější funkce se zveřejní ve stromech výrazů v ekvivalentní, starší syntaxi.</span><span class="sxs-lookup"><span data-stu-id="b392d-114">Instead, newer features will be exposed in expressions trees in the equivalent, earlier syntax.</span></span> <span data-ttu-id="b392d-115">Toto video asi co nejvíce z omezení jak si možná myslíte.</span><span class="sxs-lookup"><span data-stu-id="b392d-115">This may not be as much of a limitation as you might think.</span></span> <span data-ttu-id="b392d-116">Ve skutečnosti znamená, že váš kód, který stromů výrazů interpretuje bude pravděpodobně stále fungovat stejně při zavedení nových funkcí jazyka.</span><span class="sxs-lookup"><span data-stu-id="b392d-116">In fact, it means that your code that interprets expression trees will likely still work the same when new language features are introduced.</span></span>

<span data-ttu-id="b392d-117">I přes tato omezení stromů výrazů umožňují vytvářet dynamické algoritmy, které využívají interpretace a upravovat kód, který je reprezentován jako datová struktura.</span><span class="sxs-lookup"><span data-stu-id="b392d-117">Even with these limitations, expression trees do enable you to create dynamic algorithms that rely on interpreting and modifying code that is represented as a data structure.</span></span> <span data-ttu-id="b392d-118">Je výkonný nástroj, a je jednou z funkcí ekosystému .NET, která umožňuje rozsáhlé knihovny, jako je například rozhraní Entity Framework provedete, co dělají.</span><span class="sxs-lookup"><span data-stu-id="b392d-118">It's a powerful tool, and it's one of the features of the .NET ecosystem that enables rich libraries such as Entity Framework to accomplish what they do.</span></span>
