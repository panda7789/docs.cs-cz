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
ms.openlocfilehash: bf5602d0526fdd97f0cc14382339095a793f13c3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922771"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>Postupy: Přidružení místní nabídky ke komponentě Windows Forms NotifyIcon
> [!NOTE]
> I <xref:System.Windows.Forms.MenuStrip> když <xref:System.Windows.Forms.ContextMenuStrip> a <xref:System.Windows.Forms.ContextMenu> v <xref:System.Windows.Forms.MainMenu> případě potřeby nahrazují a přidávají funkce do ovládacích prvků <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> v předchozích verzích a jsou zachované pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.  
  
 <xref:System.Windows.Forms.NotifyIcon> Komponenta zobrazí ikonu v oznamovací oblasti hlavního panelu. Aplikace vám běžně umožní odeslat příkazy do aplikace, kterou představuje, kliknutím pravým tlačítkem myši na tuto ikonu. Tím, že přidružíte <xref:System.Windows.Forms.ContextMenu> komponentu <xref:System.Windows.Forms.NotifyIcon> ke komponentě, můžete tuto funkci přidat do svých aplikací.  
  
> [!NOTE]
> Pokud chcete, aby <xref:System.Windows.Forms.NotifyIcon> byla aplikace minimalizována při spuštění při zobrazení instance komponenty na hlavním panelu, nastavte <xref:System.Windows.Forms.Form.WindowState%2A> vlastnost hlavního formuláře <xref:System.Windows.Forms.NotifyIcon> na <xref:System.Windows.Forms.FormWindowState.Minimized> a ujistěte se, že <xref:System.Windows.Forms.NotifyIcon.Visible%2A> vlastnost komponenty je nastaven na `true`.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>Přidružení místní nabídky ke komponentě NotifyIcon v době návrhu  
  
1. Přidejte komponentu do formuláře a nastavte důležité vlastnosti, jako jsou <xref:System.Windows.Forms.NotifyIcon.Icon%2A> například vlastnosti a <xref:System.Windows.Forms.NotifyIcon.Visible%2A>. <xref:System.Windows.Forms.NotifyIcon>  
  
     Další informace najdete v tématu [jak: Přidejte ikony aplikace na hlavní panel s model Windows Forms komponentou](app-icons-to-the-taskbar-with-wf-notifyicon.md)NotifyIcon.  
  
2. <xref:System.Windows.Forms.ContextMenu> Přidejte komponentu do formuláře Windows.  
  
     Přidejte položky nabídky do místní nabídky reprezentující příkazy, které mají být v době běhu k dispozici. To je také dobrý čas pro přidání vylepšení nabídky do těchto položek nabídky, jako jsou přístupové klíče.  
  
3. <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> Nastavte vlastnost <xref:System.Windows.Forms.NotifyIcon> komponenty na místní nabídku, kterou jste přidali.  
  
     Když je tato vlastnost nastavená, zobrazí se místní nabídka při kliknutí na ikonu na hlavním panelu.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>Postup při přidružování místní nabídky k součásti NotifyIcon programově  
  
1. Vytvoření instance <xref:System.Windows.Forms.NotifyIcon> třídy <xref:System.Windows.Forms.NotifyIcon> <xref:System.Windows.Forms.NotifyIcon.Icon%2A> <xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.NotifyIcon.Visible%2A> a třídy s libovolným nastavením vlastností, které jsou nezbytné pro aplikaci (a vlastností komponenty, položek nabídky pro <xref:System.Windows.Forms.ContextMenu> součást).  
  
2. <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> Nastavte vlastnost <xref:System.Windows.Forms.NotifyIcon> komponenty na místní nabídku, kterou jste přidali.  
  
     Když je tato vlastnost nastavená, zobrazí se místní nabídka při kliknutí na ikonu na hlavním panelu.  
  
    > [!NOTE]
    > Následující příklad kódu vytvoří základní strukturu nabídky. Volby nabídky budete muset přizpůsobit na ty, které se vejdou do aplikace, kterou vyvíjíte. Navíc budete chtít napsat kód pro zpracování <xref:System.Windows.Forms.MenuItem.Click> událostí pro tyto položky nabídky.  
  
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
> Je nutné inicializovat `notifyIcon1` a `contextMenu1,` , které lze provést zahrnutím následujících příkazů do konstruktoru formuláře:  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [Postupy: Přidání ikon aplikace na hlavní panel se součástí model Windows Forms NotifyIcon](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [Komponenta NotifyIcon](notifyicon-component-windows-forms.md)
- [Přehled komponenty NotifyIcon](notifyicon-component-overview-windows-forms.md)
