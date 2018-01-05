---
title: "PrintDocument – přehled komponenty (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 414a7972550558b40403b7f4cbfd9a49194666be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="printdocument-component-overview-windows-forms"></a>PrintDocument – přehled komponenty (Windows Forms)
Windows Forms [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) komponenta se používá k nastavení vlastnosti, které popisují, co chcete vytisknout a schopnost tisk dokumentu v rámci aplikace pro systém Windows. Může sloužit ve spojení s [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) součást, kterou je možné v ovládacím prvku všech aspektů tisk dokumentu.  
  
## <a name="working-with-the-printdocument-component"></a>Práce s komponentě PrintDocument  
 Dva hlavní scénáře, které zahrnují <xref:System.Drawing.Printing.PrintDocument> komponenty jsou:  
  
-   Jednoduché tiskové úlohy, jako je například tisk jednotlivých textového souboru. V takovém případě byste přidali <xref:System.Drawing.Printing.PrintDocument> součásti na formuláři Windows pak přidejte programovací logiky, která vytiskne soubor v <xref:System.Drawing.Printing.PrintDocument.PrintPage> obslužné rutiny události. Programovací logiku by měl případech se <xref:System.Drawing.Printing.PrintDocument.Print%2A> metoda tisk dokumentu. Tato metoda odesílá <xref:System.Drawing.Graphics> objektů, obsažených v <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> třídy tiskárny. Pro příklad, který ukazuje, jak tisk dokumentu text pomocí <xref:System.Drawing.Printing.PrintDocument> součást, najdete v části [postupy: Tisk vícestránkového textového souboru v systému Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).  
  
-   Složitější tiskové úlohy, jako je například situaci, kde můžete opakovaně použít logiku tisku, který jste napsali. V takovém případě by odvozujete novou součást z <xref:System.Drawing.Printing.PrintDocument> součásti a přepsání (najdete v části [přepsání](~/docs/visual-basic/language-reference/modifiers/overrides.md) jazyka Visual Basic nebo [přepsat](~/docs/csharp/language-reference/keywords/override.md) pro jazyk C#) <xref:System.Drawing.Printing.PrintDocument.PrintPage> událostí.  
  
 Při jejím přidání do formuláře <xref:System.Drawing.Printing.PrintDocument> součást se zobrazí na hlavním panelu v dolní části Návrhář formulářů Windows.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Graphics>  
 <xref:System.Drawing.Printing.PrintDocument>  
 [Podpora tisku v modelu Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [Komponenta PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)
