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
ms.openlocfilehash: 430d869265b9add34c6de617a178aa27af6218f3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707622"
---
# <a name="notifyicon-component-overview-windows-forms"></a>NotifyIcon – přehled komponenty (Windows Forms)

Windows Forms <xref:System.Windows.Forms.NotifyIcon> komponenty se obvykle používá k zobrazení ikon pro procesy, které běží na pozadí a nezobrazovat uživateli rozhraní většinu času. Příkladem může být program antivirové ochrany, který je přístupný kliknutím na ikonu v oznamovací oblasti na hlavním panelu Stav.

## <a name="key-properties-of-notifyicons"></a>Klíčové vlastnosti NotifyIcons

Každý <xref:System.Windows.Forms.NotifyIcon> komponenty zobrazí jedna ikona v oblasti stavu. Pokud budete mít tři procesy na pozadí a chcete zobrazit ikonu pro každou, je třeba přidat tři <xref:System.Windows.Forms.NotifyIcon> komponenty do formuláře. Klíčové vlastnosti <xref:System.Windows.Forms.NotifyIcon> komponenty jsou <xref:System.Windows.Forms.NotifyIcon.Icon%2A> a <xref:System.Windows.Forms.NotifyIcon.Visible%2A>. <xref:System.Windows.Forms.NotifyIcon.Icon%2A> Vlastnost nastaví na ikonu, která se zobrazí v oblasti stavu. Aby se na ikonu se zobrazí <xref:System.Windows.Forms.NotifyIcon.Visible%2A> musí být vlastnost nastavena na `true`.

## <a name="notifyicons-options"></a>Možnosti NotifyIcons

Můžete přidružit tipy, místní nabídky a popisy tlačítek s <xref:System.Windows.Forms.NotifyIcon> pomáhat uživatele.

Můžete zobrazit tipy pro <xref:System.Windows.Forms.NotifyIcon> voláním <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> metoda určující časový interval, které chcete zobrazení tipu v bublině zobrazíte. Můžete také zadat text, ikona a záhlaví zobrazení tipu v bublině s <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> a <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>v uvedeném pořadí. <xref:System.Windows.Forms.NotifyIcon> součásti můžete mít také související popisy tlačítek a místní nabídky. Další informace najdete v tématu [ToolTip – přehled komponenty](tooltip-component-overview-windows-forms.md) a [ContextMenu – přehled komponenty](contextmenu-component-overview-windows-forms.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.NotifyIcon>
- [Komponenta NotifyIcon](notifyicon-component-windows-forms.md)