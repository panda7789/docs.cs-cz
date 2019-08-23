---
title: 'Návod: Vytvoření aplikace systému Windows s usnadněním přístupu'
ms.date: 03/30/2017
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
ms.openlocfilehash: 5768177401504f4776a34e499d07b7600597175a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957195"
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a><span data-ttu-id="3f256-102">Návod: Vytvoření aplikace systému Windows s usnadněním přístupu</span><span class="sxs-lookup"><span data-stu-id="3f256-102">Walkthrough: Creating an Accessible Windows-based Application</span></span>

<span data-ttu-id="3f256-103">Vytváření přístupných aplikací má zásadní dopad na firmu.</span><span class="sxs-lookup"><span data-stu-id="3f256-103">Creating an accessible application has important business implications.</span></span> <span data-ttu-id="3f256-104">Mnoho vlád má předpisy pro usnadnění nákupu softwaru.</span><span class="sxs-lookup"><span data-stu-id="3f256-104">Many governments have accessibility regulations for software purchase.</span></span> <span data-ttu-id="3f256-105">Logo Certified for Windows zahrnuje požadavky na usnadnění přístupu.</span><span class="sxs-lookup"><span data-stu-id="3f256-105">The Certified for Windows logo includes accessibility requirements.</span></span> <span data-ttu-id="3f256-106">Dostupnost softwaru má vliv na odhadované 30 000 000 obyvatele samotného USA, mnoho z nich potenciálních zákazníků.</span><span class="sxs-lookup"><span data-stu-id="3f256-106">An estimated 30 million residents of the U.S. alone, many of them potential customers, are affected by the accessibility of software.</span></span>

<span data-ttu-id="3f256-107">Tento návod bude řešit pět požadavků na přístupnost pro logo Certified for Windows.</span><span class="sxs-lookup"><span data-stu-id="3f256-107">This walkthrough will address the five accessibility requirements for the Certified for Windows logo.</span></span> <span data-ttu-id="3f256-108">V souladu s těmito požadavky bude dostupná aplikace:</span><span class="sxs-lookup"><span data-stu-id="3f256-108">According to these requirements, an accessible application will:</span></span>

- <span data-ttu-id="3f256-109">Podporuje nastavení velikosti, barvy, písma a vstupu ovládacích panelů.</span><span class="sxs-lookup"><span data-stu-id="3f256-109">Support Control Panel size, color, font, and input settings.</span></span> <span data-ttu-id="3f256-110">Panel nabídek, záhlaví, ohraničení a stavový řádek se změní, když uživatel změní nastavení ovládacího panelu.</span><span class="sxs-lookup"><span data-stu-id="3f256-110">The menu bar, title bar, borders, and status bar will all resize themselves when the user changes the control panel settings.</span></span> <span data-ttu-id="3f256-111">V této aplikaci nejsou vyžadovány žádné další změny ovládacích prvků nebo kódu.</span><span class="sxs-lookup"><span data-stu-id="3f256-111">No additional changes to the controls or code are required in this application.</span></span>

- <span data-ttu-id="3f256-112">Podpora režimu Vysoký kontrast.</span><span class="sxs-lookup"><span data-stu-id="3f256-112">Support High Contrast mode.</span></span>

- <span data-ttu-id="3f256-113">Poskytněte zdokumentovanému přístupu ke všem funkcím klávesnici.</span><span class="sxs-lookup"><span data-stu-id="3f256-113">Provide documented keyboard access to all features.</span></span>

- <span data-ttu-id="3f256-114">Vizuálně a programově vystavit polohu fokusu klávesnice</span><span class="sxs-lookup"><span data-stu-id="3f256-114">Expose location of the keyboard focus visually and programmatically.</span></span>

- <span data-ttu-id="3f256-115">Nevytvářejte důležité informace pouhým zvukem.</span><span class="sxs-lookup"><span data-stu-id="3f256-115">Avoid conveying important information by sound alone.</span></span>

