---
title: Instalace rozhraní .NET pro Apache Spark na poznámkové bloky Jupyter v clusterech Azure HDInsight Spark
description: Přečtěte si, jak nainstalovat rozhraní .NET pro Apache Spark do poznámkových bloků Jupyter od Azure HDInsight.
ms.date: 03/13/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 32047efcde093a3752bdd59baa88896d1547b93e
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546747"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a>Instalace rozhraní .NET pro Apache Spark na poznámkové bloky Jupyter v clusterech Azure HDInsight Spark

Tento článek vás naučí, jak nainstalovat rozhraní .NET pro Apache Spark na poznámkové bloky Jupyter v clusterech Azure HDInsight Spark. Rozhraní .NET pro Apache Spark můžete nasadit do clusterů Azure HDInsight prostřednictvím kombinace příkazového řádku a portálu Azure (další informace najdete v tématu [jak nasadit aplikaci .NET pro Apache Spark do Azure HDInsight](../tutorials/hdinsight-deployment.md)), ale poznámkové bloky poskytují více interaktivní a iterativní prostředí.

Clustery Azure HDInsight už mají notebooky Jupyter, takže jediné, co musíte udělat, je nakonfigurovat poznámkové bloky Jupyter tak, aby spouštěly rozhraní .NET pro Apache Spark. Chcete-li použít .NET pro Apache Spark ve vašich poznámkových bloků Jupyter, C# REPL je potřeba ke spuštění kódu C# řádek po řádku a zachovat stav spuštění v případě potřeby. [Try .NET](https://github.com/dotnet/try) byl integrován jako oficiální .NET REPL.

Chcete-li povolit rozhraní .NET pro Apache Spark prostřednictvím prostředí Jupyter Notebooks, musíte postupovat podle několika ručních kroků přes [Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) a odeslat [akce skriptu](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) v clusteru HDInsight Spark.

> [!NOTE]
> Tato funkce je *experimentální* a není podporována týmem HDInsight Spark.

## <a name="prerequisites"></a>Požadavky

Pokud ještě nemáte, vytvořte cluster [Azure HDInsight Spark.](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-hdinsight-spark-cluster)

