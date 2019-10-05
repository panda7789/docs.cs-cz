---
title: Vytvoření aplikace seznam s odpovídajícími hrami s Infer.NET a pravděpodobnostní programováním
description: Naučte se používat programování pravděpodobnostní s Infer.NET k vytvoření aplikace seznamu her pro zápasu v závislosti na zjednodušené verzi TrueSkill.
ms.date: 05/06/2019
ms.custom: mvc,how-to
ms.openlocfilehash: f6f91aecfe7fdeffb7e8913309046c7942ecbab7
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2019
ms.locfileid: "71957216"
---
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a><span data-ttu-id="1e862-103">Vytvoření aplikace seznam s odpovídajícími hrami s Infer.NET a pravděpodobnostní programováním</span><span class="sxs-lookup"><span data-stu-id="1e862-103">Create a game match up list app with Infer.NET and probabilistic programming</span></span>

<span data-ttu-id="1e862-104">Tato příručka vás seznámí s programováním v pravděpodobnostní pomocí Infer.NET.</span><span class="sxs-lookup"><span data-stu-id="1e862-104">This how-to guide teaches you about probabilistic programming using Infer.NET.</span></span> <span data-ttu-id="1e862-105">Programování pravděpodobnostní je přístup strojového učení, kde se vlastní modely vyjadřují jako počítačové programy.</span><span class="sxs-lookup"><span data-stu-id="1e862-105">Probabilistic programming is a machine learning approach where custom models are expressed as computer programs.</span></span> <span data-ttu-id="1e862-106">Umožňuje začlenit znalostní bázi domény v modelech a díky tomu může systém Machine Learning lépe interpretovat.</span><span class="sxs-lookup"><span data-stu-id="1e862-106">It allows for incorporating domain knowledge in the models and makes the machine learning system more interpretable.</span></span> <span data-ttu-id="1e862-107">Podporuje také online odvozování – proces učení se zadoručením nových dat.</span><span class="sxs-lookup"><span data-stu-id="1e862-107">It also supports online inference – the process of learning as new data arrives.</span></span> <span data-ttu-id="1e862-108">Infer.NET se používá v různých produktech Microsoftu v Azure, Xbox a Bingu.</span><span class="sxs-lookup"><span data-stu-id="1e862-108">Infer.NET is used in various products at Microsoft in Azure, Xbox, and Bing.</span></span>

## <a name="what-is-probabilistic-programming"></a><span data-ttu-id="1e862-109">Co je pravděpodobnostní programování?</span><span class="sxs-lookup"><span data-stu-id="1e862-109">What is probabilistic programming?</span></span>

<span data-ttu-id="1e862-110">Programování pravděpodobnostní vám umožňuje vytvářet statistické modely reálných procesů.</span><span class="sxs-lookup"><span data-stu-id="1e862-110">Probabilistic programming allows you to create statistical models of real-world processes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1e862-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1e862-111">Prerequisites</span></span>

