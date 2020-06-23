---
title: 'Postupy: Vytváření podřízených formulářů MDI'
description: Naučte se používat Visual Studio k vytvoření podřízeného formuláře MDI (Multiple Document Interface), který zobrazí ovládací prvek RichTextBox.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: 7fe5cde342f0f5ee078f888b7492cd4618bea5c4
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903178"
---
# <a name="how-to-create-mdi-child-forms"></a><span data-ttu-id="02c16-103">Postupy: vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="02c16-103">How to: Create MDI child forms</span></span>

<span data-ttu-id="02c16-104">Podřízené formuláře MDI jsou zásadním prvkem [aplikací rozhraní MDI (Multiple Document Interface)](multiple-document-interface-mdi-applications.md), protože tyto formuláře jsou centrem interakce s uživatelem.</span><span class="sxs-lookup"><span data-stu-id="02c16-104">MDI child forms are an essential element of [Multiple-Document Interface (MDI) applications](multiple-document-interface-mdi-applications.md), as these forms are the center of user interaction.</span></span>

<span data-ttu-id="02c16-105">V následujícím postupu použijete Visual Studio k vytvoření podřízeného formuláře MDI, který zobrazí <xref:System.Windows.Forms.RichTextBox> ovládací prvek podobný většině aplikací pro zpracování textu.</span><span class="sxs-lookup"><span data-stu-id="02c16-105">In the following procedure, you'll use Visual Studio to create an MDI child form that displays a <xref:System.Windows.Forms.RichTextBox> control, similar to most word-processing applications.</span></span> <span data-ttu-id="02c16-106">Nahrazením <xref:System.Windows.Forms> ovládacího prvku dalšími ovládacími prvky, jako je například <xref:System.Windows.Forms.DataGridView> ovládací prvek nebo kombinace ovládacích prvků, můžete vytvořit podřízená okna MDI (a, pomocí rozšíření, aplikací MDI) s různými možnostmi.</span><span class="sxs-lookup"><span data-stu-id="02c16-106">By substituting the <xref:System.Windows.Forms> control with other controls, such as the <xref:System.Windows.Forms.DataGridView> control, or a mixture of controls, you can create MDI child windows (and, by extension, MDI applications) with diverse possibilities.</span></span>

## <a name="create-mdi-child-forms"></a><span data-ttu-id="02c16-107">Vytvořit podřízené formuláře MDI</span><span class="sxs-lookup"><span data-stu-id="02c16-107">Create MDI child forms</span></span>

