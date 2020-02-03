---
title: Nasazení rozhraní .NET pro Apache Spark pro pracovní procesy a uživatelem definované binární soubory funkcí
description: Naučte se, jak nasadit rozhraní .NET pro Apache Spark pro pracovní procesy a uživatelem definované binární soubory funkcí.
ms.date: 01/21/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: f9197ca3cf8066f0849ebbe70d7757c9035d02f6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76748529"
---
# <a name="deploy-net-for-apache-spark-worker-and-user-defined-function-binaries"></a>Nasazení rozhraní .NET pro Apache Spark pro pracovní procesy a uživatelem definované binární soubory funkcí

Tento postup poskytuje obecné pokyny k nasazení rozhraní .NET pro Apache Spark pro pracovní procesy a uživatelem definované binární soubory funkcí. Zjistíte, které proměnné prostředí se mají nastavit, a také některé běžně používané parametry pro spouštění aplikací pomocí `spark-submit`.

## <a name="configurations"></a>Konfigurace
Konfigurace zobrazují obecné proměnné prostředí a nastavení parametrů, aby bylo možné nasadit rozhraní .NET pro Apache Spark pro pracovní procesy a uživatelem definované binární soubory funkcí.

### <a name="environment-variables"></a>Proměnné prostředí
Při nasazování pracovních procesů a psaní UDF je k dispozici několik běžně používaných proměnných prostředí, které je třeba nastavit: 

| Proměnná prostředí         | Popis
| :--------------------------- | :---------- 
| DOTNET_WORKER_DIR            | Cesta k vygenerování binárního <code>Microsoft.Spark.Worker</code>.</br>Používá ho ovladač Spark a předává se do prováděcích modulů Spark. Pokud tato proměnná není nastavená, prováděče Spark budou hledat v cestě zadané v proměnné prostředí <code>PATH</code>.</br>_například "C:\bin\Microsoft.Spark.Worker"_
| DOTNET_ASSEMBLY_SEARCH_PATHS | Čárkami oddělené cesty, kde <code>Microsoft.Spark.Worker</code> načte sestavení.</br>Všimněte si, že pokud cesta začíná znakem ".", bude pracovní adresář předcházet. Pokud v **režimu příze**, "." by představovalo pracovní adresář kontejneru.</br>_například "C:\Users\\&lt;uživatelské jméno&gt;\\&lt;mysparkapp&gt;\bin\Debug\\&lt;dotnet verze&gt;"_
| DOTNET_WORKER_DEBUG          | Pokud chcete ladit systém <a href="https://github.com/dotnet/spark/blob/master/docs/developer-guide.md#debugging-user-defined-function-udf">souborů UDF</a>, nastavte tuto proměnnou prostředí na <code>1</code> před spuštěním <code>spark-submit</code>.