<span data-ttu-id="3f256-116">Další informace najdete v tématu [prostředky pro návrh aplikací](/visualstudio/ide/reference/resources-for-designing-accessible-applications), které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="3f256-116">For more information, see [Resources for Designing Accessible Applications](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span></span>

<span data-ttu-id="3f256-117">Informace o podpoře různých rozložení klávesnice najdete v tématu [osvědčené postupy pro vývoj aplikací připravených pro použití ve světě](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span><span class="sxs-lookup"><span data-stu-id="3f256-117">For information on supporting varying keyboard layouts, see [Best Practices for Developing World-Ready Applications](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="3f256-118">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="3f256-118">Creating the Project</span></span>

<span data-ttu-id="3f256-119">Tento návod vytvoří uživatelské rozhraní pro aplikaci, která přijímá Pizza objednávky.</span><span class="sxs-lookup"><span data-stu-id="3f256-119">This walkthrough creates the user interface for an application that takes pizza orders.</span></span> <span data-ttu-id="3f256-120">Skládá se z <xref:System.Windows.Forms.TextBox> pro jméno zákazníka <xref:System.Windows.Forms.RadioButton> , skupina pro výběr velikosti Pizza, <xref:System.Windows.Forms.CheckedListBox> pro výběr toppings, dva ovládací prvky tlačítka s popiskem Order a Cancel a nabídka s příkazem Exit.</span><span class="sxs-lookup"><span data-stu-id="3f256-120">It consists of a <xref:System.Windows.Forms.TextBox> for the customer's name, a <xref:System.Windows.Forms.RadioButton> group to select the pizza size, a <xref:System.Windows.Forms.CheckedListBox> for selecting the toppings, two Button controls labeled Order and Cancel, and a Menu with an Exit command.</span></span>

<span data-ttu-id="3f256-121">Uživatel zadá jméno zákazníka, velikost Pizza a požadované toppings.</span><span class="sxs-lookup"><span data-stu-id="3f256-121">The user enters the customer's name, the size of the pizza, and the toppings desired.</span></span> <span data-ttu-id="3f256-122">Když uživatel klikne na tlačítko objednávka, v okně se zprávou se zobrazí souhrn objednávky a jeho nákladů a ovládací prvky budou vymazány a připraveny pro další objednávku.</span><span class="sxs-lookup"><span data-stu-id="3f256-122">When the user clicks the Order button, a summary of the order and its cost are displayed in a message box and the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="3f256-123">Když uživatel klikne na tlačítko Storno, ovládací prvky se vymažou a připraví k dalšímu pořadí.</span><span class="sxs-lookup"><span data-stu-id="3f256-123">When the user clicks the Cancel button, the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="3f256-124">Když uživatel klikne na položku nabídky Exit, program se zavře.</span><span class="sxs-lookup"><span data-stu-id="3f256-124">When the user clicks the Exit menu item, the program closes.</span></span>

<span data-ttu-id="3f256-125">Důrazem na tento návod není kód pro systém maloobchodních objednávek, ale přístupnost uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3f256-125">The emphasis of this walkthrough is not the code for a retail order system, but the accessibility of the user interface.</span></span> <span data-ttu-id="3f256-126">Návod ukazuje funkce přístupnosti několika často používaných ovládacích prvků, včetně tlačítek, přepínačů, textových polí a popisků.</span><span class="sxs-lookup"><span data-stu-id="3f256-126">The walkthrough demonstrates the accessibility features of several frequently used controls, including buttons, radio buttons, text boxes, and labels.</span></span>

#### <a name="to-begin-making-the-application"></a><span data-ttu-id="3f256-127">Zahájení provádění aplikace</span><span class="sxs-lookup"><span data-stu-id="3f256-127">To begin making the application</span></span>

- <span data-ttu-id="3f256-128">Vytvořte novou aplikaci pro Windows v Visual Basic nebo vizuálu C#.</span><span class="sxs-lookup"><span data-stu-id="3f256-128">Create a new Windows Application in Visual Basic or Visual C#.</span></span> <span data-ttu-id="3f256-129">Pojmenujte projekt **PizzaOrder**.</span><span class="sxs-lookup"><span data-stu-id="3f256-129">Name the project **PizzaOrder**.</span></span> <span data-ttu-id="3f256-130">(Podrobnosti najdete v tématu [vytváření nových řešení a projektů](/visualstudio/ide/creating-solutions-and-projects).)</span><span class="sxs-lookup"><span data-stu-id="3f256-130">(For details see [Creating New Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).)</span></span>

## <a name="adding-the-controls-to-the-form"></a><span data-ttu-id="3f256-131">Přidání ovládacích prvků do formuláře</span><span class="sxs-lookup"><span data-stu-id="3f256-131">Adding the Controls to the Form</span></span>

<span data-ttu-id="3f256-132">Při přidávání ovládacích prvků do formuláře mějte na paměti následující pokyny, jak zpřístupnit aplikaci, která je k dispozici:</span><span class="sxs-lookup"><span data-stu-id="3f256-132">When adding the controls to a form, keep in mind the following guidelines to make an accessible application:</span></span>

- <span data-ttu-id="3f256-133">Nastavte vlastnosti <xref:System.Windows.Forms.Control.AccessibleName%2A>a. <xref:System.Windows.Forms.Control.AccessibleDescription%2A></span><span class="sxs-lookup"><span data-stu-id="3f256-133">Set the <xref:System.Windows.Forms.Control.AccessibleDescription%2A> and <xref:System.Windows.Forms.Control.AccessibleName%2A> properties.</span></span> <span data-ttu-id="3f256-134">V tomto příkladu <xref:System.Windows.Forms.Control.AccessibleRole%2A> je výchozí nastavení pro dostatek.</span><span class="sxs-lookup"><span data-stu-id="3f256-134">In this example, the Default setting for the <xref:System.Windows.Forms.Control.AccessibleRole%2A> is sufficient.</span></span> <span data-ttu-id="3f256-135">Další informace o vlastnostech přístupnosti najdete v tématu [poskytování informací o usnadnění pro ovládací prvky ve formuláři Windows](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="3f256-135">For more information on the accessibility properties, see [Providing Accessibility Information for Controls on a Windows Form](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span></span>

- <span data-ttu-id="3f256-136">Nastavte velikost písma na 10 bodů nebo větší.</span><span class="sxs-lookup"><span data-stu-id="3f256-136">Set the font size to 10 points or larger.</span></span>

  > [!NOTE]
  > <span data-ttu-id="3f256-137">Pokud nastavíte velikost písma formuláře na hodnotu 10 při spuštění, budou mít všechny ovládací prvky následně přidané do formuláře velikost písma 10.</span><span class="sxs-lookup"><span data-stu-id="3f256-137">If you set the font size of the form to 10 when you start, then all controls subsequently added to the form will have a font size of 10.</span></span>

- <span data-ttu-id="3f256-138">Ujistěte se, že všechny ovládací prvky popisek, které popisují ovládací prvek TextBox, bezprostředně předcházejí ovládacímu prvku TextBox v pořadí prvků.</span><span class="sxs-lookup"><span data-stu-id="3f256-138">Make sure any Label control that describes a TextBox control immediately precedes the TextBox control in the tab order.</span></span>

- <span data-ttu-id="3f256-139">Přidejte přístupový klíč pomocí znaku "&" na <xref:System.Windows.Forms.Control.Text%2A> vlastnost ovládacího prvku, na který uživatel může chtít přejít.</span><span class="sxs-lookup"><span data-stu-id="3f256-139">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of any control the user may want to navigate to.</span></span>

- <span data-ttu-id="3f256-140">Přidejte přístupový klíč pomocí znaku "&" na <xref:System.Windows.Forms.Control.Text%2A> vlastnost popisku, který předchází ovládacímu prvku, na který uživatel může chtít přejít.</span><span class="sxs-lookup"><span data-stu-id="3f256-140">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of the label that precedes a control that the user may want to navigate to.</span></span> <span data-ttu-id="3f256-141">Nastavte <xref:System.Windows.Forms.Label.UseMnemonic%2A> vlastnost Labels na `true`, aby se fokus nastavil na další ovládací prvek v pořadí prvků, když uživatel stiskne přístupový klíč.</span><span class="sxs-lookup"><span data-stu-id="3f256-141">Set the labels' <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`, so that the focus is set to the next control in the tab order when the user presses the access key.</span></span>

- <span data-ttu-id="3f256-142">Přidejte přístupové klíče do všech položek nabídky.</span><span class="sxs-lookup"><span data-stu-id="3f256-142">Add access keys to all menu items.</span></span>

#### <a name="to-make-your-windows-application-accessible"></a><span data-ttu-id="3f256-143">Zpřístupnění aplikace pro Windows</span><span class="sxs-lookup"><span data-stu-id="3f256-143">To make your Windows Application accessible</span></span>

- <span data-ttu-id="3f256-144">Přidejte ovládací prvky do formuláře a nastavte vlastnosti, jak je popsáno níže.</span><span class="sxs-lookup"><span data-stu-id="3f256-144">Add the controls to the form and set the properties as described below.</span></span> <span data-ttu-id="3f256-145">Podívejte se na obrázek na konci tabulky, kde najdete model uspořádání ovládacích prvků ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="3f256-145">See the picture at the end of the table for a model of how to arrange the controls on the form.</span></span>

   |<span data-ttu-id="3f256-146">Objekt</span><span class="sxs-lookup"><span data-stu-id="3f256-146">Object</span></span>|<span data-ttu-id="3f256-147">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="3f256-147">Property</span></span>|<span data-ttu-id="3f256-148">Value</span><span class="sxs-lookup"><span data-stu-id="3f256-148">Value</span></span>|
   |------------|--------------|-----------|
   |<span data-ttu-id="3f256-149">Form1</span><span class="sxs-lookup"><span data-stu-id="3f256-149">Form1</span></span>|<span data-ttu-id="3f256-150">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="3f256-150">AccessibleDescription</span></span>|<span data-ttu-id="3f256-151">Formulář objednávky</span><span class="sxs-lookup"><span data-stu-id="3f256-151">Order form</span></span>|
   ||<span data-ttu-id="3f256-152">Přístupný</span><span class="sxs-lookup"><span data-stu-id="3f256-152">AccessibleName</span></span>|<span data-ttu-id="3f256-153">Formulář objednávky</span><span class="sxs-lookup"><span data-stu-id="3f256-153">Order form</span></span>|
   ||<span data-ttu-id="3f256-154">Velikost písma</span><span class="sxs-lookup"><span data-stu-id="3f256-154">Font Size</span></span>|<span data-ttu-id="3f256-155">10</span><span class="sxs-lookup"><span data-stu-id="3f256-155">10</span></span>|
   ||<span data-ttu-id="3f256-156">Text</span><span class="sxs-lookup"><span data-stu-id="3f256-156">Text</span></span>|<span data-ttu-id="3f256-157">Formulář objednávky Pizza</span><span class="sxs-lookup"><span data-stu-id="3f256-157">Pizza Order Form</span></span>|
   |<span data-ttu-id="3f256-158">PictureBox</span><span class="sxs-lookup"><span data-stu-id="3f256-158">PictureBox</span></span>|<span data-ttu-id="3f256-159">Name</span><span class="sxs-lookup"><span data-stu-id="3f256-159">Name</span></span>|<span data-ttu-id="3f256-160">logo</span><span class="sxs-lookup"><span data-stu-id="3f256-160">logo</span></span>|
   ||<span data-ttu-id="3f256-161">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="3f256-161">AccessibleDescription</span></span>|<span data-ttu-id="3f256-162">Řez Pizza</span><span class="sxs-lookup"><span data-stu-id="3f256-162">A slice of pizza</span></span>|
   ||<span data-ttu-id="3f256-163">Přístupný</span><span class="sxs-lookup"><span data-stu-id="3f256-163">AccessibleName</span></span>|<span data-ttu-id="3f256-164">Logo společnosti</span><span class="sxs-lookup"><span data-stu-id="3f256-164">Company logo</span></span>|
   ||<span data-ttu-id="3f256-165">Image</span><span class="sxs-lookup"><span data-stu-id="3f256-165">Image</span></span>|<span data-ttu-id="3f256-166">Libovolná ikona nebo rastrový obrázek</span><span class="sxs-lookup"><span data-stu-id="3f256-166">Any icon or bitmap</span></span>|
   |<span data-ttu-id="3f256-167">Popisek</span><span class="sxs-lookup"><span data-stu-id="3f256-167">Label</span></span>|<span data-ttu-id="3f256-168">Name</span><span class="sxs-lookup"><span data-stu-id="3f256-168">Name</span></span>|<span data-ttu-id="3f256-169">companyLabel</span><span class="sxs-lookup"><span data-stu-id="3f256-169">companyLabel</span></span>|
   ||<span data-ttu-id="3f256-170">Text</span><span class="sxs-lookup"><span data-stu-id="3f256-170">Text</span></span>|<span data-ttu-id="3f256-171">Dobrá pizza</span><span class="sxs-lookup"><span data-stu-id="3f256-171">Good Pizza</span></span>|
   ||<span data-ttu-id="3f256-172">TabIndex</span><span class="sxs-lookup"><span data-stu-id="3f256-172">TabIndex</span></span>|<span data-ttu-id="3f256-173">1</span><span class="sxs-lookup"><span data-stu-id="3f256-173">1</span></span>|
   ||<span data-ttu-id="3f256-174">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="3f256-174">AccessibleDescription</span></span>|<span data-ttu-id="3f256-175">Název společnosti</span><span class="sxs-lookup"><span data-stu-id="3f256-175">Company name</span></span>|
   ||<span data-ttu-id="3f256-176">Přístupný</span><span class="sxs-lookup"><span data-stu-id="3f256-176">AccessibleName</span></span>|<span data-ttu-id="3f256-177">Název společnosti</span><span class="sxs-lookup"><span data-stu-id="3f256-177">Company name</span></span>|
   ||<span data-ttu-id="3f256-178">BackColor</span><span class="sxs-lookup"><span data-stu-id="3f256-178">Backcolor</span></span>|<span data-ttu-id="3f256-179">Modrá</span><span class="sxs-lookup"><span data-stu-id="3f256-179">Blue</span></span>|
   ||<span data-ttu-id="3f256-180">ForeColor</span><span class="sxs-lookup"><span data-stu-id="3f256-180">Forecolor</span></span>|<span data-ttu-id="3f256-181">Opatřen</span><span class="sxs-lookup"><span data-stu-id="3f256-181">Yellow</span></span>|
   ||<span data-ttu-id="3f256-182">Velikost písma</span><span class="sxs-lookup"><span data-stu-id="3f256-182">Font size</span></span>|<span data-ttu-id="3f256-183">18</span><span class="sxs-lookup"><span data-stu-id="3f256-183">18</span></span>|
   |<span data-ttu-id="3f256-184">Popisek</span><span class="sxs-lookup"><span data-stu-id="3f256-184">Label</span></span>|<span data-ttu-id="3f256-185">Name</span><span class="sxs-lookup"><span data-stu-id="3f256-185">Name</span></span>|<span data-ttu-id="3f256-186">customerLabel</span><span class="sxs-lookup"><span data-stu-id="3f256-186">customerLabel</span></span>|
   ||<span data-ttu-id="3f256-187">Text</span><span class="sxs-lookup"><span data-stu-id="3f256-187">Text</span></span>|<span data-ttu-id="3f256-188">Název &</span><span class="sxs-lookup"><span data-stu-id="3f256-188">&Name</span></span>|
   ||<span data-ttu-id="3f256-189">TabIndex</span><span class="sxs-lookup"><span data-stu-id="3f256-189">TabIndex</span></span>|<span data-ttu-id="3f256-190">2</span><span class="sxs-lookup"><span data-stu-id="3f256-190">2</span></span>|
   ||<span data-ttu-id="3f256-191">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="3f256-191">AccessibleDescription</span></span>|<span data-ttu-id="3f256-192">Popisek názvu zákazníka</span><span class="sxs-lookup"><span data-stu-id="3f256-192">Customer name label</span></span>|
   ||<span data-ttu-id="3f256-193">Přístupný</span><span class="sxs-lookup"><span data-stu-id="3f256-193">AccessibleName</span></span>|<span data-ttu-id="3f256-194">Popisek názvu zákazníka</span><span class="sxs-lookup"><span data-stu-id="3f256-194">Customer name label</span></span>|
   ||<span data-ttu-id="3f256-195">UseMnemonic</span><span class="sxs-lookup"><span data-stu-id="3f256-195">UseMnemonic</span></span>|<span data-ttu-id="3f256-196">Pravda</span><span class="sxs-lookup"><span data-stu-id="3f256-196">True</span></span>|
   |<span data-ttu-id="3f256-197">TextBox</span><span class="sxs-lookup"><span data-stu-id="3f256-197">TextBox</span></span>|<span data-ttu-id="3f256-198">Name</span><span class="sxs-lookup"><span data-stu-id="3f256-198">Name</span></span>|<span data-ttu-id="3f256-199">customerName</span><span class="sxs-lookup"><span data-stu-id="3f256-199">customerName</span></span>|
   ||<span data-ttu-id="3f256-200">Text</span><span class="sxs-lookup"><span data-stu-id="3f256-200">Text</span></span>|<span data-ttu-id="3f256-201">nTato</span><span class="sxs-lookup"><span data-stu-id="3f256-201">(none)</span></span>|
   ||<span data-ttu-id="3f256-202">TabIndex</span><span class="sxs-lookup"><span data-stu-id="3f256-202">TabIndex</span></span>|<span data-ttu-id="3f256-203">3</span><span class="sxs-lookup"><span data-stu-id="3f256-203">3</span></span>|
   ||<span data-ttu-id="3f256-204">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="3f256-204">AccessibleDescription</span></span>|<span data-ttu-id="3f256-205">Jméno zákazníka</span><span class="sxs-lookup"><span data-stu-id="3f256-205">Customer name</span></span>|
   ||<span data-ttu-id="3f256-206">Přístupný</span><span class="sxs-lookup"><span data-stu-id="3f256-206">AccessibleName</span></span>|<span data-ttu-id="3f256-207">Jméno zákazníka</span><span class="sxs-lookup"><span data-stu-id="3f256-207">Customer name</span></span>|
   |<span data-ttu-id="3f256-208">GroupBox</span><span class="sxs-lookup"><span data-stu-id="3f256-208">GroupBox</span></span>|<span data-ttu-id="3f256-209">Name</span><span class="sxs-lookup"><span data-stu-id="3f256-209">Name</span></span>|<span data-ttu-id="3f256-210">sizeOptions</span><span class="sxs-lookup"><span data-stu-id="3f256-210">sizeOptions</span></span>|
   ||<span data-ttu-id="3f256-211">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="3f256-211">AccessibleDescription</span></span>|<span data-ttu-id="3f256-212">Pizza možnosti velikosti</span><span class="sxs-lookup"><span data-stu-id="3f256-212">Pizza size options</span></span>|
   ||<span data-ttu-id="3f256-213">Přístupný</span><span class="sxs-lookup"><span data-stu-id="3f256-213">AccessibleName</span></span>|<span data-ttu-id="3f256-214">Pizza možnosti velikosti</span><span class="sxs-lookup"><span data-stu-id="3f256-214">Pizza size options</span></span>|
   ||<span data-ttu-id="3f256-215">Text</span><span class="sxs-lookup"><span data-stu-id="3f256-215">Text</span></span>|<span data-ttu-id="3f256-216">Velikost Pizza</span><span class="sxs-lookup"><span data-stu-id="3f256-216">Pizza size</span></span>|
   ||<span data-ttu-id="3f256-217">TabIndex</span><span class="sxs-lookup"><span data-stu-id="3f256-217">TabIndex</span></span>|<span data-ttu-id="3f256-218">4</span><span class="sxs-lookup"><span data-stu-id="3f256-218">4</span></span>|
   |<span data-ttu-id="3f256-219">RadioButton</span><span class="sxs-lookup"><span data-stu-id="3f256-219">RadioButton</span></span>|<span data-ttu-id="3f256-220">Name</span><span class="sxs-lookup"><span data-stu-id="3f256-220">Name</span></span>|<span data-ttu-id="3f256-221">smallPizza</span><span class="sxs-lookup"><span data-stu-id="3f256-221">smallPizza</span></span>|
   ||<span data-ttu-id="3f256-222">Text</span><span class="sxs-lookup"><span data-stu-id="3f256-222">Text</span></span>|<span data-ttu-id="3f256-223">& malý $6,00</span><span class="sxs-lookup"><span data-stu-id="3f256-223">&Small $6.00</span></span>|
   ||<span data-ttu-id="3f256-224">Zaškrtnuto</span><span class="sxs-lookup"><span data-stu-id="3f256-224">Checked</span></span>|<span data-ttu-id="3f256-225">Pravda</span><span class="sxs-lookup"><span data-stu-id="3f256-225">True</span></span>|
   ||<span data-ttu-id="3f256-226">TabIndex</span><span class="sxs-lookup"><span data-stu-id="3f256-226">TabIndex</span></span>|<span data-ttu-id="3f256-227">0</span><span class="sxs-lookup"><span data-stu-id="3f256-227">0</span></span>|
   ||<span data-ttu-id="3f256-228">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="3f256-228">AccessibleDescription</span></span>|<span data-ttu-id="3f256-229">Malé Pizza</span><span class="sxs-lookup"><span data-stu-id="3f256-229">Small pizza</span></span>|
   ||<span data-ttu-id="3f256-230">Přístupný</span><span class="sxs-lookup"><span data-stu-id="3f256-230">AccessibleName</span></span>|<span data-ttu-id="3f256-231">Malé Pizza</span><span class="sxs-lookup"><span data-stu-id="3f256-231">Small pizza</span></span>|
   |<span data-ttu-id="3f256-232">RadioButton</span><span class="sxs-lookup"><span data-stu-id="3f256-232">RadioButton</span></span>|<span data-ttu-id="3f256-233">Name</span><span class="sxs-lookup"><span data-stu-id="3f256-233">Name</span></span>|<span data-ttu-id="3f256-234">largePizza</span><span class="sxs-lookup"><span data-stu-id="3f256-234">largePizza</span></span>|
   ||<span data-ttu-id="3f256-235">Text</span><span class="sxs-lookup"><span data-stu-id="3f256-235">Text</span></span>|<span data-ttu-id="3f256-236">& velký $10,00</span><span class="sxs-lookup"><span data-stu-id="3f256-236">&Large $10.00</span></span>|
   ||<span data-ttu-id="3f256-237">TabIndex</span><span class="sxs-lookup"><span data-stu-id="3f256-237">TabIndex</span></span>|<span data-ttu-id="3f256-238">1</span><span class="sxs-lookup"><span data-stu-id="3f256-238">1</span></span>|
   ||<span data-ttu-id="3f256-239">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="3f256-239">AccessibleDescription</span></span>|<span data-ttu-id="3f256-240">Velké Pizza</span><span class="sxs-lookup"><span data-stu-id="3f256-240">Large pizza</span></span>|
   ||<span data-ttu-id="3f256-241">Přístupný</span><span class="sxs-lookup"><span data-stu-id="3f256-241">AccessibleName</span></span>|<span data-ttu-id="3f256-242">Velké Pizza</span><span class="sxs-lookup"><span data-stu-id="3f256-242">Large pizza</span></span>|
   |<span data-ttu-id="3f256-243">Popisek</span><span class="sxs-lookup"><span data-stu-id="3f256-243">Label</span></span>|<span data-ttu-id="3f256-244">Name</span><span class="sxs-lookup"><span data-stu-id="3f256-244">Name</span></span>|<span data-ttu-id="3f256-245">toppingsLabel</span><span class="sxs-lookup"><span data-stu-id="3f256-245">toppingsLabel</span></span>|
   ||<span data-ttu-id="3f256-246">Text</span><span class="sxs-lookup"><span data-stu-id="3f256-246">Text</span></span>|<span data-ttu-id="3f256-247">& toppings ($0,75)</span><span class="sxs-lookup"><span data-stu-id="3f256-247">&Toppings ($0.75 each)</span></span>|
   ||<span data-ttu-id="3f256-248">TabIndex</span><span class="sxs-lookup"><span data-stu-id="3f256-248">TabIndex</span></span>|<span data-ttu-id="3f256-249">5</span><span class="sxs-lookup"><span data-stu-id="3f256-249">5</span></span>|
   ||<span data-ttu-id="3f256-250">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="3f256-250">AccessibleDescription</span></span>|<span data-ttu-id="3f256-251">Popisek toppings</span><span class="sxs-lookup"><span data-stu-id="3f256-251">Toppings label</span></span>|
   ||<span data-ttu-id="3f256-252">Přístupný</span><span class="sxs-lookup"><span data-stu-id="3f256-252">AccessibleName</span></span>|<span data-ttu-id="3f256-253">Popisek toppings</span><span class="sxs-lookup"><span data-stu-id="3f256-253">Toppings label</span></span>|
   ||<span data-ttu-id="3f256-254">UseMnemonic</span><span class="sxs-lookup"><span data-stu-id="3f256-254">UseMnemonic</span></span>|<span data-ttu-id="3f256-255">Pravda</span><span class="sxs-lookup"><span data-stu-id="3f256-255">True</span></span>|
   |<span data-ttu-id="3f256-256">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="3f256-256">CheckedListBox</span></span>|<span data-ttu-id="3f256-257">Name</span><span class="sxs-lookup"><span data-stu-id="3f256-257">Name</span></span>|<span data-ttu-id="3f256-258">toppings</span><span class="sxs-lookup"><span data-stu-id="3f256-258">toppings</span></span>|
   ||<span data-ttu-id="3f256-259">TabIndex</span><span class="sxs-lookup"><span data-stu-id="3f256-259">TabIndex</span></span>|<span data-ttu-id="3f256-260">6</span><span class="sxs-lookup"><span data-stu-id="3f256-260">6</span></span>|
   ||<span data-ttu-id="3f256-261">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="3f256-261">AccessibleDescription</span></span>|<span data-ttu-id="3f256-262">Dostupné toppings</span><span class="sxs-lookup"><span data-stu-id="3f256-262">Available toppings</span></span>|
   ||<span data-ttu-id="3f256-263">Přístupný</span><span class="sxs-lookup"><span data-stu-id="3f256-263">AccessibleName</span></span>|<span data-ttu-id="3f256-264">Dostupné toppings</span><span class="sxs-lookup"><span data-stu-id="3f256-264">Available toppings</span></span>|
   ||<span data-ttu-id="3f256-265">Položky</span><span class="sxs-lookup"><span data-stu-id="3f256-265">Items</span></span>|<span data-ttu-id="3f256-266">Pepperoni, Uzenec, žampiony</span><span class="sxs-lookup"><span data-stu-id="3f256-266">Pepperoni, Sausage, Mushrooms</span></span>|
   |<span data-ttu-id="3f256-267">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="3f256-267">Button</span></span>|<span data-ttu-id="3f256-268">Name</span><span class="sxs-lookup"><span data-stu-id="3f256-268">Name</span></span>|<span data-ttu-id="3f256-269">pořadí</span><span class="sxs-lookup"><span data-stu-id="3f256-269">order</span></span>|
   ||<span data-ttu-id="3f256-270">Text</span><span class="sxs-lookup"><span data-stu-id="3f256-270">Text</span></span>|<span data-ttu-id="3f256-271">Pořadí &</span><span class="sxs-lookup"><span data-stu-id="3f256-271">&Order</span></span>|
   ||<span data-ttu-id="3f256-272">TabIndex</span><span class="sxs-lookup"><span data-stu-id="3f256-272">TabIndex</span></span>|<span data-ttu-id="3f256-273">7</span><span class="sxs-lookup"><span data-stu-id="3f256-273">7</span></span>|
   ||<span data-ttu-id="3f256-274">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="3f256-274">AccessibleDescription</span></span>|<span data-ttu-id="3f256-275">Celková objednávka</span><span class="sxs-lookup"><span data-stu-id="3f256-275">Total the order</span></span>|
   ||<span data-ttu-id="3f256-276">Přístupný</span><span class="sxs-lookup"><span data-stu-id="3f256-276">AccessibleName</span></span>|<span data-ttu-id="3f256-277">Celková objednávka</span><span class="sxs-lookup"><span data-stu-id="3f256-277">Total order</span></span>|
   |<span data-ttu-id="3f256-278">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="3f256-278">Button</span></span>|<span data-ttu-id="3f256-279">Name</span><span class="sxs-lookup"><span data-stu-id="3f256-279">Name</span></span>|<span data-ttu-id="3f256-280">operaci</span><span class="sxs-lookup"><span data-stu-id="3f256-280">cancel</span></span>|
   ||<span data-ttu-id="3f256-281">Text</span><span class="sxs-lookup"><span data-stu-id="3f256-281">Text</span></span>|<span data-ttu-id="3f256-282">Zrušit &</span><span class="sxs-lookup"><span data-stu-id="3f256-282">&Cancel</span></span>|
   ||<span data-ttu-id="3f256-283">TabIndex</span><span class="sxs-lookup"><span data-stu-id="3f256-283">TabIndex</span></span>|<span data-ttu-id="3f256-284">8</span><span class="sxs-lookup"><span data-stu-id="3f256-284">8</span></span>|
   ||<span data-ttu-id="3f256-285">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="3f256-285">AccessibleDescription</span></span>|<span data-ttu-id="3f256-286">Zrušit pořadí</span><span class="sxs-lookup"><span data-stu-id="3f256-286">Cancel the order</span></span>|
   ||<span data-ttu-id="3f256-287">Přístupný</span><span class="sxs-lookup"><span data-stu-id="3f256-287">AccessibleName</span></span>|<span data-ttu-id="3f256-288">Zrušit pořadí</span><span class="sxs-lookup"><span data-stu-id="3f256-288">Cancel order</span></span>|
   |<span data-ttu-id="3f256-289">MainMenu</span><span class="sxs-lookup"><span data-stu-id="3f256-289">MainMenu</span></span>|<span data-ttu-id="3f256-290">Name</span><span class="sxs-lookup"><span data-stu-id="3f256-290">Name</span></span>|<span data-ttu-id="3f256-291">theMainMenu</span><span class="sxs-lookup"><span data-stu-id="3f256-291">theMainMenu</span></span>|
   |<span data-ttu-id="3f256-292">MenuItem</span><span class="sxs-lookup"><span data-stu-id="3f256-292">MenuItem</span></span>|<span data-ttu-id="3f256-293">Name</span><span class="sxs-lookup"><span data-stu-id="3f256-293">Name</span></span>|<span data-ttu-id="3f256-294">Příkazy příkazů</span><span class="sxs-lookup"><span data-stu-id="3f256-294">fileCommands</span></span>|
   ||<span data-ttu-id="3f256-295">Text</span><span class="sxs-lookup"><span data-stu-id="3f256-295">Text</span></span>|<span data-ttu-id="3f256-296">Soubor &</span><span class="sxs-lookup"><span data-stu-id="3f256-296">&File</span></span>|
   |<span data-ttu-id="3f256-297">MenuItem</span><span class="sxs-lookup"><span data-stu-id="3f256-297">MenuItem</span></span>|<span data-ttu-id="3f256-298">Name</span><span class="sxs-lookup"><span data-stu-id="3f256-298">Name</span></span>|<span data-ttu-id="3f256-299">exitApp</span><span class="sxs-lookup"><span data-stu-id="3f256-299">exitApp</span></span>|
   ||<span data-ttu-id="3f256-300">Text</span><span class="sxs-lookup"><span data-stu-id="3f256-300">Text</span></span>|<span data-ttu-id="3f256-301">Konec E &</span><span class="sxs-lookup"><span data-stu-id="3f256-301">E&xit</span></span>|

   <span data-ttu-id="3f256-302">Formulář bude vypadat přibližně jako na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="3f256-302">Your form will look something like the following image:</span></span>

   ![Formulář pořadí Pizza s textovým polem názvu a velikostí a toppingsm výběrem.](./media/walkthrough-creating-an-accessible-windows-based-application/visual-basic-pizza-order-form.gif)

## <a name="supporting-high-contrast-mode"></a><span data-ttu-id="3f256-304">Podpora režimu Vysoký kontrast</span><span class="sxs-lookup"><span data-stu-id="3f256-304">Supporting High Contrast Mode</span></span>

<span data-ttu-id="3f256-305">Režim Vysoký kontrast je nastavení systému Windows, které zlepšuje čitelnost pomocí kontrastních barev a velikostí písem, které jsou užitečné pro uživatele s vadami postiženými uživateli.</span><span class="sxs-lookup"><span data-stu-id="3f256-305">High Contrast mode is a Windows system setting that improves readability by using contrasting colors and font sizes that are beneficial for visually impaired users.</span></span> <span data-ttu-id="3f256-306"><xref:System.Windows.Forms.SystemInformation.HighContrast%2A> Vlastnost je k dispozici pro určení, zda je nastaven režim Vysoký kontrast.</span><span class="sxs-lookup"><span data-stu-id="3f256-306">The <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> property is provided to determine whether the High Contrast mode is set.</span></span>

<span data-ttu-id="3f256-307">Pokud je `true`SystemInformation. HighContrast, měla by aplikace:</span><span class="sxs-lookup"><span data-stu-id="3f256-307">If SystemInformation.HighContrast is `true`, the application should:</span></span>

- <span data-ttu-id="3f256-308">Zobrazit všechny prvky uživatelského rozhraní pomocí barevného schématu systému</span><span class="sxs-lookup"><span data-stu-id="3f256-308">Display all user interface elements using the system color scheme</span></span>

- <span data-ttu-id="3f256-309">Vyjádření pomocí vizuálních pomůcek nebo zvuku jakékoli informace, které jsou předány barevně.</span><span class="sxs-lookup"><span data-stu-id="3f256-309">Convey by visual cues or sound any information that is conveyed through color.</span></span> <span data-ttu-id="3f256-310">Například pokud jsou konkrétní položky seznamu zvýrazněny pomocí červeného písma, můžete také přidat tučné písmo, aby měl uživatel nebarevnou hromádku, že se položky zvýrazní.</span><span class="sxs-lookup"><span data-stu-id="3f256-310">For example, if particular list items are highlighted by using a red font, you could also add bold to the font, so that the user has a non-color cue that the items are highlighted.</span></span>

- <span data-ttu-id="3f256-311">Vynechat všechny obrázky nebo vzory za textem</span><span class="sxs-lookup"><span data-stu-id="3f256-311">Omit any images or patterns behind text</span></span>

<span data-ttu-id="3f256-312">Aplikace by měla kontrolovat nastavení <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> při spuštění aplikace a reagovat na událost <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>systému.</span><span class="sxs-lookup"><span data-stu-id="3f256-312">The application should check the setting of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> when the application starts and respond to the system event <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span></span> <span data-ttu-id="3f256-313">Událost se vyvolá vždy, když se <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> změní hodnota. <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged></span><span class="sxs-lookup"><span data-stu-id="3f256-313">The <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event is raised whenever the value of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> changes.</span></span>

<span data-ttu-id="3f256-314">V naší aplikaci je `lblCompanyName`jediným prvkem, který nepoužívá nastavení systému pro barvy.</span><span class="sxs-lookup"><span data-stu-id="3f256-314">In our application, the only element that is not using the system settings for color is `lblCompanyName`.</span></span> <span data-ttu-id="3f256-315"><xref:System.Drawing.SystemColors> Třída se používá ke změně nastavení barev popisku na systémové barvy vybrané uživatelem.</span><span class="sxs-lookup"><span data-stu-id="3f256-315">The <xref:System.Drawing.SystemColors> class is used to change the color settings of the label to the user-selected system colors.</span></span>

#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a><span data-ttu-id="3f256-316">Postup povolení režimu Vysoký kontrast účinným způsobem</span><span class="sxs-lookup"><span data-stu-id="3f256-316">To enable High Contrast mode in an effective way</span></span>

1. <span data-ttu-id="3f256-317">Vytvořte metodu pro nastavení barev popisku na systémové barvy.</span><span class="sxs-lookup"><span data-stu-id="3f256-317">Create a method to set the colors of the label to the system colors.</span></span>

    ```vb
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
    ```

    ```csharp
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

2. <span data-ttu-id="3f256-318">Zavolejte proceduru v konstruktoru formuláře (`Public Sub New()` v Visual Basic a `public class Form1` v vizuálu C#). `SetColorScheme`</span><span class="sxs-lookup"><span data-stu-id="3f256-318">Call the `SetColorScheme` procedure in the form constructor (`Public Sub New()` in Visual Basic and `public class Form1` in Visual C#).</span></span> <span data-ttu-id="3f256-319">Chcete-li získat přístup k konstruktoru v Visual Basic, bude nutné rozšířit oblast označený jako **kód vygenerovaný návrhářem Windows Form**.</span><span class="sxs-lookup"><span data-stu-id="3f256-319">To access the constructor in Visual Basic, you will need to expand the region labeled **Windows Form Designer generated code**.</span></span>

    ```vb
    ' Visual Basic
    Public Sub New()
       MyBase.New()
       InitializeComponent()
       SetColorScheme()
    End Sub
    ```

    ```csharp
    // C#
    public Form1()
    {
       InitializeComponent();
       SetColorScheme();
    }
    ```

3. <span data-ttu-id="3f256-320">Vytvořte proceduru události s odpovídající signaturou, která bude reagovat <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> na událost.</span><span class="sxs-lookup"><span data-stu-id="3f256-320">Create an event procedure, with the appropriate signature, to respond to the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event.</span></span>

    ```vb
    ' Visual Basic
    Protected Sub UserPreferenceChanged(ByVal sender As Object, _
    ByVal e As Microsoft.Win32.UserPreferenceChangedEventArgs)
       SetColorScheme()
    End Sub
    ```

    ```csharp
    // C#
    public void UserPreferenceChanged(object sender,
    Microsoft.Win32.UserPreferenceChangedEventArgs e)
    {
       SetColorScheme();
    }
    ```

4. <span data-ttu-id="3f256-321">Přidejte kód do konstruktoru formuláře po volání `InitializeComponents`, pro připojení procedury události k systémové události.</span><span class="sxs-lookup"><span data-stu-id="3f256-321">Add code to the form constructor, after the call to `InitializeComponents`, to hook up the event procedure to the system event.</span></span> <span data-ttu-id="3f256-322">Tato metoda volá `SetColorScheme` proceduru.</span><span class="sxs-lookup"><span data-stu-id="3f256-322">This method calls the `SetColorScheme` procedure.</span></span>

    ```vb
    ' Visual Basic
    Public Sub New()
       MyBase.New()
       InitializeComponent()
       SetColorScheme()
       AddHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _
          AddressOf Me.UserPreferenceChanged
    End Sub
    ```

    ```csharp
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

5. <span data-ttu-id="3f256-323">Přidejte kód do metody Form <xref:System.Windows.Forms.Control.Dispose%2A> před voláním <xref:System.Windows.Forms.Control.Dispose%2A> metody základní třídy k uvolnění události při zavření aplikace.</span><span class="sxs-lookup"><span data-stu-id="3f256-323">Add code to the form <xref:System.Windows.Forms.Control.Dispose%2A> method, before the call to the <xref:System.Windows.Forms.Control.Dispose%2A> method of the base class, to release the event when the application closes.</span></span> <span data-ttu-id="3f256-324">Chcete-li <xref:System.Windows.Forms.Control.Dispose%2A> získat přístup k metodě v Visual Basic, bude nutné rozšířit oblast označený jako kód generovaný návrhářem Windows Form.</span><span class="sxs-lookup"><span data-stu-id="3f256-324">To access the <xref:System.Windows.Forms.Control.Dispose%2A> method in Visual Basic, you will need to expand the region labeled Windows Form Designer generated code.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3f256-325">Kód systémové události spouští vlákno oddělené od hlavní aplikace.</span><span class="sxs-lookup"><span data-stu-id="3f256-325">The system event code runs a thread separate from the main application.</span></span> <span data-ttu-id="3f256-326">Pokud událost neuvolníte, kód, který zaznamenáte do události, bude spuštěn i po zavření programu.</span><span class="sxs-lookup"><span data-stu-id="3f256-326">If you do not release the event, the code that you hook up to the event will run even after the program is closed.</span></span>

    ```vb
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
    ```

    ```csharp
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

6. <span data-ttu-id="3f256-327">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3f256-327">Press F5 to run the application.</span></span>

## <a name="conveying-important-information-by-means-other-than-sound"></a><span data-ttu-id="3f256-328">Předávání důležitých informací jiným způsobem než zvuk</span><span class="sxs-lookup"><span data-stu-id="3f256-328">Conveying Important Information by Means Other Than Sound</span></span>

<span data-ttu-id="3f256-329">V této aplikaci nejsou žádné informace přenášeny samotným zvukem.</span><span class="sxs-lookup"><span data-stu-id="3f256-329">In this application, no information is conveyed by sound alone.</span></span> <span data-ttu-id="3f256-330">Pokud používáte zvuk v aplikaci, měli byste informace zadat také jinými způsoby.</span><span class="sxs-lookup"><span data-stu-id="3f256-330">If you use sound in your application, then you should supply the information by some other means as well.</span></span>

#### <a name="to-supply-information-by-some-other-means-than-sound"></a><span data-ttu-id="3f256-331">Poskytnutí informací jiným způsobem než zvuk</span><span class="sxs-lookup"><span data-stu-id="3f256-331">To supply information by some other means than sound</span></span>

1. <span data-ttu-id="3f256-332">Pomocí funkce rozhraní Windows API FlashWindow nastavte záhlaví na flash.</span><span class="sxs-lookup"><span data-stu-id="3f256-332">Make the title bar flash by using the Windows API function FlashWindow.</span></span> <span data-ttu-id="3f256-333">Příklad volání funkcí rozhraní API systému Windows naleznete v tématu [Návod: Volání rozhraní API](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)systému Windows.</span><span class="sxs-lookup"><span data-stu-id="3f256-333">For an example of how to call Windows API functions, see [Walkthrough: Calling Windows APIs](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="3f256-334">Uživatel může mít povolenou službu Windows Popis systému Windows, což způsobí, že se okno při přehrání systémových zvuků prostřednictvím integrovaného mluvčího počítače změní také na flash.</span><span class="sxs-lookup"><span data-stu-id="3f256-334">The user may have the Windows SoundSentry service enabled, which will also cause the window to flash when the system sounds are played through the computer's built-in speaker.</span></span>

2. <span data-ttu-id="3f256-335">Zobrazí důležité informace v nemodálním okně, aby na ni uživatel mohl reagovat.</span><span class="sxs-lookup"><span data-stu-id="3f256-335">Display the important information in a non-modal window so that the user may respond to it.</span></span>

3. <span data-ttu-id="3f256-336">Zobrazí okno se zprávou, které získá fokus klávesnice.</span><span class="sxs-lookup"><span data-stu-id="3f256-336">Display a message box that acquires the keyboard focus.</span></span> <span data-ttu-id="3f256-337">Vyhněte se této metodě, když uživatel může napsat.</span><span class="sxs-lookup"><span data-stu-id="3f256-337">Avoid this method when the user may be typing.</span></span>

4. <span data-ttu-id="3f256-338">Zobrazí v oznamovací oblasti hlavního panelu stavový indikátor.</span><span class="sxs-lookup"><span data-stu-id="3f256-338">Display a status indicator in the status notification area of the taskbar.</span></span> <span data-ttu-id="3f256-339">Podrobnosti najdete v tématu [Přidání ikon aplikace na hlavní panel se součástí model Windows Forms NotifyIcon](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span><span class="sxs-lookup"><span data-stu-id="3f256-339">For details, see [Adding Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>

## <a name="testing-the-application"></a><span data-ttu-id="3f256-340">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="3f256-340">Testing the Application</span></span>

<span data-ttu-id="3f256-341">Před nasazením aplikace byste měli otestovat funkce přístupnosti, které jste implementovali.</span><span class="sxs-lookup"><span data-stu-id="3f256-341">Before deploying the application, you should test the accessibility features that you have implemented.</span></span>

#### <a name="to-test-accessibility-features"></a><span data-ttu-id="3f256-342">Test funkcí pro usnadnění přístupu</span><span class="sxs-lookup"><span data-stu-id="3f256-342">To test accessibility features</span></span>

1. <span data-ttu-id="3f256-343">Chcete-li otestovat přístup k klávesnici, odpojte myš a procházejte uživatelské rozhraní pro každou funkci pouze pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="3f256-343">To test keyboard access, unplug the mouse and navigate the user interface for each feature using only the keyboard.</span></span> <span data-ttu-id="3f256-344">Ujistěte se, že všechny úlohy mohou být provedeny pouze pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="3f256-344">Ensure that all tasks may be performed using the keyboard only.</span></span>

2. <span data-ttu-id="3f256-345">Chcete-li otestovat podporu Vysoký kontrast, vyberte v Ovládacích panelech ikonu Možnosti usnadnění.</span><span class="sxs-lookup"><span data-stu-id="3f256-345">To test support of High Contrast, choose the Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="3f256-346">Klikněte na kartu zobrazení a zaškrtněte políčko použít Vysoký kontrast.</span><span class="sxs-lookup"><span data-stu-id="3f256-346">Click the Display tab and select the Use High Contrast check box.</span></span> <span data-ttu-id="3f256-347">Procházejte všemi prvky uživatelského rozhraní, abyste měli jistotu, že se projeví změny barev a písem.</span><span class="sxs-lookup"><span data-stu-id="3f256-347">Navigate through all user interface elements to ensure that the color and font changes are reflected.</span></span> <span data-ttu-id="3f256-348">Také se ujistěte, že jsou vynechány obrázky nebo vzory vykreslené za textem.</span><span class="sxs-lookup"><span data-stu-id="3f256-348">Also, ensure that images or patterns drawn behind text are omitted.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3f256-349">Systém Windows NT 4 nemá ikonu možností přístupnosti v Ovládacích panelech.</span><span class="sxs-lookup"><span data-stu-id="3f256-349">Windows NT 4 does not have an Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="3f256-350">Proto tato procedura pro změnu nastavení SystemInformation. HighContrast nefunguje v systému Windows NT 4.</span><span class="sxs-lookup"><span data-stu-id="3f256-350">Thus, this procedure for changing the SystemInformation.HighContrast setting does not work in Windows NT 4.</span></span>

3. <span data-ttu-id="3f256-351">Další nástroje jsou snadno dostupné pro testování dostupnosti aplikace.</span><span class="sxs-lookup"><span data-stu-id="3f256-351">Other tools are readily available for testing the accessibility of an application.</span></span>

4. <span data-ttu-id="3f256-352">Chcete-li otestovat vystavení fokusu klávesnice, spusťte program Lupa.</span><span class="sxs-lookup"><span data-stu-id="3f256-352">To test exposing the keyboard focus, run Magnifier.</span></span> <span data-ttu-id="3f256-353">(Pokud ho chcete otevřít, klikněte na nabídku **Start** , přejděte na **programy**, přejděte na položku **příslušenství**, přejděte na položku **usnadnění**a potom klikněte na tlačítko **Lupa**).</span><span class="sxs-lookup"><span data-stu-id="3f256-353">(To open it, click the **Start** menu, point to **Programs**, point to **Accessories**, point to **Accessibility**, and then click **Magnifier**).</span></span> <span data-ttu-id="3f256-354">Navigace v uživatelském rozhraní pomocí klávesových zkratek klávesnice a myši.</span><span class="sxs-lookup"><span data-stu-id="3f256-354">Navigate the user interface using both keyboard tabbing and the mouse.</span></span> <span data-ttu-id="3f256-355">Ujistěte se, že je veškerá navigace správně sledována v **programu Lupa**.</span><span class="sxs-lookup"><span data-stu-id="3f256-355">Ensure that all navigation is tracked properly in **Magnifier**.</span></span>

5. <span data-ttu-id="3f256-356">Chcete-li otestovat vystavení prvků obrazovky, spusťte kontrolu a k dosažení každého elementu použijte myš i klávesu TAB.</span><span class="sxs-lookup"><span data-stu-id="3f256-356">To test exposing screen elements, run Inspect, and use both the mouse and the TAB key to reach each element.</span></span> <span data-ttu-id="3f256-357">Ujistěte se, že informace uvedené v polích název, stav, role, umístění a hodnota v okně Kontrola mají význam pro uživatele pro každý objekt v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3f256-357">Ensure that the information presented in the Name, State, Role, Location, and Value fields of the Inspect window is meaningful to the user for each object in the UI.</span></span>
