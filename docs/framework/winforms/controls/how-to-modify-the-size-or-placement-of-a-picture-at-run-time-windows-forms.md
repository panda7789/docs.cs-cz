---
title: 'Postupy: Změna velikosti či umístění obrázku za běhu (Windows Forms)'
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
ms.openlocfilehash: d0a86d7fe53dba3da6bd63587561f82877bc2f06
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328332"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a><span data-ttu-id="53cdb-102">Postupy: Změna velikosti či umístění obrázku za běhu (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="53cdb-102">How to: Modify the Size or Placement of a Picture at Run Time (Windows Forms)</span></span>
<span data-ttu-id="53cdb-103">Pokud používáte Windows Forms <xref:System.Windows.Forms.PictureBox> ovládací prvek ve formuláři, můžete nastavit <xref:System.Windows.Forms.PictureBox.SizeMode%2A> vlastnost ji:</span><span class="sxs-lookup"><span data-stu-id="53cdb-103">If you use the Windows Forms <xref:System.Windows.Forms.PictureBox> control on a form, you can set the <xref:System.Windows.Forms.PictureBox.SizeMode%2A> property on it to:</span></span>  
  
-   <span data-ttu-id="53cdb-104">Zarovnání obrázku levý horní roh s levého horního rohu ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="53cdb-104">Align the picture's upper left corner with the control's upper left corner</span></span>  
  
-   <span data-ttu-id="53cdb-105">System Center na obrázku v ovládacím prvku</span><span class="sxs-lookup"><span data-stu-id="53cdb-105">Center the picture within the control</span></span>  
  
-   <span data-ttu-id="53cdb-106">Upravte velikost ovládacího prvku obrázek, který se zobrazí podle</span><span class="sxs-lookup"><span data-stu-id="53cdb-106">Adjust the size of the control to fit the picture it displays</span></span>  
  
-   <span data-ttu-id="53cdb-107">Roztáhnout obrázek se zobrazí podle ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="53cdb-107">Stretch any picture it displays to fit the control</span></span>  
  
 <span data-ttu-id="53cdb-108">Roztažení obrázku (zejména jedna ve formát rastrového obrázku) může způsobit ztrátu v kvality obrázku.</span><span class="sxs-lookup"><span data-stu-id="53cdb-108">Stretching a picture (especially one in bitmap format) can produce a loss in image quality.</span></span> <span data-ttu-id="53cdb-109">Metasoubory, což jsou seznamy grafiky pokyny pro vykreslování obrázků za běhu, se lépe hodí pro roztažení než rastrové obrázky mají.</span><span class="sxs-lookup"><span data-stu-id="53cdb-109">Metafiles, which are lists of graphics instructions for drawing images at run time, are better suited for stretching than bitmaps are.</span></span>  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a><span data-ttu-id="53cdb-110">Chcete-li nastavit vlastnosti SizeMode za běhu</span><span class="sxs-lookup"><span data-stu-id="53cdb-110">To set the SizeMode property at run time</span></span>  
  
1. <span data-ttu-id="53cdb-111">Nastavte <xref:System.Windows.Forms.PictureBox.SizeMode%2A> k <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (výchozí), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, nebo <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span><span class="sxs-lookup"><span data-stu-id="53cdb-111">Set <xref:System.Windows.Forms.PictureBox.SizeMode%2A> to <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (the default), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, or <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span></span> <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> <span data-ttu-id="53cdb-112">znamená, že v levém horním rohu ovládacího prvku; je umístěn na obrázku Pokud na obrázku je větší než ovládací prvek, jeho dolní a pravé hrany se oříznou.</span><span class="sxs-lookup"><span data-stu-id="53cdb-112">means that the image is placed in the control's upper-left corner; if the image is larger than the control, its lower and right edges are clipped.</span></span> <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> <span data-ttu-id="53cdb-113">znamená to, že na obrázku je vycentrován ovládacího prvku; Pokud na obrázku je větší než ovládací prvek, na obrázku vnějšími hranami se oříznou.</span><span class="sxs-lookup"><span data-stu-id="53cdb-113">means that the image is centered within the control; if the image is larger than the control, the picture's outside edges are clipped.</span></span> <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> <span data-ttu-id="53cdb-114">znamená to, že velikost ovládacího prvku je nastavena velikost obrázku.</span><span class="sxs-lookup"><span data-stu-id="53cdb-114">means that the size of the control is adjusted to the size of the image.</span></span> <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> <span data-ttu-id="53cdb-115">je naopak a znamená, že se upraví velikost obrázku velikosti ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="53cdb-115">is the reverse, and means that the size of the image is adjusted to the size of the control.</span></span>  
  
     <span data-ttu-id="53cdb-116">V následujícím příkladu je cesta pro umístění bitové kopie složky Dokumenty.</span><span class="sxs-lookup"><span data-stu-id="53cdb-116">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="53cdb-117">Je to, protože můžete předpokládat, že většina počítačů s operačním systémem Windows bude obsahovat tento adresář.</span><span class="sxs-lookup"><span data-stu-id="53cdb-117">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="53cdb-118">Také to umožňuje uživatelům s úrovní přístupu minimální systém bezpečně spouštět aplikace.</span><span class="sxs-lookup"><span data-stu-id="53cdb-118">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="53cdb-119">Následující příklad předpokládá formulář s <xref:System.Windows.Forms.PictureBox> ovládací prvek již přidán.</span><span class="sxs-lookup"><span data-stu-id="53cdb-119">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="53cdb-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53cdb-120">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="53cdb-121">Postupy: Načtení obrázku pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="53cdb-121">How to: Load a Picture Using the Designer</span></span>](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [<span data-ttu-id="53cdb-122">Přehled ovládacího prvku PictureBox</span><span class="sxs-lookup"><span data-stu-id="53cdb-122">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="53cdb-123">Postupy: Nastavení obrázků za běhu</span><span class="sxs-lookup"><span data-stu-id="53cdb-123">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="53cdb-124">Ovládací prvek PictureBox</span><span class="sxs-lookup"><span data-stu-id="53cdb-124">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
