---
title: PrintDialog – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: 0b0e516364277133efc83e7324345ccea8328690
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535486"
---
# <a name="printdialog-component-overview-windows-forms"></a>PrintDialog – přehled komponenty (Windows Forms)
Windows Forms [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) součást je předem nakonfigurovaný dialogové okno umožňuje vybrat tiskárnu, zvolte stránky tisknout a určit další nastavení související s tiskem v aplikacích založených na systému Windows. Použijte jako jednoduchým řešením pro tiskárny a výběr nastavení související s tiskem místo dialogové okno Vlastní konfigurace. Můžete povolit uživatelům tisknout mnoho částí své dokumenty: všechny vytisknout, vytisknout rozsah zvolené stránky nebo Tisk výběru. Podle standardní dialogová okna Windows, můžete vytvořit aplikace, jehož základní funkce je dobře obeznámeni uživatele. <xref:System.Windows.Forms.PrintDialog> Komponenta dědí z <xref:System.Windows.Forms.CommonDialog> třídy.  
  
## <a name="working-with-the-component"></a>Práce s komponentou  
 Použití <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogu za běhu. Tato součást obsahuje vlastnosti, které se vztahují k buď jednu tiskovou úlohu (<xref:System.Drawing.Printing.PrintDocument> třída) nebo nastavení jednotlivých tiskáren (<xref:System.Drawing.Printing.PrinterSettings> třídy). Jedna z těchto, pak může sdílet více tiskáren.  
  
 Při jejím přidání do formuláře <xref:System.Windows.Forms.PrintDialog> součást se zobrazí na hlavním panelu v dolní části Návrhář formulářů Windows.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.PrintDialog>  
 [Komponenta PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)
