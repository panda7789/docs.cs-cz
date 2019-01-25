---
title: Události v ovládacích prvcích Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: 253783f50fdbef0890ea16baa9ac996b63795ed8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716959"
---
# <a name="events-in-windows-forms-controls"></a>Události v ovládacích prvcích Windows Forms
Dědí z více než 60 události ovládacího prvku Windows Forms <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Patří mezi ně <xref:System.Windows.Forms.Control.Paint> událost, což způsobí, že ovládací prvek chcete kreslit, události související s zobrazení okna, například <xref:System.Windows.Forms.Control.Resize> a <xref:System.Windows.Forms.Control.Layout> události a nízké úrovně události myši a klávesnice. Některé události nízké úrovně jsou syntetizovat podle <xref:System.Windows.Forms.Control> do sémantického událostech, například <xref:System.Windows.Forms.Control.Click> a <xref:System.Windows.Forms.Control.DoubleClick>. Podrobnosti o zděděné události najdete v tématu <xref:System.Windows.Forms.Control>.  
  
 Pokud vaše vlastní ovládací prvek musí přepsat funkci zděděných událostí, přepsat zděděnou `On` *EventName* metoda místo připojením delegáta. Pokud nejste obeznámeni s modelem události v rozhraní .NET Framework, přečtěte si téma [vyvolávání událostí z komponenty](https://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).  
  
## <a name="see-also"></a>Viz také:
- [Přepsání metody OnPaint](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)
- [Zpracování uživatelského vstupu](../../../../docs/framework/winforms/controls/handling-user-input.md)
- [Definování události](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
- [Události](../../../../docs/standard/events/index.md)
