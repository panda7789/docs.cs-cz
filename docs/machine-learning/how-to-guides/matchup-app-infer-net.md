---
title: Infer.NET herní match-up aplikace - pravděpodobnostní programování
description: Zjistěte, jak pomocí pravděpodobnostního programování s Infer.NET vytvořit aplikaci pro seznam herních zápasů založenou na zjednodušené verzi TrueSkill.
ms.date: 01/30/2020
ms.custom: mvc,how-to
ms.openlocfilehash: 8e489d61c5e6cca53ba12b13fddd0b73c7f85ef9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77092600"
---
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a><span data-ttu-id="3bda9-103">Vytvoření aplikace pro seznam her se Infer.NET a pravděpodobnostním programováním</span><span class="sxs-lookup"><span data-stu-id="3bda9-103">Create a game match up list app with Infer.NET and probabilistic programming</span></span>

<span data-ttu-id="3bda9-104">Tento návod vás naučí o pravděpodobnostním programování pomocí Infer.NET.</span><span class="sxs-lookup"><span data-stu-id="3bda9-104">This how-to guide teaches you about probabilistic programming using Infer.NET.</span></span> <span data-ttu-id="3bda9-105">Pravděpodobnostní programování je přístup strojového učení, kde jsou vlastní modely vyjádřeny jako počítačové programy.</span><span class="sxs-lookup"><span data-stu-id="3bda9-105">Probabilistic programming is a machine learning approach where custom models are expressed as computer programs.</span></span> <span data-ttu-id="3bda9-106">Umožňuje začlenit znalosti domény do modelů a činí systém strojového učení více interpretovatelným.</span><span class="sxs-lookup"><span data-stu-id="3bda9-106">It allows for incorporating domain knowledge in the models and makes the machine learning system more interpretable.</span></span> <span data-ttu-id="3bda9-107">Podporuje také on-line odvození - proces učení, jak přicházejí nová data.</span><span class="sxs-lookup"><span data-stu-id="3bda9-107">It also supports online inference – the process of learning as new data arrives.</span></span> <span data-ttu-id="3bda9-108">Infer.NET se používá v různých produktech společnosti Microsoft v Azure, Xboxu a Bingu.</span><span class="sxs-lookup"><span data-stu-id="3bda9-108">Infer.NET is used in various products at Microsoft in Azure, Xbox, and Bing.</span></span>

## <a name="what-is-probabilistic-programming"></a><span data-ttu-id="3bda9-109">Co je pravděpodobnostní programování?</span><span class="sxs-lookup"><span data-stu-id="3bda9-109">What is probabilistic programming?</span></span>

<span data-ttu-id="3bda9-110">Pravděpodobnostní programování umožňuje vytvářet statistické modely reálných procesů.</span><span class="sxs-lookup"><span data-stu-id="3bda9-110">Probabilistic programming allows you to create statistical models of real-world processes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3bda9-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3bda9-111">Prerequisites</span></span>

