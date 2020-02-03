---
title: Přehled komponenty SaveFileDialog
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: 7609c29b7e932ecee7dc8a289617094bd8d480e2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743096"
---
# <a name="savefiledialog-component-overview-windows-forms"></a>SaveFileDialog – přehled komponenty (Windows Forms)

Součást model Windows Forms <xref:System.Windows.Forms.SaveFileDialog> je předem nakonfigurovaným dialogovým oknem. Je stejný jako dialogové okno standardní **Uložit soubor** používaný v systému Windows. Dědí z třídy <xref:System.Windows.Forms.CommonDialog>.

## <a name="working-with-the-savefiledialog-component"></a>Práce s komponentou SaveFileDialog

Použijte ji jako jednoduché řešení, které umožňuje uživatelům ukládat soubory místo konfigurace vlastního dialogového okna. Když se spoléháte na standardní dialogová okna systému Windows, jsou základní funkce aplikací, které vytvoříte, okamžitě známé uživatelům. Mějte ale na paměti, že při použití komponenty <xref:System.Windows.Forms.SaveFileDialog> musíte napsat vlastní logiku pro ukládání souborů.

Můžete použít metodu <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> k zobrazení dialogového okna v době běhu. Pomocí metody <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> můžete otevřít soubor v režimu pro čtení i zápis.

Při přidání do formuláře se komponenta <xref:System.Windows.Forms.SaveFileDialog> zobrazí v zásobníku v dolní části Návrhář formulářů v aplikaci Visual Studio.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.SaveFileDialog>
- [Komponenta SaveFileDialog](savefiledialog-component-windows-forms.md)
