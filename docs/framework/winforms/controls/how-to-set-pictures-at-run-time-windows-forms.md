---
title: 'Postupy: Nastavení obrázků za běhu (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- pictures [Windows Forms], setting display
- examples [Windows Forms], PictureBox control
- bitmaps [Windows Forms], displaying in PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding images
- images [Windows Forms], adding with PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 18ca41d0-68a5-4660-985e-a6c1fbc01d76
ms.openlocfilehash: c7a65bcc65710324a4457c17dd728b4771550c06
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694071"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a><span data-ttu-id="15d3f-102">Postupy: Nastavení obrázků za běhu (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="15d3f-102">How to: Set Pictures at Run Time (Windows Forms)</span></span>
<span data-ttu-id="15d3f-103">Můžete programově nastavení obrázku zobrazovaného rozhraním Windows Forms <xref:System.Windows.Forms.PictureBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="15d3f-103">You can programmatically set the image displayed by a Windows Forms <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-set-a-picture-programmatically"></a><span data-ttu-id="15d3f-104">Chcete-li nastavit obrázek prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="15d3f-104">To set a picture programmatically</span></span>  
  
-   <span data-ttu-id="15d3f-105">Nastavte <xref:System.Windows.Forms.PictureBox.Image%2A> pomocí vlastnosti <xref:System.Drawing.Image.FromFile%2A> metodu <xref:System.Drawing.Image> třídy.</span><span class="sxs-lookup"><span data-stu-id="15d3f-105">Set the <xref:System.Windows.Forms.PictureBox.Image%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image> class.</span></span>  
  
     <span data-ttu-id="15d3f-106">V následujícím příkladu je cesta pro umístění bitové kopie složky Dokumenty.</span><span class="sxs-lookup"><span data-stu-id="15d3f-106">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="15d3f-107">Je to, protože můžete předpokládat, že většina počítačů s operačním systémem Windows bude obsahovat tento adresář.</span><span class="sxs-lookup"><span data-stu-id="15d3f-107">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="15d3f-108">Také to umožňuje uživatelům s úrovní přístupu minimální systém bezpečně spouštět aplikace.</span><span class="sxs-lookup"><span data-stu-id="15d3f-108">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="15d3f-109">Následující příklad předpokládá formulář s <xref:System.Windows.Forms.PictureBox> ovládací prvek již přidán.</span><span class="sxs-lookup"><span data-stu-id="15d3f-109">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
    ```vb  
    Private Sub LoadNewPict()  
       ' You should replace the bold image   
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadNewPict(){  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    }  
    ```  
  
    ```cpp  
    private:  
       void LoadNewPict()  
       {  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
### <a name="to-clear-a-graphic"></a><span data-ttu-id="15d3f-110">Vymazat obrázek</span><span class="sxs-lookup"><span data-stu-id="15d3f-110">To clear a graphic</span></span>  
  
-   <span data-ttu-id="15d3f-111">Nejprve uvolnění paměti používané bitovou kopii a zrušte na obrázku.</span><span class="sxs-lookup"><span data-stu-id="15d3f-111">First, release the memory being used by the image, and then clear the graphic.</span></span> <span data-ttu-id="15d3f-112">Uvolňování paměti uvolní se paměť později Pokud Správa paměti stane problém.</span><span class="sxs-lookup"><span data-stu-id="15d3f-112">Garbage collection will free up the memory later if memory management becomes a problem.</span></span>  
  
    ```vb  
    If Not (PictureBox1.Image Is Nothing) Then  
       PictureBox1.Image.Dispose()  
       PictureBox1.Image = Nothing  
    End If  
    ```  
  
    ```csharp  
    if (pictureBox1.Image != null)   
    {  
       pictureBox1.Image.Dispose();  
       pictureBox1.Image = null;  
    }  
    ```  
  
    ```cpp  
    if (pictureBox1->Image != nullptr)  
    {  
       pictureBox1->Image->Dispose();  
       pictureBox1->Image = nullptr;  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="15d3f-113">Další informace o důvod, proč byste měli použít <xref:System.Drawing.Image.Dispose%2A> najdete v článku metoda tímto způsobem [Cleaning Up Unmanaged Resources](../../../../docs/standard/garbage-collection/unmanaged.md).</span><span class="sxs-lookup"><span data-stu-id="15d3f-113">For more information on why you should use the <xref:System.Drawing.Image.Dispose%2A> method in this way, see [Cleaning Up Unmanaged Resources](../../../../docs/standard/garbage-collection/unmanaged.md).</span></span>  
  
     <span data-ttu-id="15d3f-114">Tento kód se vymažou bitovou kopii, i v případě, že grafický objekt byl načten do ovládacího prvku v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="15d3f-114">This code will clear the image even if a graphic was loaded into the control at design time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15d3f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15d3f-115">See also</span></span>
- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [<span data-ttu-id="15d3f-116">Přehled ovládacího prvku PictureBox</span><span class="sxs-lookup"><span data-stu-id="15d3f-116">PictureBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="15d3f-117">Postupy: Načtení obrázku pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="15d3f-117">How to: Load a Picture Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)
- [<span data-ttu-id="15d3f-118">Postupy: Změna velikosti či umístění obrázku za běhu</span><span class="sxs-lookup"><span data-stu-id="15d3f-118">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="15d3f-119">Ovládací prvek PictureBox</span><span class="sxs-lookup"><span data-stu-id="15d3f-119">PictureBox Control</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
