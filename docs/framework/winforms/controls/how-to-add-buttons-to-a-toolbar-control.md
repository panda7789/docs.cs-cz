---
title: 'Postupy: Přidání tlačítek do ovládacího prvku ToolBar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: 78a58a8d-1041-4e38-9219-4096fa6a5c5c
ms.openlocfilehash: 1bb6de58010e70a4edafacafe3dc00b511fc63de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182342"
---
# <a name="how-to-add-buttons-to-a-toolbar-control"></a>Postupy: Přidání tlačítek do ovládacího prvku ToolBar
> [!NOTE]
> Ovládací <xref:System.Windows.Forms.ToolStrip> prvek nahradí a přidá <xref:System.Windows.Forms.ToolBar> funkce ovládacího prvku; <xref:System.Windows.Forms.ToolBar> ovládací prvek je však zachován a to jak pro zpětnou kompatibilitu, tak pro budoucí použití, pokud se rozhodnete.  
  
 Nedílnou součástí ovládacího <xref:System.Windows.Forms.ToolBar> prvku jsou tlačítka, která k němu přidáte. Ty mohou být použity k poskytnutí snadného přístupu k příkazům nabídky nebo alternativně mohou být umístěny v jiné oblasti uživatelského rozhraní aplikace a zpřístupnit tak příkazy uživatelům, které nejsou k dispozici ve struktuře nabídky.  
  
 Níže uvedené příklady <xref:System.Windows.Forms.ToolBar> předpokládají, že ovládací prvek`Form1`byl přidán do formuláře systému Windows ( ).  
  
### <a name="to-add-buttons-programmatically"></a>Přidání tlačítek programově  
  
1. V postupu vytvořte tlačítka panelu nástrojů <xref:System.Windows.Forms.ToolBar.Buttons%2A?displayProperty=nameWithType> jejich přidáním do kolekce.  
  
