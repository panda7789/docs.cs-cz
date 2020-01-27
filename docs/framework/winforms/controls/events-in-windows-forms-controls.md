---
title: Události v ovládacích prvcích
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: c60713917b9c84aa7fad50fb1c81fc9252149ad6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745750"
---
# <a name="events-in-windows-forms-controls"></a>Události v ovládacích prvcích Windows Forms
Ovládací prvek model Windows Forms dědí více než 60 událostí od <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Mezi ně patří událost <xref:System.Windows.Forms.Control.Paint>, což způsobí, že se ovládací prvek vykreslí, události související se zobrazením okna, jako jsou události <xref:System.Windows.Forms.Control.Resize> a <xref:System.Windows.Forms.Control.Layout>, a událostmi myši nízké úrovně a událostí klávesnice. Některé události nízké úrovně jsou syntetizované <xref:System.Windows.Forms.Control> se sémantickými událostmi, jako jsou <xref:System.Windows.Forms.Control.Click> a <xref:System.Windows.Forms.Control.DoubleClick>. Podrobnosti o zděděných událostech najdete v tématu <xref:System.Windows.Forms.Control>.  
  
 Pokud váš vlastní ovládací prvek potřebuje přepsat zděděné funkce události, přepište zděděnou metodu `On`*EventName* namísto připojení delegáta. Pokud nejste obeznámeni s modelem událostí v .NET Framework, přečtěte si téma [vyvolání událostí ze součásti](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).  
  
## <a name="see-also"></a>Viz také:

- [Přepsání metody OnPaint](overriding-the-onpaint-method.md)
- [Zpracování uživatelského vstupu](handling-user-input.md)
- [Definování události](defining-an-event-in-windows-forms-controls.md)
- [Události](../../../standard/events/index.md)
