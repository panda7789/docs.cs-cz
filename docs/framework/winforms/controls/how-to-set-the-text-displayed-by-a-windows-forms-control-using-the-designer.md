---
title: 'Postupy: Nastavit Text, zobrazený Windows Forms pomocí návrháře ovládacího prvku'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], setting caption
- Windows Forms, setting the text displayed
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
ms.openlocfilehash: cea2bcdb973e1deb5e0e6cf7fcc31b7c084dc446
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510582"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer"></a><span data-ttu-id="3e564-102">Postupy: Nastavit Text, zobrazený Windows Forms pomocí návrháře ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="3e564-102">How to: Set the Text Displayed by a Windows Forms Control Using the Designer</span></span>
<span data-ttu-id="3e564-103">Ovládací prvky Windows Forms obvykle zobrazí text, který souvisí s primární funkce ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3e564-103">Windows Forms controls typically display some text that is related to the primary function of the control.</span></span> <span data-ttu-id="3e564-104">Například <xref:System.Windows.Forms.Button> ovládací prvek zobrazí obvykle titulek, která určuje, jaká akce se provede při kliknutí na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="3e564-104">For example, a <xref:System.Windows.Forms.Button> control typically displays a caption that indicates what action will be performed when the button is clicked.</span></span> <span data-ttu-id="3e564-105">Pro všechny ovládací prvky, můžete nastavit nebo načíst text pomocí <xref:System.Windows.Forms.Control.Text%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3e564-105">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="3e564-106">Můžete změnit písmo pomocí <xref:System.Windows.Forms.Control.Font%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3e564-106">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>  
  
### <a name="to-set-the-text-and-font-with-the-designer"></a><span data-ttu-id="3e564-107">Chcete-li nastavit text a písma pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="3e564-107">To set the text and font with the designer</span></span>  
  
1.  <span data-ttu-id="3e564-108">V okně Vlastnosti nastavte <xref:System.Windows.Forms.Control.Text%2A> vlastnost ovládacího prvku na odpovídající řetězec.</span><span class="sxs-lookup"><span data-stu-id="3e564-108">In the Properties window, set the <xref:System.Windows.Forms.Control.Text%2A> property of the control to an appropriate string.</span></span>  
  
     <span data-ttu-id="3e564-109">Chcete-li vytvořit podtržené klávesovou zkratku, obsahuje znak ampersand (&) před písmenem, který bude klávesovou zkratku.</span><span class="sxs-lookup"><span data-stu-id="3e564-109">To create an underlined shortcut key, includes an ampersand (&) before the letter that will be the shortcut key.</span></span>  
  
2.  <span data-ttu-id="3e564-110">V okně Vlastnosti klikněte na tlačítko se třemi tečkami (![snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.Control.Font%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3e564-110">In the Properties window, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>  
  
     <span data-ttu-id="3e564-111">V dialogovém okně Standardní písmo vyberte písmo, styl písma, velikost, efektů (například podtržení nebo přeškrtnutí) a skriptů, které chcete.</span><span class="sxs-lookup"><span data-stu-id="3e564-111">In the standard font dialog box, select the font, font style, size, effects (such as strikeout or underline), and script that you want.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e564-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e564-112">See also</span></span>
- [<span data-ttu-id="3e564-113">Postupy: Nastavit Text, zobrazený ovládacím prvkem Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3e564-113">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="3e564-114">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="3e564-114">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
- [<span data-ttu-id="3e564-115">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="3e564-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
