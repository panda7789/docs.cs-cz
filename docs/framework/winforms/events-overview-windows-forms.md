---
title: Přehled událostí (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, event handling
- events [Windows Forms], about events
- delegates [Windows Forms], multicast
- delegates [Windows Forms], events and
- multicast event delegates
- Windows Forms controls, events
ms.assetid: 814a6a43-a312-4791-88d8-f75f9a4f8c4c
ms.openlocfilehash: 57802cad0a75ed21bba02a11fec39f821835c5ea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157750"
---
# <a name="events-overview-windows-forms"></a>Přehled událostí (Windows Forms)
Událost je akci, která můžete reagovat, nebo "handle" v kódu. Události mohou být generovány akci uživatele, jako je například kliknutí myší nebo stisknutí klávesy; pomocí programového kódu; nebo v systému.  
  
 Aplikací řízených událostmi spouštění kódu v reakci na událost. Každý formulář a ovládací prvek zpřístupňuje předdefinovanou sadu událostí, které můžete programovat proti. Pokud dojde k jedné z těchto událostí a není kód v obslužné rutině související události, je vyvolána, že kód.  
  
 Typy událostí vyvolaných v objektu liší, ale mnoho typů jsou společné pro většinu ovládacích prvků. Například bude zpracovávat většinu objektů <xref:System.Windows.Forms.Control.Click> událostí. Pokud uživatel klikne na formuláři, kód formuláře <xref:System.Windows.Forms.Control.Click> obslužná rutina události je proveden.  
  
> [!NOTE]
>  Mnoho událostem ve spojení s jinými událostmi. Například v průběhu z <xref:System.Windows.Forms.Control.DoubleClick> události, ke kterým dochází, <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseUp>, a <xref:System.Windows.Forms.Control.Click> dojde k událostem.  
  
 Informace o tom, jak vyvolat a zpracovat událost, naleznete v tématu [události](../../standard/events/index.md).  
  
## <a name="delegates-and-their-role"></a>Delegáty a jejich Role  
 Delegáti jsou třídy často používané v rámci [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sestavit mechanismy zpracování událostí. Delegáti zhruba odpovídá na ukazatele funkcí, běžně používaná v [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] a další jazyky objektově orientovaný. Na rozdíl od ukazatelů na funkce delegátů jsou však objektově orientované, typově bezpečné a zabezpečené. Kromě toho, kde obsahuje pouze odkaz na určitou funkci, ukazatel na funkci delegáta se skládá z odkazu na objekt a odkazy na jeden nebo více metod v rámci objektu.  
  
 Tento model událostí používá *delegáti* svázat události do metod, které se používají k jejich zpracování. Delegát umožňuje jiné třídy registrace pro oznámení události tak, že určíte metodu obslužné rutiny. Při výskytu události, delegát volá metodu vazby. Další informace o tom, jak definovat delegáty, naleznete v tématu [události](../../standard/events/index.md).  
  
 Delegáty lze vázána na jedinou metodu nebo více metod, označuje jako vícesměrové vysílání. Při vytváření delegáta pro událost, vy (nebo Návrhář formulářů Windows) obvykle vytvoříte vícesměrového vysílání události. Výjimečných výjimky může být událost, která má za následek konkrétní procedury (například zobrazení dialogového okna), která by logicky opakujte více než jednou na událost. Informace o tom, jak vytvořit delegáta vícesměrového vysílání najdete v tématu [jak: Kombinování delegátů (vícesměroví delegáti)](~/docs/csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md).  
  
 Vícesměrového vysílání delegáta udržuje seznam volání metod, které je vázán na. Delegovat podporuje vícesměrové vysílání <xref:System.Delegate.Combine%2A> metodu pro přidání do seznamu vyvolání metody a <xref:System.Delegate.Remove%2A> metoda jeho odstranění.  
  
 Když se zaznamená událost aplikací, ovládací prvek vyvolá událost vyvoláním delegátů pro tuto událost. Delegát volá metodu vazby. V případě nejběžnějších (delegáta vícesměrové vysílání) delegáta volá každou metodu vazby v seznamu vyvolání zase poskytující oznámení jeden mnoho. Tato strategie znamená, že ovládací prvek není nutné udržovat seznam cílové objektů pro oznámení události, delegát zpracovává všechny registrace a oznámení.  
  
 Delegáti také povolit více událostí bylo vázané na stejnou metodu, povolení oznámení: 1. Například kliknutí na tlačítko události a události nabídky příkazu – kliknutím můžete oba vyvolat stejného delegáta, která potom volá jedinou metodu ke zpracování stejným způsobem jako tyto samostatné události.  
  
 Mechanismus vazby, který se používá s delegáty je dynamický: delegát může být vázaný v době běhu na jakoukoli metodu, jejíž podpis odpovídá obslužné rutiny události. Pomocí této funkce můžete nastavit nebo změnit metodu vázané na podmínce a dynamicky připojit obslužnou rutinu události pro ovládací prvek.  
  
## <a name="see-also"></a>Viz také:

- [Vytváření obslužných rutin událostí ve Windows Forms](creating-event-handlers-in-windows-forms.md)
- [Přehled obslužných rutin událostí](event-handlers-overview-windows-forms.md)
