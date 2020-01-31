---
title: Přehled ovládacího prvku RichTextBox
ms.date: 03/30/2017
f1_keywords:
- RichTextBox
helpviewer_keywords:
- RichTextBox control [Windows Forms], about RichTextBox control
- text boxes [Windows Forms], about text boxes
ms.assetid: 95081194-3dd4-4b84-9545-dd373e491eca
ms.openlocfilehash: 0d40967d97622b23e9dcb07e861f190327e6baba
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742406"
---
# <a name="richtextbox-control-overview-windows-forms"></a>RichTextBox – přehled ovládacího prvku (Windows Forms)
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.RichTextBox> slouží k zobrazení, zadání a manipulaci s textem s formátováním. Ovládací prvek <xref:System.Windows.Forms.RichTextBox> provádí všechno <xref:System.Windows.Forms.TextBox> řízení, ale může také zobrazovat písma, barvy a odkazy; načtení textu a vložených obrázků ze souboru; a vyhledá zadané znaky. Ovládací prvek <xref:System.Windows.Forms.RichTextBox> se obvykle používá k poskytování funkcí pro manipulaci s textem a zobrazení podobných aplikacím pro zpracování textu, jako je například Microsoft Word. Podobně jako u ovládacího prvku <xref:System.Windows.Forms.TextBox> může ovládací prvek <xref:System.Windows.Forms.RichTextBox> Zobrazit posuvníky. ale na rozdíl od ovládacího prvku <xref:System.Windows.Forms.TextBox> má jeho výchozí nastavení zobrazovat jak vodorovný, tak svislý posuvník, jak je potřeba, a má další nastavení posuvníku.  
  
## <a name="working-with-the-richtextbox-control"></a>Práce s ovládacím prvkem RichTextBox  
 Stejně jako u ovládacího prvku <xref:System.Windows.Forms.TextBox> je zobrazený text nastaven vlastností <xref:System.Windows.Forms.RichTextBox.Text%2A>. Ovládací prvek <xref:System.Windows.Forms.RichTextBox> má mnoho vlastností pro formátování textu. Podrobnosti o těchto vlastnostech naleznete v tématu [How to: set Font Attributes model Windows Forms Control RichTextBox](how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md) a [How to: set odsazení, předsazení a odrážkové odstavce s ovládacím prvkem model Windows Forms RichTextBox](set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md). Aby bylo možné manipulovat se soubory, metody <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> a <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> mohou zobrazovat a zapisovat více formátů souborů, včetně prostého textu, prostého textu v kódování Unicode a formátu RTF (Rich Text Format). Možné formáty souborů jsou uvedeny v <xref:System.Windows.Forms.RichTextBoxStreamType>. Pomocí metody <xref:System.Windows.Forms.RichTextBox.Find%2A> můžete najít řetězce textu nebo konkrétní znaky.  
  
 Můžete také použít ovládací prvek <xref:System.Windows.Forms.RichTextBox> pro odkazy na webový styl nastavením vlastnosti <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> na `true` a psaním kódu pro zpracování události <xref:System.Windows.Forms.RichTextBox.LinkClicked>. Další informace naleznete v tématu [How to: Display Web-Style Links with model Windows Forms RichTextBox Control](how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md). Můžete zabránit uživateli v manipulaci s některým nebo všemi texty v ovládacím prvku nastavením vlastnosti <xref:System.Windows.Forms.RichTextBox.SelectionProtected%2A> na `true`.  
  
 Většinu operací úprav v ovládacím prvku <xref:System.Windows.Forms.RichTextBox> můžete vrátit zpět a znovu zavoláním metod <xref:System.Windows.Forms.TextBoxBase.Undo%2A> a <xref:System.Windows.Forms.RichTextBox.Redo%2A>. Metoda <xref:System.Windows.Forms.RichTextBox.CanRedo%2A> umožňuje určit, zda poslední operace, kterou byl uživatel vrácen zpět, lze znovu použít u ovládacího prvku.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.RichTextBox>
- [Ovládací prvek RichTextBox](richtextbox-control-windows-forms.md)
- [Přehled ovládacího prvku TextBox](textbox-control-overview-windows-forms.md)
