---
title: "Postupy: Přidání a odebrání karet s prvkem Windows Forms TabControl"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7691730f4f65d5d89f9f66f8fc1c8c6449702ae9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol"></a><span data-ttu-id="a16ad-102">Postupy: Přidání a odebrání karet s prvkem Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="a16ad-102">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>
<span data-ttu-id="a16ad-103">Ve výchozím nastavení <xref:System.Windows.Forms.TabControl> ovládací prvek obsahuje dva <xref:System.Windows.Forms.TabPage> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="a16ad-103">By default, a <xref:System.Windows.Forms.TabControl> control contains two <xref:System.Windows.Forms.TabPage> controls.</span></span> <span data-ttu-id="a16ad-104">Přistupujete prostřednictvím těchto karet <xref:System.Windows.Forms.TabControl.TabPages%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a16ad-104">You can access these tabs through the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
### <a name="to-add-a-tab-programmatically"></a><span data-ttu-id="a16ad-105">Chcete-li přidat na kartě prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="a16ad-105">To add a tab programmatically</span></span>  
  
-   <span data-ttu-id="a16ad-106">Použití <xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A> metodu <xref:System.Windows.Forms.TabControl.TabPages%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a16ad-106">Use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
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
  
### <a name="to-remove-a-tab-programmatically"></a><span data-ttu-id="a16ad-107">Chcete-li odebrat na kartě prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="a16ad-107">To remove a tab programmatically</span></span>  
  
-   <span data-ttu-id="a16ad-108">Pokud chcete odebrat vybrané karet, použijte <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> metodu <xref:System.Windows.Forms.TabControl.TabPages%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a16ad-108">To remove selected tabs, use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
     <span data-ttu-id="a16ad-109">-nebo-</span><span class="sxs-lookup"><span data-stu-id="a16ad-109">-or-</span></span>  
  
-   <span data-ttu-id="a16ad-110">Chcete-li odebrat všechny karty, použijte <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> metodu <xref:System.Windows.Forms.TabControl.TabPages%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a16ad-110">To remove all tabs, use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a16ad-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="a16ad-111">See Also</span></span>  
 [<span data-ttu-id="a16ad-112">Přehled ovládacího prvku TabControl</span><span class="sxs-lookup"><span data-stu-id="a16ad-112">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="a16ad-113">Postupy: Přidání ovládacího prvku na kartu</span><span class="sxs-lookup"><span data-stu-id="a16ad-113">How to: Add a Control to a Tab Page</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [<span data-ttu-id="a16ad-114">Postupy: Zákaz karet</span><span class="sxs-lookup"><span data-stu-id="a16ad-114">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [<span data-ttu-id="a16ad-115">Postupy: Změna vzhledu Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="a16ad-115">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
