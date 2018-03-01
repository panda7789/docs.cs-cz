---
title: "Návod: Použití pouze uložené procedury (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- vb
ms.assetid: 5a736a30-ba66-4adb-b87c-57d19476e862
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 800cc7d6a1e4aa836ebe75afcbe29a3532ee173a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="walkthrough-using-only-stored-procedures-visual-basic"></a>Návod: Použití pouze uložené procedury (Visual Basic)
Tento názorný postup obsahuje základní začátku do konce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář pro přístup k datům pomocí uložené procedury jenom. Tento přístup se často používá databázi správci omezit, jak přistupovat k úložišti dat.  
  
> [!NOTE]
>  Můžete taky uložené procedury v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikace přepsat výchozí chování, zejména pro `Create`, `Update`, a `Delete` procesy. Další informace najdete v tématu [přizpůsobení vložit, aktualizovat a odstranit operace](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
  
 Pro účely tohoto návodu budete používat dvě metody, které nebyly namapovány na uložené procedury v ukázková databáze Northwind: CustOrdersDetail a CustOrderHist. Mapování nastane, když spustíte nástroj příkazového řádku na SqlMetal ke generování [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] souboru. Další informace najdete v části požadavky dále v tomto návodu.  
  
 Tento návod na nespoléhá se [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]. Vývojáře, kteří používají [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] můžete použít také [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] k implementaci funkcí uložené procedury. V tématu [technologie LINQ to SQL nástroje v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Tento názorný postup napsané pomocí jazyka Visual Basic – vývojové nastavení.  
  
## <a name="prerequisites"></a>Požadavky  
 Tento postup vyžaduje následující:  
  
-   Tento návod používá k uložení souborů vyhrazené složky ("c:\linqtest3"). Než začnete návodu, vytvořte této složky.  
  
-   Ukázkovou databázi Northwind  
  
     Pokud jste tuto databázi ve svém vývojovém počítači, můžete ji stáhnout z webu Microsoft download. Pokyny najdete v tématu [stažení ukázkové databáze](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Po stažení databázi, zkopírujte soubor northwnd.mdf ke složce c:\linqtest3.  
  
-   A [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] vygenerovaném z databáze Northwind souboru kódu.  
  
     Tento názorný postup byla zapsána pomocí nástroje SqlMetal s následující příkazový řádek:  
  
     **SqlMetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions / pluralizovat**  
  
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
  
1.  Na [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **soubor** nabídky, klikněte na tlačítko **nový projekt**.  
  
2.  V **typy projektů** v podokně **nový projekt** dialogové okno, rozbalte seznam **jazyka Visual Basic**a potom klikněte na **Windows**.  
  
3.  V **šablony** podokně klikněte na tlačítko **formulářové aplikace Windows**.  
  
4.  V **název** zadejte **SprocOnlyApp**.  
  
5.  Click **OK**.  
  
     Otevře se Návrhář formulářů Windows.  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a>Přidávání do odkaz sestavení SQL LINQ  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Sestavení není součástí standardní šablona formulářové aplikace Windows. Budete muset přidat sestavení sami, jak je popsáno v následujících krocích:  
  
#### <a name="to-add-systemdatalinqdll"></a>To add System.Data.Linq.dll  
  
1.  V **Průzkumníku řešení**, klikněte na tlačítko **zobrazit všechny soubory**.  
  
2.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na **odkazy**a potom klikněte na **přidat odkaz na**.  
  
3.  V **přidat odkaz na** dialogové okno, klikněte na tlačítko **.NET**, klikněte na tlačítko System.Data.Linq sestavení a pak klikněte na tlačítko **OK**.  
  
     Je sestavení přidáno do projektu.  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Přidání souboru Northwind kódu do projektu  
 Tento krok předpokládá, že jste použili nástroj SqlMetal generování souboru kódu na základě ukázková databáze Northwind. Další informace najdete v části požadavky dříve v tomto návodu.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Přidání souboru northwind kódu do projektu  
  
1.  Na **projektu** nabídky, klikněte na tlačítko **přidat existující položku**.  
  
2.  V **přidat existující položku** přesunout do c:\linqtest3\northwind.vb dialogové okno a pak klikněte na tlačítko **přidat**.  
  
     Soubor northwind.vb je přidán do projektu.  
  
## <a name="creating-a-database-connection"></a>Vytvoření připojení k databázi  
 V tomto kroku definujete ukázková databáze Northwind připojení. Tento návod používá jako cestu "c:\linqtest3\northwnd.mdf".  
  
#### <a name="to-create-the-database-connection"></a>Chcete-li vytvořit připojení k databázi  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na **Form1.vb**a potom klikněte na **kód zobrazení**.  
  
     `Class Form1`Zobrazí se v editoru kódu.  
  
2.  Zadejte následující kód do `Form1` blok kódu:  
  
     [!code-vb[DLinqWalk4VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#1)]  
  
## <a name="setting-up-the-user-interface"></a>Nastavení uživatelského rozhraní  
 V této úloze vytvořit rozhraní tak, aby uživatelé mohou spouštět uložené procedury pro přístup k datům v databázi. V aplikaci, která vyvíjíte v tomto průvodci uživatelé můžou používat data v databázi jen pomocí uložené procedury vloženy do aplikace.  
  
#### <a name="to-set-up-the-user-interface"></a>Nastavení uživatelského rozhraní  
  
1.  Návrhář formulářů vraťte se do systému Windows (**Form1.vb[Design]**).  
  
2.  Na **zobrazení** nabídky, klikněte na tlačítko **sada nástrojů**.  
  
     Otevřete panel nástrojů.  
  
    > [!NOTE]
    >  Klikněte **autohide –** připínáček nechat otevřené sady nástrojů při provádění zbývající kroky v této části.  
  
3.  Přetáhněte dvě tlačítka, dvou textových polí a dva popisky z panelu nástrojů na **Form1**.  
  
     Uspořádání ovládacích prvků jako doprovodné obrázku. Rozbalte položku **Form1** tak, aby snadno umístit ovládací prvky.  
  
4.  Klikněte pravým tlačítkem na **Label1**a potom klikněte na **vlastnosti**.  
  
5.  Změna **Text** vlastnost z **Label1** k **zadejte OrderID:**.  
  
6.  Stejným způsobem pro **Label2**, změnit **Text** vlastnost z **Label2** k **zadejte CustomerID:**.  
  
7.  Stejným způsobem, změnit **Text** vlastnost pro **Button1** k **pořadí podrobnosti**.  
  
8.  Změna **Text** vlastnost pro **Button2** k **historie objednávek**.  
  
     Ovládací prvky tlačítek rozšíříte tak, aby veškerý text.  
  
#### <a name="to-handle-button-clicks"></a>Pro zpracování kliknutí na tlačítko  
  
1.  Klikněte dvakrát na **pořadí podrobnosti** na **Form1** vytvořit `Button1` obslužné rutiny události a otevřete editor kódu.  
  
2.  Zadejte následující kód do `Button1` obslužné rutiny:  
  
     [!code-vb[DLinqWalk4VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#2)]  
  
3.  Nyní klikněte dvakrát na **Button2** na Form1 vytvořit `Button2` obslužné rutiny události a otevřete editor kódu.  
  
4.  Zadejte následující kód do `Button2` obslužné rutiny:  
  
     [!code-vb[DLinqWalk4VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#3)]  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Nyní je čas k testování aplikace. Všimněte si, že vaše kontaktu s úložišti dat je omezená na libovolné akce může trvat dvě uložené procedury. Tyto akce jsou vrátit produkty, které jsou zahrnuté pro všechny orderID, které zadáte, nebo pro návrat historii produktů seřazených pro všechny CustomerID zadáte.  
  
#### <a name="to-test-the-application"></a>Testování aplikace  
  
1.  Stisknutím klávesy F5 spusťte ladění.  
  
     Zobrazí se Form1.  
  
2.  V **zadejte OrderID** zadejte **10249** a pak klikněte na **pořadí podrobnosti**.  
  
     Okno se zprávou seznamy produktů, zahrnuté v pořadí 10249.  
  
     Klikněte na tlačítko **OK** zavřete okno se zprávou.  
  
3.  V **zadejte CustomerID** zadejte `ALFKI`a potom klikněte na **historie objednávek**.  
  
     Okno se zprávou uvádí historie objednávek pro zákazníka ALFKI.  
  
     Klikněte na tlačítko **OK** zavřete okno se zprávou.  
  
4.  V **zadejte OrderID** zadejte `123`a potom klikněte na **pořadí podrobnosti**.  
  
     Zobrazí okno se zprávou "Žádné výsledky."  
  
     Klikněte na tlačítko **OK** zavřete okno se zprávou.  
  
5.  Na **ladění** nabídky, klikněte na tlačítko **Zastavte ladění**.  
  
     Zavře relaci ladění.  
  
6.  Pokud dokončíte experimentování, můžete kliknout na **zavřít projekt** na **souboru** nabídce a po zobrazení výzvy uložte projekt.  
  
## <a name="next-steps"></a>Další kroky  
 Tento projekt můžete zvýšit tak, že některé změny. Můžete například seznam dostupných uložené procedury v seznamu a mít uživatele, vyberte který postup provést. Výstup sestavy do textového souboru může také datového proudu.  
  
## <a name="see-also"></a>Viz také  
 [Učení podle návodů](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [Uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
