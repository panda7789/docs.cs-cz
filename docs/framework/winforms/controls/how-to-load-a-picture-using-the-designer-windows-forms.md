---
title: 'Postupy: Načtení obrázku pomocí Návrháře'
description: Naučte se, jak pomocí ovládacího prvku model Windows Forms PictureBox načíst a zobrazit obrázek ve formuláři v době návrhu.
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: a05ffe19412fc7a4e3e02f01336d89cce39fac8a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325599"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="65b54-103">Postupy: Načtení obrázku pomocí Návrháře (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="65b54-103">How to: Load a Picture Using the Designer (Windows Forms)</span></span>

<span data-ttu-id="65b54-104">Pomocí <xref:System.Windows.Forms.PictureBox> ovládacího prvku model Windows Forms můžete načíst a zobrazit obrázek ve formuláři v době návrhu nastavením <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnosti na platný obrázek.</span><span class="sxs-lookup"><span data-stu-id="65b54-104">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="65b54-105">V následující tabulce jsou uvedeny přijatelné typy souborů.</span><span class="sxs-lookup"><span data-stu-id="65b54-105">The following table shows the acceptable file types.</span></span>

|<span data-ttu-id="65b54-106">Typ</span><span class="sxs-lookup"><span data-stu-id="65b54-106">Type</span></span>|<span data-ttu-id="65b54-107">Přípona názvu souboru</span><span class="sxs-lookup"><span data-stu-id="65b54-107">File name extension</span></span>|
|---|---|
|<span data-ttu-id="65b54-108">Monochromatick</span><span class="sxs-lookup"><span data-stu-id="65b54-108">Bitmap</span></span>|<span data-ttu-id="65b54-109">.bmp</span><span class="sxs-lookup"><span data-stu-id="65b54-109">.bmp</span></span>|
|<span data-ttu-id="65b54-110">Ikona</span><span class="sxs-lookup"><span data-stu-id="65b54-110">Icon</span></span>|<span data-ttu-id="65b54-111">Přípona. ico</span><span class="sxs-lookup"><span data-stu-id="65b54-111">.ico</span></span>|
|<span data-ttu-id="65b54-112">GIF</span><span class="sxs-lookup"><span data-stu-id="65b54-112">GIF</span></span>|<span data-ttu-id="65b54-113">.gif</span><span class="sxs-lookup"><span data-stu-id="65b54-113">.gif</span></span>|
|<span data-ttu-id="65b54-114">Soubory</span><span class="sxs-lookup"><span data-stu-id="65b54-114">Metafile</span></span>|<span data-ttu-id="65b54-115">. WMF</span><span class="sxs-lookup"><span data-stu-id="65b54-115">.wmf</span></span>|
|<span data-ttu-id="65b54-116">JPEG</span><span class="sxs-lookup"><span data-stu-id="65b54-116">JPEG</span></span>|<span data-ttu-id="65b54-117">.jpg</span><span class="sxs-lookup"><span data-stu-id="65b54-117">.jpg</span></span>|

## <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="65b54-118">Zobrazení obrázku v době návrhu</span><span class="sxs-lookup"><span data-stu-id="65b54-118">To display a picture at design time</span></span>

1. <span data-ttu-id="65b54-119">Nakreslete <xref:System.Windows.Forms.PictureBox> ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="65b54-119">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>

2. <span data-ttu-id="65b54-120">V okně **vlastnosti** vyberte <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnost a potom kliknutím na tlačítko se třemi tečkami zobrazte dialogové okno **otevřít** .</span><span class="sxs-lookup"><span data-stu-id="65b54-120">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then select the ellipsis button to display the **Open** dialog box.</span></span>

3. <span data-ttu-id="65b54-121">Pokud hledáte určitý typ souboru (například soubory. gif), vyberte ho v poli **soubory typu** .</span><span class="sxs-lookup"><span data-stu-id="65b54-121">If you're looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>

4. <span data-ttu-id="65b54-122">Vyberte soubor, který chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="65b54-122">Select the file you want to display.</span></span>

## <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="65b54-123">Vymazání obrázku v době návrhu</span><span class="sxs-lookup"><span data-stu-id="65b54-123">To clear the picture at design time</span></span>

1. <span data-ttu-id="65b54-124">V okně **vlastnosti** vyberte <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="65b54-124">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property.</span></span> <span data-ttu-id="65b54-125">Klikněte pravým tlačítkem myši na miniaturu malého obrázku, který se zobrazí nalevo od názvu objektu obrázku, a pak zvolte možnost **obnovit**.</span><span class="sxs-lookup"><span data-stu-id="65b54-125">Right-click the small thumbnail image that appears to the left of the name of the image object, and then choose **Reset**.</span></span>

## <a name="see-also"></a><span data-ttu-id="65b54-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="65b54-126">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="65b54-127">PictureBox – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="65b54-127">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="65b54-128">Postupy: Změna velikosti či umístění obrázku za běhu</span><span class="sxs-lookup"><span data-stu-id="65b54-128">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="65b54-129">Postupy: Nastavení obrázků za běhu</span><span class="sxs-lookup"><span data-stu-id="65b54-129">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="65b54-130">PictureBox – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="65b54-130">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
