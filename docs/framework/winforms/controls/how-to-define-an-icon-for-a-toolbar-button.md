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
# <a name="how-to-define-an-icon-for-a-toolbar-button"></a><span data-ttu-id="69730-102">Postupy: Definování ikony pro tlačítko ToolBar</span><span class="sxs-lookup"><span data-stu-id="69730-102">How to: Define an Icon for a ToolBar Button</span></span>
> [!NOTE]
> <span data-ttu-id="69730-103">Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.ToolBar> <xref:System.Windows.Forms.ToolBar> ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.ToolStrip></span><span class="sxs-lookup"><span data-stu-id="69730-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="69730-104"><xref:System.Windows.Forms.ToolBar>tlačítka jsou schopna zobrazit ikony, aby je uživatelé mohli snadno identifikovat.</span><span class="sxs-lookup"><span data-stu-id="69730-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="69730-105">Toho lze dosáhnout přidáním obrázků do komponenty [komponenty ImageList](imagelist-component-windows-forms.md) a následným přiřazením <xref:System.Windows.Forms.ImageList> komponenty <xref:System.Windows.Forms.ToolBar> k ovládacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="69730-105">This is achieved through adding images to the [ImageList Component](imagelist-component-windows-forms.md) component and then associating the <xref:System.Windows.Forms.ImageList> component with the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
### <a name="to-set-an-icon-for-a-toolbar-button-programmatically"></a><span data-ttu-id="69730-106">Nastavení ikony pro tlačítko panelu nástrojů prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="69730-106">To set an icon for a toolbar button programmatically</span></span>  
  
1. <span data-ttu-id="69730-107">V proceduře vytvořte instanci <xref:System.Windows.Forms.ImageList> komponenty <xref:System.Windows.Forms.ToolBar> a ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="69730-107">In a procedure, instantiate an <xref:System.Windows.Forms.ImageList> component and a <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
2. <span data-ttu-id="69730-108">Ve stejném postupu přiřaďte k <xref:System.Windows.Forms.ImageList> komponentě obrázek.</span><span class="sxs-lookup"><span data-stu-id="69730-108">In the same procedure, assign an image to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
3. <span data-ttu-id="69730-109">Ve stejném postupu přiřaďte <xref:System.Windows.Forms.ImageList> ovládací <xref:System.Windows.Forms.ToolBar> prvek ovládacímu prvku a přiřaďte <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> vlastnost jednotlivých tlačítek panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="69730-109">In the same procedure, assign the <xref:System.Windows.Forms.ImageList> control to the <xref:System.Windows.Forms.ToolBar> control and assign the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of the individual toolbar buttons.</span></span>  
  
     <span data-ttu-id="69730-110">V následujícím příkladu kódu je cesta nastavená pro umístění obrázku složka **dokumenty** .</span><span class="sxs-lookup"><span data-stu-id="69730-110">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="69730-111">To se provádí, protože můžete předpokládat, že většina počítačů, na kterých běží operační systém Windows, bude obsahovat tento adresář.</span><span class="sxs-lookup"><span data-stu-id="69730-111">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="69730-112">To také umožňuje uživatelům s minimálními úrovněmi přístupu k systému bezpečně spustit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="69730-112">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="69730-113">Následující příklad předpokládá, že formulář s <xref:System.Windows.Forms.PictureBox> ovládacím prvkem již byl přidán.</span><span class="sxs-lookup"><span data-stu-id="69730-113">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
     <span data-ttu-id="69730-114">Podle výše uvedených kroků byste měli mít napsaný kód podobný tomu, který je zobrazený níže.</span><span class="sxs-lookup"><span data-stu-id="69730-114">Following the steps above, you should have written code similar to that displayed below.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="69730-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69730-115">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="69730-116">Postupy: Aktivace událostí nabídky pro tlačítka panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="69730-116">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [<span data-ttu-id="69730-117">Ovládací prvek ToolBar</span><span class="sxs-lookup"><span data-stu-id="69730-117">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
- [<span data-ttu-id="69730-118">Komponenta ImageList</span><span class="sxs-lookup"><span data-stu-id="69730-118">ImageList Component</span></span>](imagelist-component-windows-forms.md)
