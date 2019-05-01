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
ms.openlocfilehash: 541467b0f1285d372e5f6d502d9d8f28c8c6333e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012955"
---
# <a name="linklabel-control-overview-windows-forms"></a>LinkLabel – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.LinkLabel> ovládací prvek slouží k přidání webových odkazů do aplikace Windows Forms. Můžete použít <xref:System.Windows.Forms.LinkLabel> ovládací prvek pro všechno, co se vám <xref:System.Windows.Forms.Label> ovládací prvek pro; můžete také nastavit část textu jako odkaz na souboru, složky nebo webové stránky.  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a>Co můžete dělat pomocí ovládacího prvku LinkLabel  
 Kromě vlastnosti, metody a události <xref:System.Windows.Forms.Label> ovládací prvek, <xref:System.Windows.Forms.LinkLabel> ovládací prvek má vlastnosti pro hypertextové odkazy a barvy propojení. <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Oblast textu, který aktivuje odkaz nastaví vlastnost. <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, A <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> vlastnosti nastavte barvy propojení. <xref:System.Windows.Forms.LinkLabel.LinkClicked> Událostí určuje, co se stane, když je vybraný text odkazu.  
  
 Nejjednodušší použití <xref:System.Windows.Forms.LinkLabel> je ovládací prvek pro zobrazení jedno propojení pomocí <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> vlastnost, ale můžete také zobrazit více hypertextové odkazy pomocí <xref:System.Windows.Forms.LinkLabel.Links%2A> vlastnost. <xref:System.Windows.Forms.LinkLabel.Links%2A> Vlastnost umožňuje přístup ke kolekci odkazů. Můžete také zadat data <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> vlastnost jednotlivých <xref:System.Windows.Forms.LinkLabel.Link> objektu. Hodnota <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> vlastnost lze použít k uložení umístění souboru k zobrazení nebo adresu webu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.LinkLabel>
- [Přehled ovládacího prvku Label](label-control-overview-windows-forms.md)
- [Postupy: Odkaz na objekt nebo webovou stránku pomocí ovládacího prvku Windows Forms LinkLabel](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [Postupy: Změna vzhledu ovládacího prvku Windows Forms LinkLabel](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
