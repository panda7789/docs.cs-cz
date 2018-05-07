---
title: NotifyIcon – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
ms.openlocfilehash: 0da485bf377b263d07a2f0ec27c5e94e4274d8ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="notifyicon-component-overview-windows-forms"></a>NotifyIcon – přehled komponenty (Windows Forms)
Windows Forms <xref:System.Windows.Forms.NotifyIcon> součást se obvykle používá pro zobrazení ikon pro procesy, které běží na pozadí a nezobrazovat uživateli rozhraní většinu času. Příkladem může být antivirový program, můžete dostat kliknutím na ikonu v oznamovací oblasti stav na hlavním panelu.  
  
## <a name="key-properties-of-notifyicons"></a>Klíčové vlastnosti NotifyIcons  
 Každý <xref:System.Windows.Forms.NotifyIcon> součást zobrazí jeden ikonu na stavovém řádku. Pokud máte tři procesy na pozadí a chcete zobrazit ikony pro každou, je třeba přidat tři <xref:System.Windows.Forms.NotifyIcon> komponenty do formuláře. Klíčové vlastnosti <xref:System.Windows.Forms.NotifyIcon> jsou součástí <xref:System.Windows.Forms.NotifyIcon.Icon%2A> a <xref:System.Windows.Forms.NotifyIcon.Visible%2A>. <xref:System.Windows.Forms.NotifyIcon.Icon%2A> Vlastnost nastaví na ikonu, který se zobrazí v oblasti stavu. Aby se na ikonu se zobrazí <xref:System.Windows.Forms.NotifyIcon.Visible%2A> musí být nastavena na `true`.  
  
 Pokud používáte [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], máte přístup k rozsáhlé knihovně standardní bitové kopie, které můžete použít s <xref:System.Windows.Forms.NotifyIcon> ovládacího prvku.  
  
## <a name="notifyicons-options"></a>Možnosti NotifyIcons  
 Můžete přidružit tipech, místní nabídky a popisy tlačítek s <xref:System.Windows.Forms.NotifyIcon> pomůže uživatele.  
  
 Můžete zobrazit tipy pro <xref:System.Windows.Forms.NotifyIcon> voláním <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> metoda zadat časový interval, které chcete bublinách tip pro zobrazení. Můžete také zadat text, ikona a název tipu bublinách s <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> a <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, v uvedeném pořadí. <xref:System.Windows.Forms.NotifyIcon> součásti může mít také přidružené popisy tlačítek a místní nabídky. Další informace najdete v tématu [ToolTip – přehled komponenty](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md) a [ContextMenu – přehled komponenty](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.NotifyIcon>  
 [Komponenta NotifyIcon](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)
