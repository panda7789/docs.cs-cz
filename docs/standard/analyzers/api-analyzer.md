---
title: Analyzátor rozhraní API .NET
description: Zjistěte, jak analyzátor rozhraní API .NET vám mohou pomoci rozpoznat nepoužívané rozhraní API a problémy s kompatibilitou platformy.
author: oliag
ms.author: mairaw
ms.date: 05/31/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 4394bc77b499db1960d61bad5e828f77f1144c65
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696881"
---
# <a name="net-api-analyzer"></a>Analyzátor rozhraní API .NET

Analyzátor rozhraní API .NET je Roslyn analyzátor, který zjistí potenciální kompatibility rizika pro rozhraní API jazyka C# na různých platformách a zjistí volání rozhraní API pro zastaralé. Může být užitečné pro všechny vývojáře jazyka C# v jakékoli fázi vývoje.

Analyzátor rozhraní API se dodává jako balíčku NuGet [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/). Po jeho odkazujete v projektu, automaticky monitoruje kód a označuje problematické využití rozhraní API. Kliknutím na žárovky můžete také získat návrhy na možné opravy. V rozevírací nabídce zahrnuje možnost potlačit upozornění.

> [!NOTE]
> Analyzátor .NET API je stále předběžné verze.

## <a name="prerequisites"></a>Požadavky

* Visual Studio 2017 nebo Visual Studio pro Mac (všechny verze).

## <a name="discovering-deprecated-apis"></a>Zjišťování zastaralá rozhraní API

### <a name="what-are-deprecated-apis"></a>Co jsou zastaralé rozhraní API?

