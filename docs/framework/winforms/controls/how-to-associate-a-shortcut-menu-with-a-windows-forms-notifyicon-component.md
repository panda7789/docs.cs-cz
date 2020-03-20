---
title: Přidružení místní nabídky k komponentě NotifyIcon
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
ms.openlocfilehash: 15a4a06726de348745e5eef03217d693db496a42
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182256"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>Postupy: Přidružení místní nabídky k součásti Windows Forms NotifyIcon
> [!NOTE]
> Přesto <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip> a nahradit a přidat <xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.ContextMenu> funkce a ovládací <xref:System.Windows.Forms.MainMenu> prvky předchozích verzí a <xref:System.Windows.Forms.ContextMenu> jsou zachovány pro zpětnou kompatibilitu a budoucí použití, pokud se rozhodnete.  
  
 Komponenta <xref:System.Windows.Forms.NotifyIcon> zobrazí ikonu v oblasti oznamování stavu na hlavním panelu. Aplikace obvykle umožňují klepnout pravým tlačítkem myši na tuto ikonu a odeslat příkazy do aplikace, kterou představuje. Přisuzováním <xref:System.Windows.Forms.ContextMenu> komponenty k <xref:System.Windows.Forms.NotifyIcon> součásti můžete tuto funkci přidat do aplikací.  
  
> [!NOTE]
> Pokud chcete, aby byla aplikace při spuštění minimalizována <xref:System.Windows.Forms.NotifyIcon> při zobrazení instance součásti na <xref:System.Windows.Forms.Form.WindowState%2A> hlavním <xref:System.Windows.Forms.FormWindowState.Minimized> panelu, <xref:System.Windows.Forms.NotifyIcon> nastavte vlastnost <xref:System.Windows.Forms.NotifyIcon.Visible%2A> hlavního `true`formuláře na vlastnost a ujistěte se, že je vlastnost komponenty nastavena na .  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>Přidružení místní nabídky ke komponentě NotifyIcon v době návrhu  
  
1. Přidejte <xref:System.Windows.Forms.NotifyIcon> součást do formuláře a nastavte důležité vlastnosti, například vlastnosti <xref:System.Windows.Forms.NotifyIcon.Icon%2A> a. <xref:System.Windows.Forms.NotifyIcon.Visible%2A>  
  
     Další informace naleznete v [tématu How to: Add Application Icons to the Task Bar with the Windows Forms NotifyIcon Component](app-icons-to-the-taskbar-with-wf-notifyicon.md).  
  
2. Přidejte <xref:System.Windows.Forms.ContextMenu> komponentu do formuláře systému Windows.  
  
     Přidejte položky nabídky do místní nabídky představující příkazy, které chcete zpřístupnit za běhu. To to je také vhodná doba pro přidání vylepšení nabídky do těchto položek nabídky, jako jsou například přístupové klávesy.  
  
3. Nastavte <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> vlastnost komponenty <xref:System.Windows.Forms.NotifyIcon> na místní nabídku, kterou jste přidali.  
  
     Při této sadě vlastností se po klepnutí na ikonu na hlavním panelu zobrazí místní nabídka.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>Chcete-li přidružit místní nabídku ke komponentě NotifyIcon programově  
  
1. <xref:System.Windows.Forms.NotifyIcon> Vytvořte instanci třídy a <xref:System.Windows.Forms.ContextMenu> třídy s jakýmkoli nastavením vlastností, které je nezbytné pro aplikaci (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> a <xref:System.Windows.Forms.NotifyIcon.Visible%2A> vlastnostmi pro komponentu, <xref:System.Windows.Forms.NotifyIcon> položkami nabídky pro komponentu). <xref:System.Windows.Forms.ContextMenu>  
  
2. Nastavte <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> vlastnost komponenty <xref:System.Windows.Forms.NotifyIcon> na místní nabídku, kterou jste přidali.  
  
     Při této sadě vlastností se po klepnutí na ikonu na hlavním panelu zobrazí místní nabídka.  
  
    > [!NOTE]
    > Následující příklad kódu vytvoří základní strukturu nabídky. Budete muset přizpůsobit možnosti nabídky těm, které odpovídají aplikaci, kterou vyvíjíte. Navíc budete chtít napsat kód pro <xref:System.Windows.Forms.MenuItem.Click> zpracování událostí pro tyto položky nabídky.  
  
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
> Je nutné inicializovat `notifyIcon1` a `contextMenu1,` které můžete provést zahrnutím následujících příkazů do konstruktoru formuláře:  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [Postupy: Přidání ikon aplikací do TaskBar s komponentou Windows Forms NotifyIcon](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [Komponenta NotifyIcon](notifyicon-component-windows-forms.md)
- [NotifyIcon – přehled komponenty](notifyicon-component-overview-windows-forms.md)
