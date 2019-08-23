---
title: PrintDocument – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: 16a7f3a34ccb280f7bf91c52e29b20edc22130b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928977"
---
# <a name="printdocument-component-overview-windows-forms"></a>PrintDocument – přehled komponenty (Windows Forms)

Komponenta model Windows Forms [PrintDocument](printdocument-component-windows-forms.md) slouží k nastavení vlastností, které popisují, co tisknout a možnost tisku dokumentu v aplikacích určených pro systém Windows. Dá se použít společně s komponentou [PrintDialog](printdialog-component-windows-forms.md) k tomu, aby měla kontrolu nad všemi aspekty tisku dokumentu.

## <a name="working-with-the-printdocument-component"></a>Práce s komponentou PrintDocument

Existují dva z hlavních scénářů, které <xref:System.Drawing.Printing.PrintDocument> zahrnují komponentu:

- Jednoduché tiskové úlohy, jako je například tisk jednotlivého textového souboru. V takovém případě <xref:System.Drawing.Printing.PrintDocument> přidejte komponentu do formuláře Windows a pak přidejte programovací logiku, která vytiskne soubor <xref:System.Drawing.Printing.PrintDocument.PrintPage> v obslužné rutině události. Programovací logika by měla být ukončená <xref:System.Drawing.Printing.PrintDocument.Print%2A> metodou pro tisk dokumentu. Tato metoda odesílá <xref:System.Drawing.Graphics> objekt, který je obsažen <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> v vlastnosti <xref:System.Drawing.Printing.PrintPageEventArgs> třídy, do tiskárny. Příklad, který ukazuje, jak vytisknout textový dokument pomocí <xref:System.Drawing.Printing.PrintDocument> komponenty, naleznete v tématu [How to: Vytiskněte textový soubor s více stránkami v](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)model Windows Forms.

- Složitější tiskové úlohy, jako je situace, kdy budete chtít znovu použít logiku tisku, kterou jste napsali. V takovém případě byste měli odvodit <xref:System.Drawing.Printing.PrintDocument> novou komponentu z komponenty a přepsat ji <xref:System.Drawing.Printing.PrintDocument.PrintPage> (viz [přepsání](../../../visual-basic/language-reference/modifiers/overrides.md) pro Visual Basic nebo [přepsání](../../../csharp/language-reference/keywords/override.md) pro C#) události.

Při přidání do formuláře <xref:System.Drawing.Printing.PrintDocument> se komponenta zobrazí v zásobníku v dolní části Návrhář formulářů v aplikaci Visual Studio.

## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [Podpora tisku v modelu Windows Forms](../advanced/windows-forms-print-support.md)
- [Komponenta PrintDocument](printdocument-component-windows-forms.md)
