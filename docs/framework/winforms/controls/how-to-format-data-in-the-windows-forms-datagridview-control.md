---
title: "Postupy: Formátování dat v ovládacím prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in DataGridView control
- data grids [Windows Forms], enabling wordwrap
- currency values [Windows Forms], formatting in data grids
- data grids [Windows Forms], currency values
- data grids [Windows Forms], formatting data
- data grids [Windows Forms], text alignment
- data grids [Windows Forms], date values
- cells [Windows Forms], text alignment
ms.assetid: 8c33543c-9c08-4636-a65a-fdf714a529b7
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 49d5172b2638a7ac3a6a7bf005932ba4b3f9aba3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a>Postupy: Formátování dat v ovládacím prvku Windows Forms DataGridView
Následující postupy ukazují základní formátování hodnot v buňkách pomocí <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> vlastnost <xref:System.Windows.Forms.DataGridView> řízení a konkrétní sloupců v ovládacím prvku. Informace o formátu pokročilé dat najdete v tématu [postupy: přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-format-currency-and-date-values"></a>Hodnoty data a formátu měny  
  
-   Nastavte <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle>. Následující příklad kódu nastaví formát pro určité sloupce pomocí <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> vlastnost sloupců. Hodnoty v `UnitPrice` sloupec se zobrazí v aktuálním formátu měny specifické pro jazykovou verzi, se záporné hodnoty v závorkách. Hodnoty v `ShipDate` sloupci se zobrazují ve formátu krátkého data aktuální specifické pro jazykovou verzi. Další informace o <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> hodnoty, najdete v části [typy formátování](../../../../docs/standard/base-types/formatting-types.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a>Pro přizpůsobení zobrazení hodnot null databáze  
  
-   Nastavte <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle>. Následující příklad kódu používá <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> vlastnost zobrazíte "žádný záznam" v všechny buňky obsahující hodnoty, které se rovná <xref:System.DBNull.Value?displayProperty=nameWithType>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a>Chcete-li povolit zalamování řádků v buňkách založený na textu  
  
-   Nastavte <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle> na jednu z <xref:System.Windows.Forms.DataGridViewTriState> hodnot výčtu. Následující příklad kódu používá <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> vlastnost, která má nastaven režim zalamování pro celý ovládací prvek.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a>K určení zarovnání textu buněk DataGridView  
  
-   Nastavte <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle> na jednu z <xref:System.Windows.Forms.DataGridViewContentAlignment> hodnot výčtu. Následující příklad kódu nastaví zarovnání pro konkrétní sloupec pomocí <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> vlastnost sloupce.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tyto příklady vyžadují:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1` , který obsahuje sloupec s názvem `UnitPrice`, sloupec s názvem `ShipDate`a sloupec s názvem `CustomerName`.  
  
-   Odkazuje na <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="robust-programming"></a>Robustní programování  
 Pro maximální škálovatelnost, by měly sdílet <xref:System.Windows.Forms.DataGridViewCellStyle> objektů mezi více řádků, sloupců nebo buněk, které používají stejné styly spíše než nastavení vlastnosti stylu pro každý prvek samostatně. Další informace najdete v tématu [osvědčené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [Základní formátování a styly v systému Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Formátování dat v systému Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)  
 [Postupy: přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 [Typy formátování](../../../../docs/standard/base-types/formatting-types.md)
