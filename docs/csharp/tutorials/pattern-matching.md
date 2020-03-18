---
title: Použití prvků porovnávání vzorů k rozšíření datových typů
description: Tento pokročilý kurz ukazuje, jak používat techniky porovnávání vzorů k vytvoření funkce pomocí dat a algoritmů, které jsou vytvořeny samostatně.
ms.date: 03/13/2019
ms-technology: csharp-whats-new
ms.custom: mvc
ms.openlocfilehash: df1054d8e0ec2b2539e6a1d00bf353d8ca927397
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156529"
---
# <a name="tutorial-using-pattern-matching-features-to-extend-data-types"></a>Kurz: Použití funkcí porovnávání vzorů k rozšíření datových typů

C# 7 představil základní funkce odpovídající vzor. Tyto funkce jsou rozšířeny v C# 8 s novými výrazy a vzory. Můžete psát funkce, které se chová, jako byste rozšířené typy, které mohou být v jiných knihovnách. Další použití pro vzory je vytvořit funkce, které vaše aplikace vyžaduje, že není základní funkce typu, který je rozšířen.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> - Rozpoznat situace, kde by měl být použit porovnávání vzorů.
> - K implementaci chování na základě typů a hodnot vlastností použijte výrazy porovnávání vzorů.
> - Zkombinujte porovnávání vzorů s jinými technikami a vytvořte úplné algoritmy.

## <a name="prerequisites"></a>Požadavky

Budete muset nastavit počítač pro spuštění .NET Core, včetně kompilátoru C# 8.0. Kompilátor Jazyka C# 8 je k dispozici počínaje [sadou Visual Studio 2019 verze 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download).

Tento kurz předpokládá, že jste obeznámeni s C# a .NET, včetně Visual Studio nebo .NET Core CLI.

## <a name="scenarios-for-pattern-matching"></a>Scénáře pro porovnávání vzorů

Moderní vývoj často zahrnuje integraci dat z více zdrojů a prezentaci informací a poznatků z nich v jedné soudržné aplikaci. Vy a váš tým nebudete mít kontrolu nebo přístup pro všechny typy, které představují příchozí data.

Klasický objektově orientovaný návrh by volal pro vytváření typů ve vaší aplikaci, které představují každý datový typ z těchto více zdrojů dat. Potom aplikace bude pracovat s těmito novými typy, sestavení hierarchie dědičnosti, vytvářet virtuální metody a implementovat abstrakce. Tyto techniky fungují, a někdy jsou nejlepší nástroje. Jindy můžete napsat méně kódu. Můžete napsat více jasný kód pomocí technik, které oddělují data z operací, které pracují s daty.

V tomto kurzu vytvoříte a prozkoumáte aplikaci, která přebírá příchozí data z několika externích zdrojů pro jeden scénář. Uvidíte, jak **porovnávání vzorů** poskytuje efektivní způsob, jak využívat a zpracovávat tato data způsoby, které nebyly součástí původního systému.

Vezměme si hlavní metropolitní oblast, která používá mýtné a ceny ve špičce pro správu provozu. Napíšete aplikaci, která vypočítá mýtné pro vozidlo na základě jeho typu. Pozdější vylepšení zahrnují ceny na základě počtu cestujících ve vozidle. Další vylepšení přidávají ceny na základě času a dne v týdnu.

Z tohoto stručného popisu jste možná rychle načrtli hierarchii objektů, abyste tento systém modelovali. Vaše data však pocházejí z více zdrojů, jako jsou jiné systémy řízení registrace vozidel. Tyto systémy poskytují různé třídy pro modelování dat a nemáte jeden objektový model, který můžete použít. V tomto kurzu budete používat tyto zjednodušené třídy k modelování dat vozidel z těchto externích systémů, jak je znázorněno v následujícím kódu:

