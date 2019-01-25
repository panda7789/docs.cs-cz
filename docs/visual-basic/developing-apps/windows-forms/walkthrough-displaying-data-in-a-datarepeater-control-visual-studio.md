---
title: 'Průvodce: Zobrazení dat v ovládacím prvku DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, walkthrough
ms.assetid: 65dcdb95-6c3e-47cc-987d-190000f71653
ms.openlocfilehash: 4153fecaecc80fc4c40fb6dd9026b07c49ec0fb7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729246"
---
# <a name="walkthrough-displaying-data-in-a-datarepeater-control-visual-studio"></a>Průvodce: Zobrazení dat v ovládacím prvku DataRepeater (Visual Studio)
Tento názorný postup obsahuje základní zahájení dokončení scénář pro zobrazení vázaných dat v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
## <a name="prerequisite"></a>Předpoklad  
 Tento návod vyžaduje ukázkové databáze Northwind.  
  
 Pokud tuto databázi na vašem vývojovém počítači nemáte, můžete si ho stáhnout z webu Microsoft Download Center. Pokyny najdete v tématu [Downloading Sample Databases](../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
## <a name="overview"></a>Přehled  
 První část tohoto návodu skládá ze čtyř hlavních úloh:  
  
-   Vytvoření řešení.  
  
-   Přidání <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
-   Přidání zdroje dat.  
  
-   Přidání ovládacích prvků vázaných na data.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datarepeater-solution"></a>Vytvoření řešení DataRepeater  
 V prvním kroku vytvoříte projekt a řešení.  
  
#### <a name="to-create-a-datarepeater-solution"></a>Chcete-li vytvořit řešení DataRepeater  
  
1.  V sadě Visual Studio **souboru** nabídky, klikněte na tlačítko **nový projekt**.  
  
2.  V **typy projektů** v podokně **nový projekt** dialogového okna rozbalte **jazyka Visual Basic**a potom klikněte na tlačítko **Windows**.  
  
3.  V **šablony** podokně klikněte na tlačítko **formulářová aplikace Windows**.  
  
4.  V **název** zadejte `DataRepeaterApp`.  
  
5.  Klikněte na **OK**.  
  
     Otevře se Návrhář formulářů Windows.  
  
6.  Vyberte formulář v Návrháři formulářů Windows. V **vlastnosti** okno, nastaveno **velikost** vlastnost `800, 700`.  
  
## <a name="adding-a-datarepeater-control"></a>Přidání ovládacího prvku DataRepeater  
 V tomto kroku přidáte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku na formuláři.  
  
#### <a name="to-add-a-datarepeater-control"></a>Přidání ovládacího prvku DataRepeater  
  
1.  Na **zobrazení** nabídky, klikněte na tlačítko **nástrojů**.  
  
     **Nástrojů** otevře.  
  
2.  Vyberte **sady Visual Basic PowerPack** kartu.  
  
3.  Přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> na ovládací prvek **Form1**.  
  
4.  V okně Vlastnosti nastavte **umístění** vlastnost `0, 25`.  
  
5.  Nastavte **velikost** vlastnost `460, 600`.  
  
## <a name="adding-a-data-source"></a>Přidání zdroje dat  
 V tomto kroku přidáte zdroj dat pro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
#### <a name="to-add-a-data-source"></a>Chcete-li přidat zdroj dat  
  
1.  Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.  
  
2.  V **zdroje dat** okna, klikněte na tlačítko **přidat nový zdroj dat**.  
  
3.  Vyberte **databáze** na **zvolte typ zdroje dat** stránce a potom klikněte na tlačítko **Další**.  
  
4.  Na **vyberte datové připojení** stránce, proveďte jednu z následujících kroků:  
  
    -   Pokud připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, klikněte na něj.  
  
         -nebo-  
  
    -   Klikněte na tlačítko **nové připojení** konfigurace nové datové připojení. Další informace najdete v tématu [přidat nové připojení](/visualstudio/data-tools/add-new-connections).  
  
5.  Pokud databáze vyžaduje heslo, vyberte možnost zahrnutí důvěrných osobních údajů a pak klikněte na tlačítko **Další**.  
  
    > [!NOTE]
    >  Pokud se zobrazí dialogové okno, klikněte na tlačítko **Ano** k uložení souboru do projektu.  
  
6.  Klikněte na tlačítko **Další** na **uložit připojovací řetězec do konfiguračního souboru aplikace** stránky.  
  
7.  Rozbalte **tabulky** uzlu **zvolte vaše databázové objekty** stránky.  
  
8.  Zaškrtněte políčka vedle položky **zákazníkům** a **objednávky** tabulky a pak klikněte na tlačítko **Dokončit**.  
  
     **NorthwindDataSet** se přidá do vašeho projektu a **zákazníkům** a **objednávky** tabulky se zobrazí v **zdroje dat** okna.  
  
## <a name="adding-data-bound-controls"></a>Přidání ovládacích prvků vázaných na Data  
 V tomto kroku přidáte ovládací prvky vázané na data <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
#### <a name="to-add-data-bound-controls"></a>Přidání ovládacích prvků vázaných na data  
  
1.  V **zdroje dat** okno, vyberte uzel nejvyšší úrovně **zákazníkům** tabulky.  
  
2.  Změňte typ přetažení tabulky **podrobnosti** kliknutím **podrobnosti** v rozevíracím seznamu na uzel tabulky.  
  
3.  Vyberte **zákazníkům** tabulky uzlu a přetáhněte ji na šablonu oblast položky (horní oblasti) <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
     A <xref:System.Windows.Forms.BindingNavigator> ovládací prvek je přidán do formuláře a **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**,  **TableAdapterManager**, a **CustomersBindingNavigator** součásti jsou přidány do panelu komponent.  
  
4.  Vyberte všechny pole a jejich přidružené popisky a umístit je u levého okraje oblasti šablony položek.  
  
5.  Vyberte posledních pět polí (**oblasti**, **PSČ**, **země**, **Phone**, a **Fax**) a jejich přidružené popisky a je přesunout nahoru a napravo od prvních šest polí.  
  
6.  Vyberte šablonu položky (horní oblasti ovládacího prvku).  
  
7.  V okně Vlastnosti nastavte **velikost** vlastnost `427, 170`.  
  
 V tomto okamžiku máte funkční aplikaci, která se zobrazí s opakováním seznam zákazníků. Stisknutím klávesy F5 spusťte aplikaci, změnit data a přidat nebo odstranit záznamy o zákaznících.  
  
 V dalším volitelným krokům, se dozvíte, jak přizpůsobit <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
## <a name="next-steps-optional"></a>Další kroky (volitelné)  
 Tato část návodu se skládá ze čtyř volitelné kroky:  
  
-   Změna vzhledu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
-   Zabránění uživatelům v přidávání nebo odstraňování záznamů.  
  
-   Přidání schopností vyhledávání do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
-   Přidat tabulku do seznamu a podrobností <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
## <a name="changing-the-appearance-of-the-datarepeater-control"></a>Změna vzhledu ovládacího prvku DataRepeater  
 V tomto volitelný krok, můžete změnit `BackColor` z <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek v době návrhu. Je také přidat kód k zobrazení řádků v střídavých barvy a změnit popisku `ForeColor` podmíněně.  
  
#### <a name="to-change-the-appearance-of-the-control"></a>Chcete-li změnit vzhled ovládacího prvku  
  
1.  V Návrháři formulářů Windows vyberte hlavní oblast (nižší) <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
2.  V okně Vlastnosti nastavte `BackColor` vlastnost na bílou.  
  
3.  Dvakrát klikněte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> otevřete Editor kódu.  
  
4.  V editoru kódu, v případě rozevíracího seznamu, klikněte na tlačítko **DrawItem**.  
  
5.  V <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> obslužná rutina události, přidejte následující kód do alternativní `BackColor`:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]  
  
