---
title: LinkLabel – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- LinkLabel
helpviewer_keywords:
- links [Windows Forms], LinkLabel control
- Label control [Windows Forms], about Label control
- LinkLabel control [Windows Forms], about LinkLabel control
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
ms.openlocfilehash: 40326a9055ff51efae5f4c64744d0966870c6f6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535009"
---
# <a name="linklabel-control-overview-windows-forms"></a>LinkLabel – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.LinkLabel> řízení umožňuje přidat webových odkazů do formulářové aplikace Windows. Můžete použít <xref:System.Windows.Forms.LinkLabel> řízení pro všechno, který můžete použít <xref:System.Windows.Forms.Label> řízení pro; můžete také nastavit část textu jako odkaz na soubor, složku nebo webové stránky.  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a>Co můžete dělat s linklabel – ovládací prvek  
 Kromě všech vlastností, metod a události <xref:System.Windows.Forms.Label> ovládací prvek, <xref:System.Windows.Forms.LinkLabel> ovládací prvek má vlastnosti hypertextových odkazů a barvy propojení. <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Vlastnost nastaví oblasti text, který aktivuje odkaz. <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, A <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> vlastnosti nastavit barvy propojení. <xref:System.Windows.Forms.LinkLabel.LinkClicked> Událostí určuje, co se stane, když je vybraný text odkazu.  
  
 Nejjednodušší použití <xref:System.Windows.Forms.LinkLabel> ovládací prvek, je zobrazit odkaz pomocí <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> vlastnost, ale můžete také zobrazit více hypertextových odkazů pomocí <xref:System.Windows.Forms.LinkLabel.Links%2A> vlastnost. <xref:System.Windows.Forms.LinkLabel.Links%2A> Vlastnost umožňuje přístup ke kolekci odkazů. Můžete také zadat data <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> vlastnosti každého uživatele <xref:System.Windows.Forms.LinkLabel.Link> objektu. Hodnota <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> vlastnost lze použít k uložení umístění souboru k zobrazení nebo adresu webu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.LinkLabel>  
 [Přehled ovládacího prvku Label](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [Postupy: Odkázání na objekt nebo webovou stránku pomocí ovládacího prvku Windows Forms LinkLabel](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)  
 [Postupy: Změna vzhledu ovládacího prvku Windows Forms LinkLabel](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
