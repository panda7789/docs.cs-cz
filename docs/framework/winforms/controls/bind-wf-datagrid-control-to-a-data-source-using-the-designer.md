---
title: Svázání ovládacího prvku DataGrid ke zdroji dat pomocí návrháře
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
ms.openlocfilehash: cc0a74eca40e34f06b065980d25d922b919b0c3c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744085"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a>Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat pomocí Návrháře

> [!NOTE]
> Ovládací prvek <xref:System.Windows.Forms.DataGridView> nahrazuje a přidává funkce do ovládacího prvku <xref:System.Windows.Forms.DataGrid>; Nicméně ovládací prvek <xref:System.Windows.Forms.DataGrid> se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

 Ovládací prvek model Windows Forms <xref:System.Windows.Forms.DataGrid> je speciálně navržený tak, aby zobrazoval informace ze zdroje dat. Ovládací prvek navážete v době návrhu nastavením vlastností <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> nebo v době spuštění voláním metody <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>. I když můžete zobrazit data z nejrůznějších zdrojů dat, nejdůležitější zdroje jsou datové sady a zobrazení dat.

 Pokud je zdroj dat k dispozici v době návrhu, například pokud formulář obsahuje instanci datové sady nebo zobrazení dat, můžete vytvořit vazby mezi mřížkou a zdrojem dat v době návrhu. Pak můžete zobrazit náhled toho, jak budou data vypadat v mřížce.

 Mřížku lze také vytvořit pomocí kódu programu v době běhu. To je užitečné, pokud chcete nastavit zdroj dat na základě informací, které získáte v době běhu. Aplikace může například uživateli umožnit zadání názvu tabulky, která se má zobrazit. Je také nutné v situacích, kdy zdroj dat neexistuje v době návrhu. To zahrnuje zdroje dat, jako jsou pole, kolekce, netypové datové sady a čtečky dat.

 Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.DataGrid>. Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md). V sadě Visual Studio 2005 není ovládací prvek <xref:System.Windows.Forms.DataGrid> ve výchozím nastavení součástí **sady nástrojů** . Informace o jeho přidání naleznete v tématu [How to: Add Items to a panel nástrojů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)). Kromě toho v aplikaci Visual Studio 2005 můžete použít okno **zdroje dat** pro datovou vazbu při návrhu. Další informace najdete v tématu [vázání ovládacích prvků k datům v aplikaci Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).

## <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a>Pro datovou datovou vazby ovládacího prvku DataGrid k jedné tabulce v Návrháři

1. Nastavte vlastnost <xref:System.Windows.Forms.DataGrid.DataSource%2A> ovládacího prvku na objekt obsahující datové položky, se kterými chcete vytvořit vazby.

2. Pokud je zdrojem dat datová sada, nastavte vlastnost <xref:System.Windows.Forms.DataGrid.DataMember%2A> na název tabulky, ke které se má vytvořit vazba.

3. Pokud je zdrojem dat datová sada nebo zobrazení dat založené na tabulce DataSet, přidejte do formuláře kód, který datovou sadu vyplní.

     Přesný kód, který použijete, závisí na tom, kde datová sada získává data. Pokud je datová sada naplněna přímo z databáze, obvykle zavoláte metodu `Fill` datového adaptéru, jak je uvedeno v následujícím příkladu kódu, který naplňuje datovou sadu s názvem `DsCategories1`:

    ```vb
    sqlDataAdapter1.Fill(DsCategories1)
    ```

    ```csharp
    sqlDataAdapter1.Fill(DsCategories1);
    ```

    ```cpp
    sqlDataAdapter1->Fill(dsCategories1);
    ```

4. Volitelné Přidejte do mřížky vhodné styly tabulek a sloupců.

     Pokud neexistují žádné styly tabulek, zobrazí se tabulka, ale s minimálním formátováním a všemi zobrazenými sloupci.

## <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a>Vazba ovládacího prvku DataGrid na více tabulek v datové sadě v Návrháři

1. Nastavte vlastnost <xref:System.Windows.Forms.DataGrid.DataSource%2A> ovládacího prvku na objekt obsahující datové položky, se kterými chcete vytvořit vazby.

2. Pokud datová sada obsahuje související tabulky (to znamená, pokud obsahuje objekt relace), nastavte vlastnost <xref:System.Windows.Forms.DataGrid.DataMember%2A> na název nadřazené tabulky.

3. Zadejte kód, který bude datovou sadu vyplnit.

## <a name="see-also"></a>Viz také

- [Přehled ovládacího prvku DataGrid](datagrid-control-overview-windows-forms.md)
- [Postupy: Přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
- [Windows Forms – datová vazba](../windows-forms-data-binding.md)
- [Přístup k datům v sadě Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio)
