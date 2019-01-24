---
title: ColorDialog – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 9ef7d667b582d3b227f0f0e8af5e7e0335cd4860
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54570106"
---
# <a name="colordialog-component-overview-windows-forms"></a><span data-ttu-id="45ae4-102">ColorDialog – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="45ae4-102">ColorDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="45ae4-103">Windows Forms <xref:System.Windows.Forms.ColorDialog> komponenta je předem nakonfigurované dialogové okno, které umožňuje uživateli vybrat barvu z palety a přidat vlastní barvy palety. Tento.</span><span class="sxs-lookup"><span data-stu-id="45ae4-103">The Windows Forms <xref:System.Windows.Forms.ColorDialog> component is a pre-configured dialog box that allows the user to select a color from a palette and to add custom colors to that palette.</span></span> <span data-ttu-id="45ae4-104">Je stejný dialogovém okně, které se zobrazí v ostatních aplikace založené na Windows k výběru barev.</span><span class="sxs-lookup"><span data-stu-id="45ae4-104">It is the same dialog box that you see in other Windows-based applications to select colors.</span></span> <span data-ttu-id="45ae4-105">Použijte v rámci vaší aplikace založené na Windows jako jednoduchým řešením namísto dialogové okno Vlastní konfigurace.</span><span class="sxs-lookup"><span data-stu-id="45ae4-105">Use it within your Windows-based application as a simple solution in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="45ae4-106">Barva vybraná v dialogovém okně se vrátí v <xref:System.Windows.Forms.ColorDialog.Color%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="45ae4-106">The color selected in the dialog box is returned in the <xref:System.Windows.Forms.ColorDialog.Color%2A> property.</span></span> <span data-ttu-id="45ae4-107">Pokud <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> je nastavena na `false`, tlačítko "Definovat vlastní barvy" je vypnutá. uživatel je omezena na předdefinované barvy palety.</span><span class="sxs-lookup"><span data-stu-id="45ae4-107">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `false`, the "Define Custom Colors" button is disabled and the user is restricted to the predefined colors in the palette.</span></span> <span data-ttu-id="45ae4-108">Pokud <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> je nastavena na `true`, uživatel nemůže vybrat dithered pro bitové barvy.</span><span class="sxs-lookup"><span data-stu-id="45ae4-108">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors.</span></span> <span data-ttu-id="45ae4-109">Chcete-li zobrazit dialogové okno, musí volat jeho <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="45ae4-109">To display the dialog box, you must call its <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45ae4-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45ae4-110">See also</span></span>
- <xref:System.Windows.Forms.ColorDialog>
- [<span data-ttu-id="45ae4-111">Komponenta ColorDialog</span><span class="sxs-lookup"><span data-stu-id="45ae4-111">ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)
- [<span data-ttu-id="45ae4-112">Ovládací prvky a součásti dialogového okna</span><span class="sxs-lookup"><span data-stu-id="45ae4-112">Dialog-Box Controls and Components</span></span>](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
- [<span data-ttu-id="45ae4-113">Postupy: Změna vzhledu Windows Forms ColorDialog – komponenta</span><span class="sxs-lookup"><span data-stu-id="45ae4-113">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
