---
title: 'Postupy: Vytváření podřízených formulářů MDI'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d28a7390ea3cfbd922f029d963ad3249db399177
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-mdi-child-forms"></a>Postupy: Vytváření podřízených formulářů MDI
Podřízených formulářů MDI jsou důležitou součástí [aplikace rozhraní více dokumentů (MDI)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), jak tyto formuláře jsou center interakce s uživatelem.  
  
 V následujícím postupu vytvoříte MDI podřízené formulář, který zobrazuje <xref:System.Windows.Forms.RichTextBox> řízení, podobně jako většině textových aplikace. Nahraďte <xref:System.Windows.Forms> řídit pomocí dalších kontroly, jako <xref:System.Windows.Forms.DataGridView> ovládací prvek nebo kombinaci prvků umožňuje vytvářet podřízeného MDI windows (a při rozšíření aplikace MDI) s různé možnosti.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-mdi-child-forms"></a>Chcete-li vytvořit podřízeného MDI formuláře  
  
1.  Vytvoření nového projektu Windows Forms. V **Windows vlastnosti** pro daný formulář, nastavte jeho <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost `true`a jeho `WindowsState` vlastnost `Maximized`.  
  
     Tento formulář označí jako kontejner MDI pro podřízené windows.  
  
2.  Z `Toolbox`, přetáhněte ji <xref:System.Windows.Forms.MenuStrip> ovládacího prvku formuláře. Nastavte její `Text` vlastnost **soubor**.  
  
3.  Klikněte na výpustky (...) vedle položky **položky** vlastnost a klikněte na **přidat** přidat dva podřízené položky nabídky pruhu pro nástroj. Nastavte `Text` vlastnost pro tyto položky k **nový** a **okno**.  
  
4.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt, přejděte na **přidat**a potom vyberte **přidat novou položku**.  
  
5.  V **přidat novou položku** dialogové okno, vyberte **formuláře Windows** (v jazyce Visual Basic nebo v jazyce Visual C#) nebo **Windows Forms aplikace (.NET)** (v [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) z  **Šablony** podokně. V **název** pole, název formuláře **Form2**. Klikněte **otevřete** tlačítko pro přidání formuláře do projektu.  
  
    > [!NOTE]
    >  Podřízené formuláře MDI, kterou jste vytvořili v tomto kroku je standardní formuláře systému Windows. Jako takový má <xref:System.Windows.Forms.Form.Opacity%2A> vlastnosti, která vám umožňuje řídit průhlednost formuláře. Ale <xref:System.Windows.Forms.Form.Opacity%2A> vlastnost byl navržený pro windows nejvyšší úrovně. Nepoužívejte ho s podřízených formulářů MDI, protože může docházet k potížím Malování.  
  
     Šablona pro vaše podřízených formulářů MDI bude tento formulář.  
  
     **Návrhář formulářů Windows** otevře, zobrazení **Form2**.  
  
6.  Z **sada nástrojů**, přetáhněte ji **RichTextBox** ovládacího prvku do formuláře.  
  
7.  V **vlastnosti** nastavte `Anchor` vlastnost **Top, levém** a `Dock` vlastnost **vyplnění**.  
  
     To způsobí, že <xref:System.Windows.Forms.RichTextBox> ovládacího prvku na nejbližší oblast podřízené formuláře MDI, i v případě, že se změnila velikost formuláře.  
  
8.  Klikněte dvakrát **nový** položku vytvoříte <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro ni.  
  
9. Vložení kódu podobný následujícímu pro vytvoření nového formuláře MDI podřízené, když uživatel klikne **nový** položku nabídky.  
  
    > [!NOTE]
    >  V následujícím příkladu, zpracuje obslužná rutina události <xref:System.Windows.Forms.Control.Click> událost pro `MenuItem2`. Mějte na paměti, v závislosti na tom, jaké jsou specifikace architektuře aplikace vaše **nový** nemusí být položka nabídky `MenuItem2`.  
  
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
  
     V [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], přidejte následující `#include` direktivy v horní části Form1.h:  
  
    ```cpp  
    #include "Form2.h"  
    ```  
  
10. V rozevíracím seznamu v horní části **vlastnosti** okně vyberte pruhu nabídky, která odpovídá **soubor** pruhu nabídky a sadu <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> vlastnost do okna <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
     Tato akce povolí **okno** nabídky Spravovat seznam otevřete podřízených oken MDI s zatržení vedle active podřízeného okna.  
  
11. Stisknutím klávesy F5 spusťte aplikaci. Výběrem **nový** z **soubor** nabídky, můžete vytvořit nové MDI podřízených formulářů, které jsou zachovány přehled o v **okno** položku nabídky.  
  
    > [!NOTE]
    >  Když má podřízené formuláře MDI <xref:System.Windows.Forms.MainMenu> součást (s, obvykle struktury nabídky položek nabídky) a je otevřen v rámci nadřazené formuláře MDI, který má <xref:System.Windows.Forms.MainMenu> součást (s, obvykle struktury nabídky položek nabídek), v nabídce položky budou automaticky sloučení Pokud jste nastavili <xref:System.Windows.Forms.MenuItem.MergeType%2A> vlastnost (a volitelně <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> vlastnost). Nastavte <xref:System.Windows.Forms.MenuItem.MergeType%2A> vlastnost objektu i <xref:System.Windows.Forms.MainMenu> součásti a všechny položky nabídky podřízené formuláře <xref:System.Windows.Forms.MenuMerge.MergeItems>. Kromě toho nastavit <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> vlastnost tak, že v nabídce položky z obou nabídek zobrazí požadovaným způsobem. Kromě toho mějte na paměti, že při zavření formuláře MDI nadřazené, každý z podřízeného MDI forms vyvolá <xref:System.Windows.Forms.Form.Closing> událostí před <xref:System.Windows.Forms.Form.Closing> je vyvolána událost pro nadřazený prvek MDI. Zrušení podřízeného MDI <xref:System.Windows.Forms.Form.Closing> událostí nezabrání MDI nadřazeného objektu <xref:System.Windows.Forms.Form.Closing> vyvolání; události však <xref:System.ComponentModel.CancelEventArgs> argument pro nadřazený objekt MDI <xref:System.Windows.Forms.Form.Closing> událostí je teď možnost `true`. Můžete vynutit nadřazené MDI a všech podřízených formulářů MDI zavřete nastavením <xref:System.ComponentModel.CancelEventArgs> argument `false`.  
  
## <a name="see-also"></a>Viz také  
 [Aplikace MDI (Multiple-Document Interface)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [Postupy: Vytváření nadřazených formulářů MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Postupy: Určení podřízeného prvku aktivního MDI](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [Postupy: Odesílání dat do aktivního podřízeného MDI](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [Postupy: Uspořádání podřízených formulářů MDI](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
