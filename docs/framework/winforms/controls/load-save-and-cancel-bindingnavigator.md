---
title: 'Postupy: Přidávání tlačítek Načíst, Uložit a Storno do ovládacího prvku Windows Forms BindingNavigator'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: 8f331c67dd22a6a9e2382ecc11d23c67cd2a5cbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540488"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>Postupy: Přidávání tlačítek Načíst, Uložit a Storno do ovládacího prvku Windows Forms BindingNavigator
<xref:System.Windows.Forms.BindingNavigator> Ovládací prvek je zvláštní účely <xref:System.Windows.Forms.ToolStrip> ovládací prvek, který je určený pro navigaci a manipulace s nimi ovládacích prvků formuláře, které jsou vázané na data.  
  
 Protože je <xref:System.Windows.Forms.ToolStrip> ovládací prvek, <xref:System.Windows.Forms.BindingNavigator> součást můžete snadno upravit tak, aby zahrnout další nebo alternativní příkazy pro uživatele.  
  
 V následujícím postupu <xref:System.Windows.Forms.TextBox> ovládací prvek vázán k datům a <xref:System.Windows.Forms.ToolStrip> zahrnout zatížení, uložit a Storno tlačítka se mění ovládací prvek, který je přidán do formuláře.  
  
### <a name="to-add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>Chcete-li přidat zatížení, uložte a stornovací tlačítka pro komponentu BindingNavigator  
  
1.  Přidat <xref:System.Windows.Forms.TextBox> ovládacího prvku do svého formuláře.  
  
2.  Vytvořte mu vazbu k <xref:System.Windows.Forms.BindingSource>, který je vázán na zdroj dat. V tomto příkladu <xref:System.Windows.Forms.BindingSource> je vázán k databázi.  
  
3.  Po vygenerování adaptér datovou sadu a tabulky, přetáhněte ji <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku do formuláře.  
  
4.  Nastavte <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> vlastnost, která má <xref:System.Windows.Forms.BindingSource> na formuláři, který je vázaný na ovládací prvky.  
  
5.  Vyberte <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku.  
  
6.  Klikněte na inteligentní značky glyfy (![inteligentní značky glyfy](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) proto **BindingNavigator úlohy** se zobrazí dialogové okno a vybrat **upravit položky**.  
  
     **Editor kolekce položek** se zobrazí.  
  
7.  V **Editor kolekce položek**, proveďte následující kroky:  
  
    1.  Přidat <xref:System.Windows.Forms.ToolStripSeparator> a tři <xref:System.Windows.Forms.ToolStripButton> položky výběrem odpovídající typ <xref:System.Windows.Forms.ToolStripItem> a kliknutím **přidat** tlačítko.  
  
    2.  Nastavte <xref:System.Windows.Forms.ToolStripItem.Name%2A> vlastnost tlačítek na**LoadButton**,**SaveButton**, a**CancelButton**, v uvedeném pořadí.  
  
    3.  Nastavte <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost tlačítek na**zatížení** `,` **Uložit**, a**zrušit**.  
  
    4.  Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost pro každou z tlačítka na**Text**. Alternativně nastavte tuto vlastnost na**Image**nebo**ImageAndText**a nastavte obrázek, který se zobrazí v <xref:System.Windows.Forms.ToolStripItem.Image%2A> vlastnost.  
  
    5.  Klikněte na tlačítko **OK** zavřete dialogové okno. Tlačítka se přidají do <xref:System.Windows.Forms.ToolStrip>.  
  
8.  Klikněte pravým tlačítkem na formulář a zvolte **kód zobrazení**.  
  
9. V editoru kódu najděte řádek kódu, který načte data do tabulky adaptéru. Tento kód byl vygenerován při nastavování datové vazby v kroku 2. Kód by mělo být podobné následujícímu: `TableAdapterName.Fill(DataSetName.TableName)`. Zruší většinu pravděpodobně v formuláře <xref:System.Windows.Forms.Form.Load> událostí.  
  
10. Vytvoření obslužné rutiny události pro <xref:System.Windows.Forms.ToolStripItem.Click> události**zatížení** <xref:System.Windows.Forms.ToolStripButton> jste dříve vytvořili a přesunout tento kód načítání dat do ní.  
  
     Váš kód by teď měl vypadat podobně jako následující:  
  
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
  
11. Vytvoření obslužné rutiny události pro <xref:System.Windows.Forms.ToolStripItem.Click> události **Uložit** <xref:System.Windows.Forms.ToolStripButton> jste předtím vytvořili, a je svázaná zápisu kódu aktualizace dat v tabulce ovládacího prvku.  
  
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
    >  V některých případech <xref:System.Windows.Forms.BindingNavigator> součást se už**Uložit** tlačítko, ale žádný kód bude byla vygenerována Návrhář formulářů Windows. V takovém případě můžete umístit předchozí kód <xref:System.Windows.Forms.ToolStripItem.Click> obslužné rutiny události pro toto tlačítko, místo vytvoření na úplně novou tlačítko <xref:System.Windows.Forms.ToolStrip>. Tlačítko je však zakázána ve výchozím nastavení, takže je třeba nastavit <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> vlastnost na tlačítko `true` tak, aby měl funkce tlačítko správně.  
  
12. Vytvoření obslužné rutiny události pro <xref:System.Windows.Forms.ToolStripItem.Click> události**zrušit** <xref:System.Windows.Forms.ToolStripButton> jste dříve vytvořili a napsat kód pro zrušit všechny provedené změny k záznamu dat, který se zobrazí.  
  
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
    >  <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> Metoda je vymezen na řádek dat. Uložte změny provedené při zobrazení jednotlivých záznamů před přejdete na další záznam.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.ToolStrip>  
 [Ovládací prvek BindingNavigator](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [Přehled komponenty BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)
