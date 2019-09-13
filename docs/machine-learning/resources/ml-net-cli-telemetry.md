---
title: Kolekce telemetrie pomocí ML.NET CLI
description: Přečtěte si o funkcích telemetrie ML.NET CLI, které shromažďují informace o využití pro analýzu, shromažďovaná data a jejich zakázání. Vyhledejte také odkazy na licenční smlouvu .NET a informace o dodržování předpisů v Microsoft GDPRe.
ms.topic: conceptual
ms.date: 09/03/2019
ms.custom: ''
ms.openlocfilehash: 77a24416a8008d36006c293cb174b5a8c2f516b7
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929284"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a>Kolekce telemetrie pomocí rozhraní příkazového řádku ML.NET

[Ml.NET CLI](https://aka.ms/mlnet-cli) obsahuje funkci telemetrie, která shromažďuje anonymní data o využití, která jsou agregovaná pro použití Microsoftem.

## <a name="how-microsoft-uses-the-data"></a>Způsob, jakým společnost Microsoft používá data

Produktový tým používá data telemetrie ML.NET CLI, která vám pomůžou pochopit, jak tyto nástroje vylepšit. Pokud například zákazníci často používají konkrétní úlohu strojového učení, produktový tým prozkoumá důvody, proč a používá zjištění k určení priorit vývoje funkcí. Telemetrie ML.NET CLI také pomáhá s laděním problémů, jako jsou havárie a anomálie v kódu. 

I když se tento přehled oceňuje produktovým týmem, ví, že ne všichni chtějí posílat tato data. [Zjistěte, jak zakázat telemetrii.](#opt-out-of-data-collection)

## <a name="scope"></a>Scope

`mlnet` Příkaz spustí rozhraní příkazového řádku ml.NET, ale samotný příkaz nebude shromažďovat telemetrii.

Telemetrie *není povolená* , když `mlnet` příkaz spustíte bez dalšího příkazu. Příklad:

- `mlnet`
- `mlnet --help`

Telemetrii *je povolena* při spuštění [příkazu CLI ml.NET](../reference/ml-net-cli-reference.md) `mlnet auto-train`, například.

## <a name="opt-out-of-data-collection"></a>Odhlásit se od shromažďování dat

Funkce telemetrie ML.NET CLI je ve výchozím nastavení povolená.

Odsouhlasit funkci `MLDOTNET_CLI_TELEMETRY_OPTOUT` telemetrie nastavením proměnné prostředí na `1` nebo `true`. Tato proměnná prostředí se globálně aplikuje na nástroj ML.NET CLI.

## <a name="data-points-collected"></a>Shromážděné datové body

Tato funkce shromažďuje následující data:

- Jaký příkaz byl vyvolán, například`auto-train`
- Použité názvy parametrů příkazového řádku (to znamená "DataSet-Name; Label-column-name, ml-Task, Output-Path, Max-prozkoumává-Time, verbose")
- Adresa MAC s algoritmem hash: kryptograficky (SHA256) anonymní a jedinečné ID pro počítač
- Časové razítko vyvolání
- Tři oktety: IP adresa (nikoli plná IP adresa) se používá jenom k určení geografického umístění.
- Název všech argumentů/parametrů použitých. Nejedná se o hodnoty zákazníka, jako jsou například řetězce.
- Název souboru datové sady s algoritmem hash
- Datová sada – interval velikosti souboru
- Operační systém a verze
- Hodnota parametru--Task: Kategorií hodnoty, `regression`jako například, `binary-classification`a`multiclass-classification`
- Verze rozhraní příkazového řádku ML.NET (tj. 0.3.27703.4)

Data se na servery Microsoftu odesílají zabezpečeně pomocí technologie [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) , která se drží pod omezeným přístupem, a používají se v rámci přísných bezpečnostních mechanismů pro systémy zabezpečení [Azure Storage](https://azure.microsoft.com/services/storage/) .

### <a name="data-points-not-collected"></a>Datové body nejsou shromažďovány.
*Funkce telemetrie* neshromažďuje:

- osobní údaje, jako jsou uživatelská jména
- názvy souborů DataSet
- data ze souborů datové sady

Pokud máte podezření, že telemetrie ML.NET CLI shromažďuje citlivá data, nebo že data jsou nezabezpečená nebo nevhodně zpracovaná, zajistěte si problém v úložišti [ml.NET](https://github.com/dotnet/machinelearning) pro účely šetření.

## <a name="license"></a>Licence

Distribuce rozhraní ml.NET CLI společnosti Microsoft je licencovaná s [licenčními podmínkami pro software společnosti Microsoft: Knihovna](https://aka.ms/dotnet-core-eula)Microsoft .NET. Podrobnosti o shromažďování a zpracování dat najdete v části s názvem "data".

## <a name="disclosure"></a>Námitk

Při prvním spuštění `mlnet auto-train` [příkazu CLI ml.NET](../reference/ml-net-cli-reference.md) , jako je nástroj rozhraní příkazového řádku ml.NET, se zobrazí text s oznámením o odhlášení z telemetrie. Text se může mírně lišit v závislosti na verzi rozhraní příkazového řádku, kterou používáte.

## <a name="see-also"></a>Viz také:

- [Reference k rozhraní příkazového řádku ML.NET](../reference/ml-net-cli-reference.md)
- [Licenční smlouvy pro software společnosti Microsoft: Knihovna Microsoft .NET](https://aka.ms/dotnet-core-eula)
- [Ochrana osobních údajů v Microsoftu](https://www.microsoft.com/trustcenter/privacy/)
- [Prohlášení o zásadách ochrany osobních údajů společnosti Microsoft](https://privacy.microsoft.com/privacystatement)
