---
title: Kódování a globalizace Windows Forms
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
ms.openlocfilehash: f8e56642b6325454d2d55cd3a3d3a83d201c2eb5
ms.sourcegitcommit: 5e05f983e63d5bbd8c0b246d02c6e4f23d2fc1db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2019
ms.locfileid: "67151995"
---
# <a name="encoding-and-windows-forms-globalization"></a>Kódování a globalizace Windows Forms
Aplikace Windows Forms jsou výhradně kódování Unicode, což znamená, že každý znak je reprezentována jedinečné číslo, bez ohledu na to, jaké platformy, program nebo jazyk. Další informace o kódování Unicode naleznete v tématu [Unicode consortium webu](https://www.unicode.org).  
  
## <a name="benefits-of-unicode"></a>Výhody sady Unicode  
 Mezi výhody formuláře s podporou kódování Unicode patří možnost spolupracovat se skripty, které jsou výhradně kódování Unicode, jako je například hindština. Kromě toho můžete použít více jazyků na jeden formulář. V kódování Unicode jsou všechny znaky dva bajty, takže žádná zvláštní úsilí je potřeba k reprezentaci dvoubajtové znaky. Můžete také napsat jednu sadu kód, který bude fungovat na všech platformách. Jedná se o změnu z předchozích verzí jazyka Visual Basic, ve kterém jste museli psát jiný kód pro různé platformy, jako je například Windows NT a [!INCLUDE[win98](../../../../includes/win98-md.md)].  
  
 Nicméně některé ovládací prvky nepodporují kódování Unicode v [!INCLUDE[win98](../../../../includes/win98-md.md)] a Windows Millennium Edition. Tyto ovládací prvky, které dědí z běžný ovládací prvek, bude zpracování dat pomocí znakové stránky Windows, jako ANSI. Tyto ovládací prvky jsou: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar>, a <xref:System.Windows.Forms.StatusBar>. V důsledku toho nelze zobrazit data v kódování Unicode v těchto ovládacích prvků na uvedené platformy. Japonské znaky nelze zobrazit například v anglické [!INCLUDE[win98](../../../../includes/win98-md.md)] operačního systému.  
  
 S ohledem na Unicode alternativy k <xref:System.Windows.Forms.ToolBar> a <xref:System.Windows.Forms.StatusBar> ovládací prvky, používají <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.StatusStrip> ovládací prvky, které nahradí tyto starší ovládací prvky. Chcete-li udržovat podobá vzhledu a chování mezi vizuální prvky v aplikaci, použijte <xref:System.Windows.Forms.MenuStrip> ovládací prvek pro vykreslování nabídky místo <xref:System.Windows.Forms.MainMenu>. Stejně jako <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip> může také zpracovávat a zobrazovat znaků Unicode.  
  
## <a name="see-also"></a>Viz také:

- [Globalizace aplikací Windows Forms](globalizing-windows-forms.md)
