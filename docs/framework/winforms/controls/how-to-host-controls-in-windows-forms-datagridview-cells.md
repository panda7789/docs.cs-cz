---
title: 'Postupy: Hostitelské ovládací prvky v buňkách Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
ms.openlocfilehash: a97af9bf0ef4016e54f877d934ed401b8dde7d4e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966597"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a>Postupy: Hostitelské ovládací prvky v buňkách Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> Ovládací prvek poskytuje několik typů sloupců, které uživatelům umožňují zadávat a upravovat hodnoty mnoha různými způsoby. Pokud tyto typy sloupců nesplňují požadavky na datovou položku, můžete vytvořit vlastní typy sloupců s buňkami, které řídí ovládací prvky pro výběr. Chcete-li to provést, je nutné definovat třídy, <xref:System.Windows.Forms.DataGridViewColumn> které <xref:System.Windows.Forms.DataGridViewCell>jsou odvozeny z a. Musíte také definovat třídu, která je odvozena z <xref:System.Windows.Forms.Control> a <xref:System.Windows.Forms.IDataGridViewEditingControl> implementuje rozhraní.  
  
 Následující příklad kódu ukazuje, jak vytvořit sloupec kalendáře. Buňky v tomto sloupci zobrazují data v běžných buňkách textového pole, ale když uživatel upraví buňku, <xref:System.Windows.Forms.DateTimePicker> zobrazí se ovládací prvek. Chcete-li se vyhnout nutnosti implementovat funkce textového pole znovu, `CalendarCell` třída je odvozena <xref:System.Windows.Forms.DataGridViewTextBoxCell> od třídy <xref:System.Windows.Forms.DataGridViewCell> místo přímého dědění třídy.  
  
> [!NOTE]
> Při odvozování z <xref:System.Windows.Forms.DataGridViewCell> nebo <xref:System.Windows.Forms.DataGridViewColumn> a přidání nových vlastností na odvozenou třídu nezapomeňte přepsat `Clone` metodu pro kopírování nových vlastností během operací klonování. Měli byste také zavolat `Clone` metodu základní třídy tak, aby byly vlastnosti základní třídy zkopírovány do nové buňky nebo sloupce.  
  
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
