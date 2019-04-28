---
title: 'Postupy: Změna vzhledu komponenty Windows Forms ColorDialog'
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
ms.openlocfilehash: d2bb9e06d9d84a9b61c67510e9c012066f69d55e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61595449"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a><span data-ttu-id="abfde-102">Postupy: Změna vzhledu komponenty Windows Forms ColorDialog</span><span class="sxs-lookup"><span data-stu-id="abfde-102">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>
<span data-ttu-id="abfde-103">Můžete nakonfigurovat vzhledu Windows Forms <xref:System.Windows.Forms.ColorDialog> komponentu s celou řadou její vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="abfde-103">You can configure the appearance of the Windows Forms <xref:System.Windows.Forms.ColorDialog> component with a number of its properties.</span></span> <span data-ttu-id="abfde-104">Dialogové okno obsahuje dvě části – ten, který zobrazuje základní barvy a ten, který umožňuje uživateli definovat vlastní barvy.</span><span class="sxs-lookup"><span data-stu-id="abfde-104">The dialog box has two sections — one that shows basic colors and one that allows the user to define custom colors.</span></span>  
  
 <span data-ttu-id="abfde-105">Většina vlastností omezení jaké barev, může uživatel vybrat z dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="abfde-105">Most of the properties restrict what colors the user can select from the dialog box.</span></span> <span data-ttu-id="abfde-106">Pokud <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> je nastavena na `true`, uživatel může definovat vlastní barvy.</span><span class="sxs-lookup"><span data-stu-id="abfde-106">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `true`, the user is allowed to define custom colors.</span></span> <span data-ttu-id="abfde-107"><xref:System.Windows.Forms.ColorDialog.FullOpen%2A> Vlastnost `true` Pokud dialogovém rozbalen a definovat vlastní barvy; jinak uživatel musí kliknout na tlačítko "Definovat vlastní barvy".</span><span class="sxs-lookup"><span data-stu-id="abfde-107">The <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> property is `true` if the dialog box is expanded to define custom colors; otherwise the user must click a "Define Custom Colors" button.</span></span> <span data-ttu-id="abfde-108">Když <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> je nastavena na `true`, zobrazí dialogové okno v sadě základních barev všechny barvy k dispozici.</span><span class="sxs-lookup"><span data-stu-id="abfde-108">When the <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> property is set to `true`, the dialog box displays all available colors in the set of basic colors.</span></span> <span data-ttu-id="abfde-109">Pokud <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> je nastavena na `true`, uživatel nemůže vybrat dithered pro bitové barvy, jsou k dispozici k výběru pouze plné barvy.</span><span class="sxs-lookup"><span data-stu-id="abfde-109">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors; only solid colors are available to select.</span></span>  
  
 <span data-ttu-id="abfde-110">Pokud <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> je nastavena na `true`, v dialogovém okně se zobrazí tlačítko Nápověda.</span><span class="sxs-lookup"><span data-stu-id="abfde-110">If the <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> property is set to `true`, a Help button appears on the dialog box.</span></span> <span data-ttu-id="abfde-111">Když uživatel klikne na tlačítko Nápověda <xref:System.Windows.Forms.ColorDialog> komponenty <xref:System.Windows.Forms.CommonDialog.HelpRequest> událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="abfde-111">When the user clicks the Help button, the <xref:System.Windows.Forms.ColorDialog> component's <xref:System.Windows.Forms.CommonDialog.HelpRequest> event is raised.</span></span>  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a><span data-ttu-id="abfde-112">Konfigurace vzhledu dialogové okno barev</span><span class="sxs-lookup"><span data-stu-id="abfde-112">To configure the appearance of the color dialog box</span></span>  
  
1. <span data-ttu-id="abfde-113">Nastavte <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, a <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> vlastnosti na požadované hodnoty.</span><span class="sxs-lookup"><span data-stu-id="abfde-113">Set the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, and <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> properties to the desired values.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="abfde-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="abfde-114">See also</span></span>

- <xref:System.Windows.Forms.ColorDialog>
- [<span data-ttu-id="abfde-115">Komponenta ColorDialog</span><span class="sxs-lookup"><span data-stu-id="abfde-115">ColorDialog Component</span></span>](colordialog-component-windows-forms.md)
- [<span data-ttu-id="abfde-116">Přehled komponenty ColorDialog</span><span class="sxs-lookup"><span data-stu-id="abfde-116">ColorDialog Component Overview</span></span>](colordialog-component-overview-windows-forms.md)
