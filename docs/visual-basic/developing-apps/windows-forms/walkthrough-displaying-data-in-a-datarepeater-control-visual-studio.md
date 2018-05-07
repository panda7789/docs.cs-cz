---
title: 'Návod: Zobrazení dat v ovládacím prvku DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, walkthrough
ms.assetid: 65dcdb95-6c3e-47cc-987d-190000f71653
ms.openlocfilehash: d02668303f61f6a22f99bd7c86c41c9c139a716f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-displaying-data-in-a-datarepeater-control-visual-studio"></a>Návod: Zobrazení dat v ovládacím prvku DataRepeater (Visual Studio)
Tento názorný postup obsahuje základní scénář zahájení dokončení pro zobrazení vázaných dat v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
## <a name="prerequisite"></a>Předpoklad  
 Tento postup vyžaduje ukázková databáze Northwind.  
  
 Pokud jste tuto databázi ve svém vývojovém počítači, si můžete stáhnout z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088). Pokyny najdete v tématu [stažení ukázkové databáze](../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
## <a name="overview"></a>Přehled  
 První část tohoto návodu se skládá z čtyři hlavní úkoly:  
  
-   Vytvoření řešení.  
  
-   Přidání <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
-   Přidání zdroje dat.  
  
-   Přidání ovládacích prvků vázaných na data.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datarepeater-solution"></a>Vytváření řešení DataRepeater  
 V prvním kroku vytvořte projekt a řešení.  
  
#### <a name="to-create-a-datarepeater-solution"></a>Chcete-li vytvořit řešení DataRepeater  
  
1.  V sadě Visual Studio **soubor** nabídky, klikněte na tlačítko **nový projekt**.  
  
2.  V **typy projektů** v podokně **nový projekt** dialogové okno, rozbalte seznam **jazyka Visual Basic**a potom klikněte na **Windows**.  
  
3.  V **šablony** podokně klikněte na tlačítko **formulářové aplikace Windows**.  
  
4.  V **název** zadejte `DataRepeaterApp`.  
  
5.  Click **OK**.  
  
     Otevře se Návrhář formulářů Windows.  
  
6.  Vyberte formuláře v Návrháři formulářů Windows. V **vlastnosti** nastavte **velikost** vlastnost `800, 700`.  
  
## <a name="adding-a-datarepeater-control"></a>Přidání ovládacího prvku DataRepeater  
 V tomto kroku přidáte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku do formuláře.  
  
#### <a name="to-add-a-datarepeater-control"></a>Přidání ovládacího prvku DataRepeater  
  
1.  Na **zobrazení** nabídky, klikněte na tlačítko **sada nástrojů**.  
  
     **Sada nástrojů** otevře.  
  
2.  Vyberte **PowerPacks jazyka Visual Basic** kartě.  
  
3.  Přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> na ovládací prvek **Form1**.  
  
4.  V okně vlastnosti nastavit **umístění** vlastnost `0, 25`.  
  
5.  Nastavte **velikost** vlastnost `460, 600`.  
  
## <a name="adding-a-data-source"></a>Přidání zdroje dat  
 V tomto kroku přidáte zdroj dat pro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
#### <a name="to-add-a-data-source"></a>Chcete-li přidat zdroje dat  
  
1.  Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.  
  
2.  V **zdroje dat** okně klikněte na tlačítko **přidat nový zdroj dat**.  
  
3.  Vyberte **databáze** na **zvolte typ zdroje dat** a pak klikněte na tlačítko **Další**.  
  
4.  Na **vybrat datové připojení** proveďte některý z následujících kroků:  
  
    -   Pokud je k dispozici v rozevíracím seznamu připojení dat k ukázková databáze Northwind, klikněte na něj.  
  
         -nebo-  
  
    -   Klikněte na tlačítko **nové připojení** konfigurace nové datové připojení. Další informace najdete v tématu [přidat nová připojení](/visualstudio/data-tools/add-new-connections).  
  
5.  Pokud databáze vyžaduje heslo, vyberte možnost obsahují citlivá data, a pak klikněte na **Další**.  
  
    > [!NOTE]
    >  Pokud se zobrazí dialogové okno, klikněte na tlačítko **Ano** k uložení souboru do projektu.  
  
6.  Klikněte na tlačítko **Další** na **uložit připojovací řetězec do konfiguračního souboru aplikace** stránky.  
  
7.  Rozbalte **tabulky** uzlu **zvolte si databázové objekty** stránky.  
  
8.  Zaškrtněte políčka vedle **zákazníci** a **objednávky** tabulky a pak klikněte na tlačítko **Dokončit**.  
  
     **NorthwindDataSet** se přidá do projektu a **zákazníci** a **objednávky** tabulky se zobrazí v **zdroje dat** okno.  
  
## <a name="adding-data-bound-controls"></a>Přidání ovládacích prvků vázaných na Data  
 V tomto kroku přidáte ovládací prvky vázané na data na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
#### <a name="to-add-data-bound-controls"></a>Přidání ovládacích prvků vázaných na data  
  
1.  V **zdroje dat** okně vyberte nejvyšší uzel **zákazníci** tabulky.  
  
2.  Změňte typ tabulky na **podrobnosti** kliknutím **podrobnosti** v rozevíracím seznamu na uzlu tabulky.  
  
3.  Vyberte **zákazníci** tabulky uzel a přetáhněte ji na oblast šablony položky (horní oblasti) z <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
     A <xref:System.Windows.Forms.BindingNavigator> ovládací prvek přidán do formuláře a **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**,  **TableAdapterManager**, a **CustomersBindingNavigator** součásti jsou přidány do komponent.  
  
4.  Vyberte všechny pole a jejich přidružené popisky a umístit je téměř je levý okraj oblast šablony položky.  
  
5.  Vyberte pole, posledních pět (**oblast**, **PSČ**, **země**, **Phone**, a **Fax**) a jejich přidružené popisky a přesuňte je v provozu a napravo od pole prvních šesti.  
  
6.  Vyberte šablony položky (horní oblast ovládacího prvku).  
  
7.  V okně vlastnosti nastavit **velikost** vlastnost `427, 170`.  
  
 V tuto chvíli máte funkční aplikaci, která se zobrazí seznam opakovaných zákazníků. Můžete stisknutím klávesy F5 aplikaci spustit, změnit data a přidat nebo odstranit záznamy o zákaznících.  
  
 V dalším volitelným krokům, se dozvíte, jak přizpůsobit <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
## <a name="next-steps-optional"></a>Další kroky (volitelné)  
 Tato část průvodce se skládá ze čtyř volitelné úkoly:  
  
-   Změna vzhledu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
-   Zabránění uživatelům v přidávání nebo odstraňování záznamů.  
  
-   Přidání schopností vyhledávání do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
-   Přidávání seznamu a podrobností tabulka, která se <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
## <a name="changing-the-appearance-of-the-datarepeater-control"></a>Změna vzhledu ovládacího prvku DataRepeater  
 V tomto kroku volitelné změníte `BackColor` z <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku v době návrhu. Je také přidat kód pro zobrazení řádek v střídavých barvy a při změně štítku na `ForeColor` podmíněně.  
  
#### <a name="to-change-the-appearance-of-the-control"></a>Změna vzhledu ovládacího prvku  
  
1.  V Návrháři formulářů vyberte oblast hlavní (dolního) <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
2.  V okně vlastnosti nastavit `BackColor` vlastnosti prázdné.  
  
3.  Dvakrát klikněte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> otevření editoru kódu.  
  
4.  V editoru kódu, události rozevíracího seznamu, klikněte na tlačítko **DrawItem**.  
  
5.  V <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> obslužné rutiny události, přidejte následující kód do alternativní `BackColor`:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]  
  
