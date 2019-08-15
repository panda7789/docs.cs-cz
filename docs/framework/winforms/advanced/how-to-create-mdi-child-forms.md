---
title: 'Postupy: Vytváření podřízených formulářů MDI'
ms.date: 03/30/2017
dev_langs:
- CSharp
- CPP
- VB
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: f5e8682caf658d159f044528f040b99676355448
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040116"
---
# <a name="how-to-create-mdi-child-forms"></a><span data-ttu-id="88324-102">Postupy: Vytvořit podřízené formuláře MDI</span><span class="sxs-lookup"><span data-stu-id="88324-102">How to: Create MDI child forms</span></span>

<span data-ttu-id="88324-103">Podřízené formuláře MDI jsou zásadním prvkem [aplikací rozhraní MDI (Multiple Document Interface)](multiple-document-interface-mdi-applications.md), protože tyto formuláře jsou centrem interakce s uživatelem.</span><span class="sxs-lookup"><span data-stu-id="88324-103">MDI child forms are an essential element of [Multiple-Document Interface (MDI) applications](multiple-document-interface-mdi-applications.md), as these forms are the center of user interaction.</span></span>

<span data-ttu-id="88324-104">V následujícím postupu použijete Visual Studio k vytvoření podřízeného formuláře MDI, který zobrazí <xref:System.Windows.Forms.RichTextBox> ovládací prvek podobný většině aplikací pro zpracování textu.</span><span class="sxs-lookup"><span data-stu-id="88324-104">In the following procedure, you'll use Visual Studio to create an MDI child form that displays a <xref:System.Windows.Forms.RichTextBox> control, similar to most word-processing applications.</span></span> <span data-ttu-id="88324-105">Nahrazením <xref:System.Windows.Forms> ovládacího prvku dalšími ovládacími prvky, jako je <xref:System.Windows.Forms.DataGridView> například ovládací prvek nebo kombinace ovládacích prvků, můžete vytvořit podřízená okna MDI (a, pomocí rozšíření, aplikací MDI) s různými možnostmi.</span><span class="sxs-lookup"><span data-stu-id="88324-105">By substituting the <xref:System.Windows.Forms> control with other controls, such as the <xref:System.Windows.Forms.DataGridView> control, or a mixture of controls, you can create MDI child windows (and, by extension, MDI applications) with diverse possibilities.</span></span>

## <a name="create-mdi-child-forms"></a><span data-ttu-id="88324-106">Vytvořit podřízené formuláře MDI</span><span class="sxs-lookup"><span data-stu-id="88324-106">Create MDI child forms</span></span>

