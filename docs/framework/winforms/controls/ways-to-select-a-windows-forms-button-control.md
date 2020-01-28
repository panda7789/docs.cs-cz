---
title: Způsoby výběru ovládacího prvku tlačítko
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
ms.openlocfilehash: 145166d182f1ec51068ab3e0c23c12b471b69231
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740014"
---
# <a name="ways-to-select-a-windows-forms-button-control"></a><span data-ttu-id="4b90a-102">Metody výběru ovládacího prvku Windows Forms Button</span><span class="sxs-lookup"><span data-stu-id="4b90a-102">Ways to Select a Windows Forms Button Control</span></span>
<span data-ttu-id="4b90a-103">Tlačítko model Windows Forms může být vybráno následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="4b90a-103">A Windows Forms button can be selected in the following ways:</span></span>  
  
- <span data-ttu-id="4b90a-104">Pomocí myši klikněte na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="4b90a-104">Use a mouse to click the button.</span></span>  
  
- <span data-ttu-id="4b90a-105">Vyvolá událost <xref:System.Windows.Forms.Control.Click> tlačítka v kódu.</span><span class="sxs-lookup"><span data-stu-id="4b90a-105">Invoke the button's <xref:System.Windows.Forms.Control.Click> event in code.</span></span>  
  
- <span data-ttu-id="4b90a-106">Přesuňte fokus na tlačítko tak, že stisknete klávesu TAB a kliknete na tlačítko stisknutím klávesy MEZERNÍK nebo ZADÁNÍm příkazu.</span><span class="sxs-lookup"><span data-stu-id="4b90a-106">Move the focus to the button by pressing the TAB key, and then choose the button by pressing the SPACEBAR or ENTER.</span></span>  
  
- <span data-ttu-id="4b90a-107">Stiskněte přístupové klávesy (ALT + podtržené písmeno) pro tlačítko.</span><span class="sxs-lookup"><span data-stu-id="4b90a-107">Press the access key (ALT + the underlined letter) for the button.</span></span> <span data-ttu-id="4b90a-108">Další informace o přístupových klíčích najdete v tématu [Postupy: vytváření přístupových klíčů pro ovládací prvky model Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="4b90a-108">For more information about access keys, see [How to: Create Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
- <span data-ttu-id="4b90a-109">Pokud je tlačítko "přijmout" na formuláři, stiskněte klávesu ENTER, a to i v případě, že je vybrán jiný ovládací prvek – s výjimkou případu, kdy je tento jiný ovládací prvek další tlačítko, víceřádkové textové pole nebo vlastní ovládací prvek, který provádí soutisk klíče ENTER.</span><span class="sxs-lookup"><span data-stu-id="4b90a-109">If the button is the "accept" button of the form, pressing ENTER chooses the button, even if another control has the focus — except if that other control is another button, a multi-line text box, or a custom control that traps the enter key.</span></span>  
  
- <span data-ttu-id="4b90a-110">Pokud je tlačítko tlačítkem zrušit ve formuláři, stisknutí klávesy ESC zvolí tlačítko, a to i v případě, že je vybrán jiný ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="4b90a-110">If the button is the "cancel" button of the form, pressing ESC chooses the button, even if another control has the focus.</span></span>  
  
- <span data-ttu-id="4b90a-111">Chcete-li vybrat tlačítko programově, zavolejte metodu <xref:System.Windows.Forms.Button.PerformClick%2A>.</span><span class="sxs-lookup"><span data-stu-id="4b90a-111">Call the <xref:System.Windows.Forms.Button.PerformClick%2A> method to select the button programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b90a-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b90a-112">See also</span></span>

- [<span data-ttu-id="4b90a-113">Přehled ovládacího prvku Button</span><span class="sxs-lookup"><span data-stu-id="4b90a-113">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="4b90a-114">Postupy: Reakce na kliknutí na tlačítko Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4b90a-114">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="4b90a-115">Ovládací prvek Button</span><span class="sxs-lookup"><span data-stu-id="4b90a-115">Button Control</span></span>](button-control-windows-forms.md)
