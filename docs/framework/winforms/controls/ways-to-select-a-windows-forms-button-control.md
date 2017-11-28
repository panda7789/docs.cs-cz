---
title: "Metody výběru ovládacího prvku Windows Forms Button"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 08b5359446a80da257f5afec07cc70e3d4aad46b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ways-to-select-a-windows-forms-button-control"></a><span data-ttu-id="8bb32-102">Metody výběru ovládacího prvku Windows Forms Button</span><span class="sxs-lookup"><span data-stu-id="8bb32-102">Ways to Select a Windows Forms Button Control</span></span>
<span data-ttu-id="8bb32-103">Tlačítko Windows Forms lze vybrat následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="8bb32-103">A Windows Forms button can be selected in the following ways:</span></span>  
  
-   <span data-ttu-id="8bb32-104">Klikněte na tlačítko pomocí myši.</span><span class="sxs-lookup"><span data-stu-id="8bb32-104">Use a mouse to click the button.</span></span>  
  
-   <span data-ttu-id="8bb32-105">Vyvolání na tlačítko <xref:System.Windows.Forms.Control.Click> událostí v kódu.</span><span class="sxs-lookup"><span data-stu-id="8bb32-105">Invoke the button's <xref:System.Windows.Forms.Control.Click> event in code.</span></span>  
  
-   <span data-ttu-id="8bb32-106">Přesun zaměření pro tlačítko stisknutím klávesy TAB a pak zvolte tlačítko stisknutím klávesy MEZERNÍK nebo ENTER.</span><span class="sxs-lookup"><span data-stu-id="8bb32-106">Move the focus to the button by pressing the TAB key, and then choose the button by pressing the SPACEBAR or ENTER.</span></span>  
  
-   <span data-ttu-id="8bb32-107">Stisknutím klávesy přístup (ALT + podtržené písmeno) pro tlačítko.</span><span class="sxs-lookup"><span data-stu-id="8bb32-107">Press the access key (ALT + the underlined letter) for the button.</span></span> <span data-ttu-id="8bb32-108">Další informace o přístupových klíčů najdete v tématu [postupy: vytvoření přístup klíčů pro Windows Forms – ovládací prvky](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="8bb32-108">For more information about access keys, see [How to: Create Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
-   <span data-ttu-id="8bb32-109">Je-li na tlačítko "přijmout" tlačítko ve formuláři, stisknutím klávesy ENTER rozhodne na tlačítko i v případě, že další ovládací prvek fokus – s výjimkou je-li tuto další kontrolu jiné tlačítko, Víceřádkový textového pole nebo vlastní ovládací prvek, který traps klávesu enter.</span><span class="sxs-lookup"><span data-stu-id="8bb32-109">If the button is the "accept" button of the form, pressing ENTER chooses the button, even if another control has the focus — except if that other control is another button, a multi-line text box, or a custom control that traps the enter key.</span></span>  
  
-   <span data-ttu-id="8bb32-110">Je-li na tlačítko tlačítko "zrušit" formuláře, stisknutím klávesy ESC zvolí tlačítko, i v případě, že další ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="8bb32-110">If the button is the "cancel" button of the form, pressing ESC chooses the button, even if another control has the focus.</span></span>  
  
-   <span data-ttu-id="8bb32-111">Volání <xref:System.Windows.Forms.Button.PerformClick%2A> metoda vyberte tlačítko prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="8bb32-111">Call the <xref:System.Windows.Forms.Button.PerformClick%2A> method to select the button programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bb32-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="8bb32-112">See Also</span></span>  
 [<span data-ttu-id="8bb32-113">Přehled ovládacího prvku tlačítko</span><span class="sxs-lookup"><span data-stu-id="8bb32-113">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="8bb32-114">Postupy: reakce na kliknutí na tlačítko Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8bb32-114">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="8bb32-115">Tlačítko – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="8bb32-115">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
