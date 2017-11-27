---
title: "TextBox – ovládací prvek (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text boxes
- TextBox control [Windows Forms]
ms.assetid: e5a06987-8aec-4271-b196-2245ba992d62
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4800b06b5d0bbc5ce51d7cf00798ca98ef8bf656
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="textbox-control-windows-forms"></a><span data-ttu-id="934b4-102">TextBox – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="934b4-102">TextBox Control (Windows Forms)</span></span>
<span data-ttu-id="934b4-103">Windows Forms textová pole se používají k získání vstup od uživatele nebo k zobrazení textu.</span><span class="sxs-lookup"><span data-stu-id="934b4-103">Windows Forms text boxes are used to get input from the user or to display text.</span></span> <span data-ttu-id="934b4-104">`TextBox` Řízení se obecně používají pro upravovat text, i když ho můžete také provést jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="934b4-104">The `TextBox` control is generally used for editable text, although it can also be made read-only.</span></span> <span data-ttu-id="934b4-105">Textová pole můžete zobrazit více řádků, zalomení textu velikosti ovládacího prvku a přidat základní formátování.</span><span class="sxs-lookup"><span data-stu-id="934b4-105">Text boxes can display multiple lines, wrap text to the size of the control, and add basic formatting.</span></span> <span data-ttu-id="934b4-106">`TextBox` Řízení umožňuje formát pro text zobrazuje nebo je zadaný v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="934b4-106">The `TextBox` control allows a single format for text displayed or entered in the control.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="934b4-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="934b4-107">In This Section</span></span>  
 [<span data-ttu-id="934b4-108">Přehled ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="934b4-108">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 <span data-ttu-id="934b4-109">Vysvětluje, co je tento ovládací prvek a jeho klíčové funkce a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="934b4-109">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="934b4-110">Postupy: řízení bodu pro vkládání v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="934b4-110">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 <span data-ttu-id="934b4-111">Poskytuje pokyny pro určení, kde kurzoru se zobrazí při prvním vyvolání fokus ovládací prvek upravit.</span><span class="sxs-lookup"><span data-stu-id="934b4-111">Gives directions for specifying where the insertion point appears when an edit control first gets the focus.</span></span>  
  
 [<span data-ttu-id="934b4-112">Postupy: vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="934b4-112">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="934b4-113">Vysvětluje, jak skrýt, co je zadán do textového pole.</span><span class="sxs-lookup"><span data-stu-id="934b4-113">Explains how to conceal what is typed into a text box.</span></span>  
  
 [<span data-ttu-id="934b4-114">Postupy: vytvoření jen pro čtení textového pole</span><span class="sxs-lookup"><span data-stu-id="934b4-114">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 <span data-ttu-id="934b4-115">Popisuje, jak zabránit změnám obsah textové pole.</span><span class="sxs-lookup"><span data-stu-id="934b4-115">Describes how to prevent the contents of a text box from being changed.</span></span>  
  
 [<span data-ttu-id="934b4-116">Postupy: vkládání uvozovek do řetězce</span><span class="sxs-lookup"><span data-stu-id="934b4-116">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 <span data-ttu-id="934b4-117">Popisuje přidání uvozovky na řetězec v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="934b4-117">Explains adding quotation marks to a string in a text box.</span></span>  
  
 [<span data-ttu-id="934b4-118">Postupy: Výběr textu v systému Windows Forms TextBox – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="934b4-118">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="934b4-119">Vysvětluje, jak zvýraznění textu v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="934b4-119">Explains how to highlight text in a text box.</span></span>  
  
 [<span data-ttu-id="934b4-120">Postupy: zobrazení více řádků v systému Windows Forms TextBox – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="934b4-120">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="934b4-121">Popisuje postup nastavení posuvného textového pole.</span><span class="sxs-lookup"><span data-stu-id="934b4-121">Describes how to make a text box scrollable.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="934b4-122">Odkaz</span><span class="sxs-lookup"><span data-stu-id="934b4-122">Reference</span></span>  
 <span data-ttu-id="934b4-123"><xref:System.Windows.Forms.TextBox>– Třída</span><span class="sxs-lookup"><span data-stu-id="934b4-123"><xref:System.Windows.Forms.TextBox> class</span></span>  
 <span data-ttu-id="934b4-124">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="934b4-124">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="934b4-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="934b4-125">Related Sections</span></span>  
 [<span data-ttu-id="934b4-126">Ovládací prvky používané ve formulářích Windows</span><span class="sxs-lookup"><span data-stu-id="934b4-126">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="934b4-127">Poskytuje úplný seznam Windows Forms – ovládací prvky, odkazy na informace o jejich používání.</span><span class="sxs-lookup"><span data-stu-id="934b4-127">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
