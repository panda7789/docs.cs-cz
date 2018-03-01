---
title: "StatusStrip – přehled ovládacího prvku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StatusStrip
helpviewer_keywords:
- StatusStrip control [Windows Forms], about StatusStrip control
- status bars [Windows Forms], about status bars
ms.assetid: c0d9bcbb-f8b8-46ef-bae2-4146b8c8ce99
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f6d1eb698dbb9168bf5de6d3982e19e69d170ac0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="statusstrip-control-overview"></a>StatusStrip – přehled ovládacího prvku
A <xref:System.Windows.Forms.StatusStrip> ovládací prvek zobrazí informace o objektu se zobrazit na <xref:System.Windows.Forms.Form>, součásti objektu nebo kontextové informace, která má vztah k operaci tento objekt v rámci vaší aplikace. Obvykle <xref:System.Windows.Forms.StatusStrip> řízení se skládá z <xref:System.Windows.Forms.ToolStripStatusLabel> objekty, z nichž každý zobrazí text, ikonu nebo obojí. <xref:System.Windows.Forms.StatusStrip> Může také obsahovat <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, a <xref:System.Windows.Forms.ToolStripProgressBar> ovládací prvky.  
  
 Výchozí hodnota <xref:System.Windows.Forms.StatusStrip> nemá žádné panelů. Přidání panelů do <xref:System.Windows.Forms.StatusStrip>, použijte <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> metoda.  
  
 Je rozsáhlá podpora pro zpracování <xref:System.Windows.Forms.StatusStrip> položky a běžné příkazy v sadě Visual Studio.  
  
 Viz také [Editor kolekce položek StatusStrip](http://msdn.microsoft.com/library/ms233631\(v=vs.110\)), [Úkoly prvku StatusStrip](http://msdn.microsoft.com/library/ms233642\(v=vs.110\)).  
  
 I když <xref:System.Windows.Forms.StatusStrip> nahrazuje a rozšiřuje <xref:System.Windows.Forms.StatusBar> řízení předchozí verze, <xref:System.Windows.Forms.StatusBar> se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte.  
  
### <a name="important-statusstrip-members"></a>Důležité StatusStrip členy  
  
|Název|Popis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.StatusStrip.CanOverflow%2A>|Získá nebo nastaví hodnotu, která určuje zda <xref:System.Windows.Forms.StatusStrip> podporuje přetečení funkce.|  
|<xref:System.Windows.Forms.StatusStrip.Stretch%2A>|Získá nebo nastaví hodnotu, která určuje zda <xref:System.Windows.Forms.StatusStrip> úsecích z konce v jeho <xref:System.Windows.Forms.ToolStripContainer>.|  
  
### <a name="important-statusstrip-companion-classes"></a>Třídy důležitého pomocníka StatusStrip  
  
|Název|Popis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|Představuje panelu v <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|Zobrazí přiřazený <xref:System.Windows.Forms.ToolStripDropDown> ze kterého může uživatel vybrat jednu položku.|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|Reprezentuje ovládací prvek dvoudílný článek, který je standardní tlačítko a z rozevírací nabídky.|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|Zobrazí stav dokončení procesu.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>
