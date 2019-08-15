---
title: 'Postupy: Vytváření hlavních-podrobných seznamů s ovládacím prvkem Windows Forms DataGrid pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
ms.openlocfilehash: d1e598831954f17bdf3bc03ab880c344ca36aa5a
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039949"
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a>Postupy: Vytváření hlavních-podrobných seznamů s ovládacím prvkem Windows Forms DataGrid pomocí Návrháře

> [!NOTE]
>  Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.DataGridView> Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

 Pokud obsahuje řadu souvisejících tabulek, můžete použít dva <xref:System.Windows.Forms.DataGrid> ovládací prvky pro zobrazení dat ve formátu hlavní-podrobnosti. <xref:System.Data.DataSet> Jedna <xref:System.Windows.Forms.DataGrid> je určena jako hlavní mřížka a druhá je označena jako mřížka podrobností. Když vyberete položku v seznamu hlavní seznam, zobrazí se v seznamu podrobnosti všechny související podřízené položky. Pokud <xref:System.Data.DataSet> například obsahuje tabulku Customers (zákazníci) a související tabulky objednávek, zadali byste tabulku Customers (zákazníci), která bude hlavní mřížkou, a tabulkou Orders, která bude mřížka podrobností. Když je zákazník vybraný z hlavní mřížky, v mřížce podrobností se zobrazí všechny objednávky přidružené k tomuto zákazníkovi v tabulce Orders.

 Následující postup vyžaduje projekt **aplikace systému Windows** (**soubor** > **nového** > **projektu** > nebo**Visual C#**  **Visual Basic**  >   **Klasická desktopová** > **model Windows Forms aplikace**).

## <a name="to-create-a-master-details-list-in-the-designer"></a>Vytvoření seznamu hlavní-podrobnosti v Návrháři

1. Do formuláře <xref:System.Windows.Forms.DataGrid> přidejte dva ovládací prvky. Další informace najdete v tématu [jak: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms. V sadě Visual Studio 2005 <xref:System.Windows.Forms.DataGrid> není ovládací prvek ve výchozím nastavení součástí **sady nástrojů** . Další informace najdete v tématu [jak: Přidejte položky do sady nástrojů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).

    > [!NOTE]
    >  Následující kroky se nevztahují na Visual Studio 2005, který používá okno **zdroje dat** pro datovou vazbu při návrhu. Další informace naleznete v tématu [vázání ovládacích prvků k datům v aplikaci Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio) a [postup: Zobrazení souvisejících dat v aplikaci](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))model Windows Forms.

2. Přetáhněte dvě nebo více tabulek z **Průzkumník serveru** do formuláře.

3. V nabídce **data** vyberte možnost **Generovat datovou sadu**.

4. Nastavte vztahy mezi tabulkami pomocí návrháře XML. Podrobnosti najdete v části How to: Vytvoření vztahů 1:1 na webu MSDN schématu XML a datových sad

5. Uložte relace výběrem možnosti **Uložit vše** v nabídce **soubor** .

6. <xref:System.Windows.Forms.DataGrid> Nakonfigurujte ovládací prvek, který chcete nastavit jako hlavní mřížku, následovně:

    1. Vyberte z rozevíracího seznamu <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve vlastnosti. <xref:System.Data.DataSet>

    2. Z rozevíracího seznamu ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnosti vyberte hlavní tabulku (například "Customers").

7. <xref:System.Windows.Forms.DataGrid> Nakonfigurujte ovládací prvek, který chcete nastavit jako mřížku podrobností, následujícím způsobem:

    1. Vyberte z rozevíracího seznamu <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve vlastnosti. <xref:System.Data.DataSet>

    2. V rozevíracím seznamu ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnosti vyberte vztah (například Customers. CustOrd) mezi hlavními a podrobnými tabulkami. Chcete-li zobrazit vztah, rozbalte uzel kliknutím na symbol plus ( **+** ) vedle položky hlavní tabulka v rozevíracím seznamu.

## <a name="see-also"></a>Viz také:

- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
- [Přehled ovládacího prvku DataGrid](datagrid-control-overview-windows-forms.md)
- [Postupy: Navázání model Windows Forms ovládacího prvku DataGrid ke zdroji dat](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
