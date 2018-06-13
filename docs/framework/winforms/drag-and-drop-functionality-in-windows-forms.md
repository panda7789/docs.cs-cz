---
title: 'Přetažení funkce ve Windows Forms '
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms], Windows Forms
- Windows Forms, drag and drop
ms.assetid: 65cd2c03-8782-474e-b958-cbe43eeb902c
ms.openlocfilehash: c43d5ad9203afad67601d9e36447db7c49a5a98e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539397"
---
# <a name="drag-and-drop-functionality-in-windows-forms"></a>Přetažení funkce ve Windows Forms 
Windows Forms zahrnuje sadu metod, události a třídy, které implementují chování přetažení myší. Toto téma obsahuje přehled podpory přetažení myší v systému Windows Forms.  Viz také [operací přetažení myší a podpora schránky](http://msdn.microsoft.com/library/fe5ebfwe\(v=vs.110\)).  
  
## <a name="performing-drag-and-drop-operations"></a>Provádění operací přetažení myší  
 K provedení operace přetahování myší, pomocí <xref:System.Windows.Forms.Control.DoDragDrop%2A> metodu <xref:System.Windows.Forms.Control> třídy. Další informace o tom, jak se provádí operaci přetažení myší najdete v tématu <xref:System.Windows.Forms.Control.DoDragDrop%2A>. Obdélníku, která ukazatel myši musí přetáhli přes, před zahájením operace přetahování myší, použijte <xref:System.Windows.Forms.SystemInformation.DragSize%2A> vlastnost <xref:System.Windows.Forms.SystemInformation> třídy.  
  
## <a name="events-related-to-drag-and-drop-operations"></a>Události související s operací přetažení myší  
 Existují dvě kategorie události v rámci operace přetažení: události na aktuální cíl operace přetahování myší a události na zdroje operace přetažení.  
  
### <a name="events-on-the-current-target"></a>Události v aktuálním cílovém  
 Následující tabulka uvádí události, ke kterým došlo na aktuální cíl operace přetažení myší.  
  
|Události myši|Popis|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.DragEnter>|K této události dojde, když je objekt přetažen hranice ovládacího prvku. Obslužná rutina pro tuto událost přijme argument typu <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragOver>|K této události dojde, když objekt přetažení ukazatele myši při v rámci hranice ovládacího prvku. Obslužná rutina pro tuto událost přijme argument typu <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragDrop>|Tato událost nastane při dokončení operace přetažení myší. Obslužná rutina pro tuto událost přijme argument typu <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragLeave>|K této události dojde, když objekt ocitne mimo hranice ovládacího prvku. Obslužná rutina pro tuto událost přijme argument typu <xref:System.EventArgs>.|  
  
 <xref:System.Windows.Forms.DragEventArgs> Třída poskytuje umístění ukazatele myši, aktuální stav tlačítka myši a modifikační klávesy klávesnice, data se přetáhli, a <xref:System.Windows.Forms.DragDropEffects> hodnoty, které určují operace povoleny zdroj události přetažení a účinky rozevírací cíl pro tuto operaci.  
  
### <a name="events-on-the-source"></a>Události ve zdroji  
 Následující tabulka uvádí události, ke kterým došlo u zdroje operace přetažení myší.  
  
|Události myši|Popis|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.GiveFeedback>|K této události dojde během operace přetažení. Poskytuje možnost poskytnout vizuální upozornění uživateli, který operaci přetažení myší dochází, jako je například změna ukazatel myši. Obslužná rutina pro tuto událost přijme argument typu <xref:System.Windows.Forms.GiveFeedbackEventArgs>.|  
|<xref:System.Windows.Forms.Control.QueryContinueDrag>|Tato událost se vyvolá při operaci přetažení myší a umožňuje zdroje operace přetažení k určení, zda mají zrušit operace přetažení myší. Obslužná rutina pro tuto událost přijme argument typu <xref:System.Windows.Forms.QueryContinueDragEventArgs>.|  
  
 <xref:System.Windows.Forms.QueryContinueDragEventArgs> Třída poskytuje aktuální stav Myš, tlačítka a modifikační klávesy klávesnice, hodnotu udávající, zda byl stisknutí klávesy ESC a <xref:System.Windows.Forms.DragAction> hodnotu, která můžete nastavit k určení, zda by měly pokračovat ve operaci přetažení myší.  
  
## <a name="see-also"></a>Viz také  
 [Vstup z myši v aplikaci Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
