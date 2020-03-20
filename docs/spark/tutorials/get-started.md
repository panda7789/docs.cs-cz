---
title: Začínáme s rozhraním .NET pro Apache Spark
description: Zjistěte, jak spustit aplikaci .NET pro Apache Spark pomocí .NET Core ve Windows, MacOS a Ubuntu.
ms.date: 01/31/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7375c385245a05d7dc29d5df89d875bf6cb4141a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187541"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>Kurz: Začínáme s rozhraním .NET pro Apache Spark

Tento výukový program vás naučí, jak spustit aplikaci .NET pro Apache Spark pomocí .NET Core ve Windows, MacOS a Ubuntu.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> * Příprava prostředí na rozhraní .NET pro Apache Spark
> * Napište svou první aplikaci .NET pro Apache Spark
> * Sestavení a spuštění jednoduché aplikace .NET pro Apache Spark

## <a name="prepare-your-environment"></a>Příprava prostředí

Než začnete psát aplikaci, musíte nastavit některé požadované závislosti. Pokud můžete `dotnet`spustit `java` `mvn`, `spark-shell` , , z prostředí příkazového řádku, pak je vaše prostředí již připraveno a můžete přeskočit na další část. Pokud nelze spustit některý nebo všechny příkazy, proveďte následující kroky.

### <a name="1-install-net"></a>1. Instalace rozhraní .NET

Chcete-li začít vytvářet aplikace .NET, je třeba stáhnout a nainstalovat .NET SDK (Software Development Kit).

Stáhněte a nainstalujte sadu [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1). Instalace sady SDK `dotnet` přidá nástrojovou řetězka do cesty.

Po instalaci sady .NET Core SDK otevřete nový příkazový `dotnet`řádek nebo terminál a spusťte program .

Pokud příkaz spustí a vytiskne informace o tom, jak používat dotnet, můžete přejít k dalšímu kroku. Pokud se `'dotnet' is not recognized as an internal or external command` zobrazí chyba, před spuštěním příkazu zkontrolujte, zda jste otevřeli **nový** příkazový řádek nebo terminál.

### <a name="2-install-java"></a>2. Instalace Javy

