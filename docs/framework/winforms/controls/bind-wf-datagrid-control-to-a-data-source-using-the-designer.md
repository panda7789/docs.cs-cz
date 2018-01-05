---
title: "Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- Windows Forms controls, data binding
- bound controls [Windows Forms]
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e0bde96442e09ee33a63cecd56a4cd6e2cf19a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a>Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat pomocí Návrháře
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte. Další informace najdete v tématu [rozdíly mezi systému Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Windows Forms <xref:System.Windows.Forms.DataGrid> ovládací prvek je určená speciálně pro zobrazení informací ze zdroje dat. Vytvoření vazby ovládacího prvku v době návrhu nastavením <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnosti, nebo v době běhu voláním <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metoda. I když můžete zobrazit data z různých zdrojů dat, některé běžné zdroje jsou datové sady a data zobrazení.  
  
 Pokud je zdroj dat dostupný v době návrhu – například, pokud tento formulář obsahuje instanci datové sady nebo zobrazení dat – mřížky můžete vázat na zdroj dat v době návrhu. Potom můžete zobrazit náhled vzhled data v mřížce.  
  
 Můžete také navázat mřížky prostřednictvím kódu programu, v době běhu. To je užitečné, pokud chcete nastavit zdroj dat na základě informací, které máte v době běhu. Aplikace může například umožní uživateli zadání názvu tabulky. Chcete-li zobrazit. Je také nutné v situacích, kde se zdroji dat neexistuje v době návrhu. To zahrnuje zdroje dat jako pole, kolekce, netypové datové sady a čtečky dat.  
  
 Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře obsahující <xref:System.Windows.Forms.DataGrid> ovládacího prvku. Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). V [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], <xref:System.Windows.Forms.DataGrid> ovládací prvek není součástí **sada nástrojů** ve výchozím nastavení. Informace o přidání najdete v tématu [postupy: Přidání položky do sady nástrojů](http://msdn.microsoft.com/en-us/458e119e-17fe-450b-b889-e31c128bd7e0). Kromě toho v [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], můžete použít **zdroje dat** okna pro vázání dat v době návrhu. Další informace najdete v části [vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a>Pro data-bind DataGrid – ovládací prvek pro jednotlivé tabulky v Návrháři  
  
1.  Nastavte ovládacího prvku <xref:System.Windows.Forms.DataGrid.DataSource%2A> vlastnost, která má objekt obsahující data položky, které chcete vytvořit vazbu.  
  
2.  Pokud zdroj dat je datová sada, nastavte <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnost na název tabulky pro vazbu.  
  
3.  Pokud je zdroj dat datové sady nebo zobrazení dat na základě datové sady tabulky, přidejte kód pro formulář k vyplnění datové sady.  
  
     Přesný kód, který používáte, závisí na kterém je datová sada získávání dat. Pokud se datová sada je právě nezadají přímo z databáze, obvykle volání `Fill` metoda adaptér pro data, jako v následujícím příkladu kódu, který naplní datovou sadu s názvem `DsCategories1`:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
4.  (Volitelné) Přidejte příslušné tabulce styly a styly sloupců do mřížky.  
  
     Pokud neexistují žádné tabulky styly, zobrazí se v tabulce, ale s minimálním formátování a všechny sloupce, které jsou viditelné.  
  
### <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a>Pro data-bind ovládacího prvku DataGrid k několika tabulkám v datové sadě v Návrháři  
  
1.  Nastavte ovládacího prvku <xref:System.Windows.Forms.DataGrid.DataSource%2A> vlastnost, která má objekt obsahující data položky, které chcete vytvořit vazbu.  
  
2.  Pokud datová sada obsahuje související tabulky (to znamená, pokud obsahuje objekt relace), můžete nastavit <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnost na název v nadřazené tabulce.  
  
3.  Napište kód pro vyplnění datové sady.  
  
## <a name="see-also"></a>Viz také  
 [Přehled ovládacího prvku DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [Postupy: Přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [Ovládací prvek DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Windows Forms – datová vazba](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Přístup k datům v sadě Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio)
