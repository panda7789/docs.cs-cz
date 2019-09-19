---
title: Nasazení rozhraní .NET pro Apache Spark aplikaci do datacihlů
description: Zjistěte, jak nasadit rozhraní .NET pro Apache Spark aplikaci do datacihlů.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: f90d0fa4bdefe94dcf8390698e6445fad77a1bc2
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117939"
---
# <a name="deploy-a-net-for-apache-spark-application-to-databricks"></a>Nasazení rozhraní .NET pro Apache Spark aplikaci do datacihlů

V tomto kurzu se naučíte nasadit rozhraní .NET pro Apache Spark aplikaci do datacihlů.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> - Příprava Microsoft. spark. Worker
> - Publikování aplikace Spark .NET
> - Nasazení aplikace do datacihlů
> - Spuštění aplikace

## <a name="prerequisites"></a>Požadavky

Než začnete, udělejte toto:

- Stáhněte si rozhraní příkazového [řádku datacihly](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).
- Stáhněte si [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) do svého místního počítače. Toto je pomocný skript, který později použijete ke kopírování rozhraní .NET pro Apache Spark závislé soubory do pracovních uzlů clusteru Spark.

## <a name="prepare-worker-dependencies"></a>Příprava závislostí pracovního procesu

**Microsoft. spark. Worker** je back-endové komponenta, která je umístěná na jednotlivých pracovních uzlech clusteru Spark. Pokud chcete spustit systém C# souborů UDF (uživatelsky definovaná funkce), musí Spark pochopit, jak spustit modul CLR .NET pro spouštění systému souborů UDF. **Microsoft. spark. Worker** poskytuje kolekci tříd pro Spark, které tuto funkci povolují.

