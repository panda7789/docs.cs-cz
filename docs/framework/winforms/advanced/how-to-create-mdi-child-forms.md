---
title: 'Postupy: Vytváření podřízených formulářů MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: fbc92c03da69dd452f35e5b4e00cd4a9ca17e252
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211186"
---
# <a name="how-to-create-mdi-child-forms"></a><span data-ttu-id="7db86-102">Postupy: Vytvořit podřízený formulář MDI formuláře</span><span class="sxs-lookup"><span data-stu-id="7db86-102">How to: Create MDI child forms</span></span>

<span data-ttu-id="7db86-103">Podřízené formuláře MDI jsou důležitou součástí [aplikace rozhraní více dokumentů (MDI)](multiple-document-interface-mdi-applications.md), jako jsou centra interakci s uživatelem.</span><span class="sxs-lookup"><span data-stu-id="7db86-103">MDI child forms are an essential element of [Multiple-Document Interface (MDI) Applications](multiple-document-interface-mdi-applications.md), as these forms are the center of user interaction.</span></span>

<span data-ttu-id="7db86-104">V následujícím postupu budete používat Visual Studio k vytvoření podřízené formuláře MDI, která se zobrazí <xref:System.Windows.Forms.RichTextBox> nejvíce zpracování textu žádosti podobně jako ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="7db86-104">In the following procedure, you'll use Visual Studio to create an MDI child form that displays a <xref:System.Windows.Forms.RichTextBox> control, similar to most word-processing applications.</span></span> <span data-ttu-id="7db86-105">Nahrazování <xref:System.Windows.Forms> ovládací prvek s jinými ovládacími prvky, jako <xref:System.Windows.Forms.DataGridView> ovládací prvek nebo kombinaci ovládací prvky vám umožní vytvořit podřízený formulář MDI systému windows (a při rozšíření i pro aplikace MDI) s různými možnostmi.</span><span class="sxs-lookup"><span data-stu-id="7db86-105">Substituting the <xref:System.Windows.Forms> control with other controls, such as the <xref:System.Windows.Forms.DataGridView> control, or a mixture of controls enables you to create MDI child windows (and, by extension, MDI applications) with diverse possibilities.</span></span>

## <a name="create-mdi-child-forms"></a><span data-ttu-id="7db86-106">Vytvořit podřízený formulář MDI formuláře</span><span class="sxs-lookup"><span data-stu-id="7db86-106">Create MDI child forms</span></span>

1. <span data-ttu-id="7db86-107">Vytvoření nového projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7db86-107">Create a new Windows Forms project.</span></span> <span data-ttu-id="7db86-108">V **Windows vlastnosti** formuláři, nastavit jeho <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost `true`a jeho `WindowsState` vlastnost `Maximized`.</span><span class="sxs-lookup"><span data-stu-id="7db86-108">In **the Properties Windows** for the form, set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`, and its `WindowsState` property to `Maximized`.</span></span>

   <span data-ttu-id="7db86-109">Ta určuje formuláře jako kontejnerem MDI pro podřízená okna.</span><span class="sxs-lookup"><span data-stu-id="7db86-109">This designates the form as an MDI container for child windows.</span></span>

2. <span data-ttu-id="7db86-110">Z `Toolbox`, přetáhněte <xref:System.Windows.Forms.MenuStrip> ovládacího prvku na formuláři.</span><span class="sxs-lookup"><span data-stu-id="7db86-110">From the `Toolbox`, drag a <xref:System.Windows.Forms.MenuStrip> control to the form.</span></span> <span data-ttu-id="7db86-111">Nastavte jeho `Text` vlastnost **souboru**.</span><span class="sxs-lookup"><span data-stu-id="7db86-111">Set its `Text` property to **File**.</span></span>

