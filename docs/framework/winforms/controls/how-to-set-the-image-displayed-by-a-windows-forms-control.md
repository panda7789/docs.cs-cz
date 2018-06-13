---
title: 'Postupy: Nastavení obrázku zobrazovaného ovládacím prvkem Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
ms.openlocfilehash: 4870f9e2acc48a90e1e2193d514926fedee05f61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533738"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a><span data-ttu-id="a41dd-102">Postupy: Nastavení obrázku zobrazovaného ovládacím prvkem Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a41dd-102">How to: Set the Image Displayed by a Windows Forms Control</span></span>
<span data-ttu-id="a41dd-103">Několik Windows Forms – ovládací prvky můžete zobrazit obrázky.</span><span class="sxs-lookup"><span data-stu-id="a41dd-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="a41dd-104">Tyto Image může být ikony, které vysvětluje účel ovládacího prvku, jako je například disketu ikonu na tlačítko, které označuje **Uložit** příkaz.</span><span class="sxs-lookup"><span data-stu-id="a41dd-104">These images can be icons that clarify the purpose of the control, such as a diskette icon on a button denoting the **Save** command.</span></span> <span data-ttu-id="a41dd-105">Ikony, případně může být obrázky na pozadí vzhled a chování, které chcete poskytnout ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a41dd-105">Alternatively, the icons can be background images to give the control the appearance and behavior you want.</span></span>  
  
### <a name="to-set-the-image-displayed-by-a-control"></a><span data-ttu-id="a41dd-106">K nastavení obrázku zobrazovaného ovládacím prvkem</span><span class="sxs-lookup"><span data-stu-id="a41dd-106">To set the image displayed by a control</span></span>  
  
1.  <span data-ttu-id="a41dd-107">Nastavte ovládacího prvku `Image` nebo `BackgroundImage` vlastností pro objekt typu <xref:System.Drawing.Image>.</span><span class="sxs-lookup"><span data-stu-id="a41dd-107">Set the control's `Image` or `BackgroundImage` property to an object of type <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="a41dd-108">Obecně platí, je bude možné načítat obrázek ze souboru pomocí <xref:System.Drawing.Image.FromFile%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="a41dd-108">Generally, you will be loading the image from a file by using the <xref:System.Drawing.Image.FromFile%2A> method.</span></span>  
  
     <span data-ttu-id="a41dd-109">V následujícím příkladu kódu cesta pro umístění image je nastavena **obrázky** složky.</span><span class="sxs-lookup"><span data-stu-id="a41dd-109">In the following code example, the path set for the location of the image is the **My Pictures** folder.</span></span> <span data-ttu-id="a41dd-110">Většina počítačů s operačním systémem Windows budou obsahovat tento adresář.</span><span class="sxs-lookup"><span data-stu-id="a41dd-110">Most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="a41dd-111">To také umožňuje uživatelům s minimální systém úrovně přístupu pro spuštění aplikace bezpečně.</span><span class="sxs-lookup"><span data-stu-id="a41dd-111">This also enables users with minimal system access levels to run the application safely.</span></span> <span data-ttu-id="a41dd-112">Následující příklad kódu vyžaduje, že už máte formulář s <xref:System.Windows.Forms.PictureBox> ovládací prvek přidán.</span><span class="sxs-lookup"><span data-stu-id="a41dd-112">The following code example requires that you already have a form with a <xref:System.Windows.Forms.PictureBox> control added.</span></span>  
  
    ```vb  
    ' Replace the image named below  
    ' with an icon of your own choosing.  
    PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.MyPictures) _  
       & "\Image.gif")  
    ```  
  
    ```csharp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.MyPictures)  
       + @"\Image.gif");  
    ```  
  
    ```cpp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    pictureBox1->Image = Image::FromFile(String::Concat  
       (System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::MyPictures),  
       "\\Image.gif"));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a41dd-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="a41dd-113">See Also</span></span>  
 <xref:System.Drawing.Image.FromFile%2A>  
 <xref:System.Drawing.Image>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>
