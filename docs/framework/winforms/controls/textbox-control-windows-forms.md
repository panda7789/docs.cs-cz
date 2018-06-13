---
title: TextBox – ovládací prvek (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes
- TextBox control [Windows Forms]
ms.assetid: e5a06987-8aec-4271-b196-2245ba992d62
ms.openlocfilehash: fe5bafa5c21a3946df33821d358185f3aba67222
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536251"
---
# <a name="textbox-control-windows-forms"></a><span data-ttu-id="80fe6-102">TextBox – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="80fe6-102">TextBox Control (Windows Forms)</span></span>
<span data-ttu-id="80fe6-103">Windows Forms textová pole se používají k získání vstup od uživatele nebo k zobrazení textu.</span><span class="sxs-lookup"><span data-stu-id="80fe6-103">Windows Forms text boxes are used to get input from the user or to display text.</span></span> <span data-ttu-id="80fe6-104">`TextBox` Řízení se obecně používají pro upravovat text, i když ho můžete také provést jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="80fe6-104">The `TextBox` control is generally used for editable text, although it can also be made read-only.</span></span> <span data-ttu-id="80fe6-105">Textová pole můžete zobrazit více řádků, zalomení textu velikosti ovládacího prvku a přidat základní formátování.</span><span class="sxs-lookup"><span data-stu-id="80fe6-105">Text boxes can display multiple lines, wrap text to the size of the control, and add basic formatting.</span></span> <span data-ttu-id="80fe6-106">`TextBox` Řízení umožňuje formát pro text zobrazuje nebo je zadaný v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="80fe6-106">The `TextBox` control allows a single format for text displayed or entered in the control.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="80fe6-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="80fe6-107">In This Section</span></span>  
 [<span data-ttu-id="80fe6-108">Přehled ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="80fe6-108">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 <span data-ttu-id="80fe6-109">Vysvětluje, co je tento ovládací prvek a jeho klíčové funkce a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="80fe6-109">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="80fe6-110">Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="80fe6-110">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 <span data-ttu-id="80fe6-111">Poskytuje pokyny pro určení, kde kurzoru se zobrazí při prvním vyvolání fokus ovládací prvek upravit.</span><span class="sxs-lookup"><span data-stu-id="80fe6-111">Gives directions for specifying where the insertion point appears when an edit control first gets the focus.</span></span>  
  
 [<span data-ttu-id="80fe6-112">Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="80fe6-112">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="80fe6-113">Vysvětluje, jak skrýt, co je zadán do textového pole.</span><span class="sxs-lookup"><span data-stu-id="80fe6-113">Explains how to conceal what is typed into a text box.</span></span>  
  
 [<span data-ttu-id="80fe6-114">Postupy: Vytvoření textového pole určeného jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="80fe6-114">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 <span data-ttu-id="80fe6-115">Popisuje, jak zabránit změnám obsah textové pole.</span><span class="sxs-lookup"><span data-stu-id="80fe6-115">Describes how to prevent the contents of a text box from being changed.</span></span>  
  
 [<span data-ttu-id="80fe6-116">Postupy: Vkládání uvozovek do řetězce</span><span class="sxs-lookup"><span data-stu-id="80fe6-116">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 <span data-ttu-id="80fe6-117">Popisuje přidání uvozovky na řetězec v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="80fe6-117">Explains adding quotation marks to a string in a text box.</span></span>  
  
 [<span data-ttu-id="80fe6-118">Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="80fe6-118">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="80fe6-119">Vysvětluje, jak zvýraznění textu v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="80fe6-119">Explains how to highlight text in a text box.</span></span>  
  
 [<span data-ttu-id="80fe6-120">Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="80fe6-120">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="80fe6-121">Popisuje postup nastavení posuvného textového pole.</span><span class="sxs-lookup"><span data-stu-id="80fe6-121">Describes how to make a text box scrollable.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="80fe6-122">Odkaz</span><span class="sxs-lookup"><span data-stu-id="80fe6-122">Reference</span></span>  
 <span data-ttu-id="80fe6-123"><xref:System.Windows.Forms.TextBox> – Třída</span><span class="sxs-lookup"><span data-stu-id="80fe6-123"><xref:System.Windows.Forms.TextBox> class</span></span>  
 <span data-ttu-id="80fe6-124">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="80fe6-124">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="80fe6-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="80fe6-125">Related Sections</span></span>  
 [<span data-ttu-id="80fe6-126">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="80fe6-126">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="80fe6-127">Poskytuje úplný seznam Windows Forms – ovládací prvky, odkazy na informace o jejich používání.</span><span class="sxs-lookup"><span data-stu-id="80fe6-127">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
