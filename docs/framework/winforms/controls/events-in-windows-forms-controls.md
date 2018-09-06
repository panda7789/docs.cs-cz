---
title: Události v ovládacích prvcích Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: d18938565c302be085b7ac51f878d83ae5ab533d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44032242"
---
# <a name="events-in-windows-forms-controls"></a>Události v ovládacích prvcích Windows Forms
Dědí z více než 60 události ovládacího prvku Windows Forms <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Patří mezi ně <xref:System.Windows.Forms.Control.Paint> událost, což způsobí, že ovládací prvek chcete kreslit, události související s zobrazení okna, například <xref:System.Windows.Forms.Control.Resize> a <xref:System.Windows.Forms.Control.Layout> události a nízké úrovně události myši a klávesnice. Některé události nízké úrovně jsou syntetizovat podle <xref:System.Windows.Forms.Control> do sémantického událostech, například <xref:System.Windows.Forms.Control.Click> a <xref:System.Windows.Forms.Control.DoubleClick>. Podrobnosti o zděděné události najdete v tématu <xref:System.Windows.Forms.Control>.  
  
 Pokud vaše vlastní ovládací prvek musí přepsat funkci zděděných událostí, přepsat zděděnou `On` *EventName* metoda místo připojením delegáta. Pokud nejste obeznámeni s modelem události v rozhraní .NET Framework, přečtěte si téma [vyvolávání událostí z komponenty](https://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).  
  
## <a name="see-also"></a>Viz také  
 [Přepsání metody OnPaint](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)  
 [Zpracování uživatelského vstupu](../../../../docs/framework/winforms/controls/handling-user-input.md)  
 [Definování události](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [Události](../../../../docs/standard/events/index.md)
