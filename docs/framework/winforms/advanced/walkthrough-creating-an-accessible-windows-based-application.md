---
title: 'Návod: Vytvoření aplikace systému Windows s usnadněním přístupu'
ms.date: 03/30/2017
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
ms.openlocfilehash: 6d246c56af191189fa775be3248d3099d2aa2544
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203688"
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a><span data-ttu-id="a0bfb-102">Návod: Vytvoření aplikace systému Windows s usnadněním přístupu</span><span class="sxs-lookup"><span data-stu-id="a0bfb-102">Walkthrough: Creating an Accessible Windows-based Application</span></span>
<span data-ttu-id="a0bfb-103">Vytvoření přístupné aplikace má vliv na důležitá obchodní.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-103">Creating an accessible application has important business implications.</span></span> <span data-ttu-id="a0bfb-104">Mnoha vlád mají usnadnění předpisy pro nákup softwaru.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-104">Many governments have accessibility regulations for software purchase.</span></span> <span data-ttu-id="a0bfb-105">Logo Certified pro Windows obsahuje požadavky na usnadnění přístupu.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-105">The Certified for Windows logo includes accessibility requirements.</span></span> <span data-ttu-id="a0bfb-106">Odhadované pobytem 30 milionů amerických samostatně, mnoho z nich potenciálních zákazníků, jsou ovlivněny usnadnění softwaru.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-106">An estimated 30 million residents of the U.S. alone, many of them potential customers, are affected by the accessibility of software.</span></span>  
  
 <span data-ttu-id="a0bfb-107">Tento názorný postup bude zabývat pět požadavků usnadnění přístupu pro logo Certified pro Windows.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-107">This walkthrough will address the five accessibility requirements for the Certified for Windows logo.</span></span> <span data-ttu-id="a0bfb-108">Podle těchto požadavků se dostupné aplikace:</span><span class="sxs-lookup"><span data-stu-id="a0bfb-108">According to these requirements, an accessible application will:</span></span>  
  
-   <span data-ttu-id="a0bfb-109">Podpora velikost ovládacích panelů, barvy, písma a vstupní nastavení.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-109">Support Control Panel size, color, font, and input settings.</span></span> <span data-ttu-id="a0bfb-110">Řádku nabídek, záhlaví, ohraničení a stavový řádek všechny velikost se sami když uživatel změní nastavení ovládacího panelu.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-110">The menu bar, title bar, borders, and status bar will all resize themselves when the user changes the control panel settings.</span></span> <span data-ttu-id="a0bfb-111">Nevyžaduje žádné další změny ovládací prvky nebo kód v této aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-111">No additional changes to the controls or code are required in this application.</span></span>  
  
-   <span data-ttu-id="a0bfb-112">Podporovat režim s vysokým kontrastem.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-112">Support High Contrast mode.</span></span>  
  
-   <span data-ttu-id="a0bfb-113">Zadejte zdokumentovaných klávesnici přístup ke všem funkcím.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-113">Provide documented keyboard access to all features.</span></span>  
  
-   <span data-ttu-id="a0bfb-114">Vizuálně a programově zpřístupnit umístění fokus klávesnice.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-114">Expose location of the keyboard focus visually and programmatically.</span></span>  
  
