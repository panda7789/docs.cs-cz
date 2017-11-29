---
title: "Postupy: Přidružení místní nabídky k součásti Windows Forms NotifyIcon"
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
- context menus [Windows Forms], for background processes
- NotifyIcon component [Windows Forms], associating shortcut menus
- shortcut menus [Windows Forms], for background processes
ms.assetid: d68f3926-08d3-4f7d-949f-1981b29cf188
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 985aa58056f4c4ec8f3042c682291508f1434ee0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>Postupy: Přidružení místní nabídky k součásti Windows Forms NotifyIcon
> [!NOTE]
>  I když <xref:System.Windows.Forms.MenuStrip> a <xref:System.Windows.Forms.ContextMenuStrip> nahradit a přidání funkce do <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> ovládací prvky předchozí verze, <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> se zachovají pro zpětnou kompatibilitu a budoucí použití, pokud si zvolíte.  
  
 <xref:System.Windows.Forms.NotifyIcon> Součást zobrazí ikonu v oznamovací oblasti stav na hlavním panelu. Běžně aplikace umožňují klikněte pravým tlačítkem na tuto ikonu odesílat příkazy do aplikace, který představuje. Tím, že přidružíte <xref:System.Windows.Forms.ContextMenu> součásti s <xref:System.Windows.Forms.NotifyIcon> součásti, tato funkce můžete přidat do vaší aplikace.  
  
> [!NOTE]
>  Pokud chcete minimalizovat při spuštění při zobrazování instanci aplikace <xref:System.Windows.Forms.NotifyIcon> součásti na hlavním panelu nastavit hlavní formulář <xref:System.Windows.Forms.Form.WindowState%2A> vlastnost, která má <xref:System.Windows.Forms.FormWindowState.Minimized> a ujistěte se, <xref:System.Windows.Forms.NotifyIcon> součásti <xref:System.Windows.Forms.NotifyIcon.Visible%2A> vlastnost je nastavena na `true`.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>Chcete-li přidružení místní nabídky ke komponentě NotifyIcon v době návrhu  
  
1.  Přidat <xref:System.Windows.Forms.NotifyIcon> součásti do svého formuláře a nastavte důležité vlastnosti, jako je třeba <xref:System.Windows.Forms.NotifyIcon.Icon%2A> a <xref:System.Windows.Forms.NotifyIcon.Visible%2A> vlastnosti.  
  
     Další informace najdete v tématu [postupy: přidání ikon aplikací do TaskBar se součástí Windows Forms NotifyIcon](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).  
  
2.  Přidat <xref:System.Windows.Forms.ContextMenu> součásti do svého formuláře systému Windows.  
  
     Přidání položek nabídky do místní nabídky představující příkazy, že které chcete zpřístupnit v době běhu. Toto je také vhodná doba na vylepšení nabídky přidat do těchto položek nabídky, jako je například přístupové klíče.  
  
3.  Nastavte <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> vlastnost <xref:System.Windows.Forms.NotifyIcon> součásti do místní nabídky, které jste přidali.  
  
     S touto sadou vlastností místní nabídce se zobrazí po kliknutí na ikonu na hlavním panelu.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>Chcete-li přidružení místní nabídky ke komponentě NotifyIcon prostřednictvím kódu programu  
  
1.  Vytvoření instance <xref:System.Windows.Forms.NotifyIcon> – třída a <xref:System.Windows.Forms.ContextMenu> třídě, ať nastavení vlastností jsou nezbytné pro aplikaci (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> a <xref:System.Windows.Forms.NotifyIcon.Visible%2A> vlastnosti pro <xref:System.Windows.Forms.NotifyIcon> součásti, položky nabídky pro <xref:System.Windows.Forms.ContextMenu> komponenta).  
  
2.  Nastavte <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> vlastnost <xref:System.Windows.Forms.NotifyIcon> součásti do místní nabídky, které jste přidali.  
  
     S touto sadou vlastností místní nabídce se zobrazí po kliknutí na ikonu na hlavním panelu.  
  
    > [!NOTE]
    >  Následující příklad kódu vytvoří strukturu základní nabídky. Musíte se k přizpůsobení možnosti nabídky na ty, které aplikace, které vyvíjíte přizpůsobit. Kromě toho můžete napsat kód pro zpracování <xref:System.Windows.Forms.MenuItem.Click> události pro tyto položky nabídky.  
  
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
>  Je třeba inicializovat `notifyIcon1` a `contextMenu1,` tu lze v konstruktoru formuláře včetně následující příkazy:  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.NotifyIcon>  
 <xref:System.Windows.Forms.NotifyIcon.Icon%2A>  
 [Postupy: přidání ikon aplikací do TaskBar se Windows Forms NotifyIcon – komponenta](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md)  
 [NotifyIcon – komponenta](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)  
 [NotifyIcon – přehled komponenty](../../../../docs/framework/winforms/controls/notifyicon-component-overview-windows-forms.md)
