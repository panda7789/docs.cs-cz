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
ms.openlocfilehash: b49d43e0e1123921cb3800f0d60193d0ea7b3924
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75338596"
---
# <a name="how-to-create-mdi-child-forms"></a>Postupy: vytváření podřízených formulářů MDI

Podřízené formuláře MDI jsou zásadním prvkem [aplikací rozhraní MDI (Multiple Document Interface)](multiple-document-interface-mdi-applications.md), protože tyto formuláře jsou centrem interakce s uživatelem.

V následujícím postupu použijete Visual Studio k vytvoření podřízeného formuláře MDI, který zobrazí ovládací prvek <xref:System.Windows.Forms.RichTextBox>, podobně jako u většiny aplikací pro zpracování textu. Nahrazením ovládacího prvku <xref:System.Windows.Forms> jinými ovládacími prvky, jako je například ovládací prvek <xref:System.Windows.Forms.DataGridView> nebo kombinace ovládacích prvků, lze vytvořit podřízená okna MDI (a, pomocí rozšíření, aplikací MDI) s různými možnostmi.

## <a name="create-mdi-child-forms"></a>Vytvořit podřízené formuláře MDI

1. V aplikaci Visual Studio vytvořte nový projekt aplikace model Windows Forms. V okně **vlastnosti** formuláře nastavte jeho vlastnost <xref:System.Windows.Forms.Form.IsMdiContainer%2A> na `true` a jeho vlastnost `WindowsState` na `Maximized`.

   Tato položka označuje formulář jako kontejner MDI pro podřízená okna.

2. Z `Toolbox`přetáhněte ovládací prvek <xref:System.Windows.Forms.MenuStrip> do formuláře. Vlastnost `Text` nastavte na **soubor**.

3. Klikněte na tlačítko se třemi tečkami (...) vedle vlastnosti **Items (položky** ) a kliknutím na tlačítko **Přidat** přidejte dvě podřízené položky nabídky pruhu nástrojů. Nastavte vlastnost `Text` pro tyto položky na **nové** a **okno**.

4. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Přidat** > **Nová položka**.

5. V dialogovém okně **Přidat novou položku** vyberte v podokně **šablony** možnost **formulář Windows** (v Visual Basic nebo C#v jazyce Visual) nebo v **aplikaci model Windows Forms (** v C++jazyce Visual) (ve vizuálu). Do pole **název** zadejte název formuláře **Form2**. Vyberte **otevřít** a přidejte formulář do projektu.

    > [!NOTE]
    > Podřízený formulář MDI, který jste vytvořili v tomto kroku, je standardním formulářem Windows. V takovém případě má vlastnost <xref:System.Windows.Forms.Form.Opacity%2A>, která umožňuje ovládat průhlednost formuláře. Vlastnost <xref:System.Windows.Forms.Form.Opacity%2A> však byla navržena pro okna nejvyšší úrovně. Nepoužívejte ji s podřízenými formuláři MDI, protože mohou nastat problémy při malování.

     Tento formulář bude šablonou pro podřízené formuláře MDI.

     Otevře se **Návrhář formulářů** , kde se zobrazí **Form2**.

6. Z **panelu nástrojů**přetáhněte ovládací prvek **RichTextBox** do formuláře.

7. V okně **vlastnosti** nastavte vlastnost `Anchor` na **horní, levou** a vlastnost `Dock` na hodnotu **Fill**.

   To způsobí, že ovládací prvek <xref:System.Windows.Forms.RichTextBox> zcela vyplní oblast podřízeného formuláře MDI, a to i v případě, že se změní velikost formuláře.

8. Dvojitým kliknutím na položku **nové** nabídky vytvoříte obslužnou rutinu události <xref:System.Windows.Forms.Control.Click>.

9. Vložte kód podobný následujícímu pro vytvoření nového podřízeného formuláře MDI, když uživatel klikne na **novou** položku nabídky.

   > [!NOTE]
   > V následujícím příkladu obslužná rutina události zpracovává událost <xref:System.Windows.Forms.Control.Click> pro `MenuItem2`. Mějte na paměti, že v závislosti na konkrétních verzích vaší architektury aplikace nemusí být vaše **Nová** položka nabídky `MenuItem2`.

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

   V C++přidejte následující direktivu `#include` v horní části Form1. h:

   ```cpp
   #include "Form2.h"
   ```

10. V rozevíracím seznamu v horní části okna **vlastnosti** vyberte pruh nabídky, který odpovídá pruhu nabídky **soubor** , a nastavte vlastnost <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> na <xref:System.Windows.Forms.ToolStripMenuItem>okna.

    Tím umožníte, aby nabídka **okna** udržovala seznam otevřených podřízených oken MDI se značkou zaškrtnutí vedle aktivního podřízeného okna.

11. Stisknutím klávesy **F5** spusťte aplikaci. Výběrem možnosti **Nový** v nabídce **soubor** můžete vytvořit nové podřízené formuláře MDI, které se udržují v položce nabídky **okna** .

    > [!NOTE]
    > Pokud má podřízený formulář MDI komponentu <xref:System.Windows.Forms.MainMenu> (obvykle se jedná o strukturu nabídky položek nabídky) a je otevřená v nadřazeném formuláři MDI, který má komponentu <xref:System.Windows.Forms.MainMenu> (obvykle se jedná o strukturu nabídky položek nabídky), položky nabídky se sloučí automaticky, pokud jste nastavili vlastnost <xref:System.Windows.Forms.MenuItem.MergeType%2A> (a volitelně také vlastnost <xref:System.Windows.Forms.MenuItem.MergeOrder%2A>). Nastavte vlastnost <xref:System.Windows.Forms.MenuItem.MergeType%2A> obou komponent <xref:System.Windows.Forms.MainMenu> a všechny položky nabídky podřízeného formuláře na <xref:System.Windows.Forms.MenuMerge.MergeItems>. Kromě toho nastavte vlastnost <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> tak, aby se položky nabídky z obou nabídek zobrazovaly v požadovaném pořadí. Kromě toho mějte na paměti, že když zavřete nadřazený formulář MDI, každý z podřízených formulářů MDI vyvolá událost <xref:System.Windows.Forms.Form.Closing> před tím, než dojde k události <xref:System.Windows.Forms.Form.Closing> pro nadřazený objekt MDI. Zrušení události <xref:System.Windows.Forms.Form.Closing> podřízeného objektu MDI nezabrání v vyvolání události <xref:System.Windows.Forms.Form.Closing> nadřazených objektů MDI; Nicméně argument <xref:System.ComponentModel.CancelEventArgs> pro událost <xref:System.Windows.Forms.Form.Closing> nadřazeného objektu MDI se teď nastaví na `true`. Můžete vynutit, aby nadřazený objekt MDI a všechny podřízené formuláře MDI byly uzavřeny nastavením argumentu <xref:System.ComponentModel.CancelEventArgs> `false`.

## <a name="see-also"></a>Viz také:

- [Aplikace MDI (Multiple-Document Interface)](multiple-document-interface-mdi-applications.md)
- [Postupy: Vytváření nadřazených formulářů MDI](how-to-create-mdi-parent-forms.md)
- [Postupy: Určení podřízeného prvku aktivního MDI](how-to-determine-the-active-mdi-child.md)
- [Postupy: Odesílání dat do aktivního podřízeného MDI](how-to-send-data-to-the-active-mdi-child.md)
- [Postupy: Uspořádání podřízených formulářů MDI](how-to-arrange-mdi-child-forms.md)