1. Vyberte verzi [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp, která se má nasadit na váš cluster.

   Pokud například chcete `.NET for Apache Spark v0.1.0` použít `netcoreapp2.1`, Stáhněte si soubor [Microsoft. spark. work. netcoreapp 2.1. Linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).

2. Nahrajte `Microsoft.Spark.Worker.<release>.tar.gz` a [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) do distribuovaného systému souborů (například DBFS), ke kterému má váš cluster přístup.

## <a name="prepare-your-net-for-apache-spark-app"></a>Příprava rozhraní .NET pro aplikaci Apache Spark

1. Při sestavování aplikace postupujte podle kurzu [Začínáme](get-started.md) .

2. Publikujte aplikaci Spark .NET jako samostatnou.

   V systému Linux můžete spustit následující příkaz.

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. Vytvořte `<your app>.zip` pro publikované soubory.

   Následující příkaz můžete spustit na platformě Linux pomocí nástroje `zip`.

   ```bash
   zip -r <your app>.zip .
   ```

4. Nahrajte do distribuovaného systému souborů (například DBFS), ke kterému má cluster přístup, následující:

   - `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Tento JAR je součástí balíčku NuGet [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) a je umístěný ve výstupním adresáři sestavení vaší aplikace.
   - `<your app>.zip`
   - Soubory (jako jsou soubory závislosti nebo společná data dostupná pro každého pracovního procesu) nebo sestavení (například knihovny DLL, které obsahují uživatelem definované funkce nebo knihovny, na kterých je vaše aplikace závislá), aby se umístily do pracovního adresáře každého prováděcího modulu.

## <a name="deploy-to-databricks"></a>Nasazení do Databricks

[Datacihly](https://databricks.com) představují platformu, která poskytuje cloudové zpracování velkých objemů dat pomocí Apache Spark.

> [!Note] 
> [Datacihly](https://databricks.com/aws) [Azure Databricks](https://azure.microsoft.com/services/databricks/) a AWS jsou založené na systému Linux. Proto pokud vás zajímá nasazení vaší aplikace do datacihly, ujistěte se, že je vaše aplikace .NET Standard kompatibilní a že ke kompilaci vaší aplikace použijete [kompilátor .NET Core](https://dotnet.microsoft.com/download) .

Datacihly umožňují odesílat rozhraní .NET pro aplikace Apache Spark do existujícího aktivního clusteru nebo vytvořit nový cluster při každém spuštění úlohy. K tomu je potřeba, aby byl **Microsoft. spark. Worker** nainstalovaný předtím, než odešlete rozhraní .NET pro aplikaci Apache Spark.

### <a name="deploy-microsoftsparkworker"></a>Nasazení Microsoft. spark. Worker

Tento krok se vyžaduje jenom jednou pro cluster.

1. Stáhněte si do [svého](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) místního počítače [DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) a Install-Worker.sh.

2. Upravte **DB-init.sh** tak, aby odkazoval na verzi **Microsoft. spark. Worker** , kterou chcete stáhnout a nainstalovat do clusteru.

3. Nainstalujte rozhraní příkazového [řádku datacihly](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).

4. [Nastavte podrobnosti ověření](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication) pro rozhraní PŘÍKAZového řádku datacihly.

5. Nahrajte soubory do clusteru datacihly pomocí následujícího příkazu:

   ```bash
   cd <path-to-db-init-and-install-worker>
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   ```

6. Přejděte do pracovního prostoru Databricks. V nabídce na levé straně vyberte **clustery** a pak vyberte **vytvořit cluster**.

7. Po správné konfiguraci clusteru nastavte **skript init** a vytvořte cluster.

   ![Obrázek akce skriptu](./media/databricks-deployment/deployment-databricks-init-script.png)

## <a name="run-your-app"></a>Spuštění aplikace 

Můžete použít `set JAR` nebo `spark-submit` k odeslání vaší úlohy do datacihlů.

### <a name="use-set-jar"></a>Použít nastavení JAR

[Nastavení jar](https://docs.databricks.com/user-guide/jobs.html#create-a-job) umožňuje odeslat úlohu do existujícího aktivního clusteru.

#### <a name="one-time-setup"></a>Nastavení jednorázového času

1. Přejděte do svého clusteru datacihly a v nabídce vlevo vyberte **úlohy** . Pak vyberte **nastavit jar**.

2. Nahrajte příslušný `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` soubor.

3. Nastavte parametry odpovídajícím způsobem.

   ```
   Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
   Arguments /dbfs/apps/<your-app-name>.zip <your-app-main-class>
   ```
 
4. Nakonfigurujte **cluster** tak, aby odkazoval na existující **cluster, který** jste vytvořili v předchozí části.

#### <a name="publish-and-run-your-app"></a>Publikování a spuštění vaší aplikace

1. Použijte rozhraní příkazového [řádku datacihly](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) k nahrání vaší aplikace do vašeho clusteru datacihly.

      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
      ```

2. Tento krok je vyžadován pouze v případě, že vaše sestavení vaší aplikace (například knihovny DLL, které obsahují uživatelsky definované funkce společně s jejich závislostmi) je nutné umístit do pracovního adresáře každého z **Microsoft. spark. Worker**.

   - Nahrání sestavení vaší aplikace do clusteru datacihly
      
      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <assembly>.dll dbfs:/apps/dependencies
      ```

   - Odkomentujte a upravte část závislosti aplikací v [DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) tak, aby odkazovala na cestu k závislostem vaší aplikace a nahráli do vašeho clusteru datacihly.
   
      ```bash
      cd <path-to-db-init-and-install-worker>
      databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
      ```
   
   - Restartujte cluster.

3. V pracovním prostoru datacihly přejdete do svého clusteru datacihly. V části **úlohy**vyberte požadovanou úlohu a spusťte úlohu kliknutím na **Spustit nyní** .

### <a name="use-spark-submit"></a>Použití Spark-Submit

Příkaz [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) umožňuje odeslat úlohu do nového clusteru.

1. [Vytvořte úlohu](https://docs.databricks.com/user-guide/jobs.html) a vyberte **Konfigurovat Spark-odeslat**.

2. Nakonfigurujte `spark-submit` pomocí následujících parametrů:

      ```bash
      ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
      ```

3. V pracovním prostoru datacihly přejdete do svého clusteru datacihly. V části **úlohy**vyberte požadovanou úlohu a spusťte úlohu kliknutím na **Spustit nyní** .

## <a name="next-steps"></a>Další postup

V tomto kurzu jste nasadili rozhraní .NET pro Apache Spark aplikaci na datacihly. Pokud se chcete dozvědět víc o datacihlách, přejděte k dokumentaci Azure Databricks.

> [!div class="nextstepaction"]
> [Dokumentace k Azure Databricks](https://docs.microsoft.com/azure/azure-databricks/)
