---
title: TextBox – ovládací prvek (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes
- TextBox control [Windows Forms]
ms.assetid: e5a06987-8aec-4271-b196-2245ba992d62
ms.openlocfilehash: b687f83562b3a6f9dd5993f2af1c55ffe6dc8042
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716310"
---
# <a name="textbox-control-windows-forms"></a><span data-ttu-id="1e9ad-102">TextBox – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="1e9ad-102">TextBox Control (Windows Forms)</span></span>
<span data-ttu-id="1e9ad-103">Windows Forms textová pole se používají k získání vstupy od uživatele nebo k zobrazení textu.</span><span class="sxs-lookup"><span data-stu-id="1e9ad-103">Windows Forms text boxes are used to get input from the user or to display text.</span></span> <span data-ttu-id="1e9ad-104">`TextBox` Ovládací prvek se obecně používají pro upravitelný text, i když ji můžete také nastavit jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="1e9ad-104">The `TextBox` control is generally used for editable text, although it can also be made read-only.</span></span> <span data-ttu-id="1e9ad-105">Textová pole můžete zobrazit více řádků, zalamovat text, který má velikost ovládacího prvku a přidat základní formátování.</span><span class="sxs-lookup"><span data-stu-id="1e9ad-105">Text boxes can display multiple lines, wrap text to the size of the control, and add basic formatting.</span></span> <span data-ttu-id="1e9ad-106">`TextBox` Ovládací prvek umožňuje jeden formát pro text zobrazuje nebo je zadaný v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="1e9ad-106">The `TextBox` control allows a single format for text displayed or entered in the control.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1e9ad-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1e9ad-107">In This Section</span></span>  
 [<span data-ttu-id="1e9ad-108">Přehled ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="1e9ad-108">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)  
 <span data-ttu-id="1e9ad-109">Vysvětluje, co je tento ovládací prvek a jeho klíčové funkce a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1e9ad-109">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="1e9ad-110">Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="1e9ad-110">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 <span data-ttu-id="1e9ad-111">Poskytuje pokyny pro určení, kde se zobrazí kurzor, když ovládací prvek úprav nejprve získá fokus.</span><span class="sxs-lookup"><span data-stu-id="1e9ad-111">Gives directions for specifying where the insertion point appears when an edit control first gets the focus.</span></span>  
  
 [<span data-ttu-id="1e9ad-112">Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="1e9ad-112">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="1e9ad-113">Vysvětluje, jak skrýt, co je zadán do textového pole.</span><span class="sxs-lookup"><span data-stu-id="1e9ad-113">Explains how to conceal what is typed into a text box.</span></span>  
  
 [<span data-ttu-id="1e9ad-114">Postupy: Vytvoření pole jen pro čtení textu</span><span class="sxs-lookup"><span data-stu-id="1e9ad-114">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)  
 <span data-ttu-id="1e9ad-115">Popisuje, jak zabránit mění obsah textového pole.</span><span class="sxs-lookup"><span data-stu-id="1e9ad-115">Describes how to prevent the contents of a text box from being changed.</span></span>  
  
 [<span data-ttu-id="1e9ad-116">Postupy: Vkládání uvozovek do řetězce</span><span class="sxs-lookup"><span data-stu-id="1e9ad-116">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 <span data-ttu-id="1e9ad-117">Popisuje přidání uvozovek na řetězec v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="1e9ad-117">Explains adding quotation marks to a string in a text box.</span></span>  
  
 [<span data-ttu-id="1e9ad-118">Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="1e9ad-118">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="1e9ad-119">Vysvětluje, jak zvýraznění textu v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="1e9ad-119">Explains how to highlight text in a text box.</span></span>  
  
 [<span data-ttu-id="1e9ad-120">Postupy: Zobrazit více řádků v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="1e9ad-120">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="1e9ad-121">Popisuje, jak provést posuvný textové pole.</span><span class="sxs-lookup"><span data-stu-id="1e9ad-121">Describes how to make a text box scrollable.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1e9ad-122">Odkaz</span><span class="sxs-lookup"><span data-stu-id="1e9ad-122">Reference</span></span>  
 <span data-ttu-id="1e9ad-123"><xref:System.Windows.Forms.TextBox> Třída</span><span class="sxs-lookup"><span data-stu-id="1e9ad-123"><xref:System.Windows.Forms.TextBox> class</span></span>  
 <span data-ttu-id="1e9ad-124">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="1e9ad-124">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1e9ad-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="1e9ad-125">Related Sections</span></span>  
 [<span data-ttu-id="1e9ad-126">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1e9ad-126">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="1e9ad-127">Obsahuje úplný seznam všech ovládacích prvcích Windows Forms, s odkazy na informace o jejich použití.</span><span class="sxs-lookup"><span data-stu-id="1e9ad-127">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
