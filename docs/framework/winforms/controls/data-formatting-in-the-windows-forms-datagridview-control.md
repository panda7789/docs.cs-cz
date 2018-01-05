---
title: "Formátování dat v ovládacím prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in grids
- data grids [Windows Forms], formatting data
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6ff3452a60d9cb80a71dacd5841b120b5efbf82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="data-formatting-in-the-windows-forms-datagridview-control"></a>Formátování dat v ovládacím prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> Řízení poskytuje automatický převod mezi hodnoty buněk a typy dat, které se zobrazí nadřazené sloupce. Textové pole sloupce, například zobrazit řetězcové vyjádření datum, čas, číslo a hodnoty výčtu a převést zadanou uživatelem řetězcové hodnoty na typy úložiště dat vyžaduje.  
  
## <a name="formatting-with-the-datagridviewcellstyle-class"></a>Formátování s DataGridViewCellStyle – třída  
 <xref:System.Windows.Forms.DataGridView> Řízení poskytuje základní data formátování hodnot v buňkách prostřednictvím <xref:System.Windows.Forms.DataGridViewCellStyle> třídy. Můžete použít <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> vlastnost Formát hodnoty date, time, číslo a výčtu pro výchozí jazykovou verzi použití specifikátorů formátu popsané v [typy formátování](../../../../docs/standard/base-types/formatting-types.md). Můžete také formátovat tyto hodnoty pro konkrétní jazykové verze pomocí <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A> vlastnost. Zadaný formát slouží k zobrazení dat a analyzovat data, která uživatel zadá v zadaném formátu.  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle> Třída poskytuje další vlastnosti formátování pro zalamování řádků, zarovnání textu a vlastní zobrazení hodnot null databáze. Další informace najdete v tématu [postupy: formátování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="formatting-with-the-cellformatting-event"></a>Formátování s CellFormatting událostí  
 Pokud základní formátování nevyhovuje vašim potřebám, můžete zadat vlastní formátování dat v obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> událostí. <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> Předaný obslužná rutina má <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> vlastnost, která původně obsahuje hodnotu buňky. Za normálních okolností tato hodnota je automaticky převeden na typ zobrazení. Chcete-li převést hodnotu, nastavte <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> vlastnost na hodnotu typu zobrazení.  
  
> [!NOTE]
>  Pokud se řetězec formátu pro buňky v platnosti, přepíše vaše změna <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> není-li nastavena hodnota vlastnosti <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A> vlastnost `true`.  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting> Událostí je užitečné také, když chcete nastavit <xref:System.Windows.Forms.DataGridViewCellStyle> vlastnosti pro jednotlivé buňky na základě jejich hodnot. Další informace najdete v tématu [postupy: přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
 Pokud výchozí analýza zadaného uživatelem hodnot nevyhovuje vašim potřebám, může zpracovávat <xref:System.Windows.Forms.DataGridView.CellParsing> události <xref:System.Windows.Forms.DataGridView> řízení poskytnout vlastní analýze.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Postupy: Formátování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 [Postupy: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
