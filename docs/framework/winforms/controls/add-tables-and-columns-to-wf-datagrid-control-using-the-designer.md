---
title: "Postupy: Přidávání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ccc310303c7edb968b43f4d529782979024e8e73
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control-using-the-designer"></a>Postupy: Přidávání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid pomocí Návrháře
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte. Další informace najdete v tématu [rozdíly mezi systému Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Data můžete zobrazit v modelu Windows Forms <xref:System.Windows.Forms.DataGrid> ovládacího prvku tabulky a sloupce tak, že vytvoříte <xref:System.Windows.Forms.DataGridTableStyle> objekty a jejich přidání <xref:System.Windows.Forms.GridTableStylesCollection> objekt, který je přístupný prostřednictvím <xref:System.Windows.Forms.DataGrid> ovládacího prvku <xref:System.Windows.Forms.DataGrid.TableStyles%2A> vlastnost. Každý styl tabulky zobrazí obsah ať tabulky dat je zadán v <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> vlastnost <xref:System.Windows.Forms.DataGridTableStyle>. Ve výchozím nastavení zobrazí styl tabulky bez sloupec styly definované všechny sloupce v této tabulce data. Můžete omezit, které sloupce z tabulky se objeví přidáním <xref:System.Windows.Forms.DataGridColumnStyle> objekty ke <xref:System.Windows.Forms.GridColumnStylesCollection>, které je přístupné přes <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> vlastnost jednotlivých <xref:System.Windows.Forms.DataGridTableStyle>.  
  
 Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře, který obsahuje <xref:System.Windows.Forms.DataGrid> ovládacího prvku. Informace o tom, jak nastavit tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). Ve výchozím nastavení v [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], <xref:System.Windows.Forms.DataGrid> ovládací prvek není součástí **sada nástrojů**. Informace o přidání najdete v tématu [postupy: Přidání položky do sady nástrojů](http://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-a-table-to-the-datagrid-control-in-the-designer"></a>Chcete-li přidat tabulku do ovládacího prvku DataGrid v Návrháři  
  
1.  Chcete-li zobrazit data v tabulce, je třeba nejprve svázat <xref:System.Windows.Forms.DataGrid> ovládacího prvku do datové sady. Další informace najdete v tématu [postupy: vytvoření vazby ovládacího prvku Windows Forms DataGrid pro zdroj dat využívající návrháře](../../../../docs/framework/winforms/controls/bind-wf-datagrid-control-to-a-data-source-using-the-designer.md).  
  
2.  Vyberte <xref:System.Windows.Forms.DataGrid> ovládacího prvku <xref:System.Windows.Forms.DataGrid.TableStyles%2A> vlastnost v okně vlastností a pak klikněte na tlačítko se třemi tečkami (![– snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky vlastnost, která má zobrazit **Editor kolekce styl DataGridTableStyle**.  
  
3.  V editoru kolekce, klikněte na tlačítko **přidat** vložit styl tabulky.  
  
4.  Klikněte na tlačítko **OK** zavřete editor kolekce a potom ho znovu otevřít kliknutím tlačítko se třemi tečkami vedle možnosti <xref:System.Windows.Forms.DataGrid.TableStyles%2A> vlastnost.  
  
     Když znovu otevřete editor kolekcí, všechny tabulky dat vázáno na ovládací prvek se zobrazí v rozevíracím seznamu pro <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> vlastnost stylu tabulky.  
  
5.  V **členy** pole editor kolekce, klikněte na styl tabulky.  
  
6.  V **vlastnosti** pole editor kolekcí, vyberte <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> hodnotu pro tabulku, která se má zobrazit.  
  
### <a name="to-add-a-column-to-the-datagrid-control-in-the-designer"></a>Chcete-li přidat sloupce do ovládacího prvku DataGrid v Návrháři  
  
1.  V **členy** pole **Editor kolekce styl DataGridTableStyle**, vyberte styl příslušné tabulce. V **vlastnosti** pole editor kolekcí, vyberte <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> kolekce a potom klikněte na tlačítko se třemi tečkami (![– snímek obrazovky VisualStudioEllipsesButton] (../../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) vedle zobrazovanou vlastnost **Editor kolekce Styl DataGridColumnStyle**.  
  
2.  V editoru kolekce, klikněte na tlačítko **přidat** vložit sloupec styl nebo klikněte na šipku dolů vedle **přidat** k zadání typu sloupce.  
  
     V rozevíracím seznamu můžete vybrat, zda <xref:System.Windows.Forms.DataGridTextBoxColumn> nebo <xref:System.Windows.Forms.DataGridBoolColumn> typu.  
  
3.  Kliknutím na OK zavřete **Editor kolekce Styl DataGridColumnStyle**a poté znovu otevřete kliknutím tlačítko se třemi tečkami vedle možnosti <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> vlastnost.  
  
     Když znovu otevřete editor kolekcí, žádné sloupce dat v tabulce vázaný datový se objeví v rozevíracím seznamu pro <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> vlastnost stylu sloupce.  
  
4.  V **členy** pole editor kolekce, klikněte na styl sloupce.  
  
5.  V **vlastnosti** pole editor kolekcí, vyberte <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> hodnotu pro sloupec, který chcete zobrazit.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvek DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
