---
title: 'Postupy: Formátování ovládacího prvku Windows Forms DataGrid pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], DataGrid controls
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: 533b9814-6124-49dc-9fda-085f1502609f
ms.openlocfilehash: c6069c2557ac220a37db7f16917a029d6fa49522
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541316"
---
# <a name="how-to-format-the-windows-forms-datagrid-control-using-the-designer"></a>Postupy: Formátování ovládacího prvku Windows Forms DataGrid pomocí Návrháře
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte. Další informace najdete v tématu [rozdíly mezi systému Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Použití různých barev pro různé součásti <xref:System.Windows.Forms.DataGrid> řízení může pomoct snadněji informace v něm ke čtení a interpretovat. Barva je použít pro řádků a sloupců. Řádků a sloupců, můžete také být skrytý nebo vidět svého uvážení.  
  
 Existují tři základní aspekty formátování <xref:System.Windows.Forms.DataGrid> ovládacího prvku:  
  
-   Můžete nastavit vlastnosti pro vytvoření výchozí styl, ve kterém se zobrazí data.  
  
-   Z tohoto základní následně můžete přizpůsobit způsob zobrazování určité tabulky v době běhu.  
  
-   Nakonec můžete upravit sloupce, které se zobrazují v datové mřížce, jakož i barvy a další formátování, které se zobrazí.  
  
 Jako počáteční krok při formátování dat mřížky, můžete nastavit vlastnosti <xref:System.Windows.Forms.DataGrid> sám sebe. Tyto možnosti barvy a formát tvoří základ, ze které potom můžete provést změny v závislosti na data tabulky a sloupce zobrazí.  
  
 Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře obsahující <xref:System.Windows.Forms.DataGrid> ovládacího prvku. Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). V [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], <xref:System.Windows.Forms.DataGrid> ovládací prvek není součástí **sada nástrojů** ve výchozím nastavení. Další informace najdete v tématu [postupy: Přidání položky do sady nástrojů](http://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>Pro vytvoření výchozí styl ovládacího prvku DataGrid  
  
1.  Vyberte <xref:System.Windows.Forms.DataGrid> ovládacího prvku.  
  
2.  V **vlastnosti** okně podle potřeby nastavte následující vlastnosti.  
  
    |Vlastnost|Popis|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|`BackColor` Vlastnost definuje barvu sudých řádků mřížky. Když nastavíte <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> na jinou barvu, každý druhý řádek je nastavena na tuto novou barvu (řádků 1, 3, 5 a tak dále).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Barva pozadí sudých řádků mřížky (řádků 0, 2, 4, 6 a tak dále).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Zatímco <xref:System.Windows.Forms.DataGrid.BackColor%2A> a <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> vlastnosti určuje barvu řádků v mřížce <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> vlastnost určuje barvu oblasti mimo oblast řádek, který je zobrazen, pouze když přesunut do dolní oblasti mřížky, nebo pokud jenom pár řádků jsou obsažené v mřížce.|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Styl ohraničení mřížky, jeden z <xref:System.Windows.Forms.BorderStyle> hodnot výčtu.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|Barva pozadí mřížky okno popisek, který se zobrazí okamžitě nad mřížky.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|Písmo popisku v horní části mřížky.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|Barva pozadí záhlaví okna mřížky.|  
    |<xref:System.Windows.Forms.Control.Font%2A>|Písmo použité k zobrazení textu v mřížce.|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|Barva písma zobrazuje data v řádky mřížky data.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|Barva čar mřížky dat mřížky.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|Styl čar oddělujících buňky mřížky, jeden z <xref:System.Windows.Forms.DataGridLineStyle> hodnot výčtu.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|Barva pozadí záhlaví řádků a sloupců.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|Písmo použité pro záhlaví sloupců.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Zobrazí se barvu popředí záhlaví sloupců mřížky, včetně textu záhlaví sloupce a znaménko plus (+) a znaménka minus (-) glyfů, které rozbalení a sbalení řádků při více související tabulky.|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|Barva textu všechny odkazy na data mřížky, včetně odkazů na podřízené tabulky, název relace a tak dále.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|V podřízené tabulce je to barvu pozadí nadřazených řádků.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|V podřízené tabulce je to barvu popředí nadřazených řádků.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Určuje, zda jsou názvy tabulek a sloupců zobrazovat v řádku nadřazené prostřednictvím <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> výčtu.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Šířka výchozí sloupců v mřížce (v pixelech). Tuto vlastnost nastavit před resetováním <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnosti (buď samostatně, nebo pomocí <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metoda), nebo vlastnost nebude mít žádný vliv.<br /><br /> Vlastnost nelze nastavit na hodnotu menší než 0.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|Výška řádku řádků v mřížce (v pixelech). Tuto vlastnost nastavit před resetováním <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnosti (buď samostatně, nebo pomocí <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metoda), nebo vlastnost nebude mít žádný vliv.<br /><br /> Vlastnost nelze nastavit na hodnotu menší než 0.|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|Šířka záhlaví řádků mřížky.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Pokud je vybraný řádek nebo buňky, jde barvu pozadí.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Pokud je vybraný řádek nebo buňky, jde barvu popředí.|  
  
    > [!NOTE]
    >  Když jsou přizpůsobení barev ovládacích prvků, je možné ovládací prvek nastavit nedostupný v důsledku výběru nízký barvu (například red a zelená). Použít k dispozici na barvy **barvy systému** palety chcete tomuto problému vyhnout.  
  
     Následující postup vyžaduje <xref:System.Windows.Forms.DataGrid> ovládací prvek vázán k tabulce data. Další informace najdete v tématu [postupy: vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-at-design-time"></a>Chcete-li nastavit styl tabulky a sloupce tabulky dat v době návrhu  
  
1.  Vyberte <xref:System.Windows.Forms.DataGrid> ovládací prvek na formuláři.  
  
2.  V **vlastnosti** vyberte <xref:System.Windows.Forms.DataGrid.TableStyles%2A> vlastnost a klikněte na tlačítko **třemi tečkami** (![– snímek obrazovky VisualStudioEllipsesButton] (../../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) tlačítko.  
  
3.  V **Editor kolekce styl DataGridTableStyle** dialogové okno, klikněte na tlačítko **přidat** styl tabulky přidat do kolekce.  
  
     Pomocí **Editor kolekce styl DataGridTableStyle**, můžete přidat a odebrat tabulky styly, sadu zobrazení a rozložení vlastností a sadu mapování názvu pro styly tabulky.  
  
4.  Nastavte <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> vlastnost na název mapování pro každý styl tabulky.  
  
     Název mapování slouží k určení styl tabulky, který se má použít s tabulek, které.  
  
5.  V **Editor kolekce styl DataGridTableStyle**, vyberte <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> vlastnost a klikněte na tlačítko se třemi tečkami (![– snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton ")).  
  
6.  V **Editor kolekce Styl DataGridColumnStyle** dialogové okno pole, přidejte sloupec stylů na styl tabulky, který jste vytvořili.  
  
     Pomocí **Editor kolekce Styl DataGridColumnStyle**, můžete přidat a odebrat sloupec styly, nastaví vlastnosti zobrazení a rozložení a nastavte název mapování a formátování řetězce pro data sloupce.  
  
    > [!NOTE]
    >  Další informace o formátování řetězce najdete v tématu [typy formátování](../../../../docs/standard/base-types/formatting-types.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.GridTableStylesCollection>  
 <xref:System.Windows.Forms.GridColumnStylesCollection>  
 <xref:System.Windows.Forms.DataGrid>  
 [Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [Ovládací prvek DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
