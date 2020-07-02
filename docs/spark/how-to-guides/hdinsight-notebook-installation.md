---
title: Instalace rozhraní .NET pro Apache Spark na poznámkových blocích Jupyter v clusterech s Azure HDInsight Spark
description: Přečtěte si, jak nainstalovat .NET pro Apache Spark v poznámkových blocích Jupyter v Azure HDInsight.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 14babf7a551192b286f309393e3bbff25d4745d5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617740"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a>Instalace rozhraní .NET pro Apache Spark na poznámkových blocích Jupyter v clusterech s Azure HDInsight Spark

V tomto článku se dozvíte, jak nainstalovat .NET pro Apache Spark na poznámkových blocích Jupyter v clusterech s Azure HDInsight Spark. .NET pro Apache Spark v clusterech Azure HDInsight můžete nasadit pomocí kombinace příkazového řádku a Azure Portal (Další informace najdete v tématu [Jak nasadit rozhraní .NET pro Apache Spark aplikaci do služby Azure HDInsight](../tutorials/hdinsight-deployment.md)), ale poznámkové bloky poskytují interaktivní a iterativní možnosti.

Clustery Azure HDInsight se už dodávají s poznámkovým blokem Jupyter, takže stačí, když nakonfigurujete poznámkové bloky Jupyter tak, aby spouštěly rozhraní .NET pro Apache Spark. Chcete-li použít rozhraní .NET pro Apache Spark ve vašich poznámkových blocích Jupyter, je nutné, aby byl kód jazyka C# spouštěn po řádku a aby v případě potřeby zachoval stav provádění. [Vyzkoušejte rozhraní .NET](https://github.com/dotnet/try) , které je integrované jako oficiální REPL .NET.

Pokud chcete povolit rozhraní .NET pro Apache Spark prostřednictvím Jupyter poznámkových bloků, je nutné provést několik ručních kroků prostřednictvím [Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) a odeslat [akce skriptu](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) v clusteru HDInsight Spark.

> [!NOTE]
> Tato funkce je *experimentální* a tým HDInsight Spark ho nepodporuje.

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a>Požadavky

Pokud ho ještě nemáte, vytvořte cluster [Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight) .

