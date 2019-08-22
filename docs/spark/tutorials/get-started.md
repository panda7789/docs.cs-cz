---
title: Začínáme s .NET pro Apache Spark
description: Zjistěte, jak spustit rozhraní .NET pro Apache Spark aplikaci pomocí .NET Core ve Windows.
ms.date: 06/27/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7ce7d7aec6c15385d3d797d5a548519eea33b764
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "69577071"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>Kurz: Začínáme s .NET pro Apache Spark

V tomto kurzu se naučíte, jak spustit rozhraní .NET pro Apache Spark aplikaci pomocí .NET Core ve Windows.

V tomto kurzu se naučíte:

> [!div class="checklist"]
> * Příprava prostředí Windows pro rozhraní .NET pro Apache Spark
> * Stáhnout **Microsoft. spark. Worker**
> * Sestavení a spuštění jednoduchého rozhraní .NET pro Apache Spark aplikaci

## <a name="prepare-your-environment"></a>Příprava prostředí

Než začnete, ujistěte se, že je `dotnet`možné `java`spustit `mvn`, `spark-shell` ,, z příkazového řádku. Pokud je vaše prostředí už připravené, můžete přejít k další části. Pokud nemůžete spustit žádný nebo žádný z těchto příkazů, postupujte podle následujících kroků.

1. Stáhněte a nainstalujte [sadu .NET Core 2.1 x SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1). Instalace sady SDK přidá `dotnet` do své cesty sada nástrojů. K ověření instalace použijte `dotnet --version` příkaz prostředí PowerShell.