6.  V <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> obslužné rutiny události, přidejte následující kód, chcete-li změnit `ForeColor` popisku v závislosti na podmínce:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]  
  
7.  Stisknutím klávesy F5 spusťte aplikaci a zobrazit individuální nastavení.  
  
## <a name="preventing-users-from-adding-or-deleting-records"></a>Zabránění uživatelům v přidávání nebo odstraňování záznamů  
 V tomto kroku volitelné přidáte kód, který zabrání uživatelům v přidávání nebo odstraňování záznamů <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
#### <a name="to-prevent-users-from-adding-and-deleting-records"></a>Chcete-li zabránit uživatelům v přidávání a odstraňování záznamů  
  
1.  V Návrháři formulářů poklepejte na formulář pro otevření editoru kódu.  
  
2.  Přidejte následující kód, který `Form_Load` událostí:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]  
  
3.  V rozevíracím seznamu název třídy, klikněte na **BindingNavigatorDeleteItem**. V rozevíracím seznamu název metody, klikněte na **EnabledChanged**.  
  
4.  Přidejte následující kód, který `BindingNavigatorDeleteItem_EnabledChanged` obslužné rutiny události:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]  
  
    > [!NOTE]
    >  Tento krok je nezbytný, protože <xref:System.Windows.Forms.BindingSource> povolí **DeleteItem** tlačítko pokaždé, když se změní na aktuální záznam.  
  
