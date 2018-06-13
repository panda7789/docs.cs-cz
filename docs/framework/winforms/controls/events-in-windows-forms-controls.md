---
title: Události v ovládacích prvcích Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: 5d51b6a71bffb546c85ba253181453f6deecfa64
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525880"
---
# <a name="events-in-windows-forms-controls"></a>Události v ovládacích prvcích Windows Forms
Ovládacího prvku Windows Forms dědí více než 60 události z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Patří mezi ně <xref:System.Windows.Forms.Control.Paint> událost, což způsobí, že řízení, které se mají vykreslovat, události související s zobrazení časového období, jako <xref:System.Windows.Forms.Control.Resize> a <xref:System.Windows.Forms.Control.Layout> události a nízké úrovně události myši a klávesnice. Některé nízké úrovně události jsou syntetizován podle <xref:System.Windows.Forms.Control> do sémantického událostí jako <xref:System.Windows.Forms.Control.Click> a <xref:System.Windows.Forms.Control.DoubleClick>. Podrobnosti o zděděné události najdete v tématu <xref:System.Windows.Forms.Control>.  
  
 Pokud vaše vlastní ovládací prvek musí přepsat funkci zděděné událostí, mají přednost před zděděnou `On` *EventName* metody místo připojení delegáta. Pokud nejste obeznámeni s modelem události v rozhraní .NET Framework, přečtěte si téma [vyvolání události ze součásti](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).  
  
## <a name="see-also"></a>Viz také  
 [Přepsání metody OnPaint](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)  
 [Zpracování uživatelského vstupu](../../../../docs/framework/winforms/controls/handling-user-input.md)  
 [Definování události](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [Události](../../../../docs/standard/events/index.md)