2. Nainstalujte [Visual studio 2017](https://www.visualstudio.com/downloads/) nebo [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/) s nejnovějšími aktualizacemi. Můžete použít komunita, Professional nebo Enterprise. Verze Community je zdarma.

   Během instalace vyberte následující úlohy:
      * Vývoj desktopových aplikací .NET
          * Všechny požadované součásti
          * Vývojové nástroje .NET Framework 4.6.1
      * Vývoj pro různé platformy .NET core
          * Všechny požadované součásti

3. Nainstalujte [Java 1,8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).

    * Vyberte odpovídající verzi pro váš operační systém. Vyberte například **JDK-8u201-Windows-x64. exe** pro počítač se systémem Windows x64.
    * K ověření instalace použijte `java -version` příkaz prostředí PowerShell.

4. Nainstalujte [Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi).
    * Stáhněte si [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip).
    * Extrahuje do místního adresáře. Například, `c:\bin\apache-maven-3.6.0\`.
    * Přidejte Apache Maven do [proměnné prostředí PATH](https://www.java.com/en/download/help/path.xml). Pokud jste extrahovali do `c:\bin\apache-maven-3.6.0\`, měli byste přidat `c:\bin\apache-maven-3.6.0\bin` do své cesty.
    * K ověření instalace použijte `mvn -version` příkaz prostředí PowerShell.

5. Nainstalujte [Apache Spark 2.3 +](https://spark.apache.org/downloads.html). Apache Spark 2.4 + se nepodporuje.
    * Stáhněte si [Apache Spark 2.3 +](https://spark.apache.org/downloads.html) a extrahujte ji do místní složky pomocí nástroje, jako je [7-zip](https://www.7-zip.org/) nebo [WinZip](https://www.winzip.com/). Můžete ho například extrahovat do `c:\bin\spark-2.3.2-bin-hadoop2.7\`.
    * Přidejte Apache Spark do [proměnné prostředí PATH](https://www.java.com/en/download/help/path.xml). Pokud jste extrahovali do `c:\bin\spark-2.3.2-bin-hadoop2.7\`, měli byste přidat `c:\bin\spark-2.3.2-bin-hadoop2.7\bin` do své cesty.
    * Přidejte [novou proměnnou prostředí](https://www.java.com/en/download/help/path.xml) s názvem `SPARK_HOME`. Pokud jste extrahovali do `C:\bin\spark-2.3.2-bin-hadoop2.7\`, použijte `C:\bin\spark-2.3.2-bin-hadoop2.7\` pro **hodnotu proměnné**.
    * Ověřte, že je možné spustit `spark-shell` z příkazového řádku.

6. Nastavte [WinUtils](https://github.com/steveloughran/winutils).
    * Stáhněte si binární soubor **winutils. exe** z [úložiště winutils](https://github.com/steveloughran/winutils). Vyberte verzi Hadoop, se kterou byla distribuce Sparku zkompilována. Například můžete použít **Hadoop-2.7.1** pro **Spark 2.3.2**. Na konci názvu instalační složky Sparku se používá Poznámka k verzi systému Hadoop.
    * Uložte binární soubor **winutils. exe** do adresáře podle vašeho výběru. Například, `c:\hadoop\bin`.
    * Nastavte `HADOOP_HOME` tak, aby odrážel adresář s **winutils. exe** bez `bin`. Například, `c:\hadoop`.
    * Nastavte proměnnou prostředí PATH, která se `%HADOOP_HOME%\bin`má zahrnout.

Před přechodem na další oddíl `dotnet`dvakrát ověřte `mvn`, `spark-shell` že z příkazového řádku můžete spustit, `java`,,.

## <a name="download-the-microsoftsparkworker-release"></a>Stažení verze Microsoft. spark. Worker

1. Stáhněte si verzi [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases) ze stránky rozhraní .net pro Apache Spark verze GitHubu do svého místního počítače. Můžete ho třeba stáhnout do cesty, `c:\bin\Microsoft.Spark.Worker\`.

2. Vytvořte [novou proměnnou prostředí](https://www.java.com/en/download/help/path.xml) nazvanou `DotnetWorkerPath` a nastavte ji do adresáře, do kterého jste stáhli a extrahovali **Microsoft. spark. Worker**. Například, `c:\bin\Microsoft.Spark.Worker`.

## <a name="clone-the-net-for-apache-spark-github-repo"></a>Klonovat rozhraní .NET pro Apache Spark úložiště GitHub

K naklonování rozhraní .NET pro Apache Spark úložiště do počítače použijte následující příkaz [GitBash](https://gitforwindows.org/) .

```bash
git clone https://github.com/dotnet/spark.git c:\github\dotnet-spark
```

## <a name="write-a-net-for-apache-spark-app"></a>Zápis rozhraní .NET pro aplikaci Apache Spark

1. Otevřete **Visual Studio** a přejděte na **soubor > vytvořit nový projekt > Konzolová aplikace (.NET Core)** . Pojmenujte aplikaci **HelloSpark**.

2. Nainstalujte [balíček NuGet Microsoft. Spark](https://www.nuget.org/profiles/spark). Další informace o instalaci balíčků NuGet najdete v tématu [různé způsoby instalace balíčku NuGet](https://docs.microsoft.com/nuget/consume-packages/ways-to-install-a-package).

3. V **Průzkumník řešení**otevřete **program.cs** a napište následující C# kód:

   ```csharp
     var spark = SparkSession.Builder().GetOrCreate();
     var df = spark.Read().Json("people.json");
     df.Show();
   ```

4. Sestavte řešení.

## <a name="run-your-net-for-apache-spark-app"></a>Spuštění aplikace .NET pro Apache Spark

1. Otevřete **PowerShell** a změňte adresář na složku, ve které je uložená vaše aplikace.

   ```powershell
   cd <your-app-output-directory>
   ```

2. Vytvořte soubor s názvem **lidi. JSON** s následujícím obsahem:

   ```json
   {"name":"Michael"}
   {"name":"Andy", "age":30}
   {"name":"Justin", "age":19}
   ```

3. Ke spuštění aplikace použijte následující příkaz prostředí PowerShell:

   ```powershell
    spark-submit `
    --class org.apache.spark.deploy.dotnet.DotnetRunner `
    --master local `
    microsoft-spark-2.4.x-<version>.jar `
    dotnet HelloSpark.dll
    ```

Blahopřejeme! Úspěšně jste vytvořili a spustili rozhraní .NET pro Apache Spark aplikaci.

## <a name="next-steps"></a>Další postup

V tomto kurzu jste se naučili:
> [!div class="checklist"]
> * Příprava prostředí Windows pro rozhraní .NET pro Apache Spark
> * Stáhnout **Microsoft. spark. Worker**
> * Sestavení a spuštění jednoduchého rozhraní .NET pro Apache Spark aplikaci

Další informace najdete na stránce prostředky.
> [!div class="nextstepaction"]
> [.NET pro prostředky Apache Spark](../resources/index.md)
