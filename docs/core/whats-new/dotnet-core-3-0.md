---
title: Co je nového v .NET Core 3.0
description: Informace o nových funkcích v rozhraní .NET Core 3.0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 12/31/2018
ms.openlocfilehash: 086be4649f4e7e27ff98df6f26d08856683865c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664815"
---
# <a name="whats-new-in-net-core-30-preview-2"></a>Co je nového v .NET Core 3.0 (ve verzi Preview 2)

Tento článek popisuje, co je nového v .NET Core 3.0 (ve verzi preview 2). Jedním z největších vylepšení je podpora aplikací klasické pracovní plochy Windows (jenom Windows). S využitím .NET Core 3.0 SDK komponenty s názvem Windows Desktop, můžete port formulářů Windows a aplikace Windows Presentation Foundation (WPF). Jasno, komponenta Windows Desktop pouze podporované a součástí Windows. Další informace najdete v části [Windows desktop](#windows-desktop) níže.

Přidává podporu pro .NET core 3.0 C# 8.0.

[Stáhnout a začít pracovat s .NET Core 3.0 ve verzi Preview 2](https://aka.ms/netcore3download) teď na Windows, Mac a Linux. Zobrazí se podrobné informace o verzi v [poznámky k verzi .NET Core 3.0 ve verzi Preview 2](https://aka.ms/netcore3releasenotes).

Další informace o co bylo vydáno se sadou jednotlivé verze najdete v následující oznámení:

- [.NET core 3.0 ve verzi Preview 1 oznámení](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)
- [.NET core 3.0 ve verzi Preview 2 oznámení](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)

## <a name="c-8"></a>C# 8

.NET core 3.0 podporuje C# 8 a od .NET Core 3.0 ve verzi Preview 2 podporuje tyto nové funkce. Další informace o C# 8.0 funkce, najdete v těchto příspěvcích na blogu:

- [Lepší využití vzorů v C# 8.0](https://devblogs.microsoft.com/dotnet/do-more-with-patterns-in-c-8-0/)
- [Využijte C# 8.0 pro typu číselník](https://devblogs.microsoft.com/dotnet/take-c-8-0-for-a-spin/)
- [Vytváření C# 8.0](https://devblogs.microsoft.com/dotnet/building-c-8-0/)

### <a name="ranges-and-indices"></a>Rozsahy a indexy

Nové `Index` typ lze použít k indexování. Můžete je vytvořit z `int` , které se počítá od začátku, nebo s předponou `^` – operátor (C#), které se počítá od konce:

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

K dispozici je také `Range` typ, který se skládá ze dvou `Index` hodnoty, jeden pro spuštění a jeden pro ukončení a může být zapsaný s `x..y` výrazu v rozsahu (C#). Potom můžete index s využitím `Range` aby vytvářela řez:

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

### <a name="async-streams"></a>Asynchronní datové proudy

`IAsyncEnumerable<T>` Typ je nový asynchronní verze `IEnumerable<T>`. Jazyk umožňuje `await foreach` přes `IAsyncEnumerable<T>` využívat jejich prvky a použití `yield return` k nim pro produkci prvků.

Následující příklad ukazuje produkční scénáře i využití asynchronních streamů. `foreach` Příkaz je asynchronní a sama používá `yield return` vytvoří na asynchronní datový proud pro volající. Tento model (pomocí `yield return`) je doporučený model pro vytváření asynchronních streamů.

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

Kromě toho, že možnost `await foreach`, můžete také vytvořit asynchronní iterátory, například iterátoru, který vrátí `IAsyncEnumerable/IAsyncEnumerator` , můžete obě `await` a `yield` v. Pro objekty, které je potřeba se dá uvolnit, můžete použít `IAsyncDisposable`, které různé typy BCL implementovat jako `Stream` a `Timer`.

> [!NOTE]
> Je třeba .NET Core 3.0 ve verzi Preview 2 použít asynchronní datové proudy, pokud chcete vyvíjet s buď Visual Studio 2019 nebo verzi preview [ C# rozšíření pro Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/releases/tag/v1.18.0-beta5). Pokud používáte .NET Core 3.0 ve verzi Preview 2 na příkazovém řádku, pak vše, co bude fungovat podle očekávání.

### <a name="using-declarations"></a>Pomocí deklarace

*Pomocí deklarace* jsou nový způsob, jak zajistit objektu řádně vyřazen. A *using – deklarace* zachová objektu aktivní, i když je stále v oboru. Jakmile se objekt stane mimo rozsah, je automaticky uvolněn. Tím se sníží vnořené *příkazy using* a ujistěte se, váš kód čistější.

```csharp
static void Main(string[] args)
{
    using var options = Parse(args);
    if (options["verbose"]) { WriteLine("Logging..."); }

} // options disposed here
```

### <a name="switch-expressions"></a>Přepnout výrazy

*Přepnout výrazy* čistší způsob, jak to uděláte *switch – příkaz* ale, protože se jedná výraz vrátí hodnotu. *Přepnout výrazy* jsou také plně integrované s porovnáváním vzorů a použití vzoru zahození `_`, znázornit `default` hodnotu.

Zobrazí se syntaxe *přepnout výrazy* v následujícím příkladu:

```csharp
static string Display(object o) => o switch
{
    Point { X: 0, Y: 0 }         => "origin",
    Point { X: var x, Y: var y } => $"({x}, {y})",
    _                            => "unknown"
};
```

Existují dva způsoby hrají v tomto příkladu. `o` nejprve odpovídá `Point` *vzorek typu* a pak se *vzor pro vlastnost* uvnitř *{složených závorek}*. `_` Popisuje `discard pattern`, což je stejná jako `default` pro *příkazy switch*.

Vzorky umožňují napsat deklarativního kódu, který zachycuje máte v úmyslu namísto kódu procedury, která implementuje testy pro něj. Kompilátoru je zodpovědný za implementace tohoto kódu nudné procedury a je zaručeno, že vždy provést správně.

Nadále bude případů kde *příkazy switch* bude vhodnější než *přepnout výrazy* a vzorky lze použít s obou stylů syntaxe.

Další informace najdete v tématu [udělat více s vzory v C# 8.0](https://devblogs.microsoft.com/dotnet/do-more-with-patterns-in-c-8-0/).

## <a name="ieee-floating-point-improvements"></a>Vylepšení plovoucí desetinné čárky IEEE

Číslo s plovoucí čárkou bodu rozhraní API se právě aktualizují dodržovat [IEEE 754-2008 revize](https://en.wikipedia.org/wiki/IEEE_754-2008_revision). Cílem těchto změn je vystavit všechny operace "povinné" a ujistěte se, že jsou behaviorally kompatibilní s specifikace IEEE.

Analýza a formátování opravy:

* Správně analyzovat a zaokrouhlit vstupů o libovolné délce.
* Správně analyzovat a formátování záporná nula.
* Díky kontrole velkých a malých písmen a povolení volitelné předcházející správně analyzovat nekonečno a NaN `+` kde je to možné.

Mají nového rozhraní API:

* `BitIncrement/BitDecrement`\
Odpovídá `nextUp` a `nextDown` IEEE operace. Vrátí nejmenší s plovoucí desetinnou čárkou čísla, která porovnává větší nebo menší než vstup (v uvedeném pořadí). Například `Math.BitIncrement(0.0)` vracel `double.Epsilon`.

* `MaxMagnitude/MinMagnitude`\
Odpovídá `maxNumMag` a `minNumMag` IEEE operace, vrátí hodnotu, která je větší nebo menší řádově dva vstupy (v uvedeném pořadí). Například `Math.MaxMagnitude(2.0, -3.0)` vracel `-3.0`.

* `ILogB`\
Odpovídá `logB` IEEE operace, která vrátí celé číslo, vrátí integrální protokolu základu 2 vstupního parametru. To je v podstatě totéž jako `floor(log2(x))`, ale ukončili minimální zaokrouhlovací chyby.

* `ScaleB`\
Odpovídá `scaleB` IEEE operace, která přebírá celé číslo, vrátí efektivně `x * pow(2, n)`, ale se provádí s minimálními zaokrouhlovací chyby.

* `Log2`\
Odpovídá `log2` IEEE operace Vrátí logaritmus o základu 2. Minimalizuje zaokrouhlovací chyby.

* `FusedMultiplyAdd`\
Odpovídá `fma` IEEE operace provádí roztaveného vynásobit sčítanec. To znamená, že nemá `(x * y) + z` jako jediná operace, existuje-minimalizací zaokrouhlovací chyby. Příkladem může být `FusedMultiplyAdd(1e308, 2.0, -1e308)` která vrací `1e308`. Standardní `(1e308 * 2.0) - 1e308` vrátí `double.PositiveInfinity`.

* `CopySign`\
Odpovídá `copySign` IEEE operace, vrátí hodnotu `x`, ale s znaménko `y`.

## <a name="net-platform-dependent-intrinsics"></a>Závislé vnitřní funkce platformy .NET

Rozhraní API nepřidali, která umožňují přístup k určité pokyny orientované výkonu procesoru, jako **SIMD** nebo **Bit zpracování instrukcí** nastaví. Tyto pokyny mohou pomoci dosáhnout zvýšení výkonu velkých objemů v některých scénářích, jako je zpracování dat, efektivně paralelně. Kromě zpřístupnění k použití rozhraní API pro vaše programy, jste začali na knihovny .NET, podle těchto pokynů ke zlepšení výkonu.

Následující žádosti o přijetí změn CoreCLR ukazují některé vnitřní objekty, buď prostřednictvím implementace nebo použijte:

* [Implementujte jednoduchý vnitřní objekty SSE2 hardwaru](https://github.com/dotnet/coreclr/pull/15585)
* [Implementace vnitřní objekty SSE hardwaru](https://github.com/dotnet/coreclr/pull/15538)
* [Arm64 základního hardwaru vnitřních objektů](https://github.com/dotnet/coreclr/pull/16822)
* [Použijte TZCNT a LZCNT pro vyhledání {první | Poslední} nalezen {bajtů | Znak}](https://github.com/dotnet/coreclr/pull/21073)

Další informace najdete v tématu [závislé vnitřní funkce platformy .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md), který definuje metodu pro definování této hardwarové infrastruktury, což Microsoft, dodavatelé čip TPM, nebo jakékoli jiné společnosti nebo jednotlivých definovat hardware/čip TPM Rozhraní API, která by měla být vystavená pro kód .NET.

## <a name="default-executables"></a>Výchozí spustitelné soubory

.NET core se teď sestavení [závisí na architektuře spustitelných souborů](../deploying/index.md#framework-dependent-executables-fde) ve výchozím nastavení. Toto je nová pro aplikace, které používají globálně nainstalovanou verzi .NET Core. Až doteď jenom [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) vytvoří spustitelný soubor.

Během `dotnet build` nebo `dotnet publish`, spustitelný soubor je vytvořen, za předpokladu, který odpovídá prostředí a platforma sady SDK, kterou používáte. Můžete očekávat, že stejné operace tyto spustitelné soubory stejně jako další nativní spustitelné soubory, jako například:

* Můžete dvakrát kliknout na spustitelný soubor.
* Aplikace z příkazového řádku můžete spustit přímo, jako například `myapp.exe` na Windows, a `./myapp` v Linuxu a macOS.

## <a name="build-copies-dependencies"></a>Vytvoření kopie závislosti

`dotnet build` Nyní zkopíruje závislostí NuGet pro vaši aplikaci z mezipaměti NuGet k výstupní složce sestavení. Dříve byly závislosti pouze zkopírovány jako součást `dotnet publish`.

Existují některé operace, jako je stránka propojení a razor publikování, který se stále vyžadují publikování.

## <a name="local-dotnet-tools"></a>Nástroje pro místní dotnet

> [!WARNING]
> Došlo ke změně v .NET Core místní nástroje .NET Core 3.0 ve verzi Preview 1 až .NET Core 3.0 ve verzi Preview 2.  Pokud jste si vyzkoušeli místní nástroje ve verzi Preview 1 spuštěním příkazu jako `dotnet tool restore` nebo `dotnet tool install`, musíte odstranit složky mezipaměti místního nástroje před místní nástroje bude správně fungovat ve verzi Preview 2. Tato složka nachází tady:
>
> Na počítači mac, Linux: `rm -r $HOME/.dotnet/toolResolverCache`
>
> Ve Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`
>
> Pokud tato složka neodstraníte, dojde k chybě.

I když .NET Core 2.1 podporuje globální nástroje, .NET Core 3.0 teď má místní nástroje. Místní nástroje se podobají globální nástroje, ale jsou spojeny s konkrétní umístění na disku. Díky tomu jednotlivých projektů a nástrojů na úložiště. Libovolný nástroj nainstalovaný místně není k dispozici globálně. Nástroje se distribuují jako balíčky NuGet.

Místní nástroje spoléhají na název souboru manifestu `dotnet-tools.json` v aktuálním adresáři. Tento soubor manifestu definuje nástroje k dispozici v této složce a níže. Vytvořením tento soubor manifestu v kořenovém adresáři vašeho úložiště, zajistíte všem uživatelům klonování kódu obnovit a použít nástroje, které jsou potřeba k úspěšné práci s kódem.

Chcete-li vytvořit `dotnet-tools.json` soubor manifestu, použijte:

```console
dotnet new tool-manifest
```

Přidejte nový nástroj manifest místní pomocí:

```console
dotnet tool install <packageId>
```

Můžete také zařadit nástroje v místní manifestu pomocí:

```console
dotnet tool list
```

Pokud chcete zobrazit, jaké nástroje jsou nainstalovány globálně, použijte:

```console
dotnet tool list -g
```

Když místní nástroje manifest soubor je k dispozici, ale nebyly nainstalovány nástroje definované v manifestu, použijte následující příkaz automaticky stáhnout a nainstalovat tyto nástroje:

```console
dotnet tool restore
```

Místní nástroj spusťte pomocí následujícího příkazu:

```console
dotnet tool run <tool-command-name>
```

Při spuštění místní nástroj vyhledá dotnet manifestu do aktuální adresářovou strukturu. Když je nalezen soubor manifestu nástroj, se hledá požadovaný nástroj. Pokud nástroj je nalezena v manifestu, ale ne do mezipaměti, uživateli se zobrazí chyba a je potřeba spustit `dotnet tool restore`.

Nástroj pro odebrání souboru manifestu místní nástroje, spusťte následující příkaz:

```console
dotnet tool uninstall <packageId>
```

Soubor manifestu nástroje je navržena k umožnění ruční úpravě – které můžete využít k aktualizaci požadovaná verze pro práci s úložištěm. Tady je příklad `dotnet-tools.json` souboru:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "dotnetsay": {
      "version": "2.1.4",
      "commands": [
        "dotnetsay"
      ]
    },
    "t-rex": {
      "version": "1.0.103",
      "commands": [
        "t-rex"
      ]
    }
  }
}
```

Pro globální a místní nástroje se vyžaduje kompatibilní verze modulu runtime. Mnoho nástrojů aktuálně na NuGet.org cílit na .NET Core Runtime 2.1. Instalovat ty, globálně nebo místně, je stále třeba k instalaci [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).

## <a name="windows-desktop"></a>Plocha Windows

Od verze rozhraní .NET Core 3.0 ve verzi Preview 1, můžete vytvářet aplikace klasické pracovní plochy Windows pomocí technologií WPF a Windows Forms. Tyto architektury podporují také pomocí moderních ovládací prvky a Fluent stylů v knihovně Windows uživatelského rozhraní XAML (WinUI) prostřednictvím [XAML ostrovy](/windows/uwp/xaml-platform/xaml-host-controls).

Komponenta Windows Desktop je součástí Windows .NET Core 3.0 SDK.

Můžete vytvořit novou aplikaci WPF nebo Windows Forms s následujícími `dotnet` příkazy:

```console
dotnet new wpf
dotnet new winforms
```

Visual Studio 2019 přidá **nový projekt** šablon pro .NET Core 3.0 Windows Forms a WPF. Návrháři se stále ještě není podporována. A můžete otevřít, spuštění a ladění těchto projektů v aplikaci Visual Studio 2019.

Visual Studio 2017 15.9 přidává možnost [povolit náhledy .NET Core](https://devblogs.microsoft.com/dotnet/net-core-tooling-update-for-visual-studio-2017-version-15-9/), ale budete muset zapnout tuto funkci a není podporováno.

Nové projekty jsou stejné jako existující projekty .NET Core, s několika doplňky. Tady je porovnání základní projekt konzoly .NET Core a základního projektu Windows Forms a WPF.

V projektu aplikace konzoly .NET Core, že projekt používá `Microsoft.NET.Sdk` sady SDK a deklaruje závislost na rozhraní .NET Core 3.0 prostřednictvím `netcoreapp3.0` cílovou architekturu. K vytvoření aplikace pro Windows Desktop, použijte `Microsoft.NET.Sdk.WindowsDesktop` sady SDK a zvolte který uživatelského rozhraní framework použít:

```diff
-<Project Sdk="Microsoft.NET.Sdk">
+<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
+   <UseWPF>true</UseWPF>
  </PropertyGroup>
</Project>
```

Chcete-li tlačítko Windows Forms přes WPF, nastavte `UseWindowsForms` místo `UseWPF`:

```diff
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
-   <UseWPF>true</UseWPF>
+   <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>
</Project>
```

Obě `UseWPF` a `UseWindowsForms` může být nastaven na `true` Pokud aplikace používá obě architektury, například když dialogové okno Windows Forms je hostování ovládacího prvku WPF.

Podělte se prosím o svůj názor na [dotnet/winforms](https://github.com/dotnet/winforms/issues), [dotnet/wpf](https://github.com/dotnet/wpf/issues) a [dotnet/jádro](https://github.com/dotnet/core/issues) úložišť.

## <a name="msix-deployment-for-windows-desktop"></a>Nasazení MSIX for Windows Desktop

[MSIX](https://docs.microsoft.com/windows/msix/) je nový formát balíčku aplikace Windows. Slouží k nasazení rozhraní .NET Core 3.0 desktopové aplikace pro Windows 10.

[Projekt Windows Application Packaging](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), k dispozici v aplikaci Visual Studio 2019, vám umožní vytvořit MSIX balíčky s [samostatná](../deploying/index.md#self-contained-deployments-scd) aplikace .NET Core.

> [!NOTE]
> Soubor projektu .NET Core, musíte zadat podporované moduly Runtime v `<RuntimeIdentifiers>` vlastnost:
>
> ```xml
> <RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
> ```

## <a name="fast-built-in-json-support"></a>Rychlé integrovanou podporou JSON

Má spoléhat ekosystému .NET [ **Json.NET** ](https://www.newtonsoft.com/json) a dalších oblíbených knihoven JSON, které dál vhodná rozhodnutí. **Json.NET** používá .NET řetězce jako jeho základní datový typ, které jsou pod pokličkou UTF-16.

Nové integrované podpoře JSON je vysoce výkonné, nízká přidělení a na základě `Span<byte>`. Tři nové hlavní JSON související typy byly přidány pro .NET Core 3.0 `System.Text.Json` oboru názvů.

### <a name="utf8jsonreader"></a>Utf8JsonReader

`System.Text.Json.Utf8JsonReader` je vysoce výkonné, s nízkou přidělení, dopředné čtecí modul pro kódování UTF-8 kódovaný JSON čtení z textu `ReadOnlySpan<byte>`. `Utf8JsonReader` Je nízké úrovně, základní typ, který můžete využít k vytváření vlastních analyzátorů a deserializers. Přečtení datovou část JSON pomocí nového `Utf8JsonReader` je 2 × rychleji než při použití reader od **Json.NET**. Nástroj nepřidělí dokud budete muset actualize tokeny JSON jako řetězce (UTF-16).

Toto nové rozhraní API bude zahrnovat následující součásti:

* Ve verzi Preview 1: Čtečka JSON (sekvenční přístup)
* Chystá: Zápis JSON, modelu DOM (RAM) objektů poco serializátor, objektů poco deserializátor

Tady je smyčka čtečku pro `Utf8JsonReader` , který může sloužit jako výchozí bod:

```csharp
using System.Text.Json;

public static void Utf8JsonReaderLoop(ReadOnlySpan<byte> dataUtf8)
{
    var json = new Utf8JsonReader(dataUtf8, isFinalBlock: true, state: default);

    while (json.Read())
    {
        JsonTokenType tokenType = json.TokenType;
        ReadOnlySpan<byte> valueSpan = json.ValueSpan;
        switch (tokenType)
        {
            case JsonTokenType.StartObject:
            case JsonTokenType.EndObject:
                break;
            case JsonTokenType.StartArray:
            case JsonTokenType.EndArray:
                break;
            case JsonTokenType.PropertyName:
                break;
            case JsonTokenType.String:
                string valueString = json.GetStringValue();
                break;
            case JsonTokenType.Number:
                if (!json.TryGetInt32Value(out int valueInteger))
                {
                    throw new FormatException();
                }
                break;
            case JsonTokenType.True:
            case JsonTokenType.False:
                bool valueBool = json.GetBooleanValue();
                break;
            case JsonTokenType.Null:
                break;
            default:
                throw new ArgumentException();
        }
    }

    dataUtf8 = dataUtf8.Slice((int)json.BytesConsumed);
    JsonReaderState state = json.CurrentState;
}
```

### <a name="utf8jsonwriter"></a>Utf8JsonWriter

`System.Text.Json.Utf8JsonWriter` poskytuje vysoce výkonné, bez mezipaměti, dopředné až po zápisu kódování UTF-8, jako je JSON textu z běžných typů .NET `String`, `Int32`, a `DateTime`. Podobně jako čtenář je modul pro zápis nízké úrovně, základní typ, který můžete využít k vytvoření vlastní serializátory. Zápis datové části JSON pomocí nového `Utf8JsonWriter` je 30 80 % rychlejší než při použití modulu pro zápis z **Json.NET** a nepřidělí.

Tady je ukázkový používání `Utf8JsonWriter` , který může sloužit jako výchozí bod:

```csharp
static int WriteJson(IBufferWriter<byte> output, long[] extraData)
{
    var json = new Utf8JsonWriter(output, state: default);

    json.WriteStartObject();

    json.WriteNumber("age", 15, escape: false);
    json.WriteString("date", DateTime.Now);
    json.WriteString("first", "John");
    json.WriteString("last", "Smith");

    json.WriteStartArray("phoneNumbers", escape: false);
    json.WriteStringValue("425-000-1212", escape: false);
    json.WriteStringValue("425-000-1213");
    json.WriteEndArray();

    json.WriteStartObject("address");
    json.WriteString("street", "1 Microsoft Way");
    json.WriteString("city", "Redmond");
    json.WriteNumber("zip", 98052);
    json.WriteEndObject();

    json.WriteStartArray("ExtraArray");
    for (var i = 0; i < extraData.Length; i++)
    {
        json.WriteNumberValue(extraData[i]);
    }
    json.WriteEndArray();

    json.WriteEndObject();

    json.Flush(isFinalBlock: true);

    return (int)json.BytesWritten;
}
```

`Utf8JsonWriter` Přijímá `IBufferWriter<byte>` jako umístění výstupu synchronně zapisovat json data a abyste jako volající musí poskytnout konkrétní implementaci. Platformu současnosti nezahrnuje implementace tohoto rozhraní. Příklad `IBufferWriter<byte>`, naleznete v tématu <https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35>.

### <a name="jsondocument"></a>JsonDocument

`System.Text.Json.JsonDocument` je postavený na `Utf8JsonReader`. `JsonDocument` Poskytuje schopnost analyzovat JSON data a sestavení jen pro čtení Document Object Model (DOM), který může být dotazována k podporují náhodný přístup a výčet. Elementy JSON, které tvoří dat přístupné prostřednictvím `JsonElement` typ, který je zveřejněný prostřednictvím `JsonDocument` jako vlastnost s názvem `RootElement`. `JsonElement` Obsahuje čítačů, společně s rozhraním API pro převod textu JSON na běžné typy .NET pole a objektu JSON. Parsování typické datová část JSON a přístup k všechny její členy pomocí `JsonDocument` je 2 až 3 x rychlejší než **Json.NET** s velmi málo přidělení pro data, která jsou přiměřeně velikosti (například < 1 MB).

Tady je ukázkový používání `JsonDocument` a `JsonElement` , který může sloužit jako výchozí bod:

```csharp
static double ParseJson()
{
    const string json = " [ { \"name\": \"John\" }, [ \"425-000-1212\", 15 ], { \"grades\": [ 90, 80, 100, 75 ] } ]";

    double average = -1;

    using (JsonDocument doc = JsonDocument.Parse(json))
    {
        JsonElement root = doc.RootElement;
        JsonElement info = root[1];

        string phoneNumber = info[0].GetString();
        int age = info[1].GetInt32();

        JsonElement grades = root[2].GetProperty("grades");

        double sum = 0;
        foreach (JsonElement grade in grades.EnumerateArray())
        {
            sum += grade.GetInt32();
        }

        int numberOfCourses = grades.GetArrayLength();
        average = sum / numberOfCourses;
    }

    return average;
}
```

## <a name="assembly-unloadability"></a>Unloadability sestavení

Unloadability sestavení je nová funkce `AssemblyLoadContext`. Tato nová funkce je z velké části transparentní z hlediska rozhraní API, vystavena s několika nových rozhraní API. Umožňuje kontext načítání uvolnila, uvolňování paměti všechny instance typů, statická pole a samotného sestavení. Aplikace by měla moct načtení a uvolnění sestavení přes tento mechanismus navždy bez nevrácené paměti.

Tato nová funkce je možné pro podobné scénáře:

* Modul plug-in scénáře, ve kterém jsou vyžadována dynamických modulů plug-in, načítání a uvolňování.
* Dynamická kompilace, spouštění a pak vyprazdňování kódu. Užitečné pro webové servery, skriptovací moduly atd.
* Načítání sestavení pro introspekce (např. ReflectionOnlyLoad), i když [MetadataLoadContext](#type-metadataloadcontext) (všeobecně dostupné ve verzi Preview 1) bude vhodnější použít v mnoha případech.

Další informace najdete v tématu [pomocí Unloadability](https://github.com/dotnet/coreclr/pull/22221) dokumentu.

Sestavení uvolnění vyžaduje významné péče zajistit, že jsou všechny odkazy na spravované objekty z mimo kontext načítání porozuměl jsem jim a spravované. Při vyžádání kontextu zavaděče uvolnila všechny vnější odkazy muset neodkazovaná tak, aby kontext načítání celistvý pouze na sebe sama.

Sestavení unloadability byl zadaný v rozhraní .NET Framework podle domény aplikace (AppDomains), které nejsou podporované s .NET Core. Objektů třídy AppDomains měl výhody a omezení v porovnání s Tento nový model. Vezměte v úvahu tento nový model zavaděč, aby bylo flexibilní a vyšší výkonné ve srovnání s objektů třídy AppDomains.

## <a name="windows-native-interop"></a>Windows nativní interoperabilita

Windows nabízí bohaté nativní rozhraní API, v podobě bez stromové struktury rozhraní API jazyka C, COM a WinRT. Od .NET Core 1.0 **P/Invoke** se podporuje. Nyní s .NET Core 3.0, podporu pro možnost **souběžné vytvoření součásti COM API** a **aktivovat rozhraní API WinRT** byla přidána.

Vidíte příklad použití modelu COM s [zdrojový kód ukázkové aplikace Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).

## <a name="type-sequencereader"></a>Zadejte: SequenceReader

V rozhraní .NET Core 3.0 `System.Buffers.SequenceReader` se přidala, který může sloužit jako čtečku `ReadOnlySequence<T>`. To umožňuje snadné, vysoký výkon s nízkou přidělení parsování `System.IO.Pipelines` data, která lze napříč více vyrovnávacích pamětí zálohování.

Následující příklad přeruší vstup `Sequence` do platné `CR/LF` oddělených řádky:

```csharp
private static ReadOnlySpan<byte> CRLF => new byte[] { (byte)'\r', (byte)'\n' };

public static void ReadLines(ReadOnlySequence<byte> sequence)
{
    SequenceReader<byte> reader = new SequenceReader<byte>(sequence);

    while (!reader.End)
    {
        if (!reader.TryReadToAny(out ReadOnlySpan<byte> line, CRLF, advancePastDelimiter:false))
        {
            // Couldn't find another delimiter
            // ...
        }

        if (!reader.IsNext(CRLF, advancePast: true))
        {
            // Not a good CR/LF pair
            // ...
        }

        // line is valid, process
        ProcessLine(line);
    }
}
```

## <a name="type-metadataloadcontext"></a>Zadejte: MetadataLoadContext

`MetadataLoadContext` Byl přidán typ, který umožňuje čtení sestavení metadat, aniž by to ovlivnilo doméně aplikace volajícího. Sestavení se číst jako data, včetně sestavení vytvořená pro rozdílné architektury a platformy než aktuální běhové prostředí. `MetadataLoadContext` se překrývá s <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, který je k dispozici pouze v rozhraní .NET Framework.

`MetdataLoadContext` je k dispozici v [System.Reflection.MetadataLoadContext balíčku](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext). Jedná se o balíček rozhraní .NET Standard 2.0.

`MetadataLoadContext` Zveřejňuje rozhraní API, podobně jako <xref:System.Runtime.Loader.AssemblyLoadContext> typu, ale není na základě tohoto typu. Podobně jako <xref:System.Runtime.Loader.AssemblyLoadContext>, `MetadataLoadContext` povolí načítání sestavení v rámci izolovaného sestavení načítání universe. `MetdataLoadContext` Rozhraní API vrací <xref:System.Reflection.Assembly> objekty povoluje použití známých reflexe rozhraní API. Spuštění orientované rozhraní API, jako například [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), nejsou povoleny a vyvolá výjimku InvalidOperationException.

Následující příklad ukazuje, jak najít konkrétní typy v sestavení, který implementuje v příslušném rozhraní:

```csharp
var paths = new string[] {@"C:\myapp\mscorlib.dll", @"C:\myapp\myapp.dll"};
var resolver = new PathAssemblyResolver(paths);
using (var lc = new MetadataLoadContext(resolver))
{
    Assembly a = lc.LoadFromAssemblyName("myapp");
    Type myInterface = a.GetType("MyApp.IPluginInterface");
    foreach (Type t in a.GetTypes())
    {
        if (t.IsClass && myInterface.IsAssignableFrom(t))
            Console.WriteLine($"Class {t.FullName} implements IPluginInterface");
    }
}
```

Scénáře pro `MetadataLoadContext` obsahují funkce návrhu, nástrojů, čas sestavení a funkce modulu runtime vytáčené světla, které je potřeba zkontrolovat sadu sestavení jako data a mít všech zámků souboru a probíhá po kontrole uvolněná paměť.

`MetadataLoadContext` Má třídu překladač předaný konstruktoru. Úlohy překladače je načtení `Assembly` zadaný jeho `AssemblyName`. Překladač třída je odvozena z abstraktní `MetadataAssemblyResolver` třídy. Je součástí implementace překladače pro scénáře na základě cest `PathAssemblyResolver`.

[MetadataLoadContext testy](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) ukazují, případy použití, mnoho. [Sestavení testů](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) jsou dobrým začátkem.

## <a name="tls-13--openssl-111-on-linux"></a>TLS verze 1.3 & OpenSSL 1.1.1 v Linuxu

.NET core se nově využít výhod [podpora protokolu TLS 1.3 v OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), až bude k dispozici v daném prostředí. Existuje více výhod TLS 1,3 za [OpenSSL týmu](https://www.openssl.org/blog/blog/2018/09/11/release111/):

* Čas vylepšené připojení z důvodu snížení počet zpátečních cest vyžaduje mezi klientem a serverem.

* Vyšší úroveň zabezpečení z důvodu odstranění různých zastaralé a nezabezpečené kryptografické algoritmy a šifrování větší metoda handshake připojení.

.NET core 3.0 ve verzi Preview 1 je schopen využitím **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, nebo **OpenSSL 1.0.2** (cokoli, co nejlepší nalezená verze se v systému Linux).  Při **OpenSSL 1.1.1** je k dispozici bude používat typy SslStream a HttpClient **TLS 1.3** při použití `SslProtocols.None` (protokoly systému výchozí), za předpokladu, že klient i server podpory **TLS 1.3**.

Následující příklad ukazuje .NET Core 3.0 ve verzi Preview 1 na Ubuntu 18.10 propojíte <https://www.cloudflare.com>:

```csharp
using System;
using System.Net.Security;
using System.Net.Sockets;
using System.Threading.Tasks;

namespace tlstest
{
    class Program
    {
        static async Task Main()
        {
            using (TcpClient tcpClient = new TcpClient())
            {
                string targetHost = "www.cloudflare.com";

                await tcpClient.ConnectAsync(targetHost, 443);

                using (SslStream sslStream = new SslStream(tcpClient.GetStream()))
                {
                    await sslStream.AuthenticateAsClientAsync(targetHost);
                    await Console.Out.WriteLineAsync($"Connected to {targetHost} with {sslStream.SslProtocol}");
                }
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/tlstest$ dotnet run
Connected to www.cloudflare.com with Tls13
user@comp-ubuntu1810:~/tlstest$ openssl version
OpenSSL 1.1.1  11 Sep 2018
```

>[!IMPORTANT]
>Windows a macOS zatím ještě nepodporují **TLS 1.3**. Bude podporovat .NET core 3.0 **TLS 1.3** v těchto operačních systémech, jakmile je k dispozici podpora.

## <a name="cryptography"></a>Cryptography

Byla přidána podpora pro **AES-GCM** a **AES-CCM** šifry, prostřednictvím rozhraní `System.Security.Cryptography.AesGcm` a `System.Security.Cryptography.AesCcm`. Tyto algoritmy jsou obě [ověření šifrování pomocí algoritmů přidružení dat (AEAD)](https://en.wikipedia.org/wiki/Authenticated_encryption)a první ověření šifrování (AE) algoritmy přidané do .NET Core.

Následující kód ukazuje použití **AesGcm** šifer k šifrování a dešifrování náhodná data.

Kód pro **AesCcm** by vypadalo téměř identické (pouze názvy tříd, které proměnné by lišit).

```csharp
// key should be: pre-known, derived, or transported via another channel, such as RSA encryption
byte[] key = new byte[16];
RandomNumberGenerator.Fill(key);

byte[] nonce = new byte[12];
RandomNumberGenerator.Fill(nonce);

// normally this would be your data
byte[] dataToEncrypt = new byte[1234];
byte[] associatedData = new byte[333];
RandomNumberGenerator.Fill(dataToEncrypt);
RandomNumberGenerator.Fill(associatedData);

// these will be filled during the encryption
byte[] tag = new byte[16];
byte[] ciphertext = new byte[dataToEncrypt.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Encrypt(nonce, dataToEncrypt, ciphertext, tag, associatedData);
}

// tag, nonce, ciphertext, associatedData should be sent to the other part

byte[] decryptedData = new byte[ciphertext.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Decrypt(nonce, ciphertext, tag, decryptedData, associatedData);
}

// do something with the data
// this should always print that data is the same
Console.WriteLine($"AES-GCM: Decrypted data is{(dataToEncrypt.SequenceEqual(decryptedData) ? "the same as" : "different than")} original data.");
```

## <a name="cryptographic-key-importexport"></a>Kryptografické klíče Import/Export

.NET core 3.0 ve verzi Preview 1 podporuje import a export asymetrického veřejné a soukromé klíče ze standardní formáty, aniž by bylo nutné použít certifikát X.509.

Všechny klíče podpora typy (RSA, DSA, ECDsa, ECDiffieHellman) **X.509 SubjectPublicKeyInfo** formát pro veřejné klíče a **PKCS #8 PrivateKeyInfo** a **PKCS #8 EncryptedPrivateKeyInfo**  formáty pro privátní klíče. Kromě toho podporuje RSA **PKCS #1 RSAPublicKey** a **PKCS #1 RSAPrivateKey**. Všechny metody export vytvářejí kódování DER binární data, a metod importu očekávají, že stejné. Pokud je klíč uložený ve formátu PEM popisný text, volajícího bude nutné base64 – dekódování obsahu před voláním metody importu.

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

namespace rsakeyprint
{
    class Program
    {
        static void Main(string[] args)
        {
            using (RSA rsa = RSA.Create())
            {
                byte[] keyBytes = File.ReadAllBytes(args[0]);
                rsa.ImportRSAPrivateKey(keyBytes, out int bytesRead);

                Console.WriteLine($"Read {bytesRead} bytes, {keyBytes.Length-bytesRead} extra byte(s) in file.");
                RSAParameters rsaParameters = rsa.ExportParameters(true);
                Console.WriteLine(BitConverter.ToString(rsaParameters.D));
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/rsakeyprint$ echo Making a small key to save on screen space.
Making a small key to save on screen space.
user@comp-ubuntu1810:~/rsakeyprint$ openssl genrsa 768 | openssl rsa -outform der -out rsa.key
Generating RSA private key, 768 bit long modulus (2 primes)
..+++++++
........+++++++
e is 65537 (0x010001)
writing RSA key
user@comp-ubuntu1810:~/rsakeyprint$ dotnet run rsa.key
Read 461 bytes, 0 extra byte(s) in file.
0F-D0-82-34-F8-13-38-4A-7F-C7-52-4A-F6-93-F8-FB-6D-98-7A-6A-04-3B-BC-35-8C-7D-AC-A5-A3-6E-AD-C1-66-30-81-2C-2A-DE-DA-60-03-6A-2C-D9-76-15-7F-61-97-57-
79-E1-6E-45-62-C3-83-04-97-CB-32-EF-C5-17-5F-99-60-92-AE-B6-34-6F-30-06-03-AC-BF-15-24-43-84-EB-83-60-EF-4D-3B-BD-D9-5D-56-26-F0-51-CE-F1
user@comp-ubuntu1810:~/rsakeyprint$ openssl rsa -in rsa.key -inform der -text -noout | grep -A7 private
privateExponent:
    0f:d0:82:34:f8:13:38:4a:7f:c7:52:4a:f6:93:f8:
    fb:6d:98:7a:6a:04:3b:bc:35:8c:7d:ac:a5:a3:6e:
    ad:c1:66:30:81:2c:2a:de:da:60:03:6a:2c:d9:76:
    15:7f:61:97:57:79:e1:6e:45:62:c3:83:04:97:cb:
    32:ef:c5:17:5f:99:60:92:ae:b6:34:6f:30:06:03:
    ac:bf:15:24:43:84:eb:83:60:ef:4d:3b:bd:d9:5d:
    56:26:f0:51:ce:f1
```

Soubory PKCS č. 8 můžete prozkoumat pomocí `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` třídy.

Soubory PFX/PKCS #12, můžete ho zkontrolovat a manipulovat s `System.Security.Cryptography.Pkcs.Pkcs12Info` a `System.Security.Cryptography.Pkcs.Pkcs12Builder`v uvedeném pořadí.

## <a name="serialport-for-linux"></a>SerialPort pro Linux

.NET core 3.0 nyní podporuje <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> v Linuxu.

Dříve, .NET Core, které jsou podporovány pouze při použití `SerialPort` typu na Windows.

## <a name="more-bcl-improvements"></a>Další vylepšení BCL

`Span<T>`, `Memory<T>`, A souvisejících typů, které byly zavedeny v .NET Core 2.1, byly optimalizovány odstraněním v .NET Core 3.0. Běžné operace, jako span konstrukce, dělení, analýzy a formátování nyní líp fungovat.

Kromě toho, jako jsou typy `String` viděli v rámci titulní vylepšení je zefektivňují při použití jako klíče s `Dictionary<TKey, TValue>` i další kolekce. Abyste využili výhod těchto vylepšení nevyžaduje žádné změny kódu.

Tato vylepšení jsou také nové v rozhraní .NET Core 3 Preview 1:

* Podpora Brotli součástí HttpClient
* ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)
* Unsafe.Unbox
* CancellationToken.Unregister
* Komplexní aritmetické operátory
* Zachování soketu rozhraní API pro protokol TCP
* StringBuilder.GetChunks
* IPEndPoint analýza kódu
* RandomNumberGenerator.GetInt32

## <a name="tiered-compilation"></a>Vrstvené kompilace

[Vrstvené kompilace](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) je ve výchozím s .NET Core 3.0. To je funkce, která umožňuje modulu runtime více Adaptivně pomocí kompilátor za běhu (JIT), můžete dosáhnout lepšího výkonu, jak při spuštění a maximalizuje propustnost.

Tato funkce byla přidána jako funkce opt-in v [.NET Core 2.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-1/) a potom byla povolená ve výchozím nastavení v [.NET Core 2.2 ve verzi Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/). Následně ji byl vrácen zpět do optimalizované pomocí verze rozhraní .NET Core 2.2.

## <a name="arm64-linux-support"></a>Podpora Linuxu ARM64

Byla přidána podpora pro ARM64 pro Linux. Případem primárního použití pro ARM64 je aktuálně s scénáře IoT.

Nástroj Alpine, Debian a Ubuntu [imagí Dockeru, které jsou dostupné pro .NET Core pro ARM64](https://hub.docker.com/r/microsoft/dotnet/).

Zkontrolujte prosím [.NET Core ARM64 stav](https://github.com/dotnet/announcements/issues/82) Další informace.

>[!NOTE]
> **ARM64** podporu Windows ještě není k dispozici.

## <a name="install-net-core-30-previews-on-linux-with-snap"></a>Instalace .NET Core 3.0 náhledy v Linuxu pomocí modulu Snap

Modul snap je preferovaný způsob, jak nainstalovat a vyzkoušejte .NET Core náhledy na [Linuxových distribucích podporujících Snap](https://docs.snapcraft.io/installing-snapd/6735).

Po dokončení konfigurace Snap ve vašem systému, spusťte následující příkaz k instalaci [.NET Core SDK 3.0 ve verzi Preview SDK](https://snapcraft.io/dotnet-sdk).

```console
sudo snap install dotnet-sdk --beta --classic
```

Když .NET Core v nainstalovaných pomocí modulu Snap balíčku, výchozí příkaz .NET Core je `dotnet-sdk.dotnet`, na rozdíl od jenom `dotnet`. Výhodou namespaced příkaz je, že to nebude v konfliktu s globálně nainstalovanou verzi .NET Core, které máte uzavřeny. Tento příkaz lze použít alias na `dotnet` pomocí:

```console
sudo snap alias dotnet-sdk.dotnet dotnet
```

Některé distribuce vyžadovat další krok k povolení přístupu k certifikátu SSL. Najdete v našich [instalace v systému Linux](https://github.com/dotnet/core/blob/master/Documentation/linux-setup.md) podrobnosti.

## <a name="gpio-support-for-raspberry-pi"></a>Podpora GPIO Raspberry Pi

Byly vydány dvě nové balíčky nuget, který vám pomůže GPIO programování.

* [System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio/0.1.0-prerelease.19078.2)
* [Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings/0.1.0-prerelease.19078.2)

Balíčky GPIO zahrnuje rozhraní API pro zařízení GPIO, SPI, I2C a PWM. Sada IoT vazby zahrnuje [zařízení vazby](https://github.com/dotnet/iot/blob/master/src/devices/README.md) pro různé čipy a senzory, stejné těch, které jsou k dispozici na [dotnet/iot-src/zařízení](https://github.com/dotnet/iot/tree/master/src/devices).

Aktualizované sériového portu rozhraní API, které byly součástí rozhraní .NET Core 3.0 ve verzi Preview 1 oznámili nejsou součástí těchto balíčků, ale jsou k dispozici jako součást platformy .NET Core.

## <a name="platform-support"></a>Podpora platformy

.NET core 3 bude podporovat v následujících operačních systémech:

* Klient Windows: 7, 8.1, 10 (1607+)
* Windows Server: 2012 R2 SP1+
* macOS: 10.12+
* RHEL: 6+
* Fedora: 26+
* Ubuntu: 16.04+
* Debian: 9+
* SLES: 12+
* openSUSE: 42.3+
* Nástroj Alpine: 3.8+

Podpora čip TPM takto:

* x64 ve Windows, macOS a Linuxu
* x86 na Windows
* ARM32 ve Windows a Linuxu
* ARM64 v Linuxu

Pro Linux je podporováno ARM32 na Debian 9 + a Ubuntu 16.04 +. Pro ARM64 je stejný jako ARM32 a uveďte Alpine 3.8. Jedná se o stejné verze těchto distribuce, jako je podporovaná pro X64.

Image dockeru pro .NET Core 3.0 najdete na adrese [microsoft/dotnet na Docker Hubu](https://hub.docker.com/r/microsoft/dotnet/). Microsoft se právě přijetí [Microsoft Container Registry (MCR)](https://cloudblogs.microsoft.com/opensource/2019/01/17/improved-discovery-experience-microsoft-containers-docker-hub/) a očekává se, že finální Image .NET Core 3.0 pouze publikuje do MCR.