6.  V <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> obslužná rutina události, přidejte následující kód pro změnu `ForeColor` popisku v závislosti na podmínku:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]  
  
7.  Stisknutím klávesy F5 spusťte aplikaci a zobrazit vlastní nastavení.  
  
## <a name="preventing-users-from-adding-or-deleting-records"></a>Zabránění uživatelům v přidávání nebo odstraňování záznamů  
 V tomto volitelném kroku přidáte kód, který zabrání uživatelům v přidávání nebo odstraňování záznamů v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
#### <a name="to-prevent-users-from-adding-and-deleting-records"></a>Chcete-li zabránit uživatelům v přidávání a odstraňování záznamů  
  
1.  V Návrháři formulářů Windows klikněte dvakrát na formuláři se otevřít Editor kódu.  
  
2.  Přidejte následující kód, který `Form_Load` události:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]  
  
3.  V rozevíracím seznamu názvu třídy, klikněte na tlačítko **BindingNavigatorDeleteItem**. V rozevíracím seznamu název metody, klikněte na tlačítko **EnabledChanged**.  
  
4.  Přidejte následující kód, který `BindingNavigatorDeleteItem_EnabledChanged` obslužné rutiny události:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]  
  
    > [!NOTE]
    >  Tento krok je nezbytný, protože <xref:System.Windows.Forms.BindingSource> vám umožní **DeleteItem** tlačítko pokaždé, když se změní aktuální záznam.  
  
