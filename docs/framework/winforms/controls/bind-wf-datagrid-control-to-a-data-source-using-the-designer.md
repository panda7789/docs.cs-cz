---
title: 'Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat pomocí Návrháře'
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
ms.openlocfilehash: 665a1af990aaf615c763c1c2eae508024d9de5c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917831"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a>Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat pomocí Návrháře

> [!NOTE]
> Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.DataGridView> Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

 Model Windows Forms <xref:System.Windows.Forms.DataGrid> ovládací prvek je speciálně navržen pro zobrazení informací ze zdroje dat. Ovládací prvek navážete v době návrhu nastavením <xref:System.Windows.Forms.DataGrid.DataSource%2A> vlastností a a <xref:System.Windows.Forms.DataGrid.DataMember%2A> v době <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> spuštění voláním metody. I když můžete zobrazit data z nejrůznějších zdrojů dat, nejdůležitější zdroje jsou datové sady a zobrazení dat.

 Pokud je zdroj dat k dispozici v době návrhu, například pokud formulář obsahuje instanci datové sady nebo zobrazení dat, můžete vytvořit vazby mezi mřížkou a zdrojem dat v době návrhu. Pak můžete zobrazit náhled toho, jak budou data vypadat v mřížce.

 Mřížku lze také vytvořit pomocí kódu programu v době běhu. To je užitečné, pokud chcete nastavit zdroj dat na základě informací, které získáte v době běhu. Aplikace může například uživateli umožnit zadání názvu tabulky, která se má zobrazit. Je také nutné v situacích, kdy zdroj dat neexistuje v době návrhu. To zahrnuje zdroje dat, jako jsou pole, kolekce, netypové datové sady a čtečky dat.

 Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.DataGrid> ovládací prvek. Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms. V sadě Visual Studio 2005 <xref:System.Windows.Forms.DataGrid> není ovládací prvek ve výchozím nastavení součástí **sady nástrojů** . Informace o jeho přidání naleznete v tématu [How to: Přidejte položky do sady nástrojů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)). Kromě toho v aplikaci Visual Studio 2005 můžete použít okno **zdroje dat** pro datovou vazbu při návrhu. Další informace najdete v tématu [vázání ovládacích prvků k datům v aplikaci Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).

## <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a>Pro datovou datovou vazby ovládacího prvku DataGrid k jedné tabulce v Návrháři

1. Nastavte <xref:System.Windows.Forms.DataGrid.DataSource%2A> vlastnost ovládacího prvku na objekt obsahující datové položky, se kterými chcete vytvořit vazby.

2. Pokud je zdrojem dat datová sada, nastavte <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnost na název tabulky, ke které se má vytvořit vazba.

3. Pokud je zdrojem dat datová sada nebo zobrazení dat založené na tabulce DataSet, přidejte do formuláře kód, který datovou sadu vyplní.

     Přesný kód, který použijete, závisí na tom, kde datová sada získává data. Pokud je datová sada naplněna přímo z databáze, obvykle zavoláte `Fill` metodu datového adaptéru, jak je uvedeno v následujícím příkladu kódu, který naplňuje datovou sadu s `DsCategories1`názvem:

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

1. Nastavte <xref:System.Windows.Forms.DataGrid.DataSource%2A> vlastnost ovládacího prvku na objekt obsahující datové položky, se kterými chcete vytvořit vazby.

2. Pokud datová sada obsahuje související tabulky (to znamená, pokud obsahuje objekt relace), nastavte <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnost na název nadřazené tabulky.

3. Zadejte kód, který bude datovou sadu vyplnit.

## <a name="see-also"></a>Viz také:

- [Přehled ovládacího prvku DataGrid](datagrid-control-overview-windows-forms.md)
- [Postupy: Přidání tabulek a sloupců do model Windows Forms ovládacího prvku DataGrid](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
- [Windows Forms – datová vazba](../windows-forms-data-binding.md)
- [Přístup k datům v sadě Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio)
