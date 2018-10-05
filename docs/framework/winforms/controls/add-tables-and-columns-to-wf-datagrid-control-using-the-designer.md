---
title: 'Postupy: Přidávání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
ms.openlocfilehash: b2e8f962ed7fb9d205a9061bdc1b32c3a2f8b0bd
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48780008"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control-using-the-designer"></a>Postupy: Přidávání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid pomocí Návrháře

> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete. Další informace najdete v tématu [rozdíly mezi Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Data můžete zobrazit v modelu Windows Forms <xref:System.Windows.Forms.DataGrid> ovládacího prvku tabulky a sloupce tak, že vytvoříte <xref:System.Windows.Forms.DataGridTableStyle> objekty a jejich přidání na <xref:System.Windows.Forms.GridTableStylesCollection> objekt, který je přístupný prostřednictvím <xref:System.Windows.Forms.DataGrid> ovládacího prvku <xref:System.Windows.Forms.DataGrid.TableStyles%2A> vlastnost. Každý styl tabulky zobrazí obsah libovolné tabulka dat je zadán v <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> vlastnost <xref:System.Windows.Forms.DataGridTableStyle>. Ve výchozím nastavení styl tabulky bez styly sloupců se zobrazí všechny sloupce v tabulce data. Můžete omezit, které sloupce z tabulky zobrazí tak, že přidáte <xref:System.Windows.Forms.DataGridColumnStyle> objektů <xref:System.Windows.Forms.GridColumnStylesCollection>, který je přístupný prostřednictvím <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> vlastnosti každého <xref:System.Windows.Forms.DataGridTableStyle>.  
  
 Následující postup vyžaduje **aplikace Windows** projektu, který obsahuje formulář <xref:System.Windows.Forms.DataGrid> ovládacího prvku. Informace o tom, jak nastavit takový projekt, naleznete v tématu [postupy: vytvoření projektu aplikace Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). Ve výchozím nastavení v sadě Visual Studio 2005 <xref:System.Windows.Forms.DataGrid> ovládací prvek není v **nástrojů**. Informace o jeho přidání, naleznete v tématu [postupy: přidání položek panelu nástrojů](https://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-a-table-to-the-datagrid-control-in-the-designer"></a>Přidání tabulky do ovládacího prvku DataGrid v Návrháři  
  
1.  Pokud chcete zobrazit data v tabulce, je třeba nejdřív svázat <xref:System.Windows.Forms.DataGrid> ovládacího prvku do datové sady. Další informace najdete v tématu [postupy: vytvoření vazby ovládacího prvku Windows Forms DataGrid na zdroji dat pomocí návrháře](../../../../docs/framework/winforms/controls/bind-wf-datagrid-control-to-a-data-source-using-the-designer.md).  
  
2.  Vyberte <xref:System.Windows.Forms.DataGrid> ovládacího prvku <xref:System.Windows.Forms.DataGrid.TableStyles%2A> vlastností v okně Vlastnosti a pak klikněte na tlačítko se třemi tečkami (![snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky Vlastnost pro zobrazení **Editor kolekce styl DataGridTableStyle**.  
  
3.  V editoru kolekcí, klikněte na tlačítko **přidat** vložit styl tabulky.  
  
4.  Klikněte na tlačítko **OK** zavřete editor kolekce a znovu ho otevřít kliknutím tlačítko se třemi tečkami vedle možnosti <xref:System.Windows.Forms.DataGrid.TableStyles%2A> vlastnost.  
  
     Při opětovném otevření editoru kolekcí žádné tabulky dat. vázány na ovládací prvek se zobrazí v rozevíracím seznamu pro <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> vlastnost styl tabulky.  
  
5.  V **členy** pole editor kolekce, klikněte na styl tabulky.  
  
6.  V **vlastnosti** pole editoru kolekcí, vyberte <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> hodnotu pro tabulky, které chcete zobrazit.  
  
### <a name="to-add-a-column-to-the-datagrid-control-in-the-designer"></a>Chcete-li přidat sloupec do ovládacího prvku DataGrid v Návrháři  
  
1.  V **členy** pomocí boxingu **Editor kolekce styl DataGridTableStyle**, vyberte styl odpovídající tabulky. V **vlastnosti** pole editoru kolekcí, vyberte <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> kolekce a potom klikněte na tlačítko se třemi tečkami (![snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) vedle vlastnosti, která má zobrazit **Editor kolekce Styl DataGridColumnStyle**.  
  
2.  V editoru kolekcí, klikněte na tlačítko **přidat** k vložení objektu style sloupec nebo klikněte na šipku dolů vedle **přidat** zadat typ sloupce.  
  
     V rozevíracím seznamu můžete vybrat, zda <xref:System.Windows.Forms.DataGridTextBoxColumn> nebo <xref:System.Windows.Forms.DataGridBoolColumn> typu.  
  
3.  Kliknutím na OK zavřete **Editor kolekce Styl DataGridColumnStyle**a znovu ho otevřete kliknutím tlačítko se třemi tečkami vedle možnosti <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> vlastnost.  
  
     Při opětovném otevření editoru kolekcí žádné sloupce dat v tabulce vázaných dat se zobrazí v rozevíracím seznamu pro <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> vlastnost styl sloupce.  
  
4.  V **členy** pole editor kolekce, klikněte na styl sloupce.  
  
5.  V **vlastnosti** pole editoru kolekcí, vyberte <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> hodnotu sloupce, které chcete zobrazit.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvek DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
