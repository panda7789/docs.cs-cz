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
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a>Postupy: Změna vzhledu součásti Windows Forms ColorDialog
Můžete nakonfigurovat vzhledu Windows Forms <xref:System.Windows.Forms.ColorDialog> součásti s číslem jeho vlastnosti. Dialogové okno má dvě části – jeden, který ukazuje základní barvy a ten, který umožňuje uživateli definovat vlastní barvy.  
  
 Většinu vlastností omezit jaké barvy uživatele můžete vybrat z dialogového okna. Pokud <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> je nastavena na `true`, uživatel může definovat vlastní barvy. <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> Vlastnost je `true` Pokud dialogové okno je rozšířena definovat vlastní barvy; v opačném případě uživatele musíte kliknout na tlačítko "Definovat vlastní barvy". Když <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> je nastavena na `true`, dialogové okno zobrazí všechny dostupné barev v sadě základních barev. Pokud <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> je nastavena na `true`, uživatel nemůže vybrat tónovaná barvy; pouze plné barvy jsou k dispozici pro výběr.  
  
 Pokud <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> je nastavena na `true`, v dialogovém okně se zobrazí tlačítko Nápověda. Když uživatel klikne na tlačítko Nápověda <xref:System.Windows.Forms.ColorDialog> součásti <xref:System.Windows.Forms.CommonDialog.HelpRequest> událost se vyvolá.  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a>Konfigurace vzhledu dialogové okno barev  
  
1.  Nastavte <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, a <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> vlastnosti, které chcete požadované hodnoty.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ColorDialog>  
 [Komponenta ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [Přehled komponenty ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md)