Řada .NET je sada velké produkty, které jsou neustále aktualizovány na verzi lépe obsluhovat požadavky zákazníka. Je přirozené přestat používat některé rozhraní API a nahradíte je nové. Rozhraní API považuje za zastaralý lepší alternativou existuje. Je možné informovat o tom, že rozhraní API je zastaralá a neměl by se používat k označení její <xref:System.ObsoleteAttribute> atribut. Nevýhodou tento přístup je, že existuje jenom jeden diagnostiky ID pro všechna rozhraní API zastaralé (C# je [CS0612](../../csharp/misc/cs0612.md)). To znamená, že:
- Je možné mít vyhrazený dokumenty pro každý případ.
- Není možné potlačit určité kategorie upozornění. Můžete potlačit všech nebo žádných z nich.
- K informovat uživatele o nové vyřazení, odkazovaná sestavení nebo cílení na balíček musí aktualizovat.

Analyzátor rozhraní API používá rozhraní API specifické chybové kódy, které začít s DE (což znamená vyřazení chyby), což umožňuje kontrolu nad zobrazení jednotlivých upozornění. Zastaralá rozhraní API identifikovaný nástroje analyzer jsou definovány v [dotnet nebo platformu compat](https://github.com/dotnet/platform-compat) úložišti.

### <a name="using-the-api-analyzer"></a>Pomocí Analyzéru rozhraní API

Při nepoužívané rozhraní API, například <xref:System.Net.WebClient>, se používá v kódu, API Analyzer zvýrazní ho s zelenou vlnovkou řádku. Po přesunutí ukazatele myši volání rozhraní API, zobrazí se žárovky s informacemi o vyřazení rozhraní API, jako v následujícím příkladu:

!["Snímek WebClient rozhraní API s zelenou vlnovkou řádku a žárovky na levé straně"](media/api-analyzer/green-squiggle.jpg)

**Seznam chyb** okno obsahuje upozornění s jedinečným ID za zastaralé rozhraní API, jak je znázorněno v následujícím příkladu (`DE004`): 

!["Snímek obrazovky zobrazující upozornění na ID a popis v okně Seznam chyb"](media/api-analyzer/warnings.jpg)

Kliknutím na ID, přejděte na webovou stránku s podrobnými informacemi o proč byla zastaralá rozhraní API a návrhy týkající se alternativní rozhraní API, který lze použít.

Všechna upozornění, lze potlačit kliknutím pravým tlačítkem na zvýrazněné člen a výběrem **potlačit \<ID diagnostiky >**. Potlačení upozornění dvěma způsoby: 

* [místně (ve zdroji)](#suppressing-warnings-locally)
* [globálně (v souboru potlačení)](#suppressing-warnings-globally) – doporučené

### <a name="suppressing-warnings-locally"></a>Potlačení upozornění místně

Potlačit upozornění místně, klikněte pravým tlačítkem na člena chcete potlačení upozornění pro a pak vyberte **rychlé akce a refaktoring** > **potlačit *ID diagnostiky* \<ID diagnostiky >** > **ve zdroji**. [#Pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) upozornění direktivy preprocesoru se přidá do vašeho zdrojového kódu v oboru definován: !["Snímek obrazovky kódu služby rámcové s #pragma zakáže upozornění"](media/api-analyzer/suppress-in-source.jpg)

### <a name="suppressing-warnings-globally"></a>Potlačení upozornění globální

Potlačit upozornění globálně, klikněte pravým tlačítkem na člena chcete potlačení upozornění pro a pak vyberte **rychlé akce a refaktoring** > **potlačit *ID diagnostiky* \<ID diagnostiky >** > **v souboru potlačení**.

!["Snímek WebClient rozhraní API s zelenou vlnovkou řádku a žárovky na levé straně"](media/api-analyzer/suppress-in-sup-file.jpg)

A *GlobalSuppressions.cs* soubor je přidán do projektu po první potlačení. Nové globální suppressions se připojují k tomuto souboru.

!["Snímek WebClient rozhraní API s zelenou vlnovkou řádku a žárovky na levé straně"](media/api-analyzer/suppression-file.jpg)

Globální potlačení je doporučeným způsobem, aby byla zaručena konzistence využití rozhraní API napříč projekty.

## <a name="discovering-cross-platform-issues"></a>Zjišťování problémů a platformy

Podobně jako zastaralé rozhraní API, nástroje analyzer identifikuje všechna rozhraní API, které nejsou napříč platformami. Například <xref:System.Console.WindowWidth?displayProperty=nameWithType> funguje v systému Windows, ale ne na Linuxu a systému macOS. ID diagnostiky se zobrazí v **seznam chyb** okno. Že upozornění můžete potlačit tím, že kliknete pravým tlačítkem a vyberete **rychlé akce a refaktoring**. Na rozdíl od vyřazení případy, kdy máte dvě možnosti (zachovat pomocí nepoužívané člen a potlačení upozornění nebo ji nepoužívat vůbec), zde Pokud vyvíjíte kódu jenom pro některé platformy, můžete potlačit všech upozornění pro jiné platformy, ne plán pro spouštění vašeho kódu. Uděláte to tak, stačí upravit soubor projektu a přidat `PlatformCompatIgnore` vlastnost, která obsahuje seznam všech platformách budou ignorovány. Možné hodnoty jsou: `Linux`, `macOS`, a `Windows`.

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

Pokud váš kód cílem více platforem a chcete využít výhod rozhraní API není podporována u některých z nich, se můžete chránit část kód `if` příkaz:

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

Můžete také podmíněně zkompilovat na cílový framework nebo operační systém, ale je aktuálně potřeba udělat [ručně](../frameworks.md#how-to-specify-target-frameworks).

## <a name="supported-diagnostics"></a>Podporované diagnostiky

V současné době analyzátor zpracovává v následujících případech:

* Využití .NET standardní API, která vyvolává <xref:System.PlatformNotSupportedException> (PC001).
* Využití .NET standardní API, která není k dispozici na rozhraní .NET Framework 4.6.1 (PC002).
* Použití nativních rozhraní API, která neexistuje v UWP (PC003).
* Využití rozhraní API, která je označena jako zastaralé (DEXXXX).

## <a name="ci-machine"></a>Položky konfigurace počítače

Všechny tyto diagnostiky jsou k dispozici pouze v prostředí IDE, ale také na příkazovém řádku jako součást sestavení projektu, který zahrnuje server položek konfigurace.

## <a name="configuration"></a>Konfigurace

Uživatel rozhodne, jak by měly být považovány diagnostiku: upozornění, chyby, návrhy nebo vypnout. Například jako na architekt můžete rozhodnout, že problémy s kompatibilitou by měly být považovány za chyby, volání některé nepoužívané rozhraní API vygenerovat upozornění, zatímco ostatní generovat jenom návrhy. To můžete nakonfigurovat samostatně podle ID diagnostiky a projekt. Uděláte to tak v **Průzkumníku řešení**, přejděte na **závislosti** uzel v projektu. Rozbalte uzly **závislosti** > **analyzátorů** > **Microsoft.DotNet.Analyzers.Compatibility**. Klikněte pravým tlačítkem na ID diagnostiky, vyberte **nastavit závažnost nastavit pravidlo** a vyberte požadovanou možnost.

!["Snímek obrazovky zobrazující diagnostiky a automaticky otevíraný dialog se závažností nastavit pravidlo Průzkumníku řešení"](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a>Viz také:

* [Úvod do rozhraní API analyzátor](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) příspěvku na blogu.
* [Rozhraní API analyzátor](https://youtu.be/eeBEahYXGd0) ukázku video na YouTube.