### <a name="parameter-options"></a>Možnosti parametrů
Jakmile je aplikace Spark připojená do [balíčku](https://spark.apache.org/docs/latest/submitting-applications.html#bundling-your-applications-dependencies), můžete ji spustit pomocí `spark-submit`. V následující tabulce jsou uvedeny některé běžně používané možnosti: 

| Název parametru        | Popis
| :---------------------| :---------- 
| --Třída               | Vstupní bod pro vaši aplikaci.</br>_například org. Apache. spark. deploy. dotnet. DotnetRunner_
| – hlavní              | <a href="https://spark.apache.org/docs/latest/submitting-applications.html#master-urls">Hlavní adresa URL</a> clusteru</br>_např. příze_
| --Deploy-Mode         | Určuje, jestli se má ovladač nasadit na pracovní uzly (<code>cluster</code>) nebo lokálně jako externí klient (<code>client</code>).</br>Výchozí: <code>client</code>
| --conf                | Libovolná vlastnost konfigurace Sparku ve formátu <code>key=value</code>.</br>_například Spark. příze. appMasterEnv. DOTNET_WORKER_DIR = .\worker\Microsoft.Spark.Worker_
| --soubory               | Čárkami oddělený seznam souborů, které se umístí do pracovního adresáře každého prováděcího modulu.<br/><ul><li>Upozorňujeme, že tato možnost je platná pouze pro režim příze.</li><li>Podporuje zadání názvů souborů s # podobným Hadoop.</br></ul>_např. <code>myLocalSparkApp.dll#appSeen.dll</code>. Vaše aplikace by měla používat název jako <code>appSeen.dll</code> k odkazování <code>myLocalSparkApp.dll</code> při spuštění na VLÁKNě._</li>
| --archivy          | Čárkami oddělený seznam archivů, které se mají extrahovat do pracovního adresáře každého prováděcího modulu.</br><ul><li>Upozorňujeme, že tato možnost je platná pouze pro režim příze.</li><li>Podporuje zadání názvů souborů s # podobným Hadoop.</br></ul>_např. <code>hdfs://&lt;path to your worker file&gt;/Microsoft.Spark.Worker.zip#worker</code>. Tato akce zkopíruje a extrahuje soubor zip do složky <code>worker</code>._</li>
| aplikace – jar       | Cesta k balíčku jar včetně vaší aplikace a všech závislostí.</br>_např. hdfs://&lt;cestu k/Microsoft-Spark-&gt;&lt;verze&gt;. jar_
| argumenty aplikace | Argumenty předané metodě Main třídy Main, pokud existují.</br>_například hdfs://&lt;cestu k aplikaci&gt;/&lt;vaší aplikaci&gt;. zip &lt;název vaší aplikace&gt; &lt;argumenty aplikace&gt;_

> [!NOTE]
> Zadejte všechny `--options` před `application-jar` při spouštění aplikací pomocí `spark-submit`, jinak budou ignorovány. Další informace najdete v tématu [možnosti`spark-submit`](https://spark.apache.org/docs/latest/submitting-applications.html) a [spuštění Sparku v PODROBNOSTech o přízi](https://spark.apache.org/docs/latest/running-on-yarn.html).

## <a name="frequently-asked-questions"></a>Nejčastější dotazy
### <a name="when-i-run-a-spark-app-with-udfs-i-get-a-filenotfoundexception-error-what-should-i-do"></a>Při spuštění aplikace Spark s UDF se zobrazí chyba "FileNotFoundException". Co bych měl/a dělat?
> **Chyba:** [Chyba] [TaskRunner] [0] ProcessStream () se nezdařilo. výjimka: System. IO. FileNotFoundException: sestavení ' MySparkApp, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = null ' nebyl nalezen: ' mySparkApp. dll '

**Odpověď:** Ověřte, že je správně nastavená proměnná prostředí `DOTNET_ASSEMBLY_SEARCH_PATHS`. Měla by to být cesta, která obsahuje vaše `mySparkApp.dll`.

### <a name="after-i-upgraded-my-net-for-apache-spark-version-and-reset-the-dotnet_worker_dir-environment-variable-why-do-i-still-get-the-following-ioexception-error"></a>Po upgradu rozhraní .NET pro Apache Spark verzi a resetování proměnné prostředí `DOTNET_WORKER_DIR` se mi zobrazí následující `IOException` chyba?
> **Chyba:** Ztráta úlohy 0,0 ve fázi 11,0 (TID 24, localhost, ovladač prováděcího modulu): Java. IO. IOException: nelze spustit program Microsoft. spark. Worker. exe: Chyba CreateProcess = 2, systém nemůže najít zadaný soubor.

**Odpověď:** Zkuste nejdřív restartovat okno PowerShellu (nebo jiná okna příkazu), aby bylo možné převzít nejnovější hodnoty proměnných prostředí. Pak program spusťte.

### <a name="after-submitting-my-spark-application-i-get-the-error-systemtypeloadexception-could-not-load-type-systemruntimeremotingcontextscontext"></a>Po odeslání aplikace Spark se zobrazí chyba `System.TypeLoadException: Could not load type 'System.Runtime.Remoting.Contexts.Context'`.
> **Chyba:** [Chyba] [TaskRunner] [0] ProcessStream () se nezdařilo s výjimkou: System. TypeLoadException: nelze načíst typ ' System. Runtime. Fail. kontexts. Context ' ze sestavení ' mscorlib, Version = 4.0.0.0, Culture = neutral, PublicKeyToken =... '.

**Odpověď:** Podívejte se na verzi `Microsoft.Spark.Worker`, kterou používáte. Existují dvě verze: **.NET Framework 4.6.1** a **.NET Core 2.1. x**. V takovém případě je vhodné použít `Microsoft.Spark.Worker.net461.win-x64-<version>` (které si můžete [Stáhnout](https://github.com/dotnet/spark/releases)), protože `System.Runtime.Remoting.Contexts.Context` je jenom pro .NET Framework.

### <a name="how-do-i-run-my-spark-application-with-udfs-on-yarn-which-environment-variables-and-parameters-should-i-use"></a>Návody spustit aplikaci Spark s UDF při PŘÍZi? Které proměnné prostředí a parametry mám použít?

**Odpověď:** Chcete-li spustit aplikaci Spark na PŘÍZi, proměnné prostředí by měly být zadány jako `spark.yarn.appMasterEnv.[EnvironmentVariableName]`. Jako příklad použijte `spark-submit`:

```powershell
spark-submit \
--class org.apache.spark.deploy.dotnet.DotnetRunner \
--master yarn \
--deploy-mode cluster \
--conf spark.yarn.appMasterEnv.DOTNET_WORKER_DIR=./worker/Microsoft.Spark.Worker-<version> \
--conf spark.yarn.appMasterEnv.DOTNET_ASSEMBLY_SEARCH_PATHS=./udfs \
--archives hdfs://<path to your files>/Microsoft.Spark.Worker.net461.win-x64-<version>.zip#worker,hdfs://<path to your files>/mySparkApp.zip#udfs \
hdfs://<path to jar file>/microsoft-spark-2.4.x-<version>.jar \
hdfs://<path to your files>/mySparkApp.zip mySparkApp
```

## <a name="next-steps"></a>Další kroky

* [Začínáme s .NET pro Apache Spark](../tutorials/get-started.md)
* [Ladění rozhraní .NET pro Apache Spark aplikaci ve Windows](../how-to-guides/debug.md)
