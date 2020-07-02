---
title: Přidání a odebrání karet pomocí TabControl
description: Naučte se přidávat a odebírat karty pomocí ovládacího prvku model Windows Forms TabControl, který obsahuje dva ovládací prvky TabPage. Přístup k těmto kartám získáte pomocí vlastnosti objekty TabPages.
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
ms.openlocfilehash: 7e67d0bbc13bd7d9c8835dc6fb9b9c5c9333b8bf
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618074"
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol"></a><span data-ttu-id="e12d1-104">Postupy: Přidání a odebrání karet s prvkem Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="e12d1-104">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>
<span data-ttu-id="e12d1-105">Ve výchozím nastavení <xref:System.Windows.Forms.TabControl> ovládací prvek obsahuje dva <xref:System.Windows.Forms.TabPage> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="e12d1-105">By default, a <xref:System.Windows.Forms.TabControl> control contains two <xref:System.Windows.Forms.TabPage> controls.</span></span> <span data-ttu-id="e12d1-106">K těmto kartám máte přístup prostřednictvím <xref:System.Windows.Forms.TabControl.TabPages%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e12d1-106">You can access these tabs through the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
### <a name="to-add-a-tab-programmatically"></a><span data-ttu-id="e12d1-107">Chcete-li přidat kartu programově</span><span class="sxs-lookup"><span data-stu-id="e12d1-107">To add a tab programmatically</span></span>  
  
- <span data-ttu-id="e12d1-108">Použijte <xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A> metodu <xref:System.Windows.Forms.TabControl.TabPages%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e12d1-108">Use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
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
  
### <a name="to-remove-a-tab-programmatically"></a><span data-ttu-id="e12d1-109">Postup při programovém odebrání karty</span><span class="sxs-lookup"><span data-stu-id="e12d1-109">To remove a tab programmatically</span></span>  
  
- <span data-ttu-id="e12d1-110">Chcete-li odebrat vybrané karty, použijte <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> metodu <xref:System.Windows.Forms.TabControl.TabPages%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e12d1-110">To remove selected tabs, use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
     <span data-ttu-id="e12d1-111">-nebo-</span><span class="sxs-lookup"><span data-stu-id="e12d1-111">-or-</span></span>  
  
- <span data-ttu-id="e12d1-112">Chcete-li odebrat všechny karty, použijte <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> metodu <xref:System.Windows.Forms.TabControl.TabPages%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e12d1-112">To remove all tabs, use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e12d1-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e12d1-113">See also</span></span>

- [<span data-ttu-id="e12d1-114">TabControl – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e12d1-114">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="e12d1-115">Postupy: Přidání ovládacího prvku na kartu</span><span class="sxs-lookup"><span data-stu-id="e12d1-115">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="e12d1-116">Postupy: Zákaz stránek karet</span><span class="sxs-lookup"><span data-stu-id="e12d1-116">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="e12d1-117">Postupy: Změna vzhledu Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="e12d1-117">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
