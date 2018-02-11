---
title: "Interpolované řetězce kurz – C# místní – elementy QuickStart"
description: "V tento rychlý start o interpolované řetězce zapisovat do incude výsledek výrazu v řetězci větší kód C#."
author: rpetrusha
ms.author: ronpet
ms.date: 01/11/2018
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 02d06401f16c6205a88a42e7624b8e39ac6473cc
ms.sourcegitcommit: be1fb5d9447ad459bef22b91a91c72e3e0b2d916
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2018
---
# <a name="interpolated-strings"></a>Interpolované řetězce

Tento rychlý start se naučíte, jak používat interpolované řetězce v jazyce C# k vložení hodnoty do řetězec jeden výstup. Psaní kódu jazyka C# a zobrazit výsledky kompilace a jejím spuštěním. Rychlý Start obsahuje řadu lekce, které vložení hodnoty do řetězce a formátování tyto hodnoty různými způsoby.

Tento rychlý start očekává, že máte počítače, které můžete použít pro vývoj. Téma .NET [Začínáme za 10 minut](https://www.microsoft.com/net/core) obsahuje pokyny pro nastavení místního vývojového prostředí v Mac, počítače nebo Linux. Rychlý přehled o příkazy, které budete používat je ve [Úvod do místní quickstarts](local-environment.md) s odkazy na další podrobnosti. 

## <a name="create-an-interpolated-string"></a>Vytvoření interpolované řetězce

Vytvořte adresář s názvem **interpolované rychlý Start**. Ho nastavit aktuální adresář a v okně konzoly spusťte následující příkaz:

```console
dotnet new console -n interpolated -o .
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

Nyní si vyzkoušíte několik příkladů více interpolované řetězce s jiné datové typy.
    
## <a name="include-different-data-types"></a>Zahrnout různé datové typy

V předchozí části použít interpolované řetězce k vložení jednoho řetězce v rámci jiného. Výraz interpolované řetězce mohou být jakéhokoli typu dat, ale. Nyní si vyzkoušíte interpolované řetězec, který obsahuje hodnoty více datových typů. 
    
Následující příklad obsahuje interpolované výrazy s `Vegetable` objektu, členem `Unit` výčtu <xref:System.DateTime> hodnotu a <xref:System.Decimal> hodnotu. Nahraďte kód C# ve svém editoru následujícím kódem a pak použijte `console run` příkaz spouštět:

```csharp
using System;

public class Vegetable
{
   public Vegetable(string name) => Name = name;
   
   public string Name { get; }
   
   public override string ToString() => Name;
}

public class Example
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
    
Všimněte si, že druhá interpolované výraz obsahuje `item` objektu ve výsledném řetězci, který se zobrazí konzole a v takovém případě je řetězec "Lilek" vložena do řetězce výsledek. Důvodem je, že pokud není typ výrazu interpolované řetězce, kompilátor jazyka C# provede následující akce:

- Pokud je interpolované výraz `null`, interpolované výraz vrátí prázdný řetězec ("", nebo <xref:System.String.Empty?displayProperty=nameWithType>).

- Pokud není interpolované výraz `null`, `ToString` je volána metoda typu interpolované výrazu. Toto můžete otestovat pomocí komentářů se definice `Vegetable.ToString` metoda v příkladu umístěním symbol komentáře (`//`) úrovních před ním. Ve výstupu řetězec "Lilek" nahrazuje typ název, "Zeleniny", což je výchozí chování <xref:System.Object.ToString?displayProperty=nameWithType> metoda.   

Ve výstupu z tohoto příkladu datum je příliš přesné (cenu lilek nebude měnit druhou) a hodnotu ceny neznamená jednotku měny. V další části dozvíte, jak tyto problémy vyřešit kontrolou formát řetězce vrácené interpolované výrazy.

## <a name="control-the-formatting-of-interpolated-expressions"></a>Ovládací prvek formátování interpolované výrazy

V předchozí části byly dva řetězce chybně formátovaný vložena do řetězce výsledek. Jeden se hodnoty data a času, pro kterou se příslušná pouze datum. Druhý byl ceníku, který neobsahoval pokyn jeho jednotku měny. Obě tyto chyby lze snadno adresu. Interpolované výrazy může zahrnovat *řetězce formátu* které řídí formátování konkrétní typy. Upravit volání `Console.WriteLine` z předchozího příkladu zahrnout specifikace formátu pro pole data a ceny, jak je znázorněno na následujícím řádku:

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```
    
Pomocí následujících interpolované výraz s dvojtečkou a řetězec formátu zadáte řetězec formátu. "d" je [řetězec formátu standardní hodnoty data a času](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) představující formát krátkého data. Je "C2" [standardního řetězce formátu čísel](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) představující číslo jako hodnotu měny s dvě číslice za desetinnou čárkou.

Počet typů v rozhraní .NET standardní knihovny podporují předdefinovanou sadu řetězce formátu. Mezi ně patří všechny číselnými typy a typy data a času. Úplný seznam typů, které podporují řetězce formátu najdete v tématu [řetězce formátu a typy knihovna tříd rozhraní .NET](../../standard/base-types/formatting-types.md#stringRef) v [typy formátování v .NET](../../standard/base-types/formatting-types.md) článku. Žádný typ, může podporovat sadu řetězce formátu, a také lze vytvářet vlastní rozšíření formátování, které poskytují vlastní formátování pro existující typy. Informace o vlastní formátování tím, že poskytuje <xref:System.ICustomFormatter> implementaci, najdete v části [vlastní formátování pomocí ICustomFormatter](../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) v [typy formátování v .NET](../../standard/base-types/formatting-types.md) článku.

Zkuste upravit řetězce formátu v textovém editoru a pokaždé, když provedete změny, znovu spusťte aplikaci a zjistěte, jak vliv budou změny mít formátování data a času a číselná hodnota. Změňte "d" v `{date:d}` k "t" (zobrazíte na formát krátkého času), "y" (zobrazíte za rok a měsíc) a "rrrr" (pro zobrazení v roce jako čtyřmístné číslo). Změňte "C2" v `{price:C2}` "e" (pro exponenciální zápis) a "F3" (pro číselná hodnota se tři číslice za desetinnou čárkou).

Kromě řízení, formátování, můžete také ovládat šířku pole a zarovnání vrácený výraz interpolované řetězce. V další části dozvíte, jak to provést.

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a>Řídit šířku pole a zarovnání interpolované výrazů

Obvykle po řetězec vrácený interpolované výrazu je zahrnutý ve výsledném řetězci, nemá žádné počáteční a koncové mezery. Platí to hlavně o instancích, ve kterých pracujete s sadu dat, interpolované výrazy umožňují určit šířku pole a jeho zarovnání. Toto nahraďte všechny kód v textovém editoru následujícím kódem zobrazíte zadáním `console run` spuštění programu:
    
```csharp
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var titles = new Dictionary<string, string>();
      titles.Add("Doyle, Arthur Conan", "Hound of the Baskervilles, The");
      titles.Add("London, Jack", "Call of the Wild, The");
      titles.Add("Shakespeare, William", "Tempest, The");

      Console.WriteLine("Author and Title List");
      Console.WriteLine($"\n{"Author",-25}    {"Title",30}\n");
      foreach (var title in titles)
         Console.WriteLine($"{title.Key,-25}     {title.Value,30}");
   }
}
```
    
Názvy autoři jsou zarovnaný doleva a názvy, které vytvořil zarovnaný doprava. Zadejte zarovnání přidáním čárkou (",") po ve výrazu a určení šířku pole. Pokud je šířka pole kladné číslo, pole je zarovnaný doprava:

```text
{expression, width}
```

Pokud je šířka pole na záporné číslo, pole je zarovnaný doleva:

```text
{expression, -width}
```

Zkuste odebrat záporné přihlásí z `{"Author",-25}` a `{title.Key,-25}` interpolované výrazy a spusťte v příkladu znovu, protože následující kód:

```csharp
Console.WriteLine($"\n{"Author",25}    {"Title",30}\n");
foreach (var title in titles)
   Console.WriteLine($"{title.Key,25}     {title.Value,30}");
```

Čas, informace o autorovi je zarovnaný doprava.

Šířka pole a řetězec formátu v jediném interpolované výrazu můžete kombinovat. Šířka pole je nejdříve následovaný dvojtečkou a řetězec formátu. Nahraďte kód uvnitř `Main` metoda následujícím kódem, který zobrazuje tři formátované řetězce s definované šířky polí. Potom spusťte program zadáním `dotnet run` příkaz.

```csharp
Console.WriteLine($"{DateTime.Now,-20:d} Hour {DateTime.Now,-10:HH} {1063.342,15:N2} feet");
```
Výstup bude vypadat přibližně takto:

```console
1/11/2018            Hour 09                1,063.34 feet
```

Jste dokončili rychlé spuštění interpolované řetězce. 
    
Můžete pokračovat [pole a kolekce](arrays-and-collections.md) rychlé spuštění ve vašem vývojovém prostředí.

Další informace o práci s interpolované řetězce v [interpolované řetězce](../language-reference/keywords/interpolated-strings.md) téma v referenční dokumentace jazyka C#.

