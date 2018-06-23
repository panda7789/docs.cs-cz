---
title: .NET core SDK telemetrie
description: Seznamte se s funkcemi telemetrie .NET Core SDK, která shromažďují informace o využití za účelem analýzy, která data se shromažďují a jak ji zakázat.
author: richlander
ms.author: mairaw
ms.date: 06/20/2018
ms.openlocfilehash: f60a1eaa7b869676dfbb67529e7878ca9b9ca34a
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314874"
---
# <a name="net-core-sdk-telemetry"></a>.NET core SDK telemetrie

[.NET Core SDK](index.md) zahrnuje [telemetrie funkce](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) který shromažďuje informace o využití. Je důležité, aby týmem .NET znali použití nástrojů, je možné zlepšit. Další informace najdete v tématu [co jsme jste se naučili z .NET Core SDK Telemetrie](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).

Shromážděná data je anonymní a publikované v souhrnné podobě k použití společností Microsoft a komunitou pod [Creative Commons porušení licence](https://creativecommons.org/licenses/by/4.0/).

## <a name="scope"></a>Rozsah

`dotnet` Je příkaz použitý ke spuštění aplikace a rozhraní příkazového řádku .NET Core. `dotnet` Samotný příkaz nebude shromažďovat telemetrická data. Rozhraní .NET Core příkazového řádku spustit `dotnet` příkaz shromažďovat telemetrii.

Telemetrie *není povoleno* při použití `dotnet` samostatně, příkaz se žádný příkaz není připojen:

- `dotnet`
- `dotnet [path-to-app]`

Telemetrie *je povoleno* při použití [.NET Core rozhraní příkazového řádku](index.md), jako například:

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

## <a name="how-to-opt-out"></a>Postup chodit

Ve výchozím nastavení je povolena funkce telemetrie .NET Core SDK. Vyjádření výslovného nesouhlasu funkci telemetrie nastavením `DOTNET_CLI_TELEMETRY_OPTOUT` proměnnou prostředí `1` nebo `true`.

## <a name="data-points"></a>Datové body

Funkci shromažďuje následující data:

- Časové razítko volání&#8224;
- Příkaz vyvolat (například "sestavení")&#8224;
- Tři octet adresa IP použitá k určení zeměpisné umístění&#8224;
- `ExitCode` příkaz
- Spuštění testu (pro testovací projekty)
- Operační systém a verze&#8224;
- Jestli se nacházejí v uzlu moduly runtime ID modulu runtime
- Verze rozhraní .NET core SDK&#8224;

&#8224;Tato metrika je publikován.

Od verze rozhraní .NET Core SDK 2.0, se shromažďují nové datové body:

- `dotnet` příkaz Možnosti a argumenty: pouze známé argumenty a možnosti jsou shromážděná (ne libovolný řetězce).
- Zda je spuštěna sada SDK v kontejneru.
- Cílové architektury.
- Adresu MAC s použitím algoritmu hash: kryptograficky (SHA256) anonymní a jedinečné ID pro počítač. Tato metrika není publikována.
- Hash aktuální pracovní adresář.

Tato funkce nebude shromažďovat osobní údaje, jako jsou uživatelská jména nebo e-mailové adresy. Ji nelze kontrolovat kódu a není pro extrahování citlivých dat úrovni projektu, například název, úložišti nebo autora. Data se odesílají bezpečně servery Microsoftu pomocí [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technologie, uchovávat v části s omezeným přístupem a publikovat v části ovládací prvky přísných bezpečnostních ze zabezpečeného [Azure Storage](https://azure.microsoft.com/services/storage/) systémy.

Tým služby .NET chce vědět, jak se používají nástroje a pokud pracují dobře, co nejsou s nástroji pro vytváření. Pokud máte podezření, že telemetrii je shromažďování citlivá data nebo která data se nezabezpečeným nebo nesprávně zpracovává, problém v souboru [dotnet/cli](https://github.com/dotnet/cli/issues) úložiště pro šetření.

## <a name="published-data"></a>Publikovaná data

Publikovaná data čtvrtletně je k dispozici a jsou uvedeny v [Data o využití .NET Core SDK](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md). Sloupce datového souboru jsou:

- Časové razítko
- Occurrences&#8224;
- Příkaz
- Geography&#8225;
- Atribut OSFamily
- RuntimeID
- OSVersion
- SDKVersion

&#8224;*Výskytů* sloupec zobrazuje agregovaná počet tento příkaz použijte pro tento řádek metriky daný den.

&#8225;Obvykle *Geography* sloupec zobrazuje název země. V některých případech se zobrazí na kontinentě Antarktida v tomto sloupci, buď z důvodu výzkumných pracovníků pomocí .NET Core Antarktida nebo data nesprávné umístění.

### <a name="example"></a>Příklad

| Časové razítko      | Výskytů | Příkaz | Geography | Atribut OSFamily | RuntimeID     | OSVersion | SDKVersion |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| 4/16/2017 0:00 | 8           | Spustit     | Ugandy    | Darwin   | osx.10.12-x64 | 10.12     | 1.0.1      |

### <a name="datasets"></a>Datové sady

[2016 - 3. ČTVRTLETÍ](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)  
[2016 - 4.](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)  
[2017 - 1.](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)  
[2017 - DOTAZ Č. 2](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)  
[2017 - 3. ČTVRTLETÍ](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q3.tsv)  
[2017 – 4.](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q4.tsv)  

Další datové sady jsou odeslány standardní formátu adresy URL. Nahraďte `<YEAR>` s za rok a nahraďte `<QUARTER>` s čtvrtletí v roce (použijte `1`, `2`, `3`, nebo `4`). Soubory jsou v kartě s oddělovači (*TSV*) formátu.

`https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv`

## <a name="license"></a>Licence

Distribuce Microsoft .NET Core má licenci na [smlouvy EULA KNIHOVNY MICROSOFT .NET](https://aka.ms/dotnet-core-eula). Tuto licenci zahrnuje v části "DATA" Povolit telemetrii (zobrazené dole).

[Balíčky NuGet pro rozhraní .NET](https://www.nuget.org/profiles/dotnetframework) použít licence, které jsou stejné, ale nepovolíte telemetrie (najdete v části [oboru](#scope)).

> 2. DATA. Software může shromažďovat informace o vás a používání softwaru a který odesílat společnosti Microsoft. Microsoft může tyto informace využívat ke zlepšování našich produktů a služeb. Můžete získat další informace o shromažďování dat a použít v dokumentaci nápovědy a prohlášení o ochraně osobních údajů na adrese http://go.microsoft.com/fwlink/?LinkId=528096. Používání softwaru funguje jako svůj souhlas s tyto postupy.

## <a name="disclosure"></a>Zpřístupnění

.NET Core SDK zobrazí při prvním spuštění jeden z následující text [.NET Core rozhraní příkazového řádku](index.md) (například `dotnet restore`). Text se může mírně lišit v závislosti na verzi sady SDK, kterou používáte. Toto prostředí "nejprve spustit" je, jak Microsoft upozorní vás na shromažďování dat.

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core: https://aka.ms/dotnet-docs
Use 'dotnet --help' to see available commands or visit: https://aka.ms/dotnet-cli-docs

Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience. 
The data is anonymous and doesn't include command-line arguments. 
The data is collected by Microsoft and shared with the community. 
You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

## <a name="see-also"></a>Viz také:

[Co jsme jste se naučili z .NET Core SDK Telemetrie](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)  
[Odkaz na zdroj telemetrie (úložišti dotnet nebo rozhraní příkazového řádku)](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)  
[Data o využití .NET core SDK](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)  
