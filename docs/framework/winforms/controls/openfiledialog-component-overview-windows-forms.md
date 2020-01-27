---
title: OpenFileDialog – přehled komponenty
ms.date: 03/30/2017
f1_keywords:
- OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
ms.openlocfilehash: c519b373150a49ee41dbb0c503f7d5a4862477d5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728433"
---
# <a name="openfiledialog-component-overview-windows-forms"></a>OpenFileDialog – přehled komponenty (Windows Forms)

Součást model Windows Forms <xref:System.Windows.Forms.OpenFileDialog> je předem nakonfigurovaným dialogovým oknem. Jedná se o stejný dialog **otevřeného souboru** , který je vystavený operačním systémem Windows. Dědí z třídy <xref:System.Windows.Forms.CommonDialog>.

## <a name="use-this-component"></a>Použít tuto součást

Tuto součást použijte v aplikaci pro Windows jako jednoduché řešení pro výběr souborů namísto konfigurace vlastního dialogového okna. Když se spoléháte na standardní dialogová okna systému Windows, vytvoříte aplikace, jejichž základní funkce je pro uživatele okamžitě známa. Mějte ale na paměti, že při použití <xref:System.Windows.Forms.OpenFileDialog> komponenty musíte napsat vlastní logiku otevírání souborů.

Použijte metodu <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> k zobrazení dialogového okna v době běhu. Uživatelům můžete umožnit otevírání souborů s více výběry s vlastností <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A>. Kromě toho můžete použít vlastnost <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> k určení, zda se v dialogovém okně zobrazí zaškrtávací políčko jen pro čtení. Vlastnost <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> určuje, zda je zaškrtnuto políčko jen pro čtení. Nakonec vlastnost <xref:System.Windows.Forms.FileDialog.Filter%2A> nastaví aktuální řetězec filtru názvu souboru, který určuje možnosti, které se zobrazí v poli "soubory typu" v dialogovém okně.

Při přidání do formuláře se komponenta <xref:System.Windows.Forms.OpenFileDialog> zobrazí v zásobníku v dolní části Návrhář formulářů v aplikaci Visual Studio.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.OpenFileDialog>
- [Komponenta OpenFileDialog](openfiledialog-component-windows-forms.md)