Nainstalujte [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) pro Windows a MacOS nebo [OpenJDK 8](https://openjdk.java.net/install/) pro Ubuntu.

Vyberte příslušnou verzi operačního systému. Vyberte například **jdk-8u201-windows-x64.exe** pro počítač se systémem Windows x64 (jak je znázorněno níže) nebo **jdk-8u231-macosx-x64.dmg** pro MacOS. Potom použijte příkaz `java` k ověření instalace.

![Java ke stažení](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a>3. Instalace kompresního softwaru

Apache Spark je stažen jako komprimovaný soubor .tgz. K extrahování souboru použijte extrakční program, například [7-Zip](https://www.7-zip.org/) nebo [WinZip](https://www.winzip.com/).

### <a name="4-install-apache-spark"></a>4. Nainstalujte Apache Spark

[Stáhněte a nainstalujte Apache Spark](https://spark.apache.org/downloads.html). Budete muset vybrat z verze 2.3.* nebo 2.4.0, 2.4.1, 2.4.3 nebo 2.4.4 (.NET pro Apache Spark není kompatibilní s jinými verzemi Apache Spark).

Příkazy použité v následujících krocích předpokládají, že jste [stáhli a nainstalovali Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz). Chcete-li použít jinou verzi, nahraďte **verzi 2.4.1** příslušným číslem verze. Potom extrahujte soubor **.tar** a soubory Apache Spark.

Extrahování vnořeného souboru **TAR:**

* Vyhledejte stažený soubor **spark-2.4.1-bin-hadoop2.7.tgz.**
* Klikněte pravým tlačítkem myši na soubor a vyberte **7-Zip -> Extract zde**.
* **spark-2.4.1-bin-hadoop2.7.tar** je vytvořen vedle souboru **.tgz,** který jste stáhli.

Extrahování souborů Apache Spark:

* Klikněte pravým tlačítkem myši na **jiskru-2.4.1-bin-hadoop2.7.tar** a vyberte **7-Zip -> Extrahovat soubory ...**
* Do pole **Extrahovat do** pole Zadejte **C:\bin.**
* Zaškrtnutí políčka pod polem **Extrahovat do** zaškrtněte.
* Vyberte **OK**.
* Soubory Apache Spark jsou extrahovány do C:\bin\spark-2.4.1-bin-hadoop2.7\

![Instalace Spark](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

Spusťte následující příkazy pro nastavení proměnných prostředí používaných k vyhledání Apache Spark v **systému Windows**:

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

Spusťte následující příkazy pro nastavení proměnných prostředí používaných k vyhledání Apache Spark v **Systému MacOS** a **Ubuntu**:

```bash
export SPARK_HOME=~/bin/spark-2.4.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

Po instalaci všeho a nastavení proměnných prostředí otevřete **nový** příkazový řádek nebo terminál a spusťte následující příkaz:

`%SPARK_HOME%\bin\spark-submit --version`

Pokud příkaz spustí a vytiskne informace o verzi, můžete přejít k dalšímu kroku.

Pokud se `'spark-submit' is not recognized as an internal or external command` zobrazí chyba, zkontrolujte, zda jste otevřeli **nový** příkazový řádek.

### <a name="5-install-net-for-apache-spark"></a>5. Instalace rozhraní .NET pro Apache Spark

Stáhněte si verzi [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) z rozhraní .NET pro Apache Spark GitHub. Pokud jste například na počítači se systémem Windows a plánujete používat rozhraní .NET Core, [stáhněte si verzi netcoreapp3.1 systému Windows x64](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip).

Extrahování microsoft.spark.worker:

* Vyhledejte soubor **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip,** který jste stáhli.
* Klikněte pravým tlačítkem myši a vyberte **7-Zip -> Extrahovat soubory ...**.
* Do pole **Extrahovat do** pole Zadejte **C:\bin.**
* Zaškrtnutí políčka pod polem **Extrahovat do** zaškrtněte.
* Vyberte **OK**.

![Instalace služby .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils-windows-only"></a>6. Instalace WinUtils (pouze windows)

.NET pro Apache Spark vyžaduje, aby se WinUtils instaloval vedle Apache Spark. [Stáhnout winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe). Potom zkopírujte winutils do **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.

> [!NOTE]
> Pokud používáte jinou verzi Hadoopu, která je anotována na konci názvu instalační složky Spark, [vyberte verzi WinUtils,](https://github.com/steveloughran/winutils) která je kompatibilní s vaší verzí Hadoopu.

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a>7. Nastavení DOTNET_WORKER_DIR a kontrola závislostí

Spusťte jeden z následujících `DOTNET_WORKER_DIR` příkazů a nastavte proměnnou prostředí, kterou aplikace .NET používají k vyhledání rozhraní .NET pro Apache Spark.

V **systému Windows**vytvořte [novou proměnnou](https://www.java.com/en/download/help/path.xml) `DOTNET_WORKER_DIR` prostředí a nastavte ji do adresáře, `C:\bin\Microsoft.Spark.Worker\`do kterého jste stáhli a extrahovali microsoft.spark.worker (například ).

V **systému MacOS**vytvořte `export DOTNET_WORKER_DIR <your_path>` novou proměnnou prostředí pomocí a nastavte ji do adresáře, do kterého jste stáhli a extrahovali microsoft.spark.worker (například *~/bin/Microsoft.Spark.Worker/*).

Na **Ubuntu**, vytvořte [novou proměnnou](https://help.ubuntu.com/community/EnvironmentVariables) `DOTNET_WORKER_DIR` prostředí a nastavte ji do adresáře, kde jste stáhli a extrahovali Microsoft.Spark.Worker (například *~/bin/Microsoft.Spark.Worker*).

Nakonec před přechodem do `dotnet`další `java` `mvn`části `spark-shell` zkontrolujte, zda lze spustit příkazový řádek .

## <a name="write-a-net-for-apache-spark-app"></a>Napsat rozhraní .NET pro aplikaci Apache Spark

### <a name="1-create-a-console-app"></a>1. Vytvoření konzolové aplikace

V příkazovém řádku nebo terminálu vytvořte novou konzolovou aplikaci následujícím příkazem:

```dotnetcli
dotnet new console -o mySparkApp
cd mySparkApp
```

Příkaz `dotnet` vytvoří `new` aplikaci `console` typu pro vás. Parametr `-o` vytvoří adresář s názvem *mySparkApp,* kde je vaše aplikace uložena a naplní ji požadovanými soubory. Příkaz `cd mySparkApp` změní adresář na adresář aplikace, který jste právě vytvořili.

### <a name="2-install-nuget-package"></a>2. Nainstalujte balíček NuGet

Chcete-li v aplikaci použít rozhraní .NET pro Apache Spark, nainstalujte balíček Microsoft.Spark. V příkazovém řádku nebo terminálu spusťte následující příkaz:

`dotnet add package Microsoft.Spark --version 0.8.0`

### <a name="3-code-your-app"></a>3. Kód aplikace

Otevřete *Program.cs* v kódu Visual Studia nebo v libovolném textovém editoru a nahraďte celý kód následujícím:

```csharp
using Microsoft.Spark.Sql;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a Spark session.
            SparkSession spark = SparkSession
                .Builder()
                .AppName("word_count_sample")
                .GetOrCreate();

            // Create initial DataFrame.
            DataFrame dataFrame = spark.Read().Text("input.txt");

            // Count words.
            DataFrame words = dataFrame
                .Select(Functions.Split(Functions.Col("value"), " ").Alias("words"))
                .Select(Functions.Explode(Functions.Col("words"))
                .Alias("word"))
                .GroupBy("word")
                .Count()
                .OrderBy(Functions.Col("count").Desc());

            // Show results.
            words.Show();

            // Stop Spark session.
            spark.Stop();
        }
    }
}
```

### <a name="4-create-and-add-a-data-file"></a>4. Vytvoření a přidání datového souboru

Otevřete příkazový řádek nebo terminál a přejděte do složky aplikace.

```bash
cd <your-app-output-directory>
```

Aplikace zpracuje soubor obsahující řádky textu. Vytvořte soubor *input.txt* v adresáři *mySparkApp,* který obsahuje následující text:

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a>Spuštění aplikace .NET pro Apache Spark

1. Chcete-li vytvořit aplikaci, spusťte následující příkaz:

   ```dotnetcli
   dotnet build
   ```

2. Spusťte následující příkaz a odešlete svou žádost ke spuštění na Apache Spark:

   ```console
   spark-submit \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --master local \
   microsoft-spark-2.4.x-<version>.jar \
   dotnet HelloSpark.dll
   ```

   > [!NOTE]
   > Tento příkaz předpokládá, že jste si stáhli Apache Spark a přidali ji do proměnné prostředí PATH, abyste mohli používat `spark-submit`. V opačném případě byste museli použít úplnou cestu (například *C:\bin\apache-spark\bin\spark-submit* nebo *~/spark/bin/spark-submit).*

3. Při spuštění aplikace se do konzoly zapisují data počtu slov souboru *input.txt.*

Blahopřejeme! Úspěšně jste vytvořili a spustili .NET pro aplikaci Apache Spark.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> * Příprava prostředí Windows na rozhraní .NET pro Apache Spark
> * Napište svou první aplikaci .NET pro Apache Spark
> * Sestavení a spuštění jednoduché aplikace .NET pro Apache Spark

Chcete-li zobrazit video vysvětlující výše uvedené kroky, podívejte se na [video sérii .NET pro Apache Spark 101](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).

Další informace najdete na stránce zdrojů.
> [!div class="nextstepaction"]
> [.NET pro prostředky Apache Spark](../resources/index.md)
