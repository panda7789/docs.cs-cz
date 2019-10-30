---
title: Použití funkcí pro porovnávání vzorů k rozšiřování datových typů
description: Tento rozšířený kurz ukazuje, jak používat techniky porovnávání vzorů k vytváření funkcionality pomocí dat a algoritmů, které se vytvářejí samostatně.
ms.date: 03/13/2019
ms-technology: csharp-whats-new
ms.custom: mvc
ms.openlocfilehash: ca7ae63a038fce0b2569e7a4bd1805765bc23d44
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039194"
---
# <a name="tutorial-using-pattern-matching-features-to-extend-data-types"></a>Kurz: použití funkcí pro porovnávání vzorů k rozšiřování datových typů

C#7 představil základní funkce pro porovnávání vzorů. Tyto funkce se v C# 8 rozšiřují novými výrazy a vzorci. Můžete napsat funkčnost, která se chová, jako byste rozšířili typy, které mohou být v jiných knihovnách. Další možností použití vzorů je vytvořit funkce, které vaše aplikace vyžaduje, nejedná se o základní funkci typu, který se rozšiřuje.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> - Rozpoznává situace, kde by se měla použít porovnávání vzorů.
> - Použijte výrazy porovnávání vzorů k implementaci chování založeného na typech a hodnotách vlastností.
> - Kombinací porovnávání vzorů s jinými technikami vytvoříte kompletní algoritmy.

## <a name="prerequisites"></a>Požadavky

Musíte nastavit počítač tak, aby běžel .NET Core, včetně kompilátoru C# 8,0. Kompilátor C# 8 je k dispozici počínaje [verzí Visual Studio 2019 verze 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download).

V tomto kurzu se předpokládá, že C# máte zkušenosti s platformou a .NET, včetně sady Visual Studio nebo .NET Core CLI.

## <a name="scenarios-for-pattern-matching"></a>Scénáře pro porovnávání vzorů

Moderní vývoj často zahrnuje integraci dat z více zdrojů a prezentování informací a přehledů z těchto dat v jediné soudržné aplikaci. Vy a váš tým nebude mít kontrolu ani přístup pro všechny typy, které reprezentují příchozí data.

Klasický objektově orientovaný návrh by volal pro vytváření typů ve vaší aplikaci, které reprezentují každý datový typ z těchto více zdrojů dat. Vaše aplikace pak bude pracovat s těmito novými typy, vytvořit Hierarchie dědičnosti, vytvářet virtuální metody a implementovat abstrakce. Tyto techniky fungují a někdy jsou nejlepšími nástroji. Jindy můžete psát méně kódu. Můžete psát více jasných kódů pomocí technik, které oddělují data z operací, které manipulují s těmito daty.

V tomto kurzu vytvoříte a prozkoumáte aplikaci, která bude v jednom scénáři přijímat příchozí data z několika externích zdrojů. Uvidíte, jak **porovnávání vzorů** poskytuje efektivní způsob, jak spotřebovávat a zpracovávat tato data způsobem, který nebyl součástí původního systému.

Vezměte v úvahu hlavní metropolitní oblast, která využívá mýtné a ceny za špičku ke správě provozu. Napíšete aplikaci, která vypočítá mýtné pro vozidlo na základě jeho typu. Pozdější vylepšení zahrnují ceny na základě počtu uživatelů v rámci vozidla. Další vylepšení přidávají ceny na základě času a dne v týdnu.

Z tohoto krátkého popisu jste mohli rychle vykreslit hierarchii objektů k modelování tohoto systému. Vaše data ale pocházejí z několika zdrojů, jako jsou jiné systémy pro správu registrace vozidel. Tyto systémy poskytují různé třídy pro modelování dat a nemáte jeden objektový model, který můžete použít. V tomto kurzu použijete tyto zjednodušené třídy pro modelování dat vozidel z těchto externích systémů, jak je znázorněno v následujícím kódu:

