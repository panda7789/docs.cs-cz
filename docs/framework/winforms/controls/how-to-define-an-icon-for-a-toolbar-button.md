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
ms.openlocfilehash: 0d4a17528ca3eb81f93419491766e370be551b1e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153124"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button"></a><span data-ttu-id="811d6-102">Postupy: Definování ikony pro tlačítko ToolBar</span><span class="sxs-lookup"><span data-stu-id="811d6-102">How to: Define an Icon for a ToolBar Button</span></span>
> [!NOTE]
>  <span data-ttu-id="811d6-103"><xref:System.Windows.Forms.ToolStrip> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.ToolBar> řízení; však <xref:System.Windows.Forms.ToolBar> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="811d6-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <xref:System.Windows.Forms.ToolBar> <span data-ttu-id="811d6-104">tlačítka budou moct zobrazit ikony v nich pro snadnou identifikaci uživatelů.</span><span class="sxs-lookup"><span data-stu-id="811d6-104">buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="811d6-105">Toho můžete dosáhnout přidávání obrázků [ImageList – komponenta](imagelist-component-windows-forms.md) komponentu a potom přidružení <xref:System.Windows.Forms.ImageList> komponentu s <xref:System.Windows.Forms.ToolBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="811d6-105">This is achieved through adding images to the [ImageList Component](imagelist-component-windows-forms.md) component and then associating the <xref:System.Windows.Forms.ImageList> component with the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
### <a name="to-set-an-icon-for-a-toolbar-button-programmatically"></a><span data-ttu-id="811d6-106">Chcete-li nastavit ikonu pro tlačítko toolbar prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="811d6-106">To set an icon for a toolbar button programmatically</span></span>  
  
1.  <span data-ttu-id="811d6-107">V postupu, vytvořit instanci <xref:System.Windows.Forms.ImageList> komponenty a <xref:System.Windows.Forms.ToolBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="811d6-107">In a procedure, instantiate an <xref:System.Windows.Forms.ImageList> component and a <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
2.  <span data-ttu-id="811d6-108">Ve stejné proceduře přiřadit obrázku, který má <xref:System.Windows.Forms.ImageList> komponenty.</span><span class="sxs-lookup"><span data-stu-id="811d6-108">In the same procedure, assign an image to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
3.  <span data-ttu-id="811d6-109">Ve stejné proceduře přiřadit <xref:System.Windows.Forms.ImageList> ovládací prvek <xref:System.Windows.Forms.ToolBar> řídit a přiřadit <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> vlastnosti tlačítka panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="811d6-109">In the same procedure, assign the <xref:System.Windows.Forms.ImageList> control to the <xref:System.Windows.Forms.ToolBar> control and assign the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of the individual toolbar buttons.</span></span>  
  
     <span data-ttu-id="811d6-110">V následujícím příkladu kódu nastavena cesta pro umístění image je **dokumenty** složky.</span><span class="sxs-lookup"><span data-stu-id="811d6-110">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="811d6-111">Je to, protože můžete předpokládat, že většina počítačů s operačním systémem Windows bude obsahovat tento adresář.</span><span class="sxs-lookup"><span data-stu-id="811d6-111">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="811d6-112">Také to umožňuje uživatelům s úrovní přístupu minimální systém bezpečně spouštět aplikace.</span><span class="sxs-lookup"><span data-stu-id="811d6-112">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="811d6-113">Následující příklad předpokládá formulář s <xref:System.Windows.Forms.PictureBox> ovládací prvek již přidán.</span><span class="sxs-lookup"><span data-stu-id="811d6-113">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
     <span data-ttu-id="811d6-114">Po výše uvedených kroků by měl jste napsali kód, který se zobrazí pod podobný.</span><span class="sxs-lookup"><span data-stu-id="811d6-114">Following the steps above, you should have written code similar to that displayed below.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="811d6-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="811d6-115">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="811d6-116">Postupy: Spouštění událostí nabídky pro tlačítka ToolBar</span><span class="sxs-lookup"><span data-stu-id="811d6-116">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [<span data-ttu-id="811d6-117">ToolBar – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="811d6-117">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
- [<span data-ttu-id="811d6-118">Komponenta ImageList</span><span class="sxs-lookup"><span data-stu-id="811d6-118">ImageList Component</span></span>](imagelist-component-windows-forms.md)
