---
title: Zakázání tlačítek ve sloupci tlačítka v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
ms.openlocfilehash: 691781a43005d66e13029ab8110eb7f9daacc35f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745945"
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a>Postupy: Zákaz tlačítek ve sloupci tlačítek v ovládacím prvku Windows Forms DataGridView
Ovládací prvek <xref:System.Windows.Forms.DataGridView> obsahuje třídu <xref:System.Windows.Forms.DataGridViewButtonCell> pro zobrazení buněk s uživatelským rozhraním (UI) jako tlačítko. <xref:System.Windows.Forms.DataGridViewButtonCell> ale neposkytuje způsob, jak zakázat vzhled tlačítka zobrazovaného buňkou.  
  
 Následující příklad kódu ukazuje, jak přizpůsobit třídu <xref:System.Windows.Forms.DataGridViewButtonCell> pro zobrazení tlačítek, která se mohou zobrazit zakázané. Příklad definuje nový typ buňky `DataGridViewDisableButtonCell`, který je odvozen z <xref:System.Windows.Forms.DataGridViewButtonCell>. Tento typ buňky poskytuje novou vlastnost `Enabled`, kterou lze nastavit tak, aby `false` vykreslila zakázané tlačítko v buňce. V příkladu je také definován nový typ sloupce `DataGridViewDisableButtonColumn`, který zobrazí `DataGridViewDisableButtonCell` objekty. Chcete-li Ukázat tento nový typ buňky a sloupce, aktuální hodnota každé <xref:System.Windows.Forms.DataGridViewCheckBoxCell> v nadřazené <xref:System.Windows.Forms.DataGridView> určuje, zda je vlastnost `Enabled` `DataGridViewDisableButtonCell` na stejném řádku `true` nebo `false`.  
  
> [!NOTE]
> Při odvozování z <xref:System.Windows.Forms.DataGridViewCell> nebo <xref:System.Windows.Forms.DataGridViewColumn> a přidání nových vlastností do odvozené třídy nezapomeňte přepsat metodu `Clone` pro kopírování nových vlastností během operací klonování. Měli byste také zavolat metodu `Clone` základní třídy tak, aby byly vlastnosti základní třídy zkopírovány do nové buňky nebo sloupce.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. Drawing, System. Windows. Forms a System. Windows. Forms. VisualStyles.  
  
## <a name="see-also"></a>Viz také

- [Přizpůsobení ovládacího prvku Windows Forms DataGridView](customizing-the-windows-forms-datagridview-control.md)
- [Architektura ovládacího prvku DataGridView](datagridview-control-architecture-windows-forms.md)
- [Typy sloupců v ovládacím prvku Windows Forms DataGridView](column-types-in-the-windows-forms-datagridview-control.md)
