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
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a>Vytvoření aplikace pro seznam her se Infer.NET a pravděpodobnostním programováním

Tento návod vás naučí o pravděpodobnostním programování pomocí Infer.NET. Pravděpodobnostní programování je přístup strojového učení, kde jsou vlastní modely vyjádřeny jako počítačové programy. Umožňuje začlenit znalosti domény do modelů a činí systém strojového učení více interpretovatelným. Podporuje také on-line odvození - proces učení, jak přicházejí nová data. Infer.NET se používá v různých produktech společnosti Microsoft v Azure, Xboxu a Bingu.

## <a name="what-is-probabilistic-programming"></a>Co je pravděpodobnostní programování?

Pravděpodobnostní programování umožňuje vytvářet statistické modely reálných procesů.

## <a name="prerequisites"></a>Požadavky

- Nastavení prostředí místního rozvoje

  Tento návod očekává, že budete mít stroj, který můžete použít pro vývoj. Kurz .NET [Hello World za 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému macOS, Windows nebo Linuxu.

## <a name="create-your-app"></a>Vytvoření aplikace

1. Otevřete nový příkazový řádek a spusťte následující příkazy:

```dotnetcli
dotnet new console -o myApp
cd myApp
```

Příkaz `dotnet` vytvoří `new` aplikaci `console`typu . Parametr `-o` vytvoří adresář `myApp` s názvem, kde je aplikace uložena, a naplní ho požadovanými soubory. Příkaz `cd myApp` vás umístí do nově vytvořeného adresáře aplikace.

## <a name="install-infernet-package"></a>Nainstalovat Infer.NET balíček

Chcete-li použít Infer.NET, `Microsoft.ML.Probabilistic.Compiler` musíte nainstalovat balíček. V příkazovém řádku spusťte následující příkaz:

```dotnetcli
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a>Navrhněte svůj model

Ukázka příkladu používá stolní tenis nebo stolní fotbal zápasy hrané v kanceláři. Máte účastníky a výsledek každého zápasu.  Chcete-li odvodit dovednosti hráče z těchto dat. Předpokládejme, že každý hráč má normálně distribuované latentní dovednosti a jejich daný výkon zápasu je hlučná verze této dovednosti. Data omezuje výkon vítěze na výkon vyšší než výkon poraženého. Toto je zjednodušená verze populárního modelu [TrueSkill,](https://www.microsoft.com/research/project/trueskill-ranking-system/) který také podporuje týmy, remízy a další rozšíření. [Pokročilá verze](https://www.microsoft.com/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) tohoto modelu se používá pro dohazování v nejprodávanějších herních titulech Halo a Gears of War.

Musíte uvést odvozené hráčské dovednosti, spolu s jejich rozptylem - míra nejistoty kolem dovedností.

*Ukázková data výsledků hry*

Herní |Vítěz | Loser
---------|----------|---------
 1 | Hráč 0 | Hráč 1
 2 | Hráč 0 | Hráč 3
 3 | Hráč 0 | Hráč 4
 4 | Hráč 1 | Hráč 2
 5 | Hráč 3 | Hráč 1
 6 | Hráč 4 | Hráč 2

Při bližším pohledu na ukázková data si všimnete, že hráči 3 a 4 mají jednu výhru a jednu ztrátu. Podívejme se, jak vypadají žebříčky pomocí pravděpodobnostního programování. Všimněte si také, že je hráč nula, protože i kancelářské zápas y seznamy jsou nulové na základě nás vývojářů.

## <a name="write-some-code"></a>Napsat nějaký kód

Po navržení modelu je čas vyjádřit jej jako pravděpodobnostní program pomocí rozhraní API pro modelování Infer.NET. Otevřete `Program.cs` ve svém oblíbeném textovém editoru a nahraďte veškerý jeho obsah následujícím kódem:

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

V příkazovém řádku spusťte následující příkaz:

```dotnetcli
dotnet run
```

## <a name="results"></a>Výsledky

Vaše výsledky by měly být podobné následujícímu:

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

Ve výsledcích si všimněte, že hráč 3 je podle našeho modelu o něco vyšší než hráč 4. To proto, že vítězství hráče 3 nad hráčem 1 je významnější než vítězství hráče 4 nad hráčem 2 - všimněte si, že hráč 1 porazí hráče 2. Hráč 0 je celkový šampion!

## <a name="keep-learning"></a>Mějte učení

Navrhování statistických modelů je dovednost sama o sobě. Tým Microsoft Research Cambridge napsal [bezplatnou online knihu](http://mbmlbook.com/), která poskytuje jemný úvod do článku. Kapitola 3 této knihy pokrývá trueskill model podrobněji. Jakmile máte model na mysli, můžete jej převést do kódu pomocí [rozsáhlé dokumentace](https://dotnet.github.io/infer/) na webu Infer.NET.

## <a name="next-steps"></a>Další kroky

Podívejte se na Infer.NET úložiště GitHub, abyste se dál učili a našli další ukázky.
> [!div class="nextstepaction"]
> [dotnet/infer úložiště GitHub](https://github.com/dotnet/infer)
