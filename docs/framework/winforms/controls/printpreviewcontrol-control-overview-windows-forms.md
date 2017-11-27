---
title: "PrintPreviewControl – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 47bef441b01d8bdcf9a365c341005cff28c64f27
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a>PrintPreviewControl – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> se používá k zobrazení [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) jak se zobrazí při tisku. Tento ovládací prvek má žádné tlačítka nebo další prvky uživatelského rozhraní, takže obvykle použijete <xref:System.Windows.Forms.PrintPreviewControl> pouze v případě, že chcete napsat vlastní náhledu uživatelské rozhraní. Pokud chcete standardní uživatelské rozhraní, použijte <xref:System.Windows.Forms.PrintPreviewDialog> řízení; viz [printpreviewdialog – Přehled ovládacího prvku](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md) Přehled.  
  
## <a name="key-properties"></a>Klíčové vlastnosti  
 Klíčová vlastnost ovládacího prvku je <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, která nastaví dokument, který chcete zobrazit jejich náhled. Musí být dokument <xref:System.Drawing.Printing.PrintDocument> objektu. Přehled vytváření dokumentů pro tisk, najdete v části [PrintDocument – přehled komponenty](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md) a [podpora prostředí Windows Forms tiskových](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md). <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> a <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> vlastnosti určit, kolik stránek se zobrazí vodorovně a svisle na ovládací prvek. Vyhlazení může zvýšit text zobrazí hladší, ale také může být pomalejší; zobrazení Chcete-li použít, nastavte <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> vlastnost `true`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.PrintPreviewControl>  
 [Printpreviewdialog – ovládací prvek – přehled](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md)  
 [Printpreviewcontrol – ovládací prvek](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-windows-forms.md)  
 [Dialogové okno – Ovládací prvky a součásti](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
