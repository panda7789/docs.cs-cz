---
title: 'Postupy: Přidávání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
ms.openlocfilehash: 5e530b475745a3df7482b9ea4276f004d13ec055
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642448"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control-using-the-designer"></a>Postupy: Přidávání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid pomocí Návrháře

> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete. Další informace najdete v tématu [rozdíly mezi Windows Forms DataGridView a DataGrid – ovládací prvky](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Data můžete zobrazit v modelu Windows Forms <xref:System.Windows.Forms.DataGrid> ovládacího prvku tabulky a sloupce tak, že vytvoříte <xref:System.Windows.Forms.DataGridTableStyle> objekty a jejich přidání na <xref:System.Windows.Forms.GridTableStylesCollection> objekt, který je přístupný prostřednictvím <xref:System.Windows.Forms.DataGrid> ovládacího prvku <xref:System.Windows.Forms.DataGrid.TableStyles%2A> vlastnost. Každý styl tabulky zobrazí obsah libovolné tabulka dat je zadán v <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> vlastnost <xref:System.Windows.Forms.DataGridTableStyle>. Ve výchozím nastavení styl tabulky bez styly sloupců se zobrazí všechny sloupce v tabulce data. Můžete omezit, které sloupce z tabulky zobrazí tak, že přidáte <xref:System.Windows.Forms.DataGridColumnStyle> objektů <xref:System.Windows.Forms.GridColumnStylesCollection>, který je přístupný prostřednictvím <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> vlastnosti každého <xref:System.Windows.Forms.DataGridTableStyle>.  
  
 Následující postup vyžaduje **aplikace Windows** projektu, který obsahuje formulář <xref:System.Windows.Forms.DataGrid> ovládacího prvku. Informace o tom, jak nastavit takový projekt, naleznete v tématu [jak: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [jak: Přidání ovládacích prvků Windows Forms](how-to-add-controls-to-windows-forms.md). Ve výchozím nastavení v sadě Visual Studio 2005 <xref:System.Windows.Forms.DataGrid> ovládací prvek není v **nástrojů**. Informace o jeho přidání, naleznete v tématu [jak: Přidání položek do panelu nástrojů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-a-table-to-the-datagrid-control-in-the-designer"></a>Přidání tabulky do ovládacího prvku DataGrid v Návrháři  
  
1. Pokud chcete zobrazit data v tabulce, je třeba nejdřív svázat <xref:System.Windows.Forms.DataGrid> ovládacího prvku do datové sady. Další informace najdete v tématu [jak: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat pomocí návrháře](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md).  
  
2. Vyberte <xref:System.Windows.Forms.DataGrid> ovládacího prvku <xref:System.Windows.Forms.DataGrid.TableStyles%2A> vlastností v okně Vlastnosti a pak klikněte na tlačítko se třemi tečkami (![snímek obrazovky VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky Vlastnost pro zobrazení **Editor kolekce styl DataGridTableStyle**.  
  
3. V editoru kolekcí, klikněte na tlačítko **přidat** vložit styl tabulky.  
  
4. Klikněte na tlačítko **OK** zavřete editor kolekce a znovu ho otevřít kliknutím tlačítko se třemi tečkami vedle možnosti <xref:System.Windows.Forms.DataGrid.TableStyles%2A> vlastnost.  
  
     Při opětovném otevření editoru kolekcí žádné tabulky dat. vázány na ovládací prvek se zobrazí v rozevíracím seznamu pro <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> vlastnost styl tabulky.  
  
5. V **členy** pole editor kolekce, klikněte na styl tabulky.  
  
6. V **vlastnosti** pole editoru kolekcí, vyberte <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> hodnotu pro tabulky, které chcete zobrazit.  
  
### <a name="to-add-a-column-to-the-datagrid-control-in-the-designer"></a>Chcete-li přidat sloupec do ovládacího prvku DataGrid v Návrháři  
  
1. V **členy** pomocí boxingu **Editor kolekce styl DataGridTableStyle**, vyberte styl odpovídající tabulky. V **vlastnosti** pole editoru kolekcí, vyberte <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> kolekce a potom klikněte na tlačítko se třemi tečkami (![snímek obrazovky VisualStudioEllipsesButton](../media/vbellipsesbutton.png " vbEllipsesButton")) vedle vlastnosti, která má zobrazit **Editor kolekce Styl DataGridColumnStyle**.  
  
2. V editoru kolekcí, klikněte na tlačítko **přidat** k vložení objektu style sloupec nebo klikněte na šipku dolů vedle **přidat** zadat typ sloupce.  
  
     V rozevíracím seznamu můžete vybrat, zda <xref:System.Windows.Forms.DataGridTextBoxColumn> nebo <xref:System.Windows.Forms.DataGridBoolColumn> typu.  
  
3. Kliknutím na OK zavřete **Editor kolekce Styl DataGridColumnStyle**a znovu ho otevřete kliknutím tlačítko se třemi tečkami vedle možnosti <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> vlastnost.  
  
     Při opětovném otevření editoru kolekcí žádné sloupce dat v tabulce vázaných dat se zobrazí v rozevíracím seznamu pro <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> vlastnost styl sloupce.  
  
4. V **členy** pole editor kolekce, klikněte na styl sloupce.  
  
5. V **vlastnosti** pole editoru kolekcí, vyberte <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> hodnotu sloupce, které chcete zobrazit.  
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
- [Postupy: Odstranit nebo skrytí sloupců v ovládacím prvku Windows Forms DataGrid](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
