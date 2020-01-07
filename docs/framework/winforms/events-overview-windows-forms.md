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
ms.openlocfilehash: 4abcf20b851f349a2b5df78c1fe1d15f729a5462
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345008"
---
# <a name="events-overview-windows-forms"></a>Přehled událostí (Windows Forms)
Událost je akce, na kterou můžete reagovat nebo "zpracovat" v kódu. Události mohou být generovány akcí uživatele, jako je například kliknutí myší nebo stisknutí klávesy. podle kódu programu; nebo systémem.

 Aplikace řízené událostmi spouštějí kód jako odpověď na událost. Každý formulář a ovládací prvek zveřejňuje předdefinovanou sadu událostí, které lze programovat. Pokud dojde k jedné z těchto událostí a v přidružené obslužné rutině události je kód, je vyvolán tento kód.

 Typy událostí vyvolaných objektem se liší, ale mnoho typů je běžné pro většinu ovládacích prvků. Například většina objektů zpracuje událost <xref:System.Windows.Forms.Control.Click>. Pokud uživatel klikne na formulář, spustí se kód v obslužné rutině události <xref:System.Windows.Forms.Control.Click> formuláře.

> [!NOTE]
> K mnoha událostem dochází ve spojení s jinými událostmi. Například v průběhu události <xref:System.Windows.Forms.Control.DoubleClick> dojde k událostem <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseUp>a <xref:System.Windows.Forms.Control.Click>.

 Informace o tom, jak vyvolat a zpracovat událost, najdete v tématu [události](../../standard/events/index.md).

## <a name="delegates-and-their-role"></a>Delegáti a jejich role
 Delegáti jsou třídy, které se běžně používají v rámci .NET Framework k sestavení mechanismů pro zpracování událostí. Delegáti jsou zhruba rovni ukazatelům funkce, běžně používané v C++ vizuálů a dalších objektově orientovaných jazycích. Na rozdíl od ukazatelů na funkce jsou však delegáti objektově orientovaný, typově bezpečný a zabezpečený. Kromě toho, kde ukazatel na funkci obsahuje pouze odkaz na konkrétní funkci, se delegát skládá z odkazu na objekt a odkazuje na jednu nebo více metod v rámci objektu.

 Tento model událostí používá *delegáty* ke svázání událostí s metodami, které se používají k jejich zpracování. Delegát umožňuje registrovat jiné třídy pro oznamování událostí zadáním metody obslužné rutiny. Když dojde k události, delegát volá metodu Bound. Další informace o tom, jak definovat delegáty, najdete v tématu [události](../../standard/events/index.md).

Delegáty mohou být vázány na jedinou metodu nebo na více metod, označovaných jako vícesměrové vysílání. Při vytváření delegáta pro událost (nebo Windows) se obvykle vytvoří událost vícesměrového vysílání. Vzácná výjimka může být událost, která má za následek určitou proceduru (například zobrazení dialogového okna), která by logicky neopakovala více časů na událost. Informace o tom, jak vytvořit delegáta vícesměrového vysílání, najdete v tématu [postup kombinování delegátů (vícesměrové delegáty)](../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md).

 Delegát vícesměrového vysílání udržuje seznam volání metod, ke kterým je vázán. Delegát vícesměrového vysílání podporuje metodu <xref:System.Delegate.Combine%2A> pro přidání metody do seznamu volání a metodu <xref:System.Delegate.Remove%2A> k jejímu odebrání.

 Když aplikace zaznamená událost, ovládací prvek vyvolá událost vyvoláním delegáta pro danou událost. Delegát zase volá metodu Bound. V nejběžnějším případě (delegát vícesměrového vysílání) volá delegát každou metodu, která je v seznamu volání, a poskytuje oznámení 1:1. Tato strategie znamená, že ovládací prvek nemusí udržovat seznam cílových objektů pro oznamování událostí – delegát zpracovává veškerou registraci a oznámení.

 Delegáti také umožňují svázat více událostí se stejnou metodou, což umožňuje oznámení typu n:1. Například událost kliknutí na tlačítko a příkaz nabídky-Click může vyvolat stejný delegát, který pak volá jedinou metodu pro zpracování těchto samostatných událostí stejným způsobem.

 Mechanizmus vazby, který se používá s delegáty, je dynamický: delegát může být vázán v době běhu na jakoukoli metodu, jejíž signatura odpovídá obslužné rutině události. Pomocí této funkce můžete nastavit nebo změnit metodu vazby v závislosti na podmínce a dynamicky připojit obslužnou rutinu události k ovládacímu prvku.

## <a name="see-also"></a>Viz také:

- [Vytváření obslužných rutin událostí ve Windows Forms](creating-event-handlers-in-windows-forms.md)
- [Přehled obslužných rutin událostí](event-handlers-overview-windows-forms.md)
