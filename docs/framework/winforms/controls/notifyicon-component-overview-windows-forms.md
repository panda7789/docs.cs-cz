---
title: NotifyIcon – přehled komponenty
ms.date: 03/30/2017
f1_keywords:
- NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
ms.openlocfilehash: 587bf514db853f1122ed16abc05a195985c5ce8d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742122"
---
# <a name="notifyicon-component-overview-windows-forms"></a>NotifyIcon – přehled komponenty (Windows Forms)

Komponenta model Windows Forms <xref:System.Windows.Forms.NotifyIcon> se obvykle používá k zobrazení ikon pro procesy, které běží na pozadí, a nezobrazuje uživatelské rozhraní mnohem v čase. Příkladem může být program antivirové ochrany, ke kterému se dá dostat kliknutím na ikonu v oznamovací oblasti pro stav hlavního panelu.

## <a name="key-properties-of-notifyicons"></a>Klíčové vlastnosti NotifyIcons

Každá součást <xref:System.Windows.Forms.NotifyIcon> zobrazuje jednu ikonu v oblasti stavu. Pokud máte tři procesy na pozadí a chcete pro každou z nich zobrazit ikonu, musíte do formuláře přidat tři součásti <xref:System.Windows.Forms.NotifyIcon>. Klíčové vlastnosti součásti <xref:System.Windows.Forms.NotifyIcon> jsou <xref:System.Windows.Forms.NotifyIcon.Icon%2A> a <xref:System.Windows.Forms.NotifyIcon.Visible%2A>. Vlastnost <xref:System.Windows.Forms.NotifyIcon.Icon%2A> nastaví ikonu, která se zobrazí v oblasti stavu. Aby se ikona zobrazila, musí být vlastnost <xref:System.Windows.Forms.NotifyIcon.Visible%2A> nastavena na hodnotu `true`.

## <a name="notifyicons-options"></a>NotifyIcons možnosti

Pomocí <xref:System.Windows.Forms.NotifyIcon> můžete přidružit tipy k bublinám, místní nabídky a popisy tlačítek, které budou uživateli pomáhat.

Můžete zobrazit tipy v bublinách pro <xref:System.Windows.Forms.NotifyIcon> voláním metody <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> určující časový rozsah, ve kterém chcete zobrazit tip v bublině. Můžete také zadat text, ikonu a název tipu v bublině s <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> a <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, v uvedeném pořadí. komponenty <xref:System.Windows.Forms.NotifyIcon> mohou mít také přidružené popisy a místní nabídky. Další informace najdete v tématu [Přehled komponent popisu](tooltip-component-overview-windows-forms.md) a informování [komponent](contextmenu-component-overview-windows-forms.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.NotifyIcon>
- [Komponenta NotifyIcon](notifyicon-component-windows-forms.md)
