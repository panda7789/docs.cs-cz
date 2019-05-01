---
title: 'Postupy: Přidružení místní nabídky ke komponentě Windows Forms NotifyIcon'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- context menus [Windows Forms], for background processes
- NotifyIcon component [Windows Forms], associating shortcut menus
- shortcut menus [Windows Forms], for background processes
ms.assetid: d68f3926-08d3-4f7d-949f-1981b29cf188
ms.openlocfilehash: f2a086cc25eb6996b2643742a887bccf481916d6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010940"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>Postupy: Přidružení místní nabídky ke komponentě Windows Forms NotifyIcon
> [!NOTE]
>  I když <xref:System.Windows.Forms.MenuStrip> a <xref:System.Windows.Forms.ContextMenuStrip> nahradit a přidání funkce, které <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> ovládací prvky z předchozích verzí <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> se zachovají pro zpětnou kompatibilitu a budoucí použití, pokud se rozhodnete.  
  
 <xref:System.Windows.Forms.NotifyIcon> Komponenty zobrazuje ikonu v oznamovací oblasti na hlavním panelu Stav. Běžně aplikace vám umožňují klikněte pravým tlačítkem na tuto ikonu odesílat příkazy do aplikace, kterou představuje. Tím, že přidružíte <xref:System.Windows.Forms.ContextMenu> komponentu s <xref:System.Windows.Forms.NotifyIcon> komponentu, můžou dodat tuto funkci pro vaše aplikace.  
  
> [!NOTE]
>  Pokud chcete při zobrazování instance minimalizaci při spuštění aplikace <xref:System.Windows.Forms.NotifyIcon> komponenty na hlavním panelu nastavit hlavní formulář <xref:System.Windows.Forms.Form.WindowState%2A> vlastnost <xref:System.Windows.Forms.FormWindowState.Minimized> a ujistěte se, <xref:System.Windows.Forms.NotifyIcon> komponenty <xref:System.Windows.Forms.NotifyIcon.Visible%2A> vlastnost je nastavena na `true`.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>Chcete-li přidružení místní nabídky ke komponentě NotifyIcon v době návrhu  
  
1. Přidat <xref:System.Windows.Forms.NotifyIcon> komponentu do formuláře a nastavte důležité vlastnosti, jako je třeba <xref:System.Windows.Forms.NotifyIcon.Icon%2A> a <xref:System.Windows.Forms.NotifyIcon.Visible%2A> vlastnosti.  
  
     Další informace najdete v tématu [jak: Přidání ikon aplikací do TaskBar se Windows Forms NotifyIcon – komponenta](app-icons-to-the-taskbar-with-wf-notifyicon.md).  
  
2. Přidat <xref:System.Windows.Forms.ContextMenu> komponentu do formuláře Windows.  
  
     Přidání položek nabídky do místní nabídky představující příkazy, že které chcete zpřístupnit v době běhu. Toto je vhodná doba k přidání vylepšení nabídky do těchto položek nabídky, jako jsou přístupové klíče.  
  
3. Nastavte <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> vlastnost <xref:System.Windows.Forms.NotifyIcon> komponentu do místní nabídky, kterou jste přidali.  
  
     S touto sadou vlastností v místní nabídce se zobrazí po kliknutí na ikonu na hlavním panelu.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>Chcete-li přidružení místní nabídky ke komponentě NotifyIcon prostřednictvím kódu programu  
  
1. Vytvoření instance <xref:System.Windows.Forms.NotifyIcon> třídy a <xref:System.Windows.Forms.ContextMenu> třídy s jakékoli nastavení vlastností jsou nezbytné pro aplikaci (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> a <xref:System.Windows.Forms.NotifyIcon.Visible%2A> vlastnosti <xref:System.Windows.Forms.NotifyIcon> komponenty, položky nabídky pro <xref:System.Windows.Forms.ContextMenu> komponenta).  
  
2. Nastavte <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> vlastnost <xref:System.Windows.Forms.NotifyIcon> komponentu do místní nabídky, kterou jste přidali.  
  
     S touto sadou vlastností v místní nabídce se zobrazí po kliknutí na ikonu na hlavním panelu.  
  
    > [!NOTE]
    >  Následující příklad kódu vytvoří struktura základní nabídky. Je potřeba upravit možnosti nabídek na ty, které odpovídají aplikaci, kterou vyvíjíte. Kromě toho můžete napsat kód pro zpracování <xref:System.Windows.Forms.MenuItem.Click> události pro tyto položky nabídky.  
  
    ```vb  
    Public ContextMenu1 As New ContextMenu  
    Public NotifyIcon1 As New NotifyIcon  
  
    Public Sub CreateIconMenuStructure()  
       ' Add menu items to shortcut menu.  
       ContextMenu1.MenuItems.Add("&Open Application")  
       ContextMenu1.MenuItems.Add("S&uspend Application")  
       ContextMenu1.MenuItems.Add("E&xit")  
  
       ' Set properties of NotifyIcon component.  
       NotifyIcon1.Icon = New System.Drawing.Icon _   
          (System.Environment.GetFolderPath _   
          (System.Environment.SpecialFolder.Personal)  _   
          & "\Icon.ico")  
       NotifyIcon1.Text = "Right-click me!"  
       NotifyIcon1.Visible = True  
       NotifyIcon1.ContextMenu = ContextMenu1  
    End Sub  
    ```  
  
```csharp  
public NotifyIcon notifyIcon1 = new NotifyIcon();  
public ContextMenu contextMenu1 = new ContextMenu();  
  
public void createIconMenuStructure()  
{  
   // Add menu items to shortcut menu.  
   contextMenu1.MenuItems.Add("&Open Application");  
   contextMenu1.MenuItems.Add("S&uspend Application");  
   contextMenu1.MenuItems.Add("E&xit");  
  
   // Set properties of NotifyIcon component.  
   notifyIcon1.Icon = new System.Drawing.Icon  
      (System.Environment.GetFolderPath  
      (System.Environment.SpecialFolder.Personal)  
      + @"\Icon.ico");  
   notifyIcon1.Visible = true;  
   notifyIcon1.Text = "Right-click me!";  
   notifyIcon1.Visible = true;  
   notifyIcon1.ContextMenu = contextMenu1;  
}  
```  
  
```cpp  
public:  
   System::Windows::Forms::NotifyIcon ^ notifyIcon1;  
   System::Windows::Forms::ContextMenu ^ contextMenu1;  
  
   void createIconMenuStructure()  
   {  
      // Add menu items to shortcut menu.  
      contextMenu1->MenuItems->Add("&Open Application");  
      contextMenu1->MenuItems->Add("S&uspend Application");  
      contextMenu1->MenuItems->Add("E&xit");  
  
      // Set properties of NotifyIcon component.  
      notifyIcon1->Icon = gcnew System::Drawing::Icon  
          (String::Concat(System::Environment::GetFolderPath  
          (System::Environment::SpecialFolder::Personal),  
          "\\Icon.ico"));  
      notifyIcon1->Text = "Right-click me!";  
      notifyIcon1->Visible = true;  
      notifyIcon1->ContextMenu = contextMenu1;  
   }  
```  
  
> [!NOTE]
>  Je třeba inicializovat `notifyIcon1` a `contextMenu1,` což lze provést přidáním následující příkazy v konstruktoru formuláře:  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [Postupy: Přidání ikon aplikací do TaskBar s komponentou Windows Forms NotifyIcon](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [Komponenta NotifyIcon](notifyicon-component-windows-forms.md)
- [Přehled komponenty NotifyIcon](notifyicon-component-overview-windows-forms.md)
