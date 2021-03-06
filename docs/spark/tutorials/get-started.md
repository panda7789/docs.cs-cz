---
title: Začínáme s .NET pro Apache Spark
description: Zjistěte, jak spustit rozhraní .NET pro Apache Spark aplikaci pomocí .NET Core ve Windows, macOS a Ubuntu.
ms.date: 06/25/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: d7297b11a2b5b21420fcb2f0f9ae823cb29b88d1
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89358996"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>Kurz: Začínáme s .NET pro Apache Spark

V tomto kurzu se naučíte, jak spustit rozhraní .NET pro Apache Spark aplikaci pomocí .NET Core ve Windows, macOS a Ubuntu.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> * Příprava prostředí pro .NET pro Apache Spark
> * Zápis prvního rozhraní .NET pro Apache Spark aplikaci
> * Sestavování a spouštění jednoduchého rozhraní .NET pro Apache Spark aplikaci

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prepare-your-environment"></a>Příprava prostředí

Než začnete psát aplikaci, musíte nastavit některé závislosti požadavků. Pokud `dotnet` `java` `mvn` `spark-shell` v prostředí příkazového řádku můžete spustit,,, je vaše prostředí už připravené a můžete přejít k další části. Pokud nemůžete spustit žádný z příkazů nebo všechny, proveďte následující kroky.

### <a name="1-install-net"></a>1. instalace .NET

Chcete-li začít sestavovat aplikace .NET, je nutné stáhnout a nainstalovat sadu .NET SDK (Software Development Kit).

Stáhněte a nainstalujte [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1). Instalace sady SDK přidá do `dotnet` své cesty sada nástrojů.

Po instalaci .NET Core SDK otevřete nový příkazový řádek nebo terminál a spusťte příkaz `dotnet` .

Pokud se příkaz spustí a vytiskne informace o použití dotnet, může přejít k dalšímu kroku. Pokud se zobrazí `'dotnet' is not recognized as an internal or external command` Chyba, před spuštěním příkazu se ujistěte, že jste otevřeli **Nový** příkazový řádek nebo terminál.

### <a name="2-install-java"></a>2. instalace Java

