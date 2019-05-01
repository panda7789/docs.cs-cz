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
ms.openlocfilehash: 2c1c3d8529662c1e1f1a3d28e3853d31f5d940ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054273"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button"></a>Postupy: Definování ikony pro tlačítko ToolBar
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.ToolBar> řízení; však <xref:System.Windows.Forms.ToolBar> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.  
  
 <xref:System.Windows.Forms.ToolBar> tlačítka budou moct zobrazit ikony v nich pro snadnou identifikaci uživatelů. Toho můžete dosáhnout přidávání obrázků [ImageList – komponenta](imagelist-component-windows-forms.md) komponentu a potom přidružení <xref:System.Windows.Forms.ImageList> komponentu s <xref:System.Windows.Forms.ToolBar> ovládacího prvku.  
  
### <a name="to-set-an-icon-for-a-toolbar-button-programmatically"></a>Chcete-li nastavit ikonu pro tlačítko toolbar prostřednictvím kódu programu  
  
1. V postupu, vytvořit instanci <xref:System.Windows.Forms.ImageList> komponenty a <xref:System.Windows.Forms.ToolBar> ovládacího prvku.  
  
2. Ve stejné proceduře přiřadit obrázku, který má <xref:System.Windows.Forms.ImageList> komponenty.  
  
3. Ve stejné proceduře přiřadit <xref:System.Windows.Forms.ImageList> ovládací prvek <xref:System.Windows.Forms.ToolBar> řídit a přiřadit <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> vlastnosti tlačítka panelu nástrojů.  
  
     V následujícím příkladu kódu nastavena cesta pro umístění image je **dokumenty** složky. Je to, protože můžete předpokládat, že většina počítačů s operačním systémem Windows bude obsahovat tento adresář. Také to umožňuje uživatelům s úrovní přístupu minimální systém bezpečně spouštět aplikace. Následující příklad předpokládá formulář s <xref:System.Windows.Forms.PictureBox> ovládací prvek již přidán.  
  
     Po výše uvedených kroků by měl jste napsali kód, který se zobrazí pod podobný.  
  
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
- [Postupy: Aktivační události nabídky pro tlačítka panelu nástrojů](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [Ovládací prvek ToolBar](toolbar-control-windows-forms.md)
- [Komponenta ImageList](imagelist-component-windows-forms.md)
