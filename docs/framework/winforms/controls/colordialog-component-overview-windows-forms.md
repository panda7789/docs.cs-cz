---
title: ColorDialog – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 7dd48c8df0a36262962df596e8efadf4de1c2cd3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713329"
---
# <a name="colordialog-component-overview-windows-forms"></a>ColorDialog – přehled komponenty (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ColorDialog> komponenta je předem nakonfigurované dialogové okno, které umožňuje uživateli vybrat barvu z palety a přidat vlastní barvy palety. Tento. Je stejný dialogovém okně, které se zobrazí v ostatních aplikace založené na Windows k výběru barev. Použijte v rámci vaší aplikace založené na Windows jako jednoduchým řešením namísto dialogové okno Vlastní konfigurace.  
  
 Barva vybraná v dialogovém okně se vrátí v <xref:System.Windows.Forms.ColorDialog.Color%2A> vlastnost. Pokud <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> je nastavena na `false`, tlačítko "Definovat vlastní barvy" je vypnutá. uživatel je omezena na předdefinované barvy palety. Pokud <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> je nastavena na `true`, uživatel nemůže vybrat dithered pro bitové barvy. Chcete-li zobrazit dialogové okno, musí volat jeho <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metoda.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.ColorDialog>
- [Komponenta ColorDialog](colordialog-component-windows-forms.md)
- [Ovládací prvky a součásti dialogového okna](dialog-box-controls-and-components-windows-forms.md)
- [Postupy: Změna vzhledu Windows Forms ColorDialog – komponenta](how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
