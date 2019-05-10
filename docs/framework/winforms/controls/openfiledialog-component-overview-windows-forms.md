---
title: OpenFileDialog – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
ms.openlocfilehash: 24327ded50ac927642e2687b40b1f10de9bdf41e
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211708"
---
# <a name="openfiledialog-component-overview-windows-forms"></a>OpenFileDialog – přehled komponenty (Windows Forms)

Windows Forms <xref:System.Windows.Forms.OpenFileDialog> komponenta je předem nakonfigurované dialogového okna. Jde o stejný **otevřít soubor** dialogové okno vystavené operačního systému Windows. Dědí z <xref:System.Windows.Forms.CommonDialog> třídy.

## <a name="use-this-component"></a>Použití této komponenty

Použití této komponenty v rámci vaší aplikace pro systém Windows jako jednoduchým řešením pro výběr souboru namísto dialogové okno Vlastní konfigurace. Pomocí standardní dialogová okna Windows, můžete vytvořit aplikace, jejichž základní funkce je okamžitě uživatelé znají. Mějte na paměti, ale, že pomocí <xref:System.Windows.Forms.OpenFileDialog> komponenty, je nutné napsat vlastní logikou otevření souboru.

Použití <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogového okna v době běhu. Můžete umožnit uživatelům si vybrat víc souborů otevíraly pomocí <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> vlastnost. Kromě toho můžete použít <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> a určí, pokud se v dialogovém okně zobrazí zaškrtávací políčko jen pro čtení. <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> Vlastnost určuje, zda je zaškrtnuto zaškrtávací políčko jen pro čtení. Nakonec <xref:System.Windows.Forms.FileDialog.Filter%2A> nastaví aktuální soubor název řetězec filtru, který určuje možnosti, které se zobrazí v poli "Soubory typu" v dialogovém okně Vlastnosti.

Když se přidá do formuláře, <xref:System.Windows.Forms.OpenFileDialog> součást se zobrazí v hlavním panelu v dolní části Návrháře formulářů Windows v sadě Visual Studio.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.OpenFileDialog>
- [Komponenta OpenFileDialog](openfiledialog-component-windows-forms.md)
