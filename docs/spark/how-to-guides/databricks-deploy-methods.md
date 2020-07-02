---
title: Odeslání úlohy .NET for Apache Spark do datacihlů
description: Naučte se, jak odeslat úlohu .NET pro Apache Spark do datacihly pomocí Spark – odeslání a nastavení jar.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: bebd170a689d8ae56aa6c55486d70354da2437ea
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617766"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a>Odeslání úlohy .NET for Apache Spark do datacihlů

Můžete spustit rozhraní .NET pro Apache Spark úlohy u clusterů datacihly, ale není dostupné předem. Existují dva způsoby, jak nasadit rozhraní .NET pro Apache Spark úlohy do datacihly: `spark-submit` a nastavit jar.

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="deploy-using-spark-submit"></a>Nasazení pomocí Spark-Submit

K odeslání .NET pro úlohy Apache Spark do datacihly můžete použít příkaz [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) . `spark-submit`povolí odeslání pouze do clusteru, který se vytvoří na vyžádání.

1. Přejděte do pracovního prostoru datacihly a vytvořte úlohu. Zvolte název úlohy a pak vyberte **Konfigurovat Spark-Submit**. Do konfigurace úlohy vložte následující parametry a pak vyberte **Potvrdit**.

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > Aktualizujte obsah výše uvedeného parametru na základě konkrétních souborů a konfigurace. Například odkaz na verzi souboru Microsoft. Spark jar, který jste nahráli do DBFS, a použijte odpovídající název vaší aplikace a publikovaného souboru zip aplikace.

2. Přejděte do úlohy a výběrem **Upravit** Nakonfigurujte cluster vaší úlohy. Nastavte Databricks Runtime verzi na základě verze Apache Spark, kterou chcete ve svém nasazení použít. Pak vyberte **Upřesnit možnosti > inicializační skripty**a jako hodnotu nastavte cestu inicializačního skriptu `dbfs:/spark-dotnet/db-init.sh` . Vyberte **Potvrdit** a potvrďte nastavení clusteru.

3. Přejděte do úlohy a výběrem **Spustit nyní** spusťte úlohu na nově nakonfigurovaném clusteru Spark. Vytvoření clusteru úlohy trvá několik minut. Po vytvoření se vaše úloha odešle. Výstup můžete zobrazit tak, že v levé nabídce pracovního prostoru datacihly vyberete **clustery** a pak vyberete **protokoly ovladačů**.

## <a name="deploy-using-set-jar"></a>Nasazení pomocí Set jar

Alternativně můžete použít [Nastavení jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) v pracovním prostoru datacihly k odeslání .net pro Apache Spark úlohy do datacihlů. *Nastavení jar* povolí odeslání úlohy do existujícího aktivního clusteru.

### <a name="one-time-setup"></a>Nastavení jednorázového času

1. Přejděte do svého clusteru datacihly a v nabídce na levé straně vyberte **úlohy** a potom **nastavte jar**.

2. Nahrajte příslušné `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` .

3. Upravte následující parametry tak, aby obsahovaly správný název spustitelného souboru, který jste publikovali místo `<your-app-name>` :

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. Nakonfigurujte cluster tak, aby odkazoval na existující cluster, pro který jste již nastavili inicializační skript.

### <a name="publish-and-run-your-app"></a>Publikování a spuštění vaší aplikace

1. Ujistěte se, že jste publikovali aplikaci a že váš kód aplikace nepoužívá `SparkSession.Stop()` .

2. K nahrání vaší aplikace do clusteru datacihly použijte rozhraní příkazového [řádku datacihly](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) . Například pomocí následujícího příkazu nahrajte publikovanou aplikaci do svého clusteru:

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. Pokud máte ve své aplikaci nějaké uživatelsky definované funkce, sestavení aplikace, jako jsou knihovny DLL, které obsahují uživatelsky definované funkce společně s jejich závislostmi, musí být umístěné v pracovním adresáři každého z *Microsoft. spark. Worker*.

    Nahrajte sestavení vaší aplikace do vašeho clusteru datacihly:

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    Odkomentujte a upravte část závislosti aplikací v [DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) tak, aby odkazovala na cestu k závislostem vaší aplikace. Pak do svého clusteru nahrajte aktualizované *DB-init.sh* :

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. Chcete-li spustit úlohu, přejděte do **clusteru datacihly > úlohy > [název úlohy] > spustit nyní** .

## <a name="next-steps"></a>Další kroky

* [Začínáme s .NET pro Apache Spark](../tutorials/get-started.md)
* [Nasazení rozhraní .NET pro Apache Spark aplikaci do datacihlů](../tutorials/databricks-deployment.md)
* [Dokumentace k Azure Databricks](https://docs.microsoft.com/azure/azure-databricks/)
