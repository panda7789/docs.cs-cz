---
title: 'Postupy: Načtení obrázku pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 12b90d561a18fcffaafb9c45b7fa6be6dd060215
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736328"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="31780-102">Postupy: Načtení obrázku pomocí Návrháře (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="31780-102">How to: Load a Picture Using the Designer (Windows Forms)</span></span>

<span data-ttu-id="31780-103">Pomocí ovládacího prvku model Windows Forms <xref:System.Windows.Forms.PictureBox> můžete načíst a zobrazit obrázek ve formuláři v době návrhu nastavením vlastnosti <xref:System.Windows.Forms.PictureBox.Image%2A> na platný obrázek.</span><span class="sxs-lookup"><span data-stu-id="31780-103">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="31780-104">V následující tabulce jsou uvedeny přijatelné typy souborů.</span><span class="sxs-lookup"><span data-stu-id="31780-104">The following table shows the acceptable file types.</span></span>

|<span data-ttu-id="31780-105">Type</span><span class="sxs-lookup"><span data-stu-id="31780-105">Type</span></span>|<span data-ttu-id="31780-106">Přípona názvu souboru</span><span class="sxs-lookup"><span data-stu-id="31780-106">File name extension</span></span>|
|---|---|
|<span data-ttu-id="31780-107">Monochromatick</span><span class="sxs-lookup"><span data-stu-id="31780-107">Bitmap</span></span>|<span data-ttu-id="31780-108">. bmp</span><span class="sxs-lookup"><span data-stu-id="31780-108">.bmp</span></span>|
|<span data-ttu-id="31780-109">Ikona</span><span class="sxs-lookup"><span data-stu-id="31780-109">Icon</span></span>|<span data-ttu-id="31780-110">.ico</span><span class="sxs-lookup"><span data-stu-id="31780-110">.ico</span></span>|
|<span data-ttu-id="31780-111">GIF</span><span class="sxs-lookup"><span data-stu-id="31780-111">GIF</span></span>|<span data-ttu-id="31780-112">. gif</span><span class="sxs-lookup"><span data-stu-id="31780-112">.gif</span></span>|
|<span data-ttu-id="31780-113">Soubory</span><span class="sxs-lookup"><span data-stu-id="31780-113">Metafile</span></span>|<span data-ttu-id="31780-114">.wmf</span><span class="sxs-lookup"><span data-stu-id="31780-114">.wmf</span></span>|
|<span data-ttu-id="31780-115">JPEG</span><span class="sxs-lookup"><span data-stu-id="31780-115">JPEG</span></span>|<span data-ttu-id="31780-116">.jpg</span><span class="sxs-lookup"><span data-stu-id="31780-116">.jpg</span></span>|

## <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="31780-117">Zobrazení obrázku v době návrhu</span><span class="sxs-lookup"><span data-stu-id="31780-117">To display a picture at design time</span></span>

1. <span data-ttu-id="31780-118">Nakreslete ovládací prvek <xref:System.Windows.Forms.PictureBox> na formuláři.</span><span class="sxs-lookup"><span data-stu-id="31780-118">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>

2. <span data-ttu-id="31780-119">V okně **vlastnosti** vyberte vlastnost <xref:System.Windows.Forms.PictureBox.Image%2A> a potom vyberte tlačítko se třemi tečkami, aby se zobrazilo dialogové okno **otevřít** .</span><span class="sxs-lookup"><span data-stu-id="31780-119">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then select the ellipsis button to display the **Open** dialog box.</span></span>

3. <span data-ttu-id="31780-120">Pokud hledáte určitý typ souboru (například soubory. gif), vyberte ho v poli **soubory typu** .</span><span class="sxs-lookup"><span data-stu-id="31780-120">If you're looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>

4. <span data-ttu-id="31780-121">Vyberte soubor, který chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="31780-121">Select the file you want to display.</span></span>

## <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="31780-122">Vymazání obrázku v době návrhu</span><span class="sxs-lookup"><span data-stu-id="31780-122">To clear the picture at design time</span></span>

1. <span data-ttu-id="31780-123">V okně **vlastnosti** vyberte vlastnost <xref:System.Windows.Forms.PictureBox.Image%2A>.</span><span class="sxs-lookup"><span data-stu-id="31780-123">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property.</span></span> <span data-ttu-id="31780-124">Klikněte pravým tlačítkem myši na miniaturu malého obrázku, který se zobrazí nalevo od názvu objektu obrázku, a pak zvolte možnost **obnovit**.</span><span class="sxs-lookup"><span data-stu-id="31780-124">Right-click the small thumbnail image that appears to the left of the name of the image object, and then choose **Reset**.</span></span>

## <a name="see-also"></a><span data-ttu-id="31780-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="31780-125">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="31780-126">Přehled ovládacího prvku PictureBox</span><span class="sxs-lookup"><span data-stu-id="31780-126">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="31780-127">Postupy: Změna velikosti či umístění obrázku za běhu</span><span class="sxs-lookup"><span data-stu-id="31780-127">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="31780-128">Postupy: Nastavení obrázků za běhu</span><span class="sxs-lookup"><span data-stu-id="31780-128">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="31780-129">Ovládací prvek PictureBox</span><span class="sxs-lookup"><span data-stu-id="31780-129">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
