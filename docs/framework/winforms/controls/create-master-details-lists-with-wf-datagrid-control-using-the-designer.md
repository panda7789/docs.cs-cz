---
title: 'Postupy: Vytváření hlavních podrobných seznamů pomocí ovládacího prvku Windows Forms DataGrid pomocí návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
ms.openlocfilehash: 5773c52a1cedfe373d25d42ff78720368ecb7a5e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632774"
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a>Postupy: Vytváření hlavních podrobných seznamů pomocí ovládacího prvku Windows Forms DataGrid pomocí návrháře

> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete. Další informace najdete v tématu [rozdíly mezi Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Pokud vaše <xref:System.Data.DataSet> obsahuje řadu souvisejících tabulek, můžete použít dvě <xref:System.Windows.Forms.DataGrid> ovládacích prvků pro zobrazení dat ve formátu hlavní podrobnosti. Jeden <xref:System.Windows.Forms.DataGrid> je určen jako hlavní mřížky, a druhý je určený být mřížku podrobnosti. Když vyberete položku v seznamu hlavních, všechny související podřízené položky jsou uvedeny v seznamu podrobnosti. Například pokud vaše <xref:System.Data.DataSet> obsahuje tabulku zákazníků a související tabulku Orders, zadali byste na hlavní mřížka tabulky Zákazníci a být mřížku podrobnosti o objednávkách. Když je zákazník vybrán z hlavní mřížky, všech objednávek tohoto zákazníka v tabulce objednávky přidružené by zobrazí v mřížce podrobností.  
  
 Následující postup vyžaduje, **aplikace Windows** projektu (**souboru** > **nový** > **projektu**  >  **Visual C#** nebo **jazyka Visual Basic** > **klasický desktopový** > **Windows Forms Aplikace**).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-a-master-details-list-in-the-designer"></a>Chcete-li vytvořit seznam hlavních podrobných v Návrháři  
  
1.  Přidejte dva <xref:System.Windows.Forms.DataGrid> ovládací prvky do formuláře. Další informace najdete v tématu [jak: Přidání ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). V sadě Visual Studio 2005 <xref:System.Windows.Forms.DataGrid> ovládací prvek není v **nástrojů** ve výchozím nastavení. Další informace najdete v tématu [jak: Přidání položek do panelu nástrojů](https://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0).  
  
    > [!NOTE]
    >  Následující kroky se nevztahují na Visual Studio 2005, který používá **zdroje dat** okno pro vytvoření vazby dat doby návrhu. Další informace najdete v tématu [vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio) a [jak: Zobrazení souvisejících dat v Windows Forms aplikace](https://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd).  
  
2.  Přetáhněte dvě nebo více tabulek z **Průzkumníka serveru** do formuláře.  
  
3.  Z **Data** nabídce vyberte možnost **generovat datovou sadu**.  
  
4.  Nastavte relace mezi tabulkami pomocí návrháře XML. Podrobnosti najdete v tématu "jak: Vytvoření vztahů 1 n v datových sadách a schématech XML"na webu MSDN.  
  
5.  Uložení relace tak, že vyberete **Uložit vše** z **souboru** nabídky.  
  
6.  Konfigurace <xref:System.Windows.Forms.DataGrid> ovládací prvek, který chcete nastavit hlavní mřížky, následujícím způsobem:  
  
    1.  Vyberte <xref:System.Data.DataSet> z rozevíracího seznamu v <xref:System.Windows.Forms.DataGrid.DataSource%2A> vlastnost.  
  
    2.  Vyberte z rozevíracího seznamu v tabulce hlavní (například "zákazníci") <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnost.  
  
7.  Konfigurace <xref:System.Windows.Forms.DataGrid> ovládací prvek, který chcete určit podrobnosti mřížky, následujícím způsobem:  
  
    1.  Vyberte <xref:System.Data.DataSet> z rozevíracího seznamu v <xref:System.Windows.Forms.DataGrid.DataSource%2A> vlastnost.  
  
    2.  Vyberte relaci (například "Customers.CustOrd") mezi tabulkami a podrobností z rozevíracího seznamu v <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnost. Chcete-li zobrazit relace, rozbalte uzel kliknutím na symbol plus (**+**) znaménko vedle hlavní tabulku v rozevíracím seznamu.  
  
## <a name="see-also"></a>Viz také:
- [Ovládací prvek DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
- [Přehled ovládacího prvku DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)
- [Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
