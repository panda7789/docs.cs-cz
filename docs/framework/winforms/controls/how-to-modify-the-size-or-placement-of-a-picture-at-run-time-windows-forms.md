---
title: "Postupy: Změna velikosti či umístění obrázku za běhu (Windows Forms)"
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
- images [Windows Forms], controlling placement in PictureBox control [Windows Forms]
- examples [Windows Forms], PictureBox control
- PictureBox control [Windows Forms], picture size and alignment
- pictures [Windows Forms], controlling placement in PictureBox control [Windows Forms]
ms.assetid: d0b332a3-fae2-4891-957c-dc3e17743326
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: df67871b0b133297a6f53ff9e4a42c7630a5f56d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a><span data-ttu-id="d1c89-102">Postupy: Změna velikosti či umístění obrázku za běhu (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d1c89-102">How to: Modify the Size or Placement of a Picture at Run Time (Windows Forms)</span></span>
<span data-ttu-id="d1c89-103">Pokud používáte Windows Forms <xref:System.Windows.Forms.PictureBox> ovládací prvek na formuláři, můžete nastavit <xref:System.Windows.Forms.PictureBox.SizeMode%2A> vlastnost na jeho:</span><span class="sxs-lookup"><span data-stu-id="d1c89-103">If you use the Windows Forms <xref:System.Windows.Forms.PictureBox> control on a form, you can set the <xref:System.Windows.Forms.PictureBox.SizeMode%2A> property on it to:</span></span>  
  
-   <span data-ttu-id="d1c89-104">Zarovnat na obrázku levém horním rohu s levém horním rohu ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="d1c89-104">Align the picture's upper left corner with the control's upper left corner</span></span>  
  
-   <span data-ttu-id="d1c89-105">Center obrázků v ovládacím prvku</span><span class="sxs-lookup"><span data-stu-id="d1c89-105">Center the picture within the control</span></span>  
  
-   <span data-ttu-id="d1c89-106">Upravit velikost přizpůsobit obrázek, který se zobrazí ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="d1c89-106">Adjust the size of the control to fit the picture it displays</span></span>  
  
-   <span data-ttu-id="d1c89-107">Funkce Stretch jakýkoli obrázek zobrazuje podle ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="d1c89-107">Stretch any picture it displays to fit the control</span></span>  
  
 <span data-ttu-id="d1c89-108">Roztažení obrázku (zejména jeden ve formátu rastrového obrázku) může vytvářet ztráty bitové kopie kvality.</span><span class="sxs-lookup"><span data-stu-id="d1c89-108">Stretching a picture (especially one in bitmap format) can produce a loss in image quality.</span></span> <span data-ttu-id="d1c89-109">Metasoubory, které jsou seznamy grafiky pokyny pro vykreslování obrázků za běhu, se hodí pro roztažení než jsou.</span><span class="sxs-lookup"><span data-stu-id="d1c89-109">Metafiles, which are lists of graphics instructions for drawing images at run time, are better suited for stretching than bitmaps are.</span></span>  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a><span data-ttu-id="d1c89-110">Chcete-li nastavit vlastnost Režim velikosti za běhu</span><span class="sxs-lookup"><span data-stu-id="d1c89-110">To set the SizeMode property at run time</span></span>  
  
1.  <span data-ttu-id="d1c89-111">Nastavit <xref:System.Windows.Forms.PictureBox.SizeMode%2A> k <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (výchozí), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, nebo <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span><span class="sxs-lookup"><span data-stu-id="d1c89-111">Set <xref:System.Windows.Forms.PictureBox.SizeMode%2A> to <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (the default), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, or <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span></span> <span data-ttu-id="d1c89-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal>znamená, že obrázek je umístěn v levém horním rohu ovládacího prvku; Pokud bitovou kopii je větší než ovládacího prvku, jsou oříznut jeho dolní a pravé hrany.</span><span class="sxs-lookup"><span data-stu-id="d1c89-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal> means that the image is placed in the control's upper-left corner; if the image is larger than the control, its lower and right edges are clipped.</span></span> <span data-ttu-id="d1c89-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>znamená, že bitovou kopii je umístěn na střed ovládacího prvku; Pokud bitovou kopii je větší než ovládacího prvku, jsou oříznut na obrázku mimo okraje.</span><span class="sxs-lookup"><span data-stu-id="d1c89-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> means that the image is centered within the control; if the image is larger than the control, the picture's outside edges are clipped.</span></span> <span data-ttu-id="d1c89-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>znamená, že velikost ovládacího prvku je nastavena velikost bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="d1c89-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> means that the size of the control is adjusted to the size of the image.</span></span> <span data-ttu-id="d1c89-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>je naopak a znamená, že se upraví velikost obrázku velikosti ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d1c89-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> is the reverse, and means that the size of the image is adjusted to the size of the control.</span></span>  
  
     <span data-ttu-id="d1c89-116">V následujícím příkladu je cesta pro umístění bitové kopie nastavit složky Dokumenty.</span><span class="sxs-lookup"><span data-stu-id="d1c89-116">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="d1c89-117">Důvodem je, protože můžete předpokládat, že většina počítačů s operačním systémem Windows budou obsahovat tento adresář.</span><span class="sxs-lookup"><span data-stu-id="d1c89-117">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="d1c89-118">To také umožňuje uživatelům s minimální systém úrovně přístupu pro aplikaci bezpečně spustit.</span><span class="sxs-lookup"><span data-stu-id="d1c89-118">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="d1c89-119">Následující příklad předpokládá formulář s <xref:System.Windows.Forms.PictureBox> ovládací prvek již přidán.</span><span class="sxs-lookup"><span data-stu-id="d1c89-119">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
    ```vb  
    Private Sub StretchPic()  
       ' Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage  
       ' Load the picture into the control.  
       ' You should replace the bold image   
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void StretchPic(){  
       // Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage;  
       // Load the picture into the control.  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\Image.gif")  
    }  
    ```  
  
    ```cpp  
    private:  
       void StretchPic()  
       {  
          // Stretch the picture to fit the control.  
          pictureBox1->SizeMode = PictureBoxSizeMode::StretchImage;  
          // Load the picture into the control.  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d1c89-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1c89-120">See Also</span></span>  
 <xref:System.Windows.Forms.PictureBox>  
 [<span data-ttu-id="d1c89-121">Postupy: načtení obrázku pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="d1c89-121">How to: Load a Picture Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)  
 [<span data-ttu-id="d1c89-122">Přehled ovládacího prvku PictureBox</span><span class="sxs-lookup"><span data-stu-id="d1c89-122">PictureBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [<span data-ttu-id="d1c89-123">Postupy: nastavení obrázků za běhu</span><span class="sxs-lookup"><span data-stu-id="d1c89-123">How to: Set Pictures at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)  
 [<span data-ttu-id="d1c89-124">PictureBox – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="d1c89-124">PictureBox Control</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
