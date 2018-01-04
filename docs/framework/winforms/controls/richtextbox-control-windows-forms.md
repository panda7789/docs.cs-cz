---
title: "RichTextBox – ovládací prvek (Windows Forms)"
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
- RichTextBox control [Windows Forms]
- rich edit controls
ms.assetid: 3225f2ef-c6d9-4bd4-9d3e-2219e58edbf2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4325fd3eb2e3d7179ddb5270d073c7ba5f0f383f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="richtextbox-control-windows-forms"></a><span data-ttu-id="39a1f-102">RichTextBox – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="39a1f-102">RichTextBox Control (Windows Forms)</span></span>
<span data-ttu-id="39a1f-103">Windows Forms `RichTextBox` řízení se používá k zobrazení, zadávání a manipulace s nimi formátování textu.</span><span class="sxs-lookup"><span data-stu-id="39a1f-103">The Windows Forms `RichTextBox` control is used for displaying, entering, and manipulating text with formatting.</span></span> <span data-ttu-id="39a1f-104">`RichTextBox` Ovládací prvek provádí všechno, co <xref:System.Windows.Forms.TextBox> ovládací prvek provádí, ale můžete také zobrazit písma, barvy a odkazy; zatížení text a vložené obrázky ze souboru; zpět nebo opakování operace; úprav a najít zadané znaky.</span><span class="sxs-lookup"><span data-stu-id="39a1f-104">The `RichTextBox` control does everything the <xref:System.Windows.Forms.TextBox> control does, but it can also display fonts, colors, and links; load text and embedded images from a file; undo and redo editing operations; and find specified characters.</span></span> <span data-ttu-id="39a1f-105">`RichTextBox` Řízení se obvykle používá k poskytování manipulaci s textem a zobrazení funkce podobná zpracování textu aplikace, jako je například Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="39a1f-105">The `RichTextBox` control is typically used to provide text manipulation and display features similar to word processing applications such as Microsoft Word.</span></span> <span data-ttu-id="39a1f-106">Jako <xref:System.Windows.Forms.TextBox> ovládací prvek, `RichTextBox` ovládací prvek může zobrazovat posuvníky; ale na rozdíl od <xref:System.Windows.Forms.TextBox> řízení, ve výchozím nastavení zobrazí posuvníky vodorovného a svislého a má scrollbar další nastavení.</span><span class="sxs-lookup"><span data-stu-id="39a1f-106">Like the <xref:System.Windows.Forms.TextBox> control, the `RichTextBox` control can display scroll bars; but unlike the <xref:System.Windows.Forms.TextBox> control, it displays both horizontal and vertical scrollbars by default and has additional scrollbar settings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="39a1f-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="39a1f-107">In This Section</span></span>  
 [<span data-ttu-id="39a1f-108">Přehled ovládacího prvku RichTextBox</span><span class="sxs-lookup"><span data-stu-id="39a1f-108">RichTextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md)  
 <span data-ttu-id="39a1f-109">Představuje obecné koncepty `RichTextBox` řízení, které mohou uživatelé zadávat, zobrazit a upravit možnosti formátování textu.</span><span class="sxs-lookup"><span data-stu-id="39a1f-109">Introduces the general concepts of the `RichTextBox` control, which allows users to enter, display, and manipulate text with formatting options.</span></span>  
  
 [<span data-ttu-id="39a1f-110">Postupy: Určení momentu změny atributů formátování v ovládacím prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="39a1f-110">How to: Determine When Formatting Attributes Change in the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/determine-when-formatting-attributes-change-wf-richtextbox-control.md)  
 <span data-ttu-id="39a1f-111">Vysvětluje, jak můžete sledovat změny v písma a formátování odstavců v `RichTextBox` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="39a1f-111">Explains how to keep track of changes in font and paragraph formatting in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="39a1f-112">Postupy: Zobrazení posuvníků v ovládacím prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="39a1f-112">How to: Display Scroll Bars in the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="39a1f-113">Popisuje řadu možností, které jsou k dispozici pro posuvníků v `RichTextBox` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="39a1f-113">Describes the many choices available for scroll bars in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="39a1f-114">Postupy: Zobrazení webových odkazů pomocí ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="39a1f-114">How to: Display Web-Style Links with the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="39a1f-115">Vysvětluje, jak propojit webů z `RichTextBox` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="39a1f-115">Explains how to link to Web sites from the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="39a1f-116">Postupy: Povolení operací přetažení myší pomocí ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="39a1f-116">How to: Enable Drag-and-Drop Operations with the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/enable-drag-and-drop-operations-with-wf-richtextbox-control.md)  
 <span data-ttu-id="39a1f-117">Poskytuje pokyny pro přetažení myší data do `RichTextBox` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="39a1f-117">Provides instructions for dragging data into the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="39a1f-118">Postupy: Načtení souborů do ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="39a1f-118">How to: Load Files into the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-load-files-into-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="39a1f-119">Poskytuje pokyny pro načítání do existující soubor `RichTextBox` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="39a1f-119">Provides instructions for loading an existing file into the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="39a1f-120">Postupy: Ukládání souborů pomocí ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="39a1f-120">How to: Save Files with the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-save-files-with-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="39a1f-121">Poskytuje pokyny pro ukládání obsahu `RichTextBox` ovládacího prvku do souboru.</span><span class="sxs-lookup"><span data-stu-id="39a1f-121">Provides instructions for saving the contents of the `RichTextBox` control to a file.</span></span>  
  
 [<span data-ttu-id="39a1f-122">Postupy: Nastavení atributů písma pro ovládací prvek Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="39a1f-122">How to: Set Font Attributes for the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="39a1f-123">Popisuje, jak nastavit rodiny písem, velikost, stylu a barvy textu v `RichTextBox` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="39a1f-123">Describes how to set the font family, size, style, and color of text in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="39a1f-124">Postupy: Nastavení odsazení, předsazení a odstavců s odrážkami pomocí ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="39a1f-124">How to: Set Indents, Hanging Indents, and Bulleted Paragraphs with the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md)  
 <span data-ttu-id="39a1f-125">Popisuje způsob formátování odstavců v `RichTextBox` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="39a1f-125">Describes how to format paragraphs in the `RichTextBox` control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="39a1f-126">Odkaz</span><span class="sxs-lookup"><span data-stu-id="39a1f-126">Reference</span></span>  
 <span data-ttu-id="39a1f-127"><xref:System.Windows.Forms.RichTextBox>– Třída</span><span class="sxs-lookup"><span data-stu-id="39a1f-127"><xref:System.Windows.Forms.RichTextBox> class</span></span>  
 <span data-ttu-id="39a1f-128">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="39a1f-128">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="39a1f-129">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="39a1f-129">Related Sections</span></span>  
 [<span data-ttu-id="39a1f-130">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="39a1f-130">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="39a1f-131">Poskytuje úplný seznam Windows Forms – ovládací prvky, odkazy na informace o jejich používání.</span><span class="sxs-lookup"><span data-stu-id="39a1f-131">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="39a1f-132">Ovládací prvek TextBox</span><span class="sxs-lookup"><span data-stu-id="39a1f-132">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)  
 <span data-ttu-id="39a1f-133">Představuje obecné koncepty <xref:System.Windows.Forms.TextBox> řízení, které umožňuje upravovat, Víceřádkový vstup od uživatele.</span><span class="sxs-lookup"><span data-stu-id="39a1f-133">Introduces the general concepts of the <xref:System.Windows.Forms.TextBox> control, which allows editable, multiline input from the user.</span></span>
