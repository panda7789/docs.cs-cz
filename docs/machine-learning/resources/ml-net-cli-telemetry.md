---
title: Kolekce telemetrie pomocí ML.NET CLI
description: Přečtěte si o funkcích telemetrie ML.NET CLI, které shromažďují informace o využití pro analýzu, shromažďovaná data a jejich zakázání. Vyhledejte také odkazy na licenční smlouvu .NET a informace o dodržování předpisů v Microsoft GDPRe.
ms.topic: conceptual
ms.date: 06/03/2020
ms.custom: mlnet-tooling
ms.openlocfilehash: 833ee2ae54cf3a52adaf070837a33e00267d25dc
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599831"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a>Kolekce telemetrie pomocí rozhraní příkazového řádku ML.NET

[Ml.NET CLI](https://aka.ms/mlnet-cli) obsahuje funkci telemetrie, která shromažďuje anonymní data o využití, která jsou agregovaná pro použití Microsoftem.

## <a name="how-microsoft-uses-the-data"></a>Způsob, jakým společnost Microsoft používá data

Produktový tým používá data telemetrie ML.NET CLI, která vám pomůžou pochopit, jak tyto nástroje vylepšit. Pokud například zákazníci často používají konkrétní úlohu strojového učení, produktový tým prozkoumá důvody, proč a používá zjištění k určení priorit vývoje funkcí. Telemetrie ML.NET CLI také pomáhá s laděním problémů, jako jsou havárie a anomálie v kódu.

I když se tento přehled oceňuje produktovým týmem, ví, že ne všichni chtějí posílat tato data. [Zjistěte, jak zakázat telemetrii.](#opt-out-of-data-collection)

## <a name="scope"></a>Rozsah

`mlnet`Příkaz spustí rozhraní příkazového řádku ml.NET, ale samotný příkaz nebude shromažďovat telemetrii.

Telemetrie *není povolená* , když `mlnet` příkaz spustíte bez dalšího příkazu. Například:

- `mlnet`
- `mlnet --help`

Telemetrii *je povolena* při spuštění [příkazu CLI ml.NET](../reference/ml-net-cli-reference.md), například `mlnet classification` .

## <a name="opt-out-of-data-collection"></a>Odhlásit se od shromažďování dat

Funkce telemetrie ML.NET CLI je ve výchozím nastavení povolená.

Odsouhlasit funkci telemetrie nastavením `MLDOTNET_CLI_TELEMETRY_OPTOUT` proměnné prostředí na `1` nebo `true` . Tato proměnná prostředí se globálně aplikuje na nástroj ML.NET CLI.

## <a name="data-points-collected"></a>Shromážděné datové body

Tato funkce shromažďuje následující data:

- Jaký příkaz byl vyvolán, například`classification`
- Použité názvy parametrů příkazového řádku (to znamená "datová sada, popisek-sloupec, výstup-cesta, doba výuky, podrobnost")
- Adresa MAC s algoritmem hash: kryptograficky (SHA256) anonymní a jedinečné ID pro počítač
- Časové razítko vyvolání
- Tři oktety: IP adresa (nikoli plná IP adresa) se používá jenom k určení geografického umístění.
- Název všech argumentů/parametrů použitých. Nejedná se o hodnoty zákazníka, jako jsou například řetězce.
- Název souboru datové sady s algoritmem hash
- Datová sada – interval velikosti souboru
- Operační systém a verze
- Hodnota příkazů úkolu ML: kategorií hodnoty, například `regression` , `classification` a`recommendation`
- Verze rozhraní příkazového řádku ML.NET (tj. 0.3.27703.4)

Data se na servery Microsoftu odesílají zabezpečeně pomocí technologie [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) , která se drží pod omezeným přístupem, a používají se v rámci přísných bezpečnostních mechanismů pro systémy zabezpečení [Azure Storage](https://azure.microsoft.com/services/storage/) .

### <a name="data-points-not-collected"></a>Datové body nejsou shromažďovány.

*Funkce telemetrie* neshromažďuje:

- osobní údaje, jako jsou uživatelská jména
- názvy souborů DataSet
- data ze souborů datové sady

Pokud máte podezření, že telemetrie ML.NET CLI shromažďuje citlivá data, nebo že data jsou nezabezpečená nebo nevhodně zpracovaná, zajistěte si problém v úložišti [ml.NET](https://github.com/dotnet/machinelearning) pro účely šetření.

## <a name="license"></a>Licence

Distribuce rozhraní ML.NET CLI společnosti Microsoft je licencovaná s [licenčními podmínkami pro software společnosti Microsoft: Knihovna Microsoft .NET](https://aka.ms/dotnet-core-eula). Podrobnosti o shromažďování a zpracování dat najdete v části s názvem "data".

## <a name="disclosure"></a>Námitk

Při prvním spuštění [příkazu cli ml.NET](../reference/ml-net-cli-reference.md) `mlnet classification` , jako je nástroj rozhraní příkazového řádku ml.NET, se zobrazí text s oznámením o odhlášení z telemetrie. Text se může mírně lišit v závislosti na verzi rozhraní příkazového řádku, kterou používáte.

## <a name="see-also"></a>Viz také

- [Reference k rozhraní příkazového řádku ML.NET](../reference/ml-net-cli-reference.md)
- [Licenční smlouvy pro software společnosti Microsoft: Knihovna Microsoft .NET](https://aka.ms/dotnet-core-eula)
- [Ochrana osobních údajů ve společnosti Microsoft](https://www.microsoft.com/trustcenter/privacy/)
- [Prohlášení společnosti Microsoft o zásadách ochrany osobních údajů](https://privacy.microsoft.com/privacystatement)
