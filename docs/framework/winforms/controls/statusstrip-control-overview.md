---
title: StatusStrip – přehled ovládacího prvku
ms.date: 03/30/2017
f1_keywords:
- StatusStrip
helpviewer_keywords:
- StatusStrip control [Windows Forms], about StatusStrip control
- status bars [Windows Forms], about status bars
ms.assetid: c0d9bcbb-f8b8-46ef-bae2-4146b8c8ce99
ms.openlocfilehash: e40373dd05e59325cdb6c2272d5749f3828b0755
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864560"
---
# <a name="statusstrip-control-overview"></a>StatusStrip – přehled ovládacího prvku
A <xref:System.Windows.Forms.StatusStrip> ovládací prvek zobrazí informace o objektu na zobrazení <xref:System.Windows.Forms.Form>, komponenty, nebo objektu kontextové informace, které se týkají tohoto objektu operace v rámci vaší aplikace. Obvykle <xref:System.Windows.Forms.StatusStrip> ovládací prvek se skládá z <xref:System.Windows.Forms.ToolStripStatusLabel> objektů, z nichž každý zobrazuje text nebo ikonu. <xref:System.Windows.Forms.StatusStrip> Může také obsahovat <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, a <xref:System.Windows.Forms.ToolStripProgressBar> ovládací prvky.  
  
 Výchozí hodnota <xref:System.Windows.Forms.StatusStrip> nemá žádné panelů. K přidání panelů do <xref:System.Windows.Forms.StatusStrip>, použijte <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> metody.  
  
 Není k dispozici rozsáhlou podporu pro zpracování <xref:System.Windows.Forms.StatusStrip> položky a běžné příkazy v sadě Visual Studio.  
  
 Viz také [StatusStrip – Editor kolekce položek](https://msdn.microsoft.com/library/ms233631\(v=vs.110\)), [StatusStrip – dialogové okno úlohy](https://msdn.microsoft.com/library/ms233642\(v=vs.110\)).  
  
 I když <xref:System.Windows.Forms.StatusStrip> nahrazuje a rozšiřuje <xref:System.Windows.Forms.StatusBar> ovládacího prvku z předchozích verzí <xref:System.Windows.Forms.StatusBar> se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.  
  
### <a name="important-statusstrip-members"></a>StatusStrip – důležité členy  
  
|Název|Popis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.StatusStrip.CanOverflow%2A>|Získá nebo nastaví hodnotu označující, zda <xref:System.Windows.Forms.StatusStrip> podporuje přetečení funkce.|  
|<xref:System.Windows.Forms.StatusStrip.Stretch%2A>|Získá nebo nastaví hodnotu označující, zda <xref:System.Windows.Forms.StatusStrip> úsecích od začátku do konce v jeho <xref:System.Windows.Forms.ToolStripContainer>.|  
  
### <a name="important-statusstrip-companion-classes"></a>Třídy důležitého pomocníka StatusStrip  
  
|Název|Popis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|Představuje v panelu <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|Zobrazí přidružené <xref:System.Windows.Forms.ToolStripDropDown> ze kterého může uživatel vybrat jednu položku.|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|Představuje ovládací prvek dvě části, která je standardní tlačítko a rozevírací nabídky.|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|Zobrazí stav dokončení procesu.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>
