---
title: 'Postupy: Nastavení obrázku zobrazovaného ovládacím prvkem Windows Forms pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
- setting images [Windows Forms], Windows Forms controls
ms.assetid: ae80d07a-e469-4251-90ca-df71f5852454
ms.openlocfilehash: b914509656d3ce67d62dcd23cebdcc3b74278d72
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882008"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control-using-the-designer"></a><span data-ttu-id="3f7c6-102">Postupy: Nastavení obrázku zobrazovaného ovládacím prvkem Windows Forms pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="3f7c6-102">How to: Set the Image Displayed by a Windows Forms Control Using the Designer</span></span>
<span data-ttu-id="3f7c6-103">Několik ovládacích prvků Windows Forms nemohl zobrazit obrázky.</span><span class="sxs-lookup"><span data-stu-id="3f7c6-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="3f7c6-104">Obrázek může být ikonu, která vysvětluje účel ovládacího prvku, třeba ikony disku na tlačítko, které označuje **Uložit** příkazu.</span><span class="sxs-lookup"><span data-stu-id="3f7c6-104">The image can be an icon that clarifies the purpose of the control, such as a disk icon on a button denoting the **Save** command.</span></span> <span data-ttu-id="3f7c6-105">Případně může být ikonu poskytnout požadovaný vzhled ovládacího prvku obrázku na pozadí.</span><span class="sxs-lookup"><span data-stu-id="3f7c6-105">Alternatively, the icon can be a background image to give the control the appearance you want.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f7c6-106">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="3f7c6-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="3f7c6-107">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="3f7c6-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="3f7c6-108">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="3f7c6-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-the-image-displayed-by-a-control"></a><span data-ttu-id="3f7c6-109">K nastavení obrázku zobrazovaného ovládacím prvkem</span><span class="sxs-lookup"><span data-stu-id="3f7c6-109">To set the image displayed by a control</span></span>  
  
1. <span data-ttu-id="3f7c6-110">V **vlastnosti** okna, vyberte **Image** nebo **BackgroundImage** vlastnost ovládacího prvku, klikněte na tlačítko tří teček ()</span><span class="sxs-lookup"><span data-stu-id="3f7c6-110">In the **Properties** window, select the **Image** or **BackgroundImage** property of the control, then click the ellipsis button (</span></span>  
  
     ![Tlačítko se třemi tečkami (...) v okně Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)<span data-ttu-id="3f7c6-112">)</span><span class="sxs-lookup"><span data-stu-id="3f7c6-112">)</span></span>  
  
     <span data-ttu-id="3f7c6-113">) zobrazíte **vybrat prostředek** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="3f7c6-113">) to display the **Select Resource** dialog box.</span></span>  
  
2. <span data-ttu-id="3f7c6-114">Vyberte bitovou kopii, kterou chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="3f7c6-114">Select the image you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f7c6-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3f7c6-115">See also</span></span>

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="3f7c6-116">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="3f7c6-116">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
