---
title: Přehled komponenty FolderBrowserDialog
ms.date: 03/30/2017
f1_keywords:
- FolderBrowserDialog
helpviewer_keywords:
- FolderBrowserDialog component [Windows Forms], about FolderBrowserDialog
- directories [Windows Forms], enabling browsing in applications
- folders [Windows Forms], enabling browsing in applications
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
ms.openlocfilehash: 8b017ba08ae4205e930ac00177c89a89fde17d3b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745727"
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a>FolderBrowserDialog – přehled komponenty (Windows Forms)

Součást model Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> je modální dialogové okno, které se používá pro procházení a výběr složek. Nové složky je také možné vytvořit v rámci součásti <xref:System.Windows.Forms.FolderBrowserDialog>.

> [!NOTE]
> Chcete-li vybrat soubory namísto složek, použijte komponentu [OpenFileDialog](openfiledialog-component-windows-forms.md) .

Komponenta <xref:System.Windows.Forms.FolderBrowserDialog> se zobrazuje za běhu pomocí metody <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>. Nastavte vlastnost <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A>, aby se určila složka nejvyšší úrovně a všechny podsložky, které se zobrazí ve stromovém zobrazení dialogového okna. Po zobrazení dialogového okna můžete použít vlastnost <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> a získat tak cestu vybrané složky.

Při přidání do formuláře se komponenta <xref:System.Windows.Forms.FolderBrowserDialog> zobrazí v zásobníku v dolní části Návrhář formulářů v aplikaci Visual Studio.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [Postupy: Výběr složek pomocí komponenty Windows Forms FolderBrowserDialog](how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)
- [Komponenta FolderBrowserDialog](folderbrowserdialog-component-windows-forms.md)
