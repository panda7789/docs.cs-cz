---
title: Nasazení rozhraní .NET pro aplikaci Apache Spark do Azure HDInsight
description: Zjistěte, jak nasadit .NET pro aplikaci Apache Spark do HDInsight.
ms.date: 01/23/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 77b57463375c36444532bdd383ec4b3bfe3ab056
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77504165"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a>Kurz: Nasazení rozhraní .NET pro aplikaci Apache Spark do Azure HDInsight

Tento kurz vás naučí, jak nasadit vaši .NET pro aplikaci Apache Spark do cloudu prostřednictvím clusteru Azure HDInsight. HDInsight usnadňuje vytváření a konfiguraci clusteru Spark v Azure, protože clustery Spark ve HDInsightu jsou kompatibilní s Azure Storage a Azure Data Lake Storage.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> * Přístup k účtům úložiště pomocí Azure Storage Explorer.
> * Vytvořte cluster Azure HDInsight.
> * Publikujte svou aplikaci .NET pro Apache Spark.
> * Vytvořte a spusťte akci skriptu HDInsight.
> * Spusťte aplikaci .NET pro Apache Spark v clusteru HDInsight.

## <a name="prerequisites"></a>Požadavky

Než začnete, proveďte následující úkoly:

* Pokud nemáte předplatné Azure, vytvořte si [bezplatný účet](https://azure.microsoft.com/free/).
* Přihlaste se k [portálu Azure](https://portal.azure.com/).
* Nainstalujte Azure Storage Explorer do počítače [s Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linuxem](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)nebo [MacOS.](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409)
* Dokončete [rozhraní .NET pro Apache Spark – začínáme v kurzu 10 minut.](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)

## <a name="access-your-storage-accounts"></a>Přístup k účtům úložiště

1. Otevřete Průzkumníka úložišť Azure.

2. V levé nabídce vyberte **Přidat účet** a přihlaste se ke svému účtu Azure.

    ![Přihlášení k účtu Azure z Průzkumníka úložiště](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   Po přihlášení byste měli vidět všechny účty úložiště, které máte, a všechny prostředky, které jste nahráli do svých účtů úložiště.

## <a name="create-an-hdinsight-cluster"></a>Vytvoření clusteru HDInsight

> [!IMPORTANT]
> Fakturace pro clustery HDInsight se poměrně účtuje za minutu, i když je nepoužíváte. Až přestanete cluster používat, nezapomeňte ho odstranit. Další informace naleznete v části [Vyčištění prostředků](#clean-up-resources) v tomto kurzu.

1. Navštivte [portál Azure](https://portal.azure.com).

2. Vyberte **+ Vytvořit prostředek**. Potom vyberte **HDInsight** z kategorie **Analytics.**

    ![Vytvoření prostředků HDInsight z webu Azure Portal](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. V části **Základy** zadejte tyto hodnoty:

    |Vlastnost  |Popis  |
    |---------|---------|
    |Předplatné  | V rozevíracím programu vyberte jedno z aktivních předplatných Azure. |
    |Skupina prostředků | Určete, jestli chcete vytvořit novou skupinu prostředků, nebo použít existující. Skupina prostředků je kontejner, který obsahuje související prostředky pro řešení Azure. |
    |Název clusteru | Pojmenujte svůj cluster HDInsight Spark.|
    |Umístění   | Vyberte umístění skupiny prostředků. Šablona toto umístění používá k vytvoření clusteru i jako výchozí úložiště clusteru. |
    |Typ clusteru| Jako typ clusteru vyberte **Spark.**|
    |Verze clusteru|Toto pole se automaticky naplní výchozí verzí, jakmile bude vybrán typ clusteru. Vyberte verzi Spark 2.3 nebo 2.4.|
    |Uživatelské jméno přihlášení clusteru| Zadejte uživatelské jméno přihlášení clusteru.  Výchozí uživatelské jméno je *admin*. |
    |Heslo přihlášení clusteru| Zadejte libovolné přihlašovací heslo. |
    |Uživatelské jméno Secure Shell (SSH)| Zadejte uživatelské jméno SSH. Ve výchozím nastavení má tento účet stejné heslo jako účet *Uživatelské jméno přihlášení clusteru*. |

4. Vyberte **Další: Úložiště >>** a pokračujte na stránku **Úložiště.** V části **Úložiště** zadejte tyto hodnoty:

    |Vlastnost  |Popis  |
    |---------|---------|
    |Typ primárního úložiště|Použijte výchozí hodnotu **Azure Storage**.|
    |Metoda výběru|Použijte výchozí hodnotu **Vybrat ze seznamu**.|
    |Účet primárního úložiště|Vyberte si předplatné a jeden z vašich aktivních účtů úložiště v rámci tohoto předplatného.|
    |Kontejner|Tento kontejner je konkrétní kontejner objektů blob v účtu úložiště, kde váš cluster hledá soubory pro spuštění aplikace v cloudu. Můžete mu dát libovolné dostupné jméno.|

5. V části **Revize + vytvoření**vyberte **Vytvořit**. Vytvoření clusteru trvá přibližně 20 minut. Před pokračováním k dalšímu kroku je nutné vytvořit cluster.

## <a name="publish-your-app"></a>Publikování aplikace

Dále publikujete *mySparkApp* vytvořený v [rozhraní .NET pro Apache Spark – Začínáme v kurzu 10 minut,](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) který vašemu clusteru Spark poskytuje přístup ke všem souborům, které potřebuje ke spuštění aplikace.

1. Chcete-li publikovat *mySparkApp,* spusťte následující příkazy :

   **Ve Windows:**

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   **Na Linuxu:**

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. Chcete-li publikované soubory aplikací rozbalit, proveďte následující úkoly, abyste je mohli snadno nahrát do clusteru HDInsight.

   **Ve Windows:**

   Přejděte na *mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64*. Potom klikněte pravým tlačítkem myši na složku **Publikovat** a vyberte **příkaz Odeslat do > komprimovované (zip) složky**. Pojmenujte novou složku **publish.zip**.

   **Na Linuxu spusťte následující příkaz:**

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a>Nahrání souborů do Azure

Dále použijete Průzkumníka úložiště Azure k nahrání následujících pěti souborů do kontejneru objektů blob, který jste zvolili pro úložiště clusteru:

* Microsoft.Spark.Worker
* install-worker.sh
* publikovat.zip
* Microsoft-spark-2.3.x-0.3.0.jar
* input.txt.

1. Otevřete Azure Storage Explorer a přejděte na svůj účet úložiště z levé nabídky. Přejděte k kontejneru objektů blob pro váš cluster v části **kontejnery objektů blob** ve vašem účtu úložiště.

2. *Microsoft.Spark.Worker* pomáhá Apache Spark spouštět vaši aplikaci, jako jsou všechny uživatelem definované funkce (UDFs), které jste napsali. Stáhnout [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz). Pak vyberte **Nahrát** v Průzkumníku úložiště Azure a nahrajte pracovníka.

   ![Nahrání souborů do Průzkumníka úložiště Azure](./media/hdinsight-deployment/upload-files-to-storage.png)

3. *install-worker.sh* je skript, který umožňuje kopírovat .NET pro apache spark závislé soubory do uzlů clusteru.

   Vytvořte nový soubor s názvem **install-worker.sh** místním počítači a vložte [obsah install-worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) umístěný na GitHubu. Potom nahrajte *install-worker.sh* do kontejneru objektů blob.

4. Cluster potřebuje soubor publish.zip, který obsahuje publikované soubory vaší aplikace. Přejděte do publikované složky **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**a vyhledejte **soubor publish.zip**. Pak nahrajte *publish.zip* do kontejneru objektů blob.

5. Cluster potřebuje kód aplikace, který byl zabalen do souboru jar. Přejděte do publikované složky **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**a vyhledejte **microsoft-spark-2.3.x-0.3.0.jar**. Potom nahrajte soubor jar do kontejneru objektů blob.

   Může existovat více souborů .jar (pro verze 2.3.x a 2.4.x Spark). Musíte zvolit soubor .jar, který odpovídá verzi Spark, kterou jste zvolili při vytváření clusteru. Pokud jste například při vytváření clusteru zvolili Spark 2.3.0.3.0.jar, zvolte například *microsoft-spark-2.3.x-0.3.0.jar.*

6. Váš cluster potřebuje vstup do vaší aplikace. Přejděte do adresáře **mySparkApp** a vyhledejte **soubor input.txt**. Nahrajte vstupní soubor do **adresáře uživatele/sshuseru** v kontejneru objektů blob. Budete se připojovat ke clusteru prostřednictvím ssh a tato složka je místo, kde váš cluster hledá svůj vstup. Soubor *input.txt* je jediný soubor odeslaný do určitého adresáře.

## <a name="run-the-hdinsight-script-action"></a>Spuštění akce skriptu HDInsight

Jakmile váš cluster běží a nahrajete soubory do Azure, spustíte **install-worker.sh** skript v clusteru.

1. Přejděte do clusteru HDInsight Spark na webu Azure Portal a pak vyberte **Akce skriptu**.

2. Vyberte **+ Odeslat nové** a zadejte následující hodnoty:

   |Vlastnost  |Popis  |
   |---------|---------|
   | Typ skriptu |Vlastní|
   | Name (Název) | Instalace pracovníka|
   | Bash skript URI |https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh </br> Chcete-li tento identifikátor URI potvrdit, klikněte pravým tlačítkem myši na install-worker.sh v Průzkumníku úložiště Azure a vyberte vlastnosti. |
   | Typ uzlu| Pracovník|
   | Parametry | azure </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> /usr/místní/přihrádka

3. Chcete-li skript odeslat, vyberte **vytvořit.**

## <a name="run-your-app"></a>Spuštění aplikace

1. Přejděte do clusteru HDInsight Spark na webu Azure Portal a pak vyberte **Přihlášení SSH + Cluster**.

2. Zkopírujte přihlašovací údaje ssh a vložte přihlášení do terminálu. Přihlaste se ke clusteru pomocí hesla, které nastavíte při vytváření clusteru. Měli byste vidět zprávy, které vás vítají na Ubuntu a Spark.

3. Pomocí příkazu **spark-submit** můžete aplikaci spouštět v clusteru HDInsight. Nezapomeňte nahradit **mycontainer** a **mystorageaccount** v ukázkovém skriptu skutečnými názvy kontejneru objektů blob a účtu úložiště.

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   Při spuštění aplikace se zobrazí stejná tabulka počtu slov z místního spuštění Začínáme zapsaného do konzoly. Gratulujeme, jste spustit svůj první .NET pro Apache Spark aplikace v cloudu!

## <a name="clean-up-resources"></a>Vyčištění prostředků

HDInsight ukládá vaše data ve službě Azure Storage, takže můžete bezpečně odstranit cluster, když se nepoužívá. Za cluster služby HDInsight se účtují poplatky, i když se nepoužívá. Vzhledem k tomu, že poplatky za cluster představují několikanásobek poplatků za úložiště, dává ekonomický smysl odstraňovat clustery, které nejsou používány.

Můžete také výběrem názvu skupiny prostředků otevřít stránku skupiny prostředků a pak vybrat **Odstranit skupinu prostředků**. Odstraněním skupiny prostředků odstraníte cluster HDInsight Spark i výchozí účet úložiště.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste nasadili .NET pro aplikaci Apache Spark do Azure HDInsight. Další informace o HDInsightu najdete v dokumentaci k Azure HDInsightu.

> [!div class="nextstepaction"]
> [Dokumentace ke službě HDInsight](https://docs.microsoft.com/azure/hdinsight/)
