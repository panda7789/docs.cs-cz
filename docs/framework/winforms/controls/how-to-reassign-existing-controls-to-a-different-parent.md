---
title: 'Postupy: Přiřazení existujících ovládacích prvků jinému nadřazenému prvku'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
ms.openlocfilehash: 650d10fd681a55dfb17425111ef9d81726551da9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720183"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="ff802-102">Postupy: Přiřazení existujících ovládacích prvků jinému nadřazenému prvku</span><span class="sxs-lookup"><span data-stu-id="ff802-102">How to: Reassign Existing Controls to a Different Parent</span></span>
<span data-ttu-id="ff802-103">Můžete přiřadit ovládací prvky, které existují ve formuláři pro nový ovládací prvek kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ff802-103">You can assign controls that exist on your form to a new container control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff802-104">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="ff802-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="ff802-105">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="ff802-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="ff802-106">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="ff802-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="ff802-107">K přiřazení existujících ovládacích prvků jinému nadřazenému prvku</span><span class="sxs-lookup"><span data-stu-id="ff802-107">To reassign existing controls to a different parent</span></span>  
  
1.  <span data-ttu-id="ff802-108">Přetáhněte tři <xref:System.Windows.Forms.Button> ovládacích prvků z **nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="ff802-108">Drag three <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto the form.</span></span>  
  
     <span data-ttu-id="ff802-109">Umístěte blízko sobě navzájem, ale nechat nezarovnaných.</span><span class="sxs-lookup"><span data-stu-id="ff802-109">Position them near to each other, but leave them unaligned.</span></span>  
  
2.  <span data-ttu-id="ff802-110">V **nástrojů**, klikněte na tlačítko <xref:System.Windows.Forms.FlowLayoutPanel> ikonu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ff802-110">In the **Toolbox**, click the <xref:System.Windows.Forms.FlowLayoutPanel> control icon.</span></span>  
  
     <span data-ttu-id="ff802-111">Není přetáhněte ikonu na formuláři.</span><span class="sxs-lookup"><span data-stu-id="ff802-111">Do not drag the icon onto the form.</span></span>  
  
3.  <span data-ttu-id="ff802-112">Přesuňte ukazatel myši blízko tři <xref:System.Windows.Forms.Button> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="ff802-112">Move the mouse pointer close to the three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
     <span data-ttu-id="ff802-113">Ukazatel se změní na křížek s <xref:System.Windows.Forms.FlowLayoutPanel> ikonu ovládací prvek připojen.</span><span class="sxs-lookup"><span data-stu-id="ff802-113">The pointer changes to a crosshair with the <xref:System.Windows.Forms.FlowLayoutPanel> control icon attached.</span></span>  
  
4.  <span data-ttu-id="ff802-114">Klepněte a podržte tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="ff802-114">Click and hold the mouse button.</span></span>  
  
5.  <span data-ttu-id="ff802-115">Přetažením ukazatele myši nakreslete obrysu <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ff802-115">Drag the mouse pointer to draw the outline of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
6.  <span data-ttu-id="ff802-116">Nakreslit obrys kolem tři <xref:System.Windows.Forms.Button> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="ff802-116">Draw the outline around the three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
7.  <span data-ttu-id="ff802-117">Uvolněte tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="ff802-117">Release the mouse button.</span></span>  
  
     <span data-ttu-id="ff802-118">Tři <xref:System.Windows.Forms.Button> ovládací prvky jsou vloženy do <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ff802-118">The three <xref:System.Windows.Forms.Button> controls are now inserted into the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff802-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff802-119">See also</span></span>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="ff802-120">Uspořádávání ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ff802-120">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="ff802-121">Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ff802-121">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="ff802-122">Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar</span><span class="sxs-lookup"><span data-stu-id="ff802-122">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
