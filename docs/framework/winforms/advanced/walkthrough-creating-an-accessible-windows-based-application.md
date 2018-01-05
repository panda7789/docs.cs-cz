---
title: "Návod: Vytvoření aplikace systému Windows s usnadněnou obsluhou"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8f0a35b569b38e0d7ca79129f720034420ecd23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a><span data-ttu-id="116f8-102">Návod: Vytvoření aplikace systému Windows s usnadněnou obsluhou</span><span class="sxs-lookup"><span data-stu-id="116f8-102">Walkthrough: Creating an Accessible Windows-based Application</span></span>
<span data-ttu-id="116f8-103">Vytváření přístupné aplikací má zásadní obchodní dopad.</span><span class="sxs-lookup"><span data-stu-id="116f8-103">Creating an accessible application has important business implications.</span></span> <span data-ttu-id="116f8-104">Mnoho vlády mají požadavky na usnadnění nákup softwaru.</span><span class="sxs-lookup"><span data-stu-id="116f8-104">Many governments have accessibility regulations for software purchase.</span></span> <span data-ttu-id="116f8-105">Logo Certified for Windows obsahuje požadavky na usnadnění přístupu.</span><span class="sxs-lookup"><span data-stu-id="116f8-105">The Certified for Windows logo includes accessibility requirements.</span></span> <span data-ttu-id="116f8-106">Usnadnění softwaru se vztahuje odhadované 30 milionů obyvatele samostatně, USA, kolika z nich potenciální zákazníky.</span><span class="sxs-lookup"><span data-stu-id="116f8-106">An estimated 30 million residents of the U.S. alone, many of them potential customers, are affected by the accessibility of software.</span></span>  
  
 <span data-ttu-id="116f8-107">Tento názorný postup vyřeší pět požadavky na usnadnění přístupu pro logo Certified for Windows.</span><span class="sxs-lookup"><span data-stu-id="116f8-107">This walkthrough will address the five accessibility requirements for the Certified for Windows logo.</span></span> <span data-ttu-id="116f8-108">Dostupné aplikace se podle těchto požadavků:</span><span class="sxs-lookup"><span data-stu-id="116f8-108">According to these requirements, an accessible application will:</span></span>  
  
-   <span data-ttu-id="116f8-109">Podporovat velikost ovládacích panelů, barvy, písma a zadejte nastavení.</span><span class="sxs-lookup"><span data-stu-id="116f8-109">Support Control Panel size, color, font, and input settings.</span></span> <span data-ttu-id="116f8-110">Panel nabídek, záhlaví, ohraničení a stavového řádku změní všechny velikost sami když uživatel změní nastavení ovládacího panelu.</span><span class="sxs-lookup"><span data-stu-id="116f8-110">The menu bar, title bar, borders, and status bar will all resize themselves when the user changes the control panel settings.</span></span> <span data-ttu-id="116f8-111">V této aplikaci se nevyžadují žádné další změny ovládací prvky nebo kódu.</span><span class="sxs-lookup"><span data-stu-id="116f8-111">No additional changes to the controls or code are required in this application.</span></span>  
  
-   <span data-ttu-id="116f8-112">Podpora režimu vysokého kontrastu.</span><span class="sxs-lookup"><span data-stu-id="116f8-112">Support High Contrast mode.</span></span>  
  
-   <span data-ttu-id="116f8-113">Zadejte zdokumentovaných klávesnice přístup ke všem funkcím.</span><span class="sxs-lookup"><span data-stu-id="116f8-113">Provide documented keyboard access to all features.</span></span>  
  
-   <span data-ttu-id="116f8-114">Vystavení umístění fokus klávesnice vizuálně a programově.</span><span class="sxs-lookup"><span data-stu-id="116f8-114">Expose location of the keyboard focus visually and programmatically.</span></span>  
  
