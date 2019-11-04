---
title: Nasazení aplikace .NET pro Apache Spark do Azure HDInsight
description: Zjistěte, jak nasadit rozhraní .NET pro Apache Spark aplikaci do HDInsight.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 3604aff5d1f138071c941ea85546af03185d722d
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460716"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a>Kurz: nasazení aplikace .NET pro Apache Spark do Azure HDInsight

V tomto kurzu se naučíte, jak nasadit aplikaci .NET pro Apache Spark do cloudu prostřednictvím clusteru Azure HDInsight. HDInsight usnadňuje vytvoření a konfiguraci clusteru Spark v Azure, protože Clustery Spark v HDInsight jsou kompatibilní s Azure Storage a Azure Data Lake Storage.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> * Přístup k účtům úložiště pomocí Průzkumník služby Azure Storage.
> * Vytvořte cluster Azure HDInsight.
> * Publikování aplikace .NET pro Apache Spark.
> * Vytvořte a spusťte akci skriptu HDInsight.
> * Spusťte rozhraní .NET pro Apache Spark aplikaci v clusteru HDInsight.

## <a name="prerequisites"></a>Požadavky

Než začnete, proveďte následující úlohy:

* Pokud nemáte předplatné Azure, vytvořte si [bezplatný účet](https://azure.microsoft.com/free/).
* Přihlaste se k [Azure Portal](https://portal.azure.com/).
* Nainstalujte Průzkumník služby Azure Storage na počítač se [systémem Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)nebo [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) .
* Dokončete kurz [k rozhraní .NET pro Apache Spark – Začínáme během 10 minut](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) .

## <a name="access-your-storage-accounts"></a>Přístup k účtům úložiště

1. Otevřete Průzkumník služby Azure Storage.

2. V nabídce vlevo vyberte **Přidat účet** a přihlaste se ke svému účtu Azure.

    ![Přihlaste se k účtu Azure z Průzkumník služby Storage](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   Po přihlášení byste měli vidět všechny účty úložiště, které máte, a všechny prostředky, které jste nahráli do účtů úložiště.

## <a name="create-an-hdinsight-cluster"></a>Vytvoření clusteru HDInsight

> [!IMPORTANT]
> Fakturace za clustery HDInsight se účtuje poměrně po minutách, a to i v případě, že je nepoužíváte. Po dokončení používání clusteru nezapomeňte tento cluster odstranit. Další informace najdete v části [vyčištění prostředků](#clean-up-resources) v tomto kurzu.

1. Navštivte [Azure Portal](https://portal.azure.com).

2. Vyberte **+ vytvořit prostředek**. Pak z kategorie **Analytics** vyberte **HDInsight** .

    ![Vytvořit prostředek HDInsight z Azure Portal](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. V části **základy**zadejte následující hodnoty:

    |Vlastnost  |Popis  |
    |---------|---------|
    |Formě  | V rozevíracím seznamu vyberte jedno z aktivních předplatných Azure. |
    |Skupina prostředků | Určete, zda chcete vytvořit novou skupinu prostředků, nebo použít existující. Skupina prostředků je kontejner, který obsahuje související prostředky pro řešení Azure. |
    |Název clusteru | Zadejte název clusteru HDInsight Spark.|
    |Umístění   | Vyberte umístění pro skupinu prostředků. Šablona používá toto umístění pro vytvoření clusteru i pro výchozí úložiště clusteru. |
    |Typ clusteru| Jako typ clusteru vyberte **Spark** .|
    |Verze clusteru|Po výběru typu clusteru bude toto pole automaticky vyplněno výchozí verzí. Vyberte verzi Sparku 2,3 nebo 2,4.|
    |Uživatelské jméno přihlášení clusteru| Zadejte uživatelské jméno pro přihlášení ke clusteru.  Výchozí název je *admin*. |
    |Heslo pro přihlášení ke clusteru| Zadejte libovolné přihlašovací heslo. |
    |Uživatelské jméno Secure Shell (SSH)| Zadejte uživatelské jméno SSH. Ve výchozím nastavení tento účet sdílí stejné heslo jako účet *přihlášení ke clusteru* . |

4. Kliknutím na tlačítko **Další: úložiště > >** pokračujte na stránku **úložiště** . V části **Storage (úložiště**) zadejte následující hodnoty:

    |Vlastnost  |Popis  |
    |---------|---------|
    |Typ primárního úložiště|Použijte výchozí hodnotu **Azure Storage**.|
    |Metoda výběru|Použijte výchozí hodnotu **vybrat ze seznamu**.|
    |Primární účet úložiště|Vyberte své předplatné a jeden z aktivních účtů úložiště v rámci tohoto předplatného.|
    |vnitřního|Tento kontejner je specifickým kontejnerem objektů BLOB ve vašem účtu úložiště, ve kterém váš cluster hledá soubory ke spuštění vaší aplikace v cloudu. Můžete mu dát libovolný dostupný název.|

5. V nabídce **Revize + vytvořit**vyberte **vytvořit**. Vytvoření clusteru trvá přibližně 20 minut. Aby bylo možné pokračovat k dalšímu kroku, musí být cluster vytvořen.

## <a name="publish-your-app"></a>Publikování aplikace

V dalším kroku publikujete *mySparkApp* vytvořenou v [rozhraní .NET pro Apache Spark – Začínáme během 10 minut](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) , což vašemu clusteru Spark poskytne přístup ke všem souborům, které potřebuje ke spuštění vaší aplikace.

1. Pro publikování *mySparkApp*spusťte následující příkazy:

   **Ve Windows:**

   ```console
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   **V systému Linux:**

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. Proveďte následující úlohy pro zip publikovaných souborů aplikace, abyste je mohli snadno nahrát do clusteru HDInsight.

   **Ve Windows:**

   Přejděte na *mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64*. Potom klikněte pravým tlačítkem na složku pro **publikování** a vyberte **Odeslat do > Komprimovaná složka (ZIP)** . Pojmenujte novou složku **Publish. zip**.

   **V systému Linux spusťte následující příkaz:**

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a>Nahrání souborů do Azure

Dále pomocí Průzkumník služby Azure Storage nahrajte do kontejneru objektů blob, který jste zvolili pro úložiště clusteru, následující pět souborů:

* Microsoft. spark. Worker
* install-worker.sh
* Publish. zip
* Microsoft-Spark-2.3. x-0.3.0. jar
* Input. txt.

1. Otevřete Průzkumník služby Azure Storage a v nabídce vlevo přejděte k účtu úložiště. V části **kontejnery objektů BLOB** v účtu úložiště přejděte k podrobnostem o kontejneru objektů BLOB pro váš cluster.

2. *Microsoft. spark. Worker* pomáhá Apache Spark spustit vaši aplikaci, jako jsou například všechny uživatelsky definované funkce (UDF), které jste mohli napsat. Stáhněte si [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz). Pak vyberte **odeslat** Průzkumník služby Azure Storage a odešlete pracovní proces.

   ![Nahrání souborů do Průzkumník služby Azure Storage](./media/hdinsight-deployment/upload-files-to-storage.png)

3. *Install-Worker.sh* je skript, který umožňuje zkopírovat rozhraní .net pro Apache Spark závislé soubory do uzlů clusteru.

   Vytvořte nový soubor s názvem **install-Worker.sh** v místním počítači a vložte [obsah Install-Worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) umístěný na GitHubu. Pak nahrajte *install-Worker.sh* do kontejneru objektů BLOB.

4. Váš cluster potřebuje soubor Publish. zip, který obsahuje publikované soubory vaší aplikace. Přejděte do složky Publikováno, **mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64**a vyhledejte soubor **Publish. zip**. Pak odešlete soubor *Publish. zip* do kontejneru objektů BLOB.

5. Váš cluster potřebuje kód aplikace, který byl zabalen do souboru jar. Přejděte do složky Publikováno, **mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64**a vyhledejte **Microsoft-Spark-2.3. x-0.3.0. jar**. Pak nahrajte soubor JAR do kontejneru objektů BLOB.

   Může existovat více souborů. jar (pro verze 2.3. x a 2.4. x ze Sparku). Musíte vybrat soubor. jar, který odpovídá verzi Sparku, kterou jste zvolili při vytváření clusteru. Zvolte například *Microsoft-Spark-2.3. x-0.3.0. jar* , pokud při vytváření clusteru vyberete možnost Spark 2.3.2.

6. Váš cluster potřebuje vstup do vaší aplikace. Přejděte do adresáře **mySparkApp** a najděte **input. txt**. Nahrajte vstupní soubor do adresáře **uživatelů nebo sshuser** v kontejneru objektů BLOB. K vašemu clusteru se připojíte přes SSH a tato složka je tam, kde váš cluster hledá svůj vstup. *Vstupní soubor. txt* je jediný soubor nahraný do konkrétního adresáře.

## <a name="run-the-hdinsight-script-action"></a>Spusťte akci skriptu HDInsight.

Po spuštění clusteru a nahrání souborů do Azure spustíte skript **install-Worker.sh** v clusteru.

1. V Azure Portal přejděte do clusteru HDInsight Spark a pak vyberte **akce skriptu**.

2. Vyberte **+ Odeslat nové** a zadejte následující hodnoty:

   |Vlastnost  |Popis  |
   |---------|---------|
   | Typ skriptu |Uživatelská|
   | Name | Instalace pracovního procesu|
   | Identifikátor URI skriptu bash |https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh </br> Pokud chcete tento identifikátor URI potvrdit, klikněte pravým tlačítkem na install-worker.sh v Průzkumník služby Azure Storage a vyberte vlastnosti. |
   | Typ (typy) uzlů| Zaměstnanec|
   | Parametry | Azure </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> /usr/local/bin

3. Vyberte **vytvořit** a odešlete skript.

## <a name="run-your-app"></a>Spuštění aplikace

1. Přejděte do clusteru HDInsight Spark v Azure Portal a pak vyberte **ssh + přihlášení ke clusteru**.

2. Zkopírujte přihlašovací informace SSH a vložte přihlašovací jméno do terminálu. Přihlaste se ke svému clusteru pomocí hesla, které jste nastavili při vytváření clusteru. Měli byste vidět zprávy, které vás přivítá vás a Ubuntu a Spark.

3. Pomocí příkazu **Spark-Submit** spusťte aplikaci v clusteru HDInsight. Nezapomeňte nahradit **myContainer** a **mystorageaccount** v ukázkovém skriptu skutečnými názvy vašeho kontejneru objektů BLOB a účtu úložiště.

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   Když je vaše aplikace spuštěná, zobrazí se stejná tabulka počtu slov z místního spuštění Začínáme s konzolou. Gratulujeme, spustili jste první rozhraní .NET pro Apache Spark aplikaci v cloudu!

## <a name="clean-up-resources"></a>Vyčištění prostředků

HDInsight ukládá vaše data v Azure Storage, takže můžete cluster bezpečně odstranit, pokud se nepoužívá. Účtují se vám také poplatky za cluster HDInsight, a to i v případě, že se nepoužívá. Vzhledem k tomu, že se poplatky za cluster mnohokrát účtují rychleji než poplatky za úložiště, má ekonomický smysl odstraňovat clustery, když se nepoužívají.

Můžete také vybrat název skupiny prostředků a otevřít tak stránku skupiny prostředků a pak vybrat **Odstranit skupinu prostředků**. Odstraněním skupiny prostředků odstraníte cluster HDInsight Spark i výchozí účet úložiště.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste nasadili aplikaci .NET pro Apache Spark do služby Azure HDInsight. Pokud se chcete dozvědět víc o službě HDInsight, přejděte k dokumentaci k Azure HDInsight.

> [!div class="nextstepaction"]
> [Dokumentace ke službě Azure HDInsight](https://docs.microsoft.com/azure/hdinsight/)
