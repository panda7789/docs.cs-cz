---
title: Kolekce telemetrie podle ML.NET CLI
description: Další informace o ML.NET funkce telemetrie cli, které shromažďují informace o využití pro analýzu, která data jsou shromažďována a jak je zakázat. Najděte také odkazy na licenční smlouvu .NET a informace o dodržování nařízení Microsoft GDPR.
ms.topic: conceptual
ms.date: 09/03/2019
ms.custom: mlnet-tooling
ms.openlocfilehash: 99e11acba343cc689c3219ca9316144fc62cd618
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78849741"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a>Kolekce telemetrie podle ML.NET CLI

Rozhraní [ML.NET CLI](https://aka.ms/mlnet-cli) obsahuje funkci telemetrie, která shromažďuje anonymní data o využití, která jsou agregována pro použití společností Microsoft.

## <a name="how-microsoft-uses-the-data"></a>Jak společnost Microsoft používá data

Produktový tým používá ML.NET telemetrická data cli, které pomáhají pochopit, jak zlepšit nástroje. Pokud například zákazníci zřídka používají určitý úkol strojového učení, produktový tým zkoumá proč a pomocí zjištění upřednostňuje vývoj funkcí. ML.NET telemetrii CLI také pomáhá s laděním problémů, jako jsou selhání a anomálie kódu.

I když produktový tým tento přehled oceňuje, víme také, že ne každý chce tato data odeslat. [Zjistěte, jak zakázat telemetrii.](#opt-out-of-data-collection)

## <a name="scope"></a>Rozsah

Příkaz `mlnet` spustí ML.NET CLI, ale samotný příkaz neshromažďuje telemetrii.

Telemetrie *není povolena* při `mlnet` spuštění příkazu bez připojeného jiného příkazu. Například:

- `mlnet`
- `mlnet --help`

Telemetrie *je povolena* při spuštění [příkazu ML.NET CLI](../reference/ml-net-cli-reference.md), například `mlnet auto-train`.

## <a name="opt-out-of-data-collection"></a>Odhlásit se ze shromažďování údajů

Funkce telemetrie ML.NET CLI je ve výchozím nastavení povolena.

Odhlásit se z funkce telemetrie nastavením proměnné `MLDOTNET_CLI_TELEMETRY_OPTOUT` prostředí na `1` nebo `true`. Tato proměnná prostředí platí globálně pro nástroj ML.NET CLI.

## <a name="data-points-collected"></a>Shromážděné datové body

Tato funkce shromažďuje následující data:

- Jaký příkaz byl vyvolán, například`auto-train`
- Použité názvy parametrů příkazového řádku (to znamená "název datové sady, název sloupce popisku, ml-task, výstupní cesta, max-exploration-time, podrobnost")
- Hashed MAC adresa: kryptograficky (SHA256) anonymní a jedinečné ID pro počítač
- Časové razítko vyvolání
- Tři oktetové IP adresy (ne úplná IP adresa) používané pouze k určení zeměpisné polohy
- Název všech použitých argumentů/parametrů. Nejsou hodnoty zákazníka, například řetězce
- Název souboru hashed dataset
- Kontejner velikosti souboru datové sady
- Operační systém a verze
- Hodnota parametru --task: Kategorické `regression` `binary-classification`hodnoty, například , a`multiclass-classification`
- ML.NET verze CLI (tj. 0.3.27703.4)

Data se bezpečně odesílají na servery Microsoftu pomocí technologie [Azure Application Insights,](https://azure.microsoft.com/services/application-insights/) která je držena s omezeným přístupem a používá se pod přísnými bezpečnostními kontrolami ze zabezpečených systémů [Azure Storage.](https://azure.microsoft.com/services/storage/)

### <a name="data-points-not-collected"></a>Neshromažďované datové body

Funkce telemetrie *neshromažďuje:*

- osobních údajů, jako jsou uživatelská jména
- názvy souborů datové sady
- data ze souborů datové sady

Pokud máte podezření, že telemetrie ML.NET CLI shromažďuje citlivá data nebo že jsou data nebezpečně nebo nevhodně zpracována, zasuzujte problém do [úložiště ML.NET](https://github.com/dotnet/machinelearning) pro šetření.

## <a name="license"></a>Licence

Distribuce ML.NET cli společnosti Microsoft je licencována s [licenčními podmínkami pro software společnosti Microsoft: Microsoft .NET Library](https://aka.ms/dotnet-core-eula). Podrobnosti o shromažďování a zpracování údajů naleznete v části s názvem "Data".

## <a name="disclosure"></a>Zveřejnění

Při prvním spuštění [příkazu ML.NET příkazu příkazu příkazu,](../reference/ml-net-cli-reference.md) například `mlnet auto-train`, nástroj ML.NET příkazového příkazu zobrazí zpřístupnění text, který vám řekne, jak se odhlásit z telemetrie. Text se může mírně lišit v závislosti na verzi spuštěného vodního úpově.

## <a name="see-also"></a>Viz také

- [ML.NET odkaz na cli](../reference/ml-net-cli-reference.md)
- [Licenční podmínky pro software společnosti Microsoft: Knihovna Microsoft .NET](https://aka.ms/dotnet-core-eula)
- [Ochrana osobních údajů ve společnosti Microsoft](https://www.microsoft.com/trustcenter/privacy/)
- [Prohlášení společnosti Microsoft o zásadách ochrany osobních údajů](https://privacy.microsoft.com/privacystatement)
