---
title: Analyzátor rozhraní .NET API
description: Zjistěte, jak může nástroj .NET API Analyzer pomoci rozpoznat zastaralá rozhraní API a problémy s kompatibilitou platformy.
author: oliag
ms.date: 02/20/2020
ms.technology: dotnet-standard
ms.openlocfilehash: e214c91f2beebc7f3b3324f4879deba9a5623f86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156131"
---
# <a name="net-api-analyzer"></a>Analyzátor rozhraní .NET API

Analyzátor rozhraní .NET API je analyzátor Roslyn, který zjišťuje potenciální rizika kompatibility rozhraní API jazyka C# na různých platformách a zjišťuje volání již nepřístupných rozhraní API. To může být užitečné pro všechny vývojáře Jazyka C# v jakékoli fázi vývoje.

Analyzátor rozhraní API je dodáván jako balíček NuGet [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/). Po odkazu v projektu automaticky sleduje kód a označuje problematické využití rozhraní API. Můžete také získat návrhy na možné opravy kliknutím na žárovku. Rozevírací nabídka obsahuje možnost potlačit upozornění.

> [!NOTE]
> Analyzátor rozhraní .NET API je stále předběžnou verzí.

## <a name="prerequisites"></a>Požadavky

- Visual Studio 2017 a novější verze nebo Visual Studio pro Mac (všechny verze).

## <a name="discover-deprecated-apis"></a>Zjišťování zastaralá api

### <a name="what-are-deprecated-apis"></a>Co jsou zastaralá api?

