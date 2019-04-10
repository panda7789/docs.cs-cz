---
title: RichTextBox – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- RichTextBox
helpviewer_keywords:
- RichTextBox control [Windows Forms], about RichTextBox control
- text boxes [Windows Forms], about text boxes
ms.assetid: 95081194-3dd4-4b84-9545-dd373e491eca
ms.openlocfilehash: 0827c1919597e9eb85bfa41721676008b76564d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201595"
---
# <a name="richtextbox-control-overview-windows-forms"></a>RichTextBox – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.RichTextBox> ovládací prvek se používá pro zobrazení, zadávání a manipulace s formátování textu. <xref:System.Windows.Forms.RichTextBox> Ovládací prvek provádí všechno, co <xref:System.Windows.Forms.TextBox> ovládací prvek provádí, ale můžete také zobrazit písma, barvy a odkazy; načítání textu a vložené obrázky ze souboru a najít zadané znaky. <xref:System.Windows.Forms.RichTextBox> Ovládací prvek se obvykle používá k poskytování manipulaci s textem a zobrazení funkce podobné aplikace zpracování textu, jako je Microsoft Word. Podobně jako <xref:System.Windows.Forms.TextBox> ovládací prvek, <xref:System.Windows.Forms.RichTextBox> ovládací prvek mohl zobrazit posuvník; ale na rozdíl od <xref:System.Windows.Forms.TextBox> ovládací prvek, jeho výchozí nastavení je pro zobrazení vodorovný a svislý posuvník podle potřeby a má nastavení další posuvník.  
  
## <a name="working-with-the-richtextbox-control"></a>Práce s ovládacím prvku RichTextBox  
 Stejně jako u <xref:System.Windows.Forms.TextBox> ovládacího prvku, text, zobrazený se nastavil <xref:System.Windows.Forms.RichTextBox.Text%2A> vlastnost. <xref:System.Windows.Forms.RichTextBox> Ovládací prvek má mnoho vlastností k formátování textu. Podrobnosti o těchto vlastnostech najdete v tématu [jak: Nastavení atributů písma pro Windows Forms RichTextBox – ovládací prvek](how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md) a [jak: Nastavení odsazení, předsazení a odstavců s odrážkami pomocí ovládacího prvku Windows Forms RichTextBox](set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md). K práci se soubory, <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> a <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> metody můžete zobrazit a zapisovat více formátů souborů, včetně prostý text, Unicode ve formátu prostého textu a Rich Text Format (RTF). Formáty souborů jsou uvedeny v <xref:System.Windows.Forms.RichTextBoxStreamType>. Můžete použít <xref:System.Windows.Forms.RichTextBox.Find%2A> metody k vyhledání řetězce textu nebo určitých znaků.  
  
 Můžete také použít <xref:System.Windows.Forms.RichTextBox> ovládací prvek pro webových odkazů tak, že nastavíte <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> vlastnost `true` a psaní kódu pro zpracování <xref:System.Windows.Forms.RichTextBox.LinkClicked> událostí. Další informace najdete v tématu [jak: Zobrazení webových odkazů pomocí Windows Forms RichTextBox – ovládací prvek](how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md). Uživatel můžete zabránit manipulaci s některé nebo všechny textu v ovládacím prvku tak, že nastavíte <xref:System.Windows.Forms.RichTextBox.SelectionProtected%2A> vlastnost `true`.  
  
 Lze vrátit zpět a znovu většinu operací úpravy v <xref:System.Windows.Forms.RichTextBox> ovládacího prvku pomocí volání <xref:System.Windows.Forms.TextBoxBase.Undo%2A> a <xref:System.Windows.Forms.RichTextBox.Redo%2A> metody. <xref:System.Windows.Forms.RichTextBox.CanRedo%2A> Metoda vám umožní určit, jestli můžete znovu použít poslední operace zrušila uživatele do ovládacího prvku.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.RichTextBox>
- [Ovládací prvek RichTextBox](richtextbox-control-windows-forms.md)
- [Přehled ovládacího prvku TextBox](textbox-control-overview-windows-forms.md)
