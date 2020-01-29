---
title: Přidání a odebrání karet pomocí TabControl
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
ms.openlocfilehash: 8292d8441f9b47334b98736cf3282c846673dbb4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732714"
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol"></a><span data-ttu-id="a7cc3-102">Postupy: Přidání a odebrání karet s prvkem Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="a7cc3-102">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>
<span data-ttu-id="a7cc3-103">Ve výchozím nastavení obsahuje ovládací prvek <xref:System.Windows.Forms.TabControl> dva ovládací prvky <xref:System.Windows.Forms.TabPage>.</span><span class="sxs-lookup"><span data-stu-id="a7cc3-103">By default, a <xref:System.Windows.Forms.TabControl> control contains two <xref:System.Windows.Forms.TabPage> controls.</span></span> <span data-ttu-id="a7cc3-104">K těmto kartám máte přístup pomocí vlastnosti <xref:System.Windows.Forms.TabControl.TabPages%2A>.</span><span class="sxs-lookup"><span data-stu-id="a7cc3-104">You can access these tabs through the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
### <a name="to-add-a-tab-programmatically"></a><span data-ttu-id="a7cc3-105">Chcete-li přidat kartu programově</span><span class="sxs-lookup"><span data-stu-id="a7cc3-105">To add a tab programmatically</span></span>  
  
- <span data-ttu-id="a7cc3-106">Použijte metodu <xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A> vlastnosti <xref:System.Windows.Forms.TabControl.TabPages%2A>.</span><span class="sxs-lookup"><span data-stu-id="a7cc3-106">Use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
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
  
### <a name="to-remove-a-tab-programmatically"></a><span data-ttu-id="a7cc3-107">Postup při programovém odebrání karty</span><span class="sxs-lookup"><span data-stu-id="a7cc3-107">To remove a tab programmatically</span></span>  
  
- <span data-ttu-id="a7cc3-108">Chcete-li odebrat vybrané karty, použijte metodu <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> vlastnosti <xref:System.Windows.Forms.TabControl.TabPages%2A>.</span><span class="sxs-lookup"><span data-stu-id="a7cc3-108">To remove selected tabs, use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
     <span data-ttu-id="a7cc3-109">-nebo-</span><span class="sxs-lookup"><span data-stu-id="a7cc3-109">-or-</span></span>  
  
- <span data-ttu-id="a7cc3-110">Chcete-li odebrat všechny karty, použijte metodu <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> vlastnosti <xref:System.Windows.Forms.TabControl.TabPages%2A>.</span><span class="sxs-lookup"><span data-stu-id="a7cc3-110">To remove all tabs, use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a7cc3-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7cc3-111">See also</span></span>

- [<span data-ttu-id="a7cc3-112">Přehled ovládacího prvku TabControl</span><span class="sxs-lookup"><span data-stu-id="a7cc3-112">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="a7cc3-113">Postupy: Přidání ovládacího prvku na kartu</span><span class="sxs-lookup"><span data-stu-id="a7cc3-113">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="a7cc3-114">Postupy: Zákaz karet</span><span class="sxs-lookup"><span data-stu-id="a7cc3-114">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="a7cc3-115">Postupy: Změna vzhledu Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="a7cc3-115">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
