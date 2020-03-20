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
ms.openlocfilehash: fea813d7b9fe585e35b729b8b64e3a5f414ef76d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141963"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a><span data-ttu-id="deeae-102">Postupy: Změna velikosti či umístění obrázku za běhu (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="deeae-102">How to: Modify the Size or Placement of a Picture at Run Time (Windows Forms)</span></span>
<span data-ttu-id="deeae-103">Pokud ve formuláři <xref:System.Windows.Forms.PictureBox> používáte ovládací prvek Windows <xref:System.Windows.Forms.PictureBox.SizeMode%2A> Forms, můžete vlastnost v něm nastavit tak, aby:</span><span class="sxs-lookup"><span data-stu-id="deeae-103">If you use the Windows Forms <xref:System.Windows.Forms.PictureBox> control on a form, you can set the <xref:System.Windows.Forms.PictureBox.SizeMode%2A> property on it to:</span></span>  
  
- <span data-ttu-id="deeae-104">Zarovnání levého horního rohu obrázku s levým horním rohem ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="deeae-104">Align the picture's upper left corner with the control's upper left corner</span></span>  
  
- <span data-ttu-id="deeae-105">Vystředit obrázek v ovládacím prvku</span><span class="sxs-lookup"><span data-stu-id="deeae-105">Center the picture within the control</span></span>  
  
- <span data-ttu-id="deeae-106">Upravte velikost ovládacího prvku tak, aby odpovídal zobrazený obrázek</span><span class="sxs-lookup"><span data-stu-id="deeae-106">Adjust the size of the control to fit the picture it displays</span></span>  
  
- <span data-ttu-id="deeae-107">Roztažení libovolného obrázku, který se zobrazí, aby se vešel do ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="deeae-107">Stretch any picture it displays to fit the control</span></span>  
  
 <span data-ttu-id="deeae-108">Roztažení obrázku (zejména v bitmapovém formátu) může způsobit ztrátu kvality obrazu.</span><span class="sxs-lookup"><span data-stu-id="deeae-108">Stretching a picture (especially one in bitmap format) can produce a loss in image quality.</span></span> <span data-ttu-id="deeae-109">Metasoubory, které jsou seznamy grafických pokynů pro kreslení obrázků za běhu, jsou vhodnější pro roztahování než bitmapy.</span><span class="sxs-lookup"><span data-stu-id="deeae-109">Metafiles, which are lists of graphics instructions for drawing images at run time, are better suited for stretching than bitmaps are.</span></span>  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a><span data-ttu-id="deeae-110">Nastavení vlastnosti SizeMode v době běhu</span><span class="sxs-lookup"><span data-stu-id="deeae-110">To set the SizeMode property at run time</span></span>  
  
1. <span data-ttu-id="deeae-111"><xref:System.Windows.Forms.PictureBox.SizeMode%2A> Nastaveno <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (výchozí), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>nebo .</span><span class="sxs-lookup"><span data-stu-id="deeae-111">Set <xref:System.Windows.Forms.PictureBox.SizeMode%2A> to <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (the default), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, or <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span></span> <span data-ttu-id="deeae-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal>znamená, že obraz je umístěn v levém horním rohu ovládacího prvku; pokud je obraz větší než ovládací prvek, jeho dolní a pravé okraje se oříznou.</span><span class="sxs-lookup"><span data-stu-id="deeae-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal> means that the image is placed in the control's upper-left corner; if the image is larger than the control, its lower and right edges are clipped.</span></span> <span data-ttu-id="deeae-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>znamená, že obraz je vystředěn v ovládacím prvku; pokud je obraz větší než ovládací prvek, vnější okraje obrázku se oříznou.</span><span class="sxs-lookup"><span data-stu-id="deeae-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> means that the image is centered within the control; if the image is larger than the control, the picture's outside edges are clipped.</span></span> <span data-ttu-id="deeae-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>znamená, že velikost ovládacího prvku je přizpůsobena velikosti obrázku.</span><span class="sxs-lookup"><span data-stu-id="deeae-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> means that the size of the control is adjusted to the size of the image.</span></span> <span data-ttu-id="deeae-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>je naopak a znamená, že velikost obrázku je upravena na velikost ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="deeae-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> is the reverse, and means that the size of the image is adjusted to the size of the control.</span></span>  
  
     <span data-ttu-id="deeae-116">V níže uvedeném příkladu je nastavenou cestou pro umístění obrázku složka Dokumenty.</span><span class="sxs-lookup"><span data-stu-id="deeae-116">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="deeae-117">To je provedeno, protože můžete předpokládat, že většina počítačů s operačním systémem Windows bude obsahovat tento adresář.</span><span class="sxs-lookup"><span data-stu-id="deeae-117">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="deeae-118">To také umožňuje uživatelům s minimálními úrovněmi přístupu k systému bezpečně spustit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="deeae-118">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="deeae-119">Následující příklad předpokládá formulář s <xref:System.Windows.Forms.PictureBox> již přidaným ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="deeae-119">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="deeae-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="deeae-120">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="deeae-121">Postupy: Načtení obrázku pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="deeae-121">How to: Load a Picture Using the Designer</span></span>](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [<span data-ttu-id="deeae-122">PictureBox – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="deeae-122">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="deeae-123">Postupy: Nastavení obrázků za běhu</span><span class="sxs-lookup"><span data-stu-id="deeae-123">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="deeae-124">PictureBox – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="deeae-124">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
