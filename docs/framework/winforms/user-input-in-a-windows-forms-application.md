---
title: "Uživatelský vstup ve formulářové aplikaci Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Windows Forms, user input
ms.assetid: 9d61fa96-70f7-4754-885a-49a4a6316bdb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fb6f832b77404b57ab22e4ac472e7707f0e10dd5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="user-input-in-a-windows-forms-application"></a>Uživatelský vstup ve formulářové aplikaci Windows
V systému Windows Forms uživatelský vstup se odesílají do aplikace ve formě zpráv systému Windows. Řadu přepisovatelné metody zpracování těchto zpráv v aplikaci, formuláře a řídit úroveň. Tyto metody přijímat zprávy myši a klávesnice, vyvolají události, které může být zpracována pro získání informací o myši nebo klávesové vstup. V mnoha případech bude schopna zpracovat veškerý vstup uživatele jednoduše tak, že zpracování těchto událostí formulářových aplikací Windows. V ostatních případech možná muset aplikaci přepsat jednu z metod, které zpracovávají zprávy, aby bylo možné zachytit určité zprávy dřív, než je přijat aplikace, formulář nebo ovládací prvek.  
  
## <a name="mouse-and-keyboard-events"></a>Událostí myši a klávesnice  
 Všechny ovládací prvky Windows Forms dědit sadu událostí souvisejících s myši a vstup z klávesnice. Například může zpracovat ovládacího prvku <xref:System.Windows.Forms.Control.KeyPress> dokáže zpracovat událostí k určení kód znaku klíče, která byla stisknuta nebo ovládacího prvku <xref:System.Windows.Forms.Control.MouseClick> událostí k určení umístění myši klikněte na tlačítko. Další informace o události myši a klávesnice v tématu [události klávesnice s použitím](../../../docs/framework/winforms/using-keyboard-events.md) a [události myši ve Windows Forms](../../../docs/framework/winforms/mouse-events-in-windows-forms.md).  
  
## <a name="methods-that-process-user-input-messages"></a>Metody, které zpracovávají zprávy vstupu uživatele  
 Formuláře a ovládací prvky mít přístup k <xref:System.Windows.Forms.IMessageFilter> rozhraní a sada přepisovatelné metody, které zpracovávají zpráv systému Windows v různých fázích fronty zpráv. Tyto metody jsou vybavené <xref:System.Windows.Forms.Message> parametr, který zapouzdřuje nízké úrovně podrobnosti zpráv systému Windows. Můžete implementovat nebo přepsat tyto metody pro zkontrolujte zprávy a využívat zprávy nebo předejte jej k další příjemce ve frontě zpráv. Následující tabulka představuje metody, které zpracovávají všechny zpráv systému Windows ve Windows Forms.  
  
|Metoda|Poznámky|  
|------------|-----------|  
|<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A>|Tato metoda zachytí zařazených do fronty zpráv systému Windows (také označované jako odeslané) na úrovni aplikace.|  
|<xref:System.Windows.Forms.Control.PreProcessMessage%2A>|Tato metoda zachytí zpráv systému Windows na úrovni formuláře a ovládací prvek předtím, než byly zpracovány.|  
|<xref:System.Windows.Forms.Control.WndProc%2A>|Tato metoda zpracovává zpráv systému Windows na úrovni formuláře a ovládací prvek.|  
|<xref:System.Windows.Forms.Control.DefWndProc%2A>|Tato metoda provádí výchozí zpracování zpráv systému Windows na úrovni formuláře a ovládací prvek. To poskytuje minimální funkce časového období.|  
|<xref:System.Windows.Forms.Control.OnNotifyMessage%2A>|Tato metoda přijímá zprávy na úrovni formuláře a ovládací prvek po jejich zpracování. <xref:System.Windows.Forms.ControlStyles.EnableNotifyMessage> Bit stylu musí být nastaven pro tuto metodu, která se má volat.|  
  
 Další sadu přepisovatelné metody, které jsou specifické pro tyto typy zpráv také zpracovává zprávy klávesnici a myš. Další informace najdete v tématu [jak funguje vstup klávesnice](../../../docs/framework/winforms/how-keyboard-input-works.md) a [jak funguje vstup myši Windows Forms](../../../docs/framework/winforms/how-mouse-input-works-in-windows-forms.md).  
  
## <a name="see-also"></a>Viz také  
 [Uživatelský vstup ve Windows Forms](../../../docs/framework/winforms/user-input-in-windows-forms.md)  
 [Vstup z klávesnice ve Windows Forms aplikace](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [Vstup z myši ve Windows Forms aplikace](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
