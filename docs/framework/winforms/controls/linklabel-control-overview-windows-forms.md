---
title: LinkLabel – přehled ovládacího prvku
ms.date: 03/30/2017
f1_keywords:
- LinkLabel
helpviewer_keywords:
- links [Windows Forms], LinkLabel control
- Label control [Windows Forms], about Label control
- LinkLabel control [Windows Forms], about LinkLabel control
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
ms.openlocfilehash: 3e8607644c858ae804e384c974b5e81c1786c6a1
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739515"
---
# <a name="linklabel-control-overview-windows-forms"></a>LinkLabel – přehled ovládacího prvku (Windows Forms)
Ovládací prvek <xref:System.Windows.Forms.LinkLabel> Windows Forms umožňuje přidávat odkazy ve stylu webu do aplikací systému Windows Forms. Ovládací <xref:System.Windows.Forms.LinkLabel> prvek můžete použít pro vše, <xref:System.Windows.Forms.Label> co můžete použít ovládací prvek; Můžete také nastavit část textu jako odkaz na soubor, složku nebo webovou stránku.  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a>Co můžete dělat s ovládacím prvkem LinkLabel  
 Kromě všech vlastností, metod a událostí <xref:System.Windows.Forms.Label> ovládacího <xref:System.Windows.Forms.LinkLabel> prvku má ovládací prvek vlastnosti pro hypertextové odkazy a barvy propojení. Vlastnost <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> nastaví oblast textu, který aktivuje odkaz. <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>Vlastnosti <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> a nastavit barvy odkazu. Událost <xref:System.Windows.Forms.LinkLabel.LinkClicked> určuje, co se stane, když je vybrán text odkazu.  
  
 Nejjednodušší použití ovládacího <xref:System.Windows.Forms.LinkLabel> prvku je zobrazení jednoho <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> odkazu pomocí vlastnosti, ale můžete <xref:System.Windows.Forms.LinkLabel.Links%2A> také zobrazit více hypertextových odkazů pomocí vlastnosti. Vlastnost <xref:System.Windows.Forms.LinkLabel.Links%2A> umožňuje přístup ke kolekci odkazů. Můžete také zadat data <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> ve vlastnosti každého jednotlivého <xref:System.Windows.Forms.LinkLabel.Link> objektu. Hodnotu vlastnosti <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> lze použít k uložení umístění souboru, který má být zobrazen, nebo adresy webu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.LinkLabel>
- [Přehled ovládacího prvku Popisek](label-control-overview-windows-forms.md)
- [Postupy: Odkázání na objekt nebo webovou stránku pomocí ovládacího prvku Windows Forms LinkLabel](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [Postupy: Změna vzhledu ovládacího prvku Windows Forms LinkLabel](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
