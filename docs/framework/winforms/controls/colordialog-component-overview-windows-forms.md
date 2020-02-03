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
# <a name="colordialog-component-overview-windows-forms"></a>ColorDialog – přehled komponenty (Windows Forms)
Komponenta model Windows Forms <xref:System.Windows.Forms.ColorDialog> je předem nakonfigurovaným dialogovým oknem, které umožňuje uživateli vybrat barvu z palety a přidat k ní vlastní barvy. Je to stejné dialogové okno, které vidíte v jiných aplikacích pro systém Windows k výběru barev. Použijte ho v rámci aplikace pro Windows jako jednoduché řešení namísto konfigurace vlastního dialogového okna.  
  
 Barva vybraná v dialogovém okně se vrátí do vlastnosti <xref:System.Windows.Forms.ColorDialog.Color%2A>. Je-li vlastnost <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> nastavena na hodnotu `false`, je tlačítko "definovat vlastní barvy" zakázáno a uživatel je omezen na předdefinované barvy v paletě. Pokud je vlastnost <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> nastavena na hodnotu `true`, uživatel nemůže vybrat rozdané barvy. Chcete-li zobrazit dialogové okno, je nutné zavolat jeho metodu <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ColorDialog>
- [Komponenta ColorDialog](colordialog-component-windows-forms.md)
- [Ovládací prvky a součásti dialogového okna](dialog-box-controls-and-components-windows-forms.md)
- [Postupy: Změna vzhledu komponenty Windows Forms ColorDialog](how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
