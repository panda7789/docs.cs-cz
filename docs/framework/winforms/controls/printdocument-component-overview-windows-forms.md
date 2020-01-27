---
title: Přehled komponenty PrintDocument
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: a82cc0cdcb8cfae796c9c6bf60ab73873f85a291
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728540"
---
# <a name="printdocument-component-overview-windows-forms"></a>PrintDocument – přehled komponenty (Windows Forms)

Komponenta model Windows Forms [PrintDocument](printdocument-component-windows-forms.md) slouží k nastavení vlastností, které popisují, co tisknout a možnost tisku dokumentu v aplikacích určených pro systém Windows. Dá se použít společně s komponentou [PrintDialog](printdialog-component-windows-forms.md) k tomu, aby měla kontrolu nad všemi aspekty tisku dokumentu.

## <a name="working-with-the-printdocument-component"></a>Práce s komponentou PrintDocument

Existují dva z hlavních scénářů, které zahrnují komponentu <xref:System.Drawing.Printing.PrintDocument>:

- Jednoduché tiskové úlohy, jako je například tisk jednotlivého textového souboru. V takovém případě přidejte komponentu <xref:System.Drawing.Printing.PrintDocument> do formuláře Windows a pak přidejte programovací logiku, která vytiskne soubor v obslužné rutině události <xref:System.Drawing.Printing.PrintDocument.PrintPage>. Programovací logika by měla být ukončená metodou <xref:System.Drawing.Printing.PrintDocument.Print%2A> pro tisk dokumentu. Tato metoda odesílá objekt <xref:System.Drawing.Graphics>, který je obsažen ve vlastnosti <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> třídy <xref:System.Drawing.Printing.PrintPageEventArgs>, do tiskárny. Příklad, který ukazuje, jak vytisknout textový dokument pomocí <xref:System.Drawing.Printing.PrintDocument> komponenty, naleznete [v tématu How to: Print a multi-Page textový soubor in model Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).

- Složitější tiskové úlohy, jako je situace, kdy budete chtít znovu použít logiku tisku, kterou jste napsali. V takovém případě byste měli odvodit novou komponentu z <xref:System.Drawing.Printing.PrintDocument> komponenty a přepsat (viz [přepsání](../../../visual-basic/language-reference/modifiers/overrides.md) pro Visual Basic nebo [přepsání](../../../csharp/language-reference/keywords/override.md) pro C#) události <xref:System.Drawing.Printing.PrintDocument.PrintPage>.

Při přidání do formuláře se komponenta <xref:System.Drawing.Printing.PrintDocument> zobrazí v zásobníku v dolní části Návrhář formulářů v aplikaci Visual Studio.

## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [Podpora tisku v modelu Windows Forms](../advanced/windows-forms-print-support.md)
- [Komponenta PrintDocument](printdocument-component-windows-forms.md)
