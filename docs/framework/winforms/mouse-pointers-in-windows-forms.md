---
title: Ukazatele myši
ms.date: 03/30/2017
helpviewer_keywords:
- pointers [Windows Forms], setting
- mouse pointers
- mouse cursors
- mouse pointers [Windows Forms], setting
- cursors [Windows Forms], setting
- mouse [Windows Forms], cursors
ms.assetid: c3400d85-de5b-42e8-abc3-d6088d69ee53
ms.openlocfilehash: 4e8349effcd9b59045e39b763b4cb8b7d2fceb91
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740954"
---
# <a name="mouse-pointers-in-windows-forms"></a>Ukazatele myši ve Windows Forms
*Ukazatel*myši, který se někdy označuje jako ukazatel, je rastrový obrázek, který určuje fokus na obrazovce pro vstup uživatele pomocí myši. Toto téma poskytuje přehled ukazatele myši v model Windows Forms a popisuje některé způsoby, jak upravit a ovládat ukazatel myši.  
  
## <a name="accessing-the-mouse-pointer"></a>Přístup k ukazateli myši  
 Ukazatel myši je reprezentován třídou <xref:System.Windows.Forms.Cursor> a každý <xref:System.Windows.Forms.Control> má vlastnost <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType>, která určuje ukazatel pro daný ovládací prvek. Třída <xref:System.Windows.Forms.Cursor> obsahuje vlastnosti, které popisují ukazatel, jako jsou vlastnosti <xref:System.Windows.Forms.Cursor.Position%2A> a <xref:System.Windows.Forms.Cursor.HotSpot%2A>, a metody, které mohou upravovat vzhled ukazatele, například <xref:System.Windows.Forms.Cursor.Show%2A>, <xref:System.Windows.Forms.Cursor.Hide%2A>a <xref:System.Windows.Forms.Cursor.DrawStretched%2A> metody.  
  
## <a name="controlling-the-mouse-pointer"></a>Řízení ukazatele myši  
 Někdy možná budete chtít omezit oblast, ve které se dá ukazatel myši použít, nebo změnit polohu myši. Aktuální polohu myši můžete získat nebo nastavit pomocí vlastnosti <xref:System.Windows.Forms.Cursor.Position%2A> <xref:System.Windows.Forms.Cursor>. Kromě toho můžete omezit oblast, kterou lze použít ukazatel myši k nastavení vlastnosti <xref:System.Windows.Forms.Cursor.Clip%2A>. Oblast klipu je ve výchozím nastavení celá obrazovka.  
  
## <a name="changing-the-mouse-pointer"></a>Změna ukazatele myši  
 Změna ukazatele myši je důležitým způsobem, jak poskytnout uživateli zpětnou vazbu. Ukazatel myši lze například upravit v obslužných rutinách <xref:System.Windows.Forms.Control.MouseEnter> a <xref:System.Windows.Forms.Control.MouseLeave> události, aby uživateli informovali, že k výpočtům dochází a omezení interakce uživatele v ovládacím prvku. V některých případech se ukazatel myši změní z důvodu systémových událostí, například když je vaše aplikace součástí operace přetažení.  
  
 Hlavní způsob, jak změnit ukazatel myši, je nastavením vlastnosti <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.Control.DefaultCursor%2A> ovládacího prvku na nový <xref:System.Windows.Forms.Cursor>. Příklady, jak změnit ukazatel myši, naleznete v příkladu kódu ve třídě <xref:System.Windows.Forms.Cursor>. Kromě toho třída <xref:System.Windows.Forms.Cursors> zpřístupňuje sadu <xref:System.Windows.Forms.Cursor> objektů pro mnoho různých typů ukazatelů, jako je ukazatel, který se podobá ruky. Chcete-li zobrazit ukazatel čekání, který se podobá přesýpacích hodin, pokaždé, když je ukazatel myši na ovládacím prvku, použijte vlastnost <xref:System.Windows.Forms.Control.UseWaitCursor%2A> třídy <xref:System.Windows.Forms.Control>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Cursor>
- [Vstup z myši v aplikaci Windows Forms](mouse-input-in-a-windows-forms-application.md)
- [Funkce přetažení ve Windows Forms](drag-and-drop-functionality-in-windows-forms.md)
