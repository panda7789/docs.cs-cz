---
title: Analyzátor rozhraní API .NET
description: Zjistěte, jak analyzátor rozhraní API .NET vám může pomoct detekovat zastaralé rozhraní API a problémy s kompatibilitou platformy.
author: oliag
ms.author: mairaw
ms.date: 04/26/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 892fb5cc9fba3434b0884c88b97f784d58093303
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063343"
---
# <a name="net-api-analyzer"></a>Analyzátor rozhraní API .NET

Analyzátor rozhraní API .NET je Roslyn analyzátor, který zjišťuje potenciální rizika kompatibility pro C# rozhraní API na různých platformách a detekuje volání rozhraní API nepoužívané. Může být užitečné pro všechny C# vývojáři v jakékoli fázi vývoje.

Analyzátor rozhraní API se dodává jako balíček NuGet [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/). Po odkazovat v projektu, automaticky sleduje kód a určuje problematických použití rozhraní API. Kliknutím na žárovku můžete také získat návrhy na možné opravy. V rozevírací nabídce zahrnuje možnost potlačit upozornění.

> [!NOTE]
> Analyzátor rozhraní .NET API je stále o předběžnou verzi.

## <a name="prerequisites"></a>Požadavky

* Visual Studio 2017 a novějších verzí nebo Visual Studio pro Mac (všechny verze).

## <a name="discovering-deprecated-apis"></a>Zjišťování zastaralá rozhraní API

### <a name="what-are-deprecated-apis"></a>Co jsou zastaralé rozhraní API?

