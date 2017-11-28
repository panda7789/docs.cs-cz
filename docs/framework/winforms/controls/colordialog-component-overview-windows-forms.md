---
title: "ColorDialog – přehled komponenty (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7f3a25c601e46c18a30755a15131bba03669a2ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="colordialog-component-overview-windows-forms"></a><span data-ttu-id="300a5-102">ColorDialog – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="300a5-102">ColorDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="300a5-103">Windows Forms <xref:System.Windows.Forms.ColorDialog> součást je předem nakonfigurovaný dialogové okno umožňuje uživateli vybrat barvu z paletu a pro přidání do této palety vlastních barev.</span><span class="sxs-lookup"><span data-stu-id="300a5-103">The Windows Forms <xref:System.Windows.Forms.ColorDialog> component is a pre-configured dialog box that allows the user to select a color from a palette and to add custom colors to that palette.</span></span> <span data-ttu-id="300a5-104">Je stejné, které vidíte v dalších dialogových oken aplikace pro systém Windows a vyberte barvy.</span><span class="sxs-lookup"><span data-stu-id="300a5-104">It is the same dialog box that you see in other Windows-based applications to select colors.</span></span> <span data-ttu-id="300a5-105">Ji použijte v rámci aplikace systému Windows jako simple řešení místo dialogové okno Vlastní konfigurace.</span><span class="sxs-lookup"><span data-stu-id="300a5-105">Use it within your Windows-based application as a simple solution in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="300a5-106">Barva vybraná v dialogovém okně je vrácený v <xref:System.Windows.Forms.ColorDialog.Color%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="300a5-106">The color selected in the dialog box is returned in the <xref:System.Windows.Forms.ColorDialog.Color%2A> property.</span></span> <span data-ttu-id="300a5-107">Pokud <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> je nastavena na `false`, tlačítko "Definovat vlastní barvy" je zakázána a uživatel je omezen na předdefinované barvy palety.</span><span class="sxs-lookup"><span data-stu-id="300a5-107">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `false`, the "Define Custom Colors" button is disabled and the user is restricted to the predefined colors in the palette.</span></span> <span data-ttu-id="300a5-108">Pokud <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> je nastavena na `true`, uživatel nemůže vybrat tónovaná barvy.</span><span class="sxs-lookup"><span data-stu-id="300a5-108">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors.</span></span> <span data-ttu-id="300a5-109">Pokud chcete zobrazit dialogové okno, musí volat jeho <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="300a5-109">To display the dialog box, you must call its <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="300a5-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="300a5-110">See Also</span></span>  
 <xref:System.Windows.Forms.ColorDialog>  
 [<span data-ttu-id="300a5-111">ColorDialog – komponenta</span><span class="sxs-lookup"><span data-stu-id="300a5-111">ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [<span data-ttu-id="300a5-112">Dialogové okno – Ovládací prvky a součásti</span><span class="sxs-lookup"><span data-stu-id="300a5-112">Dialog-Box Controls and Components</span></span>](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 [<span data-ttu-id="300a5-113">Postupy: Změna vzhledu Windows Forms ColorDialog – komponenta</span><span class="sxs-lookup"><span data-stu-id="300a5-113">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
