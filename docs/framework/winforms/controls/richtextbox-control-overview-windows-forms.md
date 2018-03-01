---
title: "RichTextBox – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RichTextBox
helpviewer_keywords:
- RichTextBox control [Windows Forms], about RichTextBox control
- text boxes [Windows Forms], about text boxes
ms.assetid: 95081194-3dd4-4b84-9545-dd373e491eca
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d6ed04ab478cc6c20d88ec97934f5e45528558c8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="richtextbox-control-overview-windows-forms"></a>RichTextBox – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.RichTextBox> řízení se používá k zobrazení, zadávání a manipulace s nimi formátování textu. <xref:System.Windows.Forms.RichTextBox> Ovládací prvek provádí všechno, co <xref:System.Windows.Forms.TextBox> ovládací prvek provádí, ale můžete také zobrazit písma, barvy a odkazy; zatížení text a vložené obrázky ze souboru; a najít zadané znaky. <xref:System.Windows.Forms.RichTextBox> Řízení se obvykle používá k poskytování manipulaci s textem a zobrazení funkce podobná zpracování textu aplikace, jako je například Microsoft Word. Jako <xref:System.Windows.Forms.TextBox> ovládací prvek, <xref:System.Windows.Forms.RichTextBox> ovládací prvek může zobrazovat posuvníky; ale na rozdíl od <xref:System.Windows.Forms.TextBox> řízení, jeho výchozí nastavení je pro zobrazení vodorovného a svislého posuvníky podle potřeby a má scrollbar další nastavení.  
  
## <a name="working-with-the-richtextbox-control"></a>Práce s ovládacím prvkem RichTextBox  
 Stejně jako u <xref:System.Windows.Forms.TextBox> ovládací prvek, text zobrazený nastaven <xref:System.Windows.Forms.RichTextBox.Text%2A> vlastnost. <xref:System.Windows.Forms.RichTextBox> Řízení má mnoho vlastností k formátování textu. Podrobnosti o těchto vlastnostech najdete v tématu [postupy: nastavení atributů písma pro ovládací prvek Windows Forms RichTextBox](../../../../docs/framework/winforms/controls/how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md) a [postupy: nastavení odsazení, Hanging odsazení a odstavců s odrážkami pomocí ovládacího prvku Windows Forms RichTextBox ](../../../../docs/framework/winforms/controls/set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md). K práci se soubory, <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> a <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> metody můžete zobrazit a zápis víc formáty souborů, včetně prostý text, prostý text v kódu Unicode a RTF (RICH Text Format). Formáty možné souborů jsou uvedeny v <xref:System.Windows.Forms.RichTextBoxStreamType>. Můžete použít <xref:System.Windows.Forms.RichTextBox.Find%2A> metody k vyhledání řetězců textu nebo konkrétní znaků.  
  
 Můžete také použít <xref:System.Windows.Forms.RichTextBox> řízení pro odkazy ve stylu webového nastavením <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> vlastnost `true` a psaní kódu pro zpracování <xref:System.Windows.Forms.RichTextBox.LinkClicked> událostí. Další informace najdete v tématu [postupy: zobrazení webových odkazů pomocí ovládacího prvku Windows Forms RichTextBox](../../../../docs/framework/winforms/controls/how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md). Uživatele můžete zabránit manipulaci s některé nebo všechny textu v ovládacím prvku nastavením <xref:System.Windows.Forms.RichTextBox.SelectionProtected%2A> vlastnost `true`.  
  
 Můžete vrátit zpět a vrátit většinu operací upravit v <xref:System.Windows.Forms.RichTextBox> řízení voláním <xref:System.Windows.Forms.TextBoxBase.Undo%2A> a <xref:System.Windows.Forms.RichTextBox.Redo%2A> metody. <xref:System.Windows.Forms.RichTextBox.CanRedo%2A> Metoda umožňuje určit, zda uživatel zrušila poslední operace můžete provádět znovu ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.RichTextBox>  
 [Ovládací prvek RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Přehled ovládacího prvku TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)
