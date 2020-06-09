---
title: Nasazení rozhraní .NET pro Apache Spark pro pracovní procesy a uživatelem definované binární soubory funkcí
description: Naučte se, jak nasadit rozhraní .NET pro Apache Spark pro pracovní procesy a uživatelem definované binární soubory funkcí.
ms.date: 01/21/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 042f336431a1c8cad7d94cf10cbe64b72ddfce5b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596458"
---
# <a name="deploy-net-for-apache-spark-worker-and-user-defined-function-binaries"></a>Nasazení rozhraní .NET pro Apache Spark pro pracovní procesy a uživatelem definované binární soubory funkcí

Tento postup poskytuje obecné pokyny k nasazení rozhraní .NET pro Apache Spark pro pracovní procesy a uživatelem definované binární soubory funkcí. Zjistíte, které proměnné prostředí se mají nastavit, a také některé běžně používané parametry pro spouštění aplikací pomocí `spark-submit` .

## <a name="configurations"></a>Konfigurace
Konfigurace zobrazují obecné proměnné prostředí a nastavení parametrů, aby bylo možné nasadit rozhraní .NET pro Apache Spark pro pracovní procesy a uživatelem definované binární soubory funkcí.

### <a name="environment-variables"></a>Proměnné prostředí
Při nasazování pracovních procesů a psaní UDF je k dispozici několik běžně používaných proměnných prostředí, které je třeba nastavit:

| Proměnná prostředí         | Popis
| :--------------------------- | :----------
| DOTNET_WORKER_DIR            | Cesta k <code>Microsoft.Spark.Worker</code> vygenerování binárního souboru.</br>Používá ho ovladač Spark a předává se do prováděcích modulů Spark. Pokud tato proměnná není nastavená, prováděče Spark budou hledat v cestě zadané v <code>PATH</code> proměnné prostředí.</br>_například "C:\bin\Microsoft.Spark.Worker"_
| DOTNET_ASSEMBLY_SEARCH_PATHS | Cesty oddělené čárkami, kde <code>Microsoft.Spark.Worker</code> budou načtena sestavení.</br>Všimněte si, že pokud cesta začíná znakem ".", bude pracovní adresář předcházet. Pokud v **režimu příze**, "." by představovalo pracovní adresář kontejneru.</br>_například "C:\Users \\ &lt; uživatelské jméno &gt; \\ &lt; mysparkapp &gt; \bin\debug \\ &lt; dotnet verze &gt; "_
| DOTNET_WORKER_DEBUG          | Pokud chcete ladit systém <a href="https://github.com/dotnet/spark/blob/master/docs/developer-guide.md#debugging-user-defined-function-udf">souborů UDF</a>, nastavte před spuštěním tuto proměnnou prostředí na <code>1</code> <code>spark-submit</code> .

