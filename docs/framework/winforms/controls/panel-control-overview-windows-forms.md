---
title: Přehled ovládacího prvku Panel
ms.date: 03/30/2017
f1_keywords:
- Panel
helpviewer_keywords:
- grouping controls [Windows Forms], Panel control
- Panel control [Windows Forms], about Panel control
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
ms.openlocfilehash: 3ea86e898e8a3e1ca90ba8e0a6240414702a1a73
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744314"
---
# <a name="panel-control-overview-windows-forms"></a>Přehled ovládacího prvku Panel (Windows Forms)
Ovládací prvky <xref:System.Windows.Forms.Panel> model Windows Forms slouží k poskytnutí identifikovatelného seskupení pro jiné ovládací prvky. Obvykle používáte panely k rozdělení formuláře podle funkce. Například můžete mít formulář objednávky, který určuje možnosti pro korespondenci, jako je například to, který provozovatel v noci používá. Seskupením všech možností na panelu udělíte uživateli logickou vizuální hromádku. V době návrhu lze snadno přesunout všechny ovládací prvky – při přesunutí ovládacího prvku <xref:System.Windows.Forms.Panel>, jsou také přesunuty všechny jeho obsažené ovládací prvky. Ovládací prvky seskupené na panelu lze použít prostřednictvím vlastnosti <xref:System.Windows.Forms.Control.Controls%2A>. Tato vlastnost vrací kolekci instancí <xref:System.Windows.Forms.Control>, takže obvykle budete potřebovat přetypování ovládacího prvku, který jste načetli tímto způsobem na jeho konkrétní typ.  
  
## <a name="panel-versus-groupbox"></a>Panel Versus GroupBox  
 Ovládací prvek <xref:System.Windows.Forms.Panel> je podobný ovládacímu prvku <xref:System.Windows.Forms.GroupBox>; ale pouze ovládací prvek <xref:System.Windows.Forms.Panel> může mít posuvníky a pouze ovládací prvek <xref:System.Windows.Forms.GroupBox> zobrazí titulek.  
  
## <a name="key-properties"></a>Klíčové vlastnosti  
 Chcete-li zobrazit posuvníky, nastavte vlastnost <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> na hodnotu `true`. Můžete také přizpůsobit vzhled panelu nastavením vlastností <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>a <xref:System.Windows.Forms.Panel.BorderStyle%2A>. Další informace o vlastnostech <xref:System.Windows.Forms.Control.BackColor%2A> a <xref:System.Windows.Forms.Control.BackgroundImage%2A> naleznete v tématu [How to: set a background of the panel](how-to-set-the-background-of-a-windows-forms-panel.md). Vlastnost <xref:System.Windows.Forms.Panel.BorderStyle%2A> určuje, zda je panel ohraničený bez viditelného ohraničení (<xref:System.Windows.Forms.BorderStyle.None>), jednoduché čáry (<xref:System.Windows.Forms.BorderStyle.FixedSingle>) nebo stínové čáry (<xref:System.Windows.Forms.BorderStyle.Fixed3D>).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Panel>
- [Ovládací prvek GroupBox](groupbox-control-windows-forms.md)
- [Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí Návrháře](group-controls-with-wf-panel-control-using-the-designer.md)
- [Postupy: Nastavení pozadí panelu Windows Forms pomocí Návrháře](how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)