2. Zadejte nastavení vlastností pro jednotlivé tlačítko předáním <xref:System.Windows.Forms.ToolBar.Buttons%2A> indexu tlačítka prostřednictvím vlastnosti.  
  
     Následující příklad předpokládá formulář s <xref:System.Windows.Forms.ToolBar> již přidaným ovládacím prvkem.  
  
    > [!NOTE]
    > Kolekce <xref:System.Windows.Forms.ToolBar.Buttons%2A?displayProperty=nameWithType> je kolekce na základě nula, takže kód by měl postupovat odpovídajícím způsobem.  
  
    ```vb  
    Public Sub CreateToolBarButtons()  
    ' Create buttons and set text property.  
       ToolBar1.Buttons.Add("One")  
       ToolBar1.Buttons.Add("Two")  
       ToolBar1.Buttons.Add("Three")  
       ToolBar1.Buttons.Add("Four")  
    ' Set properties of StatusBar panels.  
    ' Set Style property.  
       ToolBar1.Buttons(0).Style = ToolBarButtonStyle.PushButton  
       ToolBar1.Buttons(1).Style = ToolBarButtonStyle.Separator  
       ToolBar1.Buttons(2).Style = ToolBarButtonStyle.ToggleButton  
       ToolBar1.Buttons(3).Style = ToolBarButtonStyle.DropDownButton  
    ' Set the ToggleButton's PartialPush property.  
       ToolBar1.Buttons(2).PartialPush = True  
    ' Instantiate a ContextMenu component and menu items.  
    ' Set the DropDownButton's DropDownMenu property to the context menu.  
       Dim cm As New ContextMenu()  
       Dim miOne As New MenuItem("One")  
       Dim miTwo As New MenuItem("Two")  
       Dim miThree As New MenuItem("Three")  
       cm.MenuItems.Add(miOne)  
       cm.MenuItems.Add(miTwo)  
       cm.MenuItems.Add(miThree)  
       ToolBar1.Buttons(3).DropDownMenu = cm  
    ' Set the PushButton's Pushed property.  
       ToolBar1.Buttons(0).Pushed = True  
    ' Set the ToolTipText property of one of the buttons.  
       ToolBar1.Buttons(1).ToolTipText = "Button 2"  
    End Sub  
    ```  
  
    ```csharp  
    public void CreateToolBarButtons()  
    {  
       // Create buttons and set text property.  
       toolBar1.Buttons.Add("One");  
       toolBar1.Buttons.Add("Two");  
       toolBar1.Buttons.Add("Three");  
       toolBar1.Buttons.Add("Four");  
  
       // Set properties of StatusBar panels.  
       // Set Style property.  
       toolBar1.Buttons[0].Style = ToolBarButtonStyle.PushButton;  
       toolBar1.Buttons[1].Style = ToolBarButtonStyle.Separator;  
       toolBar1.Buttons[2].Style = ToolBarButtonStyle.ToggleButton;  
       toolBar1.Buttons[3].Style = ToolBarButtonStyle.DropDownButton;  
  
       // Set the ToggleButton's PartialPush property.  
       toolBar1.Buttons[2].PartialPush = true;  
  
       // Instantiate a ContextMenu component and menu items.  
       // Set the DropDownButton's DropDownMenu property to
       // the context menu.  
       ContextMenu cm = new ContextMenu();  
       MenuItem miOne = new MenuItem("One");  
       MenuItem miTwo = new MenuItem("Two");  
       MenuItem miThree = new MenuItem("Three");  
       cm.MenuItems.Add(miOne);  
       cm.MenuItems.Add(miTwo);  
       cm.MenuItems.Add(miThree);  
  
       toolBar1.Buttons[3].DropDownMenu = cm;  
       // Set the PushButton's Pushed property.  
       toolBar1.Buttons[0].Pushed = true;  
       // Set the ToolTipText property of 1 of the buttons.  
       toolBar1.Buttons[1].ToolTipText = "Button 2";  
    }  
    ```  
  
    ```cpp  
    public:  
       void CreateToolBarButtons()  
       {  
          // Create buttons and set text property.  
          toolBar1->Buttons->Add( "One" );  
          toolBar1->Buttons->Add( "Two" );  
          toolBar1->Buttons->Add( "Three" );  
          toolBar1->Buttons->Add( "Four" );  
  
          // Set properties of StatusBar panels.  
          // Set Style property.  
          toolBar1->Buttons[0]->Style = ToolBarButtonStyle::PushButton;  
          toolBar1->Buttons[1]->Style = ToolBarButtonStyle::Separator;  
          toolBar1->Buttons[2]->Style = ToolBarButtonStyle::ToggleButton;  
          toolBar1->Buttons[3]->Style = ToolBarButtonStyle::DropDownButton;  
  
          // Set the ToggleButton's PartialPush property.  
          toolBar1->Buttons[2]->PartialPush = true;  
  
          // Instantiate a ContextMenu component and menu items.  
          // Set the DropDownButton's DropDownMenu property to
          // the context menu.  
          System::Windows::Forms::ContextMenu^ cm = gcnew System::Windows::Forms::ContextMenu;  
          MenuItem^ miOne = gcnew MenuItem( "One" );  
          MenuItem^ miTwo = gcnew MenuItem( "Two" );  
          MenuItem^ miThree = gcnew MenuItem( "Three" );  
          cm->MenuItems->Add( miOne );  
          cm->MenuItems->Add( miTwo );  
          cm->MenuItems->Add( miThree );  
          toolBar1->Buttons[3]->DropDownMenu = cm;  
  
          // Set the PushButton's Pushed property.  
          toolBar1->Buttons[0]->Pushed = true;  
  
          // Set the ToolTipText property of 1 of the buttons.  
          toolBar1->Buttons[1]->ToolTipText = "Button 2";  
       }  
    ```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ToolBar>
- [Postupy: Definování ikony pro tlačítko ToolBar](how-to-define-an-icon-for-a-toolbar-button.md)
- [Postupy: Spouštění událostí nabídky pro tlačítka panelu nástrojů](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [ToolBar – přehled ovládacího prvku](toolbar-control-overview-windows-forms.md)
- [ToolBar – ovládací prvek](toolbar-control-windows-forms.md)
