---
title: "Postupy: Vytváření podřízených formulářů MDI"
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
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7a779229a61d18ec835197bafac66579c026e2ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-mdi-child-forms"></a><span data-ttu-id="7d72e-102">Postupy: Vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="7d72e-102">How to: Create MDI Child Forms</span></span>
<span data-ttu-id="7d72e-103">Podřízených formulářů MDI jsou důležitou součástí [aplikace rozhraní více dokumentů (MDI)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), jak tyto formuláře jsou center interakce s uživatelem.</span><span class="sxs-lookup"><span data-stu-id="7d72e-103">MDI child forms are an essential element of [Multiple-Document Interface (MDI) Applications](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), as these forms are the center of user interaction.</span></span>  
  
 <span data-ttu-id="7d72e-104">V následujícím postupu vytvoříte MDI podřízené formulář, který zobrazuje <xref:System.Windows.Forms.RichTextBox> řízení, podobně jako většině textových aplikace.</span><span class="sxs-lookup"><span data-stu-id="7d72e-104">In the following procedure, you will create MDI child form that displays a <xref:System.Windows.Forms.RichTextBox> control, similar to most word-processing applications.</span></span> <span data-ttu-id="7d72e-105">Nahraďte <xref:System.Windows.Forms> řídit pomocí dalších kontroly, jako <xref:System.Windows.Forms.DataGridView> ovládací prvek nebo kombinaci prvků umožňuje vytvářet podřízeného MDI windows (a při rozšíření aplikace MDI) s různé možnosti.</span><span class="sxs-lookup"><span data-stu-id="7d72e-105">Substituting the <xref:System.Windows.Forms> control with other controls, such as the <xref:System.Windows.Forms.DataGridView> control, or a mixture of controls enables you to create MDI child windows (and, by extension, MDI applications) with diverse possibilities.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d72e-106">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="7d72e-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7d72e-107">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="7d72e-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7d72e-108">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="7d72e-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-mdi-child-forms"></a><span data-ttu-id="7d72e-109">Chcete-li vytvořit podřízeného MDI formuláře</span><span class="sxs-lookup"><span data-stu-id="7d72e-109">To create MDI child forms</span></span>  
  
1.  <span data-ttu-id="7d72e-110">Vytvoření nového projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7d72e-110">Create a new Windows Forms project.</span></span> <span data-ttu-id="7d72e-111">V **Windows vlastnosti** pro daný formulář, nastavte jeho <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost `true`a jeho `WindowsState` vlastnost `Maximized`.</span><span class="sxs-lookup"><span data-stu-id="7d72e-111">In **the Properties Windows** for the form, set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`, and its `WindowsState` property to `Maximized`.</span></span>  
  
     <span data-ttu-id="7d72e-112">Tento formulář označí jako kontejner MDI pro podřízené windows.</span><span class="sxs-lookup"><span data-stu-id="7d72e-112">This designates the form as an MDI container for child windows.</span></span>  
  
2.  <span data-ttu-id="7d72e-113">Z `Toolbox`, přetáhněte ji <xref:System.Windows.Forms.MenuStrip> ovládacího prvku formuláře.</span><span class="sxs-lookup"><span data-stu-id="7d72e-113">From the `Toolbox`, drag a <xref:System.Windows.Forms.MenuStrip> control to the form.</span></span> <span data-ttu-id="7d72e-114">Nastavte její `Text` vlastnost **soubor**.</span><span class="sxs-lookup"><span data-stu-id="7d72e-114">Set its `Text` property to **File**.</span></span>  
  
3.  <span data-ttu-id="7d72e-115">Klikněte na výpustky (...) vedle položky **položky** vlastnost a klikněte na **přidat** přidat dva podřízené položky nabídky pruhu pro nástroj.</span><span class="sxs-lookup"><span data-stu-id="7d72e-115">Click the ellipses (…) next to the **Items** property, and click **Add** to add two child tool strip menu items.</span></span> <span data-ttu-id="7d72e-116">Nastavte `Text` vlastnost pro tyto položky k **nový** a **okno**.</span><span class="sxs-lookup"><span data-stu-id="7d72e-116">Set the `Text` property for these items to **New** and **Window**.</span></span>  
  
