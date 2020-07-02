---
title: 'Postupy: Vytvoření textového pole určeného jen pro čtení'
description: Přečtěte si informace o transformaci upravitelný model Windows Forms textového pole do textového pole model Windows Forms jen pro čtení.
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 5baa7c66d5f16560a4ea23861d563b099592957f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619361"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a><span data-ttu-id="7b25e-103">Postupy: Vytvoření textového pole určeného jen pro čtení (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="7b25e-103">How to: Create a Read-Only Text Box (Windows Forms)</span></span>

<span data-ttu-id="7b25e-104">Můžete transformovat upravitelný model Windows Forms textové pole na ovládací prvek jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="7b25e-104">You can transform an editable Windows Forms text box into a read-only control.</span></span> <span data-ttu-id="7b25e-105">Například v textovém poli se může zobrazit hodnota, která je obvykle upravována, ale nemusí být v současné době způsobena stavem aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b25e-105">For example, the text box may display a value that is usually edited but may not be currently, due to the state of the application.</span></span>

## <a name="to-create-a-read-only-text-box"></a><span data-ttu-id="7b25e-106">Vytvoření textového pole určeného jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7b25e-106">To create a read-only text box</span></span>

1. <span data-ttu-id="7b25e-107">Nastavte <xref:System.Windows.Forms.TextBox> vlastnost ovládacího prvku <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> na `true` .</span><span class="sxs-lookup"><span data-stu-id="7b25e-107">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property to `true`.</span></span> <span data-ttu-id="7b25e-108">Když je vlastnost nastavena na hodnotu `true` , uživatelé mohou v textovém poli přesouvat a zvýrazňovat text bez povolení změn.</span><span class="sxs-lookup"><span data-stu-id="7b25e-108">With the property set to `true`, users can still scroll and highlight text in a text box without allowing changes.</span></span> <span data-ttu-id="7b25e-109">Příkaz pro **kopírování** je funkční v textovém poli, ale příkazy pro **vyjmutí** a **vložení** nejsou.</span><span class="sxs-lookup"><span data-stu-id="7b25e-109">A **Copy** command is functional in a text box, but **Cut** and **Paste** commands are not.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7b25e-110"><xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>Vlastnost ovlivňuje pouze interakci uživatele v době běhu.</span><span class="sxs-lookup"><span data-stu-id="7b25e-110">The <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property only affects user interaction at run time.</span></span> <span data-ttu-id="7b25e-111">Změnou vlastnosti textového pole můžete i nadále měnit obsah textového pole programově za běhu <xref:System.Windows.Forms.TextBox.Text%2A> .</span><span class="sxs-lookup"><span data-stu-id="7b25e-111">You can still change text box contents programmatically at run time by changing the <xref:System.Windows.Forms.TextBox.Text%2A> property of the text box.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b25e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b25e-112">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="7b25e-113">Přehled ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="7b25e-113">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="7b25e-114">Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="7b25e-114">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="7b25e-115">Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="7b25e-115">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="7b25e-116">Postupy: Vkládání uvozovek do řetězce</span><span class="sxs-lookup"><span data-stu-id="7b25e-116">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="7b25e-117">Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="7b25e-117">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="7b25e-118">Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="7b25e-118">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="7b25e-119">TextBox – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="7b25e-119">TextBox Control</span></span>](textbox-control-windows-forms.md)