Řada .NET je sada velké produkty, které jsou neustále aktualizovány na dokázaly lépe vyhovět potřebám zákazníků. Je přirozené přestat používat některá rozhraní API a je nahradit za nové. Rozhraní API se považuje za zastaralý, lepší alternativou existuje. Jedním ze způsobů informovat, že rozhraní API je zastaralý a neměl by se používat je označit pomocí <xref:System.ObsoleteAttribute> atribut. Nevýhody tohoto přístupu je, že existuje pouze jedno ID diagnostiky pro všechny zastaralé rozhraní API (pro C#, [CS0612](../../csharp/misc/cs0612.md)). To znamená, že:
- Není možné mít vyhrazené dokumenty pro každý případ.
- Není možné potlačit určité upozornění. Můžete potlačit všech nebo žádných z nich.
- Pokud chcete informovat uživatele o nové vyřazení odkazované sestavení nebo cílení balíčku musí být aktualizovány.

Analyzátor rozhraní API používá rozhraní API specifické chybové kódy, které začínají s DE (což je zkratka pro vyřazení chyba), která umožňuje ovládat zobrazení jednotlivých upozornění. Zastaralé rozhraní API identifikovat analyzátor jsou definovány v [dotnet/platform – compat](https://github.com/dotnet/platform-compat) úložiště.

### <a name="using-the-api-analyzer"></a>Analyzátor rozhraní API pomocí

Když zastaralé rozhraní API, například <xref:System.Net.WebClient>, se používá v kódu, analyzátor rozhraní API zvýrazní ho s řádkem zelenou vlnovkou. Při najetí myší na volání rozhraní API, zobrazí se žárovka s informacemi o vyřazení podpory rozhraní API, jako v následujícím příkladu:

!["Snímek obrazovky WebClient rozhraní API s zelenou vlnovkou čáru a návrhy na levé straně"](media/api-analyzer/green-squiggle.jpg)

**Seznam chyb** okno obsahuje upozornění s jedinečným ID rozhraní API nepoužívané, jak je znázorněno v následujícím příkladu (`DE004`): 

!["Snímek obrazovky okna Seznam chyb, které se zobrazují upozornění na ID a description"](media/api-analyzer/warnings-id-and-descriptions.jpg "okna Seznam chyb, který obsahuje upozornění.")

Po kliknutí na ID, přejděte na webové stránce s podrobnými informacemi o Proč se přestala nabízet rozhraní API a návrhy týkající se alternativní rozhraní API, která lze použít.

Všechna upozornění můžete potlačit pomocí pravým tlačítkem na zvýrazněné člena a výběrem **potlačit \<ID diagnostiky >**. Existují dva způsoby, jak potlačit upozornění: 

* [místně (ve zdroji)](#suppressing-warnings-locally)
* [(v souboru potlačení)](#suppressing-warnings-globally) – doporučené

### <a name="suppressing-warnings-locally"></a>Potlačení upozornění místně

Potlačení upozornění místně, klikněte pravým tlačítkem na člena chcete potlačit upozornění pro a pak vyberte **rychlé akce a Refaktoringy** > **potlačit *ID diagnostiky* \<ID diagnostiky >** > **ve zdroji**. [#Pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) upozornění direktivy preprocesoru je přidán do zdrojového kódu v rámci definice: !["Snímek kódu, které jsou uvedeny s zakázat varování #pragma"](media/api-analyzer/suppress-in-source.jpg)

### <a name="suppressing-warnings-globally"></a>Potlačení upozornění globálně

Potlačit upozornění globálně, klikněte pravým tlačítkem na člena chcete potlačit upozornění pro a pak vyberte **rychlé akce a Refaktoringy** > **potlačit *ID diagnostiky* \<ID diagnostiky >** > **v souboru potlačení**.

!["Snímek obrazovky WebClient rozhraní API s zelenou vlnovkou čáru a návrhy na levé straně"](media/api-analyzer/suppress-in-sup-file.jpg)

A *GlobalSuppressions.cs* přidá soubor do projektu po první potlačení. Nové globální potlačení se připojují k tomuto souboru.

!["Snímek obrazovky WebClient rozhraní API s zelenou vlnovkou čáru a návrhy na levé straně"](media/api-analyzer/suppression-file.jpg)

Globální potlačení je doporučeným způsobem, jak zajistit konzistenci použití rozhraní API napříč projekty.

## <a name="discovering-cross-platform-issues"></a>Zjišťování problémů napříč platformami

Podobně jako zastaralé rozhraní API, analyzátor identifikuje všechna rozhraní API, které nejsou napříč platformami. Například <xref:System.Console.WindowWidth?displayProperty=nameWithType> funguje na Windows, ale není v Linuxu a macOS. ID diagnostiky se zobrazí v **seznam chyb** okna. Že upozornění můžete potlačit kliknutím pravým tlačítkem myši a vyberete **rychlé akce a Refaktoringy**. Na rozdíl od vyřazení případy, které mají dvě možnosti (nadále používat zastaralé člena a potlačit upozornění nebo není vůbec používat), zde vyvíjíte kódu pouze pro určité platformy, můžete potlačit všechna upozornění pro jiné platformy, ne plán pro spouštění vašeho kódu. K tomu stačí úpravou souboru projektu a přidejte `PlatformCompatIgnore` vlastnost, která obsahuje seznam všech platformách se ignoruje. Přípustné hodnoty jsou: `Linux`, `macOS`, a `Windows`.

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

Pokud váš kód cílí na různé platformy a chcete využít rozhraní API není podporována na některé z nich, můžete chránit tuto část kódu pomocí `if` – příkaz:

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

Můžete také podmíněné kompilaci na cílové rozhraní framework nebo operační systém, ale aktuálně je potřeba udělat [ručně](../frameworks.md#how-to-specify-target-frameworks).

## <a name="supported-diagnostics"></a>Podporované diagnostiky

V současné době analyzátor zpracovává následujících případech:

* Použití standardních rozhraní API .NET, která vyvolá <xref:System.PlatformNotSupportedException> (PC001).
* Použití standardních rozhraní API .NET, která není k dispozici v rozhraní .NET Framework 4.6.1 (PC002).
* Použití nativních rozhraní API, která neexistuje v UPW (PC003).
* Využití Delegate.BeginInvoke a EndInvoke u rozhraní API (PC004).
* Využití rozhraní API, která je označena jako zastaralá (DEXXXX).

## <a name="ci-machine"></a>Položky konfigurace počítače

Všechny tyto Diagnostika je k dispozici pouze v rozhraní IDE, ale také v příkazovém řádku jako část sestavení vašeho projektu, která obsahuje CI server.

## <a name="configuration"></a>Konfigurace

Uživatel rozhodne, jak by měly být považovány Diagnostika: jako upozornění, chyby, návrhy nebo jej nejprve vypnout. Například jako architekt, se můžete rozhodnout, že problémy s kompatibilitou by měla být považována za chyby, volání některá rozhraní API nepoužívané vygenerovat upozornění, zatímco ostatní návrhy generovat jenom. To můžete nakonfigurovat samostatně podle ID diagnostiky a projektu. Provedete to tak v **Průzkumníku řešení**, přejděte **závislosti** uzlu projektu. Rozbalte uzly **závislosti** > **analyzátory** > **Microsoft.DotNet.Analyzers.Compatibility**. Klikněte pravým tlačítkem na ID diagnostiky, vyberte **nastavit závažnost pravidla nastavit** a vyberte požadovanou možnost.

!["Snímek Průzkumník řešení zobrazující diagnostiky a zobrazení dialogu se nastavit závažnost pravidla"](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a>Viz také:

- [Úvod do rozhraní API analyzátor](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) blogový příspěvek.
- [Analyzátor rozhraní API](https://youtu.be/eeBEahYXGd0) ukázkové video na YouTube.
