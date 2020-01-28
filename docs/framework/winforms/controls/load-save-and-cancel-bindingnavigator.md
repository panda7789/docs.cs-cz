---
title: Přidání tlačítek načíst, Uložit a Storno do ovládacího prvku BindingNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: ac862d163f1bd8b66f29160d836bc459e4bf4081
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745136"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>Postupy: Přidávání tlačítek Načíst, Uložit a Storno do ovládacího prvku Windows Forms BindingNavigator

<xref:System.Windows.Forms.BindingNavigator> ovládací prvek je <xref:System.Windows.Forms.ToolStrip> ovládací prvek pro zvláštní účely, který je určen pro navigaci a manipulaci s ovládacími prvky formuláře, které jsou vázány na data.

Vzhledem k tomu, že se jedná o ovládací prvek <xref:System.Windows.Forms.ToolStrip>, lze komponentu <xref:System.Windows.Forms.BindingNavigator> snadno upravit tak, aby zahrnovala další nebo alternativní příkazy pro uživatele.

V následujícím postupu je ovládací prvek <xref:System.Windows.Forms.TextBox> vázán na data a ovládací prvek <xref:System.Windows.Forms.ToolStrip> přidaný do formuláře se upraví tak, aby zahrnoval tlačítka načíst, Uložit a Storno.

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>Přidání tlačítek načíst, Uložit a Storno do komponenty BindingNavigator

1. V aplikaci Visual Studio přidejte ovládací prvek <xref:System.Windows.Forms.TextBox> do formuláře.

2. Vytvořte vazbu na <xref:System.Windows.Forms.BindingSource>, která je svázána se zdrojem dat. V tomto příkladu je <xref:System.Windows.Forms.BindingSource> svázán s databází.

3. Po vygenerování datové sady a adaptéru tabulky přetáhněte ovládací prvek <xref:System.Windows.Forms.BindingNavigator> do formuláře.

4. Nastavte vlastnost <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> ovládacího prvku <xref:System.Windows.Forms.BindingNavigator> na <xref:System.Windows.Forms.BindingSource> ve formuláři, který je svázán s ovládacími prvky.

5. Vyberte ovládací prvek <xref:System.Windows.Forms.BindingNavigator>.

6. Klikněte na glyf inteligentních značek (![glyf inteligentních značek](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), aby se zobrazil dialog **úlohy BindingNavigator** , a vyberte **Upravit položky**.

     Zobrazí se **Editor kolekce Items** .

7. V **editoru kolekce položek**proveďte následující:

    1. Přidejte <xref:System.Windows.Forms.ToolStripSeparator> a tři <xref:System.Windows.Forms.ToolStripButton> položky výběrem příslušného typu <xref:System.Windows.Forms.ToolStripItem> a kliknutím na tlačítko **Přidat** .

    2. Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.Name%2A> pro tlačítka na **LoadButton**, **SaveButton**a **CancelButton**v uvedeném pořadí.

    3. Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.Text%2A> pro tlačítka na **načíst**, **Uložit**a **Zrušit**.

    4. Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> pro každé z tlačítek na **text**. Alternativně můžete tuto vlastnost nastavit na hodnotu **Image** nebo **ImageAndText**a nastavit obrázek, který se má zobrazit ve vlastnosti <xref:System.Windows.Forms.ToolStripItem.Image%2A>.

    5. Dialogové okno zavřete kliknutím na tlačítko **OK** . Tlačítka jsou přidána do <xref:System.Windows.Forms.ToolStrip>.

8. Klikněte pravým tlačítkem na formulář a vyberte **Zobrazit kód**.

9. V editoru kódu vyhledejte řádek kódu, který načte data do adaptéru tabulky. Tento kód byl vygenerován při nastavení datové vazby v kroku 2. Kód by měl vypadat přibližně takto: `TableAdapterName.Fill(DataSetName.TableName)`. Pravděpodobně bude v události <xref:System.Windows.Forms.Form.Load> formuláře.

10. Vytvořte obslužnou rutinu události pro událost <xref:System.Windows.Forms.ToolStripItem.Click> **zátěžového** <xref:System.Windows.Forms.ToolStripButton>, kterou jste vytvořili dříve, a přesuňte do ní kód pro načtení dat.

     Váš kód by teď měl vypadat nějak takto:

    ```vb
    Private Sub LoadButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles LoadButton.Click
        TableAdapterName.Fill(DataSetName.TableName)
    End Sub
    ```

    ```csharp
    private void LoadButton_Click(System.Object sender,
        System.EventArgs e)
    {
        TableAdapterName.Fill(DataSetName.TableName);
    }
    ```

11. Vytvořte obslužnou rutinu události pro událost <xref:System.Windows.Forms.ToolStripItem.Click> **uloženého**<xref:System.Windows.Forms.ToolStripButton>, kterou jste vytvořili dříve, a napište kód pro aktualizaci dat v tabulce, ke které je ovládací prvek vázán.

    ```vb
    Private Sub SaveButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles SaveButton.Click
        TableAdapterName.Update(DataSetName.TableName)
    End Sub
    ```

    ```csharp
    private void SaveButton_Click(System.Object sender,
        System.EventArgs e)
    {
        TableAdapterName.Update(DataSetName.TableName);
    }
    ```

    > [!NOTE]
    > V některých případech již komponenta <xref:System.Windows.Forms.BindingNavigator> obsahuje tlačítko **Uložit** , ale Návrhář formulářů nevytvořil žádný kód. V tomto případě můžete umístit předchozí kód do obslužné rutiny události <xref:System.Windows.Forms.ToolStripItem.Click> pro toto tlačítko místo vytvoření zcela nového tlačítka v <xref:System.Windows.Forms.ToolStrip>. Toto tlačítko je ale ve výchozím nastavení zakázané, takže musíte nastavit vlastnost <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> tlačítka, aby `true`, aby správně fungovalo tlačítko.

12. Vytvořte obslužnou rutinu události pro událost <xref:System.Windows.Forms.ToolStripItem.Click> <xref:System.Windows.Forms.ToolStripButton> **zrušení** , kterou jste vytvořili dříve, a napište kód, který zruší všechny změny v zobrazeném datovém záznamu.

    ```vb
    Private Sub CancelButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles CancelButton.Click
        BindingSourceName.CancelEdit()
    End Sub
    ```

    ```csharp
    private void CancelButton_Click(System.Object sender, System.EventArgs e)
    {
        BindingSourceName.CancelEdit();
    }
    ```

    > [!NOTE]
    > Metoda <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> je vymezena na řádek dat. Před přechodem na další záznam uložte všechny změny, které provedete při prohlížení tohoto jednotlivého záznamu.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [Ovládací prvek BindingNavigator](bindingnavigator-control-windows-forms.md)
- [Přehled komponenty BindingSource](bindingsource-component-overview.md)