- <span data-ttu-id="3bda9-112">Nastavení prostředí místního rozvoje</span><span class="sxs-lookup"><span data-stu-id="3bda9-112">Local development environment setup</span></span>

  <span data-ttu-id="3bda9-113">Tento návod očekává, že budete mít stroj, který můžete použít pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="3bda9-113">This how-to guide expects you to have a machine you can use for development.</span></span> <span data-ttu-id="3bda9-114">Kurz .NET [Hello World za 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému macOS, Windows nebo Linuxu.</span><span class="sxs-lookup"><span data-stu-id="3bda9-114">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on macOS, Windows, or Linux.</span></span>

## <a name="create-your-app"></a><span data-ttu-id="3bda9-115">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="3bda9-115">Create your app</span></span>

1. <span data-ttu-id="3bda9-116">Otevřete nový příkazový řádek a spusťte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="3bda9-116">Open a new command prompt and run the following commands:</span></span>

```dotnetcli
dotnet new console -o myApp
cd myApp
```

<span data-ttu-id="3bda9-117">Příkaz `dotnet` vytvoří `new` aplikaci `console`typu .</span><span class="sxs-lookup"><span data-stu-id="3bda9-117">The `dotnet` command creates a `new` application of type `console`.</span></span> <span data-ttu-id="3bda9-118">Parametr `-o` vytvoří adresář `myApp` s názvem, kde je aplikace uložena, a naplní ho požadovanými soubory.</span><span class="sxs-lookup"><span data-stu-id="3bda9-118">The `-o` parameter creates a directory named `myApp` where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="3bda9-119">Příkaz `cd myApp` vás umístí do nově vytvořeného adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="3bda9-119">The `cd myApp` command puts you into the newly created app directory.</span></span>

## <a name="install-infernet-package"></a><span data-ttu-id="3bda9-120">Nainstalovat Infer.NET balíček</span><span class="sxs-lookup"><span data-stu-id="3bda9-120">Install Infer.NET package</span></span>

<span data-ttu-id="3bda9-121">Chcete-li použít Infer.NET, `Microsoft.ML.Probabilistic.Compiler` musíte nainstalovat balíček.</span><span class="sxs-lookup"><span data-stu-id="3bda9-121">To use Infer.NET, you need to install the `Microsoft.ML.Probabilistic.Compiler` package.</span></span> <span data-ttu-id="3bda9-122">V příkazovém řádku spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="3bda9-122">In your command prompt, run the following command:</span></span>

```dotnetcli
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a><span data-ttu-id="3bda9-123">Navrhněte svůj model</span><span class="sxs-lookup"><span data-stu-id="3bda9-123">Design your model</span></span>

<span data-ttu-id="3bda9-124">Ukázka příkladu používá stolní tenis nebo stolní fotbal zápasy hrané v kanceláři.</span><span class="sxs-lookup"><span data-stu-id="3bda9-124">The example sample uses table tennis or foosball matches played in the office.</span></span> <span data-ttu-id="3bda9-125">Máte účastníky a výsledek každého zápasu.</span><span class="sxs-lookup"><span data-stu-id="3bda9-125">You have the participants and outcome of each match.</span></span>  <span data-ttu-id="3bda9-126">Chcete-li odvodit dovednosti hráče z těchto dat.</span><span class="sxs-lookup"><span data-stu-id="3bda9-126">You want to infer the player's skills from this data.</span></span> <span data-ttu-id="3bda9-127">Předpokládejme, že každý hráč má normálně distribuované latentní dovednosti a jejich daný výkon zápasu je hlučná verze této dovednosti.</span><span class="sxs-lookup"><span data-stu-id="3bda9-127">Assume that each player has a normally distributed latent skill and their given match performance is a noisy version of this skill.</span></span> <span data-ttu-id="3bda9-128">Data omezuje výkon vítěze na výkon vyšší než výkon poraženého.</span><span class="sxs-lookup"><span data-stu-id="3bda9-128">The data constrains the winner’s performance to be greater than the loser’s performance.</span></span> <span data-ttu-id="3bda9-129">Toto je zjednodušená verze populárního modelu [TrueSkill,](https://www.microsoft.com/research/project/trueskill-ranking-system/) který také podporuje týmy, remízy a další rozšíření.</span><span class="sxs-lookup"><span data-stu-id="3bda9-129">This is a simplified version of the popular [TrueSkill](https://www.microsoft.com/research/project/trueskill-ranking-system/) model, which also supports teams, draws, and other extensions.</span></span> <span data-ttu-id="3bda9-130">[Pokročilá verze](https://www.microsoft.com/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) tohoto modelu se používá pro dohazování v nejprodávanějších herních titulech Halo a Gears of War.</span><span class="sxs-lookup"><span data-stu-id="3bda9-130">An [advanced version](https://www.microsoft.com/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) of this model is used for matchmaking in the best-selling game titles Halo and Gears of War.</span></span>

<span data-ttu-id="3bda9-131">Musíte uvést odvozené hráčské dovednosti, spolu s jejich rozptylem - míra nejistoty kolem dovedností.</span><span class="sxs-lookup"><span data-stu-id="3bda9-131">You need to list the inferred player skills, alongside with their variance – the measure of uncertainty around the skills.</span></span>

<span data-ttu-id="3bda9-132">*Ukázková data výsledků hry*</span><span class="sxs-lookup"><span data-stu-id="3bda9-132">*Game result sample data*</span></span>

<span data-ttu-id="3bda9-133">Herní</span><span class="sxs-lookup"><span data-stu-id="3bda9-133">Game</span></span> |<span data-ttu-id="3bda9-134">Vítěz</span><span class="sxs-lookup"><span data-stu-id="3bda9-134">Winner</span></span> | <span data-ttu-id="3bda9-135">Loser</span><span class="sxs-lookup"><span data-stu-id="3bda9-135">Loser</span></span>
---------|----------|---------
 <span data-ttu-id="3bda9-136">1</span><span class="sxs-lookup"><span data-stu-id="3bda9-136">1</span></span> | <span data-ttu-id="3bda9-137">Hráč 0</span><span class="sxs-lookup"><span data-stu-id="3bda9-137">Player 0</span></span> | <span data-ttu-id="3bda9-138">Hráč 1</span><span class="sxs-lookup"><span data-stu-id="3bda9-138">Player 1</span></span>
 <span data-ttu-id="3bda9-139">2</span><span class="sxs-lookup"><span data-stu-id="3bda9-139">2</span></span> | <span data-ttu-id="3bda9-140">Hráč 0</span><span class="sxs-lookup"><span data-stu-id="3bda9-140">Player 0</span></span> | <span data-ttu-id="3bda9-141">Hráč 3</span><span class="sxs-lookup"><span data-stu-id="3bda9-141">Player 3</span></span>
 <span data-ttu-id="3bda9-142">3</span><span class="sxs-lookup"><span data-stu-id="3bda9-142">3</span></span> | <span data-ttu-id="3bda9-143">Hráč 0</span><span class="sxs-lookup"><span data-stu-id="3bda9-143">Player 0</span></span> | <span data-ttu-id="3bda9-144">Hráč 4</span><span class="sxs-lookup"><span data-stu-id="3bda9-144">Player 4</span></span>
 <span data-ttu-id="3bda9-145">4</span><span class="sxs-lookup"><span data-stu-id="3bda9-145">4</span></span> | <span data-ttu-id="3bda9-146">Hráč 1</span><span class="sxs-lookup"><span data-stu-id="3bda9-146">Player 1</span></span> | <span data-ttu-id="3bda9-147">Hráč 2</span><span class="sxs-lookup"><span data-stu-id="3bda9-147">Player 2</span></span>
 <span data-ttu-id="3bda9-148">5</span><span class="sxs-lookup"><span data-stu-id="3bda9-148">5</span></span> | <span data-ttu-id="3bda9-149">Hráč 3</span><span class="sxs-lookup"><span data-stu-id="3bda9-149">Player 3</span></span> | <span data-ttu-id="3bda9-150">Hráč 1</span><span class="sxs-lookup"><span data-stu-id="3bda9-150">Player 1</span></span>
 <span data-ttu-id="3bda9-151">6</span><span class="sxs-lookup"><span data-stu-id="3bda9-151">6</span></span> | <span data-ttu-id="3bda9-152">Hráč 4</span><span class="sxs-lookup"><span data-stu-id="3bda9-152">Player 4</span></span> | <span data-ttu-id="3bda9-153">Hráč 2</span><span class="sxs-lookup"><span data-stu-id="3bda9-153">Player 2</span></span>

<span data-ttu-id="3bda9-154">Při bližším pohledu na ukázková data si všimnete, že hráči 3 a 4 mají jednu výhru a jednu ztrátu.</span><span class="sxs-lookup"><span data-stu-id="3bda9-154">With a closer look at the sample data, you’ll notice that players 3 and 4 both have one win and one loss.</span></span> <span data-ttu-id="3bda9-155">Podívejme se, jak vypadají žebříčky pomocí pravděpodobnostního programování.</span><span class="sxs-lookup"><span data-stu-id="3bda9-155">Let's see what the rankings look like using probabilistic programming.</span></span> <span data-ttu-id="3bda9-156">Všimněte si také, že je hráč nula, protože i kancelářské zápas y seznamy jsou nulové na základě nás vývojářů.</span><span class="sxs-lookup"><span data-stu-id="3bda9-156">Notice also there is a player zero because even office match up lists are zero based to us developers.</span></span>

## <a name="write-some-code"></a><span data-ttu-id="3bda9-157">Napsat nějaký kód</span><span class="sxs-lookup"><span data-stu-id="3bda9-157">Write some code</span></span>

<span data-ttu-id="3bda9-158">Po navržení modelu je čas vyjádřit jej jako pravděpodobnostní program pomocí rozhraní API pro modelování Infer.NET.</span><span class="sxs-lookup"><span data-stu-id="3bda9-158">Having designed the model, it’s time to express it as a probabilistic program using the Infer.NET modeling API.</span></span> <span data-ttu-id="3bda9-159">Otevřete `Program.cs` ve svém oblíbeném textovém editoru a nahraďte veškerý jeho obsah následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="3bda9-159">Open `Program.cs` in your favorite text editor and replace all of its contents with the following code:</span></span>

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

## <a name="run-your-app"></a><span data-ttu-id="3bda9-160">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="3bda9-160">Run your app</span></span>

<span data-ttu-id="3bda9-161">V příkazovém řádku spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="3bda9-161">In your command prompt, run the following command:</span></span>

```dotnetcli
dotnet run
```

## <a name="results"></a><span data-ttu-id="3bda9-162">Výsledky</span><span class="sxs-lookup"><span data-stu-id="3bda9-162">Results</span></span>

<span data-ttu-id="3bda9-163">Vaše výsledky by měly být podobné následujícímu:</span><span class="sxs-lookup"><span data-stu-id="3bda9-163">Your results should be similar to the following:</span></span>

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

<span data-ttu-id="3bda9-164">Ve výsledcích si všimněte, že hráč 3 je podle našeho modelu o něco vyšší než hráč 4.</span><span class="sxs-lookup"><span data-stu-id="3bda9-164">In the results, notice that player 3 ranks slightly higher than player 4 according to our model.</span></span> <span data-ttu-id="3bda9-165">To proto, že vítězství hráče 3 nad hráčem 1 je významnější než vítězství hráče 4 nad hráčem 2 - všimněte si, že hráč 1 porazí hráče 2.</span><span class="sxs-lookup"><span data-stu-id="3bda9-165">That’s because the victory of player 3 over player 1 is more significant than the victory of player 4 over player 2 – note that player 1 beats player 2.</span></span> <span data-ttu-id="3bda9-166">Hráč 0 je celkový šampion!</span><span class="sxs-lookup"><span data-stu-id="3bda9-166">Player 0 is the overall champ!</span></span>

## <a name="keep-learning"></a><span data-ttu-id="3bda9-167">Mějte učení</span><span class="sxs-lookup"><span data-stu-id="3bda9-167">Keep learning</span></span>

<span data-ttu-id="3bda9-168">Navrhování statistických modelů je dovednost sama o sobě.</span><span class="sxs-lookup"><span data-stu-id="3bda9-168">Designing statistical models is a skill on its own.</span></span> <span data-ttu-id="3bda9-169">Tým Microsoft Research Cambridge napsal [bezplatnou online knihu](http://mbmlbook.com/), která poskytuje jemný úvod do článku.</span><span class="sxs-lookup"><span data-stu-id="3bda9-169">The Microsoft Research Cambridge team has written a [free online book](http://mbmlbook.com/), which gives a gentle introduction to the article.</span></span> <span data-ttu-id="3bda9-170">Kapitola 3 této knihy pokrývá trueskill model podrobněji.</span><span class="sxs-lookup"><span data-stu-id="3bda9-170">Chapter 3 of this book covers the TrueSkill model in more detail.</span></span> <span data-ttu-id="3bda9-171">Jakmile máte model na mysli, můžete jej převést do kódu pomocí [rozsáhlé dokumentace](https://dotnet.github.io/infer/) na webu Infer.NET.</span><span class="sxs-lookup"><span data-stu-id="3bda9-171">Once you have a model in mind, you can transform it into code using the [extensive documentation](https://dotnet.github.io/infer/) on the Infer.NET website.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3bda9-172">Další kroky</span><span class="sxs-lookup"><span data-stu-id="3bda9-172">Next steps</span></span>

<span data-ttu-id="3bda9-173">Podívejte se na Infer.NET úložiště GitHub, abyste se dál učili a našli další ukázky.</span><span class="sxs-lookup"><span data-stu-id="3bda9-173">Check out the Infer.NET GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="3bda9-174">dotnet/infer úložiště GitHub</span><span class="sxs-lookup"><span data-stu-id="3bda9-174">dotnet/infer GitHub repository</span></span>](https://github.com/dotnet/infer)
