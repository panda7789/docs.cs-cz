---
title: "Postupy: Vytváření přístupových klíčů pomocí ovládacích prvků Windows Forms Label"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4ad6cd99a6399adea2e69cbf844b9f134d2e592e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a><span data-ttu-id="78b94-102">Postupy: Vytváření přístupových klíčů pomocí ovládacích prvků Windows Forms Label</span><span class="sxs-lookup"><span data-stu-id="78b94-102">How to: Create Access Keys with Windows Forms Label Controls</span></span>
<span data-ttu-id="78b94-103">Windows Forms <xref:System.Windows.Forms.Label> ovládací prvky můžete použít k definování přístupové klíče pro další ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="78b94-103">Windows Forms <xref:System.Windows.Forms.Label> controls can be used to define access keys for other controls.</span></span> <span data-ttu-id="78b94-104">Když definujete přístupový klíč v ovládacím prvku popisek, může uživatel stisknout klávesy ALT a znak, který určíte přesunout fokus na ovládací prvek, který následuje v pořadí.</span><span class="sxs-lookup"><span data-stu-id="78b94-104">When you define an access key in a label control, the user can press the ALT key plus the character you designate to move the focus to the control that follows it in the tab order.</span></span> <span data-ttu-id="78b94-105">Protože popisky nemůže přijmout fokus, automaticky aktivuje na další ovládací prvek v pořadí.</span><span class="sxs-lookup"><span data-stu-id="78b94-105">Because labels cannot receive focus, focus automatically moves to the next control in the tab order.</span></span> <span data-ttu-id="78b94-106">Tento postup slouží k přiřazení přístupových klíčů k textová pole, pole se seznamem, seznamy a datové mřížky.</span><span class="sxs-lookup"><span data-stu-id="78b94-106">Use this technique to assign access keys to text boxes, combo boxes, list boxes, and data grids.</span></span>  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a><span data-ttu-id="78b94-107">Přiřadit přístupový klíč do ovládacího prvku s popiskem</span><span class="sxs-lookup"><span data-stu-id="78b94-107">To assign an access key to a control with a label</span></span>  
  
1.  <span data-ttu-id="78b94-108">Nejprve kreslení štítek a potom kreslení další ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="78b94-108">Draw the label first, and then draw the other control.</span></span>  
  
     <span data-ttu-id="78b94-109">-nebo-</span><span class="sxs-lookup"><span data-stu-id="78b94-109">-or-</span></span>  
  
     <span data-ttu-id="78b94-110">Vykreslení ovládacích prvků v libovolném pořadí a nastavte <xref:System.Windows.Forms.Control.TabIndex%2A> vlastnost popisku k jednomu menší než ostatní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="78b94-110">Draw the controls in any order and set the <xref:System.Windows.Forms.Control.TabIndex%2A> property of the label to one less than the other control.</span></span>  
  
2.  <span data-ttu-id="78b94-111">Nastavte jeho <xref:System.Windows.Forms.Label.UseMnemonic%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="78b94-111">Set the label's <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`.</span></span>  
  
3.  <span data-ttu-id="78b94-112">Použít znak ampersand (&) v atributu label <xref:System.Windows.Forms.Label.Text%2A> vlastnost přiřadit přístupový klíč pro popisek.</span><span class="sxs-lookup"><span data-stu-id="78b94-112">Use an ampersand (&) in the label's <xref:System.Windows.Forms.Label.Text%2A> property to assign the access key for the label.</span></span> <span data-ttu-id="78b94-113">Další informace najdete v tématu [vytváření přístup klíčů pro Windows Forms – ovládací prvky](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="78b94-113">For more information, see [Creating Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="78b94-114">Můžete do zobrazení ampersandy v ovládacím prvku popisek, nikoli je použít k vytvoření přístupové klíče.</span><span class="sxs-lookup"><span data-stu-id="78b94-114">You may want to display ampersands in a label control, rather than use them to create access keys.</span></span> <span data-ttu-id="78b94-115">To může dojít, pokud vytvoření vazby ovládací prvek popisek na pole v sadě záznamů, kde data obsahují tyto znaky.</span><span class="sxs-lookup"><span data-stu-id="78b94-115">This may occur if you bind a label control to a field in a recordset where the data includes ampersands.</span></span> <span data-ttu-id="78b94-116">Chcete-li zobrazit tyto znaky v ovládacím prvku popisek, nastavte <xref:System.Windows.Forms.Label.UseMnemonic%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="78b94-116">To display ampersands in a label control, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `false`.</span></span> <span data-ttu-id="78b94-117">Pokud chcete zobrazit tyto znaky a také mít přístupový klíč, nastavte <xref:System.Windows.Forms.Label.UseMnemonic%2A> vlastnost, která má `true` a uvést přístupového klíče s jeden ampersand (&) a ampersand zobrazíte s dva tyto znaky.</span><span class="sxs-lookup"><span data-stu-id="78b94-117">If you wish to display ampersands and also have an access key, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true` and indicate the access key with one ampersand (&) and the ampersand to display with two ampersands.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="78b94-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="78b94-118">See Also</span></span>  
 [<span data-ttu-id="78b94-119">Postupy: velikost Windows Forms – ovládací prvek popisek podle obsahu</span><span class="sxs-lookup"><span data-stu-id="78b94-119">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>](../../../../docs/framework/winforms/controls/how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)  
 [<span data-ttu-id="78b94-120">Přehled ovládacího prvku popisek</span><span class="sxs-lookup"><span data-stu-id="78b94-120">Label Control Overview</span></span>](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [<span data-ttu-id="78b94-121">Popisek – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="78b94-121">Label Control</span></span>](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
