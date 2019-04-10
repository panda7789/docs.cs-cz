---
title: 'Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: 1a3fcac56df1328c12d7a5dcb542138afdb486f5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214829"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a><span data-ttu-id="6f124-102">Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="6f124-102">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>
<span data-ttu-id="6f124-103">Windows Forms <xref:System.Windows.Forms.Panel> ovládací prvky se používají k seskupování další ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="6f124-103">Windows Forms <xref:System.Windows.Forms.Panel> controls are used to group other controls.</span></span> <span data-ttu-id="6f124-104">Existují tři hlavní důvody k seskupování ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="6f124-104">There are three reasons to group controls.</span></span> <span data-ttu-id="6f124-105">Jeden je vizuální seskupení elementů související formuláře pro jasné uživatelské rozhraní; Další je programový seskupování, přepínačů. poslední slouží k přesunutí ovládacích prvků jako jednotka v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="6f124-105">One is visual grouping of related form elements for a clear user interface; another is programmatic grouping, of radio buttons for example; the last is for moving the controls as a unit at design time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f124-106">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="6f124-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="6f124-107">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="6f124-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="6f124-108">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="6f124-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="6f124-109">Chcete-li vytvořit skupinu ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="6f124-109">To create a group of controls</span></span>  
  
1.  <span data-ttu-id="6f124-110">Přetáhněte <xref:System.Windows.Forms.Panel> ovládacího prvku **Windows Forms** kartu na panelu nástrojů do formuláře.</span><span class="sxs-lookup"><span data-stu-id="6f124-110">Drag a <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab of the Toolbox onto a form.</span></span>  
  
2.  <span data-ttu-id="6f124-111">Přidejte další ovládací prvky panel, kreslení každý uvnitř panelu.</span><span class="sxs-lookup"><span data-stu-id="6f124-111">Add other controls to the panel, drawing each inside the panel.</span></span>  
  
     <span data-ttu-id="6f124-112">Pokud máte existující ovládací prvky, které chcete uvést v panelu, můžete vybrat všechny ovládací prvky, vyjmout data do schránky, vyberte <xref:System.Windows.Forms.Panel> ovládací prvek a pak je vložte do panelu.</span><span class="sxs-lookup"><span data-stu-id="6f124-112">If you have existing controls that you want to enclose in a panel, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.Panel> control, and then paste them into the panel.</span></span> <span data-ttu-id="6f124-113">Můžete také přetáhnout do panelu.</span><span class="sxs-lookup"><span data-stu-id="6f124-113">You can also drag them into the panel.</span></span>  
  
3.  <span data-ttu-id="6f124-114">(Volitelné) Pokud chcete doplnit o ohraničení panelu, nastavte jeho <xref:System.Windows.Forms.BorderStyle> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6f124-114">(Optional) If you want to add a border to a panel, set its <xref:System.Windows.Forms.BorderStyle> property.</span></span> <span data-ttu-id="6f124-115">Existují tři možnosti: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, a <xref:System.Windows.Forms.BorderStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="6f124-115">There are three choices: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, and <xref:System.Windows.Forms.BorderStyle.None>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f124-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6f124-116">See also</span></span>

- [<span data-ttu-id="6f124-117">Ovládací prvek Panel</span><span class="sxs-lookup"><span data-stu-id="6f124-117">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="6f124-118">Přehled ovládacího prvku Panel</span><span class="sxs-lookup"><span data-stu-id="6f124-118">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="6f124-119">Postupy: Nastavení pozadí panelu</span><span class="sxs-lookup"><span data-stu-id="6f124-119">How to: Set the Background of a Panel</span></span>](how-to-set-the-background-of-a-windows-forms-panel.md)
