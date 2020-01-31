---
title: Ovládací prvek RichTextBox
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes
- RichTextBox control [Windows Forms]
- rich edit controls
ms.assetid: 3225f2ef-c6d9-4bd4-9d3e-2219e58edbf2
ms.openlocfilehash: 9d26ec7bfc4d75b304bbc9dc98dbbeaed64effe7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743134"
---
# <a name="richtextbox-control-windows-forms"></a><span data-ttu-id="0124b-102">RichTextBox – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="0124b-102">RichTextBox Control (Windows Forms)</span></span>
<span data-ttu-id="0124b-103">Ovládací prvek model Windows Forms `RichTextBox` slouží k zobrazení, zadání a manipulaci s textem s formátováním.</span><span class="sxs-lookup"><span data-stu-id="0124b-103">The Windows Forms `RichTextBox` control is used for displaying, entering, and manipulating text with formatting.</span></span> <span data-ttu-id="0124b-104">Ovládací prvek `RichTextBox` provádí všechno <xref:System.Windows.Forms.TextBox> řízení, ale může také zobrazovat písma, barvy a odkazy; načtení textu a vložených obrázků ze souboru; operace zrušení a opětovného provedení úprav; a vyhledá zadané znaky.</span><span class="sxs-lookup"><span data-stu-id="0124b-104">The `RichTextBox` control does everything the <xref:System.Windows.Forms.TextBox> control does, but it can also display fonts, colors, and links; load text and embedded images from a file; undo and redo editing operations; and find specified characters.</span></span> <span data-ttu-id="0124b-105">Ovládací prvek `RichTextBox` se obvykle používá k poskytování funkcí pro manipulaci s textem a zobrazení podobných aplikacím pro zpracování textu, jako je například Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="0124b-105">The `RichTextBox` control is typically used to provide text manipulation and display features similar to word processing applications such as Microsoft Word.</span></span> <span data-ttu-id="0124b-106">Podobně jako u ovládacího prvku <xref:System.Windows.Forms.TextBox> může ovládací prvek `RichTextBox` Zobrazit posuvníky. ale na rozdíl od ovládacího prvku <xref:System.Windows.Forms.TextBox> zobrazuje ve výchozím nastavení vodorovný i svislý posuvník a má další nastavení posuvníku.</span><span class="sxs-lookup"><span data-stu-id="0124b-106">Like the <xref:System.Windows.Forms.TextBox> control, the `RichTextBox` control can display scroll bars; but unlike the <xref:System.Windows.Forms.TextBox> control, it displays both horizontal and vertical scrollbars by default and has additional scrollbar settings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0124b-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0124b-107">In This Section</span></span>  
 [<span data-ttu-id="0124b-108">Přehled ovládacího prvku RichTextBox</span><span class="sxs-lookup"><span data-stu-id="0124b-108">RichTextBox Control Overview</span></span>](richtextbox-control-overview-windows-forms.md)  
 <span data-ttu-id="0124b-109">Zavádí obecné koncepty ovládacího prvku `RichTextBox`, který umožňuje uživatelům zadávat, zobrazovat a manipulovat s možnostmi formátování.</span><span class="sxs-lookup"><span data-stu-id="0124b-109">Introduces the general concepts of the `RichTextBox` control, which allows users to enter, display, and manipulate text with formatting options.</span></span>  
  
 [<span data-ttu-id="0124b-110">Postupy: Určení momentu změny atributů formátování v ovládacím prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="0124b-110">How to: Determine When Formatting Attributes Change in the Windows Forms RichTextBox Control</span></span>](determine-when-formatting-attributes-change-wf-richtextbox-control.md)  
 <span data-ttu-id="0124b-111">Vysvětluje, jak sledovat změny v formátování písma a odstavců v ovládacím prvku `RichTextBox`.</span><span class="sxs-lookup"><span data-stu-id="0124b-111">Explains how to keep track of changes in font and paragraph formatting in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="0124b-112">Postupy: Zobrazení posuvníků v ovládacím prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="0124b-112">How to: Display Scroll Bars in the Windows Forms RichTextBox Control</span></span>](how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="0124b-113">Popisuje řadu možností, které jsou k dispozici pro posuvníky v ovládacím prvku `RichTextBox`.</span><span class="sxs-lookup"><span data-stu-id="0124b-113">Describes the many choices available for scroll bars in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="0124b-114">Postupy: Zobrazení webových odkazů pomocí ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="0124b-114">How to: Display Web-Style Links with the Windows Forms RichTextBox Control</span></span>](how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="0124b-115">Vysvětluje, jak propojit weby z ovládacího prvku `RichTextBox`.</span><span class="sxs-lookup"><span data-stu-id="0124b-115">Explains how to link to Web sites from the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="0124b-116">Postupy: Povolení operací přetažení myší pomocí ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="0124b-116">How to: Enable Drag-and-Drop Operations with the Windows Forms RichTextBox Control</span></span>](enable-drag-and-drop-operations-with-wf-richtextbox-control.md)  
 <span data-ttu-id="0124b-117">Poskytuje pokyny pro přetahování dat do ovládacího prvku `RichTextBox`.</span><span class="sxs-lookup"><span data-stu-id="0124b-117">Provides instructions for dragging data into the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="0124b-118">Postupy: Načtení souborů do ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="0124b-118">How to: Load Files into the Windows Forms RichTextBox Control</span></span>](how-to-load-files-into-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="0124b-119">Poskytuje pokyny pro načtení existujícího souboru do ovládacího prvku `RichTextBox`.</span><span class="sxs-lookup"><span data-stu-id="0124b-119">Provides instructions for loading an existing file into the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="0124b-120">Postupy: Ukládání souborů pomocí ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="0124b-120">How to: Save Files with the Windows Forms RichTextBox Control</span></span>](how-to-save-files-with-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="0124b-121">Obsahuje pokyny pro uložení obsahu ovládacího prvku `RichTextBox` do souboru.</span><span class="sxs-lookup"><span data-stu-id="0124b-121">Provides instructions for saving the contents of the `RichTextBox` control to a file.</span></span>  
  
 [<span data-ttu-id="0124b-122">Postupy: Nastavení atributů písma pro ovládací prvek Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="0124b-122">How to: Set Font Attributes for the Windows Forms RichTextBox Control</span></span>](how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="0124b-123">Popisuje, jak nastavit rodinu písem, velikost, styl a barvu textu v ovládacím prvku `RichTextBox`.</span><span class="sxs-lookup"><span data-stu-id="0124b-123">Describes how to set the font family, size, style, and color of text in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="0124b-124">Postupy: Nastavení odsazení, předsazení a odstavců s odrážkami pomocí ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="0124b-124">How to: Set Indents, Hanging Indents, and Bulleted Paragraphs with the Windows Forms RichTextBox Control</span></span>](set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md)  
 <span data-ttu-id="0124b-125">Popisuje, jak formátovat odstavce v ovládacím prvku `RichTextBox`.</span><span class="sxs-lookup"><span data-stu-id="0124b-125">Describes how to format paragraphs in the `RichTextBox` control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0124b-126">Odkaz</span><span class="sxs-lookup"><span data-stu-id="0124b-126">Reference</span></span>  
 <span data-ttu-id="0124b-127"><xref:System.Windows.Forms.RichTextBox> – třída</span><span class="sxs-lookup"><span data-stu-id="0124b-127"><xref:System.Windows.Forms.RichTextBox> class</span></span>  
 <span data-ttu-id="0124b-128">Popisuje tuto třídu a má odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="0124b-128">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0124b-129">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0124b-129">Related Sections</span></span>  
 [<span data-ttu-id="0124b-130">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0124b-130">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="0124b-131">Obsahuje úplný seznam model Windows Formsch ovládacích prvků s odkazy na informace o jejich použití.</span><span class="sxs-lookup"><span data-stu-id="0124b-131">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="0124b-132">Ovládací prvek TextBox</span><span class="sxs-lookup"><span data-stu-id="0124b-132">TextBox Control</span></span>](textbox-control-windows-forms.md)  
 <span data-ttu-id="0124b-133">Zavádí obecné koncepty ovládacího prvku <xref:System.Windows.Forms.TextBox>, který umožňuje upravit Víceřádkový vstup od uživatele.</span><span class="sxs-lookup"><span data-stu-id="0124b-133">Introduces the general concepts of the <xref:System.Windows.Forms.TextBox> control, which allows editable, multiline input from the user.</span></span>
