---
title: "Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], setting caption
- Windows Forms, setting the text displayed
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 59d66df2c6f18ad28ad4b912c00e35f786d773da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer"></a><span data-ttu-id="7384a-102">Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="7384a-102">How to: Set the Text Displayed by a Windows Forms Control Using the Designer</span></span>
<span data-ttu-id="7384a-103">Ovládací prvky Windows Forms obvykle zobrazí text související s primární funkce ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7384a-103">Windows Forms controls typically display some text that is related to the primary function of the control.</span></span> <span data-ttu-id="7384a-104">Například <xref:System.Windows.Forms.Button> obvykle zobrazí popisek, který určuje, jaká akce se provede při kliknutí na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="7384a-104">For example, a <xref:System.Windows.Forms.Button> control typically displays a caption that indicates what action will be performed when the button is clicked.</span></span> <span data-ttu-id="7384a-105">Pro všechny ovládací prvky, můžete nastavit nebo vrátí text s použitím <xref:System.Windows.Forms.Control.Text%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7384a-105">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="7384a-106">Písmo můžete změnit pomocí <xref:System.Windows.Forms.Control.Font%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7384a-106">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>  
  
### <a name="to-set-the-text-and-font-with-the-designer"></a><span data-ttu-id="7384a-107">Chcete-li nastavit text a písma pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="7384a-107">To set the text and font with the designer</span></span>  
  
1.  <span data-ttu-id="7384a-108">V okně vlastnosti nastavit <xref:System.Windows.Forms.Control.Text%2A> vlastnost ovládacího prvku na odpovídající řetězec.</span><span class="sxs-lookup"><span data-stu-id="7384a-108">In the Properties window, set the <xref:System.Windows.Forms.Control.Text%2A> property of the control to an appropriate string.</span></span>  
  
     <span data-ttu-id="7384a-109">Chcete-li vytvořit podtržené klávesová obsahuje znak ampersand (&) před písmeno, které bude klávesovou zkratku.</span><span class="sxs-lookup"><span data-stu-id="7384a-109">To create an underlined shortcut key, includes an ampersand (&) before the letter that will be the shortcut key.</span></span>  
  
2.  <span data-ttu-id="7384a-110">V okně vlastností klikněte na tlačítko se třemi tečkami (![– snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.Control.Font%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7384a-110">In the Properties window, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>  
  
     <span data-ttu-id="7384a-111">V dialogovém okně standardní písma vyberte písmo, styl písma, velikost, efekty (například přeškrtnutí nebo podtržení) a skriptu které chcete.</span><span class="sxs-lookup"><span data-stu-id="7384a-111">In the standard font dialog box, select the font, font style, size, effects (such as strikeout or underline), and script that you want.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7384a-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="7384a-112">See Also</span></span>  
 [<span data-ttu-id="7384a-113">Postupy: nastavení textu zobrazovaného prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7384a-113">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="7384a-114">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="7384a-114">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="7384a-115">Popisování jednotlivých Windows Forms – ovládací prvky a zajišťování zástupců pro tyto</span><span class="sxs-lookup"><span data-stu-id="7384a-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
