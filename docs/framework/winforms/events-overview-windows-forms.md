---
title: "Přehled událostí (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, event handling
- events [Windows Forms], about events
- delegates [Windows Forms], multicast
- delegates [Windows Forms], events and
- multicast event delegates
- Windows Forms controls, events
ms.assetid: 814a6a43-a312-4791-88d8-f75f9a4f8c4c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f73a336da5b61de90a67a8392b5cfc8f28619254
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="events-overview-windows-forms"></a>Přehled událostí (Windows Forms)
Událost je akci, která může reagovat, nebo "zpracování" v kódu. Události může být generována akci uživatele, jako je například kliknutí myši nebo stisknutím klávesy; v kódu programu; nebo v systému.  
  
 Událostmi řízené aplikace spustit kód v reakci na událost. Každý formulář a řízení zpřístupní předdefinovanou sadu událostí, které můžete naprogramovat oproti. Pokud dojde k jedné z těchto událostí a v související události obslužná rutina je kód, je vyvolána tento kód.  
  
 Typy událostí vyvolaných objektem liší, ale mnoho typů jsou společné pro většinu ovládacích prvků. Například bude zpracovávat většinu objektů <xref:System.Windows.Forms.Control.Click> událostí. Pokud uživatel klikne na formuláři, kód na formuláře <xref:System.Windows.Forms.Control.Click> se spustí obslužnou rutinu události.  
  
> [!NOTE]
>  Mnoho událostem ve spojení s jinými událostmi. Například v nahradil z <xref:System.Windows.Forms.Control.DoubleClick> událostí, ke kterým dochází, <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseUp>, a <xref:System.Windows.Forms.Control.Click> události.  
  
 Informace o tom, jak vyvolávání a zpracovávání událostí najdete v tématu [události](../../../docs/standard/events/index.md).  
  
## <a name="delegates-and-their-role"></a>Delegáti a jejich Role  
 Delegáti jsou běžně používané v rámci třídy [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] k sestavení mechanismy zpracování událostí. Delegáti zhruba rovnat ukazatelů na funkce, se běžně používají při [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] a další jazyky objektově orientovaný. Na rozdíl od ukazatelů na funkce Delegáti jsou však objektově orientované, bezpečnost typů a zabezpečení. Kromě toho, kde ukazatel na funkci obsahuje pouze odkaz na určitou funkci, delegáta se skládá z odkaz na objekt a odkazuje na jeden nebo více metod v rámci objektu.  
  
 Tento model událostí používá *delegáti* k vytvoření vazby události metody, které se používají k jejich zpracování. Delegát umožňuje ostatní třídy registrace pro oznámení o události zadáním metody obslužné rutiny. Když dojde k události, delegát volá metodu vazby. Další informace o tom, jak definovat delegáti najdete v tématu [události](../../../docs/standard/events/index.md).  
  
 Delegáti mohou být vázány do jedné metody nebo na několik metod, označuje jako vícesměrového vysílání. Při vytváření delegát pro událost, vy (nebo Windows Forms designerem) obvykle vytvoření vícesměrového vysílání události. Výjimečných výjimka může být událost, která má za následek konkrétní procedury (například zobrazení dialogového okna), která by logicky opakovat vícekrát na událost. Informace o tom, jak vytvořit vícesměrového vysílání delegáta najdete v tématu [postupy: kombinování delegátů (vícesměroví delegáti)](~/docs/csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md).  
  
 Vícesměrového vysílání delegáta udržuje seznam vyvolání metod, které je vázána na. Podporuje delegovat vícesměrové vysílání <xref:System.Delegate.Combine%2A> metoda pro přidání do seznamu vyvolání metody a <xref:System.Delegate.Remove%2A> metoda jeho odebrání.  
  
 Když událost se zaznamená aplikací, ovládacího prvku vyvolává událost vyvoláním delegáta pro tuto událost. Delegát volá metodu vazby. V případě nejběžnějších (delegovat vícesměrové vysílání) delegát volá každý vázané metodu v seznamu vyvolání zase, který poskytuje oznámení na více. Tato strategie znamená, že ovládací prvek není potřeba spravovat seznam cílové objekty pro oznámení o události – delegát zpracovává všechny registrace a oznámení.  
  
 Delegáti také povolit více událostí bylo vázané na stejnou metodu povolení oznámení n 1. Například kliknutí na tlačítko události a události nabídky příkaz – kliknutím obě vyvolat stejné delegáta, který pak zavolá jedné metody pro zpracování tyto samostatné události stejným způsobem.  
  
 Vazba používáno s delegáti je dynamický: delegáta mohou být vázány v době běhu na libovolné metody, jejichž podpis odpovídá obslužné rutiny události. Pomocí této funkce můžete nastavit nebo změnit metodu vazby v závislosti na podmínce a dynamicky připojit obslužné rutiny událostí do ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření obslužných rutin událostí ve Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [Přehled obslužných rutin událostí](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)
