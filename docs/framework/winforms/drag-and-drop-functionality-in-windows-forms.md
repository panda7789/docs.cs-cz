---
title: Funkce přetažení
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms], Windows Forms
- Windows Forms, drag and drop
ms.assetid: 65cd2c03-8782-474e-b958-cbe43eeb902c
ms.openlocfilehash: 603dc158719c0b11def4386eb24a33f235cf3a42
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732757"
---
# <a name="drag-and-drop-functionality-in-windows-forms"></a>Přetažení funkce ve Windows Forms
Model Windows Forms obsahuje sadu metod, událostí a tříd, které implementují chování přetažení. V tomto tématu najdete přehled podpory přetahování myší v model Windows Forms.  Viz také [operace přetažení a podpora schránky](./advanced/drag-and-drop-operations-and-clipboard-support.md).  
  
## <a name="performing-drag-and-drop-operations"></a>Provádění operací přetažení  
 Chcete-li provést operaci přetažení, použijte metodu <xref:System.Windows.Forms.Control.DoDragDrop%2A> třídy <xref:System.Windows.Forms.Control>. Další informace o tom, jak se provádí operace přetažení, najdete v tématu <xref:System.Windows.Forms.Control.DoDragDrop%2A>. Chcete-li získat obdélník, který je třeba přetáhnout ukazatelem myši před zahájením operace přetažení, použijte vlastnost <xref:System.Windows.Forms.SystemInformation.DragSize%2A> třídy <xref:System.Windows.Forms.SystemInformation>.  
  
## <a name="events-related-to-drag-and-drop-operations"></a>Události související s operacemi přetažení  
 V operaci přetažení existují dvě kategorie událostí: události, ke kterým dochází na aktuálním cíli operace přetažení, a události, ke kterým dochází ve zdroji operace přetažení.  
  
### <a name="events-on-the-current-target"></a>Události v aktuálním cíli  
 V následující tabulce jsou uvedeny události, ke kterým dochází v aktuálním cíli operace přetažení.  
  
|Událost myši|Popis|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.DragEnter>|Tato událost nastane, pokud je objekt přetažen do hranic ovládacího prvku. Obslužná rutina pro tuto událost obdrží argument typu <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragOver>|Tato událost nastane, pokud je objekt přetažen, zatímco ukazatel myši je v rámci meze ovládacího prvku. Obslužná rutina pro tuto událost obdrží argument typu <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragDrop>|Tato událost nastane, když se dokončí operace přetažení myší. Obslužná rutina pro tuto událost obdrží argument typu <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragLeave>|Tato událost nastane, pokud je objekt přetažen mimo hranice ovládacího prvku. Obslužná rutina pro tuto událost obdrží argument typu <xref:System.EventArgs>.|  
  
 Třída <xref:System.Windows.Forms.DragEventArgs> poskytuje umístění ukazatele myši, aktuální stav tlačítek myši a modifikační klávesy klávesnice, přetažená data a <xref:System.Windows.Forms.DragDropEffects> hodnoty, které určují operace povolené zdrojem události přetažení a cílového cílového efektu pro operaci.  
  
### <a name="events-on-the-source"></a>Události ve zdroji  
 V následující tabulce jsou uvedeny události, ke kterým dochází ve zdroji operace přetažení.  
  
|Událost myši|Popis|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.GiveFeedback>|Tato událost nastane během operace přetažení. Nabízí možnost poskytnout uživateli vizuální upozornění, že probíhá operace přetažení, jako je například změna ukazatele myši. Obslužná rutina pro tuto událost obdrží argument typu <xref:System.Windows.Forms.GiveFeedbackEventArgs>.|  
|<xref:System.Windows.Forms.Control.QueryContinueDrag>|Tato událost je vyvolána během operace přetažení a umožňuje zdroji přetažení určit, zda má být operace přetažení zrušena. Obslužná rutina pro tuto událost obdrží argument typu <xref:System.Windows.Forms.QueryContinueDragEventArgs>.|  
  
 Třída <xref:System.Windows.Forms.QueryContinueDragEventArgs> poskytuje aktuální stav tlačítek myši a modifikační klávesy klávesnice, hodnotu určující, zda byla stisknuta klávesa ESC, a hodnotu <xref:System.Windows.Forms.DragAction>, která může být nastavena k určení, zda má být operace přetažení pokračovat.  
  
## <a name="see-also"></a>Viz také

- [Vstup z myši v aplikaci Windows Forms](mouse-input-in-a-windows-forms-application.md)
