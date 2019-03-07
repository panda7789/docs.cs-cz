---
title: Vytvoření hry shoda seznamu aplikaci pomocí Infer.NET a probalistic programování
description: Objevte, jak pomocí probalistic programování Infer.NET k vytvoření aplikace seznamu her zápasu založen na zjednodušené verzi TrueSkill.
ms.date: 03/01/2019
ms.custom: mvc,how-to
ms.openlocfilehash: d760c364d874ec9670823be0664005d62526ee93
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473131"
---
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a>Vytvoření hry shoda seznamu aplikaci pomocí Infer.NET a pravděpodobnostní programování

Tato příručka vás naučí o pravděpodobnostní programování pomocí Infer.NET. Pravděpodobnostní programování je přístup založený na machine learning, ve kterém jsou vlastní modely vyjádřené jako počítačové programy. Umožňuje pro začlenění znalosti v těchto modelech a je strojové učení více interpretovatelném systému. Podporuje také online odvození – proces učení příchodu nových dat. Infer.NET se používá v různých produktů v Microsoftu v Azure, Xbox a Bing.

## <a name="what-is-probabilistic-programming"></a>Co je pravděpodobnostní programování?

Pravděpodobnostní programování umožňuje vytvořit statistických modelů procesů reálného světa. 

## <a name="prerequisites"></a>Požadavky

- Nastavení místního vývojového prostředí

  Tato příručka se očekává, že budete mít počítač, který používáte pro vývoj. .NET [zahájení práce během 10 minut](https://www.microsoft.com/net/core) kurz obsahuje pokyny pro nastavení místního vývojového prostředí v Mac, PC nebo Linux.

## <a name="create-your-app"></a>Vytvoření aplikace

1. Otevřete nový příkazový řádek a spusťte následující příkazy:

```console
dotnet new console -o myApp
cd myApp
```

`dotnet` Příkaz vytvoří `new` aplikace typu `console`. `-o` Parametr vytvoří adresář s názvem `myApp` kde vaše aplikace je uložena a naplní ho s požadovanými soubory. `cd myApp` Příkaz vloží do adresáře nově vytvořené aplikace.

## <a name="install-infernet-package"></a>Nainstalujte balíček Infer.NET

Pokud chcete použít Infer.NET, je potřeba nainstalovat `Microsoft.ML.Probabilistic.Compiler` balíčku. V příkazovém řádku spusťte následující příkaz:

```console
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a>Návrh modelu

Vzorový příklad používá tenis tabulky nebo foosball shody přehrát v kanceláři. Máte účastníky a výsledek jednotlivých shod.  Chcete hráče dovednosti z těchto dat odvodit. Předpokládejme, že oba hráči má obvykle distribuované latentní dovedností a jejich výkon daného shoda je hlučného verzi této dovedností. Data omezí vítěze výkon a být větší než odstraněných výkonu. Toto je zjednodušenou verzi Oblíbené [TrueSkill](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/) model, který podporuje také týmy, nakreslí a další rozšíření. [Rozšířená verze](https://www.microsoft.com/en-us/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) tento model se používá pro matchmaking v nejprodávanějšího herních titulů Halo a Gears War.

Seznam odvozené player dovedností, společně s jejich odchylky – míra nejistoty dovednosti, které potřebujete.

*Herní výsledek ukázková data*

Hra |Vítěz | Odstraněných
---------|----------|---------
 1 | Přehrávač 0 | Přehrávač 1
 2 | Přehrávač 0 | Přehrávač 3
 3 | Přehrávač 0 | Přehrávač 4
 4 | Přehrávač 1 | Přehrávač 2
 5 | Přehrávač 3 | Přehrávač 1
 6 | Přehrávač 4 | Přehrávač 2

S bližší pohled na ukázková data můžete si všimnout, že přehrávače 3 a 4 mají jeden win a ztráty jedné. Podívejme se, jak pořadí vypadat, pomocí pravděpodobnostní programování. Všimněte si že také je přehrávač nule vzhledem k tomu, že i office odpovídající seznamy jsou pro nás vývojáře od nuly.

## <a name="write-some-code"></a>Napsání kódu

S navržená modelem, je čas ji je možné vyjádřit jako pravděpodobnostní programu pomocí Infer.NET modelování rozhraní API. Otevřít `Program.cs` ve svém oblíbeném textovém editoru a veškerý jeho obsah nahraďte následujícím kódem:

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

```console
dotnet run
```

## <a name="results"></a>Výsledky

Výsledky by měl vypadat přibližně takto:

```
Compiling model...done.
Iterating:
.........|.........|.........|.........|.........| 50
Player 0 skill: Gaussian(9.517, 3.926)
Player 3 skill: Gaussian(6.834, 3.892)
Player 4 skill: Gaussian(6.054, 4.731)
Player 1 skill: Gaussian(4.955, 3.503)
Player 2 skill: Gaussian(2.639, 4.288)
```

Ve výsledcích Všimněte si, že tento přehrávač 3 řadí mírně zvýšené v přehrávači 4 podle našeho modelu. Důvodem je, že vítězství player 3 přes player 1 je mnohem závažnější než vítězství player 4 přes player 2 – Poznámka: Tento přehrávač 1 údery player 2. Přehrávač 0 je celkový specialita!  

## <a name="keep-learning"></a>Zajištění, že výuka

Navrhování statistických modelů je dovednosti sama o sobě. Tým Microsoft Research Cambridge zapsala [bezplatné online knihy](http://mbmlbook.com/), což dává mírného Úvod do článku. Tato kniha kapitolu 3 se týká modelu TrueSkill podrobněji. Jakmile budete mít modelu v paměti, můžete jeho transformaci na kódu pomocí [si rozsáhlou dokumentaci k](https://dotnet.github.io/infer/) na webu Infer.NET.

## <a name="next-steps"></a>Další kroky

Projděte si úložiště Infer.NET GitHub pokračujte ve čtení a najít další ukázky.
> [!div class="nextstepaction"]
> [DotNet/odvodit úložiště GitHub](https://github.com/dotnet/infer)