- <span data-ttu-id="1e862-112">Nastavení místního vývojového prostředí</span><span class="sxs-lookup"><span data-stu-id="1e862-112">Local development environment setup</span></span>

  <span data-ttu-id="1e862-113">Tato průvodce vám očekává, že máte počítač, který můžete použít pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="1e862-113">This how-to guide expects you to have a machine you can use for development.</span></span> <span data-ttu-id="1e862-114">Kurz rozhraní .NET [Hello World v 10 minutách](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v MacOS, Windows nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="1e862-114">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on macOS, Windows, or Linux.</span></span>

## <a name="create-your-app"></a><span data-ttu-id="1e862-115">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="1e862-115">Create your app</span></span>

1. <span data-ttu-id="1e862-116">Otevřete nový příkazový řádek a spusťte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="1e862-116">Open a new command prompt and run the following commands:</span></span>

```dotnetcli
dotnet new console -o myApp
cd myApp
```

<span data-ttu-id="1e862-117">Příkaz `dotnet` vytvoří aplikaci `new` typu `console`.</span><span class="sxs-lookup"><span data-stu-id="1e862-117">The `dotnet` command creates a `new` application of type `console`.</span></span> <span data-ttu-id="1e862-118">Parametr `-o` vytvoří adresář s názvem `myApp`, kde je vaše aplikace uložená, a naplní ji požadovanými soubory.</span><span class="sxs-lookup"><span data-stu-id="1e862-118">The `-o` parameter creates a directory named `myApp` where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="1e862-119">Příkaz `cd myApp` vloží do nově vytvořeného adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="1e862-119">The `cd myApp` command puts you into the newly created app directory.</span></span>

## <a name="install-infernet-package"></a><span data-ttu-id="1e862-120">Nainstalovat balíček Infer.NET</span><span class="sxs-lookup"><span data-stu-id="1e862-120">Install Infer.NET package</span></span>

<span data-ttu-id="1e862-121">Chcete-li použít Infer.NET, je třeba nainstalovat balíček `Microsoft.ML.Probabilistic.Compiler`.</span><span class="sxs-lookup"><span data-stu-id="1e862-121">To use Infer.NET, you need to install the `Microsoft.ML.Probabilistic.Compiler` package.</span></span> <span data-ttu-id="1e862-122">Na příkazovém řádku spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="1e862-122">In your command prompt, run the following command:</span></span>

```dotnetcli
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a><span data-ttu-id="1e862-123">Návrh modelu</span><span class="sxs-lookup"><span data-stu-id="1e862-123">Design your model</span></span>

<span data-ttu-id="1e862-124">Vzorový příklad používá v sadě Office shodu tabulky tenis nebo Foosball.</span><span class="sxs-lookup"><span data-stu-id="1e862-124">The example sample uses table tennis or foosball matches played in the office.</span></span> <span data-ttu-id="1e862-125">Máte účastníky a výsledek každé shody.</span><span class="sxs-lookup"><span data-stu-id="1e862-125">You have the participants and outcome of each match.</span></span>  <span data-ttu-id="1e862-126">Chcete odvodit dovednosti přehrávače od těchto dat.</span><span class="sxs-lookup"><span data-stu-id="1e862-126">You want to infer the player's skills from this data.</span></span> <span data-ttu-id="1e862-127">Předpokládejme, že každý hráč má obvykle distribuovanou latentní dovednost a jejich odpovídající výkon je tato dovednostní verze.</span><span class="sxs-lookup"><span data-stu-id="1e862-127">Assume that each player has a normally distributed latent skill and their given match performance is a noisy version of this skill.</span></span> <span data-ttu-id="1e862-128">Data omezí výkon vítěze tak, aby byla větší než výkon loser.</span><span class="sxs-lookup"><span data-stu-id="1e862-128">The data constrains the winner’s performance to be greater than the loser’s performance.</span></span> <span data-ttu-id="1e862-129">Toto je zjednodušená verze oblíbeného modelu [TrueSkill](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/) , která také podporuje týmy, kreslení a další rozšíření.</span><span class="sxs-lookup"><span data-stu-id="1e862-129">This is a simplified version of the popular [TrueSkill](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/) model, which also supports teams, draws, and other extensions.</span></span> <span data-ttu-id="1e862-130">[Pokročilá verze](https://www.microsoft.com/en-us/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) tohoto modelu se používá pro Matchmaking v nejlepším prodeji názvů her Halo a ozubeného kolaci války.</span><span class="sxs-lookup"><span data-stu-id="1e862-130">An [advanced version](https://www.microsoft.com/en-us/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) of this model is used for matchmaking in the best-selling game titles Halo and Gears of War.</span></span>

<span data-ttu-id="1e862-131">Musíte uvést, jaké dovednosti v přehrávači jsou společně s jejich odchylkou – míra nejistoty v rámci dovedností.</span><span class="sxs-lookup"><span data-stu-id="1e862-131">You need to list the inferred player skills, alongside with their variance – the measure of uncertainty around the skills.</span></span>

<span data-ttu-id="1e862-132">*Ukázková data výsledků her*</span><span class="sxs-lookup"><span data-stu-id="1e862-132">*Game result sample data*</span></span>

<span data-ttu-id="1e862-133">Lovu</span><span class="sxs-lookup"><span data-stu-id="1e862-133">Game</span></span> |<span data-ttu-id="1e862-134">Replik</span><span class="sxs-lookup"><span data-stu-id="1e862-134">Winner</span></span> | <span data-ttu-id="1e862-135">Loser</span><span class="sxs-lookup"><span data-stu-id="1e862-135">Loser</span></span>
---------|----------|---------
 <span data-ttu-id="1e862-136">první</span><span class="sxs-lookup"><span data-stu-id="1e862-136">1</span></span> | <span data-ttu-id="1e862-137">Přehrávač 0</span><span class="sxs-lookup"><span data-stu-id="1e862-137">Player 0</span></span> | <span data-ttu-id="1e862-138">Hráč 1</span><span class="sxs-lookup"><span data-stu-id="1e862-138">Player 1</span></span>
 <span data-ttu-id="1e862-139">odst</span><span class="sxs-lookup"><span data-stu-id="1e862-139">2</span></span> | <span data-ttu-id="1e862-140">Přehrávač 0</span><span class="sxs-lookup"><span data-stu-id="1e862-140">Player 0</span></span> | <span data-ttu-id="1e862-141">Hráč 3</span><span class="sxs-lookup"><span data-stu-id="1e862-141">Player 3</span></span>
 <span data-ttu-id="1e862-142">3</span><span class="sxs-lookup"><span data-stu-id="1e862-142">3</span></span> | <span data-ttu-id="1e862-143">Přehrávač 0</span><span class="sxs-lookup"><span data-stu-id="1e862-143">Player 0</span></span> | <span data-ttu-id="1e862-144">Hráč 4</span><span class="sxs-lookup"><span data-stu-id="1e862-144">Player 4</span></span>
 <span data-ttu-id="1e862-145">4</span><span class="sxs-lookup"><span data-stu-id="1e862-145">4</span></span> | <span data-ttu-id="1e862-146">Hráč 1</span><span class="sxs-lookup"><span data-stu-id="1e862-146">Player 1</span></span> | <span data-ttu-id="1e862-147">Hráč 2</span><span class="sxs-lookup"><span data-stu-id="1e862-147">Player 2</span></span>
 <span data-ttu-id="1e862-148">5</span><span class="sxs-lookup"><span data-stu-id="1e862-148">5</span></span> | <span data-ttu-id="1e862-149">Hráč 3</span><span class="sxs-lookup"><span data-stu-id="1e862-149">Player 3</span></span> | <span data-ttu-id="1e862-150">Hráč 1</span><span class="sxs-lookup"><span data-stu-id="1e862-150">Player 1</span></span>
 <span data-ttu-id="1e862-151">6</span><span class="sxs-lookup"><span data-stu-id="1e862-151">6</span></span> | <span data-ttu-id="1e862-152">Hráč 4</span><span class="sxs-lookup"><span data-stu-id="1e862-152">Player 4</span></span> | <span data-ttu-id="1e862-153">Hráč 2</span><span class="sxs-lookup"><span data-stu-id="1e862-153">Player 2</span></span>

<span data-ttu-id="1e862-154">Podíváme se na vzorová data a Všimněte si, že hráči 3 a 4 mají jednu ze všech výher a jednu ztrátu.</span><span class="sxs-lookup"><span data-stu-id="1e862-154">With a closer look at the sample data, you’ll notice that players 3 and 4 both have one win and one loss.</span></span> <span data-ttu-id="1e862-155">Pojďme se podívat, jak pořadí vypadá pomocí pravděpodobnostní programování.</span><span class="sxs-lookup"><span data-stu-id="1e862-155">Let's see what the rankings look like using probabilistic programming.</span></span> <span data-ttu-id="1e862-156">Všimněte si také, že je přehrávač nulový, protože v seznamech pro nás, které jsou v souladu s více kancelářemi, je nula.</span><span class="sxs-lookup"><span data-stu-id="1e862-156">Notice also there is a player zero because even office match up lists are zero based to us developers.</span></span>

## <a name="write-some-code"></a><span data-ttu-id="1e862-157">Napsat nějaký kód</span><span class="sxs-lookup"><span data-stu-id="1e862-157">Write some code</span></span>

<span data-ttu-id="1e862-158">Model byl navržený tak, jak ho vyjádřit jako pravděpodobnostní program pomocí rozhraní API pro modelování Infer.NET.</span><span class="sxs-lookup"><span data-stu-id="1e862-158">Having designed the model, it’s time to express it as a probabilistic program using the Infer.NET modeling API.</span></span> <span data-ttu-id="1e862-159">V oblíbeném textovém editoru otevřete `Program.cs` a nahraďte jeho obsah následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="1e862-159">Open `Program.cs` in your favorite text editor and replace all of its contents with the following code:</span></span>

```csharp
namespace myApp

{
    using System;
    using System.Linq;
    using Microsoft.ML.Probabilistic;
    using Microsoft.ML.Probabilistic.Distributions;
    using Microsoft.ML.Probabilistic.Models;

    class Program
    {

        static void Main(string[] args)
        {
            // The winner and loser in each of 6 samples games
            var winnerData = new[] { 0, 0, 0, 1, 3, 4 };
            var loserData = new[] { 1, 3, 4, 2, 1, 2 };

            // Define the statistical model as a probabilistic program
            var game = new Range(winnerData.Length);
            var player = new Range(winnerData.Concat(loserData).Max() + 1);
            var playerSkills = Variable.Array<double>(player);
            playerSkills[player] = Variable.GaussianFromMeanAndVariance(6, 9).ForEach(player);

            var winners = Variable.Array<int>(game);
            var losers = Variable.Array<int>(game);

            using (Variable.ForEach(game))
            {
                // The player performance is a noisy version of their skill
                var winnerPerformance = Variable.GaussianFromMeanAndVariance(playerSkills[winners[game]], 1.0);
                var loserPerformance = Variable.GaussianFromMeanAndVariance(playerSkills[losers[game]], 1.0);

                // The winner performed better in this game
                Variable.ConstrainTrue(winnerPerformance > loserPerformance);
            }

            // Attach the data to the model
            winners.ObservedValue = winnerData;
            losers.ObservedValue = loserData;

            // Run inference
            var inferenceEngine = new InferenceEngine();
            var inferredSkills = inferenceEngine.Infer<Gaussian[]>(playerSkills);

            // The inferred skills are uncertain, which is captured in their variance
            var orderedPlayerSkills = inferredSkills
               .Select((s, i) => new { Player = i, Skill = s })
               .OrderByDescending(ps => ps.Skill.GetMean());

            foreach (var playerSkill in orderedPlayerSkills)
            {
                Console.WriteLine($"Player {playerSkill.Player} skill: {playerSkill.Skill}");
            }
        }
    }
}
```

## <a name="run-your-app"></a><span data-ttu-id="1e862-160">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="1e862-160">Run your app</span></span>

<span data-ttu-id="1e862-161">Na příkazovém řádku spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="1e862-161">In your command prompt, run the following command:</span></span>

```dotnetcli
dotnet run
```

## <a name="results"></a><span data-ttu-id="1e862-162">Výsledky</span><span class="sxs-lookup"><span data-stu-id="1e862-162">Results</span></span>

<span data-ttu-id="1e862-163">Výsledky by měly být podobné následujícímu:</span><span class="sxs-lookup"><span data-stu-id="1e862-163">Your results should be similar to the following:</span></span>

```console
Compiling model...done.
Iterating:
.........|.........|.........|.........|.........| 50
Player 0 skill: Gaussian(9.517, 3.926)
Player 3 skill: Gaussian(6.834, 3.892)
Player 4 skill: Gaussian(6.054, 4.731)
Player 1 skill: Gaussian(4.955, 3.503)
Player 2 skill: Gaussian(2.639, 4.288)
```

<span data-ttu-id="1e862-164">Ve výsledcích si všimněte, že hráč 3 rozhodne o něco vyšším než hráč 4 podle našeho modelu.</span><span class="sxs-lookup"><span data-stu-id="1e862-164">In the results, notice that player 3 ranks slightly higher than player 4 according to our model.</span></span> <span data-ttu-id="1e862-165">Důvodem je to, že Victory of Player 3 over Player 1 je důležitější než Victory Player 4 přes Player 2 – Poznámka: Player 1 Beats Player 2.</span><span class="sxs-lookup"><span data-stu-id="1e862-165">That’s because the victory of player 3 over player 1 is more significant than the victory of player 4 over player 2 – note that player 1 beats player 2.</span></span> <span data-ttu-id="1e862-166">Přehrávač 0 je celkový Champ!</span><span class="sxs-lookup"><span data-stu-id="1e862-166">Player 0 is the overall champ!</span></span>

## <a name="keep-learning"></a><span data-ttu-id="1e862-167">Průběžné učení</span><span class="sxs-lookup"><span data-stu-id="1e862-167">Keep learning</span></span>

<span data-ttu-id="1e862-168">Návrh statistických modelů je dovedností sám o sobě.</span><span class="sxs-lookup"><span data-stu-id="1e862-168">Designing statistical models is a skill on its own.</span></span> <span data-ttu-id="1e862-169">Tým Microsoft Research Cambridge napsal [bezplatnou online knihu](http://mbmlbook.com/), která poskytuje mírné představení tohoto článku.</span><span class="sxs-lookup"><span data-stu-id="1e862-169">The Microsoft Research Cambridge team has written a [free online book](http://mbmlbook.com/), which gives a gentle introduction to the article.</span></span> <span data-ttu-id="1e862-170">Kapitola 3 této knihy pokrývá model TrueSkill podrobněji.</span><span class="sxs-lookup"><span data-stu-id="1e862-170">Chapter 3 of this book covers the TrueSkill model in more detail.</span></span> <span data-ttu-id="1e862-171">Jakmile máte model, můžete ho transformovat na kód pomocí [obsáhlé dokumentace](https://dotnet.github.io/infer/) na webu Infer.NET.</span><span class="sxs-lookup"><span data-stu-id="1e862-171">Once you have a model in mind, you can transform it into code using the [extensive documentation](https://dotnet.github.io/infer/) on the Infer.NET website.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1e862-172">Další kroky</span><span class="sxs-lookup"><span data-stu-id="1e862-172">Next steps</span></span>

<span data-ttu-id="1e862-173">Podívejte se na úložiště GitHub Infer.NET a pokračujte v učení a Najděte další ukázky.</span><span class="sxs-lookup"><span data-stu-id="1e862-173">Check out the Infer.NET GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="1e862-174">dotnet/odvodit úložiště GitHub</span><span class="sxs-lookup"><span data-stu-id="1e862-174">dotnet/infer GitHub repository</span></span>](https://github.com/dotnet/infer)
