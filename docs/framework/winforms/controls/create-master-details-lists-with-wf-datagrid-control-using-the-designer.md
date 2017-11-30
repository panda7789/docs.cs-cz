---
title: "Postupy: Vytváření hlavních-podrobných seznamů s ovládacím prvkem Windows Forms DataGrid pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 66de6fb17e3ee5b916c4bb20dfa0799758375406
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a>Postupy: Vytváření hlavních-podrobných seznamů s ovládacím prvkem Windows Forms DataGrid pomocí Návrháře
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte. Další informace najdete v tématu [rozdíly mezi systému Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Pokud vaše <xref:System.Data.DataSet> obsahuje řadu související tabulky, můžete použít dva <xref:System.Windows.Forms.DataGrid> ovládacích prvků pro zobrazení dat ve formátu seznam podrobnosti. Jeden <xref:System.Windows.Forms.DataGrid> je určen jako hlavní mřížky, a druhý je určený jako podrobnosti mřížky. Když vyberete položku v seznamu hlavní, všech souvisejících podřízených položek se zobrazí v seznamu podrobnosti. Například pokud vaše <xref:System.Data.DataSet> obsahuje tabulku zákazníků a související tabulky objednávky, zadali byste tabulku zákazníků jako hlavní mřížky a tabulky objednávky být podrobnosti mřížky. Pokud zákazník je vybraná z hlavní mřížky, všechny objednávky přidružené tohoto zákazníka v tabulce objednávky bude zobrazen v mřížce podrobností.  
  
 Následující postup vyžaduje **aplikace Windows** projektu. Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-a-master-details-list-in-the-designer"></a>Můžete vytvořit seznam hlavních podrobných v Návrháři  
  
1.  Přidejte dva <xref:System.Windows.Forms.DataGrid> ovládacích prvků formuláře. Další informace najdete v tématu [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). V [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], <xref:System.Windows.Forms.DataGrid> ovládací prvek není součástí **sada nástrojů** ve výchozím nastavení. Další informace najdete v tématu [postupy: Přidání položky do sady nástrojů](http://msdn.microsoft.com/en-us/458e119e-17fe-450b-b889-e31c128bd7e0).  
  
    > [!NOTE]
    >  Následující postup se nejsou použitelné [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], které používá **zdroje dat** okna pro vázání dat v době návrhu. Další informace najdete v tématu [vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio) a [postupy: zobrazení souvisejících dat ve formulářové aplikaci Windows](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd).  
  
2.  Přetáhněte dvou nebo více tabulek z **Průzkumníka serveru** do formuláře.  
  
3.  Z **Data** nabídce vyberte možnost **generovat datovou sadu**.  
  
4.  Nastavte relace mezi tabulkami pomocí návrháře XML. Podrobnosti najdete v tématu "postup: vytvoření na více vztahy v datových sadách a schématech XML" na webu MSDN.  
  
5.  Uložit vztahy výběrem **Uložit vše** z **souboru** nabídky.  
  
6.  Konfigurace <xref:System.Windows.Forms.DataGrid> ovládací prvek, který chcete určit hlavní mřížky, následujícím způsobem:  
  
    1.  Vyberte <xref:System.Data.DataSet> v rozevíracím seznamu v <xref:System.Windows.Forms.DataGrid.DataSource%2A> vlastnost.  
  
    2.  Vyberte v rozevíracím seznamu v hlavní tabulku (například "zákazníci") <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnost.  
  
7.  Konfigurace <xref:System.Windows.Forms.DataGrid> ovládací prvek, který chcete určit podrobnosti mřížky, následujícím způsobem:  
  
    1.  Vyberte <xref:System.Data.DataSet> v rozevíracím seznamu v <xref:System.Windows.Forms.DataGrid.DataSource%2A> vlastnost.  
  
    2.  Vyberte vztah mezi tabulkami v rozevíracím seznamu v seznamu a podrobností (například "Customers.CustOrd") <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnost. Chcete-li zobrazit relace, rozbalte uzel kliknutím na znaménko plus (**+**) znaménkem hlavní tabulku v rozevíracím seznamu.  
  
## <a name="see-also"></a>Viz také  
 [DataGrid – ovládací prvek](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Přehled ovládacího prvku DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [Postupy: vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
