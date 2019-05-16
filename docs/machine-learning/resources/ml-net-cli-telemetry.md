---
title: Shromažďování telemetrie pomocí rozhraní příkazového řádku ML.NET
description: Další informace o rozhraní příkazového řádku ML.NET telemetrické funkce, která shromažďují využití informace pro analýzu, která data se shromažďují a jak ji zakázat. Dozvíte se taky, odkazy na licenční smlouvy .NET a informace o dodržování předpisů Microsoft GDPR.
ms.topic: conceptual
ms.date: 05/05/2019
ms.custom: ''
ms.openlocfilehash: 36f4af48615e2e3247f8e21343d0a00519ba1c0a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645025"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a>Shromažďování telemetrie pomocí rozhraní příkazového řádku ML.NET

[ML.NET CLI](http://aka.ms/mlnet-cli) obsahuje funkci telemetrická data, která shromažďuje anonymní data o využití, která se zobrazují se pro použití společností Microsoft.

## <a name="how-microsoft-uses-the-data"></a>Jak Microsoft používá data

Produktový tým pochopit, jak vylepšit nástroje pomocí rozhraní příkazového řádku ML.NET telemetrická data. Například pokud zřídka používají zákazníci konkrétní služby machine learning úkolu, produktový tým prověří důvod, proč a zjištění používá k určení priority vývoj funkcí. Rozhraní příkazového řádku ML.NET telemetrie vám také pomůže s laděním problémů, jako je například selhání a kód anomálie. 

Zatímco produktový tým oceňuje tyto informace, Víme také, že ne každý chce, aby se tato data Neodesílat. [Zjistěte, jak zakázat telemetrii.](#opt-out-of-data-collection)

## <a name="scope"></a>Scope

`mlnet` Spustí příkaz rozhraní příkazového řádku ML.NET, ale samotný příkaz telemetrii neshromažďuje.

Telemetrie *není povoleno* při spuštění `mlnet` příkaz příkazem žádné další připojené. Příklad:

- `mlnet`
- `mlnet --help`

Telemetrie *je povoleno* při spuštění [příkazu rozhraní příkazového řádku ML.NET](../reference/ml-net-cli-reference.md), například `mlnet auto-train`.

## <a name="opt-out-of-data-collection"></a>Odhlásit ze shromažďování dat

Ve výchozím nastavení je povolena funkce telemetrie ML.NET rozhraní příkazového řádku.

Vyjádřit výslovný nesouhlas funkce telemetrie nastavením `DOTNET_CLI_TELEMETRY_OPTOUT` proměnnou prostředí, aby `1` nebo `true`. Tato proměnná prostředí se týká globálně nástroj rozhraní příkazového řádku .NET.

## <a name="data-points-collected"></a>Shromážděné datových bodů

Funkci shromažďuje následující data:

- Byla vyvolána jaké příkazu, jako například `auto-train`
- Názvy parametrů příkazového řádku používá (to znamená "název datové sady, popisek název sloupce, ml úkolu, výstupní cesta, max běhu zkoumání podrobností")
- Hodnoty hash adresy MAC: kryptograficky (SHA256) anonymní a jedinečné ID počítače
- Časové razítko vyvolání
- Tři octet IP adresa (IP adresa není úplně) používá jenom k určení zeměpisného umístění
- Název všech argumentů a parametrů použitých. Není zákazníka hodnoty, jako jsou třeba řetězce
- Název souboru hashované datové sady
- Interval velikosti souboru datové sady
- Operační systém a verze
- Hodnota parametru--úloh: Hodnoty zařazené do kategorií, jako například `regression`, `binary-classification`, a `multiclass-classification`
- Verze rozhraní příkazového řádku ML.NET (tj. 0.3.27703.4)

Data se odesílají bezpečně na servery Microsoftu pomocí [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technologie nachází v části s omezeným přístupem a použít v striktní bezpečnostní opatření ze zabezpečeného [služby Azure Storage](https://azure.microsoft.com/services/storage/) systémy.

### <a name="data-points-not-collected"></a>Datové body nejsou shromážděna
Funkce telemetrie *nebude* shromažďovat:
- osobní údaje, jako jsou uživatelská jména
- názvy souborů datové sady
- data z datové sady souborů

Pokud máte podezření, že se citlivá data nebo, který sbírá telemetrie ML.NET rozhraní příkazového řádku dat probíhá nezabezpečeným způsobem nebo neoprávněně zpracována, založte problém v [ML.NET](https://github.com/dotnet/machinelearning) úložiště pro šetření.

## <a name="license"></a>Licence

Je distribuce Microsoftu příkazového řádku ML.NET licenci [licenční podmínky pro Software společnosti Microsoft: Knihovna rozhraní Microsoft .NET](https://aka.ms/dotnet-core-eula). Podrobnosti o shromažďování dat a zpracování najdete v části s názvem "Data".

## <a name="disclosure"></a>Zpřístupnění

Při prvním spuštění [příkazu rozhraní příkazového řádku ML.NET](../reference/ml-net-cli-reference.md) jako `mlnet auto-train`, nástroje rozhraní příkazového řádku ML.NET zobrazí zpřístupnění text, který vysvětluje, jak vyjádřit výslovný nesouhlas telemetrická data. Text může mírně lišit v závislosti na verzi rozhraní příkazového řádku, kterou používáte.

## <a name="see-also"></a>Viz také:
- [Referenční informace k ML.NET CLI](../reference/ml-net-cli-reference.md)
- [Licenční podmínky pro Software společnosti Microsoft: Knihovna rozhraní Microsoft .NET](https://aka.ms/dotnet-core-eula)
- [Ochrana osobních údajů společnosti Microsoft](https://www.microsoft.com/en-us/trustcenter/privacy/)
- [Prohlášení o ochraně osobních údajů společnosti Microsoft](https://privacy.microsoft.com/en-us/privacystatement)
