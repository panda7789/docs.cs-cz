---
title: 'Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], setting caption
- Windows Forms, setting the text displayed
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
ms.openlocfilehash: e41ce3e91e6c2a3c91dd0dc39723df1185721096
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532991"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer"></a><span data-ttu-id="84c43-102">Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="84c43-102">How to: Set the Text Displayed by a Windows Forms Control Using the Designer</span></span>
<span data-ttu-id="84c43-103">Ovládací prvky Windows Forms obvykle zobrazí text související s primární funkce ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="84c43-103">Windows Forms controls typically display some text that is related to the primary function of the control.</span></span> <span data-ttu-id="84c43-104">Například <xref:System.Windows.Forms.Button> obvykle zobrazí popisek, který určuje, jaká akce se provede při kliknutí na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="84c43-104">For example, a <xref:System.Windows.Forms.Button> control typically displays a caption that indicates what action will be performed when the button is clicked.</span></span> <span data-ttu-id="84c43-105">Pro všechny ovládací prvky, můžete nastavit nebo vrátí text s použitím <xref:System.Windows.Forms.Control.Text%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="84c43-105">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="84c43-106">Písmo můžete změnit pomocí <xref:System.Windows.Forms.Control.Font%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="84c43-106">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>  
  
### <a name="to-set-the-text-and-font-with-the-designer"></a><span data-ttu-id="84c43-107">Chcete-li nastavit text a písma pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="84c43-107">To set the text and font with the designer</span></span>  
  
1.  <span data-ttu-id="84c43-108">V okně vlastnosti nastavit <xref:System.Windows.Forms.Control.Text%2A> vlastnost ovládacího prvku na odpovídající řetězec.</span><span class="sxs-lookup"><span data-stu-id="84c43-108">In the Properties window, set the <xref:System.Windows.Forms.Control.Text%2A> property of the control to an appropriate string.</span></span>  
  
     <span data-ttu-id="84c43-109">Chcete-li vytvořit podtržené klávesová obsahuje znak ampersand (&) před písmeno, které bude klávesovou zkratku.</span><span class="sxs-lookup"><span data-stu-id="84c43-109">To create an underlined shortcut key, includes an ampersand (&) before the letter that will be the shortcut key.</span></span>  
  
2.  <span data-ttu-id="84c43-110">V okně vlastností klikněte na tlačítko se třemi tečkami (![– snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.Control.Font%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="84c43-110">In the Properties window, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>  
  
     <span data-ttu-id="84c43-111">V dialogovém okně standardní písma vyberte písmo, styl písma, velikost, efekty (například přeškrtnutí nebo podtržení) a skriptu které chcete.</span><span class="sxs-lookup"><span data-stu-id="84c43-111">In the standard font dialog box, select the font, font style, size, effects (such as strikeout or underline), and script that you want.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84c43-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="84c43-112">See Also</span></span>  
 [<span data-ttu-id="84c43-113">Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms</span><span class="sxs-lookup"><span data-stu-id="84c43-113">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="84c43-114">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="84c43-114">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="84c43-115">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="84c43-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
