---
title: Nasazení rozhraní .NET pro aplikaci Apache Spark do databricks
description: Zjistěte, jak nasadit .NET pro aplikaci Apache Spark do Databricks.
ms.date: 01/23/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c5308530831fa288bf637849c1342f51769c3ad4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77503958"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a>Kurz: Nasazení rozhraní .NET pro aplikaci Apache Spark do databricks

Tento kurz vás naučí, jak nasadit aplikaci do cloudu prostřednictvím Azure Databricks, analytické platformy založené na Apache Spark s nastavením jedním kliknutím, zjednodušenými pracovními postupy a interaktivním pracovním prostorem, který umožňuje spolupráci.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> - Vytvořte pracovní prostor Azure Databricks.
> - Publikujte svou aplikaci .NET pro Apache Spark.
> - Vytvořte úlohu Spark a cluster Spark.
> - Spusťte aplikaci v clusteru Spark.

## <a name="prerequisites"></a>Požadavky

Než začnete, proveďte následující úkoly:

* Pokud nemáte účet Azure, vytvořte si [bezplatný účet](https://azure.microsoft.com/free/).
* Přihlaste se k [portálu Azure](https://portal.azure.com/).
* Dokončete [rozhraní .NET pro Apache Spark – začínáme v kurzu 10 minut.](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)

## <a name="create-an-azure-databricks-workspace"></a>Vytvoření pracovního prostoru Azure Databricks

> [!Note]
> Tento kurz nelze provést pomocí **bezplatného zkušebního předplatného Azure**.
> Pokud máte bezplatný účet, přejděte na svůj profil a změňte předplatné na **průběžně placené**. Další informace najdete na stránce [bezplatného účtu Azure](https://azure.microsoft.com/free/). Potom [odeberte limit útraty](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit)a [požádejte o zvýšení kvóty](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) pro virtuální procesory ve vaší oblasti. Když vytvoříte pracovní prostor Azure Databricks, můžete vybrat **zkušební (premium - 14denní jednotku DBU)** a poskytnout tak pracovnímu prostoru přístup k bezplatným dbům Azure Databricks Azure na 14 dní.

V této části vytvoříte pomocí portálu Azure pracovní prostor služby Azure Databricks.

1. Na webu Azure Portal vyberte **Vytvořit zdroj** > **Analytics** > **Azure Databricks**.

   ![Vytvoření prostředku Azure Databricks na webu Azure Portal](./media/databricks-deployment/create-databricks-resource.png)

2. V části **Služba Azure Databricks** zadejte hodnoty pro vytvoření pracovního prostoru Databricks.

    |Vlastnost  |Popis  |
    |---------|---------|
    |**Název pracovního prostoru**     | Zadejte název pracovního prostoru Databricks.        |
    |**Předplatné**     | Z rozevíracího seznamu vyberte své předplatné Azure.        |
    |**Skupina prostředků**     | Určete, jestli chcete vytvořit novou skupinu prostředků, nebo použít existující. Skupina prostředků je kontejner, který obsahuje související prostředky pro řešení Azure. Další informace naleznete v tématu [Přehled skupin prostředků v Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview). |
    |**Umístění**     | Vyberte preferovanou oblast. Informace o dostupných oblastech najdete v [tématu Služby Azure dostupné podle oblastí](https://azure.microsoft.com/regions/services/).        |
    |**Cenová úroveň**     |  Vyberte si mezi **standardními**, **prémiovými**nebo **zkušebními verzemi**. Další informace o těchto úrovních najdete na [stránce s cenami za Databricks](https://azure.microsoft.com/pricing/details/databricks/).       |
    |**Virtuální síť**     |   Ne       |

3. Vyberte **Vytvořit**. Vytvoření pracovního prostoru trvá několik minut. Během vytváření pracovního prostoru můžete zobrazit stav nasazení v **oznámení .**

## <a name="install-azure-databricks-tools"></a>Instalace nástrojů Azure Databricks

**Cli Databricks** můžete použít k připojení ke clusterům Azure Databricks a k nahrání souborů z místního počítače. Clustery Databricks přistupují k souborům prostřednictvím DBFS (Databricks File System).

1. Nařízení o cli Databricks vyžaduje Python 3.6 nebo vyšší. Pokud již máte nainstalovaný Python, můžete tento krok přeskočit.

   **Ve Windows:**

   [Stažení Pythonu pro Windows](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   **Pro Linux:** Python je předinstalován na většině linuxových distribucí. Spuštěním následujícího příkazu zobrazíte, kterou verzi jste nainstalovali:

   ```bash
   python3 --version
   ```

2. Použijte pip k instalaci Databricks CLI. Python 3.4 a novější ve výchozím nastavení obsahují pip. Použijte pip3 pro Python 3. Spusťte následující příkaz:

   ```bash
   pip3 install databricks-cli
   ```

3. Po instalaci příkazového řádku Databricks otevřete nový příkazový `databricks`řádek a spusťte příkaz . Pokud se zobrazí **'databricks' není rozpoznán jako vnitřní nebo externí chyba příkazu**, ujistěte se, že jste otevřeli nový příkazový řádek.

## <a name="set-up-azure-databricks"></a>Nastavení Datových cihel Azure

Nyní, když máte nainstalováno nařízení cli Databricks, je třeba nastavit podrobnosti ověřování.

1. Spusťte příkaz `databricks configure --token`příkazu příkazu příkazu příkazu Příkaz příkazu Databricks .

2. Po spuštění příkazu configure budete vyzváni k zadání hostitele. Adresa URL hostitele používá formát: **https://<\Location>.azuredatabricks.net**. Například pokud jste vybrali **eastus2** během vytváření služby Azure **https://eastus2.azuredatabricks.net**Databricks, hostitel by .

3. Po zadání hostitele budete vyzváni k zadání tokenu. Na webu Azure Portal vyberte **Spustit pracovní prostor** a spusťte pracovní prostor Azure Databricks.

   ![Spuštění pracovního prostoru Azure Databricks](./media/databricks-deployment/launch-databricks-workspace.png)

4. Na domovské stránce pracovního prostoru vyberte **Uživatelská nastavení**.

   ![Uživatelská nastavení v pracovním prostoru Azure Databricks](./media/databricks-deployment/databricks-user-settings.png)

5. Na stránce Nastavení uživatele můžete vygenerovat nový token. Zkopírujte vygenerovaný token a vložte jej zpět do příkazového řádku.

   ![Generování nového přístupového tokenu v pracovním prostoru Azure Databricks](./media/databricks-deployment/generate-token.png)

Teď byste měli mít přístup ke všem clusterům Azure Databricks, které vytvoříte a nahrajete soubory do DBFS.

## <a name="download-worker-dependencies"></a>Stáhnout závislosti pracovníků

1. Microsoft.Spark.Worker pomáhá Apache Spark spouštět vaši aplikaci, jako jsou všechny uživatelem definované funkce (UDFs), které jste napsali. Stáhnout [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).

2. *install-worker.sh* je skript, který umožňuje kopírovat .NET pro apache spark závislé soubory do uzlů clusteru.

   Vytvořte nový soubor s názvem **install-worker.sh** v místním počítači a vložte [obsah install-worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) umístěný na GitHubu.

3. Db-init.sh *db-init.sh* je skript, který instaluje závislosti do clusteru Databricks Spark.

   Vytvořte nový soubor s názvem **db-init.sh** v místním počítači a vložte [obsah db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) umístěný na GitHubu.

   V souboru, který jste `DOTNET_SPARK_RELEASE` právě `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`vytvořili, nastavte proměnnou na . Zbytek *souboru db-init.sh* ponechejte tak, jak je.

> [!Note]
> Pokud používáte systém Windows, ověřte, zda koncovky řádků ve *skriptech install-worker.sh* a *db-init.sh* jsou ve stylu Unixu (LF). Konce řádků můžete měnit prostřednictvím textových editorů, jako je Notepad++ a Atom.

## <a name="publish-your-app"></a>Publikování aplikace

Dále publikujete *mySparkApp* vytvořený v [rozhraní .NET pro Apache Spark – Začínáme v kurzu 10 minut,](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) abyste zajistili, že váš cluster Spark bude mít přístup ke všem souborům, které potřebuje ke spuštění vaší aplikace.

1. Chcete-li publikovat *mySparkApp,* spusťte následující příkazy :

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. Proveďte následující úkoly, abyste mohli publikované soubory aplikací zipovat, abyste je mohli snadno nahrát do clusteru Databricks Spark.

   **Ve Windows:**

   Přejděte na mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64. Potom klikněte pravým tlačítkem myši na složku **Publikovat** a vyberte **příkaz Odeslat do > komprimovované (zip) složky**. Pojmenujte novou složku **publish.zip**.

   **Na Linuxu spusťte následující příkaz:**

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a>Nahrání souborů

V této části nahrajete několik souborů do DBFS, aby váš cluster měl vše, co potřebuje ke spuštění aplikace v cloudu. Při každém nahrání souboru do dbfs, ujistěte se, že jste v adresáři, kde je tento soubor umístěn v počítači.

1. Spusťte následující příkazy pro nahrání *db-init.sh*, *install-worker.sh*a *Microsoft.Spark.Worker* do DBFS:

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz dbfs:/spark-dotnet/   Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz
   ```

2. Spusťte následující příkazy k nahrání zbývajících souborů, které bude váš cluster potřebovat ke spuštění aplikace: složka publikování na zip, *input.txt*a *microsoft-spark-2.4.x-0.3.0.jar*.

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.0\ubuntu.16.04-x64 directory
   databricks fs cp mySparkApp.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2.4.x-0.6.0.jar dbfs:/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar
   ```

## <a name="create-a-job"></a>Vytvoření úlohy

Vaše aplikace běží na Azure Databricks prostřednictvím úlohy, která spouští **spark-submit**, což je příkaz, který používáte ke spuštění .NET pro úlohy Apache Spark.

1. V pracovním prostoru Azure Databricks vyberte ikonu **Úlohy** a potom **+ Vytvořit úlohu**.

   ![Vytvoření úlohy Azure Databricks](./media/databricks-deployment/create-job.png)

2. Vyberte název úlohy a pak vyberte **Konfigurovat spark-submit**.

   ![Konfigurace úlohy spark-submit pro Databricks](./media/databricks-deployment/configure-spark-submit.png)

3. Vložte do konfigurace úlohy následující parametry. Potom vyberte **Potvrdit**.

   ```
   ["--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a>Vytvoření clusteru

1. Přejděte do úlohy a vyberte **Upravit** a nakonfigurujte cluster své úlohy.

2. Nastavte cluster na **Spark 2.4.1**. Potom vyberte **Možnosti upřesnit** > **init skripty**. Nastavte cestu skriptu `dbfs:/spark-dotnet/db-init.sh`Init jako .

   ![Konfigurace clusteru spark v Azure Databricks](./media/databricks-deployment/cluster-config.png)

3. Chcete-li potvrdit nastavení clusteru, vyberte potvrdit možnost **Potvrdit.**

## <a name="run-your-app"></a>Spuštění aplikace

1. Přejděte ke své úloze a vyberte **Spustit nyní,** chcete-li spustit úlohu v nově nakonfigurovaném clusteru Spark.

2. Vytvoření clusteru úlohy trvá několik minut. Jakmile je vytvořena, bude vaše úloha odeslána a můžete zobrazit výstup.

3. V levé nabídce vyberte **Clustery** a potom název a spuštění úlohy.

4. Chcete-li zobrazit výstup úlohy, vyberte **protokoly ovladačů.** Po dokončení provádění aplikace se zobrazí stejná tabulka počtu slov z místního spuštění Začínáme zapsaného do standardní výstupní konzoly.

   ![Výstupní tabulka úloh Azure Databricks](./media/databricks-deployment/table-output.png)

   Gratulujeme, jste spustit svůj první .NET pro Apache Spark aplikace v cloudu!

## <a name="clean-up-resources"></a>Vyčištění prostředků

Pokud už nepotřebujete pracovní prostor Databricks, můžete odstranit prostředek Azure Databricks na webu Azure Portal. Můžete také výběrem názvu skupiny prostředků otevřít stránku skupiny prostředků a pak vybrat **Odstranit skupinu prostředků**.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste nasadili .NET pro aplikaci Apache Spark do Databricks. Další informace o Databricks, pokračujte v dokumentaci Azure Databricks.

> [!div class="nextstepaction"]
> [Dokumentace k Azure Databricks](https://docs.microsoft.com/azure/azure-databricks/)