5.  Stisknutím klávesy F5 spusťte aplikaci. Všimněte si, že **DeleteItem** tlačítko k dispozici a nelze odstranit položky po stisknutí klávesy odstranit.  
  
## <a name="adding-search-capability-to-the-datarepeater-control"></a>Přidání schopností vyhledávání do ovládacího prvku DataRepeater  
 V tomto volitelné kroku implementujete schopnost vyhledejte hodnotu v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Pokud se řetězec najde, ovládacího prvku vybere položku, která obsahuje hodnotu a posune položky do zobrazení.  
  
#### <a name="to-add-search-capability"></a>Přidání schopností vyhledávání  
  
1.  Přetažení <xref:System.Windows.Forms.TextBox> řídit z **sada nástrojů** do formuláře, který obsahuje <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
     Umístěte ho <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
2.  V okně vlastností změňte **název** vlastnost **SearchTextBox**.  
  
3.  Přetažení <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** do formuláře, který obsahuje <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Umístěte ho <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
4.  V okně vlastností změňte **název** vlastnost **SearchButton**. Změna **Text** vlastnost **vyhledávání**.  
  
5.  Dvakrát klikněte <xref:System.Windows.Forms.Button> řídit k otevření editoru kódu a přidejte následující kód do `SearchButton_Click` obslužné rutiny události.  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]  
  
6.  Stisknutím klávesy F5 spusťte aplikaci. Zadejte ID zákazníka v **SearchTextBox** a klikněte na **vyhledávání** tlačítko.  
  
## <a name="adding-a-master-and-detail-table-to-the-datarepeater"></a>Přidávání do DataRepeater hlavní a tabulka podrobností  
 V tomto kroku volitelné přidejte druhý <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řízení k zobrazení související objednávky pro každého zákazníka.  
  
#### <a name="to-add-a-master-and-detail-table"></a>Chcete-li přidat tabulku seznamu a podrobností  
  
1.  Přetáhněte druhý <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řídit z **PowerPacks jazyka Visual Basic** ve **sada nástrojů** do formuláře.  
  
2.  V okně vlastnosti nastavit **umístění** vlastnost `465, 25`.  
  
3.  Nastavte **velikost** vlastnost `315, 600`.  
  
4.  V **zdroje dat** okno, rozbalte **zákazníci** tabulky uzel a vyberte uzel podrobností pro **objednávky** tabulky.  
  
5.  Změňte typ tohoto **objednávky** tabulky Podrobnosti o kliknutím **podrobnosti** v rozevíracím seznamu na uzlu tabulky.  
  
6.  Přetáhněte to **objednávky** uzlu tabulky na oblast šablony položky (horní oblasti) druhého <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
     **OrdersBindingSource** součásti a **OrdersTableAdapter** součásti jsou přidány do komponent.  
  
7.  Stisknutím klávesy F5 spusťte aplikaci. Když vyberete každého zákazníka v prvním <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řídit, objednávky tohoto zákazníka jsou zobrazeny ve druhém <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Postupy: Zobrazení vázaných dat v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Postupy: Zobrazení nevázaných ovládacích prvků v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [Postupy: Změna rozložení ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [Postupy: Zobrazení záhlaví položek v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)  
 [Postupy: Vyhledávání dat v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)  
 [Postupy: vytvoření hlavního a podrobného formuláře pomocí dvou ovládacích prvků DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [Postupy: Změna vzhledu ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [Postupy: Zákaz přidávání a odstraňování položek DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)  
 [Řešení potíží s ovládacím prvkem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
