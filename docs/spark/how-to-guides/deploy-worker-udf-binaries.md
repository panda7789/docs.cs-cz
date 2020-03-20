---
title: Nasazení rozhraní .NET pro pracovníka Apache Spark a uživatelem definované binární soubory funkcí
description: Přečtěte si, jak nasadit rozhraní .NET pro pracovníka Apache Spark a uživatelem definované binární soubory funkcí.
ms.date: 01/21/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: f373ccee398149adcadeac91f02d9896214706b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187599"
---
# <a name="deploy-net-for-apache-spark-worker-and-user-defined-function-binaries"></a>Nasazení rozhraní .NET pro pracovníka Apache Spark a uživatelem definované binární soubory funkcí

Tento návod poskytuje obecné pokyny, jak nasadit rozhraní .NET pro pracovníka Apache Spark a uživatelem definované binární soubory funkcí. Dozvíte se, které proměnné prostředí nastavit, stejně jako některé běžně `spark-submit`používané parametry pro spouštění aplikací s .

## <a name="configurations"></a>Konfigurace
Konfigurace zobrazují obecné proměnné prostředí a nastavení parametrů pro nasazení rozhraní .NET pro pracovníka Apache Spark a uživatelem definované binární soubory funkcí.

### <a name="environment-variables"></a>Proměnné prostředí
Při nasazování pracovníků a psaní udfs existuje několik běžně používaných proměnných prostředí, které budete muset nastavit:

| Proměnná prostředí         | Popis
| :--------------------------- | :----------
| DOTNET_WORKER_DIR            | Cesta, <code>Microsoft.Spark.Worker</code> kde byl vygenerován binární soubor.</br>Používá ho ovladač Spark a bude předán vykonavatelům Spark. Pokud tato proměnná není nastavena, budou vykonavatelé Spark prohledávat cestu zadanou v proměnné <code>PATH</code> prostředí.</br>_například "C:\bin\Microsoft.Spark.Worker"_
| DOTNET_ASSEMBLY_SEARCH_PATHS | Cesty oddělené čárkami, <code>Microsoft.Spark.Worker</code> kde budou načítat sestavení.</br>Všimněte si, že pokud cesta začíná na ".", bude pracovní adresář předřazený. Pokud v **režimu příze**, "." by představovaly pracovní adresář kontejneru.</br>_například\\&lt;"C:\Uživatelské jméno&gt;\\&lt;mysparkapp&gt;\bin\Debug\\&lt;dotnet version&gt;"_
| DOTNET_WORKER_DEBUG          | Pokud chcete <a href="https://github.com/dotnet/spark/blob/master/docs/developer-guide.md#debugging-user-defined-function-udf">ladit UDF</a>, nastavte tuto proměnnou prostředí před <code>1</code> spuštěním <code>spark-submit</code>.

