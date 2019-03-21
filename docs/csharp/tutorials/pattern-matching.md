---
title: Použít porovnávání vzorů funkce k rozšíření datových typů
description: V tomto kurzu pokročilé ukazuje, jak použít porovnávání vzorů techniky k vytvoření funkce pomocí dat a algoritmy, které se vytvářejí zvlášť.
ms.date: 03/13/2019
ms.custom: mvc
ms.openlocfilehash: c064af5fdf85587d0c4fa1471894122d6fe0d2f7
ms.sourcegitcommit: e994e47d3582bf09ae487ecbd53c0dac30aebaf7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2019
ms.locfileid: "58262525"
---
# <a name="tutorial-using-pattern-matching-features-to-extend-data-types"></a>Kurz: Použití porovnávání vzorů funkce k rozšíření datových typů

C#7 zavedené základní vzor odpovídající funkce. Tyto funkce jsou rozšířeny v C# 8 s výrazy typu new a vzory. Můžete napsat funkci, která se chová, jako jste rozšířili typy, které mohou být v jiných knihovnách. Další možností použití vzorců je vytvoření funkce, které vaše aplikace vyžaduje, která nejsou základní funkce rozšiřovaného typu.

V tomto kurzu se dozvíte jak:

> [!div class="checklist"]
> * Rozpoznat situacích, kdy porovnávání vzorů by měl být použít.
> * Použití vzoru porovnávání výrazů k implementaci chování na základě typů a hodnot vlastností.
> * Kombinovat porovnávání vzorů s dalšími technikami, chcete-li vytvořit kompletní algoritmy.

## <a name="prerequisites"></a>Požadavky

Budete muset nastavit počítač pro spuštění .NET Core, včetně C# kompilátoru 8.0 ve verzi preview. C# 8 kompilátoru ve verzi preview jsou k dispozici nejnovější [Visual Studio 2019 preview](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019+preview), nebo si prohlédnout nejnovější [ve verzi preview rozhraní .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).

Tento kurz předpokládá, že jste obeznámeni s C# a .NET, včetně sady Visual Studio nebo rozhraní příkazového řádku .NET Core.

## <a name="scenarios-for-pattern-matching"></a>Scénáře pro porovnávání vzorů

Moderní vývoj často zahrnuje integraci dat z více zdrojů a vám informace a přehledy na základě těchto dat v jedné aplikaci získá na ucelenosti. Vy a váš tým nebude mít ovládací prvek nebo přístupu pro všechny typy, které představují příchozí data.

Pro vytváření typů ve vaší aplikaci, které představují jednotlivé typy dat z těchto různých zdrojů dat by volat klasické objektově orientovaný návrh. Aplikace by pak pracovat s těmito novými typy, vytváření hierarchie dědičnosti, vytvoření virtuální metody a implementaci abstrakcí. Tyto techniky fungují a někdy jsou ty nejlepší nástroje. Jindy můžete napsat menším množstvím kódu. Můžete napsat další kód zrušte pomocí technik, které oddělují data od operací, které zpracovávají data.

V tomto kurzu vytvoříte a prozkoumejte aplikaci, která přebere příchozí data z několika externích zdrojů pro jeden scénář. Uvidíte jak **porovnávání vzorů** poskytuje efektivní způsob, jak spotřebovat a zpracovat data způsoby, které nebyly součástí původního systému.

Vezměte v úvahu hlavní metro oblast, která používá ke správě přenosů dat mýtné a ceny za dobu ve špičce. Můžete napsat aplikaci, která vypočítá mýtné vozidla na základě jeho typu. Novější vylepšení zahrnují ceny na základě počtu osob ve vozidle. Dále přidejte ceny založené na čas a den v týdnu.

Z tohoto stručný popis vám může mít rychle šrafují si hierarchii objektů modelování tohoto systému. Však vaše data pochází z více zdrojů, jako jsou jinými systémy pro správu registrace vozidlo. Tyto systémy poskytují různé třídy k modelování dat a není nutné jeden objekt modelu, která vám pomůže. V tomto kurzu použijete tyto zjednodušené třídy k modelování dat vozidla mezi těmito externími systémy, jak je znázorněno v následujícím kódu:

[!code-csharp[ExternalSystems](~/samples/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

Můžete stáhnout počáteční kód z [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) úložiště GitHub. Uvidíte, že třídy vozidlo jsou z různých systémů a jsou v různých oborech názvů. Žádné společné základní třídy, jiné než `System.Object` můžete využít.

## <a name="pattern-matching-designs"></a>Vzor odpovídající návrhy

Scénář používaných pro tento kurz stručný přehled druhy problémů, které vzorovou shodu je vhodná pro řešení:

- Objekty, které potřebujete k práci s nejsou v hierarchii objektů, který odpovídá vaše cíle. Pracujete s třídami, které jsou součástí nesouvisejících systémy.
- Funkce, které přidáváte, které nejsou součástí základní abstrakce pro tyto třídy. Linka zaplaceno vozidla *změny* pro různé typy vozidel, ale linka není základní funkce vozidlo.

Když *tvar* dat a *operace* zabývat data nejsou společně popsané porovnávání vzorů funkce v C# usnadňují práci s.

## <a name="implement-the-basic-toll-calculations"></a>Provádění výpočtů základní linka

Pouze na typ, který využívá nejzákladnější výpočtu linka:

- A `Car` je $2.00.
- A `Taxi` je 3.50 $.
- A `Bus` je 5.00 $.
- A `DeliveryTruck` je 10,00 USD

Vytvořte nový `TollCalculator` třídy a implementovat vzorce pro porovnávání na typ, který má získat velikost linka. Následující kód ukazuje počáteční implementace `TollCalculator`.

```csharp
using System;
using CommercialRegistration;
using ConsumerVehicleRegistration;
using LiveryRegistration;

namespace toll_calculator
{
    public class TollCalculator
    {
        public decimal CalculateToll(object vehicle) =>
            vehicle switch
        {
            Car c           => 2.00m,
            Taxi t          => 3.50m,
            Bus b           => 5.00m,
            DeliveryTruck t => 10.00m,
            { }             => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
            null            => throw new ArgumentNullException(nameof(vehicle))
        };
    }
}
```

Předchozí kód používá **výraz switch** (není stejný jako [ `switch` ](../language-reference/keywords/switch.md) příkaz), který testuje **vzor typu**. A **výraz switch** začíná proměnnou, `vehicle` v předchozím kódu, za nímž následuje `switch` – klíčové slovo. Dále obsahuje všechny **přepnout arms** uvnitř složených závorek. `switch` Výraz vytvoří další upřesnění zpráv o syntaxi, která obklopuje `switch` příkazu. `case` – Klíčové slovo je vynechán, a výsledek každého arm je výraz. Poslední dva arms zobrazit novou funkci jazyka. `{ }` Případ odpovídá libovolný nenulový objekt, který neodpovídal starší arm. Tato arm zachytí nesprávné typy předaný této metodě.  `{ }` Případu musí následovat případů pro každý typ vozidlo. Pokud pořadí byly vráceny zpět, `{ }` případ má přednost. Nakonec `null` zjistí vzor, kdy `null` je předaný této metodě. `null` Model může být poslední, protože jiné vzory typ shodný s pouze nenulový objekt nesprávného typu.

Můžete otestovat tento kód, pomocí následujícího kódu v `Program.cs`:

```csharp
using System;
using CommercialRegistration;
using ConsumerVehicleRegistration;
using LiveryRegistration;

namespace toll_calculator
{
    class Program
    {
        static void Main(string[] args)
        {
            var tollCalc = new TollCalculator();

            var car = new Car();
            var taxi = new Taxi();
            var bus = new Bus();
            var truck = new DeliveryTruck();

            Console.WriteLine($"The toll for a car is {tollCalc.CalculateToll(car)}");
            Console.WriteLine($"The toll for a taxi is {tollCalc.CalculateToll(taxi)}");
            Console.WriteLine($"The toll for a bus is {tollCalc.CalculateToll(bus)}");
            Console.WriteLine($"The toll for a truck is {tollCalc.CalculateToll(truck)}");

            try
            {
                tollCalc.CalculateToll("this will fail");
            }
            catch (ArgumentException e)
            {
                Console.WriteLine("Caught an argument exception when using the wrong type");
            }
            try
            {
                tollCalc.CalculateToll(null);
            }
            catch (ArgumentNullException e)
            {
                Console.WriteLine("Caught an argument exception when using null");
            }
        }
    }
}
```

Tento kód je součástí počáteční projekt, ale je označené jako komentář. Odstranit znaky komentářů, a budete moci otestovat, co jste napsali.

Začínáte naleznete v tématu Jak vzory vám může pomoci vytvořit algoritmy, kde jsou oddělené kód a data. `switch` Výraz testuje typ a vytváří různé hodnoty na základě výsledků. To je jenom začátek.

## <a name="add-occupancy-pricing"></a>Přidat obsazení ceny

Autorita linka se chce podporovat vozidel projít využívá maximální kapacitu. Jste se rozhodli účtovat více při vozidel mají menší počet cestujících a podporovat plnou vozidel tím, že nabízí nižší ceny:

- Auta nebo taxi s žádné cestujících platit navíc 0,50 USD.
- Auta nebo taxi s dvěma cestujících získat 0,50 slevu.
- Auta nebo taxi se třemi nebo více cestujících získat slevu 1,00 $.
- Sběrnice, které jsou kratší než 50 % úplné platit navíc 2.00 $.
- Sběrnice, které jsou více než 90 % úplné získat slevu 1,00 $.

Tato pravidla je možné implementovat pomocí **vlastnost vzor** ve stejném výrazu přepínače. Vzor pro vlastnost prozkoumá vlastností objektu po určil typ. Jeden případ `Car` rozšíří na čtyři různé případy:

```csharp
vehicle switch
{
    Car { Passengers: 0}        => 2.00m + 0.50m,
    Car { Passengers: 1 }       => 2.0m,
    Car { Passengers: 2}        => 2.0m - 0.50m,
    Car c                       => 2.00m - 1.0m,

    // ...
};
```

První tři případy typ jako testu `Car`, zkontrolujte hodnotu `Passengers` vlastnost. Pokud se obě shodovat, tento výraz je vyhodnocen a vrácena.

By bylo třeba rozbalit také případy taxi podobným způsobem:

```csharp
vehicle switch
{
    // ...

    Taxi { Fares: 0}  => 3.50m + 1.00m,
    Taxi { Fares: 1 } => 3.50m,
    Taxi { Fares: 2}  => 3.50m - 0.50m,
    Taxi t            => 3.50m - 1.00m,

    // ...
};
```

V předchozím příkladu `when` na posledním případě vynechání klauzule.

V dalším kroku implementujte obsazení pravidla tak, že rozbalíte případů pro sběrnice, jak je znázorněno v následujícím příkladu:

```csharp
vehicle switch
{
    // ...

    Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
    Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
    Bus b => 5.00m,

    // ...
};
```

Autorita linka není problémem počet cestujících v trucks doručování. Místo toho že účtovat více založené na třídě váha nákladních vozů. Trucks víc než 5000 lbs se účtují další 5.00 $. Světle trucks v části 3000 lbs disponují $2.00 slevy. Toto pravidlo je implementováno s následujícím kódem:

```csharp
vehicle switch
{
    // ...

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

Předchozí kód ukazuje `when` klauzule přepínače arm. Můžete použít `when` klauzule k testování podmínek jiné než rovnost pro vlastnost. Po dokončení budete mít metodu, která vypadá podobně jako následující:

```csharp
vehicle switch
{
    Car { Passengers: 0}        => 2.00m + 0.50m,
    Car { Passengers: 1}        => 2.0m,
    Car { Passengers: 2}        => 2.0m - 0.50m,
    Car c                       => 2.00m - 1.0m,

    Taxi { Fares: 0}  => 3.50m + 1.00m,
    Taxi { Fares: 1 } => 3.50m,
    Taxi { Fares: 2}  => 3.50m - 0.50m,
    Taxi t            => 3.50m - 1.00m,

    Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
    Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
    Bus b => 5.00m,

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

Mnohé z nich přepnout arms jsou příklady **rekurzivní vzory**. Například `Car { Passengers: 1}` zobrazuje konstantní vzorek uvnitř vlastnosti modelu.

Méně opakované tento kód můžete provést pomocí vnořených přepínače. `Car` a `Taxi` mají čtyři různé arms v předchozích příkladech. V obou případech můžete vytvořit typ vzor, který se předají do vlastnosti modelu. Tato technika je znázorněno v následujícím kódu:

```csharp
public decimal CalculateToll(object vehicle) =>
    vehicle switch
    {
        Car c => c.Passengers switch
        {
            0 => 2.00m + 0.5m,
            1 => 2.0m,
            2 => 2.0m - 0.5m,
            _ => 2.00m - 1.0m
        },

        Taxi t => t.Fares switch
        {
            0 => 3.50m + 1.00m,
            1 => 3.50m,
            2 => 3.50m - 0.50m,
            _ => 3.50m - 1.00m
        },

        Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
        Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
        Bus b => 5.00m,

        DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
        DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
        DeliveryTruck t => 10.00m,

        { }  => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
        null => throw new ArgumentNullException(nameof(vehicle))
    };
```

V předchozím příkladu, pomocí výrazu rekurzivní znamená, že nemusíte opakovat `Car` a `Taxi` arms obsahující arms podřízený, které testují hodnotu vlastnosti. Tato technika se nepoužívá pro `Bus` a `DeliveryTruck` zbraní protože zbraně testování rozsahy pro vlastnost, nikoli jednotlivých hodnot.

## <a name="add-peak-pricing"></a>Přidat ceny ve špičce

Pro poslední funkci autority linka chce přidat dobu ve špičce citlivé ceny. Během ráno a špičce hodin večer jsou mýtné dvojitá. Toto pravidlo ovlivní pouze provoz v jednom směru: Město ráno příchozí a odchozí ve špičce hodině večer. Během jindy během pracovního dne mýtné zvýšit o 50 %. Noční pozdní a časná ráno, mýtné jsou sníženy o 25 %. Během víkendu je normální rychlosti, bez ohledu na čas.

Porovnávání vzorů pro tuto funkci použijete, ale budete ji integrovat s dalšími technikami. Může vytvořit jeden vzor odpovídající výraz, který by účet pro všechny kombinace směr, den v týdnu a čas. Výsledek by byl složitý výraz. By bylo obtížné číst a obtížně srozumitelné. Díky tomu se obtížně zajistili její správnost. Místo toho sloučit tyto metody pro vytvoření n-tice hodnot, která stručně popisuje tyto stavy. Pak pomocí porovnávání vzorů pro výpočet multiplikátor pro placená linka. Řazené kolekce členů obsahuje tři samostatné podmínky:

- Den je jeden den v týdnu nebo víkendech.
- Vzdálené čas, kdy se shromažďují linka.
- Směr je do město nebo z něj Město

Následující tabulka uvádí kombinace vstupních hodnot a ceny multiplikátor ve špičce:

| Den        | Čas         | Směr | Premium |
| ---------- | ------------ | --------- |--------:|
| Den v týdnu    | naléhavá ráno | Příchozí   | x 2.00  |
| Den v týdnu    | naléhavá ráno | Odchozí  | x 1,00  |
| Den v týdnu    | denní      | Příchozí   | x 1.50  |
| Den v týdnu    | denní      | Odchozí  | x 1.50  |
| Den v týdnu    | večer špičce | Příchozí   | x 1,00  |
| Den v týdnu    | večer špičce | Odchozí  | x 2.00  |
| Den v týdnu    | přes noc    | Příchozí   | x 0,75.  |
| Den v týdnu    | přes noc    | Odchozí  | x 0,75.  |
| Víkendu    | naléhavá ráno | Příchozí   | x 1,00  |
| Víkendu    | naléhavá ráno | Odchozí  | x 1,00  |
| Víkendu    | denní      | Příchozí   | x 1,00  |
| Víkendu    | denní      | Odchozí  | x 1,00  |
| Víkendu    | večer špičce | Příchozí   | x 1,00  |
| Víkendu    | večer špičce | Odchozí  | x 1,00  |
| Víkendu    | přes noc    | Příchozí   | x 1,00  |
| Víkendu    | přes noc    | Odchozí  | x 1,00  |

Existují 16 různé kombinace tří proměnných. Díky kombinaci některá z podmínek, zjednodušíte výraz konečné přepínače.

Používá systém, který shromažďuje mýtné <xref:System.DateTime> struktury po dobu, kdy byla shromážděna linka. Vytvořte člena metody, které z předchozí tabulky vytvořte proměnné. Následující funkce, která používá vzor odpovídající výraz přepínače vyjádřit, jestli <xref:System.DateTime> představuje víkend nebo jeden den v týdnu:

```csharp
private static bool IsWeekDay(DateTime timeOfToll) =>
    timeOfToll.DayOfWeek switch
    {
        DayOfWeek.Monday    => true,
        DayOfWeek.Tuesday   => true,
        DayOfWeek.Wednesday => true,
        DayOfWeek.Thursday  => true,
        DayOfWeek.Friday    => true,
        DayOfWeek.Saturday  => false,
        DayOfWeek.Sunday    => false
    };
```

Tato metoda funguje, ale je automatizujete. Nemůžete zjednodušit, jak je znázorněno v následujícím kódu:

[!code-csharp[IsWeekDay](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

V dalším kroku přidejte podobnou funkci ke kategorizaci času bloky:

[!code-csharp[GetTimeBand](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

Předchozí metoda nepoužívá porovnávání vzorů. Je jasnější, pomocí známých cascade z `if` příkazy. Přidat soukromé `enum` převést každý časový rozsah na diskrétní hodnoty.

Po vytvoření tyto metody můžete použít jiné `switch` výraz s **vzor n-tice** k výpočtu cenové úrovně premium. Může vytvářet `switch` výraz s všechny 16 arms:

[!code-csharp[FullTuplePattern](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

Výše kód funguje, ale můžete se dá zjednodušit. Všechny osm kombinace pro víkendu mají stejné linka. Můžete nahradit všechny osm tento řádek:

```csharp
(false, _, _) => 1.0m,
```

Příchozí a odchozí provoz mají stejné multiplikátor během denní den v týdnu a hodiny přes noc. Tyto čtyři přepínač arms je možné nahradit následující dva řádky:

```csharp
(true, TimeBand.Overnight, _) => 0.75m,
(true, TimeBand.Daytime, _)   => 1.5m,
```

Kód by měl vypadat jako v následujícím kódu až tyto dvě změny:

```csharp
public decimal PeakTimePremium(DateTime timeOfToll, bool inbound) =>
    (IsWeekDay(timeOfToll), GetTimeBand(timeOfToll), inbound) switch
    {
        (true, TimeBand.MorningRush, true)  => 2.00m,
        (true, TimeBand.MorningRush, false) => 1.00m,
        (true, TimeBand.Daytime,     _)     => 1.50m,
        (true, TimeBand.EveningRush, true)  => 1.00m,
        (true, TimeBand.EveningRush, false) => 2.00m,
        (true, TimeBand.Overnight,   _)     => 0.75m,
        (false, _,                   _)     => 1.00m,
    };
```

Nakonec můžete odebrat dvě špičce hodinu případů, kdy platíte běžná cena. Po odebrání těchto arms můžete nahradit `false` s zahození (`_`) v posledním přepínač arm. Budete mít hotové následující metodu:

[!code-csharp[SimplifiedTuplePattern](../../../samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

Tento příklad ukazuje, jednou z výhod porovnávání vzorů: větví vzor se vyhodnocují v pořadí. Pokud změníte uspořádání, je tak, aby starší větev zpracovává jeden z novějších případy, kompilátor vás upozorní o nedosažitelném kódu. Tato pravidla jazyk usnadnili provést předchozí zjednodušení s vědomím, že kód nezměnila.

Porovnávání vzorů provede některé typy kód lépe čitelný a nabízí alternativu k objektově orientované techniky, když kód nelze přidat do vašich tříd. Data a funkce live této doby změny nepublikujete, příčinou je v cloudu. *Tvar* dat a *operace* na to nejsou popsané nutně společně. V tomto kurzu využívat existující data z jeho původní funkce zcela různými způsoby. Porovnávání vzorů přiřadil schopnost psát funkce, které overrode těchto typů, i když nelze rozšířit, je.

## <a name="next-steps"></a>Další kroky

Dokončený kód z si můžete stáhnout [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) úložiště GitHub. Prozkoumávání vzorců sami a přidejte tuto techniku regulární kódování aktivit. Tyto techniky učení nabízí další způsob, jak přistupovat ke problémy a vytvořit nové funkce.
