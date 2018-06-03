---
title: Kompatibilita aplikací v rozhraní .NET Framework
ms.date: 05/19/2017
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31d14a8ef6a4b17eea1b9160e811bb92946d775b
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728638"
---
# <a name="application-compatibility-in-the-net-framework"></a>Kompatibilita aplikací v rozhraní .NET Framework

## <a name="introduction"></a>Úvod
Kompatibilita je velmi důležité cílem každou verzi rozhraní .NET. Kompatibilita zajišťuje, že každou verzi sčítání, takže předchozí verze budou i nadále fungovat. Na druhé straně změny předchozí funkce (zvýšit výkon, řeší problémy zabezpečení, nebo opravit chyby) může způsobit problémy s kompatibilitou existující kód nebo existující aplikace, které běží v novější verzi. Rozhraní .NET Framework rozpozná Změna orientace změny a změny v modulu runtime. Změna orientace změny ovlivní aplikace, které cílí na konkrétní verzi rozhraní .NET Framework, ale běží na novější verzi. Změny v modulu runtime vliv na všechny aplikace spuštěné na konkrétní verzi.

Každá aplikace cílí na konkrétní verzi rozhraní .NET Framework, který může být určena:

* Definování cílové rozhraní v sadě Visual Studio.
* Určení cílové rozhraní v souboru projektu.
* Použití <xref:System.Runtime.Versioning.TargetFrameworkAttribute> ke zdrojovému kódu.

Když se používá novější verze, než jaké byla cílem, rozhraní .NET Framework použije quirked chování tak, aby napodoboval starší cílovou verzi. Jinými slovy aplikace bude spouštět na novější verzi rozhraní Framework, ale fungovat jako, pokud je spuštěn na starší verzi. Prostřednictvím tohoto modelu quirking jsou omezeny řadu problémy s kompatibilitou mezi verze rozhraní .NET Framework. Verze rozhraní .NET Framework aplikace cílena určené aplikací cílovou verzi sady položku sestavení pro doménu aplikace, na kterém kód běží v. Všechny další sestavení načíst v této cílové domény aplikace této verze rozhraní .NET Framework. Například v případě spustitelný soubor, rozhraní cíle pro spustitelný soubor je režim kompatibility AppDomain všechna sestavení v tom, že budou spouštěny pod.

## <a name="runtime-changes"></a>Změny v modulu runtime

Modul runtime problémy jsou ty, které se vynoří během nový modul runtime je umístěn na počítači a spouštějí stejnou binární soubory, ale je vidět různé chování. Pokud byl binární zkompilovaném pro rozhraní .NET Framework 4.0 se spustí v režimu kompatibility rozhraní .NET Framework 4.0 na verze 4.5 nebo novější. Mnoho změn, které mají vliv 4.5 nebude mít vliv na binární zkompilovaném pro 4.0. Toto je specifické pro domény aplikace a závisí na nastavení sestavení položky.

## <a name="retargeting-changes"></a>Změny cíle

Změna orientace problémy jsou ty, které se vynoří během sestavení, které se cílení na 4.0 je teď nastavená na cíl 4.5. Nyní požádá sestavení do nové funkce, jakož i potenciální problémy s kompatibilitou na starých funkcí. Znovu, to je závisí na položku sestavení, takže konzolovou aplikaci, která používá sestavení nebo web, který odkazuje na sestavení.

## <a name="net-compatibility-diagnostics"></a>Diagnostika kompatibility rozhraní .NET

Diagnostika kompatibility .NET jsou zapnuté Roslyn analyzátorů, které pomáhají identifikovat problémy s kompatibilitou aplikací mezi verze rozhraní .NET Framework. Tento seznam obsahuje všechny analyzátory k dispozici, i když pouze podmnožinu budou platit pro všechny konkrétní migrace. Analyzátory určí problémy, které platí pro plánované migrace a bude pouze surface ty.

Každý problém obsahuje následující informace:

-   Popis co se změnilo z předchozí verze.

-   Jak tato změna ovlivňuje zákazníky a jestli jsou dostupné pro zachování kompatibility mezi verzemi žádné alternativní řešení.

-   Posouzení jak důležité je změnu. Potíže s kompatibilitou aplikací jsou rozdělené takto:

    |   |   |
    |---|---|
    |Hlavní|Významné změny, která ovlivňuje velký počet aplikací, nebo vyžaduje významné úpravu kódu.|
    |Vedlejší|Změna, která ovlivňuje malý počet aplikací nebo který vyžaduje menší úpravu kódu.|
    |Okrajový případ|Změnu, která ovlivňuje aplikací v rámci velmi konkrétní, neobvyklé scénáře.|
    |Transparentní|Změna bez znatelného vlivu na vývojáře aplikace nebo uživatele.|

-   Verze označuje, když tato změna se nejprve zobrazí v rozhraní framework. Některé změny jsou umístěna v konkrétní verzi a vrátit v novější verzi; který také uvedené.

-   Typ změny:

    |   |   |
    |---|---|
    |Změna orientace|Změna ovlivní aplikace, které jsou překompilovat, jehož cílem je nová verze rozhraní .NET Framework.|
    |Modul runtime|Změna ovlivní existující aplikaci, která cílí na předchozí verzi rozhraní .NET Framework, ale běží na novější verzi.|

-   Ovlivněné rozhraní API, pokud existuje.

-   ID dostupné diagnostiky

## <a name="usage"></a>Použití
Pokud chcete začít, vyberte typ kompatibility změny níže:

* [Odlišnosti ve změnách cílení](./retargeting/index.md)
* [Změny v modulu runtime](./runtime/index.md)


## <a name="see-also"></a>Viz také

* [Verze a závislosti](../../../docs/framework/migration-guide/versions-and-dependencies.md)
* [Co je nového](../../../docs/framework/whats-new/index.md)
* [Zastaralé položky v knihovně tříd](../../../docs/framework/whats-new/whats-obsolete.md)
