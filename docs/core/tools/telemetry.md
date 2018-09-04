---
title: Telemetrická data sady SDK .NET core
description: Seznamte se s funkcemi telemetrie .NET Core SDK, které shromažďují informace o využití pro analýzy, která data se shromažďují a jak ji zakázat.
author: richlander
ms.author: mairaw
ms.date: 06/20/2018
ms.openlocfilehash: b60fc9d9d619334269343fd858a782cdfeb09ba4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513337"
---
# <a name="net-core-sdk-telemetry"></a>Telemetrická data sady SDK .NET core

[.NET Core SDK](index.md) zahrnuje [funkce telemetrie](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) , který shromažďuje informace o využití. Je důležité, že tým rozhraní .NET rozumí použití nástroje tak může zlepšit. Další informace najdete v tématu [co jsme se naučili v .NET Core SDK Telemetrie](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).

Shromážděná data jsou anonymní a publikované v souhrnné podobě k použití Microsoftem a komunitou v části [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).

## <a name="scope"></a>Rozsah

`dotnet` Příkaz se používá ke spuštění aplikace a rozhraní příkazového řádku .NET Core. `dotnet` Telemetrii neshromažďuje příkazu samého. Příkazy rozhraní příkazového řádku .NET Core spuštěné `dotnet` příkaz shromažďovat telemetrická data.

Telemetrie *není povoleno* při použití `dotnet` s příkazem pro samotného, není příkaz připojit:

- `dotnet`
- `dotnet [path-to-app]`

Telemetrie *je povoleno* při použití [příkazy rozhraní příkazového řádku .NET Core](index.md), jako například:

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

## <a name="how-to-opt-out"></a>Jak se chcete odhlásit

Ve výchozím nastavení je povolena funkce telemetrická data sady SDK .NET Core. Vyjádřit výslovný nesouhlas funkce telemetrie nastavením `DOTNET_CLI_TELEMETRY_OPTOUT` proměnnou prostředí, aby `1` nebo `true`.

## <a name="data-points"></a>Datové body

Funkci shromažďuje následující data:

- Časové razítko volání&#8224;
- Příkaz vyvolána (například "sestavení")&#8224;
- Tři octet IP adresy použité k určení zeměpisného umístění&#8224;
- `ExitCode` příkaz
- Nástroj test runner (pro projekty testů)
- Operační systém a verze&#8224;
- Určuje, zda jsou k dispozici v uzlu moduly runtime ID modulu runtime
- Verze .NET core SDK&#8224;

&#8224;Tato metrika je publikována.

Počínaje .NET Core SDK 2.0, jsou shromažďovány nové datové body:

- `dotnet` příkaz možností a argumentů: pouze známé možnosti a argumenty jsou shromážděná (ne libovolné řetězce).
- Určuje, zda sada SDK je spuštěn v kontejneru.
- Cílové architektury.
- Hodnoty hash adresy MAC: kryptograficky (SHA256) anonymní a jedinečné ID pro počítač. Tato metrika není publikována.
- Hodnoty hash aktuálního pracovního adresáře.

Funkci neshromažďuje osobní údaje, jako jsou uživatelská jména nebo e-mailové adresy. Nebude Kontrola kódu a nebude extrahovat citlivých dat na úrovni projektu, jako je například název, úložiště nebo autora. Data se odesílají bezpečně na servery Microsoftu pomocí [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technologie, uchovávat v části s omezeným přístupem a publikování na základě striktní bezpečnostní opatření z zabezpečené [službyAzureStorage](https://azure.microsoft.com/services/storage/) systémy.

Tým .NET chce vědět, jak se používají nástroje a pokud pracují dobře, nejsou sestavení pomocí nástrojů. Pokud máte podezření, že se citlivá data nebo, který sbírá telemetrických dat dat se nezabezpečeným způsobem nebo neoprávněně zpracována, založte problém v [dotnet/cli](https://github.com/dotnet/cli/issues) úložiště pro šetření.

## <a name="published-data"></a>Publikovaná data

Publikovaná data čtvrtletně je k dispozici a jsou uvedeny v tématu [Data o využití sady SDK .NET Core](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md). Jsou sloupce datového souboru:

- Časové razítko
- Occurrences&#8224;
- Příkaz
- Zeměpisné oblasti&#8225;
- Atribut OSFamily
- RuntimeID
- OSVersion
- SDKVersion

&#8224;*Výskyty* sloupec zobrazuje agregace počet použití tohoto příkazu pro tento řádek metrik daný den.

&#8225;Obvykle *zeměpisné oblasti* sloupec zobrazuje název země. V některých případech se v tomto sloupci, ať už z důvodu výzkumných pracovníků pomocí platformy .NET Core v Antarktida nebo nesprávné umístění dat zobrazí kontinent Antarktida.

### <a name="example"></a>Příklad

| Časové razítko      | Výskyty | Příkaz | Zeměpisné oblasti | Atribut OSFamily | RuntimeID     | OSVersion | SDKVersion |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| 4/16/2017 0:00 | 8           | Spuštění     | Uganda    | Darwin   | osx.10.12-x64 | 10.12     | 1.0.1      |

### <a name="datasets"></a>Datové sady

[2016 - 3. ČTVRTLETÍ](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)  
[2016 – 4.](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)  
[2017 – Q1](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)  
[2017 - 2. ČTVRTLETÍ](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)  
[2017 - 3. ČTVRTLETÍ](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q3.tsv)  
[2017 - 4.](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q4.tsv)  

Další datové sady jsou odeslány pomocí standardní formát adresy URL. Nahraďte `<YEAR>` rokem a nahradit `<QUARTER>` s čtvrtletí v roce (použijte `1`, `2`, `3`, nebo `4`). Soubory jsou v hodnoty oddělené tabulátorem (*TSV*) formát.

`https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv`

## <a name="license"></a>Licence

Je distribuce Microsoftu .NET Core licenci [smlouva EULA KNIHOVNY MICROSOFT .NET](https://aka.ms/dotnet-core-eula). Platnost této licence obsahuje oddíl "DATA" Povolit telemetrii (viz dole).

[Balíčky .NET NuGet](https://www.nuget.org/profiles/dotnetframework) používají stejné licence, ale nepovolí telemetrie (naleznete v tématu [oboru](#scope)).

> 2. DATA. Software může shromažďovat informace o vás a vaše užívání tohoto softwaru a zasílat je společnosti Microsoft. Microsoft může použít tyto informace k vylepšování našich produktů a služeb. Můžete získat další informace o shromažďování dat a používat v dokumentaci nápovědy a v prohlášení o ochraně osobních údajů na adrese http://go.microsoft.com/fwlink/?LinkId=528096. Pracuje vaše užívání tohoto softwaru vyjadřujete souhlas s těmito postupy.

## <a name="disclosure"></a>Zpřístupnění

.NET Core SDK zobrazí při prvním spuštění jednu z následující text [příkazy rozhraní příkazového řádku .NET Core](index.md) (například `dotnet restore`). Text může mírně lišit v závislosti na verzi sady SDK, kterou používáte. Toto prostředí "prvního spuštění" je, jak Microsoft upozorní vás na shromažďování dat.

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

- [Co jsme se naučili z telemetrická data sady SDK .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)
- [Odkaz na zdroj telemetrie (úložišti dotnet/cli)](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)
- [Data o využití sady SDK .NET core](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)
