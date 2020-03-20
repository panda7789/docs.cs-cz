---
title: Odeslat úlohu .NET pro Apache Spark do Databricks
description: Naučte se, jak odeslat úlohu .NET pro Apache Spark do Databricks pomocí spark-submit a Set Jar.
ms.date: 12/05/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 65976f9095ecef66e0538c398492033c612c1430
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187613"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a>Odeslat úlohu .NET pro Apache Spark do Databricks

Existují dva způsoby nasazení úlohy .NET pro Apache `spark-submit` Spark do Databricks: a Set Jar.

## <a name="deploy-using-spark-submit"></a>Nasazení pomocí spark-submit

Příkaz [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) můžete použít k odeslání úloh .NET pro Apache Spark do Databricks. `spark-submit`umožňuje odesílání pouze do clusteru, který získá vytvořené na vyžádání.

1. Přejděte do pracovního prostoru Databricks a vytvořte úlohu. Vyberte název úlohy a pak vyberte **Konfigurovat spark-submit**. Vložte do konfigurace úlohy následující parametry a vyberte **potvrdit**.

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > Aktualizujte obsah výše uvedeného parametru na základě vašich konkrétních souborů a konfigurace. Například odkazovat na verzi microsoft.spark jar soubor, který jste nahráli do DBFS a použijte příslušný název aplikace a publikované aplikace zip soubor.

2. Přejděte do úlohy a vyberte **Upravit** a nakonfigurujte cluster své úlohy. Nastavte datovou verzi runtime na základě verze Apache Spark, kterou chcete použít ve svém nasazení. Pak vyberte **Upřesnit možnosti > init skripty**a nastavte Init Script Path as `dbfs:/spark-dotnet/db-init.sh`. Chcete-li potvrdit nastavení clusteru, vyberte potvrdit možnost **Potvrdit.**

3. Přejděte ke své úloze a vyberte **Spustit nyní,** chcete-li spustit úlohu v nově nakonfigurovaném clusteru Spark. Vytvoření clusteru úlohy trvá několik minut. Jakmile je vytvořen, vaše práce bude odeslána. Výstup můžete zobrazit výběrem **clusterů** z levé nabídky pracovního prostoru Databricks a vyberte **položku Protokoly ovladačů**.

## <a name="deploy-using-set-jar"></a>Nasazení pomocí sady jar

Případně můžete použít [Set Jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) v pracovním prostoru Databricks k odeslání .NET pro úlohy Apache Spark databricks. *Set Jar* umožňuje odeslání úlohy do existujícího aktivního clusteru.

### <a name="one-time-setup"></a>Jednorázové nastavení

1. Přejděte do clusteru Databricks a v yberte **Úlohy** z nabídky na levé straně, následované **sadou JAR**.

2. Nahrajte `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`příslušnou .

3. Upravte následující parametry tak, aby obsahovaly správný název spustitelného souboru, který jste publikovali místo `<your-app-name>`:

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. Nakonfigurujte cluster tak, aby ukazoval na existující cluster, pro který jste již nastavili skript init.

### <a name="publish-and-run-your-app"></a>Publikování a spuštění aplikace

1. Ujistěte se, že jste aplikaci publikovali `SparkSession.Stop()`a že kód aplikace nepoužívá .

2. Pomocí zapisování se k odeslání aplikace do clusteru Databricks použijte [zapisovatelská](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) nastavení datových cli datových zoadů. K nahrání publikované aplikace do clusteru například nahrajte následující příkaz:

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. Pokud máte ve vaší aplikaci nějaké uživatelem definované funkce, je třeba do pracovního adresáře každého *Microsoft.Spark.Worker*umístit sestavení aplikací, například knihovny DLL, které obsahují uživatelem definované funkce spolu s jejich závislostmi.

    Nahrajte sestavení aplikací do clusteru Databricks:

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    Odkomentujte a upravte oddíl závislostí aplikací v [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) tak, aby ukazoval na cestu závislosti aplikace. Potom nahrajte aktualizovanou *db-init.sh* do clusteru:

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. Přejděte do **clusteru Databricks > úlohy > [Job-name] > Spustit nyní** spustit úlohu.

## <a name="next-steps"></a>Další kroky

* [Začínáme s rozhraním .NET pro Apache Spark](../tutorials/get-started.md)
* [Nasazení rozhraní .NET pro aplikaci Apache Spark do databricks](../tutorials/databricks-deployment.md)
* [Dokumentace k Azure Databricks](https://docs.microsoft.com/azure/azure-databricks/)
