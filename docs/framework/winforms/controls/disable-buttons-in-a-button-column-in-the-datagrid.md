---
title: 'Postupy: Zákaz tlačítek ve sloupci tlačítek v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
ms.openlocfilehash: b8bb503186e41c682b0685e4c9c4bf0bb3adcbe8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967387"
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a>Postupy: Zákaz tlačítek ve sloupci tlačítek v ovládacím prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> Ovládací prvek <xref:System.Windows.Forms.DataGridViewButtonCell> obsahuje třídu pro zobrazení buněk s uživatelským rozhraním (UI) jako tlačítko. <xref:System.Windows.Forms.DataGridViewButtonCell> Ale neposkytuje způsob, jak zakázat vzhled tlačítka zobrazovaného buňkou.  
  
 Následující příklad kódu ukazuje, jak přizpůsobit <xref:System.Windows.Forms.DataGridViewButtonCell> třídu pro zobrazení tlačítek, která se mohou zobrazit zakázané. Příklad definuje nový typ `DataGridViewDisableButtonCell`buňky,, který je odvozen z. <xref:System.Windows.Forms.DataGridViewButtonCell> Tento typ buňky poskytuje novou `Enabled` vlastnost, kterou lze `false` nastavit na vykreslení zakázaného tlačítka v buňce. V příkladu je také definován nový typ `DataGridViewDisableButtonColumn`sloupce, který zobrazuje `DataGridViewDisableButtonCell` objekty. Pro ukázku tohoto nového typu buňky a sloupce určuje aktuální <xref:System.Windows.Forms.DataGridViewCheckBoxCell> hodnota každého v nadřazeném objektu <xref:System.Windows.Forms.DataGridView> , `DataGridViewDisableButtonCell` zda `Enabled` je `true` vlastnost ve stejném řádku nebo `false`.  
  
> [!NOTE]
> Při odvozování z <xref:System.Windows.Forms.DataGridViewCell> nebo <xref:System.Windows.Forms.DataGridViewColumn> a přidání nových vlastností na odvozenou třídu nezapomeňte přepsat `Clone` metodu pro kopírování nových vlastností během operací klonování. Měli byste také zavolat `Clone` metodu základní třídy tak, aby byly vlastnosti základní třídy zkopírovány do nové buňky nebo sloupce.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. Drawing, System. Windows. Forms a System. Windows. Forms. VisualStyles.  
  
## <a name="see-also"></a>Viz také:

- [Přizpůsobení ovládacího prvku Windows Forms DataGridView](customizing-the-windows-forms-datagridview-control.md)
- [Architektura ovládacího prvku DataGridView](datagridview-control-architecture-windows-forms.md)
- [Typy sloupců v ovládacím prvku Windows Forms DataGridView](column-types-in-the-windows-forms-datagridview-control.md)
