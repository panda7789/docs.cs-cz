---
title: "Ukazatele myši ve Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pointers [Windows Forms], setting
- mouse pointers
- mouse cursors
- mouse pointers [Windows Forms], setting
- cursors [Windows Forms], setting
- mouse [Windows Forms], cursors
ms.assetid: c3400d85-de5b-42e8-abc3-d6088d69ee53
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aaca18bff265fafbb5bad26adfe2a8c490d85132
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="mouse-pointers-in-windows-forms"></a>Ukazatele myši ve Windows Forms
Myš *ukazatel*, která se někdy označuje jako kurzor, je rastrového obrázku, který určuje bod fokus na obrazovce na vstup uživatele pomocí myši. Toto téma obsahuje přehled ukazatele myši ve Windows Forms a popisuje některé z způsobů, jak upravit a ovládat ukazatel myši.  
  
## <a name="accessing-the-mouse-pointer"></a>Přístup k ukazatele myši  
 Je reprezentována ukazatel myši <xref:System.Windows.Forms.Cursor> třídy a každý <xref:System.Windows.Forms.Control> má <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> vlastnost, která určuje ukazatele pro ovládací prvek. <xref:System.Windows.Forms.Cursor> Třída obsahuje vlastnosti, které popisují, jako má ukazatel <xref:System.Windows.Forms.Cursor.Position%2A> a <xref:System.Windows.Forms.Cursor.HotSpot%2A> vlastnosti a metody, které můžete upravit vzhled ukazatele, například <xref:System.Windows.Forms.Cursor.Show%2A>, <xref:System.Windows.Forms.Cursor.Hide%2A>, a <xref:System.Windows.Forms.Cursor.DrawStretched%2A> metody.  
  
## <a name="controlling-the-mouse-pointer"></a>Řízení ukazatele myši  
 V některých případech může chtít omezit oblasti, ve kterém ukazatele myši můžete použít nebo změní pozici myší. Můžete získat nebo nastavit aktuální umístění pomocí myši <xref:System.Windows.Forms.Cursor.Position%2A> vlastnost <xref:System.Windows.Forms.Cursor>. Kromě toho můžete omezit oblasti ukazatele myši můžete použít se nastavení <xref:System.Windows.Forms.Cursor.Clip%2A> vlastnost. Oblasti klip ve výchozím nastavení, je na celou obrazovku.  
  
## <a name="changing-the-mouse-pointer"></a>Změnu ukazatele myši  
 Změna ukazatel myši je důležité způsob, jak poskytnout zpětnou vazbu pro uživatele. Například můžete upravit ukazatel myši v obslužné rutiny z <xref:System.Windows.Forms.Control.MouseEnter> a <xref:System.Windows.Forms.Control.MouseLeave> události informuje uživatele, že se vyskytnou výpočty a interakci s uživatelem v ovládacím prvku. V některých případech se ukazatel myši změní z důvodu systémové události, například když je aplikace součástí operaci přetažení myší.  
  
 Primární způsob, jak změnit ukazatel myši je nastavením <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.Control.DefaultCursor%2A> vlastností ovládacího prvku na nový <xref:System.Windows.Forms.Cursor>. Příklady změnu ukazatele myši, viz příklad kódu v <xref:System.Windows.Forms.Cursor> třídy. Kromě toho <xref:System.Windows.Forms.Cursors> třída zpřístupňuje sadu <xref:System.Windows.Forms.Cursor> objekty pro mnoho různých typů ukazatele, jako je například ukazatele, který vypadá takto: dlaně. Chcete-li zobrazit ukazatele čekání, která vypadá přibližně takto: přesýpací hodiny, vždy, když ukazatel myši na ovládací prvek, použijte <xref:System.Windows.Forms.Control.UseWaitCursor%2A> vlastnost <xref:System.Windows.Forms.Control> – třída.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Cursor>  
 [Vstup z myši v aplikaci Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)  
 [Funkce přetažení ve Windows Forms](../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)
