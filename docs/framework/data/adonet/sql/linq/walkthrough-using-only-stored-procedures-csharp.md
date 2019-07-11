---
title: 'Návod: Použití jen uložených procedur (C#)'
ms.date: 03/30/2017
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
ms.openlocfilehash: f16cbdc1d22e7ec08237c0f13db9499ee2f9194f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742548"
---
# <a name="walkthrough-using-only-stored-procedures-c"></a>Návod: Použití jen uložených procedur (C#)
Tento názorný postup obsahuje základní začátku do konce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář pro přístup k datům spuštěním uložené procedury pouze. Tento přístup se často používá ve správci databází a omezit způsob přístupu k úložišti dat.  
  
> [!NOTE]
>  Můžete také použít uložené procedury v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacím přepsat výchozí chování, zejména u `Create`, `Update`, a `Delete` procesy. Další informace najdete v tématu [přizpůsobení Insert, Update a operace odstranění](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
  
 Pro účely tohoto názorného postupu budete používat dvě metody, které byly namapovány na uložené procedury v ukázkové databázi Northwind: CustOrdersDetail a CustOrderHist. Mapování nastane, když spustíte nástroj příkazového řádku SqlMetal k vygenerování C# souboru. Další informace najdete v části požadavky později v tomto názorném postupu.  
  
 Tento názorný postup nevyžaduje Návrhář relací objektů. Vývojáři, kteří používají Visual Studio můžete také O/R Designer k implementaci funkcionality uloženou proceduru. Zobrazit [LINQ to SQL nástroje v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Tento návod byl napsán s použitím Visual C# vývojovým nastavením.  
  
## <a name="prerequisites"></a>Požadavky  
 Tento postup vyžaduje následující:  
  
- Tento návod používá vyhrazené složky ("c:\linqtest7") pro uložení souborů. Vytvoření této složky, před zahájením návodu.  
  
- Ukázkovou databázi Northwind  
  
     Pokud tuto databázi na vašem vývojovém počítači nemáte, můžete si ho stáhnout z webu Microsoft download. Pokyny najdete v tématu [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Po stažení databáze, zkopírujte do složky c:\linqtest7 northwnd.mdf souboru.  
  
- A C# soubor kód generovaný z databáze Northwind.  
  
     Tento návod byl napsán s použitím nástroje SqlMetal s následujícím příkazovým řádkem:  
  
     **SqlMetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions / pluralize**  
  
     Další informace najdete v tématu [SqlMetal.exe (nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Přehled  
 Tento názorný postup se skládá z šesti hlavních úloh:  
  
- Nastavení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] řešení v sadě Visual Studio.  
  
- Přidání System.Data.Linq sestavení do projektu.  
  
- Přidání kódu databázový soubor do projektu.  
  
- Vytvoření připojení k databázi.  
  
- Nastavení uživatelského rozhraní.  
  
- Spuštění a testování aplikace.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Vytvoření LINQ to SQL řešení  
 V této první úloze vytvoříte řešení sady Visual Studio, který obsahuje potřebné odkazy na sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>K vytvoření LINQ to SQL řešení  
  
1. V sadě Visual Studio **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.  
  
2. V **typy projektů** v podokně **nový projekt** dialogové okno, klikněte na tlačítko **Visual C#** .  
  
3. V **šablony** podokně klikněte na tlačítko **formulářová aplikace Windows**.  
  
4. V **název** zadejte **SprocOnlyApp**.  
  
5. V **umístění** pole, ověřte, kam chcete uložit soubory projektu.  
  
6. Klikněte na **OK**.  
  
     Otevře se Návrhář formulářů Windows.  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a>Přidání LINQ na odkaz na sestavení SQL  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Sestavení není součástí standardní šablony aplikace Windows Forms. Budete muset přidat sestavení sami, jak je popsáno v následujících krocích:  
  
#### <a name="to-add-systemdatalinqdll"></a>To add System.Data.Linq.dll  
  
1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy**a potom klikněte na tlačítko **přidat odkaz**.  
  
2. V **přidat odkaz** dialogové okno, klikněte na tlačítko **.NET**, klikněte na tlačítko System.Data.Linq sestavení a klikněte na **OK**.  
  
     Sestavení se přidá do projektu.  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Přidání souboru Northwind kódu do projektu  
 Tento krok předpokládá, že jste použili nástroj SqlMetal ke generování souboru kódu z ukázkové databáze Northwind. Další informace najdete v oddílu požadavky dříve v tomto návodu.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Chcete-li přidat soubor kódu northwind do projektu  
  
1. Na **projektu** nabídky, klikněte na tlačítko **přidat existující položku**.  
  
2. V **přidat existující položku** dialogové okno, přesunout do c:\linqtest7\northwind.cs a potom klikněte na tlačítko **přidat**.  
  
     Soubor northwind.cs je přidán do projektu.  
  
## <a name="creating-a-database-connection"></a>Vytváří se připojení k databázi  
 V tomto kroku definujete připojení k ukázkové databázi Northwind. Tento návod používá jako cestu "c:\linqtest7\northwnd.mdf".  
  
#### <a name="to-create-the-database-connection"></a>Chcete-li vytvořit připojení k databázi  
  
1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **Form1.cs**a potom klikněte na tlačítko **zobrazit kód**.  
  
2. Zadejte následující kód do `Form1` třídy:  
  
     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]  
  
## <a name="setting-up-the-user-interface"></a>Nastavení uživatelského rozhraní  
 V této úloze nastavíte rozhraní tak, aby uživatelé můžou spouštět uložené procedury pro přístup k datům v databázi. V aplikacích, které vyvíjíte s tímto názorným postupem můžou uživatelé k datům v databázi pouze pomocí uložených procedur, které jsou vloženy do aplikace.  
  
#### <a name="to-set-up-the-user-interface"></a>Nastavení uživatelského rozhraní  
  
1. Vraťte se Windows Forms Designer (**Form1.cs[Design]** ).  
  
2. Na **zobrazení** nabídky, klikněte na tlačítko **nástrojů**.  
  
     Otevře se panel nástrojů.  
  
    > [!NOTE]
    >  Klikněte na tlačítko **automatické skrývání** připínáčku nechat otevřené sady nástrojů, zatímco provádíte zbývající kroky v této části.  
  
3. Přetáhněte z panelu nástrojů na dvě tlačítka, dvě textová pole a dva popisky **Form1**.  
  
     Uspořádání ovládacích prvků jako doprovodné ilustrace. Rozbalte **Form1** tak, aby snadno umístit ovládací prvky.  
  
4. Klikněte pravým tlačítkem na **label1**a potom klikněte na tlačítko **vlastnosti**.  
  
5. Změnit **Text** vlastnost z **label1** k **zadejte OrderID:** .  
  
6. Stejně jako u **label2**, změnit **Text** vlastnost z **label2** k **zadejte ID zákazníka:** .  
  
7. Stejným způsobem, změnit **Text** vlastnost **button1** k **OrderDetails**.  
  
8. Změnit **Text** vlastnost **button2** k **historie objednávek**.  
  
     Ovládací prvky tlačítka rozšíříte tak, aby veškerý text.  
  
#### <a name="to-handle-button-clicks"></a>Pro zpracování kliknutí na tlačítko  
  
1. Dvakrát klikněte na panel **OrderDetails** na **Form1** obslužná rutina události button1 otevřít v editoru kódu.  
  
2. Zadejte následující kód do `button1` obslužné rutiny:  
  
     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]  
  
3. Teď klikněte dvakrát na **button2** na **Form1** otevřít `button2` obslužné rutiny  
  
4. Zadejte následující kód do `button2` obslužné rutiny:  
  
     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Nyní je čas k testování aplikace. Všimněte si, že váš kontakt s úložišti dat je omezená na libovolné akce může trvat dvě uložené procedury. Tyto akce jsou vrátit produkty zahrnuté pro všechny orderID, které zadáte, nebo vrátit historie produktů seřazených pro jakékoli CustomerID zadáte.  
  
#### <a name="to-test-the-application"></a>Testování aplikace  
  
1. Stisknutím klávesy F5 spusťte ladění.  
  
     Form1 se zobrazí.  
  
2. V **zadejte OrderID** zadejte `10249`a potom klikněte na tlačítko **OrderDetails**.  
  
     Okno se zprávou zobrazí seznam produktům zahrnutým v pořadí 10249.  
  
     Klikněte na tlačítko **OK** zavřete okno se zprávou.  
  
3. V **zadejte CustomerID** zadejte `ALFKI`a potom klikněte na tlačítko **historie objednávek**.  
  
     Zobrazí se okno se zprávou, která obsahuje seznam historie objednávek pro zákazníka ALFKI.  
  
     Klikněte na tlačítko **OK** zavřete okno se zprávou.  
  
4. V **zadejte OrderID** zadejte `123`a potom klikněte na tlačítko **OrderDetails**.  
  
     Zobrazí se okno se zprávou, která se zobrazí "Žádné výsledky."  
  
     Klikněte na tlačítko **OK** zavřete okno se zprávou.  
  
5. Na **ladění** nabídky, klikněte na tlačítko **Zastavit ladění**.  
  
     Ukončí relaci ladění.  
  
6. Pokud jste dokončili, experimentování, můžete kliknout na **zavřít projekt** na **souboru** nabídky a po zobrazení výzvy uložte projekt.  
  
## <a name="next-steps"></a>Další kroky  
 Tento projekt můžete vylepšit tím, že některé změny. Můžete například seznam dostupných uložené procedury v seznamu a mít uživatele, který postup ke spuštění vyberte. Může také datový proud výstupu sestavy do textového souboru.  
  
## <a name="see-also"></a>Viz také:

- [Učení podle návodů](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [Uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
