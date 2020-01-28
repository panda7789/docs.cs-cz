---
title: Vytvoření seznamu hlavní-podrobnosti pomocí ovládacího prvku DataGrid pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
ms.openlocfilehash: 0dea3dd88a8c6c2aceb894789ace8ef3b5c83632
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743382"
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a>Postupy: Vytváření hlavních-podrobných seznamů s ovládacím prvkem Windows Forms DataGrid pomocí Návrháře

> [!NOTE]
> Ovládací prvek <xref:System.Windows.Forms.DataGridView> nahrazuje a přidává funkce do ovládacího prvku <xref:System.Windows.Forms.DataGrid>; Nicméně ovládací prvek <xref:System.Windows.Forms.DataGrid> se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

 Pokud vaše <xref:System.Data.DataSet> obsahuje řadu souvisejících tabulek, můžete použít dva ovládací prvky <xref:System.Windows.Forms.DataGrid> k zobrazení dat ve formátu hlavní-podrobnosti. Jeden <xref:System.Windows.Forms.DataGrid> je označený jako hlavní mřížka a druhý je označený jako mřížka podrobností. Když vyberete položku v seznamu hlavní seznam, zobrazí se v seznamu podrobnosti všechny související podřízené položky. Pokud například vaše <xref:System.Data.DataSet> obsahuje tabulku Customers (zákazníci) a související tabulky Orders, zadali byste tabulku Customers (zákazníci), která bude hlavní mřížkou, a tabulkou objednávky, která bude mřížka podrobností. Když je zákazník vybraný z hlavní mřížky, v mřížce podrobností se zobrazí všechny objednávky přidružené k tomuto zákazníkovi v tabulce Orders.

 Následující postup vyžaduje projekt **aplikace systému Windows** (**soubor** > **Nový** > **projekt** > **vizuálu C#**  nebo **Visual Basic** > **klasické desktopové** > **model Windows Forms aplikaci**).

## <a name="to-create-a-master-details-list-in-the-designer"></a>Vytvoření seznamu hlavní-podrobnosti v Návrháři

1. Do formuláře přidejte dva ovládací prvky <xref:System.Windows.Forms.DataGrid>. Další informace naleznete v tématu [How to: Add Controls to model Windows Forms](how-to-add-controls-to-windows-forms.md). V sadě Visual Studio 2005 není ovládací prvek <xref:System.Windows.Forms.DataGrid> ve výchozím nastavení součástí **sady nástrojů** . Další informace najdete v tématu [Postup: Přidání položek do sady nástrojů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).

    > [!NOTE]
    > Následující kroky se nevztahují na Visual Studio 2005, který používá okno **zdroje dat** pro datovou vazbu při návrhu. Další informace naleznete v tématu [vázání ovládacích prvků k datům v aplikaci Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio) a [Postupy: zobrazení souvisejících dat v aplikaci model Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120)).

2. Přetáhněte dvě nebo více tabulek z **Průzkumník serveru** do formuláře.

3. V nabídce **data** vyberte možnost **Generovat datovou sadu**.

4. Nastavte vztahy mezi tabulkami pomocí návrháře XML. Podrobnosti najdete v tématu "postupy: vytvoření vztahů 1:1 na základě schémat XML a datových sad" na webu MSDN.

5. Uložte relace výběrem možnosti **Uložit vše** v nabídce **soubor** .

6. Nakonfigurujte <xref:System.Windows.Forms.DataGrid> ovládací prvek, který chcete nastavit jako hlavní mřížku, a to následujícím způsobem:

    1. V rozevíracím seznamu ve vlastnosti <xref:System.Windows.Forms.DataGrid.DataSource%2A> vyberte <xref:System.Data.DataSet>.

    2. Z rozevíracího seznamu ve vlastnosti <xref:System.Windows.Forms.DataGrid.DataMember%2A> vyberte hlavní tabulku (například "Customers").

7. Nakonfigurujte <xref:System.Windows.Forms.DataGrid> ovládací prvek, který chcete nastavit jako mřížku podrobností, následovně:

    1. V rozevíracím seznamu ve vlastnosti <xref:System.Windows.Forms.DataGrid.DataSource%2A> vyberte <xref:System.Data.DataSet>.

    2. Vyberte vztah (například Customers. CustOrd) mezi hlavní tabulkou a tabulkami podrobností z rozevíracího seznamu ve vlastnosti <xref:System.Windows.Forms.DataGrid.DataMember%2A>. Chcete-li zobrazit vztah, rozbalte uzel kliknutím na symbol plus ( **+** ) vedle položky hlavní tabulka v rozevíracím seznamu.

## <a name="see-also"></a>Viz také:

- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
- [Přehled ovládacího prvku DataGrid](datagrid-control-overview-windows-forms.md)
- [Postupy: Vázání ovládacího prvku Windows Forms DataGrid ke zdroji dat](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