### <a name="parameter-options"></a>Možnosti parametrů
Jakmile je aplikace Spark připojená do [balíčku](https://spark.apache.org/docs/latest/submitting-applications.html#bundling-your-applications-dependencies), můžete ji spustit pomocí `spark-submit` . V následující tabulce jsou uvedeny některé běžně používané možnosti:

| Název parametru        | Popis
| :---------------------| :----------
| --Třída               | Vstupní bod pro vaši aplikaci.</br>_například org. Apache. spark. deploy. dotnet. DotnetRunner_
| – hlavní              | <a href="https://spark.apache.org/docs/latest/submitting-applications.html#master-urls">Hlavní adresa URL</a> clusteru</br>_např. příze_
| --Deploy-Mode         | Zda se má ovladač nasadit do pracovních uzlů ( <code>cluster</code> ) nebo místně jako externí klient ( <code>client</code> ).</br>Výchozí<code>client</code>
| --conf                | Libovolná vlastnost konfigurace Sparku ve <code>key=value</code> formátu</br>_například Spark. příze. appMasterEnv. DOTNET_WORKER_DIR = .\worker\Microsoft.Spark.Worker_
| --soubory               | Čárkami oddělený seznam souborů, které se umístí do pracovního adresáře každého prováděcího modulu.<br/><ul><li>Upozorňujeme, že tato možnost je platná pouze pro režim příze.</li><li>Podporuje zadání názvů souborů s # podobným Hadoop.</br></ul>_například <code>myLocalSparkApp.dll#appSeen.dll</code> . Vaše aplikace by měla používat název jako <code>appSeen.dll</code> odkaz na <code>myLocalSparkApp.dll</code> spuštění v případě příze._</li>
| --archivy          | Čárkami oddělený seznam archivů, které se mají extrahovat do pracovního adresáře každého prováděcího modulu.</br><ul><li>Upozorňujeme, že tato možnost je platná pouze pro režim příze.</li><li>Podporuje zadání názvů souborů s # podobným Hadoop.</br></ul>_například <code>hdfs://&lt;path to your worker file&gt;/Microsoft.Spark.Worker.zip#worker</code> . Tato akce zkopíruje a extrahuje soubor zip do <code>worker</code> složky._</li>
| aplikace – jar       | Cesta k balíčku jar včetně vaší aplikace a všech závislostí.</br>_např. hdfs:// &lt; cesta k vašemu jar &gt; /Microsoft-Spark- &lt; verze &gt; . jar_
| argumenty aplikace | Argumenty předané metodě Main třídy Main, pokud existují.</br>_např. HDFS:// &lt; cesta k aplikaci &gt; / &lt; vaše aplikace &gt; . zip &lt; &gt; &lt; argumenty aplikace název aplikace&gt;_

> [!NOTE]
> Zadejte všechny `--options` před spuštěním `application-jar` aplikací s `spark-submit` , jinak budou ignorovány. Další informace najdete v tématu [ `spark-submit` Možnosti](https://spark.apache.org/docs/latest/submitting-applications.html) a [spuštění Sparku v podrobnostech o přízi](https://spark.apache.org/docs/latest/running-on-yarn.html).

## <a name="frequently-asked-questions"></a>Nejčastější dotazy
### <a name="when-i-run-a-spark-app-with-udfs-i-get-a-filenotfoundexception-error-what-should-i-do"></a>Při spuštění aplikace Spark s UDF se zobrazí chyba "FileNotFoundException". Co bych měl/a dělat?
> **Chyba:** [Chyba] [TaskRunner] [0] ProcessStream () se nezdařilo. výjimka: System. IO. FileNotFoundException: sestavení ' MySparkApp, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = null ' nebyl nalezen: ' mySparkApp. dll '

**Odpověď:** Ověřte, že `DOTNET_ASSEMBLY_SEARCH_PATHS` je správně nastavená proměnná prostředí. Měla by to být cesta, která obsahuje vaše `mySparkApp.dll` .

### <a name="after-i-upgraded-my-net-for-apache-spark-version-and-reset-the-dotnet_worker_dir-environment-variable-why-do-i-still-get-the-following-ioexception-error"></a>Po upgradu rozhraní .NET pro Apache Spark verzi a resetování `DOTNET_WORKER_DIR` proměnné prostředí se mi zobrazí následující `IOException` Chyba?
> **Chyba:** Ztráta úlohy 0,0 ve fázi 11,0 (TID 24, localhost, ovladač prováděcího modulu): Java. IO. IOException: nelze spustit program Microsoft. spark. Worker. exe: Chyba CreateProcess = 2, systém nemůže najít zadaný soubor.

**Odpověď:** Zkuste nejdřív restartovat okno PowerShellu (nebo jiná okna příkazu), aby bylo možné převzít nejnovější hodnoty proměnných prostředí. Pak program spusťte.

### <a name="after-submitting-my-spark-application-i-get-the-error-systemtypeloadexception-could-not-load-type-systemruntimeremotingcontextscontext"></a>Po odeslání aplikace Spark se zobrazí chyba `System.TypeLoadException: Could not load type 'System.Runtime.Remoting.Contexts.Context'` .
> **Chyba:** [Chyba] [TaskRunner] [0] ProcessStream () se nezdařilo s výjimkou: System. TypeLoadException: nelze načíst typ ' System. Runtime. Fail. kontexts. Context ' ze sestavení ' mscorlib, Version = 4.0.0.0, Culture = neutral, PublicKeyToken =... '.

**Odpověď:** Ověřte `Microsoft.Spark.Worker` verzi, kterou používáte. Existují dvě verze: **.NET Framework 4.6.1** a **.NET Core 2.1. x**. V takovém případě, `Microsoft.Spark.Worker.net461.win-x64-<version>` (který si můžete [Stáhnout](https://github.com/dotnet/spark/releases)), by se měla použít jenom v případě, že `System.Runtime.Remoting.Contexts.Context` je k dis.NET Framework.

### <a name="how-do-i-run-my-spark-application-with-udfs-on-yarn-which-environment-variables-and-parameters-should-i-use"></a>Návody spustit aplikaci Spark s UDF při PŘÍZi? Které proměnné prostředí a parametry mám použít?

**Odpověď:** Chcete-li spustit aplikaci Spark na PŘÍZi, proměnné prostředí by měly být zadány jako `spark.yarn.appMasterEnv.[EnvironmentVariableName]` . Jako příklad použijte `spark-submit` :

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
* [Ladění rozhraní .NET pro Apache Spark aplikaci ve Windows](debug.md)