1. <span data-ttu-id="02c16-108">V aplikaci Visual Studio vytvořte nový projekt aplikace model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="02c16-108">Create a new Windows Forms application project in Visual Studio.</span></span> <span data-ttu-id="02c16-109">V okně **vlastnosti** formuláře nastavte jeho <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost na `true` `WindowsState` `Maximized` .</span><span class="sxs-lookup"><span data-stu-id="02c16-109">In the **Properties** window for the form, set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true` and its `WindowsState` property to `Maximized`.</span></span>

   <span data-ttu-id="02c16-110">Tato položka označuje formulář jako kontejner MDI pro podřízená okna.</span><span class="sxs-lookup"><span data-stu-id="02c16-110">This designates the form as an MDI container for child windows.</span></span>

2. <span data-ttu-id="02c16-111">Z rozhraní `Toolbox` přetáhněte <xref:System.Windows.Forms.MenuStrip> ovládací prvek do formuláře.</span><span class="sxs-lookup"><span data-stu-id="02c16-111">From the `Toolbox`, drag a <xref:System.Windows.Forms.MenuStrip> control to the form.</span></span> <span data-ttu-id="02c16-112">Nastavte `Text` vlastnost na **soubor**.</span><span class="sxs-lookup"><span data-stu-id="02c16-112">Set its `Text` property to **File**.</span></span>

3. <span data-ttu-id="02c16-113">Klikněte na tlačítko se třemi tečkami (...) vedle vlastnosti **Items (položky** ) a kliknutím na tlačítko **Přidat** přidejte dvě podřízené položky nabídky pruhu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="02c16-113">Click the ellipsis (…) next to the **Items** property, and click **Add** to add two child tool strip menu items.</span></span> <span data-ttu-id="02c16-114">Nastavte `Text` vlastnost pro tyto položky na **nové** a **okno**.</span><span class="sxs-lookup"><span data-stu-id="02c16-114">Set the `Text` property for these items to **New** and **Window**.</span></span>

4. <span data-ttu-id="02c16-115">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat**  >  **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="02c16-115">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

5. <span data-ttu-id="02c16-116">V dialogovém okně **Přidat novou položku** vyberte v podokně **šablony** možnost **formulář Windows** (v Visual Basic nebo v jazyce Visual C#) nebo **model Windows Forms aplikace (** v Visual C++).</span><span class="sxs-lookup"><span data-stu-id="02c16-116">In the **Add New Item** dialog box, select **Windows Form** (in Visual Basic or in Visual C#) or **Windows Forms Application (.NET)** (in Visual C++) from the **Templates** pane.</span></span> <span data-ttu-id="02c16-117">Do pole **název** zadejte název formuláře **Form2**.</span><span class="sxs-lookup"><span data-stu-id="02c16-117">In the **Name** box, name the form **Form2**.</span></span> <span data-ttu-id="02c16-118">Vyberte **otevřít** a přidejte formulář do projektu.</span><span class="sxs-lookup"><span data-stu-id="02c16-118">Select **Open** to add the form to the project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="02c16-119">Podřízený formulář MDI, který jste vytvořili v tomto kroku, je standardním formulářem Windows.</span><span class="sxs-lookup"><span data-stu-id="02c16-119">The MDI child form you created in this step is a standard Windows Form.</span></span> <span data-ttu-id="02c16-120">V takovém případě má <xref:System.Windows.Forms.Form.Opacity%2A> vlastnost, která umožňuje ovládat průhlednost formuláře.</span><span class="sxs-lookup"><span data-stu-id="02c16-120">As such, it has an <xref:System.Windows.Forms.Form.Opacity%2A> property, which enables you to control the transparency of the form.</span></span> <span data-ttu-id="02c16-121"><xref:System.Windows.Forms.Form.Opacity%2A>Vlastnost byla však navržena pro okna nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="02c16-121">However, the <xref:System.Windows.Forms.Form.Opacity%2A> property was designed for top-level windows.</span></span> <span data-ttu-id="02c16-122">Nepoužívejte ji s podřízenými formuláři MDI, protože mohou nastat problémy při malování.</span><span class="sxs-lookup"><span data-stu-id="02c16-122">Do not use it with MDI child forms, as painting problems can occur.</span></span>

     <span data-ttu-id="02c16-123">Tento formulář bude šablonou pro podřízené formuláře MDI.</span><span class="sxs-lookup"><span data-stu-id="02c16-123">This form will be the template for your MDI child forms.</span></span>

     <span data-ttu-id="02c16-124">Otevře se **Návrhář formulářů** , kde se zobrazí **Form2**.</span><span class="sxs-lookup"><span data-stu-id="02c16-124">The **Windows Forms Designer** opens, displaying **Form2**.</span></span>

6. <span data-ttu-id="02c16-125">Z **panelu nástrojů**přetáhněte ovládací prvek **RichTextBox** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="02c16-125">From the **Toolbox**, drag a **RichTextBox** control to the form.</span></span>

7. <span data-ttu-id="02c16-126">V okně **vlastnosti** nastavte `Anchor` vlastnost na **horní, levou** a `Dock` vlastnost na **vyplnit**.</span><span class="sxs-lookup"><span data-stu-id="02c16-126">In the **Properties** window, set the `Anchor` property to **Top, Left** and the `Dock` property to **Fill**.</span></span>

   <span data-ttu-id="02c16-127">To způsobí <xref:System.Windows.Forms.RichTextBox> , že ovládací prvek zcela vyplní oblast podřízeného formuláře MDI, i když se změní velikost formuláře.</span><span class="sxs-lookup"><span data-stu-id="02c16-127">This causes the <xref:System.Windows.Forms.RichTextBox> control to completely fill the area of the MDI child form, even when the form is resized.</span></span>

8. <span data-ttu-id="02c16-128">Dvojitým kliknutím na položku **nové** nabídky vytvořte <xref:System.Windows.Forms.Control.Click> pro ni obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="02c16-128">Double click the **New** menu item to create a <xref:System.Windows.Forms.Control.Click> event handler for it.</span></span>

9. <span data-ttu-id="02c16-129">Vložte kód podobný následujícímu pro vytvoření nového podřízeného formuláře MDI, když uživatel klikne na **novou** položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="02c16-129">Insert code similar to the following to create a new MDI child form when the user clicks the **New** menu item.</span></span>

   > [!NOTE]
   > <span data-ttu-id="02c16-130">V následujícím příkladu obslužná rutina události zpracovává <xref:System.Windows.Forms.Control.Click> událost pro `MenuItem2` .</span><span class="sxs-lookup"><span data-stu-id="02c16-130">In the following example, the event handler handles the <xref:System.Windows.Forms.Control.Click> event for `MenuItem2`.</span></span> <span data-ttu-id="02c16-131">Mějte na paměti, že v závislosti na konkrétní architektuře vaší aplikace nemusí být vaše **Nová** položka nabídky `MenuItem2` .</span><span class="sxs-lookup"><span data-stu-id="02c16-131">Be aware that, depending on the specifics of your application architecture, your **New** menu item may not be `MenuItem2`.</span></span>

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

   <span data-ttu-id="02c16-132">V jazyce C++ přidejte následující `#include` direktivu v horní části Form1. h:</span><span class="sxs-lookup"><span data-stu-id="02c16-132">In C++, add the following `#include` directive at the top of Form1.h:</span></span>

   ```cpp
   #include "Form2.h"
   ```

