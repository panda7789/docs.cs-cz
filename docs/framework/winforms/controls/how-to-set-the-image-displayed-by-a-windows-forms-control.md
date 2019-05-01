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
ms.openlocfilehash: 1de835bda5ac906837ac3fbd97b87f68f14d1953
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013137"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a><span data-ttu-id="1771a-102">Postupy: Nastavení obrázku zobrazovaného ovládacím prvkem Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1771a-102">How to: Set the Image Displayed by a Windows Forms Control</span></span>
<span data-ttu-id="1771a-103">Několik ovládacích prvků Windows Forms nemohl zobrazit obrázky.</span><span class="sxs-lookup"><span data-stu-id="1771a-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="1771a-104">Tyto Image může být ikon, které vysvětluje účel ovládacího prvku, jako je například ikonu diskety na tlačítko, které označuje **Uložit** příkazu.</span><span class="sxs-lookup"><span data-stu-id="1771a-104">These images can be icons that clarify the purpose of the control, such as a diskette icon on a button denoting the **Save** command.</span></span> <span data-ttu-id="1771a-105">Ikony, případně může být obrázky na pozadí vzhledu a chování, které chcete poskytnout ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="1771a-105">Alternatively, the icons can be background images to give the control the appearance and behavior you want.</span></span>  
  
### <a name="to-set-the-image-displayed-by-a-control"></a><span data-ttu-id="1771a-106">K nastavení obrázku zobrazovaného ovládacím prvkem</span><span class="sxs-lookup"><span data-stu-id="1771a-106">To set the image displayed by a control</span></span>  
  
1. <span data-ttu-id="1771a-107">Nastavit u tohoto prvku `Image` nebo `BackgroundImage` vlastnost na objekt typu <xref:System.Drawing.Image>.</span><span class="sxs-lookup"><span data-stu-id="1771a-107">Set the control's `Image` or `BackgroundImage` property to an object of type <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="1771a-108">Obecně platí, můžete se načítá image ze souboru pomocí <xref:System.Drawing.Image.FromFile%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1771a-108">Generally, you will be loading the image from a file by using the <xref:System.Drawing.Image.FromFile%2A> method.</span></span>  
  
     <span data-ttu-id="1771a-109">V následujícím příkladu kódu nastavena cesta pro umístění image je **obrázky** složky.</span><span class="sxs-lookup"><span data-stu-id="1771a-109">In the following code example, the path set for the location of the image is the **My Pictures** folder.</span></span> <span data-ttu-id="1771a-110">Tento adresář bude obsahovat většinu počítačů s operačním systémem Windows.</span><span class="sxs-lookup"><span data-stu-id="1771a-110">Most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="1771a-111">Také to umožňuje uživatelům s úrovní přístupu minimální systém bezpečně spouštět aplikace.</span><span class="sxs-lookup"><span data-stu-id="1771a-111">This also enables users with minimal system access levels to run the application safely.</span></span> <span data-ttu-id="1771a-112">Následující příklad kódu vyžaduje, abyste už měli formulář s <xref:System.Windows.Forms.PictureBox> přidán ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="1771a-112">The following code example requires that you already have a form with a <xref:System.Windows.Forms.PictureBox> control added.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1771a-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1771a-113">See also</span></span>

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
