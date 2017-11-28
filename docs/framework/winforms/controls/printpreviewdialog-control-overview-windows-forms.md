---
title: "PrintPreviewDialog – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PrintPreviewDialog
helpviewer_keywords: PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3c898dc24c9a4418e3af45fce507e6befcf905a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a>PrintPreviewDialog – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> řízení je předem nakonfigurovaný dialogové okno slouží k zobrazení jak [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) se zobrazí při tisku. Ji použijte v rámci aplikace systému Windows jako simple řešení namísto dialogové okno Vlastní konfigurace. Ovládací prvek obsahuje tlačítka pro tisk, přiblížení, zobrazení jednu nebo více stránek a zavření dialogového okna.  
  
## <a name="key-properties-and-methods"></a>Klíčové vlastnosti a metody  
 Klíčová vlastnost ovládacího prvku je <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, která nastaví dokument, který chcete zobrazit jejich náhled. Musí být dokument <xref:System.Drawing.Printing.PrintDocument> objektu. Aby bylo možné zobrazit dialogové okno, musí volat jeho <xref:System.Windows.Forms.Form.ShowDialog%2A> metoda. Vyhlazení může zvýšit text zobrazí hladší, ale také může být pomalejší; zobrazení Chcete-li použít, nastavte <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> vlastnost `true`.  
  
 Některé vlastnosti jsou k dispozici prostřednictvím <xref:System.Windows.Forms.PrintPreviewControl> , <xref:System.Windows.Forms.PrintPreviewDialog> obsahuje. (Není nutné přidejte tuto <xref:System.Windows.Forms.PrintPreviewControl> do formuláře; je automaticky obsažené v <xref:System.Windows.Forms.PrintPreviewDialog> dialogové okno když přidáte do svého formuláře.) Příklady vlastností, které jsou k dispozici prostřednictvím <xref:System.Windows.Forms.PrintPreviewControl> jsou <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> a <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> vlastnosti, které určuje, kolik stránek se zobrazí vodorovně a svisle na ovládací prvek. Dostanete <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> vlastnost jako `PrintPreviewDialog1.PrintPreviewControl.Columns` v [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], `printPreviewDialog1.PrintPreviewControl.Columns` v [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], nebo `printPreviewDialog1->PrintPreviewControl->Columns` v [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.PrintPreviewDialog>  
 [Printpreviewcontrol – ovládací prvek – přehled](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-overview-windows-forms.md)  
 [Printpreviewdialog – ovládací prvek](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [Dialogové okno – Ovládací prvky a součásti](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