10. <span data-ttu-id="02c16-133">V rozevíracím seznamu v horní části okna **vlastnosti** vyberte pruh nabídky, který odpovídá pruhu nabídky **soubor** , a nastavte <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> vlastnost na okno <xref:System.Windows.Forms.ToolStripMenuItem> .</span><span class="sxs-lookup"><span data-stu-id="02c16-133">In the drop-down list at the top of the **Properties** window, select the menu strip that corresponds to the **File** menu strip and set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to the Window <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

    <span data-ttu-id="02c16-134">Tím umožníte, aby nabídka **okna** udržovala seznam otevřených podřízených oken MDI se značkou zaškrtnutí vedle aktivního podřízeného okna.</span><span class="sxs-lookup"><span data-stu-id="02c16-134">This enables the **Window** menu to maintain a list of open MDI child windows with a check mark next to the active child window.</span></span>

11. <span data-ttu-id="02c16-135">Stisknutím klávesy **F5** spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="02c16-135">Press **F5** to run the application.</span></span> <span data-ttu-id="02c16-136">Výběrem možnosti **Nový** v nabídce **soubor** můžete vytvořit nové podřízené formuláře MDI, které se udržují v položce nabídky **okna** .</span><span class="sxs-lookup"><span data-stu-id="02c16-136">By selecting **New** from the **File** menu, you can create new MDI child forms, which are kept track of in the **Window** menu item.</span></span>

    > [!NOTE]
    > <span data-ttu-id="02c16-137">Pokud má podřízený formulář MDI <xref:System.Windows.Forms.MainMenu> komponentu (se obvykle strukturou nabídky položek nabídky) a je otevřena v nadřazeném formuláři MDI, který má <xref:System.Windows.Forms.MainMenu> komponentu (obvykle se jedná o strukturu nabídky položek nabídky), položky nabídky se sloučí automaticky, pokud jste nastavili <xref:System.Windows.Forms.MenuItem.MergeType%2A> vlastnost (a volitelně <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> vlastnost).</span><span class="sxs-lookup"><span data-stu-id="02c16-137">When an MDI child form has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items) and it is opened within an MDI parent form that has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items), the menu items will merge automatically if you have set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property (and optionally, the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property).</span></span> <span data-ttu-id="02c16-138">Nastavte <xref:System.Windows.Forms.MenuItem.MergeType%2A> vlastnost obou <xref:System.Windows.Forms.MainMenu> komponent a všechny položky nabídky podřízeného formuláře na <xref:System.Windows.Forms.MenuMerge.MergeItems> .</span><span class="sxs-lookup"><span data-stu-id="02c16-138">Set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property of both <xref:System.Windows.Forms.MainMenu> components and all of the menu items of the child form to <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span></span> <span data-ttu-id="02c16-139">Kromě toho nastavte <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> vlastnost tak, aby se položky nabídky z obou nabídek zobrazovaly v požadovaném pořadí.</span><span class="sxs-lookup"><span data-stu-id="02c16-139">Additionally, set the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property so that the menu items from both menus appear in the desired order.</span></span> <span data-ttu-id="02c16-140">Kromě toho mějte na paměti, že při zavření nadřazeného formuláře MDI vyvolá každá z podřízených formulářů MDI událost před vyvoláním <xref:System.Windows.Forms.Form.Closing> <xref:System.Windows.Forms.Form.Closing> události pro nadřazený objekt MDI.</span><span class="sxs-lookup"><span data-stu-id="02c16-140">Moreover, keep in mind that when you close an MDI parent form, each of the MDI child forms raises a <xref:System.Windows.Forms.Form.Closing> event before the <xref:System.Windows.Forms.Form.Closing> event for the MDI parent is raised.</span></span> <span data-ttu-id="02c16-141">Zrušení události podřízeného objektu MDI <xref:System.Windows.Forms.Form.Closing> nebrání vyvolání události nadřazeného objektu MDI <xref:System.Windows.Forms.Form.Closing> . <xref:System.ComponentModel.CancelEventArgs> argument pro událost nadřazené položky MDI však <xref:System.Windows.Forms.Form.Closing> bude nyní nastaven na hodnotu `true` .</span><span class="sxs-lookup"><span data-stu-id="02c16-141">Canceling an MDI child's <xref:System.Windows.Forms.Form.Closing> event will not prevent the MDI parent's <xref:System.Windows.Forms.Form.Closing> event from being raised; however, the <xref:System.ComponentModel.CancelEventArgs> argument for the MDI parent's <xref:System.Windows.Forms.Form.Closing> event will now be set to `true`.</span></span> <span data-ttu-id="02c16-142">Můžete vynutit, aby nadřazený objekt MDI a všechny podřízené formuláře MDI byly uzavřeny nastavením <xref:System.ComponentModel.CancelEventArgs> argumentu na `false` .</span><span class="sxs-lookup"><span data-stu-id="02c16-142">You can force the MDI parent and all MDI child forms to close by setting the <xref:System.ComponentModel.CancelEventArgs> argument to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="02c16-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="02c16-143">See also</span></span>

- [<span data-ttu-id="02c16-144">Aplikace MDI (Multiple-Document Interface)</span><span class="sxs-lookup"><span data-stu-id="02c16-144">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="02c16-145">Postupy: Vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="02c16-145">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="02c16-146">Postupy: Určení podřízeného prvku aktivního MDI</span><span class="sxs-lookup"><span data-stu-id="02c16-146">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="02c16-147">Postupy: Odesílání dat do aktivního podřízeného MDI</span><span class="sxs-lookup"><span data-stu-id="02c16-147">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="02c16-148">Postupy: Uspořádání podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="02c16-148">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
