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
# <a name="how-to-define-an-icon-for-a-toolbar-button"></a><span data-ttu-id="c8de1-102">Postupy: Definování ikony pro tlačítko ToolBar</span><span class="sxs-lookup"><span data-stu-id="c8de1-102">How to: Define an Icon for a ToolBar Button</span></span>
> [!NOTE]
> <span data-ttu-id="c8de1-103">Ovládací <xref:System.Windows.Forms.ToolStrip> prvek nahradí a přidá <xref:System.Windows.Forms.ToolBar> funkce ovládacího prvku; <xref:System.Windows.Forms.ToolBar> ovládací prvek je však zachován a to jak pro zpětnou kompatibilitu, tak pro budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="c8de1-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="c8de1-104"><xref:System.Windows.Forms.ToolBar>tlačítka jsou schopna zobrazit ikony v nich pro snadnou identifikaci uživateli.</span><span class="sxs-lookup"><span data-stu-id="c8de1-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="c8de1-105">Toho je dosaženo přidáním obrazů do [komponenty ImageList](imagelist-component-windows-forms.md) Component <xref:System.Windows.Forms.ImageList> a <xref:System.Windows.Forms.ToolBar> následným přidružením komponenty k ovládacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="c8de1-105">This is achieved through adding images to the [ImageList Component](imagelist-component-windows-forms.md) component and then associating the <xref:System.Windows.Forms.ImageList> component with the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
### <a name="to-set-an-icon-for-a-toolbar-button-programmatically"></a><span data-ttu-id="c8de1-106">Nastavení ikony tlačítka panelu nástrojů programově</span><span class="sxs-lookup"><span data-stu-id="c8de1-106">To set an icon for a toolbar button programmatically</span></span>  
  
1. <span data-ttu-id="c8de1-107">V postupu vytvořte instanci <xref:System.Windows.Forms.ImageList> součásti a ovládacího <xref:System.Windows.Forms.ToolBar> prvku.</span><span class="sxs-lookup"><span data-stu-id="c8de1-107">In a procedure, instantiate an <xref:System.Windows.Forms.ImageList> component and a <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
2. <span data-ttu-id="c8de1-108">Stejným postupem přiřaďte <xref:System.Windows.Forms.ImageList> komponentě obrázek.</span><span class="sxs-lookup"><span data-stu-id="c8de1-108">In the same procedure, assign an image to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
3. <span data-ttu-id="c8de1-109">Stejným postupem přiřaďte <xref:System.Windows.Forms.ImageList> <xref:System.Windows.Forms.ToolBar> ovládací prvek <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> ovládacímu prvku a přiřaďte vlastnost jednotlivých tlačítek panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="c8de1-109">In the same procedure, assign the <xref:System.Windows.Forms.ImageList> control to the <xref:System.Windows.Forms.ToolBar> control and assign the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of the individual toolbar buttons.</span></span>  
  
     <span data-ttu-id="c8de1-110">V následujícím příkladu kódu je nastavená cesta pro umístění obrázku složka **Dokumenty.**</span><span class="sxs-lookup"><span data-stu-id="c8de1-110">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="c8de1-111">To je provedeno, protože můžete předpokládat, že většina počítačů s operačním systémem Windows bude obsahovat tento adresář.</span><span class="sxs-lookup"><span data-stu-id="c8de1-111">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="c8de1-112">To také umožňuje uživatelům s minimálními úrovněmi přístupu k systému bezpečně spustit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c8de1-112">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="c8de1-113">Následující příklad předpokládá formulář s <xref:System.Windows.Forms.PictureBox> již přidaným ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="c8de1-113">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
     <span data-ttu-id="c8de1-114">V návaznosti na výše uvedené kroky byste měli napsat kód podobný tomu, který je zobrazen níže.</span><span class="sxs-lookup"><span data-stu-id="c8de1-114">Following the steps above, you should have written code similar to that displayed below.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c8de1-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="c8de1-115">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="c8de1-116">Postupy: Spouštění událostí nabídky pro tlačítka panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="c8de1-116">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [<span data-ttu-id="c8de1-117">ToolBar – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="c8de1-117">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
- [<span data-ttu-id="c8de1-118">Komponenta ImageList</span><span class="sxs-lookup"><span data-stu-id="c8de1-118">ImageList Component</span></span>](imagelist-component-windows-forms.md)
