---
title: SaveFileDialog – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: ab8eb5409d017c6ea73a44e4e57ccec9cece4824
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631058"
---
# <a name="savefiledialog-component-overview-windows-forms"></a>SaveFileDialog – přehled komponenty (Windows Forms)
Windows Forms <xref:System.Windows.Forms.SaveFileDialog> komponenta je předem nakonfigurované dialogového okna. Je stejný jako standardní **uložit soubor** dialogové okno používá Windows. Dědí z <xref:System.Windows.Forms.CommonDialog> třídy.  
  
## <a name="working-with-the-savefiledialog-component"></a>Práce s SaveFileDialog – komponenta  
 Použijte jako jednoduché řešení umožňující uživatelům ukládat soubory místo dialogové okno Vlastní konfigurace. Základní funkce aplikací, které vytvoříte je pomocí standardní dialogová okna Windows, okamžitě uživatelé znají. Mějte na paměti, ale, že pomocí <xref:System.Windows.Forms.SaveFileDialog> komponenty, je nutné napsat vlastní logikou ukládání souborů.  
  
 Můžete použít <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogového okna v době běhu. Můžete otevřít soubor pomocí režimu pro čtení a zápis <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> metody.  
  
 Když se přidá do formuláře, <xref:System.Windows.Forms.SaveFileDialog> součást se zobrazí v hlavním panelu v dolní části Návrháře formulářů Windows.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.SaveFileDialog>
- [Komponenta SaveFileDialog](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)
