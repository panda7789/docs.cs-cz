---
title: Kurz interpolace řetězců – c#
description: Tento kurz ukazuje, jak pomocí funkce interpolace řetězce Jazyka C# zahrnout formátovaný výraz výsledky ve větším řetězci.
ms.date: 10/23/2018
ms.openlocfilehash: 593f3a77370da73dfd5f090be98112327b86b1f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75346784"
---
# <a name="use-string-interpolation-to-construct-formatted-strings"></a>Použití interpolace řetězců k vytvoření formátovaných řetězců

Tento kurz vás naučí, jak pomocí [interpolace řetězce](../../language-reference/tokens/interpolated.md) Jazyka C# vložit hodnoty do jednoho výsledného řetězce. Napíšete kód Jazyka C# a zobrazí výsledky kompilace a spuštění. Kurz obsahuje řadu lekcí, které vám ukáží, jak vložit hodnoty do řetězce a formátovat tyto hodnoty různými způsoby.

Tento kurz očekává, že máte počítač, který můžete použít pro vývoj. Kurz .NET [Hello World za 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo macOS. Můžete také dokončit [interaktivní verzi](interpolated-strings.yml) tohoto kurzu ve vašem prohlížeči.

## <a name="create-an-interpolated-string"></a>Vytvoření interpolovaného řetězce

Vytvořte adresář s názvem *Interpolované*. Zmizte z něj aktuální adresář a spusťte z okna konzoly následující příkaz:

```dotnetcli
dotnet new console
```

Tento příkaz vytvoří novou aplikaci konzoly .NET Core v aktuálním adresáři.

Otevřete *Program.cs* v oblíbeném editoru a nahraďte `Console.WriteLine("Hello World!");` `<name>` řádek následujícím kódem, kde nahradíte svým jménem:

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

Zkuste tento kód `dotnet run` zadáním do okna konzole. Po spuštění programu se zobrazí jeden řetězec s pozdravem, který obsahuje vaše jméno. Řetězec obsažený ve <xref:System.Console.WriteLine%2A> volání metody je *interpolovaný řetězcový výraz*. Jedná se o druh šablony, který umožňuje vytvořit jeden řetězec (označovaný jako *výsledný řetězec*) z řetězce obsahujícího vložený kód. Interpolované řetězce se hodí hlavně k vkládání hodnot do řetězce nebo k řetězení (spojování) řetězců.

Tento jednoduchý příklad obsahuje oba prvky, které jsou v každém interpolovaném řetězci povinné:

- Řetězcový literál, který začíná znakem `$` před počátečním znakem uvozovek. Mezi symbolem `$` a znakem uvozovek nesmí být žádné mezery. (Pokud chcete zjistit, co se stane, pokud jej zahrnete, vložte za `$` znak mezeru, uložte soubor a znovu spusťte program zadáním `dotnet run` v okně konzoly. Kompilátor Jazyka C# zobrazí chybovou zprávu "error CS1056: Unexpected character '$'".)

- Jeden nebo více *interpolačních výrazů*. Interpolační výraz je označen otevírací a uzavírací složenou závorkou (`{` a `}`). Do složených závorek můžete vložit libovolný výraz v C#, který vrací hodnotu (včetně hodnoty `null`).

Zkusme několik dalších příkladů interpolace řetězce s některými jinými datovými typy.

## <a name="include-different-data-types"></a>Zahrnutí různých datových typů

V předchozí části jste použili interpolaci řetězce k vložení jednoho řetězce do jiného. Výsledkem interpolačního výrazu však může být libovolný datový typ. Zahrňme hodnoty různých datových typů do interpolovaného řetězce.

V následujícím příkladu nejprve definujeme `Vegetable` datový `Name` typ [třídy,](../../programming-guide/classes-and-structs/classes.md) který má [vlastnost](../../properties.md) <xref:System.Object.ToString?displayProperty=nameWithType> a `ToString` [metodu](../../methods.md), která [přepíše](../../language-reference/keywords/override.md) chování metody. [ `public` Modifikátor přístupu](../../language-reference/keywords/public.md) zpřístupňuje tuto metodu pro `Vegetable` libovolný kód klienta, aby získal řetězcovou reprezentaci instance. V příkladu `Vegetable.ToString` metoda vrátí hodnotu vlastnosti, `Name` která `Vegetable` je inicializována na [konstruktoru](../../programming-guide/classes-and-structs/constructors.md):

```csharp
public Vegetable(string name) => Name = name;
```

Potom vytvoříme instanci `Vegetable` `item` třídy pojmenované pomocí [ `new` operátoru](../../language-reference/operators/new-operator.md) a `Vegetable`zadáním názvu pro konstruktor :

```csharp
var item = new Vegetable("eggplant");
```

Nakonec zahrneme `item` proměnnou do interpolovaného <xref:System.DateTime> řetězce, <xref:System.Decimal> který také `Unit` obsahuje hodnotu, hodnotu a hodnotu [výčtu.](../../language-reference/builtin-types/enum.md) Nahraďte veškerý kód Jazyka C# v editoru následujícím `dotnet run` kódem a potom jej spusťte pomocí příkazu:

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

Všimněte si, `item` že interpolační výraz v interpolovaném řetězci se překládá na text "lilek" ve výsledném řetězci. Je to proto, že když typ výsledku výrazu není řetězec, výsledek je vyřešen na řetězec následujícím způsobem:

- Pokud se výraz interpolace vyhodnotí na , použije se `null`prázdný řetězec (""nebo) <xref:System.String.Empty?displayProperty=nameWithType>.

- Pokud se výraz interpolace `null`nevyhodnocuje na , obvykle se nazývá `ToString` metoda typu výsledek. Můžete otestovat aktualizací implementace `Vegetable.ToString` metody. Pravděpodobně ani není nutné `ToString` implementovat metodu, protože každý typ má některé implementace této metody. Chcete-li to otestovat, `Vegetable.ToString` zakomentujte definici metody v příkladu `//`(k tomu, že, dát symbol komentáře, , před ním). Ve výstupu je řetězec "lilek" nahrazen plně kvalifikovaným názvem typu ("Zelenina" v tomto <xref:System.Object.ToString?displayProperty=nameWithType> příkladu), což je výchozí chování metody. Výchozí chování `ToString` metody pro hodnotu výčtu je vrátit řetězcové reprezentace hodnoty.

Ve výstupu z tohoto příkladu je datum příliš přesné (cena lilku se nemění každou sekundu) a hodnota ceny neoznačuje měnovou jednotku. V další části se dozvíte, jak tyto problémy vyřešit řízením formátu řetězcových reprezentací výsledků výrazu.

## <a name="control-the-formatting-of-interpolation-expressions"></a>Řízení formátování interpolačních výrazů

V předchozí části byly do výsledného řetězce vloženy dva špatně formátované řetězce. Jedním byla hodnota data a času, ze které potřebujeme zachovat jenom datum. Druhá byla cena, která neuváděla její měnovou jednotku. Oba problémy můžeme snadno vyřešit. Interpolace řetězců umožňuje určit *formátovací řetězce,* které řídí formátování určitých typů. Upravte volání `Console.WriteLine` z předchozího příkladu tak, aby zahrnovalo formátovací řetězce pro výrazy data a ceny, jak je znázorněno na následujícím řádku:

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

Formátovací řetězec určíte tak, že se budete řídit interpolačním výrazem s dvojtečkou (":") a formátovacím řetězcem. „d“ je [standardní formátovací řetězec data a času](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier), který představuje krátký formát data. „C2“ je [standardní číselný formátovací řetězec](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier), který představuje číslo jako hodnotu měny se dvěma číslicemi za desetinnou čárkou.

Počet typů v knihovnách .NET podporuje předdefinovanou sadu formátovacích řetězců. Mezi ně patří i všechny číselné typy a typy data a času. Úplný seznam typů podporujících formátovací řetězce najdete v části [Formátovací řetězce a typy v knihovně tříd .NET](../../../standard/base-types/formatting-types.md#format-strings-and-net-types) v článku [Formátovací typy v rozhraní .NET](../../../standard/base-types/formatting-types.md).

Zkuste upravit formátovací řetězce v textovém editoru a pokaždé, když provedete změnu, znovu spusťte program, abyste zjistili, jak změny ovlivňují formátování data a času a číselné hodnoty. Ve výrazu `{date:d}` změňte „d“ na „t“ (zobrazí se krátký formát času), „y“ (zobrazí se rok a měsíc) a „yyyy“ (zobrazí se rok v podobě čtyřmístného čísla). Ve výrazu `{price:C2}` změňte „C2“ na „e“ (zobrazí se exponenciální tvar čísla) a „F3“ (zobrazí se číselná hodnota se třemi číslicemi za desetinnou čárkou).

Kromě řízení formátování můžete také řídit šířku pole a zarovnání formátovaných řetězců, které jsou zahrnuty ve výsledném řetězci. V další části se dozvíte, jak to udělat.

## <a name="control-the-field-width-and-alignment-of-interpolation-expressions"></a>Řízení šířky pole a zarovnání interpolačních výrazů

Obvykle při výsledek interpolační výraz je formátován na řetězec, tento řetězec je součástí výsledkového řetězce bez úvodní nebo koncové mezery. Zejména při práci se sadou dat pomáhá ovládat šířku pole a zarovnání textu čitelnější výstup. Chcete-li to vidět, nahraďte veškerý kód v `dotnet run` textovém editoru následujícím kódem a zadejte pro spuštění programu:

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

Jména autorů jsou zarovnána doleva a názvy, které napsali, jsou zarovnány doprava. Trasu určíte přidáním čárky (",") za interpolační výraz a určením *minimální* šířky pole. Pokud je zadanou hodnotou kladné číslo, je pole zarovnáno doprava. Pokud se jedná o záporné číslo, je pole zarovnáno doleva.

Zkuste odebrat negativní `{"Author",-25}` znaménky z kódu a `{title.Key,-25}` spusťte příklad znovu, jako následující kód:

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

Tentokrát jsou informace o autorovi zarovnány doprava.

Můžete kombinovat specifikátor zarovnání a formátovací řetězec pro jeden interpolační výraz. Chcete-li to provést, nejprve zadejte zarovnání následované dvojtečkou a formátovacím řetězcem. Nahraďte celý kód `Main` uvnitř metody následujícím kódem, který zobrazuje tři formátované řetězce s definovanými šířkami polí. Poté spusťte program `dotnet run` zadáním příkazu.

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

Výstup vypadá podobně jako následující:

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

Dokončili jste kurz interpolace řetězce.

Další informace naleznete v tématu [Interpolace řetězce](../../language-reference/tokens/interpolated.md) a [string interpolace v c#](../../tutorials/string-interpolation.md) kurzu.
