---
title: PageSetupDialog – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
ms.openlocfilehash: 702e9a40652e00cc2f93dd52af29a61a50c90ae0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715799"
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a>PageSetupDialog – přehled komponenty (Windows Forms)
Windows Forms <xref:System.Windows.Forms.PageSetupDialog> komponenta je předem nakonfigurované dialogové okno používá k nastavení stránky podrobností pro tisk v aplikacích založených na Windows. Použití v rámci aplikace založené na Windows jako jednoduché řešení pro uživatele nastavit předvolby stránky namísto dialogové okno Vlastní konfigurace. Můžete povolit uživatelům nastavit okraj a okraj úpravy, záhlaví a zápatí a orientaci na výšku nebo na šířku. Pomocí standardní dialogová okna Windows, můžete vytvořit aplikace, jejichž základní funkce je okamžitě uživatelé znají.  
  
## <a name="key-properties-and-methods"></a>Klíčové vlastnosti a metody  
 Použití <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogového okna v době běhu. Tato součást oznámila vlastnosti můžete nastavit, které se týkají buď jednu stránku (<xref:System.Drawing.Printing.PrintDocument> třídy) nebo jakýkoliv dokument (<xref:System.Drawing.Printing.PageSettings> třídy). Kromě toho <xref:System.Windows.Forms.PageSetupDialog> součást je možné určit konkrétní nastavení tiskárny, které jsou uloženy v <xref:System.Drawing.Printing.PrinterSettings> třídy.  
  
 Když se přidá do formuláře, <xref:System.Windows.Forms.PageSetupDialog> součást se zobrazí v hlavním panelu v dolní části Návrháře formulářů Windows.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.PageSetupDialog>
- [Komponenta PageSetupDialog](pagesetupdialog-component-windows-forms.md)
