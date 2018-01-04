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
ms.workload: dotnet
ms.openlocfilehash: d955febe528add4b774766a3b204f96eef5a119d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-the-printdialog-component"></a>Postupy: Zobrazení součásti PrintDialog
<xref:System.Windows.Forms.PrintDialog> Součást je standardní tiskové dialogové okno, mnoho uživatelů bude znát. Protože uživatelé budou okamžitě vyhovuje, je výhodné pro použití <xref:System.Windows.Forms.PrintDialog> součásti.  
  
### <a name="to-display-the-printdialog-component"></a>K zobrazení součásti PrintDialog  
  
-   Volání <xref:System.Windows.Forms.Form.ShowDialog%2A> metoda z kódu vaší aplikace.  
  
     Jakmile se zobrazí komponentu, uživatelé budou komunikovat s, nastavení vlastností tiskové úlohy. Tyto jsou uloženy ve <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting` – třída (a <xref:System.Drawing.Printing.PageSettings> třídy, pokud uživatel přistoupí k [PageSetupDialog – komponenta](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) prostřednictvím <xref:System.Windows.Forms.PrintDialog> součásti) spojené s danou tiskovou úlohu. Potom můžete provést volání do vlastností že nastavují k určení specifika tiskové úlohy.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vytváření standardních tiskových úloh modelu Windows Forms](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 [Postupy: Zachycení uživatelského vstupu z komponenty PrintDialog při běhu](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 [Ovládací prvek PrintPreviewDialog](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [Komponenta PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 [Podpora tisku v modelu Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [Windows Forms – ovládací prvky](../../../../docs/framework/winforms/controls/index.md)
