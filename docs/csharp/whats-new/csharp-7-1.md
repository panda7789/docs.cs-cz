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
# <a name="whats-new-in-c-71"></a><span data-ttu-id="cd14d-104">Co je nového v C# 7.1</span><span class="sxs-lookup"><span data-stu-id="cd14d-104">What's new in C# 7.1</span></span>

<span data-ttu-id="cd14d-105">C# 7.1 je první bod release to jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="cd14d-105">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="cd14d-106">Označuje vyšší verzi cadence pro jazyk.</span><span class="sxs-lookup"><span data-stu-id="cd14d-106">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="cd14d-107">Můžete vytvořit nové funkce dříve, v ideálním případě při každé nové funkce je připraven.</span><span class="sxs-lookup"><span data-stu-id="cd14d-107">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="cd14d-108">C# 7.1 přidá možnost konfigurace kompilátoru tak, aby odpovídaly zadaná verze jazyka.</span><span class="sxs-lookup"><span data-stu-id="cd14d-108">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="cd14d-109">Která umožňuje oddělit rozhodnutí pro upgrade nástroje z rozhodnutí o upgrade jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="cd14d-109">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="cd14d-110">C# 7.1 přidá [výběr verze jazyka](#language-version-selection) konfigurační prvek, tři nové jazykové funkce a nové chování kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="cd14d-110">C# 7.1 adds the [language version selection](#language-version-selection) configuration element, three new language features and new compiler behavior.</span></span>

<span data-ttu-id="cd14d-111">Mezi nové jazykové funkce v této verzi jsou:</span><span class="sxs-lookup"><span data-stu-id="cd14d-111">The new language features in this release are:</span></span>