5.  Stisknutím klávesy F5 spusťte aplikaci. Všimněte si, **DeleteItem** je tlačítko neaktivní a nelze odstranit položky, stisknutím klávesy DELETE.  
  
## <a name="adding-search-capability-to-the-datarepeater-control"></a>Přidání schopností vyhledávání do ovládacího prvku DataRepeater  
 V tomto kroku volitelné implementace umožňuje najít hodnotu v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Pokud se řetězec najde, vybere ovládací prvek položky, který obsahuje hodnotu a položce se posune do zobrazení.  
  
#### <a name="to-add-search-capability"></a>Můžete přidat možnosti vyhledávání  
  
1.  Přetáhněte <xref:System.Windows.Forms.TextBox> ovládacího prvku **nástrojů** do formuláře, který obsahuje <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
     Přesuňte ho pod <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
2.  V okně Vlastnosti změňte **název** vlastnost **SearchTextBox**.  
  
3.  Přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do formuláře, který obsahuje <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Přesuňte ho pod <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
4.  V okně Vlastnosti změňte **název** vlastnost **SearchButton**. Změnit **Text** vlastnost **hledání**.  
  
5.  Dvakrát klikněte <xref:System.Windows.Forms.Button> ovládací prvek, otevře se Editor kódu a přidejte následující kód, který `SearchButton_Click` obslužné rutiny události.  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]  
  
6.  Stisknutím klávesy F5 spusťte aplikaci. Zadejte ID zákazníka v **SearchTextBox** a klikněte na tlačítko **hledání** tlačítko.  
  
## <a name="adding-a-master-and-detail-table-to-the-datarepeater"></a>Přidání do ovládacího prvku DateRepeater. hlavní a tabulka podrobností  
 V tomto kroku volitelné přidejte druhý <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek zobrazí související objednávky pro každého zákazníka.  
  
#### <a name="to-add-a-master-and-detail-table"></a>Chcete-li přidat tabulku a podrobností  
  
1.  Přetáhněte druhý <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku **sady Visual Basic PowerPack** kartu **nástrojů** do formuláře.  
  
2.  V okně Vlastnosti nastavte **umístění** vlastnost `465, 25`.  
  
3.  Nastavte **velikost** vlastnost `315, 600`.  
  
4.  V **zdroje dat** okna, rozbalte **zákazníkům** tabulky uzlů a vyberte uzel podrobností pro **objednávky** tabulky.  
  
5.  Změňte typ přetažení tohoto objektu **objednávky** tabulky Podrobnosti kliknutím **podrobnosti** v rozevíracím seznamu na uzel tabulky.  
  
6.  Přetáhněte toto **objednávky** uzel tabulky na oblast šablony položky (horní oblasti) druhého <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
     **OrdersBindingSource** komponenty a **OrdersTableAdapter** součásti jsou přidány do panelu komponent.  
  
7.  Stisknutím klávesy F5 spusťte aplikaci. Když vyberete každého zákazníka v prvním <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řídit, objednávky daného zákazníka se zobrazí v druhé <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
## <a name="see-also"></a>Viz také:
- [Úvod do ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [Postupy: Zobrazení vázaných dat v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)
- [Postupy: Zobrazení nevázaných ovládacích prvků v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)
- [Postupy: Změna rozložení ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)
- [Postupy: Zobrazení položek záhlaví v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)
- [Postupy: Vyhledávání dat v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)
- [Postupy: Vytvoření hlavního/podrobného formuláře pomocí dvou ovládacích prvků DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
- [Postupy: Změna vzhledu ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
- [Postupy: Zákaz přidávání a odstraňování položek DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)
- [Řešení potíží s ovládacím prvkem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
