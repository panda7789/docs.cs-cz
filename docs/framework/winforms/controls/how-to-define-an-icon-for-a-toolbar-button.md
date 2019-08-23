---
title: 'Postupy: Definování ikony pro tlačítko ToolBar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- buttons [Windows Forms], icons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: 84db98b4-8566-49ce-b2c8-1fd66a5eb3a0
ms.openlocfilehash: 2b85f734a5f8b31531cfe48f87681d98304db09b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929633"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button"></a>Postupy: Definování ikony pro tlačítko ToolBar
> [!NOTE]
> Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.ToolBar> <xref:System.Windows.Forms.ToolBar> ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.ToolStrip>  
  
 <xref:System.Windows.Forms.ToolBar>tlačítka jsou schopna zobrazit ikony, aby je uživatelé mohli snadno identifikovat. Toho lze dosáhnout přidáním obrázků do komponenty [komponenty ImageList](imagelist-component-windows-forms.md) a následným přiřazením <xref:System.Windows.Forms.ImageList> komponenty <xref:System.Windows.Forms.ToolBar> k ovládacímu prvku.  
  
### <a name="to-set-an-icon-for-a-toolbar-button-programmatically"></a>Nastavení ikony pro tlačítko panelu nástrojů prostřednictvím kódu programu  
  
1. V proceduře vytvořte instanci <xref:System.Windows.Forms.ImageList> komponenty <xref:System.Windows.Forms.ToolBar> a ovládacího prvku.  
  
2. Ve stejném postupu přiřaďte k <xref:System.Windows.Forms.ImageList> komponentě obrázek.  
  
3. Ve stejném postupu přiřaďte <xref:System.Windows.Forms.ImageList> ovládací <xref:System.Windows.Forms.ToolBar> prvek ovládacímu prvku a přiřaďte <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> vlastnost jednotlivých tlačítek panelu nástrojů.  
  
     V následujícím příkladu kódu je cesta nastavená pro umístění obrázku složka **dokumenty** . To se provádí, protože můžete předpokládat, že většina počítačů, na kterých běží operační systém Windows, bude obsahovat tento adresář. To také umožňuje uživatelům s minimálními úrovněmi přístupu k systému bezpečně spustit aplikaci. Následující příklad předpokládá, že formulář s <xref:System.Windows.Forms.PictureBox> ovládacím prvkem již byl přidán.  
  
     Podle výše uvedených kroků byste měli mít napsaný kód podobný tomu, který je zobrazený níže.  
  
    ```vb  
    Public Sub InitializeMyToolBar()  
    ' Instantiate an ImageList component and a ToolBar control.  
       Dim ToolBar1 as New ToolBar  
       Dim ImageList1 as New ImageList  
    ' Assign an image to the ImageList component.  
    ' You should replace the bold image  
    ' in the sample below with an icon of your own choosing.  
       Dim myImage As System.Drawing.Image = _   
          Image.FromFile Image.FromFile _  
          (System.Environment.GetFolderPath _  
          (System.Environment.SpecialFolder.Personal) _  
          & "\Image.gif")  
       ImageList1.Images.Add(myImage)  
    ' Create a ToolBarButton.  
       Dim ToolBarButton1 As New ToolBarButton()  
    ' Add the ToolBarButton to the ToolBar.  
       ToolBar1.Buttons.Add(toolBarButton1)  
    ' Assign an ImageList to the ToolBar.  
       ToolBar1.ImageList = ImageList1  
    ' Assign the ImageIndex property of the ToolBarButton.  
       ToolBarButton1.ImageIndex = 0  
    End Sub  
    ```  
  
    ```csharp  
    public void InitializeMyToolBar()  
    {  
       // Instantiate an ImageList component and a ToolBar control.  
       ToolBar toolBar1 = new  ToolBar();   
       ImageList imageList1 = new ImageList();  
       // Assign an image to the ImageList component.  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       Image myImage = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
       imageList1.Images.Add(myImage);  
       // Create a ToolBarButton.  
       ToolBarButton toolBarButton1 = new ToolBarButton();  
       // Add the ToolBarButton to the ToolBar.  
       toolBar1.Buttons.Add(toolBarButton1);  
       // Assign an ImageList to the ToolBar.  
       toolBar1.ImageList = imageList1;  
       // Assign ImageIndex property of the ToolBarButton.  
       toolBarButton1.ImageIndex = 0;  
    }  
    ```  
  
    ```cpp  
    public:  
       void InitializeMyToolBar()  
       {  
          // Instantiate an ImageList component and a ToolBar control.  
          ToolBar ^ toolBar1 = gcnew  ToolBar();   
          ImageList ^ imageList1 = gcnew ImageList();  
          // Assign an image to the ImageList component.  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          Image ^ myImage = Image::FromFile(String::Concat  
             (System::Environment::GetFolderPath  
             (System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
          imageList1->Images->Add(myImage);  
          // Create a ToolBarButton.  
          ToolBarButton ^ toolBarButton1 = gcnew ToolBarButton();  
          // Add the ToolBarButton to the ToolBar.  
          toolBar1->Buttons->Add(toolBarButton1);  
          // Assign an ImageList to the ToolBar.  
          toolBar1->ImageList = imageList1;  
          // Assign ImageIndex property of the ToolBarButton.  
          toolBarButton1->ImageIndex = 0;  
       }  
    ```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolBar>
- [Postupy: Aktivace událostí nabídky pro tlačítka panelu nástrojů](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [Ovládací prvek ToolBar](toolbar-control-windows-forms.md)
- [Komponenta ImageList](imagelist-component-windows-forms.md)
