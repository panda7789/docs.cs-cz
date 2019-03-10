---
title: 'Postupy: Nastavení obrázku zobrazovaného podle Windows Forms pomocí návrháře ovládací prvek'
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
- setting images [Windows Forms], Windows Forms controls
ms.assetid: ae80d07a-e469-4251-90ca-df71f5852454
ms.openlocfilehash: 265fc88fb2bb9aef0696ea0d7e707ae07084df1d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702254"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control-using-the-designer"></a><span data-ttu-id="b4332-102">Postupy: Nastavení obrázku zobrazovaného podle Windows Forms pomocí návrháře ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="b4332-102">How to: Set the Image Displayed by a Windows Forms Control Using the Designer</span></span>
<span data-ttu-id="b4332-103">Několik ovládacích prvků Windows Forms nemohl zobrazit obrázky.</span><span class="sxs-lookup"><span data-stu-id="b4332-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="b4332-104">Obrázek může být ikonu, která vysvětluje účel ovládacího prvku, třeba ikony disku na tlačítko, které označuje **Uložit** příkazu.</span><span class="sxs-lookup"><span data-stu-id="b4332-104">The image can be an icon that clarifies the purpose of the control, such as a disk icon on a button denoting the **Save** command.</span></span> <span data-ttu-id="b4332-105">Případně může být ikonu poskytnout požadovaný vzhled ovládacího prvku obrázku na pozadí.</span><span class="sxs-lookup"><span data-stu-id="b4332-105">Alternatively, the icon can be a background image to give the control the appearance you want.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4332-106">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="b4332-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b4332-107">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="b4332-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b4332-108">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="b4332-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-the-image-displayed-by-a-control"></a><span data-ttu-id="b4332-109">K nastavení obrázku zobrazovaného ovládacím prvkem</span><span class="sxs-lookup"><span data-stu-id="b4332-109">To set the image displayed by a control</span></span>  
  
1.  <span data-ttu-id="b4332-110">V **vlastnosti** okna, vyberte **Image** nebo **BackgroundImage** vlastnost ovládacího prvku, klikněte na tlačítko tří teček ()</span><span class="sxs-lookup"><span data-stu-id="b4332-110">In the **Properties** window, select the **Image** or **BackgroundImage** property of the control, then click the ellipsis button (</span></span>  
  
     <span data-ttu-id="b4332-111">![Snímek obrazovky VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton")</span><span class="sxs-lookup"><span data-stu-id="b4332-111">![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")</span></span>  
  
     <span data-ttu-id="b4332-112">) zobrazíte **vybrat prostředek** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="b4332-112">) to display the **Select Resource** dialog box.</span></span>  
  
2.  <span data-ttu-id="b4332-113">Vyberte bitovou kopii, kterou chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="b4332-113">Select the image you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4332-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4332-114">See also</span></span>
- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="b4332-115">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="b4332-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
