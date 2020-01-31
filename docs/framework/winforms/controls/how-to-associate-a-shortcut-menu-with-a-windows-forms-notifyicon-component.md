---
title: Přidružení místní nabídky ke komponentě NotifyIcon
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
ms.openlocfilehash: 392c04f73feaec201033ad76f9419a0e070bec70
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742046"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>Postupy: Přidružení místní nabídky k součásti Windows Forms NotifyIcon
> [!NOTE]
> I když <xref:System.Windows.Forms.MenuStrip> a <xref:System.Windows.Forms.ContextMenuStrip> nahrazují a přidává funkce do <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu>ových ovládacích prvků předchozích verzí, <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> se uchovávají pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.  
  
 Komponenta <xref:System.Windows.Forms.NotifyIcon> zobrazí ikonu v oznamovací oblasti hlavního panelu. Aplikace vám běžně umožní odeslat příkazy do aplikace, kterou představuje, kliknutím pravým tlačítkem myši na tuto ikonu. Tím, že přidružíte komponentu <xref:System.Windows.Forms.ContextMenu> ke komponentě <xref:System.Windows.Forms.NotifyIcon>, můžete tuto funkci přidat do svých aplikací.  
  
> [!NOTE]
> Pokud chcete, aby byla aplikace minimalizována při spuštění při zobrazení instance <xref:System.Windows.Forms.NotifyIcon> komponenty na hlavním panelu, nastavte vlastnost <xref:System.Windows.Forms.Form.WindowState%2A> hlavního formuláře na hodnotu <xref:System.Windows.Forms.FormWindowState.Minimized> a ujistěte se, že vlastnost <xref:System.Windows.Forms.NotifyIcon.Visible%2A> komponenty <xref:System.Windows.Forms.NotifyIcon> je nastavena na hodnotu `true`.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>Přidružení místní nabídky ke komponentě NotifyIcon v době návrhu  
  
1. Přidejte do formuláře komponentu <xref:System.Windows.Forms.NotifyIcon> a nastavte důležité vlastnosti, jako jsou vlastnosti <xref:System.Windows.Forms.NotifyIcon.Icon%2A> a <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.  
  
     Další informace najdete v tématu [Postup: přidání ikon aplikace na hlavní panel s model Windows Forms komponentou NotifyIcon](app-icons-to-the-taskbar-with-wf-notifyicon.md).  
  
2. Přidejte <xref:System.Windows.Forms.ContextMenu>ovou komponentu do formuláře Windows.  
  
     Přidejte položky nabídky do místní nabídky reprezentující příkazy, které mají být v době běhu k dispozici. To je také dobrý čas pro přidání vylepšení nabídky do těchto položek nabídky, jako jsou přístupové klíče.  
  
3. Nastavte vlastnost <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> komponenty <xref:System.Windows.Forms.NotifyIcon> na místní nabídku, kterou jste přidali.  
  
     Když je tato vlastnost nastavená, zobrazí se místní nabídka při kliknutí na ikonu na hlavním panelu.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>Postup při přidružování místní nabídky k součásti NotifyIcon programově  
  
1. Vytvořte instanci třídy <xref:System.Windows.Forms.NotifyIcon> a třídu <xref:System.Windows.Forms.ContextMenu>, s jakýmkoli nastavením vlastností, které jsou nezbytné pro aplikaci (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> a <xref:System.Windows.Forms.NotifyIcon.Visible%2A> vlastnosti pro součást <xref:System.Windows.Forms.NotifyIcon>, položky nabídky pro součást <xref:System.Windows.Forms.ContextMenu>).  
  
2. Nastavte vlastnost <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> komponenty <xref:System.Windows.Forms.NotifyIcon> na místní nabídku, kterou jste přidali.  
  
     Když je tato vlastnost nastavená, zobrazí se místní nabídka při kliknutí na ikonu na hlavním panelu.  
  
    > [!NOTE]
    > Následující příklad kódu vytvoří základní strukturu nabídky. Volby nabídky budete muset přizpůsobit na ty, které se vejdou do aplikace, kterou vyvíjíte. Navíc budete chtít napsat kód, který bude zpracovávat události <xref:System.Windows.Forms.MenuItem.Click> pro tyto položky nabídky.  
  
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
> Je nutné inicializovat `notifyIcon1` a `contextMenu1,`, které lze provést zahrnutím následujících příkazů do konstruktoru formuláře:  
  
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
