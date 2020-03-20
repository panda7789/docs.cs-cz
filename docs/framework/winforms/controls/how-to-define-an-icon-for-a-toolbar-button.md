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
ms.openlocfilehash: 84c67c7d2584390ba3e48cb83820c65c6bb45d1f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182209"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button"></a>Postupy: Definování ikony pro tlačítko ToolBar
> [!NOTE]
> Ovládací <xref:System.Windows.Forms.ToolStrip> prvek nahradí a přidá <xref:System.Windows.Forms.ToolBar> funkce ovládacího prvku; <xref:System.Windows.Forms.ToolBar> ovládací prvek je však zachován a to jak pro zpětnou kompatibilitu, tak pro budoucí použití, pokud se rozhodnete.  
  
 <xref:System.Windows.Forms.ToolBar>tlačítka jsou schopna zobrazit ikony v nich pro snadnou identifikaci uživateli. Toho je dosaženo přidáním obrazů do [komponenty ImageList](imagelist-component-windows-forms.md) Component <xref:System.Windows.Forms.ImageList> a <xref:System.Windows.Forms.ToolBar> následným přidružením komponenty k ovládacímu prvku.  
  
### <a name="to-set-an-icon-for-a-toolbar-button-programmatically"></a>Nastavení ikony tlačítka panelu nástrojů programově  
  
1. V postupu vytvořte instanci <xref:System.Windows.Forms.ImageList> součásti a ovládacího <xref:System.Windows.Forms.ToolBar> prvku.  
  
2. Stejným postupem přiřaďte <xref:System.Windows.Forms.ImageList> komponentě obrázek.  
  
3. Stejným postupem přiřaďte <xref:System.Windows.Forms.ImageList> <xref:System.Windows.Forms.ToolBar> ovládací prvek <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> ovládacímu prvku a přiřaďte vlastnost jednotlivých tlačítek panelu nástrojů.  
  
     V následujícím příkladu kódu je nastavená cesta pro umístění obrázku složka **Dokumenty.** To je provedeno, protože můžete předpokládat, že většina počítačů s operačním systémem Windows bude obsahovat tento adresář. To také umožňuje uživatelům s minimálními úrovněmi přístupu k systému bezpečně spustit aplikaci. Následující příklad předpokládá formulář s <xref:System.Windows.Forms.PictureBox> již přidaným ovládacím prvkem.  
  
     V návaznosti na výše uvedené kroky byste měli napsat kód podobný tomu, který je zobrazen níže.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ToolBar>
- [Postupy: Spouštění událostí nabídky pro tlačítka panelu nástrojů](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [ToolBar – ovládací prvek](toolbar-control-windows-forms.md)
- [Komponenta ImageList](imagelist-component-windows-forms.md)
