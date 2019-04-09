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
ms.openlocfilehash: 52d4fc32836a5d20bd99d8ebfd3119c761376e30
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098712"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>Postupy: Přidávání tlačítek Načíst, Uložit a Zrušit do ovládacího prvku Windows Forms BindingNavigator
<xref:System.Windows.Forms.BindingNavigator> Ovládací prvek se speciálním účelem <xref:System.Windows.Forms.ToolStrip> ovládací prvek, který je určený pro navigaci a manipulaci se ovládací prvky na formuláři, které jsou vázány na data.  
  
 Protože se jedná <xref:System.Windows.Forms.ToolStrip> ovládací prvek, <xref:System.Windows.Forms.BindingNavigator> součásti můžete snadno upravit tak, aby patří další nebo alternativní příkazy pro daného uživatele.  
  
 V následujícím postupu <xref:System.Windows.Forms.TextBox> ovládací prvek vázán na data a <xref:System.Windows.Forms.ToolStrip> ovládací prvek, který je přidán do formuláře je upravit tak, aby zahrnout načíst, uložit a stornovací tlačítka.  
  
### <a name="to-add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>Chcete-li přidat zatížení, uložte a stornovací tlačítka na komponentu BindingNavigator  
  
1.  Přidat <xref:System.Windows.Forms.TextBox> ovládací prvek do formuláře.  
  
2.  Vytvořte mu vazbu k <xref:System.Windows.Forms.BindingSource>, který je svázán se zdrojem dat. V tomto příkladu <xref:System.Windows.Forms.BindingSource> je vázán na databázi.  
  
3.  Po vygenerování adaptér datová sada a tabulky, přetáhněte <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku na formuláři.  
  
4.  Nastavte <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> vlastnost <xref:System.Windows.Forms.BindingSource> ve formuláři, který je vázán k ovládacím prvkům.  
  
5.  Vyberte <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku.  
  
6.  Klikněte na inteligentní označit piktogram (![piktogram inteligentní](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) proto **BindingNavigator úlohy** dialogové okno se zobrazí a vyberte **upravit položky**.  
  
     **Editor kolekce položek** se zobrazí.  
  
7.  V **Editor kolekce položek**, proveďte následující kroky:  
  
    1.  Přidat <xref:System.Windows.Forms.ToolStripSeparator> a tři <xref:System.Windows.Forms.ToolStripButton> položky tak, že vyberete příslušný typ <xref:System.Windows.Forms.ToolStripItem> a kliknete **přidat** tlačítko.  
  
    2.  Nastavte <xref:System.Windows.Forms.ToolStripItem.Name%2A> vlastnost tlačítek na hodnotu **LoadButton**, **SaveButton**, a **CancelButton**v uvedeném pořadí.  
  
    3.  Nastavte <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost tlačítek na hodnotu **zatížení**, **Uložit**, a **zrušit**.  
  
    4.  Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost pro každý z tlačítka **Text**. Alternativně nastavte tuto vlastnost na **Image** nebo **ImageAndText**a nastavit obrázek, který se zobrazí v <xref:System.Windows.Forms.ToolStripItem.Image%2A> vlastnost.  
  
    5.  Klikněte na tlačítko **OK** zavřete dialogové okno. Tlačítka jsou přidány do <xref:System.Windows.Forms.ToolStrip>.  
  
8.  Klikněte pravým tlačítkem na formuláři a zvolte **zobrazit kód**.  
  
9. V editoru kódu vyhledejte řádek kódu, který načte data do tabulky adaptéru. Tento kód se vygeneroval při nastavení datové vazby v kroku 2. Kód by měl vypadat přibližně takto: `TableAdapterName.Fill(DataSetName.TableName)`. Bude většinu pravděpodobně v formuláře <xref:System.Windows.Forms.Form.Load> událostí.  
  
10. Vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> událost **zatížení** <xref:System.Windows.Forms.ToolStripButton> jste vytvořili dříve a přesuňte tento kód načítání dat do něj.  
  
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
  
11. Vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> událost **Uložit** <xref:System.Windows.Forms.ToolStripButton> jste vytvořili dříve a napsat kód k aktualizaci dat v ovládacím prvku tabulka je vázána na.  
  
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
    > V některých případech <xref:System.Windows.Forms.BindingNavigator> již komponenty budou **Uložit** tlačítko, ale žádný kód bude byly vytvořeny v Návrháři formulářů Windows. V takovém případě můžete umístit v předchozím kódu <xref:System.Windows.Forms.ToolStripItem.Click> obslužné rutiny události pro toto tlačítko, místo vytvoření zcela nové tlačítko na <xref:System.Windows.Forms.ToolStrip>. Nicméně je tlačítko neaktivní ve výchozím nastavení, proto musíte nastavit <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> vlastnost tlačítka `true` má tlačítko funkce správně.
  
12. Vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> událost **zrušit** <xref:System.Windows.Forms.ToolStripButton> vytvořené dříve a napsat kód, který zrušit všechny změny na datový záznam, který se zobrazí.  
  
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
    >  <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> Metoda působí na řádek dat. Uložte všechny změny, které pronesete při zobrazení jednotlivých záznamu před přechodu na další záznam.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [Ovládací prvek BindingNavigator](bindingnavigator-control-windows-forms.md)
- [BindingSource – přehled komponenty](bindingsource-component-overview.md)