1. <span data-ttu-id="88324-107">V aplikaci Visual Studio vytvořte nový projekt aplikace model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="88324-107">Create a new Windows Forms application project in Visual Studio.</span></span> <span data-ttu-id="88324-108">V okně **vlastnosti** formuláře nastavte jeho <xref:System.Windows.Forms.Form.IsMdiContainer%2A> `WindowsState` vlastnost na `true`. `Maximized`</span><span class="sxs-lookup"><span data-stu-id="88324-108">In the **Properties** window for the form, set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true` and its `WindowsState` property to `Maximized`.</span></span>

   <span data-ttu-id="88324-109">Tato položka označuje formulář jako kontejner MDI pro podřízená okna.</span><span class="sxs-lookup"><span data-stu-id="88324-109">This designates the form as an MDI container for child windows.</span></span>

2. <span data-ttu-id="88324-110">Z rozhraní `Toolbox` <xref:System.Windows.Forms.MenuStrip> přetáhněte ovládací prvek do formuláře.</span><span class="sxs-lookup"><span data-stu-id="88324-110">From the `Toolbox`, drag a <xref:System.Windows.Forms.MenuStrip> control to the form.</span></span> <span data-ttu-id="88324-111">Nastavte vlastnost na **soubor.** `Text`</span><span class="sxs-lookup"><span data-stu-id="88324-111">Set its `Text` property to **File**.</span></span>

3. <span data-ttu-id="88324-112">Klikněte na tlačítko se třemi tečkami (...) vedle vlastnosti Items ( **položky** ) a kliknutím na tlačítko **Přidat** přidejte dvě podřízené položky nabídky pruhu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="88324-112">Click the ellipsis (…) next to the **Items** property, and click **Add** to add two child tool strip menu items.</span></span> <span data-ttu-id="88324-113">Nastavte vlastnost pro tyto položky na **nové** a **okno.** `Text`</span><span class="sxs-lookup"><span data-stu-id="88324-113">Set the `Text` property for these items to **New** and **Window**.</span></span>

4. <span data-ttu-id="88324-114">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="88324-114">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

5. <span data-ttu-id="88324-115">V dialogovém okně **Přidat novou položku** vyberte v podokně **šablony** možnost **formulář Windows** (v Visual Basic nebo C#v jazyce Visual) nebo v **aplikaci model Windows Forms (** v C++jazyce Visual) (ve vizuálu).</span><span class="sxs-lookup"><span data-stu-id="88324-115">In the **Add New Item** dialog box, select **Windows Form** (in Visual Basic or in Visual C#) or **Windows Forms Application (.NET)** (in Visual C++) from the **Templates** pane.</span></span> <span data-ttu-id="88324-116">Do pole **název** zadejte název formuláře **Form2**.</span><span class="sxs-lookup"><span data-stu-id="88324-116">In the **Name** box, name the form **Form2**.</span></span> <span data-ttu-id="88324-117">Vyberte **otevřít** a přidejte formulář do projektu.</span><span class="sxs-lookup"><span data-stu-id="88324-117">Select **Open** to add the form to the project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="88324-118">Podřízený formulář MDI, který jste vytvořili v tomto kroku, je standardním formulářem Windows.</span><span class="sxs-lookup"><span data-stu-id="88324-118">The MDI child form you created in this step is a standard Windows Form.</span></span> <span data-ttu-id="88324-119">V takovém případě má <xref:System.Windows.Forms.Form.Opacity%2A> vlastnost, která umožňuje ovládat průhlednost formuláře.</span><span class="sxs-lookup"><span data-stu-id="88324-119">As such, it has an <xref:System.Windows.Forms.Form.Opacity%2A> property, which enables you to control the transparency of the form.</span></span> <span data-ttu-id="88324-120"><xref:System.Windows.Forms.Form.Opacity%2A> Vlastnost byla však navržena pro okna nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="88324-120">However, the <xref:System.Windows.Forms.Form.Opacity%2A> property was designed for top-level windows.</span></span> <span data-ttu-id="88324-121">Nepoužívejte ji s podřízenými formuláři MDI, protože mohou nastat problémy při malování.</span><span class="sxs-lookup"><span data-stu-id="88324-121">Do not use it with MDI child forms, as painting problems can occur.</span></span>

     <span data-ttu-id="88324-122">Tento formulář bude šablonou pro podřízené formuláře MDI.</span><span class="sxs-lookup"><span data-stu-id="88324-122">This form will be the template for your MDI child forms.</span></span>

     <span data-ttu-id="88324-123">Otevře se **Návrhář formulářů** , kde se zobrazí **Form2**.</span><span class="sxs-lookup"><span data-stu-id="88324-123">The **Windows Forms Designer** opens, displaying **Form2**.</span></span>

6. <span data-ttu-id="88324-124">Z **panelu nástrojů**přetáhněte ovládací prvek **RichTextBox** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="88324-124">From the **Toolbox**, drag a **RichTextBox** control to the form.</span></span>

7. <span data-ttu-id="88324-125">V okně **vlastnosti** nastavte `Anchor` vlastnost na `Dock` **horní, levou** a vlastnost na **vyplnit**.</span><span class="sxs-lookup"><span data-stu-id="88324-125">In the **Properties** window, set the `Anchor` property to **Top, Left** and the `Dock` property to **Fill**.</span></span>

   <span data-ttu-id="88324-126">To způsobí, <xref:System.Windows.Forms.RichTextBox> že ovládací prvek zcela vyplní oblast podřízeného formuláře MDI, i když se změní velikost formuláře.</span><span class="sxs-lookup"><span data-stu-id="88324-126">This causes the <xref:System.Windows.Forms.RichTextBox> control to completely fill the area of the MDI child form, even when the form is resized.</span></span>

8. <span data-ttu-id="88324-127">Dvojitým kliknutím na položku **nové** nabídky vytvořte <xref:System.Windows.Forms.Control.Click> pro ni obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="88324-127">Double click the **New** menu item to create a <xref:System.Windows.Forms.Control.Click> event handler for it.</span></span>

9. <span data-ttu-id="88324-128">Vložte kód podobný následujícímu pro vytvoření nového podřízeného formuláře MDI, když uživatel klikne na **novou** položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="88324-128">Insert code similar to the following to create a new MDI child form when the user clicks the **New** menu item.</span></span>

   > [!NOTE]
   > <span data-ttu-id="88324-129">V následujícím příkladu obslužná rutina události zpracovává <xref:System.Windows.Forms.Control.Click> událost pro. `MenuItem2`</span><span class="sxs-lookup"><span data-stu-id="88324-129">In the following example, the event handler handles the <xref:System.Windows.Forms.Control.Click> event for `MenuItem2`.</span></span> <span data-ttu-id="88324-130">Mějte na paměti, že v závislosti na konkrétní architektuře vaší aplikace nemusí být `MenuItem2`vaše **Nová** položka nabídky.</span><span class="sxs-lookup"><span data-stu-id="88324-130">Be aware that, depending on the specifics of your application architecture, your **New** menu item may not be `MenuItem2`.</span></span>

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

   <span data-ttu-id="88324-131">V C++přidejte následující `#include` direktivu v horní části Form1. h:</span><span class="sxs-lookup"><span data-stu-id="88324-131">In C++, add the following `#include` directive at the top of Form1.h:</span></span>

   ```cpp
   #include "Form2.h"
   ```

