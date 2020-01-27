---
title: Změna vzhledu součásti ColorDialog
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ColorDialog component [Windows Forms], examples
- ColorDialog component [Windows Forms], formatting appearance
- color dialog box [Windows Forms], configuring appearance
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
ms.openlocfilehash: 0402d7f3c03a0771512a03ac54e1b093c9fe6e9b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746637"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a><span data-ttu-id="ef89f-102">Postupy: Změna vzhledu součásti Windows Forms ColorDialog</span><span class="sxs-lookup"><span data-stu-id="ef89f-102">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>
<span data-ttu-id="ef89f-103">Můžete nakonfigurovat vzhled součásti model Windows Forms <xref:System.Windows.Forms.ColorDialog> s řadou vlastností.</span><span class="sxs-lookup"><span data-stu-id="ef89f-103">You can configure the appearance of the Windows Forms <xref:System.Windows.Forms.ColorDialog> component with a number of its properties.</span></span> <span data-ttu-id="ef89f-104">Dialogové okno obsahuje dvě části, které zobrazují základní barvy a jeden, který uživateli umožňuje definovat vlastní barvy.</span><span class="sxs-lookup"><span data-stu-id="ef89f-104">The dialog box has two sections — one that shows basic colors and one that allows the user to define custom colors.</span></span>  
  
 <span data-ttu-id="ef89f-105">Většina vlastností omezuje barvy, které uživatel může vybrat z dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="ef89f-105">Most of the properties restrict what colors the user can select from the dialog box.</span></span> <span data-ttu-id="ef89f-106">Pokud je vlastnost <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> nastavena na hodnotu `true`, uživatel může definovat vlastní barvy.</span><span class="sxs-lookup"><span data-stu-id="ef89f-106">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `true`, the user is allowed to define custom colors.</span></span> <span data-ttu-id="ef89f-107">Vlastnost <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> je `true`, pokud je dialogové okno rozbaleno pro definování vlastních barev; v opačném případě musí uživatel kliknout na tlačítko "definovat vlastní barvy".</span><span class="sxs-lookup"><span data-stu-id="ef89f-107">The <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> property is `true` if the dialog box is expanded to define custom colors; otherwise the user must click a "Define Custom Colors" button.</span></span> <span data-ttu-id="ef89f-108">Pokud je vlastnost <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> nastavena na hodnotu `true`, dialogové okno zobrazí všechny dostupné barvy v sadě základních barev.</span><span class="sxs-lookup"><span data-stu-id="ef89f-108">When the <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> property is set to `true`, the dialog box displays all available colors in the set of basic colors.</span></span> <span data-ttu-id="ef89f-109">Pokud je vlastnost <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> nastavena na hodnotu `true`, uživatel nemůže vybrat rozdané barvy; pro výběr jsou k dispozici pouze plné barvy.</span><span class="sxs-lookup"><span data-stu-id="ef89f-109">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors; only solid colors are available to select.</span></span>  
  
 <span data-ttu-id="ef89f-110">Pokud je vlastnost <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> nastavena na hodnotu `true`, zobrazí se v dialogovém okně tlačítko Help.</span><span class="sxs-lookup"><span data-stu-id="ef89f-110">If the <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> property is set to `true`, a Help button appears on the dialog box.</span></span> <span data-ttu-id="ef89f-111">Když uživatel klikne na tlačítko Help, vyvolá se událost <xref:System.Windows.Forms.CommonDialog.HelpRequest> <xref:System.Windows.Forms.ColorDialog> komponenty.</span><span class="sxs-lookup"><span data-stu-id="ef89f-111">When the user clicks the Help button, the <xref:System.Windows.Forms.ColorDialog> component's <xref:System.Windows.Forms.CommonDialog.HelpRequest> event is raised.</span></span>  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a><span data-ttu-id="ef89f-112">Konfigurace vzhledu dialogového okna Barva</span><span class="sxs-lookup"><span data-stu-id="ef89f-112">To configure the appearance of the color dialog box</span></span>  
  
1. <span data-ttu-id="ef89f-113">Nastavte vlastnosti <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>a <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> na požadované hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ef89f-113">Set the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, and <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> properties to the desired values.</span></span>  
  
    ```vb  
    ColorDialog1.AllowFullOpen = True  
    ColorDialog1.AnyColor = True  
    ColorDialog1.SolidColorOnly = False  
    ColorDialog1.ShowHelp = True  
    ```  
  
    ```csharp  
    colorDialog1.AllowFullOpen = true;  
    colorDialog1.AnyColor = true;  
    colorDialog1.SolidColorOnly = false;  
    colorDialog1.ShowHelp = true;  
    ```  
  
    ```cpp  
    colorDialog1->AllowFullOpen = true;  
    colorDialog1->AnyColor = true;  
    colorDialog1->SolidColorOnly = false;  
    colorDialog1->ShowHelp = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ef89f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef89f-114">See also</span></span>

- <xref:System.Windows.Forms.ColorDialog>
- [<span data-ttu-id="ef89f-115">Komponenta ColorDialog</span><span class="sxs-lookup"><span data-stu-id="ef89f-115">ColorDialog Component</span></span>](colordialog-component-windows-forms.md)
- [<span data-ttu-id="ef89f-116">Přehled komponenty ColorDialog</span><span class="sxs-lookup"><span data-stu-id="ef89f-116">ColorDialog Component Overview</span></span>](colordialog-component-overview-windows-forms.md)
