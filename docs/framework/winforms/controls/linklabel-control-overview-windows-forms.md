---
title: Přehled ovládacího prvku LinkLabel
ms.date: 03/30/2017
f1_keywords:
- LinkLabel
helpviewer_keywords:
- links [Windows Forms], LinkLabel control
- Label control [Windows Forms], about Label control
- LinkLabel control [Windows Forms], about LinkLabel control
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
ms.openlocfilehash: 9837902bf56a402d623adbcf41558dcc568b7105
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745223"
---
# <a name="linklabel-control-overview-windows-forms"></a>LinkLabel – přehled ovládacího prvku (Windows Forms)
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.LinkLabel> umožňuje přidat odkazy na webový styl do aplikací model Windows Forms. Ovládací prvek <xref:System.Windows.Forms.LinkLabel> lze použít pro vše, co lze použít pro možnost <xref:System.Windows.Forms.Label> ovládací prvek pro. Můžete také nastavit část textu jako odkaz na soubor, složku nebo webovou stránku.  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a>Co se dá dělat s ovládacím prvkem LinkLabel  
 Kromě všech vlastností, metod a událostí ovládacího prvku <xref:System.Windows.Forms.Label> má ovládací prvek <xref:System.Windows.Forms.LinkLabel> vlastnosti pro hypertextové odkazy a barvy odkazů. Vlastnost <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> nastaví oblast textu, který aktivuje odkaz. Vlastnosti <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>a <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> nastaví barvy odkazu. Událost <xref:System.Windows.Forms.LinkLabel.LinkClicked> určuje, co se stane, když je vybrán text odkazu.  
  
 Nejjednodušší způsob použití ovládacího prvku <xref:System.Windows.Forms.LinkLabel> je zobrazit jediný odkaz pomocí vlastnosti <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, ale můžete také zobrazit více hypertextových odkazů pomocí vlastnosti <xref:System.Windows.Forms.LinkLabel.Links%2A>. Vlastnost <xref:System.Windows.Forms.LinkLabel.Links%2A> umožňuje přístup ke kolekci odkazů. Můžete také zadat data ve vlastnosti <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> každého objektu <xref:System.Windows.Forms.LinkLabel.Link>. Hodnotu vlastnosti <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> lze použít k uložení umístění souboru, který se má zobrazit, nebo adresy webu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.LinkLabel>
- [Přehled ovládacího prvku Label](label-control-overview-windows-forms.md)
- [Postupy: Odkázání na objekt nebo webovou stránku pomocí ovládacího prvku Windows Forms LinkLabel](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [Postupy: Změna vzhledu ovládacího prvku Windows Forms LinkLabel](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
