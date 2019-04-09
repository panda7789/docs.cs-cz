---
title: 'Postupy: Načtení obrázku pomocí návrháře (Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 5aa8ff1efa045d52382cc5c24a0cae1f0f1bb510
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127137"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="079be-102">Postupy: Načtení obrázku pomocí návrháře (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="079be-102">How to: Load a Picture Using the Designer (Windows Forms)</span></span>
<span data-ttu-id="079be-103">Pomocí Windows Forms <xref:System.Windows.Forms.PictureBox> ovládacího prvku, lze načíst a zobrazit obrázek na formulář v době návrhu tak, že nastavíte <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnost platný obrázek.</span><span class="sxs-lookup"><span data-stu-id="079be-103">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="079be-104">Následující tabulka uvádí typy souborů přijatelné.</span><span class="sxs-lookup"><span data-stu-id="079be-104">The following table shows the acceptable file types.</span></span>  
  
|<span data-ttu-id="079be-105">Type</span><span class="sxs-lookup"><span data-stu-id="079be-105">Type</span></span>|<span data-ttu-id="079be-106">Přípona názvu souboru</span><span class="sxs-lookup"><span data-stu-id="079be-106">File name extension</span></span>|  
|----------|-------------------------|  
|<span data-ttu-id="079be-107">Rastrový obrázek</span><span class="sxs-lookup"><span data-stu-id="079be-107">Bitmap</span></span>|<span data-ttu-id="079be-108">BMP</span><span class="sxs-lookup"><span data-stu-id="079be-108">.bmp</span></span>|  
|<span data-ttu-id="079be-109">Ikona</span><span class="sxs-lookup"><span data-stu-id="079be-109">Icon</span></span>|<span data-ttu-id="079be-110">.ico</span><span class="sxs-lookup"><span data-stu-id="079be-110">.ico</span></span>|  
|<span data-ttu-id="079be-111">GIF</span><span class="sxs-lookup"><span data-stu-id="079be-111">GIF</span></span>|<span data-ttu-id="079be-112">GIF</span><span class="sxs-lookup"><span data-stu-id="079be-112">.gif</span></span>|  
|<span data-ttu-id="079be-113">Metasoubor</span><span class="sxs-lookup"><span data-stu-id="079be-113">Metafile</span></span>|<span data-ttu-id="079be-114">.wmf</span><span class="sxs-lookup"><span data-stu-id="079be-114">.wmf</span></span>|  
|<span data-ttu-id="079be-115">JPEG</span><span class="sxs-lookup"><span data-stu-id="079be-115">JPEG</span></span>|<span data-ttu-id="079be-116">.jpg</span><span class="sxs-lookup"><span data-stu-id="079be-116">.jpg</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="079be-117">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="079be-117">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="079be-118">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="079be-118">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="079be-119">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="079be-119">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="079be-120">Chcete-li zobrazit obrázek v době návrhu</span><span class="sxs-lookup"><span data-stu-id="079be-120">To display a picture at design time</span></span>  
  
1.  <span data-ttu-id="079be-121">Vykreslení <xref:System.Windows.Forms.PictureBox> ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="079be-121">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>  
  
2.  <span data-ttu-id="079be-122">V okně Vlastnosti vyberte <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnost a potom klikněte na tlačítko se třemi tečkami zobrazíte **otevřít** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="079be-122">On the Properties window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then click the ellipsis button to display the **Open** dialog box.</span></span>  
  
3.  <span data-ttu-id="079be-123">Pokud chcete pro určitý typ souboru (například soubory GIF), vyberte ho **soubory typu** pole.</span><span class="sxs-lookup"><span data-stu-id="079be-123">If you are looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>  
  
4.  <span data-ttu-id="079be-124">Vyberte soubor, který chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="079be-124">Select the file you want to display.</span></span>  
  
### <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="079be-125">Vymazat obrázek v době návrhu</span><span class="sxs-lookup"><span data-stu-id="079be-125">To clear the picture at design time</span></span>  
  
1.  <span data-ttu-id="079be-126">Na **vlastnosti** okna, vyberte <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnosti a kliknutím pravým tlačítkem na malé miniaturu, která se zobrazí nalevo od názvu objektu bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="079be-126">On the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property and right-click the small thumbnail image that appears to the left of the name of the image object.</span></span> <span data-ttu-id="079be-127">Zvolte **resetování**.</span><span class="sxs-lookup"><span data-stu-id="079be-127">Choose **Reset**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="079be-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="079be-128">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="079be-129">Přehled ovládacího prvku PictureBox</span><span class="sxs-lookup"><span data-stu-id="079be-129">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="079be-130">Postupy: Změna velikosti či umístění obrázku za běhu</span><span class="sxs-lookup"><span data-stu-id="079be-130">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="079be-131">Postupy: Nastavení obrázků za běhu</span><span class="sxs-lookup"><span data-stu-id="079be-131">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="079be-132">Ovládací prvek PictureBox</span><span class="sxs-lookup"><span data-stu-id="079be-132">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
