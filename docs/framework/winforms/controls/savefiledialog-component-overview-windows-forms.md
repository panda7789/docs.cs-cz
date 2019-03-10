---
title: SaveFileDialog – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: 93bf0f63e18ee3a384aa062c80faa991b68a6abe
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721499"
---
# <a name="savefiledialog-component-overview-windows-forms"></a>SaveFileDialog – přehled komponenty (Windows Forms)
Windows Forms <xref:System.Windows.Forms.SaveFileDialog> komponenta je předem nakonfigurované dialogového okna. Je stejný jako standardní **uložit soubor** dialogové okno používá Windows. Dědí z <xref:System.Windows.Forms.CommonDialog> třídy.  
  
## <a name="working-with-the-savefiledialog-component"></a>Práce s SaveFileDialog – komponenta  
 Použijte jako jednoduché řešení umožňující uživatelům ukládat soubory místo dialogové okno Vlastní konfigurace. Základní funkce aplikací, které vytvoříte je pomocí standardní dialogová okna Windows, okamžitě uživatelé znají. Mějte na paměti, ale, že pomocí <xref:System.Windows.Forms.SaveFileDialog> komponenty, je nutné napsat vlastní logikou ukládání souborů.  
  
 Můžete použít <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogového okna v době běhu. Můžete otevřít soubor pomocí režimu pro čtení a zápis <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> metody.  
  
 Když se přidá do formuláře, <xref:System.Windows.Forms.SaveFileDialog> součást se zobrazí v hlavním panelu v dolní části Návrháře formulářů Windows.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.SaveFileDialog>
- [Komponenta SaveFileDialog](savefiledialog-component-windows-forms.md)
