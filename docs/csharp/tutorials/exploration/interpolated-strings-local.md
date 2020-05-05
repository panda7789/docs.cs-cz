---
title: Interpolace řetězců – kurz C#
description: V tomto kurzu se dozvíte, jak používat funkci interpolace řetězců v jazyce C# k zahrnutí formátovaného výrazu do většího řetězce.
ms.date: 10/23/2018
ms.openlocfilehash: d1b78670361e8b333499d12b68c0364ad9e40a85
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82796051"
---
# <a name="use-string-interpolation-to-construct-formatted-strings"></a>Použití interpolace řetězců k vytvoření formátovaných řetězců

V tomto kurzu se naučíte, jak pomocí [interpolace řetězců](../../language-reference/tokens/interpolated.md) v jazyce C# vkládat hodnoty do jediného výsledného řetězce. Napíšete kód v jazyce C# a zobrazíte výsledky jeho kompilace a spuštění. Kurz obsahuje řadu lekcí, které ukazují, jak vkládat hodnoty do řetězce a naformátovat tyto hodnoty různými způsoby.

V tomto kurzu se očekává, že máte počítač, který můžete použít pro vývoj. Kurz rozhraní .NET [Hello World v 10 minutách](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo MacOS. V prohlížeči můžete také dokončit [interaktivní verzi](interpolated-strings.yml) tohoto kurzu.

## <a name="create-an-interpolated-string"></a>Vytvoření interpolovaného řetězce

Vytvořte adresář s názvem *interpoled*. Nastavte ho na aktuální adresář a spusťte následující příkaz z okna konzoly:

```dotnetcli
dotnet new console
```

Tento příkaz vytvoří novou konzolovou aplikaci .NET Core v aktuálním adresáři.

Ve svém oblíbeném editoru otevřete *program.cs* a nahraďte řádek `Console.WriteLine("Hello World!");` následujícím kódem, kde nahradíte `<name>` jméno:

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

Tento kód zkuste zadat `dotnet run` v okně konzoly. Po spuštění programu se zobrazí jeden řetězec s pozdravem, který obsahuje vaše jméno. Řetězec zahrnutý ve volání <xref:System.Console.WriteLine%2A> metody je *výraz interpolující řetězec*. Jedná se o druh šablony, který umožňuje vytvořit jeden řetězec (označovaný jako *výsledný řetězec*) z řetězce obsahujícího vložený kód. Interpolované řetězce se hodí hlavně k vkládání hodnot do řetězce nebo k řetězení (spojování) řetězců.

Tento jednoduchý příklad obsahuje oba prvky, které jsou v každém interpolovaném řetězci povinné:

- Řetězcový literál, který začíná znakem `$` před počátečním znakem uvozovek. Mezi symbolem `$` a znakem uvozovek nesmí být žádné mezery. (Pokud se chcete podívat, co se stane, když ho vložíte, vložte mezeru za `$` znakem, uložte soubor a spusťte program znovu zadáním `dotnet run` v okně konzoly. Kompilátor jazyka C# zobrazí chybovou zprávu "Chyba CS1056: Neočekávaný znak" $ ".)

- Jeden nebo více *výrazů interpolace*. Výraz interpolace je označen levou a pravou závorkou (`{` a `}`). Do složených závorek můžete vložit libovolný výraz v C#, který vrací hodnotu (včetně hodnoty `null`).

Pojďme vyzkoušet několik příkladů interpolace řetězců s některými jinými datovými typy.

## <a name="include-different-data-types"></a>Zahrnutí různých datových typů

V předchozí části jste použili interpolaci řetězců pro vložení jednoho řetězce do jiného. Výsledek výrazu interpolace může být libovolný datový typ, ale. Pojďme do interpolované řetězcové hodnoty zahrnout hodnoty různých datových typů.

V následujícím příkladu jsme nejdřív definovali `Vegetable` datový typ [třídy](../../programming-guide/classes-and-structs/classes.md) , který má `Name` [vlastnost](../../properties.md) a `ToString` [metodu](../../methods.md), která [přepíše](../../language-reference/keywords/override.md) chování <xref:System.Object.ToString?displayProperty=nameWithType> metody. [ `public` Modifikátor přístupu](../../language-reference/keywords/public.md) zpřístupňuje tuto metodu pro jakýkoliv klientský kód, aby získal řetězcovou reprezentaci `Vegetable` instance. V příkladu `Vegetable.ToString` metoda vrátí hodnotu `Name` vlastnosti, která je inicializována v `Vegetable` [konstruktoru](../../programming-guide/classes-and-structs/constructors.md):

```csharp
public Vegetable(string name) => Name = name;
```

Pak vytvoříme `Vegetable` instanci třídy s `item` názvem pomocí [ `new` operátoru](../../language-reference/operators/new-operator.md) a zadáním názvu konstruktoru: `Vegetable`

```csharp
var item = new Vegetable("eggplant");
```

Nakonec zahrneme `item` proměnnou do interpolované řetězcové hodnoty, která také obsahuje <xref:System.DateTime> hodnotu, <xref:System.Decimal> hodnotu a `Unit` hodnotu [výčtu](../../language-reference/builtin-types/enum.md) . Nahraďte celý kód jazyka C# v editoru následujícím kódem a poté jej spusťte pomocí `dotnet run` příkazu:

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

- Pokud výraz interpolace není vyhodnocen `null`, obvykle je volána `ToString` metoda typu výsledku. Můžete ho otestovat aktualizací implementace `Vegetable.ToString` metody. Je možné, že ani nebudete `ToString` muset implementovat metodu, protože každý typ má určitou implementaci této metody. Pokud to chcete otestovat, zakomentujte definici `Vegetable.ToString` metody v příkladu (k tomu vložte symbol komentáře, `//`před ním). Ve výstupu je řetězec "lilk" nahrazen plně kvalifikovaným názvem typu ("rostlinný" v tomto příkladu), což je výchozí chování <xref:System.Object.ToString?displayProperty=nameWithType> metody. Výchozím chováním `ToString` metody pro hodnotu výčtu je vrácení řetězcové reprezentace hodnoty.

Ve výstupu z tohoto příkladu je datum příliš přesné (cena za lilek se nemění každou sekundu) a hodnota Price neindikuje jednotku měny. V další části se dozvíte, jak tyto problémy vyřešit kontrolou formátu řetězcové reprezentace výsledků výrazu.

## <a name="control-the-formatting-of-interpolation-expressions"></a>Řízení formátování výrazů interpolace

V předchozí části byly do výsledného řetězce vloženy dva špatně formátované řetězce. Jedním byla hodnota data a času, ze které potřebujeme zachovat jenom datum. Druhá se jednalo o cenu, která neuváděla jednotku měny. Oba problémy můžeme snadno vyřešit. Interpolace řetězců umožňuje zadat *formátovací řetězce* , které řídí formátování konkrétních typů. Upravte volání `Console.WriteLine` z předchozího příkladu tak, aby zahrnovalo formátovací řetězce pro výrazy data a ceny, jak je znázorněno na následujícím řádku:

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

Řetězec formátu určíte pomocí výrazu interpolace dvojtečkou (":") a formátovacím řetězcem. „d“ je [standardní formátovací řetězec data a času](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier), který představuje krátký formát data. „C2“ je [standardní číselný formátovací řetězec](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier), který představuje číslo jako hodnotu měny se dvěma číslicemi za desetinnou čárkou.

Řada typů v knihovnách .NET podporuje předdefinovanou sadu formátovacích řetězců. Mezi ně patří i všechny číselné typy a typy data a času. Úplný seznam typů podporujících formátovací řetězce najdete v části [Formátovací řetězce a typy v knihovně tříd .NET](../../../standard/base-types/formatting-types.md#format-strings-and-net-types) v článku [Formátovací typy v rozhraní .NET](../../../standard/base-types/formatting-types.md).

Zkuste upravit řetězce formátu v textovém editoru a pokaždé, když uděláte změnu, spusťte program znovu, abyste viděli, jak změny ovlivňují formátování data a času a číselné hodnoty. Ve výrazu `{date:d}` změňte „d“ na „t“ (zobrazí se krátký formát času), „y“ (zobrazí se rok a měsíc) a „yyyy“ (zobrazí se rok v podobě čtyřmístného čísla). Ve výrazu `{price:C2}` změňte „C2“ na „e“ (zobrazí se exponenciální tvar čísla) a „F3“ (zobrazí se číselná hodnota se třemi číslicemi za desetinnou čárkou).

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

Zkuste odebrat záporné znaménka z kódu `{"Author",-25}` a `{title.Key,-25}` a spustit tento příklad znovu, jak je uvedeno v následujícím kódu:

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

Tentokrát jsou informace o autorovi zarovnány doprava.

Můžete zkombinovat specifikátor zarovnání a formátovací řetězec pro jedinou interpolaci výrazu. Chcete-li to provést, zadejte nejprve zarovnání následovaný dvojtečkou a řetězcem formátu. Nahraďte celý kód v `Main` metodě následujícím kódem, který zobrazí tři formátované řetězce s definovanými šířkami polí. Pak program spusťte zadáním `dotnet run` příkazu.

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

Výstup vypadá nějak takto:

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

Dokončili jste kurz o interpolaci řetězce.

Další informace naleznete v tématu o [interpolaci řetězců](../../language-reference/tokens/interpolated.md) a o [interpolaci řetězce v jazyce C#](../string-interpolation.md) .
