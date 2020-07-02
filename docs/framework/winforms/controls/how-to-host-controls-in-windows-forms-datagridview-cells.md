---
title: Hostitelské ovládací prvky v buňkách DataGridView
description: Naučte se hostovat ovládací prvky v model Windows Formsch buňkách DataGridView a umožnit tak uživatelům zadávat a upravovat hodnoty různými způsoby.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
ms.openlocfilehash: 87901cbf86689bec49f5692feeabdae79f6b93ba
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619543"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a>Postupy: Umisťování ovládacích prvků do buněk Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView>Ovládací prvek poskytuje několik typů sloupců, které uživatelům umožňují zadávat a upravovat hodnoty mnoha různými způsoby. Pokud tyto typy sloupců nesplňují požadavky na datovou položku, můžete vytvořit vlastní typy sloupců s buňkami, které řídí ovládací prvky pro výběr. Chcete-li to provést, je nutné definovat třídy, které jsou odvozeny z <xref:System.Windows.Forms.DataGridViewColumn> a <xref:System.Windows.Forms.DataGridViewCell> . Musíte také definovat třídu, která je odvozena z <xref:System.Windows.Forms.Control> a implementuje <xref:System.Windows.Forms.IDataGridViewEditingControl> rozhraní.  
  
 Následující příklad kódu ukazuje, jak vytvořit sloupec kalendáře. Buňky v tomto sloupci zobrazují data v běžných buňkách textového pole, ale když uživatel upraví buňku, <xref:System.Windows.Forms.DateTimePicker> zobrazí se ovládací prvek. Chcete-li se vyhnout nutnosti implementovat funkce textového pole znovu, třída je `CalendarCell` odvozena od <xref:System.Windows.Forms.DataGridViewTextBoxCell> třídy místo přímého dědění <xref:System.Windows.Forms.DataGridViewCell> třídy.  
  
> [!NOTE]
> Při odvozování z <xref:System.Windows.Forms.DataGridViewCell> nebo <xref:System.Windows.Forms.DataGridViewColumn> a přidání nových vlastností na odvozenou třídu nezapomeňte přepsat `Clone` metodu pro kopírování nových vlastností během operací klonování. Měli byste také zavolat metodu základní třídy `Clone` tak, aby byly vlastnosti základní třídy zkopírovány do nové buňky nebo sloupce.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Následující příklad vyžaduje:  
  
- Odkazy na sestavení System a System. Windows. Forms.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>
- <xref:System.Windows.Forms.IDataGridViewEditingControl>
- <xref:System.Windows.Forms.DateTimePicker>
- [Přizpůsobení ovládacího prvku Windows Forms DataGridView](customizing-the-windows-forms-datagridview-control.md)
- [Architektura ovládacího prvku DataGridView](datagridview-control-architecture-windows-forms.md)
- [Typy sloupců v ovládacím prvku Windows Forms DataGridView](column-types-in-the-windows-forms-datagridview-control.md)
