---
title: 'Postupy: Změna velikosti či umístění obrázku za běhu'
ms.date: 03/30/2017
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
ms.openlocfilehash: 9bb094ce0b7945f23a2e9b8614e56c9492d5f832
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736033"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a><span data-ttu-id="9cf5e-102">Postupy: Změna velikosti či umístění obrázku za běhu (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="9cf5e-102">How to: Modify the Size or Placement of a Picture at Run Time (Windows Forms)</span></span>
<span data-ttu-id="9cf5e-103">Použijete-li ovládací prvek model Windows Forms <xref:System.Windows.Forms.PictureBox> na formuláři, můžete pro něj nastavit vlastnost <xref:System.Windows.Forms.PictureBox.SizeMode%2A> na:</span><span class="sxs-lookup"><span data-stu-id="9cf5e-103">If you use the Windows Forms <xref:System.Windows.Forms.PictureBox> control on a form, you can set the <xref:System.Windows.Forms.PictureBox.SizeMode%2A> property on it to:</span></span>  
  
- <span data-ttu-id="9cf5e-104">Zarovnat levý horní roh obrázku do levého horního rohu ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="9cf5e-104">Align the picture's upper left corner with the control's upper left corner</span></span>  
  
- <span data-ttu-id="9cf5e-105">Vycentrovat obrázek v ovládacím prvku</span><span class="sxs-lookup"><span data-stu-id="9cf5e-105">Center the picture within the control</span></span>  
  
- <span data-ttu-id="9cf5e-106">Upravte velikost ovládacího prvku tak, aby odpovídala obrázku, který se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="9cf5e-106">Adjust the size of the control to fit the picture it displays</span></span>  
  
- <span data-ttu-id="9cf5e-107">Roztáhnout libovolný obrázek, který se zobrazí, aby odpovídal ovládacímu prvku</span><span class="sxs-lookup"><span data-stu-id="9cf5e-107">Stretch any picture it displays to fit the control</span></span>  
  
 <span data-ttu-id="9cf5e-108">Roztažení obrázku (zejména ve formátu rastrového obrázku) může způsobit ztrátu kvality obrazu.</span><span class="sxs-lookup"><span data-stu-id="9cf5e-108">Stretching a picture (especially one in bitmap format) can produce a loss in image quality.</span></span> <span data-ttu-id="9cf5e-109">Metasoubory, které jsou seznamy instrukcí grafiky pro vykreslování obrázků za běhu, jsou vhodnější pro roztažení než rastry.</span><span class="sxs-lookup"><span data-stu-id="9cf5e-109">Metafiles, which are lists of graphics instructions for drawing images at run time, are better suited for stretching than bitmaps are.</span></span>  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a><span data-ttu-id="9cf5e-110">Nastavení vlastnosti SizeMode v době běhu</span><span class="sxs-lookup"><span data-stu-id="9cf5e-110">To set the SizeMode property at run time</span></span>  
  
1. <span data-ttu-id="9cf5e-111">Nastavte <xref:System.Windows.Forms.PictureBox.SizeMode%2A> na <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (výchozí), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>nebo <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span><span class="sxs-lookup"><span data-stu-id="9cf5e-111">Set <xref:System.Windows.Forms.PictureBox.SizeMode%2A> to <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (the default), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, or <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span></span> <span data-ttu-id="9cf5e-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal> znamená, že se obrázek umístí do levého horního rohu ovládacího prvku; je-li obrázek větší než ovládací prvek, jeho dolní a pravé hrany jsou oříznuty.</span><span class="sxs-lookup"><span data-stu-id="9cf5e-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal> means that the image is placed in the control's upper-left corner; if the image is larger than the control, its lower and right edges are clipped.</span></span> <span data-ttu-id="9cf5e-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> znamená, že obrázek je umístěn na střed v rámci ovládacího prvku. Pokud je obrázek větší než ovládací prvek, jsou oříznuty vnější okraje obrázku.</span><span class="sxs-lookup"><span data-stu-id="9cf5e-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> means that the image is centered within the control; if the image is larger than the control, the picture's outside edges are clipped.</span></span> <span data-ttu-id="9cf5e-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> znamená, že velikost ovládacího prvku se upraví na velikost obrázku.</span><span class="sxs-lookup"><span data-stu-id="9cf5e-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> means that the size of the control is adjusted to the size of the image.</span></span> <span data-ttu-id="9cf5e-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> je reverzní a to znamená, že velikost obrázku je upravena na velikost ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9cf5e-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> is the reverse, and means that the size of the image is adjusted to the size of the control.</span></span>  
  
     <span data-ttu-id="9cf5e-116">V následujícím příkladu je cesta nastavená pro umístění obrázku složkou Dokumenty.</span><span class="sxs-lookup"><span data-stu-id="9cf5e-116">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="9cf5e-117">To se provádí, protože můžete předpokládat, že většina počítačů, na kterých běží operační systém Windows, bude obsahovat tento adresář.</span><span class="sxs-lookup"><span data-stu-id="9cf5e-117">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="9cf5e-118">To také umožňuje uživatelům s minimálními úrovněmi přístupu k systému bezpečně spustit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9cf5e-118">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="9cf5e-119">Následující příklad předpokládá, že formulář s již přidaným ovládacím prvkem <xref:System.Windows.Forms.PictureBox>.</span><span class="sxs-lookup"><span data-stu-id="9cf5e-119">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9cf5e-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9cf5e-120">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="9cf5e-121">Postupy: Načtení obrázku pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="9cf5e-121">How to: Load a Picture Using the Designer</span></span>](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [<span data-ttu-id="9cf5e-122">Přehled ovládacího prvku PictureBox</span><span class="sxs-lookup"><span data-stu-id="9cf5e-122">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="9cf5e-123">Postupy: Nastavení obrázků za běhu</span><span class="sxs-lookup"><span data-stu-id="9cf5e-123">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="9cf5e-124">Ovládací prvek PictureBox</span><span class="sxs-lookup"><span data-stu-id="9cf5e-124">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
