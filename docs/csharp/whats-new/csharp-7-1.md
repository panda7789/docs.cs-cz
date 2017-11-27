---
title: "Co je nového v C# 7.1"
description: "Přehled nových funkcí v C# 7.1."
keywords: "C# jazyka návrhu, 7.1, Visual Studio 2017"
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: 02f1f8fc8f0a3221e00e2a3c43ce06423ca43672
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="whats-new-in-c-71"></a>Co je nového v C# 7.1

C# 7.1 je první bod release to jazyka C#. Označuje vyšší verzi cadence pro jazyk. Můžete vytvořit nové funkce dříve, v ideálním případě při každé nové funkce je připraven. C# 7.1 přidá možnost konfigurace kompilátoru tak, aby odpovídaly zadaná verze jazyka. Která umožňuje oddělit rozhodnutí pro upgrade nástroje z rozhodnutí o upgrade jazykové verze.

C# 7.1 přidá [výběr verze jazyka](#language-version-selection) konfigurační prvek, tři nové jazykové funkce a nové chování kompilátoru.

Mezi nové jazykové funkce v této verzi jsou:

* [`async``Main` – metoda](#async-main)
  - Vstupní bod pro aplikace může mít `async` modifikátor.
* [`default`literálové výrazy](#default-literal-expressions)
  - Výchozí literálu výrazy můžete použít ve výrazech hodnot výchozí při lze odvodit typ cíle.
* [Názvy elementů odvozené řazené kolekce členů](#inferred-tuple-element-names)
  - Názvy elementů řazené kolekce členů lze odvodit z inicializace řazené kolekce členů v mnoha případech.

Nakonec kompilátor má dvě možnosti `/refout` a `/refonly` tuto kontrolu [odkazovat vytváření sestavení](#reference-assembly-generation).

## <a name="language-version-selection"></a>Výběr verze jazyka

Kompilátor jazyka C# podporuje C# 7.1 od verze Visual Studio 2017 verze 15.3 nebo .NET Core SDK 2.0. Ale 7.1 funkce jsou ve výchozím nastavení vypnuté. K zajištění funkcí, 7.1, budete muset změnit nastavení jazykové verze pro svůj projekt.

V sadě Visual Studio, klikněte pravým tlačítkem na uzel projektu v Průzkumníku řešení a vyberte **vlastnosti**. Vyberte **sestavení** a vyberte **Upřesnit** tlačítko. V rozevírací nabídce, a vyberte **C# nejnovější podverzi (nejnovější)**, nebo na konkrétní verzi **C# 7.1** jak ukazuje následující obrázek. `latest` Hodnota znamená, že chcete používat nejnovější podverzi, do aktuálního počítače. `C# 7.1` Znamená, že chcete použít C# 7.1, i když jsou vydávány novější podverze.

![Nastavení jazykové verze](./media/csharp-7-1/advanced-build-settings.png)

Alternativně můžete upravit soubor "csproj" a přidat nebo upravit následující řádky:

```xml
<PropertyGroup>
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> Pokud používáte Visual Studio IDE aktualizace souborů csproj, rozhraní IDE vytvoří samostatné uzly pro každou konfiguraci sestavení. Budete obvykle nastavíte hodnotu stejné ve všech konfigurací sestavení, ale je potřeba explicitně nastaven pro každou konfiguraci sestavení, nebo vyberte "Všechny konfigurace" při změně tohoto nastavení. V souboru csproj se zobrazí následující:

```xml
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Platná nastavení pro `LangVersion` element jsou:

* `ISO-1`
* `ISO-2`
* `3`
* `4`
* `5`
* `6`
* `7`
* `7.1`
* `default`
* `latest`

Speciální řetězce `default` a `latest` odkazující na nejnovější verzi hlavní a podverze jazyk nainstalovaný v počítači sestavení v uvedeném pořadí.

Toto nastavení oddělí instalaci nové verze sady SDK a nástroje ve vašem vývojovém prostředí z rozhodnete začlenit nové jazykové funkce v projektu. Nejnovější sady SDK a nástrojů můžete nainstalovat na počítači pro sestavení. Každý projekt, lze nakonfigurovat k využívání na konkrétní verzi jazyka pro jeho sestavení.

## <a name="async-main"></a>Asynchronní hlavní

*Asynchronní hlavní* metoda umožňuje používat `await` ve vaší `Main` metoda.
Dříve museli byste zápisu:

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

Teď můžete napsat:

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

Pokud není váš program vrátí ukončovací kód, můžou deklarovat `Main` metodu, která vrátí <xref:System.Threading.Tasks.Task>:

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

Si můžete přečíst více o podrobnostech v [asynchronní hlavní](../programming-guide/main-and-command-args/index.md) tématu v Průvodci programování.

## <a name="default-literal-expressions"></a>Výchozí literálu výrazy

Výchozí literálu výrazy jsou vylepšení výrazy výchozí hodnotu.
Tyto výrazy inicializovat proměnné na výchozí hodnotu. Pokud jste dříve by zápisu:

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

Nyní můžete vynechat typ na pravé straně inicializace:

```csharp
Func<string, bool> whereClause = default;
```

Další informace o toto vylepšení v tématu Průvodce programováním v C# na [výchozí hodnotu výrazy](../programming-guide/statements-expressions-operators/default-value-expressions.md).

Toto vylepšení také změní některé analýzy pravidel pro [default – klíčové slovo](../language-reference/keywords/default.md).

## <a name="inferred-tuple-element-names"></a>Názvy elementů odvozené řazené kolekce členů

Tato funkce je malý vylepšení pro funkci řazených kolekcí členů byla zavedená v C# 7.0. Kolikrát při inicializaci řazené kolekce členů proměnných, které slouží pro pravé straně přiřazení jsou stejné jako názvy, které chcete pro elementy řazené kolekce členů:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

Názvy elementů řazené kolekce členů lze odvodit z proměnných, které slouží k chybě při inicializaci řazené kolekce členů v C# 7.1:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

Další informace o této funkci v [řazených kolekcí členů](../tuples.md) tématu.

## <a name="reference-assembly-generation"></a>Vytváření odkaz na sestavení

Existují dvě nové možnosti kompilátoru, která generují *pouze odkaz na sestavení*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) a [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).
Propojené témata popisují tyto možnosti a odkaz na sestavení podrobněji.