1. Přejděte na [Azure Portal](https://portal.azure.com) a vyberte **+ vytvořit prostředek**.

1. Vytvořte nový prostředek clusteru Azure HDInsight. Během vytváření clusteru vyberte **Spark 2,4** a **HDI 4,0** .

## <a name="install-net-for-apache-spark"></a>Instalace rozhraní .NET pro Apache Spark

V Azure Portal vyberte **cluster HDInsight Spark** , který jste vytvořili v předchozím kroku.

### <a name="stop-the-livy-server"></a>Zastavení serveru Livy

1. Na portálu vyberte **Přehled**a pak vyberte **Ambari Home (domů**). Pokud se zobrazí výzva, zadejte přihlašovací údaje pro cluster.

   ![Zastavit Livy Server](./media/hdinsight-notebook-installation/select-ambari.png)

2. V levé navigační nabídce vyberte **Spark2** a jako **Server Spark2 vyberte LIVY**.

   ![Zastavit Livy Server](./media/hdinsight-notebook-installation/select-livyserver.png)

3. Vybrat **hn0... Hostitel**:

   ![Zastavit Livy Server](./media/hdinsight-notebook-installation/select-host.png)

4. Vyberte tři tečky vedle **Livy pro server Spark2** a vyberte **zastavit**. Po zobrazení výzvy pokračujte výběrem **OK** .

   Zastavte Livy pro server Spark2.
   ![Zastavit Livy Server](./media/hdinsight-notebook-installation/stop-server.png)

5. Opakujte předchozí postup pro **HN1... Hostitel**:

### <a name="submit-an-hdinsight-script-action"></a>Odeslat akci skriptu HDInsight

1. `install-interactive-notebook.sh`Je skript, který nainstaluje rozhraní .NET pro Apache Spark a provede změny v Apache Livy a sparkmagic. Než odešlete akci skriptu do HDInsight, je potřeba vytvořit a nahrát `install-interactive-notebook.sh` .

   V místním počítači vytvořte nový soubor s názvem **install-Interactive-notebook.sh** a vložte obsah [install-Interactive-notebook.sh obsahu](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).

   Nahrajte skript do [identifikátoru URI](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) , který je přístupný z clusteru HDInsight. Například, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.

2. Spusťte `install-interactive-notebook.sh` v clusteru pomocí [akcí skriptu HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).

   Vraťte se do clusteru HDI ve Azure Portal a vyberte **akce skriptu** z možností na levé straně. Odešlete jednu akci skriptu pro nasazení rozhraní .NET pro Apache Spark REPL do clusteru HDInsight Spark. Použijte následující nastavení:

   |Vlastnost  |Popis  |
   |---------|---------|
   | Typ skriptu | Vlastní |
   | Name | *Instalace rozhraní .NET pro Apache Spark interaktivní Poznámkový blok* |
   | Identifikátor URI skriptu bash | Identifikátor URI, na který jste nahráli `install-interactive-notebook.sh` . |
   | Typ (typy) uzlů| Vedoucí a pracovní proces |
   | Parametry | Rozhraní .NET pro Apache Spark verzi. Můžete kontrolovat [verze rozhraní .NET pro Apache Spark](https://github.com/dotnet/spark/releases). Například pokud chcete nainstalovat Sparkdotnet verze 0.6.0, bude `0.6.0` .

   Přejděte k dalšímu kroku, když se vedle stavu akce skriptu zobrazí zelené zaškrtnutí.

### <a name="start-the-livy-server"></a>Spuštění serveru Livy

Postupujte podle pokynů v oddílu [zastavení Livy serveru](#stop-the-livy-server) a **Spusťte** (místo **zastavení**) Livy pro server Spark2 pro hostitele **hn0** a **HN1**.

### <a name="set-up-spark-default-configurations"></a>Nastavení výchozích konfigurací Sparku

1. Na portálu vyberte **Přehled**a pak vyberte **Ambari Home (domů**). Po zobrazení výzvy zadejte přihlašovací údaje clusteru.

2. Vyberte **Spark2** a **Konfigurace**. Pak vyberte **vlastní spark2 – výchozí**.

   ![Nastavení konfigurací](./media/hdinsight-notebook-installation/spark-configs.png)

3. Pokud chcete přidat výchozí nastavení Sparku, vyberte **Přidat vlastnost...**

   ![Přidat vlastnost](./media/hdinsight-notebook-installation/add-property.png)

   Existují tři jednotlivé vlastnosti. Současně je přidejte pomocí typu vlastnosti **text** v režimu přidání jedné vlastnosti. Ověřte, že nemáte žádné nadbytečné mezery před nebo za libovolnými klíči/hodnotami.

   * **Vlastnost 1**
       * Zkrat&ensp;&ensp;`spark.dotnet.shell.command`
       * Hodnota: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`

   * **Vlastnost 2** Použijte verzi rozhraní .NET pro Apache Spark, kterou jste zahrnuli do předchozí akce skriptu.
       * Zkrat&ensp;&ensp;`spark.dotnet.packages`
       * Hodnota: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`

   * **Vlastnost 3**
       * Zkrat&ensp;&ensp;`spark.dotnet.interpreter`
       * Hodnota: `try`

   Například následující obrázek zachytí nastavení pro přidání vlastnosti 1:

   ![Nastavení konfigurací](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   Po přidání tří vlastností vyberte **Uložit**. Pokud se zobrazí varovná obrazovka s doporučeními pro konfiguraci, vyberte **pokračovat**.

4. Příslušné součásti restartujte.

   Po přidání nových vlastností je nutné restartovat součásti, které byly ovlivněny změnami. V horní části vyberte **restartovat**a pak **všechny ovlivněné** z rozevíracího seznamu.

   ![Nastavení konfigurací](./media/hdinsight-notebook-installation/restart-affected.png)

   Po zobrazení výzvy vyberte **Potvrdit RESTARTOVÁNÍ všech** , aby se dalo dokončit, a pak klikněte na **OK** .

## <a name="submit-jobs-through-a-jupyter-notebook"></a>Odesílání úloh prostřednictvím poznámkového bloku Jupyter

Po dokončení předchozích kroků můžete nyní odeslat .NET pro Apache Spark úlohy prostřednictvím poznámkových bloků Jupyter.

1. Vytvoří nový Poznámkový blok .NET pro Apache Spark. Z clusteru HDI z Azure Portal spusťte Poznámkový blok Jupyter.

   ![Spustit Jupyter Notebook](./media/hdinsight-notebook-installation/launch-notebook.png)

   Pak vyberte **Nový**  >  **.NET Spark (C#)** a vytvořte Poznámkový blok.

   ![Poznámkový blok Jupyter](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. Odeslání úloh pomocí .NET pro Apache Spark.

   Pomocí následujícího fragmentu kódu vytvořte datový rámec:

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![Odeslat Sparkovou úlohu](./media/hdinsight-notebook-installation/create-df.png)

   Pomocí následujícího fragmentu kódu Zaregistrujte uživatelsky definovanou funkci (UDF) a použijte UDF s datovými rámečky:

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![Odeslat Sparkovou úlohu](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a>Další kroky

* [Nasazení aplikace .NET pro Apache Spark do Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [Dokumentace ke službě HDInsight](https://docs.microsoft.com/azure/hdinsight/)
