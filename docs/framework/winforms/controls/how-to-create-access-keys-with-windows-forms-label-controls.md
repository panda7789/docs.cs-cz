---
title: 'Postupy: Vytváření přístupových klíčů pomocí ovládacích prvků Windows Forms Label'
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
ms.openlocfilehash: ffe4bf6fb29e82b04938e2ba9a2d9d21e5eabcde
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747105"
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a><span data-ttu-id="5a93d-102">Postupy: Vytváření přístupových klíčů pomocí ovládacích prvků Windows Forms Label</span><span class="sxs-lookup"><span data-stu-id="5a93d-102">How to: Create Access Keys with Windows Forms Label Controls</span></span>
<span data-ttu-id="5a93d-103">Windows Forms <xref:System.Windows.Forms.Label> ovládací prvky lze použít k definování přístupové klíče pro ostatní ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="5a93d-103">Windows Forms <xref:System.Windows.Forms.Label> controls can be used to define access keys for other controls.</span></span> <span data-ttu-id="5a93d-104">Při definování přístupový klíč v ovládacím prvku popisek, může uživatel stisknout klávesy ALT a znak, který určíte přesunout fokus na ovládací prvek, který následuje v pořadí.</span><span class="sxs-lookup"><span data-stu-id="5a93d-104">When you define an access key in a label control, the user can press the ALT key plus the character you designate to move the focus to the control that follows it in the tab order.</span></span> <span data-ttu-id="5a93d-105">Protože popisků nemůže být vybrán, automaticky aktivuje další ovládací prvek v pořadí karet.</span><span class="sxs-lookup"><span data-stu-id="5a93d-105">Because labels cannot receive focus, focus automatically moves to the next control in the tab order.</span></span> <span data-ttu-id="5a93d-106">Tento postup použijte k přiřazení přístupových klíčů a textová pole, pole se seznamem, pole se seznamem datových mřížkách.</span><span class="sxs-lookup"><span data-stu-id="5a93d-106">Use this technique to assign access keys to text boxes, combo boxes, list boxes, and data grids.</span></span>  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a><span data-ttu-id="5a93d-107">K přiřazení přístupový klíč k ovládacímu prvku s popiskem</span><span class="sxs-lookup"><span data-stu-id="5a93d-107">To assign an access key to a control with a label</span></span>  
  
1. <span data-ttu-id="5a93d-108">Nejprve vykreslení popisku a nakreslete jiný ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="5a93d-108">Draw the label first, and then draw the other control.</span></span>  
  
     <span data-ttu-id="5a93d-109">-nebo-</span><span class="sxs-lookup"><span data-stu-id="5a93d-109">-or-</span></span>  
  
     <span data-ttu-id="5a93d-110">Vykreslení ovládacích prvků v libovolném pořadí a nastavit <xref:System.Windows.Forms.Control.TabIndex%2A> popisku na jeden menší než druhý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="5a93d-110">Draw the controls in any order and set the <xref:System.Windows.Forms.Control.TabIndex%2A> property of the label to one less than the other control.</span></span>  
  
2. <span data-ttu-id="5a93d-111">Nastavte jeho <xref:System.Windows.Forms.Label.UseMnemonic%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="5a93d-111">Set the label's <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`.</span></span>  
  
3. <span data-ttu-id="5a93d-112">Použít znak ampersand (&) v popisku <xref:System.Windows.Forms.Label.Text%2A> vlastnost má být přiřazena přístupový klíč pro popisek.</span><span class="sxs-lookup"><span data-stu-id="5a93d-112">Use an ampersand (&) in the label's <xref:System.Windows.Forms.Label.Text%2A> property to assign the access key for the label.</span></span> <span data-ttu-id="5a93d-113">Další informace najdete v tématu [vytváření klíčů pro Windows Forms řízení přístupu](how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="5a93d-113">For more information, see [Creating Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5a93d-114">Můžete chtít zobrazit tyto znaky v ovládacím prvku popisek, nikoli jejich používání při vytváření přístupových klíčů.</span><span class="sxs-lookup"><span data-stu-id="5a93d-114">You may want to display ampersands in a label control, rather than use them to create access keys.</span></span> <span data-ttu-id="5a93d-115">To může dojít, pokud vytvoření vazby ovládacího prvku popisku na pole v sadě záznamů, pokud data obsahují tyto znaky.</span><span class="sxs-lookup"><span data-stu-id="5a93d-115">This may occur if you bind a label control to a field in a recordset where the data includes ampersands.</span></span> <span data-ttu-id="5a93d-116">Chcete-li tyto znaky zobrazit v ovládacím prvku popisek, nastavte <xref:System.Windows.Forms.Label.UseMnemonic%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="5a93d-116">To display ampersands in a label control, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `false`.</span></span> <span data-ttu-id="5a93d-117">Pokud si chcete zobrazit tyto znaky a mít taky přístupový kód, nastavte <xref:System.Windows.Forms.Label.UseMnemonic%2A> vlastnost `true` a přístupový klíč se jeden znak ampersand (&) a ampersand k zobrazení mají tyto dva znaky.</span><span class="sxs-lookup"><span data-stu-id="5a93d-117">If you wish to display ampersands and also have an access key, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true` and indicate the access key with one ampersand (&) and the ampersand to display with two ampersands.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5a93d-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a93d-118">See also</span></span>

- [<span data-ttu-id="5a93d-119">Postupy: Velikost ovládacího prvku Windows Forms Label k zobrazení jeho obsahu</span><span class="sxs-lookup"><span data-stu-id="5a93d-119">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [<span data-ttu-id="5a93d-120">Přehled ovládacího prvku Label</span><span class="sxs-lookup"><span data-stu-id="5a93d-120">Label Control Overview</span></span>](label-control-overview-windows-forms.md)
- [<span data-ttu-id="5a93d-121">Ovládací prvek Label</span><span class="sxs-lookup"><span data-stu-id="5a93d-121">Label Control</span></span>](label-control-windows-forms.md)