[!code-csharp[ExternalSystems](~/samples/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

Počáteční kód si můžete stáhnout z úložiště [dotnet/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) GitHub. Můžete vidět, že třídy vozidel jsou z různých systémů a jsou v různých oborech názvů. Není možné využít žádnou společnou základní třídu, kromě `System.Object`.

## <a name="pattern-matching-designs"></a>Vzory porovnávání vzorů

Scénář použitý v tomto kurzu zvýrazňuje druhy problémů, které porovnávání vzorů je vhodné pro řešení:

- Objekty, se kterými potřebujete pracovat, nejsou v hierarchii objektů, které odpovídají vašim cílům. Možná budete pracovat s třídami, které jsou součástí nesouvisejících systémů.
- Funkce, kterou přidáváte, není součástí základní abstrakce pro tyto třídy. Telefonní linka *placená změnou vozidla pro různé* typy vozidel, ale placená linka není základní funkcí vozidla.

Pokud *tvar* dat a *operace* na těchto datech nejsou popsány společně, funkce pro porovnávání vzorů v C# nástroji usnadňuje práci s.

## <a name="implement-the-basic-toll-calculations"></a>Implementace základních výpočtů mýtné

Základní výpočet placená linka se spoléhá jenom na typ vozidla:

- `Car` je $2,00.
- `Taxi` je $3,50.
- `Bus` je $5,00.
- `DeliveryTruck` je $10,00

Vytvořte novou třídu `TollCalculator` a implementujte porovnávání vzorů pro typ vozidla, abyste získali hodnotu mýtné. Následující kód ukazuje počáteční implementaci `TollCalculator`.

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

Předchozí kód používá **výraz Switch** (není stejný jako příkaz [`switch`](../language-reference/keywords/switch.md) ), který testuje **vzor typu**. **Výraz Switch** začíná proměnnou, `vehicle` v předchozím kódu následovaný klíčovým slovem `switch`. Dál přijde všechna **ramena přepínače** uvnitř složených závorek. Výraz `switch` umožňuje další upřesnění syntaxe, která obklopuje příkaz `switch`. Klíčové slovo `case` je vynecháno a výsledek každého ARM je výraz. Poslední dvě paže zobrazují novou funkci jazyka. `{ }` Case odpovídá jakémukoli objektu, který není null, který se neshodoval s dřívějším procesorem ARM. Tato ARM zachytí všechny nesprávné typy předané do této metody.  `{ }` případ musí splňovat jednotlivé typy vozidel. Pokud byla objednávka stornována, má `{ }` případ přednost. A konečně, `null` vzor detekuje, když se do této metody předává `null`. Vzor `null` může být poslední, protože jiné vzorce typu odpovídají pouze nenulovému objektu správného typu.

Tento kód můžete otestovat pomocí následujícího kódu v `Program.cs`:

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

Tento kód je obsažen v projektu Starter, ale je označen jako komentář. Odstraňte komentáře a můžete testovat, co jste napsali.

Začínáte, jak vzory vám pomohou vytvořit algoritmy, kde je kód a data odděleny. Výraz `switch` testuje typ a vytváří různé hodnoty na základě výsledků. To je jenom začátek.

## <a name="add-occupancy-pricing"></a>Přidat ceny obsazení

Autorita pro telefonní linky chce, aby dokázala povzbudit kapacitu vozidel při maximální kapacitě. Rozhodla se doúčtovat více, pokud vozidlo má méně cestujících, a podporuje plná vozidla tím, že nabízí nižší ceny:

- Automobily a Taxis bez cestujících platíte navíc $0,50.
- Automobily a Taxis se dvěma cestujícími získají slevu $0,50.
- Automobily a Taxis se třemi nebo více cestujícími získají slevu $1,00.
- Na sběrnicích, které jsou menší než 50%, se zaplatí extra $2,00.
- Pro autobusy, které jsou v plném rozsahu 90%, se zobrazí sleva $1,00.

Tato pravidla lze implementovat pomocí **vzoru vlastnosti** ve stejném výrazu přepínače. Po určení typu se vzorek vlastnosti prověřuje vlastnostmi objektu. Jednotlivý případ `Car` se rozšíří na čtyři různé případy:

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

První tři případy testují typ jako `Car`a pak zkontrolují hodnotu vlastnosti `Passengers`. Pokud oba odpovídají, vyhodnotí se tento výraz a vrátí se.

Také rozšíříte případy pro Taxis podobným způsobem:

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

V předchozím příkladu byla klauzule `when` v konečném případě vynechána.

Dále implementujte pravidla obsazení rozšířením případů pro autobusy, jak je znázorněno v následujícím příkladu:

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

Autorita pro telefonní linky se netýká počtu cestujících v dodacích vozíkech. Místo toho upraví hodnotu mýtné na základě váhy třídy nákladových vozíků následujícím způsobem:

- Za vozíky nad 5000 kg se účtuje extra $5,00.
- Lehkými nákladními za 3000 kg se předává sleva $2,00.

Toto pravidlo je implementováno s následujícím kódem:

```csharp
vehicle switch
{
    // ...

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

Předchozí kód ukazuje klauzuli `when` ARM přepínače. Použijte klauzuli `when` pro testování jiných podmínek než rovnosti u vlastnosti. Až budete hotovi, budete mít metodu, která vypadá podobně jako následující:

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

Mnohé z těchto palných zbraní jsou příklady **rekurzivních vzorů**. Například `Car { Passengers: 1}` zobrazuje v rámci vzoru vlastnosti konstantní vzorek.

Pomocí vnořených přepínačů můžete tento kód méně vyměnit. V předchozích příkladech mají `Car` a `Taxi` obě různé zbraně. V obou případech můžete vytvořit vzor typu, který bude informační kanál do vzoru vlastnosti. Tato technika je znázorněna v následujícím kódu:

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

V předchozím příkladu použití rekurzivního výrazu znamená, že neopakujete `Car` a `Taxi` zbraně obsahující podřízená ramena, která testují hodnotu vlastnosti. Tato technika se nepoužívá pro `Bus` a `DeliveryTruck` zbraně, protože tyto zbraně jsou testovací rozsahy pro vlastnost, nikoli diskrétní hodnoty.

## <a name="add-peak-pricing"></a>Přidat ceny ve špičce

U konečné funkce chce autorita pro telefonní linky přidat ceny za špičku v časově citlivém čase. Během ráno a večer nespěcháte hodin se telefonní linky zdvojnásobí. Toto pravidlo má vliv pouze na provoz v jednom směru: příchozí na město v ráno a odchozí v večer nespěcháte hodinu. Během jiné doby během pracovního dne se telefonní linky zvyšují o 50%. Pozdě v noci a včas ráno se telefonní linky snižují o 25%. Během víkendu se jedná o normální sazbu bez ohledu na čas.

Pro tuto funkci použijete porovnávání vzorů, ale budete je integrovat s jinými technikami. Můžete sestavit výraz porovnávání s jednou maskou, který by měl být v souladu se všemi kombinacemi směr, den v týdnu a čas. Výsledkem by byl složitý výraz. Bylo těžké ho přečíst a obtížně pochopit. Díky tomu je obtížné zajistit správnost. Místo toho Zkombinujte tyto metody pro sestavení řazené kolekce členů hodnot, které stručně popisují všechny tyto stavy. Pak použijte porovnávání vzorů k výpočtu násobitele pro mýtné. Řazená kolekce členů obsahuje tři diskrétní podmínky:

- Den je buď den v týdnu, nebo víkend.
- Časové pásmo, ve kterém se má linka nashromáždit.
- Směr je na město nebo od města.

V následující tabulce jsou uvedeny kombinace vstupních hodnot a násobitele cen ve špičce:

| Den        | Interval         | Směr | Nárok |
| ---------- | ------------ | --------- |--------:|
| Názvy    | ráno nespěcháte | Příjem   | × 2,00  |
| Názvy    | ráno nespěcháte | Komunikace  | × 1,00  |
| Názvy    | Daytime      | Příjem   | × 1,50  |
| Názvy    | Daytime      | Komunikace  | × 1,50  |
| Názvy    | večerní nespěcháte | Příjem   | × 1,00  |
| Názvy    | večerní nespěcháte | Komunikace  | × 2,00  |
| Názvy    | přes noc    | Příjem   | × 0,75  |
| Názvy    | přes noc    | Komunikace  | × 0,75  |
| Volné    | ráno nespěcháte | Příjem   | × 1,00  |
| Volné    | ráno nespěcháte | Komunikace  | × 1,00  |
| Volné    | Daytime      | Příjem   | × 1,00  |
| Volné    | Daytime      | Komunikace  | × 1,00  |
| Volné    | večerní nespěcháte | Příjem   | × 1,00  |
| Volné    | večerní nespěcháte | Komunikace  | × 1,00  |
| Volné    | přes noc    | Příjem   | × 1,00  |
| Volné    | přes noc    | Komunikace  | × 1,00  |

Existují 16 různých kombinací tří proměnných. Kombinací některých podmínek zjednodušete výraz finálního přepínače.

Systém, který shromažďuje mýtné, používá strukturu <xref:System.DateTime> pro čas, kdy byla placená linka shromažďována. Sestavujte členské metody, které vytvoří proměnné z předchozí tabulky. Následující funkce používá výraz porovnávání vzorů k vyjádření, zda <xref:System.DateTime> představuje víkend nebo den v týdnu:

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

Tato metoda funguje, ale je repetitious. Můžete ho zjednodušit, jak je znázorněno v následujícím kódu:

[!code-csharp[IsWeekDay](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

Dále přidejte podobnou funkci pro kategorizaci času do bloků:

[!code-csharp[GetTimeBand](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

Předchozí metoda nepoužívá porovnávání vzorů. Je jasné, že se seznámíte s `if`mi příkazy. Můžete přidat privátní `enum` pro převod jednotlivých časových úseků na samostatnou hodnotu.

Po vytvoření těchto metod můžete použít jiný výraz `switch` se **vzorem řazené kolekce členů** pro výpočet cenové úrovně Premium. Můžete sestavit výraz `switch` se všemi 16 opěrkami rukou:

[!code-csharp[FullTuplePattern](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

Výše uvedený kód funguje, ale může být zjednodušený. Všechny osm kombinací pro daný víkend mají stejnou mýtné. Všechna osm můžete nahradit následujícím řádkem:

```csharp
(false, _, _) => 1.0m,
```

Příchozí i odchozí provoz mají stejný násobitel během dne v týdnu denní a jednodenních hodin. Tyto čtyři paže s přepínačem lze nahradit následujícími dvěma řádky:

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

Nakonec můžete odebrat dvě nespěcháte hodiny, které platí pro běžnou cenu. Po odebrání těchto zbraní můžete `false` nahradit pomocí zahození (`_`) v konečném přepínači ARM. Budete mít následující metodu, kterou jste dokončili:

[!code-csharp[SimplifiedTuplePattern](../../../samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

Tento příklad zvýrazňuje jednu z výhod porovnávání vzorů: větve vzorů jsou vyhodnocovány v pořadí. V případě, že je změníte jejich uspořádání tak, aby předchozí větev zpracovává jeden z vašich pozdějších případů, kompilátor vás upozorní na nedosažitelný kód. Tato jazyková pravidla usnadňují provádění předchozích zjednodušení s jistotou, že se kód nezměnil.

Porovnávání vzorů usnadňuje čtení některých typů kódu a nabízí alternativu k objektově orientovaným technikám, když nemůžete přidat kód do tříd. Cloud způsobuje živá data a funkce. *Tvar* dat a jeho *operace* nejsou nutně popsány společně. V tomto kurzu jste ze své původní funkce využili stávající data zcela různými způsoby. Porovnávání vzorů vám dává možnost psát funkce, které tyto typy overrode, i když je nemůžete roztáhnout.

## <a name="next-steps"></a>Další kroky

Hotový kód si můžete stáhnout z úložiště GitHub [/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) GitHub. Prozkoumejte vlastní modely a přidejte tuto techniku do vašich běžných kódovacích aktivit. Výukové postupy poskytují další způsob přístupu k problémům a vytváření nových funkcí.