### <a name="parameter-options"></a>Možnosti parametrů
Jakmile je aplikace Spark [sbalená](https://spark.apache.org/docs/latest/submitting-applications.html#bundling-your-applications-dependencies), `spark-submit`můžete ji spustit pomocí . V následující tabulce jsou uvedeny některé běžně používané možnosti:

| Název parametru        | Popis
| :---------------------| :----------
| --třída               | Vstupní bod pro vaši aplikaci.</br>_například org.apache.spark.deploy.dotnet.DotnetRunner_
| --master              | Adresa <a href="https://spark.apache.org/docs/latest/submitting-applications.html#master-urls">URL hlavního serveru</a> pro cluster.</br>_například příze_
| --deploy-mode         | Určuje, zda má být ovladač<code>cluster</code>nasazen v pracovních uzlech ( ) nebo místně jako externí klient (<code>client</code>).</br>Výchozí:<code>client</code>
| --conf                | Libovolná vlastnost konfigurace <code>key=value</code> Spark ve formátu.</br>_například spark.yarn.appMasterEnv.DOTNET_WORKER_DIR=.\worker\Microsoft.Spark.Worker_
| --soubory               | Seznam souborů oddělených čárkami, které mají být umístěny do pracovního adresáře každého vykonavatele.<br/><ul><li>Vezměte prosím na vědomí, že tato možnost je použitelná pouze pro režim příze.</li><li>Podporuje určení názvů souborů s # podobně jako Hadoop.</br></ul>_např. <code>myLocalSparkApp.dll#appSeen.dll</code> Vaše aplikace by měla <code>appSeen.dll</code> používat <code>myLocalSparkApp.dll</code> název jako odkaz při spuštění na YARN._</li>
| --archivy          | Seznam archivů oddělených čárkami, které mají být extrahovány do pracovního adresáře každého vykonavatele.</br><ul><li>Vezměte prosím na vědomí, že tato možnost je použitelná pouze pro režim příze.</li><li>Podporuje určení názvů souborů s # podobně jako Hadoop.</br></ul>_např. <code>hdfs://&lt;path to your worker file&gt;/Microsoft.Spark.Worker.zip#worker</code> Tím zkopírujete a extrahujete soubor zip do <code>worker</code> složky._</li>
| aplikace-jar       | Cesta k přibalené nádobě včetně vaší aplikace a všech závislostí.</br>_například&lt;hdfs:// cestu k&gt;vaší nádobě&lt;/microsoft-spark- version&gt;.jar_
| argumenty aplikace | Argumenty předány hlavní metodě vaší hlavní třídy, pokud existuje.</br>_hdfs://&lt;cestu k&gt;/&lt;aplikaci aplikace&gt;.zip &lt;název&gt; &lt;aplikace args&gt;_

> [!NOTE]
> Zadejte `--options` všechny `application-jar` před při `spark-submit`spouštění aplikací s , jinak budou ignorovány. Další informace naleznete v [ `spark-submit` tématu možnosti](https://spark.apache.org/docs/latest/submitting-applications.html) a [spuštění jiskry na podrobnosti YARN](https://spark.apache.org/docs/latest/running-on-yarn.html).

## <a name="frequently-asked-questions"></a>Nejčastější dotazy
### <a name="when-i-run-a-spark-app-with-udfs-i-get-a-filenotfoundexception-error-what-should-i-do"></a>Když spustím aplikaci jiskry s UDFs, dostanu chybu 'FileNotFoundException'. Co bych měl/a dělat?
> **Chyba:** [Error] [TaskRunner] [0] ProcessStream() se nezdařilo s výjimkou: System.IO.FileNotFoundException: Assembly 'mySparkApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null' soubor nebyl nalezen: 'mySparkApp.dll'

**Odpověď:** Zkontrolujte, `DOTNET_ASSEMBLY_SEARCH_PATHS` zda je proměnná prostředí nastavena správně. Měla by to být `mySparkApp.dll`cesta, která obsahuje vaši .

### <a name="after-i-upgraded-my-net-for-apache-spark-version-and-reset-the-dotnet_worker_dir-environment-variable-why-do-i-still-get-the-following-ioexception-error"></a>Po upgradu rozhraní .NET pro verzi `DOTNET_WORKER_DIR` Apache Spark a obnovení proměnné `IOException` prostředí, proč se mi stále zobrazuje následující chyba?
> **Chyba:** Ztracená úloha 0.0 ve fázi 11.0 (TID 24, localhost, ovladač vykonavatele): java.io.IOException: Nelze spustit program "Microsoft.Spark.Worker.exe": CreateProcess error=2, Systém nemůže najít zadaný soubor.

**Odpověď:** Nejprve zkuste restartovat okno Prostředí PowerShell (nebo jiná příkazová okna), aby mohlo trvat nejnovější hodnoty proměnných prostředí. Pak spusťte program.

### <a name="after-submitting-my-spark-application-i-get-the-error-systemtypeloadexception-could-not-load-type-systemruntimeremotingcontextscontext"></a>Po odeslání aplikace Spark se zobrazí `System.TypeLoadException: Could not load type 'System.Runtime.Remoting.Contexts.Context'`chyba .
> **Chyba:** [Error] [TaskRunner] [0] ProcessStream() se nezdařilo s výjimkou: System.TypeLoadException: Nelze načíst typ System.Runtime.Remoting.Contexts.Context' ze sestavení 'mscorlib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=...'.

**Odpověď:** Zkontrolujte `Microsoft.Spark.Worker` verzi, kterou používáte. Existují dvě verze: **.NET Framework 4.6.1** a **.NET Core 2.1.x**. V tomto `Microsoft.Spark.Worker.net461.win-x64-<version>` případě (které si můžete [stáhnout)](https://github.com/dotnet/spark/releases)by měl být použit, protože `System.Runtime.Remoting.Contexts.Context` je pouze pro rozhraní .NET Framework.

### <a name="how-do-i-run-my-spark-application-with-udfs-on-yarn-which-environment-variables-and-parameters-should-i-use"></a>Jak spustím svou jiskřicí aplikaci s UDF s YARN? Jaké proměnné a parametry prostředí mám použít?

**Odpověď:** Chcete-li spustit aplikaci jiskry na YARN, `spark.yarn.appMasterEnv.[EnvironmentVariableName]`proměnné prostředí by měly být určeny jako . Viz níže jako příklad `spark-submit`pomocí :

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

* [Začínáme s rozhraním .NET pro Apache Spark](../tutorials/get-started.md)
* [Ladění rozhraní .NET pro aplikaci Apache Spark v systému Windows](../how-to-guides/debug.md)
