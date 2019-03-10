---
title: 'Postupy: Formátování v ovládacím prvku Windows Forms DataGrid pomocí návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], DataGrid controls
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: 533b9814-6124-49dc-9fda-085f1502609f
ms.openlocfilehash: 92939f1bdddaca1d743116a4ae4ee9da657abf19
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725360"
---
# <a name="how-to-format-the-windows-forms-datagrid-control-using-the-designer"></a>Postupy: Formátování v ovládacím prvku Windows Forms DataGrid pomocí návrháře

> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete. Další informace najdete v tématu [rozdíly mezi Windows Forms DataGridView a DataGrid – ovládací prvky](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Rozlišení barvami různých částí <xref:System.Windows.Forms.DataGrid> ovládací prvek může pomoct usnadňují informace v něm přečíst a interpretovat. Barva lze použít k řádků a sloupců. Řádky a sloupce můžete také skrytí nebo zobrazení na vašem uvážení.  
  
 Existují tři základní aspekty formátování <xref:System.Windows.Forms.DataGrid> ovládacího prvku:  
  
-   Můžete nastavit vlastnosti, které chcete vytvořit výchozí styl, ve kterém se zobrazí data.  
  
-   Z této základní třídě potom můžete přizpůsobit způsob, jakým některé tabulky se zobrazí v době běhu.  
  
-   Nakonec můžete upravit sloupce, které se zobrazí v mřížce dat, jakož i barvy a další formátování, které se zobrazí.  
  
 Jako první krok v datové mřížce formátování, můžete nastavit vlastnosti <xref:System.Windows.Forms.DataGrid> samotný. Tyto možnosti barvu a formát tvoří základ, ze kterého můžete pak provádět změny v závislosti na datových tabulek a sloupců zobrazených.  
  
 Následující postup vyžaduje, **aplikace Windows** projektu s formulář obsahující <xref:System.Windows.Forms.DataGrid> ovládacího prvku. Informace o nastavení takový projekt, naleznete v tématu [jak: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [jak: Přidání ovládacích prvků Windows Forms](how-to-add-controls-to-windows-forms.md). V sadě Visual Studio 2005 <xref:System.Windows.Forms.DataGrid> ovládací prvek není v **nástrojů** ve výchozím nastavení. Další informace najdete v tématu [jak: Přidání položek do panelu nástrojů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>Stanovit výchozí styl ovládacího prvku DataGrid  
  
1.  Vyberte <xref:System.Windows.Forms.DataGrid> ovládacího prvku.  
  
2.  V **vlastnosti** okno, nastavte následující vlastnosti, podle potřeby.  
  
    |Vlastnost|Popis|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|`BackColor` Vlastnost určuje barvu sudých řádků mřížky. Při nastavení <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> na jinou barvu, každý řádek je nastavena na tuto novou barvu (řádky 1, 3, 5 a tak dále).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Barva pozadí sudých řádků mřížky (řádky, 0, 2, 4, 6 a tak dále).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Vzhledem k tomu <xref:System.Windows.Forms.DataGrid.BackColor%2A> a <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> vlastnosti určuje barvu řádků v mřížce <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> vlastnost určuje barvu z oblasti mimo řádek oblast, která je viditelná pouze když mřížky je přesunut do dolní části oblasti nebo pokud pouze několik řádků obsažené v mřížce.|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Styl ohraničení mřížky, jeden z <xref:System.Windows.Forms.BorderStyle> hodnot výčtu.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|Barva pozadí titulek okna mřížky, které se zobrazí okamžitě nad mřížkou.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|Písmo záhlaví v horní části stránky mřížky.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|Barva pozadí titulek okna mřížky.|  
    |<xref:System.Windows.Forms.Control.Font%2A>|Písmo použité k zobrazení textu v mřížce.|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|Barva písma, zobrazí data v řádcích datové mřížce.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|Barva čar mřížky dat mřížky.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|Styl čar oddělujících buňky ovládacího prvku mřížky, jeden z <xref:System.Windows.Forms.DataGridLineStyle> hodnot výčtu.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|Barva pozadí záhlaví řádků a sloupců.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|Písmo použité pro záhlaví sloupců.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Barva popředí záhlaví sloupců mřížky, včetně textu záhlaví sloupce a znaménko plus (+) a znaménko minus (-) glyfy, které rozbalovat a sbalovat řádků při více související tabulky se zobrazí.|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|Barva textu na odkazy v datové mřížce, včetně odkazů na podřízené tabulky, název relace a tak dále.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|V podřízené tabulce je to barvu pozadí nadřazených řádků.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|V podřízené tabulce je to barvu popředí nadřazených řádků.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Určuje, zda názvy tabulek a sloupců se zobrazí v řádku nadřazené prostřednictvím <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> výčtu.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Výchozí šířku (v pixelech) sloupce v mřížce. Tuto vlastnost nastavte před resetováním <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnosti (buď samostatně, nebo prostřednictvím <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metoda), nebo vlastnost nebude mít žádný efekt.<br /><br /> Vlastnost nelze nastavit na hodnotu menší než 0.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|Výška řádku řádků v mřížce (v pixelech). Tuto vlastnost nastavte před resetováním <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnosti (buď samostatně, nebo prostřednictvím <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metoda), nebo vlastnost nebude mít žádný efekt.<br /><br /> Vlastnost nelze nastavit na hodnotu menší než 0.|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|Šířka záhlaví řádků mřížky.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Při výběru řádku nebo buňky, to je barvu pozadí.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Při výběru řádku nebo buňky, to je barvu popředí.|  
  
    > [!NOTE]
    >  K přizpůsobení barev ovládacích prvků, je možné provádět ovládacího prvku nejsou dostupné kvůli špatnému barva výběru (například red a zelená). Použití barev, které jsou k dispozici na **systémové barvy** palety chcete vyhnout tomuto problému.

     Následující postup vyžaduje, <xref:System.Windows.Forms.DataGrid> ovládací prvek vázán na data tabulky. Další informace najdete v tématu [jak: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).

### <a name="to-set-the-table-and-column-style-of-a-data-table-at-design-time"></a>Nastavit styl tabulky a sloupce z tabulky dat v době návrhu

1.  Vyberte <xref:System.Windows.Forms.DataGrid> ovládací prvek na formuláři.

2.  V **vlastnosti** okna, vyberte <xref:System.Windows.Forms.DataGrid.TableStyles%2A> vlastnosti a klikněte na tlačítko **tlačítko se třemi tečkami** (![VisualStudioEllipsesButton snímek obrazovky](../media/vbellipsesbutton.png " vbEllipsesButton")) tlačítko.

3.  V **Editor kolekce styl DataGridTableStyle** dialogové okno, klikněte na tlačítko **přidat** styl tabulky přidat do kolekce.

     S **Editor kolekce styl DataGridTableStyle**, můžete přidat a odebrat styly tabulky, zobrazení sady a vlastnosti rozložení a sada mapování názvu pro styly tabulky.

4.  Nastavte <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> nastavte název mapování pro každý styl tabulky.

     Název mapování slouží k určení, jaký styl tabulky je nutné používat s které tabulky.

5.  V **Editor kolekce styl DataGridTableStyle**, vyberte <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> vlastnosti a klikněte na tlačítko se třemi tečkami (![snímek obrazovky VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton ")).

6.  V **Editor kolekce Styl DataGridColumnStyle** dialogovém okně Přidat styly sloupců styl tabulky, který jste vytvořili.

     S **Editor kolekce Styl DataGridColumnStyle**, můžete přidat a odebrat styly sloupců, nastavit vlastnosti zobrazení a rozložení a nastavte název mapování a formátování řetězce data sloupců.

    > [!NOTE]
    >  Další informace o formátovacích řetězcích naleznete v tématu [Formatting Types](../../../standard/base-types/formatting-types.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [Postupy: Odstranit nebo skrytí sloupců v ovládacím prvku Windows Forms DataGrid](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)