* [<span data-ttu-id="cd14d-112">`async``Main` – metoda</span><span class="sxs-lookup"><span data-stu-id="cd14d-112">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="cd14d-113">Vstupní bod pro aplikace může mít `async` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="cd14d-113">The entry point for an application can have the `async` modifier.</span></span>
* [<span data-ttu-id="cd14d-114">`default`literálové výrazy</span><span class="sxs-lookup"><span data-stu-id="cd14d-114">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="cd14d-115">Výchozí literálu výrazy můžete použít ve výrazech hodnot výchozí při lze odvodit typ cíle.</span><span class="sxs-lookup"><span data-stu-id="cd14d-115">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
* [<span data-ttu-id="cd14d-116">Názvy elementů odvozené řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="cd14d-116">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="cd14d-117">Názvy elementů řazené kolekce členů lze odvodit z inicializace řazené kolekce členů v mnoha případech.</span><span class="sxs-lookup"><span data-stu-id="cd14d-117">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>

<span data-ttu-id="cd14d-118">Nakonec kompilátor má dvě možnosti `/refout` a `/refonly` tuto kontrolu [odkazovat vytváření sestavení](#reference-assembly-generation).</span><span class="sxs-lookup"><span data-stu-id="cd14d-118">Finally, the compiler has two options `/refout` and `/refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

## <a name="language-version-selection"></a><span data-ttu-id="cd14d-119">Výběr verze jazyka</span><span class="sxs-lookup"><span data-stu-id="cd14d-119">Language version selection</span></span>

<span data-ttu-id="cd14d-120">Kompilátor jazyka C# podporuje C# 7.1 od verze Visual Studio 2017 verze 15.3 nebo .NET Core SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="cd14d-120">The C# compiler supports C# 7.1 starting with Visual Studio 2017 version 15.3, or the .NET Core SDK 2.0.</span></span> <span data-ttu-id="cd14d-121">Ale 7.1 funkce jsou ve výchozím nastavení vypnuté.</span><span class="sxs-lookup"><span data-stu-id="cd14d-121">However, the 7.1 features are turned off by default.</span></span> <span data-ttu-id="cd14d-122">K zajištění funkcí, 7.1, budete muset změnit nastavení jazykové verze pro svůj projekt.</span><span class="sxs-lookup"><span data-stu-id="cd14d-122">To enable the 7.1 features, you need to change the language version setting for your project.</span></span>

<span data-ttu-id="cd14d-123">V sadě Visual Studio, klikněte pravým tlačítkem na uzel projektu v Průzkumníku řešení a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="cd14d-123">In Visual Studio, right-click on the project node in Solution Explorer and select **Properties**.</span></span> <span data-ttu-id="cd14d-124">Vyberte **sestavení** a vyberte **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="cd14d-124">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="cd14d-125">V rozevírací nabídce, a vyberte **C# nejnovější podverzi (nejnovější)**, nebo na konkrétní verzi **C# 7.1** jak ukazuje následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="cd14d-125">In the dropdown, select **C# latest minor version (latest)**, or the specific version **C# 7.1** as shown in the image following.</span></span> <span data-ttu-id="cd14d-126">`latest` Hodnota znamená, že chcete používat nejnovější podverzi, do aktuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="cd14d-126">The `latest` value means you want to use the latest minor version on the current machine.</span></span> <span data-ttu-id="cd14d-127">`C# 7.1` Znamená, že chcete použít C# 7.1, i když jsou vydávány novější podverze.</span><span class="sxs-lookup"><span data-stu-id="cd14d-127">The `C# 7.1` means that you want to use C# 7.1, even after newer minor versions are released.</span></span>

![Nastavení jazykové verze](./media/csharp-7-1/advanced-build-settings.png)

<span data-ttu-id="cd14d-129">Alternativně můžete upravit soubor "csproj" a přidat nebo upravit následující řádky:</span><span class="sxs-lookup"><span data-stu-id="cd14d-129">Alternatively, you can edit the "csproj" file and add or modify the following lines:</span></span>

```xml
<PropertyGroup>
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="cd14d-130">Pokud používáte Visual Studio IDE aktualizace souborů csproj, rozhraní IDE vytvoří samostatné uzly pro každou konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="cd14d-130">If you use the Visual Studio IDE to update your csproj files, the IDE creates separate nodes for each build configuration.</span></span> <span data-ttu-id="cd14d-131">Budete obvykle nastavíte hodnotu stejné ve všech konfigurací sestavení, ale je potřeba explicitně nastaven pro každou konfiguraci sestavení, nebo vyberte "Všechny konfigurace" při změně tohoto nastavení.</span><span class="sxs-lookup"><span data-stu-id="cd14d-131">You'll typically set the value the same in all build configurations, but you need to set it explicitly for each build configuration, or select "All Configurations" when you modify this setting.</span></span> <span data-ttu-id="cd14d-132">V souboru csproj se zobrazí následující:</span><span class="sxs-lookup"><span data-stu-id="cd14d-132">You'll see the following in your csproj file:</span></span>

```xml
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="cd14d-133">Platná nastavení pro `LangVersion` element jsou:</span><span class="sxs-lookup"><span data-stu-id="cd14d-133">Valid settings for the `LangVersion` element are:</span></span>

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

<span data-ttu-id="cd14d-134">Speciální řetězce `default` a `latest` odkazující na nejnovější verzi hlavní a podverze jazyk nainstalovaný v počítači sestavení v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="cd14d-134">The special strings `default` and `latest` resolve to the latest major and minor language versions installed on the build machine, respectively.</span></span>

<span data-ttu-id="cd14d-135">Toto nastavení oddělí instalaci nové verze sady SDK a nástroje ve vašem vývojovém prostředí z rozhodnete začlenit nové jazykové funkce v projektu.</span><span class="sxs-lookup"><span data-stu-id="cd14d-135">This setting decouples installing new versions of the SDK and tools in your development environment from choosing to incorporate new language features in a project.</span></span> <span data-ttu-id="cd14d-136">Nejnovější sady SDK a nástrojů můžete nainstalovat na počítači pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="cd14d-136">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="cd14d-137">Každý projekt, lze nakonfigurovat k využívání na konkrétní verzi jazyka pro jeho sestavení.</span><span class="sxs-lookup"><span data-stu-id="cd14d-137">Each project can be configured to use a specific version of the language for its build.</span></span>

## <a name="async-main"></a><span data-ttu-id="cd14d-138">Asynchronní hlavní</span><span class="sxs-lookup"><span data-stu-id="cd14d-138">Async main</span></span>

<span data-ttu-id="cd14d-139">*Asynchronní hlavní* metoda umožňuje používat `await` ve vaší `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="cd14d-139">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="cd14d-140">Dříve museli byste zápisu:</span><span class="sxs-lookup"><span data-stu-id="cd14d-140">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="cd14d-141">Teď můžete napsat:</span><span class="sxs-lookup"><span data-stu-id="cd14d-141">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="cd14d-142">Pokud není váš program vrátí ukončovací kód, můžou deklarovat `Main` metodu, která vrátí <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="cd14d-142">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="cd14d-143">Si můžete přečíst více o podrobnostech v [asynchronní hlavní](../programming-guide/main-and-command-args/index.md) tématu v Průvodci programování.</span><span class="sxs-lookup"><span data-stu-id="cd14d-143">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) topic in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="cd14d-144">Výchozí literálu výrazy</span><span class="sxs-lookup"><span data-stu-id="cd14d-144">Default literal expressions</span></span>

<span data-ttu-id="cd14d-145">Výchozí literálu výrazy jsou vylepšení výrazy výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cd14d-145">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="cd14d-146">Tyto výrazy inicializovat proměnné na výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cd14d-146">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="cd14d-147">Pokud jste dříve by zápisu:</span><span class="sxs-lookup"><span data-stu-id="cd14d-147">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="cd14d-148">Nyní můžete vynechat typ na pravé straně inicializace:</span><span class="sxs-lookup"><span data-stu-id="cd14d-148">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="cd14d-149">Další informace o toto vylepšení v tématu Průvodce programováním v C# na [výchozí hodnotu výrazy](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="cd14d-149">You can learn more about this enhancement in the C# Programming Guide topic on [default value expressions](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span></span>

<span data-ttu-id="cd14d-150">Toto vylepšení také změní některé analýzy pravidel pro [default – klíčové slovo](../language-reference/keywords/default.md).</span><span class="sxs-lookup"><span data-stu-id="cd14d-150">This enhancement also changes some of the parsing rules for the [default keyword](../language-reference/keywords/default.md).</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="cd14d-151">Názvy elementů odvozené řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="cd14d-151">Inferred tuple element names</span></span>

<span data-ttu-id="cd14d-152">Tato funkce je malý vylepšení pro funkci řazených kolekcí členů byla zavedená v C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="cd14d-152">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="cd14d-153">Kolikrát při inicializaci řazené kolekce členů proměnných, které slouží pro pravé straně přiřazení jsou stejné jako názvy, které chcete pro elementy řazené kolekce členů:</span><span class="sxs-lookup"><span data-stu-id="cd14d-153">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="cd14d-154">Názvy elementů řazené kolekce členů lze odvodit z proměnných, které slouží k chybě při inicializaci řazené kolekce členů v C# 7.1:</span><span class="sxs-lookup"><span data-stu-id="cd14d-154">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="cd14d-155">Další informace o této funkci v [řazených kolekcí členů](../tuples.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="cd14d-155">You can learn more about this feature in the [Tuples](../tuples.md) topic.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="cd14d-156">Vytváření odkaz na sestavení</span><span class="sxs-lookup"><span data-stu-id="cd14d-156">Reference assembly generation</span></span>

<span data-ttu-id="cd14d-157">Existují dvě nové možnosti kompilátoru, která generují *pouze odkaz na sestavení*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) a [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="cd14d-157">There are two new compiler options that generate *reference-only assemblies*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) and [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="cd14d-158">Propojené témata popisují tyto možnosti a odkaz na sestavení podrobněji.</span><span class="sxs-lookup"><span data-stu-id="cd14d-158">The linked topics explain these options and reference assemblies in more detail.</span></span>
