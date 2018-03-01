---
title: "Přehled ovládacího prvku Tlačítko (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Button
helpviewer_keywords:
- Button control [Windows Forms], about Button control
- buttons [Windows Forms], about buttons
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e04b99c9d85ae92ad4d013abc01c5b16914fe1c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="button-control-overview-windows-forms"></a><span data-ttu-id="c2275-102">Přehled ovládacího prvku Tlačítko (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="c2275-102">Button Control Overview (Windows Forms)</span></span>
<span data-ttu-id="c2275-103">Windows Forms <xref:System.Windows.Forms.Button> řízení umožňuje uživateli klikněte na něj k provedení akce.</span><span class="sxs-lookup"><span data-stu-id="c2275-103">The Windows Forms <xref:System.Windows.Forms.Button> control allows the user to click it to perform an action.</span></span> <span data-ttu-id="c2275-104">Při kliknutí na tlačítko efekt stisknuté a vydání.</span><span class="sxs-lookup"><span data-stu-id="c2275-104">When the button is clicked, it looks as if it is being pushed in and released.</span></span> <span data-ttu-id="c2275-105">Vždy, když uživatel klikne tlačítko <xref:System.Windows.Forms.Control.Click> je volána obslužná rutina události.</span><span class="sxs-lookup"><span data-stu-id="c2275-105">Whenever the user clicks a button, the <xref:System.Windows.Forms.Control.Click> event handler is invoked.</span></span> <span data-ttu-id="c2275-106">Umístit kód <xref:System.Windows.Forms.Control.Click> obslužné rutiny události provádět veškeré akce, které zvolíte.</span><span class="sxs-lookup"><span data-stu-id="c2275-106">You place code in the <xref:System.Windows.Forms.Control.Click> event handler to perform any action you choose.</span></span>  
  
 <span data-ttu-id="c2275-107">Text zobrazovaný na tlačítko se nachází v <xref:System.Windows.Forms.Control.Text%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c2275-107">The text displayed on the button is contained in the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="c2275-108">Pokud text přesahuje šířku tlačítko, budou zahrnovat na další řádek.</span><span class="sxs-lookup"><span data-stu-id="c2275-108">If your text exceeds the width of the button, it will wrap to the next line.</span></span> <span data-ttu-id="c2275-109">Však bude oříznut Pokud ovládací prvek neumožňuje celkové výšku.</span><span class="sxs-lookup"><span data-stu-id="c2275-109">However, it will be clipped if the control cannot accommodate its overall height.</span></span> <span data-ttu-id="c2275-110">Další informace najdete v tématu [postupy: nastavení zobrazí Text pomocí ovládacího prvku Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span><span class="sxs-lookup"><span data-stu-id="c2275-110">For more information, see [How to: Set the Text Displayed by a Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span></span> <span data-ttu-id="c2275-111"><xref:System.Windows.Forms.Control.Text%2A> Vlastnost může obsahovat přístupový klíč, který umožňuje uživateli "Kliknutím" ovládacího prvku stisknutím klávesy ALT přístupovým klíčem.</span><span class="sxs-lookup"><span data-stu-id="c2275-111">The <xref:System.Windows.Forms.Control.Text%2A> property can contain an access key, which allows a user to "click" the control by pressing the ALT key with the access key.</span></span> <span data-ttu-id="c2275-112">Podrobnosti najdete v tématu [postupy: vytvoření přístup klíčů pro Windows Forms – ovládací prvky](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="c2275-112">For details, see [How to: Create Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span></span> <span data-ttu-id="c2275-113">Řídí vzhled text <xref:System.Windows.Forms.Control.Font%2A> vlastnost a <xref:System.Windows.Forms.ButtonBase.TextAlign%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c2275-113">The appearance of the text is controlled by the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.ButtonBase.TextAlign%2A> property.</span></span>  
  
 <span data-ttu-id="c2275-114"><xref:System.Windows.Forms.Button> Řízení lze také zobrazit obrázky pomocí <xref:System.Windows.Forms.ButtonBase.Image%2A> a <xref:System.Windows.Forms.ButtonBase.ImageList%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c2275-114">The <xref:System.Windows.Forms.Button> control can also display images using the <xref:System.Windows.Forms.ButtonBase.Image%2A> and <xref:System.Windows.Forms.ButtonBase.ImageList%2A> properties.</span></span> <span data-ttu-id="c2275-115">Další informace najdete v tématu [postupy: nastavení obrázek zobrazit pomocí ovládacího prvku Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md).</span><span class="sxs-lookup"><span data-stu-id="c2275-115">For more information, see [How to: Set the Image Displayed by a Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2275-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2275-116">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="c2275-117">Postupy: Reakce na kliknutí na tlačítko Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c2275-117">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="c2275-118">Metody výběru ovládacího prvku Windows Forms Button</span><span class="sxs-lookup"><span data-stu-id="c2275-118">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="c2275-119">Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Přijmout pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="c2275-119">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)  
 [<span data-ttu-id="c2275-120">Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Zrušit pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="c2275-120">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)  
 [<span data-ttu-id="c2275-121">Ovládací prvek Button</span><span class="sxs-lookup"><span data-stu-id="c2275-121">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
