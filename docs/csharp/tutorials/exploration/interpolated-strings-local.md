---
title: Interpolace řetězců – C# kurz
description: V tomto kurzu se dozvíte, jak C# používat funkci interpolace řetězců k zahrnutí formátovaného výrazu do většího řetězce.
author: rpetrusha
ms.author: ronpet
ms.date: 10/23/2018
ms.openlocfilehash: 3e4e886d898854f5c1d966529e94f49c752220d8
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850924"
---
# <a name="use-string-interpolation-to-construct-formatted-strings"></a>Použití interpolace řetězců k vytvoření formátovaných řetězců

V tomto kurzu se naučíte, jak C# pomocí [interpolace řetězců](../../language-reference/tokens/interpolated.md) vkládat hodnoty do jediného výsledného řetězce. Napíšete C# kód a zobrazíte výsledky jeho kompilace a spuštění. Kurz obsahuje řadu lekcí, které ukazují, jak vkládat hodnoty do řetězce a naformátovat tyto hodnoty různými způsoby.

V tomto kurzu se očekává, že máte počítač, který můžete použít pro vývoj. Kurz rozhraní .NET [Hello World v 10 minutách](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v počítačích Mac, PC nebo Linux. [Interaktivní verzi](interpolated-strings.yml) tohoto kurzu můžete také dokončit v prohlížeči.

## <a name="create-an-interpolated-string"></a>Vytvořit interpolované řetězce

Vytvořte adresář s názvem **interpoled**. Nastavte ho na aktuální adresář a spusťte následující příkaz z okna konzoly:

```console
dotnet new console
```

Tento příkaz vytvoří novou konzolovou aplikaci .NET Core v aktuálním adresáři.

Ve svém oblíbeném editoru otevřete **program.cs** a nahraďte řádek `Console.WriteLine("Hello World!");` následujícím kódem, kde nahradíte `<name>` jméno:

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

Tento kód zkuste zadat `dotnet run` v okně konzoly. Když program spustíte, zobrazí se jeden řetězec, který obsahuje vaše jméno na přání. Řetězec zahrnutý ve <xref:System.Console.WriteLine%2A> volání metody je *výraz interpolující řetězec*. Je to druh šablony, která umožňuje vytvořit jeden řetězec (nazývaný *výsledný řetězec*) z řetězce, který obsahuje vložený kód. Interpolované řetězce jsou zvláště užitečné pro vkládání hodnot do řetězce nebo zřetězení (spojování) řetězců.

Tento jednoduchý příklad obsahuje dva prvky, které každý interpolující řetězec musí mít:

- Řetězcový literál, který začíná `$` znakem před počátečním znakem uvozovky. Mezi `$` symbolem a znakem uvozovky nesmí být žádné mezery. (Pokud se chcete podívat, co se stane, když ho vložíte, vložte mezeru za `$` znakem, uložte soubor a spusťte program znovu `dotnet run` zadáním v okně konzoly. C# Kompilátor zobrazí chybovou zprávu "Chyba CS1056: Neočekávaný znak $

- Jeden nebo více *výrazů interpolace*. Výraz interpolace je označen levou a pravou závorkou (`{` a `}`). Můžete vložit libovolný C# výraz, který vrátí hodnotu (včetně `null`) uvnitř složených závorek.

Pojďme vyzkoušet několik příkladů interpolace řetězců s některými jinými datovými typy.

## <a name="include-different-data-types"></a>Zahrnutí různých datových typů

V předchozí části jste použili interpolaci řetězců pro vložení jednoho řetězce do jiného. Výsledek výrazu interpolace může být libovolný datový typ, ale. Pojďme do interpolované řetězcové hodnoty zahrnout hodnoty různých datových typů.

`Vegetable` V následujícím příkladu jsme nejdřív definovali datový typ [třídy](../../programming-guide/classes-and-structs/classes.md) , který má `Name` [vlastnost](../../properties.md) a `ToString` [metodu](../../methods.md), která [přepíše](../../language-reference/keywords/override.md) chování <xref:System.Object.ToString?displayProperty=nameWithType> metody. Modifikátor přístupu zpřístupňuje tuto metodu pro jakýkoliv klientský kód, aby získal `Vegetable` řetězcovou reprezentaci instance. [ `public` ](../../language-reference/keywords/public.md) V příkladu `Vegetable.ToString` metoda vrátí hodnotu `Name` vlastnosti `Vegetable` , která je inicializována v [konstruktoru](../../programming-guide/classes-and-structs/constructors.md):

```csharp
public Vegetable(string name) => Name = name;
```

Pak `Vegetable` vytvoříme instanci třídy s `item` názvem [ `new` pomocí operátoru](../../language-reference/operators/new-operator.md) a zadáním názvu konstruktoru: `Vegetable`

```csharp
var item = new Vegetable("eggplant");
```

Nakonec zahrneme `item` proměnnou do interpolované řetězcové hodnoty, která také <xref:System.DateTime> obsahuje hodnotu, <xref:System.Decimal> hodnotu a `Unit` hodnotu [výčtu](../../programming-guide/enumeration-types.md) . Nahraďte celý C# kód v editoru následujícím kódem a poté jej spusťte pomocí `dotnet run` příkazu:

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

Všimněte si, že výraz `item` interpolace v interpolované řetězci se překládá na text "lilek" ve výsledném řetězci. To je způsobeno tím, že když typ výsledku výrazu není řetězec, výsledek je přeložen na řetězec následujícím způsobem:

- Pokud je výraz interpolace vyhodnocen `null`, je použit prázdný řetězec ("" nebo <xref:System.String.Empty?displayProperty=nameWithType>).

- Pokud výraz interpolace není vyhodnocen `null`, `ToString` obvykle je volána metoda typu výsledku. Můžete ho otestovat aktualizací implementace `Vegetable.ToString` metody. Je možné, že ani nebudete `ToString` muset implementovat metodu, protože každý typ má určitou implementaci této metody. Pokud to chcete otestovat, zakomentujte definici `Vegetable.ToString` metody v příkladu (k tomu vložte symbol komentáře, `//`před ním). Ve výstupu je řetězec "lilk" nahrazen plně kvalifikovaným názvem typu ("rostlinný" v tomto příkladu), což je výchozí chování <xref:System.Object.ToString?displayProperty=nameWithType> metody. Výchozím chováním `ToString` metody pro hodnotu výčtu je vrácení řetězcové reprezentace hodnoty.

Ve výstupu z tohoto příkladu je datum příliš přesné (cena za lilek se nemění každou sekundu) a hodnota Price neindikuje jednotku měny. V další části se dozvíte, jak tyto problémy vyřešit kontrolou formátu řetězcové reprezentace výsledků výrazu.

## <a name="control-the-formatting-of-interpolation-expressions"></a>Řízení formátování výrazů interpolace

V předchozí části byly do výsledného řetězce vloženy dva špatně formátované řetězce. Jedna byla hodnota data a času, pro kterou bylo pouze vhodné datum. Druhá se jednalo o cenu, která neuváděla jednotku měny. Oba problémy se snadno řeší. Interpolace řetězců umožňuje zadat *formátovací řetězce* , které řídí formátování konkrétních typů. Upravte volání `Console.WriteLine` z předchozího příkladu tak, aby zahrnovalo formátovací řetězce pro výrazy data a ceny, jak je znázorněno na následujícím řádku:

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

Řetězec formátu určíte pomocí výrazu interpolace dvojtečkou (":") a formátovacím řetězcem. "d" je [standardní řetězec formátu data a času](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) , který představuje formát krátkého data. C2 je [standardní číselný formátovací řetězec](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) , který představuje číslo jako hodnotu měny se dvěma číslicemi za desetinnou čárkou.

Řada typů v knihovnách .NET podporuje předdefinovanou sadu formátovacích řetězců. Patří sem všechny číselné typy a typy data a času. Úplný seznam typů, které podporují řetězce formátu, naleznete v tématu [formátovací řetězce a typy knihoven tříd .NET](../../../standard/base-types/formatting-types.md#stringRef) v článku [formátování typů v rozhraní .NET](../../../standard/base-types/formatting-types.md) .

Zkuste upravit řetězce formátu v textovém editoru a pokaždé, když uděláte změnu, spusťte program znovu, abyste viděli, jak změny ovlivňují formátování data a času a číselné hodnoty. Změňte "d" `{date:d}` na "t" (pro zobrazení krátkého formátu času), "y" (zobrazí se rok a měsíc) a "rrrr" (zobrazí se rok jako čtyřmístné číslo). Změňte "C2" `{price:C2}` na "e" (pro exponenciální zápis) a "F3" (pro číselnou hodnotu se třemi číslicemi za desetinnou čárkou).

Kromě řízení formátování můžete také nastavit šířku pole a zarovnání formátovaných řetězců, které jsou zahrnuty ve výsledném řetězci. V další části se dozvíte, jak to provést.

## <a name="control-the-field-width-and-alignment-of-interpolation-expressions"></a>Řízení šířky pole a zarovnání výrazů interpolace

V případě, že je výsledek výrazu interpolace formátován na řetězec, je tento řetězec obsažen ve výsledném řetězci bez počátečních nebo koncových mezer. Zejména při práci se sadou dat, která je schopná řídit šířku pole a zarovnání textu, pomáhají vytvořit čitelnější výstup. Chcete-li se podívat, nahraďte veškerý kód v textovém editoru následujícím kódem a potom zadejte `dotnet run` příkaz pro spuštění programu:

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

Zkuste odebrat záporné znaménka z `{"Author",-25}` kódu a `{title.Key,-25}` a spustit tento příklad znovu, jak je uvedeno v následujícím kódu:

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

Tentokrát jsou informace o autorovi zarovnány doprava.

Můžete zkombinovat specifikátor zarovnání a formátovací řetězec pro jedinou interpolaci výrazu. Chcete-li to provést, zadejte nejprve zarovnání následovaný dvojtečkou a řetězcem formátu. Nahraďte celý kód `Main` v metodě následujícím kódem, který zobrazí tři formátované řetězce s definovanými šířkami polí. Pak program spusťte zadáním `dotnet run` příkazu.

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

Výstup vypadá nějak takto:

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

Dokončili jste kurz o interpolaci řetězce.

Další informace naleznete v tématu o [interpolaci řetězců](../../language-reference/tokens/interpolated.md) a o [interpolaci řetězce v C# ](../../tutorials/string-interpolation.md) kurzu.
