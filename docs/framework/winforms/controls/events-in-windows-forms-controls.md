---
title: Události v ovládacích prvcích Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: 41ad95de7a65dbd0cb3a0d1af8f5c8cb00c1ccdd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971974"
---
# <a name="events-in-windows-forms-controls"></a>Události v ovládacích prvcích Windows Forms
Dědí z více než 60 události ovládacího prvku Windows Forms <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Patří mezi ně <xref:System.Windows.Forms.Control.Paint> událost, což způsobí, že ovládací prvek chcete kreslit, události související s zobrazení okna, například <xref:System.Windows.Forms.Control.Resize> a <xref:System.Windows.Forms.Control.Layout> události a nízké úrovně události myši a klávesnice. Některé události nízké úrovně jsou syntetizovat podle <xref:System.Windows.Forms.Control> do sémantického událostech, například <xref:System.Windows.Forms.Control.Click> a <xref:System.Windows.Forms.Control.DoubleClick>. Podrobnosti o zděděné události najdete v tématu <xref:System.Windows.Forms.Control>.  
  
 Pokud vaše vlastní ovládací prvek musí přepsat funkci zděděných událostí, přepsat zděděnou `On` *EventName* metoda místo připojením delegáta. Pokud nejste obeznámeni s modelem události v rozhraní .NET Framework, přečtěte si téma [vyvolávání událostí z komponenty](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).  
  
## <a name="see-also"></a>Viz také:

- [Přepsání metody OnPaint](overriding-the-onpaint-method.md)
- [Zpracování uživatelského vstupu](handling-user-input.md)
- [Definování události](defining-an-event-in-windows-forms-controls.md)
- [Události](../../../standard/events/index.md)