4.  <span data-ttu-id="7d72e-117">V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt, přejděte na **přidat**a potom vyberte **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="7d72e-117">In **Solution Explorer**, right-click the project, point to **Add**, and then select **Add New Item**.</span></span>  
  
5.  <span data-ttu-id="7d72e-118">V **přidat novou položku** dialogové okno, vyberte **formuláře Windows** (v [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo v [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) nebo **Windows Forms aplikace (.NET)** (v [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) z **šablony** podokně.</span><span class="sxs-lookup"><span data-stu-id="7d72e-118">In the **Add New Item** dialog box, select **Windows Form** (in [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or in [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) or **Windows Forms Application (.NET)** (in [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) from the **Templates** pane.</span></span> <span data-ttu-id="7d72e-119">V **název** pole, název formuláře **Form2**.</span><span class="sxs-lookup"><span data-stu-id="7d72e-119">In the **Name** box, name the form **Form2**.</span></span> <span data-ttu-id="7d72e-120">Klikněte **otevřete** tlačítko pro přidání formuláře do projektu.</span><span class="sxs-lookup"><span data-stu-id="7d72e-120">Click the **Open** button to add the form to the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7d72e-121">Podřízené formuláře MDI, kterou jste vytvořili v tomto kroku je standardní formuláře systému Windows.</span><span class="sxs-lookup"><span data-stu-id="7d72e-121">The MDI child form you created in this step is a standard Windows Form.</span></span> <span data-ttu-id="7d72e-122">Jako takový má <xref:System.Windows.Forms.Form.Opacity%2A> vlastnosti, která vám umožňuje řídit průhlednost formuláře.</span><span class="sxs-lookup"><span data-stu-id="7d72e-122">As such, it has an <xref:System.Windows.Forms.Form.Opacity%2A> property, which enables you to control the transparency of the form.</span></span> <span data-ttu-id="7d72e-123">Ale <xref:System.Windows.Forms.Form.Opacity%2A> vlastnost byl navržený pro windows nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="7d72e-123">However, the <xref:System.Windows.Forms.Form.Opacity%2A> property was designed for top-level windows.</span></span> <span data-ttu-id="7d72e-124">Nepoužívejte ho s podřízených formulářů MDI, protože může docházet k potížím Malování.</span><span class="sxs-lookup"><span data-stu-id="7d72e-124">Do not use it with MDI child forms, as painting problems can occur.</span></span>  
  
     <span data-ttu-id="7d72e-125">Šablona pro vaše podřízených formulářů MDI bude tento formulář.</span><span class="sxs-lookup"><span data-stu-id="7d72e-125">This form will be the template for your MDI child forms.</span></span>  
  
     <span data-ttu-id="7d72e-126">**Návrhář formulářů Windows** otevře, zobrazení **Form2**.</span><span class="sxs-lookup"><span data-stu-id="7d72e-126">The **Windows Forms Designer** opens, displaying **Form2**.</span></span>  
  
6.  <span data-ttu-id="7d72e-127">Z **sada nástrojů**, přetáhněte ji **RichTextBox** ovládacího prvku do formuláře.</span><span class="sxs-lookup"><span data-stu-id="7d72e-127">From the **Toolbox**, drag a **RichTextBox** control to the form.</span></span>  
  
7.  <span data-ttu-id="7d72e-128">V **vlastnosti** nastavte `Anchor` vlastnost **Top, levém** a `Dock` vlastnost **vyplnění**.</span><span class="sxs-lookup"><span data-stu-id="7d72e-128">In the **Properties** window, set the `Anchor` property to **Top, Left** and the `Dock` property to **Fill**.</span></span>  
  
     <span data-ttu-id="7d72e-129">To způsobí, že <xref:System.Windows.Forms.RichTextBox> ovládacího prvku na nejbližší oblast podřízené formuláře MDI, i v případě, že se změnila velikost formuláře.</span><span class="sxs-lookup"><span data-stu-id="7d72e-129">This causes the <xref:System.Windows.Forms.RichTextBox> control to completely fill the area of the MDI child form, even when the form is resized.</span></span>  
  
8.  <span data-ttu-id="7d72e-130">Klikněte dvakrát **nový** položku vytvoříte <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro ni.</span><span class="sxs-lookup"><span data-stu-id="7d72e-130">Double click the **New** menu item to create a <xref:System.Windows.Forms.Control.Click> event handler for it.</span></span>  
  
9. <span data-ttu-id="7d72e-131">Vložení kódu podobný následujícímu pro vytvoření nového formuláře MDI podřízené, když uživatel klikne **nový** položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="7d72e-131">Insert code similar to the following to create a new MDI child form when the user clicks the **New** menu item.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7d72e-132">V následujícím příkladu, zpracuje obslužná rutina události <xref:System.Windows.Forms.Control.Click> událost pro `MenuItem2`.</span><span class="sxs-lookup"><span data-stu-id="7d72e-132">In the following example, the event handler handles the <xref:System.Windows.Forms.Control.Click> event for `MenuItem2`.</span></span> <span data-ttu-id="7d72e-133">Mějte na paměti, v závislosti na tom, jaké jsou specifikace architektuře aplikace vaše **nový** nemusí být položka nabídky `MenuItem2`.</span><span class="sxs-lookup"><span data-stu-id="7d72e-133">Be aware that, depending on the specifics of your application architecture, your **New** menu item may not be `MenuItem2`.</span></span>  
  
    ```vb  
    Protected Sub MDIChildNew_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MenuItem2.Click  
       Dim NewMDIChild As New Form2()  
       'Set the Parent Form of the Child window.  
       NewMDIChild.MdiParent = Me  
       'Display the new form.  
       NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    protected void MDIChildNew_Click(object sender, System.EventArgs e){  
       Form2 newMDIChild = new Form2();  
       // Set the Parent Form of the Child window.  
       newMDIChild.MdiParent = this;  
       // Display the new form.  
       newMDIChild.Show();  
    }  
    ```  
  
    ```cpp  
    private:  
       void menuItem2_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          Form2^ newMDIChild = gcnew Form2();  
          // Set the Parent Form of the Child window.  
          newMDIChild->MdiParent = this;  
          // Display the new form.  
          newMDIChild->Show();  
       }  
    ```  
  
     <span data-ttu-id="7d72e-134">V [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], přidejte následující `#include` direktivy v horní části Form1.h:</span><span class="sxs-lookup"><span data-stu-id="7d72e-134">In [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], add the following `#include` directive at the top of Form1.h:</span></span>  
  
    ```cpp  
    #include "Form2.h"  
    ```  
  
10. <span data-ttu-id="7d72e-135">V rozevíracím seznamu v horní části **vlastnosti** okně vyberte pruhu nabídky, která odpovídá **soubor** pruhu nabídky a sadu <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> vlastnost do okna <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="7d72e-135">In the drop-down list at the top of the **Properties** window, select the menu strip that corresponds to the **File** menu strip and set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to the Window <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
     <span data-ttu-id="7d72e-136">Tato akce povolí **okno** nabídky Spravovat seznam otevřete podřízených oken MDI s zatržení vedle active podřízeného okna.</span><span class="sxs-lookup"><span data-stu-id="7d72e-136">This will enable the **Window** menu to maintain a list of open MDI child windows with a check mark next to the active child window.</span></span>  
  
11. <span data-ttu-id="7d72e-137">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7d72e-137">Press F5 to run the application.</span></span> <span data-ttu-id="7d72e-138">Výběrem **nový** z **soubor** nabídky, můžete vytvořit nové MDI podřízených formulářů, které jsou zachovány přehled o v **okno** položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="7d72e-138">By selecting **New** from the **File** menu, you can create new MDI child forms, which are kept track of in the **Window** menu item.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7d72e-139">Když má podřízené formuláře MDI <xref:System.Windows.Forms.MainMenu> součást (s, obvykle struktury nabídky položek nabídky) a je otevřen v rámci nadřazené formuláře MDI, který má <xref:System.Windows.Forms.MainMenu> součást (s, obvykle struktury nabídky položek nabídek), v nabídce položky budou automaticky sloučení Pokud jste nastavili <xref:System.Windows.Forms.MenuItem.MergeType%2A> vlastnost (a volitelně <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> vlastnost).</span><span class="sxs-lookup"><span data-stu-id="7d72e-139">When an MDI child form has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items) and it is opened within an MDI parent form that has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items), the menu items will merge automatically if you have set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property (and optionally, the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property).</span></span> <span data-ttu-id="7d72e-140">Nastavte <xref:System.Windows.Forms.MenuItem.MergeType%2A> vlastnost objektu i <xref:System.Windows.Forms.MainMenu> součásti a všechny položky nabídky podřízené formuláře <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span><span class="sxs-lookup"><span data-stu-id="7d72e-140">Set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property of both <xref:System.Windows.Forms.MainMenu> components and all of the menu items of the child form to <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span></span> <span data-ttu-id="7d72e-141">Kromě toho nastavit <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> vlastnost tak, že v nabídce položky z obou nabídek zobrazí požadovaným způsobem.</span><span class="sxs-lookup"><span data-stu-id="7d72e-141">Additionally, set the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property so that the menu items from both menus appear in the desired order.</span></span> <span data-ttu-id="7d72e-142">Kromě toho mějte na paměti, že při zavření formuláře MDI nadřazené, každý z podřízeného MDI forms vyvolá <xref:System.Windows.Forms.Form.Closing> událostí před <xref:System.Windows.Forms.Form.Closing> je vyvolána událost pro nadřazený prvek MDI.</span><span class="sxs-lookup"><span data-stu-id="7d72e-142">Moreover, keep in mind that when you close an MDI parent form, each of the MDI child forms raises a <xref:System.Windows.Forms.Form.Closing> event before the <xref:System.Windows.Forms.Form.Closing> event for the MDI parent is raised.</span></span> <span data-ttu-id="7d72e-143">Zrušení podřízeného MDI <xref:System.Windows.Forms.Form.Closing> událostí nezabrání MDI nadřazeného objektu <xref:System.Windows.Forms.Form.Closing> vyvolání; události však <xref:System.ComponentModel.CancelEventArgs> argument pro nadřazený objekt MDI <xref:System.Windows.Forms.Form.Closing> událostí je teď možnost `true`.</span><span class="sxs-lookup"><span data-stu-id="7d72e-143">Canceling an MDI child's <xref:System.Windows.Forms.Form.Closing> event will not prevent the MDI parent's <xref:System.Windows.Forms.Form.Closing> event from being raised; however, the <xref:System.ComponentModel.CancelEventArgs> argument for the MDI parent's <xref:System.Windows.Forms.Form.Closing> event will now be set to `true`.</span></span> <span data-ttu-id="7d72e-144">Můžete vynutit nadřazené MDI a všech podřízených formulářů MDI zavřete nastavením <xref:System.ComponentModel.CancelEventArgs> argument `false`.</span><span class="sxs-lookup"><span data-stu-id="7d72e-144">You can force the MDI parent and all MDI child forms to close by setting the <xref:System.ComponentModel.CancelEventArgs> argument to `false`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d72e-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d72e-145">See Also</span></span>  
 [<span data-ttu-id="7d72e-146">Aplikace rozhraní více dokumentů (MDI)</span><span class="sxs-lookup"><span data-stu-id="7d72e-146">Multiple-Document Interface (MDI) Applications</span></span>](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [<span data-ttu-id="7d72e-147">Postupy: vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="7d72e-147">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="7d72e-148">Postupy: určení podřízeného prvku aktivního MDI</span><span class="sxs-lookup"><span data-stu-id="7d72e-148">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [<span data-ttu-id="7d72e-149">Postupy: odesílání dat do aktivního podřízeného MDI</span><span class="sxs-lookup"><span data-stu-id="7d72e-149">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [<span data-ttu-id="7d72e-150">Postupy: uspořádání podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="7d72e-150">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
