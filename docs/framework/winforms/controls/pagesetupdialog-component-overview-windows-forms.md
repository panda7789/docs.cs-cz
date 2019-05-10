---
title: PageSetupDialog – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
ms.openlocfilehash: 989183b6152dfccb6167d89433317cea596d83c5
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211745"
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a>PageSetupDialog – přehled komponenty (Windows Forms)

Windows Forms <xref:System.Windows.Forms.PageSetupDialog> komponenta je předem nakonfigurované dialogové okno používá k nastavení stránky podrobností pro tisk v aplikacích založených na Windows. Použití v rámci aplikace založené na Windows jako jednoduché řešení pro uživatele nastavit předvolby stránky namísto dialogové okno Vlastní konfigurace. Můžete povolit uživatelům nastavit okraj a okraj úpravy, záhlaví a zápatí a orientaci na výšku nebo na šířku. Pomocí standardní dialogová okna Windows, můžete vytvořit aplikace, jejichž základní funkce je okamžitě uživatelé znají.

## <a name="key-properties-and-methods"></a>Klíčové vlastnosti a metody

Použití <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogového okna v době běhu. Tato součást oznámila vlastnosti můžete nastavit, které se týkají buď jednu stránku (<xref:System.Drawing.Printing.PrintDocument> třídy) nebo jakýkoliv dokument (<xref:System.Drawing.Printing.PageSettings> třídy). Kromě toho <xref:System.Windows.Forms.PageSetupDialog> součást je možné určit konkrétní nastavení tiskárny, které jsou uloženy v <xref:System.Drawing.Printing.PrinterSettings> třídy.

Když se přidá do formuláře, <xref:System.Windows.Forms.PageSetupDialog> součást se zobrazí v hlavním panelu v dolní části Návrháře formulářů Windows v sadě Visual Studio.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.PageSetupDialog>
- [Komponenta PageSetupDialog](pagesetupdialog-component-windows-forms.md)
