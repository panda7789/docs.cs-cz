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
ms.openlocfilehash: 73f2004470d5d1da04199af75832cefd6348ce18
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342456"
---
# <a name="how-to-create-mdi-child-forms"></a>Postupy: Vytváření podřízených formulářů MDI
Podřízené formuláře MDI jsou důležitou součástí [aplikace rozhraní více dokumentů (MDI)](multiple-document-interface-mdi-applications.md), jako jsou centra interakci s uživatelem.  
  
 V následujícím postupu vytvoříte podřízený formulář MDI, která se zobrazí <xref:System.Windows.Forms.RichTextBox> nejvíce zpracování textu žádosti podobně jako ovládací prvek. Nahrazování <xref:System.Windows.Forms> ovládací prvek s jinými ovládacími prvky, jako <xref:System.Windows.Forms.DataGridView> ovládací prvek nebo kombinaci ovládací prvky vám umožní vytvořit podřízený formulář MDI systému windows (a při rozšíření i pro aplikace MDI) s různými možnostmi.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-mdi-child-forms"></a>Chcete-li vytvořit podřízený formulář MDI formuláře  
  
1. Vytvoření nového projektu Windows Forms. V **Windows vlastnosti** formuláři, nastavit jeho <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost `true`a jeho `WindowsState` vlastnost `Maximized`.  
  
     Ta určuje formuláře jako kontejnerem MDI pro podřízená okna.  
  
2. Z `Toolbox`, přetáhněte <xref:System.Windows.Forms.MenuStrip> ovládacího prvku na formuláři. Nastavte jeho `Text` vlastnost **souboru**.  
  
3. Klikněte na symbol tří teček (...) vedle položky **položky** vlastnost a klikněte na tlačítko **přidat** přidat dva podřízené položky nabídky pruhu pro nástroj. Nastavte `Text` vlastnost pro tyto položky **nový** a **okno**.  
  
4. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt, přejděte na **přidat**a pak vyberte **přidat novou položku**.  
  
5. V **přidat novou položku** dialogu **formuláře Windows** (v jazyce Visual Basic nebo Visual C#) nebo **Windows Forms aplikace (.NET)** (v [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) z  **Šablony** podokně. V **název** pole, pojmenujte formulář **Form2**. Klikněte na tlačítko **otevřít** tlačítko pro přidání formuláře do projektu.  
  
    > [!NOTE]
    >  Podřízený formulář MDI, které jste vytvořili v tomto kroku je běžného formuláře Windows. V důsledku toho je <xref:System.Windows.Forms.Form.Opacity%2A> vlastnost, která vám umožňuje řídit průhlednost formuláře. Ale <xref:System.Windows.Forms.Form.Opacity%2A> vlastnost je navržená pro okna nejvyšší úrovně. Nepoužívejte ho s podřízených formulářů MDI, protože může dojít k problémům Malování.  
  
     Šablona pro podřízené formuláře MDI bude tento formulář.  
  
     **Návrháře formulářů Windows** otevře zobrazení **Form2**.  
  
6. Z **nástrojů**, přetáhněte **RichTextBox** ovládacího prvku na formuláři.  
  
7. V **vlastnosti** okno, nastaveno `Anchor` vlastnost **horní, levý** a `Dock` vlastnost **vyplnit**.  
  
     To způsobí, že <xref:System.Windows.Forms.RichTextBox> ovládací prvek pro úplně naplnění oblasti podřízený formulář MDI, i když se změní velikost formuláře.  
  
8. Dvakrát klikněte **nový** vytvořit položku nabídky <xref:System.Windows.Forms.Control.Click> obslužnou rutinu události pro něj.  
  
9. Vložte kód podobný následujícímu vytvořit nový podřízený formulář MDI, když uživatel klikne **nový** položky nabídky.  
  
    > [!NOTE]
    >  V následujícím příkladu, zpracuje obslužná rutina události <xref:System.Windows.Forms.Control.Click> událost pro `MenuItem2`. Mějte na paměti, že v závislosti na tom, jaké jsou specifikace architektury aplikace, vaše **nový** nemusí být položka nabídky `MenuItem2`.  
  
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
  
     V [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], přidejte následující `#include` direktiv v horní části Form1.h:  
  
    ```cpp  
    #include "Form2.h"  
    ```  
  
10. V rozevíracím seznamu v horní části **vlastnosti** okna, vyberte pruh nabídky, která odpovídá **souboru** pruhu nabídky a nastavte <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> vlastností v okně <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
     To vám umožní **okno** nabídky Spravovat seznam otevřít podřízených oken MDI zaškrtnutí vedle aktivní podřízené okno.  
  
11. Stisknutím klávesy F5 spusťte aplikaci. Výběrem **nový** z **souboru** nabídku, můžete vytvořit nové MDI podřízené formuláře, které jsou udržovat přehled o v **okno** položky nabídky.  
  
    > [!NOTE]
    >  Pokud má podřízený formulář MDI <xref:System.Windows.Forms.MainMenu> součásti (s většinou, nabídky strukturu položek nabídky) a je otevřen v rámci, který má nadřazený formulář MDI <xref:System.Windows.Forms.MainMenu> součásti (s většinou, nabídky strukturu položek nabídek), v nabídce položky budou automaticky sloučit Pokud jste nastavili <xref:System.Windows.Forms.MenuItem.MergeType%2A> vlastnosti (a volitelně také <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> vlastnost). Nastavte <xref:System.Windows.Forms.MenuItem.MergeType%2A> vlastnost objektu i <xref:System.Windows.Forms.MainMenu> komponenty a všechny položky nabídky podřízené formuláře <xref:System.Windows.Forms.MenuMerge.MergeItems>. Kromě toho nastavení <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> vlastnost tak, aby z obou nabídek položky nabídky zobrazí do požadovaného pořadí. Kromě toho vzít v úvahu, že při zavření nadřazený formulář MDI každý podřízený formulář MDI formuláře vyvolá <xref:System.Windows.Forms.Form.Closing> události před <xref:System.Windows.Forms.Form.Closing> se vyvolá událost pro nadřazený objekt MDI. Zrušení podřízený formulář MDI <xref:System.Windows.Forms.Form.Closing> události nezabrání nadřazený objekt MDI <xref:System.Windows.Forms.Form.Closing> událost vyvolána; však <xref:System.ComponentModel.CancelEventArgs> argument pro nadřazený objekt MDI <xref:System.Windows.Forms.Form.Closing> události se nastaví na `true`. Můžete vynutit nadřazený objekt MDI a všechny podřízené formuláře MDI zavřete tak, že nastavíte <xref:System.ComponentModel.CancelEventArgs> argument `false`.  
  
## <a name="see-also"></a>Viz také:

- [Aplikace MDI (Multiple-Document Interface)](multiple-document-interface-mdi-applications.md)
- [Postupy: Vytváření nadřazených formulářů MDI](how-to-create-mdi-parent-forms.md)
- [Postupy: Určení podřízeného prvku aktivního MDI](how-to-determine-the-active-mdi-child.md)
- [Postupy: Odesílání dat do aktivního podřízeného MDI](how-to-send-data-to-the-active-mdi-child.md)
- [Postupy: Uspořádání podřízených formulářů MDI](how-to-arrange-mdi-child-forms.md)
