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
# <a name="how-to-create-mdi-child-forms"></a>Postupy: vytváření podřízených formulářů MDI

Podřízené formuláře MDI jsou zásadním prvkem [aplikací rozhraní MDI (Multiple Document Interface)](multiple-document-interface-mdi-applications.md), protože tyto formuláře jsou centrem interakce s uživatelem.

V následujícím postupu použijete Visual Studio k vytvoření podřízeného formuláře MDI, který zobrazí <xref:System.Windows.Forms.RichTextBox> ovládací prvek podobný většině aplikací pro zpracování textu. Nahrazením <xref:System.Windows.Forms> ovládacího prvku dalšími ovládacími prvky, jako je například <xref:System.Windows.Forms.DataGridView> ovládací prvek nebo kombinace ovládacích prvků, můžete vytvořit podřízená okna MDI (a, pomocí rozšíření, aplikací MDI) s různými možnostmi.

## <a name="create-mdi-child-forms"></a>Vytvořit podřízené formuláře MDI

1. V aplikaci Visual Studio vytvořte nový projekt aplikace model Windows Forms. V okně **vlastnosti** formuláře nastavte jeho <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost na `true` `WindowsState` `Maximized` .

   Tato položka označuje formulář jako kontejner MDI pro podřízená okna.

2. Z rozhraní `Toolbox` přetáhněte <xref:System.Windows.Forms.MenuStrip> ovládací prvek do formuláře. Nastavte `Text` vlastnost na **soubor**.

3. Klikněte na tlačítko se třemi tečkami (...) vedle vlastnosti **Items (položky** ) a kliknutím na tlačítko **Přidat** přidejte dvě podřízené položky nabídky pruhu nástrojů. Nastavte `Text` vlastnost pro tyto položky na **nové** a **okno**.

4. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat**  >  **novou položku**.

5. V dialogovém okně **Přidat novou položku** vyberte v podokně **šablony** možnost **formulář Windows** (v Visual Basic nebo v jazyce Visual C#) nebo **model Windows Forms aplikace (** v Visual C++). Do pole **název** zadejte název formuláře **Form2**. Vyberte **otevřít** a přidejte formulář do projektu.

    > [!NOTE]
    > Podřízený formulář MDI, který jste vytvořili v tomto kroku, je standardním formulářem Windows. V takovém případě má <xref:System.Windows.Forms.Form.Opacity%2A> vlastnost, která umožňuje ovládat průhlednost formuláře. <xref:System.Windows.Forms.Form.Opacity%2A>Vlastnost byla však navržena pro okna nejvyšší úrovně. Nepoužívejte ji s podřízenými formuláři MDI, protože mohou nastat problémy při malování.

     Tento formulář bude šablonou pro podřízené formuláře MDI.

     Otevře se **Návrhář formulářů** , kde se zobrazí **Form2**.

6. Z **panelu nástrojů**přetáhněte ovládací prvek **RichTextBox** do formuláře.

7. V okně **vlastnosti** nastavte `Anchor` vlastnost na **horní, levou** a `Dock` vlastnost na **vyplnit**.

   To způsobí <xref:System.Windows.Forms.RichTextBox> , že ovládací prvek zcela vyplní oblast podřízeného formuláře MDI, i když se změní velikost formuláře.

8. Dvojitým kliknutím na položku **nové** nabídky vytvořte <xref:System.Windows.Forms.Control.Click> pro ni obslužnou rutinu události.

9. Vložte kód podobný následujícímu pro vytvoření nového podřízeného formuláře MDI, když uživatel klikne na **novou** položku nabídky.

   > [!NOTE]
   > V následujícím příkladu obslužná rutina události zpracovává <xref:System.Windows.Forms.Control.Click> událost pro `MenuItem2` . Mějte na paměti, že v závislosti na konkrétní architektuře vaší aplikace nemusí být vaše **Nová** položka nabídky `MenuItem2` .

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

   V jazyce C++ přidejte následující `#include` direktivu v horní části Form1. h:

   ```cpp
   #include "Form2.h"
   ```

10. V rozevíracím seznamu v horní části okna **vlastnosti** vyberte pruh nabídky, který odpovídá pruhu nabídky **soubor** , a nastavte <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> vlastnost na okno <xref:System.Windows.Forms.ToolStripMenuItem> .

    Tím umožníte, aby nabídka **okna** udržovala seznam otevřených podřízených oken MDI se značkou zaškrtnutí vedle aktivního podřízeného okna.

11. Stisknutím klávesy **F5** spusťte aplikaci. Výběrem možnosti **Nový** v nabídce **soubor** můžete vytvořit nové podřízené formuláře MDI, které se udržují v položce nabídky **okna** .

    > [!NOTE]
    > Pokud má podřízený formulář MDI <xref:System.Windows.Forms.MainMenu> komponentu (se obvykle strukturou nabídky položek nabídky) a je otevřena v nadřazeném formuláři MDI, který má <xref:System.Windows.Forms.MainMenu> komponentu (obvykle se jedná o strukturu nabídky položek nabídky), položky nabídky se sloučí automaticky, pokud jste nastavili <xref:System.Windows.Forms.MenuItem.MergeType%2A> vlastnost (a volitelně <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> vlastnost). Nastavte <xref:System.Windows.Forms.MenuItem.MergeType%2A> vlastnost obou <xref:System.Windows.Forms.MainMenu> komponent a všechny položky nabídky podřízeného formuláře na <xref:System.Windows.Forms.MenuMerge.MergeItems> . Kromě toho nastavte <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> vlastnost tak, aby se položky nabídky z obou nabídek zobrazovaly v požadovaném pořadí. Kromě toho mějte na paměti, že při zavření nadřazeného formuláře MDI vyvolá každá z podřízených formulářů MDI událost před vyvoláním <xref:System.Windows.Forms.Form.Closing> <xref:System.Windows.Forms.Form.Closing> události pro nadřazený objekt MDI. Zrušení události podřízeného objektu MDI <xref:System.Windows.Forms.Form.Closing> nebrání vyvolání události nadřazeného objektu MDI <xref:System.Windows.Forms.Form.Closing> . <xref:System.ComponentModel.CancelEventArgs> argument pro událost nadřazené položky MDI však <xref:System.Windows.Forms.Form.Closing> bude nyní nastaven na hodnotu `true` . Můžete vynutit, aby nadřazený objekt MDI a všechny podřízené formuláře MDI byly uzavřeny nastavením <xref:System.ComponentModel.CancelEventArgs> argumentu na `false` .

## <a name="see-also"></a>Viz také

- [Aplikace MDI (Multiple-Document Interface)](multiple-document-interface-mdi-applications.md)
- [Postupy: Vytváření nadřazených formulářů MDI](how-to-create-mdi-parent-forms.md)
- [Postupy: Určení podřízeného prvku aktivního MDI](how-to-determine-the-active-mdi-child.md)
- [Postupy: Odesílání dat do aktivního podřízeného MDI](how-to-send-data-to-the-active-mdi-child.md)
- [Postupy: Uspořádání podřízených formulářů MDI](how-to-arrange-mdi-child-forms.md)
