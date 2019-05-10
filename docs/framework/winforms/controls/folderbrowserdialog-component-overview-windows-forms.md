---
title: FolderBrowserDialog – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- FolderBrowserDialog
helpviewer_keywords:
- FolderBrowserDialog component [Windows Forms], about FolderBrowserDialog
- directories [Windows Forms], enabling browsing in applications
- folders [Windows Forms], enabling browsing in applications
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
ms.openlocfilehash: cd89980ccad7e6c73094c1fb462d93cee8094959
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210397"
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a>FolderBrowserDialog – přehled komponenty (Windows Forms)

Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> komponenta je modální dialogové okno, které slouží k procházení a výběr složky. V rámci lze také vytvořit nové složky <xref:System.Windows.Forms.FolderBrowserDialog> komponenty.

> [!NOTE]
> Vyberte soubory, místo složky, použijte [OpenFileDialog](openfiledialog-component-windows-forms.md) komponenty.

<xref:System.Windows.Forms.FolderBrowserDialog> Součást se zobrazí v době běhu pomocí <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody. Nastavte <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> vlastnosti k určení složky úplně nahoře a jakýmkoliv podsložkám, které se zobrazí ve stromovém zobrazení dialogového okna. Jakmile se zobrazí dialogové okno, můžete použít <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> vlastnost k získání cesty ke složce, která byla vybrána.

Když se přidá do formuláře, <xref:System.Windows.Forms.FolderBrowserDialog> součást se zobrazí v hlavním panelu v dolní části Návrháře formulářů Windows v sadě Visual Studio.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [Postupy: Zvolte složky s komponentou Windows Forms FolderBrowserDialog](how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)
- [Komponenta FolderBrowserDialog](folderbrowserdialog-component-windows-forms.md)