3. <span data-ttu-id="7db86-112">Klikněte na symbol tří teček (...) vedle položky **položky** vlastnost a klikněte na tlačítko **přidat** přidat dva podřízené položky nabídky pruhu pro nástroj.</span><span class="sxs-lookup"><span data-stu-id="7db86-112">Click the ellipses (…) next to the **Items** property, and click **Add** to add two child tool strip menu items.</span></span> <span data-ttu-id="7db86-113">Nastavte `Text` vlastnost pro tyto položky **nový** a **okno**.</span><span class="sxs-lookup"><span data-stu-id="7db86-113">Set the `Text` property for these items to **New** and **Window**.</span></span>

4. <span data-ttu-id="7db86-114">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt, přejděte na **přidat**a pak vyberte **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="7db86-114">In **Solution Explorer**, right-click the project, point to **Add**, and then select **Add New Item**.</span></span>

5. <span data-ttu-id="7db86-115">V **přidat novou položku** dialogu **formuláře Windows** (v jazyce Visual Basic nebo Visual C#) nebo **Windows Forms aplikace (.NET)** (v [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) z  **Šablony** podokně.</span><span class="sxs-lookup"><span data-stu-id="7db86-115">In the **Add New Item** dialog box, select **Windows Form** (in Visual Basic or in Visual C#) or **Windows Forms Application (.NET)** (in [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) from the **Templates** pane.</span></span> <span data-ttu-id="7db86-116">V **název** pole, pojmenujte formulář **Form2**.</span><span class="sxs-lookup"><span data-stu-id="7db86-116">In the **Name** box, name the form **Form2**.</span></span> <span data-ttu-id="7db86-117">Klikněte na tlačítko **otevřít** tlačítko pro přidání formuláře do projektu.</span><span class="sxs-lookup"><span data-stu-id="7db86-117">Click the **Open** button to add the form to the project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7db86-118">Podřízený formulář MDI, které jste vytvořili v tomto kroku je běžného formuláře Windows.</span><span class="sxs-lookup"><span data-stu-id="7db86-118">The MDI child form you created in this step is a standard Windows Form.</span></span> <span data-ttu-id="7db86-119">V důsledku toho je <xref:System.Windows.Forms.Form.Opacity%2A> vlastnost, která vám umožňuje řídit průhlednost formuláře.</span><span class="sxs-lookup"><span data-stu-id="7db86-119">As such, it has an <xref:System.Windows.Forms.Form.Opacity%2A> property, which enables you to control the transparency of the form.</span></span> <span data-ttu-id="7db86-120">Ale <xref:System.Windows.Forms.Form.Opacity%2A> vlastnost je navržená pro okna nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="7db86-120">However, the <xref:System.Windows.Forms.Form.Opacity%2A> property was designed for top-level windows.</span></span> <span data-ttu-id="7db86-121">Nepoužívejte ho s podřízených formulářů MDI, protože může dojít k problémům Malování.</span><span class="sxs-lookup"><span data-stu-id="7db86-121">Do not use it with MDI child forms, as painting problems can occur.</span></span>

     <span data-ttu-id="7db86-122">Šablona pro podřízené formuláře MDI bude tento formulář.</span><span class="sxs-lookup"><span data-stu-id="7db86-122">This form will be the template for your MDI child forms.</span></span>

     <span data-ttu-id="7db86-123">**Návrháře formulářů Windows** otevře zobrazení **Form2**.</span><span class="sxs-lookup"><span data-stu-id="7db86-123">The **Windows Forms Designer** opens, displaying **Form2**.</span></span>

6. <span data-ttu-id="7db86-124">Z **nástrojů**, přetáhněte **RichTextBox** ovládacího prvku na formuláři.</span><span class="sxs-lookup"><span data-stu-id="7db86-124">From the **Toolbox**, drag a **RichTextBox** control to the form.</span></span>

7. <span data-ttu-id="7db86-125">V **vlastnosti** okno, nastaveno `Anchor` vlastnost **horní, levý** a `Dock` vlastnost **vyplnit**.</span><span class="sxs-lookup"><span data-stu-id="7db86-125">In the **Properties** window, set the `Anchor` property to **Top, Left** and the `Dock` property to **Fill**.</span></span>

   <span data-ttu-id="7db86-126">To způsobí, že <xref:System.Windows.Forms.RichTextBox> ovládací prvek pro úplně naplnění oblasti podřízený formulář MDI, i když se změní velikost formuláře.</span><span class="sxs-lookup"><span data-stu-id="7db86-126">This causes the <xref:System.Windows.Forms.RichTextBox> control to completely fill the area of the MDI child form, even when the form is resized.</span></span>

8. <span data-ttu-id="7db86-127">Dvakrát klikněte **nový** vytvořit položku nabídky <xref:System.Windows.Forms.Control.Click> obslužnou rutinu události pro něj.</span><span class="sxs-lookup"><span data-stu-id="7db86-127">Double click the **New** menu item to create a <xref:System.Windows.Forms.Control.Click> event handler for it.</span></span>

9. <span data-ttu-id="7db86-128">Vložte kód podobný následujícímu vytvořit nový podřízený formulář MDI, když uživatel klikne **nový** položky nabídky.</span><span class="sxs-lookup"><span data-stu-id="7db86-128">Insert code similar to the following to create a new MDI child form when the user clicks the **New** menu item.</span></span>

   > [!NOTE]
   > <span data-ttu-id="7db86-129">V následujícím příkladu, zpracuje obslužná rutina události <xref:System.Windows.Forms.Control.Click> událost pro `MenuItem2`.</span><span class="sxs-lookup"><span data-stu-id="7db86-129">In the following example, the event handler handles the <xref:System.Windows.Forms.Control.Click> event for `MenuItem2`.</span></span> <span data-ttu-id="7db86-130">Mějte na paměti, že v závislosti na tom, jaké jsou specifikace architektury aplikace, vaše **nový** nemusí být položka nabídky `MenuItem2`.</span><span class="sxs-lookup"><span data-stu-id="7db86-130">Be aware that, depending on the specifics of your application architecture, your **New** menu item may not be `MenuItem2`.</span></span>

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

   <span data-ttu-id="7db86-131">V C++, přidejte následující `#include` direktiv v horní části Form1.h:</span><span class="sxs-lookup"><span data-stu-id="7db86-131">In C++, add the following `#include` directive at the top of Form1.h:</span></span>

   ```cpp
   #include "Form2.h"
   ```

10. <span data-ttu-id="7db86-132">V rozevíracím seznamu v horní části **vlastnosti** okna, vyberte pruh nabídky, která odpovídá **souboru** pruhu nabídky a nastavte <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> vlastností v okně <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="7db86-132">In the drop-down list at the top of the **Properties** window, select the menu strip that corresponds to the **File** menu strip and set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to the Window <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

    <span data-ttu-id="7db86-133">To vám umožní **okno** nabídky Spravovat seznam otevřít podřízených oken MDI zaškrtnutí vedle aktivní podřízené okno.</span><span class="sxs-lookup"><span data-stu-id="7db86-133">This will enable the **Window** menu to maintain a list of open MDI child windows with a check mark next to the active child window.</span></span>

11. <span data-ttu-id="7db86-134">Stisknutím klávesy **F5** ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="7db86-134">Press **F5** to run the application.</span></span> <span data-ttu-id="7db86-135">Výběrem **nový** z **souboru** nabídku, můžete vytvořit nové MDI podřízené formuláře, které jsou udržovat přehled o v **okno** položky nabídky.</span><span class="sxs-lookup"><span data-stu-id="7db86-135">By selecting **New** from the **File** menu, you can create new MDI child forms, which are kept track of in the **Window** menu item.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7db86-136">Pokud má podřízený formulář MDI <xref:System.Windows.Forms.MainMenu> součásti (s většinou, nabídky strukturu položek nabídky) a je otevřen v rámci, který má nadřazený formulář MDI <xref:System.Windows.Forms.MainMenu> součásti (s většinou, nabídky strukturu položek nabídek), v nabídce položky budou automaticky sloučit Pokud jste nastavili <xref:System.Windows.Forms.MenuItem.MergeType%2A> vlastnosti (a volitelně také <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> vlastnost).</span><span class="sxs-lookup"><span data-stu-id="7db86-136">When an MDI child form has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items) and it is opened within an MDI parent form that has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items), the menu items will merge automatically if you have set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property (and optionally, the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property).</span></span> <span data-ttu-id="7db86-137">Nastavte <xref:System.Windows.Forms.MenuItem.MergeType%2A> vlastnost objektu i <xref:System.Windows.Forms.MainMenu> komponenty a všechny položky nabídky podřízené formuláře <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span><span class="sxs-lookup"><span data-stu-id="7db86-137">Set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property of both <xref:System.Windows.Forms.MainMenu> components and all of the menu items of the child form to <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span></span> <span data-ttu-id="7db86-138">Kromě toho nastavení <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> vlastnost tak, aby z obou nabídek položky nabídky zobrazí do požadovaného pořadí.</span><span class="sxs-lookup"><span data-stu-id="7db86-138">Additionally, set the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property so that the menu items from both menus appear in the desired order.</span></span> <span data-ttu-id="7db86-139">Kromě toho vzít v úvahu, že při zavření nadřazený formulář MDI každý podřízený formulář MDI formuláře vyvolá <xref:System.Windows.Forms.Form.Closing> události před <xref:System.Windows.Forms.Form.Closing> se vyvolá událost pro nadřazený objekt MDI.</span><span class="sxs-lookup"><span data-stu-id="7db86-139">Moreover, keep in mind that when you close an MDI parent form, each of the MDI child forms raises a <xref:System.Windows.Forms.Form.Closing> event before the <xref:System.Windows.Forms.Form.Closing> event for the MDI parent is raised.</span></span> <span data-ttu-id="7db86-140">Zrušení podřízený formulář MDI <xref:System.Windows.Forms.Form.Closing> události nezabrání nadřazený objekt MDI <xref:System.Windows.Forms.Form.Closing> událost vyvolána; však <xref:System.ComponentModel.CancelEventArgs> argument pro nadřazený objekt MDI <xref:System.Windows.Forms.Form.Closing> události se nastaví na `true`.</span><span class="sxs-lookup"><span data-stu-id="7db86-140">Canceling an MDI child's <xref:System.Windows.Forms.Form.Closing> event will not prevent the MDI parent's <xref:System.Windows.Forms.Form.Closing> event from being raised; however, the <xref:System.ComponentModel.CancelEventArgs> argument for the MDI parent's <xref:System.Windows.Forms.Form.Closing> event will now be set to `true`.</span></span> <span data-ttu-id="7db86-141">Můžete vynutit nadřazený objekt MDI a všechny podřízené formuláře MDI zavřete tak, že nastavíte <xref:System.ComponentModel.CancelEventArgs> argument `false`.</span><span class="sxs-lookup"><span data-stu-id="7db86-141">You can force the MDI parent and all MDI child forms to close by setting the <xref:System.ComponentModel.CancelEventArgs> argument to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="7db86-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7db86-142">See also</span></span>

- [<span data-ttu-id="7db86-143">Aplikace MDI (Multiple-Document Interface)</span><span class="sxs-lookup"><span data-stu-id="7db86-143">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="7db86-144">Postupy: Vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="7db86-144">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="7db86-145">Postupy: Určení podřízeného prvku aktivního MDI</span><span class="sxs-lookup"><span data-stu-id="7db86-145">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="7db86-146">Postupy: Odesílání dat do aktivního podřízeného MDI</span><span class="sxs-lookup"><span data-stu-id="7db86-146">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="7db86-147">Postupy: Uspořádání podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="7db86-147">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
