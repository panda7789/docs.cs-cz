---
title: Přehled ovládacího prvku Panel (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Panel
helpviewer_keywords:
- grouping controls [Windows Forms], Panel control
- Panel control [Windows Forms], about Panel control
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
ms.openlocfilehash: 1ba766629f923b091459531ce74d28dca4b4ea0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539339"
---
# <a name="panel-control-overview-windows-forms"></a>Přehled ovládacího prvku Panel (Windows Forms)
Windows Forms <xref:System.Windows.Forms.Panel> ovládací prvky používané k zajištění osobní seskupení pro další ovládací prvky. Obvykle použijete panelů dále dělit formuláře podle funkce. Například můžete mít formulář objednávky, který určuje poštovní možnosti, například které přes noc poskytovatel používat. Všechny možnosti panelu seskupení umožňuje uživateli logické vizuální upozornění. V návrhu čas všechny ovládací prvky lze snadno přesunout – když přesunete <xref:System.Windows.Forms.Panel> řídit, všechny její obsažené ovládací prvky příliš přesunout. Ovládací prvky jsou seskupené v panelu je přístupná přes jeho <xref:System.Windows.Forms.Control.Controls%2A> vlastnost. Tato vlastnost vrátí kolekci <xref:System.Windows.Forms.Control> instance, takže obvykle bude potřeba převést ovládacího prvku načíst tento způsob, jak jeho konkrétního typu.  
  
## <a name="panel-versus-groupbox"></a>Panel Versus GroupBox  
 <xref:System.Windows.Forms.Panel> Ovládací prvek je podobný <xref:System.Windows.Forms.GroupBox> řízení; však pouze <xref:System.Windows.Forms.Panel> ovládací prvek může mít posuvníky a jenom <xref:System.Windows.Forms.GroupBox> zobrazí popisek.  
  
## <a name="key-properties"></a>Klíčové vlastnosti  
 Chcete-li zobrazit posuvníky, nastavte <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> vlastnost `true`. Můžete také přizpůsobit vzhled panelu nastavení <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, a <xref:System.Windows.Forms.Panel.BorderStyle%2A> vlastnosti. Další informace o <xref:System.Windows.Forms.Control.BackColor%2A> a <xref:System.Windows.Forms.Control.BackgroundImage%2A> najdete v části vlastnosti, [postupy: nastavení pozadí panelu](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md). <xref:System.Windows.Forms.Panel.BorderStyle%2A> Vlastnost určuje, pokud je panel uvedených bez viditelné okraje (<xref:System.Windows.Forms.BorderStyle.None>), prostý řádku (<xref:System.Windows.Forms.BorderStyle.FixedSingle>), nebo stíněné řádku (<xref:System.Windows.Forms.BorderStyle.Fixed3D>).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Panel>  
 [Ovládací prvek GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)  
 [Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí Návrháře](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)  
 [Postupy: Nastavení pozadí panelu Windows Forms pomocí Návrháře](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)