Nainstalujte [Java 8,1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) pro Windows a MacOS nebo [OpenJDK 8](https://openjdk.java.net/install/) pro Ubuntu.

Vyberte odpovídající verzi pro váš operační systém. Vyberte například **jdk-8u201-windows-x64.exe** pro počítač se systémem Windows x64 (jak je vidět níže) nebo **JDK-8u231-MacOSX-x64. dmg** pro MacOS. Pak pomocí příkazu `java` Ověřte instalaci.

![Stažení Java](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a>3. instalace kompresního softwaru

Apache Spark se stáhl jako komprimovaný soubor. tgz. K extrakci souboru použijte program pro extrakci, například [7-zip](https://www.7-zip.org/) nebo [WinZip](https://www.winzip.com/).

### <a name="4-install-apache-spark"></a>4. instalace Apache Spark

[Stáhněte a nainstalujte Apache Spark](https://spark.apache.org/downloads.html). Bude nutné vybrat z verze 2,3. * nebo 2.4.0, 2.4.1, 2.4.3 nebo 2.4.4 (rozhraní .NET pro Apache Spark není kompatibilní s jinými verzemi Apache Spark).

Příkazy použité v následujících krocích předpokládají, že jste [stáhli a nainstalovali Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz). Pokud chcete použít jinou verzi, nahraďte hodnotu **2.4.1** příslušným číslem verze. Pak extrahujte soubor **. tar** a Apache Spark soubory.

Extrahování vnořeného souboru **. tar** :

* Vyhledejte soubor **Spark-2.4.1-bin-Hadoop 2.7. tgz** , který jste si stáhli.
* Klikněte pravým tlačítkem na soubor a vyberte **7-zip-> extrakci**.
* **Spark-2.4.1-bin-Hadoop 2.7. tar** se vytvoří společně s souborem **. tgz** , který jste stáhli.

Extrahování Apache Spark souborů:

* Klikněte pravým tlačítkem na **Spark-2.4.1-bin-Hadoop 2.7. tar** a vyberte **7-zip-> extrahování souborů...**
* Do pole **extrahovat do** zadejte **C:\Bin** .
* Zrušte zaškrtnutí políčka pod polem **extrahovat do** .
* Vyberte **OK**.
* Soubory Apache Spark jsou extrahovány do C:\bin\spark-2.4.1-bin-hadoop2.7\

![Instalace Sparku](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

Spuštěním následujících příkazů nastavte proměnné prostředí používané k vyhledání Apache Spark ve **Windows**:

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

Spuštěním následujících příkazů nastavte proměnné prostředí používané k vyhledání Apache Spark v **MacOS** a **Ubuntu**:

```bash
export SPARK_HOME=~/bin/spark-2.4.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

Jakmile nainstalujete vše a nastavíte proměnné prostředí, otevřete **Nový** příkazový řádek nebo terminál a spusťte následující příkaz:

`%SPARK_HOME%\bin\spark-submit --version`

Pokud se příkaz spustí a zobrazí informace o verzi, můžete přejít k dalšímu kroku.

Pokud se zobrazí `'spark-submit' is not recognized as an internal or external command` Chyba, ujistěte se, že jste otevřeli **Nový** příkazový řádek.

### <a name="5-install-net-for-apache-spark"></a>5. Nainstalujte rozhraní .NET pro Apache Spark

Stáhněte si verzi [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases) z rozhraní .net pro Apache Spark GitHub. Pokud jste například na počítači s Windows a plánujete použít .NET Core, [Stáhněte si verzi Windows x64 netcoreapp 3.1](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip).

Extrakce Microsoft. spark. Worker:

* Vyhledejte soubor **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** , který jste stáhli.
* Klikněte pravým tlačítkem a vyberte **7-zip-> extrahování souborů...**.
* Do pole **extrahovat do** zadejte **C:\Bin** .
* Zrušte zaškrtnutí políčka pod polem **extrahovat do** .
* Vyberte **OK**.

![Instalace .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils-windows-only"></a>6. instalace WinUtils (jenom Windows)

Rozhraní .NET pro Apache Spark vyžaduje, aby se WinUtils nainstalovaly společně s Apache Spark. [Stáhněte si winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe). Pak zkopírujte WinUtils do **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.

> [!NOTE]
> Pokud používáte jinou verzi systému Hadoop, která je Poznáma na konci názvu instalační složky Sparku, [Vyberte verzi WinUtils](https://github.com/steveloughran/winutils) , která je kompatibilní s vaší verzí Hadoop.

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a>7. Nastavte DOTNET_WORKER_DIR a ověřte závislosti.

Spusťte jeden z následujících příkazů, abyste nastavili `DOTNET_WORKER_DIR` proměnnou prostředí, kterou aplikace .NET používá k vyhledání rozhraní .NET pro Apache Spark.

V **systému Windows**vytvořte [novou proměnnou prostředí](https://www.java.com/en/download/help/path.xml) `DOTNET_WORKER_DIR` a nastavte ji do adresáře, do kterého jste stáhli a extrahovali Microsoft. spark. Worker (například `C:\bin\Microsoft.Spark.Worker\` ).

V **MacOS**vytvořte novou proměnnou prostředí pomocí `export DOTNET_WORKER_DIR <your_path>` a nastavte ji do adresáře, do kterého jste stáhli a extrahovali Microsoft. spark. Worker (například *~/bin/Microsoft.spark.Worker/*).

V **Ubuntu**vytvořte [novou proměnnou prostředí](https://help.ubuntu.com/community/EnvironmentVariables) `DOTNET_WORKER_DIR` a nastavte ji do adresáře, do kterého jste stáhli a extrahovali Microsoft. spark. Worker (například *~/bin/Microsoft.spark.Worker*).

Nakonec dvakrát kontrolujte, že `dotnet` `java` `mvn` `spark-shell` před přechodem na další část můžete z příkazového řádku spustit,,.

## <a name="write-a-net-for-apache-spark-app"></a>Zápis rozhraní .NET pro aplikaci Apache Spark

### <a name="1-create-a-console-app"></a>1. vytvoření konzolové aplikace

V příkazovém řádku nebo terminálu spusťte následující příkazy k vytvoření nové konzolové aplikace:

```dotnetcli
dotnet new console -o mySparkApp
cd mySparkApp
```

`dotnet`Příkaz vytvoří `new` aplikaci typu `console` pro vás. `-o`Parametr vytvoří adresář s názvem *mySparkApp* , kde je vaše aplikace uložená, a naplní ji požadovanými soubory. `cd mySparkApp`Příkaz změní adresář na adresář aplikace, který jste právě vytvořili.

### <a name="2-install-nuget-package"></a>2. instalace balíčku NuGet

Pokud chcete použít .NET pro Apache Spark v aplikaci, nainstalujte balíček Microsoft. spark. V příkazovém řádku nebo terminálu spusťte následující příkaz:

`dotnet add package Microsoft.Spark --version 0.8.0`

### <a name="3-code-your-app"></a>3. kódování aplikace

Otevřete *program.cs* v Visual Studio Code nebo libovolný textový editor a nahraďte celý kód následujícím kódem:

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

### <a name="4-create-and-add-a-data-file"></a>4. vytvoření a přidání datového souboru

Otevřete příkazový řádek nebo terminál a přejděte do složky aplikace.

```bash
cd <your-app-output-directory>
```

Vaše aplikace zpracovává soubor obsahující řádky textu. Vytvořte soubor *input.txt* v adresáři *mySparkApp* , který obsahuje následující text:

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a>Spuštění aplikace .NET pro Apache Spark

1. Spuštěním následujícího příkazu sestavte aplikaci:

   ```dotnetcli
   dotnet build
   ```

2. Spuštěním následujícího příkazu odešlete aplikaci, která se má spustit na Apache Spark:

   ```console
   spark-submit \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --master local \
   microsoft-spark-2.4.x-<version>.jar \
   dotnet HelloSpark.dll
   ```

   > [!NOTE]
   > Tento příkaz předpokládá, že jste stáhli Apache Spark a přidali ho do proměnné prostředí PATH, aby bylo možné ho použít `spark-submit` . V opačném případě byste měli použít úplnou cestu (například *C:\bin\apache-spark\bin\spark-Submit* nebo *~/Spark/bin/Spark-Submit*).

3. Po spuštění vaší aplikace se do konzoly zapíše data počtu slov *input.txt* souboru.

Blahopřejeme! Úspěšně jste vytvořili a spustili rozhraní .NET pro Apache Spark aplikaci.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> * Příprava prostředí Windows pro rozhraní .NET pro Apache Spark
> * Zápis prvního rozhraní .NET pro Apache Spark aplikaci
> * Sestavování a spouštění jednoduchého rozhraní .NET pro Apache Spark aplikaci

Pokud se chcete podívat na video s vysvětlením výše uvedených kroků, Zarezervujte si [řadu videí .NET pro Apache Spark 101](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).

Další informace najdete na stránce prostředky.
> [!div class="nextstepaction"]
> [.NET pro prostředky Apache Spark](../resources/index.md)
