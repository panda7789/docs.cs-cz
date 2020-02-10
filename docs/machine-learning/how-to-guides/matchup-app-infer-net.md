---
title: Infer.NET hra – párování aplikací – pravděpodobnostní programování
description: Naučte se používat programování v pravděpodobnostní s Infer.NET k vytvoření rozhodné aplikace seznamu pro porovnávání her na základě zjednodušené verze TrueSkill.
ms.date: 01/30/2020
ms.custom: mvc,how-to
ms.openlocfilehash: 8e489d61c5e6cca53ba12b13fddd0b73c7f85ef9
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092600"
---
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a><span data-ttu-id="9088d-103">Vytvoření aplikace seznam s odpovídajícími hrami s Infer.NET a pravděpodobnostní programováním</span><span class="sxs-lookup"><span data-stu-id="9088d-103">Create a game match up list app with Infer.NET and probabilistic programming</span></span>

<span data-ttu-id="9088d-104">Tato příručka vás seznámí s programováním v pravděpodobnostní pomocí Infer.NET.</span><span class="sxs-lookup"><span data-stu-id="9088d-104">This how-to guide teaches you about probabilistic programming using Infer.NET.</span></span> <span data-ttu-id="9088d-105">Programování pravděpodobnostní je přístup strojového učení, kde se vlastní modely vyjadřují jako počítačové programy.</span><span class="sxs-lookup"><span data-stu-id="9088d-105">Probabilistic programming is a machine learning approach where custom models are expressed as computer programs.</span></span> <span data-ttu-id="9088d-106">Umožňuje začlenit znalostní bázi domény v modelech a díky tomu může systém Machine Learning lépe interpretovat.</span><span class="sxs-lookup"><span data-stu-id="9088d-106">It allows for incorporating domain knowledge in the models and makes the machine learning system more interpretable.</span></span> <span data-ttu-id="9088d-107">Podporuje také online odvozování – proces učení se zadoručením nových dat.</span><span class="sxs-lookup"><span data-stu-id="9088d-107">It also supports online inference – the process of learning as new data arrives.</span></span> <span data-ttu-id="9088d-108">Infer.NET se používá v různých produktech Microsoftu v Azure, Xbox a Bingu.</span><span class="sxs-lookup"><span data-stu-id="9088d-108">Infer.NET is used in various products at Microsoft in Azure, Xbox, and Bing.</span></span>

## <a name="what-is-probabilistic-programming"></a><span data-ttu-id="9088d-109">Co je pravděpodobnostní programování?</span><span class="sxs-lookup"><span data-stu-id="9088d-109">What is probabilistic programming?</span></span>

<span data-ttu-id="9088d-110">Programování pravděpodobnostní vám umožňuje vytvářet statistické modely reálných procesů.</span><span class="sxs-lookup"><span data-stu-id="9088d-110">Probabilistic programming allows you to create statistical models of real-world processes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9088d-111">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="9088d-111">Prerequisites</span></span>

