---
title: 'Průvodce: Použití jen uložených procedur (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 5a736a30-ba66-4adb-b87c-57d19476e862
ms.openlocfilehash: 7c696d24dd84aee568706200389839dea080d7b4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577384"
---
# <a name="walkthrough-using-only-stored-procedures-visual-basic"></a>Průvodce: Použití jen uložených procedur (Visual Basic)
Tento názorný postup obsahuje základní začátku do konce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář pro přístup k datům pomocí uložených procedur komponentami TableAdapter pouze. Tento přístup se často používá ve správci databází a omezit způsob přístupu k úložišti dat.  
  
> [!NOTE]
>  Můžete také použít uložené procedury v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacím přepsat výchozí chování, zejména u `Create`, `Update`, a `Delete` procesy. Další informace najdete v tématu [přizpůsobení Insert, Update a operace odstranění](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
  
 Pro účely tohoto názorného postupu budete používat dvě metody, které byly namapovány na uložené procedury v ukázkové databázi Northwind: CustOrdersDetail a CustOrderHist. Mapování nastane, když spustíte nástroj příkazového řádku SqlMetal generuje soubor jazyka Visual Basic. Další informace najdete v části požadavky později v tomto názorném postupu.  
  
 Tento názorný postup nevyžaduje [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]. Vývojáři, kteří používají Visual Studio můžete také použít [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] k implementaci funkcionality uloženou proceduru. Zobrazit [LINQ to SQL nástroje v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Tento návod byl napsán s použitím vývojového nastavení jazyka Visual Basic.  
  
## <a name="prerequisites"></a>Požadavky  
 Tento postup vyžaduje následující:  
  
-   Tento návod používá vyhrazené složky ("c:\linqtest3") pro uložení souborů. Vytvoření této složky, před zahájením návodu.  
  
-   Ukázkovou databázi Northwind  
  
     Pokud tuto databázi na vašem vývojovém počítači nemáte, můžete si ho stáhnout z webu Microsoft download. Pokyny najdete v tématu [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Po stažení databáze, zkopírujte do složky c:\linqtest3 northwnd.mdf souboru.  
  
-   Soubor kódu jazyka Visual Basic generují z databáze Northwind.  
  
     Tento návod byl napsán s použitím nástroje SqlMetal s následujícím příkazovým řádkem:  
  
     **SqlMetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions / pluralize**  
  
     Další informace najdete v tématu [SqlMetal.exe (nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Přehled  
 Tento názorný postup se skládá z šesti hlavních úloh:  
  
-   Nastavení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] řešení v sadě Visual Studio.  
  
-   Přidání System.Data.Linq sestavení do projektu.  
  
-   Přidání kódu databázový soubor do projektu.  
  
-   Vytvoření připojení k databázi.  
  
-   Nastavení uživatelského rozhraní.  
  
-   Spuštění a testování aplikace.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Vytvoření LINQ to SQL řešení  
 V této první úloze vytvoříte řešení sady Visual Studio, který obsahuje potřebné odkazy na sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>K vytvoření LINQ to SQL řešení  
  
1.  V sadě Visual Studio **souboru** nabídky, klikněte na tlačítko **nový projekt**.  
  
2.  V **typy projektů** v podokně **nový projekt** dialogového okna rozbalte **jazyka Visual Basic**a potom klikněte na tlačítko **Windows**.  
  
3.  V **šablony** podokně klikněte na tlačítko **formulářová aplikace Windows**.  
  
4.  V **název** zadejte **SprocOnlyApp**.  
  
5.  Klikněte na **OK**.  
  
     Otevře se Návrhář formulářů Windows.  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a>Přidání LINQ na odkaz na sestavení SQL  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Sestavení není součástí standardní šablony aplikace Windows Forms. Budete muset přidat sestavení sami, jak je popsáno v následujících krocích:  
  
#### <a name="to-add-systemdatalinqdll"></a>To add System.Data.Linq.dll  
  
1.  V **Průzkumníka řešení**, klikněte na tlačítko **zobrazit všechny soubory**.  
  
2.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy**a potom klikněte na tlačítko **přidat odkaz**.  
  
3.  V **přidat odkaz** dialogové okno, klikněte na tlačítko **.NET**, klikněte na tlačítko System.Data.Linq sestavení a klikněte na **OK**.  
  
     Sestavení se přidá do projektu.  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Přidání souboru Northwind kódu do projektu  
 Tento krok předpokládá, že jste použili nástroj SqlMetal ke generování souboru kódu z ukázkové databáze Northwind. Další informace najdete v oddílu požadavky dříve v tomto návodu.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Chcete-li přidat soubor kódu northwind do projektu  
  
1.  Na **projektu** nabídky, klikněte na tlačítko **přidat existující položku**.  
  
2.  V **přidat existující položku** dialogové okno, přesunout do c:\linqtest3\northwind.vb a potom klikněte na tlačítko **přidat**.  
  
     Soubor northwind.vb je přidán do projektu.  
  
## <a name="creating-a-database-connection"></a>Vytváří se připojení k databázi  
 V tomto kroku definujete připojení k ukázkové databázi Northwind. Tento návod používá jako cestu "c:\linqtest3\northwnd.mdf".  
  
#### <a name="to-create-the-database-connection"></a>Chcete-li vytvořit připojení k databázi  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **Form1.vb**a potom klikněte na tlačítko **zobrazit kód**.  
  
     `Class Form1` Zobrazí se v editoru kódu.  
  
2.  Zadejte následující kód do `Form1` blok kódu:  
  
     [!code-vb[DLinqWalk4VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#1)]  
  
## <a name="setting-up-the-user-interface"></a>Nastavení uživatelského rozhraní  
 V této úloze vytvoříte rozhraní tak, aby uživatelé můžou spouštět uložené procedury pro přístup k datům v databázi. V aplikaci, kterou vyvíjíte s tímto názorným postupem můžou uživatelé k datům v databázi pouze pomocí uložených procedur, které jsou vloženy do aplikace.  
  
#### <a name="to-set-up-the-user-interface"></a>Nastavení uživatelského rozhraní  
  
1.  Vraťte se Windows Forms Designer (**Form1.vb[Design]**).  
  
2.  Na **zobrazení** nabídky, klikněte na tlačítko **nástrojů**.  
  
     Otevře se panel nástrojů.  
  
    > [!NOTE]
    >  Klikněte na tlačítko **automatické skrývání** připínáčku nechat otevřené sady nástrojů, zatímco provádíte zbývající kroky v této části.  
  
3.  Přetáhněte z panelu nástrojů na dvě tlačítka, dvě textová pole a dva popisky **Form1**.  
  
     Uspořádání ovládacích prvků jako doprovodné ilustrace. Rozbalte **Form1** tak, aby snadno umístit ovládací prvky.  
  
4.  Klikněte pravým tlačítkem na **Label1**a potom klikněte na tlačítko **vlastnosti**.  
  
5.  Změnit **Text** vlastnost z **Label1** k **zadejte OrderID:**.  
  
6.  Stejně jako u **Label2**, změnit **Text** vlastnost z **Label2** k **zadejte ID zákazníka:**.  
  
7.  Stejným způsobem, změnit **Text** vlastnost **Button1** k **OrderDetails**.  
  
8.  Změnit **Text** vlastnost **Button2** k **historie objednávek**.  
  
     Ovládací prvky tlačítka rozšíříte tak, aby veškerý text.  
  
#### <a name="to-handle-button-clicks"></a>Pro zpracování kliknutí na tlačítko  
  
1.  Dvakrát klikněte na panel **OrderDetails** na **Form1** vytvořit `Button1` obslužná rutina události a otevřete editor kódu.  
  
2.  Zadejte následující kód do `Button1` obslužné rutiny:  
  
     [!code-vb[DLinqWalk4VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#2)]  
  
3.  Teď klikněte dvakrát na **Button2** na Form1 vytvořit `Button2` obslužná rutina události a otevřete editor kódu.  
  
4.  Zadejte následující kód do `Button2` obslužné rutiny:  
  
     [!code-vb[DLinqWalk4VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#3)]  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Nyní je čas k testování aplikace. Všimněte si, že váš kontakt s úložišti dat je omezená na libovolné akce může trvat dvě uložené procedury. Tyto akce jsou vrátit produkty zahrnuté pro všechny orderID, které zadáte, nebo vrátit historie produktů seřazených pro jakékoli CustomerID zadáte.  
  
#### <a name="to-test-the-application"></a>Testování aplikace  
  
1.  Stisknutím klávesy F5 spusťte ladění.  
  
     Form1 se zobrazí.  
  
2.  V **zadejte OrderID** zadejte **10249** a potom klikněte na tlačítko **OrderDetails**.  
  
     Okno se zprávou zobrazí seznam produktům zahrnutým v pořadí 10249.  
  
     Klikněte na tlačítko **OK** zavřete okno se zprávou.  
  
3.  V **zadejte CustomerID** zadejte `ALFKI`a potom klikněte na tlačítko **historie objednávek**.  
  
     Okno se zprávou zobrazí seznam historie objednávek pro zákazníka ALFKI.  
  
     Klikněte na tlačítko **OK** zavřete okno se zprávou.  
  
4.  V **zadejte OrderID** zadejte `123`a potom klikněte na tlačítko **OrderDetails**.  
  
     Zobrazí okno se zprávou "Žádné výsledky."  
  
     Klikněte na tlačítko **OK** zavřete okno se zprávou.  
  
5.  Na **ladění** nabídky, klikněte na tlačítko **Zastavit ladění**.  
  
     Ukončí relaci ladění.  
  
6.  Pokud jste dokončili, experimentování, můžete kliknout na **zavřít projekt** na **souboru** nabídky a po zobrazení výzvy uložte projekt.  
  
## <a name="next-steps"></a>Další kroky  
 Tento projekt můžete vylepšit tím, že některé změny. Můžete například seznam dostupných uložené procedury v seznamu a mít uživatele, který postup ke spuštění vyberte. Může také datový proud výstupu sestavy do textového souboru.  
  
## <a name="see-also"></a>Viz také:
- [Učení podle návodů](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [Uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
