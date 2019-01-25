---
title: 'Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat pomocí návrháře'
ms.date: 03/30/2017
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
ms.openlocfilehash: 414c989d258ca4b7a9097afa2b7f2407505fb629
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687580"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a>Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat pomocí návrháře

> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete. Další informace najdete v tématu [rozdíly mezi Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Windows Forms <xref:System.Windows.Forms.DataGrid> ovládací prvek je navržená speciálně pro zobrazení informací ze zdroje dat. Vazbu ovládacího prvku v době návrhu tak, že nastavíte <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnosti, nebo za běhu pomocí volání <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metoda. Přestože lze zobrazit data z různých zdrojů dat, obvykle zdroje jsou datové sady a data zobrazení.  
  
 Pokud zdroj dat je k dispozici v době návrhu – například, pokud formulář obsahuje instance datové sady nebo zobrazení dat – mřížky můžete vázat na zdroj dat v době návrhu. Pak můžete zobrazit náhled dat bude vypadat v mřížce.  
  
 Můžete také navázat mřížky prostřednictvím kódu programu, v době běhu. To je užitečné, když chcete nastavit zdroj dat na základě informací, které získáte v době běhu. Například aplikace může uživatelům povolit, zadejte název tabulky. Chcete-li zobrazit. Je také nutné v situacích, kde se zdroji dat neexistuje v době návrhu. To zahrnuje zdroje dat, jako je například pole, kolekcí, netypové datové sady a čtečky dat.  
  
 Následující postup vyžaduje, **aplikace Windows** projektu s formulář obsahující <xref:System.Windows.Forms.DataGrid> ovládacího prvku. Informace o nastavení takový projekt, naleznete v tématu [jak: Vytvoření projektu aplikace Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) a [jak: Přidání ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). V sadě Visual Studio 2005 <xref:System.Windows.Forms.DataGrid> ovládací prvek není v **nástrojů** ve výchozím nastavení. Informace o jeho přidání, naleznete v tématu [jak: Přidání položek do panelu nástrojů](https://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0). Kromě toho v sadě Visual Studio 2005, můžete použít **zdroje dat** okno pro vytvoření vazby dat doby návrhu. Další informace najdete v části [vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a>Chcete svázat data – ovládací prvek DataGrid jedné tabulky v Návrháři  
  
1.  Nastavit u tohoto prvku <xref:System.Windows.Forms.DataGrid.DataSource%2A> vlastnost na objekt obsahující data položky, které chcete vytvořit vazbu.  
  
2.  Pokud zdroj dat je datová sada, nastavte <xref:System.Windows.Forms.DataGrid.DataMember%2A> nastavte název tabulky k vytvoření vazby.  
  
3.  Pokud je zdroj dat datové sady nebo zobrazení dat na základě tabulky datovou sadu, přidejte kód pro formulář k vyplnění datové sady.  
  
     Přesný kód, který používáte závisí na datové sady je kde získávají data. Pokud probíhá naplňování datové sady přímo z databáze, obvykle volat `Fill` metoda adaptéru dat, stejně jako v následujícím příkladu kódu, který naplňuje datovou sadu s názvem `DsCategories1`:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
4.  (Volitelné) Přidejte příslušné tabulky styly a styly sloupců do mřížky.  
  
     Pokud neexistují žádné tabulky styly, zobrazí se v tabulce, ale s minimální formátování a všechny viditelné sloupce.  
  
### <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a>Chcete svázat data – ovládací prvek DataGrid více tabulek v datové sadě v Návrháři  
  
1.  Nastavit u tohoto prvku <xref:System.Windows.Forms.DataGrid.DataSource%2A> vlastnost na objekt obsahující data položky, které chcete vytvořit vazbu.  
  
2.  Pokud datová sada obsahuje související tabulky (to znamená, pokud obsahuje objekt relace), můžete nastavit <xref:System.Windows.Forms.DataGrid.DataMember%2A> nastavte název nadřazené tabulky.  
  
3.  Napište kód pro naplnění dataset.  
  
## <a name="see-also"></a>Viz také:
- [Přehled ovládacího prvku DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)
- [Postupy: Přidávání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Ovládací prvek DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
- [Windows Forms – datová vazba](../../../../docs/framework/winforms/windows-forms-data-binding.md)
- [Přístup k datům v sadě Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio)
