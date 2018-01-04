---
title: "Postupy: Přidání tlačítek do ovládacího prvku ToolBar"
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
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: 78a58a8d-1041-4e38-9219-4096fa6a5c5c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c0db83277be1dcecc2463c45481671c2ee1ee737
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-buttons-to-a-toolbar-control"></a>Postupy: Přidání tlačítek do ovládacího prvku ToolBar
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.ToolBar> řízení; však <xref:System.Windows.Forms.ToolBar> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte.  
  
 Nedílnou součástí <xref:System.Windows.Forms.ToolBar> ovládací prvek je přidejte do ní tlačítek. To slouží k poskytování snadného přístupu k příkazům nabídky nebo Alternativně můžete umístit v jiné oblasti uživatelského rozhraní pro vaší aplikace, která zveřejňuje příkazy pro vaše uživatele, kteří nejsou k dispozici ve struktuře nabídky.  
  
 Následující příklady předpokládají, že <xref:System.Windows.Forms.ToolBar> ovládací prvek byl přidán do formuláře systému Windows (`Form1`).  
  
### <a name="to-add-buttons-programmatically"></a>Přidání tlačítka prostřednictvím kódu programu  
  
1.  V postupu, vytvořit jejich přidáním do tlačítka panelu nástrojů <xref:System.Windows.Forms.ToolBar.Buttons%2A?displayProperty=nameWithType> kolekce.  
  
2.  Zadejte nastavení pro jednotlivé tlačítko předáním indexu na tlačítko prostřednictvím <xref:System.Windows.Forms.ToolBar.Buttons%2A> vlastnost.  
  
     Následující příklad předpokládá formulář s <xref:System.Windows.Forms.ToolBar> ovládací prvek již přidán.  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.ToolBar.Buttons%2A?displayProperty=nameWithType> Kolekce je soubor od nuly, kód by měl pokračovat odpovídajícím způsobem.  
  
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
 <xref:System.Windows.Forms.ToolBar>  
 [Postupy: Definování ikony pro tlačítko ToolBar](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 [Postupy: Spouštění událostí nabídky pro tlačítka panelu nástrojů](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [Přehled ovládacího prvku ToolBar](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)  
 [Ovládací prvek ToolBar](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)