[!code-csharp[ExternalSystems](~/samples/snippets/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

Startovací kód si můžete stáhnout z úložiště [GitHub dotnet/samples.](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) Můžete vidět, že třídy vozidel jsou z různých systémů a jsou v různých oborech názvů. Žádná společná základní třída, kromě `System.Object` toho, že může být využita.

## <a name="pattern-matching-designs"></a>Vzory odpovídající návrhy

Scénář použitý v tomto kurzu upozorňuje na druhy problémů, které odpovídá vzor je vhodný k řešení:

- Objekty, se kterými potřebujete pracovat, nejsou v hierarchii objektů, která odpovídá vašim cílům. Je možné, že pracujete s třídami, které jsou součástí nesouvisejících systémů.
- Funkce, které přidáváte, není součástí základní abstrakce pro tyto třídy. Mýtné placené vozidlem *se mění* pro různé typy vozidel, ale mýtné není základní funkcí vozidla.

Pokud *tvar* dat a *operace* na těchto datech nejsou popsány společně, funkce porovnávání vzorů v C# usnadňují práci s.

## <a name="implement-the-basic-toll-calculations"></a>Provedení základních výpočtů mýtného

Nejzákladnější výpočet mýtného se opírá pouze o typ vozidla:

- A `Car` je 2,00 dolarů.
- A `Taxi` je 3,50 dolarů.
- A `Bus` je 5,00 dolarů.
- A `DeliveryTruck` je 10,00 dolarů

Vytvořte `TollCalculator` novou třídu a implementujte odpovídající vzor na typu vozidla, abyste získali částku mýtného. Následující kód ukazuje počáteční implementaci `TollCalculator`.

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

Předchozí kód používá **výraz přepínače** (není [`switch`](../language-reference/keywords/switch.md) stejný jako příkaz), který testuje **vzor typu**. **Výraz přepínače** začíná proměnnou `vehicle` v předchozím kódu následovaném klíčovým slovem. `switch` Dále přicházejí všechny **ramena spínače** uvnitř kudrnatých šle. Výraz `switch` provede další vylepšení syntaxe, která `switch` obklopuje příkaz. Klíčové `case` slovo je vynecháno a výsledkem každé rameno je výraz. Poslední dvě paže ukazují novou jazykovou funkci. Případ `{ }` odpovídá všem objektům, které nemají hodnotu null a které neodpovídají předchozí ruce. Toto rameno zachytí všechny nesprávné typy předané této metodě.  Pouzdro `{ }` musí následovat případy pro každý typ vozidla. Pokud by bylo pořadí `{ }` obráceno, měl by přednost případ. Nakonec `null` vzor detekuje při `null` předání této metodě. Vzorek `null` může být poslední, protože jiné vzory typu odpovídají pouze objektu bez hodnoty null správného typu.

Tento kód můžete otestovat pomocí `Program.cs`následujícího kódu v :

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

Tento kód je součástí počátečního projektu, ale je zakomentován. Odeberte komentáře a můžete otestovat, co jste napsali.

Začínáte vidět, jak vzory vám mohou pomoci vytvořit algoritmy, kde kód a data jsou oddělené. Výraz `switch` testuje typ a vytváří různé hodnoty na základě výsledků. To je jen začátek.

## <a name="add-occupancy-pricing"></a>Přidání cen obsazenosti

Mýtný úřad chce motivovat vozidla k jízdě na maximální kapacitu. Rozhodli se účtovat více, když mají vozidla méně cestujících, a podporují plná vozidla tím, že nabízejí nižší ceny:

- Auta a taxíky bez pasažérů zaplatí dalších 0,50 usd.
- Auta a taxíky se dvěma cestujícími získat slevu 0,50 dolarů.
- Auta a taxíky se třemi nebo více cestujícími získají slevu 1,00 dolarů.
- Autobusy, které jsou méně než 50% plné platit extra 2,00 dolarů.
- Autobusy, které jsou více než 90% plné získat slevu 1,00 dolarů.

Tato pravidla lze implementovat pomocí **vzoru vlastnosti** ve stejném výrazu přepínač. Vzor vlastností zkoumá vlastnosti objektu po určení typu. Jediný případ pro `Car` rozšíření na čtyři různé případy:

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

První tři případy test typu `Car`jako , pak `Passengers` zkontrolujte hodnotu vlastnosti. Pokud obě shody, tento výraz je vyhodnocena a vrácena.

Byste také rozšířit případy pro taxíky podobným způsobem:

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

V předchozím příkladu `when` byla klauzule vynechána v konečném případě.

Dále implementujte pravidla obsazenosti rozšířením případů pro autobusy, jak je znázorněno v následujícím příkladu:

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

Mýtný úřad se nezabývá počtem cestujících v dodávkách. Místo toho upraví výši mýtného na základě hmotnostní třídy nákladních vozidel takto:

- Nákladní vozidla nad 5000 liber jsou účtovány extra 5,00 dolarů.
- Lehké nákladní automobily pod 3000 liber jsou uvedeny 2,00 dolarů slevu.

Toto pravidlo je implementováno pomocí následujícího kódu:

```csharp
vehicle switch
{
    // ...

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

Předchozí kód zobrazuje `when` klauzuli ramene switch. Klauzule `when` slouží k testování podmínek jiných než rovnost na vlastnost. Po dokončení budete mít metodu, která vypadá podobně jako následující:

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

    { }     => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
    null    => throw new ArgumentNullException(nameof(vehicle))
};
```

Mnohé z těchto přepínačů jsou příklady **rekurzivních vzorů**. Například `Car { Passengers: 1}` zobrazuje konstantní vzorek uvnitř vzoru vlastností.

Tento kód můžete provést méně opakující se pomocí vnořené přepínače. `Car` A `Taxi` oba mají čtyři různé zbraně v předchozích příkladech. V obou případech můžete vytvořit vzorek textu, který se vkládá do vzoru vlastností. Tato technika je uvedena v následujícím kódu:

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

V předchozí ukázce použití rekurzivního výrazu znamená, že neopakujete `Car` a `Taxi` ramena obsahující podřízené ramena, která testují hodnotu vlastnosti. Tato technika se nepoužívá `Bus` pro `DeliveryTruck` a zbraně, protože tyto zbraně jsou testovací rozsahy pro vlastnost, nikoli diskrétní hodnoty.

## <a name="add-peak-pricing"></a>Přidání špičkových cen

Pro konečnou funkci chce orgán pro výběr mýtného přidat časově citlivé ceny ve špičce. Během ranní a večerní špičky se mýtné zdvojnásobí. Toto pravidlo ovlivňuje pouze provoz v jednom směru: příchozí do města v dopoledních hodinách, a odchozí ve večerní špičce. Během jiných časů během pracovního dne se mýtné zvyšuje o 50 %. Pozdě v noci a brzy ráno se mýtné snižuje o 25%. Během víkendu je to běžná sazba, bez ohledu na čas.

Budete používat porovnávání vzorů pro tuto funkci, ale budete integrovat s jinými technikami. Můžete vytvořit jeden vzor odpovídající výraz, který by účet pro všechny kombinace směru, den v týdnu a čas. Výsledkem by byl složitý výraz. Bylo by těžké číst a těžko pochopit. To ztěžuje zajištění správnosti. Místo toho zkombinujte tyto metody k vytvoření řazené kolekce členů s hodnotami, které výstižně popisují všechny tyto stavy. Pak použijte porovnávání vzorů k výpočtu multiplikátoru pro mýtné. Řazená kolekce členů obsahuje tři diskrétní podmínky:

- Den je buď všední den nebo víkend.
- Pásmo času, kdy se vybírá mýtné.
- Směr je do města nebo mimo město

V následující tabulce jsou uvedeny kombinace vstupních hodnot a násobitele cen ve špičce:

| Den        | Time         | Směr | Premium |
| ---------- | ------------ | --------- |--------:|
| Weekday    | ranní spěch | inbound   | x 2,00  |
| Weekday    | ranní spěch | Odchozí  | x 1,00  |
| Weekday    | Denní      | inbound   | x 1,50  |
| Weekday    | Denní      | Odchozí  | x 1,50  |
| Weekday    | večerní spěch | inbound   | x 1,00  |
| Weekday    | večerní spěch | Odchozí  | x 2,00  |
| Weekday    | Přes noc    | inbound   | x 0,75  |
| Weekday    | Přes noc    | Odchozí  | x 0,75  |
| Weekend    | ranní spěch | inbound   | x 1,00  |
| Weekend    | ranní spěch | Odchozí  | x 1,00  |
| Weekend    | Denní      | inbound   | x 1,00  |
| Weekend    | Denní      | Odchozí  | x 1,00  |
| Weekend    | večerní spěch | inbound   | x 1,00  |
| Weekend    | večerní spěch | Odchozí  | x 1,00  |
| Weekend    | Přes noc    | inbound   | x 1,00  |
| Weekend    | Přes noc    | Odchozí  | x 1,00  |

Existuje 16 různých kombinací tří proměnných. Kombinací některých podmínek zjednodušíte konečný výraz přepínače.

Systém, který vybírá mýtné, <xref:System.DateTime> používá strukturu pro čas, kdy bylo mýtné vybráno. Vytvořte členské metody, které vytvářejí proměnné z předchozí tabulky. Následující funkce používá vzor odpovídající přepínač výraz <xref:System.DateTime> vyjádřit, zda představuje víkend nebo den v týdnu:

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

Tato metoda funguje, ale je to opakující se. Můžete jej zjednodušit, jak je znázorněno v následujícím kódu:

[!code-csharp[IsWeekDay](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

Dále přidejte podobnou funkci kategorizovat čas do bloků:

[!code-csharp[GetTimeBand](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

Předchozí metoda nepoužívá porovnávání vzorů. Je to jasnější pomocí známé `if` kaskády prohlášení. Přidáte soukromé `enum` převést každý rozsah času na diskrétní hodnotu.

Po vytvoření těchto metod můžete `switch` použít jiný výraz se **vzorem řazené kolekce členů** k výpočtu cenové prémie. Dalo by `switch` se vytvořit výraz se všemi 16 zbraněmi:

[!code-csharp[FullTuplePattern](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

Výše uvedený kód funguje, ale může být zjednodušen. Všech osm kombinací na víkend má stejnou daň. Všech osm můžete nahradit následujícím řádkem:

```csharp
(false, _, _) => 1.0m,
```

Příchozí i odchozí provoz mají stejný multiplikátor během denních a nočních hodin ve všední den. Tato čtyři ramena spínače mohou být nahrazena těmito dvěma řádky:

```csharp
(true, TimeBand.Overnight, _) => 0.75m,
(true, TimeBand.Daytime, _)   => 1.5m,
```

Kód by měl vypadat jako následující kód po těchto dvou změnách:

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

Nakonec můžete odstranit dvě doby dopravní špičky, které platí běžnou cenu. Jakmile tato ramena vyjmete, můžete je v posledním rameni spínače nahradit `false` výmětem (`_`). Budete mít následující hotovou metodu:

[!code-csharp[SimplifiedTuplePattern](../../../samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

Tento příklad zvýrazní jednu z výhod porovnávání vzorů: větve vzoru jsou vyhodnoceny v pořadí. Pokud je změníte uspořádání tak, aby starší větev zpracovává jeden z vašich pozdějších případů, kompilátor vás upozorní na nedostupný kód. Tato jazyková pravidla usnadnila předchozí zjednodušení s jistotou, že se kód nezměnil.

Porovnávání vzorů umožňuje některé typy kódu čitelnější a nabízí alternativu k objektově orientované techniky, když nelze přidat kód do tříd. Cloud způsobuje, že data a funkce žijí odděleně. *Tvar* dat a *operace* na něm nejsou nutně popsány společně. V tomto kurzu jste spotřebovávají existující data zcela odlišnými způsoby než původní funkce. Porovnávání vzorů vám dalo možnost psát funkce, které tyto typy přeruší, i když je nelze rozšířit.

## <a name="next-steps"></a>Další kroky

Hotový kód si můžete stáhnout z úložiště [GitHub dotnet/samples.](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) Prozkoumejte vzory na vlastní pěst a přidejte tuto techniku do svých pravidelných kódovacích aktivit. Učení těchto technik vám dává jiný způsob, jak přistupovat k problémům a vytvářet nové funkce.
