---
title: Přehled komponenty ColorDialog
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 48d9d5072335908f85e65933dadafb1b69f28528
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736962"
---
# <a name="colordialog-component-overview-windows-forms"></a><span data-ttu-id="4d097-102">ColorDialog – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="4d097-102">ColorDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="4d097-103">Komponenta model Windows Forms <xref:System.Windows.Forms.ColorDialog> je předem nakonfigurovaným dialogovým oknem, které umožňuje uživateli vybrat barvu z palety a přidat k ní vlastní barvy.</span><span class="sxs-lookup"><span data-stu-id="4d097-103">The Windows Forms <xref:System.Windows.Forms.ColorDialog> component is a pre-configured dialog box that allows the user to select a color from a palette and to add custom colors to that palette.</span></span> <span data-ttu-id="4d097-104">Je to stejné dialogové okno, které vidíte v jiných aplikacích pro systém Windows k výběru barev.</span><span class="sxs-lookup"><span data-stu-id="4d097-104">It is the same dialog box that you see in other Windows-based applications to select colors.</span></span> <span data-ttu-id="4d097-105">Použijte ho v rámci aplikace pro Windows jako jednoduché řešení namísto konfigurace vlastního dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="4d097-105">Use it within your Windows-based application as a simple solution in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="4d097-106">Barva vybraná v dialogovém okně se vrátí do vlastnosti <xref:System.Windows.Forms.ColorDialog.Color%2A>.</span><span class="sxs-lookup"><span data-stu-id="4d097-106">The color selected in the dialog box is returned in the <xref:System.Windows.Forms.ColorDialog.Color%2A> property.</span></span> <span data-ttu-id="4d097-107">Je-li vlastnost <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> nastavena na hodnotu `false`, je tlačítko "definovat vlastní barvy" zakázáno a uživatel je omezen na předdefinované barvy v paletě.</span><span class="sxs-lookup"><span data-stu-id="4d097-107">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `false`, the "Define Custom Colors" button is disabled and the user is restricted to the predefined colors in the palette.</span></span> <span data-ttu-id="4d097-108">Pokud je vlastnost <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> nastavena na hodnotu `true`, uživatel nemůže vybrat rozdané barvy.</span><span class="sxs-lookup"><span data-stu-id="4d097-108">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors.</span></span> <span data-ttu-id="4d097-109">Chcete-li zobrazit dialogové okno, je nutné zavolat jeho metodu <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="4d097-109">To display the dialog box, you must call its <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d097-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d097-110">See also</span></span>

- <xref:System.Windows.Forms.ColorDialog>
- [<span data-ttu-id="4d097-111">Komponenta ColorDialog</span><span class="sxs-lookup"><span data-stu-id="4d097-111">ColorDialog Component</span></span>](colordialog-component-windows-forms.md)
- [<span data-ttu-id="4d097-112">Ovládací prvky a součásti dialogového okna</span><span class="sxs-lookup"><span data-stu-id="4d097-112">Dialog-Box Controls and Components</span></span>](dialog-box-controls-and-components-windows-forms.md)
- [<span data-ttu-id="4d097-113">Postupy: Změna vzhledu komponenty Windows Forms ColorDialog</span><span class="sxs-lookup"><span data-stu-id="4d097-113">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>](how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
