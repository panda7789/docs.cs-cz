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
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a>Vytvoření aplikace seznam s odpovídajícími hrami s Infer.NET a pravděpodobnostní programováním

Tato příručka vás seznámí s programováním v pravděpodobnostní pomocí Infer.NET. Programování pravděpodobnostní je přístup strojového učení, kde se vlastní modely vyjadřují jako počítačové programy. Umožňuje začlenit znalostní bázi domény v modelech a díky tomu může systém Machine Learning lépe interpretovat. Podporuje také online odvozování – proces učení se zadoručením nových dat. Infer.NET se používá v různých produktech Microsoftu v Azure, Xbox a Bingu.

## <a name="what-is-probabilistic-programming"></a>Co je pravděpodobnostní programování?

Programování pravděpodobnostní vám umožňuje vytvářet statistické modely reálných procesů.

## <a name="prerequisites"></a>Předpoklady

- Nastavení místního vývojového prostředí

  Tato průvodce vám očekává, že máte počítač, který můžete použít pro vývoj. Kurz rozhraní .NET [Hello World v 10 minutách](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v MacOS, Windows nebo Linux.

## <a name="create-your-app"></a>Vytvoření aplikace

1. Otevřete nový příkazový řádek a spusťte následující příkazy:

```dotnetcli
dotnet new console -o myApp
cd myApp
```

Příkaz `dotnet` vytvoří `new` aplikace typu `console`. Parametr `-o` vytvoří adresář s názvem `myApp`, kde je vaše aplikace uložená, a naplní ji požadovanými soubory. Příkaz `cd myApp` vloží do nově vytvořeného adresáře aplikace.

## <a name="install-infernet-package"></a>Nainstalovat balíček Infer.NET

Pokud chcete používat Infer.NET, musíte nainstalovat balíček `Microsoft.ML.Probabilistic.Compiler`. Na příkazovém řádku spusťte následující příkaz:

```dotnetcli
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a>Návrh modelu

Vzorový příklad používá v sadě Office shodu tabulky tenis nebo Foosball. Máte účastníky a výsledek každé shody.  Chcete odvodit dovednosti přehrávače od těchto dat. Předpokládejme, že každý hráč má obvykle distribuovanou latentní dovednost a jejich odpovídající výkon je tato dovednostní verze. Data omezí výkon vítěze tak, aby byla větší než výkon loser. Toto je zjednodušená verze oblíbeného modelu [TrueSkill](https://www.microsoft.com/research/project/trueskill-ranking-system/) , která také podporuje týmy, kreslení a další rozšíření. [Pokročilá verze](https://www.microsoft.com/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) tohoto modelu se používá pro Matchmaking v nejlepším prodeji názvů her Halo a ozubeného kolaci války.

Musíte uvést, jaké dovednosti v přehrávači jsou společně s jejich odchylkou – míra nejistoty v rámci dovedností.

*Ukázková data výsledků her*

Hra |Replik | Loser
---------|----------|---------
 1 | Přehrávač 0 | Hráč 1
 2 | Přehrávač 0 | Hráč 3
 3 | Přehrávač 0 | Hráč 4
 4 | Hráč 1 | Hráč 2
 5 | Hráč 3 | Hráč 1
 6 | Hráč 4 | Hráč 2

Podíváme se na vzorová data a Všimněte si, že hráči 3 a 4 mají jednu ze všech výher a jednu ztrátu. Pojďme se podívat, jak pořadí vypadá pomocí pravděpodobnostní programování. Všimněte si také, že je přehrávač nulový, protože v seznamech pro nás, které jsou v souladu s více kancelářemi, je nula.

## <a name="write-some-code"></a>Napsat nějaký kód

Model byl navržený tak, jak ho vyjádřit jako pravděpodobnostní program pomocí rozhraní API pro modelování Infer.NET. Ve svém oblíbeném textovém editoru otevřete `Program.cs` a nahraďte jeho obsah následujícím kódem:

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

## <a name="run-your-app"></a>Spuštění aplikace

Na příkazovém řádku spusťte následující příkaz:

```dotnetcli
dotnet run
```

## <a name="results"></a>Výsledky

Výsledky by měly být podobné následujícímu:

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

Ve výsledcích si všimněte, že hráč 3 rozhodne o něco vyšším než hráč 4 podle našeho modelu. Důvodem je to, že Victory of Player 3 over Player 1 je důležitější než Victory Player 4 přes Player 2 – Poznámka: Player 1 Beats Player 2. Přehrávač 0 je celkový Champ!

## <a name="keep-learning"></a>Průběžné učení

Návrh statistických modelů je dovedností sám o sobě. Tým Microsoft Research Cambridge napsal [bezplatnou online knihu](http://mbmlbook.com/), která poskytuje mírné představení tohoto článku. Kapitola 3 této knihy pokrývá model TrueSkill podrobněji. Jakmile máte model, můžete ho transformovat na kód pomocí [obsáhlé dokumentace](https://dotnet.github.io/infer/) na webu Infer.NET.

## <a name="next-steps"></a>Další kroky

Podívejte se na úložiště GitHub Infer.NET a pokračujte v učení a Najděte další ukázky.
> [!div class="nextstepaction"]
> [dotnet/odvodit úložiště GitHub](https://github.com/dotnet/infer)
