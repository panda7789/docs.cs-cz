---
title: Přehled ovládacího prvku Panel (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Panel
helpviewer_keywords:
- grouping controls [Windows Forms], Panel control
- Panel control [Windows Forms], about Panel control
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
ms.openlocfilehash: c346a9b77d49cde007310a2beb13bed3b1f30d71
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501762"
---
# <a name="panel-control-overview-windows-forms"></a>Přehled ovládacího prvku Panel (Windows Forms)
Windows Forms <xref:System.Windows.Forms.Panel> ovládací prvky se používají k zajištění identifikovatelné seskupení pro ostatní ovládací prvky. Obvykle použijete panelů rozdělení formuláře funkcí. Například může mít formulář objednávky, který určuje poštovní možnosti, jako je například které jednodenní dopravce používat. Všechny možnosti v panelu seskupení umožňuje uživateli logické vizuální upozornění. Při návrhu čas, všechny ovládací prvky lze snadno přesunout – při přesunu <xref:System.Windows.Forms.Panel> řídit, všechny její obsažené ovládací prvky příliš přesunout. Ovládací prvky v panelu lze přistupovat prostřednictvím její <xref:System.Windows.Forms.Control.Controls%2A> vlastnost. Tato vlastnost vrátí kolekci <xref:System.Windows.Forms.Control> instance, tak budete obvykle muset ovládací přetypovat načíst tento způsob, jak jeho určitého typu.  
  
## <a name="panel-versus-groupbox"></a>Panel Versus GroupBox  
 <xref:System.Windows.Forms.Panel> Ovládací prvek je podobný <xref:System.Windows.Forms.GroupBox> řízení; však pouze <xref:System.Windows.Forms.Panel> ovládací prvek může mít posuvníky a jenom <xref:System.Windows.Forms.GroupBox> ovládací prvek zobrazí popisek.  
  
## <a name="key-properties"></a>Vlastnosti klíče  
 Chcete-li zobrazit posuvníky, nastavte <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> vlastnost `true`. Můžete také přizpůsobit vzhled panelu tak, že nastavíte <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, a <xref:System.Windows.Forms.Panel.BorderStyle%2A> vlastnosti. Další informace o <xref:System.Windows.Forms.Control.BackColor%2A> a <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnosti, viz [jak: Nastavení pozadí panelu](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md). <xref:System.Windows.Forms.Panel.BorderStyle%2A> Určuje vlastnost, pokud je popsaný na panelu s žádné viditelné ohraničení (<xref:System.Windows.Forms.BorderStyle.None>), jednoduchou čáru (<xref:System.Windows.Forms.BorderStyle.FixedSingle>), nebo Stínovaný řádku (<xref:System.Windows.Forms.BorderStyle.Fixed3D>).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.Panel>
- [Ovládací prvek GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)
- [Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí návrháře](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)
- [Postupy: Nastavení pozadí panelu Windows Forms pomocí návrháře](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)
