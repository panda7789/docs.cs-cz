---
title: Kurz interpolace řetězce – místní rychlé starty C#
description: Tento rychlý start ukazuje, jak používat funkce interpolace řetězců C# zahrnout výsledky formátovaný výrazu ve větším řetězci.
author: rpetrusha
ms.author: ronpet
ms.date: 04/14/2018
ms.custom: mvc
ms.openlocfilehash: da111790ebbc299df16297650347045b9395a90f
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47201047"
---
# <a name="string-interpolation"></a>Interpolace řetězců

V tomto rychlém startu se naučíte, jak pomocí jazyka C# [interpolace](../language-reference/tokens/interpolated.md) k vložení hodnoty do jedné výsledného řetězce. Napíšete kód v C# a zobrazovat výsledky kompilace a spuštění. Tento rychlý Start obsahuje posloupnost lekcí, které ukazují, jak se vkládání hodnot do řetězce a tyto hodnoty formátují různými způsoby.

V tomto rychlém startu očekává, že máte počítač, který používáte pro vývoj. Téma .NET [zahájení práce během 10 minut](https://www.microsoft.com/net/core) obsahuje pokyny pro nastavení místního vývojového prostředí v Mac, PC nebo Linux. Je rychlý přehled toho, příkazy, které použijete v [Úvod do místní rychlých startů](local-environment.md) s odkazy na další podrobnosti. Můžete také použít [interaktivní verze](interpolated-strings.yml) části tohoto rychlého startu ve vašem prohlížeči.

## <a name="create-an-interpolated-string"></a>Vytvoření interpolovaného řetězce

Vytvořte adresář **interpolované**. Byl do aktuálního adresáře a spusťte následující příkaz z okna konzoly:

```console
dotnet new console
```

Tento příkaz vytvoří novou konzolovou aplikaci .NET Core v aktuálním adresáři.

Otevřít **Program.cs** ve svém oblíbeném editoru a nahraďte řádek `Console.WriteLine("Hello World!");` následujícím kódem, ve kterém nahradíte `<name>` s názvem:

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

Vyzkoušejte tento kód tak, že zadáte `dotnet run` v okně konzoly. Při spuštění programu se zobrazí jeden řetězec, který obsahuje vaše jméno pozdrav. Řetězec obsažený ve <xref:System.Console.WriteLine%2A> je volání metody *interpolovaný řetězec*. Je druh šablony, který umožňuje vytvořit jeden řetězec (volá se, *výsledný řetězec*) z řetězce obsahujícího vložený kód. Interpolované řetězce se hodí hlavně k vkládání hodnot do řetězce nebo k řetězení (spojování) řetězců.

Tento jednoduchý příklad obsahuje dva elementy, které musí mít každém interpolovaném řetězci povinné:

- Řetězcový literál, který začíná `$` znak, před jeho znakem uvozovek. Nesmí být žádné mezery mezi `$` symbolů a znakem uvozovek. (Pokud jste chtěli naleznete v tématu co se stane, když tak přece, vkládat mezeru po `$` znak, uložte soubor a znovu spusťte program zadáním `dotnet run` v okně konzoly. Kompilátor jazyka C# se zobrazí chybová zpráva "Chyba CS1056: Neočekávaný znak"$"".)

- Jeden nebo více *interpolovaných výrazů*. Interpolovaný výraz se vyznačuje otevírací a zavírací závorkou (`{` a `}`). Můžete vložit libovolný výraz C#, která vrací hodnotu (včetně `null`) uvnitř složených závorek.

Teď si vyzkoušíme pár dalších příkladů interpolace řetězce, s jinými datovými typy.

## <a name="include-different-data-types"></a>Zahrnutí různých datových typů

V předchozí části jste použili interpolace řetězců vložili jeden řetězec do druhého. Výsledek interpolovaného výrazu může být libovolného datového typu, ale. Umožňuje zahrnout hodnoty různých datových typů v interpolovaném řetězci.

V následujícím příkladu nejdřív nadefinujeme [třídy](../programming-guide/classes-and-structs/classes.md) datový typ `Vegetable` , který má `Name` [vlastnost](../properties.md) a `ToString` [metoda](../methods.md), který [přepíše](../language-reference/keywords/override.md) chování <xref:System.Object.ToString?displayProperty=nameWithType> metody. [ `public` Modifikátor přístupu](../language-reference/keywords/public.md) zpřístupní metody pro jakýkoli kód klienta, k získání řetězcové reprezentace `Vegetable` instance. V příkladu `Vegetable.ToString` metoda vrátí hodnotu `Name` vlastnost, která je inicializována na `Vegetable` [konstruktor](../programming-guide/classes-and-structs/constructors.md):

```csharp
public Vegetable(string name) => Name = name;
```

Pak vytvoříme instanci `Vegetable` pomocí [ `new` – klíčové slovo](../language-reference/keywords/new-operator.md) a poskytují parametr name pro konstruktor `Vegetable`:

```csharp
var item = new Vegetable("eggplant");
```

Nakonec jsme zahrnuli `item` proměnné v interpolovaném řetězci, který také obsahuje <xref:System.DateTime> hodnotu, <xref:System.Decimal> hodnotu a `Unit` [výčet](../programming-guide/enumeration-types.md) hodnotu. Veškerý kód jazyka C# ve svém editoru nahraďte následujícím kódem a pak použít `dotnet run` příkazu ho spusťte:

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
   public enum Unit { item, kilogram, gram, dozen };

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

Všimněte si, že interpolovaný výraz `item` v interpolovaném řetězci se překládá na text "eggplant" ve výsledném řetězci. Je to proto, že pokud typ výsledku výrazu není řetězec, výsledek je přeložen na řetězec následujícím způsobem:

- Pokud interpolovaný výraz vyhodnocen `null`, prázdný řetězec ("", nebo <xref:System.String.Empty?displayProperty=nameWithType>) se používá.

- Pokud interpolovaný výraz se nevyhodnocuje na `null`, obvykle `ToString` je volána metoda typ výsledku. Můžete ho otestovat provádění aktualizací `Vegetable.ToString` metody. Ještě není nutné implementovat `ToString` metoda vzhledem k tomu, že každý typ má některé implementace této metody. Abyste to mohli otestovat, okomentujte definici `Vegetable.ToString` metoda v příkladu (stačí vložit symbol komentáře `//`, před). Ve výstupu se řetězec "eggplant" nahradí podle plně kvalifikovaného názvu ("rostlinné" v tomto příkladu), což je výchozí chování sady <xref:System.Object.ToString?displayProperty=nameWithType> metody. Výchozí chování `ToString` metodou hodnota výčtu je vrátí řetězcovou reprezentaci hodnoty.

Ve výstupu tohoto příkladu je datum zbytečně přesné (cena lilku nemění každou sekundu) a hodnota ceny neuvádí jednotku měny. V další části se dozvíte, jak tyto problémy napravit prostřednictvím nastavení formátu řetězcové reprezentace výsledku výrazu.

## <a name="control-the-formatting-of-interpolated-expressions"></a>Ovládací prvek formátu interpolovaných výrazů

V předchozí části vložily dva špatně naformátované řetězce do výsledného řetězce. Jedna se hodnoty data a času, pro který byl pouze data odpovídající. Druhým byla cena, která nebyla označení jednotku měny. Jsou oba problémy můžeme snadno vyřešit. Interpolace řetězců umožňuje určit *řetězce formátu* , které nastavují formátování konkrétních typů. Upravte volání `Console.WriteLine` z předchozího příkladu zahrnout formátovací řetězce pro výrazy data a ceny, jak je znázorněno na následujícím řádku:

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

Zadejte řetězec formátu podle interpolovaný výraz s čárkou (":") a nakonec formátovací řetězec. "d" je [řetězec formátu data a času](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) , která představuje formátu krátkého data. "C2" je [řetězec standardního číselného formátu](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) , který představuje číslo jako hodnotu měny se dvěma číslicemi za desetinnou čárkou.

Počet typů v knihovny .NET podporují předdefinovanou množinu řetězců formátu. Patří mezi ně číselné typy a typy data a času. Úplný seznam typů podporujících formátovací řetězce, naleznete v tématu [formátovací řetězce a typy v knihovně tříd rozhraní .NET](../../standard/base-types/formatting-types.md#stringRef) v [formátovací typy v .NET](../../standard/base-types/formatting-types.md) článku.

Zkuste upravit formátovací řetězce v textovém editoru a pokaždé, když provedete změnu, znovu spusťte aplikaci a zjistěte, jak změny se projeví u formátování data a času a číselné hodnoty. Změňte "d" v `{date:d}` "t" (pro zobrazení formátu krátkého formátu času), "y" (zobrazí se rok a měsíc) a "yyyy" (zobrazí se rok jako čtyřmístné číslo). Změňte "C2" v `{price:C2}` "e" (pro exponenciální notaci) a "F3" (pro číselnou hodnotu, s třemi číslicemi za desetinnou čárkou).

Vedle nastavení formátování můžete také řídit šířku pole a zarovnání formátovaného řetězce, které jsou obsaženy ve výsledném řetězci. V další části se dozvíte, jak na to.

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a>Řídit šířku pole a zarovnání interpolovaných výrazů

Obvykle když výsledek interpolovaného výrazu má formát na řetězec, tento řetězec je součástí výsledného řetězce bez úvodní a koncové mezery. Zejména při práci se sadou dat, nebudou moct řídit šířku pole a zarovnání textu pomáhá lépe čitelný výstup. Tento údaj zobrazíte, veškerý kód v textovém editoru nahraďte následujícím kódem, zadejte `dotnet run` spuštění programu:

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

Jména autorů jsou zarovnané vlevo a názvy, které vytvořil jsou zarovnaná vpravo. Zarovnání určíte přidáním čárky (",") po interpolovaný výraz a uvedením *minimální* šířku pole. Pokud zadaná hodnota je kladné číslo, pole zarovnané vpravo. Pokud je záporné číslo, pole zarovnané vlevo.

Zkuste odstranit záporná znaménka z `{"Author",-25}` a `{title.Key,-25}` kód a znovu spustit příklad jako následující kód:

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

Tentokrát, informace o autorovi zarovnán doprava.

Specifikátor zarovnání a řetězec formátu pro jednom interpolovaném výrazu můžete kombinovat. K tomuto účelu Určuje zarovnání nejprve, za nímž následuje dvojtečka a nakonec formátovací řetězec. Nahraďte kód uvnitř `Main` definována metoda následujícím kódem, který zobrazí tři zformátované řetězce s určenými šířkami polí. Potom spusťte program zadáním `dotnet run` příkazu.

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

Výstup bude vypadat přibližně takto:

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

Dokončili jste rychlý start interpolace řetězce.

Můžete pokračovat [seznamu kolekce](arrays-and-collections.md) rychlý start ve svém vlastním vývojovém prostředí.

Další informace najdete v tématu [interpolace](../language-reference/tokens/interpolated.md) tématu a [interpolace v jazyce C#](../tutorials/string-interpolation.md) kurzu.
