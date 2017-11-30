---
title: "Postupy: Nastavení výchozích stylů buňky a datových formátů pro ovládací prvek Windows Forms DataGridView pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], setting styles
- data formats
- data [Windows Forms], setting formats
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 28f81efa3d9f63127ad9748aaba9ce3483246a69
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-default-cell-styles-and-data-formats-for-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Nastavení výchozích stylů buňky a datových formátů pro ovládací prvek Windows Forms DataGridView pomocí Návrháře
<xref:System.Windows.Forms.DataGridView> Řízení umožňuje zadejte výchozích stylů buňky a data formátů pro celý ovládací prvek pro konkrétní sloupce, pro záhlaví řádků a sloupců a střídavých řádků vytvořit hlavní knihy efekt buňky. Ve výchozím nastavení se styly nastavení pro sloupce a střídavých řádků se přepíšou výchozí styly pro celý ovládací prvek. Kromě toho stylů, které se nastavují v kódu pro jednotlivé řádky a buněk přepsat výchozí styly.  
  
 Další informace o styly buňky najdete v tématu [styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md). Nastavení stylů střídavých řádků, najdete v části [postupy: nastavení střídavých řádků styly Windows Forms DataGridView – ovládací prvek s využitím návrháře](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md).  
  
 Můžete vytvořit také pomocí stylů <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> vlastnost, která má vliv na všechny řádky, které budou přidány do ovládacího prvku. Další informace o šabloně řádek najdete v tématu [postupy: použití šablony řádku k přizpůsobení řádků v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/use-the-row-template-to-customize-rows-in-the-datagrid.md).  
  
 Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře obsahující <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-default-styles-for-all-cells-in-the-control"></a>K nastavení výchozích stylů pro všechny buňky v ovládacím prvku  
  
1.  Vyberte <xref:System.Windows.Forms.DataGridView> ovládacího prvku v návrháři.  
  
2.  V **vlastnosti** okně klikněte na tlačítko se třemi tečkami (![– snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>, nebo <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> vlastnost. **Objektu CellStyle** zobrazí se dialogové okno.  
  
3.  Definovat styl nastavením vlastností, pomocí **Preview** podokně k potvrzení voleb.  
  
> [!NOTE]
>  Pokud jsou povolené vizuální styly, záhlaví řádků a sloupců (s výjimkou <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) jsou automaticky ve podle aktuálního motivu přepsání <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> a <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> hodnot vlastností.  
>   
>  Můžete nastavit styly buňky pro více vybraných <xref:System.Windows.Forms.DataGridView> ovládací prvky pomocí návrháře, ale pouze v případě, že mají stejné hodnoty pro vlastnost stylu buněk, které chcete upravit. Pokud žádné styly buňky liší pro tuto vlastnost **vlastnosti** windows z **objektu CellStyle** dialogové okno bude prázdné.  
  
### <a name="to-set-default-styles-for-cells-in-individual-columns"></a>Chcete-li nastavit výchozí styl buněk v jednotlivých sloupcích  
  
1.  Klikněte pravým tlačítkem myši <xref:System.Windows.Forms.DataGridView> řízení v návrháři a zvolte **upravit sloupce**.  
  
2.  Vyberte sloupce z **vybrané sloupce** seznamu.  
  
3.  V **vlastnosti sloupce** mřížky, klikněte na tlačítko se třemi tečkami (![– snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> vlastnost. **Objektu CellStyle** zobrazí se dialogové okno.  
  
4.  Definovat styl nastavením vlastností, pomocí **Preview** podokně k potvrzení voleb.  
  
### <a name="to-format-data-in-cells"></a>Formátování dat v buňkách  
  
1.  Použijte jednu z předchozích postupů k zobrazení **objektu CellStyle** dialogové okno související s výchozí vlastnost styl buněk.  
  
2.  V **objektu CellStyle** dialogovém okně klikněte na tlačítko se třemi tečkami (![VisualStudioEllipsesButton snímek](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> Vlastnost. **Řetězec formátu** zobrazí se dialogové okno.  
  
3.  Vyberte typ formátu a pak upravit podrobnosti o typu (například počet desetinných míst k zobrazení), pomocí **ukázka** políčka potvrďte vybrané možnosti.  
  
4.  Pokud vytváříte vazbu <xref:System.Windows.Forms.DataGridView> řízení ke zdroji dat, která by mohla obsahovat hodnoty null, zadejte **hodnotu Null** textové pole. Tato hodnota se zobrazí, pokud buňka hodnota se rovná odkaz s hodnotou null (`Nothing` v jazyce Visual Basic) nebo <xref:System.DBNull.Value?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=nameWithType>  
 [Styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Postupy: nastavení střídavých stylů řádků pro Windows Forms DataGridView – ovládací prvek pomocí návrháře](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)  
 [Postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