10. <span data-ttu-id="88324-132">V rozevíracím seznamu v horní části okna **vlastnosti** vyberte pruh nabídky, který odpovídá pruhu nabídky **soubor** , <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> a nastavte vlastnost na okno <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="88324-132">In the drop-down list at the top of the **Properties** window, select the menu strip that corresponds to the **File** menu strip and set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to the Window <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

    <span data-ttu-id="88324-133">Tím umožníte, aby nabídka **okna** udržovala seznam otevřených podřízených oken MDI se značkou zaškrtnutí vedle aktivního podřízeného okna.</span><span class="sxs-lookup"><span data-stu-id="88324-133">This enables the **Window** menu to maintain a list of open MDI child windows with a check mark next to the active child window.</span></span>

11. <span data-ttu-id="88324-134">Stisknutím klávesy **F5** spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="88324-134">Press **F5** to run the application.</span></span> <span data-ttu-id="88324-135">Výběrem možnosti **Nový** v nabídce **soubor** můžete vytvořit nové podřízené formuláře MDI, které se udržují v položce nabídky **okna** .</span><span class="sxs-lookup"><span data-stu-id="88324-135">By selecting **New** from the **File** menu, you can create new MDI child forms, which are kept track of in the **Window** menu item.</span></span>

    > [!NOTE]
    > <span data-ttu-id="88324-136">Pokud má <xref:System.Windows.Forms.MainMenu> podřízený formulář MDI komponentu (se obvykle strukturou nabídky položek nabídky) a je otevřena v nadřazeném formuláři MDI, který <xref:System.Windows.Forms.MainMenu> má komponentu (obvykle se jedná o strukturu nabídky položek nabídky), položky nabídky se sloučí automaticky. Pokud jste nastavili <xref:System.Windows.Forms.MenuItem.MergeType%2A> vlastnost (a volitelně <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> vlastnost).</span><span class="sxs-lookup"><span data-stu-id="88324-136">When an MDI child form has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items) and it is opened within an MDI parent form that has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items), the menu items will merge automatically if you have set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property (and optionally, the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property).</span></span> <span data-ttu-id="88324-137">Nastavte vlastnost obou <xref:System.Windows.Forms.MainMenu> komponent a všechny položky nabídky podřízeného formuláře na <xref:System.Windows.Forms.MenuMerge.MergeItems>. <xref:System.Windows.Forms.MenuItem.MergeType%2A></span><span class="sxs-lookup"><span data-stu-id="88324-137">Set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property of both <xref:System.Windows.Forms.MainMenu> components and all of the menu items of the child form to <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span></span> <span data-ttu-id="88324-138">Kromě toho nastavte <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> vlastnost tak, aby se položky nabídky z obou nabídek zobrazovaly v požadovaném pořadí.</span><span class="sxs-lookup"><span data-stu-id="88324-138">Additionally, set the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property so that the menu items from both menus appear in the desired order.</span></span> <span data-ttu-id="88324-139">Kromě toho mějte na paměti, že při zavření nadřazeného formuláře MDI vyvolá <xref:System.Windows.Forms.Form.Closing> každá z podřízených formulářů MDI událost <xref:System.Windows.Forms.Form.Closing> před vyvoláním události pro nadřazený objekt MDI.</span><span class="sxs-lookup"><span data-stu-id="88324-139">Moreover, keep in mind that when you close an MDI parent form, each of the MDI child forms raises a <xref:System.Windows.Forms.Form.Closing> event before the <xref:System.Windows.Forms.Form.Closing> event for the MDI parent is raised.</span></span> <span data-ttu-id="88324-140">Zrušení <xref:System.Windows.Forms.Form.Closing> události podřízeného objektu MDI nebrání <xref:System.ComponentModel.CancelEventArgs> vyvolání <xref:System.Windows.Forms.Form.Closing> události nadřazeného objektu MDI. argument pro <xref:System.Windows.Forms.Form.Closing> událost nadřazené položky MDI však bude nyní nastaven na `true`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="88324-140">Canceling an MDI child's <xref:System.Windows.Forms.Form.Closing> event will not prevent the MDI parent's <xref:System.Windows.Forms.Form.Closing> event from being raised; however, the <xref:System.ComponentModel.CancelEventArgs> argument for the MDI parent's <xref:System.Windows.Forms.Form.Closing> event will now be set to `true`.</span></span> <span data-ttu-id="88324-141">Můžete vynutit, aby nadřazený objekt MDI a všechny podřízené formuláře MDI byly uzavřeny <xref:System.ComponentModel.CancelEventArgs> nastavením argumentu na. `false`</span><span class="sxs-lookup"><span data-stu-id="88324-141">You can force the MDI parent and all MDI child forms to close by setting the <xref:System.ComponentModel.CancelEventArgs> argument to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="88324-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="88324-142">See also</span></span>

- [<span data-ttu-id="88324-143">Aplikace MDI (Multiple-Document Interface)</span><span class="sxs-lookup"><span data-stu-id="88324-143">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="88324-144">Postupy: Vytvoření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="88324-144">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="88324-145">Postupy: Zjistit aktivní podřízenou položku MDI</span><span class="sxs-lookup"><span data-stu-id="88324-145">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="88324-146">Postupy: Odeslat data do aktivního podřízeného rozhraní MDI</span><span class="sxs-lookup"><span data-stu-id="88324-146">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="88324-147">Postupy: Uspořádat podřízené formuláře MDI</span><span class="sxs-lookup"><span data-stu-id="88324-147">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
