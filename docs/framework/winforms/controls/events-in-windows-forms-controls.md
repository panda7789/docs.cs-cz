---
title: "Události v ovládacích prvcích Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2dba74214fe439e09d1855f7ab248c075bd8257c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="events-in-windows-forms-controls"></a>Události v ovládacích prvcích Windows Forms
Ovládacího prvku Windows Forms dědí více než 60 události z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Patří mezi ně <xref:System.Windows.Forms.Control.Paint> událost, což způsobí, že řízení, které se mají vykreslovat, události související s zobrazení časového období, jako <xref:System.Windows.Forms.Control.Resize> a <xref:System.Windows.Forms.Control.Layout> události a nízké úrovně události myši a klávesnice. Některé nízké úrovně události jsou syntetizován podle <xref:System.Windows.Forms.Control> do sémantického událostí jako <xref:System.Windows.Forms.Control.Click> a <xref:System.Windows.Forms.Control.DoubleClick>. Podrobnosti o zděděné události najdete v tématu <xref:System.Windows.Forms.Control>.  
  
 Pokud vaše vlastní ovládací prvek musí přepsat funkci zděděné událostí, mají přednost před zděděnou `On` *EventName* metody místo připojení delegáta. Pokud nejste obeznámeni s modelem události v rozhraní .NET Framework, přečtěte si téma [vyvolání události ze součásti](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).  
  
## <a name="see-also"></a>Viz také  
 [Přepsání metody OnPaint](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)  
 [Zpracování uživatelského vstupu](../../../../docs/framework/winforms/controls/handling-user-input.md)  
 [Definování události](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [Události](../../../../docs/standard/events/index.md)
