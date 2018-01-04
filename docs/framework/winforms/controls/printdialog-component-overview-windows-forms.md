---
title: "PrintDialog – přehled komponenty (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b90d94165de6985b43d47809ae57bfcae204f0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="printdialog-component-overview-windows-forms"></a>PrintDialog – přehled komponenty (Windows Forms)
Windows Forms [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) součást je předem nakonfigurovaný dialogové okno umožňuje vybrat tiskárnu, zvolte stránky tisknout a určit další nastavení související s tiskem v aplikacích založených na systému Windows. Použijte jako jednoduchým řešením pro tiskárny a výběr nastavení související s tiskem místo dialogové okno Vlastní konfigurace. Můžete povolit uživatelům tisknout mnoho částí své dokumenty: všechny vytisknout, vytisknout rozsah zvolené stránky nebo Tisk výběru. Podle standardní dialogová okna Windows, můžete vytvořit aplikace, jehož základní funkce je dobře obeznámeni uživatele. <xref:System.Windows.Forms.PrintDialog> Komponenta dědí z <xref:System.Windows.Forms.CommonDialog> třídy.  
  
## <a name="working-with-the-component"></a>Práce s komponentou  
 Použití <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogu za běhu. Tato součást obsahuje vlastnosti, které se vztahují k buď jednu tiskovou úlohu (<xref:System.Drawing.Printing.PrintDocument> třída) nebo nastavení jednotlivých tiskáren (<xref:System.Drawing.Printing.PrinterSettings> třídy). Jedna z těchto, pak může sdílet více tiskáren.  
  
 Při jejím přidání do formuláře <xref:System.Windows.Forms.PrintDialog> součást se zobrazí na hlavním panelu v dolní části Návrhář formulářů Windows.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.PrintDialog>  
 [Komponenta PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)