- <span data-ttu-id="9088d-112">Nastavení místního vývojového prostředí</span><span class="sxs-lookup"><span data-stu-id="9088d-112">Local development environment setup</span></span>

  <span data-ttu-id="9088d-113">Tato průvodce vám očekává, že máte počítač, který můžete použít pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="9088d-113">This how-to guide expects you to have a machine you can use for development.</span></span> <span data-ttu-id="9088d-114">Kurz rozhraní .NET [Hello World v 10 minutách](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v MacOS, Windows nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="9088d-114">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on macOS, Windows, or Linux.</span></span>

## <a name="create-your-app"></a><span data-ttu-id="9088d-115">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="9088d-115">Create your app</span></span>

1. <span data-ttu-id="9088d-116">Otevřete nový příkazový řádek a spusťte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="9088d-116">Open a new command prompt and run the following commands:</span></span>

```dotnetcli
dotnet new console -o myApp
cd myApp
```

<span data-ttu-id="9088d-117">Příkaz `dotnet` vytvoří `new` aplikace typu `console`.</span><span class="sxs-lookup"><span data-stu-id="9088d-117">The `dotnet` command creates a `new` application of type `console`.</span></span> <span data-ttu-id="9088d-118">Parametr `-o` vytvoří adresář s názvem `myApp`, kde je vaše aplikace uložená, a naplní ji požadovanými soubory.</span><span class="sxs-lookup"><span data-stu-id="9088d-118">The `-o` parameter creates a directory named `myApp` where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="9088d-119">Příkaz `cd myApp` vloží do nově vytvořeného adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="9088d-119">The `cd myApp` command puts you into the newly created app directory.</span></span>

## <a name="install-infernet-package"></a><span data-ttu-id="9088d-120">Nainstalovat balíček Infer.NET</span><span class="sxs-lookup"><span data-stu-id="9088d-120">Install Infer.NET package</span></span>

<span data-ttu-id="9088d-121">Pokud chcete používat Infer.NET, musíte nainstalovat balíček `Microsoft.ML.Probabilistic.Compiler`.</span><span class="sxs-lookup"><span data-stu-id="9088d-121">To use Infer.NET, you need to install the `Microsoft.ML.Probabilistic.Compiler` package.</span></span> <span data-ttu-id="9088d-122">Na příkazovém řádku spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="9088d-122">In your command prompt, run the following command:</span></span>

```dotnetcli
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a><span data-ttu-id="9088d-123">Návrh modelu</span><span class="sxs-lookup"><span data-stu-id="9088d-123">Design your model</span></span>

<span data-ttu-id="9088d-124">Vzorový příklad používá v sadě Office shodu tabulky tenis nebo Foosball.</span><span class="sxs-lookup"><span data-stu-id="9088d-124">The example sample uses table tennis or foosball matches played in the office.</span></span> <span data-ttu-id="9088d-125">Máte účastníky a výsledek každé shody.</span><span class="sxs-lookup"><span data-stu-id="9088d-125">You have the participants and outcome of each match.</span></span>  <span data-ttu-id="9088d-126">Chcete odvodit dovednosti přehrávače od těchto dat.</span><span class="sxs-lookup"><span data-stu-id="9088d-126">You want to infer the player's skills from this data.</span></span> <span data-ttu-id="9088d-127">Předpokládejme, že každý hráč má obvykle distribuovanou latentní dovednost a jejich odpovídající výkon je tato dovednostní verze.</span><span class="sxs-lookup"><span data-stu-id="9088d-127">Assume that each player has a normally distributed latent skill and their given match performance is a noisy version of this skill.</span></span> <span data-ttu-id="9088d-128">Data omezí výkon vítěze tak, aby byla větší než výkon loser.</span><span class="sxs-lookup"><span data-stu-id="9088d-128">The data constrains the winner’s performance to be greater than the loser’s performance.</span></span> <span data-ttu-id="9088d-129">Toto je zjednodušená verze oblíbeného modelu [TrueSkill](https://www.microsoft.com/research/project/trueskill-ranking-system/) , která také podporuje týmy, kreslení a další rozšíření.</span><span class="sxs-lookup"><span data-stu-id="9088d-129">This is a simplified version of the popular [TrueSkill](https://www.microsoft.com/research/project/trueskill-ranking-system/) model, which also supports teams, draws, and other extensions.</span></span> <span data-ttu-id="9088d-130">[Pokročilá verze](https://www.microsoft.com/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) tohoto modelu se používá pro Matchmaking v nejlepším prodeji názvů her Halo a ozubeného kolaci války.</span><span class="sxs-lookup"><span data-stu-id="9088d-130">An [advanced version](https://www.microsoft.com/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) of this model is used for matchmaking in the best-selling game titles Halo and Gears of War.</span></span>

<span data-ttu-id="9088d-131">Musíte uvést, jaké dovednosti v přehrávači jsou společně s jejich odchylkou – míra nejistoty v rámci dovedností.</span><span class="sxs-lookup"><span data-stu-id="9088d-131">You need to list the inferred player skills, alongside with their variance – the measure of uncertainty around the skills.</span></span>

<span data-ttu-id="9088d-132">*Ukázková data výsledků her*</span><span class="sxs-lookup"><span data-stu-id="9088d-132">*Game result sample data*</span></span>

<span data-ttu-id="9088d-133">Hra</span><span class="sxs-lookup"><span data-stu-id="9088d-133">Game</span></span> |<span data-ttu-id="9088d-134">Replik</span><span class="sxs-lookup"><span data-stu-id="9088d-134">Winner</span></span> | <span data-ttu-id="9088d-135">Loser</span><span class="sxs-lookup"><span data-stu-id="9088d-135">Loser</span></span>
---------|----------|---------
 <span data-ttu-id="9088d-136">1</span><span class="sxs-lookup"><span data-stu-id="9088d-136">1</span></span> | <span data-ttu-id="9088d-137">Přehrávač 0</span><span class="sxs-lookup"><span data-stu-id="9088d-137">Player 0</span></span> | <span data-ttu-id="9088d-138">Hráč 1</span><span class="sxs-lookup"><span data-stu-id="9088d-138">Player 1</span></span>
 <span data-ttu-id="9088d-139">2</span><span class="sxs-lookup"><span data-stu-id="9088d-139">2</span></span> | <span data-ttu-id="9088d-140">Přehrávač 0</span><span class="sxs-lookup"><span data-stu-id="9088d-140">Player 0</span></span> | <span data-ttu-id="9088d-141">Hráč 3</span><span class="sxs-lookup"><span data-stu-id="9088d-141">Player 3</span></span>
 <span data-ttu-id="9088d-142">3</span><span class="sxs-lookup"><span data-stu-id="9088d-142">3</span></span> | <span data-ttu-id="9088d-143">Přehrávač 0</span><span class="sxs-lookup"><span data-stu-id="9088d-143">Player 0</span></span> | <span data-ttu-id="9088d-144">Hráč 4</span><span class="sxs-lookup"><span data-stu-id="9088d-144">Player 4</span></span>
 <span data-ttu-id="9088d-145">4</span><span class="sxs-lookup"><span data-stu-id="9088d-145">4</span></span> | <span data-ttu-id="9088d-146">Hráč 1</span><span class="sxs-lookup"><span data-stu-id="9088d-146">Player 1</span></span> | <span data-ttu-id="9088d-147">Hráč 2</span><span class="sxs-lookup"><span data-stu-id="9088d-147">Player 2</span></span>
 <span data-ttu-id="9088d-148">5</span><span class="sxs-lookup"><span data-stu-id="9088d-148">5</span></span> | <span data-ttu-id="9088d-149">Hráč 3</span><span class="sxs-lookup"><span data-stu-id="9088d-149">Player 3</span></span> | <span data-ttu-id="9088d-150">Hráč 1</span><span class="sxs-lookup"><span data-stu-id="9088d-150">Player 1</span></span>
 <span data-ttu-id="9088d-151">6</span><span class="sxs-lookup"><span data-stu-id="9088d-151">6</span></span> | <span data-ttu-id="9088d-152">Hráč 4</span><span class="sxs-lookup"><span data-stu-id="9088d-152">Player 4</span></span> | <span data-ttu-id="9088d-153">Hráč 2</span><span class="sxs-lookup"><span data-stu-id="9088d-153">Player 2</span></span>

<span data-ttu-id="9088d-154">Podíváme se na vzorová data a Všimněte si, že hráči 3 a 4 mají jednu ze všech výher a jednu ztrátu.</span><span class="sxs-lookup"><span data-stu-id="9088d-154">With a closer look at the sample data, you’ll notice that players 3 and 4 both have one win and one loss.</span></span> <span data-ttu-id="9088d-155">Pojďme se podívat, jak pořadí vypadá pomocí pravděpodobnostní programování.</span><span class="sxs-lookup"><span data-stu-id="9088d-155">Let's see what the rankings look like using probabilistic programming.</span></span> <span data-ttu-id="9088d-156">Všimněte si také, že je přehrávač nulový, protože v seznamech pro nás, které jsou v souladu s více kancelářemi, je nula.</span><span class="sxs-lookup"><span data-stu-id="9088d-156">Notice also there is a player zero because even office match up lists are zero based to us developers.</span></span>

## <a name="write-some-code"></a><span data-ttu-id="9088d-157">Napsat nějaký kód</span><span class="sxs-lookup"><span data-stu-id="9088d-157">Write some code</span></span>

<span data-ttu-id="9088d-158">Model byl navržený tak, jak ho vyjádřit jako pravděpodobnostní program pomocí rozhraní API pro modelování Infer.NET.</span><span class="sxs-lookup"><span data-stu-id="9088d-158">Having designed the model, it’s time to express it as a probabilistic program using the Infer.NET modeling API.</span></span> <span data-ttu-id="9088d-159">Ve svém oblíbeném textovém editoru otevřete `Program.cs` a nahraďte jeho obsah následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="9088d-159">Open `Program.cs` in your favorite text editor and replace all of its contents with the following code:</span></span>

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

## <a name="run-your-app"></a><span data-ttu-id="9088d-160">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="9088d-160">Run your app</span></span>

<span data-ttu-id="9088d-161">Na příkazovém řádku spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="9088d-161">In your command prompt, run the following command:</span></span>

```dotnetcli
dotnet run
```

## <a name="results"></a><span data-ttu-id="9088d-162">Výsledky</span><span class="sxs-lookup"><span data-stu-id="9088d-162">Results</span></span>

<span data-ttu-id="9088d-163">Výsledky by měly být podobné následujícímu:</span><span class="sxs-lookup"><span data-stu-id="9088d-163">Your results should be similar to the following:</span></span>

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

<span data-ttu-id="9088d-164">Ve výsledcích si všimněte, že hráč 3 rozhodne o něco vyšším než hráč 4 podle našeho modelu.</span><span class="sxs-lookup"><span data-stu-id="9088d-164">In the results, notice that player 3 ranks slightly higher than player 4 according to our model.</span></span> <span data-ttu-id="9088d-165">Důvodem je to, že Victory of Player 3 over Player 1 je důležitější než Victory Player 4 přes Player 2 – Poznámka: Player 1 Beats Player 2.</span><span class="sxs-lookup"><span data-stu-id="9088d-165">That’s because the victory of player 3 over player 1 is more significant than the victory of player 4 over player 2 – note that player 1 beats player 2.</span></span> <span data-ttu-id="9088d-166">Přehrávač 0 je celkový Champ!</span><span class="sxs-lookup"><span data-stu-id="9088d-166">Player 0 is the overall champ!</span></span>

## <a name="keep-learning"></a><span data-ttu-id="9088d-167">Průběžné učení</span><span class="sxs-lookup"><span data-stu-id="9088d-167">Keep learning</span></span>

<span data-ttu-id="9088d-168">Návrh statistických modelů je dovedností sám o sobě.</span><span class="sxs-lookup"><span data-stu-id="9088d-168">Designing statistical models is a skill on its own.</span></span> <span data-ttu-id="9088d-169">Tým Microsoft Research Cambridge napsal [bezplatnou online knihu](http://mbmlbook.com/), která poskytuje mírné představení tohoto článku.</span><span class="sxs-lookup"><span data-stu-id="9088d-169">The Microsoft Research Cambridge team has written a [free online book](http://mbmlbook.com/), which gives a gentle introduction to the article.</span></span> <span data-ttu-id="9088d-170">Kapitola 3 této knihy pokrývá model TrueSkill podrobněji.</span><span class="sxs-lookup"><span data-stu-id="9088d-170">Chapter 3 of this book covers the TrueSkill model in more detail.</span></span> <span data-ttu-id="9088d-171">Jakmile máte model, můžete ho transformovat na kód pomocí [obsáhlé dokumentace](https://dotnet.github.io/infer/) na webu Infer.NET.</span><span class="sxs-lookup"><span data-stu-id="9088d-171">Once you have a model in mind, you can transform it into code using the [extensive documentation](https://dotnet.github.io/infer/) on the Infer.NET website.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9088d-172">Další kroky</span><span class="sxs-lookup"><span data-stu-id="9088d-172">Next steps</span></span>

<span data-ttu-id="9088d-173">Podívejte se na úložiště GitHub Infer.NET a pokračujte v učení a Najděte další ukázky.</span><span class="sxs-lookup"><span data-stu-id="9088d-173">Check out the Infer.NET GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="9088d-174">dotnet/odvodit úložiště GitHub</span><span class="sxs-lookup"><span data-stu-id="9088d-174">dotnet/infer GitHub repository</span></span>](https://github.com/dotnet/infer)
