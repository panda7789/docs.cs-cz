---
title: Řetězec interpolace kurz – C# místní – elementy QuickStart
description: Tento rychlý start ukazuje, jak pomocí funkce interpolace řetězec jazyka C# lze zahrnout výsledky formátovaný výraz větší řetězce.
author: rpetrusha
ms.author: ronpet
ms.date: 04/14/2018
ms.custom: mvc
ms.openlocfilehash: 5af7cf1d0f541661acb23ec2cad4bada5d9e03e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="string-interpolation"></a>Řetězec interpolace

Tento rychlý start se naučíte, jak používat C# [řetězec interpolace](../language-reference/tokens/interpolated.md) vložení hodnoty do jednoho výsledný řetězec. Psaní kódu jazyka C# a zobrazit výsledky kompilace a jejím spuštěním. Rychlý Start obsahuje řadu lekce, které ukazují, jak a vložení hodnoty do řetězce formátu tyto hodnoty různými způsoby.

Tento rychlý start očekává, že máte počítače, které můžete použít pro vývoj. Téma .NET [Začínáme za 10 minut](https://www.microsoft.com/net/core) obsahuje pokyny pro nastavení místního vývojového prostředí v Mac, počítače nebo Linux. Rychlý přehled o příkazy, které budete používat je ve [Úvod do místní quickstarts](local-environment.md) s odkazy na další podrobnosti. Můžete také provést [interaktivní verze](interpolated-strings.yml) z tento rychlý start v prohlížeči.

## <a name="create-an-interpolated-string"></a>Vytvoření interpolované řetězce

Vytvořte adresář s názvem **interpolované**. Ho nastavit aktuální adresář a v okně konzoly spusťte následující příkaz:

```console
dotnet new console
```

Tento příkaz vytvoří novou konzolovou aplikaci .NET Core v aktuálním adresáři.

Otevřete **Program.cs** v oblíbeném editoru a nahraďte řádku `Console.WriteLine("Hello World!");` následujícím kódem, kde nahradíte `<name>` nahraďte názvem:

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

Zkuste tento kód zadáním `dotnet run` v okně konzoly. Když spustíte program, zobrazí jeden řetězec, který obsahuje název vaší v pozdrav. Řetězec, které jsou součástí <xref:System.Console.WriteLine%2A> volání metody, které je *interpolované řetězce*. Je typ šablony, která umožňuje vytvořit jeden řetězec (volat *způsobit řetězec*) z řetězce, který obsahuje integrovaný kód. Interpolované řetězce jsou obzvláště užitečná pro vložení hodnoty do řetězec nebo řetězce zřetězení (spojení).

Tento jednoduchý příklad obsahuje dva elementy, které musí mít každý interpolované řetězce:

- Řetězcový literál, který začíná `$` znak před jeho otevření nabídky označit znak. Nesmí být žádné mezery mezi `$` symbolů a znak uvozovky. (Pokud byste chtěli vidět co se stane, když obsahují jeden, mezeru po vložení `$` znak, soubor uložte a program spusťte znovu zadáním `dotnet run` v okně konzoly. Jazyce C# kompilátoru zobrazí chybovou zprávu, "Chyba CS1056: Neočekávaný znak"$"".)

- Jeden nebo více *interpolované výrazy*. Interpolované výrazu je indikován otevírací a uzavírací závorku (`{` a `}`). Můžete vložit jakékoli C# výraz, který vrací hodnotu (včetně `null`) uvnitř složené závorky.

Nyní si vyzkoušíte několik další příklady interpolace řetězce, pomocí některé jiné datové typy.

## <a name="include-different-data-types"></a>Zahrnout různé datové typy

V předchozí části použít řetězec interpolace vložit jeden řetězec uvnitř jiného. Výsledek interpolované výraz může být jakékoli datového typu, ale. Umožňuje zahrnout hodnoty různých datových typů v interpolované řetězce.

V následujícím příkladu se nejdřív jsme definovali vlastní datový typ `Vegetable` který má `Name` [vlastnost](../properties.md) a `ToString` metoda. Kód klienta tuto metodu můžete použít k získání řetězcovou reprezentaci `Vegetable` instance. V příkladu `Vegetable.ToString` metoda vrátí hodnotu `Name` vlastnost, která je inicializován v `Vegetable` konstruktor:

```csharp
public Vegetable(string name) => Name = name;
```

Nemůžeme vytvořit instanci `Vegetable` typu pomocí `new` – klíčové slovo a poskytuje název parametr pro konstruktor `Vegetable`:

```csharp
var item = new Vegetable("eggplant");
```

Nakonec zahrnuta `item` proměnné do interpolované řetězce, který také obsahuje <xref:System.DateTime> hodnotu, <xref:System.Decimal> hodnotu a `Unit` [– výčet](../programming-guide/enumeration-types.md) hodnotu. Nahraďte kód C# ve svém editoru následujícím kódem a pak použijte `dotnet run` příkaz spouštět:

```csharp
using System;

public class Vegetable
{
   public Vegetable(string name) => Name = name;
   
   public string Name { get; }
   
   public override string ToString() => Name;
}

public class Program
{
   public enum Unit { item, pound, ounce, dozen };

   public static void Main()
   {
      var item = new Vegetable("eggplant");
      var date = DateTime.Now;
      var price = 1.99m;
      var unit = Unit.item;
      Console.WriteLine($"On {date}, the price of {item} was {price} per {unit}.");
   }
}
```

Všimněte si, že interpolované výraz `item` interpolované řetězce přeloží na text "Lilek" ve výsledném řetězci. Důvodem je, že pokud typ výsledku výrazu není řetězec, výsledek je přeložit na řetězec následujícím způsobem:

- Pokud je výsledkem výrazu interpolované `null`, prázdný řetězec ("", nebo <xref:System.String.Empty?displayProperty=nameWithType>) se používá.

- Pokud není vyhodnocení interpolované výraz `null`, obvykle `ToString` je volána metoda typ výsledku. Toto můžete otestovat aktualizací implementace `Vegetable.ToString` metoda. Může i není implementovat `ToString` metoda vzhledem k tomu, že každý typ dat C# má některé implementace této metody. Otestujte, jestli, komentář definice `Vegetable.ToString` metoda v příkladu (k tomu, put symbol komentáře `//` úrovních před ním). Ve výstupu řetězec "Lilek" nahrazuje plně kvalifikovaného názvu ("rostlinné" v tomto příkladu), což je výchozí chování z <xref:System.Object.ToString?displayProperty=nameWithType> metoda. Výchozí chování `ToString` metodou pro typ výčtu je vrátí řetězcovou reprezentaci hodnoty použít v definici výčtu.

Ve výstupu z tohoto příkladu datum je příliš přesné (cenu lilek nemění za sekundu) a hodnotu ceny neznamená jednotku měny. V další části dozvíte, jak vyřešit tyto problémy kontrolou formát řetězcové vyjádření výsledků výrazu.

## <a name="control-the-formatting-of-interpolated-expressions"></a>Ovládací prvek formátování interpolované výrazy

V předchozí části byly dva řetězce chybně formátovaný vložena do řetězce výsledek. Jeden se hodnoty data a času, pro kterou se příslušná pouze datum. Druhá se ceny, které nebylo signalizovat jeho jednotku měny. Obě tyto chyby lze snadno adresu. Řetězec interpolace umožňuje určit *řetězce formátu* které řídí formátování konkrétní typy. Upravit volání `Console.WriteLine` z předchozího příkladu zahrnout řetězce formátu pro data a cena výrazy, jak je znázorněno na následujícím řádku:

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

Zadejte řetězec, ve formátu podle interpolované výraz s dvojtečkou (":") a řetězec formátu. "d" je [řetězec formátu standardní hodnoty data a času](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) představující formát krátkého data. Je "C2" [standardního řetězce formátu čísel](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) představující číslo jako hodnotu měny s dvě číslice za desetinnou čárkou.

Počet typů v na knihovny .NET podporují předdefinovanou sadu řetězce formátu. Mezi ně patří všechny číselnými typy a typy data a času. Úplný seznam typů, které podporují řetězce formátu najdete v tématu [řetězce formátu a typy knihovna tříd rozhraní .NET](../../standard/base-types/formatting-types.md#stringRef) v [typy formátování v .NET](../../standard/base-types/formatting-types.md) článku.

Zkuste upravit řetězce formátu v textovém editoru a pokaždé, když provedete změny, znovu spusťte aplikaci a zjistěte, jak vliv budou změny mít formátování data a času a číselná hodnota. Změňte "d" v `{date:d}` k "t" (zobrazíte na formát krátkého času), "y" (zobrazíte za rok a měsíc) a "rrrr" (pro zobrazení v roce jako čtyřmístné číslo). Změňte "C2" v `{price:C2}` "e" (pro exponenciální zápis) a "F3" (pro číselná hodnota se tři číslice za desetinnou čárkou).

Kromě řízení, formátování, můžete také ovládat šířku pole a zarovnání formátované řetězce, které jsou zahrnuté ve výsledném řetězci. V další části dozvíte, jak to provést.

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a>Řídit šířku pole a zarovnání interpolované výrazů

Normálně Pokud je výsledkem výrazu interpolované formátována na řetězec, tento řetězec je součástí výsledný řetězec bez počáteční nebo koncové mezery. Zejména při práci s sadu dat, bude možné řídit šířku pole a zarovnání textu pomáhá k vytváření srozumitelnější výstupu. Toto nahraďte všechny kód v textovém editoru následujícím kódem zobrazíte zadáním `dotnet run` spuštění programu:

```csharp
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var titles = new Dictionary<string, string>()
      {
          ["Doyle, Arthur Conan"] = "Hound of the Baskervilles, The",
          ["London, Jack"] = "Call of the Wild, The",
          ["Shakespeare, William"] = "Tempest, The"
      };

      Console.WriteLine("Author and Title List");
      Console.WriteLine();
      Console.WriteLine($"|{"Author",-25}|{"Title",30}|");
      foreach (var title in titles)
         Console.WriteLine($"|{title.Key,-25}|{title.Value,30}|");
   }
}
```

Názvy autoři jsou zarovnaný doleva a názvy, které vytvořil zarovnaný doprava. Zadejte zarovnání přidáním čárkou (",") po interpolované výrazu a určení *minimální* pole Šířka. Pokud zadaná hodnota je kladné číslo, je pole zarovnaný doprava. Pokud je na záporné číslo, pole je zarovnaný doleva.

Zkuste odebrat záporné přihlásí z `{"Author",-25}` a `{title.Key,-25}` kód a spusťte v příkladu znovu, protože následující kód:

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

Čas, informace o autorovi je zarovnaný doprava.

Můžete kombinovat specifikace zarovnání a řetězec formátu pro jeden výraz interpolované. K tomu, zadejte zarovnání nejprve následovaný dvojtečkou a řetězec formátu. Nahraďte kód uvnitř `Main` metoda následujícím kódem, který zobrazuje tři formátované řetězce s definované šířky polí. Potom spusťte program zadáním `dotnet run` příkaz.

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

Výstup bude vypadat přibližně takto:

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

Jste dokončili rychlé spuštění interpolace řetězec.

Můžete pokračovat [seznamu kolekce](arrays-and-collections.md) rychlé spuštění ve vašem vývojovém prostředí.

Další informace o řetězce interpolace v [řetězec interpolace](../language-reference/tokens/interpolated.md) téma v referenční dokumentace jazyka C#.
