---
title: Metody výběru ovládacího prvku Windows Forms Button
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
ms.openlocfilehash: 908751401d812be0403af5517d9bbf2ad7344f35
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573800"
---
# <a name="ways-to-select-a-windows-forms-button-control"></a><span data-ttu-id="c57ef-102">Metody výběru ovládacího prvku Windows Forms Button</span><span class="sxs-lookup"><span data-stu-id="c57ef-102">Ways to Select a Windows Forms Button Control</span></span>
<span data-ttu-id="c57ef-103">Tlačítka Windows Forms je vybrat následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="c57ef-103">A Windows Forms button can be selected in the following ways:</span></span>  
  
-   <span data-ttu-id="c57ef-104">Pomocí myši klikněte na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c57ef-104">Use a mouse to click the button.</span></span>  
  
-   <span data-ttu-id="c57ef-105">Vyvolání tlačítka <xref:System.Windows.Forms.Control.Click> událost v kódu.</span><span class="sxs-lookup"><span data-stu-id="c57ef-105">Invoke the button's <xref:System.Windows.Forms.Control.Click> event in code.</span></span>  
  
-   <span data-ttu-id="c57ef-106">Přesunutí výběru na tlačítko stisknutím klávesy TAB a pak klikněte na tlačítko stisknutím klávesy MEZERNÍK nebo ENTER.</span><span class="sxs-lookup"><span data-stu-id="c57ef-106">Move the focus to the button by pressing the TAB key, and then choose the button by pressing the SPACEBAR or ENTER.</span></span>  
  
-   <span data-ttu-id="c57ef-107">Stisknutím klávesy (ALT + podtržené písmeno) pro tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c57ef-107">Press the access key (ALT + the underlined letter) for the button.</span></span> <span data-ttu-id="c57ef-108">Další informace o přístupových klíčů najdete v tématu [jak: Vytváření přístupových klíčů pro ovládací prvky Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="c57ef-108">For more information about access keys, see [How to: Create Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
-   <span data-ttu-id="c57ef-109">Pokud je tlačítko "přijímat" tlačítko formuláře, stisknutím klávesy ENTER vybere tlačítko, i v případě, že jiný ovládací prvek má fokus – s výjimkou, pokud tento jiný ovládací prvek je jiné tlačítko, víceřádkové textové pole nebo vlastního ovládacího prvku, který zachycuje klávesu enter.</span><span class="sxs-lookup"><span data-stu-id="c57ef-109">If the button is the "accept" button of the form, pressing ENTER chooses the button, even if another control has the focus — except if that other control is another button, a multi-line text box, or a custom control that traps the enter key.</span></span>  
  
-   <span data-ttu-id="c57ef-110">Pokud je tlačítko "Storno" tlačítko formuláře, stiskněte klávesu ESC vybere tlačítko, i v případě, že jiný ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="c57ef-110">If the button is the "cancel" button of the form, pressing ESC chooses the button, even if another control has the focus.</span></span>  
  
-   <span data-ttu-id="c57ef-111">Volání <xref:System.Windows.Forms.Button.PerformClick%2A> metoda klikněte na tlačítko prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="c57ef-111">Call the <xref:System.Windows.Forms.Button.PerformClick%2A> method to select the button programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c57ef-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c57ef-112">See also</span></span>
- [<span data-ttu-id="c57ef-113">Přehled ovládacího prvku Button</span><span class="sxs-lookup"><span data-stu-id="c57ef-113">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)
- [<span data-ttu-id="c57ef-114">Postupy: Reakce na kliknutí na tlačítko Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c57ef-114">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="c57ef-115">Ovládací prvek Button</span><span class="sxs-lookup"><span data-stu-id="c57ef-115">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
