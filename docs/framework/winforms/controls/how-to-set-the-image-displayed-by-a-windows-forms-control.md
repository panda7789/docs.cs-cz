---
title: Nastavení obrázku zobrazovaného ovládacím prvkem
ms.date: 08/20/2019
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
ms.openlocfilehash: 5df0068c8462bbaab0cb0135de1dd1b91ababe06
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746868"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a><span data-ttu-id="8e700-102">Postupy: nastavení obrázku zobrazovaného ovládacím prvkem model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8e700-102">How to: Set the image displayed by a Windows Forms control</span></span>

<span data-ttu-id="8e700-103">Obrázek může zobrazit několik ovládacích prvků model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8e700-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="8e700-104">Tyto obrázky mohou být ikony, které objasňují účel ovládacího prvku, jako je například ikona diskety na tlačítku, které označuje příkaz Save.</span><span class="sxs-lookup"><span data-stu-id="8e700-104">These images can be icons that clarify the purpose of the control, such as a diskette icon on a button denoting the Save command.</span></span> <span data-ttu-id="8e700-105">Alternativně mohou být ikony obrázky na pozadí, aby ovládací prvek poskytoval vzhled a chování, které chcete.</span><span class="sxs-lookup"><span data-stu-id="8e700-105">Alternatively, the icons can be background images to give the control the appearance and behavior you want.</span></span>

## <a name="programmatic"></a><span data-ttu-id="8e700-106">Blokují</span><span class="sxs-lookup"><span data-stu-id="8e700-106">Programmatic</span></span>

<span data-ttu-id="8e700-107">Nastavte vlastnost `Image` nebo `BackgroundImage` ovládacího prvku na objekt typu <xref:System.Drawing.Image>.</span><span class="sxs-lookup"><span data-stu-id="8e700-107">Set the control's `Image` or `BackgroundImage` property to an object of type <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="8e700-108">Obecně se načítá obrázek ze souboru pomocí metody <xref:System.Drawing.Image.FromFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="8e700-108">Generally, you'll be loading the image from a file by using the <xref:System.Drawing.Image.FromFile%2A> method.</span></span>

<span data-ttu-id="8e700-109">V následujícím příkladu kódu je cesta nastavená pro umístění obrázku složka **obrázky** .</span><span class="sxs-lookup"><span data-stu-id="8e700-109">In the following code example, the path set for the location of the image is the **My Pictures** folder.</span></span> <span data-ttu-id="8e700-110">Tento adresář zahrnuje Většina počítačů s operačním systémem Windows.</span><span class="sxs-lookup"><span data-stu-id="8e700-110">Most computers running the Windows operating system include this directory.</span></span> <span data-ttu-id="8e700-111">To také umožňuje uživatelům s minimálními úrovněmi přístupu k systému bezpečně spustit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8e700-111">This also enables users with minimal system access levels to run the application safely.</span></span> <span data-ttu-id="8e700-112">Následující příklad kódu vyžaduje, abyste již měli formulář s přidaným ovládacím prvkem <xref:System.Windows.Forms.PictureBox>.</span><span class="sxs-lookup"><span data-stu-id="8e700-112">The following code example requires that you already have a form with a <xref:System.Windows.Forms.PictureBox> control added.</span></span>

```vb
' Replace the image named below with your own icon.
PictureBox1.Image = Image.FromFile _
   (System.Environment.GetFolderPath _
   (System.Environment.SpecialFolder.MyPictures) _
   & "\Image.gif")
```

```csharp
// Replace the image named below with your own icon.
// Note the escape character used (@) when specifying the path.
pictureBox1.Image = Image.FromFile
   (System.Environment.GetFolderPath
   (System.Environment.SpecialFolder.MyPictures)
   + @"\Image.gif");
```

```cpp
// Replace the image named below with your own icon.
pictureBox1->Image = Image::FromFile(String::Concat
   (System::Environment::GetFolderPath
   (System::Environment::SpecialFolder::MyPictures),
   "\\Image.gif"));
```

## <a name="designer"></a><span data-ttu-id="8e700-113">Návrhář</span><span class="sxs-lookup"><span data-stu-id="8e700-113">Designer</span></span>

1. <span data-ttu-id="8e700-114">V okně **vlastnosti** sady Visual Studio vyberte vlastnost **Image** nebo **BackgroundImage** ovládacího prvku a potom vyberte tlačítko se třemi tečkami (![se třemi tečkami v aplikaci Visual Studio](./media/visual-studio-ellipsis-button.png)), aby se zobrazilo dialogové okno **Vybrat prostředek** .</span><span class="sxs-lookup"><span data-stu-id="8e700-114">In the **Properties** window of Visual Studio, select the **Image** or **BackgroundImage** property of the control, and then select the ellipsis (![Ellipsis button in Visual Studio](./media/visual-studio-ellipsis-button.png)) to display the **Select Resource** dialog box.</span></span>

2. <span data-ttu-id="8e700-115">Vyberte obrázek, který chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="8e700-115">Select the image you want to display.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e700-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e700-116">See also</span></span>

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