-   <span data-ttu-id="a0bfb-115">Vyhněte se předávání důležitých informací zvukovou samostatně.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-115">Avoid conveying important information by sound alone.</span></span>  
  
 <span data-ttu-id="a0bfb-116">Další informace najdete v tématu [prostředky pro návrh aplikace přístupné](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span><span class="sxs-lookup"><span data-stu-id="a0bfb-116">For more information, see [Resources for Designing Accessible Applications](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span></span>  
  
 <span data-ttu-id="a0bfb-117">Informace o podpoře proměnlivé rozložení klávesnice, naleznete v tématu [osvědčené postupy pro vývoj globalizovaných aplikací](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span><span class="sxs-lookup"><span data-stu-id="a0bfb-117">For information on supporting varying keyboard layouts, see [Best Practices for Developing World-Ready Applications](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="a0bfb-118">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="a0bfb-118">Creating the Project</span></span>  
 <span data-ttu-id="a0bfb-119">Tento návod vytvoří uživatelské rozhraní pro aplikace, která přebírá pizza objednávky.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-119">This walkthrough creates the user interface for an application that takes pizza orders.</span></span> <span data-ttu-id="a0bfb-120">Skládá se z <xref:System.Windows.Forms.TextBox> pro jméno zákazníka <xref:System.Windows.Forms.RadioButton> skupina a vyberte velikost pizza <xref:System.Windows.Forms.CheckedListBox> pro výběr toppings, dva ovládací prvky tlačítek označené jako pořadí a zrušit a nabídky pomocí příkazu pro ukončení.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-120">It consists of a <xref:System.Windows.Forms.TextBox> for the customer's name, a <xref:System.Windows.Forms.RadioButton> group to select the pizza size, a <xref:System.Windows.Forms.CheckedListBox> for selecting the toppings, two Button controls labeled Order and Cancel, and a Menu with an Exit command.</span></span>  
  
 <span data-ttu-id="a0bfb-121">Uživatel zadá název zákazníka, velikost pizza a toppings potřeby.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-121">The user enters the customer's name, the size of the pizza, and the toppings desired.</span></span> <span data-ttu-id="a0bfb-122">Když uživatel klikne na tlačítko pořadí, souhrn pořadí a její náklady jsou zobrazeny v okně se zprávou a ovládací prvky se vymažou a připravené pro další objednávku.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-122">When the user clicks the Order button, a summary of the order and its cost are displayed in a message box and the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="a0bfb-123">Když uživatel klikne na tlačítko Storno, ovládací prvky se vymažou a připravené pro další objednávku.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-123">When the user clicks the Cancel button, the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="a0bfb-124">Když uživatel klikne na položku nabídky ukončení, program se ukončí.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-124">When the user clicks the Exit menu item, the program closes.</span></span>  
  
 <span data-ttu-id="a0bfb-125">Zvýraznění tohoto názorného postupu není kód systému prodejní objednávky, ale usnadnění přístupu uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-125">The emphasis of this walkthrough is not the code for a retail order system, but the accessibility of the user interface.</span></span> <span data-ttu-id="a0bfb-126">Návodu ukazuje, že funkce pro usnadnění přístupu z několika často používané ovládací prvky, včetně tlačítek, přepínacích tlačítek, textová pole a popisky.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-126">The walkthrough demonstrates the accessibility features of several frequently used controls, including buttons, radio buttons, text boxes, and labels.</span></span>  
  
#### <a name="to-begin-making-the-application"></a><span data-ttu-id="a0bfb-127">Chcete-li začít vytvářet aplikace</span><span class="sxs-lookup"><span data-stu-id="a0bfb-127">To begin making the application</span></span>  
  
-   <span data-ttu-id="a0bfb-128">Vytvoření nové aplikace Windows v jazyce Visual Basic nebo Visual C#.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-128">Create a new Windows Application in Visual Basic or Visual C#.</span></span> <span data-ttu-id="a0bfb-129">Pojmenujte projekt **PizzaOrder**.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-129">Name the project **PizzaOrder**.</span></span> <span data-ttu-id="a0bfb-130">(Podrobnosti najdete v tématu [vytváří se nová řešení a projekty](/visualstudio/ide/creating-solutions-and-projects).)</span><span class="sxs-lookup"><span data-stu-id="a0bfb-130">(For details see [Creating New Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).)</span></span>  
  
## <a name="adding-the-controls-to-the-form"></a><span data-ttu-id="a0bfb-131">Přidání ovládacích prvků do formuláře</span><span class="sxs-lookup"><span data-stu-id="a0bfb-131">Adding the Controls to the Form</span></span>  
 <span data-ttu-id="a0bfb-132">Když přidáváte ovládací prvky do formuláře, mějte na paměti následující pokyny, aby dostupné aplikace:</span><span class="sxs-lookup"><span data-stu-id="a0bfb-132">When adding the controls to a form, keep in mind the following guidelines to make an accessible application:</span></span>  
  
-   <span data-ttu-id="a0bfb-133">Nastavte <xref:System.Windows.Forms.Control.AccessibleDescription%2A> a <xref:System.Windows.Forms.Control.AccessibleName%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-133">Set the <xref:System.Windows.Forms.Control.AccessibleDescription%2A> and <xref:System.Windows.Forms.Control.AccessibleName%2A> properties.</span></span> <span data-ttu-id="a0bfb-134">V tomto příkladu ve výchozím nastavení <xref:System.Windows.Forms.Control.AccessibleRole%2A> je dostačující.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-134">In this example, the Default setting for the <xref:System.Windows.Forms.Control.AccessibleRole%2A> is sufficient.</span></span> <span data-ttu-id="a0bfb-135">Další informace o vlastnostech usnadnění, naleznete v tématu [poskytování informací o usnadnění pro ovládací prvky ve formuláři Windows](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="a0bfb-135">For more information on the accessibility properties, see [Providing Accessibility Information for Controls on a Windows Form](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span></span>  
  
-   <span data-ttu-id="a0bfb-136">Nastavte velikost písma 10 bodů nebo větší.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-136">Set the font size to 10 points or larger.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a0bfb-137">Pokud nastavíte velikost písma formuláře na 10 při spuštění, bude mít všechny ovládací prvky do formuláře přidán následně velikost písma 10.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-137">If you set the font size of the form to 10 when you start, then all controls subsequently added to the form will have a font size of 10.</span></span>  
  
-   <span data-ttu-id="a0bfb-138">Zajistěte, aby libovolný ovládací prvek popisek, který popisuje ovládací prvek textového pole bezprostředně předchází ovládacího prvku textového pole v pořadí.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-138">Make sure any Label control that describes a TextBox control immediately precedes the TextBox control in the tab order.</span></span>  
  
-   <span data-ttu-id="a0bfb-139">Přidat přístupový kód, používat "&" znak <xref:System.Windows.Forms.Control.Text%2A> vlastnost libovolný ovládací prvek, uživatel může chtít přejít na.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-139">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of any control the user may want to navigate to.</span></span>  
  
-   <span data-ttu-id="a0bfb-140">Přidat přístupový kód, používat "&" znak <xref:System.Windows.Forms.Control.Text%2A> popisku, který předchází ovládací prvek, který uživatel může chtít přejít na.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-140">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of the label that precedes a control that the user may want to navigate to.</span></span> <span data-ttu-id="a0bfb-141">Nastavit jmenovky <xref:System.Windows.Forms.Label.UseMnemonic%2A> vlastnost `true`, tak, aby fokus na další ovládací prvek v pořadí karet při stisknutí přístupové klávesy.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-141">Set the labels' <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`, so that the focus is set to the next control in the tab order when the user presses the access key.</span></span>  
  
-   <span data-ttu-id="a0bfb-142">Přidáte všechny položky nabídky přístupové klíče.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-142">Add access keys to all menu items.</span></span>  
  
#### <a name="to-make-your-windows-application-accessible"></a><span data-ttu-id="a0bfb-143">Chcete-li zpřístupnit svoji aplikaci Windows</span><span class="sxs-lookup"><span data-stu-id="a0bfb-143">To make your Windows Application accessible</span></span>  
  
-   <span data-ttu-id="a0bfb-144">Přidat ovládací prvky do formuláře a nastavte vlastnosti, jak je popsáno níže.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-144">Add the controls to the form and set the properties as described below.</span></span> <span data-ttu-id="a0bfb-145">Podívejte se na obrázku na konec tabulky modelu o tom, jak uspořádat ovládací prvky ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-145">See the picture at the end of the table for a model of how to arrange the controls on the form.</span></span>  
  
    |<span data-ttu-id="a0bfb-146">Objekt</span><span class="sxs-lookup"><span data-stu-id="a0bfb-146">Object</span></span>|<span data-ttu-id="a0bfb-147">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="a0bfb-147">Property</span></span>|<span data-ttu-id="a0bfb-148">Value</span><span class="sxs-lookup"><span data-stu-id="a0bfb-148">Value</span></span>|  
    |------------|--------------|-----------|  
    |<span data-ttu-id="a0bfb-149">Form1</span><span class="sxs-lookup"><span data-stu-id="a0bfb-149">Form1</span></span>|<span data-ttu-id="a0bfb-150">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="a0bfb-150">AccessibleDescription</span></span>|<span data-ttu-id="a0bfb-151">Formulář objednávky</span><span class="sxs-lookup"><span data-stu-id="a0bfb-151">Order form</span></span>|  
    ||<span data-ttu-id="a0bfb-152">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="a0bfb-152">AccessibleName</span></span>|<span data-ttu-id="a0bfb-153">Formulář objednávky</span><span class="sxs-lookup"><span data-stu-id="a0bfb-153">Order form</span></span>|  
    ||<span data-ttu-id="a0bfb-154">Velikost písma</span><span class="sxs-lookup"><span data-stu-id="a0bfb-154">Font Size</span></span>|<span data-ttu-id="a0bfb-155">10</span><span class="sxs-lookup"><span data-stu-id="a0bfb-155">10</span></span>|  
    ||<span data-ttu-id="a0bfb-156">Text</span><span class="sxs-lookup"><span data-stu-id="a0bfb-156">Text</span></span>|<span data-ttu-id="a0bfb-157">Formulář objednávky pizza</span><span class="sxs-lookup"><span data-stu-id="a0bfb-157">Pizza Order Form</span></span>|  
    |<span data-ttu-id="a0bfb-158">PictureBox</span><span class="sxs-lookup"><span data-stu-id="a0bfb-158">PictureBox</span></span>|<span data-ttu-id="a0bfb-159">Name</span><span class="sxs-lookup"><span data-stu-id="a0bfb-159">Name</span></span>|<span data-ttu-id="a0bfb-160">logo</span><span class="sxs-lookup"><span data-stu-id="a0bfb-160">logo</span></span>|  
    ||<span data-ttu-id="a0bfb-161">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="a0bfb-161">AccessibleDescription</span></span>|<span data-ttu-id="a0bfb-162">Řez pizza</span><span class="sxs-lookup"><span data-stu-id="a0bfb-162">A slice of pizza</span></span>|  
    ||<span data-ttu-id="a0bfb-163">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="a0bfb-163">AccessibleName</span></span>|<span data-ttu-id="a0bfb-164">Logo společnosti</span><span class="sxs-lookup"><span data-stu-id="a0bfb-164">Company logo</span></span>|  
    ||<span data-ttu-id="a0bfb-165">Image</span><span class="sxs-lookup"><span data-stu-id="a0bfb-165">Image</span></span>|<span data-ttu-id="a0bfb-166">Žádné ikona nebo rastrový obrázek</span><span class="sxs-lookup"><span data-stu-id="a0bfb-166">Any icon or bitmap</span></span>|  
    |<span data-ttu-id="a0bfb-167">Popisek</span><span class="sxs-lookup"><span data-stu-id="a0bfb-167">Label</span></span>|<span data-ttu-id="a0bfb-168">Name</span><span class="sxs-lookup"><span data-stu-id="a0bfb-168">Name</span></span>|<span data-ttu-id="a0bfb-169">companyLabel</span><span class="sxs-lookup"><span data-stu-id="a0bfb-169">companyLabel</span></span>|  
    ||<span data-ttu-id="a0bfb-170">Text</span><span class="sxs-lookup"><span data-stu-id="a0bfb-170">Text</span></span>|<span data-ttu-id="a0bfb-171">Good Pizza</span><span class="sxs-lookup"><span data-stu-id="a0bfb-171">Good Pizza</span></span>|  
    ||<span data-ttu-id="a0bfb-172">TabIndex</span><span class="sxs-lookup"><span data-stu-id="a0bfb-172">TabIndex</span></span>|<span data-ttu-id="a0bfb-173">1</span><span class="sxs-lookup"><span data-stu-id="a0bfb-173">1</span></span>|  
    ||<span data-ttu-id="a0bfb-174">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="a0bfb-174">AccessibleDescription</span></span>|<span data-ttu-id="a0bfb-175">Název společnosti</span><span class="sxs-lookup"><span data-stu-id="a0bfb-175">Company name</span></span>|  
    ||<span data-ttu-id="a0bfb-176">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="a0bfb-176">AccessibleName</span></span>|<span data-ttu-id="a0bfb-177">Název společnosti</span><span class="sxs-lookup"><span data-stu-id="a0bfb-177">Company name</span></span>|  
    ||<span data-ttu-id="a0bfb-178">Barva pozadí</span><span class="sxs-lookup"><span data-stu-id="a0bfb-178">Backcolor</span></span>|<span data-ttu-id="a0bfb-179">Modrá</span><span class="sxs-lookup"><span data-stu-id="a0bfb-179">Blue</span></span>|  
    ||<span data-ttu-id="a0bfb-180">Barva popředí</span><span class="sxs-lookup"><span data-stu-id="a0bfb-180">Forecolor</span></span>|<span data-ttu-id="a0bfb-181">Žlutá</span><span class="sxs-lookup"><span data-stu-id="a0bfb-181">Yellow</span></span>|  
    ||<span data-ttu-id="a0bfb-182">Velikost písma</span><span class="sxs-lookup"><span data-stu-id="a0bfb-182">Font size</span></span>|<span data-ttu-id="a0bfb-183">18</span><span class="sxs-lookup"><span data-stu-id="a0bfb-183">18</span></span>|  
    |<span data-ttu-id="a0bfb-184">Popisek</span><span class="sxs-lookup"><span data-stu-id="a0bfb-184">Label</span></span>|<span data-ttu-id="a0bfb-185">Name</span><span class="sxs-lookup"><span data-stu-id="a0bfb-185">Name</span></span>|<span data-ttu-id="a0bfb-186">customerLabel</span><span class="sxs-lookup"><span data-stu-id="a0bfb-186">customerLabel</span></span>|  
    ||<span data-ttu-id="a0bfb-187">Text</span><span class="sxs-lookup"><span data-stu-id="a0bfb-187">Text</span></span>|<span data-ttu-id="a0bfb-188">& název</span><span class="sxs-lookup"><span data-stu-id="a0bfb-188">&Name</span></span>|  
    ||<span data-ttu-id="a0bfb-189">TabIndex</span><span class="sxs-lookup"><span data-stu-id="a0bfb-189">TabIndex</span></span>|<span data-ttu-id="a0bfb-190">2</span><span class="sxs-lookup"><span data-stu-id="a0bfb-190">2</span></span>|  
    ||<span data-ttu-id="a0bfb-191">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="a0bfb-191">AccessibleDescription</span></span>|<span data-ttu-id="a0bfb-192">Popisek názvu zákazníka</span><span class="sxs-lookup"><span data-stu-id="a0bfb-192">Customer name label</span></span>|  
    ||<span data-ttu-id="a0bfb-193">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="a0bfb-193">AccessibleName</span></span>|<span data-ttu-id="a0bfb-194">Popisek názvu zákazníka</span><span class="sxs-lookup"><span data-stu-id="a0bfb-194">Customer name label</span></span>|  
    ||<span data-ttu-id="a0bfb-195">Usemnemonic –</span><span class="sxs-lookup"><span data-stu-id="a0bfb-195">UseMnemonic</span></span>|<span data-ttu-id="a0bfb-196">Pravda</span><span class="sxs-lookup"><span data-stu-id="a0bfb-196">True</span></span>|  
    |<span data-ttu-id="a0bfb-197">TextBox</span><span class="sxs-lookup"><span data-stu-id="a0bfb-197">TextBox</span></span>|<span data-ttu-id="a0bfb-198">Name</span><span class="sxs-lookup"><span data-stu-id="a0bfb-198">Name</span></span>|<span data-ttu-id="a0bfb-199">customerName</span><span class="sxs-lookup"><span data-stu-id="a0bfb-199">customerName</span></span>|  
    ||<span data-ttu-id="a0bfb-200">Text</span><span class="sxs-lookup"><span data-stu-id="a0bfb-200">Text</span></span>|<span data-ttu-id="a0bfb-201">(žádné)</span><span class="sxs-lookup"><span data-stu-id="a0bfb-201">(none)</span></span>|  
    ||<span data-ttu-id="a0bfb-202">TabIndex</span><span class="sxs-lookup"><span data-stu-id="a0bfb-202">TabIndex</span></span>|<span data-ttu-id="a0bfb-203">3</span><span class="sxs-lookup"><span data-stu-id="a0bfb-203">3</span></span>|  
    ||<span data-ttu-id="a0bfb-204">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="a0bfb-204">AccessibleDescription</span></span>|<span data-ttu-id="a0bfb-205">Jméno zákazníka</span><span class="sxs-lookup"><span data-stu-id="a0bfb-205">Customer name</span></span>|  
    ||<span data-ttu-id="a0bfb-206">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="a0bfb-206">AccessibleName</span></span>|<span data-ttu-id="a0bfb-207">Jméno zákazníka</span><span class="sxs-lookup"><span data-stu-id="a0bfb-207">Customer name</span></span>|  
    |<span data-ttu-id="a0bfb-208">GroupBox</span><span class="sxs-lookup"><span data-stu-id="a0bfb-208">GroupBox</span></span>|<span data-ttu-id="a0bfb-209">Name</span><span class="sxs-lookup"><span data-stu-id="a0bfb-209">Name</span></span>|<span data-ttu-id="a0bfb-210">sizeOptions</span><span class="sxs-lookup"><span data-stu-id="a0bfb-210">sizeOptions</span></span>|  
    ||<span data-ttu-id="a0bfb-211">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="a0bfb-211">AccessibleDescription</span></span>|<span data-ttu-id="a0bfb-212">Možnosti velikosti pizza</span><span class="sxs-lookup"><span data-stu-id="a0bfb-212">Pizza size options</span></span>|  
    ||<span data-ttu-id="a0bfb-213">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="a0bfb-213">AccessibleName</span></span>|<span data-ttu-id="a0bfb-214">Možnosti velikosti pizza</span><span class="sxs-lookup"><span data-stu-id="a0bfb-214">Pizza size options</span></span>|  
    ||<span data-ttu-id="a0bfb-215">Text</span><span class="sxs-lookup"><span data-stu-id="a0bfb-215">Text</span></span>|<span data-ttu-id="a0bfb-216">Velikost pizza</span><span class="sxs-lookup"><span data-stu-id="a0bfb-216">Pizza size</span></span>|  
    ||<span data-ttu-id="a0bfb-217">TabIndex</span><span class="sxs-lookup"><span data-stu-id="a0bfb-217">TabIndex</span></span>|<span data-ttu-id="a0bfb-218">4</span><span class="sxs-lookup"><span data-stu-id="a0bfb-218">4</span></span>|  
    |<span data-ttu-id="a0bfb-219">RadioButton</span><span class="sxs-lookup"><span data-stu-id="a0bfb-219">RadioButton</span></span>|<span data-ttu-id="a0bfb-220">Name</span><span class="sxs-lookup"><span data-stu-id="a0bfb-220">Name</span></span>|<span data-ttu-id="a0bfb-221">smallPizza</span><span class="sxs-lookup"><span data-stu-id="a0bfb-221">smallPizza</span></span>|  
    ||<span data-ttu-id="a0bfb-222">Text</span><span class="sxs-lookup"><span data-stu-id="a0bfb-222">Text</span></span>|<span data-ttu-id="a0bfb-223">& malé $6.00</span><span class="sxs-lookup"><span data-stu-id="a0bfb-223">&Small $6.00</span></span>|  
    ||<span data-ttu-id="a0bfb-224">Zaškrtnuto</span><span class="sxs-lookup"><span data-stu-id="a0bfb-224">Checked</span></span>|<span data-ttu-id="a0bfb-225">Pravda</span><span class="sxs-lookup"><span data-stu-id="a0bfb-225">True</span></span>|  
    ||<span data-ttu-id="a0bfb-226">TabIndex</span><span class="sxs-lookup"><span data-stu-id="a0bfb-226">TabIndex</span></span>|<span data-ttu-id="a0bfb-227">0</span><span class="sxs-lookup"><span data-stu-id="a0bfb-227">0</span></span>|  
    ||<span data-ttu-id="a0bfb-228">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="a0bfb-228">AccessibleDescription</span></span>|<span data-ttu-id="a0bfb-229">Malé pizza</span><span class="sxs-lookup"><span data-stu-id="a0bfb-229">Small pizza</span></span>|  
    ||<span data-ttu-id="a0bfb-230">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="a0bfb-230">AccessibleName</span></span>|<span data-ttu-id="a0bfb-231">Malé pizza</span><span class="sxs-lookup"><span data-stu-id="a0bfb-231">Small pizza</span></span>|  
    |<span data-ttu-id="a0bfb-232">RadioButton</span><span class="sxs-lookup"><span data-stu-id="a0bfb-232">RadioButton</span></span>|<span data-ttu-id="a0bfb-233">Name</span><span class="sxs-lookup"><span data-stu-id="a0bfb-233">Name</span></span>|<span data-ttu-id="a0bfb-234">largePizza</span><span class="sxs-lookup"><span data-stu-id="a0bfb-234">largePizza</span></span>|  
    ||<span data-ttu-id="a0bfb-235">Text</span><span class="sxs-lookup"><span data-stu-id="a0bfb-235">Text</span></span>|<span data-ttu-id="a0bfb-236">& velké 10,00 USD</span><span class="sxs-lookup"><span data-stu-id="a0bfb-236">&Large $10.00</span></span>|  
    ||<span data-ttu-id="a0bfb-237">TabIndex</span><span class="sxs-lookup"><span data-stu-id="a0bfb-237">TabIndex</span></span>|<span data-ttu-id="a0bfb-238">1</span><span class="sxs-lookup"><span data-stu-id="a0bfb-238">1</span></span>|  
    ||<span data-ttu-id="a0bfb-239">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="a0bfb-239">AccessibleDescription</span></span>|<span data-ttu-id="a0bfb-240">Velké pizza</span><span class="sxs-lookup"><span data-stu-id="a0bfb-240">Large pizza</span></span>|  
    ||<span data-ttu-id="a0bfb-241">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="a0bfb-241">AccessibleName</span></span>|<span data-ttu-id="a0bfb-242">Velké pizza</span><span class="sxs-lookup"><span data-stu-id="a0bfb-242">Large pizza</span></span>|  
    |<span data-ttu-id="a0bfb-243">Popisek</span><span class="sxs-lookup"><span data-stu-id="a0bfb-243">Label</span></span>|<span data-ttu-id="a0bfb-244">Name</span><span class="sxs-lookup"><span data-stu-id="a0bfb-244">Name</span></span>|<span data-ttu-id="a0bfb-245">toppingsLabel</span><span class="sxs-lookup"><span data-stu-id="a0bfb-245">toppingsLabel</span></span>|  
    ||<span data-ttu-id="a0bfb-246">Text</span><span class="sxs-lookup"><span data-stu-id="a0bfb-246">Text</span></span>|<span data-ttu-id="a0bfb-247">& toppings ($0,75 každý)</span><span class="sxs-lookup"><span data-stu-id="a0bfb-247">&Toppings ($0.75 each)</span></span>|  
    ||<span data-ttu-id="a0bfb-248">TabIndex</span><span class="sxs-lookup"><span data-stu-id="a0bfb-248">TabIndex</span></span>|<span data-ttu-id="a0bfb-249">5</span><span class="sxs-lookup"><span data-stu-id="a0bfb-249">5</span></span>|  
    ||<span data-ttu-id="a0bfb-250">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="a0bfb-250">AccessibleDescription</span></span>|<span data-ttu-id="a0bfb-251">Popisek toppings</span><span class="sxs-lookup"><span data-stu-id="a0bfb-251">Toppings label</span></span>|  
    ||<span data-ttu-id="a0bfb-252">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="a0bfb-252">AccessibleName</span></span>|<span data-ttu-id="a0bfb-253">Popisek toppings</span><span class="sxs-lookup"><span data-stu-id="a0bfb-253">Toppings label</span></span>|  
    ||<span data-ttu-id="a0bfb-254">Usemnemonic –</span><span class="sxs-lookup"><span data-stu-id="a0bfb-254">UseMnemonic</span></span>|<span data-ttu-id="a0bfb-255">Pravda</span><span class="sxs-lookup"><span data-stu-id="a0bfb-255">True</span></span>|  
    |<span data-ttu-id="a0bfb-256">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="a0bfb-256">CheckedListBox</span></span>|<span data-ttu-id="a0bfb-257">Name</span><span class="sxs-lookup"><span data-stu-id="a0bfb-257">Name</span></span>|<span data-ttu-id="a0bfb-258">toppings</span><span class="sxs-lookup"><span data-stu-id="a0bfb-258">toppings</span></span>|  
    ||<span data-ttu-id="a0bfb-259">TabIndex</span><span class="sxs-lookup"><span data-stu-id="a0bfb-259">TabIndex</span></span>|<span data-ttu-id="a0bfb-260">6</span><span class="sxs-lookup"><span data-stu-id="a0bfb-260">6</span></span>|  
    ||<span data-ttu-id="a0bfb-261">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="a0bfb-261">AccessibleDescription</span></span>|<span data-ttu-id="a0bfb-262">K dispozici toppings</span><span class="sxs-lookup"><span data-stu-id="a0bfb-262">Available toppings</span></span>|  
    ||<span data-ttu-id="a0bfb-263">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="a0bfb-263">AccessibleName</span></span>|<span data-ttu-id="a0bfb-264">K dispozici toppings</span><span class="sxs-lookup"><span data-stu-id="a0bfb-264">Available toppings</span></span>|  
    ||<span data-ttu-id="a0bfb-265">Položky</span><span class="sxs-lookup"><span data-stu-id="a0bfb-265">Items</span></span>|<span data-ttu-id="a0bfb-266">Pepperoni salám, hub</span><span class="sxs-lookup"><span data-stu-id="a0bfb-266">Pepperoni, Sausage, Mushrooms</span></span>|  
    |<span data-ttu-id="a0bfb-267">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="a0bfb-267">Button</span></span>|<span data-ttu-id="a0bfb-268">Name</span><span class="sxs-lookup"><span data-stu-id="a0bfb-268">Name</span></span>|<span data-ttu-id="a0bfb-269">pořadí</span><span class="sxs-lookup"><span data-stu-id="a0bfb-269">order</span></span>|  
    ||<span data-ttu-id="a0bfb-270">Text</span><span class="sxs-lookup"><span data-stu-id="a0bfb-270">Text</span></span>|<span data-ttu-id="a0bfb-271">& pořadí</span><span class="sxs-lookup"><span data-stu-id="a0bfb-271">&Order</span></span>|  
    ||<span data-ttu-id="a0bfb-272">TabIndex</span><span class="sxs-lookup"><span data-stu-id="a0bfb-272">TabIndex</span></span>|<span data-ttu-id="a0bfb-273">7</span><span class="sxs-lookup"><span data-stu-id="a0bfb-273">7</span></span>|  
    ||<span data-ttu-id="a0bfb-274">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="a0bfb-274">AccessibleDescription</span></span>|<span data-ttu-id="a0bfb-275">Celkový počet pořadí</span><span class="sxs-lookup"><span data-stu-id="a0bfb-275">Total the order</span></span>|  
    ||<span data-ttu-id="a0bfb-276">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="a0bfb-276">AccessibleName</span></span>|<span data-ttu-id="a0bfb-277">Celkový počet pořadí</span><span class="sxs-lookup"><span data-stu-id="a0bfb-277">Total order</span></span>|  
    |<span data-ttu-id="a0bfb-278">Tlačítko</span><span class="sxs-lookup"><span data-stu-id="a0bfb-278">Button</span></span>|<span data-ttu-id="a0bfb-279">Name</span><span class="sxs-lookup"><span data-stu-id="a0bfb-279">Name</span></span>|<span data-ttu-id="a0bfb-280">Zrušit</span><span class="sxs-lookup"><span data-stu-id="a0bfb-280">cancel</span></span>|  
    ||<span data-ttu-id="a0bfb-281">Text</span><span class="sxs-lookup"><span data-stu-id="a0bfb-281">Text</span></span>|<span data-ttu-id="a0bfb-282">& Zrušit</span><span class="sxs-lookup"><span data-stu-id="a0bfb-282">&Cancel</span></span>|  
    ||<span data-ttu-id="a0bfb-283">TabIndex</span><span class="sxs-lookup"><span data-stu-id="a0bfb-283">TabIndex</span></span>|<span data-ttu-id="a0bfb-284">8</span><span class="sxs-lookup"><span data-stu-id="a0bfb-284">8</span></span>|  
    ||<span data-ttu-id="a0bfb-285">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="a0bfb-285">AccessibleDescription</span></span>|<span data-ttu-id="a0bfb-286">Zrušit pořadí</span><span class="sxs-lookup"><span data-stu-id="a0bfb-286">Cancel the order</span></span>|  
    ||<span data-ttu-id="a0bfb-287">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="a0bfb-287">AccessibleName</span></span>|<span data-ttu-id="a0bfb-288">Zrušit objednávku</span><span class="sxs-lookup"><span data-stu-id="a0bfb-288">Cancel order</span></span>|  
    |<span data-ttu-id="a0bfb-289">MainMenu</span><span class="sxs-lookup"><span data-stu-id="a0bfb-289">MainMenu</span></span>|<span data-ttu-id="a0bfb-290">Name</span><span class="sxs-lookup"><span data-stu-id="a0bfb-290">Name</span></span>|<span data-ttu-id="a0bfb-291">theMainMenu</span><span class="sxs-lookup"><span data-stu-id="a0bfb-291">theMainMenu</span></span>|  
    |<span data-ttu-id="a0bfb-292">Položku nabídky</span><span class="sxs-lookup"><span data-stu-id="a0bfb-292">MenuItem</span></span>|<span data-ttu-id="a0bfb-293">Name</span><span class="sxs-lookup"><span data-stu-id="a0bfb-293">Name</span></span>|<span data-ttu-id="a0bfb-294">fileCommands</span><span class="sxs-lookup"><span data-stu-id="a0bfb-294">fileCommands</span></span>|  
    ||<span data-ttu-id="a0bfb-295">Text</span><span class="sxs-lookup"><span data-stu-id="a0bfb-295">Text</span></span>|<span data-ttu-id="a0bfb-296">& soubor</span><span class="sxs-lookup"><span data-stu-id="a0bfb-296">&File</span></span>|  
    |<span data-ttu-id="a0bfb-297">Položku nabídky</span><span class="sxs-lookup"><span data-stu-id="a0bfb-297">MenuItem</span></span>|<span data-ttu-id="a0bfb-298">Name</span><span class="sxs-lookup"><span data-stu-id="a0bfb-298">Name</span></span>|<span data-ttu-id="a0bfb-299">exitApp</span><span class="sxs-lookup"><span data-stu-id="a0bfb-299">exitApp</span></span>|  
    ||<span data-ttu-id="a0bfb-300">Text</span><span class="sxs-lookup"><span data-stu-id="a0bfb-300">Text</span></span>|<span data-ttu-id="a0bfb-301">U & končit</span><span class="sxs-lookup"><span data-stu-id="a0bfb-301">E&xit</span></span>|
    
      <span data-ttu-id="a0bfb-302">Formulář bude vypadat podobně jako na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="a0bfb-302">Your form will look something like the following image:</span></span>
    
      ![Formulář objednávky pizza s názvem textového pole a velikost a toppings výběru.](./media/walkthrough-creating-an-accessible-windows-based-application/visual-basic-pizza-order-form.gif)  

## <a name="supporting-high-contrast-mode"></a><span data-ttu-id="a0bfb-304">Podporující režim s vysokým kontrastem</span><span class="sxs-lookup"><span data-stu-id="a0bfb-304">Supporting High Contrast Mode</span></span>  
 <span data-ttu-id="a0bfb-305">Vysoký kontrast je nastavení systému Windows, který zlepšuje čitelnost pomocí kontrastní barvy a velikosti písem, které jsou užitečné pro uživatele se zrakovým postižením.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-305">High Contrast mode is a Windows system setting that improves readability by using contrasting colors and font sizes that are beneficial for visually impaired users.</span></span> <span data-ttu-id="a0bfb-306"><xref:System.Windows.Forms.SystemInformation.HighContrast%2A> Vlastnost je k dispozici k určení, zda je nastaven režim s vysokým kontrastem.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-306">The <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> property is provided to determine whether the High Contrast mode is set.</span></span>  
  
 <span data-ttu-id="a0bfb-307">Pokud je SystemInformation.HighContrast `true`, by měla aplikace:</span><span class="sxs-lookup"><span data-stu-id="a0bfb-307">If SystemInformation.HighContrast is `true`, the application should:</span></span>  
  
-   <span data-ttu-id="a0bfb-308">Zobrazit všechny prvky uživatelského rozhraní pomocí systému barevné schéma</span><span class="sxs-lookup"><span data-stu-id="a0bfb-308">Display all user interface elements using the system color scheme</span></span>  
  
-   <span data-ttu-id="a0bfb-309">Oznamují vizuální prvky nebo zvuk veškeré informace, které se předávají prostřednictvím barvu.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-309">Convey by visual cues or sound any information that is conveyed through color.</span></span> <span data-ttu-id="a0bfb-310">Například pokud pomocí red písma jsou zvýrazněny konkrétní seznam položek, můžete také přidat tučné písmo, tak, aby uživatel měl jiné barvy upozornění, že jsou zvýrazněné položky.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-310">For example, if particular list items are highlighted by using a red font, you could also add bold to the font, so that the user has a non-color cue that the items are highlighted.</span></span>  
  
-   <span data-ttu-id="a0bfb-311">Vynechat všechny obrázky nebo vzory za text</span><span class="sxs-lookup"><span data-stu-id="a0bfb-311">Omit any images or patterns behind text</span></span>  
  
 <span data-ttu-id="a0bfb-312">Aplikace by měla kontrolovat nastavení <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> když aplikaci spustí a reagovat na událost systému <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-312">The application should check the setting of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> when the application starts and respond to the system event <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span></span> <span data-ttu-id="a0bfb-313"><xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> Událost se vyvolá vždy, když hodnota <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> změny.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-313">The <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event is raised whenever the value of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> changes.</span></span>  
  
 <span data-ttu-id="a0bfb-314">V naší aplikaci, je jediným prvkem, který se nepoužívá nastavení systému pro barvu `lblCompanyName`.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-314">In our application, the only element that is not using the system settings for color is `lblCompanyName`.</span></span> <span data-ttu-id="a0bfb-315"><xref:System.Drawing.SystemColors> Třída se používá, chcete-li změnit nastavení barev popisku uživatel vybral systémových barev.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-315">The <xref:System.Drawing.SystemColors> class is used to change the color settings of the label to the user-selected system colors.</span></span>  
  
#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a><span data-ttu-id="a0bfb-316">Povolit režim s vysokým kontrastem účinným způsobem</span><span class="sxs-lookup"><span data-stu-id="a0bfb-316">To enable High Contrast mode in an effective way</span></span>  
  
1.  <span data-ttu-id="a0bfb-317">Vytvořte metodu pro nastavení barvy popisku na systémových barev.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-317">Create a method to set the colors of the label to the system colors.</span></span>  
  
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
  
2.  <span data-ttu-id="a0bfb-318">Volání `SetColorScheme` postup v konstruktoru formuláře (`Public Sub New()` v jazyce Visual Basic a `public class Form1` ve Vizuálu C#).</span><span class="sxs-lookup"><span data-stu-id="a0bfb-318">Call the `SetColorScheme` procedure in the form constructor (`Public Sub New()` in Visual Basic and `public class Form1` in Visual C#).</span></span> <span data-ttu-id="a0bfb-319">Pro přístup k konstruktoru v jazyce Visual Basic, budete muset rozbalit oblast s názvem **kód generovaný návrhářem formulářů Windows**.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-319">To access the constructor in Visual Basic, you will need to expand the region labeled **Windows Form Designer generated code**.</span></span>  
  
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
  
3.  <span data-ttu-id="a0bfb-320">Vytvořit procedury události s odpovídajícím podpisem na <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> událostí.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-320">Create an event procedure, with the appropriate signature, to respond to the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event.</span></span>  
  
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
  
4.  <span data-ttu-id="a0bfb-321">Přidejte kód konstruktoru formuláře po volání `InitializeComponents`, k připojení události postup systémové události.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-321">Add code to the form constructor, after the call to `InitializeComponents`, to hook up the event procedure to the system event.</span></span> <span data-ttu-id="a0bfb-322">Tato metoda volá `SetColorScheme` postup.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-322">This method calls the `SetColorScheme` procedure.</span></span>  
  
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
  
5.  <span data-ttu-id="a0bfb-323">Přidejte kód do formuláře <xref:System.Windows.Forms.Control.Dispose%2A> metoda před voláním <xref:System.Windows.Forms.Control.Dispose%2A> metody základní třídy k uvolnění události po zavření aplikace.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-323">Add code to the form <xref:System.Windows.Forms.Control.Dispose%2A> method, before the call to the <xref:System.Windows.Forms.Control.Dispose%2A> method of the base class, to release the event when the application closes.</span></span> <span data-ttu-id="a0bfb-324">Pro přístup <xref:System.Windows.Forms.Control.Dispose%2A> metody v jazyce Visual Basic, budete muset rozbalit oblast s názvem kód generovaný návrhářem formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-324">To access the <xref:System.Windows.Forms.Control.Dispose%2A> method in Visual Basic, you will need to expand the region labeled Windows Form Designer generated code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a0bfb-325">Kód události systému běží vlákno oddělená od hlavní aplikace.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-325">The system event code runs a thread separate from the main application.</span></span> <span data-ttu-id="a0bfb-326">Pokud vydané události, spustí kód, který jste připojili k této události i po ukončení programu.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-326">If you do not release the event, the code that you hook up to the event will run even after the program is closed.</span></span>  
  
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
  
6.  <span data-ttu-id="a0bfb-327">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-327">Press F5 to run the application.</span></span>  
  
## <a name="conveying-important-information-by-means-other-than-sound"></a><span data-ttu-id="a0bfb-328">Předávání důležitých informací prostředky než zvuku</span><span class="sxs-lookup"><span data-stu-id="a0bfb-328">Conveying Important Information by Means Other Than Sound</span></span>  
 <span data-ttu-id="a0bfb-329">V této aplikaci žádné informace předávají zvukovou samostatně.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-329">In this application, no information is conveyed by sound alone.</span></span> <span data-ttu-id="a0bfb-330">Pokud používáte zvuku ve vaší aplikaci, by měl jiným způsobem a zadejte informace.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-330">If you use sound in your application, then you should supply the information by some other means as well.</span></span>  
  
#### <a name="to-supply-information-by-some-other-means-than-sound"></a><span data-ttu-id="a0bfb-331">Slouží k poskytování informací jiným způsobem než zvuku</span><span class="sxs-lookup"><span data-stu-id="a0bfb-331">To supply information by some other means than sound</span></span>  
  
1.  <span data-ttu-id="a0bfb-332">Vytvoření záhlaví flash pomocí funkce rozhraní Windows API FlashWindow.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-332">Make the title bar flash by using the Windows API function FlashWindow.</span></span> <span data-ttu-id="a0bfb-333">Příklad toho, jak volat funkce rozhraní API Windows, naleznete v tématu [názorný postup: Volání rozhraní API Windows](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span><span class="sxs-lookup"><span data-stu-id="a0bfb-333">For an example of how to call Windows API functions, see [Walkthrough: Calling Windows APIs](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a0bfb-334">Uživatel může mít povoleno, službu Windows Popis zvuku, která také způsobí, že v okně tak, aby při přehrávání zvuků systému prostřednictvím vestavěné reproduktorů počítače.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-334">The user may have the Windows SoundSentry service enabled, which will also cause the window to flash when the system sounds are played through the computer's built-in speaker.</span></span>  
  
2.  <span data-ttu-id="a0bfb-335">Zobrazení důležitých informací v nemodálním okně tak, aby uživatel může odpovědět na ni.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-335">Display the important information in a non-modal window so that the user may respond to it.</span></span>  
  
3.  <span data-ttu-id="a0bfb-336">Zobrazí okno se zprávou, která získá fokus klávesnice.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-336">Display a message box that acquires the keyboard focus.</span></span> <span data-ttu-id="a0bfb-337">Tato metoda vyhněte, když uživatel může být psaní.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-337">Avoid this method when the user may be typing.</span></span>  
  
4.  <span data-ttu-id="a0bfb-338">Zobrazte indikátor stavu v oznamovací oblasti na hlavním panelu Stav.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-338">Display a status indicator in the status notification area of the taskbar.</span></span> <span data-ttu-id="a0bfb-339">Podrobnosti najdete v tématu [přidání ikon aplikací do TaskBar s komponentou Windows Forms NotifyIcon](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span><span class="sxs-lookup"><span data-stu-id="a0bfb-339">For details, see [Adding Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
## <a name="testing-the-application"></a><span data-ttu-id="a0bfb-340">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="a0bfb-340">Testing the Application</span></span>  
 <span data-ttu-id="a0bfb-341">Před nasazením aplikace, měli byste otestovat funkce pro usnadnění přístupu, které jste implementovali.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-341">Before deploying the application, you should test the accessibility features that you have implemented.</span></span>  
  
#### <a name="to-test-accessibility-features"></a><span data-ttu-id="a0bfb-342">K otestování funkce pro usnadnění přístupu</span><span class="sxs-lookup"><span data-stu-id="a0bfb-342">To test accessibility features</span></span>  
  
1.  <span data-ttu-id="a0bfb-343">K otestování klávesnice, myš odpojte a Navigovat v uživatelském rozhraní pro každou funkci pouze pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-343">To test keyboard access, unplug the mouse and navigate the user interface for each feature using only the keyboard.</span></span> <span data-ttu-id="a0bfb-344">Ujistěte se, že všechny úlohy lze provádět pomocí klávesnice pouze.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-344">Ensure that all tasks may be performed using the keyboard only.</span></span>  
  
2.  <span data-ttu-id="a0bfb-345">K otestování podpory vysoký kontrast, zvolte ikonu možností usnadnění přístupu v Ovládacích panelech.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-345">To test support of High Contrast, choose the Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="a0bfb-346">Klikněte na kartu zobrazení a použití vysoký kontrast – zaškrtnutím políčka.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-346">Click the Display tab and select the Use High Contrast check box.</span></span> <span data-ttu-id="a0bfb-347">Procházejte všechny prvky uživatelského rozhraní k zajištění, že se projeví změny barev a písma.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-347">Navigate through all user interface elements to ensure that the color and font changes are reflected.</span></span> <span data-ttu-id="a0bfb-348">Také se ujistěte, že jsou vynechány Image nebo vzorce vykreslit za text.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-348">Also, ensure that images or patterns drawn behind text are omitted.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a0bfb-349">Windows NT 4 nemá ikonu možností usnadnění přístupu v Ovládacích panelech.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-349">Windows NT 4 does not have an Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="a0bfb-350">Tento postup pro změnu nastavení SystemInformation.HighContrast proto nebude fungovat v systému Windows NT 4.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-350">Thus, this procedure for changing the SystemInformation.HighContrast setting does not work in Windows NT 4.</span></span>  
  
3.  <span data-ttu-id="a0bfb-351">Další nástroje jsou snadno dostupné pro testování přístupnosti aplikace.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-351">Other tools are readily available for testing the accessibility of an application.</span></span>  
  
4.  <span data-ttu-id="a0bfb-352">Pokud chcete otestovat, vystavení fokus klávesnice, spusťte Lupa.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-352">To test exposing the keyboard focus, run Magnifier.</span></span> <span data-ttu-id="a0bfb-353">(Pokud chcete soubor otevřít, klikněte na tlačítko **Start** nabídky, přejděte k **programy**, přejděte na **Příslušenství**, přejděte na **usnadnění**a potom klikněte na tlačítko  **Lupa**).</span><span class="sxs-lookup"><span data-stu-id="a0bfb-353">(To open it, click the **Start** menu, point to **Programs**, point to **Accessories**, point to **Accessibility**, and then click **Magnifier**).</span></span> <span data-ttu-id="a0bfb-354">Navigovat v uživatelském rozhraní pomocí tabulátor klávesnice a myši.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-354">Navigate the user interface using both keyboard tabbing and the mouse.</span></span> <span data-ttu-id="a0bfb-355">Ujistěte se, že je správně v sledovat všechny navigační **Lupa**.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-355">Ensure that all navigation is tracked properly in **Magnifier**.</span></span>  
  
5.  <span data-ttu-id="a0bfb-356">K otestování zpřístupňuje prvky na obrazovce, spusťte zkontrolujte, jestli se a pomocí myši a klávesu TAB k dosažení jednotlivých prvků.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-356">To test exposing screen elements, run Inspect, and use both the mouse and the TAB key to reach each element.</span></span> <span data-ttu-id="a0bfb-357">Ujistěte se, že informace uváděné v pole název, stav, Role, umístění a hodnota okna zkontrolujte, jestli se má smysl pro uživatele pro každý objekt v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a0bfb-357">Ensure that the information presented in the Name, State, Role, Location, and Value fields of the Inspect window is meaningful to the user for each object in the UI.</span></span>
