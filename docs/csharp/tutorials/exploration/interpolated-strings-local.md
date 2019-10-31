---
title: Interpolace řetězců – C# kurz
description: V tomto kurzu se dozvíte, jak C# používat funkci interpolace řetězců k zahrnutí formátovaného výrazu do většího řetězce.
ms.date: 10/23/2018
ms.openlocfilehash: 53b9afa4c5ccdcb1f18d2947981aee6571b73134
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120122"
---
# <a name="use-string-interpolation-to-construct-formatted-strings"></a>Použití interpolace řetězců k vytvoření formátovaných řetězců

V tomto kurzu se naučíte, jak C# pomocí [interpolace řetězců](../../language-reference/tokens/interpolated.md) vkládat hodnoty do jediného výsledného řetězce. Napíšete C# kód a zobrazíte výsledky jeho kompilace a spuštění. Kurz obsahuje řadu lekcí, které ukazují, jak vkládat hodnoty do řetězce a naformátovat tyto hodnoty různými způsoby.

V tomto kurzu se očekává, že máte počítač, který můžete použít pro vývoj. Kurz rozhraní .NET [Hello World v 10 minutách](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo MacOS. [Interaktivní verzi](interpolated-strings.yml) tohoto kurzu můžete také dokončit v prohlížeči.

## <a name="create-an-interpolated-string"></a>Vytvořit interpolované řetězce

Vytvořte adresář s názvem *interpoled*. Nastavte ho na aktuální adresář a spusťte následující příkaz z okna konzoly:

```dotnetcli
dotnet new console
```

Tento příkaz vytvoří novou konzolovou aplikaci .NET Core v aktuálním adresáři.

Ve svém oblíbeném editoru otevřete *program.cs* a nahraďte `Console.WriteLine("Hello World!");` řádku následujícím kódem, kde nahradíte `<name>` vaším jménem:

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

Tento kód zkuste zadat `dotnet run` v okně konzoly. Když program spustíte, zobrazí se jeden řetězec, který obsahuje vaše jméno na přání. Řetězec zahrnutý v volání metody <xref:System.Console.WriteLine%2A> je *výraz interpolující řetězec*. Je to druh šablony, která umožňuje vytvořit jeden řetězec (nazývaný *výsledný řetězec*) z řetězce, který obsahuje vložený kód. Interpolované řetězce jsou zvláště užitečné pro vkládání hodnot do řetězce nebo zřetězení (spojování) řetězců.

Tento jednoduchý příklad obsahuje dva prvky, které každý interpolující řetězec musí mít:

- Řetězcový literál, který začíná znakem `$` před počátečním znakem uvozovky. Mezi symbolem `$` a znakem uvozovky nesmí být žádné mezery. (Pokud se chcete podívat, co se stane, když jednu vložíte, vložte mezeru za `$` znak, uložte soubor a spusťte program znovu zadáním `dotnet run` v okně konzoly. C# Kompilátor zobrazí chybovou zprávu "Error CS1056: Neočekávaný znak" $ ".)

- Jeden nebo více *výrazů interpolace*. Výraz interpolace je označen levou a pravou složenou závorkou (`{` a `}`). Do složených závorek C# můžete vložit libovolný výraz, který vrátí hodnotu (včetně `null`).

Pojďme vyzkoušet několik příkladů interpolace řetězců s některými jinými datovými typy.

## <a name="include-different-data-types"></a>Zahrnutí různých datových typů

V předchozí části jste použili interpolaci řetězců pro vložení jednoho řetězce do jiného. Výsledek výrazu interpolace může být libovolný datový typ, ale. Pojďme do interpolované řetězcové hodnoty zahrnout hodnoty různých datových typů.

V následujícím příkladu jsme nejprve definovali datový typ [třídy](../../programming-guide/classes-and-structs/classes.md) `Vegetable`, který má [vlastnost](../../properties.md) `Name` a [metodu](../../methods.md)`ToString`, která [přepíše](../../language-reference/keywords/override.md) chování metody <xref:System.Object.ToString?displayProperty=nameWithType>. [Modifikátor přístupu `public`](../../language-reference/keywords/public.md) zpřístupňuje tuto metodu libovolnému klientskému kódu a získá tak řetězcovou reprezentaci instance `Vegetable`. V příkladu `Vegetable.ToString` metoda vrátí hodnotu vlastnosti `Name`, která je inicializována v [konstruktoru](../../programming-guide/classes-and-structs/constructors.md)`Vegetable`:

```csharp
public Vegetable(string name) => Name = name;
```

Pak vytvoříme instanci `Vegetable` třídy s názvem `item` pomocí [operátoru `new`](../../language-reference/operators/new-operator.md) a zadáním názvu konstruktoru `Vegetable`:

```csharp
var item = new Vegetable("eggplant");
```

Nakonec zahrneme `item` proměnnou do interpolované řetězce, který obsahuje také hodnotu <xref:System.DateTime>, <xref:System.Decimal> hodnotu a hodnotu [výčtu](../../programming-guide/enumeration-types.md) `Unit`. Nahraďte celý C# kód v editoru následujícím kódem a pak použijte příkaz `dotnet run` pro jeho spuštění:

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

Všimněte si, že výraz interpolace `item` v interpolované řetězci se přeloží na text "lilek" ve výsledném řetězci. To je způsobeno tím, že když typ výsledku výrazu není řetězec, výsledek je přeložen na řetězec následujícím způsobem:

- Pokud je výraz interpolace vyhodnocen jako `null`, je použit prázdný řetězec ("" nebo <xref:System.String.Empty?displayProperty=nameWithType>).

- Pokud výraz interpolace není vyhodnocen jako `null`, je obvykle volána metoda `ToString` výsledného typu. Můžete ji otestovat aktualizací implementace metody `Vegetable.ToString`. Je možné, že ani nemusíte implementovat metodu `ToString`, protože každý typ má určitou implementaci této metody. Pokud to chcete otestovat, zakomentujte definici metody `Vegetable.ToString` v příkladu (k tomu je potřeba vložit symbol komentáře, `//`, před ním). Ve výstupu je řetězec "lilk" nahrazen plně kvalifikovaným názvem typu ("rostlinný" v tomto příkladu), což je výchozí chování metody <xref:System.Object.ToString?displayProperty=nameWithType>. Výchozím chováním metody `ToString` pro hodnotu výčtu je vrácení řetězcové reprezentace hodnoty.

Ve výstupu z tohoto příkladu je datum příliš přesné (cena za lilek se nemění každou sekundu) a hodnota Price neindikuje jednotku měny. V další části se dozvíte, jak tyto problémy vyřešit kontrolou formátu řetězcové reprezentace výsledků výrazu.

## <a name="control-the-formatting-of-interpolation-expressions"></a>Řízení formátování výrazů interpolace

V předchozí části byly do výsledného řetězce vloženy dva špatně formátované řetězce. Jedna byla hodnota data a času, pro kterou bylo pouze vhodné datum. Druhá se jednalo o cenu, která neuváděla jednotku měny. Oba problémy se snadno řeší. Interpolace řetězců umožňuje zadat *formátovací řetězce* , které řídí formátování konkrétních typů. Upravte volání `Console.WriteLine` v předchozím příkladu pro zahrnutí formátovacích řetězců pro výrazy data a ceny, jak je znázorněno na následujícím řádku:

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

Řetězec formátu určíte pomocí výrazu interpolace dvojtečkou (":") a formátovacím řetězcem. "d" je [standardní řetězec formátu data a času](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) , který představuje formát krátkého data. C2 je [standardní číselný formátovací řetězec](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) , který představuje číslo jako hodnotu měny se dvěma číslicemi za desetinnou čárkou.

Řada typů v knihovnách .NET podporuje předdefinovanou sadu formátovacích řetězců. Patří sem všechny číselné typy a typy data a času. Úplný seznam typů, které podporují řetězce formátu, naleznete v tématu [formátovací řetězce a typy knihoven tříd .NET](../../../standard/base-types/formatting-types.md#format-strings-and-net-types) v článku [formátování typů v rozhraní .NET](../../../standard/base-types/formatting-types.md) .

Zkuste upravit řetězce formátu v textovém editoru a pokaždé, když uděláte změnu, spusťte program znovu, abyste viděli, jak změny ovlivňují formátování data a času a číselné hodnoty. Změňte "d" v `{date:d}` na "t" (pro zobrazení krátkého formátu času), "y" (zobrazí se rok a měsíc) a "rrrr" (zobrazí se rok jako číslo se čtyřmi číslicemi). Změňte "C2" v `{price:C2}` na "e" (pro exponenciální zápis) a "F3" (pro číselnou hodnotu se třemi číslicemi za desetinnou čárkou).

Kromě řízení formátování můžete také nastavit šířku pole a zarovnání formátovaných řetězců, které jsou zahrnuty ve výsledném řetězci. V další části se dozvíte, jak to provést.

## <a name="control-the-field-width-and-alignment-of-interpolation-expressions"></a>Řízení šířky pole a zarovnání výrazů interpolace

V případě, že je výsledek výrazu interpolace formátován na řetězec, je tento řetězec obsažen ve výsledném řetězci bez počátečních nebo koncových mezer. Zejména při práci se sadou dat, která je schopná řídit šířku pole a zarovnání textu, pomáhají vytvořit čitelnější výstup. Pokud to chcete vidět, nahraďte veškerý kód v textovém editoru následujícím kódem a pak zadejte `dotnet run` pro spuštění programu:

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

Názvy autorů jsou zarovnané vlevo a tituly, které napsaly, jsou zarovnané vpravo. Zarovnání zadáte přidáním čárky (",") po výrazu interpolace a určením *minimální* šířky pole. Pokud je zadaná hodnota kladné číslo, bude pole zarovnáno vpravo. Pokud se jedná o záporné číslo, bude pole zarovnané vlevo.

Zkuste odebrat záporné znaménka z `{"Author",-25}` a `{title.Key,-25}` kódu a znovu spustit tento příklad, jak je uvedeno v následujícím kódu:

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

Tentokrát jsou informace o autorovi zarovnány doprava.

Můžete zkombinovat specifikátor zarovnání a formátovací řetězec pro jedinou interpolaci výrazu. Chcete-li to provést, zadejte nejprve zarovnání následovaný dvojtečkou a řetězcem formátu. Nahraďte celý kód uvnitř metody `Main` následujícím kódem, který zobrazí tři formátované řetězce s definovanými šířkami polí. Pak program spusťte zadáním příkazu `dotnet run`.

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

Výstup vypadá nějak takto:

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

Dokončili jste kurz o interpolaci řetězce.

Další informace naleznete v tématu o [interpolaci řetězců](../../language-reference/tokens/interpolated.md) a o [interpolaci řetězce v C# ](../../tutorials/string-interpolation.md) kurzu.
