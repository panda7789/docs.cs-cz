---
title: "Postupy: Změna vzhledu součásti Windows Forms ColorDialog"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ColorDialog component [Windows Forms], examples
- ColorDialog component [Windows Forms], formatting appearance
- color dialog box [Windows Forms], configuring appearance
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af3a9ec6ba301a27a7940bc752ffaf12f345abec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a><span data-ttu-id="290f8-102">Postupy: Změna vzhledu součásti Windows Forms ColorDialog</span><span class="sxs-lookup"><span data-stu-id="290f8-102">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>
<span data-ttu-id="290f8-103">Můžete nakonfigurovat vzhledu Windows Forms <xref:System.Windows.Forms.ColorDialog> součásti s číslem jeho vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="290f8-103">You can configure the appearance of the Windows Forms <xref:System.Windows.Forms.ColorDialog> component with a number of its properties.</span></span> <span data-ttu-id="290f8-104">Dialogové okno má dvě části – jeden, který ukazuje základní barvy a ten, který umožňuje uživateli definovat vlastní barvy.</span><span class="sxs-lookup"><span data-stu-id="290f8-104">The dialog box has two sections — one that shows basic colors and one that allows the user to define custom colors.</span></span>  
  
 <span data-ttu-id="290f8-105">Většinu vlastností omezit jaké barvy uživatele můžete vybrat z dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="290f8-105">Most of the properties restrict what colors the user can select from the dialog box.</span></span> <span data-ttu-id="290f8-106">Pokud <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> je nastavena na `true`, uživatel může definovat vlastní barvy.</span><span class="sxs-lookup"><span data-stu-id="290f8-106">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `true`, the user is allowed to define custom colors.</span></span> <span data-ttu-id="290f8-107"><xref:System.Windows.Forms.ColorDialog.FullOpen%2A> Vlastnost je `true` Pokud dialogové okno je rozšířena definovat vlastní barvy; v opačném případě uživatele musíte kliknout na tlačítko "Definovat vlastní barvy".</span><span class="sxs-lookup"><span data-stu-id="290f8-107">The <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> property is `true` if the dialog box is expanded to define custom colors; otherwise the user must click a "Define Custom Colors" button.</span></span> <span data-ttu-id="290f8-108">Když <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> je nastavena na `true`, dialogové okno zobrazí všechny dostupné barev v sadě základních barev.</span><span class="sxs-lookup"><span data-stu-id="290f8-108">When the <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> property is set to `true`, the dialog box displays all available colors in the set of basic colors.</span></span> <span data-ttu-id="290f8-109">Pokud <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> je nastavena na `true`, uživatel nemůže vybrat tónovaná barvy; pouze plné barvy jsou k dispozici pro výběr.</span><span class="sxs-lookup"><span data-stu-id="290f8-109">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors; only solid colors are available to select.</span></span>  
  
 <span data-ttu-id="290f8-110">Pokud <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> je nastavena na `true`, v dialogovém okně se zobrazí tlačítko Nápověda.</span><span class="sxs-lookup"><span data-stu-id="290f8-110">If the <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> property is set to `true`, a Help button appears on the dialog box.</span></span> <span data-ttu-id="290f8-111">Když uživatel klikne na tlačítko Nápověda <xref:System.Windows.Forms.ColorDialog> součásti <xref:System.Windows.Forms.CommonDialog.HelpRequest> událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="290f8-111">When the user clicks the Help button, the <xref:System.Windows.Forms.ColorDialog> component's <xref:System.Windows.Forms.CommonDialog.HelpRequest> event is raised.</span></span>  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a><span data-ttu-id="290f8-112">Konfigurace vzhledu dialogové okno barev</span><span class="sxs-lookup"><span data-stu-id="290f8-112">To configure the appearance of the color dialog box</span></span>  
  
1.  <span data-ttu-id="290f8-113">Nastavte <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, a <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> vlastnosti, které chcete požadované hodnoty.</span><span class="sxs-lookup"><span data-stu-id="290f8-113">Set the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, and <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> properties to the desired values.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="290f8-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="290f8-114">See Also</span></span>  
 <xref:System.Windows.Forms.ColorDialog>  
 [<span data-ttu-id="290f8-115">Komponenta ColorDialog</span><span class="sxs-lookup"><span data-stu-id="290f8-115">ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [<span data-ttu-id="290f8-116">Přehled komponenty ColorDialog</span><span class="sxs-lookup"><span data-stu-id="290f8-116">ColorDialog Component Overview</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md)
