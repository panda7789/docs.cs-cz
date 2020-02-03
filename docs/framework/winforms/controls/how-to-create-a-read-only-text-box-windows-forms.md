---
title: 'Postupy: Vytvoření textového pole určeného jen pro čtení'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 17ae9524009c687cd62fb315f842e188e120ac68
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731268"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a><span data-ttu-id="56301-102">Postupy: Vytvoření textového pole určeného jen pro čtení (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="56301-102">How to: Create a Read-Only Text Box (Windows Forms)</span></span>

<span data-ttu-id="56301-103">Můžete transformovat upravitelný model Windows Forms textové pole na ovládací prvek jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="56301-103">You can transform an editable Windows Forms text box into a read-only control.</span></span> <span data-ttu-id="56301-104">Například v textovém poli se může zobrazit hodnota, která je obvykle upravována, ale nemusí být v současné době způsobena stavem aplikace.</span><span class="sxs-lookup"><span data-stu-id="56301-104">For example, the text box may display a value that is usually edited but may not be currently, due to the state of the application.</span></span>

## <a name="to-create-a-read-only-text-box"></a><span data-ttu-id="56301-105">Vytvoření textového pole určeného jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="56301-105">To create a read-only text box</span></span>

1. <span data-ttu-id="56301-106">Nastavte vlastnost <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> <xref:System.Windows.Forms.TextBox>ho ovládacího prvku na hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="56301-106">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property to `true`.</span></span> <span data-ttu-id="56301-107">Když je vlastnost nastavená na `true`, můžou uživatelé pořád přesouvat a zvýrazňovat text v textovém poli bez povolení změn.</span><span class="sxs-lookup"><span data-stu-id="56301-107">With the property set to `true`, users can still scroll and highlight text in a text box without allowing changes.</span></span> <span data-ttu-id="56301-108">Příkaz pro **kopírování** je funkční v textovém poli, ale příkazy pro **vyjmutí** a **vložení** nejsou.</span><span class="sxs-lookup"><span data-stu-id="56301-108">A **Copy** command is functional in a text box, but **Cut** and **Paste** commands are not.</span></span>

    > [!NOTE]
    > <span data-ttu-id="56301-109">Vlastnost <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> má vliv na interakci uživatele v době běhu.</span><span class="sxs-lookup"><span data-stu-id="56301-109">The <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property only affects user interaction at run time.</span></span> <span data-ttu-id="56301-110">Změnou vlastnosti <xref:System.Windows.Forms.TextBox.Text%2A> v textovém poli můžete i nadále měnit obsah textového pole programově v době běhu.</span><span class="sxs-lookup"><span data-stu-id="56301-110">You can still change text box contents programmatically at run time by changing the <xref:System.Windows.Forms.TextBox.Text%2A> property of the text box.</span></span>

## <a name="see-also"></a><span data-ttu-id="56301-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="56301-111">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="56301-112">Přehled ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="56301-112">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="56301-113">Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="56301-113">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="56301-114">Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="56301-114">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="56301-115">Postupy: Vkládání uvozovek do řetězce</span><span class="sxs-lookup"><span data-stu-id="56301-115">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="56301-116">Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="56301-116">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="56301-117">Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="56301-117">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="56301-118">Ovládací prvek TextBox</span><span class="sxs-lookup"><span data-stu-id="56301-118">TextBox Control</span></span>](textbox-control-windows-forms.md)
