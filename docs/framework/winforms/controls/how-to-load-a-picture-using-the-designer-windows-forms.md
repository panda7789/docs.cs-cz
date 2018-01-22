---
title: "Postupy: Načtení obrázku pomocí Návrháře (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1dec3c71c0c93ce580925744fe55f05cd2e5f383
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="75d87-102">Postupy: Načtení obrázku pomocí Návrháře (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="75d87-102">How to: Load a Picture Using the Designer (Windows Forms)</span></span>
<span data-ttu-id="75d87-103">S Windows Forms <xref:System.Windows.Forms.PictureBox> ovládací prvek, můžete načíst a zobrazit obrázek v době návrhu nastavením ve formuláři <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnost, která má platný obrázek.</span><span class="sxs-lookup"><span data-stu-id="75d87-103">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="75d87-104">Následující tabulka uvádí typy souborů přijatelný.</span><span class="sxs-lookup"><span data-stu-id="75d87-104">The following table shows the acceptable file types.</span></span>  
  
|<span data-ttu-id="75d87-105">Typ</span><span class="sxs-lookup"><span data-stu-id="75d87-105">Type</span></span>|<span data-ttu-id="75d87-106">Přípona názvu souboru</span><span class="sxs-lookup"><span data-stu-id="75d87-106">File name extension</span></span>|  
|----------|-------------------------|  
|<span data-ttu-id="75d87-107">Bitmap</span><span class="sxs-lookup"><span data-stu-id="75d87-107">Bitmap</span></span>|<span data-ttu-id="75d87-108">.bmp</span><span class="sxs-lookup"><span data-stu-id="75d87-108">.bmp</span></span>|  
|<span data-ttu-id="75d87-109">Ikona</span><span class="sxs-lookup"><span data-stu-id="75d87-109">Icon</span></span>|<span data-ttu-id="75d87-110">.ico</span><span class="sxs-lookup"><span data-stu-id="75d87-110">.ico</span></span>|  
|<span data-ttu-id="75d87-111">GIF</span><span class="sxs-lookup"><span data-stu-id="75d87-111">GIF</span></span>|<span data-ttu-id="75d87-112">.GIF</span><span class="sxs-lookup"><span data-stu-id="75d87-112">.gif</span></span>|  
|<span data-ttu-id="75d87-113">Metafile</span><span class="sxs-lookup"><span data-stu-id="75d87-113">Metafile</span></span>|<span data-ttu-id="75d87-114">.wmf</span><span class="sxs-lookup"><span data-stu-id="75d87-114">.wmf</span></span>|  
|<span data-ttu-id="75d87-115">JPEG</span><span class="sxs-lookup"><span data-stu-id="75d87-115">JPEG</span></span>|<span data-ttu-id="75d87-116">.jpg</span><span class="sxs-lookup"><span data-stu-id="75d87-116">.jpg</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="75d87-117">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="75d87-117">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="75d87-118">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="75d87-118">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="75d87-119">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="75d87-119">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="75d87-120">Chcete-li zobrazit obrázek v době návrhu</span><span class="sxs-lookup"><span data-stu-id="75d87-120">To display a picture at design time</span></span>  
  
1.  <span data-ttu-id="75d87-121">Kreslení <xref:System.Windows.Forms.PictureBox> prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="75d87-121">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>  
  
2.  <span data-ttu-id="75d87-122">V okně Vlastnosti, vyberte <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnost a potom klikněte na tlačítko se třemi tečkami zobrazíte **otevřete** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="75d87-122">On the Properties window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then click the ellipsis button to display the **Open** dialog box.</span></span>  
  
3.  <span data-ttu-id="75d87-123">Pokud hledáte určitý typ souboru (například soubory GIF), vyberte ho **soubory typu** pole.</span><span class="sxs-lookup"><span data-stu-id="75d87-123">If you are looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>  
  
4.  <span data-ttu-id="75d87-124">Vyberte soubor, který chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="75d87-124">Select the file you want to display.</span></span>  
  
### <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="75d87-125">Chcete-li vymazat obrázek v době návrhu</span><span class="sxs-lookup"><span data-stu-id="75d87-125">To clear the picture at design time</span></span>  
  
1.  <span data-ttu-id="75d87-126">Na **vlastnosti** vyberte <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnost a klikněte pravým tlačítkem na malé miniatury, který se zobrazí nalevo od názvu objektu bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="75d87-126">On the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property and right-click the small thumbnail image that appears to the left of the name of the image object.</span></span> <span data-ttu-id="75d87-127">Zvolte **resetovat**.</span><span class="sxs-lookup"><span data-stu-id="75d87-127">Choose **Reset**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75d87-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="75d87-128">See Also</span></span>  
 <xref:System.Windows.Forms.PictureBox>  
 [<span data-ttu-id="75d87-129">Přehled ovládacího prvku PictureBox</span><span class="sxs-lookup"><span data-stu-id="75d87-129">PictureBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [<span data-ttu-id="75d87-130">Postupy: Změna velikosti či umístění obrázku za běhu</span><span class="sxs-lookup"><span data-stu-id="75d87-130">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)  
 [<span data-ttu-id="75d87-131">Postupy: Nastavení obrázků za běhu</span><span class="sxs-lookup"><span data-stu-id="75d87-131">How to: Set Pictures at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)  
 [<span data-ttu-id="75d87-132">Ovládací prvek PictureBox</span><span class="sxs-lookup"><span data-stu-id="75d87-132">PictureBox Control</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