-   <span data-ttu-id="116f8-115">Vyhněte se předávání důležitých informací zvukovou samostatně.</span><span class="sxs-lookup"><span data-stu-id="116f8-115">Avoid conveying important information by sound alone.</span></span>  
  
 <span data-ttu-id="116f8-116">Další informace najdete v tématu [prostředky pro navrhování přístupné aplikace](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span><span class="sxs-lookup"><span data-stu-id="116f8-116">For more information, see [Resources for Designing Accessible Applications](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span></span>  
  
 <span data-ttu-id="116f8-117">Informace na podporu různých rozložení klávesnice najdete v tématu [osvědčené postupy pro vývoj aplikací připravených](../../../../docs/standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span><span class="sxs-lookup"><span data-stu-id="116f8-117">For information on supporting varying keyboard layouts, see [Best Practices for Developing World-Ready Applications](../../../../docs/standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="116f8-118">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="116f8-118">Creating the Project</span></span>  
 <span data-ttu-id="116f8-119">Tento návod vytvoří uživatelské rozhraní pro aplikaci, která přebírá pizza objednávky.</span><span class="sxs-lookup"><span data-stu-id="116f8-119">This walkthrough creates the user interface for an application that takes pizza orders.</span></span> <span data-ttu-id="116f8-120">Skládá se z <xref:System.Windows.Forms.TextBox> pro název zákazníka, <xref:System.Windows.Forms.RadioButton> skupina a vyberte velikost pizza <xref:System.Windows.Forms.CheckedListBox> pro výběr toppings, dvou ovládacích prvků tlačítko s názvem bez přípony pořadí a zrušit a nabídky pomocí příkazu pro ukončení.</span><span class="sxs-lookup"><span data-stu-id="116f8-120">It consists of a <xref:System.Windows.Forms.TextBox> for the customer's name, a <xref:System.Windows.Forms.RadioButton> group to select the pizza size, a <xref:System.Windows.Forms.CheckedListBox> for selecting the toppings, two Button controls labeled Order and Cancel, and a Menu with an Exit command.</span></span>  
  
 <span data-ttu-id="116f8-121">Uživatel zadá název zákazníka, velikost pizza a toppings potřeby.</span><span class="sxs-lookup"><span data-stu-id="116f8-121">The user enters the customer's name, the size of the pizza, and the toppings desired.</span></span> <span data-ttu-id="116f8-122">Když uživatel klikne na tlačítko pořadí, souhrn pořadí a jeho náklady jsou zobrazeny v okně se zprávou a ovládací prvky jsou nezaškrtnuté a připravené pro další pořadí.</span><span class="sxs-lookup"><span data-stu-id="116f8-122">When the user clicks the Order button, a summary of the order and its cost are displayed in a message box and the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="116f8-123">Když uživatel klikne na tlačítko Storno, ovládací prvky jsou nezaškrtnuté a připravené pro další pořadí.</span><span class="sxs-lookup"><span data-stu-id="116f8-123">When the user clicks the Cancel button, the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="116f8-124">Když uživatel klikne na položku nabídky ukončení, program se ukončí.</span><span class="sxs-lookup"><span data-stu-id="116f8-124">When the user clicks the Exit menu item, the program closes.</span></span>  
  
 <span data-ttu-id="116f8-125">Zvýraznění tohoto návodu není kód pro maloobchodní pořadí systému, ale usnadnění uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="116f8-125">The emphasis of this walkthrough is not the code for a retail order system, but the accessibility of the user interface.</span></span> <span data-ttu-id="116f8-126">Průvodce ukazuje, že funkce pro usnadnění přístupu několik často používané ovládací prvky, včetně tlačítka, přepínače, textových polí a popisky.</span><span class="sxs-lookup"><span data-stu-id="116f8-126">The walkthrough demonstrates the accessibility features of several frequently used controls, including buttons, radio buttons, text boxes, and labels.</span></span>  
  
#### <a name="to-begin-making-the-application"></a><span data-ttu-id="116f8-127">Chcete-li začít vytvářet aplikace</span><span class="sxs-lookup"><span data-stu-id="116f8-127">To begin making the application</span></span>  
  
-   <span data-ttu-id="116f8-128">Vytvoření nové aplikace Windows v [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="116f8-128">Create a new Windows Application in [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)].</span></span> <span data-ttu-id="116f8-129">Název projektu **PizzaOrder**.</span><span class="sxs-lookup"><span data-stu-id="116f8-129">Name the project **PizzaOrder**.</span></span> <span data-ttu-id="116f8-130">(Podrobnosti najdete v tématu [vytváření nových řešení a projekty](/visualstudio/ide/creating-solutions-and-projects).)</span><span class="sxs-lookup"><span data-stu-id="116f8-130">(For details see [Creating New Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).)</span></span>  
  
## <a name="adding-the-controls-to-the-form"></a><span data-ttu-id="116f8-131">Přidání ovládacích prvků formuláře</span><span class="sxs-lookup"><span data-stu-id="116f8-131">Adding the Controls to the Form</span></span>  
 <span data-ttu-id="116f8-132">Při přidávání ovládacích prvků na formuláři, mějte na paměti následující pokyny, aby se aplikace dostupné:</span><span class="sxs-lookup"><span data-stu-id="116f8-132">When adding the controls to a form, keep in mind the following guidelines to make an accessible application:</span></span>  
  
-   <span data-ttu-id="116f8-133">Nastavte <xref:System.Windows.Forms.Control.AccessibleDescription%2A> a <xref:System.Windows.Forms.Control.AccessibleName%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="116f8-133">Set the <xref:System.Windows.Forms.Control.AccessibleDescription%2A> and <xref:System.Windows.Forms.Control.AccessibleName%2A> properties.</span></span> <span data-ttu-id="116f8-134">V tomto příkladu výchozí nastavení <xref:System.Windows.Forms.Control.AccessibleRole%2A> je dostačující.</span><span class="sxs-lookup"><span data-stu-id="116f8-134">In this example, the Default setting for the <xref:System.Windows.Forms.Control.AccessibleRole%2A> is sufficient.</span></span> <span data-ttu-id="116f8-135">Další informace o vlastnostech usnadnění přístupu najdete v tématu [poskytuje informace o usnadnění pro ovládací prvky na formuláři Windows](../../../../docs/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="116f8-135">For more information on the accessibility properties, see [Providing Accessibility Information for Controls on a Windows Form](../../../../docs/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span></span>  
  
-   <span data-ttu-id="116f8-136">Nastavení velikosti písma 10 bodů nebo větší.</span><span class="sxs-lookup"><span data-stu-id="116f8-136">Set the font size to 10 points or larger.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="116f8-137">Pokud nastavíte velikost písma formuláře na 10, při spuštění, bude mít všechny ovládací prvky, později přidané do formuláře velikost písma 10.</span><span class="sxs-lookup"><span data-stu-id="116f8-137">If you set the font size of the form to 10 when you start, then all controls subsequently added to the form will have a font size of 10.</span></span>  
  
-   <span data-ttu-id="116f8-138">Ujistěte se, že libovolný ovládací prvek popisek, který popisuje ovládacím prvku TextBox okamžitě předchází TextBox – ovládací prvek v pořadí.</span><span class="sxs-lookup"><span data-stu-id="116f8-138">Make sure any Label control that describes a TextBox control immediately precedes the TextBox control in the tab order.</span></span>  
  
-   <span data-ttu-id="116f8-139">Přidat přístupový klíč, pomocí znaku "&" na <xref:System.Windows.Forms.Control.Text%2A> vlastnosti libovolného ovládacího prvku, uživatel může chtít přejděte do.</span><span class="sxs-lookup"><span data-stu-id="116f8-139">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of any control the user may want to navigate to.</span></span>  
  
-   <span data-ttu-id="116f8-140">Přidat přístupový klíč, pomocí znaku "&", položky <xref:System.Windows.Forms.Control.Text%2A> vlastnost štítek, který předchází ovládacího prvku, který uživatel může chtít přejděte do.</span><span class="sxs-lookup"><span data-stu-id="116f8-140">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of the label that precedes a control that the user may want to navigate to.</span></span> <span data-ttu-id="116f8-141">Nastavit zobrazí popisky <xref:System.Windows.Forms.Label.UseMnemonic%2A> vlastnost `true`, tak, aby fokus je nastavena na další ovládací prvek v pořadí, když uživatel stiskne přístupový klíč.</span><span class="sxs-lookup"><span data-stu-id="116f8-141">Set the labels' <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`, so that the focus is set to the next control in the tab order when the user presses the access key.</span></span>  
  
-   <span data-ttu-id="116f8-142">Přidejte přístupové klíče pro všechny položky nabídky.</span><span class="sxs-lookup"><span data-stu-id="116f8-142">Add access keys to all menu items.</span></span>  
  
#### <a name="to-make-your-windows-application-accessible"></a><span data-ttu-id="116f8-143">Pro zpřístupnění aplikací pro Windows</span><span class="sxs-lookup"><span data-stu-id="116f8-143">To make your Windows Application accessible</span></span>  
  
-   <span data-ttu-id="116f8-144">Přidání ovládacích prvků formuláře a nastavte vlastnosti, jak je popsáno níže.</span><span class="sxs-lookup"><span data-stu-id="116f8-144">Add the controls to the form and set the properties as described below.</span></span> <span data-ttu-id="116f8-145">Zobrazí se obrázek na konci v tabulce pro model, jak k uspořádání ovládacích prvků na formuláři.</span><span class="sxs-lookup"><span data-stu-id="116f8-145">See the picture at the end of the table for a model of how to arrange the controls on the form.</span></span>  
  
    |<span data-ttu-id="116f8-146">Objekt</span><span class="sxs-lookup"><span data-stu-id="116f8-146">Object</span></span>|<span data-ttu-id="116f8-147">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="116f8-147">Property</span></span>|<span data-ttu-id="116f8-148">Hodnota</span><span class="sxs-lookup"><span data-stu-id="116f8-148">Value</span></span>|  
    |------------|--------------|-----------|  
    |<span data-ttu-id="116f8-149">Form1</span><span class="sxs-lookup"><span data-stu-id="116f8-149">Form1</span></span>|<span data-ttu-id="116f8-150">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="116f8-150">AccessibleDescription</span></span>|<span data-ttu-id="116f8-151">Pořadí formuláře</span><span class="sxs-lookup"><span data-stu-id="116f8-151">Order form</span></span>|  
    ||<span data-ttu-id="116f8-152">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="116f8-152">AccessibleName</span></span>|<span data-ttu-id="116f8-153">Pořadí formuláře</span><span class="sxs-lookup"><span data-stu-id="116f8-153">Order form</span></span>|  
    ||<span data-ttu-id="116f8-154">Velikost písma</span><span class="sxs-lookup"><span data-stu-id="116f8-154">Font Size</span></span>|<span data-ttu-id="116f8-155">10</span><span class="sxs-lookup"><span data-stu-id="116f8-155">10</span></span>|  
    ||<span data-ttu-id="116f8-156">Text</span><span class="sxs-lookup"><span data-stu-id="116f8-156">Text</span></span>|<span data-ttu-id="116f8-157">Formulář pro objednání pizzy</span><span class="sxs-lookup"><span data-stu-id="116f8-157">Pizza Order Form</span></span>|  
    |<span data-ttu-id="116f8-158">PictureBox</span><span class="sxs-lookup"><span data-stu-id="116f8-158">PictureBox</span></span>|<span data-ttu-id="116f8-159">Název</span><span class="sxs-lookup"><span data-stu-id="116f8-159">Name</span></span>|<span data-ttu-id="116f8-160">Logo</span><span class="sxs-lookup"><span data-stu-id="116f8-160">logo</span></span>|  
    ||<span data-ttu-id="116f8-161">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="116f8-161">AccessibleDescription</span></span>|<span data-ttu-id="116f8-162">Řez pizza</span><span class="sxs-lookup"><span data-stu-id="116f8-162">A slice of pizza</span></span>|  
    ||<span data-ttu-id="116f8-163">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="116f8-163">AccessibleName</span></span>|<span data-ttu-id="116f8-164">Logo společnosti</span><span class="sxs-lookup"><span data-stu-id="116f8-164">Company logo</span></span>|  
    ||<span data-ttu-id="116f8-165">Image</span><span class="sxs-lookup"><span data-stu-id="116f8-165">Image</span></span>|<span data-ttu-id="116f8-166">Všechny ikony nebo rastrového obrázku</span><span class="sxs-lookup"><span data-stu-id="116f8-166">Any icon or bitmap</span></span>|  
    |<span data-ttu-id="116f8-167">Popisek</span><span class="sxs-lookup"><span data-stu-id="116f8-167">Label</span></span>|<span data-ttu-id="116f8-168">Název</span><span class="sxs-lookup"><span data-stu-id="116f8-168">Name</span></span>|<span data-ttu-id="116f8-169">companyLabel</span><span class="sxs-lookup"><span data-stu-id="116f8-169">companyLabel</span></span>|  
    ||<span data-ttu-id="116f8-170">Text</span><span class="sxs-lookup"><span data-stu-id="116f8-170">Text</span></span>|<span data-ttu-id="116f8-171">Dobrý Pizza</span><span class="sxs-lookup"><span data-stu-id="116f8-171">Good Pizza</span></span>|  
    ||<span data-ttu-id="116f8-172">Pořadové číslo prvku</span><span class="sxs-lookup"><span data-stu-id="116f8-172">TabIndex</span></span>|<span data-ttu-id="116f8-173">1</span><span class="sxs-lookup"><span data-stu-id="116f8-173">1</span></span>|  
    ||<span data-ttu-id="116f8-174">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="116f8-174">AccessibleDescription</span></span>|<span data-ttu-id="116f8-175">Název společnosti</span><span class="sxs-lookup"><span data-stu-id="116f8-175">Company name</span></span>|  
    ||<span data-ttu-id="116f8-176">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="116f8-176">AccessibleName</span></span>|<span data-ttu-id="116f8-177">Název společnosti</span><span class="sxs-lookup"><span data-stu-id="116f8-177">Company name</span></span>|  
    ||<span data-ttu-id="116f8-178">Barva pozadí</span><span class="sxs-lookup"><span data-stu-id="116f8-178">Backcolor</span></span>|<span data-ttu-id="116f8-179">modrá</span><span class="sxs-lookup"><span data-stu-id="116f8-179">Blue</span></span>|  
    ||<span data-ttu-id="116f8-180">ForeColor</span><span class="sxs-lookup"><span data-stu-id="116f8-180">Forecolor</span></span>|<span data-ttu-id="116f8-181">žlutý</span><span class="sxs-lookup"><span data-stu-id="116f8-181">Yellow</span></span>|  
    ||<span data-ttu-id="116f8-182">Velikost písma</span><span class="sxs-lookup"><span data-stu-id="116f8-182">Font size</span></span>|<span data-ttu-id="116f8-183">18</span><span class="sxs-lookup"><span data-stu-id="116f8-183">18</span></span>|  
    |<span data-ttu-id="116f8-184">Popisek</span><span class="sxs-lookup"><span data-stu-id="116f8-184">Label</span></span>|<span data-ttu-id="116f8-185">Název</span><span class="sxs-lookup"><span data-stu-id="116f8-185">Name</span></span>|<span data-ttu-id="116f8-186">customerLabel</span><span class="sxs-lookup"><span data-stu-id="116f8-186">customerLabel</span></span>|  
    ||<span data-ttu-id="116f8-187">Text</span><span class="sxs-lookup"><span data-stu-id="116f8-187">Text</span></span>|<span data-ttu-id="116f8-188">& název</span><span class="sxs-lookup"><span data-stu-id="116f8-188">&Name</span></span>|  
    ||<span data-ttu-id="116f8-189">Pořadové číslo prvku</span><span class="sxs-lookup"><span data-stu-id="116f8-189">TabIndex</span></span>|<span data-ttu-id="116f8-190">2</span><span class="sxs-lookup"><span data-stu-id="116f8-190">2</span></span>|  
    ||<span data-ttu-id="116f8-191">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="116f8-191">AccessibleDescription</span></span>|<span data-ttu-id="116f8-192">Popisek názvu zákazníka</span><span class="sxs-lookup"><span data-stu-id="116f8-192">Customer name label</span></span>|  
    ||<span data-ttu-id="116f8-193">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="116f8-193">AccessibleName</span></span>|<span data-ttu-id="116f8-194">Popisek názvu zákazníka</span><span class="sxs-lookup"><span data-stu-id="116f8-194">Customer name label</span></span>|  
    ||<span data-ttu-id="116f8-195">Usemnemonic –</span><span class="sxs-lookup"><span data-stu-id="116f8-195">UseMnemonic</span></span>|<span data-ttu-id="116f8-196">Hodnota TRUE</span><span class="sxs-lookup"><span data-stu-id="116f8-196">True</span></span>|  
    |<span data-ttu-id="116f8-197">TextBox</span><span class="sxs-lookup"><span data-stu-id="116f8-197">TextBox</span></span>|<span data-ttu-id="116f8-198">Název</span><span class="sxs-lookup"><span data-stu-id="116f8-198">Name</span></span>|<span data-ttu-id="116f8-199">JménoZákazníka</span><span class="sxs-lookup"><span data-stu-id="116f8-199">customerName</span></span>|  
    ||<span data-ttu-id="116f8-200">Text</span><span class="sxs-lookup"><span data-stu-id="116f8-200">Text</span></span>|<span data-ttu-id="116f8-201">(žádný)</span><span class="sxs-lookup"><span data-stu-id="116f8-201">(none)</span></span>|  
    ||<span data-ttu-id="116f8-202">Pořadové číslo prvku</span><span class="sxs-lookup"><span data-stu-id="116f8-202">TabIndex</span></span>|<span data-ttu-id="116f8-203">3</span><span class="sxs-lookup"><span data-stu-id="116f8-203">3</span></span>|  
    ||<span data-ttu-id="116f8-204">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="116f8-204">AccessibleDescription</span></span>|<span data-ttu-id="116f8-205">Jméno zákazníka</span><span class="sxs-lookup"><span data-stu-id="116f8-205">Customer name</span></span>|  
    ||<span data-ttu-id="116f8-206">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="116f8-206">AccessibleName</span></span>|<span data-ttu-id="116f8-207">Jméno zákazníka</span><span class="sxs-lookup"><span data-stu-id="116f8-207">Customer name</span></span>|  
    |<span data-ttu-id="116f8-208">GroupBox</span><span class="sxs-lookup"><span data-stu-id="116f8-208">GroupBox</span></span>|<span data-ttu-id="116f8-209">Název</span><span class="sxs-lookup"><span data-stu-id="116f8-209">Name</span></span>|<span data-ttu-id="116f8-210">sizeOptions</span><span class="sxs-lookup"><span data-stu-id="116f8-210">sizeOptions</span></span>|  
    ||<span data-ttu-id="116f8-211">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="116f8-211">AccessibleDescription</span></span>|<span data-ttu-id="116f8-212">Možnosti velikosti pizza</span><span class="sxs-lookup"><span data-stu-id="116f8-212">Pizza size options</span></span>|  
    ||<span data-ttu-id="116f8-213">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="116f8-213">AccessibleName</span></span>|<span data-ttu-id="116f8-214">Možnosti velikosti pizza</span><span class="sxs-lookup"><span data-stu-id="116f8-214">Pizza size options</span></span>|  
    ||<span data-ttu-id="116f8-215">Text</span><span class="sxs-lookup"><span data-stu-id="116f8-215">Text</span></span>|<span data-ttu-id="116f8-216">Velikost pizza</span><span class="sxs-lookup"><span data-stu-id="116f8-216">Pizza size</span></span>|  
    ||<span data-ttu-id="116f8-217">Pořadové číslo prvku</span><span class="sxs-lookup"><span data-stu-id="116f8-217">TabIndex</span></span>|<span data-ttu-id="116f8-218">4</span><span class="sxs-lookup"><span data-stu-id="116f8-218">4</span></span>|  
    |<span data-ttu-id="116f8-219">RadioButton</span><span class="sxs-lookup"><span data-stu-id="116f8-219">RadioButton</span></span>|<span data-ttu-id="116f8-220">Název</span><span class="sxs-lookup"><span data-stu-id="116f8-220">Name</span></span>|<span data-ttu-id="116f8-221">smallPizza</span><span class="sxs-lookup"><span data-stu-id="116f8-221">smallPizza</span></span>|  
    ||<span data-ttu-id="116f8-222">Text</span><span class="sxs-lookup"><span data-stu-id="116f8-222">Text</span></span>|<span data-ttu-id="116f8-223">& malé $6.00</span><span class="sxs-lookup"><span data-stu-id="116f8-223">&Small $6.00</span></span>|  
    ||<span data-ttu-id="116f8-224">Zaškrtnutí</span><span class="sxs-lookup"><span data-stu-id="116f8-224">Checked</span></span>|<span data-ttu-id="116f8-225">Hodnota TRUE</span><span class="sxs-lookup"><span data-stu-id="116f8-225">True</span></span>|  
    ||<span data-ttu-id="116f8-226">Pořadové číslo prvku</span><span class="sxs-lookup"><span data-stu-id="116f8-226">TabIndex</span></span>|<span data-ttu-id="116f8-227">0</span><span class="sxs-lookup"><span data-stu-id="116f8-227">0</span></span>|  
    ||<span data-ttu-id="116f8-228">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="116f8-228">AccessibleDescription</span></span>|<span data-ttu-id="116f8-229">Malé pizza</span><span class="sxs-lookup"><span data-stu-id="116f8-229">Small pizza</span></span>|  
    ||<span data-ttu-id="116f8-230">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="116f8-230">AccessibleName</span></span>|<span data-ttu-id="116f8-231">Malé pizza</span><span class="sxs-lookup"><span data-stu-id="116f8-231">Small pizza</span></span>|  
    |<span data-ttu-id="116f8-232">RadioButton</span><span class="sxs-lookup"><span data-stu-id="116f8-232">RadioButton</span></span>|<span data-ttu-id="116f8-233">Název</span><span class="sxs-lookup"><span data-stu-id="116f8-233">Name</span></span>|<span data-ttu-id="116f8-234">largePizza</span><span class="sxs-lookup"><span data-stu-id="116f8-234">largePizza</span></span>|  
    ||<span data-ttu-id="116f8-235">Text</span><span class="sxs-lookup"><span data-stu-id="116f8-235">Text</span></span>|<span data-ttu-id="116f8-236">& velké 10,00 USD</span><span class="sxs-lookup"><span data-stu-id="116f8-236">&Large $10.00</span></span>|  
    ||<span data-ttu-id="116f8-237">Pořadové číslo prvku</span><span class="sxs-lookup"><span data-stu-id="116f8-237">TabIndex</span></span>|<span data-ttu-id="116f8-238">1</span><span class="sxs-lookup"><span data-stu-id="116f8-238">1</span></span>|  
    ||<span data-ttu-id="116f8-239">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="116f8-239">AccessibleDescription</span></span>|<span data-ttu-id="116f8-240">Velké pizza</span><span class="sxs-lookup"><span data-stu-id="116f8-240">Large pizza</span></span>|  
    ||<span data-ttu-id="116f8-241">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="116f8-241">AccessibleName</span></span>|<span data-ttu-id="116f8-242">Velké pizza</span><span class="sxs-lookup"><span data-stu-id="116f8-242">Large pizza</span></span>|  
    |<span data-ttu-id="116f8-243">Popisek</span><span class="sxs-lookup"><span data-stu-id="116f8-243">Label</span></span>|<span data-ttu-id="116f8-244">Název</span><span class="sxs-lookup"><span data-stu-id="116f8-244">Name</span></span>|<span data-ttu-id="116f8-245">toppingsLabel</span><span class="sxs-lookup"><span data-stu-id="116f8-245">toppingsLabel</span></span>|  
    ||<span data-ttu-id="116f8-246">Text</span><span class="sxs-lookup"><span data-stu-id="116f8-246">Text</span></span>|<span data-ttu-id="116f8-247">& toppings ($0,75 každý)</span><span class="sxs-lookup"><span data-stu-id="116f8-247">&Toppings ($0.75 each)</span></span>|  
    ||<span data-ttu-id="116f8-248">Pořadové číslo prvku</span><span class="sxs-lookup"><span data-stu-id="116f8-248">TabIndex</span></span>|<span data-ttu-id="116f8-249">5</span><span class="sxs-lookup"><span data-stu-id="116f8-249">5</span></span>|  
    ||<span data-ttu-id="116f8-250">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="116f8-250">AccessibleDescription</span></span>|<span data-ttu-id="116f8-251">Popisek toppings</span><span class="sxs-lookup"><span data-stu-id="116f8-251">Toppings label</span></span>|  
    ||<span data-ttu-id="116f8-252">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="116f8-252">AccessibleName</span></span>|<span data-ttu-id="116f8-253">Popisek toppings</span><span class="sxs-lookup"><span data-stu-id="116f8-253">Toppings label</span></span>|  
    ||<span data-ttu-id="116f8-254">Usemnemonic –</span><span class="sxs-lookup"><span data-stu-id="116f8-254">UseMnemonic</span></span>|<span data-ttu-id="116f8-255">Hodnota TRUE</span><span class="sxs-lookup"><span data-stu-id="116f8-255">True</span></span>|  
    |<span data-ttu-id="116f8-256">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="116f8-256">CheckedListBox</span></span>|<span data-ttu-id="116f8-257">Název</span><span class="sxs-lookup"><span data-stu-id="116f8-257">Name</span></span>|<span data-ttu-id="116f8-258">toppings</span><span class="sxs-lookup"><span data-stu-id="116f8-258">toppings</span></span>|  
    ||<span data-ttu-id="116f8-259">Pořadové číslo prvku</span><span class="sxs-lookup"><span data-stu-id="116f8-259">TabIndex</span></span>|<span data-ttu-id="116f8-260">6</span><span class="sxs-lookup"><span data-stu-id="116f8-260">6</span></span>|  
    ||<span data-ttu-id="116f8-261">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="116f8-261">AccessibleDescription</span></span>|<span data-ttu-id="116f8-262">K dispozici toppings</span><span class="sxs-lookup"><span data-stu-id="116f8-262">Available toppings</span></span>|  
    ||<span data-ttu-id="116f8-263">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="116f8-263">AccessibleName</span></span>|<span data-ttu-id="116f8-264">K dispozici toppings</span><span class="sxs-lookup"><span data-stu-id="116f8-264">Available toppings</span></span>|  
    ||<span data-ttu-id="116f8-265">Položky</span><span class="sxs-lookup"><span data-stu-id="116f8-265">Items</span></span>|<span data-ttu-id="116f8-266">Pepperoni salám, hub</span><span class="sxs-lookup"><span data-stu-id="116f8-266">Pepperoni, Sausage, Mushrooms</span></span>|  
    |<span data-ttu-id="116f8-267">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="116f8-267">Button</span></span>|<span data-ttu-id="116f8-268">Název</span><span class="sxs-lookup"><span data-stu-id="116f8-268">Name</span></span>|<span data-ttu-id="116f8-269">pořadí</span><span class="sxs-lookup"><span data-stu-id="116f8-269">order</span></span>|  
    ||<span data-ttu-id="116f8-270">Text</span><span class="sxs-lookup"><span data-stu-id="116f8-270">Text</span></span>|<span data-ttu-id="116f8-271">& pořadí</span><span class="sxs-lookup"><span data-stu-id="116f8-271">&Order</span></span>|  
    ||<span data-ttu-id="116f8-272">Pořadové číslo prvku</span><span class="sxs-lookup"><span data-stu-id="116f8-272">TabIndex</span></span>|<span data-ttu-id="116f8-273">7</span><span class="sxs-lookup"><span data-stu-id="116f8-273">7</span></span>|  
    ||<span data-ttu-id="116f8-274">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="116f8-274">AccessibleDescription</span></span>|<span data-ttu-id="116f8-275">Celkový počet pořadí</span><span class="sxs-lookup"><span data-stu-id="116f8-275">Total the order</span></span>|  
    ||<span data-ttu-id="116f8-276">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="116f8-276">AccessibleName</span></span>|<span data-ttu-id="116f8-277">Celkové pořadí</span><span class="sxs-lookup"><span data-stu-id="116f8-277">Total order</span></span>|  
    |<span data-ttu-id="116f8-278">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="116f8-278">Button</span></span>|<span data-ttu-id="116f8-279">Název</span><span class="sxs-lookup"><span data-stu-id="116f8-279">Name</span></span>|<span data-ttu-id="116f8-280">Zrušit</span><span class="sxs-lookup"><span data-stu-id="116f8-280">cancel</span></span>|  
    ||<span data-ttu-id="116f8-281">Text</span><span class="sxs-lookup"><span data-stu-id="116f8-281">Text</span></span>|<span data-ttu-id="116f8-282">& Zrušit</span><span class="sxs-lookup"><span data-stu-id="116f8-282">&Cancel</span></span>|  
    ||<span data-ttu-id="116f8-283">Pořadové číslo prvku</span><span class="sxs-lookup"><span data-stu-id="116f8-283">TabIndex</span></span>|<span data-ttu-id="116f8-284">8</span><span class="sxs-lookup"><span data-stu-id="116f8-284">8</span></span>|  
    ||<span data-ttu-id="116f8-285">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="116f8-285">AccessibleDescription</span></span>|<span data-ttu-id="116f8-286">Zrušit pořadí</span><span class="sxs-lookup"><span data-stu-id="116f8-286">Cancel the order</span></span>|  
    ||<span data-ttu-id="116f8-287">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="116f8-287">AccessibleName</span></span>|<span data-ttu-id="116f8-288">Zrušit pořadí</span><span class="sxs-lookup"><span data-stu-id="116f8-288">Cancel order</span></span>|  
    |<span data-ttu-id="116f8-289">MainMenu</span><span class="sxs-lookup"><span data-stu-id="116f8-289">MainMenu</span></span>|<span data-ttu-id="116f8-290">Název</span><span class="sxs-lookup"><span data-stu-id="116f8-290">Name</span></span>|<span data-ttu-id="116f8-291">theMainMenu</span><span class="sxs-lookup"><span data-stu-id="116f8-291">theMainMenu</span></span>|  
    |<span data-ttu-id="116f8-292">Položka nabídky</span><span class="sxs-lookup"><span data-stu-id="116f8-292">MenuItem</span></span>|<span data-ttu-id="116f8-293">Název</span><span class="sxs-lookup"><span data-stu-id="116f8-293">Name</span></span>|<span data-ttu-id="116f8-294">fileCommands</span><span class="sxs-lookup"><span data-stu-id="116f8-294">fileCommands</span></span>|  
    ||<span data-ttu-id="116f8-295">Text</span><span class="sxs-lookup"><span data-stu-id="116f8-295">Text</span></span>|<span data-ttu-id="116f8-296">& souboru</span><span class="sxs-lookup"><span data-stu-id="116f8-296">&File</span></span>|  
    |<span data-ttu-id="116f8-297">Položka nabídky</span><span class="sxs-lookup"><span data-stu-id="116f8-297">MenuItem</span></span>|<span data-ttu-id="116f8-298">Název</span><span class="sxs-lookup"><span data-stu-id="116f8-298">Name</span></span>|<span data-ttu-id="116f8-299">exitApp</span><span class="sxs-lookup"><span data-stu-id="116f8-299">exitApp</span></span>|  
    ||<span data-ttu-id="116f8-300">Text</span><span class="sxs-lookup"><span data-stu-id="116f8-300">Text</span></span>|<span data-ttu-id="116f8-301">& Konec</span><span class="sxs-lookup"><span data-stu-id="116f8-301">E&xit</span></span>|  
  
     <span data-ttu-id="116f8-302">![Formulář pro objednání pizzy](../../../../docs/framework/winforms/advanced/media/vbpizzaorderform.gif "vbPizzaOrderForm")</span><span class="sxs-lookup"><span data-stu-id="116f8-302">![Pizza Order Form](../../../../docs/framework/winforms/advanced/media/vbpizzaorderform.gif "vbPizzaOrderForm")</span></span>  
<span data-ttu-id="116f8-303">Formulář bude vypadat přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="116f8-303">Your form will look something like the following:</span></span>  
  
## <a name="supporting-high-contrast-mode"></a><span data-ttu-id="116f8-304">Podpora režimu vysokého kontrastu</span><span class="sxs-lookup"><span data-stu-id="116f8-304">Supporting High Contrast Mode</span></span>  
 <span data-ttu-id="116f8-305">V režimu Vysoký kontrast je nastavení systému Windows, který zlepšuje čitelnosti pomocí kontrastní barvy a velikosti písma, které jsou užitečné pro uživatele se zrakovým postižením.</span><span class="sxs-lookup"><span data-stu-id="116f8-305">High Contrast mode is a Windows system setting that improves readability by using contrasting colors and font sizes that are beneficial for visually impaired users.</span></span> <span data-ttu-id="116f8-306"><xref:System.Windows.Forms.SystemInformation.HighContrast%2A> Vlastnost je poskytována k určení, zda je nastaven režimu vysokého kontrastu.</span><span class="sxs-lookup"><span data-stu-id="116f8-306">The <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> property is provided to determine whether the High Contrast mode is set.</span></span>  
  
 <span data-ttu-id="116f8-307">Pokud je SystemInformation.HighContrast `true`, by měla aplikace:</span><span class="sxs-lookup"><span data-stu-id="116f8-307">If SystemInformation.HighContrast is `true`, the application should:</span></span>  
  
-   <span data-ttu-id="116f8-308">Zobrazit všechny prvky uživatelského rozhraní pomocí barevného schématu systému</span><span class="sxs-lookup"><span data-stu-id="116f8-308">Display all user interface elements using the system color scheme</span></span>  
  
-   <span data-ttu-id="116f8-309">Oznamují vizuální upozornění nebo zvukových veškeré informace, které se bude předávat přes barvu.</span><span class="sxs-lookup"><span data-stu-id="116f8-309">Convey by visual cues or sound any information that is conveyed through color.</span></span> <span data-ttu-id="116f8-310">Například pokud konkrétní seznam položek se zvýrazní pomocí red písmo, můžete také přidat tučné písmo, tak, aby uživatel má jiný color upozornění, že jsou vyznačené položky.</span><span class="sxs-lookup"><span data-stu-id="116f8-310">For example, if particular list items are highlighted by using a red font, you could also add bold to the font, so that the user has a non-color cue that the items are highlighted.</span></span>  
  
-   <span data-ttu-id="116f8-311">Vynechat všechny bitové kopie nebo vzory za text</span><span class="sxs-lookup"><span data-stu-id="116f8-311">Omit any images or patterns behind text</span></span>  
  
 <span data-ttu-id="116f8-312">Aplikace by se mělo zjistit nastavením <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> když aplikaci spustí a reagovat na systémové události <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span><span class="sxs-lookup"><span data-stu-id="116f8-312">The application should check the setting of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> when the application starts and respond to the system event <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span></span> <span data-ttu-id="116f8-313"><xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> Událost se vyvolá, vždy, když hodnota <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> změny.</span><span class="sxs-lookup"><span data-stu-id="116f8-313">The <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event is raised whenever the value of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> changes.</span></span>  
  
 <span data-ttu-id="116f8-314">V naší aplikaci, je jediným prvkem, který nepoužívá nastavení systému pro barvu `lblCompanyName`.</span><span class="sxs-lookup"><span data-stu-id="116f8-314">In our application, the only element that is not using the system settings for color is `lblCompanyName`.</span></span> <span data-ttu-id="116f8-315"><xref:System.Drawing.SystemColors> Třída se používá k změňte nastavení barvu popisku na barvy vybraných uživatelem systému.</span><span class="sxs-lookup"><span data-stu-id="116f8-315">The <xref:System.Drawing.SystemColors> class is used to change the color settings of the label to the user-selected system colors.</span></span>  
  
#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a><span data-ttu-id="116f8-316">Chcete-li povolit režimu vysokého kontrastu účinným způsobem</span><span class="sxs-lookup"><span data-stu-id="116f8-316">To enable High Contrast mode in an effective way</span></span>  
  
1.  <span data-ttu-id="116f8-317">Vytvořte metodu a nastavit barvy popisku pro barev systému.</span><span class="sxs-lookup"><span data-stu-id="116f8-317">Create a method to set the colors of the label to the system colors.</span></span>  
  
    ```  
    ' Visual Basic  
    Private Sub SetColorScheme()  
       If SystemInformation.HighContrast Then  
          companyLabel.BackColor = SystemColors.Window  
          companyLabel.ForeColor = SystemColors.WindowText  
       Else  
          companyLabel.BackColor = Color.Blue  
          companyLabel.ForeColor = Color.Yellow  
       End If  
    End Sub  
  
    // C#  
    private void SetColorScheme()  
    {  
       if (SystemInformation.HighContrast)  
       {  
          companyLabel.BackColor = SystemColors.Window;  
          companyLabel.ForeColor = SystemColors.WindowText;  
       }  
       else  
       {  
          companyLabel.BackColor = Color.Blue;  
          companyLabel.ForeColor = Color.Yellow;  
       }  
    }  
    ```  
  
2.  <span data-ttu-id="116f8-318">Volání `SetColorScheme` postup v konstruktoru formuláře (`Public Sub New()` v jazyce Visual Basic a `public class Form1` v jazyce Visual C#).</span><span class="sxs-lookup"><span data-stu-id="116f8-318">Call the `SetColorScheme` procedure in the form constructor (`Public Sub New()` in Visual Basic and `public class Form1` in Visual C#).</span></span> <span data-ttu-id="116f8-319">Pro přístup k konstruktoru v jazyce Visual Basic, budete muset rozbalte oblast s názvem bez přípony **Windows Form Designer generovaného kódu**.</span><span class="sxs-lookup"><span data-stu-id="116f8-319">To access the constructor in Visual Basic, you will need to expand the region labeled **Windows Form Designer generated code**.</span></span>  
  
    ```  
    ' Visual Basic   
    Public Sub New()  
       MyBase.New()  
       InitializeComponent()  
       SetColorScheme()  
    End Sub  
  
    // C#  
    public Form1()  
    {  
       InitializeComponent();  
       SetColorScheme();  
    }  
    ```  
  
3.  <span data-ttu-id="116f8-320">Vytvořit procedury události s odpovídajícím podpisem, aby odpovídal na <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> událostí.</span><span class="sxs-lookup"><span data-stu-id="116f8-320">Create an event procedure, with the appropriate signature, to respond to the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event.</span></span>  
  
    ```  
    ' Visual Basic  
    Protected Sub UserPreferenceChanged(ByVal sender As Object, _  
    ByVal e As Microsoft.Win32.UserPreferenceChangedEventArgs)  
       SetColorScheme()  
    End Sub  
  
    // C#  
    public void UserPreferenceChanged(object sender,   
    Microsoft.Win32.UserPreferenceChangedEventArgs e)  
    {  
       SetColorScheme();  
    }  
    ```  
  
4.  <span data-ttu-id="116f8-321">Přidejte do konstruktoru formuláře kód po volání `InitializeComponents`, spojit události postup systémové události.</span><span class="sxs-lookup"><span data-stu-id="116f8-321">Add code to the form constructor, after the call to `InitializeComponents`, to hook up the event procedure to the system event.</span></span> <span data-ttu-id="116f8-322">Tato metoda volá `SetColorScheme` postupu.</span><span class="sxs-lookup"><span data-stu-id="116f8-322">This method calls the `SetColorScheme` procedure.</span></span>  
  
    ```  
    ' Visual Basic  
    Public Sub New()  
       MyBase.New()  
       InitializeComponent()  
       SetColorScheme()  
       AddHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _  
          AddressOf Me.UserPreferenceChanged  
    End Sub  
  
    // C#  
    public Form1()  
    {  
       InitializeComponent();  
       SetColorScheme();  
       Microsoft.Win32.SystemEvents.UserPreferenceChanged   
          += new Microsoft.Win32.UserPreferenceChangedEventHandler(  
          this.UserPreferenceChanged);  
    }  
    ```  
  
5.  <span data-ttu-id="116f8-323">Přidejte kód pro formulář <xref:System.Windows.Forms.Control.Dispose%2A> metody před volání <xref:System.Windows.Forms.Control.Dispose%2A> metoda základní třídy, chcete-li uvolnit událostí po ukončení aplikace.</span><span class="sxs-lookup"><span data-stu-id="116f8-323">Add code to the form <xref:System.Windows.Forms.Control.Dispose%2A> method, before the call to the <xref:System.Windows.Forms.Control.Dispose%2A> method of the base class, to release the event when the application closes.</span></span> <span data-ttu-id="116f8-324">Abyste měli přístup <xref:System.Windows.Forms.Control.Dispose%2A> metody v jazyce Visual Basic, budete muset rozbalte oblast s názvem bez přípony Windows Form Designer vygenerovat kód.</span><span class="sxs-lookup"><span data-stu-id="116f8-324">To access the <xref:System.Windows.Forms.Control.Dispose%2A> method in Visual Basic, you will need to expand the region labeled Windows Form Designer generated code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="116f8-325">Spustí kód událostí systému vlákno odděleně od hlavní aplikace.</span><span class="sxs-lookup"><span data-stu-id="116f8-325">The system event code runs a thread separate from the main application.</span></span> <span data-ttu-id="116f8-326">Pokud není verze události, kód, který spojit události se spustí i po ukončení programu.</span><span class="sxs-lookup"><span data-stu-id="116f8-326">If you do not release the event, the code that you hook up to the event will run even after the program is closed.</span></span>  
  
    ```  
    ' Visual Basic  
    Protected Overloads Overrides Sub Dispose(ByVal disposing As Boolean)  
       If disposing Then  
          If Not (components Is Nothing) Then  
             components.Dispose()  
          End If  
       End If  
       RemoveHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _  
          AddressOf Me.UserPreferenceChanged  
       MyBase.Dispose(disposing)  
    End Sub  
  
    // C#  
    protected override void Dispose( bool disposing )  
    {  
       if( disposing )  
       {  
          if (components != null)   
          {  
             components.Dispose();  
          }  
       }  
       Microsoft.Win32.SystemEvents.UserPreferenceChanged   
          -= new Microsoft.Win32.UserPreferenceChangedEventHandler(  
          this.UserPreferenceChanged);  
       base.Dispose( disposing );  
    }  
    ```  
  
6.  <span data-ttu-id="116f8-327">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="116f8-327">Press F5 to run the application.</span></span>  
  
## <a name="conveying-important-information-by-means-other-than-sound"></a><span data-ttu-id="116f8-328">Předávání důležitých informací jiným způsobem než zvuk</span><span class="sxs-lookup"><span data-stu-id="116f8-328">Conveying Important Information by Means Other Than Sound</span></span>  
 <span data-ttu-id="116f8-329">V této aplikaci žádné informace předávají zvukovou samostatně.</span><span class="sxs-lookup"><span data-stu-id="116f8-329">In this application, no information is conveyed by sound alone.</span></span> <span data-ttu-id="116f8-330">Pokud používáte zvuku ve vaší aplikaci, musí jiným způsobem a zadejte informace.</span><span class="sxs-lookup"><span data-stu-id="116f8-330">If you use sound in your application, then you should supply the information by some other means as well.</span></span>  
  
#### <a name="to-supply-information-by-some-other-means-than-sound"></a><span data-ttu-id="116f8-331">K poskytování informací jiným způsobem než zvuk</span><span class="sxs-lookup"><span data-stu-id="116f8-331">To supply information by some other means than sound</span></span>  
  
1.  <span data-ttu-id="116f8-332">Zkontrolujte záhlaví s použitím funkce rozhraní API systému Windows FlashWindow, flash.</span><span class="sxs-lookup"><span data-stu-id="116f8-332">Make the title bar flash by using the Windows API function FlashWindow.</span></span> <span data-ttu-id="116f8-333">Příklad toho, jak volat funkce rozhraní API systému Windows, naleznete v části [návod: volání rozhraní API systému Windows](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span><span class="sxs-lookup"><span data-stu-id="116f8-333">For an example of how to call Windows API functions, see [Walkthrough: Calling Windows APIs](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="116f8-334">Uživatel může mít povoleno, službu Popis zvuku Windows, která způsobí také okno na flash po přehrání zvuku systému prostřednictvím předdefinované mluvčího počítače.</span><span class="sxs-lookup"><span data-stu-id="116f8-334">The user may have the Windows SoundSentry service enabled, which will also cause the window to flash when the system sounds are played through the computer's built-in speaker.</span></span>  
  
2.  <span data-ttu-id="116f8-335">Důležité informace zobrazí v nemodálním okně, tak, aby uživatel může odpovědět na ni.</span><span class="sxs-lookup"><span data-stu-id="116f8-335">Display the important information in a non-modal window so that the user may respond to it.</span></span>  
  
3.  <span data-ttu-id="116f8-336">Zobrazte okno se zprávou, který získá fokus klávesnice.</span><span class="sxs-lookup"><span data-stu-id="116f8-336">Display a message box that acquires the keyboard focus.</span></span> <span data-ttu-id="116f8-337">Tato metoda Vyhněte se při uživatel může být psaní.</span><span class="sxs-lookup"><span data-stu-id="116f8-337">Avoid this method when the user may be typing.</span></span>  
  
4.  <span data-ttu-id="116f8-338">Zobrazí indikátor stavu v oznamovací oblasti stav na hlavním panelu.</span><span class="sxs-lookup"><span data-stu-id="116f8-338">Display a status indicator in the status notification area of the taskbar.</span></span> <span data-ttu-id="116f8-339">Podrobnosti najdete v tématu [přidání ikon aplikací do TaskBar se součástí Windows Forms NotifyIcon](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span><span class="sxs-lookup"><span data-stu-id="116f8-339">For details, see [Adding Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
## <a name="testing-the-application"></a><span data-ttu-id="116f8-340">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="116f8-340">Testing the Application</span></span>  
 <span data-ttu-id="116f8-341">Před nasazením aplikace, měli byste otestovat funkce usnadnění, které jste implementovali.</span><span class="sxs-lookup"><span data-stu-id="116f8-341">Before deploying the application, you should test the accessibility features that you have implemented.</span></span>  
  
#### <a name="to-test-accessibility-features"></a><span data-ttu-id="116f8-342">Testování funkce pro usnadnění přístupu</span><span class="sxs-lookup"><span data-stu-id="116f8-342">To test accessibility features</span></span>  
  
1.  <span data-ttu-id="116f8-343">Test přístupu k klávesnice, myš odpojte a Navigovat v uživatelském rozhraní pro každou funkci pouze pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="116f8-343">To test keyboard access, unplug the mouse and navigate the user interface for each feature using only the keyboard.</span></span> <span data-ttu-id="116f8-344">Zajistěte, aby všechny úlohy mohou být provedeny pomocí klávesnice jenom.</span><span class="sxs-lookup"><span data-stu-id="116f8-344">Ensure that all tasks may be performed using the keyboard only.</span></span>  
  
2.  <span data-ttu-id="116f8-345">K otestování podpory vysoký kontrast, zvolte ikonu Možnosti usnadnění v Ovládacích panelech.</span><span class="sxs-lookup"><span data-stu-id="116f8-345">To test support of High Contrast, choose the Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="116f8-346">Klikněte na kartu zobrazení a zaškrtněte políčko použití vysokého kontrastu.</span><span class="sxs-lookup"><span data-stu-id="116f8-346">Click the Display tab and select the Use High Contrast check box.</span></span> <span data-ttu-id="116f8-347">Procházejte všechny prvky uživatelského rozhraní pro zajištění, že barev a písem změny se projeví.</span><span class="sxs-lookup"><span data-stu-id="116f8-347">Navigate through all user interface elements to ensure that the color and font changes are reflected.</span></span> <span data-ttu-id="116f8-348">Ujistěte se také, vynechání bitové kopie nebo vzory vykreslovat za text.</span><span class="sxs-lookup"><span data-stu-id="116f8-348">Also, ensure that images or patterns drawn behind text are omitted.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="116f8-349">Systém Windows NT 4 nemá ikonu Možnosti usnadnění v Ovládacích panelech.</span><span class="sxs-lookup"><span data-stu-id="116f8-349">Windows NT 4 does not have an Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="116f8-350">Tento postup pro změnu nastavení SystemInformation.HighContrast proto nefunguje v systému Windows NT 4.</span><span class="sxs-lookup"><span data-stu-id="116f8-350">Thus, this procedure for changing the SystemInformation.HighContrast setting does not work in Windows NT 4.</span></span>  
  
3.  <span data-ttu-id="116f8-351">Další nástroje jsou snadno dostupné pro testování usnadnění aplikace.</span><span class="sxs-lookup"><span data-stu-id="116f8-351">Other tools are readily available for testing the accessibility of an application.</span></span>  
  
4.  <span data-ttu-id="116f8-352">Chcete-li otestovat vystavení fokus klávesnice, spusťte Lupa.</span><span class="sxs-lookup"><span data-stu-id="116f8-352">To test exposing the keyboard focus, run Magnifier.</span></span> <span data-ttu-id="116f8-353">(Otevřete ho kliknutím na **spustit** nabídky, přejděte na příkaz **programy**, přejděte na příkaz **Příslušenství**, přejděte na **usnadnění**a pak klikněte na tlačítko  **Lupa**).</span><span class="sxs-lookup"><span data-stu-id="116f8-353">(To open it, click the **Start** menu, point to **Programs**, point to **Accessories**, point to **Accessibility**, and then click **Magnifier**).</span></span> <span data-ttu-id="116f8-354">Navigovat v uživatelském rozhraní, pomocí procházení tabulátorem klávesnice a myši.</span><span class="sxs-lookup"><span data-stu-id="116f8-354">Navigate the user interface using both keyboard tabbing and the mouse.</span></span> <span data-ttu-id="116f8-355">Ujistěte se, že je správně sledovat všechny navigační **Lupa**.</span><span class="sxs-lookup"><span data-stu-id="116f8-355">Ensure that all navigation is tracked properly in **Magnifier**.</span></span>  
  
5.  <span data-ttu-id="116f8-356">K testování zpřístupňuje prvky obrazovky, spusťte kontroly a použít k dosažení každý prvek myši a klávesy TAB.</span><span class="sxs-lookup"><span data-stu-id="116f8-356">To test exposing screen elements, run Inspect, and use both the mouse and the TAB key to reach each element.</span></span> <span data-ttu-id="116f8-357">Zajistěte, aby byl informace uvedené v polích pro název, stav, Role, umístění a hodnota okna kontroly srozumitelné pro uživatele pro každý objekt v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="116f8-357">Ensure that the information presented in the Name, State, Role, Location, and Value fields of the Inspect window is meaningful to the user for each object in the UI.</span></span>
