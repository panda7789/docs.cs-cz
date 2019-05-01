---
title: PrintDocument – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: a3f08aa4bd5b63769cef35dbea2209d5d83261be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012617"
---
# <a name="printdocument-component-overview-windows-forms"></a>PrintDocument – přehled komponenty (Windows Forms)
Windows Forms [PrintDocument](printdocument-component-windows-forms.md) komponenty se používá k nastavení vlastnosti, které popisují, jak vytisknout a umožňuje vytisknout dokument v rámci aplikace pro systém Windows. Je možné použít ve spojení s [PrintDialog](printdialog-component-windows-forms.md) komponenty v řízení všech aspektů tisk dokumentu.  
  
## <a name="working-with-the-printdocument-component"></a>Práce s PrintDocument – komponenta  
 Dva hlavní scénáře, které se týkají <xref:System.Drawing.Printing.PrintDocument> komponenty jsou:  
  
- Jednoduché tiskové úlohy, jako je například tisk jednotlivé textového souboru. V takovém případě přidejte <xref:System.Drawing.Printing.PrintDocument> komponentu do formuláře Windows, pak přidejte programovou logiku, která vytiskne souboru v <xref:System.Drawing.Printing.PrintDocument.PrintPage> obslužné rutiny události. By měla s přineslo programovou logiku <xref:System.Drawing.Printing.PrintDocument.Print%2A> metoda se dokument vytiskne na. Tato metoda odesílá <xref:System.Drawing.Graphics> objektů obsažených v <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> třídy tiskárny. Příklad, který ukazuje, jak vytisknout textu dokumentu pomocí <xref:System.Drawing.Printing.PrintDocument> komponenty, naleznete v tématu [jak: Tisk vícestránkového textového souboru ve Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).  
  
- Složitější tiskové úlohy, jako je situace, ve kterém můžete opakovaně použít logiku tisk, který jste napsali. V takovém případě by odvozovat nové komponenty z <xref:System.Drawing.Printing.PrintDocument> komponenty a přepsání (naleznete v tématu [přepíše](~/docs/visual-basic/language-reference/modifiers/overrides.md) v jazyce Visual Basic nebo [přepsat](~/docs/csharp/language-reference/keywords/override.md) pro C#) <xref:System.Drawing.Printing.PrintDocument.PrintPage> událostí.  
  
 Když se přidá do formuláře, <xref:System.Drawing.Printing.PrintDocument> součást se zobrazí v hlavním panelu v dolní části Návrháře formulářů Windows.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [Podpora tisku v modelu Windows Forms](../advanced/windows-forms-print-support.md)
- [Komponenta PrintDocument](printdocument-component-windows-forms.md)
