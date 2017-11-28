---
title: "Postupy: Zobrazení součásti PrintDialog"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7e1162a4e926d5be35f8f7bb7cdeb92264f293aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-the-printdialog-component"></a>Postupy: Zobrazení součásti PrintDialog
<xref:System.Windows.Forms.PrintDialog> Součást je standardní tiskové dialogové okno, mnoho uživatelů bude znát. Protože uživatelé budou okamžitě vyhovuje, je výhodné pro použití <xref:System.Windows.Forms.PrintDialog> součásti.  
  
### <a name="to-display-the-printdialog-component"></a>K zobrazení součásti PrintDialog  
  
-   Volání <xref:System.Windows.Forms.Form.ShowDialog%2A> metoda z kódu vaší aplikace.  
  
     Jakmile se zobrazí komponentu, uživatelé budou komunikovat s, nastavení vlastností tiskové úlohy. Tyto jsou uloženy ve <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting` – třída (a <xref:System.Drawing.Printing.PageSettings> třídy, pokud uživatel přistoupí k [PageSetupDialog – komponenta](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) prostřednictvím <xref:System.Windows.Forms.PrintDialog> součásti) spojené s danou tiskovou úlohu. Potom můžete provést volání do vlastností že nastavují k určení specifika tiskové úlohy.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vytvoření tiskových úloh standardní Windows Forms](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 [Postupy: zachycení uživatelského vstupu z komponenty PrintDialog za běhu](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 [Printpreviewdialog – ovládací prvek](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [PrintDialog – komponenta](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 [Podpora tisku ve Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [Ovládací prvky Windows Forms](../../../../docs/framework/winforms/controls/index.md)
