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
ms.workload: dotnet
ms.openlocfilehash: 5df0d7ddd16de5bd8bb052c09731df6583ca4903
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="colordialog-component-overview-windows-forms"></a>ColorDialog – přehled komponenty (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ColorDialog> součást je předem nakonfigurovaný dialogové okno umožňuje uživateli vybrat barvu z paletu a pro přidání do této palety vlastních barev. Je stejné, které vidíte v dalších dialogových oken aplikace pro systém Windows a vyberte barvy. Ji použijte v rámci aplikace systému Windows jako simple řešení místo dialogové okno Vlastní konfigurace.  
  
 Barva vybraná v dialogovém okně je vrácený v <xref:System.Windows.Forms.ColorDialog.Color%2A> vlastnost. Pokud <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> je nastavena na `false`, tlačítko "Definovat vlastní barvy" je zakázána a uživatel je omezen na předdefinované barvy palety. Pokud <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> je nastavena na `true`, uživatel nemůže vybrat tónovaná barvy. Pokud chcete zobrazit dialogové okno, musí volat jeho <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metoda.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ColorDialog>  
 [Komponenta ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [Ovládací prvky a součásti dialogového okna](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 [Postupy: Změna vzhledu komponenty Windows Forms ColorDialog](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
