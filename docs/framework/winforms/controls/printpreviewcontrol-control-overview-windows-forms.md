---
title: PrintPreviewControl – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
ms.openlocfilehash: acf21365d2694cdc1bf2213187fb2ae047205c4c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54665370"
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a>PrintPreviewControl – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> slouží k zobrazení [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) jak bude vypadat po vytištění. Tento ovládací prvek nemá žádné tlačítka nebo další prvky uživatelského rozhraní, proto obvykle použijete <xref:System.Windows.Forms.PrintPreviewControl> pouze v případě, že chcete napsat vlastní náhled tisku uživatelské rozhraní. Pokud chcete, aby se standardní uživatelské rozhraní, použijte <xref:System.Windows.Forms.PrintPreviewDialog> ovládací prvek; viz [printpreviewdialog – Přehled ovládacího prvku](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md) Přehled.  
  
## <a name="key-properties"></a>Vlastnosti klíče  
 Klíčová vlastnost ovládacího prvku je <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, který nastaví dokumentu, který má být zobrazen. Dokument musí být <xref:System.Drawing.Printing.PrintDocument> objektu. Přehled vytváření dokumentů pro tisk, naleznete v tématu [PrintDocument – přehled komponenty](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md) a [podpora Windows Forms tisk](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md). <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> a <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> vlastnosti určují počet stránek zobrazených vodorovně a svisle na ovládacím prvku. Vyhlazení může zvýšit zobrazí hladší text, ale také může být pomalejší; zobrazení Chcete-li použít, nastavte <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> vlastnost `true`.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.PrintPreviewControl>
- [Přehled ovládacího prvku PrintPreviewDialog](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md)
- [Ovládací prvek PrintPreviewControl](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-windows-forms.md)
- [Ovládací prvky a součásti dialogového okna](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
