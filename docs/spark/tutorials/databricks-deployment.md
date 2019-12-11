---
title: Nasazení rozhraní .NET pro Apache Spark aplikaci do datacihlů
description: Zjistěte, jak nasadit rozhraní .NET pro Apache Spark aplikaci do datacihlů.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: dfd33e83c04428b7a6a72e4992c40f00982b1958
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960459"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a>Kurz: nasazení rozhraní .NET pro Apache Spark aplikaci do datacihlů

V tomto kurzu se naučíte, jak nasadit vaši aplikaci do cloudu prostřednictvím Azure Databricks, analytických platforem založených na Apache Spark s nastavením jedním kliknutím, zjednodušenými pracovními postupy a interaktivním pracovním prostorem, který umožňuje spolupráci.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> - Vytvořte pracovní prostor Azure Databricks.
> - Publikování aplikace .NET pro Apache Spark.
> - Vytvoření úlohy Spark a clusteru Spark
> - Spusťte aplikaci v clusteru Spark.

## <a name="prerequisites"></a>Požadavky

Než začnete, proveďte následující úlohy:

* Pokud nemáte účet Azure, vytvořte si [bezplatný účet](https://azure.microsoft.com/free/).
* Přihlaste se k [webu Azure portal](https://portal.azure.com/).
* Dokončete kurz [k rozhraní .NET pro Apache Spark – Začínáme během 10 minut](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) .

## <a name="create-an-azure-databricks-workspace"></a>Vytvoření pracovního prostoru Azure Databricks

> [!Note]
> Tento kurz se nedá provést pomocí **předplatného Azure free zkušební verze**.
> Pokud máte bezplatný účet, přejděte na svůj profil a změňte si předplatné na **průběžné platby**. Další informace najdete na stránce [bezplatného účtu Azure](https://azure.microsoft.com/free/). Pak [odeberte limit útraty](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit)a [požádejte o zvýšení kvóty](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) pro vCPU ve vaší oblasti. Když vytváříte pracovní prostor Azure Databricks, můžete vybrat cenovou úroveň **DBU (Premium-14-days)** a poskytnout tak přístup k pracovnímu prostoru zdarma Premium Azure Databricks DBU po dobu 14 dnů.

V této části vytvoříte pomocí portálu Azure pracovní prostor služby Azure Databricks.

1. Na webu Azure Portal vyberte **Vytvořit prostředek** > **Analýza** > **Azure Databricks**.

   ![Vytvoření prostředku Azure Databricks v Azure Portal](./media/databricks-deployment/create-databricks-resource.png)

2. V části **Služba Azure Databricks** zadejte hodnoty pro vytvoření pracovního prostoru Databricks.

    |Vlastnost  |Popis  |
    |---------|---------|
    |**Název pracovního prostoru**     | Zadejte název pracovního prostoru Databricks.        |
    |**Předplatné**     | Z rozevíracího seznamu vyberte své předplatné Azure.        |
    |**Skupina prostředků**     | Určete, jestli chcete vytvořit novou skupinu prostředků, nebo použít existující. Skupina prostředků je kontejner, který uchovává související prostředky pro řešení Azure. Další informace naleznete v tématu [Přehled skupin prostředků v Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview). |
    |**Poloha**     | Vyberte preferovanou oblast. Informace o dostupných oblastech najdete v tématu [služby Azure dostupné v jednotlivých oblastech](https://azure.microsoft.com/regions/services/).        |
    |**Cenová úroveň**     |  Vyberte si mezi **standardem**, **Premium**nebo **zkušební verzí**. Další informace o těchto úrovních najdete na [stránce s cenami za Databricks](https://azure.microsoft.com/pricing/details/databricks/).       |
    |**Virtual Network**     |   Ne       |

3. Vyberte **vytvořit**. Vytvoření pracovního prostoru trvá několik minut. Při vytváření pracovního prostoru můžete zobrazit stav nasazení v části **oznámení**.

## <a name="install-azure-databricks-tools"></a>Nainstalovat Azure Databricks nástroje

Pomocí rozhraní příkazového **řádku datacihly** se můžete připojit k Azure Databricks clusterům a odesílat do nich soubory z místního počítače. Clustery datacihly přistupují k souborům prostřednictvím DBFS (systém souborů datacihly).

1. Rozhraní příkazového řádku datacihly vyžaduje Python 3,6 nebo vyšší. Pokud už máte nainstalovaný Python, můžete tento krok přeskočit.

   **Pro Windows:**

   [Stažení Pythonu pro Windows](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   **Pro Linux:** Python přichází do předinstalovaných distribucí pro Linux. Spuštěním následujícího příkazu zobrazíte verzi, kterou jste nainstalovali:

   ```bash
   python3 --version
   ```

2. Pomocí PIP nainstalujte rozhraní příkazového řádku datacihly. Python 3,4 a novější standardně zahrnují PIP. Použijte PIP3 pro Python 3. Spusťte následující příkaz:

   ```bash
   pip3 install databricks-cli
   ```

3. Po instalaci CLI datacihly otevřete nový příkazový řádek a spusťte příkaz `databricks`. Pokud **se zobrazí "datacihly" nejsou rozpoznány jako vnitřní nebo externí Chyba příkazu**, otevřete nový příkazový řádek.

## <a name="set-up-azure-databricks"></a>Nastavit Azure Databricks

Teď, když máte nainstalované rozhraní příkazového řádku datacihly, je potřeba nastavit podrobnosti ověřování.

1. Spusťte příkaz rozhraní příkazového řádku datacihly `databricks configure --token`.

2. Po spuštění příkazu konfigurace se zobrazí výzva k zadání hostitele. Adresa URL hostitele používá formát: **https://< \Location >. NET**. Pokud jste například během vytváření Azure Databricks služby vybrali možnost **eastus2** , bude hostitel **https://eastus2.azuredatabricks.net** .

3. Po zadání hostitele se zobrazí výzva k zadání tokenu. V Azure Portal vyberte **Spustit pracovní prostor** a spusťte Azure Databricks pracovní prostor.

   ![Spustit Azure Databricks pracovní prostor](./media/databricks-deployment/launch-databricks-workspace.png)

4. Na domovské stránce pracovního prostoru vyberte **nastavení uživatele**.

   ![Nastavení uživatele v pracovním prostoru Azure Databricks](./media/databricks-deployment/databricks-user-settings.png)

5. Na stránce nastavení uživatele můžete vygenerovat nový token. Zkopírujte vygenerovaný token a vložte ho zpátky do příkazového řádku.

   ![Vygenerování nového přístupového tokenu v pracovním prostoru Azure Databricks](./media/databricks-deployment/generate-token.png)

Nyní byste měli mít přístup k jakýmkoli Azure Databricks clusterům, které vytvoříte a nahrajete soubory do DBFS.

## <a name="download-worker-dependencies"></a>Stáhnout závislosti pracovního procesu

1. Microsoft. spark. Worker pomáhá Apache Spark spustit vaši aplikaci, jako jsou například všechny uživatelsky definované funkce (UDF), které jste mohli napsat. Stáhněte si [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).

2. *Install-Worker.sh* je skript, který umožňuje zkopírovat rozhraní .net pro Apache Spark závislé soubory do uzlů clusteru.

   V místním počítači vytvořte nový soubor s názvem **install-Worker.sh** a vložte [obsah Install-Worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) umístěný na GitHubu.

3. *DB-init.sh* je skript, který nainstaluje závislosti do vašeho clusteru datacihly Spark.

   V místním počítači vytvořte nový soubor s názvem **DB-init.sh** a vložte [obsah DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) umístěný na GitHubu.

   V souboru, který jste právě vytvořili, nastavte proměnnou `DOTNET_SPARK_RELEASE` na `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`. Zbývající část souboru *DB-init.sh* ponechte beze změny.

> [!Note]
> Pokud používáte systém Windows, ověřte, že zakončení řádků ve skriptech *install-Worker.sh* a *DB-init.sh* mají formát UNIX (LF). Konce řádků můžete změnit pomocí textových editorů, jako je Poznámkový blok + + a Atom.

## <a name="publish-your-app"></a>Publikování aplikace

V dalším kroku publikujete *mySparkApp* vytvořenou v [rozhraní .NET pro Apache Spark – Začínáme s 10 minutami](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) , abyste zajistili, že cluster Spark bude mít přístup ke všem souborům, které potřebuje ke spuštění vaší aplikace.

1. Pro publikování *mySparkApp*spusťte následující příkazy:

   **Ve Windows:**

   ```console
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   **V systému Linux:**

   ```bash
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. Proveďte následující úlohy pro zip publikovaných souborů aplikace, abyste je mohli snadno nahrát do vašeho clusteru datacihly Spark.

   **Ve Windows:**

   Přejděte na mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64. Potom klikněte pravým tlačítkem na složku pro **publikování** a vyberte **Odeslat do > Komprimovaná složka (ZIP)** . Pojmenujte novou složku **Publish. zip**.

   **V systému Linux spusťte následující příkaz:**

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a>Nahrání souborů

V této části nahrajete několik souborů do DBFS, aby měl váš cluster vše, co potřebuje ke spuštění vaší aplikace v cloudu. Pokaždé, když nahrajete soubor do DBFS, ujistěte se, že jste v adresáři, ve kterém je tento soubor umístěný ve vašem počítači.

1. Spusťte následující příkazy, abyste nahráli *DB-init.sh*, *install-Worker.sh*a *Microsoft. spark. Worker* do DBFS:

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz dbfs:/spark-dotnet/   Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz
   ```

2. Spuštěním následujících příkazů nahrajte zbývající soubory, které cluster bude potřebovat ke spuštění vaší aplikace: složku pro stažení zip, *input. txt*a *Microsoft-Spark-2.4. x-0.3.0. jar*.

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.0\ubuntu.16.04-x64 directory
   databricks fs cp mySparkApp.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2.4.x-0.6.0.jar dbfs:/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar
   ```

## <a name="create-a-job"></a>Vytvoření úlohy

Vaše aplikace se spouští na Azure Databricks prostřednictvím úlohy, která spouští **Spark-Submit**, což je příkaz, který použijete ke spuštění .NET pro úlohy Apache Spark.

1. V pracovním prostoru Azure Databricks vyberte ikonu **úlohy** a potom **+ vytvořit úlohu**.

   ![Vytvoření úlohy Azure Databricks](./media/databricks-deployment/create-job.png)

2. Zvolte název úlohy a pak vyberte **Konfigurovat Spark-Submit**.

   ![Konfigurace úlohy Spark-submit pro datacihly](./media/databricks-deployment/configure-spark-submit.png)

3. Do konfigurace úlohy vložte následující parametry. Pak vyberte **Potvrdit**.

   ```
   ["--class","org.apache.spark.deploy.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a>Vytvoření clusteru

1. Přejděte do úlohy a výběrem **Upravit** Nakonfigurujte cluster vaší úlohy.

2. Nastavte cluster na **Spark 2.4.1**. Pak vyberte **Upřesnit možnosti** > **skripty init**. Nastavte cestu ke skriptu init jako `dbfs:/spark-dotnet/db-init.sh`.

   ![Konfigurace clusteru Spark v Azure Databricks](./media/databricks-deployment/cluster-config.png)

3. Vyberte **Potvrdit** a potvrďte nastavení clusteru.

## <a name="run-your-app"></a>Spuštění aplikace

1. Přejděte do úlohy a výběrem **Spustit nyní** spusťte úlohu na nově nakonfigurovaném clusteru Spark.

2. Vytvoření clusteru úlohy trvá několik minut. Po vytvoření bude vaše úloha odeslána a můžete zobrazit výstup.

3. V nabídce vlevo vyberte **clustery** a potom název a spuštění úlohy.

4. Vyberte **protokoly ovladačů** a zobrazte výstup vaší úlohy. Až se vaše aplikace dokončí, zobrazí se stejná tabulka počtu slov z místního spouštěného příkazu Začínáme do standardní výstupní konzoly.

   ![Výstupní tabulka úlohy Azure Databricks](./media/databricks-deployment/table-output.png)

   Gratulujeme, spustili jste první rozhraní .NET pro Apache Spark aplikaci v cloudu!

## <a name="clean-up-resources"></a>Vyčištění prostředků

Pokud už nepotřebujete pracovní prostor datacihly, můžete prostředek Azure Databricks odstranit v Azure Portal. Můžete také výběrem názvu skupiny prostředků otevřít stránku skupiny prostředků a pak vybrat **Odstranit skupinu prostředků**.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste nasadili rozhraní .NET pro Apache Spark aplikaci na datacihly. Pokud se chcete dozvědět víc o datacihlách, přejděte k dokumentaci Azure Databricks.

> [!div class="nextstepaction"]
> [Dokumentace k Azure Databricks](https://docs.microsoft.com/azure/azure-databricks/)
