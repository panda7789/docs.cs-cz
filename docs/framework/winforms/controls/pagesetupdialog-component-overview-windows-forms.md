---
title: Přehled komponenty PageSetupDialog
ms.date: 03/30/2017
f1_keywords:
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
ms.openlocfilehash: a891cb8cc77007d7591d41461c94f61c077eb300
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744343"
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a>PageSetupDialog – přehled komponenty (Windows Forms)

Součást model Windows Forms <xref:System.Windows.Forms.PageSetupDialog> je předem nakonfigurovaným dialogovým oknem použitým k nastavení podrobností o tisku v aplikacích založených na systému Windows. Použijte ji v aplikaci pro Windows jako jednoduché řešení pro uživatele, aby se místo konfigurace vlastního dialogového okna nastavily předvolby stránky. Uživatelům můžete povolit nastavení úprav ohraničení a okrajů, záhlaví a zápatí a orientace na výšku nebo na šířku. Když se spoléháte na standardní dialogová okna systému Windows, vytvoříte aplikace, jejichž základní funkce je pro uživatele okamžitě známa.

## <a name="key-properties-and-methods"></a>Klíčové vlastnosti a metody

Použijte metodu <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> k zobrazení dialogového okna v době běhu. Tato součást obsahuje vlastnosti, které můžete nastavit, které se vztahují k jedné stránce (<xref:System.Drawing.Printing.PrintDocument> třídě) nebo k libovolnému dokumentu (<xref:System.Drawing.Printing.PageSettings> třídě). Kromě toho lze komponentu <xref:System.Windows.Forms.PageSetupDialog> použít k určení konkrétního nastavení tiskárny, která jsou uložena ve třídě <xref:System.Drawing.Printing.PrinterSettings>.

Při přidání do formuláře se komponenta <xref:System.Windows.Forms.PageSetupDialog> zobrazí v zásobníku v dolní části Návrhář formulářů v aplikaci Visual Studio.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.PageSetupDialog>
- [Komponenta PageSetupDialog](pagesetupdialog-component-windows-forms.md)
