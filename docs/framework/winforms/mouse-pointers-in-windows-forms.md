---
title: Ukazatele myši ve Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- pointers [Windows Forms], setting
- mouse pointers
- mouse cursors
- mouse pointers [Windows Forms], setting
- cursors [Windows Forms], setting
- mouse [Windows Forms], cursors
ms.assetid: c3400d85-de5b-42e8-abc3-d6088d69ee53
ms.openlocfilehash: e9b572ba40618a72b8db58917008ebd61a23de79
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122782"
---
# <a name="mouse-pointers-in-windows-forms"></a>Ukazatele myši ve Windows Forms
Myši *ukazatel*, které se někdy označuje jako ukazatel, je rastrový obrázek, který určuje zaměření na obrazovce pro uživatelský vstup pomocí myši. Toto téma obsahuje základní informace o umístění ukazatele myši ve Windows Forms a popisuje některé ze způsobů, jak upravit a řízení umístění ukazatele myši.  
  
## <a name="accessing-the-mouse-pointer"></a>Přístup k umístění ukazatele myši  
 Je reprezentován ukazatel myši <xref:System.Windows.Forms.Cursor> třídy a každý <xref:System.Windows.Forms.Control> má <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> vlastnost, která určuje ukazatele pro tento ovládací prvek. <xref:System.Windows.Forms.Cursor> Třída obsahuje vlastnosti, které popisují ukazatel, jako <xref:System.Windows.Forms.Cursor.Position%2A> a <xref:System.Windows.Forms.Cursor.HotSpot%2A> vlastnosti a metody, které lze změnit vzhled ukazatele, například <xref:System.Windows.Forms.Cursor.Show%2A>, <xref:System.Windows.Forms.Cursor.Hide%2A>, a <xref:System.Windows.Forms.Cursor.DrawStretched%2A> metody.  
  
## <a name="controlling-the-mouse-pointer"></a>Řízení umístění ukazatele myši  
 Někdy můžete chtít omezit oblasti, ve kterém ukazatel myši lze použít nebo změně pozice myši. Můžete získat nebo nastavit aktuální umístění pomocí myši <xref:System.Windows.Forms.Cursor.Position%2A> vlastnost <xref:System.Windows.Forms.Cursor>. Kromě toho můžete omezit oblasti, lze ukazatel myši se nastavení <xref:System.Windows.Forms.Cursor.Clip%2A> vlastnost. Galerie oblast, ve výchozím nastavení, je na celé obrazovce.  
  
## <a name="changing-the-mouse-pointer"></a>Změna umístění ukazatele myši  
 Změna umístění ukazatele myši je to důležité způsob poskytnutí zpětné vazby pro uživatele. Například lze upravit umístění ukazatele myši v obslužné rutině z <xref:System.Windows.Forms.Control.MouseEnter> a <xref:System.Windows.Forms.Control.MouseLeave> události říct uživatelům, že dochází k výpočtům a omezit interakce s uživatelem v ovládacím prvku. V některých případech ukazatel myši se změní z důvodu systémové události, například když je aplikace součástí operace přetažení myší.  
  
 Primárním způsob, jak změnit ukazatel myši je tak, že nastavíte <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.Control.DefaultCursor%2A> vlastnost ovládacího prvku do nového <xref:System.Windows.Forms.Cursor>. Příklady změnu ukazatele myši, naleznete v příkladu kódu v <xref:System.Windows.Forms.Cursor> třídy. Kromě toho <xref:System.Windows.Forms.Cursors> třída zveřejňuje sadu <xref:System.Windows.Forms.Cursor> objekty pro mnoho různých typů ukazatelů, jako je ukazatel, který vypadá podobně jako na tvar ruky. Chcete-li zobrazení ukazatele čekání, který se podobá přesýpací hodiny, pokaždé, když je ukazatel myši na ovládací prvek, použijte <xref:System.Windows.Forms.Control.UseWaitCursor%2A> vlastnost <xref:System.Windows.Forms.Control> třídy.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Cursor>
- [Vstup z myši v aplikaci Windows Forms](mouse-input-in-a-windows-forms-application.md)
- [Přetažení funkce ve Windows Forms ](drag-and-drop-functionality-in-windows-forms.md)