Řada .NET je sada velkých produktů, které jsou neustále upgradovány tak, aby lépe sloužily potřebám zákazníků. Je přirozené odsuzovat některá api a nahradit je novými. Rozhraní API se považuje za zastaralé, pokud existuje lepší alternativa. Jedním ze způsobů, jak informovat, že rozhraní API je zastaralé a <xref:System.ObsoleteAttribute> nemělo by být použito, je označit jej atributem. Nevýhodou tohoto přístupu je, že existuje pouze jedno id diagnostiky pro všechna zastaralá nastavení API (pro C#, [CS0612).](../../csharp/misc/cs0612.md) To znamená, že:

- Je nemožné mít vyhrazené dokumenty pro každý případ.
- Je nemožné potlačit určitou kategorii varování. Můžete potlačit buď všechny nebo žádný z nich.
- Chcete-li informovat uživatele o novém vyřazení, je třeba aktualizovat odkazované sestavení nebo balíček cílení.

Analyzátor rozhraní API používá kódy chyb specifické pro rozhraní API, které začínají de (což je zkratka pro chyba vyřazení), což umožňuje kontrolu nad zobrazením jednotlivých upozornění. Zastaralá rozhraní API identifikovaná analyzátorem jsou definována v repo [dotnet/platform-compat.](https://github.com/dotnet/platform-compat)

### <a name="add-the-api-analyzer-to-your-project"></a>Přidání analyzátoru rozhraní API do projektu

1. Otevřete sadu Visual Studio.
2. Otevřete projekt, na kterém chcete spustit analyzátor.
3. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a zvolte **Spravovat balíčky NuGet**. (Tato možnost je k dispozici také v nabídce **Projekt.)**
4. Na kartě NuGet Package Manager:
   1. Jako zdroj balíčku vyberte "nuget.org".
   2. Přejděte na kartu **Procházet.**
   3. Vyberte **Zahrnout předběžnou verzi**.
   4. Vyhledejte **soubor Microsoft.DotNet.Analyzers.Compatibility**.
   5. Vyberte tento balíček v seznamu.
   6. Vyberte tlačítko **Instalovat.**
   7. V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně **Přijetí licence** vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.

### <a name="use-the-api-analyzer"></a>Použití analyzátoru rozhraní API

Když zastaralé rozhraní API, například <xref:System.Net.WebClient>, se používá v kódu, analyzátor rozhraní API zvýrazní ji zelenou klikatou čárou. Když najedete ukazatel na volání rozhraní API, zobrazí se žárovka s informacemi o vyřazení rozhraní API, jako v následujícím příkladu:

!["Snímek obrazovky s rozhraním API webového klienta se zelenou klikatou čárou a žárovkou vlevo"](media/api-analyzer/green-squiggle.jpg)

Okno **Seznam chyb** obsahuje upozornění s jedinečným ID na zastaralé rozhraní API, jak je znázorněno v následujícím příkladu (`DE004`):

!["Snímek obrazovky okna Seznam chyb zobrazující iD a popis upozornění"](media/api-analyzer/warnings-id-and-descriptions.jpg "Okno seznamu chyb, které obsahuje upozornění.")

Kliknutím na ID přejdete na webovou stránku s podrobnými informacemi o tom, proč bylo rozhraní API zastaralé, a návrhy týkajícími se alternativních rozhraní API, která lze použít.

Všechna upozornění lze potlačit kliknutím pravým tlačítkem myši na zvýrazněný člen a výběrem **možnosti Potlačit \<id diagnostiky>**. Upozornění lze potlačit dvěma způsoby:

- [lokálně (ve zdroji)](#suppress-warnings-locally)
- [globálně (v odrušovacím souboru)](#suppress-warnings-globally) - doporučeno

### <a name="suppress-warnings-locally"></a>Potlačit upozornění místně

Chcete-li potlačit upozornění místně, klepněte pravým tlačítkem myši na člen, pro který chcete potlačit upozornění, a pak vyberte **možnost Rychlé akce a Refaktoringy** > **potlačit id *diagnostic ID*\<diagnostiky diagnostiky>**  > ve **zdroji**. [Direktiva](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) preprocesoru #pragma upozornění je přidána do zdrojového kódu v definovaném oboru: !["Snímek obrazovky kódu zarámovaný #pragma upozornění zakázat"](media/api-analyzer/suppress-in-source.jpg)

### <a name="suppress-warnings-globally"></a>Potlačit varování globálně

Chcete-li potlačit upozornění globálně, klepněte pravým tlačítkem myši na člen, pro který chcete potlačit upozornění, a pak vyberte **možnost Rychlé akce a Refaktoringy** > **potlačit id *diagnostic ID*\<diagnostiky **diagnostiky> >  **v souboru potlačení**.

!["Snímek obrazovky s rozhraním API webového klienta se zelenou klikatou čárou a žárovkou vlevo"](media/api-analyzer/suppress-in-sup-file.jpg)

Po prvním potlačení je do projektu přidán *soubor GlobalSuppressions.cs.* K tomuto souboru jsou připojena nová globální potlačení.

!["Snímek obrazovky s rozhraním API webového klienta se zelenou klikatou čárou a žárovkou vlevo"](media/api-analyzer/suppression-file.jpg)

Globální potlačení je doporučený způsob, jak zajistit konzistenci využití rozhraní API napříč projekty.

## <a name="discover-cross-platform-issues"></a>Objevte problémy s více platformami

Podobně jako zastaralá api, analyzátor identifikuje všechna api, která nejsou napříč platformami. Například <xref:System.Console.WindowWidth?displayProperty=nameWithType> funguje na Windows, ale ne na Linuxu a macOS. ID diagnostiky se zobrazí v okně **Seznam chyb.** Toto upozornění můžete potlačit klepnutím pravým tlačítkem myši a výběrem **rychlých akcí a refaktoringů**. Na rozdíl od případů vyřazení, kdy máte dvě možnosti (buď nadále používat zastaralá člen a potlačit varování nebo nepoužívat vůbec), zde, pokud vyvíjíte kód pouze pro určité platformy, můžete potlačit všechna upozornění pro všechny ostatní platformy, které nemáte naplánujte spuštění kódu. Chcete-li tak učinit, stačí upravit soubor `PlatformCompatIgnore` projektu a přidat vlastnost, která obsahuje seznam všech platforem, které mají být ignorovány. Přijaté hodnoty `Linux`jsou: `macOS`, `Windows`, a .

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

Pokud váš kód cílí na více platforem a chcete využít rozhraní API, které není u `if` některých z nich podporováno, můžete tuto část kódu chránit pomocí příkazu:

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

Můžete také podmíněně zkompilovat podle cílového rozhraní nebo operačního systému, ale v současné době je třeba provést [ručně](../frameworks.md#how-to-specify-target-frameworks).

## <a name="supported-diagnostics"></a>Podporovaná diagnostika

V současné době analyzátor zpracovává následující případy:

- Použití rozhraní .NET Standard API, které vyvolá <xref:System.PlatformNotSupportedException> (PC001).
- Použití rozhraní .NET Standard API, které není k dispozici v rozhraní .NET Framework 4.6.1 (PC002).
- Použití nativní rozhraní API, které neexistuje v UPW (PC003).
- Použití Delegate.BeginInvoke a EndInvoke API (PC004).
- Použití rozhraní API, které je označeno jako zastaralé (DEXXXX).

## <a name="ci-machine"></a>Ci stroj

Všechny tyto diagnostiky jsou k dispozici nejen v rozhraní IDE, ale také na příkazovém řádku jako součást vytváření projektu, který zahrnuje server CI.

## <a name="configuration"></a>Konfigurace

Uživatel rozhodne, jak má být diagnostika považována za: jako upozornění, chyby, návrhy nebo vypnutí. Například jako architekt můžete rozhodnout, že problémy s kompatibilitou by měly být považovány za chyby, volání některých zastaralá řešení API generovat upozornění, zatímco jiní pouze generovat návrhy. Můžete nakonfigurovat samostatně pomocí ID diagnostiky a podle projektu. Chcete-li tak učinit v **Průzkumníku řešení**, přejděte do uzlu **Závislosti** v rámci projektu. Rozbalte**analyzátory** >  **závislostí** > uzlů**Microsoft.DotNet.Analyzers.Compatibility**. Klikněte pravým tlačítkem myši na ID diagnostiky, vyberte **nastavit závažnost sady pravidel** a vyberte požadovanou možnost.

!["Snímek obrazovky Průzkumníka řešení zobrazujícího diagnostiku a automaticky otevíraný dialog se závažností sady pravidel](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a>Viz také

- [Představujeme blogu ANALYZátoru rozhraní API.](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/)
- [API Analyzer](https://youtu.be/eeBEahYXGd0) demo video na YouTube.