1. Navštivte [portál Azure](https://portal.azure.com) a vyberte **+ Vytvořit prostředek**.

1. Vytvořte nový prostředek clusteru Azure HDInsight. Vyberte **Spark 2.4** a **HDI 4.0** během vytváření clusteru.

## <a name="install-net-for-apache-spark"></a>Instalace rozhraní .NET pro Apache Spark

Na webu Azure Portal vyberte **cluster HDInsight Spark,** který jste vytvořili v předchozím kroku.

### <a name="stop-the-livy-server"></a>Zastavení serveru Livy

1. Na portálu vyberte **Přehled**a pak vyberte **Ambari home**. Po zobrazení výzvy zadejte přihlašovací údaje clusteru.

   ![Zastavit livy server](./media/hdinsight-notebook-installation/select-ambari.png)

2. V levé navigační nabídce vyberte **Spark2** a vyberte **LIVY FOR SPARK2 SERVER**.

   ![Zastavit livy server](./media/hdinsight-notebook-installation/select-livyserver.png)

3. Vyberte **hn0... hostitele**.

   ![Zastavit livy server](./media/hdinsight-notebook-installation/select-host.png)

4. Vyberte tři tečky vedle **Livy pro Spark2 Server** a vyberte **Zastavit**. Po zobrazení výzvy pokračujte výběrem **možnosti OK.**

   Zastavte Livy pro Spark2 Server.
   ![Zastavit livy server](./media/hdinsight-notebook-installation/stop-server.png)

5. Opakujte předchozí kroky pro **hn1... hostitele**.

### <a name="submit-an-hdinsight-script-action"></a>Odeslání akce skriptu HDInsight

1. Je `install-interactive-notebook.sh` skript, který instaluje .NET pro Apache Spark a provádí změny Apache Livy a sparkmagic. Před odesláním akce skriptu do služby HDInsight je třeba vytvořit a nahrát `install-interactive-notebook.sh`.

   Vytvořte nový soubor s názvem **install-interactive-notebook.sh** v místním počítači a vložte obsah [install-interactive-notebook.sh obsahu](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).

   Nahrajte skript do [identifikátoru URI,](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) který je přístupný z clusteru HDInsight. Například, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.

2. Spouštění `install-interactive-notebook.sh` v clusteru pomocí [akcí skriptu HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).

   Vraťte se do clusteru HDI na webu Azure Portal a z možností vlevo vyberte **Akce skriptu.** Odešlete jednu akci skriptu pro nasazení rozhraní .NET pro Apache Spark REPL v clusteru HDInsight Spark. Použijte následující nastavení:

   |Vlastnost  |Popis  |
   |---------|---------|
   | Typ skriptu | Vlastní |
   | Name (Název) | *Instalace rozhraní .NET pro interaktivní poznámkové bloky Apache Spark* |
   | Bash skript URI | Identifikátor URI, do `install-interactive-notebook.sh`kterého jste nahráli . |
   | Typ uzlu| Vedoucí a pracovník |
   | Parametry | .NET pro verzi Apache Spark. Můžete zkontrolovat [.NET pro Apache Spark verze](https://github.com/dotnet/spark/releases). Například, pokud chcete nainstalovat Sparkdotnet verze 0.6.0 `0.6.0`pak by to bylo .

   Přechod na další krok, když se vedle stavu akce skriptu zobrazí zelené značky.

### <a name="start-the-livy-server"></a>Spuštění serveru Livy

Postupujte podle pokynů v části [Stop Livy server](#stop-the-livy-server) na **Start** (spíše než **Stop)** Livy for Spark2 Server pro hostitele **hn0** a **hn1**.

### <a name="set-up-spark-default-configurations"></a>Nastavení výchozích konfigurací Spark

1. Na portálu vyberte **Přehled**a pak vyberte **Ambari home**. Po zobrazení výzvy zadejte přihlašovací údaje clusteru.

2. Vyberte **Spark2** a **CONFIGS**. Potom vyberte **Vlastní spark2-výchozí hodnoty**.

   ![Nastavit konfigurace](./media/hdinsight-notebook-installation/spark-configs.png)

3. Vyberte **Přidat vlastnost...** a přidejte výchozí nastavení Spark.

   ![Přidat vlastnost](./media/hdinsight-notebook-installation/add-property.png)

   Existují tři individuální vlastnosti. Přidejte je jeden po druhém pomocí typu vlastnosti **TEXT** v režimu přidání vlastnosti Single. Zkontrolujte, zda nemáte žádné mezery před nebo za některou z klíčů / hodnot.

   * **Vlastnost 1**
       * Klíč:&ensp;&ensp;`spark.dotnet.shell.command`
       * Hodnota: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`

   * **Vlastnost 2** Použijte verzi rozhraní .NET pro Apache Spark, kterou jste zahrnuli do předchozí akce skriptu.
       * Klíč:&ensp;&ensp;`spark.dotnet.packages`
       * Hodnota: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`

   * **Vlastnost 3**
       * Klíč:&ensp;&ensp;`spark.dotnet.interpreter`
       * Hodnota: `try`

   Například následující obrázek zachycuje nastavení pro přidání vlastnosti 1:

   ![Nastavit konfigurace](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   Po přidání tří vlastností vyberte **ULOŽIT**. Pokud se zobrazí varovná obrazovka doporučení konfiguračních konfigurací, vyberte **možnost POKRAČOVAT V OPAČNÉM PŘÍPADĚ**.

4. Restartujte ohrožené součásti.

   Po přidání nových vlastností je třeba restartovat součásti, které byly ovlivněny změnami. V horní části vyberte **restartovat**a potom **restartujte všechny ovlivněné** z rozevíracího souboru.

   ![Nastavit konfigurace](./media/hdinsight-notebook-installation/restart-affected.png)

   Po zobrazení výzvy vyberte **možnost POTVRDIT RESTART ALL,** chcete-li pokračovat, a pak klepněte na tlačítko **OK,** abyste to dokončili.

## <a name="submit-jobs-through-a-jupyter-notebook"></a>Odeslání úloh prostřednictvím poznámkového bloku Jupyter

Po dokončení předchozích kroků můžete nyní odeslat úlohy .NET pro Apache Spark prostřednictvím poznámkových bloků Jupyter.

1. Vytvořte novou .NET pro poznámkový blok Apache Spark. Spusťte poznámkový blok Jupyter z clusteru HDI na webu Azure Portal.

   ![Spuštění notebooku Jupyter](./media/hdinsight-notebook-installation/launch-notebook.png)

   Potom vyberte **Nový** > **.NET Spark (C#)** pro vytvoření poznámkového bloku.

   ![Poznámkový blok Jupyter](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. Odeslat úlohy pomocí rozhraní .NET pro Apache Spark.

   K vytvoření datového rámce použijte následující fragment kódu:

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![Odeslat úlohu Spark](./media/hdinsight-notebook-installation/create-df.png)

   Pomocí následujícího fragmentu kódu zaregistrujte uživatelem definovanou funkci (UDF) a použijte UDF s datovými rámci:

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![Odeslat úlohu Spark](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a>Další kroky

* [Nasazení rozhraní .NET pro aplikaci Apache Spark do Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [Dokumentace ke službě HDInsight](https://docs.microsoft.com/azure/hdinsight/)
