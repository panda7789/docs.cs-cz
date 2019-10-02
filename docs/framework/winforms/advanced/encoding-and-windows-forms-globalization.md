---
title: Kódování a model Windows Forms globalizace
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], lack of Unicode support
- DateTimePicker control [Windows Forms], lack of Unicode support
- TrackBar control [Windows Forms], lack of Unicode support
- ImageList component [Windows Forms], lack of Unicode support
- Unicode [Windows Forms]
- ToolBar control [Windows Forms], lack of Unicode support
- international applications [Windows Forms], character display
- StatusBar control [Windows Forms], lack of Unicode support
- MonthCalendar control [Windows Forms], lack of Unicode support
- international characters
- TabControl control [Windows Forms], lack of Unicode support
- Windows Forms, encoding
- TreeView control [Windows Forms], lack of Unicode support
- ProgressBar control [Windows Forms], Unicode-enabled forms
- localization [Windows Forms], character sets
- globalization [Windows Forms], character sets
ms.assetid: 22e8965d-a712-42b3-8167-3ee346bd70f9
ms.openlocfilehash: 60ca9f7ba2f716b5dab1b0276bc3cd07ddd8f65c
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736888"
---
# <a name="encoding-and-windows-forms-globalization"></a>Kódování a model Windows Forms globalizace

Model Windows Forms aplikace jsou ve formátu Unicode povoleny, což znamená, že každý znak je reprezentován jedinečným číslem bez ohledu na to, jakou platformu, program nebo jazyk. Další informace o kódování Unicode najdete na webu [Unicode Consortium](https://www.unicode.org).

## <a name="benefits-of-unicode"></a>Výhody sady Unicode

Výhody formulářů s podporou kódování Unicode zahrnují schopnost pracovat se skripty, které jsou jenom Unicode, například Hindština. Kromě toho můžete použít více jazyků v jednom formuláři. V kódování Unicode jsou všechny znaky dlouhé dva bajty, takže nemusíte nic speciálního dělat k reprezentaci dvoubajtových znaků. Můžete také napsat jednu sadu kódu, která bude fungovat na všech platformách. Jedná se o změnu z předchozích verzí Visual Basic, ve které jste museli psát jiný kód pro různé platformy, například Windows NT a Windows 98.

Některé ovládací prvky ale nepodporují kódování Unicode v edicích Windows 98 a Windows Millennium Edition. Všechny tyto ovládací prvky, které dědí z obecného ovládacího prvku, budou zpracovávat data pomocí znakových stránek Windows jako ANSI. Jsou to tyto ovládací prvky: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar> a <xref:System.Windows.Forms.StatusBar>. V důsledku toho nemůžete v těchto ovládacích prvcích na uvedených platformách zobrazit data Unicode. V anglickém operačním systému Windows 98 například nemůžete zobrazit japonské znaky.

Pro alternativy podporující kódování Unicode do ovládacích prvků <xref:System.Windows.Forms.ToolBar> a <xref:System.Windows.Forms.StatusBar> použijte ovládací prvky <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.StatusStrip>, které nahradí tyto starší ovládací prvky. Chcete-li zachovat podobný vzhled a chování mezi vizuálními prvky v aplikaci, použijte ovládací prvek <xref:System.Windows.Forms.MenuStrip> pro vykreslování nabídek místo <xref:System.Windows.Forms.MainMenu>. Stejně jako <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.MenuStrip> také může zpracovávat a zobrazovat znaky Unicode.

## <a name="see-also"></a>Další informace najdete v tématech

- [Globalizace model Windows Formsch aplikací](globalizing-windows-forms.md)
