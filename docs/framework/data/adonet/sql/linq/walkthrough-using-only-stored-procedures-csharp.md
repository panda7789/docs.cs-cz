---
title: "Návod: Použití pouze uložené procedury (C#)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1b3cc18f481a0e66d52f021b7bf6b76938fc5018
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-using-only-stored-procedures-c"></a>Návod: Použití pouze uložené procedury (C#)
Tento názorný postup obsahuje základní začátku do konce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář pro přístup k datům spuštěním uložené procedury jenom. Tento přístup se často používá databázi správci omezit, jak přistupovat k úložišti dat.  
  
> [!NOTE]
>  Můžete taky uložené procedury v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikace přepsat výchozí chování, zejména pro `Create`, `Update`, a `Delete` procesy. Další informace najdete v tématu [přizpůsobení vložit, aktualizovat a odstranit operace](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
  
 Pro účely tohoto návodu budete používat dvě metody, které nebyly namapovány na uložené procedury v ukázková databáze Northwind: CustOrdersDetail a CustOrderHist. Mapování nastane, když spustíte nástroj příkazového řádku na SqlMetal ke generování souboru C#. Další informace najdete v části požadavky dále v tomto návodu.  
  
 Tento návod na nespoléhá se [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]. Vývojáře, kteří používají [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] můžete použít také [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] k implementaci funkcí uložené procedury. V tématu [technologie LINQ to SQL nástroje v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Tento názorný postup napsané pomocí Visual C# – vývojové nastavení.  
  
## <a name="prerequisites"></a>Požadavky  
 Tento postup vyžaduje následující:  
  
-   Tento návod používá k uložení souborů vyhrazené složky ("c:\linqtest7"). Než začnete návodu, vytvořte této složky.  
  
-   Ukázkovou databázi Northwind  
  
     Pokud jste tuto databázi ve svém vývojovém počítači, můžete ji stáhnout z webu Microsoft download. Pokyny najdete v tématu [stažení ukázkové databáze](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Po stažení databázi, zkopírujte soubor northwnd.mdf ke složce c:\linqtest7.  
  
-   C# soubor kódu vygenerovaném z databáze Northwind.  
  
     Tento názorný postup byla zapsána pomocí nástroje SqlMetal s následující příkazový řádek:  
  
     **SqlMetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions / pluralizovat**  
  
     Další informace najdete v tématu [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Přehled  
 Tento názorný postup se skládá z šesti hlavní úlohy:  
  
-   Nastavení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] řešení v [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].  
  
-   Přidání System.Data.Linq sestavení do projektu.  
  
-   Přidání souboru kódu databáze do projektu.  
  
-   Vytvoření připojení k databázi.  
  
-   Nastavení uživatelského rozhraní.  
  
-   Spuštění a testování aplikace.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Vytváření dotazu LINQ to SQL řešení  
 V této úloze první vytvoříte [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] řešení, který obsahuje potřebné odkazy na sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Chcete-li vytvořit LINQ to SQL řešení  
  
1.  Na [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **soubor** nabídky, přejděte na příkaz **nový**a potom klikněte na **projektu**.  
  
2.  V **typy projektů** v podokně **nový projekt** dialogové okno, klikněte na tlačítko **Visual C#**.  
  
3.  V **šablony** podokně klikněte na tlačítko **formulářové aplikace Windows**.  
  
4.  V **název** zadejte **SprocOnlyApp**.  
  
5.  V **umístění** ověřte, kam chcete uložit soubory projektu.  
  
6.  Click **OK**.  
  
     Otevře se Návrhář formulářů Windows.  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a>Přidávání do odkaz sestavení SQL LINQ  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Sestavení není součástí standardní šablona formulářové aplikace Windows. Budete muset přidat sestavení sami, jak je popsáno v následujících krocích:  
  
#### <a name="to-add-systemdatalinqdll"></a>Chcete-li přidat knihovně System.Data.Linq.dll  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na **odkazy**a potom klikněte na **přidat odkaz na**.  
  
2.  V **přidat odkaz na** dialogové okno, klikněte na tlačítko **.NET**, klikněte na tlačítko System.Data.Linq sestavení a pak klikněte na tlačítko **OK**.  
  
     Je sestavení přidáno do projektu.  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Přidání souboru Northwind kódu do projektu  
 Tento krok předpokládá, že jste použili nástroj SqlMetal generování souboru kódu na základě ukázková databáze Northwind. Další informace najdete v části požadavky dříve v tomto návodu.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Přidání souboru northwind kódu do projektu  
  
1.  Na **projektu** nabídky, klikněte na tlačítko **přidat existující položku**.  
  
2.  V **přidat existující položku** přesunout do c:\linqtest7\northwind.cs dialogové okno a pak klikněte na tlačítko **přidat**.  
  
     Soubor northwind.cs je přidán do projektu.  
  
## <a name="creating-a-database-connection"></a>Vytvoření připojení k databázi  
 V tomto kroku definujete ukázková databáze Northwind připojení. Tento návod používá jako cestu "c:\linqtest7\northwnd.mdf".  
  
#### <a name="to-create-the-database-connection"></a>Chcete-li vytvořit připojení k databázi  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na **Form1.cs**a potom klikněte na **kód zobrazení**.  
  
2.  Zadejte následující kód do `Form1` třídy:  
  
     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]  
  
## <a name="setting-up-the-user-interface"></a>Nastavení uživatelského rozhraní  
 V této úloze nastavíte rozhraní tak, aby uživatelé mohou spouštět uložené procedury pro přístup k datům v databázi. V aplikacích, které vyvíjíte v tomto průvodci uživatelé můžou používat data v databázi jen pomocí uložené procedury vloženy do aplikace.  
  
#### <a name="to-set-up-the-user-interface"></a>Nastavení uživatelského rozhraní  
  
1.  Návrhář formulářů vraťte se do systému Windows (**Form1.cs[Design]**).  
  
2.  Na **zobrazení** nabídky, klikněte na tlačítko **sada nástrojů**.  
  
     Otevřete panel nástrojů.  
  
    > [!NOTE]
    >  Klikněte **autohide –** připínáček nechat otevřené sady nástrojů při provádění zbývající kroky v této části.  
  
3.  Přetáhněte dvě tlačítka, dvou textových polí a dva popisky z panelu nástrojů na **Form1**.  
  
     Uspořádání ovládacích prvků jako doprovodné obrázku. Rozbalte položku **Form1** tak, aby snadno umístit ovládací prvky.  
  
4.  Klikněte pravým tlačítkem na **label1**a potom klikněte na **vlastnosti**.  
  
5.  Změna **Text** vlastnost z **label1** k **zadejte OrderID:**.  
  
6.  Stejným způsobem pro **label2**, změnit **Text** vlastnost z **label2** k **zadejte CustomerID:**.  
  
7.  Stejným způsobem, změnit **Text** vlastnost pro **button1** k **pořadí podrobnosti**.  
  
8.  Změna **Text** vlastnost pro **button2** k **historie objednávek**.  
  
     Ovládací prvky tlačítek rozšíříte tak, aby veškerý text.  
  
#### <a name="to-handle-button-clicks"></a>Pro zpracování kliknutí na tlačítko  
  
1.  Klikněte dvakrát na **pořadí podrobnosti** na **Form1** obslužné rutiny události button1 otevřete v editoru kódu.  
  
2.  Zadejte následující kód do `button1` obslužné rutiny:  
  
     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]  
  
3.  Nyní klikněte dvakrát na **button2** na **Form1** otevřete `button2` obslužné rutiny  
  
4.  Zadejte následující kód do `button2` obslužné rutiny:  
  
     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Nyní je čas k testování aplikace. Všimněte si, že vaše kontaktu s úložišti dat je omezená na libovolné akce může trvat dvě uložené procedury. Tyto akce jsou vrátit produkty, které jsou zahrnuté pro všechny orderID, které zadáte, nebo pro návrat historii produktů seřazených pro všechny CustomerID zadáte.  
  
#### <a name="to-test-the-application"></a>Testování aplikace  
  
1.  Stisknutím klávesy F5 spusťte ladění.  
  
     Zobrazí se Form1.  
  
2.  V **zadejte OrderID** zadejte `10249`a potom klikněte na **pořadí podrobnosti**.  
  
     Okno se zprávou seznamy produktů, zahrnuté v pořadí 10249.  
  
     Klikněte na tlačítko **OK** zavřete okno se zprávou.  
  
3.  V **zadejte CustomerID** zadejte `ALFKI`a potom klikněte na **historie objednávek**.  
  
     Zobrazí se okno se zprávou, která uvádí historie objednávek pro zákazníka ALFKI.  
  
     Klikněte na tlačítko **OK** zavřete okno se zprávou.  
  
4.  V **zadejte OrderID** zadejte `123`a potom klikněte na **pořadí podrobnosti**.  
  
     Zobrazí se okno se zprávou, která zobrazuje "Žádné výsledky."  
  
     Klikněte na tlačítko **OK** zavřete okno se zprávou.  
  
5.  Na **ladění** nabídky, klikněte na tlačítko **Zastavte ladění**.  
  
     Zavře relaci ladění.  
  
6.  Pokud dokončíte experimentování, můžete kliknout na **zavřít projekt** na **souboru** nabídce a po zobrazení výzvy uložte projekt.  
  
## <a name="next-steps"></a>Další kroky  
 Tento projekt můžete zvýšit tak, že některé změny. Můžete například seznam dostupných uložené procedury v seznamu a mít uživatele, vyberte který postup provést. Výstup sestavy do textového souboru může také datového proudu.  
  
## <a name="see-also"></a>Viz také  
 [Učení podle návodů](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [Uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
