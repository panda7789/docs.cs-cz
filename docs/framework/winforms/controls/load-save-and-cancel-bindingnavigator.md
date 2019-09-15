---
title: 'Postupy: Přidávání tlačítek Načíst, Uložit a Zrušit do ovládacího prvku Windows Forms BindingNavigator'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: 2d4867c0bc4feb7b43e15614fc56a3c709cef9e7
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991740"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>Postupy: Přidávání tlačítek Načíst, Uložit a Zrušit do ovládacího prvku Windows Forms BindingNavigator

Ovládací prvek je zvláštním účelem <xref:System.Windows.Forms.ToolStrip> , který je určen pro navigaci a manipulaci s ovládacími prvky formuláře, které jsou vázány na data. <xref:System.Windows.Forms.BindingNavigator>

Vzhledem k tomu <xref:System.Windows.Forms.BindingNavigator> , <xref:System.Windows.Forms.ToolStrip> že se jedná o ovládací prvek, lze komponentu snadno upravit tak, aby zahrnovala další nebo alternativní příkazy pro uživatele.

V následujícím postupu <xref:System.Windows.Forms.TextBox> je ovládací prvek vázán na data <xref:System.Windows.Forms.ToolStrip> a ovládací prvek přidaný do formuláře se upraví tak, aby zahrnoval tlačítka načíst, Uložit a Storno.

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>Přidání tlačítek načíst, Uložit a Storno do komponenty BindingNavigator

1. V aplikaci Visual Studio přidejte <xref:System.Windows.Forms.TextBox> ovládací prvek do formuláře.

2. Vytvořte vazbu na objekt <xref:System.Windows.Forms.BindingSource>, který je svázán se zdrojem dat. V <xref:System.Windows.Forms.BindingSource> tomto příkladu je svázána s databází.

3. Po vygenerování datové sady a adaptéru tabulky přetáhněte <xref:System.Windows.Forms.BindingNavigator> ovládací prvek do formuláře.

4. <xref:System.Windows.Forms.BindingNavigator> Nastavte <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> vlastnost ovládacíhoprvkunaformuláři,kterýjesvázánsovládacímiprvky.<xref:System.Windows.Forms.BindingSource>

5. <xref:System.Windows.Forms.BindingNavigator> Vyberte ovládací prvek.

6. Klikněte na glyf inteligentních značek (![inteligentní značky glyf](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), aby se zobrazil dialog **úlohy BindingNavigator** , a vyberte **Upravit položky**.

     Zobrazí se **Editor kolekce Items** .

7. V **editoru kolekce položek**proveďte následující:

    1. Přidejte a tři <xref:System.Windows.Forms.ToolStripButton> položky<xref:System.Windows.Forms.ToolStripItem> výběrem příslušného typu a kliknutím na tlačítko **Přidat.** <xref:System.Windows.Forms.ToolStripSeparator>

    2. Nastavte vlastnost tlačítek na **LoadButton**, **SaveButton**a CancelButton v uvedeném pořadí. <xref:System.Windows.Forms.ToolStripItem.Name%2A>

    3. Nastavte vlastnost tlačítek na **načíst**, **Uložit**a **zrušit.** <xref:System.Windows.Forms.ToolStripItem.Text%2A>

    4. Nastavte vlastnost pro každé z tlačítek na text. <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> Alternativně můžete tuto vlastnost nastavit na hodnotu **Image** nebo **ImageAndText**a nastavit obrázek, který se má <xref:System.Windows.Forms.ToolStripItem.Image%2A> zobrazit ve vlastnosti.

    5. Kliknutím na **OK** zavřete dialogové okno. Tlačítka jsou přidána do <xref:System.Windows.Forms.ToolStrip>.

8. Klikněte pravým tlačítkem na formulář a vyberte **Zobrazit kód**.

9. V editoru kódu vyhledejte řádek kódu, který načte data do adaptéru tabulky. Tento kód byl vygenerován při nastavení datové vazby v kroku 2. Kód by měl vypadat přibližně takto: `TableAdapterName.Fill(DataSetName.TableName)`. Bude pravděpodobně v <xref:System.Windows.Forms.Form.Load> události formuláře.

10. Vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> událost **zatížení** <xref:System.Windows.Forms.ToolStripButton> , kterou jste vytvořili dříve, a přesuňte do ní kód pro načtení dat.

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

11. Vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> událost **uložení** <xref:System.Windows.Forms.ToolStripButton> , kterou jste vytvořili dříve, a napište kód pro aktualizaci dat v tabulce, ke které je ovládací prvek vázán.

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
    > V některých případech <xref:System.Windows.Forms.BindingNavigator> komponenta již obsahuje tlačítko **Save** , ale Návrhář formulářů negeneruje žádný kód. V tomto případě můžete umístit předchozí kód v <xref:System.Windows.Forms.ToolStripItem.Click> obslužné rutině události pro toto tlačítko místo vytvoření zcela nového tlačítka <xref:System.Windows.Forms.ToolStrip>na. Toto tlačítko je ale ve výchozím nastavení zakázané, takže musíte nastavit <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> vlastnost tlačítka na `true` , aby bylo tlačítko správně fungovat.

12. Vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> událost **zrušení** <xref:System.Windows.Forms.ToolStripButton> , kterou jste vytvořili dříve, a napište kód, který zruší všechny změny v zobrazeném datovém záznamu.

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
    > <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> Metoda je vymezena na řádek dat. Před přechodem na další záznam uložte všechny změny, které provedete při prohlížení tohoto jednotlivého záznamu.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [Ovládací prvek BindingNavigator](bindingnavigator-control-windows-forms.md)
- [Přehled komponenty BindingSource](bindingsource-component-overview.md)
