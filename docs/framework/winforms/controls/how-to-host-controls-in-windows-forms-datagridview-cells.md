---
title: "Postupy: Umisťování ovládacích prvků do buněk Windows Forms DataGridView"
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
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dbd315b5980c0aed222c9576632064ea9f7b2ce1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a>Postupy: Umisťování ovládacích prvků do buněk Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> Ovládací prvek obsahuje několik typů sloupce, povolíte uživatelům zadat a upravit hodnoty v mnoha různými způsoby. Pokud tyto typy sloupců nevyhovuje vašim potřebám zadávání dat, ale můžete vytvořit vlastní typy sloupců s buněk, které jsou hostiteli ovládací prvky dle vlastního výběru. Chcete-li to provést, je nutné definovat třídy, které jsou odvozeny od <xref:System.Windows.Forms.DataGridViewColumn> a <xref:System.Windows.Forms.DataGridViewCell>. Je třeba definovat třídu odvozenou z <xref:System.Windows.Forms.Control> a implementuje <xref:System.Windows.Forms.IDataGridViewEditingControl> rozhraní.  
  
 Následující příklad kódu ukazuje, jak vytvořit kalendář sloupec. V buňkách v tomto sloupci zobrazení dat v buňkách obyčejného textového pole, ale když uživatel upravuje buňku, <xref:System.Windows.Forms.DateTimePicker> ovládací prvek se zobrazí. Aby se zabránilo museli znovu, implementovat funkce zobrazení textového pole `CalendarCell` třída odvozená z <xref:System.Windows.Forms.DataGridViewTextBoxCell> třída spíše než dědění <xref:System.Windows.Forms.DataGridViewCell> přímo třídu.  
  
> [!NOTE]
>  Pokud odvozujete od <xref:System.Windows.Forms.DataGridViewCell> nebo <xref:System.Windows.Forms.DataGridViewColumn> a přidání nových vlastností do odvozené třídy, je nutné přepsat `Clone` metoda kopírování nové vlastnosti během operací klonování. Měli byste také zavolat základní třídy `Clone` metoda tak, aby vlastnosti základní třídy jsou zkopírovány do nového buňky nebo sloupec.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Následující příklad vyžaduje:  
  
-   Odkazy na systém a System.Windows.Forms sestavení.  
  
 Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 <xref:System.Windows.Forms.DateTimePicker>  
 [Přizpůsobení ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [Architektura ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [Typy sloupců v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
