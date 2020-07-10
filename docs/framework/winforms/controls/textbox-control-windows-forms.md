---
title: TextBox – ovládací prvek
description: Přečtěte si o různých aspektech ovládacího prvku TextBox model Windows Forms, včetně jeho použití k upravitelnému textu a jeho nastavení jen pro čtení.
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes
- TextBox control [Windows Forms]
ms.assetid: e5a06987-8aec-4271-b196-2245ba992d62
ms.openlocfilehash: 026f6d2653e41dabd3db7490660b6ce19846d397
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174442"
---
# <a name="textbox-control-windows-forms"></a><span data-ttu-id="81a8f-103">TextBox – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="81a8f-103">TextBox Control (Windows Forms)</span></span>
<span data-ttu-id="81a8f-104">Textová pole model Windows Forms slouží k získání vstupu od uživatele nebo k zobrazení textu.</span><span class="sxs-lookup"><span data-stu-id="81a8f-104">Windows Forms text boxes are used to get input from the user or to display text.</span></span> <span data-ttu-id="81a8f-105">Tento `TextBox` ovládací prvek se obecně používá pro upravitelný text, i když ho lze také nastavit jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="81a8f-105">The `TextBox` control is generally used for editable text, although it can also be made read-only.</span></span> <span data-ttu-id="81a8f-106">Textová pole mohou zobrazovat více řádků, zalamovat text podle velikosti ovládacího prvku a přidat základní formátování.</span><span class="sxs-lookup"><span data-stu-id="81a8f-106">Text boxes can display multiple lines, wrap text to the size of the control, and add basic formatting.</span></span> <span data-ttu-id="81a8f-107">`TextBox`Ovládací prvek umožňuje v ovládacím prvku zobrazit nebo zadat jeden formát textu.</span><span class="sxs-lookup"><span data-stu-id="81a8f-107">The `TextBox` control allows a single format for text displayed or entered in the control.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="81a8f-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="81a8f-108">In This Section</span></span>  
 [<span data-ttu-id="81a8f-109">Přehled ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="81a8f-109">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)  
 <span data-ttu-id="81a8f-110">Vysvětluje, co je tento ovládací prvek a jeho klíčové funkce a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="81a8f-110">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="81a8f-111">Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="81a8f-111">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 <span data-ttu-id="81a8f-112">Poskytuje pokyny pro určení, kde se bod vložení zobrazí, když ovládací prvek pro úpravy nejprve získá fokus.</span><span class="sxs-lookup"><span data-stu-id="81a8f-112">Gives directions for specifying where the insertion point appears when an edit control first gets the focus.</span></span>  
  
 [<span data-ttu-id="81a8f-113">Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="81a8f-113">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="81a8f-114">Vysvětluje, jak skrýt, co je zapsáno do textového pole.</span><span class="sxs-lookup"><span data-stu-id="81a8f-114">Explains how to conceal what is typed into a text box.</span></span>  
  
 [<span data-ttu-id="81a8f-115">Postupy: Vytvoření textového pole určeného jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="81a8f-115">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)  
 <span data-ttu-id="81a8f-116">Popisuje, jak zabránit změně obsahu textového pole.</span><span class="sxs-lookup"><span data-stu-id="81a8f-116">Describes how to prevent the contents of a text box from being changed.</span></span>  
  
 [<span data-ttu-id="81a8f-117">Postupy: Vkládání uvozovek do řetězce</span><span class="sxs-lookup"><span data-stu-id="81a8f-117">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 <span data-ttu-id="81a8f-118">Vysvětluje přidání uvozovek do řetězce v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="81a8f-118">Explains adding quotation marks to a string in a text box.</span></span>  
  
 [<span data-ttu-id="81a8f-119">Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="81a8f-119">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="81a8f-120">Vysvětluje, jak zvýraznit text v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="81a8f-120">Explains how to highlight text in a text box.</span></span>  
  
 [<span data-ttu-id="81a8f-121">Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="81a8f-121">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="81a8f-122">Popisuje, jak nastavit procházení textového pole.</span><span class="sxs-lookup"><span data-stu-id="81a8f-122">Describes how to make a text box scrollable.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="81a8f-123">Reference</span><span class="sxs-lookup"><span data-stu-id="81a8f-123">Reference</span></span>  
 <span data-ttu-id="81a8f-124">Třída <xref:System.Windows.Forms.TextBox></span><span class="sxs-lookup"><span data-stu-id="81a8f-124"><xref:System.Windows.Forms.TextBox> class</span></span>  
 <span data-ttu-id="81a8f-125">Popisuje tuto třídu a má odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="81a8f-125">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="81a8f-126">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="81a8f-126">Related Sections</span></span>  
 [<span data-ttu-id="81a8f-127">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="81a8f-127">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="81a8f-128">Obsahuje úplný seznam model Windows Formsch ovládacích prvků s odkazy na informace o jejich použití.</span><span class="sxs-lookup"><span data-stu-id="81a8f-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
