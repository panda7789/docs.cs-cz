---
title: 'Postupy: Přidání a odebrání karet pomocí ovládacího prvku Windows Forms TabControl'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tabs [Windows Forms], removing from pages
- TabPage control
- TabControl control [Windows Forms], adding and removing tabs
- tabs [Windows Forms], adding to pages
- tab pages
ms.assetid: 66d4dfca-41e8-44e3-9c80-fb7ac4cb1619
ms.openlocfilehash: 4420f598f1243e6c834ecd82bb6ea7071cc95402
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707938"
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol"></a>Postupy: Přidání a odebrání karet pomocí ovládacího prvku Windows Forms TabControl
Ve výchozím nastavení <xref:System.Windows.Forms.TabControl> ovládací prvek obsahuje dva <xref:System.Windows.Forms.TabPage> ovládacích prvků. Můžete přistupovat prostřednictvím těchto karet <xref:System.Windows.Forms.TabControl.TabPages%2A> vlastnost.  
  
### <a name="to-add-a-tab-programmatically"></a>Chcete-li přidat na kartě prostřednictvím kódu programu  
  
-   Použití <xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A> metodu <xref:System.Windows.Forms.TabControl.TabPages%2A> vlastnost.  
  
    ```vb  
    Dim myTabPage As New TabPage()  
    myTabPage.Text = "TabPage" & (TabControl1.TabPages.Count + 1)  
    TabControl1.TabPages.Add(myTabPage)  
    ```  
  
    ```csharp  
    string title = "TabPage " + (tabControl1.TabCount + 1).ToString();  
    TabPage myTabPage = new TabPage(title);  
    tabControl1.TabPages.Add(myTabPage);  
    ```  
  
    ```cpp  
    String^ title = String::Concat("TabPage ",  
       (tabControl1->TabCount + 1).ToString());  
    TabPage^ myTabPage = gcnew TabPage(title);  
    tabControl1->TabPages->Add(myTabPage);  
    ```  
  
### <a name="to-remove-a-tab-programmatically"></a>Chcete-li odebrat kartu prostřednictvím kódu programu  
  
-   Pokud chcete odebrat vybrané karty, použijte <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> metodu <xref:System.Windows.Forms.TabControl.TabPages%2A> vlastnost.  
  
     -nebo-  
  
-   Chcete-li odebrat všechny karty, použijte <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> metodu <xref:System.Windows.Forms.TabControl.TabPages%2A> vlastnost.  
  
    ```vb  
    ' Removes the selected tab:  
    TabControl1.TabPages.Remove(TabControl1.SelectedTab)  
    ' Removes all the tabs:  
    TabControl1.TabPages.Clear()  
    ```  
  
    ```csharp  
    // Removes the selected tab:  
    tabControl1.TabPages.Remove(tabControl1.SelectedTab);  
    // Removes all the tabs:  
    tabControl1.TabPages.Clear();  
    ```  
  
    ```cpp  
    // Removes the selected tab:  
    tabControl1->TabPages->Remove(tabControl1->SelectedTab);  
    // Removes all the tabs:  
    tabControl1->TabPages->Clear();  
    ```  
  
## <a name="see-also"></a>Viz také:
- [Přehled ovládacího prvku TabControl](tabcontrol-control-overview-windows-forms.md)
- [Postupy: Přidání ovládacího prvku do stránky karty](how-to-add-a-control-to-a-tab-page.md)
- [Postupy: Zákaz stránek karet](how-to-disable-tab-pages.md)
- [Postupy: Změna vzhledu ovládacího prvku Windows Forms TabControl](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
