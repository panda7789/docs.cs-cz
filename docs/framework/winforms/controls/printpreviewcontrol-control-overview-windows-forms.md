---
title: Přehled ovládacího prvku PrintPreviewControl
ms.date: 03/30/2017
f1_keywords:
- PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
ms.openlocfilehash: 8dfe5802a24d5ec85ed908fd04c5550e1fbec012
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741437"
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a>PrintPreviewControl – přehled ovládacího prvku (Windows Forms)
<xref:System.Windows.Forms.PrintPreviewControl> model Windows Forms se používá k zobrazení [PrintDocument](printdocument-component-windows-forms.md) , jak se zobrazí po vytištění. Tento ovládací prvek nemá žádná tlačítka ani jiné prvky uživatelského rozhraní, takže se <xref:System.Windows.Forms.PrintPreviewControl> obvykle používá pouze v případě, že chcete napsat vlastní uživatelské rozhraní pro tisk náhledu. Pokud chcete standardní uživatelské rozhraní, použijte ovládací prvek <xref:System.Windows.Forms.PrintPreviewDialog>; Přehled najdete v tématu [Přehled ovládacího prvku PrintPreviewDialog –](printpreviewdialog-control-overview-windows-forms.md) .  
  
## <a name="key-properties"></a>Klíčové vlastnosti  
 Vlastnost klíče ovládacího prvku je <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, ve kterém se nastaví náhled dokumentu. Dokument musí být objekt <xref:System.Drawing.Printing.PrintDocument>. Přehled vytváření dokumentů pro tisk najdete v tématu [Přehled komponent PrintDocument](printdocument-component-overview-windows-forms.md) a [Podpora tisku model Windows Forms](../advanced/windows-forms-print-support.md). Vlastnosti <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> a <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> určují počet stránek zobrazených vodorovně a svisle na ovládacím prvku. Antialiasing může zobrazit hladší text, ale může také zpomalit zobrazení. Pokud ho chcete použít, nastavte vlastnost <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> na `true`.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.PrintPreviewControl>
- [Přehled ovládacího prvku PrintPreviewDialog](printpreviewdialog-control-overview-windows-forms.md)
- [Ovládací prvek PrintPreviewControl](printpreviewcontrol-control-windows-forms.md)
- [Ovládací prvky a součásti dialogového okna](dialog-box-controls-and-components-windows-forms.md)
