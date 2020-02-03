---
title: Vytváření přístupových klíčů pomocí ovládacích prvků popisek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- Label control [Windows Forms], creating access keys
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- Windows Forms controls, access keys
- UseMnemonic property [Windows Forms], Label control
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
ms.assetid: 5ee8f823-80be-4a4f-96a4-412671e2e306
ms.openlocfilehash: 800afc03e71435e2721456b93bb9704af01f714a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731047"
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a><span data-ttu-id="08408-102">Postupy: Vytváření přístupových klíčů pomocí ovládacích prvků Windows Forms Label</span><span class="sxs-lookup"><span data-stu-id="08408-102">How to: Create Access Keys with Windows Forms Label Controls</span></span>
<span data-ttu-id="08408-103">Ovládací prvky model Windows Forms <xref:System.Windows.Forms.Label> lze použít k definování přístupových klíčů pro jiné ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="08408-103">Windows Forms <xref:System.Windows.Forms.Label> controls can be used to define access keys for other controls.</span></span> <span data-ttu-id="08408-104">Při definování přístupového klíče v ovládacím prvku popisek může uživatel stisknout klávesu ALT a znak, který určíte, chcete-li přesunout fokus na ovládací prvek, který následuje v pořadí prvků.</span><span class="sxs-lookup"><span data-stu-id="08408-104">When you define an access key in a label control, the user can press the ALT key plus the character you designate to move the focus to the control that follows it in the tab order.</span></span> <span data-ttu-id="08408-105">Vzhledem k tomu, že popisky nemohou získat fokus, fokus se automaticky přesune na další ovládací prvek v pořadí prvků.</span><span class="sxs-lookup"><span data-stu-id="08408-105">Because labels cannot receive focus, focus automatically moves to the next control in the tab order.</span></span> <span data-ttu-id="08408-106">Tento postup slouží k přiřazení přístupových kláves k textovým polím, polím se seznamem, seznamům a datovým mřížkám.</span><span class="sxs-lookup"><span data-stu-id="08408-106">Use this technique to assign access keys to text boxes, combo boxes, list boxes, and data grids.</span></span>  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a><span data-ttu-id="08408-107">Přiřazení přístupového klíče k ovládacímu prvku s popiskem</span><span class="sxs-lookup"><span data-stu-id="08408-107">To assign an access key to a control with a label</span></span>  
  
1. <span data-ttu-id="08408-108">Nejprve nakreslete popisek a potom nakreslete druhý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="08408-108">Draw the label first, and then draw the other control.</span></span>  
  
     <span data-ttu-id="08408-109">-nebo-</span><span class="sxs-lookup"><span data-stu-id="08408-109">-or-</span></span>  
  
     <span data-ttu-id="08408-110">Nakreslete ovládací prvky v libovolném pořadí a nastavte vlastnost <xref:System.Windows.Forms.Control.TabIndex%2A> popisku na hodnotu menší, než je ten jiný ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="08408-110">Draw the controls in any order and set the <xref:System.Windows.Forms.Control.TabIndex%2A> property of the label to one less than the other control.</span></span>  
  
2. <span data-ttu-id="08408-111">Nastavte vlastnost <xref:System.Windows.Forms.Label.UseMnemonic%2A> popisku na hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="08408-111">Set the label's <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`.</span></span>  
  
3. <span data-ttu-id="08408-112">Pomocí ampersandu (&) ve vlastnosti <xref:System.Windows.Forms.Label.Text%2A> popisku přiřaďte přístupový klíč pro popisek.</span><span class="sxs-lookup"><span data-stu-id="08408-112">Use an ampersand (&) in the label's <xref:System.Windows.Forms.Label.Text%2A> property to assign the access key for the label.</span></span> <span data-ttu-id="08408-113">Další informace najdete v tématu [vytváření přístupových klíčů pro ovládací prvky model Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="08408-113">For more information, see [Creating Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="08408-114">V ovládacím prvku popisek možná budete chtít zobrazit ampersandy namísto použití pro vytváření přístupových klíčů.</span><span class="sxs-lookup"><span data-stu-id="08408-114">You may want to display ampersands in a label control, rather than use them to create access keys.</span></span> <span data-ttu-id="08408-115">K této chybě může dojít, Pokud svážete ovládací prvek popisek s polem v sadě záznamů, kde data obsahují ampersandy.</span><span class="sxs-lookup"><span data-stu-id="08408-115">This may occur if you bind a label control to a field in a recordset where the data includes ampersands.</span></span> <span data-ttu-id="08408-116">Chcete-li v ovládacím prvku popisek zobrazit ampersandy, nastavte vlastnost <xref:System.Windows.Forms.Label.UseMnemonic%2A> na hodnotu `false`.</span><span class="sxs-lookup"><span data-stu-id="08408-116">To display ampersands in a label control, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `false`.</span></span> <span data-ttu-id="08408-117">Pokud chcete zobrazit ampersandy a také přístupový klíč, nastavte vlastnost <xref:System.Windows.Forms.Label.UseMnemonic%2A> na `true` a označte přístupový klíč jedním ampersandem (&) a ampersandem, který se má zobrazit dvěma ampersandy.</span><span class="sxs-lookup"><span data-stu-id="08408-117">If you wish to display ampersands and also have an access key, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true` and indicate the access key with one ampersand (&) and the ampersand to display with two ampersands.</span></span>  
  
    ```vb  
    Label1.UseMnemonic = True  
    Label1.Text = "&Print"  
    Label2.UseMnemonic = True  
    Label2.Text = "&Copy && Paste"  
    ```  
  
    ```csharp  
    label1.UseMnemonic = true;  
    label1.Text = "&Print";  
    label2.UseMnemonic = true;  
    label2.Text = "&Copy && Paste";  
    ```  
  
    ```cpp  
    label1->UseMnemonic = true;  
    label1->Text = "&Print";  
    label2->UseMnemonic = true;  
    label2->Text = "&Copy && Paste";  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="08408-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="08408-118">See also</span></span>

- [<span data-ttu-id="08408-119">Postupy: Určení velikosti ovládacího prvku Windows Forms Label k zobrazení jeho obsahu</span><span class="sxs-lookup"><span data-stu-id="08408-119">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [<span data-ttu-id="08408-120">Přehled ovládacího prvku Label</span><span class="sxs-lookup"><span data-stu-id="08408-120">Label Control Overview</span></span>](label-control-overview-windows-forms.md)
- [<span data-ttu-id="08408-121">Ovládací prvek Label</span><span class="sxs-lookup"><span data-stu-id="08408-121">Label Control</span></span>](label-control-windows-forms.md)
